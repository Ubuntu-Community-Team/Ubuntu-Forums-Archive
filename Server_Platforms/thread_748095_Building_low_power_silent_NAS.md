---
title: "Building low power silent NAS"
date: 2008-04-07
forum: Server Platforms
---

### Post by jethro10 on 2008-04-07
Right,
after buying a NAS and finding it a bit limiting, I'm going to build a NAS,

using a micro ITX board and external UPS.
I'm looking at as low power as possible, and fanless. Going to put Ubuntu server on it, s/w site I have no issues.
Need to be small and unobtrusive, hence itx

Questions though :-

Anyone any experience with ITX stuff

It Dont need to be ultra powerfull, serving uPNP, Itunes, storage, apache for simple CMS etc. What level VIA process would be ok, they seem to be the fanless ones.

IDE or Sata to CF converters. What about installing ubuntu on a CF flash, so cheap I dont mind replaciing it, no swap will make it last longer though? Is this a sensible choice then put storage on a seperate disk

any alternative thoughts? must run ubuntu and be quiet!

Thanks for any thoughts,
Jeff

---

### Post by jethro10 on 2008-04-07
Browsing away, just found this 
[http://www.tmc-uk.com/Products/open-e/open-e.htm](http://www.tmc-uk.com/Products/open-e/open-e.htm)

Looks like a commercial solution of a flash based product in a real neat package for an ide slot

Nice.

Jeff

---

### Post by smileypaul on 2008-04-07
Be sure to check out FreeNAS as well.

---

### Post by jethro10 on 2008-04-10
> **smileypaul said:**
> Be sure to check out FreeNAS as well.

This seems quite limited on extendability.

However I have found Clarkconnect which is a redhat based nas/server with full extendability to the extend of how far redhat can be extended.


Jeff

---

### Post by simonn on 2008-04-10
Have a look at getting a Koolu. Very low power 8-13W!!! Less than your average external 3.5" drive. It can only take an  80Gb internal hard drive, but has 4 USB ports, so you could plug in 4 USB devices.

I do not really use mine as a NAS, but I have the 80Gb drive + 160Gb 2.5" external and it is virtually silent. I use electrical tape to mask the LEDs. 4 x 250gb 2.5" external drives would give ~1TB and be hotpluggable and virtually silent.

See my post here [http://forums.slimdevices.com/showpost.php?p=246338&postcount=27](http://forums.slimdevices.com/showpost.php?p=246338&postcount=27)

---

### Post by jethro10 on 2008-04-10
> **simonn said:**
> Have a look at getting a Koolu. Very low power 8-13W!!! Less than your average external 3.5" drive. It can only take an  80Gb internal hard drive, but has 4 USB ports, so you could plug in 4 USB devices.

I do not really use mine as a NAS, but I have the 80Gb drive + 160Gb 2.5" external and it is virtually silent. I use electrical tape to mask the LEDs. 4 x 250gb 2.5" external drives would give ~1TB and be hotpluggable and virtually silent.

See my post here [http://forums.slimdevices.com/showpost.php?p=246338&postcount=27](http://forums.slimdevices.com/showpost.php?p=246338&postcount=27)

Thanks. It looks good.
What i'm finding is there is a lot of options here in this market, but not very well publicised.
A shame

J

---

### Post by Cancerkazoo on 2008-04-10
I built a NAS, running Ubuntu server 7.10 + Samba, on a Jetway mini ITX board. It does have a fan, but it is in my basement by all my other network equipment so I can't hear it anyway. It has 2 gb LAN ports which I thought was nice.

Here is my layout.

[img]http://home.comcast.net/~cancerkazoo/images/pc/network.jpg[/img]

I bet you could find a fanless heatsink for it. it is supposed to pull 25w max + your drives.

---

### Post by kerry_s on 2008-04-10
my friends looking to do a similar project. he's looking at the artigo build kit, he want to put a cf card adpter & cf in place of the hd for the os and storage will be by usb hd's, he keeps different things on the various usb hd's and can just swap the usb drives for different things. for instance swapping the drives to his music & movies drives(yes, he has that many) then there's his office drives, with various things. etc..

anyway's-> [http://www.linuxdevices.com/news/NS4473724652.html](http://www.linuxdevices.com/news/NS4473724652.html)

---

### Post by netlogic on 2008-04-11
I can't find the link, but there are many sites show you how to mod your drive to be very silent. Also, liquid cooliants have became very cheap. We do have few servers without any fans. We got too tired of admins passing out during the winter, because it was too cold at NOC.

---

### Post by jethro10 on 2008-04-11
> **Cancerkazoo said:**
> I built a NAS, running Ubuntu server 7.10 + Samba, on a Jetway mini ITX board. It does have a fan, but it is in my basement by all my other network equipment so I can't hear it anyway. It has 2 gb LAN ports which I thought was nice.

Here is my layout.

[img]http://home.comcast.net/~cancerkazoo/images/pc/network.jpg[/img]

I bet you could find a fanless heatsink for it. it is supposed to pull 25w max + your drives.

Well I've ordered a jetway board, 1.2Ghz Via processor - cooled by heatsink only, fanless, 1Gb memory, Case, 500Gb sata disk etc.

Looks like it will be low powered and quiet(ish)

Jeff

---

### Post by volkswagner on 2008-04-11
Build your own Koolu.  This MOBO has CF slot onboard.

[http://www.newegg.com/Product/Product.aspx?Item=N82E16813153096]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813153096")

Very "COOL".  You have tempted me into one.  7 WATTS, WOW!

---

### Post by jethro10 on 2008-05-13
I've recently been asked a few questions by PM so will answer here.

I'm from the UK so bought from here [http://www.itx-warehouse.co.uk](http://www.itx-warehouse.co.uk)
and this is the one I got
[http://www.itx-warehouse.co.uk/Product.aspx?ProductID=631](http://www.itx-warehouse.co.uk/Product.aspx?ProductID=631)

For a headless server it's great, but the built in graphics card does not have a decent driver and looks very poor.
I actually installed gnome as it's easier to set stuff up, and the graphics are just good enough to get by.
However in normal use, I just switch on and it gets to a log on prompt I guess, as its healess mostly, and just tap the power button on the front and it powers down by itself. A worthwhile compromise between a pure server and ease of use when setting up.

It's ran flawlessly since I got it BTW.

Jeff

---

### Post by Cancerkazoo on 2008-06-07
Glad to hear it is working for you.

Just running mine headless with putty and openssh. It works great that way.

---

### Post by drsox1899 on 2008-06-12
Can someone direct me to a good HowTo for this ?  I want to do this but don't need the low power silent parts as it will be on the end of a GB LAN and my local PCs are very very silent.

It's the SW that I have as yet no experience in.  ClarkConnect was going to be one of my items to look at, but I feel I should give U8.04 a go as I'm happy using this on 3 PCs already.

Thanks

PS ClarkConnect has fallen off the table.  Just too macho.  Hey, a mouse would be nice in a GUI !!!  Ubuntu 8.04 server HO !

---

### Post by drsox1899 on 2008-06-18
> **netlogic said:**
> I can't find the link, but there are many sites show you how to mod your drive to be very silent. Also, liquid cooliants have became very cheap. We do have few servers without any fans. We got too tired of admins passing out during the winter, because it was too cold at NOC.


Go look at Silent PC Review

[http://www.silentpcreview.com/](http://www.silentpcreview.com/)

All you need to know about making stuff silent

---

### Post by Uluen on 2008-06-29
FreeNAS limited on extendability?
How did you reach that conclusion? :confused:

---

