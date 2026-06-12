---
title: "need help updating GRUB -ubuntu 20.04 LTS"
date: 2021-11-29
forum: Ubuntu/Debian BASED
---

### Post by unknowable on 2021-11-29
Hi everyone.  I installed Ubuntu a couple of weeks ago (for the first time) and have spent a lot of time getting it set up and customized properly.  One of the things I wanted was a LUKS encrypted filesystem.  I currently have partitions for _/boot_, _/boot/UEFI_, and my home directory.  The home directory's partition is LUKS encrypted.  Later I wanted to reinstall Windows somewhere because I **love** my old photo organization tool and can't find a replacement in Linux that does what I want.  I didn't really want to shrink my Ubuntu partitions at all, so I dug up an old 1TB disk that I was able to add to the computer (internally) and installed Windows 10 to it last night.  Here's the issue:

Now when I start up the machine, it goes right into Windows.  I am able to use the Boot Menu in the BIOS to boot to my ubuntu partition with no issues, but I'd really like to add windows to grub.conf and just have GRUB control everything, like without having to go through the boot menu every time.  After installing windows, I opened a terminal and ran *sudo update-grub*.  That ran for a bit, but it didn't find my windows partition located on /dev/sdb.  In fact, the main Win10 partition is /dev/sdb2/ but of course, windows creates a few extra partitions, probably including a boot partition.

My problem is just that I can't add Windows to GRUB, at least not using the above command line.  I did try loading Grub Customizer, but I don't know how to get it to search for other boot partitions, and those are the only ways I can think of to bring windows into GRUB by a noob like me.  I was able to locate the grub.conf and edit it, at least to make sure the GRUB Customizer was looking at the right file.  I can bring up the grub.conf by using the command *sudo nano /boot/grub/grub.cfg* but I have no idea how to add a partition, specifically a windows partition, to GRUB.  I was hoping that *sudo update-grub* would do it, but it didn't find it.  So now I'm a little stuck, and that's where you come in (hopefully).   :D

What I'd really love to make happen would be to change one of the existing options in GRUB - "elementary OS, with Linux 5.11.0-37-generic" - to instead boot Windows 10 on /sdb.  In other words, the menu item in GRUB should still say the same thing - "elementary OS, with Linux 5.11.0-37-generic" - but would instead secretly load Windows.   I currently have GRUB loading the default OS in 2 seconds I think it is, so if anyone else ever used my computer, they would just default to eOS and wouldn't be able to unlock the user partition, and it wouldn't boot.  I know if I hit an arrow key at all on the GRUB screen it stops the timer, so that shouldn't be an issue for me to choose.  Here's a screencap of nano /boot/grub/grub.  Sorry it's full size.  If I should shrink these in the future, say so.  I just thought a full size screencap would let you clearly see everything.


[ATTACH=CONFIG]289547[/ATTACH]

Wow, that's huge!  I'm only at 1920*1080, but that image looks gigantic.  Oh well, there it is. I guess just right click and Open image in a new tab.   :D

At any rate, thank you again in advance for your time and attention.  I promise I'm keeping careful notes on everything I do to the system, and your assistance will be greatly appreciated, as well as recorded in my personal notes.
____________________________________________

EDIT:  Oh, look at that.  The forum is smart enough to shrink my picture so it fits on the page.  That's something to remember.

---

### Post by #&amp;thj^% on 2021-11-29
Run the following on the command line (Ctrl+Alt+t):
```

sudo os-prober
```

If your Windows installation was found, you can then run:
```

sudo update-grub
```

If a "command not found" error is returned, use:
```
sudo apt install os-prober
```
Good luck. BTW I'm not a fan of "**Grub-Customize**r" in the wrong hands cause more grief than necessary

---

### Post by oldfred on 2021-11-29
Moved to Other OS, since elementary OS is not Ubuntu.

Are both installed in UEFI or both in BIOS boot mode?
How you boot install media, for both Linux & Windows is how it installs.

Systems since 2012 are UEFI, as Microsoft has required vendors to install in UEFI boot mode to gpt partitioned drives. 
Windows only boots in UEFI mode from gpt and only in BIOS/CSM/Legacy mode from MBR.
Only recently have some vendors made systems that are UEFI only.

---

### Post by #&amp;thj^% on 2021-11-29
> **oldfred said:**
> 

Are both installed in UEFI or both in BIOS boot mode?

Only recently have some vendors made systems that are UEFI only.

Thought never even occurred to me, good call oldfred.
Due to this from OP >  I am able to use the Boot Menu in the BIOS to boot to my ubuntu partition with no issues,
My Lenovo Legion 5 is in deed UEFI Only (2020)

---

### Post by unknowable on 2021-11-29
> **1fallen said:**
> Run the following on the command line (Ctrl+Alt+t):
```

sudo os-prober
```

Cool, thanks for the help! I tried this and it found Windows partition:

```
unknowable@Elite8300:~$ sudo os-prober
[sudo] password for unknowable:
  /dev/sdf: open failed: No medium found
  /dev/sdf: open failed: No medium found
/dev/sda1@/EFI/Microsoft/Boot/bootmgfw.efi:Windows Boot Manager:Windows:efi
```

Great!  Continuing...

> **1fallen said:**
>  If your Windows installation was found, you can then run:
```

sudo update-grub
```

Hm.  Did that, and it couldn't find a disk:

