---
title: "retrieving data from 7 year old laptop HDD"
date: 2013-07-10
forum: The Cafe
---

### Post by su:bhatta on 2013-07-10
Dear All,

I used a laptop from 2006-2010, it had a 2.5" 80GB SATA HDD. Then I was using WinXP.
The HDD had the following partitions:
C for WinXP, D,E & F for data....

I have not used the HDD for last 3 years, as my laptop broke down, some problem with powerchip, & such old parts are not available anymore...

I have recently acquired a HDD external case and tried to retrieve the data from the said drive....

There was no response from the HDD at first, after warming up for 30 minutes, there were sounds like that of the HDD running...

Ubuntu 13.04 couldn't read it in the end....

Any ideas on how to retrieve the data from that drive?
Any pathways will be of great help as I have a lot of important data just lying on that disk.....

---

### Post by mr-woof on 2013-07-10
Have you tried any other hard drives in the external drive case? I know my cheap one can be a bit iffy at times

Have you got a desktop? Connect the drive as the second drive and see if you can read it from there?

---

### Post by mips on 2013-07-10
If you have a desktop connect it directly to a sata port.

What does **sudo fdisk -l** give you with the drive connected?

---

### Post by su:bhatta on 2013-07-10
Thanks for the replies...
I do not have a desktop with me anymore, but that can be arranged this weekend... am surely gonna try that..

I do not have any more laptop HDD's with me to try that china made case so i dont know if that is flawed...(all i can say is that the power light shows on i.e. it is glowing red)
Here is the result of sudo fdisk -l:

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xa33b6c03

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    84198054    42098996    7  HPFS/NTFS/exFAT
Partition 1 does not start on physical sector boundary.
/dev/sda2       168072032   976768064   404348016+   7  HPFS/NTFS/exFAT
/dev/sda3        84199422   168071167    41935873    5  Extended
Partition 3 does not start on physical sector boundary.
/dev/sda5       158072832   168071167     4999168   82  Linux swap / Solaris
/dev/sda6        84199424   158072470    36936523+  83  Linux

Partition table entries are not in disk order

    There is a valid Mac label on this disk.
    Unfortunately fdisk(1) cannot handle these disks.
    Use either pdisk or parted to modify the partition table.
    Nevertheless some advice:
    1. fdisk will destroy its contents on write.
    2. Be sure that this disk is NOT a still vital
       part of a volume group. (Otherwise you may
       erase the other disks as well, if unmirrored.)


Disk /dev/mapper/cryptswap1: 5119 MB, 5119148032 bytes
255 heads, 63 sectors/track, 622 cylinders, total 9998336 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes

                  Device Boot      Start         End      Blocks   Id  System
