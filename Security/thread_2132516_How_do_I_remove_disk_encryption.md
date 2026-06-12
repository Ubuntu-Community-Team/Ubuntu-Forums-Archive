---
title: "How do I remove disk encryption?"
date: 2013-04-05
forum: Security
---

### Post by NomadAU on 2013-04-05
Hi,

I have Ubuntu 12.04 LTS running off a disk that is encrypted - can't recall the exact steps, but this was an option I selected when I installed Ubuntu.
So, on boot, I am presented with a screen requesting my passphrase to unlock the disk, before bootup continues.

I no longer have a need for full disk encryption, and would like to 'remove' it.  I am guessing that the high-level activities I would need to perform would be something like the following:

- boot up and perform a full backup of the current (unencrypted) image
- perform some reorganisation of the disk partition(s) to remove the encryption
- restore the backed up image onto an unencrypted partition

What I'm looking for are some more detailed instructions that would cover
- how to backup the image so that EVERYTHING is copied - I seem to remember doing backups in the past, where not everything was copied and don't want a repeat of this.
  What I mean by this, is that when a full backup is initiated/executed from within the image, i.e. while the OS is running, there are often files that cannot be copied out.  Normally, a full backup is taken while the OS is stopped, using an external tool.  However, I can't see how this can be done if I need the OS up and running for the disk decryption to function.
- how to remove the encrypted partition and create the new one
- how to restore the backed up image

Any pointers much appreciated.

---

### Post by KaosuX on 2013-04-06
> **NomadAU said:**
> Hi,

I have Ubuntu 12.04 LTS running off a disk that is encrypted - can't recall the exact steps, but this was an option I selected when I installed Ubuntu.
So, on boot, I am presented with a screen requesting my passphrase to unlock the disk, before bootup continues.

I no longer have a need for full disk encryption, and would like to 'remove' it.  I am guessing that the high-level activities I would need to perform would be something like the following:

- boot up and perform a full backup of the current (unencrypted) image
- perform some reorganisation of the disk partition(s) to remove the encryption
- restore the backed up image onto an unencrypted partition

What I'm looking for are some more detailed instructions that would cover
- how to backup the image so that EVERYTHING is copied - I seem to remember doing backups in the past, where not everything was copied and don't want a repeat of this.
  What I mean by this, is that when a full backup is initiated/executed from within the image, i.e. while the OS is running, there are often files that cannot be copied out.  Normally, a full backup is taken while the OS is stopped, using an external tool.  However, I can't see how this can be done if I need the OS up and running for the disk decryption to function.
- how to remove the encrypted partition and create the new one
- how to restore the backed up image

Any pointers much appreciated.

I don't know if you're still monitoring this thread, but here are some helpful suggestions to help you get this project going.....

1) Create a LiveCD using an installation image from the official Ubuntu site. The next steps assume you have successfully done this and are at the desktop of the live environment
2) Open a terminal and issue the command: ```
 sudo [COLOR=#333333][FONT=UbuntuMono]apt-get install cryptsetup lvm2[/FONT][/COLOR]
```
3) Now issue the command: ```
[COLOR=#333333][FONT=UbuntuMono]sudo modprobe dm-crypt[/FONT][/COLOR]
```
4) Now issue the command: ```
cryptsetup luksOpen /dev/sda1 crypt
``` 

*Replace sda1 with the actual partition. This will prompt for your passphrase and open the partition to /dev/mapper/crypt*

5) Use whatever backup software that you prefer to make an image of the unlocked partition

You will need to do a little research to help guide you through your specific situation, but this should be enough to help get you started.

---

### Post by NomadAU on 2013-04-07
Thanks for the advice KaosuX.  I hadn't made the 'jump' to boot up using another OS implementation - I can now see how to proceed with this.  Much appreciated, thanks.

---

### Post by NomadAU on 2013-04-10
Thanks once again to KaosuX - disk encryption has been removed, and my OS is back working once more.

For anyone else who is contemplating doing something similar, here are a few extra details that I omitted in my original post.

- I am running LVM
- I found a spare SATA drive that I could use to direct copy from original disk to new disk

The process I followed was the same as advised by KaosuX, once I had created a LiveCD and booted from it (I did this using a thumbdrive, which left my DVD slot spare for a second HD)
- install crypt and lvm
```
sudo [COLOR=#333333][FONT=UbuntuMono]apt-get install cryptsetup lvm2[/FONT][/COLOR]
```
- load the modules
```
[COLOR=#333333][FONT=UbuntuMono]sudo modprobe dm-crypt[/FONT][/COLOR]
```
- open the encrypted partition
```
cryptsetup luksOpen /dev/sda5 crypt
```

I then had to go through the LVM commands so that the logical volume would be detected.  I found excellent instructions for doing this in [http://linuxwave.blogspot.com.au/2007/11/mounting-lvm-disk-using-ubuntu-livecd.html](http://linuxwave.blogspot.com.au/2007/11/mounting-lvm-disk-using-ubuntu-livecd.html)

Once I had mounted the relevant partitions, it was a simple matter to copy the contents from my original disk to the second disk.  In my case, the second disk had also been initialised using LVM and similar sized partitions created.  
Note: On the encrypted disk, the boot sector was in a separate partition (I guess because it can't be encrypted).  In the target disk (the non-encrpted one), the boot sector is in the same partition as the remainder of my OS.

Having mounted the old and new partitions at ~/oldDisk and ~/newDisk respectively, I used the following command to copy every file across.
```
rsync -a ~/oldDisk/ ~/newDisk
```
Note the '/' at the end of oldDisk....this tells rsync to copy the **contents** of oldDisk to the target.

Finally, a couple of gotchas I experienced...

On bootup with the new disk, I got the following error message
> The disk drive for /boot is not ready yet or not present

I eventually figured out that this was caused by an incorrect entry in my /etc/fstab file.  
The entry contained the UUID for the **old** disk, i.e.

UUID=**7df57494-c161-4a65-ae9d-4868832ee8e9** /boot           ext2    defaults        0       2

Changing this to the UUID value of my new disk fixed the problem - use the blkid command to find out what this value is. 

The second problem concerned my NVIDIA display driver...not sure why it screwed up, but I could only get low resolution graphics until I reinstalled the drivers.  I did this by following instructions at [[COLOR=#000000]http://www.noobslab.com/2012/10/install-latest-nvidia-drivers-in-ubuntu.html[/COLOR]]("http://www.noobslab.com/2012/10/install-latest-nvidia-drivers-in-ubuntu.html")

In essence, here are the commands I ran.
```

[COLOR=#000000][FONT=arial black]sudo apt-add-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install nvidia-current[/FONT][/COLOR][COLOR=red]
[/COLOR]
```

And that was it...now have everything running smoothly (and probably slightly quicker) without any LUKS disk encryption.

---

### Post by tubbygweilo on 2013-04-10
Thanks to you both for collecting and recording this knowledge. 
I have bookmarked it as you never know when it may be of use.

---