```
unknowable@Elite8300:~$ sudo update-grub
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
  /dev/sdf: open failed: No medium found
  /dev/sdf: open failed: No medium found
  /dev/sdf: open failed: No medium found
  /dev/sdf: open failed: No medium found
  /dev/sdf: open failed: No medium found
  /dev/sdf: open failed: No medium found
  /dev/sdf: open failed: No medium found
  /dev/sdf: open failed: No medium found
  /dev/sdf: open failed: No medium found
  /dev/sdf: open failed: No medium found
  /dev/sdf: open failed: No medium found
  /dev/sdf: open failed: No medium found
  /dev/sdf: open failed: No medium found
  /dev/sdf: open failed: No medium found
  /dev/sdf: open failed: No medium found
  /dev/sdf: open failed: No medium found
  /dev/sdf: open failed: No medium found
  /dev/sdf: open failed: No medium found
  /dev/sdf: open failed: No medium found
  /dev/sdf: open failed: No medium found
  /dev/sdf: open failed: No medium found
  /dev/sdf: open failed: No medium found
  /dev/sdf: open failed: No medium found
  /dev/sdf: open failed: No medium found
Found linux image: /boot/vmlinuz-5.11.0-41-generic
Found initrd image: /boot/initrd.img-5.11.0-41-generic
Found linux image: /boot/vmlinuz-5.11.0-40-generic
Found initrd image: /boot/initrd.img-5.11.0-40-generic
Found linux image: /boot/vmlinuz-5.11.0-37-generic
Found initrd image: /boot/initrd.img-5.11.0-37-generic
  /dev/sdf: open failed: No medium found
  /dev/sdf: open failed: No medium found
  /dev/sdf: open failed: No medium found
  /dev/sdf: open failed: No medium found
done
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
  /dev/sdf: open failed: No medium found
  /dev/sdf: open failed: No medium found
  /dev/sdf: open failed: No medium found
  /dev/sdf: open failed: No medium found
  /dev/sdf: open failed: No medium found
  /dev/sdf: open failed: No medium found
  /dev/sdf: open failed: No medium found
  /dev/sdf: open failed: No medium found
  /dev/sdf: open failed: No medium found
  /dev/sdf: open failed: No medium found
  /dev/sdf: open failed: No medium found
  /dev/sdf: open failed: No medium found
  /dev/sdf: open failed: No medium found
  /dev/sdf: open failed: No medium found
  /dev/sdf: open failed: No medium found
  /dev/sdf: open failed: No medium found
  /dev/sdf: open failed: No medium found
  /dev/sdf: open failed: No medium found
  /dev/sdf: open failed: No medium found
  /dev/sdf: open failed: No medium found
  /dev/sdf: open failed: No medium found
  /dev/sdf: open failed: No medium found
  /dev/sdf: open failed: No medium found
  /dev/sdf: open failed: No medium found
Found linux image: /boot/vmlinuz-5.11.0-41-generic
Found initrd image: /boot/initrd.img-5.11.0-41-generic
Found linux image: /boot/vmlinuz-5.11.0-40-generic
Found initrd image: /boot/initrd.img-5.11.0-40-generic
Found linux image: /boot/vmlinuz-5.11.0-37-generic
Found initrd image: /boot/initrd.img-5.11.0-37-generic
  /dev/sdf: open failed: No medium found
  /dev/sdf: open failed: No medium found
  /dev/sdf: open failed: No medium found
  /dev/sdf: open failed: No medium found
done
```

I checked the Disks utility, and it looks like /dev/sdf is the encrypted drive mounted by LUKS, I guess:

[ATTACH=CONFIG]289548[/ATTACH]

Although  it does say it's a USB disk of some sort.  It doesn't say what size it  is, so I don't have any idea which one it is.  :p  Hm.  Well, no success  yet, so I kept following:

> **1fallen said:**
> If a "command not found" error is returned, use:
```
sudo apt install os-prober
```

I  have to admit, I've been up for like 30 hours, and I had a total Windows  user moment.  :D   I followed your instructions without looking to see  what I was doing.  Obviously os-prober worked when I tried it, which was  the first command, but I wasn't thinking and just ran it anyway.  It just said that os-prober was the latest version:

```
unknowable@Elite8300:~$ sudo apt install os-prober
Reading package lists... Done
Building dependency tree       
Reading state information... Done
os-prober is already the newest version (1.74ubuntu2).
os-prober set to manually installed.
```

Hm.  I did try opening up that disk in Files, and also from the command line, but there wasn't anything there.  :p

> **1fallen said:**
> Good luck. BTW I'm not a fan of  "Grub-Customizer" in the wrong hands cause more grief than  necessary

Heh.  Thank you for the note.  I only used it  to make some changes once, and it broke GRUB, so I had to re-image the  drive from backup.  Took a while, but no issue in that case.  I'll be  careful.

That being said, your first command worked, it found the Windows partition right away, but *sudo update-grub*  did not.  I see someone else posted, let me see where they're taking  me.  Thanks for the first step though, that's a useful command to know  and I have notated it in my record.  Thank you.

---

### Post by unknowable on 2021-11-29
> **oldfred said:**
> Moved to Other OS, since elementary OS is not Ubuntu.

Sorry about the misplaced post.  I thought it would be good to post there because eOS is based on Ubuntu 20.04 LTS, and everything I've Google'd for help generally works when I add "AND ubuntu" to the end of my search terms.  Sorry!
______________________________

EDIT: Oh, I see!  You moved it to Ubuntu BASED.  That makes sense, thanks.
______________________________

> **oldfred said:**
>  Are both installed in UEFI or both in BIOS boot mode?
How you boot install media, for both Linux & Windows is how it installs.

Systems since 2012 are UEFI, as Microsoft has required vendors to install in UEFI boot mode to gpt partitioned drives. 
Windows only boots in UEFI mode from gpt and only in BIOS/CSM/Legacy mode from MBR.
Only recently have some vendors made systems that are UEFI only.

