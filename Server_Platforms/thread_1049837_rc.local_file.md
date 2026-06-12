---
title: "rc.local file"
date: 2009-01-25
forum: Server Platforms
---

### Post by test006 on 2009-01-25
Hi,
I am trying to add some commands which needs to be loaded during bootup process. 
On my ubuntu server (8.10) there are to rc.local files i.e. /etc/init.d/rc.local and /etc/rc.local.
Which rc.local file should i put my commands so it gets loaded at the bootup time?
Looking at the /etc/rc.local file it says the following:
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

exit 0

```
and when i do ls -lh on /etc/rc.local file i get
```
-rwxr-xr-x 1 root root 306 2009-01-17 10:57 rc.local

```

What changes do i have to do add my commands to this file?

Thanks

---

### Post by pnutzh4x0r on 2009-01-25
You can add your commands to the /etc/rc.local file.  Just put your commands before the exit 0 line.  Your execution bits are fine, and don't need changing (if you want it enabled).

---

