---
title: "Encrypting Ubuntu 9.10"
date: 2009-11-11
forum: Security
---

### Post by Moji on 2009-11-11
I have recently been trying out and enjoying Ubuntu but I have not been able to successfully encrypt the root Ubuntu partition.

I have tried installing from the alternate cd, for both 9.04 and 9.10, but neither system was able to boot passed the initramfs stage.

I would like to try this one more time as this is the only operating system on my laptop that is not encrypted.

I would like to:

1: Install using the standard install ISO, as I have had luck with that.
2: Copy the root system over to another drive.
3: Encrypt the Ubuntu partition using LUKS.
4: Move the root system back to the encrypted partition.
5: Adjust the appropriate configuration files.

I can't seem to find comprehensive information on which configuration files need to be changed in order for this setup to work.

I have the /etc/fstab and /etc/crypttab from an encrypted system but before I try installing Ubuntu again I was hoping that someone else knew of all the changes that need to be made in order to boot from an encrypted drive. Specifically if there are any boot options that need to be passed in the /boot/grub/menu.lst, if the kernel needs to be recompiled, or if the initramfs needs to be adjusted.

My current system looks like this:

sda
-1> Windows 7 professional - Encrypted with TrueCrypt
-2> Boot - Not encrypted
-3> Swap - Encrypted with LUKS (In Gentoo and Ubuntu)
-4> EXTENDED
-5> Gentoo - Encrypted with LUKS
-6> Ubuntu - Not encrypted
-7> Home - Encrypted with LUKS

I am planning on using the following LUKS options:

```
cryptsetup luksFormat -c aes-xts-essiv:sha256 -s 512 -h sha512 /dev/sda6
```Grub is installed on the MBR and sda2[Boot] is the only drive that won't be encrypted.
I would share both sda2[Boot] and sda7[Home] between Ubuntu and Gentoo.

Thank you for any help you can provide,

-MJ

---

### Post by fargle on 2009-11-19
I see noone has responded.  About the only thing I can tell you is that, as far as I know, you have to use the alternate install CD to set this up, so I would perhaps check to make sure that you have a good burn of that - one easy way is to use your current Ubuntu to download the ISO, use md5sum to verify it, then use the USB Startup Disk creator to put it on a USB key that you can boot off of.  That's how I installed my current system and there's no uncertainty then about CD media and failure to read and such.

Once you do that and boot successfully, if you do manual partitioning you should be able to set things up properly, although I'm not sure I've ever told it to mount an existing encrypted partition - I assume it will work though.  For the Ubuntu root, just select the partition and select "encrypted container" or whatever the wording is and configure that to be the root partition.

Obviously I would strongly recommend you back up everything as this will involve mucking about with the partition table and sharing to OS's is a bit of a twist.

Also, good luck sharing your home directory between Gentoo and Ubuntu - I hope it's the same version of Gnome or else I'm sure there will be some user config file thrashing.  You might want to think about having separate home directories for each with a shared document area instead.

---

### Post by Moji on 2009-11-20
fargle,

         Thank you very much for responding. I thought perhaps my questions were not very composed or I was asking for information that was widely available.

         Yes I did make sure when creating my install DVD's to verify the written data, I used:
    ```
filesize="$(ls -l ${iso} --block-size=2K | gawk '{print $5}')";
dd if="${dvd_device}" bs=2K count="${filesize}" | md5sum | sed "s/-/${iso}/g" | md5sum -c;

```
Although using a USB device would have saved many DVD's as I have now attempted various methods with 9.04[alternate], 9.10[minimal(server)/alternate/standard].        [LEFT]&#65279;> Once you do that and boot successfully, if you do manual partitioning you should be able to set things up properly, although I'm not sure I've ever told it to mount an existing encrypted partition - I assume it will work though. For the Ubuntu root, just select the partition and select "encrypted container" or whatever the wording is and configure that to be the root partition.[/LEFT]
        [LEFT]My plan was to have the installer use only a encrypted root and an unencrypted boot to start with, I would go in afterwards and add the home directory mounting options and just copy over what I needed. I just wanted to get past the first step of having an encrypted root.[/LEFT]
    [LEFT] 
> Also, good luck sharing your home directory between Gentoo and Ubuntu - I hope it's the same version of Gnome or else I'm sure there will be some user config file thrashing. You might want to think about having separate home directories for each with a shared document area instead.[/LEFT]
        [LEFT]This is a very good point, while I do not use gnome I would share many programs between the two and so I will have to make sure their versions match.

[/LEFT]
        [LEFT]Thank you again for your input, I would have replied sooner but I was in the middle of trying out a few different installations to see if I could this working.[/LEFT]
        [LEFT]
-MJ[/LEFT]

---