```

That 500GB is my current laptop HDD....

The HDD is running, its making periodic click-click sound, thatz all i can say...

---

### Post by stalkingwolf on 2013-07-10
i have at times had issues with external adapters.  sometimes changing the usb port has helped

---

### Post by CharlesA on 2013-07-10
Clicking usually means a head crash and it's unlikely the data on the drive is accessible.

As far as recovering the data, I guess you could try the whole "put drive in freezer" and then try to access your data, but that procedure is a bit iffy at best.

If you really want that data, you'll probably have to pay for a data recovery service to take a look at it, which can be quite expensive.

---

### Post by su:bhatta on 2013-07-11
Thanks again... I have already tried the 3 available USB ports in my laptop... only thing left is usin another case... or trying it in a Desktop, which i will try this weekend...

"put drive in the freezer" i got no clue about... but paying for data recovery, yes costly! 

Got no projects in hand currently, so recovery will have to wait....

---

### Post by CharlesA on 2013-07-11
I've never tried it, but there is a disclaimer on this wiki page..
[http://howto.wired.com/wiki/Save_Your_Hard_Drive_by_Freezing_It](http://howto.wired.com/wiki/Save_Your_Hard_Drive_by_Freezing_It)

---

### Post by deadflowr on 2013-07-11
Way way way before I ever thought about putting a hard drive in a freezer, I would seek out a recovery specialist first.

---

### Post by su:bhatta on 2013-07-11
Really, thatz not something i would try, better to live without that data...

Anyways, thanks for the suggestion...

ps: Please dont take it as an insult or trolling/attack or flaming: I just dont like the guy in your avatar picture (James Bond, forgot which 1)

---

### Post by su:bhatta on 2013-07-11
> **deadflowr said:**
> Way way way before I ever thought about putting a hard drive in a freezer, I would seek out a recovery specialist first.

precisely what i am gonna do, in case i cannot make it work with a desktop !

---

### Post by mips on 2013-07-11
> **CharlesA said:**
> 
As far as recovering the data, I guess you could try the whole "put drive in freezer" and then try to access your data, but that procedure is a bit iffy at best.


[http://www.youtube.com/watch?feature=player_embedded&v=ad1uVAB5bNA](http://www.youtube.com/watch?feature=player_embedded&v=ad1uVAB5bNA)

---

### Post by mastablasta on 2013-07-11
they succesfully recovered data of one of my coworkers using the freezer. we thought it was lost and they made this final attempt (since she had plenty of important customer's data stored there). it worked.

---

### Post by CharlesA on 2013-07-11
> **mips said:**
> [http://www.youtube.com/watch?feature=player_embedded&v=ad1uVAB5bNA](http://www.youtube.com/watch?feature=player_embedded&v=ad1uVAB5bNA)

Haha. I've never put much faith in that whole freezer thing, but I guess if it works, it works, otherwise you still have a dead drive.

@OP: Backups are your friend. ;)

---

### Post by tgalati4 on 2013-07-11
The bearings in old disk drives get sticky.  The low power available with USB external enclosures usually can't spin up these old drives properly.  You would have better luck finding an IDE adapter and plugging it into the ribbon cable inside a linux desktop computer.  That would give you full power and better chance of getting the drive to spin up to full speed so you can read it.

---

### Post by mips on 2013-07-11
> **CharlesA said:**
> Haha. I've never put much faith in that whole freezer thing, but I guess if it works, it works, otherwise you still have a dead drive.


Thing is you might have some luck but the damage could be way worse. If you really have to try this then stick the drive in a bag with a lot of silica gel packs to absorve the moisture & then add another 2 vacuum sealed bags after that.

The issue here is spindle motor stiction and when you cool it down the tolerances become a bit better and the drive might start up. Ideally in this scenario you should do a platter swap to a donor drive chassis but you need the right tools & environment to this in.

---

### Post by su:bhatta on 2013-07-12
> **mips said:**
> Thing is you might have some luck but the damage could be way worse. If you really have to try this then stick the drive in a bag with a lot of silica gel packs to absorve the moisture & then add another 2 vacuum sealed bags after that.

The issue here is spindle motor stiction and when you cool it down the tolerances become a bit better and the drive might start up. Ideally in this scenario you should do a platter swap to a donor drive chassis but you need the right tools & environment to this in.

Thanks for all suggestions, 

but that freezer thing I am not really considering, I will first try connecting the drive to the desktop, this Sunday. Pray that it works. Else I will get the Data recovery done.

I also have client related information as well as plain personal data, pictures n videos on that HDD...

so itz kinda dear to me... 

If all else fails, I might and I say, I just Might toss it in the freezer and see what happens...

---

### Post by su:bhatta on 2013-07-15
Sad to report, the HDD didn't work with the Desktop...

Will have to go for recovery....

---

### Post by mips on 2013-07-15
> **bhattabhishek said:**
> Sad to report, the HDD didn't work with the Desktop...

Will have to go for recovery....

Hang on what are the exact symptoms of the HDD when you connect it?
Is it recognised by the BIOS?
Does it spin up?
Does it make any noises?
Full make & model details?

Maybe a video with microphone closeup would help.

It might be blown TVS diodes which is easy to get around.

---

### Post by su:bhatta on 2013-07-15
Ok, Thanks for the help !

1)When I connect the HDD the BIOS is not recognising it at all !
2)It is spinning up(Guessing that) and getting warm in about 10 mins !
3) It is making 'clicking' noises like that of a clock ! That also is stopping, say afetr, 5 mins !

Model & Make:

Hitachi
Model : HTS541280H9SA00, 5400RPM SATA 80Gb 5V, 1.0 A DC

I dont know if this is relevant but anyways:

16383CYL, 16 Heads, 63SEC/T

---

### Post by mips on 2013-07-15
> **bhattabhishek said:**
> 
1)When I connect the HDD the BIOS is not recognising it at all !

3) It is making 'clicking' noises like that of a clock ! That also is stopping, say afetr, 5 mins !


1) I would check the TVS diodes on the drive for starters.

3) Could you possibly record the sound from power up to say 2 minutes afterwards?

---

### Post by su:bhatta on 2013-07-15
I have no clue about TVS diodes really! & gimme a day and i will record the sound, if it makes any again, & post it in my box account and share the link! would that be ok?

---

### Post by mips on 2013-07-15
No rush take your time.

---

