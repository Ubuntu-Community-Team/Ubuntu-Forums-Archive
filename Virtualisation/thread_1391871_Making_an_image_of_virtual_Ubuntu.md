---
title: "Making an image of virtual Ubuntu"
date: 2010-01-27
forum: Virtualisation
---

### Post by MayaChl on 2010-01-27
Hi guys!

I'm working with:
- On Vista with.
- ubuntu 9.10 on a...
- VMPlayer 3.0.0 build-203739

Now I'm preparing this Ubuntu to make the final switch from Windows to Linux. Currently I'm preparing it with the (minimal)  necessary software to able to get the work done while I'm learning linux in the process. Progs like Maya, Photoshop and Indesign are for example progs where no (not yet) linux based alternatives cut it for me (escept for maya Hybrid ofc.) 

Long story short: When its done I would like to image the whole OS and the prepared config including the progs in Wine etc.. - burn it - boot and install it

Question is which is the best way to do just that? Can I make an image within the virtual computer itself with some sort of ghosting tool or can I simply make an image from the whole virtual computer found on my (Windows) drive?

tnx in advance

---

### Post by vandorjw on 2010-01-27
I do not know how to make an image from what you have, but you can try this if no one else knows how to do it.

----------------------------------------------------------------------------------------------------------------


A full install of ubuntu is much larger than what can fit on a DVD.

If you have an external hard drive, or just a second hard drive for that matter, what you can try is mount it using Ubuntu, and copy everything to this drive. You might want to partition it beforehand to ext3 or ext4.

```

sudo cp -r /

```

Now, I doubt you'll be able to boot your system using this drive, because grub, mtab and your fstab files will be messed up.

To fix fstab isn't to difficult.
Take a live cd of almost any linux distro and boot into it.
open the terminal, and type

```

sudo chroot /media/****** /bin/bash
env-update

```

** please notice the ****** I don't know the name of the hard-drive or what it is mounted at, I do know that in the typical ubuntu install, it will be mounted to /media and will likely be called something to the effect of "disk1"

These last two commands will put you in your copied over ubuntu installation.

Now run this command

```

sudo blkid

```
This command spits back the UUID of your hard drives. (Think of it as a serial number)

**Example output**
> 
/dev/sda1: UUID="746cb561-c67f-41a3-bcab-8f065daacf72" TYPE="ext4" 
/dev/sda2: UUID="m2xM8I-GYtC-tRMo-uRVD-K9pF-lW5H-3OHiOy" TYPE="LVM2_member" 
....


I have more than 2 drives, and in case you also do, look for the type.
Hopefully you only have one drive formated to ext4 or ext3, and this is the drive who's UUID you want. copy this down. (This should be the drive you copied your ubuntu install to)

Now open fstab
```

sudo gedit /etc/fstab

```
** please note that if you didn't chroot into the your copied linux install, the fstab file you want to edit is actuall /media/????/etc/fstab **

you can delete everything you see here and instead put this down.

> 
UUID=GIANT-LIST-OF-NUMBERS /                   auto    defaults        1 1


replace "GIANT-LIST-OF-NUMBERS" with the UUID you obtained using "blkid"
save and close this file.

Now to restore GRUB (your boot loader) do the following
```

grub


root (hd0,0)    (Specify where your /boot partition resides)
setup (hd0)     (Install GRUB in the MBR)
quit            (Exit the GRUB shell)

```

Once again, I do not know where your /boot partition is going to be, so do not copy and paste (hd0,0) as it will likely be wrong.

----------------------------------------------------------------------------------------------------------------

I think that this is all that is needed to be changed in order for you to boot into your system.

However, I think it you're going to hit a lot of permission problems and ownership problems once this is over. (Which can all very easily be fixed using the "chown" and "chmod" commands, but..

I recommend you take a live disk and just re-install everything.
if you don't want to reconfigure everything, copy all your configuration files, save them somewhere and then reuse them as needed.

Hope this helps.

CC7gir

---

### Post by MayaChl on 2010-01-28
Tnx cc7gir,

That is one big reply, althought I was looking for an easier way to get a boot from the Ubuntu I'm configuring, not saying I will try this (learning Ubuntu is 1 of my goals).

Maybe I am better off getting a clean LiveCD and reinstall everything, after all it isn't that must work with knowing the drill and all...

Anyway tnx man/'women :P

---

