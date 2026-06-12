---
title: "udev rules to check if file exists"
date: 2011-06-09
forum: Server Platforms
---

### Post by Chrus on 2011-06-09
Is it possible to set up a udev rule that will check  if a file exists on a USB drive?

I've got a few ubuntu servers in environments with some very not-techy peoples. Im hoping to get to the point where I can give them a few USB sticks with scripts on them, and if they plus one of these sticks in it will be mounted in, say, /media/special (rather than /media/usb0..7) and then the script would be run. But if a usb drive without special.sh is inserted, it should be mounted to /media/usb0..7 as normal.

I've been googeling for udev rules, and it seems simple enough to specify a mount point based on brand/model/serialnumber/etc... but i havent been able to find anything about checking for the existance of a file.

Tho the more i think about it, the more im starting to think its not going to be that straight forward. Can udev check for a file on a drive before that drive is mounted? Is it going to be a case of mounting every drive to /media/usb0..7 then having a script run that will check for the file, and if its there change the mount point before running special.sh?

Any advice would be appreciated.

Thanks.

---

### Post by Lars Noodén on 2011-06-09
> **Chrus said:**
> ... but i havent been able to find anything about checking for the existance of a file...

You could do it in the shell with [test -f](http://manpages.ubuntu.com/manpages/natty/en/man1/test.1posix.html).  

```

test -f /path/to/somefile && echo YES || echo NO

```

The hard part will be to guess the mount point if it moves around.

---

