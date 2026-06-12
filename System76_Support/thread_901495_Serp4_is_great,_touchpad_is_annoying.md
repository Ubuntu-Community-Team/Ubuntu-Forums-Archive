---
title: "Serp4 is great, touchpad is annoying"
date: 2008-08-26
forum: System76 Support
---

### Post by nightmareci on 2008-08-26
So yeah, got my new serp4 model now, am glad I got it before the stock ran out. But the main problem I'm having is getting the touchpad configurable. I've read about enabling SHMConfig in xorg.conf, and I've tried that, only to either have nothing happen, or have Xorg crash the next time I start Xorg, requiring me to revert to a working xorg.conf. I just want to turn off tap-clicking, as it makes working with the touchpad difficult. I also tried putting Synaptics configuration options in xorg.conf, only to have those ignored as well.

---

### Post by thomasaaron on 2008-08-26
The serp4 has an elantech touchpad. GSynaptics will not work with it, and there is not another driver ready for it, though there is one in development.

For now, the only configuration for it is via System > Preferences > Mouse.

---

### Post by nightmareci on 2008-08-26
Thank you for the reply. I think I read somewhere that it might be an elantech touchpad, but I had no way to confirm it for the serp4 model. I'm getting somewhat used to the annoying tap-clicking, so I guess I'll manage until the driver is ready.

Oh, just a quick question, there's these two rectangular buttons on the left of the keyboard on the serp4, one that has an 'S' shape with a power plug on the end as a label, the other with a USB symbol with a tiny lightening bolt near it, and I have no idea what they're for. I'd like to know if they do anything, or are just buttons that generate keycodes that aren't used right now. I already read about the other extra buttons above the F# keys, such as "Wow Video" and "Wow Audio", they're just extra keys.

---

### Post by SilverDragon on 2008-08-26
> I already read about the other extra buttons above the F# keys, such as "Wow Video" and "Wow Audio", they're just extra keys.

I was wondering what those were for. Thanks for clearing that up.

> Oh, just a quick question, there's these two rectangular buttons on the left of the keyboard on the serp4, one that has an 'S' shape with a power plug on the end as a label, the other with a USB symbol with a tiny lightening bolt near it, and I have no idea what they're for

I thought the S button was the suspend button, but I haven't tested that out. I'm also curious to know what the tiny lightening bolt does.

---

### Post by nightmareci on 2008-08-27
Turns out the "driver disc" that the serp4 came with isn't worthless to us Linux users: It contains two user manuals, with some useful information (lots of XP/Vista stuff, though). The one you'd want to read would be '/media/cdrom0/manual/FL92-30_UM.pdf' (on my system/disc), as the serp4 is really a Compal JFL92, rebranded system76. The manual talks a little about those two buttons, calling the 'S' button the 'Q-Charging'  button, which has something to do with charging the battery (no idea exactly what), and the USB/Lightening button is called the 'Power USB' button, which supposedly makes high-powered devices (think iPod's or something that charges) get more mA than the usual 100mA, when using the left-side USB ports (the ones nearest the side-panel buttons). I really don't know how you'd go about actually using those buttons, as the manual doesn't even say how you would in XP/Vista... Turns out the Q-Charging button actually generates some keyboard input, as I did a 'sudo cat /dev/input/event1', and some junk comes out when I hit the Q-Charging button, but not for the Power USB button, so I bet you could possibly just map that button to some power management function, or whatever.

Maybe I'll get around to figuring out those 'Wow Video' and 'Wow Audio' buttons some time, as they aren't generating an input for X programs for me right now. Might be nice to have that bit added to the System76 Driver.

---

### Post by osx424242 on 2008-08-27
> **SilverDragon said:**
> I thought the S button was the suspend button, but I haven't tested that out. I'm also curious to know what the tiny lightening bolt does.

On my panv3, the USB/lightning bolt button allows you to charge USB devices (phone, mp3 player) without turning on your computer.  When I press it, the button lights up (orange) and the device starts charging (I think I've only used it once, but it's nice to know the feature is available).  It appears that it is supposed to do the same on the serp4:

> **thomasaaron said:**
> The USB button would allow you to leave a device that charges up via a USB connection in your laptop while the computer is off and plugged in.

---

