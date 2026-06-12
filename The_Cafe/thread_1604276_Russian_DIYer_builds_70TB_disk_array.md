---
title: "Russian DIYer builds 70TB disk array"
date: 2010-10-23
forum: The Cafe
---

### Post by Sporkman on 2010-10-23
[http://englishrussia.com/index.php/2010/10/20/home-data-storage-for-70-tb/](http://englishrussia.com/index.php/2010/10/20/home-data-storage-for-70-tb/)

Wow. :)

---

### Post by inobe on 2010-10-23
no sata cards or cables ?

that is a huge array of drives yet they are only being powered if that ?

---

### Post by Dustin2128 on 2010-10-23
> **inobe said:**
> no sata cards or cables ?

that is a huge array of drives yet they are only being powered if that ?
perhaps he plugs them in as he uses them? Then why are they powered... the mind reels...

---

### Post by inobe on 2010-10-23
that setup would require several or more power supplies, i don't even see one ?

---

### Post by Sporkman on 2010-10-23
> **inobe said:**
> that setup would require several or more power supplies, i don't even see one ?

There is one attached to the inside of the cabinet.

---

### Post by inobe on 2010-10-23
so basically he has the ability to connect five or less drives simultaneously.

dustin i guess your correct, he may manually move data cables to empty disks.

for certain it would cost hundreds to thousands in sata cards to run all those drives and a few more power supplies.

---

### Post by kaldor on 2010-10-23
[quote=Dschinghis Khan]Those Russians...[/quote]

;)

---

### Post by cammin on 2010-10-24
> **inobe said:**
> no sata cards or cables ?

that is a huge array of drives yet they are only being powered if that ?

You don't see the sata cables or raid cards because they're not installed in those photos.

[http://basanovich.livejournal.com/163813.html](http://basanovich.livejournal.com/163813.html) shows more build photos and gives some more information.

---

### Post by Random_Dude on 2010-10-24
English Russia is awesome.

I had already seen that. When it's cold outside you come up with some really cool projects.

---

### Post by CharlesA on 2010-10-24
Wow. I haven't even found a way to use up the 4TB of space I have on my server.

---

### Post by perspectoff on 2010-10-24
Garsh, Popeye, maybe he'll be able to do multiple-processor computing, too!

Perhaps distributed in a load-balanced fashion. Think of what he could do with all that memory and processors -- maybe start a cool search engine or online encyclopedia or file-trading service, or something.

---

### Post by koleoptero on 2010-10-24
Imagine fsck or chkdsk running for all those things after a power failure...

---

### Post by Spice Weasel on 2010-10-24
> **koleoptero said:**
> Imagine fsck or chkdsk running for all those things after a power failure...

Fscking hell! That would take years. :)

---

### Post by blueturtl on 2010-10-24
Imagine how ridiculous that's going to look in retrospect after we have 80 TB in a single drive.

---

### Post by NCLI on 2010-10-24
Meh, nothing special. I also have to qualms about the design:

1. Wood. Really? I don't think that's a very good idea...
2. I *really* hope he uses RAID6 for that setup, or the odds of it lasting more than 1-2 years are low...

---

### Post by darkscout on 2010-10-24
The array of fans is a waste. He could have easily installed a tiny quiet (but huge CF/m) squirrel fan, made an array of holes in the bottom and run that.

Who said he is using RAID anything. Could easily be running ZFS or a sane file system for that many drives.

---

### Post by madhi19 on 2010-10-24
That would make one hell of a seed box! lolll

---

### Post by Mike'sHardLinux on 2010-10-24
Part of me says that's cool. The other part says BFD. If I had the extra $ laying around, I could do that easily.

I have a server running 24/7 that has 11.5TB of storage that I actually use and I know there are several Ubuntu forums members who can say the same (or more!).

:guitar:

Anyway.......neat.

---

### Post by phaed on 2010-10-24
The lengths people will go to to store their porn.

---

### Post by 98cwitr on 2010-10-24
that's a lot of pr0n, someone get dude's IP address ;)

---

### Post by mr clark25 on 2010-10-24
if you look closely, you can see that there are two server power supplies in it...

definitely interesting. i wonder how he will manage the space on those drives... (as in with a raid, partition them all separately, etc.)

---

### Post by handy on 2010-10-25
I'm surely glad that for some reason I didn't think that (his idea) was a good idea!

---

### Post by Moozillaaa on 2010-10-25
! have 11.5Tb, and they're just about full. 

(not RAIDED, cause the back-ups for each one are on the hself, except the active disk, which also is full) > 

chuckhtpc@chuckhtpc-desktop:~$ sudo fdisk -l
[sudo] password for chuckhtpc: 

Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x59db0ebc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *       30402       92230   496641442+  83  Linux
/dev/sda2               1       30401   244196001   83  Linux
/dev/sda3           92231      121601   235922557+  83  Linux
/dev/sda4          121602      243201   976752000   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000dc754

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       82863   665597016   83  Linux
/dev/sdb2           82864      162539   639997470   83  Linux
/dev/sdb3          162540      243201   647917515   83  Linux

