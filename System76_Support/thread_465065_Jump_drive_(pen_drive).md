---
title: "Jump drive (pen drive)"
date: 2007-06-05
forum: System76 Support
---

### Post by riseringseeker on 2007-06-05
I very much appreciate the tip on how to flash the BIOS using a jump drive, or pen drive, if you prefer.  It worked great.

I now have a little problem though.  I was using the "My Flash" usb drive that I purchased with the Darter.  After I was done, I reformatted that usb drive using fdisk, and now the Darter sees it as a "Digital Audio Player", instead of a removable storage device.  It pops up with "sound-juicer" as the default application, instead of just opening the drive with a file browser.

Tom, I know you said that Carl has seen this behavior if one is running Amarok, but the desktop is also running Amarok, and it opens properly (as a removable drive in a file browser).

I believe it was something I did in reformatting that caused the Darter (and apparently **only** the Darter) to see it as a music player.  When I click on properties and the "drive" tab, it tells me the "Media:" is a "Digital Audio Player", yet when I put it in the Desktop computer, the same tab tells me it's a "Removable Hard Drive".

Is there something in fstab, or mtab I need to edit to have it open with a file browser?

---

### Post by thomasaaron on 2007-06-05
I've been researching this, and the answer is just not 'forthcoming'.

Carl's darter pulls up rythmbox, I've heard of one that pulls up amarok, and yours pulls up sound juicer. It's got to be a configuration setting, but we're not sure what the quick answer is.

Can you post the results of /etc/fstab and /etc/mtab?

Also, it might be worth it to try reformatting the drive again. I like to use gparted to delete all partitions and then rebuild the formatting. It has some quirks though, so if you want me to talk you through it, give me a call.

---EDIT---
Actually, I just tried Carl's USB on my Darter, and it pulled up no applications other than Nautilus. So, that probably eliminates formatting as the problem.

---

### Post by thomasaaron on 2007-06-05
I may be way off on this, but it is almost as if the computer is mistaking the usb pen drive for the cdrom and opening an application specified in System > Preferences > Removable Media and Devices.

---

### Post by riseringseeker on 2007-06-05
> **thomasaaron said:**
> I've been researching this, and the answer is just not 'forthcoming'.

Carl's darter pulls up rythmbox, I've heard of one that pulls up amarok, and yours pulls up sound juicer. It's got to be a configuration setting, but we're not sure what the quick answer is.

Can you post the results of /etc/fstab and /etc/mtab?

No, but I can post the contents.  :p

```

/etc/fstab =

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=586c9167-91a0-4351-ad10-20be95f1953a /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda3
UUID=3e5fbeed-6226-42b6-9984-ac71724d9bd9 /data           ext3    defaults        0       2
# /dev/sda2
UUID=e0aeee44-ee0b-4da9-895c-d5b18c988438 /home           ext3    defaults        0       2
# /dev/sda4
UUID=2b6f8d85-5164-4eea-b4ca-cd869e27a46b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

```

```


/etc/mtab =

/dev/hda1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.20-16-generic/volatile tmpfs rw 0 0
/dev/hda3 /data ext3 rw 0 0
/dev/hda2 /home ext3 rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0

```

> Also, it might be worth it to try reformatting the drive again. I like to use gparted to delete all partitions and then rebuild the formatting. It has some quirks though, so if you want me to talk you through it, give me a call.

---EDIT---
Actually, I just tried Carl's USB on my Darter, and it pulled up no applications other than Nautilus. So, that probably eliminates formatting as the problem.

Yeah, usb jump drive shows in nautilus on the decktop here, so I've got to think it's something in fstab, mtab, or maybe some file I am not aware of.

---

### Post by riseringseeker on 2007-06-06
> **thomasaaron said:**
> 
Carl's darter pulls up rythmbox, I've heard of one that pulls up amarok, and yours pulls up sound juicer. It's got to be a configuration setting, but we're not sure what the quick answer is.

THAT configuration setting I believe is under System->Preferences->Removable Drives and Media->Multimedia.

The question remains though, why does the Darter show the jump drive as something other than a removable HD?  Look at Properties - Drive tab to see what it thinks the drive is.

---

### Post by thomasaaron on 2007-06-06
Properties for Carl's USB pen drive:

Type: Folder
Volume: Disk


What do you get when you put in a different USB pen drive?

---

### Post by riseringseeker on 2007-06-06
> **thomasaaron said:**
> Properties for Carl's USB pen drive:

Type: Folder
Volume: Disk


What do you get when you put in a different USB pen drive?

I'll tell you when I can borrow one.  Gave my last one to someone I setup Ubuntu for.

---

### Post by thomasaaron on 2007-06-07
OK, I've done some pretty in-depth research on this, including following a number of forum leads that did not pan out.

I've got a Darter that will identify a My Flash 4GB drive as an audio player, but it will not do this with Lexar 512MB drive.

I tried completely tearing down all partitions and re-partitioning both drives with vfat partitions.
This did NOT change the results.

This left three questions in my mind:
Does it have to do with the size of the drive?
Does it have to do with the drive's firmware?
Is it just a weird bug with Feisty?

