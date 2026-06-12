---
title: "Ubuntu TV"
date: 2012-02-24
forum: The Cafe
---

### Post by Dragonbite on 2012-02-24
I am looking to set up a media PC and originally thought of trying Mythbuntu.  This was before Ubuntu announced Ubuntu TV.

I don't know when Ubuntu TV will be released and whether it will be able to install on a regular PC.

So I am debating whether to wait for Ubuntu TV or look at Mythbuntu.  Or any other recommended distributions?

I actually will not be tuning into TV, but want to play internet video, physical DVDs and from the hard drive.

---

### Post by wyliecoyoteuk on 2012-02-24
If you don't want a TV tuner, [XBMC]("http://xbmc.org/") is probably better for you than Mythbuntu.
MythTV is more TV centred than XBMC.
There is even a beta XBMCbuntu.

---

### Post by BrokenKingpin on 2012-02-24
Just install *buntu on the PC and then install XBMC from the PPA. I would not wait for Ubuntu TV, as it probably will not be available this years, and XBMC will probably end up being better anyways.

Or if you a super lazy buy a boxee box... again, will be way better than anything Canonical will put out.

---

### Post by Royke on 2012-02-24
Hello @Dragonbite,

About UbuntuTV, i have read the most part of it and my conclusion for you is that it will run(even smoothly) if you are running Ubuntu well right now.
I can't confirm Mythbuntu will just work too then on your machine but why not make a dual or triple bootsystem on different partitions? One for stability and normal use, the rest to figure out and play. Maybe you can tell ús what to do in a while:lolflag:

Reading about and knowing Ubuntu's ways it shall be worth the waiting anyway.

Yeah, Ubuntu TV! If the developement of this goes the way i hope, we might be able to install it on some TV's itself or i am dreaming too much..

---

### Post by grahammechanical on 2012-02-24
Ubuntu 12.04 now has a video lens

[http://www.omgubuntu.co.uk/2012/02/ubuntu-12-04-adds-new-video-lens-for-finding-movies-tv-shows-online/]("http://www.omgubuntu.co.uk/2012/02/ubuntu-12-04-adds-new-video-lens-for-finding-movies-tv-shows-online/")

By the way, Ubuntu TV will not be able to do what MythTV or Video for Linux cannot do. If Linux does not recognise the TV card then nothing will work.

For example, I have the new video lens installed on 12.04 right now but it is blank. That is because I do not have any videos nor am I subscribed to any video download services. I do have a TV card that does not work because there are no drivers for it. I have MythUbuntu installed and it does not work with this card. I am sure that if I installed this Ubuntu TV OS, then that will not work either.

Regards.

---

### Post by Paqman on 2012-02-24
> **wyliecoyoteuk said:**
> If you don't want a TV tuner, [XBMC]("http://xbmc.org/") is probably better for you than Mythbuntu.


+1 to this. MythTV is great if you want to build your own PVR, but otherwise XBMC is the way.

---

### Post by Dragonbite on 2012-02-24
XBMC looks interesting.

I don't plan on using a TV tuner so if that is a key component for MythTV/Mythbuntu then that's just going to cause headaches.

I have an P4 I plan on using for this (2GHz, 2GB Ram) and a card that has DVI & S-something-out and about 128 MB but seemingly no tuner.

Can you tell I'm moving into "new" territory ;)

---

### Post by LowSky on 2012-02-24
MythTV doesn't require a tuner at all. It is still a great program for video watching, and keeping all your files organize if you use multiple folder locations. The only downside to MythTV and XBMC is setting up the directories, both require you know exactly what folders things are stored, and to make sure they are accessible. Another downside to MythTV is its reliance on MySQL for database keeping, but the great upside is that MythTV can be used as a UPnP and allow a user to watch from other computers or devices, either suing the Myth Frontend or heck even XBMC.

---

### Post by drawkcab on 2012-02-24
I love XBMC but most of the time I prefer to just log into the desktop environment using a wireless keyboard and mouse.  I prefer Gnome 3 even though it is a bit sluggish on my atom ion nettop.  Flirc will adapt itself to any IR remote you have.  Mplayer2 + UMplayer seems to work best for me in terms of playing bakck HD formats.

---

### Post by Paqman on 2012-02-25
> **LowSky said:**
> MythTV doesn't require a tuner at all.

No it doesn't, but if you don't have a tuner then all the extra complexity of MythTV isn't required, so a simpler package like XBMC would do the job.

>  The only downside to MythTV and XBMC is setting up the directories, both require you know exactly what folders things are stored

I've found it's also best to mount your content locally through fstab. XBMC's own SMB implementation wasn't 100% reliable in my experience. It's much happier if it thinks it's accessing local content and let the OS handle the connectivity to the shares. Apart from that I've found it's pretty bombproof.

---

### Post by lovinglinux on 2012-02-28
I just saw the video at [http://www.ubuntu.com/devices/tv](http://www.ubuntu.com/devices/tv)

I want that on my PC!!!! Looks awesome.

---

### Post by Roasted on 2012-02-28
> **BrokenKingpin said:**
> Just install *buntu on the PC and then install XBMC from the PPA. I would not wait for Ubuntu TV, as it probably will not be available this years, and XBMC will probably end up being better anyways.


I like this idea. It's exactly what I did. I just set up XBMC to auto start so it launches right into XBMC without even seeing Ubuntu. With a quick hit of the "\" key I can unmaximize XBMC and use the HTPC as a regular computer. It's really the best of both worlds.

---

