---
title: "Help me build a media server..."
date: 2009-06-16
forum: Server Platforms
---

### Post by kidux on 2009-06-16
I'm going to deploy in a few months, and I plan on having a media server setup so people can stream movies/TV shows/music. I'm anticipating no more than 50 people on at any one time, so what do you guys think would be a good setup? I'm thinking a quad-core processor with 4GB (or higher) of RAM, and 2 NICs, with TB drives in a RAID array... Anything I may be missing/overlooking? What OS should I use?

---

### Post by kustomjs on 2009-06-16
what type of connection do you have? like cable,T1,FTTH (fiber to the home) dsl?

---

### Post by Cheesemill on 2009-06-16
The limiting factor will probably be the network between the server and clients.
Is this to be run over a LAN or the internet?

Also does the server need to process/transcode the video at all or will the clients be doing this?

Give us the specs of the clients and video formats involved and someone may have a more definite answer for you.

---

### Post by kidux on 2009-06-17
It's going to be in country with me on a LAN or WAN, depending on infrastructure and availablity of materials, i.e. CAT5/6 cabling.

The clients will more than likely be XP/Vista laptops, with some 360's and PS3's thrown in as well.

Most of the video files are avi in either lavc or xvid codecs, and the audio are MP3's.

---

### Post by kustomjs on 2009-06-17
we need to know what type of connection your getting from your isp and type of connection your clients is going to use.

---

### Post by sloggerkhan on 2009-06-17
Assuming you are just serving the media files and that all the traffic will be behind your own router, I'd go for 1000 megabit network, at least to your media server, the RAM and CPU requirement won't be that high, though. Based off my experiences, your limiting factor with this will be local bandwidth. A 720P movie can have a bitrate (if decently encoded) in the 4000 - 5000 Kbps range, which is roughly 5.5 megabits/sec. That means to stream 720P video encoded in h264 or vc-1 to 50 clients at once, the bandwidth load is roughly 275 megabits/second. So in other words the SERVER needs faster than 100 megabit network uplink. Your clients don't, though (They could still be on 100 megabit, though if you're planning on needing to transfer large files quickly instead of just streaming them, keep in mind that transferring 1 terabyte over a 100 megabit connection will take days).
Likewise, since you'll just be streaming files, the CPU load shouldn't be too high, and you shouldn't need tons of RAM either. I'd guess you could use 1 gig RAM and a single core CPU and be fine so long as the computers not doing anything significant outside of streaming static files. Otherwise, I recommend you put a RAID V using mdadm in the box for storing the media files. You can find 2nd gen terabyte drives for $70-100, so go for 4 - 6 of them, I'd say. RAID (IMO) is the 2nd key thing after having 1000 megabit uplink. Anyhow, good luck.

---

### Post by kidux on 2009-06-17
> **kustomjs said:**
> we need to know what type of connection your getting from your isp and type of connection your clients is going to use.
No ISP. It's an internal network. Clients will use either CAT5 or WAN connection.

---

### Post by kidux on 2009-06-17
> **sloggerkhan said:**
> Assuming you are just serving the media files and that all the traffic will be behind your own router, I'd go for 1000 megabit network, at least to your media server, the RAM and CPU requirement won't be that high, though. Based off my experiences, your limiting factor with this will be local bandwidth. A 720P movie can have a bitrate (if decently encoded) in the 4000 - 5000 Kbps range, which is roughly 5.5 megabits/sec. That means to stream 720P video encoded in h264 or vc-1 to 50 clients at once, the bandwidth load is roughly 275 megabits/second. So in other words the SERVER needs faster than 100 megabit network uplink. Your clients don't, though (They could still be on 100 megabit, though if you're planning on needing to transfer large files quickly instead of just streaming them, keep in mind that transferring 1 terabyte over a 100 megabit connection will take days).
Likewise, since you'll just be streaming files, the CPU load shouldn't be too high, and you shouldn't need tons of RAM either. I'd guess you could use 1 gig RAM and a single core CPU and be fine so long as the computers not doing anything significant outside of streaming static files. Otherwise, I recommend you put a RAID V using mdadm in the box for storing the media files. You can find 2nd gen terabyte drives for $70-100, so go for 4 - 6 of them, I'd say. RAID (IMO) is the 2nd key thing after having 1000 megabit uplink. Anyhow, good luck.
The files are all in the 300-800MB range, and will be either streamed via Mediatomb/Tversity or simple static.

---

### Post by ugm6hr on 2009-06-17
> **kidux said:**
> The files are all in the 300-800MB range, and will be either streamed via Mediatomb/Tversity or simple static.

I think there are still problems with the XBox 360 & MediaTomb.  FUPPES may be worth considering as an alternative.

I am uncertain whether it would achieve what you want, but perhaps FreeNAS might be the simplest way to go.  That way, you could concentrate your money on storage for all the media, rather than the CPU, RAM etc.  I have never known anyone use it to serve 50 clients, but I can't see any reason why it wouldn't.

---

### Post by papenpj on 2009-06-23
Well for streaming to Xbox360 and PS3 I use Ushare.  I select the enable Xbox360 option, which seams to work perfectly fine with my PS3 as well as my brothers 360. Ignore the option they suggest for PS3.

As far as streaming to PCs I use samba and just have a generic account with no write access, after all it easier to create 1 account that anyone can use with no destructive powers. Im able to login with root, or whoever you want to own the folder to perform maintenance or add things easily from windows.

I guess if you also want to do things locally on the computer and don't care about spending extra money you could go for quad core like you suggested instead of using a stripped down server edition.  Basically anything you can setup and install on a dedicated server you can do on a desktop install of ubuntu. I know this because my laptop uses ushare also, but I don't have it hosting websites and what not.

---

