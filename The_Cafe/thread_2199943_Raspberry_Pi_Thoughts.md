---
title: "Raspberry Pi Thoughts"
date: 2014-01-16
forum: The Cafe
---

### Post by punkboy22 on 2014-01-16
Curious on what you guys think of the Raspberry pi thinking about picking one up to do a file server sort of thing with it attached to a 2TB external harddrive? 

Good idea or Dumb Idea?

---

### Post by Don_Stahl on 2014-01-16
You might check this topic: [http://ubuntuforums.org/showthread.php?t=2154216](http://ubuntuforums.org/showthread.php?t=2154216)

Upshot is Ubuntu probably won't run on an ARM processor, but Raspian Wheezy (Debian fork) will.

---

### Post by papibe on 2014-01-16
Hi punkboy22.

It would work and it would be very low power consuming. Make sure the external drive has its own power supply as the Pi won't be providing much power over USB.

There are some limitations though. If you have a gigabit network, the Pi would be your bottle neck because it's only 100Mb/s.

Some people, including me, have experienced different speeds inbound and outbound. Inbound (to the Pi) it's fine, however outbound (from the Pi to another device), it is disappointedly slow: around ~30Mb/s.

Since I'm using it as a HTPC (running raspbian) that's not a problem, but I can imagine that as file server it would have that limitation.

Just my thoughts,
Regards.

---

### Post by Linuxratty on 2014-01-16
I think it has a lot of potential!
Someone on our forum (see link in sig) has plans for using one with his chickens.

---

### Post by corbin.loftis on 2014-01-19
My work (an off-campus bookstore) is planning on switching all the computers that the clerks use to Raspberry Pi, because of cost reasons and the need for upgrades. The computers that they're running now are all Windows 98 or XP. Personally, I think they should shoot for higher specs than the Pi offers, but then again, they're cheap.

---

### Post by Bucky Ball on 2014-01-19
> **corbin.loftis said:**
> My work (an off-campus bookstore) is planning on switching all the computers that the clerks use to Raspberry Pi, because of cost reasons and the need for upgrades. The computers that they're running now are all Windows 98 or XP. Personally, I think they should shoot for higher specs than the Pi offers, but then again, they're cheap.

Off topic, but I wouldn't run a production/work environment on a RPi. They are great and I have been using one as a media server for about a year, but they are temperamental and never really intended as more than an educational tool, tweaking and experimenting. The enthusiastic Linux community has done the rest and designed new roles for the little tyke.

I wouldn't go there. There are other, more reliable, options which are NOT designed as tweak boxes.

---

### Post by mastablasta on 2014-01-20
There are also cheap and faster solutions for that other than RPi. Raspbery pi is kind of slow for desktop use.

[http://en.wikipedia.org/wiki/List_of_single-board_computers](http://en.wikipedia.org/wiki/List_of_single-board_computers)

many of them cost only a few $ more than the Pi and are a lot faster.

---

### Post by 3rdalbum on 2014-01-21
> **mastablasta said:**
> There are also cheap and faster solutions for that other than RPi. Raspbery pi is kind of slow for desktop use.

[http://en.wikipedia.org/wiki/List_of_single-board_computers](http://en.wikipedia.org/wiki/List_of_single-board_computers)

many of them cost only a few $ more than the Pi and are a lot faster.

The main advantages of the Raspberry Pi are its large developer community, abundance of custom-made shields, and maybe the low cost of the actual unit itself. Otherwise, other similar boards are better, especially if you're going to run a desktop.

I too have heard that the Pi is a bit flaky at times, especially its USB. I've also heard it's not very tolerant of brownouts or low-quality USB chargers. Probably not quite appropriate for a file server.

You might do better with one of the more popular Android media boxes (the ones made to plug into your TV) like a Rikomagic MK802. You can install Ubuntu onto certain models although I haven't tried it myself, and I haven't had any power/USB troubles with my unit. I do use a decent quality USB charger, though (official Apple iPhone charger). The MK802 and later versions/variants have a lot more processing power than the Pi, and are also very small and energy efficient.

---

### Post by mastablasta on 2014-01-22
yup plenty of andorid boxes. and they have wuad core CPU and way more ram. but they are a bit more expencive. but they probably can be used as normal desktop. especialyl if one can isntall UButnu ARM image on them

---

### Post by help_me2 on 2014-01-22
> **Bucky Ball said:**
> they are temperamental and never really intended as more than an educational tool, tweaking and experimenting.
I have to disagree. I've been using one as an XBMC media player (think Roku) and it's been wonderful. As a matter of fact, if someone gave me a brand new roku player, I would sell it, as I think an XBMC player is better once you add repos and tweak it.

---

### Post by linuxyogi on 2014-01-27
I know how to assemble PCs but I am not really sure how to setup a R Pi. I mean what kind of PSU does it need ? I have seen a Raspberry Pi in in a transparent plastic enclosure in Linux Action Show on youtube so I got answer to that question. One more thing my Samsung LCD monitor has a DSUB port and a DVI port but not HDMI so I guess I will have to use a HDMI to DVI cable but when I googled about it I found people having issues using that kind of cable. I actually read this on raspberry pi forums.

---

### Post by Roasted on 2014-01-27
I have a raspberry pi sitting on the shelf. I'm going to set it up as a secondary backup server. I have a low power i3 server that I use for all of my home-server needs, but I wanted to set up something on my LAN for more up to date backups to accompany my current once-a-month syncs I do to an external drive and then store in my desk at work. This will be using a 1TB (soon to be 3TB) external HDD with Raspbian. It will hardly run anything else. My main server will just rsync data over ssh to it likely twice a day. That way if my RAID explodes or my server itself self destructs then worst case scenario I have all data as of 12 hours ago backed up, along with the obvious benefit of an offsite external HDD in case (God forbid) the house ever burns down.

---

### Post by Bucky Ball on 2014-01-27
I'll just throw this in here as not sure if anyone has ...

RPi MUST boot from the SD, but ... you can store everything else on a USB. Much better performance. What improves the performance further still is a powered hub rather than the USB into the PI. The USB install and powered hub are must haves IMHO (DON'T attempt to power a hub from the Pi, incidentally). If you're using it on anything with a screen, don't think twice.

RaspBMC allows you to install using the USB and SD in Linux or Windows has an easy GUI installer that can include the USB with a click. Not sure about other distros. 

Thought I'd mention it ... ;)

---

### Post by mastablasta on 2014-01-28
yah well you can also overclock it for some extra speed.

external HDD also needs (for data safety) separate power source or USB hub that is powered separatelly. 

but this really is "the little computer that could...". it's cheap, quiet, low on power usage. ok so it can't run fast but it does certain jobs quite well. 

we have a saying that you goes something like "you get far by going slow" :-D At the moment it serves as media center. in the future if i have some money saved up i will make an offsite backup mashcine. the family photos are now on 3 disks/computers but all are in same room. ouch.

---

### Post by mastablasta on 2014-01-28
> **linuxyogi said:**
> I know how to assemble PCs but I am not really sure how to setup a R Pi. I mean what kind of PSU does it need ? I have seen a Raspberry Pi in in a transparent plastic enclosure in Linux Action Show on youtube so I got answer to that question. One more thing my Samsung LCD monitor has a DSUB port and a DVI port but not HDMI so I guess I will have to use a HDMI to DVI cable but when I googled about it I found people having issues using that kind of cable. I actually read this on raspberry pi forums.

PSU is like for mobile phones. suggets you buy a good one along with Pi. same goes for SD card and box (if you want to).

as for DVI you would need to try it out. what kind of issues are they having? sound is not transmited via DVI (at least with most DVI ports it's not). i have AMD card on computer with DVI and is attached to HDMI port on LG TV. there is no sound going via that cable, but otherwise it works fine.

---

### Post by help_me2 on 2014-01-29
> **linuxyogi said:**
> I know how to assemble PCs but I am not really sure how to setup a R Pi. I mean what kind of PSU does it need ? I have seen a Raspberry Pi in in a transparent plastic enclosure in Linux Action Show on youtube so I got answer to that question. One more thing my Samsung LCD monitor has a DSUB port and a DVI port but not HDMI so I guess I will have to use a HDMI to DVI cable but when I googled about it I found people having issues using that kind of cable. I actually read this on raspberry pi forums.
The PSU I use is just a 2 amp micro usb I got off of amazon. For the rest of my peripherals, I use a powered usb hub.

Using the hdmi to dvi cable, I think you'll have to set the video settings manually. There are **a lot** of youtube how-to's on setting up and using a pi.

---

