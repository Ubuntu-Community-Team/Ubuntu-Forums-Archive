---
title: "problem to add physical hd to vmware"
date: 2008-04-26
forum: Virtualisation
---

### Post by dimiboy on 2008-04-26
hi i am new to linux.
i installed the new 8.04 and its just perfect!
now i installed vmware workstation and i am trying to add to it my C: partition (there is a windows xp on it) so as far as i know it is /dev/sda1
but when i try it or different things vmware says: "the specified device is not a valid physical disk device" or "insufficient permission to access file"
can someone please help me?
i want to try after it the "coherence" (seamless) thing...
if it matters i have a laptop Toshiba satellite A205-S4587

---

### Post by fjgaude on 2008-04-26
You have to setup Shares in Ubuntu and made that drive a share. Then you have to have Samba installed to access the drive, using your smb password to do it.

Remember you are going to an NTFS filesystem from an ext3 in Ubuntu. It's like a miracle that this can be done, but it can.

You will have to educate yourself on setting all this up. There is much in the Forums here to assist.

---

### Post by dimiboy on 2008-04-26
thanks!
i will search for those.
but it will be easier if somene gives me links for those two.
and yes... ubuntu is a miracle! i love it!

---

### Post by fjgaude on 2008-04-26
Here's one to get you started, it's a Sticky up top of this Forum:

[http://ubuntuforums.org/showthread.php?t=582729](http://ubuntuforums.org/showthread.php?t=582729)

It's going to take lots of learning, one way or the other.

Let us know how you are doing.

---

### Post by Georgi Sotirov on 2008-10-06
Excuse me, but it shouldn't be that complex. I have created virtual machines in the past (with vmware Workstation 4.x) and I think the problem in 6.5 will not be solved by using samba and shares. It's something else...

---

