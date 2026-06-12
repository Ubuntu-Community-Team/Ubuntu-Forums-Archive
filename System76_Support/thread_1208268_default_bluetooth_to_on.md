---
title: "default bluetooth to on?"
date: 2009-07-09
forum: System76 Support
---

### Post by slide_o_mix on 2009-07-09
I purchased a System76 Pangolin Performance laptop for my wife who is a novice computer user (she knows how to email, surf the web and do word processing). I recently purchased a bluetooth mouse for her because she doesn't like the trackpad. I would like to know if it is possible to have the bluetooth default to on instead of having to press Fn+F12 to turn it on each time.

Thanks!

slide

---

### Post by ibutho on 2009-07-09
Try running
```
sudo update-rc.d bluetooth defaults
```

---

### Post by Derath on 2009-07-09
If I recall correctly, the onboard bluetooth is hardware controlled, I don't recall seeing anything on how to default it on. Although I'm eagerly awaiting Tom's response on this one as well.

---

### Post by TheBuzzSaw on 2009-07-09
I don't know about the Pangolin, but on my daru2, the Bluetooth seems to be automatically paired with the Wifi antennae. They both turn on/off together. So, naturally, mine is always on.

---

### Post by thomasaaron on 2009-07-09
Yes, the DarU2 is a different story altogether. On the DarU3, the PanP4n, PanP5, SerP5, BonP2, the bluetooth is off by default and must be enabled by the function key combination.

I've spent many a weary night trying get it to be on by defalut. No dice.

The link between the Fn-F12 combination and the bluetooth adapter seems to be at the BIOS level.

---

### Post by TheBuzzSaw on 2009-07-09
I wish I had the answer, but *someone* has to know how to trigger those function key combination signals using a simple script. From there, it would be easy to have that script run on startup consistently.

---

### Post by robert.rankin.jr on 2009-07-22
Bleh, this is frustrating. I've googled forever, but the problem is that the Fn key triggers a Bios event -- apparently Ubuntu doesn't even recognize it, and cannot trigger it. I guess it's just laziness on my part, but it would be nice.

Robert

---

### Post by Lee_Machine on 2009-07-23
I too wanted to do this in my Panp4n about six months ago, but I never did find a way to do it. 

I did discover a tool called hciconfig that lets you do all sorts of cool stuff with your bluetooth card. But alas Fn-F12 has to be pressed to turn the card on. 

Another one is hcidump...like I never knew IPv6 worked over bluetooth with strong encryption..hmmm :D

Anywho your wife must press Fn-F12

---

### Post by Lee_Machine on 2009-07-23
Oh btw bluetooth is kept off to save power.

---

### Post by rumblered on 2009-07-24
Try this:

ls -l /sys/class/rfkill

There might be something useful in there. On Karmic with a 2.6.31-rc4 kernel, I now have an rfkill device specifically for Bluetooth. On my gazv5 with a hardware switch, I can't actually write to its state, but that might work for you. You'd want to try writing a 0, 1, or 2 to the state file in the rfkill device as root:

sudo bash
echo 1 > /sys/class/rfkill/rfkill1/state

If there's no rfkill device for your Bluetooth interface, you could try booting a Karmic daily build and checking for one there. If you find that it works there, you'll know a resolution is coming.

---

