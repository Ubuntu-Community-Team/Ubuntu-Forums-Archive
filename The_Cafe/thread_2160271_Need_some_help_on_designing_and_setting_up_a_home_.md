---
title: "Need some help on designing and setting up a home multimedia system."
date: 2013-07-06
forum: The Cafe
---

### Post by legolas_w on 2013-07-06
Greetings,

I thought I can get some help on how to design and setup a home multimedia system.

What I have:

[LIST]
[*]I have some external hard disks which contains my video and music files (most importantly videos).
[*]I have two TV that I want to be able to watch any of the videos stored on those external drives in any of these two TVs without disconnecting and connecting them between the TVs.
[*]I have wired and wireless internet across the home.
[/LIST]


I was thinking whether it is possible to have a setup like this:

[LIST]
[*]Get two Raspberry Pi or something similar and connect them to both TVs using HDMI port.
[*]Get an old laptop or tower and connect all hard disks to that laptop/tower and keep it in a closet and connect it to the network
[*]Make the Raspberry Pi (or similar device) to read the files over the network and play them on the TV.
[*]Have some Android app on my phone/tablet to control the playback
[/LIST]

Is that possible or I am taking things too simple and such a setup cannot happen?

Any help or verifying/ enhancing/ recommending tools/hardware/software is very welcome.

Thanks.

---

### Post by DJ_Max on 2013-07-06
I have a PandaBoard ES running XMBC connected to my television, I either hook my HDD directly up to it, or access files on my Desktop via NFS over ethernet.

I just use a small keyboard to control playback, since it's mapped to characters already.

---

### Post by Paqman on 2013-07-06
> **legolas_w said:**
> 
[*]Get two Raspberry Pi or something similar and connect them to both TVs using HDMI port.

Totally doable. I recommend [Raspbmc]("http://www.raspbmc.com/"), it's the RPi version of XBMC on top of Raspbian. It's a doddle to install and works well, you'll get sound and CEC over HDMI if you want. 720p playback is buttery smooth, I've had very slight issues with 1080p but this could well have been my network.
> 
[*]Get an old laptop or tower and connect all hard disks to that laptop/tower and keep it in a closet and connect it to the network
[*]Make the Raspberry Pi (or similar device) to read the files over the network and play them on the TV.

Again, very doable. You could use a RAID array in an old tower or something like a Proliant microserver, or one of the off-the-shelf ARM/Atom NAS boxes. XBMC can speak all the usual network protocols (SMB/CIFS, NFS, etc) so you can set the shares up however is convenient to you.
> 
[*]Have some Android app on my phone/tablet to control the playback

The official XBMC Android app works beautifully on both tablets and phones. Highly recommended, get it from the Google Play store (it's free).

---

### Post by Gnawnsense on 2013-07-06
I installed PLEX to my main machine, selected the folders where my media was contained, purchased a ROKU 3 ($99) for my living room, and a Roku LT ($49.99) or Roku 2 XD ($79.99) in any other room with a television, and voila -- one of the easiest and cost effective multimedia solutions I came across.

The PLEX app for viewing content on the Roku is free, as is the PLEX server. It also has the nifty Android/iOS remote if you opt to not use the Roku remote. But I love the Roku remote due to the quality of the audio that you get when you utilize the headphone jack. Really amazing and simple feature.

Cost effective solution, and virtually no setup with Plex. Just download, select media folders, and you're good to go. Granted, you might be looking for a system that's setup a bit different, but this worked for me quite well.

---

### Post by Double.J on 2013-07-06
> **legolas_w said:**
> 

[LIST]
[*]Get an old laptop or tower and connect all hard disks to that laptop/tower and keep it in a closet and connect it to the network
[/LIST]
Just to add a quicky - I wouldn't recommend keeping a desktop box in a closet, particularly during the summer months due to airflow.  That said an old desktop may be better suited to the task than an old laptop as the laptop will likely have a max of 2 x 2.5" bays for hdds with the ODD removed and they wouldn't provide enough power for desktop drives. You could caddy the drives, but each caddy would need it's own additional power supply - also old laptops are a lot more costly than a 20 quid ebay box ... Especially if you have to buy a bunch of caddies ;)

i use an old netbook motherboard due to low power usage, but then the 1tb drive is all I need.

---

### Post by Roasted on 2013-07-06
Raspberry Pi + OpenELEC = winner. I've tried many of the XBMC spins for the Raspberry Pi. OpenELEC was the best and most stable in my experience.

---

### Post by speedwell68 on 2013-07-07
> **Roasted said:**
> Raspberry Pi + OpenELEC = winner. I've tried many of the XBMC spins for the Raspberry Pi. OpenELEC was the best and most stable in my experience.

Openelec is the by far the best XBMC distro on the Pi.  What I have done is overclock my RPi to 800Mhz and then created Openelec's storage on a flash drive instead of the SD card for faster read/write times.  Then I stream video over my home network, either from shared folders on either of my PCs or from a NAS drive connected to my router.  Works well.

---

### Post by legolas_w on 2013-07-07
Thank you all for contributing to the thread. One question, do we know for sure that Raspberry Pi can play full HD? Does its hardware capability lets it play full hd over HDMI?

---

### Post by Paqman on 2013-07-07
> **legolas_w said:**
> Thank you all for contributing to the thread. One question, do we know for sure that Raspberry Pi can play full HD? Does its hardware capability lets it play full hd over HDMI?

Yes, it can. As I mentioned above I've had slight hiccups streaming 1080p, but that could have been my network. I haven't looked into it as I'm not that bothered. 720p playback is excellent.

---

### Post by DJ_Max on 2013-07-07
> **Paqman said:**
> Yes, it can. As I mentioned above I've had slight hiccups streaming 1080p, but that could have been my network. I haven't looked into it as I'm not that bothered. 720p playback is excellent.

Wired or Wireless? I only have issues over WiFi on full 1080p

---

### Post by Paqman on 2013-07-07
Wired, but it's on a splitter, so isn't a particularly quick bit of cable. I should really get a switch and gigabit that segment up, especially since I'm getting a fibre connection installed tomorrow.

---