Disk /dev/sdc: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfc1bf690

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       33145   266237181   83  Linux
/dev/sdc2           33146       81588   389118397+  83  Linux
/dev/sdc3           81589      132581   409601272+  83  Linux
/dev/sdc4          132582      182401   400179150   83  Linux

Disk /dev/sdd: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0006b622

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1      101986   819202513+  83  Linux
/dev/sdd2          101987      191223   716796202+  83  Linux
/dev/sdd3          191224      243201   417513285   83  Linux

Disk /dev/sde: 30.7 GB, 30735581184 bytes
255 heads, 63 sectors/track, 3736 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x04620462

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *           1        1759    14129136    7  HPFS/NTFS
/dev/sde3            1760        3736    15880252+  83  Linux

Disk /dev/sdf: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0006ca0a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1        8924    71681998+  83  Linux
/dev/sdf2            8925        9434     4096575   82  Linux swap / Solaris

Disk /dev/sdg: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00062946

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1               1       82863   665597016   83  Linux
/dev/sdg2           82864      162539   639997470   83  Linux
/dev/sdg3          162540      243201   647917515   83  Linux
chuckhtpc@chuckhtpc-desktop:~$ 

---

### Post by Dixon Bainbridge on 2010-10-25
Perhaps the guy just did it because he could. Does it matter if something is sensible or not? It was probably a fantastic learning experience too. Who cares if its inefficient or impractical? 

I like the wood - I think all technology should be made of wood or brass. Or both.

Makes for an interesting talking point at parties as well :)

---

### Post by koleoptero on 2010-10-25
> **Dixon Bainbridge said:**
> Makes for an interesting talking point at parties as well :)

*[FONT="Book Antiqua"]"Hey babe, want me to show you my 70TB **hard** drive stack?"[/FONT]*

---

### Post by handy on 2010-10-25
30TB, 40TB, 50TB, 120TB... So what?

It is just an expanding procedure.

As has already been stated, maintaining such a large amount of data would be an ongoing nightmare.

---

### Post by cammin on 2010-10-25
> **darkscout said:**
> Who said he is using RAID anything. Could easily be running ZFS or a sane file system for that many drives.

"The Hards are collected in the raids, mostly raid5, from time to time I also make experiments with raid 50."

He's also using Windows server 2008, if you wanted to know.

---

### Post by mips on 2010-10-25
I would rather **[COLOR="Red"]DIY[/COLOR]** one of these [http://blog.backblaze.com/2009/09/01/petabytes-on-a-budget-how-to-build-cheap-cloud-storage/](http://blog.backblaze.com/2009/09/01/petabytes-on-a-budget-how-to-build-cheap-cloud-storage/)

[IMG]http://blog.backblaze.com/wp-content/uploads/2009/08/backblaze-storage-pod-partially-assembled.jpg[/IMG]

---

### Post by Sporkman on 2010-10-25
> **mips said:**
> I would rather DIY one of these [http://blog.backblaze.com/2009/09/01/petabytes-on-a-budget-how-to-build-cheap-cloud-storage/](http://blog.backblaze.com/2009/09/01/petabytes-on-a-budget-how-to-build-cheap-cloud-storage/)

That is awesome!

---

### Post by Dustin2128 on 2010-10-25
> **koleoptero said:**
> *[FONT=Book Antiqua]"Hey babe, want me to show you my 70TB **hard** drive stack?"[/FONT]*
stop stealing my pickup lines!

---

### Post by mips on 2010-10-26
> **Sporkman said:**
> That is awesome!

The beauty is you can buy those chassis online or download the cad drawings and have the metal laser cut and assembled yourself. With the newer 2TB & 3TB drives you are looking at 90TB-135TB and you can even change the chassis design.

I think everyone should build one of these during their lifetime :D

---

### Post by mips on 2010-10-26
> **inobe said:**
> no sata cards or cables ?

that is a huge array of drives yet they are only being powered if that ?

> **Dustin2128 said:**
> perhaps he plugs them in as he uses them? Then why are they powered... the mind reels...

> **inobe said:**
> that setup would require several or more power supplies, i don't even see one ?

> **inobe said:**
> so basically he has the ability to connect five or less drives simultaneously.

dustin i guess your correct, he may manually move data cables to empty disks.

for certain it would cost hundreds to thousands in sata cards to run all those drives and a few more power supplies.

> **cammin said:**
> You don't see the sata cables or raid cards because they're not installed in those photos.

[http://basanovich.livejournal.com/163813.html](http://basanovich.livejournal.com/163813.html) shows more build photos and gives some more information.

In a situation like this he is most likely using a [Port Multiplier/Replicator]("http://en.wikipedia.org/wiki/Port_multiplier") which allows you to run 5xHDDs off a single SATA port.

[http://www.serialata.org/technology/port_multipliers.asp](http://www.serialata.org/technology/port_multipliers.asp)
[http://www.tomshardware.com/reviews/silicon-image-brings-virtualization-esata,1610-3.html](http://www.tomshardware.com/reviews/silicon-image-brings-virtualization-esata,1610-3.html)

---

