---
title: "Wipe old HDD?"
date: 2009-07-17
forum: Security
---

### Post by mavis311 on 2009-07-17
Can anyone help me wipe an old HDD of mine.  I've put together a crappy system out of old components and I'm going to try and sell it.  Obviously, I wouldn't want anyone recovering any data off of that disk, so I'd like to wipe it pretty well.  

Is there a tool distributed with ubuntu that will help me do this?
If not, does anyone know of a good util?

I read something on another forum about the "dd" command...?

---

### Post by hansdown on 2009-07-17
Hi mavis311.

DBAN works wonders.

Could take some time, but it's worth it to be careful.

[http://www.dban.org/download](http://www.dban.org/download)

---

### Post by bodhi.zazen on 2009-07-17
You can simply over write teh drive with zeros using dd

dd if=/dev/zero of=/dev/sda

The idea that you need to over write the data multiple times has been de-bunked.


[Can Intelligence Agencies Read Overwritten Data?]("http://www.nber.org/sys-admin/overwritten-data-gutmann.html") 

[Overwriting Hard Drive Data « SANS Computer Forensics, Investigation, and Response]("http://sansforensics.wordpress.com/2009/01/15/overwriting-hard-drive-data/")

---

### Post by John.Michael.Kane on 2009-07-17
> **mavis311 said:**
> Can anyone help me wipe an old HDD of mine.  I've put together a crappy system out of old components and I'm going to try and sell it.  Obviously, I wouldn't want anyone recovering any data off of that disk, so I'd like to wipe it pretty well.  

Is there a tool distributed with ubuntu that will help me do this?
If not, does anyone know of a good util?

I read something on another forum about the "dd" command...?

The below may be of some help.
[HDDerase]("http://cmrr.ucsd.edu/people/Hughes/SecureErase.shtml")
[dban]("http://www.dban.org/")

The shred command from a live cd may work.
```
shred -vfz -n 2 /dev/hda
```

or

```
dd if=/dev/urandom of=/dev/hda
```

One, or Two write with zeros should be sufficient, however. You can edit the shred number to suit.

Edit: bodhi.zazen, answer covered the issue.

---

### Post by MontelEdwards on 2009-07-17
> **John.Michael.Kane said:**
> The below may be of some help.
[HDDerase]("http://cmrr.ucsd.edu/people/Hughes/SecureErase.shtml")
[dban]("http://www.dban.org/")

The shred command from a live cd may work.
```
shred -vfz -n 2 /dev/hda
```or

```
dd if=/dev/urandom of=/dev/hda
```One, or Two write with zeros should be sufficient, however. You can edit the shred number to suit.

Edit: bodhi.zazen, answer covered the issue.
Shred takes too damn long
just format the ****

umount the drive,
mkfs.(filesystem)
so for example, if my drive is

/dev/sdb1
i would do 
umount /dev/sdb1
and if i was the VFAT fs i would do 
mkfs.vfat /dev/sdb1
or mkfs.ext4 /dev/sdb1
whatever you want



edit: those a partitions btw,
check which yours it by doing fdisk -l


these commands alll have to either be done sudo or root :)

edit2: I am pretty sure that formating is the best you're going to get
shred just overwrites the data with a whole bunch of ****, you still have to rm it.

---

### Post by Agent ME on 2009-07-17
Formatting a drive doesn't securely erase the data that was on it. Files can still be recovered off of a drive that was simply formatted.

---

### Post by MontelEdwards on 2009-07-17
> **Agent ME said:**
> Formatting a drive doesn't securely erase the data that was on it. Files can still be recovered off of a drive that was simply formatted.
hmm, ok then

---

### Post by HermanAB on 2009-07-17
Howdy,

There is a secure erase function built into the drive controller of ALL hard disks.  You can activate it with hdparm.  This is the best way to erase a drive.

It is a two step process:

```
sudo hdparm --security-set-pass PWD /dev/sdb

sudo hdparm --security-erase PWD /dev/sdb
```

See the man page.

---

### Post by mavis311 on 2009-07-17
> **John.Michael.Kane said:**
> 
```
dd if=/dev/urandom of=/dev/hda
```One, or Two write with zeros should be sufficient, however. You can edit the shred number to suit.

> **bodhi.zazen said:**
> You can simply over write teh drive with zeros using dd

dd if=/dev/zero of=/dev/sda

