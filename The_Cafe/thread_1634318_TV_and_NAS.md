---
title: "TV and NAS"
date: 2010-11-30
forum: The Cafe
---

### Post by Hexley on 2010-11-30
Anyone here knows how well a NAS works with a TV?
(The NAS will be connected to the network and not directly to the TV...)

---

### Post by cariboo on 2010-11-30
Ive have all my media, video and audio, stored on a server. I have a system running XBMC connected to my TV. I just auto mount the shares in /etc/fstab on boot, and you can't tell that server is located 50 feet away from the house.

---

### Post by Hexley on 2010-11-30
What about ethernet hard drives then? 
If I want something super light....

---

### Post by Zzl1xndd on 2010-11-30
I have a similar set up to cariboo907. You should have any issues as long as your Media streaming device (in my case a Mac Mini) can access the shares. 

+1 to XBMC as well great software.

---

### Post by endotherm on 2010-11-30
> **Hexley said:**
> What about ethernet hard drives then? 
If I want something super light....
whatever storage technology you want  to use (NAS/NetHDD/fileserver/localhdd/etc) shouldn't matter too much as long as there is a PC of some type directly connected to the TV. as long as the PC can get to the storage location, all shoudl be well. I do strongly recommend gigabit ethernet for media streaming, especially for HD content. 

so do you have a PC like device attached to your TV? 

if not, DLNA may work for you, but your TV and your NAS will both have to support the same version of the protocol. more trouble than it's worth in my opinion, and it locks you to a hardware platform on multiple devices.

---

### Post by madhi19 on 2010-11-30
I suppose the biggest bottleneck is the speed of the network but even a standard 100 network would do fine. Hell my mediatomp media server can stream media wirelessly to my ps3 at half that speed fine! If we are talking about on the fly re-encoding that another story!

---

### Post by Hexley on 2010-11-30
> **endotherm said:**
> shouldn't matter too much as long as there is a PC of some type directly connected to the TV.

I don't want a pc or media box to my TV, I wonder if this is possible if the TV got ethernet port.. Can I then access the storage from my TV interface?

---

### Post by cariboo on 2010-11-30
Just to do a bit of testing, I started up vlc on 3 different systems as well as running the media center system and had 4 different ripped dvds running with no degradation in quality on any of the systems. I have a 100Mbps network.

I used vobcopy to rip the dvds, so the files are pretty well the same size and bitrate as the original dvd.

---

### Post by Zzl1xndd on 2010-11-30
> **Hexley said:**
> I don't want a pc or media box to my TV, I wonder if this is possible if the TV got ethernet port.. Can I then access the storage from my TV interface?

If thats the case then it will largely depend on the functionality of the TV. Is the TV an DLNA device?

---

### Post by Hexley on 2010-11-30
> **tweakedenigma said:**
> Is the TV an DLNA device?

I don't know, I have not bought such TV yet..
But on all TVs on the website it only says: Network - Yes...

---

### Post by Paqman on 2010-11-30
> **cariboo907 said:**
> Ive have all my media, video and audio, stored on a server. I have a system running XBMC connected to my TV. I just auto mount the shares in /etc/fstab on boot

I do the exact same. I built a mini-ITX machine that sits in my TV cabinet.

---

### Post by endotherm on 2010-11-30
the network port does not likely allow you the functionality you want. see, getting to the file is only the first part of playing it. you then need protocols for streaming, codecs for decoding video, and applications to use these codecs to consume these streams. if you don't have some kind of media box there, all of this must be programmed into the TV itself by the manufacturer, so you don't have any control of it. if your TV doesn't recognize x.264 video, what do you do about that? you can't easily install a codec, so you're just sol.

---

### Post by handy on 2010-12-01
My 100 Mbit LAN has no problem serving 2 computers 2 different movies at the same time from my tiny ReadyNAS box.

My LAN is faster than my internet connection speed & we can watch 2 Google/YouTube vids at the same time.

---

### Post by CharlesA on 2010-12-01
Make sure the TV is DLNA (Digital Living Network Alliance) compliant, that way you can use something like ps3mediaserver to stream directly to the TV.

---

