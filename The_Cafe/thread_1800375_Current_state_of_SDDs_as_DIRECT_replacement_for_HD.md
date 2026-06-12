---
title: "Current state of SDDs as DIRECT replacement for HDDs"
date: 2011-07-08
forum: The Cafe
---

### Post by Bart_D on 2011-07-08
Solid State Drives have been around for quite a few years now. I suspect that the technology has matured over that time. They are becoming quite popular, especially with netbooks.

With this in mind, I have a question regarding the current state of solid state drives.

Have SDDs matured to the point that, when a consumer purchases a brand new laptop (or possibly even for a new desktop), is a SDD a better option than a HDD for the new device?

EDIT: ASSUME --> Storage capacity is not an issue.

---

### Post by psusi on 2011-07-08
Like all things, it depends on how you define "better".  You get a lot less storage that is a lot faster than you would spending a similar amount on a hdd.  Whether that is better or not is entirely up to you.

---

### Post by Bart_D on 2011-07-08
Good point.

For the purposes of this thread, assume that storage capacity is NOT an issue.

---

### Post by psusi on 2011-07-08
> **Bart_D said:**
> Good point.

For the purposes of this thread, assume that storage capacity is NOT an issue.

Then if you don't mind the down side, that just leaves the up side, so win-don'tcare.

---

### Post by Dustin2128 on 2011-07-08
More than ready but pricey.

---

### Post by wolfen69 on 2011-07-08
I have one in my netbook and thought it would be like night and day, but it's not. It is certainly faster, but a netbook has bottlenecks, so some of the advantage is negated. I'm sure it would be a better experience on a nice desktop or laptop.

---

### Post by Khakilang on 2011-07-08
Or you can have a SSD in your netbook or notebook and a external hard disk if you need extra storage. I use an 80GB hard disk which is hardly can store anything since I store a lot of photos. So I had an external hard disk. SSD is certainly faster and it would be an advantage for multiple application.

---

### Post by wolfen69 on 2011-07-09
> **psusi said:**
> Like all things, it depends on how you define "better".  You get a lot less storage that is a lot faster than you would spending a similar amount on a hdd.  Whether that is better or not is entirely up to you.

Some people are using ssd's just for /, and put /home on a regular drive. So apps open quick, but media is the same. Is it worth it? Maybe.

---

### Post by wizard10000 on 2011-07-09
> **Khakilang said:**
> Or you can have a SSD in your netbook or notebook and a external hard disk if you need extra storage. I use an 80GB hard disk which is hardly can store anything since I store a lot of photos. So I had an external hard disk. SSD is certainly faster and it would be an advantage for multiple application.

I have a 60gb OCZ Agility 2 in my netbook and a 500gb laptop drive in an external enclosure that holds backups and my multimedia.

The SSD is hellaciously fast but on a netbook (at least on my netbook) the bottleneck is the disk controller so 125mb/sec is about all I get out of it, which is about a quarter faster than the 500gb drive I used to have in machine (which is now the external drive)  grub to desktop is ~29 seconds, which ain't bad for a netbook  ;)

I've done all the right things - partitions are aligned correctly, I'm using the noop scheduler as a kernel argument, noatime and discard are set in fstab and and /tmp is on tmpfs.  Although I'm about to change it back to the default, ext4 commit interval is 120 sec instead of the default 5 sec.

I will say that data loss on a SSD is normally catastrophic when they fail, so good backups are critical - the 64gb Corsair Extreme X64 in my desktop PC has been running strong for two years now but again, I'm pretty religious about backups.

---

### Post by wizard10000 on 2011-07-09
> **wolfen69 said:**
> Some people are using ssd's just for /, and put /home on a regular drive. So apps open quick, but media is the same. Is it worth it? Maybe.

This is what I do on my desktop PC.  / is on the SSD but swap and /home are on a 1TB mechanical hard drive.  I don't put /tmp in RAM on this machine because I do write DVD images to disk and the machine's only got 6gb RAM.

---

### Post by KUU on 2011-08-10
SSD drives have amazing speed because they compress the data, when the drive eventually fails all the data is lost, whereas on HDD drives fails most of the data is recoverable.

The other hing is that SSD drives have very short write endurance compared to disks.

---

### Post by psusi on 2011-08-10
> **KUU said:**
> SSD drives have amazing speed because they compress the data, when the drive eventually fails all the data is lost, whereas on HDD drives fails most of the data is recoverable.

No, they don't; this is complete BS.  They have amazing speed because they have no moving parts; they do not do internal compression.

Hard disks also frequently fail completely so the computer can't even recognize it exists, let alone get any data off of it.  There is no evidence that this is the case any more or less with SSDs.

> **KUU said:**
> The other hing is that SSD drives have very short write endurance compared to disks.

