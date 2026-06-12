---
title: "VirtualBox Guest Additions causes crashing (Kubuntu guest, XP host)"
date: 2009-08-11
forum: Virtualisation
---

### Post by smillerc on 2009-08-11
I have an annoying problem with virtualbox.

The install of Kubuntu 9.04 works just fine on my xp host system. I install guest additions and then when I reboot, the resolution goes haywire.

In the top of my virtualbox window, Kubuntu is crammed into the top 1 or 2 inches of the window, while the rest of the window is all black.

I can get around this by going to tty1 (Ctrl-Alt-F1), logging in, and then going back to the login screen by hitting Alt-F7. Once I do that, the screen is fine.

Ive also tried this with an OpenSUSE 11.1 on virtualbox and I get the same problems...

Any ideas?

I'm running virtualbox 3 and kde 4.2 by the way...

---

### Post by jocampo on 2009-08-11
I tried to install VirtualBox 3 on my headless Ubuntu Server and was getting some weird errors and problems; so, I uninstall and re-install one version lower and is working like a charm. My advice is using one version lower, like 2.4 I think? I believe is more stable and less prone to errors.

By the way, I think that if you keep your vdi files, you can import your virtual hard disks later ... a step that you can skip and save time ...

---

### Post by smillerc on 2009-08-17
Thanks, this worked out great... I'm running on VirtualBox 2.2 now and it works w/o flaws...

---

### Post by jocampo on 2009-08-18
> **smillerc said:**
> Thanks, this worked out great... I'm running on VirtualBox 2.2 now and it works w/o flaws...

;-) great, enjoy!

---

