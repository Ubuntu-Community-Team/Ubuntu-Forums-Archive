---
title: "Lemur Ultra - unboxing video, general impressions and Wifi issue"
date: 2012-08-19
forum: System76 Support
---

### Post by matthewpetty on 2012-08-19
I've had my Lemur Ultra for a few weeks now, and I wanted to share my first impressions, and a couple of issues I have with it.

I have an unboxing video (with a twist) here: [https://vimeo.com/46599898](https://vimeo.com/46599898)

I also have a couple of blog posts about my first impressions: [http://petty.me.uk/?p=2801](http://petty.me.uk/?p=2801)
[http://petty.me.uk/?p=2777](http://petty.me.uk/?p=2777)

Overall I'm happy, but there are a couple of issues which are annoying me.

Firstly, the wifi is pretty bad at getting a signal. Between my wife and I, we have various laptops. They often get used in the office, away from the router. They all connect and get a wifi signal fine. That's a couple of Lenovo Thinkpad Windows work laptops, my wife's Macbook, and my old Dell 10V, which I got free with my cable package and installed Lubuntu on. But this Lemur won't connect until I bring it out near the router, and then it's pretty weak connection.

Even now, I'm sitting right in front of the router, about 8 feet away, and the signal fluctuates.

I can't move the router to the office. I don't want to have to get some kind of booster - I shouldn't have to, when it's clearly an issue with the Lemur. The model of the router shouldn't matter, when all the other laptops work fine with it. FWIW, it's an Apple Airport Extreme.

The wifi module is Intel Centrino 1030 – 802.11 b/g/n Wireless LAN + Bluetooth Combo Module. Are there some settings I can tweak? Any suggestions? I specifically got a System76 so I wouldn't have to worry about compatibility and stuff.

I also have an issue with the Bluetooth. I have a Logitech bluetooth mouse, which has suddenly stopped connecting. I had to install blueman to be able to pair it (which is crazy). Now I have two bluetooth logos in the notification area. The mouse worked for a while, reconnecting after suspend, and working smoothly. Just today, it started lagging badly, and then stopped working. Now it won't connect. The batteries are fresh.

Hope someone can help.

---

### Post by Ubun2to on 2012-08-20
> **matthewpetty said:**
> I've had my Lemur Ultra for a few weeks now, and I wanted to share my first impressions, and a couple of issues I have with it.

I have an unboxing video (with a twist) here: [https://vimeo.com/46599898](https://vimeo.com/46599898)

I also have a couple of blog posts about my first impressions: [http://petty.me.uk/?p=2801](http://petty.me.uk/?p=2801)
[http://petty.me.uk/?p=2777](http://petty.me.uk/?p=2777)

Overall I'm happy, but there are a couple of issues which are annoying me.

Firstly, the wifi is pretty bad at getting a signal. Between my wife and I, we have various laptops. They often get used in the office, away from the router. They all connect and get a wifi signal fine. That's a couple of Lenovo Thinkpad Windows work laptops, my wife's Macbook, and my old Dell 10V, which I got free with my cable package and installed Lubuntu on. But this Lemur won't connect until I bring it out near the router, and then it's pretty weak connection.

Even now, I'm sitting right in front of the router, about 8 feet away, and the signal fluctuates.

I can't move the router to the office. I don't want to have to get some kind of booster - I shouldn't have to, when it's clearly an issue with the Lemur. The model of the router shouldn't matter, when all the other laptops work fine with it. FWIW, it's an Apple Airport Extreme.

The wifi module is Intel Centrino 1030 – 802.11 b/g/n Wireless LAN + Bluetooth Combo Module. Are there some settings I can tweak? Any suggestions? I specifically got a System76 so I wouldn't have to worry about compatibility and stuff.

I also have an issue with the Bluetooth. I have a Logitech bluetooth mouse, which has suddenly stopped connecting. I had to install blueman to be able to pair it (which is crazy). Now I have two bluetooth logos in the notification area. The mouse worked for a while, reconnecting after suspend, and working smoothly. Just today, it started lagging badly, and then stopped working. Now it won't connect. The batteries are fresh.

Hope someone can help.

Your lucky-my laptop didn't come pre-charged. But, I live on the east coast, so it had plenty of time to drain itself during shipping (and when it was sitting around at my house, waiting to be opened), so it doesn't surprise me.
Also, since you got the SSD, I take it that you got a Crucial? I remember getting a sticker that said "Speed Demon" on it, as I got the Intel SSD (but I obviously didn't use it-I dislike how ugly stickers make laptops look if they aren't made to blend in with the color scheme).
Anyway, what kernel do you have? Post the output of this command:
```
uname -a
```
There was a bug with the kernel not being upgraded and it had issues with the Intel HD graphics, but there could also be an undocumented bug caused by an outdated kernel.
I have the Intel A/B/G/N + Bluetooth chip, so I can't really help you, besides suggest that the chip woke up on the wrong end of the manufacturing line (see what I did there?).
I started using the Bluetooth last night, and I LOVE it. It is so nice being able to send and receive stuff to and from my Droid Razr without hooking in the USB cable. I just wish the Internet sharing feature would work.

---

### Post by gaussian on 2012-08-20
I might becoming an official spokepearson for disabling N-mode in wirelest :) 

Gven my experience with two laptops having Intel cards (one Lemur, other an Acer), I would recommend trying to disable 802.11N from the Kernel driver. See this thread for ideas: [http://ubuntuforums.org/showthread.php?t=2029509](http://ubuntuforums.org/showthread.php?t=2029509)

---

### Post by matthewpetty on 2012-08-20
Ubun2to, here's the results of uname -a:
Linux matthew-Lemur-Ultra 3.2.0-29-generic #46-Ubuntu SMP Fri Jul 27 17:03:23 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

When I first got the laptop, there were a couple of freezes, and I had to run some updates on the advice of System76 support. I seem to recall them saying something about the kernel. Don't know if that's related.

gaussian, I saw that thread while searching. I'll give it a shot.

---

### Post by Ubun2to on 2012-08-21
> **matthewpetty said:**
> Ubun2to, here's the results of uname -a:
Linux matthew-Lemur-Ultra 3.2.0-29-generic #46-Ubuntu SMP Fri Jul 27 17:03:23 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

When I first got the laptop, there were a couple of freezes, and I had to run some updates on the advice of System76 support. I seem to recall them saying something about the kernel. Don't know if that's related.

gaussian, I saw that thread while searching. I'll give it a shot.

Well, you have the latest kernel. So, that clearly can't be the problem (I mean bad drivers included with the kernel).

---

### Post by brdmn on 2012-08-22
> **gaussian said:**
> I might becoming an official spokepearson for disabling N-mode in wirelest :) 
[]("http://ubuntuforums.org/showthread.php?t=2029509")

Interesting.  I'm using stock configuration, and just looked at my connection information for the first time.  I'm not sure what the default tool in Xubuntu is, but the info doesn't say anything about g vs. n.  Reported speed is 65 Mb/s, which seems too high for g and too low for n.

---

### Post by Ubun2to on 2012-08-22
> **brdmn said:**
> Interesting.  I'm using stock configuration, and just looked at my connection information for the first time.  I'm not sure what the default tool in Xubuntu is, but the info doesn't say anything about g vs. n.  Reported speed is 65 Mb/s, which seems too high for g and too low for n.

Lucky. I got 1 MB/s. But, that's probably because I'm on the edge of my network.

---

### Post by matthewpetty on 2012-08-27
Gaussian, I followed the instructions you linked to, to disable N-mode, and that seems to have worked. I'm now able to work in my office, connected to the router in the other room. It connects automatically after booting, and reconnects after suspend.

Thank you very much! :D

The Bluetooth issue seems to have been fixed by replacing the batteries in the mouse. I was using the ones supplied with the mouse, so I guess they died after a week's use. Oh well.

---