### Post by Moji on 2009-11-20
I now have the booting into the root partition encrypted, all I need to do now is setup the crypttab so that I can mount my home partition on boot.

         I used the Ubuntu standard installation DVD 9.10.

         I selected the &quot;Try without installing&quot; option.

         I opened a terminal and su'ed to root.
        [LEFT]I then created the luks partition with these commands:[/LEFT]
        [LEFT]```
cryptsetup luksFormat /dev/sda6 -h sha512 -s 512 -c aes-xts-essiv:sha256;
cryptsetup luksOpen /dev/sda6 ubuntu;
mkfs.xfs /dev/mapper/ubuntu;
```[/LEFT]

I proceeded with the installation telling the installer to use /dev/mapper/ubuntu as the root device, and /dev/sda2 as the boot device. Making sure NOT to install the boot loader as grub2 is incompatible with chainloading truecrypt on my windows partition.        [LEFT]I added the modules that I would need and then added two scripts to the initramfs folder in /etc.[/LEFT]
        [LEFT]After that I chrooted into the new system from the terminal and did a:[/LEFT]
        [LEFT]```
update-initramfs -u ALL;
```[/LEFT]
        [LEFT]With a bit of tweaking I was able to get this command to work and so I rebooted, after reboot I received the luks password prompt.[/LEFT]
        [LEFT]
Here are the files that I changed, I do not know if all that I did was correct but it seems to have worked so far.
Any input for corrections is welcome, thank you.

-MJ

[/LEFT]
#/etc/crypttab    [LEFT]> ubuntu          /dev/sda6       none    luks[/LEFT]
        [LEFT]#/etc/fstab[/LEFT]
    [LEFT]> proc                    /proc   proc    defaults        0 0
/dev/mapper/ubuntu      /       xfs     defaults        0 1
/dev/sda2               /boot   xfs     defaults        0 2
/dev/sda3               none    swap    sw              0 0#/etc/initramfs-tools/hooks/root_encryption[/LEFT]
> PREREQ=&quot;&quot;
[LEFT] prereqs()[/LEFT]
     [LEFT]{[/LEFT]
    [LEFT]        echo &quot;$PREREQ&quot;[/LEFT]
    [LEFT]}[/LEFT]
        [LEFT]case $1 in[/LEFT]
    [LEFT]prereqs)[/LEFT]
    [LEFT]        prereqs[/LEFT]
    [LEFT]        exit 0[/LEFT]
    [LEFT]        ;;[/LEFT]
    [LEFT]esac[/LEFT]
        [LEFT]if [ ! -x /sbin/cryptsetup ]; then[/LEFT]
    [LEFT]        exit 0[/LEFT]
    [LEFT]fi[/LEFT]
        [LEFT]. /usr/share/initramfs-tools/hook-functions[/LEFT]
        [LEFT]mkdir ${DESTDIR}/etc/console[/LEFT]
    [LEFT]#cp /etc/console/boottime.kmap.gz ${DESTDIR}/etc/console[/LEFT]
    [LEFT]copy_exec /bin/loadkeys /bin[/LEFT]
    [LEFT]copy_exec /bin/chvt /bin[/LEFT]
    [LEFT]copy_exec /sbin/cryptsetup /sbin[/LEFT]
[LEFT]
 #/etc/initramfs-tools/scripts/local-top/root_encryption[/LEFT]
> PREREQ=&quot;udev&quot;
[LEFT] prereqs()
{[/LEFT]
    [LEFT]        echo &quot;$PREREQ&quot;[/LEFT]
    [LEFT]}[/LEFT]
        [LEFT]case $1 in[/LEFT]
    [LEFT]# get pre-requisites[/LEFT]
    [LEFT]prereqs)[/LEFT]
    [LEFT]        prereqs[/LEFT]
    [LEFT]        exit 0[/LEFT]
    [LEFT]        ;;[/LEFT]
    [LEFT]esac[/LEFT]
        [LEFT]/bin/loadkeys /etc/console/boottime.kmap.gz[/LEFT]
    [LEFT]modprobe -qb dm_crypt[/LEFT]
    [LEFT]modprobe -qb loopcbc[/LEFT]
    [LEFT]modprobe -qb blkcipher[/LEFT]
    [LEFT]modprobe -qb gf128mul[/LEFT]
    [LEFT]modprobe -qb xts[/LEFT]
    [LEFT]modprobe -qb aes_generic[/LEFT]
    [LEFT]modprobe -qb aes_i586[/LEFT]
    [LEFT]modprobe -qb sha256_generic[/LEFT]
    [LEFT]if grep -q splash /proc/cmdline; then[/LEFT]
    [LEFT]    /bin/chvt 1[/LEFT]
    [LEFT]fi[/LEFT]
    [LEFT]/sbin/cryptsetup luksOpen /dev/sda6 ubuntu[/LEFT]
    [LEFT]if grep -q splash /proc/cmdline; then[/LEFT]
    [LEFT]       /sbin/usplash -c &[/LEFT]
    [LEFT]       sleep 1[/LEFT]
    [LEFT]fi[/LEFT]
