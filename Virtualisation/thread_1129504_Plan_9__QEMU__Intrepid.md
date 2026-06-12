---
title: "Plan 9 / QEMU / Intrepid"
date: 2009-04-18
forum: Virtualisation
---

### Post by jimhabegger on 2009-04-18
Here's what I had to do to use Plan 9 from Bell Labs in QEMU in Intrepid:

1. Install QEMU.
2. Add a VGA kernel option in the Ubuntu boot menu.
3. Include a keyboard language option in the qemu command.
4. Install Plan 9.

1. Install QEMU.
I couldn't find it in Synaptic or in the Updater, but I did find it in Aptitude, so I installed it from there.

Then I followed the instructions at [http://www.9grid.fr/wiki/plan9/Installing_Plan_9_on_Qemu/index.html]("http://www.9grid.fr/wiki/plan9/Installing_Plan_9_on_Qemu/index.html").

2. Add a VGA kernel option in the Ubuntu boot menu.
When I did
```
qemu -hda Plan9.qcow.img -cdrom plan9.iso -boot d
```
it failed with this message:
>      =======================|  DirectFB 1.0.1  |=======================
          (c) 2001-2007  The DirectFB Organization (directfb.org)
          (c) 2000-2004  Convergence (integrated media) GmbH
        ------------------------------------------------------------

(*) DirectFB/Core: Single Application Core. (2008-09-12 19:59) 
(!) Direct/Util: opening '/dev/fb0' and '/dev/fb/0' failed
    --> No such file or directory
(!) DirectFB/FBDev: Error opening framebuffer device!
(!) DirectFB/FBDev: Use 'fbdev' option or set FRAMEBUFFER environment variable.
(!) DirectFB/Core: Could not initialize 'system' core!
    --> Initialization error!
Could not initialize SDL - exiting

After some research and experimenting, I resolved that by adding VGA=773 to the kernel options in the Ubuntu boot menu. I found the VGA codes at [https://wiki.ubuntu.com/FrameBuffer]("https://wiki.ubuntu.com/FrameBuffer").

3. Include a keyboard language option in the qemu command.
Then, after I rebooted, when I did
```
qemu -hda Plan9.qcow.img -cdrom plan9.iso -boot d
```
it started, but it scrambled my keyboard, so I couldn't respond to the prompts. After some research and experimenting, I resolved that by adding "-k en-us" to the qemu command, like this:
```
qemu Plan9.qcow.img -k en-us
```

4. Install Plan 9.
I followed the instructions at [http://plan9.bell-labs.com/wiki/plan9/installation_instructions/]("http://plan9.bell-labs.com/wiki/plan9/installation_instructions/").

---

### Post by jimhabegger on 2009-04-18
I'm still looking for better solutions to some minor problems:
1. Display size.
2. How to exit QEMU.
3. It hangs up sometimes.
4. Acceleration layer.

1. Display size.
When I finally got it working, my Plan 9 display did not fill my whole display. I re-installed it, giving a new display size at the prompt. I still need to learn how to change the display size without re-installing.

2. How to exit from QEMU.
I couldn't find anything in the man pages about how to exit from QEMU, that worked. For now, I'm just adding -no-reboot to the qemu command. Then when I do "fshalt -r" in Plan 9, it exits from QEMU.

3. It hangs up sometimes.
If I don't wait a few seconds before I respond to each prompt when I start Plan 9, sometimes it hangs up and stops responding to the keyboard. It doesn't even respond to Alt-Ctrl-Del. I have to shut it down with the power button.

4. Acceleration layer.
I see this message below the qemu command:
> Could not open '/dev/kqemu' - QEMU acceleration layer not activated: No such file or directory
I been doing some research on that, but I'm still confused about whether kqemu is included in Intrepid, and if so how to activate it.

---

### Post by bodhi.zazen on 2009-04-19
I do not have a solution, but, quem is going to be slow, slower then almost any other option.

Because of speed you *may* wish to consider virtualbox or VMWare (virtualbox is probably easier, vmware *may or may mot* have better support for plan 9).

qemu is slow even with kqemu :(

---

### Post by jimhabegger on 2009-04-20
> **bodhi.zazen said:**
> Because of speed you *may* wish to consider virtualbox or VMWare (virtualbox is probably easier, vmware *may or may mot* have better support for plan 9).

Exactly. That's the whole question. What kind of support do they have for Plan 9, and more important, how many hundreds of hours would I have to spend getting it to work in virtualbox or VMWare? I had enough trouble getting it to work with QEMU.

---

