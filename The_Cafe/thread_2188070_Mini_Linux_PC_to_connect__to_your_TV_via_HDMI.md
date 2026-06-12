---
title: "Mini Linux PC to connect  to your TV via HDMI"
date: 2013-11-15
forum: The Cafe
---

### Post by tea for one on 2013-11-15
Good afternoon

I've noticed the availability of a tiny unit with a derivative of Ubuntu installed:-

[http://www.rikomagic.co.uk/linux_mini_pcs.html](http://www.rikomagic.co.uk/linux_mini_pcs.html)

The description on the site is,of course, very appealing but I was wondering if anyone had purchased and used this little device?

I am interested to establish if this mini pc would act as a PVR if I plugged in a compatible USB TV Tuner and added, Kaffeine or similar?

---

### Post by TheFu on 2013-11-15
Nope. Those are playback devices.

Recording requires more than an Atom-class computer of a few yrs ago.  I've tried on an N280 and it wasn't fast enough to record even 1 stream.

For a linux-based PVR, look at MythTV compatible hardware and suggested CPUs.  I can highly recommend the Silicon Dust HDHomerun network tuners. I love mine.  Get the Android HdHomerun Signal Meter if you do OTA like me (not cableCARD).

Seems that folks are trying to use those devices as MythTV "front-ends".

---

### Post by tea for one on 2013-11-16
Thanks for your reply.

I asked the supplier the same question and did not receive a response. 

I suspect that they knew that their device was not powerful enough to act as a PVR and therefore did not want to reply with a negative answer.

Anyway, thanks for the hardware recommendations, I'll do a bit more research.

Kind regards

---

### Post by TheFu on 2013-11-16
> **tea for one said:**
> Thanks for your reply.

I asked the supplier the same question and did not receive a response. 

I suspect that they knew that their device was not powerful enough to act as a PVR and therefore did not want to reply with a negative answer.

Anyway, thanks for the hardware recommendations, I'll do a bit more research.

Kind regards

Suppliers will answer questions about a feature listed in their marketing materials. Most suppliers for that thing are really just resellers ... they thought it would sell without any real effort.  My business partner ordered 2, BTW, from China.

It is basically an android machine, so while it doesn't claim to be recording device (where would you put the data?) that doesn't mean that someone couldn't come up with a magical new encoding that creates a 1080p recording using only integer math that takes only 1% of a watch CPU and stores 5 hrs of video into a 5KB file.  It could happen, it is just highly, highly, highly (over 1Mx more times) unlikely.  Perhaps you are that person?  You'd need to purchase 1 and get to work. ;)

OTOH, I think most people (probably NOT you or me) will be happier with that $35 Chromecast dongle thing that will watch everything you watch and let google know about every click from the remote.

A $100 XBMC box is my playback device - AMD/E350 APU with onboard ATI GPU. For a recorder, I've got (sorry) Windows7 media center running inside a VM using a HDHR3 dual OTA tuner on the network. The physical machine that VM sits on handled 5 other VMs too. 7MC has free schedule data (unlike MythTV) and has broad support for TV tuners. I did have to fight with VM storage configuration to get enough throughput for dual 1080i recordings. Sometimes there are hiccups still, but not that often. If one of the streams is 720p, the recordings are gorgeous.

Anyway, if you are have more interest ... ask. I've written a few blog articles about it and building an OTA antenna for $20 that actually works (receives stations from 50+ miles away).

---

### Post by tea for one on 2013-11-16
Good afternoon

Yes, I agree, a Google Chromecast regularly 'phoning home is not exactly what I'm looking for............

I'm OK with UK DVB reception via my aerial and I am comfortable recording TV either on my Toshiba PVR and also on my Netbook running Kaffeine inside Lubuntu.
I use an Aver Media Volar Black HD tuner with my Lubuntu netbook.

