---
title: "Trying to build a NAS"
date: 2010-12-02
forum: Server Platforms
---

### Post by fvargasfrank on 2010-12-02
I have been looking around at parts that people have use but they seem to be outdated topic nothing current. This is what im trying to do with the NAS, i would like it to stream movies 720 and 1080 to my Samsungs tvs, this may require trans coding(i think that the word), storage wise i would like to start with 2 2tb hardrives(The energy ones), i don't know if i need a raid(5) card for what i need if so, whats a good one ? i would like to save as much power as possible.

Motherboard ?
CPU = maybe an I3
RAM = 2g DDR3
Power-supply = ?
OS = FreeNas

also i have read a lot of places were you can do a automatic bit-torrent clients to downloads show and unrar them for you and maybe organize them in to separate folder, but my question is can i do this with megashare and Hotfile (premium) links ?

---

### Post by CharlesA on 2010-12-02
Get a cheap AMD quad core, compatible mobo and memory and go to town. :)

Note: I don't think FreeNAS supports DLNA media servers. The one I recommend is PS3media server if you need to do transcoding.

---

### Post by fvargasfrank on 2010-12-02
> **CharlesA said:**
> Get a cheap AMD quad core, compatible mobo and memory and go to town. :)

Note: I don't think FreeNAS supports DLNA media servers. The one I recommend is PS3media server if you need to do transcoding.

Will an AMD quad core trans code my media with no problem ? what about the downloading automatic with hotfile or rapidshare or megashare? do i need to set up a raid for my nas?

---

### Post by CharlesA on 2010-12-02
Depending if you want 1080p or 720p. It should do 1080p fine.

As for the file sharing question, anything can serve files.

---

### Post by fvargasfrank on 2010-12-03
> **CharlesA said:**
> Depending if you want 1080p or 720p. It should do 1080p fine.

As for the file sharing question, anything can serve files.

Hey i was looking at the AMD quad but they consume a lot of power. this machine will be on 24/7.

---

### Post by arrrghhh on 2010-12-03
> **fvargasfrank said:**
> Hey i was looking at the AMD quad but they consume a lot of power. this machine will be on 24/7.

That's your choice then - do you want it to be able to stream 1080p movies and transcode them on the fly?  Or do you want a low-power solution?  You can't have both.

Now streaming 1080p without any transcoding you could easily do with a low-power proc.  However, as soon as we throw transcoding (splitting the video & audio, re-encoding, then re-splicing the video & audio back together in real-time...) then you'll need some beefy specs.

Also not sure how compatible "samsung tvs" are... The PS3 is still one of the most standards-compliant DLNA devices, and I still have some issues with it... mainly because of what it supports.

---

### Post by CharlesA on 2010-12-03
> **fvargasfrank said:**
> Hey i was looking at the AMD quad but they consume a lot of power. this machine will be on 24/7.

An [i3]("http://www.newegg.com/Product/Product.aspx?Item=N82E16819115221&cm_re=i3-_-19-115-221-_-Product") (dual core) has a TDP of 73W. A [quad core AMD]("http://www.newegg.com/Product/Product.aspx?Item=N82E16819103656") has a TDP of 95W.

Of course the CPU with more cores will use more power.

@arrrghhh: I picked up a Sony blu-ray player that was DLNA compatible and couldn't get it to work with PS3Mediaserver. I'm probably doing something wrong, but *shrug*

---

### Post by lukeiamyourfather on 2010-12-03
AMD makes quad core processors with as low as 45W TDP like the Athlon II X4 615e. If you want lower than that you'll have to use ultra low voltage processors (Intel Atom, AMD Geode, VIA Nano, etc.). As for the RAID controller, you only need that if you want to do RAID and don't want to use software RAID in Linux. How important is this data? If you don't want to lose any of it then RAID will add some redundancy (but not as good as regular backups).

---

### Post by endotherm on 2010-12-03
my recommendation is that instead of "streaming" directly to the TV, that you build a media PC and a desktop fileserver. it gives you maximum flexibility, eliminates the need for transcoding, can be done with a much lower power cpu (dualcore 45-65w  would be fine and run cool) , and does not rely on a particular hardware platform they way DLNA does. 

just my personal opinion. I don't like embedded systems that I can't modify. if I can't install the required codecs or switch player applications to suit a particular video file/format, I think there would be large chunks of my collection that would be unplayable.

---

### Post by CharlesA on 2010-12-03
> **endotherm said:**
> 
just my personal opinion. I don't like embedded systems that I can't modify. if I can't install the required codecs or switch player applications to suit a particular video file/format, I think there would be large chunks of my collection that would be unplayable.

I'm still leaning that way, since it's still loads easier to set up (and way more configurable)

---

