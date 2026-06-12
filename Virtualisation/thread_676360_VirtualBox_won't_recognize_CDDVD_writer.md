---
title: "VirtualBox won't recognize CD/DVD writer"
date: 2008-01-23
forum: Virtualisation
---

### Post by A-dogg on 2008-01-23
VirtualBox recognzies my CD/DVD writer as a CD/DVD-ROM device, but it doesn't see it's writing capabilities. Is there a way to fix that? I'm using the USB-enabled version in Gutsy.

Thanks!

---

### Post by sofamensch on 2008-02-18
Yesss there is a way!

When VMWare can do, why shouldn't VirtualBox. When not running your Virtual OS, open the Settings, go to CD/DVD and when you already have your CD Drive set up to work with VirtualBox, you only need to enable "Passthrough" option :)

---

### Post by stevesdigicams on 2008-07-20
I have the same prob with hardy and I have the "passthrough" option enabled and it still refuses to write to a DVD but reads from them OK.  I have checked the other refs to the DVD-R drive and they are there and it has no prob writing to CD or DVD in Linux but not when in VirtualBox WinXP mode.

---

### Post by QuicksilverPrince on 2008-09-17
Can you write in any other operating system? Maybe your drive is dieing on you.

---

### Post by devauda on 2011-05-01
Thanks Sofamensch, works fine for me 

(Windows7 SP1 64bits on Ubuntu Natty 11.04)

---