First of all, thanks for being helpful, I truly appreciate it!  However, I'm still learning about linux... and I love to learn -- everything.  

I understand that /dev/[device] is how linux/unix handles devices such as media, but what exactly are /sda and /hda.  I'm not just going to issue these commands since the HDD I want to wipe will probably not be either of the devices listed in these example command lines.  I prefer to use the command line, but I'm still learning about the commands/utilities under linux.  So, how can I find out what device name the HDD I need to erase has been given by the kernel?

> **Agent ME said:**
> Formatting a drive doesn't securely erase the data that was on it. Files can still be recovered off of a drive that was simply formatted.

True.  At least under DOS & Windows anyway.  Formating just prepares the file table and leaves the actual data exactly as it is.  Also, if I remember correclty, under DOS, the first letter of the file name was simply replaced with a ? when one would "del somefile.ext" so file recovery is a pretty simple matter.

Also, does linux actually have an fdisk?

---

### Post by mavis311 on 2009-07-17
> **HermanAB said:**
> Howdy,

There is a secure erase function built into the drive controller of ALL hard disks.  You can activate it with hdparm.  This is the best way to erase a drive.

It is a two step process:

```
sudo hdparm --security-set-pass PWD /dev/sdb

sudo hdparm --security-erase PWD /dev/sdb
```See the man page.

yeah about that...  (from the man page for hdparm)

       ATA Security Feature Set

       These switches are DANGEROUS to experiment with,  and  [U]might  not  work
[/U]       _with every kernel._  USE AT YOUR OWN RISK.


[FONT=Courier New]       --security-set-pass PWD
              Lock  the  drive, using password PWD (Set Password) (DANGEROUS).
              Password is given as an ASCII string and is padded with NULs  to
              reach  32 bytes.  The applicable drive password is selected with
              the --user-master switch and the applicable security  mode  with
              the --security-mode switch.  No other flags are permitted on the
              command line with this one.  [U]THIS FEATURE  IS  EXPERIMENTAL  AND
[/U]              _NOT WELL TESTED. USE AT YOUR OWN RISK._[/FONT]

       --security-erase PWD
              Erase (locked) drive, using password PWD (DANGEROUS).   Password
              is  given as an ASCII string and is padded with NULs to reach 32
              bytes.  The applicable  drive  password  is  selected  with  the
              --user-master  switch.  No other flags are permitted on the com&#8208;
              mand line with this one.  [U]THIS FEATURE IS EXPERIMENTAL  AND  NOT
[/U]              _WELL TESTED. USE AT YOUR OWN RISK._

       The Linux kernel up until 2.6.12 (and probably  later)  doesn´t  handle
       the  security  unlock and disable commands gracefully and will segfault
       and in some cases even  panic.  The  security  commands  however  might
       indeed  have  been  executed  by  the drive. This poor kernel behaviour
       makes the PIO data security commands rather useless at the moment.



I'd really like to not buy another drive to sell with the system I've assembled, so since there is a risk that I could eff up my drive, I will not be using this option.  I will however, dig out an old drive that is of zero use to me and play with it.  Thanks.

---

### Post by bodhi.zazen on 2009-07-17
> **mavis311 said:**
> I understand that /dev/[device] is how linux/unix handles devices such as media, but what exactly are /sda and /hda.  I'm not just going to issue these commands since the HDD I want to wipe will probably not be either of the devices listed in these example command lines.  I prefer to use the command line, but I'm still learning about the commands/utilities under linux.  So, how can I find out what device name the HDD I need to erase has been given by the kernel?

NO - Do not issue those commands if you do not understand the devices, lol.

See if this helps :

