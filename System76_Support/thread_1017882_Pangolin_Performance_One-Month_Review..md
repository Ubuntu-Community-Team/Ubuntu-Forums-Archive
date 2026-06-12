---
title: "Pangolin Performance One-Month Review."
date: 2008-12-21
forum: System76 Support
---

### Post by ResumeMan on 2008-12-21
Someone on another thread asked for a review of my Panp4. Since that thread had already devolved from a "yay, I just ordered my laptop" thread to a long tech support discussion, I thought I'd start a new one to discuss the computer itself.

Ordered just before Thanksgiving, the machine is:

```
Pangolin Performance (PAN-P4) = $1,079.00
       Operating System Ubuntu 8.10 (Intrepid Ibex) 64 Bit Linux
       Display Resolution 15.4" WXGA Super Clear Glossy LCD (1280 x 800)
       Processor Core 2 Duo P8400 2.26 GHz 1066 MHz FSB 3 MB L2 (25 Watt)
       Memory 4 GB - DDR2 800 MHz - 2 DIMMs
       Hard Drive 320 GB 5400 RPM SATA II
       Optical Drive CD-RW / DVD-RW
       Wireless 802.11 agn
       Bluetooth Bluetooth
       Extra Battery no extra battery
       Extra AC Adapter no extra AC adapter
       Car AC Adapter no car AC adapter
       Laptop Bag no bag       Hardware Warranty 1 Yr. Ltd. Warranty and Technical Support
```

As you can see from the [other thread]("http://ubuntuforums.org/showthread.php?t=985845"), I've had an ongoing problem with the machine acting really weird on shutdown, which the S76 support team has been great in helping me figure out. It seems that it's finally been isolated as an issue with sharing files via Samba, and hasn't been totally figured out yet. Aside from that glitch it's been fantastic. *(edit: as indicated on the other thread I think I solved that problem by using NFS to share files instead of Samba).*

It's very fast and works well. The keyboard is very good and plenty big. The track pad works well; one nice touch is that along the right side is a line of bumps to help find the spot where you can use the track pad to scroll up and down. My one gripe with the mouse buttons is that they are separated, with the fingerprint scanner between them, and require a fair bit of force to push. This makes it hard to click both buttons at the same time, simulating a middle-click. But I'm getting used to it.

Hardware all seems to work quite well. I'm not totally thrilled w/the camera, but it certainly works, and Cheese handles it appropriately.

Power management works well-but-not-quite-perfectly. Most of the time it suspends just fine when I close the lid, but about 10% of the time the suspend just doesn't happen. I've never had a problem coming back from suspension, though about 2/3 of the time there is no sound when I do (edit: it's now fine, see below). 

Speaking of sound, the speakers *suck*. Cranked to 11, you can hardly hear the sound if there is any ambient noise at all (edit: was just a preset issue; the volume is adequate; perfectly fine for a laptop). Played through headphones, the sound quality is just fine. The wireless card is nice and strong, gets a much better signal from across the house than my old laptop.

The machine is definitely nice looking. I do like the glossy black lid, though it 's a total fingerprint magnet. To say the least I'm not accustomed to cleaning the *outside* of my laptop, but I find myself wiping off fingerprints with the included soft cloth regularly.

This probably isn't pertinent to S76 pe se, but I've been amazed at how well World of Warcraft runs through Wine. It feels just like a native application, with no bugs that I've come across.

It's a robust spec, runs great, and I expect it to be solid for me for a long time.

As alluded to above, the personalized support has been fantastic. Tom has carried on a looooooonnnnggggg troubleshooting thread with me about a very peculiar problem, and has been very responsive. 

So overall I am quite happy with my purchase. If you want a Linux OEM laptop, I think this would be a very good choice.

---

### Post by ResumeMan on 2008-12-28
I just wanted to follow up to note that in the week or so since I fixed the file share issue, the sound has consistently been there on resume. It seems as though the Samba problem was also somehow affecting sound in suspend. I can now pretty much say everything "just works."

---

### Post by DRM_free on 2008-12-28
If the onboard speakers seem too soft, you might need to crank up the "PCM" and "Front" settings using the "alsamixer" command-line utility instead of the default GNOME mixer.

---

### Post by ResumeMan on 2008-12-31
Huh. OK well first of all there was no obvious Gnome settings option. I had to enable "volume control" in the menu. In this dialogue the "Front" slider was down about 1/4 of the way. I moved that to the top, and it really boosted the volume.

I'm not gonna say I'm blown away by the volume or sound quality by any stretch, but for sure it's much better, and is really plenty adequate for a laptop.

Thanks for the (indirect ;)) hint. Now I really don't have much of anything to complain about.

---

### Post by chez17 on 2009-01-06
I also got a Pangolin and wanted to register my thoughts. So far it has been great. The only thing that seems to be not top notch is the actual case for the laptop. I don't know what you would call it. The physical laptop itself, not the hardware inside. I don't know, it just seems cheap to me. The mouse buttons are too hard to click and the cd drive is crazy loud. Anyone else think this?

Also, what command did you run to get the run down on your system like that?

Edit: I realized that it wasn't a command, it's just the summary from the email you get when you buy it. Also, I didn't mean to sound too negative. Literally, every other thing about this laptop is great. Not to mention the top notch support you get in this forum. The only thing I haven't liked so far is the case itself.

---

