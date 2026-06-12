---
title: "Linux Kernel 2.6 UDEV Local Privilege Escalation Exploit by kcope"
date: 2009-04-20
forum: Security
---

### Post by x3roconf on 2009-04-20
Link: [http://milw0rm.com/exploits/download/8478]("http://milw0rm.com/exploits/download/8478")
...............
# Linux 2.6
# bug found by Sebastian Krahmer
#
# lame sploit using LD technique 
# by kcope in 2009
# tested on debian-etch,ubuntu,gentoo
# do a 'cat /proc/net/netlink'
# and set the first arg to this
# script to the pid of the netlink socket
# (the pid is udevd_pid - 1 most of the time)
# + sploit has to be UNIX formatted text :)
# + if it doesn't work the 1st time try more often
#
# WARNING: maybe needs some FIXUP to work flawlessly
## greetz fly out to alex,andi,adize,wY!,revo,j! and the gang

...............

Has anyone tried this?

---

### Post by cdenley on 2009-04-20
[http://www.ubuntu.com/usn/usn-758-1](http://www.ubuntu.com/usn/usn-758-1)

---