[LEFT]
#/etc/initramfs-tools/modules[/LEFT]
> sd_mod
[LEFT] ehci_hcd[/LEFT]
     [LEFT]uhci_hcd[/LEFT]
    [LEFT]ohci_hcd[/LEFT]
    [LEFT]usb_storage[/LEFT]
    [LEFT]nls_cp437[/LEFT]
    [LEFT]nls_iso8859_1[/LEFT]
    [LEFT]dm-cryptaes[/LEFT]
    [LEFT]sha256[/LEFT]
    [LEFT]loopcbc[/LEFT]
    [LEFT]blkcipher[/LEFT]
    [LEFT]gf128mul[/LEFT]
    [LEFT]xts[/LEFT]
    [LEFT]aes_generic[/LEFT]
    [LEFT]aes_i586[/LEFT]
    [LEFT]dm_crypt[/LEFT]
    [LEFT]sha256_generic[/LEFT]


---

### Post by fargle on 2009-11-20
Overall looks good and I'm glad it works - though I'd definitely watch updates if you messed with the initramfs stuff to make sure it doesn't get overwritten, generate a new initramfs, and break your boot.

Did I miss something, though?  It doesn't look like based on your fstab that your swap area is encrypted, and to make sure you're secure it's very important that it is.  I've done tests and things like passwords have shown up cleartext in the swap, even if it's not used much.

I encrypt my swap with a random key since it doesn't need to survive a reboot.  You can do that with this in your crypttab:

```
cryptoswap /dev/sda3 /dev/urandom cipher=aes-cbc-essiv:sha256,size=256,hash=sha256,swap
```

and then changing your fstab entry for swap to specify /dev/mapper/cryptoswap.  You can of course change algorithms and hashes as you like.  Using /dev/urandom may not be as random as would be optimal, but if you use /dev/random then I think it blocks until it has things like mouse moves to generate random data, which is not good for boot times!

I'm sure you know, but doing this means you can't hibernate successfully and you should shut that totally off in the power settings.  You can still suspend to ram, though, my system does that fine.  That's more for info for people searching than you, I think you know that.

---

### Post by Moji on 2009-11-21
Yes, sorry, I left out the settings I changed once I got the system working correctly.

I copied most of the user files from {ubuntu}/home to {gentoo}/home. Deleted the files in {ubuntu}/home/*.
Then adjusted the crypttab and the fstab one more time.

I decided to go with a static encryption key for the swap partition because I have heard that it is possible to hibernate as long as the key is not random, as random keys essentially erase the mapped device after leaving, which is the point of a random key in the first place.
This is just something that I have heard, it looked just briefly at it and I think that I would have to adjust the initramfs again so that the mount of root happens before the attempt to read the swap.

Thank you again for your help.

-MJ

#/etc/crypttab
> ubuntu          /dev/sda6       none                    luks
home            /dev/sda7       /etc/crypt/home.key    luks
swap            /dev/sda3       /etc/crypt/swap.key     cipher=aes-xts-essiv:sha256,size=512,hash=sha512#/etc/fstab
> proc                    /proc   proc    defaults        0 0
/dev/mapper/ubuntu      /       xfs     defaults        0 1
/dev/mapper/home        /home   xfs     defaults        0 1
/dev/sda2               /boot   xfs     defaults        0 2
/dev/mapper/swap        none    swap    sw              0 0

---

### Post by Moji on 2009-12-23
I have since done this two more times and I've found that there is an even more straight forward way to accomplish this. In 17 simple steps.

You need:

A USB device large enough to hold your root/home partition.
A Ubuntu standard install DVD.

1: Using the Ubuntu install CD boot into the system without installing Ubuntu.
2: Open a terminal and sudo -s to root.
3: Make the directories /mnt/ubuntu and /mnt/backup.
4: Mount your root partition to the /mnt/ubuntu folder.
5: Mount your home paritition to the /mnt/ubuntu/home folder.
6: Mount your USB device to /mnt/backup.
*You need to have a filesystem
*If you want you can encrypt the backup device so that your data doesn't make into the clear, you could also just shred the device after useage.
7: Copy all files from /mnt/ubuntu to /mnt/backup.
8: Unmount your home/root directories.
9: Encrypt your home and root directories.
10: Open and then remount your home and root partions to /mnt/ubuntu and /mnt/ubuntu/home.
11: Copy back all files from /mnt/backup to /mnt/ubuntu.
12: Edit /etc/initramfs-tools/modules [add any encryption modules you need], /etc/crypttab [add all of the newly encrypted partitions and swap] /etc/fstab [add the mapper root, home and swap].
13: Chroot into the encrypted system.
14: Mount your boot parition.
15: Run update-initramfs -u ALL.
16: Edit your /boot/grub/menu.lst.
17: Reboot.

Most of the commands and configurations files are already listed in this thread, with the one big difference is that instead of adding modules to the installed scripts I add it to the modules file in etc.

I have done this twice on unencrypted systems changing them to encrypted versions and it does work well.

If anyone does need help don't hesitate to ask.

-MJ

---

