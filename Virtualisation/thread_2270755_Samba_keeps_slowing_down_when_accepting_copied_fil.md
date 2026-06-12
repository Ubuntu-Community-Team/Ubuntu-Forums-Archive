---
title: "Samba keeps slowing down when accepting copied files on a Ubuntu Server VM"
date: 2015-03-25
forum: Virtualisation
---

### Post by Roman_Mironov on 2015-03-25
Hello,

I am running VirtualBox on Ubuntu Server 14.04 64 bit (the host machine). The virtual machine that is run on the host machine also uses Ubuntu Server 14.04 64 bit. The VM has a Samba share. I noticed that Samba slows down occasionally, about every couple hours. This slowdown is evident when I try to copy files to a share: there is a pause before each file is copied, as if Samba is thinking too long whether to accept the file, and then the file is transferred with normal speed.

I used the "top" command to see what is happening. When I start copying several files, the Samba process keeps appearing and disappearing in the list instead of being there all the time while the process is running.

I already tried to replace the switch the host machine is connected to, but to no avail.

Any clues will be much appreciated.

---

### Post by TheFu on 2015-03-26
Good VM performance is about sharing the physical hardware. You cannot just look at the guestVM for performance issues. Look at everything running on the physical hardware - disk I/O, network I/O, CPU, RAM ... everything.  For example, perhaps some hostOS monitoring software builds new graphs every few hrs? That can be CPU intensive.

To help correlate all this data, make certain all systems run ntp and have their clocks synched. Then install some performance monitoring on all the systems that is granular enough to see the issue.

Also - if there is any USB storage involved - know that USB can run into queuing issues when multiple requests happen. I've seen a server stop doing anything for 30+ seconds as it tried to figure out which USB request to handle when more than 3 were in the queue.

---

### Post by TheFu on 2015-03-26
dup. Dno't know why.

---

### Post by Roman_Mironov on 2015-04-29
I moved the VM to another (more powerful) host to see whether this is a hardware or software issue.

I also noticed that the previous host sometimes used its RAM to the fullest, so adding more RAM to the host and assigning more RAM to the VM is another troubleshotting idea.

---

### Post by TheFu on 2015-04-29
> **Roman_Mironov said:**
> I moved the VM to another (more powerful) host to see whether this is a hardware or software issue.

I also noticed that the previous host sometimes used its RAM to the fullest, so adding more RAM to the host and assigning more RAM to the VM is another troubleshotting idea.

Assigning too much RAM or too many cores is just as bad as not having enough.
VirtualBox tuning suggestions: [http://blog.jdpfu.com/slowVbox](http://blog.jdpfu.com/slowVbox)
Getting 90%+ of native performance for non-graphical workloads should be pretty easy.

---

