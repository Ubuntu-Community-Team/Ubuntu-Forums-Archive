---
title: "IDE vs SATA? Enclosed vs. External? Recommendations?"
date: 2008-03-10
forum: The Cafe
---

### Post by Chessmaster on 2008-03-10
Hey all,

some advice please. 

I am looking at getting some external storage. In terms of hard drives, I guess there are two options. 1) Standard hard drive in a hard drive enclosure or 2) an external hard drive. 

The former is cheaper per GB, but is there any significant difference? Are the any features that come with External Hard Drives that I would not be able replicate on enclosed Standard Hard Drive?

Also, what is the difference between IDE and SATA? Is the only real significance speed? Can I use either if used as an enclosed hard drive via USB? Or can some machines only run some types of drives?

Lots of questions I know. Any suggestions, advice would be great. 

Thanks

---

### Post by frankos44 on 2008-03-10
Internal drive:
IDE and SATA use different interface technology and different physical connectors.  If your PC supports SATA then go for that.

External USB:
An external USB drive, it dosent matter because the external enclosue will have a matching interface inside for the drive. Most new external backup drives would be using SATA inside anyway.

Extenal SATA:
This option is slightly different. You PC would have additional connectors on the back supporting SATA. Usually in the form of an additional Card. Personally I find USB more useful for backups bacause I can hot plug into any PC, however, having the luxury of external SATA connectors is great for loading an OS. For example I have been testing Hardy on a spare 80G SATA without playing around with any of my partitions on my mission critical computer.

---

### Post by jinx099 on 2008-03-10
Is your data important?

If it is, then you should consider a NAS box and do RAID-1 or RAID 5 with it (NOT RAID-0).  Or if you prefer, like I do, build your own server and run linux software RAID on a couple of drives.  

If your data is not important, then just assume that the drive is going to break on you one day and all your data will be gone.  :(  I am telling you this from personal experience.

---

### Post by Chessmaster on 2008-03-10
I only really want it for some backups, photos, and music. I can afford to lose the backups (assuming that my system doesn't crash at the same time as any external drive), the music can always be re-ripped...and the photos I always keep to copies of in two different places. 

So a NAS box or server does seem unnecessary - at the moment that is! No doubt one day soon I will want to expand my computer city, which is currently a very small village. 

I am also a relative newbie so such projects may need to wait a while until I get some more experience. On day though....

Another question: is there any significant difference between SATA and SATA II - or should one not worry?

Also, do many people use 2.5 inch drives? Is there any benefit other than being smaller?

---

### Post by prshah on 2008-03-10
> **Chessmaster said:**
> I only really want it for some backups, photos, and music. I can afford to lose the backups (assuming that my system doesn't crash at the same time as any external drive), the music can always be re-ripped...and the photos I always keep to copies of in two different places. 

So a NAS box or server does seem unnecessary - at the moment that is! No doubt one day soon I will want to expand my computer city, which is currently a very small village. 

I am also a relative newbie so such projects may need to wait a while until I get some more experience. On day though....

Another question: is there any significant difference between SATA and SATA II - or should one not worry?

Also, do many people use 2.5 inch drives? Is there any benefit other than being smaller?

Go for a SATA drive in an external SATA box. You will get 5 years warranty on the drive. Only 1 year for the box, but that no hardship.

2.5" drives will generally not require an external power brick, which will be required for HDD enclosure boxes.

Personally I would recommend you go for a SATA HDD drive in an external 3.5" enclosure.

Cheers,
PRShah

---

### Post by jinx099 on 2008-03-10
> **Chessmaster said:**
> I only really want it for some backups, photos, and music. I can afford to lose the backups (assuming that my system doesn't crash at the same time as any external drive), the music can always be re-ripped...and the photos I always keep to copies of in two different places. 

So a NAS box or server does seem unnecessary - at the moment that is! No doubt one day soon I will want to expand my computer city, which is currently a very small village. 

I am also a relative newbie so such projects may need to wait a while until I get some more experience. On day though....

Another question: is there any significant difference between SATA and SATA II - or should one not worry?

Also, do many people use 2.5 inch drives? Is there any benefit other than being smaller?

The server is something think about for the future.  I personally think its fun, but maybe it's just me.

Anyways, with SATAII you can get NCQ and hotplugging.  Hotpluggin would be nice if you got a eSATA enclosure, but that would require an eSATA motherboard or card.  If you have eSATA, go with that and a SATAII drive.  Otherwise, it doesnt matter much.  The drive and the USB connection will both bottleneck the SATA connection.

---

### Post by futureproof on 2008-03-10
Get an internal SATA II drive and put it in a removable bay,  you can pick up a decent one for about $30,  that way you can hot swap your drives any time you want.  USB external drives are terrible slow when compared to internals.  check the links


[http://www.akihabaranews.com/en/review-90-Need+a+USB+e-SATA+Rack%3F++Here+are+Four%21.html](http://www.akihabaranews.com/en/review-90-Need+a+USB+e-SATA+Rack%3F++Here+are+Four%21.html)


I dont endorse the next product, its just to give you an idea

[http://www.thetechlounge.com/articles.php?id=69](http://www.thetechlounge.com/articles.php?id=69)

---

### Post by Chessmaster on 2008-03-11
Thanks for the advice. 

Removable bay definitely sounds like a good option, especially w/r to speed. 

Although one of the reasons I want an external drive is music storage so I can take my music on holiday, to friends places etc without having to take the whole desktop! So, I would need something to be able to connect it to other computers - hence the need for portability. 

Couple of questions then:

1) With respect to speed, am I right to assume that using a eSATA connection would be comparably fast as having a removable bay? (the eSATA PCI cards seem relatively cheap so not an issue getting one if that is the way to go)

2) If I am just playing music files from the external drive would I actually notice any difference between eSATA connection and USB? 

Thanks

---

### Post by Pekkalainen on 2008-03-11
The standard you mean is PATA, not IDE. Both PATA and SATA are IDE.

---

### Post by futureproof on 2008-03-11
> **Chessmaster said:**
> Thanks for the advice. 

Removable bay definitely sounds like a good option, especially w/r to speed. 

Although one of the reasons I want an external drive is music storage so I can take my music on holiday, to friends places etc without having to take the whole desktop! So, I would need something to be able to connect it to other computers - hence the need for portability. 

Couple of questions then:

1) With respect to speed, am I right to assume that using a eSATA connection would be comparably fast as having a removable bay? (the eSATA PCI cards seem relatively cheap so not an issue getting one if that is the way to go)

2) If I am just playing music files from the external drive would I actually notice any difference between eSATA connection and USB? 

Thanks

1) The eSATA will be as fast as the internal

2) You will notice no difference at all with any type of drive if you're just playing music,  if you start moving 10s og GBs of data then you might notice a difference.


