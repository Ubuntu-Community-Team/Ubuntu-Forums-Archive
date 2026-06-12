---
title: "VMware &amp; Ubuntu question"
date: 2006-04-19
forum: The Cafe
---

### Post by Moif_Murphy on 2006-04-19
I have VMWare for Linux and Windows at home and a copy of Windows 2000 & XP. I'm thinking of installing Windows 2000 / XP as a VM machine under Ubuntu and ditching my XP install.

Now the intelligent way of doing this is booting into Ubuntu, installing VMWare and installing XP.

But, I'm at work and doing this remotely and can only remote into Windows XP via LogMeIn. So I'm going to install a Windows 2000 VM Machine ready for when I get home.

My question is can I still use that VM Image under VMWare in Linux after I've created it in Windows?

---

### Post by alamba on 2006-04-19
Absolutely. The "image" file are .vmdk files which would work under any environment of vmware (i.e. win or linux). I personally have Win 98, Win 2K and WinXP images working in ubuntu which were originally created under windoze.

A

---

### Post by Moif_Murphy on 2006-04-19
Fantastic.

That brings me to my next question. If I only have 1 copy of XP do I need to re-activate that copy with MS during the VM creation?

---

### Post by somuchfortheafter on 2006-04-19
yes.. but if you call ms they are very understanding as long as you removed the original install.

---

### Post by paul cooke on 2006-04-19
[QUOTE=Moif_Murphy]I have VMWare for Linux and Windows at home and a copy of Windows 2000 & XP. I'm thinking of installing Windows 2000 / XP as a VM machine under Ubuntu and ditching my XP install.

Now the intelligent way of doing this is booting into Ubuntu, installing VMWare and installing XP.

But, I'm at work and doing this remotely and can only remote into Windows XP via LogMeIn. So I'm going to install a Windows 2000 VM Machine ready for when I get home.

My question is can I still use that VM Image under VMWare in Linux after I've created it in Windows?[/QUOTE]

Yes, but you'll have to change some of the settings to point to sensible Linux drive points ect. (the DVD/CD drive D especially has to be set to point to where your DVD/CD drive is /dev/hdc in my case)

---

