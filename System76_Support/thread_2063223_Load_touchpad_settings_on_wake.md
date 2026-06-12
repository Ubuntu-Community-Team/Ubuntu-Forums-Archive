---
title: "Load touchpad settings on wake"
date: 2012-09-26
forum: System76 Support
---

### Post by Carleas on 2012-09-26
I'm running 12.04 on a Star4, and I've had problems with my touchpad settings in the past (see [this thread]("http://ubuntuforums.org/showthread.php?t=1846404")), but following the instructions in the System76 knowledge base, my settings load properly at startup.  However, they reset after I close the lid, which is a mild annoyance.  I usually just execute the settings file, but I've been trying to set up a script to do it automatically.  

I created a file **/etc/pm/sleep.d/90_toupadsettings** 

These are the contents:

```
#!/bin/bash

# Reload touchpad setting on wake.
# Settings are stored at /usr/bin/start-touchpad

case "{$1}" in
        suspend|hibernate)
                # do nothing
        ;;
        resume|thaw|wake)
                /usr/bin/start-touchpad
        ;;
esac

```

This doesn't work.  Is there something wrong with the script?  Could it be the permisisons?
These are the permissions for **90_touchpadsettings**
```
$ ls -l 90_touchpadsettings
-rwxr-xr-x 1 root root  213 Sep 26 13:27 90_touchpadsettings
```
And here they are for **start-touchpad**
```
$ ls -l start-touchpad 
-rwxr-xr-x 1 root root 46 Nov 10  2011 start-touchpad

```
Any ideas?

---

### Post by Carleas on 2013-01-15
I fixed this problem after some googling, I thought I'd share the solution.

For some reason, fspc won't run from a script, nor aparently from a file executed from a script.  But from [this bug report](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/311869), I learned that the settings can be set directly, without going through fspc.

I changed my wakeup script to look like this:
```

#!/bin/sh
# disable tap-to-click on wake by modifying the flags file.
 
case "${1}" in
        resume|thaw)
        echo "c" > /sys/devices/platform/i8042/serio2/flags
        ;;
esac

```

The lowercase 'c' is the flag to turn off tap-to-click (uppercase C turns it on).  Other flags are listed in the discussion of the bug report.  Other options are set in other files in serio2, such as vscroll and hscroll for vertical and horizontal scrolling respectively.  Also, the bug report discussion indcates that the directory serio# can be differently numbered.

Hope this helps someone with a similar problem. :)

---