Windows is installed in UEFI mode, but Ubuntu isn't.  It's MBR, and I  can't get my BIOS to boot /dev/sda because of that.  This computer is  just a couple of weeks old, and I still can't find where in the BIOS to  allow MBR booting.  I'll check again at some point looking for  CSM/Legacy mode, but I haven't found it yet.  What that means right now  is that no matter what, I **have** to go into the Boot Menu  when it starts up and then load Ubuntu.  I did try disabling EFI  booting mode on everything, and only allowing Legacy mode drives to  start, but my system just hangs at boot time unless UEFI mode is  enabled.

---

### Post by unknowable on 2021-11-29
> **oldfred said:**
> [COLOR=Navy]UEFI boot install & repair info - Regularly Updated :[/COLOR][INDENT] [https://ubuntuforums.org/showthread.php?t=2147295]("http://ubuntuforums.org/showthread.php?t=2147295")
       Please use Thread Tools above first post to change to [Solved] when/if answered completely.[/INDENT]
[INDENT]

[/INDENT]
Hmm, this is some good reading, really informative.  I'll be doing a bit of reading for a while.  Although to be honest, while I do see switching to UEFI will help solve my issue, the primary issue still exists: GRUB can't see Windows at all.  Even if I get eOS to UEFI, that will still mean going into the Boot Menu regularly, since GRUB doesn't handle both of them.  But I haven't read it yet, so I don't know anything.   :D  We'll see, and thanks for your help.

---

### Post by #&amp;thj^% on 2021-11-29
> **unknowable said:**
> Although to be honest, while I do see switching to UEFI will help solve my issue, the primary issue still exists: GRUB can't see Windows at all. 
 Even if I get eOS to UEFI, that will still mean going into the Boot Menu regularly, since GRUB doesn't handle both of them.  .

Once they are both in proper booting order **"UEFI"** they both will show up>>>Windows&Buntu in grub. :)
I would now>> if i were you is just install eOS in UEFI mode.

---

### Post by QIII on 2021-11-29
@unknowable

Please do not insert large images into your posts.  Believe it or not, there are users who still have slow connections or data limits.  You may cause users to wait for a long time for the image to download.  Worse, you may cost them money.

To insert expandable thumbnails, please use the attachment facility provided by the "paperclip" button above the text entry box.

---

### Post by unknowable on 2021-11-29
> **QIII said:**
> @unknowable

Please do not insert large images into your posts.  Believe it or not, there are users who still have slow connections or data limits.  You may cause users to wait for a long time for the image to download.  Worse, you may cost them money.

To insert expandable thumbnails, please use the attachment facility provided by the "paperclip" button above the text entry box.

Ack, sorry!  Yes, I'll do that from now on.  I see the paperclip, I'll start doing that from now on.  Thank you for the instruction.

---

### Post by oldfred on 2021-11-29
Did you say what brand/model system?

Some other users have posted that system seems to be UEFI only. Not sure if then user could not find setting, as some seem to hide it or not.
Lenovo announced all 2020 products will be UEFI only (UEFI Class 3 or no CSM).
[https://support.lenovo.com/us/en/solutions/ht510878-legacy-bios-boot-support-removed-in-lenovo-2020-products](https://support.lenovo.com/us/en/solutions/ht510878-legacy-bios-boot-support-removed-in-lenovo-2020-products)

But if you were able to boot installer in BIOS mode, I would think you could boot an install in BIOS mode.

---

### Post by unknowable on 2021-11-29
> **1fallen said:**
> Once they are both in proper booting order **"UEFI"** they both will show up>>>Windows&Buntu in grub. :)
I would now>> if i were you is just install eOS in UEFI mode.

Hm.  I checked my iso of eOS, and it's just named "elementaryos-6.0-stable.20211005.iso".  I was sure it was x64, but the boot partitions I'm sure are MBR only.  It looks like that's my answer.  I guess now I have to figure out how to do that.  :D

Oh, now that I look at the [eOS install page]("https://elementary.io/docs/installation#recommended-system-specifications"), it specifically tells you how to install in EFI mode.  Looks like I have some work ahead of me.  Good thing I've kept good notes on everything I've done.  Thanks for your help!

---

### Post by unknowable on 2021-11-29
> **oldfred said:**
> 
....

But if you were able to boot installer in BIOS mode, I would think you could boot an install in BIOS mode.

I just used the Boot Menu to boot from the USB thumb drive that I had installed the installation OS to.  Hm.  Lots of reading to do....

---

### Post by unknowable on 2021-11-29
> **oldfred said:**
> Did you say what brand/model system?

Oh sorry, no I didn't.  I'm using an HP/Compaq Elite 8300.  According to System Settings, it's a "Quad-Core Intel® Core™ i5-3470 CPU @ 3.20GHz".  Does that help at all?

---

### Post by oldfred on 2021-11-29
Conversion from MBR to gpt will erase drive, so if you have any other data on drive, be sure to have good backups.
There are tools to convert MBR to gpt without erasing data (backups still required). But full reinstall of grub and edit of anyplace like fstab with UUIDs has to be manually edited as change creates new UUIDs. Conversion better for data only drives. New install often easier.

How you boot install media from UEFI boot menu is then how it installs.
So your UEFI boot menu for the USB flash drive should have two entries.
But some tools like Rufus make either UEFI only or BIOS only installers.

---

### Post by #&amp;thj^% on 2021-11-29
> **oldfred said:**
> 
But if you were able to boot installer in BIOS mode, I would think you could boot an install in BIOS mode.
 GRUB can't switch between these two boot modes, at least to my knowledge.
