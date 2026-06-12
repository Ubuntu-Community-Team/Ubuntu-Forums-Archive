---
title: "Serval Performance powering off duing game"
date: 2007-12-07
forum: System76 Support
---

### Post by Rasputin_III on 2007-12-07
I am currently dual booting my S.P between Ubuntu and WinXP.
I only enter the latter when playing games and I've only seen this problem on the Windows side.

Twice now (while playing Neverwinter Nights), the system has froze up for a second, then powered off.  When I bring the system back up, there is nothing unusual in any of the event logs.

Has anyone else had this problem (possibly during a long-duration high-cpu activity)?
 I don't know of any "normal" application problems that will completely power down the system as opposed to freezing and/or generating errors.  Could this be heat related?  I've never had anything like this happen before, so it's a bit of a guess.  Suggestions?

---

### Post by thomasaaron on 2007-12-10
We aren't really equipped to diagnose windows problems. My initial question would be: does it only happen with certain games/programs?

To really help you, we would need to see if we could replicate it on the Ubuntu side. There are some pretty heavy games and graphical programs you could try.

You might start with running two or tree instances of glxgears simultaneously. This will tax your nVidia card pretty well and might cause a shutdown if there is a hardware problem. If it is a hardware problem, it most likely would be a memory card on the fritz.

GoogleEarth might be another one to try.

---

### Post by Rasputin_III on 2007-12-10
I'll give it a shot, thanks.

---

### Post by Rasputin_III on 2007-12-25
Running multiple instances of glxgears did not cause the system to overheat or power off.  I did notice that the fan operated differently when in the two environments:  when glxgears was running under linux, the fan was blowing pretty much at full speed; when neverwinter was running under windows, it appeared to run at a somewhat slower speed and kick on and off intermittently.

In light of this, I was wondering if you had any bios updates that would give more fine-tuning control over fan functions (and others--the menus seem relatively sparse).  Compal's latest is what is on the system now, but I didn't know if you had anything else available.

I have also installed nwn on the linux side (to check performance, stability, etc) and while it doesn't power off, after playing from anywhere between 30 minutes to a couple of hours, it will freeze up about half of the time.
The order of events:  the game would get very choppy for a couple of seconds; then stop responding, leaving the screen as was last viewed; then the screen would blank; and finally a few distorted lines would appear at the bottom of the screen (like if the X11 modelines were completely messed up).  Up until I discovered the SysRq-R-S-E-I-U-B trick, the only thing that worked was powering off the system.

Ideas?  Nvidia driver related?  Has anyone else had (extended) success or problems with this?

---

### Post by thomasaaron on 2007-12-26
You can email me with either your order number or the name under which the computer was purchased. That way I can see exactly which SP you have and see if there are any bios updates.

---

