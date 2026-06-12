---
title: "System Encryption via Truecrypt?"
date: 2011-12-15
forum: Security
---

### Post by davethewave83 on 2011-12-15
I've read that it is not supported with GNU/Linux to encrypt the system drive with Truecrypt and to use LUKS, is this true? 

I prefer to use Truecrypt as I have had problems with LUKS in the past. 

What happens when TrueCrypt encrypts the system? Doesn't it just create an encrypted filesystem and an unencrypted bootloader to decrypt the filesystem? Why wouldn't it be possible to do this with GNU/Linux?

---

### Post by tubbygweilo on 2011-12-15
davethewave83, is it possible for you to outline your problems with LUKS? I do not think [Truecrypt]("http://www.truecrypt.org/docs/sys-encryption-supported-os") can be used to encrypt a GNU/Linux type system but am always willing to hear otherwise.

---

### Post by davethewave83 on 2011-12-15
> **tubbygweilo said:**
> davethewave83, is it possible for you to outline your problems with LUKS? I do not think [Truecrypt]("http://www.truecrypt.org/docs/sys-encryption-supported-os") can be used to encrypt a GNU/Linux type system but am always willing to hear otherwise.

I had a booting issue in the past, if it were a truecrypt drive I could just mount it on another machine. I could not mount the LUKS to recover my data, so it was all lost. 

A similar thing happened when I said "Encrypt my home folder" at install once, I found the problem and recovered the data that time though.

I have a Windows System drive encrypted with Truecrypt

in linux I used Truecrypt to mount the volume

I ran sudo fdisk /dev/mapper/truecrypt1 on the drive in linux, delete the NTFS partition then used sudo mkfs.ext4 /dev/mapper/truecrypt1

it worked, so I have a ext4 partition that has a Truecrypt bootloader to decrypt it at boot. so that much works.

I installed Ubuntu to it but at the end of the install it fails to install grub. I tried to install grub manually with grub-install /dev/mapper/truecrypt1 but it still fails. When I look into the drive 'truecrypt1' I see it has a folder called boot and a folder inside there called grub, there are also other files, so although it says it failed to install, it appears to have installed. ?

when I reboot, truecrypt bootloader still comes up, i enter the password and it says no bootable partition found. 

I think it's mainly because the drive is ext4 and the windows truecrypt probably does not have support to read ext4. It's likely also because grub failed to install.

For now I've installed ubuntu with no encryption. I hate to do that but I need an OS to work with.

---

### Post by sh4d0w808 on 2011-12-16
At least /boot filesystem should be on an unencrypted filesystem because Linux cannot boot from an encypted one. Leave your /boot at the size of 500 MB - it will be enough 'til end of line. All the other filesystems could be encrypted as your initrd will contain necessary modules to read encrypted disks.

You can apply LUKS encryption later but it is a lot of work.

---

### Post by JustinR on 2011-12-17
> **davethewave83 said:**
> I had a booting issue in the past, if it were a truecrypt drive I could just mount it on another machine. I could not mount the LUKS to recover my data, so it was all lost. 

A similar thing happened when I said "Encrypt my home folder" at install once, I found the problem and recovered the data that time though.

I have a Windows System drive encrypted with Truecrypt

in linux I used Truecrypt to mount the volume

I ran sudo fdisk /dev/mapper/truecrypt1 on the drive in linux, delete the NTFS partition then used sudo mkfs.ext4 /dev/mapper/truecrypt1

it worked, so I have a ext4 partition that has a Truecrypt bootloader to decrypt it at boot. so that much works.

I installed Ubuntu to it but at the end of the install it fails to install grub. I tried to install grub manually with grub-install /dev/mapper/truecrypt1 but it still fails. When I look into the drive 'truecrypt1' I see it has a folder called boot and a folder inside there called grub, there are also other files, so although it says it failed to install, it appears to have installed. ?

when I reboot, truecrypt bootloader still comes up, i enter the password and it says no bootable partition found. 

I think it's mainly because the drive is ext4 and the windows truecrypt probably does not have support to read ext4. It's likely also because grub failed to install.

For now I've installed ubuntu with no encryption. I hate to do that but I need an OS to work with.

Hi, Windows software [FreeOTFE]("freeotfe.org") supports [LUKS ]("http://www.freeotfe.org/docs/Explorer/Linux_volumes.htm#level_3_heading_3")encrypted devices. (Scroll down to LUKS).

Also, you can encrypt your [drive without LUKS]("http://and1equals1.blogspot.com/2009/10/encrypting-your-hdd-with-plausible.html") if you prefer.

---

### Post by davethewave83 on 2012-01-22
Thank you all for the replies, I have given up on the attempt for now. It seems to me that Truecrypt has a boot-loader in a sense, I don't understand why it couldn't be made to work with Grub/Linux for whole-disk encryption. 

I guess the two aren't compatible if they are both bootloaders. 

Truecrypt (decryption password)-> Grub -> Linux wouldn't work, as grub would have to be on the boot sector wouldn't it? I've never tried to install grub to a partition, maybe it would work. 

Truecrypt -> Grub dedicated partition (boot sector emulated?) -> Linux

or implement Truecrypts bootloader into Grub somehow so that it's all in one package. 

I don't really know, someone smart will figure it out someday :P

---

