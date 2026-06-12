---
title: "Help buying a server"
date: 2013-06-18
forum: Server Platforms
---

### Post by cpu2007 on 2013-06-18
I hope someone can give me some advice on this.
I'd like to setup a low powered server at home, something not too expensive but that could do things such as :
-be connected to few cctv cameras through wireless and wire and monitor motions, saves videos of detections.
-allow me to run backups and save my other laptops data in the server hdd.
-allow me to run some normal programs such as torrents etc.

What sort of hardware would you advice in order to build something appropriate for the tasks I need?
and yeah, I'd like to run ubuntu on it, do you think that will do the job?

Thank you

---

### Post by volkswagner on 2013-06-18
I just picked up [one of these]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813128585").  They sip electric and can hold 16Gig's RAM!

I think this board or similar will be up to the task.

---

### Post by 3L33T on 2013-06-18
> **cpu2007 said:**
> 
...
I'd like to setup a low powered server at home, *_[SIZE=2]something not too expensive[/SIZE]_* but that could do things such as :
...


You specified everything nicely except your budget.   How much is your budget for this *not too expensive* machine?  Do you need just the CPU or the whole kit and kaboodle (monitor, keyboard, mouse)?

There are old but nicely spec'd and decent refurb PC's between $179-$299 [HERE]("http://www.tigerdirect.com/applications/category/category_tlc.asp?CatId=2628").

---

### Post by mörgæs on 2013-06-18
It sounds like a light workload, and I don't think you need anything expensive. 

I think you should begin with a Xubuntu server installation on any random box you have around. When you have experience with that you know if there's a reason to upgrade.

---

### Post by rubylaser on 2013-06-18
> **volkswagner said:**
> I just picked up [one of these]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813128585").  They sip electric and can hold 16Gig's RAM!

I think this board or similar will be up to the task.

+1.  I have (3) of these Sandy Bridge Celeron 847 boards at home.  They all work great, where inexpensive, and use very little power. I use (2) of these Gigabyte boards to run Openelec for XBMC and a [Biostar version that came with 8GB of RAM]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813138368") for my fileserver with (8) 2TB disks in a [SnapRAID]("http://zackreed.me/articles/72-snapraid-on-ubuntu-12-04") double parity array (I needed the PCIe slot for my IBM M1015 card). 

The fileserver runs SABnzbd+, Sickbeard, Couchpotato, Headphones, Syslog-NG, Nut, LAMP, Unifi Controller, and plexmediaserver without breaking a sweat. This board should be more than up to the tasks you mentioned.

[Openelec]("http://openelec.tv/") worked great and works out of the box, but I did need to disable rc6 in Ubuntu by editing /etc/default/grub to prevent the box from randomly crashing.  Editing the GRUB_CMDLINE_LINUX_DEFAULT line as follows and rebooting made my fileserver rock solid (Ubuntu 12.04 Server).

```
GRUB_CMDLINE_LINUX_DEFAULT="i915.i915_enable_rc6=0"
```

The [Ivy Bridge]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813128598") version of this board is a little more expensive, more powerful, and uses even slightly less power.

---

### Post by matt_symes on 2013-06-18
Hi

Interesting looking board. It may do what i need as well.

Does anybody have any statistics on the actual power usage ?

My google-fu must be letting me down as i could not find any when i searched.

Kind regards

---

### Post by CharlesA on 2013-06-18
> **rubylaser said:**
> +1.  I have (3) of these Sandy Bridge Celeron 847 boards at home.  They all work great, where inexpensive, and use very little power. I use (2) of these Gigabyte boards to run Openelec for XBMC and a [Biostar version that came with 8GB of RAM]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813138368") for my fileserver with (8) 2TB disks in a [SnapRAID]("http://zackreed.me/articles/72-snapraid-on-ubuntu-12-04") double parity array (I needed the PCIe slot for my IBM M1015 card). 

That Biostar one is nice. I'm getting the itch to try building an HTPC now.. except with my media server being my file server....

What kind of cases do you use with them? The last HTPC I built was in a monster case. >.<

---

### Post by rubylaser on 2013-06-19
> **CharlesA said:**
> That Biostar one is nice. I'm getting the itch to try building an HTPC now.. except with my media server being my file server....

What kind of cases do you use with them? The last HTPC I built was in a monster case. >.<

I used [this case]("http://www.newegg.com/Product/Product.aspx?Item=N82E16811154091&Tpk=apex%20mi-008&IsVirtualParent=1").  It's cheap, quiet, and is about the size of a Shuttle case cut in half vertically.  Also, my fileserver with (9) total disks uses less than 30 watts of power when my data disks are spun down.  This saves me a MASSIVE amount of electricity compared to my previous Core2Quad setup (100+ Watts).

Here's a couple pictures of my development area with two of these Celeron 847 boxes running (one of them was one of my fileservers and the second is an ipfire box), and the two budget gigabit switches, and then a second picture of my APC showing the current load (41 Watts).  Don't comment on the cable management, this is a development / working / testing area :)


[IMG]http://zackreed.me/images/Overall.png[/IMG]

[IMG]http://zackreed.me/images/APC.png[/IMG]

---

### Post by CharlesA on 2013-06-19
Cool. I was actually looking at that case but I had never heard of the APEX brand before. I really like that it has an internal 3.5" bay, and since that Biostar ITX board has Intel graphics, that would work out nicely.

Sidenote, I don't see any pictures. :p

---

### Post by rubylaser on 2013-06-20
> **CharlesA said:**
> Sidenote, I don't see any pictures. :p

