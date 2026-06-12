---
title: "Main Ecrypted LVM not Accessible after Deleting a Different Encrypted LVM on USB HD"
date: 2011-03-07
forum: Security
---

### Post by jreece on 2011-03-07
I installed Ubuntu 10.10 64 on my laptop with the entire 500gb setup as encrypted LVM. This has worked well for several months with no problems. During this time i have been backing up the data to an external usb drive (1tb) on a regular basis. The usb drive was not encrypted. So, I thought it would be a good idea to encrypt the backup drive too. I wiped out the backup drive and set it up as one large encrypted lvm and mbr. This seemed to work fine but immediately afterwards I decided to erase that and set it up as encrypted lvm guid instead of mbr. I couldn't delete it while logged into my desktop so i decided to do it from a bootable gparted usb stick. In gparted i erased the 1TB backup drive once again and planned on setting it up the way I wanted once I was logged back into my ubuntu desktop. Now I cant boot into my desktop with the following errors:
 
cryptsetup: evms_activate is not available
b0d) does not begin with /dev/mapper/
 
Then after waiting for a few minutes I get an error followed by (initramfs) 
 
When booting from a live version of ubuntu the 250MB boot patition is recognized and 500 partion is there but it is labeled as empty/unused. 
 
Also, I did choose to use the exact same passphrase as what is used on the main bootable drive when I set up the encrypted partition on the external 1TB drive. 
 
Thanks for your help.

---

### Post by bodhi.zazen on 2011-03-07
Boot a live CD and try to mount (open) the crypt and LVM.

---

### Post by jreece on 2011-03-07
"When booting from a live version of ubuntu the 250MB boot patition is recognized and 500 partion is there but it is labeled as empty/unused."
 
Already tried that.

---

### Post by bodhi.zazen on 2011-03-07
> **jreece said:**
> "When booting from a live version of ubuntu the 250MB boot patition is recognized and 500 partion is there but it is labeled as empty/unused."
 
Already tried that.

It does not sound as if you know how to mount a crypt or a LVM with a live CD then.

See :

[http://ubuntuforums.org/showthread.php?p=4530641](http://ubuntuforums.org/showthread.php?p=4530641)

You need to install a few packages, then open them with the command line.

```
sudo cryptsetup luksOpen /dev/sdXY crypt
```

Change "sdXY" to the partition to decrypt.

Then continue with the LVM commands

```
sudo vgscan --mknodes
sudo vgchange -ay
```

Then mount the LVM

```
sudo mount /dev/mapper/your_lvm /mnt
```

---

### Post by jreece on 2011-03-07
Awesome, I'll try that when I get a chance in an hour or two. Thanks.

---

### Post by jreece on 2011-03-07
I tried that too and nothing happens and it doesn't prompt for password. I'm getting a little concerned because the disk utility shows the sda2 partition as free and unused, not encrypted.

---

### Post by bodhi.zazen on 2011-03-07
> **jreece said:**
> I tried that too and nothing happens and it doesn't prompt for password. I'm getting a little concerned because the disk utility shows the sda2 partition as free and unused, not encrypted.

Output of :

```
sudo cryptsetup luksOpen /dev/sda2 crypt
```

?

---

### Post by jreece on 2011-03-07
Just goes back to prompt. There is no output.

---

### Post by bodhi.zazen on 2011-03-07
> **jreece said:**
> Just goes back to prompt. There is no output.

That is odd. It should return something, can you copy-paste the output.

---

### Post by jreece on 2011-03-07
ubuntu@ubuntu:~$ sudo cryptsetup luksOpen /dev/sda2 crypt
ubuntu@ubuntu:~$

---

### Post by bodhi.zazen on 2011-03-07
I have not seen that behavior before, it either aks for a password or gives an error message if it is not a LUKS partition.

Try changing to root:

```
sudo -i
``` and run the command from there.

You can also try proceeding with the lvm commands (vgscan ... )

---

### Post by jreece on 2011-03-07
ubuntu@ubuntu:~$ sudo cryptsetup luksOpen /dev/sda2 crypt
ubuntu@ubuntu:~$ sudo -i
root@ubuntu:~# cryptsetup luksOpen /dev/sda2 crypt
root@ubuntu:~# vgscan --mknodes
  Reading all physical volumes.  This may take a while...
root@ubuntu:~# vgchange -ay
root@ubuntu:~#

---

### Post by jreece on 2011-03-07
Here is a screen shot of the disk utility.

---

### Post by bodhi.zazen on 2011-03-07
Mount it =)

