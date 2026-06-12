---
title: "[SOLVED] Laptop installation of Vista guest in VB"
date: 2008-12-04
forum: Virtualisation
---

### Post by dansan on 2008-12-04
Is Vista difficult to install successfully as a guest in VB?

Vista installed without trouble as a VB guest in Hardy 8.04 on my desktop PC, but I've had no success doing the same thing on my Acer Aspire laptop. The installation goes to the final step "Completing installation..." and hangs there until I kill the process.

On the other hand, Windows XP easily installed on the same laptop. The desktop has an Intel Core 2 CPU (2.4GHz) and 2 GB RAM. The laptop runs on AMD Turion 64 X2 Dual-Core Mobile Processor (1.66GHz) and also has 2 GB RAM. I don't have much in the way of tech-chops, but I would think the laptop would run a Vista guest ok.

There is a difference between my desktop and laptop setups. I did a clean install of Hardy on the desktop, but I updated from Gutsy on my laptop. Could this make any difference to installing a Vista guest on VB? Should I do a clean install on the laptop?

I haven't generally found much in these forums about Vista and VirtualBox. I did find one thing on installation, though: install XP first and update to Vista. This might be worth a try. Are there technical reasons for not going this route?

Any help is appreciated.

---

### Post by HotShotDJ on 2008-12-04
I have had no trouble with VirtualBox and Vista.  In earlier versions of VirtualBox, there was an issue with directory sharing, but that has been resolved for awhile now.

The only difficulty that I've heard of with Vista in VirtualBox is with certain OEM versions that don't use an authorization key.  If I recall correctly, this is because those versions are tied directly to the hardware.  In my case, although Vista is an OEM version, it still uses an authorization key for installation, so there was no problem.

I don't know why you'd have a problem on your laptop when there was no problem on your desktop, unless, again, it is an OEM version which may somehow be recognizing that it not licensed for that machine.  (I have no clue how it would do that, but one never knows... those Microsoft people are pretty sneaky).

---

### Post by HermanAB on 2008-12-04
If you can make a working VM on another machine, then you can just copy the VM over.

---

### Post by dansan on 2008-12-04
Thanks for the heads-up:

> **HotShotDJ said:**
> ...

The only difficulty that I've heard of with Vista in VirtualBox is with certain OEM versions that don't use an authorization key.  ...

I didn't know about this interesting twist, but I doesn't apply in this case. I'll try the tip in the Herman's post and report back.

---

### Post by dansan on 2008-12-04
Bullseye, Herman ;)

> **HermanAB said:**
> If you can make a working VM on another machine, then you can just copy the VM over.

Now, all I have to do is research how to do it, but I'm sure I'll find out here.

---

### Post by dansan on 2008-12-08
I followed Herman's tip, but I first had to decide what "copy the VM over" meant. After reading more about this in these forums, I decided it meant:

1. Copy the vdi of the working VM.
2. Paste it into the .VirtualBox/VDI directory on my laptop.
3. Detach the failed vdi from the laptop VM.
4. Attach the vdi from the from my desktop's working VM to the laptop's VM.

After doing this, I clicked Start, and Vista did. But maybe my copy-over wasn't quite right because -

Although Vista seems to run normally, there is nevertheless a potential "gotcha" on shutdown. If I shut down from a small window, shutdown is slow, but finishes. If I shut down from a full-screen window, there's a good chance shutdown will hang. If it does, not even "Force Quit" will get rid of the VM. I have to Ctrl+Alt+Backspace to log out of Ubuntu and choose "Action>Shutdown" or "Restart" for Ubuntu. Naturally, this is not sound.

Is there a different way to copy over a VM?

---

