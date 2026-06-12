---
title: "found a 2TB drive in atic"
date: 2009-07-30
forum: The Cafe
---

### Post by ssam on 2009-07-30
Digging through some old boxes i found some old hard disks. On pluging one in to my laptop i got a bit of a surprise in dmesg

```

scsi 3:0:0:0: Direct-Access     WDC AC28 0                     PQ: 0 ANSI: 0 CCS
sd 3:0:0:0: [sdb] **Very big device**. Trying to use READ CAPACITY(16).
sd 3:0:0:0: [sdb] READ CAPACITY(16) failed
sd 3:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
sd 3:0:0:0: [sdb] Use 0xffffffff as device size
sd 3:0:0:0: [sdb] 4294967296 512-byte hardware sectors (**2199023 MB**)
sd 3:0:0:0: [sdb] Write Protect is off
sd 3:0:0:0: [sdb] Mode Sense: 00 14 00 00
sd 3:0:0:0: [sdb] Assuming drive cache: write through
sd 3:0:0:0: [sdb] Very big device. Trying to use READ CAPACITY(16).
sd 3:0:0:0: [sdb] READ CAPACITY(16) failed
sd 3:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
sd 3:0:0:0: [sdb] Use 0xffffffff as device size
sd 3:0:0:0: [sdb] 4294967296 512-byte hardware sectors (2199023 MB)
sd 3:0:0:0: [sdb] Write Protect is off
sd 3:0:0:0: [sdb] Mode Sense: 00 14 00 00
sd 3:0:0:0: [sdb] Assuming drive cache: write through
 sdb:

```

wow, 2.2TB.

here is a photo

---

### Post by JillSwift on 2009-07-30
Wow.

Imagine how much that tiger cost when it was new.

---

### Post by frup on 2009-07-30
It's meant to be 85mb?

---

### Post by rannable on 2009-07-30
you found a 2tb drive in the attic? wow! they have only just been released in the UK :)

---

### Post by Delever on 2009-07-30
I want such attic too.

---

### Post by 4th guy on 2009-07-30
What was in it? A secret stash? *wink*wink*

---

### Post by ssam on 2009-07-30
> **rannable said:**
> you found a 2tb drive in the attic? wow! they have only just been released in the UK :)

it says its made in 1991, must be :evil: military tech

---

### Post by rannable on 2009-07-30
Bloody hell thats fantastic! What else do you have in that attic- Jimmy Hoffa and the Lost Ark? :D

Is it sata or ide? Dumb question but i just wondered if there was some surprises there...

---

### Post by nowin4me on 2009-07-30
> **rannable said:**
> Is it sata or ide? Dumb question but i just wondered if there was some surprises there...

Look at the picture. It's conected to a "Easy**IDE**"!

---

### Post by bear24rw on 2009-07-30
what was on it? lol

---

### Post by LowSky on 2009-07-30
Well the thing must be broken if it's reading as 2199023 MB when its clearly 85.3MB

```

scsi 3:0:0:0: Direct-Access     WDC AC28 0                     PQ: 0 ANSI: 0 CCS
sd 3:0:0:0: [sdb] **Very big device**. Trying to use READ CAPACITY(16).
sd 3:0:0:0: [sdb] [COLOR="Red"]READ CAPACITY(16) failed[/COLOR]
sd 3:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
sd 3:0:0:0: [sdb] Use 0xffffffff as device size
sd 3:0:0:0: [sdb] [COLOR="Red"]4294967296 512-byte hardware sectors [/COLOR](**2199023 MB**)
sd 3:0:0:0: [sdb] Write Protect is off
sd 3:0:0:0: [sdb] Mode Sense: 00 14 00 00
sd 3:0:0:0: [sdb] Assuming drive cache: write through
sd 3:0:0:0: [sdb] Very big device. Trying to use READ CAPACITY(16).
sd 3:0:0:0: [sdb] [COLOR="Red"]READ CAPACITY(16) failed[/COLOR]
sd 3:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
sd 3:0:0:0: [sdb] Use 0xffffffff as device size
sd 3:0:0:0: [sdb] 4294967296 512-byte hardware sectors (2199023 MB)
sd 3:0:0:0: [sdb] Write Protect is off
sd 3:0:0:0: [sdb] Mode Sense: 00 14 00 00
sd 3:0:0:0: [sdb] Assuming drive cache: write through
 sdb:

```



[IMG]http://farm3.static.flickr.com/2270/2129771538_172be6fdc8_b.jpg[/IMG]

---

### Post by RD1 on 2009-07-30
Great! You've found the experimental Trans-Dimensional Storage Device. This device stores all human knowledge .. Past, Present and Future. That thing went missing some time ago. Agents from Warehouse 13 will be there soon to reclaim it. Please remain calm. Thank you.

---

### Post by MasterNetra on 2009-07-30
> **LowSky said:**
> Well the thing must be broken if it's reading as 2199023 MB when its clearly 85.3MB

