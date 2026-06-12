---
title: "PLEASE!! Help me solve E: Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2015-06-12
forum: Ubuntu/Debian BASED
---

### Post by Leo_Wong on 2015-06-12
Elementary os:
```
(Reading database ... 166187 files and directories currently installed.)
Removing sogoupinyin (1.2.0.0056) ...
/var/lib/dpkg/info/sogoupinyin.postrm: 7: local: OS": bad variable name
dpkg: error processing package sogoupinyin (--remove):
 subprocess installed post-removal script returned error exit status 2
Errors were encountered while processing:
 sogoupinyin
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

---

### Post by denizdurmus on 2016-01-16
Related part of the file is like:

```
 #!/bin/sh
  2 set -e
  3 
  4 detect_distro ()
  5 {
  6 if [ -r /etc/os-release ]; then
  7     local RELEASE_ID=$(grep '^ID=' /etc/os-release  | cut -f2 -d'=')
  8     local RELEASE_ID_LIKE=$(grep '^ID_LIKE=' /etc/os-release  | cut -f2 -d'=')
  9 fi
 10 case $RELEASE_ID in
 11     ubuntu|debian)
 12         RELEASE_GENERIC=debian
 13         ;;
 14     fedora|rhel)
 15         RELEASE_GENERIC=fedora
 16         ;;
 17     opensuse|suse)
 18         RELEASE_GENERIC=opensuse
 19         ;;
 20     *)
 21         if `echo $RELEASE_ID_LIKE | grep ubuntu >/dev/null` || `echo $RELEASE_ID_LIKE | grep debian >/dev/null`; then
 22             RELEASE_GENERIC=debian
 23         elif `echo $RELEASE_ID_LIKE | grep fedora >/dev/null` || `echo $RELEASE_ID_LIKE | grep rhel >/dev/null`; then
 24             RELEASE_GENERIC=fedora
 25         elif `echo $RELEASE_ID_LIKE | grep opensuse >/dev/null` || `echo $RELEASE_ID_LIKE | grep suse >/dev/null`; then
 26             RELEASE_GENERIC=opensuse
 27         else
 28             RELEASE_GENERIC=unknown
 29         fi
 30         ;;
 31 esac
 32 }
```

so it doesnt have any checks for elementary os... you need to put a # at the begining of the line 7, then just press enter to a newline, add

local RELEASE_ID=ubuntu

then save it and re-run the command, it will run smooth

---

