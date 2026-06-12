---
title: "Boot Existing XP Partition in Sun VirtualBox - Ubuntu 9.10 - Quick Questions"
date: 2010-01-06
forum: Virtualisation
---

### Post by manco on 2010-01-06
Hey everyone.

I have Sun VirtualBox (**not** OSE) installed and working fine in Ubuntu 9.10 :D

I'm running a dual-boot setup with Windows XP, and I'd like to access that partition w/o having to boot into it.

My questions:

1) If I am able to boot my XP partition in VirtualBox, will I still be able to boot into it through GRUB?

2) Are the "Guest Additions" working with the latest version?  I'd really like to have that feature working :)

3) If "1" is true, can anyone point me towards a good tutorial?

Thanks

---

### Post by fouadatmeh on 2010-01-07
Hello,
in answering your question:
1) probably yes by creating two hardware profiles for windows xp..
2) they are working great for me :)
3) I haven't tried this myself but google came up with this:
[http://mesbalivernes.blogspot.com/2008/01/virtual-box-booting-from-existing.html](http://mesbalivernes.blogspot.com/2008/01/virtual-box-booting-from-existing.html)

---

### Post by oldfred on 2010-01-07
I was planning on doing this but have not got round2it, still dual booting.

Howto: Windows XP in both VM and native
[http://forums.virtualbox.org/viewtopic.php?t=9697](http://forums.virtualbox.org/viewtopic.php?t=9697)

---

### Post by Objekt on 2010-01-07
What?  You can mount an existing, real partition as a virtual machine in Virtualbox?  Neat.  I'll have to give that a try.  I thought you could only mount a *.vdi virtual machine image.

I would think this would not work, because the virtual machine will not have all the same virtualized hardware as my physical machine.  I would expect just a bluescreen if I tried to boot my Windows XP volume on a virtual machine which will not, of course, have the same (virtual) hardware.

---

