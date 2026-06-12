---
title: "TASCAM US-122 mkII not recognised"
date: 2009-12-01
forum: Ubuntu Studio
---

### Post by delaossa on 2009-12-01
Dear all,
I have just got a new usb audio/midi interface [TASCAM US-122 mkII]("http://www.tascam.com/products/us-122mkII.html"), which doesn't work at all with ubuntu karmic. 
I have been reading long enough about the previous models [TASCAM US-122]("http://ubuntuforums.org/showpost.php?p=6272809&postcount=3") and [US-122l]("http://www.premiumorange.com/la-page-web-of-phil/index.php?page=P030001"), to realize that, in principle, they should work out of the box in latest ubuntu distributions (jaunty, karmic). All the solutions proposed all around to make these cards to work are [already implemented]("http://wiki.briata.org/doku.php#how_to_install_tascam_us-122l") in the latest alsa-firmware-1.0.17 from medibuntu (I have also installed the 1.0.20 version from source), and there is nothing left to do by my side (I think).
The problem seems to be that the new TASCAM US-122 mkII is not compatible with its predecessors.
I don't have any response at all when I plug in the interface: The lights get on for a second and then nothing.. No green light at all, no sound card recognised.
I write here because I don't have any idea about what else to do. This is a brand new model which is replacing the popular previous ones and then, I think it will be necessary to try to make it work with ubuntu.

Is anybody of you familiar with usb audio interfaces and alsa? How could we address this problem?

I will also try to contact alsa for this.
Thanks in advance!

---

### Post by AutoStatic on 2009-12-01
I checked the specifications:
> Bus-powered USB 2.0 audio interface
As far as I know support for USB 2 audio devices is very poor. So the worst case scenario could be that you won't be able to get your device working at the moment. But maybe someone else has better experiences with this device.

---

### Post by delaossa on 2009-12-01
But the TASCAM US-122l model is also a usb 2.0 audio interface and it seems to work..

---

### Post by AutoStatic on 2009-12-02
I don't own a Tascam device myself so it's just an opinion actually amalgamated from what I've read here and there. And like you say, the 122L seems to work but if I'm to believe some of the topics I've read here then it doesn't work flawlessly.

---

### Post by Earl_Maroon on 2010-01-28
If I understand correctly the US122 MkII is an upgrade of the US122L with similar hardware and should work similarly. However, I have a US122L and for some reason I just can't get it to work under Linux though others seem to have more luck, even after following the instructions. I even have a Win 7 partition just for it. It's pretty ridiculous, I know. You might just have to do the same as me for now if you can't get it working. Still, rebooting every time I want to record or play music through my hifi is just stupid. This is easily my main gripe about Linux, but I don't have anything close to the knowledge I need to do anything about it.

---

### Post by robeast on 2010-01-28
The original version of the Tascam US122 was reported to work for some, but from what I've heard the majority of people gave up before they got it usable. I wouldn't be surprised if the mk2 simply won't work at all. Tascam interfaces are not reliable with linux.

---

### Post by Radoka on 2010-02-28
I got 122L, just bought it, and Alsa finds it fine but mixers and programs don't. Getting really frustrated by this. After days of searching I found that I need usb_streams - an alsa module - to fix this, and I got it on my computer, but can't fins out how to use it.

The reason I bought this card was that it was the only one i could find that did what I needed and was reported to work with Ubuntu. It's about time the hardware manufacturers take the Linux world serious and begin to work on drivers for us! I don't want to be forced to buy a windows license just to be able to use my hardware.

---

### Post by sgx on 2010-02-28
> **Radoka said:**
> I got 122L, just bought it, and Alsa finds it fine but mixers and programs don't. Getting really frustrated by this. After days of searching I found that I need usb_streams - an alsa module - to fix this, and I got it on my computer, but can't fins out how to use it.

The reason I bought this card was that it was the only one i could find that did what I needed and was reported to work with Ubuntu. It's about time the hardware manufacturers take the Linux world serious and begin to work on drivers for us! I don't want to be forced to buy a windows license just to be able to use my hardware.
Just sell or trade it, Lexicon, m-audio, Edirol, Focusrite, are among those who make interfaces and soundcards known to work, with capabilities you need. Linux is backwards, in that you must buy hardware known to work, and linux people, sometimes overzealous, give misleading results. I tell people Reaper works for basic Multi-track recording in linux, but don't guarantee advance midi editing, or 40 track multi-format symphonies are possible. 
There must be market share for most companies to see $potential$ in before hiring a coder just to write drivers for what they see as a few dozen loons, who might actually by a soundcard based on a penguin sticker on the box. Linux is under 2% in non-server OS users, and musicians a tiny
slice of that.

Devices stating they work on a Mac are often good choices. But a good hour on google can save you frustration and money, using terms like error, problem, fails, alsa, jackd, a distro name like Fedora/ubuntu/suse, and with the soundcard name in quotes.
Good luck!

---

### Post by Radoka on 2010-03-01
Thanx for your reply, sgx! I guess I'll go back to the store and trade it for a M-audio Fast Track MKII instead. My previous card was a M-audio MobilePre usb-card and it worked fine since I just plugged it in. No driver issues or configurations... Would've kept it if my sound hadn't been distorted in all applications lately. (Think it's broken.)


Edit: Actually my main program is Reaper now and WoW is my favorite game... It makes no sense that I use Ubuntu instead of Windows anymore, just that it is the OS I feel at home with. Damn it! :S

---

### Post by sgx on 2010-03-01
The wine team  has lots of game efforts, this is a WoW/wine page

[http://www.wowwiki.com/World_of_Warcraft_functionality_on_Wine](http://www.wowwiki.com/World_of_Warcraft_functionality_on_Wine)

I use Reaper for recording, and an old maudio pci card, pretty flawless.
There is a linux firmware package for tascam cards out there that helped some people, but new card revisions are usually bad news for us linux folks.

I use this nice audio distro currently
 
[http://www.mellosonic.com/rocxshop.htm](http://www.mellosonic.com/rocxshop.htm) 

download and burn this: 

RXS-Test2.iso 

Its about 340 meg download, makes a nice realtime live-CD based on
PCLinuxOS. 

Cheers




Cheers

---

### Post by Radoka on 2010-03-01
Never seen that distro. I'll check it out! I've been om Ubuntu Studio for four years now and yeah, I'm using Wine for WoW. :) Now I also use Wine for Reaper, Guitar Rig 3 and a bunch of vst-plugins. It's stable and reliable and I can also work with Rosegarden or Ardour if I like. I really hope I can continue like that, but I need good and at least nearly up-to-date hardware too. My old card was using USB 1.1 and I had problems with XRUNS or latency when recording many channels and using lot of realtime effects.

---

### Post by Radoka on 2010-03-01
Damn, Im' good! :P Finally got it working, most thanx to this guide: [http://wiki.briata.org/doku.php?id=testing_us122l_under_linux](http://wiki.briata.org/doku.php?id=testing_us122l_under_linux) 

Step 1 and 2 can be skipped in Ubuntu 9.10 and the rest is easy. The problem was that I was trying to use Qjackctl first with the result usb_stream couldn't be used, or I just couldn't figure out right settings. The command is something like "jackd -RP50 -dalsa -dusb_stream:1 -r44100 -p64 -n2" to start Jack. I had to change 64 to 256 or 512 (depending on projekt size and number of channels).

Another problem was that the card must be plugged after boot to be found at all. So... I boot, connect the US-122L, start Jack with the command line and then open qjackctl. Both Ardour and Reaper works fine now.

---

