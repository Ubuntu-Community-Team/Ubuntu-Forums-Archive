---
title: "Format virtual Windows XP drive in VirtualBox question"
date: 2008-09-13
forum: Virtualisation
---

### Post by k3lt01 on 2008-09-13
I have been looking at virtualization in my Hardy setup as a means of learning more about he intricacies of computers and I have come across something that has got me thinking.

While installing XP in VirtualBox the install went through all the usual Windows setup processes which I expected it to do. What has got me thinking is it asked me how I wanted the virtual drive formatted. My setup is a 250GB Western Digital HDD in an older Acer laptop (as explained in my signature) and it is all formatted as Ext3. If I keep going with the VirtualBox Windows XP install should I just select NTFS and continue on? If I do will it really reformat the Virtual Windows XP partition as NTFS or does it just think it has?

Thanks.
Michael.

---

### Post by Shazaam on 2008-09-14
Virtualbox (and VMware) virtual hard drives can be formatted any way you like without affecting the host system. All tools will work including a Ubuntu/linux livecd, a Windows cd, a Gparted livecd, etc. Virtual hard drives are really just a file instead of an actual physical drive.
And, you can set up a virtual dual/multi-boot system with multiple virtual hard drives in one virtual machine. :)

---

### Post by k3lt01 on 2008-09-15
Thanks for that, I have worked out I will need more RAM so I will upgrade that and then reinstall virtual Windows

---

