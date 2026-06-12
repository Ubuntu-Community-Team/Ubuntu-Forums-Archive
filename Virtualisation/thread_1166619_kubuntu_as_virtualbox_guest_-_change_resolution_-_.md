---
title: "kubuntu as virtualbox guest - change resolution - install guest additions"
date: 2009-05-21
forum: Virtualisation
---

### Post by charonred on 2009-05-21
I've just installed Kubuntu 'Jaunty' 9.04 in VirtualBox 2.2.2 on my Ubuntu 'Hardy' 8.04 system, but have 2 problems I need help with;

1 - how do I increase the display resolution - only options in the Kunutu install are 800 x 600 and 640 x 480 (I can run XP and Win7 @ 1024 x 768 in VirtualBox)

2 - How do I install guest additions, it asks me to run it as root, but I don't know how to do that in Kubuntu.

---

### Post by charonred on 2009-05-21
DOH ... solved it via link in another thread
[http://www.robotification.com/compon...on-ubuntu.html]("http://www.robotification.com/component/content/article/8-programming/7-how-to-install-virtual-box-additions-on-ubuntu.html")

basically inserted Kubuntu CD in cdrom, then opened Konsole Terminal and entered the following
> sudo sh /media/cdrom/VBoxLinuxAdditions-x86.run
then hit enter.

all fixed :D

---