OP can boot to both windows and eOS, just wants grub to pick them both up.

---

### Post by unknowable on 2021-11-29
> **oldfred said:**
> Conversion from MBR to gpt will erase drive, so if you have any other data on drive, be sure to have good backups.
There are tools to convert MBR to gpt without erasing data (backups still required). But full reinstall of grub and edit of anyplace like fstab with UUIDs has to be manually edited as change creates new UUIDs. Conversion better for data only drives. New install often easier.

Hm.  Well I image the entire drive every night using Clonezilla, so I have some decent backups.  I don't know if I can just reinstall one partition though, my home directory.  I have some research to do...

> **oldfred said:**
>  How you boot install media from UEFI boot menu is then how it installs.
So your UEFI boot menu for the USB flash drive should have two entries.
But some tools like Rufus make either UEFI only or BIOS only installers.

Yah, I think I was trying out Kubuntu when I installed elementary OS, so I was able to use Etcher.  I don't know what it does.  :D   Looks like I should just boot the Clonezilla USB iso and see if it will reinstall just one partition.  If it does, then I can reinstall eOS as EFI, and use Clonezilla to rebuild just the home directory's partition.  Hmm.

---

### Post by unknowable on 2021-11-29
> **1fallen said:**
> GRUB can't switch between these two boot modes, at least to my knowledge.
OP can boot to both windows and eOS, just wants grub to pick them both up.

Yes, that's basically correct.  If I don't do anything on bootup, it  goes straight into windows with no choices.  If I hit the Boot Menu  key, it gives me lots of choices, like for every drive I have.  :)   Because of what you say - GRUB can't switch between two boot modes - I  need to reinstall eOS as EFI, according to the way they instruct on the  eOS website.

---

### Post by #&amp;thj^% on 2021-11-29
> **unknowable said:**
>  If it does, then I can reinstall eOS as EFI, and use Clonezilla to rebuild just the home directory's partition.  Hmm.
[s]That's quite advanced, probably easier and less stressful to just re-install in UEFI, the learning curve is beneficial. IMHO[/s]
missed the part "Home Only" very do-able.

---

### Post by unknowable on 2021-11-29
> **1fallen said:**
> [s]That's quite advanced, probably easier and less stressful to just re-install in UEFI, the learning curve is beneficial. IMHO[/s]
missed the part "Home Only" very do-able.

Ok then that should be as easy as it sounds, assuming Clonezilla will let me reinstall only selected partitions.  I'm sure it will do that, I just need to research it.  Great!  Does that mean that if I reinstall eOS as EFI, then use Clonezilla (if it will do this) to reimage just the home directory, that all my programs and settings and things will still be in place?  Boy, that would be awesome!  That's just like an hour of work, and that's nothing.  If it works that way.  :D   If it might be able to do that, I really need to back up one more time, which will take 3 hours, but it will save me a lot of trouble as compared to reinstalling **everything**.  Yes, research.  Thank you.

---

### Post by #&amp;thj^% on 2021-11-29
You can use the following command in a terminal:
```

sudo tar -cvf /path/to/archive/backup.tar /home/username
```
**_**Proper naming is crucial here take your time._**
This file will contain all the content of /home, and can be stored on for instance a USB disk.

Once you have reinstalled 20.04 you can restore this with
```

sudo -i
cd /home/
tar --exclude=.cache -xvf /path/to/archive/backup.tar
```

In addition you may have to restore ownership of your home directory.

```
sudo chown -R username.username /home/username
```

If you make a separate partition for /home (or you already have this) you can simply re-install 20.04, and use the old /home.

---

### Post by unknowable on 2021-11-29
Hm.  Disks says that sda1 (/boot/efi) **is **an EFI type partition, and that it's FAT32.  Do I really need to reinstall?

Also, it doesn't look like Clonezilla can restore just one partition.   Would it be possible, since it's just the user directory, to use  something like KDE Partition Manager to just copy the home directory's  partition onto a USB HDD, then reinstall eOS, then just copy the home  directory's partition back over what I installed?

---

### Post by unknowable on 2021-11-29
Dang.  I posted, attached the image, and had it put it inline.  Turns out that does the same thing I was doing earlier.  I reposted correctly, bu there's no way to delete my initial (wrong) post.  Sorry everyone, I'm learning.

---

### Post by #&amp;thj^% on 2021-11-29
> **unknowable said:**
> Dang.  I posted, attached the image, and had it put it inline.  Turns out that does the same thing I was doing earlier.  I reposted correctly, bu there's no way to delete my initial (wrong) post.  Sorry everyone, I'm learning.
All Good we all have been here as well. :)

---

### Post by unknowable on 2021-11-29
> **1fallen said:**
> You can use the following command in a terminal:
```

sudo tar -cvf /path/to/archive/backup.tar /home/username
```
**_**Proper naming is crucial here take your time._**
This file will contain all the content of /home, and can be stored on for instance a USB disk.

Once you have reinstalled 20.04 you can restore this with
```

sudo -i
cd /home/
tar --exclude=.cache -xvf /path/to/archive/backup.tar
```

In addition you may have to restore ownership of your home directory.

```
sudo chown -R username.username /home/username
```

If you make a separate partition for /home (or you already have this)  you can simply re-install 20.04, and use the old /home.

OK!!   Thank you!!  Cool, I can back up my home partition, reinstall eOS, and  then restore just the home partition!  Wow, you are awesome!  Well,  you're awesome if this works.   :D   Haha, just kidding.  Thank you for  all your help, all of you.  I've bookmarked this page, copied down what I  need to do, and am just about to start doing it.  I have no further  questions, and I'll see you back here in a few hours to let you know it  worked.  :)

