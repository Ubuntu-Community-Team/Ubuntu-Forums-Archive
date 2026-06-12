---
title: "LVM setup and Partitioning issues during 64 bit server install"
date: 2013-08-21
forum: Server Platforms
---

### Post by jiangshi on 2013-08-21
A couple of days ago, I spent several hours trying to work through setting up a logical volume during the installation of the 12.04 64 bit Server edition. My machine had twin 80gb IDE drives. I finally gave up and removed the twin drives and installed a large single drive, thus side-stepping the problem. However, I am sure that setting up LVM on two drives is possible. After all, that is one to the reasons to use it in the first place. After MANY iterations of this portion of the install, I managed to get a logical drive that spanned the two 80gb drives. But I could not ever get them set up with the standard partitions. And if you will pardon a short critical editorial, I find that the so-called guided setup is anything but guided. The setup interface is not intuitive to anyone who has not gone through the process before. I went through the trouble of trying both CentOS 6.4 and Fedora 19 server installations, and in both cases, the installation software handled the LVM setup very smoothly. I am left with the thought that in Ubuntu's setup, much could be streamlined, or at the very least, some better instructions on the order of processes to do. 

To that end, I would very much appreciate it if someone who has been through the LVM setup for more than one drive, would please explain to me the order of processes. I do not mean every little detail, but more like what menu tasks to do and in the proper order. As mentioned, my server is already setup with a single large drive, but I have another older machine that as soon as I can find some mounting hardware for the second drive, I can use it to practice on.

Thank you!

---

