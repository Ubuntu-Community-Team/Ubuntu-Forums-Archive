---
title: "Mini Review of HP 311 Mini"
date: 2009-11-09
forum: The Cafe
---

### Post by decoherence on 2009-11-09
I just got an HP 311, an Ion-powered NetBook. Aside from having a half-decent graphics chip, the display resolution is a fairly comfortable 1366x768 and the keyboard is pretty nice. Takes a bit of getting used to, much like the keys on the MacBooks, but once I got used to it I'm able to type at full speed.

After tax and shipping, the system was just under $500 Canadian from Amazon. And of course, it ships with Windows. XP, in this case.

Because this is a Canadian multi-lingual model (french or english) I had to pick one when it first started. I picked English, being fairly sucky at French, put in the other information it wanted and less than ten minutes later I was logged in to a fairly stock XP desktop. God what an ugly theme, but I digress. I did some typing and found that I had some wacky keymap. Evidently this is the standard multi-lingual Canadian keymap. Switched it to US, thankyouverymuch. Do any Canadians actually use that keymap? Why would we want easy access to a British pound symbol, anyway? Ah, I digress yet again.

One hugely annoying thing is that, by default, the trackpad is set to "tap-to-click." On such a small computer, it is only a matter of time before an errant thumb brushes the trackpad and moves your cursor two paragraphs up. Fixed that, thankyouverymuch.

Anyway, you might be wondering what my Linux plans are for this currently XP desktop. I'll be putting Karmic on it, for sure, but first I'm downloading my main vice (WoW) to see how it runs with the Ion hardware.

I'm very happy with how cool and quiet it is, though we'll see how it does with WoW running.

I'll post a 'part 2' comparing its performance to that of the other computers I have run WoW on (a PowerPC Mac and via WINE on an older Athlon.) Don't expect huge numbers, but as long as it can beat out the Mac and WINE, I'll be pleased.

Then I'll post a 'part 3' once I have Ubuntu on it. I imagine that'll be the 'meat.'

Thanks for reading!

---

### Post by decoherence on 2009-11-10
Here's a quick part-two. It runs WoW a bit better than the Mac and the AMD/WINE while running at a higher resolution and similar special effects settings (slider in the middle.)

I played for half an hour with it sitting on my lap and it did not warm up significantly. Heat is definitely not an issue, even when doing interactive 3D at 1366x768.

I've had enough of this OS, though. I switched from the silly blue theme to the "classic" windows theme which bought XP some time, but I'm writing UNR to a USB disk right now, so its time has come.

---

### Post by decoherence on 2009-11-12
Quick part-3!

As I was downloading UNR and replying to a post on here (yes, I was using Windows to post on here! Horrors!) Windows downloaded a bunch of updates that required the system to be restarted. Every five minutes it would pop up a dialogue box saying the computer would shut down if I didn't tell it not to. Super annoying. So when UNR finally downloaded it and I imaged it to the USB disk, I waited for the dialogue to pop up again and let it restart. And that was the last Windows ever saw of that computer. Sure, it's pretty cheap poetic justice, but it's poetic justice all the same.

The only problem with UNR was after the hard drive installation when Jockey wouldn't offer to install restricted drivers (wireless and nvidia.) It did offer when I was running it from the USB key. Can anyone tell me why it would work in one and not the other?

Once I plugged it in to ethernet and updated things, jockey started working properly. But I wasn't plugged in to ethernet when I was booted from the USB key so it is still a mystery to me.

Anyhoo, with all that sorted, things are running beautifully! Clutter screams along nicely.

---

### Post by m4sterblast3r on 2009-11-12
nice i just got my hp 311 too. its very cool also cause this is my first portable machine. i plan on putting ubuntu but im still waiting for a dvd burner to arrive that i got on amazon. need to burn a recovery disk of win 7 before i start messing around heh. cant wait for your results, laters.

---

### Post by watchthestars on 2009-11-15
I got the 311 also. I opted for Win7, 160gb, 1 bg ram (hp charged too much and I'll upgrade on my own at some point) and the 802.11 b/g w/bluetooth.

I promptly installed 9.10 and everything worked out for the most part.  I used System > Administration > Hardware Drivers to update the ION and Broadcom drivers. Bluetooth was a bit of a pain. Until today the rf kill switch would stop wifi and blutooth but only bring back up wifi. I performed a package update today and now the rf kill switch is fine (I even got the mini to pair with an iphone and enable tethering).

The only annoyance left is the trackpad. I need to figure out how to turn it off while typing. Any suggestions would be great.

Windows 7 doesn't like sharing and forces me into a recovery mode almost every time I boot into it now. Whenever I have the time I'll sort that out, it's just not a priority at this point. 

Also, if you have an 8gb usb flash drive you can use that to create a bootable recovery drive using hp's utility.

---

### Post by Ian dewhurst on 2009-11-15
I think the problem you had with the drivers was that it was blacklisted. I had the same trouble after a fresh install of karmic.
This is easily rectified with uncommenting the blacklisted drivers in

sudo gedit /etc/modprobe.d/blacklist.conf

They should then be available in restricted drivers.
(If memory serves me correct)

---

### Post by watchthestars on 2009-11-15
> **Ian dewhurst said:**
> I think the problem you had with the drivers was that it was blacklisted. I had the same trouble after a fresh install of karmic.
This is easily rectified with uncommenting the blacklisted drivers in

sudo gedit /etc/modprobe.d/blacklist.conf

They should then be available in restricted drivers.
(If memory serves me correct)

At some point during the process of sorting everything out I made sure my drivers weren't on the blacklist. I even went so far as to add b43 and ssb to the blacklist since I was having a boot issue when the b43 driver would load as the default when STA wasn't installed.

---

### Post by nroof22 on 2010-02-06
My HP Mini 311 is configured to dual boot (Win 7 and UNR).  All working well, now want to add an external DVD burner.  Searched forums for recommendations and/or working solutions.  Any suggestions, recommendations or experiences to relate?

---

### Post by juancarlospaco on 2010-02-06
Attach a picture of the big machine on action ;)

---

### Post by xenmax on 2010-02-25
hope get my hands on my hp mini 311 arriving next week!!

---

