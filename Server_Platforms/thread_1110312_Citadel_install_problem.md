---
title: "Citadel install problem"
date: 2009-03-29
forum: Server Platforms
---

### Post by Diverted Income on 2009-03-29
Trying to use the Easy Citadel Install. It dies without completing. Here is the tail end of the log file. 

/usr/bin/install -c setup /usr/local/webcit/setup
test -d /usr/local/webcit/static.local || mkdir -p /usr/local/webcit/static.local
test -d /usr/local/webcit/static || mkdir -p /usr/local/webcit/static
for i in `find static -type f | grep -v .svn`; do \
		/usr/bin/install -c $i /usr/local/webcit/$i; \
	done
test -d /usr/local/webcit/static || mkdir -p /usr/local/webcit/static
for i in `find tiny_mce -type d | grep -v .svn` \
		; do \
		test -d /usr/local/webcit/$i || mkdir -p /usr/local/webcit/$i; \
	done
for i in \
		`find tiny_mce -type f | grep -v .svn` \
		; do \
		/usr/bin/install -c $i /usr/local/webcit/$i; \
	done
cd po; make
make[1]: Entering directory `/tmp/citadel-build.7036/webcit/po'
Makefile:39: warning: overriding commands for target `../locale/nl/LC_MESSAGES/webcit.mo'
Makefile:35: warning: ignoring old commands for target `../locale/nl/LC_MESSAGES/webcit.mo'
[ -d ../locale/de/LC_MESSAGES ] || mkdir -p ../locale/de/LC_MESSAGES
msgfmt de.po -o ../locale/de/LC_MESSAGES/webcit.mo
make[1]: msgfmt: Command not found
make[1]: *** [../locale/de/LC_MESSAGES/webcit.mo] Error 127
make[1]: Leaving directory `/tmp/citadel-build.7036/webcit/po'
make: *** [install-locale] Error 2
Operating system: Linux Debian lenny/sid ( 2.6.27-11-server i686)






Any thoughts?

---

### Post by windependence on 2009-03-30
Yes, why didn't you just do:

```
sudo apt-get install citadel-suite
```

Don't compile if you don't have to.

-Tim

---

