---
title: "Virtualize single application"
date: 2010-04-22
forum: Virtualisation
---

### Post by Hydrohs on 2010-04-22
Curious to see if there is a virtualization program out there that works like Windows 7's XP Mode that allows only a single application to be virtualized, rather than running an entire machine.

---

### Post by TheFu on 2010-04-23
VirtualBox has a "seemless mode", which appears to be just 1 app without the entire VM under it.
WINE does this too - so if you just want 1 MS-Windows program to run under Ubuntu, I always check WINE and search for any get-it-working-hints they have there.

BTW, Windows7 XP-Mode is a complete install of WinXP and is running a complete VirtualPC VM. Win7 also has compatibility modes which don't run a VM, rather they allow non-standard settings that look like Win2000, Win98, WinXP, Vista to the program via environment settings to be setup before launching a program. This may allow a program to run under Win7.

My terms may not be exactly correct as MS uses them.

---

### Post by Hydrohs on 2010-04-23
Well yeah XP mode is an entire machine, but you don't have to click through it to open programs etc. I've used Virtual Box's seamless mode and the taskbar is still stuck at the bottom of the screen.

I'm also mainly looking for this for Visual Studio, which doesn't work in WINE at all.

---

### Post by HermanAB on 2010-04-25
You can do it via Cendio Seamless RDP:
[http://www.cendio.com/seamlessrdp/](http://www.cendio.com/seamlessrdp/)

---

### Post by Hydrohs on 2010-04-26
> **HermanAB said:**
> You can do it via Cendio Seamless RDP:
[http://www.cendio.com/seamlessrdp/](http://www.cendio.com/seamlessrdp/)

From reading that it makes it sound like I have to run the program from a server, that correct?

---

### Post by HermanAB on 2010-04-27
Basically you are doing ordinary RDP and running a program.  The difference being that you are running the program via a modified Windows shell, so that it doesn't paint the whole Windows desktop.  

Just try it.

---

### Post by Hydrohs on 2010-04-27
> **HermanAB said:**
> Basically you are doing ordinary RDP and running a program.  The difference being that you are running the program via a modified Windows shell, so that it doesn't paint the whole Windows desktop.  

Just try it.

But I don't have any sort of server to RDP to O_o

---