[HowTo: Partitioning Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=282018")

---

### Post by bodhi.zazen on 2009-07-17
> **HermanAB said:**
> Howdy,

There is a secure erase function built into the drive controller of ALL hard disks.  You can activate it with hdparm.  This is the best way to erase a drive.

It is a two step process:

```
sudo hdparm --security-set-pass PWD /dev/sdb

sudo hdparm --security-erase PWD /dev/sdb
```See the man page.

Just curious,  is this any faster or more secure then dd ?

---

### Post by Dave_Connor on 2009-07-17
DD is secure, whiping large amounts of data take time. Heck there is a challenge for hardisks that have been whiped with zero's that hasen't been solved yet. So dd with /dev/zero is pretty much secure.

---

### Post by HermanAB on 2009-07-17
Howdy,

Data is written in tracks, but the data also bleeds into the areas between the tracks.  The drive controller can also remap bad sectors on the drive so that areas that contain some data, can become inaccessible to ordinary drive operations.  With special equipment, some information can be recovered from these areas.  

The Data Definition (dd) command will only overwrite the active tracks and sectors, because it uses the drive controller in the normal way.  Dd cannot overwrite bad sectors or areas between tracks.  The drive controller erase function triggered with hdparm, can overwrite everything, including bad sectors and the areas between the tracks.  It can do that because it *is* the drive controller after all.

Consequently, the best (and slowest) way to erase all data is by telling the drive controller with hdparm to erase the drive.

---

### Post by mavis311 on 2009-07-20
[SIZE=2]> **bodhi.zazen said:**
> [HowTo: Partitioning Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=282018")

UPDATE:

Thanks bodhi, that link helped me quite a bit.  I can never seem to find that sort of thing on my own 85% of the time!

I've been having a lot of hardware trouble with this issue.  At least now I understand how to go about what I was trying to accomplish.

dd is a great command.  Very simple to understand and easy to use.  Just what I'd use if I didn't already have a util installed.  Good to know.

Still not too sure about hdparm, going to have to play around with it before I'd ever use it on a drive I didn't intend to trash.  I'm not so concerned with making the drive completely unrecoverable, just want to trash the data enough so that it couldn't really be useful if anything was recovered.  (The HDD in question was in my parent's old computer and I don't have any idea what they had on there: financials, tax info, etc.)  I figure that if I muck it up just a bit, anything that could be recovered would most likely just be bits and pieces and pretty useless.

I never got a chance to try dban and the other utilities that were posted.  I preferred to do it manually if possible just so I can have the opportunity to learn more about linux.  That said, thanks to those that posted them, I'm sure I'll give them a try sometime in the near future.

I've learned a lot more about linux since I started this thread, and that was my main goal.  I'm in no hurry to get the HDD in the machine, as I won't be installing an OS... probably.  I though about some linux install, but maybe I'll leave that decision to the buyer -- or ebayer.  However, I probably won't be using the HDD I started this thread about -- all the problems I've been having with it seem to be due in large part to quite a few bad sectors scattered across the disks surfaces.  So after all that, I have to get another drive anyway :(.  Oh well.  [/SIZE] [FONT=Verdana][SIZE=2]Que será, será.  No?[/SIZE][/FONT]

---

### Post by tubbygweilo on 2009-07-20
> **mavis311 said:**
> 
...

I never got a chance to try dban and the other utilities that were posted.  I preferred to do it manually if possible just so I can have the opportunity to learn more about linux.  That said, thanks to those that posted them, I'm sure I'll give them a try sometime in the near future.
...

DBAN gives great CYA if selling disks on to others and if disposing of disks on behalf of others. Give it a go when you don't need it and I'm sure it will repay you when you need it for real.

---

### Post by JockVSJock on 2009-07-20
Can use [Ultimate Book Disk]("http://www.ultimatebootcd.com/").

I've used this a number of times to wipe a HD and it has a number of utilities to get the job done. 

thanks

---

### Post by Pitt Stains on 2009-07-25
> **John.Michael.Kane said:**
> 

The shred command from a live cd may work.
```
shred -vfz -n 2 /dev/hda
```

or

```
dd if=/dev/urandom of=/dev/hda
```

One, or Two write with zeros should be sufficient, however. You can edit the shred number to suit.


I've been testing this out for a presentation I'm giving in the near future (using an SD card mounted at /media/disk), and I'm getting very surprising results.

Using...
```

dd if=/dev/urandom of=/media/disk

```
... I'm still able to recover the data on the SD card using photorec.

Using...
```

dd if=/dev/urandom of=/dev/mmcblk0p1

```
... seems to make the data unrecoverable, but it also messes up the card and requires me to reformat it before I can use it again.  In my tests, reformatting the card alone is not sufficient to make the data unrecoverable.

If I learn anything else of interest, I'll post it here.

---

### Post by Jack99 on 2009-07-26
Is it not fair to say that you can never truly "Clean / Wipe " a Hard Drive , there will always be something left on it...:)

---

### Post by Pitt Stains on 2009-07-26
> **Pitt Stains said:**
> If I learn anything else of interest, I'll post it here.

I found that using this command...
```

shred -fvz -n 1 /dev/mmcblk0p1

```
... makes the data unrecoverable (at least by photorec) but it also requires that I reformat the SD card before it can be used again.

---

### Post by bodhi.zazen on 2009-07-26
Thank you for the follow up Pitt Stains. Yes, most of what you are doing writes data to the hd , overwriting both the data and the partition table. so yes you need to format the HD to re-use it.

It has been shown you can not recover the data if you write 0 to the HD with dd using /dev/zero

[Overwriting Hard Drive Data « SANS Computer Forensics, Investigation, and Response]("http://sansforensics.wordpress.com/2009/01/15/overwriting-hard-drive-data/") 

[Can Intelligence Agencies Read Overwritten Data?]("http://www.nber.org/sys-admin/overwritten-data-gutmann.html")

---

### Post by mavis311 on 2009-07-28
Someone on another thread ([http://ubuntuforums.org/showthread.php?t=1168110](http://ubuntuforums.org/showthread.php?t=1168110)) had mentioned, perhaps jokingly, thermite in regards to secure destruction of data.  Well, I just came across this entry on the hack-a-day blog complete with videos.  Probably a very secure way of completely destroying a harddrive and making it about as unrecoverable as possibly in a short a span of time as possible.  Of course, I just hope the people living above me never decide to use that method!

[http://hackaday.com/2008/09/16/how-to-thermite-based-hard-drive-anti-forensic-destruction/](http://hackaday.com/2008/09/16/how-to-thermite-based-hard-drive-anti-forensic-destruction/)

---

### Post by lyall on 2009-12-21
to wipe a hard drive clean of all data

get WipeDrive which costs. it writes 0 and 1 to all sectors and completely fills the sector with 0 and 1.  so that all data is over written. you have a choose of how many time ( 1,3 or 7)it will rewrite to the drive.

or you can get Boot n Nuke, it is free at the following web site
[http://www.dban.org/]("http://www.dban.org/")
it is as good as WipeDrive

both will write the data to DOD specs

You have to understand the hard drive first
the data on the platers are several layers thick, not one layer for the data to be written to, that is why you need to run Boot n Nuke or WipeDrive to 7 passes.  then if you really do not want anybody to recover any data you should run it again a two or three time at 7 passes

when you deleted the data or over write data to a hard drive the old data is in a lower level (deeper) on the plater and each time the data has been deleted or over write it goes deeper and so forth.

That is why you need it to rewrite several time to clean the hard drive, so the your old data gets buried so dept that it is so hard to get it back.

a 40gb hard drive will take over 4 hours to run 7 passes
and you run it again an other 4 hours

I have had to wipe hard drives, so that where I work can sell the the PC or Laptops to the general public. I have done hundreds if not thousands of hard drives over the years

to get the hard drive work again you need to fdisk then low level format the drive, then you can install an OS

I hope this info help you all

good luck and have fun leaning :)

---

### Post by bodhi.zazen on 2009-12-21
> **lyall said:**
> to wipe a hard drive clean of all data

get WipeDrive which costs. it writes 0 and 1 to all sectors and completely fills the sector with 0 and 1.  so that all data is over written. you have a choose of how many time ( 1,3 or 7)it will rewrite to the drive.

or you can get Boot n Nuke, it is free at the following web site
[http://www.dban.org/](http://www.dban.org/)
it is as good as WipeDrive

both will write the data to DOD specs

You have to understand the hard drive first
the data on the platers are several layers thick, not one layer for the data to be written to, that is why you need to run Boot n Nuke or WipeDrive to 7 passes.  then if you really do not want anybody to recover any data you should run it again a two or three time at 7 passes

when you deleted the data or over write data to a hard drive the old data is in a lower level (deeper) on the plater and each time the data has been deleted or over write it goes deeper and so forth.

That is why you need it to rewrite several time to clean the hard drive, so the your old data gets buried so dept that it is so hard to get it back.

a 40gb hard drive will take over 4 hours to run 7 passes
and you run it again an other 4 hours

I have had to wipe hard drives, so that where I work can sell the the PC or Laptops to the general public. I have done hundreds if not thousands of hard drives over the years

to get the hard drive work again you need to fdisk then low level format the drive, then you can install an OS

I hope this info help you all

good luck and have fun leaning :)

Your claims have been disproved =)

One write is sufficient, could be all 0, all 1, or random data.

[http://ubuntuforums.org/showpost.php?p=7681587&postcount=21](http://ubuntuforums.org/showpost.php?p=7681587&postcount=21)

---