Thanks again!  See ya soon!
______________________________________________

EDIT:  Cool!  I don't even have to keep a local copy of this thread.  I just got an email with your entire reply in one message.  I can read that from my phone if necessary.  Sweet, thanks again!

---

### Post by #&amp;thj^% on 2021-11-29
> **unknowable said:**
> Hm.  Disks says that sda1 (/boot/efi) **is **an EFI type partition, and that it's FAT32.  Do I really need to reinstall?


I would just to be safe.
> **unknowable said:**
>    Would it be possible, since it's just the user directory, to use  something like KDE Partition Manager to just copy the home directory's  partition onto a USB HDD, then reinstall eOS, then just copy the home  directory's partition back over what I installed?
If you follow my suggestions all should be good.
If it's just the data, like Pictures Documents Videos yada yada just plug a usb/in **_ext4 format_** large enough to hold what you have in your now /Home just copy it to that.

---

### Post by unknowable on 2021-11-29
> **1fallen said:**
> If it's just the data, like Pictures Documents Videos yada yada just plug a usb/in **_ext4 format_** large enough to hold what you have in your now /Home just copy it to that.
 
Hm,  ok.  All my programs are installed to the home directory, as the boot  partitions are less than a GB combined.  No big deal though.  I'll work  it out.  I'll probably just move all of my media to another USB drive  without copying the entire partition, then copy just the home partition  (without all the extra media files, like a TB,) to another drive.   That'll take a little longer, but then I only have to copy like I dunno,  maybe a GB or two?  Ok, I know what I need to do.  I'm on it now.   Thanks again for all your help and encouragement.  I'll update this  thread when I get finished.  Later!

---

### Post by #&amp;thj^% on 2021-11-29
Are you sure "programs are installed to the home directory,"??
as for the size of your /boot>>>sounds about right.
```
df -h
Filesystem      Size  Used Avail Use% Mounted on
dev             5.8G     0  5.8G   0% /dev
run             5.8G  1.8M  5.8G   1% /run
/dev/sda4       407G   29G  358G   8% /
tmpfs           5.8G     0  5.8G   0% /dev/shm
tmpfs           5.8G  7.7M  5.8G   1% /tmp
/dev/sda1       [COLOR="#FF0000"]511M  4.6M  507M   1% /boot/efi[/COLOR]
tmpfs           1.2G   92K  1.2G   1% /run/user/1000

```.

---

### Post by unknowable on 2021-11-29
> **1fallen said:**
> In addition you may have to restore ownership of your home directory.

```
sudo chown -R username.username /home/username
```

Hm.  My username is unknowable.  Does that mean the command should be:

```
sudo chown -R unknowable.unknowable /home/unknowable
```

Is that close?  I'm moving all of the media to another drive right now, then I'll move just (much smaller) home directory to another drive.  Is that the right command to retake ownership of the home directory?

---

### Post by #&amp;thj^% on 2021-11-29
Yes Sir. And you might not need to, we'll just have to see your finished results.

---

### Post by unknowable on 2021-11-29
> **1fallen said:**
> Are you sure "programs are installed to the home directory,"??
as for the size of your /boot>>>sounds about right.
```
df -h
Filesystem      Size  Used Avail Use% Mounted on
dev             5.8G     0  5.8G   0% /dev
run             5.8G  1.8M  5.8G   1% /run
/dev/sda4       407G   29G  358G   8% /
tmpfs           5.8G     0  5.8G   0% /dev/shm
tmpfs           5.8G  7.7M  5.8G   1% /tmp
/dev/sda1       [COLOR=#FF0000]511M  4.6M  507M   1% /boot/efi[/COLOR]
tmpfs           1.2G   92K  1.2G   1% /run/user/1000

```.

Yes, I'm pretty sure that's right.  /dev/sda1 and /sda2 are the boot partitions, and sda3 is my encrypted LUKS partition where the home directory resides, although it's not listed by the command you just taught me:

```
unknowable@Elite8300:~$ df -h
df: /run/user/1000/doc: Operation not permitted
Filesystem             Size  Used Avail Use% Mounted on
udev                   6.8G     0  6.8G   0% /dev
tmpfs                  1.4G  2.1M  1.4G   1% /run
/dev/mapper/data-root  912G  834G   32G  97% /
tmpfs                  6.8G  1.5M  6.8G   1% /dev/shm
tmpfs                  5.0M  4.0K  5.0M   1% /run/lock
tmpfs                  6.8G     0  6.8G   0% /sys/fs/cgroup
/dev/loop1              56M   56M     0 100% /snap/core18/2253
/dev/loop3             2.4M  2.4M     0 100% /snap/irfanview/30
/dev/loop2              66M   66M     0 100% /snap/gtk-common-themes/1519
/dev/loop5              56M   56M     0 100% /snap/core18/2246
/dev/loop0             165M  165M     0 100% /snap/gnome-3-28-1804/161
/dev/loop4             128K  128K     0 100% /snap/bare/5
/dev/loop6             3.2M  3.2M     0 100% /snap/irfanview/48
/dev/loop7              33M   33M     0 100% /snap/snapd/13640
/dev/loop10             43M   43M     0 100% /snap/snapd/14066
/dev/loop9             323M  323M     0 100% /snap/wine-platform-6-stable/14
/dev/loop8             347M  347M     0 100% /snap/wine-platform-runtime/272
/dev/loop11            100M  100M     0 100% /snap/wine-platform-3-stable/14
/dev/loop12            347M  347M     0 100% /snap/wine-platform-runtime/271
/dev/sda2              457M  229M  195M  54% /boot
/dev/sda1              263M   37M  227M  14% /boot/efi
tmpfs                  1.4G   80K  1.4G   1% /run/user/1000
/dev/sdg1              982M  645M  338M  66% /media/unknowable/1_GB
/dev/sde1              7.7G   27M  7.6G   1% /media/unknowable/8GB
/dev/sdd1              6.0G  3.8G  2.3G  64% /media/unknowable/400GB
/dev/sdc1              2.7T  958G  1.7T  37% /media/unknowable/BACKUP
/dev/sdb4              200G   96M  200G   1% /media/unknowable/55893A4F71939806
/dev/sdb2              200G  144G   57G  72% /media/unknowable/B80A14810A143EB6
unknowable@Elite8300:~$ 
```

