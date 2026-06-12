---
title: "HowTo: Transfer your bootable Ubuntu installation between hard drives"
date: 2007-11-01
forum: Tutorials
---

### Post by Old Pink on 2007-11-01
Maybe you're moving to a bigger/faster/quieter hard drive. Or just want a complete backup. Or maybe you're cloning systems in order to get closer to world domination, it doesn't matter. This is a guide to clone the contents of one hard drive to another.

Basically, use dd to clone your hard drive. **The hard drive/partition you are cloning to will need to be formatted first**. It's recommended you dd to an identical partition for optimal results. If you're upgrading to a larger hard drive, create a partition the same size as the old partition first, follow this guide then use the Live CD to resize the new partition. It is possible to dd a smaller partition into a larger partition, but results differ.

** If you can get both plugged in at the same time** (maybe you have two internal slots, or an internal slot and an external hard drive case) then it's simply a case of finding the two in /dev and running ```
sudo dd if=FROM of=TO
```(say you found hda1, which must be copied to sda1)```
sudo dd if=/dev/hda1 of=/dev/sda1
``` and await finish. Now move on to "then" 

**If you can only mount one at a time, **you'll need to dd to an image, and then dd to the next hard drive.```
sudo dd if=FROM of=/location/of/image/save/file.raw
```and then```
sudo dd if=/location/of/image/save/file.raw of=TO
```so say you had sda1, which was going onto another hard drive. But before this you needed to make an image, as you had no way of mounting both. So you'll put the image in /home/user (assuming your username is user) you'd use:```
sudo dd if=/dev/sda1 of=/home/user/image.raw
```and you then dismounted sda1, inserted your new hard drive, which became /dev/sda1 instead. You'd then have to run```
sudo dd if=/home/user/image.raw of=/dev/sda1
```(this can be VERY slow if you're using an external hard drive connection, especially at USB 1.1) 

**Then** you have a clone of your hard drive. You need to boot from a Live CD with the clone in a computer in order to install/fix grub on the MBR. To do this:[LIST=1]
[*]Boot the live CD
[*]Wait for the GUI and use CTRL + ALT + F1 to get a a terminal
[*]Run ```
sudo grub
```
[*]Wait for a "grub>" prompt
[*]Enter ```
find /boot/grub/stage1
``` in order to locate the cloned hard drive. You'll get a result like hd(0,0) - REMEMBER THIS
[*]Enter ```
root RESULT
``` with RESULT being the result of the last action, the find. So if hd(0,0) was found, run ```
root hd(0,0)
```
[*]Now run ```
setup (hd0)
```regardless of the result you got in #5.
[*]Grub will complete the installation, you can use a ```
quit
``` command to exit the grub prompt, then ```
sudo shutdown -r now
``` to reboot (make sure you eject Live CD at reboot to boot from new hard drive)[/LIST]**Now, **your system may boot fine, it will certainly process grub OK and get to your Ubuntu loading splash. Chances are though in all the dd'ing, you'll have hurt the image a little, and maybe gotten a few sectors broken on the way. If this is the case, you hard drive will try to force a scan. Usually these fail, and you are told to run fsck yourself, and given a root terminal. If this should happen, merely run```
fsck
```and answer all questions. If you don't know the answer, hit return/enter to accept the default answer. fsck should complete fairly quickly and leave you with a healed, bootable hard drive. Just use CTRL + D to reboot after fsck has succesfully completed. 

**Enjoy your new hard drive! **(of course, now it's bootable, you may choose to move it elsewhere, or store it safely if it's just a back up. The old one will work just the same, as if nothing had happened) 

**Variations of this: **(will be updated often) 

If you're going out, and want to leave dd copying your stuff around while you go, you can set your computer to shut down afterwards. sudo only lasts 15 minutes, so to do this you'll need a root terminal. Simply open a normal terminal and type```
sudo su
```and enter password at prompt. Then use, in the root terminal ```
dd if=FROM of=TO && shutdown -h now
```having read above for FROM and TO information, and your system will complete the dd and go to shutdown with a "halt" - you'll return to a copied hard drive and a nicely shutdown system.

---

### Post by ManInTheLake on 2007-11-03
A couple points:

In the last example, where it uses the "dev" command I think you mean dd.

Be very careful with dd.  Make sure the "if=" and "of=" files are pointing at the correct partitions.  dd will cheerfully overwrite partitions without warning.

If there's any chance of errors on your disk, use the noerror and sync flags on dd.  For example,
[INDENT]
   dd noerror sync if=/dev/hda1 of=/dev/sda1
[/INDENT]

Another way to copy a data from one partition to somewhere else is "cp -a".  This works on mounted file systems, not raw partitions.  For "cp -a" to work, the target partition must already have a file system on it.  Assuming we want to copy from /mnt/hda1 to /mnt/sda2,
[INDENT]
  cp -av /mnt/hda1/* /mnt/sda2
[/INDENT]
The v flag causes cp to list all the files as it copies them.

---

### Post by Old Pink on 2007-11-03
Thanks, fixed the "dev" thing, was tired and wrote this quickly.

Also, the "cp" command is great for some things but for this I'd recommend dd. You can't guarantee it will be bootable, certain things (like /dev /mnt /tmp and /media) can get in the way, file permissions aren't kept, not everything can be moved whilst in use and lots of files can get confusing. dd makes the move alot more simple.

---

### Post by coffeecat on 2007-11-03
> **Old Pink said:**
> Also, the "cp" command 

<snip>

file permissions aren't kept

Actually, they are, so long as you use the -a flag as ManInTheLake says. I've used cp several times to clone/move whole partitions and it has always worked.

> **Old Pink said:**
> not everything can be moved whilst in use and lots of files can get confusing.

Agreed for the first part. It's best to cp a mounted partition from another distro on another partition or from a live CD. As for getting confusing? Just issue the cp command and go and have a coffee. You don't have to watch the terminal output. :wink:

---

### Post by Old Pink on 2007-11-03
> **coffeecat said:**
> Agreed for the first part. It's best to cp a mounted partition from another distro on another partition or from a live CD. As for getting confusing? Just issue the cp command and go and have a coffee. You don't have to watch the terminal output. :wink:

True, but you agreed with not everything being available for copy while in use. Then you have to sift through and find what didn't copy. And it's just generally less neat than keeping everything concealed in one image with dd. 

Whatever, it's personal preference. This is dd specific, and people are offered cp as an alternative when they scroll to the replies. I may add it to "variations" at a later date :)

---

### Post by coffeecat on 2007-11-04
You mention everything in one neat image - or words to that effect. Have you tried using tar? That's my preferred method for archiving/cloning/copying partitions now. As you say - one image, and a nicely compressed one too.

There is one problem - Ubuntu's use of UUIDs in fstab. Of course, they will have changed if you've moved your installation from one HD to another using tar or cp, so you have to edit fstab. I've never used dd. Is the UUID preserved or is this something you need to add to your howto?

---

### Post by Old Pink on 2007-11-04
In my experiences with using dd, the UUIDs are preserved, yes. 

Remember, with using tar, not everything can be copied if in use, and you need to to trigger it into keeping file permissions, and avoid certain folders being archived (such as /mnt, /tmp and /proc), and of course, you have to extract everything as soon as it's archived, what a hassle! 

But yes, there is some element of personal preference. dd just worked perfectly for me, and was very fast and efficient, with absolutely no flaws (most of the time I don't even get prompted to fsck after) and I thought I'd share my method.

---

### Post by agurk on 2007-11-04
While it's pretty cool that you can do these things from the command line, I'd still like to recommend the excellent [GParted LiveCD](http://gparted-livecd.tuxfamily.org).

---

### Post by Old Pink on 2007-11-07
> **agurk said:**
> While it's pretty cool that you can do these things from the command line, I'd still like to recommend the excellent [GParted LiveCD]("http://gparted-livecd.tuxfamily.org").Why spend ages downloading and burning the CD image, not to mention booting in RAM from a CD, just to copy the image, when, as the website [says]("http://gparted.sourceforge.net/features.php#copy") > The actual copy is performed by 'dd'.meaning it's the same function, you just waste an unnecessary half hour plus getting a slow GUI up? Follow my guide, quicker, easier, makes much more sense.

---

### Post by agurk on 2007-11-08
I'm not knocking your nice how-to, it's just that with age I've come to appreciate the simplicity of point-and-click, not having to memorize or print a list of cli commands. Each to his own, I guess.

---

### Post by hydraconsole on 2008-01-20
can i dd a windows partition? lets say the entire windows drive c:?

---

### Post by AlanRogers on 2008-01-21
ASAIK, *dd* copies block by block from one drive or partition to another. It doesn't care about operating system or even file system so yes, you should be able to use it on Windows as well.
 
You should bear two things in mind though:
[LIST=1]
[*]*dd* is a Linux utility, so you can't install it on Windows. You'll need to boot to a Linux Live CD on the Windows machine in order to use it.
[*]*dd* prefers to copy to a partition with similar attributes as the one it's copying from; size, etc.[/LIST]In closing, dare I remind you to make sure you've got a good backup of your important Windows data before you start this?

---

### Post by dbqp on 2008-01-28
>  If you can get both plugged in at the same time (maybe you have two internal slots, or an internal slot and an external hard drive case) then it's simply a case of finding the two in /dev and running
Code:

sudo dd if=FROM of=TO

(say you found hda1, which must be copied to sda1)
Code:

sudo dd if=/dev/hda1 of=/dev/sda1

and await finish. Now move on to "then"


This really goes out to anyone, not just the OP. What if you had a particular folder you wanted this backup to be copied to? Such as...

sudo dd if=/dev/hda1 of=/dev/sda1/FOLDERNAME

If it is mounted as /dev/sda1, but the location is actually:  /media/MYBOOK/server-bu

:confused:

---

### Post by dbqp on 2008-01-28
> **dbqp said:**
> This really goes out to anyone, not just the OP. What if you had a particular folder you wanted this backup to be copied to? Such as...

sudo dd if=/dev/hda1 of=/dev/sda1/FOLDERNAME

If it is mounted as /dev/sda1, but the location is actually:  /media/MYBOOK/server-bu

:confused:

Okay, maybe I asked too quickly without reading through...

It appears I need to write to:

sudo dd if=/dev/hda1 of=/MYBOOK/server-bu/file.raw

???

The 'file.raw' is what I need confirmed. Do I name it this exactly or can I name it JAN282008.raw - do I need the raw extension?

Also, there was mention of overwriting partitions...By writing to this particular location and giving it a file name it restricts it from creating a partition and just backs up data? I don't want to overwrite my external MyBook with 300GB+

---

### Post by dbqp on 2008-01-29
^bump

---

### Post by funkelauge on 2008-03-02
Hey Old Pink!

Just wanted to say thank you very MUCH!!! :)

Because of experienced guys like you sharing their knowledge its possible to make ubuntu even more user-friendly!

Thanks again,

David

---

### Post by linfidel on 2008-04-20
I've had some experience moving partitions around, and thought I'd add a few points.

First, using dd is fine, no problems with that, although I thought there was an issue with how many bytes/blocks to copy at a time (bs = size).  That mainly affects speed, though, IIRC.  Anyway, I believe you can run gparted from ubuntu itself, and copy/paste a partition, if you have both drives available.

But, the main thing I wanted to add is that if you are adding a drive rather than replacing it, you need to learn about UUIDs a little if you try to keep both drives at the same time.  You will need to change the UUID or delete the old partition.  If you need to assign a new UUID, use tune2fs with the -U option to assign a random UUID.  When I added a 2nd drive, and rearranged partitions, I learned all about this the hard way.  :)

---

### Post by flostre on 2008-04-29
Is it possible to use, say, if=/dev/hda of=/dev/hdb (instead of "if=/dev/hda1 of=/dev/hdb1" to "if=/dev/hdaN of=/dev/hdbN")? Would save the partioning step and you could just issue one command, go to bed and wake up with a new complete harddrive.

flostre

---

### Post by scorp123 on 2008-05-07
> **Old Pink said:**
>  Remember, with using tar, not everything can be copied if in use  Not exactly 100% true. "tar" will happily copy whatever it finds on the filesystem. The problem is if e.g. a program is still active and still writing files, it could be that "tar" catches only the last version before the write operation. Workaround: temporarily stop the program in question and let "tar" do its job.

As for "cp" not catching everything ... There are better alternatives such as "rsync". Feed it with the right parameters and it will happily copy everything incl. the right permissions, e.g. ```
rsync -av /path/to/local/dir user@remote:/path/to/remote/dir
```

> **Old Pink said:**
>  and you need to to trigger it into keeping file permissions, and avoid certain folders being archived (such as /mnt, /tmp and /proc), and of course, you have to extract everything as soon as it's archived, what a hassle!  Like with everything, you have to know what you do. :-)

> **Old Pink said:**
>  dd just worked perfectly for me, and was very fast and efficient, with absolutely no flaws (most of the time I don't even get prompted to fsck after) and I thought I'd share my method.  "dd" is OK for as long as you don't care about copying gigabytes and gigabytes of even unused disk space. And "dd" is definitely not the fastest method. As soon as you have to do this over a network or between two harddisks with a very different geometry you'd be better off using something else.

But for locally attached disks ... OK.

---

### Post by a_rojilla on 2008-05-15
Sorry for the bump (and my poor english), but after a disk failure I'm looking forward to a good backup procedure and after reading this nice how-to I have a question...

So, once I have cloned the disks... should I clone them again and again or is there a way to update only modified files?

I mean some way to heve them sync and avoid to clone the whole disk when I all I want is to save the changes...

Thanks in advance for your time!

---

### Post by scorp123 on 2008-05-15
> **a_rojilla said:**
>  should I clone them again and again  Why? :confused:

> **a_rojilla said:**
>  or is there a way to update only modified files?  With methods such as "tar" and "rsync": yes. With "dd": Nope!

> **a_rojilla said:**
>  I mean some way to heve them sync and avoid to clone the whole disk when I all I want is to save the changes...  Use the "tar" method or use "rsync" then.

Read here ... maybe it's useful for your purposes - I once wrote this for the Linux Mint forums and this is how I have been doing backups for years now (in the office I use tape streamers etc. but basically it's still the same method as described here):

"How to backup your stuff UNIX-style"
[http://www.linuxmint.com/forum/viewtopic.php?f=42&t=3969&start=0&st=0&sk=t&sd=a](http://www.linuxmint.com/forum/viewtopic.php?f=42&t=3969&start=0&st=0&sk=t&sd=a)

---

### Post by flostre on 2008-05-20
> **flostre said:**
> Is it possible to use, say, if=/dev/hda of=/dev/hdb (instead of "if=/dev/hda1 of=/dev/hdb1" to "if=/dev/hdaN of=/dev/hdbN")?

It works (I just did it). You still have to enlarge your partition after dd is finished though.

flostre

---

### Post by KuroYoma on 2008-07-18
I am trying to transfer my Ubuntu Hardy Heron OS from my internal HD to my external HD.  I want the OS i tranfer to my External HD to be bootable from my external HD so i can plug it into any PC i wish and boot from USB Device and run my OS.

---

### Post by alphanaut on 2008-10-02
I would use Clonezilla Live :: [http://clonezilla.org](http://clonezilla.org)

---

### Post by Person98 on 2009-01-07
I was hoping to transfer my install to a usb key so i can have a bootable usb back-up of my computer, Is it possible to use this guide to dd from an 8 gig hard drive to an 8 gig usb stick? or if anyone has any other suggestions they would be appreciated greatly

---

### Post by ukripper on 2009-01-08
> **alphanaut said:**
> I would use Clonezilla Live :: [http://clonezilla.org](http://clonezilla.org)

+1. i already use it in conjuction with the rsync

---

### Post by kevinguillorytraining on 2009-10-09
hile it's pretty cool that you can do these things from the command line

---

### Post by AlexanderDGreat on 2009-12-19
Hi, I have 1 question, in this tutorial you said that you can transfer your bootable Ubuntu Installation between hard drives.

What if I want to transfer my old Ubuntu hard disk to my shiny new computer with a new hard disk? What about the dev, proc, sys, new motherboard, new processor, wouldn't the old Ubuntu OS overwrite the settings and files of the new Computer?

As far as I know, this is practically backing up your old harddisk and transferring it to a new one, together with the settings and files of the old.

So will this work for me?

Out of topic also, if I plainly attach an old hard disk to a NEW COMPUTER without hard disk, will that old hard disk boot and AUTO ADJUST to the new Computer? Or do I really need to follow your tutorial?

---

### Post by slgtheindividual on 2011-01-04
> **linfidel said:**
> I've had some experience moving partitions around, and thought I'd add a few points.

First, using dd is fine, no problems with that, although I thought there was an issue with how many bytes/blocks to copy at a time (bs = size).  That mainly affects speed, though, IIRC.  Anyway, I believe you can run gparted from ubuntu itself, and copy/paste a partition, if you have both drives available.

But, the main thing I wanted to add is that if you are adding a drive rather than replacing it, you need to learn about UUIDs a little if you try to keep both drives at the same time.  You will need to change the UUID or delete the old partition.  If you need to assign a new UUID, use tune2fs with the -U option to assign a random UUID.  When I added a 2nd drive, and rearranged partitions, I learned all about this the hard way.  :)

So if I wanted to copy the partition to a new hard drive then delete it from the old hard drive I wouldn't need to edit any UUID's? Can anybody give me any information on this? Also on how to check that the new partition is working and booting fine with a GRUB that works before deleting the old partition? Thank you very much in advance

---

### Post by bayvista on 2011-04-30
Had some fun with the 'dd'. Wanted to copy sdb8 (40gb) to sdb1. Using gparted I resized sdb1 and formatted. Then ran the following:

sudo dd if=/dev/sdb8 of=/dev/sdb1

Well, 90 minutes later with the disk light still flashing, I cancelled. Any ideas?

---

### Post by JohnMac on 2011-05-14
Thanks for your good Howto.I followed your procedure but, although I made a copy, I have not been able to get it to boot on its own.
I have a plug IDE drive the same size as my normal HDD and I am trying to make a bootable copy so I can be ready should my new Natty instal fails.
All goes well until I get to step 5)sudo grub. The response is "command not found" The copy HDD will boot as long as the normal HDD is there, but won't boot if I disconnect the main HDD. I get: error: out of disk. grub rescue.

My Boot Info Script (can't recall how to attach it) does show something not right with my Boot Sector info - "core.img cannot be found at this location"

My system: Desktop AMD Dual 5200 CPU, 2G RAM, Geforce N439GT graphics.
HDD: SATA 160G and IDE 160G removable.
Distro: Maverick

Any Hints?

---

### Post by Zookalicious on 2011-12-02
Might be worth mentioning, dd uses an incredibly small bit size by default, which makes the speed very very slow when copying. 

To fix this, specify a larger bit size. I use roughly 4 MB and that sped up the transfer by about 15 times!

```
sudo dd if=FROM of=TO bs=4194304
```Also, if you want to see the progress of dd once it has already started running, run the following command in a seperate terminal window:

```
watch -n 10 killall -USR1 dd
``` *Source: *[http://enhancedlinux.com/2010/07/11/check-the-status-of-dd-command/]("http://enhancedlinux.com/2010/07/11/check-the-status-of-dd-command/comment-page-1/#comment-428")

You'll now see when you switch back to the window / virtual terminal that dd is running in that it has started to output how much data it has transfered. Really useful.

---

### Post by Zookalicious on 2011-12-02
> **JohnMac said:**
> ... All goes well until I get to step 5)sudo grub. The response is "command not found" ...
Any Hints?

This guide is a bit old. Ubuntu no longer uses the old version of grub but now rather uses GRUB2. A very good guide on how to install grub2 from a liveCD is availible here: [http://www.webtechquery.com/index.php/2010/04/install-grub2-from-live-cd/](http://www.webtechquery.com/index.php/2010/04/install-grub2-from-live-cd/)

Hope it helps!

---