Hopefully, you can view them now.  I moved them out of Evernote, and hosted them on my webserver.

---

### Post by CharlesA on 2013-06-20
> **rubylaser said:**
> Hopefully, you can view them now.  I moved them out of Evernote, and hosted them on my webserver.

Works now. :)

Nice setup.. and the cable management look a bit like the mess I have around my router/switch. Heh.

---

### Post by Grenage on 2013-06-20
> **CharlesA said:**
> What kind of cases do you use with them? The last HTPC I built was in a monster case. >.<

Screw compact PC cases, stick to **monsters**! You can always stick them in a cupboard somewhere, and run a dinky front end by the TV; or HDMI/IR over cat6, that's even more practical and minimalist.

---

### Post by CharlesA on 2013-06-20
> **Grenage said:**
> Screw compact PC cases, stick to **monsters**! You can always stick them in a cupboard somewhere, and run a dinky front end by the TV; or HDMI/IR over cat6, that's even more practical and minimalist.

Haha. The first HTPC I built was running a Micro ATX board, full size PSU and huge TV capture card (which failed miserably, cuz my cable provider encrypts their HDTV channels and their support had no idea what a cablecard was. :o

The case I used took up almost the entire cabinet:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16811204032](http://www.newegg.com/Product/Product.aspx?Item=N82E16811204032)

All cuz I wanted to throw a big card in there. I'll be sticking with a smaller one if I decide to do it again.

---

### Post by Grenage on 2013-06-20
Well at least you can easily throw in lots of extra drives, be they in bays or cable-tied to random sections.  Can't do that with an all-in-one tiny PC. ;)

---

### Post by CharlesA on 2013-06-20
> **Grenage said:**
> Well at least you can easily throw in lots of extra drives, be they in bays or cable-tied to random sections.  Can't do that with an all-in-one tiny PC. ;)

True. I don't have it any more and I was thinking of using it as a file server, but it ran way too hot for my liking.

At least there are advantages of having **monster** cases. :p

---

### Post by rubylaser on 2013-06-20
I would really suggest breaking apart your media storage from your playback devices.  In that picture is one of my media servers.  Around the house, I have (4) small Openelec XBMC boxes and (1) iMac + Plex in the kids' area.  This makes your playback area very quiet (no drives spinning). 
 
Charles, one more option for a Celeron 847 based playback device, the [Intel NUC]("http://www.newegg.com/Product/Product.aspx?Item=N82E16856102004&Tpk=celeron%20nuc&IsVirtualParent=1"). That thing is REALLY small and comes with a VESA mount to attach it to the back of a TV, but will end up costing a little more unless you run the OS off of a thumb drive, you need to use an mSATA drive if you want a drive inside the case (and you need to buy a 3 prong power cable too).

---

### Post by Grenage on 2013-06-20
> **CharlesA said:**
> At least there are advantages of having **monster** cases. :p

I'm probably just trying to make myself feel better about having a massive beast in the livingroom.  I had grand plans to move it under the stairs and route HDMI to the main rooms, but I never got round to it!

---

### Post by CharlesA on 2013-06-20
> **rubylaser said:**
> I would really suggest breaking apart your media storage from your playback devices.  In that picture is one of my media servers.  Around the house, I have (4) small Openelec XBMC boxes and (1) iMac + Plex in the kids' area.  This makes your playback area very quiet (no drives spinning). 

I think that's where I originally messed things up. The huge case I had was running 4 fans + CPU fan + PSU fan, so while it wasn't super loud, you could hear it and that kinda ruined things.
 
> Charles, one more option for a Celeron 847 based playback device, the [Intel NUC]("http://www.newegg.com/Product/Product.aspx?Item=N82E16856102004&Tpk=celeron%20nuc&IsVirtualParent=1"). That thing is REALLY small and comes with a VESA mount to attach it to the back of a TV, but will end up costing a little more unless you run the OS off of a thumb drive, you need to use an mSATA drive if you want a drive inside the case (and you need to buy a 3 prong power cable too).

That box looks awesome. It looks like it would need an SSD and RAM and then be good to go. It's only 4 inches by 4 inches with is just insane.

I originally wanted to be able to record stuff and stream over the network and I really should have done my research first by my cable company didn't do cable cards at the time (I have no clue if they do now or not, but meh). That would have saved me from getting the tv tuner and needed a bigger case to fit it.

---

### Post by rubylaser on 2013-06-20
> **CharlesA said:**
> I think that's where I originally messed things up. The huge case I had was running 4 fans + CPU fan + PSU fan, so while it wasn't super loud, you could hear it and that kinda ruined things.
 


That box looks awesome. It looks like it would need an SSD and RAM and then be good to go. It's only 4 inches by 4 inches with is just insane.

I originally wanted to be able to record stuff and stream over the network and I really should have done my research first by my cable company didn't do cable cards at the time (I have no clue if they do now or not, but meh). That would have saved me from getting the tv tuner and needed a bigger case to fit it.

It does need RAM, but you can't use a 2.5" SSD, you would need to buy an mSATA drive for it to fit.

---

### Post by CharlesA on 2013-06-20
D'oh! I've never heard of a mSATA drive before. I guess the thumb drive approach would be easier to manage. :)

---

### Post by rubylaser on 2013-06-20
[This]("http://www.newegg.com/Product/Product.aspx?Item=N82E16820167143") is what they look like.  They are very nice if you are willing to pony up the bucks for one, but obviously more expensive than an 8GB thumb drive :)

---

### Post by CharlesA on 2013-06-20
Crikey! Those are tiny.

---