I use 

[http://usb.brando.com.hk/prod_detail.php?prod_id=00002](http://usb.brando.com.hk/prod_detail.php?prod_id=00002) 

on my removable drives when I go elsewhere.  

Not the exact same product but the same thing that I got for about $15

and 

[http://www.geeks.com/details.asp?invtid=SHP-2&cat=HDD](http://www.geeks.com/details.asp?invtid=SHP-2&cat=HDD)


to protect the drives when in transit.

---

### Post by regomodo on 2008-03-11
I'm surprised nobody has mentioned it yet, but a crucial advantage of internal sata over pata is the considerably thinner cables.

It's not really an issue with one or two drives but if you have 6  3.5" hdd's in your pc it becomes a major concern. Not just for managing the cables but also for airflow (overheating).

---

### Post by Chame_Wizard on 2008-03-11
i would  add 2 SATA HDD,enclosed and external,both from the same manufacture:guitar:

---

### Post by regomodo on 2008-03-11
> **Chame_Wizard said:**
> i would  add 2 SATA HDD,enclosed and external,both from the same manufacture:guitar:

but not from the same manufacturing batch. Just in case you decide to RAID

[edit] Just noticed the ext and int

---

### Post by futureproof on 2008-03-11
> **regomodo said:**
> I'm surprised nobody has mentioned it yet, but a crucial advantage of internal sata over pata is the considerably thinner cables.

It's not really an issue with one or two drives but if you have 6  3.5" hdd's in your pc it becomes a major concern. Not just for managing the cables but also for airflow (overheating).


I have a mix of 9 SATA and IDE drives in my case,  the really old ribbons could be a problem for airflow so i use

[http://www.xoxide.com/roundidecables1.html](http://www.xoxide.com/roundidecables1.html)

kind of cables

---

### Post by regomodo on 2008-03-11
> **futureproof said:**
> I have a mix of 9 SATA and IDE drives in my case,  the really old ribbons could be a problem for airflow so i use

[http://www.xoxide.com/roundidecables1.html](http://www.xoxide.com/roundidecables1.html)

kind of cables

Actually, i have 2 of those as well. Unfortunately, my case design and the long 8800gt doesn't allow those to be practical. At one point, the connector would stop a fan from turning and the other end there is not enough room between the hdd and the card. I still have a pata but flat ribbon cable is only possible in my setup.

Overall sata cables are a lot better despite there tendency to fall of when you mess around inside the case.

---

### Post by futureproof on 2008-03-11
> **regomodo said:**
> Actually, i have 2 of those as well. Unfortunately, my case design and the long 8800gt doesn't allow those to be practical. At one point, the connector would stop a fan from turning and the other end there is not enough room between the hdd and the card. I still have a pata but flat ribbon cable is only possible in my setup.

Overall sata cables are a lot better despite there tendency to fall of when you mess around inside the case.

haha @ falling off!  

you dont happen to have a p180 case do you?

my 8800gts is such a tight fit, I had to put the sata drives where it ends because the ide just wouldnt fit by 2mm

DOH just read your sig!  isnt that a great case!

---

### Post by regomodo on 2008-03-11
> **futureproof said:**
> haha @ falling off!  

you dont happen to have a p180 case do you?

my 8800gts is such a tight fit, I had to put the sata drives where it ends because the ide just wouldnt fit by 2mm

DOH just read your sig!  isnt that a great case!

haha, it is a great case. Well built. Just a few little niggly issues. It needs to be at least 2cm longer for a comfy fit and the stickers on the back of the 12cm fans can come loose and start flapping.

---

### Post by futureproof on 2008-03-11
A little bit longer would be good, does yours have the liquid cooler holes in the back?

---

