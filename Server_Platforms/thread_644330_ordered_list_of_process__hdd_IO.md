---
title: "ordered list of process  hdd I/O"
date: 2007-12-18
forum: Server Platforms
---

### Post by frankabel on 2007-12-18
Hi all,

Ones can see the amount of memory and cpu a process is consuming easily with top, etc. But what command I must use to see the amount of I/O (harddisk and why not, network too) each process is making?

Happen that some times a server get slow due to I/O, not due to cpu or memory.

Salute
Frank Abel

---

### Post by craigp84 on 2007-12-20
Hi Frank,

Quick notes to point you in the right direction.The following commands are infinitely useful

iostat, vmstat, netstat & sar.

Other "fancy" tools like darkstat may help too.

---

### Post by frankabel on 2008-02-05
Very useful commands, but no way of found what parameters I must pass to them to get a list of process sorted by its IO usage.

I think that such stats is really important, because lots of time a process that is downing the performance of the whole system "only consume" IO.

Salute
Frank Abel

---

### Post by craigp84 on 2008-02-05
These commands are general "system level" commands; that is they will show you the system as a whole, not per application as it sound's you need.

Don't despair! SystemTap sounds like a better fit for your needs. Google it and you'll find the wiki, there's a .stp file already out there to show per application I/O usage.

For installing on Ubuntu there's a gotcha - after you "sudo apt-get install systemtap" you'll also need to "sudo apt-get install linux-image-debug" which is required by systemtap but not configured in the systemtap .deb as a dependancy. There's 1 more gotcha - you'll need to create a symlink in /boot from /boot/vmlinux-version to the installed /boot/vmlinux-debug-version -that is the exact same filename, minus the "-debug". Systemtap will then work: sudo ln -s /boot/vmlinux-debug-version /boot/vmlinux-version.

I'm in the process of trying to get stap adopted at my work for all new production builds of Linux (redhat). It isn't quite as elegant as dtrace (the Solaris / FreeBSD / Apple) equivelant IMO. My main frustration's down to permissioning - if i give a user sudo access to stap, they can modify the running kernel. That's about all the granularity you get, whereas on Solaris 10 i get slightly (thought not much) better control over what they can / cannot do using dtrace through Solaris Privileges.

Hope this helps,

-c

---

