---
title: "Moving virtualbox image to physical computer"
date: 2015-08-11
forum: Virtualisation
---

### Post by stas7 on 2015-08-11
Hello,

I have a virtualbox image with Xubuntu 14 and trying to move it a physical computer. I first converted virtualbox image to raw format using virtualbox utility, then mounted and copied all / files to a real HDD on physical computer preserving ownership and attributes (the physical computer is about 10 years old but when I installed the same version of Xubuntu from DVD it worked well though very slow). I don't paste exact commands simply b/c don't remember them exactly. Boot loader is created using the same version of Xubuntu I believe.
During startup in the very beginning I get:
error: no such-device 'long hexidecimal number' press any key to continue

After I press some key, it continue booting in console mode and hangs up with the following messages:
[ATTACH=CONFIG]263784[/ATTACH]

Is there a way to resolve these issues?
Thank you.

---

### Post by TheFu on 2015-08-11
This is just a guess.

The UUID for the disks have probably changed. You'll need to fix that in the /etc/fstab.
In the short term, it might be easier to just use the partition device to get it booted, then determine the disk UUID and update the fstab from inside the booted OS.
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by stas7 on 2015-08-11
> **TheFu said:**
> use the partition device to get it booted

Thank you for your reply. What do you mean by 'partition device'?
Should I boot from Xubuntu DVD on physical machine without installation and determine UUID from such boot?


 > **TheFu said:**
> 
, then determine the disk UUID and update the fstab from inside the booted OS.
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

does each partition have its own UUID or it is defined only per physical disc?
I installed Xubuntu into ext4 partition, there are still 2 more ntfs partitions on the same HDD.

---

### Post by TheFu on 2015-08-12
Device : /dev/sdxy 

Yes, boot from a liveCD/flash drive.

---

### Post by stas7 on 2015-08-14
I am sorry, still don't understand your sentence "use the partition device to get it booted".
In my understanding one can either boot from liveCD or from partition of HDD. Since you advice to boot from liveCD, how can I use partition to boot at the same time?
Could you tell your advise in steps, I am really confused?
thank you

---

### Post by TheFu on 2015-08-14
Thanks for asking for clarification. I often assume things.
* boot off a liveCD or flash drive that contains Linux
* mount the storage of the hard disk with the OS that isn't booting to /mnt
* **sudoedit** the /mnt/etc/fstab - always use the sudoedit command when editing files that need elevated authority. Do not use sudo gedit or anything similar.
* Rather than using a LABEL or UUID, use the specific /dev/sdXY "device" that you used to mount the disk under /mnt inside the fstab.  This is how we mounted disks for 20+ years, before uuids were used. Reply #2 above has a link which explains.  There is also the manpage for fstab entries - **man fstab** which explains some helpful details.  Every program and most config files have a helpful manpage.

Unrelated, but something new to Linux people don't get is that whenever someone says to edit a specific file to add some text and the file doesn't exist already ... we expect that you will create the file and add the text, then set the file ownership and permissions to be like other files in that directory.  It is impossible there isn't an fstab on the system, so that won't happen here. Don't worry.

---

### Post by stas7 on 2015-08-15
Thank you, now I was able to doit! You are right in fstab it was 'LABEL=cloudimg-rootfs ...', which I changed to:
/dev/sda1 / ext4 defaults 0 1
I put 1 in the end so that it checked filesystem. But the system still does not boot with exactly same behavior. Anything else I could try?
I used sudoedit for fstab and checked fstab file several times.

I found which device and filesystem type  to mount by double-clicking on harddrive icon in ubuntu livecd, and then used mount command in terminal. Also checked the content of partition, so I think the device name is correct

---

### Post by TheFu on 2015-08-15
Hard to help without updated information:

Please post the exact fstab, **ls -al /dev/sd*** AND the updated output from **sudo blkid**. Please use "code tags" so things line up too.


VMs sometimes don't use sdXY devices, so look for things in the /dev/ directory that look like disks or partitions.  My KVM VMs always use virtio drivers, so the disks are /dev/vd* ....

---

### Post by stas7 on 2015-08-15
Shall I execute these commands from inside virtualbox or boot from livecd on physical computer and mount nonbooting partition? 
And which fstab should I upload? Original from virtualbox?
Thanks

---

### Post by TheFu on 2015-08-16
> **stas7 said:**
> Shall I execute these commands from inside virtualbox or boot from livecd on physical computer and mount nonbooting partition? 
And which fstab should I upload? Original from virtualbox?
Thanks
 
Ah - I was confused.  We are done with the VM. Any disk information from inside it is wrong.

BTW, the method you chose to move from VM to physical is NOT the method I would have used.  I would have performed a backup of all files inside the VM using rsync, rdiff-backup or some other well-known tool.  Then I'd install a fresh xubuntu onto the physical HDD of the machine I want to use, and restore the backup files.  Then I'd fix the fstab and perhaps delete any rules inside /etc/udev//.... 70*net*.rules so the old MAC address didn't interfere.