I could also buy a mini PC with a similar specification to yours e.g. [http://www.dinopc.com/shop/pc/NEW-Minisaur-E350-124p1807.htm](http://www.dinopc.com/shop/pc/NEW-Minisaur-E350-124p1807.htm)

I was and still am curious about these newish dongle type devices to record radio and TV programs, and also to play back the recordings on a variety of units.

It is often the case that PVRs only allow the playback of the recording on the device where it was recorded. 

I was hoping to introduce a little more flexibility into my media use and also have a little bit of fun with a cheapish disposable device.

Thanks for your replies

---

### Post by TheFu on 2013-11-16
Perhaps the store-bought (or content provided) PVRs are the issue?

I've never seen regular PC-PVRs have that issue.  Even my Win7 recorder lets me move, transcode, edit the content as I like.  In the USA, there is a "broadcast flag" that can be set to prevent this stuff, but either it doesn't work or it has not been used for OTA channels.  I think it is used all the time for premium cable channels, but I've never had a digital recorder that honored those flags that also worked with premium cable.

Lots of people in the US use the "analog hole" to get around the DRM added recently to satellite and cable devices. This lets them legally time-shift the shows. In the USA, timeshifting is legal (there is a supreme court ruling).

Anyway, good luck and have fun!

---

### Post by v1k1ng1001 on 2013-11-17
I think there's really a market for something like this but so far I haven't seen anything that has enticed me to bite.

Nonetheless, when my atom ion nettop htpc died a year ago I just picked up another low-wattage atom-based barebones unit for $200.  It has enough snort to run Gnome Shell (which easily scales the desktop to the television--I'm typing on it from across the room right now) plays 1080 just fine and with added storage it doubles as my home/web server (instead of running a power-hungry desktop.)  Add and IR dongle and xbmc for an awesome media experience.  Add some emulators, Steam and a few controllers and its a gaming console.  Load up some music and it drives my stereo system.  This is all for the same costs of four months of basic cable.

I think these devices are coming, just not yet.  Especially since most of the mass market is still figuring out what a Roku is, how to share files over their network, etc.

---

### Post by TheFu on 2013-11-17
> **v1k1ng1001 said:**
> I think there's really a market for something like this but so far I haven't seen anything that has enticed me to bite.

Nonetheless, when my atom ion nettop htpc died a year ago I just picked up another low-wattage atom-based barebones unit for $200.  It has enough snort to run Gnome Shell (which easily scales the desktop to the television--I'm typing on it from across the room right now) plays 1080 just fine and with added storage it doubles as my home/web server (instead of running a power-hungry desktop.)  Add and IR dongle and xbmc for an awesome media experience.  Add some emulators, Steam and a few controllers and its a gaming console.  Load up some music and it drives my stereo system.  This is all for the same costs of four months of basic cable.

I think these devices are coming, just not yet.  Especially since most of the mass market is still figuring out what a Roku is, how to share files over their network, etc.

@v1k1ng1001, playback is relatively easy.  Content over 600p needs GPU support for playback, thankfully, almost all current-gen GPUs have HW support for h.264, mpeg2 and AVC1 decoding.  I have a slightly older dual-core Atom (N280) that cannot playback anything over 600p with any codec since the GPU is not involved at all.  600p is the highest resolution that Atom can decode in software without stuttering.

Recording TV is a completely different animal, IME.  Does any Atom have enough CPU to do that with HiDef content ... from 2 concurrent streams?  My attempts doing that have failed completely. I've tried with a device that claims all encoding occurs off the device ... and it never recorded a single 1080i frame.  The same device happily handles everything I throw at it on a 1st-gen Core i5 laptop.

Also have a roku3 and hate it. It is extremely limiting, especially for the price  ... can't play anything from my local network at all without running a special server (plex) that I don't want and registering a "private channel" with roku.  Big brother is watching; no thanks. All my other devices have worked with NFS, CIFS, or DLNA for years. The Roku3 does allow directly connected USB storage to be used, but I doubt it supports ext4 file systems and I am not inclined to pull 6TB of storage off the server currently connected just to watch a TV show.  The WD-TV Live HD plays 1080p content fine over the network as does the XBMC (frodo) AMD/E350 box (26W at boot; 16W when running).  Neither are capable of recording  ... though the XBMC might work. I may connect a USB dongle Hauppauge 950Q tuner to see if that helps even for live TV.  Huuummmmm another "project."

These are just my experiences, so they may not be everyone else's. 
I'd love to hear the smallest, lowest power recording solutions from others that can handle 2 concurrent 1080i streams from OTA sources.

---

