---
title: "Home Server / File Server build advice."
date: 2012-01-11
forum: The Cafe
---

### Post by sb360 on 2012-01-11
Hi,
I am looking to build myself a little home/file server to run on Ubuntu (Probably 12.04 LTS when available but 11.10 until then). It will mostly be used for NAS storage, as a torrent client and for media streaming but I would like something fairly adaptable, as I may well want to convert to a semi-gaming or editing rig in the future. I don't want it to run 24/7 but will probably have it running for up to a week at a time so something reasonably energy efficient would be good. This will be my first full build and so I am writing this post to ask for some advice, below I have outlined my current thinking, but would greatly appreciate any help, suggestions and problems with the current plan.

My thinking was to base this on an AMD Fusion Chip (Probably [[COLOR="RoyalBlue"]**A6-3500**[/COLOR]](http://www.ebuyer.com/281336-amd-llano-a6-a3500-2-1ghz-socket-fm1-3mb-l2-cache-retail-boxed-ad3500ojgxbox)) as its relatively low power (65W TDP) and yet plenty powerful enough, particularly taking into account the onboard graphics which I understand is important for transcoding and streaming.

I don't want anything too big so was looking at a micro ATX case, probably something from an HTPC line as I like the style and size and want to have it on, rather than under, a desk. [[COLOR="RoyalBlue"]**[COLOR="RoyalBlue"]This is the favourite so far.[/COLOR]**[/COLOR]](http://www.ebuyer.com/130945-antec-nsk-2480-matx-desktop-case-with-380w-earthwatts-psu-0761345-00281-3)

I don't know too much about motherboards but was looking at something along the lines of [**[COLOR="RoyalBlue"]this[/COLOR]**](http://www.overclockers.co.uk/showproduct.php?prodid=MB-497-AS&groupid=701&catid=1903&subcat=2058) as it has onboard gigabit lan, plenty of I/O ports and is made by a company I have heard of.

Software wise, although I have been using Ubuntu on and off for a number of years, I am not yet confident enough to have a command line only interface. Because of this I would intend to use standard Ubuntu running programs such as Transmission and Mediatomb to fulfill my needs.

Any help, advice or pointing out of problems is greatly appreciated.

Thanks in advance
Sam.

---

### Post by BrokenKingpin on 2012-01-11
I am not up on my AMD chips so I have no comments on the chip you mentioned, but an Intel i3 might be a good way to go. Plenty of performance and relatively low power usage.

---

### Post by sb360 on 2012-01-11
> **BrokenKingpin said:**
> I am not up on my AMD chips so I have no comments on the chip you mentioned, but an Intel i3 might be a good way to go. Plenty of performance and relatively low power usage.

That was my first thought as well, but as far as I can see it uses a little bit more power and costs a bit more, the big draw of the AMD was the powerful onboard graphics chip, although admittedly I have no knowledge at all of Ubuntu on the new Fusion chips.

---

### Post by Buntumatic on 2012-01-11
For a file server Intel Atom will do. I wouldn't transcode on Atom, though.

---

### Post by CharlesA on 2012-01-11
Keep in mind that that case only has *two* 3.5" bays, so you'd have to use USB drives for the storage portion.

I was going to go the HTPC-size route, but I wasn't able to find any that could hold the number of drives that I wanted to use and keep them cool at the same time.

I ended up just getting a regular desktop midtower and cramming everything into it. It just sits in the corner of one of my room now, looking pretty. ;)

---

### Post by sb360 on 2012-01-11
I think I would only need 2 bays though, one for the 250GB boot drive, which is actually 2.5" but would still fit, and one for my 2TB Data drive.

On a related note, this 2TB drive is currently inside an old WD Desktop Hard drive that I just bought cheap from work, are these normally 3.5" or 5.25", if its the latter then I definitely need to change the case.

Would cooling be an issue with that case? the reviews say it is good for that.

---

### Post by sb360 on 2012-01-11
> **Buntumatic said:**
> For a file server Intel Atom will do. I wouldn't transcode on Atom, though.
Yeah a friend of mine has an Atom setup, nothing wrong with it but its not up to HD streaming and streaming/transcoding are a big part of the plan for my machine, I will also probably eventually want to turn it into a normal desktop machine and I want something more powerful than an Atom if I do choose to go down that route.

---

### Post by cariboo on 2012-01-11
I have to agree with CharlesA, get a case that allows you to install many hard drives, as once you have the server up and running, you'll find your data will fill your current hard drive, and you'll be soon looking for more storage space.

The other thing to keep in mind, is that hard drives fail, always have a good backup strategy in place, so that  when disaster happens, you can be up and running again with out a lose of data.

---

### Post by sb360 on 2012-01-11
Thats probably sensible advice, does anyone know of any cases with a similar form factor that would accommodate more than 2 HDDs?

I do really want to keep something similar in style because it  will have to go on top of the desk. The machine is partially for use as a backup anyway, so at any point everything should be on at least one other computer on the network. Anything truly important is on Dropbox anyway.

---

### Post by sb360 on 2012-01-11
Or I could just use the 5.25" bays with adapters for 3.5", that would give me 4 drives to play with, that would seem to be enough, because otherwise that case seemed perfect for size (and price) and the included PSU.

---

### Post by CharlesA on 2012-01-11
> **sb360 said:**
> Thats probably sensible advice, does anyone know of any cases with a similar form factor that would accommodate more than 2 HDDs?

I do really want to keep something similar in style because it  will have to go on top of the desk. The machine is partially for use as a backup anyway, so at any point everything should be on at least one other computer on the network. Anything truly important is on Dropbox anyway.
The one I tried to use was this [one]("http://www.newegg.com/Product/Product.aspx?Item=N82E16811204037&nm_mc=OTC-Froogle&cm_mmc=OTC-Froogle-_-Cases+%28+HTPC/Media+Center+Cases%29-_-NMEDIAPC-_-11204037").

It's bloody gigantic and not that pretty looking (and it ran hot).

---

### Post by sb360 on 2012-01-11
> **CharlesA said:**
> The one I tried to use was this [one]("http://www.newegg.com/Product/Product.aspx?Item=N82E16811204037&nm_mc=OTC-Froogle&cm_mmc=OTC-Froogle-_-Cases+%28+HTPC/Media+Center+Cases%29-_-NMEDIAPC-_-11204037").

It's bloody gigantic and not that pretty looking (and it ran hot).

What did you put in it? was it a server build or a htpc?
I still quite like the look of my original one, if I can use the 5.25" bays for extra HDDs if required I may still go with with that.

---

### Post by CharlesA on 2012-01-11
> **sb360 said:**
> What did you put in it? was it a server build or a htpc?
I still quite like the look of my original one, if I can use the 5.25" bays for extra HDDs if required I may still go with with that.
Server build.

---

