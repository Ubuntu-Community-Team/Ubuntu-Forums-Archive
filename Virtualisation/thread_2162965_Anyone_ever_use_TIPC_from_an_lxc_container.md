---
title: "Anyone ever use TIPC from an lxc container?"
date: 2013-07-16
forum: Virtualisation
---

### Post by srhadden on 2013-07-16
I'm trying to get a program running within an lxc container, but it uses the TIPC inter-process communication module. 

The socket to tipc fails from the lxc container, it works fine from the host.

Having a hard time finding any info on this, only a couple of posts on the tipc discussion groups, so I thought I'd try here.

One idea but it's probably an ignorant question, because I don't understand the LXC architecture at a low enough level, is that I noticed the LXC container doesn't have a kernel directory.  I thought maybe I could shut down tipc module in the host and then install/run the tipc module inside the container.  Is that even possible?  


Thank you.

---

### Post by srhadden on 2014-02-10
I solved this a long time ago. Needed to run a ubuntu precise kernel greater than 3.3, where tipc was fixed to work within an lxc container.  But you must run sudo modprobe tipc from the host machine. You can't run it inside the container itself.

---

