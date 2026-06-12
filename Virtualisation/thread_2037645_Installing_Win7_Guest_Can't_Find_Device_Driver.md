---
title: "Installing Win7 Guest Can't Find Device Driver"
date: 2012-08-05
forum: Virtualisation
---

### Post by MiniVanMan on 2012-08-05
I'm shopping around for an answer here.  I'm extremely frustrated.  

Trying to load a Win7 64bit guest on Vbox, and in the beginning of the install process I get an error "A required CD/DVD device driver is missing."

I've tried every combination of settings in Vbox, scoured the net for ideas (this is a rampant problem) and every suggestion yields nothing.  

What's even more frustrating is that it loaded with absolutely no problem on my computer in a virtual machine, but it won't load on my wife's which has the exact same hardware.  The only difference is she runs Kubuntu, and I run Mint.  She actually needs Windows because she has a damn iPhone and Garmin that both need Windows to download and sync with.  

This is a Windows issue, but I'm getting nowhere with the Windows people.  This issue also occurs when trying to load Win7 as a base O/S for many.  So, I'm hoping enough people here have virtualized Win 7 and maybe ran into this issue.  

All ideas appreciated at this point.

---

### Post by CharlesA on 2012-08-06
Never had a problem loading Win7 on a VM. Have you recreated the VM from scratch?

---

### Post by SeijiSensei on 2012-08-06
I've always had no problems installing from a Win7 ISO image.  Try creating an ISO image on your hard drive from the Win7 DVD using brasero or K3b.  Then point the VirtualBox installer at the ISO image.  Does that work for you?

---

