---
title: "Ubumtu host / XP guest partioning and swap for development"
date: 2009-06-15
forum: Virtualisation
---

### Post by golfcaddy on 2009-06-15
Ive recently been playing around with Ubuntu again and loving it so im going to install it as the main OS on my laptop.

I cant switch completly as I need Visual Studio for work for days im in the office. Ok, I could just dual boot as I am now but I like to tinker with stuff so im going to give this a go :D

So questions, and any help on this would be much apprecaited!

1)Sharing files between guest and host - are VMWare tools safe to allow file copying between ext4 and NTFS? Or would I be better off using either VMWare or VirtualBox and creating say a 10GB FAT32 partion as a network folder to share between the two?

2)Partioning, ive got 250GB space and i can see the XP (or possibly server 08 ) image taking a safe 30GB. Id like to keep my images should i choose to do a fresh install of Ubunutu or indeed another distro. So, im thinking simply 50GB for / and the rest for /home so that I can keep the contents of home (including my virtual images) should i reinstall for whatever reason.

3)Swap space; using VMWARE and Visual Studio is going to munch away at RAM. Ive got 2GB on the laptop with a dual core CPU, would 4GB swap be preferable? Or possibly more? 

Thanks

---

### Post by jimv on 2009-06-15
I use Visual Studio in VirtualBox and I have two gigs of RAM.  I allocated 800 MB to the VM and it runs just fine.  No swapping occurs...that said, if your XP VM did need to swap, XP would do it inside it's virtual HD, not in your swap partition.

---

