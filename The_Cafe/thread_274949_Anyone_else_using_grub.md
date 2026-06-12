---
title: "Anyone else using grub?"
date: 2006-10-10
forum: The Cafe
---

### Post by robcarr2 on 2006-10-10
Does anyone else use grub for booting into either windows or ubuntu?

For some reason today i got error 17 with grub

Anyways I booted off the live cd, and took a look at the list and for some reason my ubuntu partition (which is at hd0,5 / sda6 ) was changed to hd0,6 / sda7 ) in the list :-?

This ever happened to anyone else?

---

### Post by meng on 2006-10-10
Not me boss, grub's been very well behaved for me.

---

### Post by Mihkal on 2006-10-10
So, did you fix it?

grub starts counting partitions at 0, not 1

something similar happened to me while trying to set up gentoo](*,)

---

### Post by Kateikyoushi on 2006-10-10
I think he means it changed all by itself and he had to correct it.
If so I have no idea why would it change.

---

### Post by robcarr2 on 2006-10-11
Yer it changed all by itself :-? I am clueless to why.

---

### Post by Herman on 2006-10-14
> Yer it changed all by itself :???: I am clueless to why.When we recieve a software update over the internet, is sometimes includes a new kernel. If it does, instead of making users need to manually edit each of our Grub menus, ( /boot/grub/menu.lst ), in Ubuntu it is set up to run 'sudo update-grub' automatically, which re-writes our menu.lst files with the new kernel particulars, so next time we boot up, we'll be booting the new kernel instead of the old one.
This is so well done, that the only thing most people notice is their list in thier Grub menus getting longer. It bothers most people because it looks messy. However, it is important to be running the latest kernel, they don't go to all the trouble of giving us new kernels for nothing.
Anyway, there is a special section of the /boot/grub/menu.lst file called the 'Automagic Kernels List', and there are settings there to control the user-configurable parts of this process.
Normally, this part of our /boot/grub/menu.lst file needs no attention at all. It is set correctly during our installation.
If, however, we have the partition number of our Ubuntu / (root of the filesystem) changed somehow, the automagic kernels list might still have the old partition numbers in it. For example, the partition was copied and pasted with GParted, or another disk partitioner, and grub was re-installed and /etc/fstab was updated. Most people forget to update their automagic kernels list entries. The same thing might happen if the partition was backed up with Partimage, and later restored with a different partition number.
So, you might want to check what is in your /boot/grub/menu.lst after  'kopt' and 'groot', this is kind of hard to explain without an illustration, so, to see what I mean, [click here]("http://users.bigpond.net.au/hermanzone/p15.htm#DEBIAN_AUTOMAGIC_KERNELS_LIST").
(And you can skip the first paragraph if you want, but read on after that).
Probably if you don't edit your Automagic Kernels List (if I'm right and that's the problem), then this will keep on happening every time you get a new kernel. Of course, use your own judgement as well, I'm not in front of your computer, and I can't tell for sure what's really going on from here. But I hope I'm being helpful, that's all.

Regards, Herman :D

---

### Post by robcarr2 on 2006-10-14
That would explain why it changed, thanks for the post :) I dont mind altering the list manually every now and again when the kernel is updated. Just aslong as I know why I am doing it.

Cheers :)

---

