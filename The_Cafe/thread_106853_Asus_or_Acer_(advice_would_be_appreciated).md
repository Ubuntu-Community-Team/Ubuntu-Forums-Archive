---
title: "Asus or Acer (advice would be appreciated)"
date: 2005-12-21
forum: The Cafe
---

### Post by dyous87 on 2005-12-21
Ok I'm in the market for a new laptop due to the fact that my old gatway arc200 is starting to die or me and just isnt suiting my needs:

The notebooks I'm interested in right now are as follows:

A custom built on Asus Z71v
-Penitum M 2.26 gigs (sonoma platform)
-1 gig of memory
-an 80 gig sata hard drive (7200 rpms)
-15.4” WSXGA+ (1680X1050) TFT Display
-*Modular* PCI Express Nvidia 6600-128MB
    14.0”x10.8”x1.4”
<6.6lbs

A custom built on Asus Z70va (refresh)
--Penitum M 2.26 gigs (sonoma platform)
-1 gig of memory
-an 80 gig hard drive (7200 rpms)
-15.4” WSXGA+ (1680X1050) TFT Display
- PCI Express Radeon X700 128mb DDR
-carbon alloy chasis with built in bluetooth
     14"x10.5"x1.5" wxdxh
5.60 lbs

or finally...

The Acer Ferrari 4000
-AMD Turion™ 64 Mobile Technology ML-37
1MB L2 cache, 2.0GHz
-1GB (512/512) DDR333 SDRAM
-100 gig hard drive (5400 rpms)
-15.4" WSXGA+ (1680 x 1050)
-ATI® MOBILITYTM RADEON® X700 graphics, 128MB DDR
      14.3" (363.0mm) W x 10.5" (265.7mm) D x 1.2" – 1.4” (30.5mm – 34.3mm) H / 6.3 lb

They all include built in wireless with dvd-r-rw super drives and they are all around the same price range for the most part.

I'm obviously going to install Ubuntu as soon as I get it. I'm just curious as to what would be the better machine and what would be the most compatible with Ubuntu 5.10.

Thanks in advance
-Dave :)

---

### Post by psoleko on 2005-12-21
I want all of them...(wipes drool from chin). Even though I prefer AMD personally the ASUS Z71V would probably be the most comaptible under ubuntu as ATI's drivers are not that great. My ideal laptop which I have yet to find would combine an AMD Turion with Nvidia graphics.

---

### Post by Wallakoala on 2005-12-21
I would say the first one. They are all really good laptops but I have heard that ati support for linux is not-so-good. The last one looks nice because it has the 100 gig hd, but I think that the Pentium M is better than the Turion as far as processors go.

---

### Post by prizrak on 2005-12-21
I like Asus, used to have an Acer desktop and didn't really like it all that much (course that was back in 97 but still)

---

### Post by dyous87 on 2005-12-21
Yea I also thought that same thing about the Z71v. The only reluctance I have with it is that it's a bit heavier the the other two and the chassis is not made of carbon fiber so it is not as durable.

I have also read in places that the screen on the Z71z has the sparkle problem and this is something that would really annoy me. *sighs* It's so hard to get everything you want in one machine lol

---

### Post by mstlyevil on 2005-12-21
When it comes to laptops, all rules are out concerning performance. I would probally go with a pentium M on the z70 if the weight and carbon casing are a concern. Pentium laptop processors are still the best but if you are talking desktops, that is another story. ;)

---

### Post by dyous87 on 2005-12-21
oh...well in that case if i do end up going for the z70va does anyone know how good the screen and built in speakers are...also will I have lots of issues with the ati video adapter since it doesn't work well with linux?

---

### Post by mstlyevil on 2005-12-21
As far as I know the ATI video will work if you do not need 3d enabled by the ATI linux drivers. There is an open source driver that is supposed to unlock the 3D capabilities, but I can not remember what it is for the life of me.

---

### Post by poofyhairguy on 2005-12-21
[QUOTE=dyous87]Ok I'm in the market for a new laptop due to the fact that my old gatway arc200 is starting to die or me and just isnt suiting my needs:

The notebooks I'm interested in right now are as follows:

