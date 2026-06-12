---
title: "Darter monitor trouble"
date: 2007-08-18
forum: System76 Support
---

### Post by poetbeware on 2007-08-18
1. The laptop screen doesn't seem to be in 24 bit color. I'm getting weird banding in the gradients as if it's only 16 bit color. Everything looks fine on an external monitor. How can I tell what xorg decided to use?

2. I can only get an external monitor to work if I reboot after hooking up the VGA cord, is that normal?

3. Any attempt to change the resolution using System/Preferences causes X to quit, and punts me to gdm. (This is only if I have an external monitor connected.)

4. I have a HDTV that's 1920x1080 with a VGA input. When I try to hook the Darter to it, the TV says "Invalid mode." Not sure what that means, but can the Darter's graphics card handle 1920x1080 resolution?

5. What should Fn-F2 and Fn-F3 do on this machine? It looks like one of those two should cycle through the video outputs but when I hit Fn-F2, nothing happens, and when I hit Fn-F3 the machine locks up (can't move the cursor) until I hit Fn-F3 again. All of the other Fn F keys work, F4 and F5 control the brightness properly.

Any help is much appreciated...

-Paul

---

### Post by imhavoc on 2007-08-18
5: Fn-F3 switches the touchpad on/off

the rest, I can't help you with.

---

### Post by saxamo on 2007-08-18
> **poetbeware said:**
> 1. The laptop screen doesn't seem to be in 24 bit color. I'm getting weird banding in the gradients as if it's only 16 bit color. Everything looks fine on an external monitor. How can I tell what xorg decided to use?

3. Any attempt to change the resolution using System/Preferences causes X to quit, and punts me to gdm. (This is only if I have an external monitor connected.)



I am having trouble with these two as well. I haven't tried hooking up to an external monitor but I will. 

And the resolution lock up happens to me even without an external monitor. It even locks up when I try to play a full screen game or something that changes the screen resolution. I'm on a new darter too...

---

### Post by ackey on 2007-08-18
The first time I hooked up to an external monitor I had to restart, but since then it has worked as soon as I plugged it in.  Also had a project work once I plugged it in.  When the external monitor is connected both it and the laptop screen display, so I haven't tried to switch display.  I'm running Feisty on the new darter.

---

### Post by poetbeware on 2007-08-19
OK. I was planning to get a new monitor anyway, so I accelerated that plan and now have a beautiful 24" LG monitor hooked up to my little Darter, so now I'm mostly happy.

1. /var/log/Xorg.0.log tells you the color depth. According to the log, the Intel graphics chip thingy is spitting out 24 bits of color depth. This makes sense, as external monitors do not have the banding issue. Now, this is not a huge issue for ME, what with the beautiful new monitor, but I do think that System76 should perhaps mention on the Darter product page that the laptop screen only does 16 bit color. 

2. Thank you ackey, you are correct. When I hooked up the Darter to the monitor a second time I did not have to reboot. This is weird to me; apparently the BIOS has to be consulted to see what's attached? Weird weird weird. But only having to reboot once per monitor is acceptable to me, as I only have my work monitor and my beautiful new home monitor to worry about.

3. This is still unresolved. Seems like a bug. Not a big deal for me at this point, as my monitors' default resolutions are correct, and I was only trying to change the resolution to see if that would trick the laptop into recognizing new monitors. Still, it might be a deal-breaker for others.

4. I'm still investigating this, but the modprobe is noticing two 1920x1080 modes for the TV, one at 59hz and one at 60hz. It's using the 59hz one by default, I'm going to see if I can wiggle it to use the 60hz instead. That might be what my TV expects.

5. Thanks imahavoc, the icon on the F3 key made no sense to me. So I guess Fn-F3 works as advertised. Fn-F2 doesn't do anything; it would be nice to be able to shut off the laptop screen while I have the beautiful new monitor hooked up. Pressing Fn-F2 does cause some disk activity, and the following gets spit to Xorg.0.log:

(II) PM Event received: Capability Changed
I830PMEvent: Capability change

So the key is getting noticed, but nothing happens.

As a side note, I installed Beryl, and Beryl + 24" LG Monitor = Happiness.

If anyone can provide clues towards #3 or #5, I'd appreciate it. With #5, I don't necessarily need Fn-F2 to work, as long as there's some other way (even command-line) to shut off the laptop screen when I don't need it.

Thanks everyone,

-Paul

---

### Post by thomasaaron on 2007-08-20
Regarding number 5. If the key is being recognized, blanking the monitor is probably as simple as a little shell script.

Post a bug on it, and we'll see what we can do.

Best,
Tom

---

### Post by ackey on 2007-08-20
It looks like Fn-F2 does do something.  I attached the monitor before boot and it was doubling output, until the login screen.  Then it was receiving a signal but not displaying.  Fn-F2 made the external monitor display, but any further Fn-F2 didn't do anything.  

So Fn-F2 activates the external monitor, but doesn't seem to toggle...

---

### Post by crichell on 2007-08-22
Hi Guys,

> 3. This is still unresolved. Seems like a bug. Not a big deal for me at this point, as my monitors' default resolutions are correct, and I was only trying to change the resolution to see if that would trick the laptop into recognizing new monitors. Still, it might be a deal-breaker for others.

This is a bug (or lack of feature) in X.  Good news however; significant improvments to external monitor recognition or coming down with Ubuntu's next release in October.  X 7.3 includes many enhancements and in my testing works far better than Feisty.  I don't advocate upgrading until release - stuff breaks along the way :-).

---

### Post by poetbeware on 2007-08-22
I have submitted bug #133974 for #5.

Hopefully Gutsy will address #3.

Still unresolved is System/Preferences/Screen Resolution crashing X, should I file another bug on that?

Also, does HDMI output work? My new monitor has HDMI in. Xorg.log spits out a bunch of new stuff when I try connecting via HDMI, but it's defaulting to the wrong resolution (1300ish when the monitor prefers 1920x1080). If HDMI isn't supported I'll just continue to use VGA, but at this point I'm morbidly curious about my hardware. ;)

---

### Post by poetbeware on 2007-08-22
PS thank you everyone!

---

### Post by crichell on 2007-08-22
> Still unresolved is System/Preferences/Screen Resolution crashing X, should I file another bug on that?

I think this is an X bug (i.e. not particluar to the Darter).  X isn't recognizing that the monitor does not support a particular resolution + refresh rate and when X tries to apply the combination it chokes.  We'll give it another look in our lab.  (BTW, never hurts to file a bug report - even if we have to say "it has to be fixed upstream".  I think that's the case with this one.

> Also, does HDMI output work? My new monitor has HDMI in. Xorg.log spits out a bunch of new stuff when I try connecting via HDMI, but it's defaulting to the wrong resolution (1300ish when the monitor prefers 1920x1080). If HDMI isn't supported I'll just continue to use VGA, but at this point I'm morbidly curious about my hardware.

That is a sweet monitor.  I don't have HDMI equipment to test yet.  Try to plug in the monitor via HDMI and run:

sudo dpkg-reconfigure xserver-xorg

That may be your best shot.  Make a backup of your xorg.conf file first:

sudo cp /etc/X11/xorg.conf /etc/X11/xorg,conf_backup

---

