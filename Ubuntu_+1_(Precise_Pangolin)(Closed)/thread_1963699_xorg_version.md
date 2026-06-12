---
title: "xorg version"
date: 2012-04-22
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Miykel on 2012-04-22
G'Day; How can I find out which version of xorg server I have installed, I just went through the exercise of adding the xorg ppa to my sources,

as per    [https://launchpad.net/~xorg-edgers/+archive/ppa]("https://launchpad.net/%7Exorg-edgers/+archive/ppa")

 then upgraded and I thought it worked, reading what was running on the terminal, but I would like to check. 

Regards Miykel

---

### Post by papibe on 2012-04-22
Hi Miykel.

You can run this on a terminal:
```
X -version
```
Hope that helps.
Regards.

---

### Post by Miykel on 2012-04-22
Thanks Papide for the replie;

  The upgrade worked...another miracle   LOL.

miykel@miykel-H61M-USB3-B3:~$ X -version

X.Org X Server 1.12.1
Release Date: 2012-04-13
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-31-xen x86_64 Ubuntu
Current Operating System: Linux miykel-H61M-USB3-B3 3.2.0-23-generic #36-Ubuntu SMP Tue Apr 10 20:39:51 UTC 2012 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-23-generic root=UUID=4316d366-9bc4-400e-90c2-3503c3895fbf ro quiet splash vt.handoff=7
Build Date: 21 April 2012  07:00:08PM

Try to install the new kernel now   ):P

Thanks Guys
Regards Miykel

---

### Post by papibe on 2012-04-22
:) Great! Please mark the thread [solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") when you have the chance.

Regards.

---

### Post by Miykel on 2012-04-22
Blast !!!!    The xorg upgrade worked fine but the kernel was a dismal failure, wouldn't even boot to the login screen, back to the drawing board.  LOL
 Will try again before I mark this as solved.
regards Miykel

---

