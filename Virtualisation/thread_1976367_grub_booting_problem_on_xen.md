---
title: "grub booting problem on xen"
date: 2012-05-08
forum: Virtualisation
---

### Post by essential1 on 2012-05-08
hi all, 

i asked this question elsewhere but thought i might have more chance of a response here. i have tried to install xen on ubuntu 10.04 and have run into a problem on what looks like the final hurdle. 

i followed the guide [here]("https://help.ubuntu.com/community/Xen")  on the ubuntu site. everything until attempting to start xen worked  fine, steps 1 (compiling and installing xen) and step 2 (downloading and  compiling a dom0) passed without any problem. i can confirm that the  dom0 kernel works well by itself as it starts up and runs without any  problems.

after editing my grub entry to include the downloaded dom0 kernel, and including xen (included below), i get the message:

error: couldn't open file
error: you need to load the multiboot kernel first

my grub entry is the following, the only thing i can think is that some  of the entries might need to have options included, but i have tried  with some of the ones mentioned such as including a dummy=dummy on the  end of the module entries. however i cannot understand what the problem  might be. 

menuentry "Xen 4.0.1 / Ubuntu" {
insmod ext2
set root='(hd0,1)'
multiboot [(hd0,1)]/boot/xen.gz dummy=dummy
module [(hd0,1)]/boot/vmlinuz-3.1.0-rc9+
module [(hd0,1)]/boot/initrd.img-3.1.0-rc9+
}

i know about the package install, but i am installing from source because i would like to play around with xen so i would really appreciate any help on this.

---