A custom built on Asus Z71v
-Penitum M 2.26 gigs (sonoma platform)
-1 gig of memory
-an 80 gig sata hard drive (7200 rpms)
-15.4” WSXGA+ (1680X1050) TFT Display
-*Modular* PCI Express Nvidia 6600-128MB
    14.0”x10.8”x1.4”
<6.6lbs
[/QUOTE]

This one. By far. The other two have new ATI cards. New ATI cards is the easiest way to bring pain upon yourself in Linux.

Really. You get the ATI laptops and trouble waits for you!

---

### Post by dejitarob on 2005-12-21
I would definately go with the z70va. I got the z70v before the refresh model came out and I love it. The only difference I would get with your listed specs would be a 400FSB Pentium M so you can do the [pinmod]("http://www.notebookforums.com/showthread.php?t=80879") (can't be done the z71v btw nor an acer I believe). I did it with a 1.7ghz so I am running great at 2.2ghz with ~$300 extra in my pocket :D. I got my system through [http://1toppc.com](http://1toppc.com) and they carried the 400FSB P-M's at the time.

The only downside is the built in speaker's bass is not as good compared to the Dell Inspiron 9300 I traded it in for but that's not a biggie for most people. Another downside like you say could be the ATI driver support. I guess it depends on what you mean by "work well". It is annoying that to change to TV-out you have to edit your xorg.conf (easier to just switch 2 with the settings already in them) and restart X. I don't play games anymore but I was able to get DRI (3-D) working fine on kubuntu with my old Inspiron 9300 which had a ATI x300 card. My FPS were slightly better than in XP for ET too!

---

### Post by poofyhairguy on 2005-12-21
[QUOTE=mstlyevil]As far as I know the ATI video will work if you do not need 3d enabled by the ATI linux drivers. [/QUOTE]

With some of the newest ATI cards, almost NOTHING outside the official ATI drivers work (cept mesa probably). 

> 
There is an open source driver that is supposed to unlock the 3D capabilities, but I can not remember what it is for the life of me.

Its the new dri driver that comes with Xorg7 and it is still absolute crap at this point compared to the Nvidia closed drivers. Those drivers are for people that have a high end ATI card that just moved to Linux. If you have a choice, NEVER buy a new ATI card. Ever.

 Actually...for 3D and eye candy effects almost EVERYTHING is crap compared to the closed Nvidia drivers. The second best option is the ATI 9250s and I hear that in games that the open source drivers is still slower than the flgrx one on the same card. And the flgrx driver is about half as slow as the Window's one and sometimes you have to sacrifice a chicken to get it installed.

When it comes to high end graphics cards and Linux, its either Nvidia or pain. The only downside to the Nvidia driver (besides its closed nature) is the fact that often it does not allow hardware suspend. But often that does not work on newer laptops anyway and I read somewhere  they are working on that. The Linux Nvidia driver has a unified code based with the Windows one (I hear they share like 85% of the same code) and so the performance is  near the Windows driver. No other modern card (now or in the near future) in Linux can boast that claim.

If you can deal with mesa or will be willing to go through the pain of installing the newest ATI driver from their website, don't mind getting the hottest Linux eye candy later than everyone else and will never play a game on the thing that is newer than ET then go ahead and get the one with the ATI card. For me it seems like a waste, but that little list I just said is my favorite parts of Linux.

---

### Post by GreyFox503 on 2005-12-21
I didn't look too deeply, but I'd pick #1

-better mobile processor (intel)
-better graphics card (nvidia)

Pentium Ms are pretty good at managing heat/battery life, and nvidia graphics are usually better w/ linux support.

---

### Post by dyous87 on 2005-12-21
so looks like i better stick with the z71v then...hmm still does anyone know anything about the screen quality that is something that concerns me since i will be using it for graphics and web design. :confused:

---

### Post by psoleko on 2005-12-22
Found a review of the z71v here.
[http://www.notebookreview.com/default.asp?newsID=2346](http://www.notebookreview.com/default.asp?newsID=2346)

---

### Post by dyous87 on 2005-12-22
aright looks like i'm going to go with the Z71v. I could get it from Integrated System Technologies for $2086 US dollars with an 80 gig SATA hard drive and an Intel Pentium M 2.24 gigs and 1 gig of ram. I may wait till after the holidays to see if the prices end up going down.

anyway thanks to everyone for your advice is helping me choose, i really apprreciate it :D

---

