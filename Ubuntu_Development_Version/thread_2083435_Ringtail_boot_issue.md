---
title: "Ringtail boot issue"
date: 2012-11-12
forum: Ubuntu Development Version
---

### Post by heavyonion on 2012-11-12
Ok so I ended up simplifying and wiped my hard drive and I just have 4 partitions now. I installed Ringtail fresh and when the grub screen comes up there is no Ubuntu option? There is a Mem test instead. Opensuse is there along with Windows 8 but no way to boot Ubuntu.
Any Ideas????

---

### Post by oldfred on 2012-11-12
Post the link to the BootInfo report that this creates.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.Install in Ubuntu liveCD or USB or:
Full RepairCD with Boot-Repair (for newer computers) 
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by ventrical on 2012-11-12
I use Grub Rescue or SuperGrub 2.

---

### Post by heavyonion on 2012-11-12
I have used boot repair< no help, probably just a tweak in the ISO I pulled down. No biggy, I have already installed 12.10 and maybe I will just change the repos. Thanks.

---

### Post by cariboo on 2012-11-12
It almost looks like grub didn't get installed to the right place. You can chroot the / partition on your Raring install, and re-install grub correctly. Use the following commands to chroot your root partition:

```
sudo mount /dev/sdxX /mnt
sudo mount -o bind /sys /mnt/sys
sudo mount -o bind /dev /mnt/dev
sudo mount -o bind /proc /mnt/proc
sudo cp /etc/resolv.conf /mnt/etc/resolv.conf
sudo chroot /mnt
```

/dev/sdxX = / on your Raring install

I've added a command to copy /etc/resolv.conf to your chroot, in case you need internet access to download the grub packages.

Once you've chrooted / issue the following commands:

```
grub-install /dev/sdx
```

and then:

```
update-grub
```

After running update-grub, you should see a listing of all the different versions you have installed.

**Note:** You don't need sudo for the last two commands, as you are running with elevated privileges.

---