While they do have limits, they are high enough that you won't ever reach them with normal usage within the expected lifetime of a drive ( 7 years ).  I've had mine for a year and a half now and only used something like 5% of its write cycles, so at that rate it should be good for another 30 years.

---

### Post by PhillyPhil on 2011-08-10
> **psusi said:**
> While they do have limits, they are high enough that you won't ever reach them with normal usage within the expected lifetime of a drive ( 7 years ).  I've had mine for a year and a half now and only used something like 5% of its write cycles, so at that rate it should be good for another 30 years.

Much longer than that even.  I posted about this somewhere, sometime, but I've lost it.
SSDs will last a ridiculously long time.

Only bad thing about SSDs is dollars per GB.

---

### Post by Evil-Ernie on 2011-08-10
I work for Intel and its all about the SSD's at the moment. Because they are non-mechanical they just dont wear out like HDD's, are a lot quicker and more hardy to knock and vibration.
 
Only drawbacks are they are still expensive (but with mass production the price will fall as they get popular) also there is the issue touched on earlier that on failure (which is rare but it happens) all data is lost so its a good idea to have a backup routine (like you should have anyway ;) ) 
 
They are going to be like LCD screens, start of as an expensive product but as they get accepted will be seen as the norm.

---

### Post by forrestcupp on 2011-08-10
> **Khakilang said:**
> Or you can have a SSD in your netbook or notebook and a external hard disk if you need extra storage. I use an 80GB hard disk which is hardly can store anything since I store a lot of photos. So I had an external hard disk. SSD is certainly faster and it would be an advantage for multiple application.

This is what I do with my nettop. I have a 30GB SSD only for the OS, and I have an external drive for all of my DVD videos and music.

About the whole issue with netbook bottlenecks. It's still worth it to have a SSD in a netbook. If a netbook used a HDD, it would feel extremely slow. SSDs are pretty much required for them to be usable. (Except maybe from some of the newer ones that are more like small laptops.)

---

### Post by Evil-Ernie on 2011-08-10
> **forrestcupp said:**
> This is what I do with my nettop. I have a 30GB SSD only for the OS, and I have an external drive for all of my DVD videos and music.
 
 
That is a good way to get round the SSD price premium, just buy enough GB to cover your OS and then whack your big stuff on a second larger HDD.
 
Like I said in my other comment soon I think the price will drop to make them competetive with HDD's so you have to weigh up is it worth spending the cash now on a large SSD when in 12 months time the same will be available at a fraction of the price.

---

### Post by mips on 2011-08-10
> **forrestcupp said:**
> This is what I do with my nettop. I have a 30GB SSD only for the OS, and I have an external drive for all of my DVD videos and music.


Does your laptop have a optical drive?

Another option would be to remove the optical drive and put a normal hard drive in there for your data.

---

### Post by Copper Bezel on 2011-08-10
A "nettop" is a marketing term for a mini-tower, like the Mac Mini. Asus has its EeeBox line, and there are a few others. It's meant to evoke "netbook" and "desktop" despite sounding like "webtop," which gets used to mean a netbook with even more limited specs.

I saw a marked improvement in performance in the two machines I've installed an SSD in, one of which was a netbook, and my current netbook came with integrated flash storage. On portables, the SSDs' greater durability becomes a big advantage, too.

---

### Post by forrestcupp on 2011-08-10
> **mips said:**
> Does your laptop have a optical drive?

Another option would be to remove the optical drive and put a normal hard drive in there for your data.

No, it's a nettop. That's like a desktop version of a netbook. It only has space for a RAM module and one 3.5" HD. Its only video out is hdmi. I use it to watch my ripped DVDs which I have on a 2TB external. I'll bet a 2TB SSD would cost a fortune. :)

---

### Post by mips on 2011-08-10
> **forrestcupp said:**
> It only has space for a RAM module and **one 3.5" HD**.

You can fit 2x 2.5" drives into the space of a 3.5" bay so one can be a SSD while the other can be a normal drive.

How many sata ports does it have though? If only one then there's the option of a port multiplier.

---

### Post by forrestcupp on 2011-08-10
> **mips said:**
> You can fit 2x 2.5" drives into the space of a 3.5" bay so one can be a SSD while the other can be a normal drive.

How many sata ports does it have though? If only one then there's the option of a port multiplier.

It only has one sata port. Not only that, but the case is so small that it was hard enough to cram the one drive in. The way it's built, I really doubt if you could fit a port multiplier in there. But it does have an eSATA port for external drives. I haven't been able to get it to work, though, so I've been stuck with USB 2.0. 

Since it is a stationary device, and not meant to be portable, it works just fine with an external. It's all hiding behind my TV, and I don't ever have to mess with it, unless the power goes out and I have to turn it back on.

But for portable computers, your idea would probably be a better solution.

---

