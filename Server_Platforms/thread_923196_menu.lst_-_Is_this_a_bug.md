---
title: "menu.lst - Is this a bug?"
date: 2008-09-18
forum: Server Platforms
---

### Post by chrislynch8 on 2008-09-18
Hi,

A few weeks back I posted a thread about my kernel.log log messages getting printed to the screen. I found the cause of this at last, and I don't understand how it can be. Maybe someone here knows - it may be a bug in Ubuntu!!!

I use Ubuntu Server 6.06 LTS 64bit AMD and its fully update-to-date and has the most recent kernel 2.6.15-52-amd64-server.

I an LCD display with the server but the screen dosn't fit correctly - it either too high or too low and I can't get it in between.

I edited menu.lst and instead of the line

```
defeoptions=quite
```

I put in ```
defoptions=vga=ask
```

I updated grub and rebooted the server. On the reboot I get asked to press enter to choose available display options. 

I can just hit space and continue the boot and when it fully boots and I log in the console fully fit correctly onto the LCD display.

This also occured on an old CRT monitor so its not just my LCDs (I've now tested it on three different ones)

Is this a bug in Ubuntu or id there something I can do to make the console fit the LCD screen without the kernel.log getting printed to the screen.

Thanks
Chris

---

### Post by Dedoimedo on 2008-09-18
Hello,
You don't want to see the log (i.e. turn off the verbosity) while booting, is that it? Or do you have a problem with screen resolution?
Dedoimedo

---

### Post by chrislynch8 on 2008-09-18
The problem is the screen resolution - it will ony fit correctly when I use defoptions=vga=ask but with this option while I'm logged into the server any message that is logged into the kernel.log will also be printed to the screen.

When I use defoption=quiet the kernel.log messages are not printed to the screen then but the resolution is wrong and I'm unable to see the full screen.

---