Lastly, I'd install grub and update grub (chroot needed) as spelled out by 20 "fix ubuntu boot" how-to guides.  If you do this a few times, you'll learn the technique and have it for a year.  There is also the **boot-repair** tool, which often works in this situation, but not always.

So - I await the information.

---

### Post by stas7 on 2015-08-16
I am sorry I forgot to mention that I likely deleted all the partition content before copying files from VM. Probably all /dev and other files therefore come from VM and they are likely VM hardware specific. Is this the reason you advise to use rsync so that /dev files do not change on physical computer?
I remember it was advised to use rsync, but I couldn't get it work and used cp instead.

I thought that installation of xubuntu from livecd prior to copying VM content is needed only to configure master boot record to boot linux from correct partition and or bootloader... Is this incorrect?

---

### Post by TheFu on 2015-08-17
Please provide the requested data, if you'd like help.

---

### Post by stas7 on 2015-08-19
sorry for delayed reply, my internet access is limited.
 fstab is attached, I had to rename it otherwise the forum gives an error.

```
xubuntu@xubuntu:~$ ls -al /media/xubuntu/e0313a05-5a1d-4932-8e02-5ff36ba731e7/dev/sd*
ls: cannot access /media/xubuntu/e0313a05-5a1d-4932-8e02-5ff36ba731e7/dev/sd*: No such file or directory


xubuntu@xubuntu:~$ ls -al /media/xubuntu/e0313a05-5a1d-4932-8e02-5ff36ba731e7/dev/vd*
ls: cannot access /media/xubuntu/e0313a05-5a1d-4932-8e02-5ff36ba731e7/dev/vd*: No such file or directory
```

The only device I found that looks like drive is "disk".

```
xubuntu@xubuntu:~$ sudo blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="e0313a05-5a1d-4932-8e02-5ff36ba731e7" TYPE="ext4" 
/dev/sda2: UUID="F6B4A4EEB4A4B313" TYPE="ntfs" 
/dev/sda4: UUID="00fbf1ec-cf4b-46e8-8bf5-8216d2fa5cfd" TYPE="swap" 
/dev/sda5: LABEL="Private_External" UUID="4220D2FD20D2F6BF" TYPE="ntfs" 
/dev/sr0: LABEL="Xubuntu 14.04.1 LTS i386" TYPE="iso9660"
```