Oh, and if it matters, windows is on /sdb.  But yah, I'm pretty sure.  I guess I'll get to find out one way or the other.   :D

---

### Post by tea for one on 2021-11-30
> **unknowable said:**
> Hm.  Well I image the entire drive every night using Clonezilla, so I have some decent backups.  I don't know if I can just reinstall one partition though, my home directory.  I have some research to do
Yah, I think I was trying out Kubuntu when I installed elementary OS, so I was able to use Etcher.  I don't know what it does.  :D   Looks like I should just boot the Clonezilla USB iso and see if it will reinstall just one partition.  If it does, then I can reinstall eOS as EFI, and use Clonezilla to rebuild just the home directory's partition.  Hmm.
> Also, it doesn't look like Clonezilla can restore just one partition

Clonezilla will allow you to choose and restore one partition if you have chosen the correct option when cloning.

If you have cloned the entire drive, then you will not be able to choose an individual partition

Rather than [COLOR="#0000FF"]savedisk[/COLOR] - save disk as a local image
Try [COLOR="#0000FF"]saveparts[/COLOR] - save partitions as a local image

---

### Post by #&amp;thj^% on 2021-11-30
> **tea for one said:**
> Clonezilla will allow you to choose and restore one partition if you have chosen the correct option when cloning.

If you have cloned the entire drive, then you will not be able to choose an individual partition

Rather than [COLOR="#0000FF"]savedisk[/COLOR] - save disk as a local image
Try [COLOR="#0000FF"]saveparts[/COLOR] - save partitions as a local image

+1 and Agreed.
That's why we did this:
```
sudo tar -cvf /path/to/archive/backup.tar /home/username
```
Before OP re-installed the OS.

---

### Post by unknowable on 2021-11-30
Ok, I messed up - I'll tell you how later, after I fix this thing - and I had to reinstall *everything*.  Right now I'm trying to figure out how to get xrandr to use a resolution that it doesn't list, but it used earlier.  Don't worry about helping me right now, I am getting it, but I had to eventually check in and let you know a little about what's going on.  I do promise that when I get some free time I will update this thread like I promised, but as of now I've been working on the issue since like 2:30 this morning, and it's 5:30 PM right now.

On a side note, yes, reinstalling worked for the reason I wanted it to!  Now GRUB loads up automatically on bootup and elementary OS is the default choice.  I haven't set the timeout back down yet, nor have I gotten back into windows at all since I reinstalled.  It's an uphill battle, but I will get this done successfully.

One more time, thank you all for your help and guidance.  It's not going to waste, it's just taking time and effort getting things set up again.  More detail later, I promise.

---

