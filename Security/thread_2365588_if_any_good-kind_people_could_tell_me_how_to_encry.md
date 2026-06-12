---
title: "if any good-kind people could tell me how to encrypt system..."
date: 2017-07-08
forum: Security
---

### Post by unityforever on 2017-07-08
when i look at these manuals and instructions i get headache...

i have a ubuntu, installed on GPT EFI computer. i want to encrypt ubuntu partition then every times i/bad-guys turn on my computer, it requires phrase to mount system.

i wish there have a good person who can tell me the steps to achieve that.

and i will thank you with deeply grateful, pray for you, hope you good-luck forever.

---

### Post by Bucky Ball on 2017-07-08
You are not being asked for a password when you turn on your computer? Do you mean you want to be asked for a password when you open the lid of your laptop?

You don't need to encrypt the drive if what you want is a password request when you switch on or open the lid. You should be asked for one when you switch on and if you're not, that is unsafe and a puzzle why (this is default). Did you change that? If you are not being asked for a password when you open the laptop lid, the system can be setup so that happens.

---

### Post by unityforever on 2017-07-08
> **Bucky Ball said:**
> You are not being asked for a password when you turn on your computer? Do you mean you want to be asked for a password when you open the lid of your laptop?

You don't need to encrypt the drive if what you want is a password request when you switch on or open the lid. You should be asked for one when you switch on and if you're not, that is unsafe and a puzzle why (this is default). Did you change that? If you are not being asked for a password when you open the laptop lid, the system can be setup so that happens.

oh, i mean i need that form to decrypt system, just type password, no usb sticks.

surely i have login password and i wouldn't ask this easy question. If computer is stolen, offline attacked, the valuable and private data will be seen.

---

### Post by HermanAB on 2017-07-08
When you install Ubuntu, select full disk encryption.  That's all there is to it.

---

### Post by deadflowr on 2017-07-08
Easy way: Do what HermanAB suggests, a full reinstall and select the Full disk encryption option during setup.
The not so easy way: Follow some very arcane instructions which may be old and outdated, and hope they still work.


Seconadry to doing a full disk encryption setup is you can do a simple home migration, which migrates your home folder into an encrypted home.
Here's a basic rundown of how to do that:
[http://blog.dustinkirkland.com/2011/02/long-overdue-introduction-ecryptfs.html]("http://blog.dustinkirkland.com/2011/02/long-overdue-introduction-ecryptfs.html")

But for whichever method of migrating you system to an encrypted system you choose, best to run a backup first.
(run a backup anyway. Backups are good)

---

### Post by HermanAB on 2017-07-09
BTW, if you want to encrypt a removable data disk / USB stick / SD card - you can use the utility cryptsetup directly.  Just read the man page.  With this, it is best to read the man page yourself, rather than reading misleading outdated information in random web sites.

---

### Post by unityforever on 2017-07-20
thanks
however I had already installed the system, and i have a lots of valuable data meanwhile i have a lots of jobs to do for getting the salary and feeding myself, i(or my boss) don't have time to wait for resetting the system up. Therefore, i can't reinstall the system by now, im seeking a way to encrypt it in current situation.
Full disk encryption needs to clear all the data on disk and this is not acceptable, can i just encrypt specific partition during installing?
is there any parameters to skip backup procedure before encrypt home folder? 

jesus, i really regret to use linux now... in windows i could just click a button and application would deal anything else then.

---

### Post by HermanAB on 2017-07-22
Yes, you can encrypt parts of the system, but it isn't as effective, since some data will end up in the swap partition, some on the /tmp directories, some in the disk journals etc.

Yes, you can use Windows, and then the whole thing will look like it works, but it won't really - the constant stream of crapware, viruses and ransomware are sufficient proof of that.  IMHO, an unencrypted Linux machine is more safe and secure than an encrypted Windows one, so maybe you should just relax about it all for now.

---

### Post by thehighhat2 on 2017-08-05
encrypting data at rest (full disk encryption) is a good idea.


do you have another drive availble?   if so then
1)  encrypt the new drive
2)  move everything as in to the new drive
3)  update fstab to have the correct device identifiers
4)  install grub to mbr on new drive
5)  make new drive the primary, reboot.

how full is your disk?  if less than say 40% full, 
*be super careful with this approach*
1)  shrink the partitition
2)  create a new partition in the free'd space
3)  encrypt the new partition
4)  using livecd, copy all of the data from unencrypted to encrypted partition
5)  unmount the old partition and delete it
6) replace old partition with small boot partition (512MB) and the rest
7) encrypt the rest
8) format the boot partition and copy the /boot contents from the encrypted paritition
9) create lvm on mounted new encrypted partition
10)  create swap volume and root volume 
11)  format both 
12)  copy everything into this new root partition
13)  edit /etc/fstab to use the lvm mounts for root and swap, and the correct device id for boot;  also use tmpfs for /tmp
14)  do the grub steps to be able to boot
15)  reboot.  now delete that temporary encrypted partition
16)  resize (grow) the large partition
17)  resize the lvm group, resize the lvm volume, resize the root filesystem
18)  done


now everything is fully encrypted.  this definitely beats Windows setup

---