```
xubuntu@xubuntu:~$ ls -al /media/xubuntu/e0313a05-5a1d-4932-8e02-5ff36ba731e7/dev/
total 20
drwxr-xr-x  5 root root     4096 Jul 16  2014 .
drwxr-xr-x 23 root root     4096 Feb  1 19:08 ..
crw-rw----  1 root video 10, 175 Jul 16  2014 agpgart
crw-rw----  1 root audio 14,   4 Jul 16  2014 audio
crw-rw----  1 root audio 14,  20 Jul 16  2014 audio1
crw-rw----  1 root audio 14,  36 Jul 16  2014 audio2
crw-rw----  1 root audio 14,  52 Jul 16  2014 audio3
crw-rw----  1 root audio 14,   7 Jul 16  2014 audioctl
drwxr-xr-x  2 root root     4096 Jul 16  2014 block
crw-------  1 root tty    5,   1 Jul 16  2014 console
lrwxrwxrwx  1 root root       11 Jul 16  2014 core -> /proc/kcore
drwxr-xr-x  4 root root     4096 Jul 16  2014 disk
crw-rw----  1 root audio 14,   3 Jul 16  2014 dsp
crw-rw----  1 root audio 14,  19 Jul 16  2014 dsp1
crw-rw----  1 root audio 14,  35 Jul 16  2014 dsp2
crw-rw----  1 root audio 14,  51 Jul 16  2014 dsp3
lrwxrwxrwx  1 root root       13 Jul 16  2014 fd -> /proc/self/fd
crw-rw-rw-  1 root root   1,   7 Jul 16  2014 full
crw-r-----  1 root kmem   1,   2 Jul 16  2014 kmem
brw-rw----  1 root disk   7,   0 Jul 16  2014 loop0
brw-rw----  1 root disk   7,   1 Jul 16  2014 loop1
brw-rw----  1 root disk   7,   2 Jul 16  2014 loop2
brw-rw----  1 root disk   7,   3 Jul 16  2014 loop3
brw-rw----  1 root disk   7,   4 Jul 16  2014 loop4
brw-rw----  1 root disk   7,   5 Jul 16  2014 loop5
brw-rw----  1 root disk   7,   6 Jul 16  2014 loop6
brw-rw----  1 root disk   7,   7 Jul 16  2014 loop7
crw-r-----  1 root kmem   1,   1 Jul 16  2014 mem
crw-rw----  1 root audio 35,   0 Jul 16  2014 midi0
crw-rw----  1 root audio 14,   2 Jul 16  2014 midi00
crw-rw----  1 root audio 14,  18 Jul 16  2014 midi01
crw-rw----  1 root audio 14,  34 Jul 16  2014 midi02
crw-rw----  1 root audio 14,  50 Jul 16  2014 midi03
crw-rw----  1 root audio 35,   1 Jul 16  2014 midi1
crw-rw----  1 root audio 35,   2 Jul 16  2014 midi2
crw-rw----  1 root audio 35,   3 Jul 16  2014 midi3
crw-rw----  1 root audio 14,   0 Jul 16  2014 mixer
crw-rw----  1 root audio 14,  16 Jul 16  2014 mixer1
crw-rw----  1 root audio 14,  32 Jul 16  2014 mixer2
crw-rw----  1 root audio 14,  48 Jul 16  2014 mixer3
crw-rw----  1 root audio 31,   0 Jul 16  2014 mpu401data
crw-rw----  1 root audio 31,   1 Jul 16  2014 mpu401stat
crw-rw-rw-  1 root root   1,   3 Jul 16  2014 null
crw-r-----  1 root kmem   1,   4 Jul 16  2014 port
crw-rw-rw-  1 root tty    5,   2 Jun 23  2014 ptmx
drwxr-xr-x  2 root root     4096 Jul 16  2014 pts
lrwxrwxrwx  1 root root        4 Jul 16  2014 ram -> ram1
brw-rw----  1 root disk   1,   0 Jul 16  2014 ram0
brw-rw----  1 root disk   1,   1 Jul 16  2014 ram1
brw-rw----  1 root disk   1,  10 Jul 16  2014 ram10
brw-rw----  1 root disk   1,  11 Jul 16  2014 ram11
brw-rw----  1 root disk   1,  12 Jul 16  2014 ram12
brw-rw----  1 root disk   1,  13 Jul 16  2014 ram13
brw-rw----  1 root disk   1,  14 Jul 16  2014 ram14
brw-rw----  1 root disk   1,  15 Jul 16  2014 ram15
brw-rw----  1 root disk   1,  16 Jul 16  2014 ram16
brw-rw----  1 root disk   1,   2 Jul 16  2014 ram2
brw-rw----  1 root disk   1,   3 Jul 16  2014 ram3
brw-rw----  1 root disk   1,   4 Jul 16  2014 ram4
brw-rw----  1 root disk   1,   5 Jul 16  2014 ram5
brw-rw----  1 root disk   1,   6 Jul 16  2014 ram6
brw-rw----  1 root disk   1,   7 Jul 16  2014 ram7
brw-rw----  1 root disk   1,   8 Jul 16  2014 ram8
brw-rw----  1 root disk   1,   9 Jul 16  2014 ram9
crw-rw-rw-  1 root root   1,   8 Jul 16  2014 random
crw-rw----  1 root audio 35,  64 Jul 16  2014 rmidi0
crw-rw----  1 root audio 35,  65 Jul 16  2014 rmidi1
crw-rw----  1 root audio 35,  66 Jul 16  2014 rmidi2
crw-rw----  1 root audio 35,  67 Jul 16  2014 rmidi3
crw-rw----  1 root audio 14,   1 Jul 16  2014 sequencer
lrwxrwxrwx  1 root root        8 Jul 16  2014 shm -> /run/shm
crw-rw----  1 root audio 35, 128 Jul 16  2014 smpte0
crw-rw----  1 root audio 35, 129 Jul 16  2014 smpte1
crw-rw----  1 root audio 35, 130 Jul 16  2014 smpte2
crw-rw----  1 root audio 35, 131 Jul 16  2014 smpte3
crw-rw----  1 root audio 14,   6 Jul 16  2014 sndstat
lrwxrwxrwx  1 root root        4 Jul 16  2014 stderr -> fd/2
lrwxrwxrwx  1 root root        4 Jul 16  2014 stdin -> fd/0
lrwxrwxrwx  1 root root        4 Jul 16  2014 stdout -> fd/1
crw-rw-rw-  1 root tty    5,   0 Jul 16  2014 tty
crw-------  1 root tty    4,   0 Jul 16  2014 tty0
crw-------  1 root tty    4,   1 Jul 16  2014 tty1
crw-------  1 root tty    4,   2 Jul 16  2014 tty2
crw-------  1 root tty    4,   3 Jul 16  2014 tty3
crw-------  1 root tty    4,   4 Jul 16  2014 tty4
crw-------  1 root tty    4,   5 Jul 16  2014 tty5
crw-------  1 root tty    4,   6 Jul 16  2014 tty6
crw-------  1 root tty    4,   7 Jul 16  2014 tty7
crw-------  1 root tty    4,   8 Jul 16  2014 tty8
crw-------  1 root tty    4,   9 Jul 16  2014 tty9
crw-rw-rw-  1 root root   1,   9 Jul 16  2014 urandom
prw-r-----  1 root adm         0 Jul 16  2014 xconsole
crw-rw-rw-  1 root root   1,   5 Jul 16  2014 zero
```

---

### Post by TheFu on 2015-08-19
If you boot off the CDROM, is there an option to "boot from the first disk?"  Does that work?

If not, boot from the CDROM, install **boot-repair** and post the generated output link back here. For the time wasted so far, probably would have been easier to just install the OS onto the physical machine and copy over the files from the VM storage.

---

