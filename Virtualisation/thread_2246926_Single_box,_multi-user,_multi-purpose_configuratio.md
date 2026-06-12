---
title: "Single box, multi-user, multi-purpose configurations: Virtualbox, MultiseatX, other?"
date: 2014-10-04
forum: Virtualisation
---

### Post by skyemoor on 2014-10-04
I am weighing the pros and cons of 3 primary architectural alternatives with Ubuntu Studio 14.04 as the  host OS for a primary computer, and would appreciate the insights of those who have had experience using Ubuntu in multi-user, multi-purpose configurations. I've been running Ubuntu (and now *Ubuntu Studio 14.04*) at home for several years now, have some Java development and systems engineering experience, and consider myself a capable Linux beginner, not yet at the intermediate stage.

**[SIZE=4]Needs:[/SIZE]**

1. Home automation runtime ([OpenHab]("http://www.openhab.org/")), including HD camera monitoring and video analytics on all the time, access to USB devices and future various peripherals
2. Home automation development (also OpenHab, somewhat heavy Eclipse environment)
3. Personal computer for me. My 2GB Latitude D630 is too weak to support the home automation runtime, development environment, and dozens of Firefox tabs, etc
4. Personal computer for teenage daughter. Her Dell Mini with Atom N450 is rather slow, though could possible act as a dumb terminal along with her 23" monitor.
5. Musical composition and multitrack audio studio (hence Ubuntu Studio, but this is not required for the complete system, I could use this only on my laptop)
6. No need for special gaming support

**[SIZE=4]Assets;[/SIZE]**
 - soon-to-arrive [Zotac Zbox i7-4770T 16GB mini desktop]("http://www.zotac.com/products/mini-pcs/zbox/intel/product/intel/detail/zbox-iq01/sort/starttime/order/DESC/amount/10/section/specifications.html") with SSD intended to cover as much as the above as possible.
 - Latitude D630 (not terribly long for this world) with a 23" monitor
 - Dell Mini with Atom N450 (not powerful enough on its own to run a browser with many windows, Libre suite, etc) with a 23" monitor, keyboard, mouse

**[SIZE=4]Alternatives[/SIZE]**:

A. **Virtualbox** with separate VMs for myself and my daughter. The [Virtualbox instructions]("http://www.virtualbox.org/manual/ch03.html#idp55245984") for accessing USB, audio, serial, etc seem straightforward, though as I'm currently using a USB ZWave controller and will be using audio (perhaps SPDIF), one-wire, and other hardware interfaces, I would like to know what hw peripheral experience others have had before going too far down that pike.

B. [**MultiSeatX** ]("https://help.ubuntu.com/community/MultiseatX")approach (which is not straightforward for even regular Ubuntu much less Studio), or 

C. **1 user local, 1 remote**; Letting my daughter use the Zbox as her computer with me utilizing a remote logon (FreeNX, etc) to access the home automation runtime, development, personal use from the older laptop. I am assuming I can leave a desktop process running the OpenHab runtime on all the time, just reattaching to it via FreeNX when I want to make any adjustments.

D. **KVM** (update: thanks *TheFu*!): (I need to look into this more, though lack of video playback would preclude it's use for camera video playback)

Thoughts, cautions, suggestions, humour?

---

### Post by TheFu on 2014-10-04
I don't know anything about home automation. Sorry.

Is 16G enough to run java? ;) I avoid anything with java for a number of reasons, both at home and work. Promises made by Sun, then Oracle have never been achieved. Too much history that began in 1994-ish to get into.

FreeNX isn't working so well with 14.04 and later. Check out x2go as a replacement. It is easier to setup and has built-in audio support. Uses the NX protocol and is actively developed. Sadly, no Android client, but all the other platforms are covered.

Instead of virtualbox, perhaps a more stable solution like KVM would make sense?  With x2go, you can have everyone remote into the main system over the network and use that for most things - just not video playback.  I switched to using a KVM remote desktop over 2 yrs ago. I'm using it now.  Switched from FreeNX to x2go over the summer. Mostly happy about the switch - some of the client-side features in x2go are nicer, 1 is worse, but probably won't matter to 99.95% of the people.

Passthru to VMs of any sort isn't always possible or straight forward.  Often, it works perfectly, but ... sometimes not.  This applies more to non-standard things - anything that isn't storage, basically.  I know places that use passthru constantly and don't have issues - these are mostly for network or storage cards - not consumer-type things.

---

### Post by skyemoor on 2014-10-05
Thanks, TheFu. Since I plan on running Ubuntu Studio, XFCE4 is the desktop, which is not yet supported by x2go.  However, my server doesn't have to run US, so I may choose a vanilla Gnome version.

---

### Post by TheFu on 2014-10-05
I'm confused.  What is special about xfce4 that mean you can not start it with the "custom" option? Provided it doesn't require accel-GPU support, it will work.
I run openbox directly this way, but I have used a non-standard lxde and tried other WMs too.  Google found a "gist" that explained how to do this for XFCE4. Basically, it is just setting up a few environment variables before running the normal startxfce4 script. I didn't test it; don't have xfce4 installed here and don't want to have all that extra stuff on the systems.

"US"?

---

### Post by skyemoor on 2014-10-05
You are right, I was overly focused on the [Desktop Binding]("http://wiki.x2go.org/doku.php/wiki:advanced:desktopbindings") planned support for xfce4 for x2go. I'm setting x2go up now, actually, thanks for the pointer.

"US" = Ubuntu Studio

---