### Post by fvargasfrank on 2010-12-03
maybe i will just remux my files the samsung plays some mkv movies but not all. all my movies are around 720 p i have like one or two 1080. I will have backup date of my other pc so i need a little data recovery protection, as for the movies and tv shows if they go bye bye i wouldn't care. that amd sound good the one that has 45 tdp do you have more info ?

---

### Post by endotherm on 2010-12-03
> **fvargasfrank said:**
> maybe i will just remux my files the samsung plays some mkv movies but not all. all my movies are around 720 p i have like one or two 1080. I will have backup date of my other pc so i need a little data recovery protection, as for the movies and tv shows if they go bye bye i wouldn't care. that amd sound good the one that has 45 tdp do you have more info ?
AVI/MKV are just containers, so the audio and video streams within them may use a wide array of codecs, some of which samsung has licensed, and likely others that they have not.

as for your Bit torrent question, yeah, most NASs come with a web-accessible BT client, and if you built one, then you have lots of options. Ubuntu's Transmission client has a web-accessible front end you can enable, and there is also Torrentflux.

---

### Post by arrrghhh on 2010-12-03
> **CharlesA said:**
> @arrrghhh: I picked up a Sony blu-ray player that was DLNA compatible and couldn't get it to work with PS3Mediaserver. I'm probably doing something wrong, but *shrug*

Sorry for continuing the OT, but I've never used a set-top box for DLNA, and I've had inconsistent successes and failures when interfacing with DLNA-compliant TVs.  A computer is probably the best DLNA client, with the PS3 a good solution, but there's still a lot of types of video it doesn't support.  There's a lot of little set-top DLNA streamers setup just for this, I'm sure they would work very well.

Ha, lots of responses since this post!  I would echo the other responses of having a server and a small PC hooked up to the TV would be much better than any DLNA solution.

---

### Post by CharlesA on 2010-12-03
> **arrrghhh said:**
> Sorry for continuing the OT, but I've never used a set-top box for DLNA, and I've had inconsistent successes and failures when interfacing with DLNA-compliant TVs.  A computer is probably the best DLNA client, with the PS3 a good solution, but there's still a lot of types of video it doesn't support.  There's a lot of little set-top DLNA streamers setup just for this, I'm sure they would work very well.

Agreed. I'm probably just going to stick with the HTPC I currently have since I don't need to do any transcoding and it's able to play files directly from samba shares, instead of screwing around with a DLNA server.

> Ha, lots of responses since this post!  I would echo the other responses of having a server and a small PC hooked up to the TV would be much better than any DLNA solution.

That's what I was doing originally, and after trying both the PS3 way and the set-top-box way, I'm more then likely going to be going back to it. It's just easier to setup and use IMO.

---

### Post by lukeiamyourfather on 2010-12-03
> **fvargasfrank said:**
> that amd sound good the one that has 45 tdp do you have more info ?

This is the processor.