SIZE:
I repartitioned the large drive to appear as a 500MB drive.
This changed nothing.

THUS FAR, I'm left thinking it is a bug with Ubuntu in which the HAL mistakes CERTAIN USB flash drive/firmware combinations for an audio player.

That said, probably the best next step (unless someone can come up with a configuration setting somewhere to fix it) is to file a bug report with Ubuntu. 

(And you can get it to stop pulling up a media player by going to System > Prefs > Removable Drives and Media. Select the multimedia tab and un-check 'play portable music and medai files when connected'.

---

### Post by dolson on 2007-06-08
There's already a bug open for this.. [https://launchpad.net/bugs/85424](https://launchpad.net/bugs/85424)

PLEASE comment there, confirm the bug, raise the severity.. This should not still be an issue many months later.

---

### Post by thomasaaron on 2007-06-08
That doesn't sound like the same bug.

It deals with problems un-mounting USB devices, not with USB devices being seen as audio players.

Perhaps the two are related, but are you sure you posted the correct bug report?

---

### Post by riseringseeker on 2007-06-09
> **thomasaaron said:**
> OK, I've done some pretty in-depth research on this, including following a number of forum leads that did not pan out.

I've got a Darter that will identify a My Flash 4GB drive as an audio player, but it will not do this with Lexar 512MB drive.

I tried completely tearing down all partitions and re-partitioning both drives with vfat partitions.
This did NOT change the results.

This left three questions in my mind:
Does it have to do with the size of the drive?
Does it have to do with the drive's firmware?
Is it just a weird bug with Feisty?

SIZE:
I repartitioned the large drive to appear as a 500MB drive.
This changed nothing.

THUS FAR, I'm left thinking it is a bug with Ubuntu in which the HAL mistakes CERTAIN USB flash drive/firmware combinations for an audio player.

That said, probably the best next step (unless someone can come up with a configuration setting somewhere to fix it) is to file a bug report with Ubuntu. 

(And you can get it to stop pulling up a media player by going to System > Prefs > Removable Drives and Media. Select the multimedia tab and un-check 'play portable music and medai files when connected'.

What I think is even weirder is that before using it to flash the bios on the Darter, it did not see it as a Media Player, and the desktop still opens it with Nautilus instead of a music program.

---

### Post by thomasaaron on 2007-06-11
That is interesting.
However, I've now found the same problem on a Gazelle.
So, it is not specific to the Darter.

I'm feeling more comfortable that the problem is at the Ubuntu level.

---

### Post by riseringseeker on 2007-06-12
> **thomasaaron said:**
> That is interesting.
However, I've now found the same problem on a Gazelle.
So, it is not specific to the Darter.

I'm feeling more comfortable that the problem is at the Ubuntu level.

I can buy it's a Ubuntu problem rather than a Darter/System76 problem.  The reason I posted it here instead of on a "higher level" forum is because it did not open as a Music device prior to using it to flash the BIOS.  I will get hold of another jump drive this evening, and I will bet it opens with Nautilus, rather than the music player De 'Jour.  

The "My Flash" I bought with the Darter (and used to flash the BIOS) opens in Nautilus on another Ubuntu machine, so I've got to think that something went awry in the formatting of the stick, and when I reformatted it, something in HAL/fstab/mtab on the Darter got set to show it as a music device.  I'll keep poking around and let you know.

Now, if I can just get the remote access thing working properly - I'll post the error message(s) I get on that thread.

---

### Post by thomasaaron on 2007-06-12
Yeah, let me know what you find.

Just a note: The gazelle that does the same thing has never had its BIOS flashed, and I tested both the Darter and Gazelle with a pen drive that had NEVER been made bootable.

------------------

and I think I might have figured out the remote access issue. Check that thread.

---

### Post by riseringseeker on 2007-06-13
> **thomasaaron said:**
> Yeah, let me know what you find.

Just a note: The gazelle that does the same thing has never had its BIOS flashed, and I tested both the Darter and Gazelle with a pen drive that had NEVER been made bootable.

------------------

and I think I might have figured out the remote access issue. Check that thread.

Out of curiosity I booted off a the live CD, and put the "My Flash" in.  It came up just like it does on my desktop - in Nautilus.  I also was able to borrow another (smaller) jump drive last night, and put it in the Darter.  It too came up just like I think it should, with nautilus.

Given the Darter recognizes it as a removable storage device, rather than as a music device using the live CD, it would seem that perhaps an update somewhere along the line caused the problem - but the fact that it comes up "properly" in the desktop, which is also current on updates negates this.

Guess I will just keep poking around.

---

### Post by riseringseeker on 2007-06-14
Well, I have it opening in nautilus.  I just "unclicked" the setting in System->Preferences->Removable Disks and Media->Multimedia->Portable Music Players.

Of course this does not explain why Ubuntu showed it as a Media Player instead of a jump drive in the first place - and only after I had formetted to flash the BIOS, but at least it's doing what I want it to.

I am tempted to reformat it using XP and see what happens, if anything.

---

### Post by thomasaaron on 2007-06-14
I'd be interested in knowing what effect that would have. (I don't have XP, so the ball's in your court ;) )

---

