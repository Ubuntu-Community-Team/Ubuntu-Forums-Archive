---
title: "What the heck? Ubuntu can't recognize the Motorola Xoom via USB"
date: 2011-03-13
forum: The Cafe
---

### Post by billdotson on 2011-03-13
What the heck? Ubuntu cannot recognize the Motorola Xoom via USB. You have to download a special Windows driver to make it work. My HTC Incredible works just fine without any special drivers.

I even read an article that says that to make it work on Windows you have to enable USB debugging even after the driver is installed (here it is: [http://blogs.computerworld.com/17881/cant_get_your_motorola_xoom_to_work_with_your_pc_heres_how_to_fix_it](http://blogs.computerworld.com/17881/cant_get_your_motorola_xoom_to_work_with_your_pc_heres_how_to_fix_it))

What the heck? Why does my HTC phone not require any special drivers but the Xoom does? What makes it even more dumb is I don't think it has Mac OS X support either. 

It wouldn't be so bad if I could use a microSD card, but Motorola thought it would be a good idea to release the thing before the software could actually recognize one. Great job.

---

### Post by Paqman on 2011-03-13
> **billdotson said:**
> Motorola thought it would be a good idea to release the thing before the software could actually recognize one. Great job.

I think this is the root of your problem. Sounds like a lot of quite basic functionality is missing from the Xoom at launch. Bit of a shocker really; pay full price, get half a tablet.

Will probably be sorted in updates, but that shows a bit a of a lack of respect for the early adopters if you ask me.

---

### Post by andras artois on 2011-03-14
> **Paqman said:**
> I think this is the root of your problem. Sounds like a lot of quite basic functionality is missing from the Xoom at launch. Bit of a shocker really; pay full price, get half a tablet.

Will probably be sorted in updates, but that shows a bit a of a lack of respect for the early adopters if you ask me.

Would you rather have had to wait longer for it? It'll also allow them to fix some of the more apparent bugs in the first update they churn out.

---

### Post by Paqman on 2011-03-14
> **andras artois said:**
> Would you rather have had to wait longer for it?

If I was paying that much money, i'd expect something that worked, so yes. I'd be fuming if later buyers got a better device for cheaper.

---

### Post by NCLI on 2011-03-14
> **Paqman said:**
> If I was paying that much money, i'd expect something that worked, so yes. I'd be fuming if later buyers got a better device for cheaper.
If you're an early adopter, you should expect problems, and for the product to improve and its price lowered down the road.

That's just how it is.

When I bought my PS3 at launch, the internet browser sucked, the store sucked, there was no in-game menu access, I couldn't download stuff in the background, I couldn't connect to my media server, I couldn't connect to netlix, etc. All that has been fixed/added/improved now, and people can get that improved experience at a lower price than what I paid.

Am I pissed? Nope, because I've had longer time with the product, and derived great enjoyment from using it for years now, even with the lacking featureset.

---

### Post by billdotson on 2011-03-15
I just saw something that showed a Mac and Windows file transfer utility (here: [https://motorola-global-portal.custhelp.com/app/answers/detail/a_id/61296/~/motorola-xoom---transfer-files-to%2Ffrom-my-computer#mac](https://motorola-global-portal.custhelp.com/app/answers/detail/a_id/61296/~/motorola-xoom---transfer-files-to%2Ffrom-my-computer#mac))
and something about transferring files to and from the device using Linux OSes here: [https://supportforums.motorola.com/thread/45977?tstart=0]("https://supportforums.motorola.com/thread/45977?tstart=0")

I haven't tried the Linux fix yet, but that is still ridiculous. I didn't have to do anything special at all to make my HTC droid act as removable media.

I am just testing it now and it automatically installs the right driver in Windows Vista x64. However, it doesn't mount it as a normal drive, it mounts it as a media player. When you are in the Xoom folder you cannot create files via the Windows explorer file manager. The only way to put things on the device is to copy them. I don't know what other things you can't do since it is seen as a media player instead of a FAT partition or something else.

I'm not as irritated about this device as I would think other people would be because I got mine as a gift. However, I wish the person who gave me the device would've asked me about it first because I would have gladly gotten a netbook or a laptop instead. If I decide to do any freelance work I can't really do anything all that important on a tablet (OS, filesystem utilities, media editing, etc.) Heck, I could have probably gotten a netbook and had enough money saved to buy all the PC games I want to get this year.

I will post my frustrations with it in another thread, as that isn't what this thread is about.

NCLI: the difference between the Xoom not working correctly and the PS3 not working correctly is that the PS3 still performed its main function of playing games. Internet on a game console isn't a high priority, download backgrounds are nice but they don't ruin the device, media server could be a big deal depending on who it is (I've never had the need for a media server personally as all my stuff has always been in the same room), and the store is iffy on importance. If games didn't work correctly on it then you would be pissed.
My experience with the Xoom is that lots of advertised features are missing or not working correctly.

---

### Post by sog on 2011-03-15
I can confirm that the linked solution to file transfer works on Ubuntu. Or at least I did, until an upgrade to Maverick removed gnomad2. The catch - assuming you can install it - is that gnomad2 is very buggy. 

Otherwise, it's a matter of waiting for tools to catch up. The MTP libraries are present, they're just immature for want of demand; as most Android devices have used USB storage, there just wasn't much incentive. If the MTP transition w/ Honeycomb is permanent, expect the tools on Ubuntu and elsewhere to become more stable.

---

### Post by Paqman on 2011-03-15
> **sog said:**
> I can confirm that the linked solution to file transfer works on Ubuntu. Or at least I did, until an upgrade to Maverick removed gnomad2. The catch - assuming you can install it - is that gnomad2 is very buggy. 

Otherwise, it's a matter of waiting for tools to catch up. The MTP libraries are present, they're just immature for want of demand; as most Android devices have used USB storage, there just wasn't much incentive. If the MTP transition w/ Honeycomb is permanent, expect the tools on Ubuntu and elsewhere to become more stable.

I've found Gnomad has become a bit unnecessary. Banshee can handle MTP devices really well now, and I assume it's the same with other players.

---

### Post by sog on 2011-03-15
> I've found Gnomad has become a bit unnecessary. Banshee can handle MTP devices really well now, and I assume it's the same with other players.


Does Banshee handle video and other non-music assets? My problem wasn't music, but everything else I wanted to load. 

In the meantime, here's a [working solution]("http://forum.xda-developers.com/showthread.php?t=981774") for MTP mounting on 10.10. No gnomad required.

---

### Post by Paqman on 2011-03-15
> **sog said:**
> Does Banshee handle video and other non-music assets? My problem wasn't music, but everything else I wanted to load. 


Definitely does video, haven't tried anything else.

---

### Post by 3rdalbum on 2011-03-15
> **NCLI said:**
> If you're an early adopter, you should expect problems, and for the product to improve and its price lowered down the road.

That's just how it is.

When I bought my PS3 at launch, the internet browser sucked, the store sucked, there was no in-game menu access, I couldn't download stuff in the background, I couldn't connect to my media server, I couldn't connect to netlix, etc. All that has been fixed/added/improved now, and people can get that improved experience at a lower price than what I paid.

When I bought my PS3, it wouldn't play certain Blurays, and sometimes would freeze up while playing other certain Blurays.

I bought it last year, and the problems still occur.

By comparison, the Nintendo Wii has been pretty well flawless since day dot.

Early adopters shouldn't have to have problems, and there's no guarantees that the problems will be fixed.

---

### Post by NCLI on 2011-03-15
> **3rdalbum said:**
> When I bought my PS3, it wouldn't play certain Blurays, and sometimes would freeze up while playing other certain Blurays.

I bought it last year, and the problems still occur.

By comparison, the Nintendo Wii has been pretty well flawless since day dot.

Early adopters shouldn't have to have problems, and there's no guarantees that the problems will be fixed.
You must be unlucky, [PS3 and Wii failure rates are pretty much the same]("http://www.engadget.com/2008/02/14/xbox-360-failure-rate-at-16/"), which is honestly kinda embarrasing for the Wii, considering the old, well-tested technology it's built on.

You should return your PS3, they'll give you a new one for free.

---

### Post by 3rdalbum on 2011-03-15
My PS3 hasn't failed, it's not broken... it's a software problem. Can't find my receipt anyway (major electronics purchases should involve you getting an A4-size receipt, so you can find it when you need to claim on the warranty).

---