### Post by oldfred on 2021-11-30
One of the regulars who posts, says if it takes more than an hour or two, better to just reinstall & restore from backups.
Of course he also wants everyone to have good backups and if LVM with encryption, you must have really good backups.
theFu on another LVM issue:
[https://ubuntuforums.org/showthread.php?t=2469475&p=14069404#post14069404](https://ubuntuforums.org/showthread.php?t=2469475&p=14069404#post14069404)

---

### Post by unknowable on 2021-11-30
> **oldfred said:**
> One of the regulars who posts, says if it takes more than an hour or two, better to just reinstall & restore from backups.

Yah, I can see the wisdom in that.  I screwed up though, and that's why I had to start from fresh.  Here's what happened:  I keep like 800 GB of media on my machine at all times, so my home directory was stuffed to the max yesterday.  I've got a few external HDD's that I can back up to, so I just figured I'd *move* (not copy) all of my media out to the other drives.  That way I could copy the home directory in a much smaller state.  It would be way faster to backup as well as restore, so it only seemed natural to do that.  Well, moving 7-800GB over USB 2.0 and 3.0 connections takes hours, and I had already been up for 24 hours by last night so I just started the last move and went to sleep.  Woke up around 2:30 AM and all the files were moved.  I was ecstatic - that means I'm ready to backup home directory, reinstall, and restore home - should be just as easy as we talked about last night, right?  Well I noticed that my home directory came to a total of right around 10GB!  I thought wow, great, I can just *copy* the home directory to another drive and reinstall.  No big deal that I wasn't tarring it up like you suggested, or so I thought.

So I reinstalled, and then I thought that just to be sure that I had permission to do it I should either create another user and login as them, or just boot from a thumb drive with Linux on it so that I could see the filesystem.  So that's what I did.  Of course I had Show Hidden Files turned on, as I always have in windows, so it's a natural step to show everything here in Linux.  Copied the entire home directory to another drive and reinstalled.  Still all good, right?  Downloaded a Kubuntu iso after installation of eOS and booted to that.  Since I didn't tar up the files, all I had to do was just open a graphical file manager and move the home directory back to its place in /home/.  That went smoothly, so I completely replaced the newly installed home directory with the one I backed up.  Still good, right?  I booted into Ubuntu without having to use the Boot Menu, so that issue was immediately resolved - glad the thing I wanted the most was fixed.  So the Pantheon login screen comes up (Pantheon is the window manager that elementary OS 6 Odin uses) with my username in place, waiting for my password.  I type in my password, the screen goes blank for a few seconds, then I'm back at the login screen.  Hmm.  That's not good.  Tried it again, same results.  Then I tried a *different* password, and then the login window just shook "no" at me instead of going to a blank screen.  Hm.  That indicates that it knows that I have the correct password, but something's not right.  When I use the wrong password, it just tells me immediately.  Shoot.

I didn't know what else to do, so I reinstalled *again*, deciding to keep the stock home directory and just configure everything by hand.  I've kept pretty clear notes on everything I've done to the system since I started learning this OS, so I knew what to do and how to do it up to the point that I was at before I reinstalled.  So I knew it would be a lot of work to do it, but I still had all my media files and most of my downloaded Linux apps on the HDD, so not *really* a major issue.  My thought was, at least this time I can do everything the way I want it the first time around, so I won't have a bunch of junk files that I didn't want after all installed - I've done this before, so I knew what I wanted and how to do it.  Bummer that I started over from scratch, but I couldn't just restore an old image, because then I wouldn't have resolved the issue of having to go into the Boot Menu every time just to get into my favorite OS.  So I'm keeping what I have, and configuring it until it's right.

I did figure out what I did wrong though, other than not tarring up the files and just restoring the tar file.  If I had done that, it would probably have worked out easily, just like we talked about yesterday.  The step I missed that probably screwed up everything was this:  when I booted to the Kubuntu iso so that I could restore my home directory, _**I forgot to turn on Show Hidden Files**_.  In other words, all the directories that had useful system configuration stuff in them didn't get restored.  Dangit.  Again, if I had just done what you told me to do - tar up the home directory and restore it later - it would have worked fine, I'm sure.  It only makes sense.  Obviously, however, I did not do that.  Even if I had turned on Hidden Files it probably would have worked out properly.

Oh well.  Lesson learned.  Never try to be smarter than the expert telling you how to fix something.   :D

The other thing that's kept me busy all day is this:  my old video cable was going out so I ordered a couple of new ones from amazon.  They showed up this afternoon so I immediately installed one.  When I did that, Ubuntu suddenly didn't know what monitor I had hooked up so it set the max resolution at 1024*768 (instead of 1920*1080.)  I spent a long time trying to fix it, and I learned a dang lot more than one person needs to know about forcing resolution at the command line.  :p   BTW, here's [the page on xrandr]("https://xorg-team.pages.debian.net/xorg/howto/use-xrandr.html"), the command line utility to force new video modes.  :D  Learned way more than I wanted to know about forcing unsupported video modes and so on.

Anyway, after like 5 hours of trying to get the new cables to work, I finally just pulled my old cable out of the trash and plugged it back in - no reboot, no logging off, nothing - just plugged it in while the system was running, which shouldn't be a big deal (for a video cable anyway).  All my video issues suddenly went away - Ubuntu immediately saw my monitor and video card, set it back to the right resolution and refresh rate, and I didn't even have to do anything.  It just started working when I plugged in the old cable.

So anyway, that's where I am right now - reinstalling all my favorite apps and reconfiguring everything from each individual program, to the wallpaper, my cursors, the dock preferences, everything.  Like I said though, this time I know a little more about what I'm doing, and it is getting done much faster.  Like I got my wifi setup in like half an hour, and before it was either impossible or took a few days.  Now I've got it down to a science, so it's just putting everything back together the way I like it.

So thanks again for all your help - most of it isn't going to waste.   :D   I did notate how to tar up and restore the home directory, I just didn't follow it ***this time***.  Hopefully I'll not need to do this again for a very long time, and if I have any luck at all I'll get through it a lot quicker (and more successfully) the next time I do.
______________________________________________

EDIT:  Oh yah, I haven't even *tried* to boot into windows all day.  GRUB doesn't see the windows partition even after using *sudo update-grub*, maybe because it's on another physical drive.  Oh well, I'm sure it will all come together eventually.  :D

---

### Post by oldfred on 2021-11-30
Main reasons grub does not see Windows is that it is hibernated. Windows turns hibernation back on with updates, so first check that. If Windows on separate drive, you should be able to directly boot from UEFI boot menu.

Or You have Windows installed in UEFI mode & Elementary in BIOS boot mode. Those are not compatible. Once you start booting in one mode, you cannot switch. Or grub cannot find another install in different boot mode.

I prefer rsync, tar is considered old school. 
Rsync is really just for a copy, but I have many copies on flash drives and different systems. And most critical data (grandkids photos) are also archived onto DVDs.

---

### Post by unknowable on 2021-12-01
> **oldfred said:**
> Main reasons grub does not see Windows is that it is hibernated. Windows turns hibernation back on with updates, so first check that. If Windows on separate drive, you should be able to directly boot from UEFI boot menu.

Ok I will, thanks.  It is on the second drive, /dev/sdb.  I can get into windows from the boot menu, I just want to keep the number of things I have to interact with before the OS is ready to a minimum - i.e., prefer not to mess with the boot menu if I can make it happen.

> **oldfred said:**
>  Or You have Windows installed in UEFI mode & Elementary in BIOS boot mode. Those are not compatible. Once you start booting in one mode, you cannot switch. Or grub cannot find another install in different boot mode.

eOS ***was*** in BIOS mode, so I reinstalled it last night.  It's now booting in UEFI mode, andI can get to it without doing anything but entering passwords.  Default boot item from the BIOS, default OS listed in GRUB.

> **oldfred said:**
>  I prefer rsync, tar is considered old school. 
Rsync is really just for a copy, but I have many copies on flash drives and different systems. And most critical data (grandkids photos) are also archived onto DVDs.

Heh.  Grandkids.  :D   It still sounds "old" to me, but I've got 2 grandkids myself.   :D  Yah, everything important gets backed up to at least one external HDD, so no real issue there.  Thanks for the heads up though.

---

### Post by unknowable on 2021-12-01
For those of you joining us late in the game, I previously had Windows  10 installed to /dev/sdb and elementary OS (based on Ubuntu 20.04 LTS)  installed to /dev/sda.  The issue that I was trying to solve was simply  to get both windows and eOS to be able to be seen by GRUB so that I  don't have to go through the BIOS Boot Menu every time I want to use one  or the other OS.  I had installed eOS first, then windows.  I was tired  of dealing with the Boot Menu, so came here for help and found that I  needed to reinstall elementary in order to make it UEFI bootable.  Last  night I reinstalled elementary and was very happy that it booted  automatically with no interaction from me, short of putting in my  passwords.  Unfortunately when I reinstalled eOS, it seemed to break  windows somehow and I couldn't boot into it, even using the Boot Menu.   Obviously since elementary was now working properly the best solution  was simply to reinstall windows to /sdb, right?

I reinstalled  windows 10 just now, and now elementary OS will not boot unless I use  the Boot Menu.  Along the way of installing windows, I found somewhere  that it seems to change the bootup of your primary drive, even Linux, by  adding something to the EFI directory (I think it was, I'll search for  it later.)  Which means that now, windows boots automatically and I'm  right back where I was yesterday, having to use the Boot Menu to get  into eOS.  That's no good.  I just reinstalled from nothing to fix that  issue.   :p   So I'm thinking my next good step is to search the hard  drive for anything containing "Microsoft" (should be easy since win10 is  installed to /sdb) and see what it modified to make my Ubuntu partition  now BIOS bootable only.

A mess it looks like, but I think I  might be able to figure it out.  That being said, since I just  reinstalled windows I'm going to spend tonight setting that up and I'll  be back in Linux tomorrow, searching for M$.  If you have any knowledge  on this sort of issue or how Microsoft modifies even Linux partitions,  please chime in and give me a hint.  :D   Once again, your contribution  is greatly appreciated and **will** be notated in my  instructions for setting up eOS properly.  Thank you for your time, even  if all you did was read this.  Have a good day.  :)
__________________________________________-

EDIT: Wow!  I said I was going to wait until tomorrow, but I couldn't resist one quick search.  I opened up Files as root, went to the root of the drive ( / ), and searched for "Microsoft".  I found almost 6,800 entries!  In my Linux partition!  Windows isn't even on this drive, it's on /sdb which should have nothing to do with Ubuntu.  That must be why my system stopped autostarting into Linux.

Anyway, with almost 6,800 entries this will definitely have to wait until tomorrow.  Once again though, if you have any clues about where to go first, I'd appreciate it.

---

### Post by unknowable on 2021-12-01
Wow, ok.  I've been working on this issue day and night for a while now  (many of you have, thanks again!) and I think I'm really close to  getting it resolved.  I finally got around to an Advanced Google search  that showed me that this has been a known issue with users who added  Windows 10 to their system, and it broke GRUB.  The solution I found  (sorry I've lost the actual site since then,) was basically just about  reinstalling and updating GRUB.  The instructions I found didn't work  with my setup exactly, as I have partitions for /EFI and /boot, along  with the root as another partition and the directions I found didn't  address that type of setup.

At any rate, as of right now, I can  let GRUB load up like it should (no Boot Menu!) and there are options  for eOS, Advanced elementary options, and one for Windows, and they all  work!  So it looks like (with all of your help) I've got my issue  resolved, and we shouldn't need to visit this anymore.  As a small  pointer, if anyone else comes in who can't boot right for pretty much  any reason, just have them *sudo update-grub* first, and if that  doesn't do it just reinstall GRUB to the boot partition *only*.  Took a  while to get all the commands right, as the directions I found were for  Ubuntu version 9 so they were outdated, but they got the general idea  across.

Anyway, that's pretty much it.  I'm about to mark this  issue resolved, and again I am so grateful to each of you for your  guidance and patience.  Take it easy today!

Thank you all again for guiding me in the right direction - I am so grateful to be up and running again.

---

### Post by #&amp;thj^% on 2021-12-01
Good Job unknowable, impressed with how quickly your grasping at so much information. :)
Cheers

---

### Post by unknowable on 2021-12-01
Oh, I found a thing that *really* helped me out, and it will probably help you to solve others' issues, too.  It's called the Boot Repair CD, and it's just an iso that you can burn to a thumb drive just like any other.  The instructions I found were a little dated, but I'm thinking this is probably one of the things that really helped resolve my issue.  There is no  "Recommended repair" anymore, but it's a pretty straightforward app.  You can find it on [SourceForge]("https://sourceforge.net/p/boot-repair-cd/home/Home/"), along with some outdated instructions.   :D



> **1fallen said:**
> Good Job unknowable, impressed with how quickly your grasping at so much information. :)
Cheers

Heh, wow, thanks for the compliment, 1fallen.  I'm pretty sure that it only *seems* fast to everyone else because I've been working on this issue basically night and day for a while now, either doing what you told me or Googling for more once I needed more.

Either way, thanks again for all your help, 1fallen!  You helped get me where I need to be.

---

### Post by yancek on 2021-12-01
If you are using Ubuntu or one of its derivatives installed or on a live usb, you can also get boot repair from the link below.  Best to use the 2nd option shown on that page to Create BootInfo Summary as it is more up to date than the other.

---

