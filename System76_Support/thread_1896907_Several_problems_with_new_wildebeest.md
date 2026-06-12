---
title: "Several problems with new wildebeest"
date: 2011-12-18
forum: System76 Support
---

### Post by AMusingFool on 2011-12-18
I just got a new Wildebeest, and the speed of it is certainly very nice.  But (and I got the GeForce GT430 option on it) it has problems with multiple monitors, and some limitations.  (I am running 11.10, and have updated everything since receiving it.  And I am using the nvidia drivers.)

Plugging in two monitors, it is very finicky about which one is the main desktop monitor.  (DVI takes precendence over HDMI, which takes precedence over VGA.  This can be worked around by running nvidia-settings a couple of times (disable one monitor, set other one, restart X, re-enable other monitor positioned relative to first monitor, restart X), but this is not really a usable configuration.)

Anyway, knowing the precedence, I was able to set it up with the correct monitor as desktop.  Ok.

But, once I have the settings in nvidia-settings, and saved to xorg.conf, if I then go to 'display settings', only one monitor shows up (whichever one has the main desktop).  'Detect displays' doesn't do anything (plus, dunno if this gives any added info, but the Display settings shows UNKNOWN for monitor type, regardless of which monitor it is seeing, whereas nvidia-settings will show something akin to 'DELL 2009W').

More importantly, while occasionally I'll see an Ubuntu background on the secondary monitor during boot-up or shut-down, the rest of the time it is a uniform white.  While the mouse cursor will move onto the secondary screen as appropriate, I can't move windows onto that display, nor run them directly via the "-display" option.

Perhaps things would work ok if I set to TwinView in nvidia-settings, but that would require me buying a new, higher resolution monitor (the second monitor is my home theater projector; lowering the resolution on that defeats the purpose of having the computer).  In any event, I haven't tried that yet, but might do so tomorrow (just out of curiosity).

So, any suggestions on what I should try to be able to display onto the second monitor?

Moving on, there're also some sound issues that I've largely worked out, but have some questions about.

First of all, getting sound going out the HDMI was significant more complicated than suggested on the sound page.  Part of that might have been using the GT430, instead of the motherboard connector.

Regardless, I wasn't able to output sound until running the nvidia-settings program, and re-saving the xorg.conf file.  Before that, on the output tab of the Sound Settings, clicking on that controller only offered an output of HDMI.  That didn't work.  After running nvidia-settings, it the option of HDMI4.  Once I went to the hardware tab, and selected 'Surround Sound 5.1 nr 4' (or something very close to that; the 'nr 4' is the important part; the other three didn't work), then it was ok.

Thinking about it, I haven't confirmed that it will keep that working through a reboot cycle.  If not, well, can't exactly run that every time I boot up.  I'll certainly test that tomorrow.

In any event, my question here relates to 7.1 sound.  The system was advertised as supporting that, but doesn't give me that option (either through the GT430 or the motherboard controller; both only offer options up to 5.1).  Since I don't have a lot of 7.1 source material, it isn't a big deal, but it would be nice.  Is this a linux limitation?  I did find a hint, via 'aplay -L' that the on-board controller should support 7.1, but there's certainly no option to select that.

Also, is there any way to get (discrete) surround out via the S/PDIF output?  I could only get stereo, and I'm not about to matrix the other channels.  (Also not a big deal, but I'm curious if I missed something.)

Finally, one last problem that is certainly a hardware one.  I opened up the box to put my Intel gigabit controller in, expecting to see two empty PCIe x1 slots and one 32-bit PCI one.  My gigabit controller took the only empty slot.  Where are the other two?  I didn't have any immediate plans for filling those slots, but now I don't have the option.

Thanks for any help,

Dave

---

### Post by AMusingFool on 2011-12-19
Looks like the multiple monitors issue is mostly solved.  The TwinView feature in nvidia-settings was not for display mirroring, as it sounded, but did pretty much what I wanted.  The only weirdness is an error message that comes up on startup, and that fullscreen apps think the screen is 3520x1080 (1600x900 and 1920x1080, side-by-side).  But it seems that most apps still work ok with that.  Plex's client, running via wine, isn't ok, but since I can't get any sound out of that (yet, at least; there might be one or two more things to try, now that I think about it), that isn't too big a deal.

The sound thing does seem to survive a reboot, so that looks ok.

So, it seems that things are about there.

-Dave

---

### Post by isantop on 2011-12-19
Sorry about the confusion. The Nvidia Proprietary driver is not compatible with the built-in displays tool, so you need to use the Nvidia setup program. 

TwinView (confusingly) does not mirror the displays, rather it puts both displays on the same X screen (literally, it stretches the display across both monitors). To mirror them, you need to select TwinView and then drag the monitors on top of one another.

---

