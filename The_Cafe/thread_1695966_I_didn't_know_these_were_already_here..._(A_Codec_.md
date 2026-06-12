---
title: "I didn't know these were already here... (A Codec Discussion)"
date: 2011-02-26
forum: The Cafe
---

### Post by Captain Smiley Pants on 2011-02-26
So today I've been messing around on a Debian 64bit GNOME Live DVD and trying it out on my new computer to see what works, what doesn't, etc. I think it's the latest stable version, not entirely sure myself but I can double check later.
 
I open my music folder, assuming that none of my music would work (using .mp3s) but just wondering what program is assigned to that sort of file type when, lo and behold, my music started playing.
 
This was different; usually on Ubuntu I'd have to install certain codec packages, or have some software check for me where a suitable codec was.
 
I open my movie folder. There are .mp4s, .avis, .mkvs, a whole slew of stuff. Everything played!
 
I try to play a commercial DVD; still need libdvdcss2, of course (or whatever is used today, I usually don't even bother with buying physical copies of movies anymore).
 
So here's what I'm getting at: For every distribution, what is the difference in how codecs are handles and provided? Are there good enough free codecs to work with most file types? Does it matter by where the distro came from? And so on (feel free to discuss your own details regarding free or closed source codecs).

---

### Post by cariboo on 2011-02-26
I know the gstreamer packages replace the need for a lot of codecs we used to have to install. I haven't really paid that much attention to them, as everything but commercial dvds just work out of the box.

---

### Post by Khakilang on 2011-02-27
I usually had to install Ubuntu restricted extras to play music and movies. But I heard Linux Mint include most of this codec.

---

### Post by cariboo on 2011-02-27
The latest Ubuntu installer gives you the option to download and install codecs right at the start of the installation process. Actually it started with the 10.10 release.

---

### Post by Zlatan on 2011-02-27
> **cariboo907 said:**
> The latest Ubuntu installer gives you the option to download and install codecs right at the start of the installation process. Actually it started with the 10.10 release.

the OP was about LIVE media

---

### Post by stmiller on 2011-02-27
Maybe that particular live DVD contained the needed codecs?

The default Debian install has no non-free codec support.

There has always been debian multimedia for debian to easily add, however:

[http://debian-multimedia.org/dists/stable/main/binary-i386/](http://debian-multimedia.org/dists/stable/main/binary-i386/)

Each disto handles this differently for various reasons - mainly to remain GPL software as a release, and also to comply with US and other laws. If you aren't in the US, most of the restrictions to this stuff don't apply to you.

---

### Post by Captain Smiley Pants on 2011-02-28
> **Zlatan said:**
> the OP was about LIVE media
Eh, it can be about that too :)

---

### Post by Zlatan on 2011-02-28
> **Captain Smiley Pants said:**
> Eh, it can be about that too :)

Sure, no problem with me, sorry for interrupting:)

---

### Post by 3Miro on 2011-02-28
mp3 codecs are not "free as in freedom". There are restrictions on what can and cannot be done with them. Hence, Ubuntu (and other foundation/corporation distributions) usually don't package those by default. On the other hand, community based distros (like Mint and PSLOS) come with more codecs and drivers pre-installed.

---

### Post by ubuntu-freak on 2011-02-28
> **stmiller said:**
> Each disto handles this differently for various reasons - mainly to remain GPL software as a release, and also to comply with US and other laws. If you aren't in the US, most of the restrictions to this stuff don't apply to you.

Makes me think of a song by Morrissey called "America Is Not the World".

Anywho, the previous Debian  leader Steve McIntyre made a nifty Debian 5 rehash for Linux Format in the UK a couple of years ago, with all GStreamer codecs pre-installed. I was surprised at first, but then I realised I wasn't in the US.

---

### Post by Captain Smiley Pants on 2011-03-01
Weird question; is there a distro known for _not_ supporting .ogg file types?

---