```

scsi 3:0:0:0: Direct-Access     WDC AC28 0                     PQ: 0 ANSI: 0 CCS
sd 3:0:0:0: [sdb] **Very big device**. Trying to use READ CAPACITY(16).
sd 3:0:0:0: [sdb] [COLOR="Red"]READ CAPACITY(16) failed[/COLOR]
sd 3:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
sd 3:0:0:0: [sdb] Use 0xffffffff as device size
sd 3:0:0:0: [sdb] [COLOR="Red"]4294967296 512-byte hardware sectors [/COLOR](**2199023 MB**)
sd 3:0:0:0: [sdb] Write Protect is off
sd 3:0:0:0: [sdb] Mode Sense: 00 14 00 00
sd 3:0:0:0: [sdb] Assuming drive cache: write through
sd 3:0:0:0: [sdb] Very big device. Trying to use READ CAPACITY(16).
sd 3:0:0:0: [sdb] [COLOR="Red"]READ CAPACITY(16) failed[/COLOR]
sd 3:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
sd 3:0:0:0: [sdb] Use 0xffffffff as device size
sd 3:0:0:0: [sdb] 4294967296 512-byte hardware sectors (2199023 MB)
sd 3:0:0:0: [sdb] Write Protect is off
sd 3:0:0:0: [sdb] Mode Sense: 00 14 00 00
sd 3:0:0:0: [sdb] Assuming drive cache: write through
 sdb:

```



[IMG]http://farm3.static.flickr.com/2270/2129771538_172be6fdc8_b.jpg[/IMG]

+1
It must not be functioning properly. Its doubtful it will let you store 2TB of info.

---

### Post by linuxguymarshall on 2009-07-30
[http://www.computerjunk.com/catalog/items/item133.htm](http://www.computerjunk.com/catalog/items/item133.htm)

It is an 86 MB drive, see link above. Still, that is badass dude. Try to load a large (100 MB+) file onto it to see what happens.

---

### Post by mr.propre on 2009-07-30
> **linuxguymarshall said:**
> [http://www.computerjunk.com/catalog/items/item133.htm](http://www.computerjunk.com/catalog/items/item133.htm)

It is an 86 MB drive, see link above. Still, that is badass dude. Try to load a large (100 MB+) file onto it to see what happens.

Do we really want that? Maybe it opens a portal to another dimension and who knows what will happened than?

---

### Post by aktiwers on 2009-07-30
I wanna see the 100mb file on it as well :)

---

### Post by ssam on 2009-07-30
sorry, it wont mount. parted can't see the drive so i can't make new partitions.

probably for the best, i would not want to create some nasty space time vortex. not all physicists want to destroy the world (in fact most of them quite like our planet).

---

### Post by moster on 2009-07-30
Maybe aliens forgot it.
When they landed in night in your back yard and exploring your attic.

Is there anything on that disk? :)
(maybe dirty pictures)

---

### Post by darco on 2009-07-30
I'm checking MY attic now...I might find an I7!.......

darco

edit* ahh, dang.....it was just a Celeron

---

### Post by 0per4t0r on 2009-07-30
Holy Mongoose on a Monster Truck! You just stumbled upon this in your attic?! I better search mine, maybe I'll find the holy grail!

---

### Post by clonne4crw on 2009-07-30
Thats awesome. What year is it?

---

### Post by moster on 2009-07-30
I will too, maybe Santa drop something.

:)

---

### Post by koleoptero on 2009-07-30
I have a spare 60 GB drive. Can I put it in your attic for some years. Perhaps it'll come out as 1,5 hexabytes in a decade.

---

### Post by starcannon on 2009-07-30
Can I come dig through your attic? I need to find a fresh 4g63 2.4 liter stroker motor for my Eagle Talon, perhaps you got one of those in a box up there? :D

Grats on the great find.

Edit:
NM after looking at picture, and reading up on the WDAC280-32, I can see now what happened. Your OS magically transformed it from an 85mb hdd to a 2tb; again though, may I come over? I'd like to plug your computer into my Eagle Talon and have it upgrade my motor for me :P

---

### Post by DaveAK on 2009-07-30
Wow!! That's a great find!!  Based on the picture I think I might have some old drives ranging from 1TB to 4TB just collecting dust.

---

### Post by Chronon on 2009-07-30
> **koleoptero said:**
> I have a spare 60 GB drive. Can I put it in your attic for some years. Perhaps it'll come out as 1,5 hexabytes in a decade.

I think you mean "exa".  ;)

hexa = 6
exa = 1 000 000 000 000 000 000

---

### Post by koleoptero on 2009-07-30
Yeah it's been a while since I had to count that high.

---

### Post by jflaker on 2009-07-30
> **moster said:**
> Maybe aliens forgot it.
When they landed in night in your back yard and exploring your attic.

Is there anything on that disk? :)
(maybe dirty pictures)

I'm thinking if the visitors can master interstellar travel, they stopped using spinning media eons ago!

---

### Post by koleoptero on 2009-07-30
> **jflaker said:**
> I'm thinking if the visitors can master interstellar travel, they stopped using spinning media eons ago!

That's why they dropped it and never came back for it. :roll:

---

### Post by tom66 on 2009-07-30
4294967296 sectors is 2^32. It seems its configuration got corrupted. Since all bits are 1, that would probably be the cause... In which case it probably won't work because it doesn't know where all its data is.

---

### Post by CharmyBee on 2009-07-30
Image the drive. :)

---