[http://www.provantage.com/amd-ad615ehdgmbox~7AAMD2J0.htm](http://www.provantage.com/amd-ad615ehdgmbox~7AAMD2J0.htm)
[http://www.provantage.com/amd-ad600ehdgibox~7AAMD2C7.htm](http://www.provantage.com/amd-ad600ehdgibox~7AAMD2C7.htm) (slower and cheaper)

What do you want to know about it? :-k

---

### Post by CharlesA on 2010-12-03
> **lukeiamyourfather said:**
> This is the processor.

[http://www.provantage.com/amd-ad615ehdgmbox~7AAMD2J0.htm](http://www.provantage.com/amd-ad615ehdgmbox~7AAMD2J0.htm)
[http://www.provantage.com/amd-ad600ehdgibox~7AAMD2C7.htm](http://www.provantage.com/amd-ad600ehdgibox~7AAMD2C7.htm) (slower and cheaper)

What do you want to know about it? :-k

The first one is actually a very nice processor. If I didn't have to replace a mobo and memory to upgrade, I'd go for it, myself, as my server is running a 45W dual core at the moment.

---

### Post by Cosma on 2010-12-03
> **fvargasfrank said:**
> storage wise i would like to start with 2 2tb hardrives(The energy ones)

be carefull with energy saving hdd's (green drives) in a raid volume. many people had problems with them because they switch to powersaving mode at random times and destroy the raid.

---

### Post by lukeiamyourfather on 2010-12-03
> **Cosma said:**
> be carefull with energy saving hdd's (green drives) in a raid volume. many people had problems with them because they switch to powersaving mode at random times and destroy the raid.

This is FUD as far as I'm concerned. I've been using Barracuda LP drives in RAID arrays for a long time with zero issues. There are specialized SATA drives with features that make them more reliable in a RAID array, but the "green" drives are no more unreliable than regular 7200 RPM SATA drives.

---

### Post by lukeiamyourfather on 2010-12-03
> **CharlesA said:**
> The first one is actually a very nice processor. If I didn't have to replace a mobo and memory to upgrade, I'd go for it, myself, as my server is running a 45W dual core at the moment.

What motherboard? If it has AM2/AM2+/AM3 then it should work. Might require a BIOS update though.

---

### Post by CharlesA on 2010-12-03
> **lukeiamyourfather said:**
> What motherboard? If it has AM2/AM2+/AM3 then it should work. Might require a BIOS update though.

My server is currently running an Intel dual core with DDR2 RAM atm, so I'd need to get a new mobo and memory, which I'm not ready to do just yet.

---

### Post by fvargasfrank on 2010-12-03
> **lukeiamyourfather said:**
> This is the processor.

[http://www.provantage.com/amd-ad615ehdgmbox~7AAMD2J0.htm](http://www.provantage.com/amd-ad615ehdgmbox~7AAMD2J0.htm)
[http://www.provantage.com/amd-ad600ehdgibox~7AAMD2C7.htm](http://www.provantage.com/amd-ad600ehdgibox~7AAMD2C7.htm) (slower and cheaper)

What do you want to know about it? :-k

I really like the amd 615e what a good mother board for that processor? sata 3 and at least 5 sata port

---

### Post by CharlesA on 2010-12-03
> **fvargasfrank said:**
> I really like the amd 615e what a good mother board for that processor? sata 3 and at least 5 sata port
[Take yer pick]("http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=100007625+600054095&QksAutoSuggestion=&ShowDeactivatedMark=False&Configurator=&IsNodeId=1&Subcategory=22&description=&Ntk=&CFG=&SpeTabStoreType=&srchInDesc=").

---

### Post by endotherm on 2010-12-03
> **CharlesA said:**
> [Take yer pick]("http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=100007625+600054095&QksAutoSuggestion=&ShowDeactivatedMark=False&Configurator=&IsNodeId=1&Subcategory=22&description=&Ntk=&CFG=&SpeTabStoreType=&srchInDesc=").
I was just about to post an almost identical link. good on ya.

---

### Post by CharlesA on 2010-12-03
> **endotherm said:**
> I was just about to post an almost identical link. good on ya.
I love newegg's filters. <3

---

### Post by fvargasfrank on 2010-12-03
So here is what im going with the mother is this one [http://www.newegg.com/Product/Product.aspx?Item=N82E16813131654](http://www.newegg.com/Product/Product.aspx?Item=N82E16813131654)
and the processor is Athlon II X4 615E.

now i need to find a decent case and power supply(any suggestion?) can i run ubuntu server of a usb? or its better to installed on the hardrive?

---

### Post by CharlesA on 2010-12-03
> **fvargasfrank said:**
> So here is what im going with the mother is this one [http://www.newegg.com/Product/Product.aspx?Item=N82E16813131654](http://www.newegg.com/Product/Product.aspx?Item=N82E16813131654)
and the processor is Athlon II X4 615E.

now i need to find a decent case and power supply(any suggestion?) can i run ubuntu server of a usb? or its better to installed on the hardrive?
You might be able to install it on a usb drive, but I'd suggest installing it on a regular hard drive.

My server is sitting in an Antec 900 with a OCZ 500W power supply.

---

### Post by fvargasfrank on 2010-12-03
i have the Antec 900 is a great case but i was looking for something smaller. i have read its better to install the os separate from the server hardrive, i dont know why.

---

### Post by endotherm on 2010-12-03
> **fvargasfrank said:**
> i have the Antec 900 is a great case but i was looking for something smaller. i have read its better to install the os separate from the server hardrive, i dont know why.
you want to keep the system on a differant drive or at least partition that your data, but you would definitely want to put your os on the fastest bus to ram, and that is sata at the second.

if your data is kinda valuable, buy a second hdd, but if your os/services are more important, just partition a single hdd.  since you are building a nas, I would get a small fast  drive for the os, and another large capacity drive for storage. be sure to consider your growth potential, and make sure that you have enough ports for future upgrades. its a lot cheaper to build in scalability now, than to have to upgrade everything to get it in 3 years.

---

### Post by CharlesA on 2010-12-03
> **fvargasfrank said:**
> i have the Antec 900 is a great case but i was looking for something smaller. i have read its better to install the os separate from the server hardrive, i dont know why.

I guess they mean install the OS on a separate drive from yer data. That's what I did, at least, the OS is on it's own drive and my RAID array is mounted as my data drive.

If you go much smaller, you might run into problems with heat and air flow if you are running a lot of hard drives.

I moved my server into a different case and had to go back to the 900, since hard drive temps were 10-15C higher then in the Antec 900.

---

### Post by fvargasfrank on 2010-12-05
Thank you guys for all the help I just order all the parts and updated my router to the cisco e3000 I will post  pic when I have everything set up.

---

