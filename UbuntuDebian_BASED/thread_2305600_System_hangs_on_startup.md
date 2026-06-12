---
title: "System hangs on startup"
date: 2015-12-07
forum: Ubuntu/Debian BASED
---

### Post by jdsmith2 on 2015-12-07
Greetings everyone.  I set up a XBMCBuntu box and the system hangs are startup.  Sometimes (1 time out of 10) the system doesn't hang and takes me to the login screen without any problems... unfortunately I am a newbie.  

[COLOR=#000000][FONT=Verdana]Here's the output from my Xorg.0.log file:[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Here's the output: [/FONT][/COLOR][http://paste.ubuntu.com/13686942/](http://paste.ubuntu.com/13686942/)

[COLOR=#000000][FONT=Verdana]Here's the output from my [/FONT][/COLOR][COLOR=#000000][FONT=Verdana]/var/log/upstart/lightdm[/FONT][/COLOR][COLOR=#000000][FONT=Verdana]t file:[/FONT][/COLOR]
[http://paste.ubuntu.com/13712809/](http://paste.ubuntu.com/13712809/)

Does anyone have suggestions on what I should do?

Thank you!

JD

---

### Post by howefield on 2015-12-07
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

### Post by matt_symes on 2015-12-07
Hi

Welcome to the forums :)

Does it boot to a desktop if you unplug the projector and attach a standard monitor ?

Kind regards

---

### Post by jdsmith2 on 2015-12-07
Actually I just tried it and it does!  If I have 'both' attached, it will long into the monitor one and the projector screen just 'hangs.'  That's weird, it seems like it will always boot to the monitor... and 'sometimes' boot to the projector.  How do I get it to always boot on the projector?  I don't need two displays.

---

### Post by matt_symes on 2015-12-07
Hi

> Actually I just tried it and it does! 

I thought it might work.

This is the problem i believe.

```

[    41.636] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    41.636] (**) NVIDIA(0):     device Delta PROJECTOR (DFP-1) (Using EDID frequencies has
[    41.636] (**) NVIDIA(0):     been enabled on all display devices.)
[    41.638] (WW) NVIDIA(GPU-0): The EDID for Delta PROJECTOR (DFP-1) contradicts itself: mode
[    41.638] (WW) NVIDIA(GPU-0):     "1920x1080" is specified in the EDID; however, the EDID's
[    41.638] (WW) NVIDIA(GPU-0):     valid HorizSync range (30.000-100.000 kHz) would exclude
[    41.638] (WW) NVIDIA(GPU-0):     this mode's HorizSync (28.1 kHz); ignoring HorizSync check
[    41.638] (WW) NVIDIA(GPU-0):     for mode "1920x1080".
[    41.639] (WW) NVIDIA(GPU-0): The EDID for Delta PROJECTOR (DFP-1) contradicts itself: mode
[    41.639] (WW) NVIDIA(GPU-0):     "720x576" is specified in the EDID; however, the EDID's
[    41.639] (WW) NVIDIA(GPU-0):     valid HorizSync range (30.000-100.000 kHz) would exclude
[    41.639] (WW) NVIDIA(GPU-0):     this mode's HorizSync (15.6 kHz); ignoring HorizSync check
[    41.639] (WW) NVIDIA(GPU-0):     for mode "720x576".
[    41.640] (WW) NVIDIA(GPU-0): The EDID for Delta PROJECTOR (DFP-1) contradicts itself: mode
[    41.640] (WW) NVIDIA(GPU-0):     "720x480" is specified in the EDID; however, the EDID's
[    41.640] (WW) NVIDIA(GPU-0):     valid HorizSync range (30.000-100.000 kHz) would exclude
[    41.640] (WW) NVIDIA(GPU-0):     this mode's HorizSync (15.7 kHz); ignoring HorizSync check
[    41.640] (WW) NVIDIA(GPU-0):     for mode "720x480".
[    41.640] (WW) NVIDIA(GPU-0): The EDID for Delta PROJECTOR (DFP-1) contradicts itself: mode
[    41.640] (WW) NVIDIA(GPU-0):     "720x480" is specified in the EDID; however, the EDID's
[    41.640] (WW) NVIDIA(GPU-0):     valid HorizSync range (30.000-100.000 kHz) would exclude
[    41.640] (WW) NVIDIA(GPU-0):     this mode's HorizSync (15.7 kHz); ignoring HorizSync check
[    41.640] (WW) NVIDIA(GPU-0):     for mode "720x480".
[    41.640] (WW) NVIDIA(GPU-0): The EDID for Delta PROJECTOR (DFP-1) contradicts itself: mode
[    41.640] (WW) NVIDIA(GPU-0):     "720x576" is specified in the EDID; however, the EDID's
[    41.640] (WW) NVIDIA(GPU-0):     valid HorizSync range (30.000-100.000 kHz) would exclude
[    41.640] (WW) NVIDIA(GPU-0):     this mode's HorizSync (15.6 kHz); ignoring HorizSync check
[    41.640] (WW) NVIDIA(GPU-0):     for mode "720x576".
[    41.642] (WW) NVIDIA(GPU-0): The EDID for Delta PROJECTOR (DFP-1) contradicts itself: mode
[    41.642] (WW) NVIDIA(GPU-0):     "1920x1080" is specified in the EDID; however, the EDID's
[    41.642] (WW) NVIDIA(GPU-0):     valid HorizSync range (30.000-100.000 kHz) would exclude
[    41.642] (WW) NVIDIA(GPU-0):     this mode's HorizSync (28.1 kHz); ignoring HorizSync check
[    41.642] (WW) NVIDIA(GPU-0):     for mode "1920x1080".
```

The EDID information being returned by the projector is invalid.

It's saying that the best resolution it supports is 1920x1080 at a horizontal sync rate of 28.1 kHz but then saying its horizontal sync rate values range from 30 - 100 kHz. 

28.1 obviously falls outside the range of 30-100 and nothing is being displayed because of it.

I'm not 100% sure this is the problem but I'd place a wager it is.

What make and model is the projector ?

The rhetorical question is how to fix it ?

I'll so some research for you.

Kind regards

---

### Post by matt_symes on 2015-12-07
Hi

Let's try something. 

Connect both the monitor and project to the computer. 

On the monitor screen, open a terminal and copy and paste these commands into it.

```
xrandr --newmode "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
```                        

```
xrandr --addmode DFP-1 1920x1080_60.00
```                    

```
xrandr --output DFP-1 --mode 1920x1080_60.00
```

Post back any errors.

Do you get output from the projector ? 

It doesn't matter what the output is; just output and not a blank screen. 

If you do, it will not persist after a reboot so is a test only.

Kind regards

---

