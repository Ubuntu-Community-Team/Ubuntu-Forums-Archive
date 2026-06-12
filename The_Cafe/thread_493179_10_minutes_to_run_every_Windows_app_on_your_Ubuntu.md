---
title: "10 minutes to run every Windows app on your Ubuntu desktop"
date: 2007-07-05
forum: The Cafe
---

### Post by Dragonbite on 2007-07-05
This is a very interesting article, and one that shows a concept of using virtual machines.

[[COLOR="Blue"]http://element14.wordpress.com/2007/07/05/10-minutes-to-run-every-windows-app-on-your-ubuntu-desktop/[/COLOR]]("http://element14.wordpress.com/2007/07/05/10-minutes-to-run-every-windows-app-on-your-ubuntu-desktop/")

Basically it seems to use VMServer to run Windows (XP Pro) without the full desktop, and allow individual windows to run applications installed in the Windows VM.

So instead of running Photoshop or iTunes or Dreamweaver in a whole other desktop, this would run the application in a window-only! Kool, eh?\\:D/

---

### Post by vexorian on 2007-07-05
... 3d acceleration

---

### Post by suterb42 on 2007-07-05
Is there a way to do this when your Windows partition is on the same drive as your Linux partition?

---

### Post by Dragonbite on 2007-07-05
> **suterb42 said:**
> Is there a way to do this when your Windows partition is on the same drive as your Linux partition?I don't think so. I think the whole premis is you're running a vritual machine but not showing it until you open an application, then the window of the application is passed through to the Linux desktop and made visible.

---

### Post by super breadfish on 2007-07-05
I thought this was fairly common....[It's even in the official help](https://help.ubuntu.com/community/SeamlessVirtualization). I was going to give it a go a while back, but I couldn't find my Windows disc to install ](*,)

---

### Post by vexorian on 2007-07-05
> **suterb42 said:**
> Is there a way to do this when your Windows partition is on the same drive as your Linux partition?
Don't ever use a physical partition in a virtual machine...

---

### Post by reclusivemonkey on 2007-07-05
I tried this and the VM Ware Server works great, but when I ran the

```
rdesktop -A -s 'c:\seamlessrdp\seamlessrdpshell.exe c:\windows\explorer.exe' 192.168.129.129 -u user -p password
```

It doesn't seem to work. Nothing happens.

---

### Post by phrostbyte on 2007-07-05
> **vexorian said:**
> ... 3d acceleration

It's only a matter of time. VMWare Fusion already has pretty good 3D acceleration. But yeah I agree... it shouldn't be "every", but saying "most" is fair.

---

### Post by thisllub on 2007-07-05
> **reclusivemonkey said:**
> I tried this and the VM Ware Server works great, but when I ran the

```
rdesktop -A -s 'c:\seamlessrdp\seamlessrdpshell.exe c:\windows\explorer.exe' 192.168.129.129 -u user -p password
```

It doesn't seem to work. Nothing happens.

Assuming you did put real a username and password, did you install the seamlessrdp first?

---

### Post by reclusivemonkey on 2007-07-05
> **thisllub said:**
> Assuming you did put real a username and password, did you install the seamlessrdp first?

D'OH! Thanks. It must of been late :-S

---

### Post by Medieval_Creations on 2007-07-05
Is there any performance issues running it that way, on either host system and guest/app?  I currently use VBox and only fire it up when I need it.   I can't see running the VMServer all the time if I don't need it all the time.

---

### Post by scxtt on 2007-07-05
there are no performance issues (if your box can handle it) ... i have a box that runs vmware server and 3 VMs all the time (sometimes 4) ... load average is ~ .10 - .30 when i'm not really using them ...

---

### Post by Warpnow on 2007-07-05
I would imagine running Ubuntu AND windows xp would be pretty cpu intensive...

---

### Post by scxtt on 2007-07-05
nah ... i mean it depends on what you're doing ... like i said above, i run 2 linux VMs and 2 windows VMs pretty constantly ... runs great on my AMD 3600+ (dual-core 2GHz)+ w/ 4Gb of RAM ...

---

### Post by Warpnow on 2007-07-05
I've got a pentium 4 3ghz, not dual core...has what's called "hyperthreading" but I don't know how effective that is with 2gb of ram. Think I'll have trouble running ubuntu + xp?

---

### Post by scxtt on 2007-07-05
no problems w/ that, my other PC is a P4 (no HT) w/ 2GB of RAM, could run Ubuntu + 3 VMs reasonably well ...

---

### Post by Medieval_Creations on 2007-07-06
Good to know... My rig isn't quite that beefy, AMD 64 3000+ 2.2Ghz, 1Gb of Ram.  Plenty to run 1 VM I'm sure...
I plan on checking it out this weekend and see how it works.

---

### Post by vexorian on 2007-07-06
> **Warpnow said:**
> I've got a pentium 4 3ghz, not dual core...has what's called "hyperthreading" but I don't know how effective that is with 2gb of ram. Think I'll have trouble running ubuntu + xp?
I didn't find much issues running ubuntu and windows XP and I just have 768MB of RAM, thus  I would dare to say you will be fine.

---