Your partitions are listed in /dev/mapper

```
mount /dev/mapper/your_partition /mnt

ls /mnt
```

---

### Post by jreece on 2011-03-07
Here it is again.

---

### Post by jreece on 2011-03-07
ubuntu@ubuntu:~$ mount /dev/mapper/your_partition /mnt
mount: only root can do that
ubuntu@ubuntu:~$ sudo -i
root@ubuntu:~# mount /dev/mapper/your_partition /mnt
mount: special device /dev/mapper/your_partition does not exist
root@ubuntu:~# ls /mnt
root@ubuntu:~#

---

### Post by bodhi.zazen on 2011-03-07
The screen shot is not helpful as I do not think the graphical tool recognizes either a crypt or LVM.

What is listed in /dev/mapper ?

What happens when you mount your LVM partition ?

---

### Post by bodhi.zazen on 2011-03-07
> **jreece said:**
> ubuntu@ubuntu:~$ mount /dev/mapper/your_partition /mnt
mount: only root can do that
ubuntu@ubuntu:~$ sudo -i
root@ubuntu:~# mount /dev/mapper/your_partition /mnt
mount: special device /dev/mapper/your_partition does not exist
root@ubuntu:~# ls /mnt
root@ubuntu:~#

You have to change "your_partition" to the name of your LVM partition. If you do not know what that is, ls /dev/mapper

Side note: If you are going to use encryption and LVM I highly advise you do some reading. The time to learn how these tools work is NOT when you are having problems.

---

### Post by jreece on 2011-03-07
ubuntu@ubuntu:~$ ls /dev/mapper
control
ubuntu@ubuntu:~$ sudo mount /dev/mapper/control /mnt
mount: /dev/mapper/control is not a block device
ubuntu@ubuntu:~$

---

### Post by bodhi.zazen on 2011-03-07
If this is a live CD, and you installed all the packages I advised, it then appears you have lost your data.

It is odd there were no error messages, but that leaves me with nothing to go on.

I am not aware of any data recovery software or techniques that will recover your data.

My only guess would be you managed your partitions with a graphical tool (such as gparted) that does not recognize crypts or lvm and that this tool somehow corrupted your crypt.

You can try

```
mount /dev/sda2 /mnt
ls /mnt
```

---

### Post by jreece on 2011-03-07
ubuntu@ubuntu:~$ sudo mount /dev/sda2 /mnt
mount: you must specify the filesystem type

---

### Post by jreece on 2011-03-07
I appreciate your help. I use the encrypted partitions to comply with company policy and have used it for a couple of years. I understand the concepts of lvm and encryption but have always used the GUI. After all, that's why most people use Ubuntu because it tends to geared more towards people who are not Linux experts.

---

### Post by bodhi.zazen on 2011-03-07
> **jreece said:**
> I appreciate your help. I use the encrypted partitions to comply with company policy and have used it for a couple of years. I understand the concepts of lvm and encryption but have always used the GUI. After all, that's why most people use Ubuntu because it tends to geared more towards people who are not Linux experts.

I understand, but after using encryption for some time I highly advise you learn to use the command line tools.

The "problem" with the graphical tools is, as I said, they really do not manage crypts and then you have data loss.

---

### Post by jreece on 2011-03-07
Thanks again for your help. I was afraid the data was gone and you have confirmed that. As with most data loss, it's not the end of the world but is highly inconvenient. Do you have any suggestions for learning the command line tools?

---

### Post by bodhi.zazen on 2011-03-07
> **jreece said:**
> Thanks again for your help. I was afraid the data was gone and you have confirmed that. As with most data loss, it's not the end of the world but is highly inconvenient. Do you have any suggestions for learning the command line tools?

Manually configure a crypt (LUKS) and LVM.

Work though something like :

[https://wiki.archlinux.org/index.php/System_Encryption_with_LUKS_for_dm-crypt](https://wiki.archlinux.org/index.php/System_Encryption_with_LUKS_for_dm-crypt)

[http://www.g-loaded.eu/2005/11/10/encrypt-devices-using-dm-crypt-and-luks/](http://www.g-loaded.eu/2005/11/10/encrypt-devices-using-dm-crypt-and-luks/)

Read up on LVM

See also :

[http://ubuntuforums.org/showthread.php?p=4530641](http://ubuntuforums.org/showthread.php?p=4530641)

If you can manually set up a crypt, configure LVM, then configure it to mount at boot.

Then mount it with a live CD.

---

