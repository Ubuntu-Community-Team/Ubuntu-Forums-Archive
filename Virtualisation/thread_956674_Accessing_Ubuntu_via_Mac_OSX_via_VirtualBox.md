---
title: "Accessing Ubuntu via Mac OSX via VirtualBox"
date: 2008-10-23
forum: Virtualisation
---

### Post by dauber on 2008-10-23
Okay, I have my MacBook (3.1, OSX 10.5.5) on a dual-boot with Hardy Heron. The dual boot works beautifully.

Now, kind of adapting the advice of this thread...

[http://ubuntuforums.org/showthread.php?p=4850772](http://ubuntuforums.org/showthread.php?p=4850772)

...I configured VirtualBox to boot my Ubuntu partitions from within OSX.

However, when I try, I get the "frozen GRUB" problem -- it just says "GRUB..." at the top of the window and hangs. However, a regular boot into Ubuntu works fine.

What should I be looking out for?

---

### Post by Moonforest on 2011-01-30
Hi,
I am kind of a newbie at this. I have a rEFIt dual boot setup for my OSX to be able to boot Ubuntu, and it works fine. I was wondering if you could explain how to use VirtualBox to access my Ubuntu partition from OSX… all of the tutorials/posts I've read are just confusing. Thanks

---

### Post by ChasHutch on 2011-02-02
Do you want to access the guest (ubuntu) partition or the files ON the partition? If you want to access the files, you need to configure the share folders between the host and the guest. It's pretty easy.  This thread [here]("http://ubuntuforums.org/showthread.php?t=1258729&highlight=virtualbox+shared+folders&page=2") shows an example.

---

