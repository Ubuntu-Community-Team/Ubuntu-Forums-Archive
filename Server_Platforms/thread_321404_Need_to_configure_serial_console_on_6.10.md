---
title: "Need to configure serial console on 6.10"
date: 2006-12-18
forum: Server Platforms
---

### Post by ghstridr on 2006-12-18
I've been searching for a few days and spent some time in irc and haven't found my answers.
I have a box with 6.10 on it that I need to get a serial console working on.
I do have 'console=tty0 console=ttyS0,9600' in the grub conf and can see the text output on the serial port.
I just don't ever get a login prompt.
Normally I would simply edit /etc/inittab and be done with it.  Since 6.10 now uses 'udev', I haven't a clue how to accomplish what I need.  I've tried reading the docs for udev, but haven't found anything I could use.
Anybody have any input? ](*,)

---

### Post by nandy1925 on 2007-01-31
here's the URL i just found that may solve our problem:

[http://www.mail-archive.com/ubuntu-in@lists.ubuntu.com/msg00295.html](http://www.mail-archive.com/ubuntu-in@lists.ubuntu.com/msg00295.html)

good luck!

---

