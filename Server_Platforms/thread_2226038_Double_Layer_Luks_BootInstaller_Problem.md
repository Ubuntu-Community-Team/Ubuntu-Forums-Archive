---
title: "Double Layer Luks Boot/Installer Problem"
date: 2014-05-24
forum: Server Platforms
---

### Post by mayday2 on 2014-05-24
Hi Guys,

I am trying to migrate a few of my systems from Centos to Ubuntu and I've ran into an issue i'm unable to fix.
I am working on this actively so i might come up with a solution but i thought i would ask the community.

My setup is like this

/dev/sda1 => /boot
/dev/sda2  => aes-xts opened to /dev/mapper/luks-level1
/dev/mapper/luks-level1 =>  twofish-xts opened to /dev/mapper/luks-level2
/dev/mapper/luls-level2 LVM with root and swap.

Basically it's a two layer encryption.

Normally on Centos during the install it detects both levels of encryption and creates all the necessary  files (cryptab dracut)needed to boot. I never had issues with this.
However after the install reboot the Ubuntu system will not start. After further inspection it seems the installer does not create /etc/crypttab or /etc/initramfs-tools/conf.d/crtyptroot.

During the Install process i am able to detect and unlock each encryption level without any issue but the files necessary to boot are not created.
I'm trying to set them manually right now but still unable to get past waiting for encryted ... anyway i'm attaching a few screenshots.


[ATTACH=CONFIG]253423[/ATTACH][ATTACH=CONFIG]253424[/ATTACH][ATTACH=CONFIG]253425[/ATTACH][ATTACH=CONFIG]253426[/ATTACH][ATTACH=CONFIG]253427[/ATTACH]

---

### Post by mayday2 on 2014-05-25
Hi Everyone,


I was able to get this thing going here is what i did.
After Successfully installed Ubuntu i started up in rescue mode i unlocked my encryption chain.


cryptsetup luksOpen /dev/sda2 luks1
cryptsetup luksOpen /dev/mapper/luks1 luks2
pvscan
vgscan
lvscan
mount /dev/vg/root /mnt
mount /dev/sda1 /mnt/boot
mount --bind /dev /mnt/dev
chroot /mnt /bin/bash
mount -t proc proc /proc
mount -t sysfs sys /sys
mount -t devpts devpts /dev/pts


From this point on just need to create the crypttab and cryptroot files properly
The UUID used has to be the same one USED by luks there are two levels of encryption so we will have two UUID sda2 and level1.


cryptsetup luksUUID /dev/sda2 => e94cff36-2fa8-434a-884d-af57e771c96c
cryptsetup luksUUID /dev/mapper/luks1 => 7233088f-2a72-40b2-8468-65508962b871


Edit file /etc/crypttab


# <target name> <source device>         <key file>      <options>
lukslevel1 UUID=e94cff36-2fa8-434a-884d-af57e771c96c none luks,discard
lukslevel2 UUID=7233088f-2a72-40b2-8468-65508962b871 none luks,discard


create /etc/initramfs-tools/conf.d/cryptroot and edit it adding the info.


target=lukslevel1,source=UUID=e94cff36-2fa8-434a-884d-af57e771c96c,key=none,discard
target=lukslevel2,source=UUID=7233088f-2a72-40b2-8468-65508962b871,key=none,rootdev,lvm=vg-root,discard
target=lukslevel2,source=UUID=7233088f-2a72-40b2-8468-65508962b871,key=none,lvm=vg-swap,discard


update-initramfs -k all -c




That's it. reboot and it will ask for level1 pass then level2 then boot the system from the lvm.


After this just slap dropbear with remote unlock and it's good to go.


I hope this helps someone else.

---

