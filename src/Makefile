deb:
	cd docs; make; cd ..;
	for subd in backups lib  logs  temp  webapps; do \
	  mkdir -p ./pkg/usr/share/dhis2-tools/skel/$$subd; \
	done

	mkdir -p ./pkg/var/lib/dhis2;

	#permissions
	find ./pkg/usr -type d -exec chmod 0755 {} \;
	find ./pkg/usr -type f -exec chmod 0644 {} \;
	find ./pkg/etc -type d -exec chmod 0755 {} \;
	find ./pkg/etc -type f -exec chmod 0644 {} \;

clean:
	cd docs; make clean; cd ..
	for subd in backups lib  logs  temp  webapps; do \
	   rm -rf ./pkg/usr/share/dhis2-tools/skel/$$subd; \
	done

	rm -rf ./pkg/var/lib/dhis2;

	#perimissions
	find ./pkg/usr -type d -exec chmod 0755 {} \;
	find ./pkg/usr -type f -exec chmod 0644 {} \;

install:
		set -e

		#perimissions

		find ./pkg/etc -type d -exec chmod 0755 {} \;
		find ./pkg/etc -type f -exec chmod 0644 {} \;

		# Copy binaries and configs

		cp -rf ./pkg/etc/sudoers.d/dhis2 /etc/sudoers.d/
		cp -rf ./pkg/var/lib/dhis2 /var/lib/
		cp -rf ./pkg/var/log/dhis2 /var/log/
		cp -rf ./pkg/usr/share/dhis2-tools /usr/share/
		cp -rf ./pkg/usr/share/doc/dhis2-tools /usr/share/doc/
		cp -rf ./pkg/usr/share/man/man1/* /usr/share/man/man1/
		cp -rf ./pkg/usr/bin/* /usr/bin/

		# postinstall

		echo "create group for dhis instances and group for dhis admins"
		addgroup dhis2admin 2>/dev/null || { echo "dhis2admin group exists"; }
		addgroup dhis2 2>/dev/null || { echo "dhis2 group exists"; }
