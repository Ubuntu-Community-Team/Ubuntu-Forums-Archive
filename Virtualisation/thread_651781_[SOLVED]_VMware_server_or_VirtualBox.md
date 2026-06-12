---
title: "[SOLVED] VMware server or VirtualBox?"
date: 2007-12-27
forum: Virtualisation
---

### Post by A-dogg on 2007-12-27
Sounds like people tend to prefer VirtualBox, but that could be me only reading the noobie posts... :)

If you have a sec, could you tell me which you think is better for a relative noob who doesn't need 3d gaming or anything? Mostly I want to install palm desktop to use programs with conduits that I can't use with J-Pilot, and to use some non-Linux programs like Final Draft... Internet access (like I have in Ubuntu Gutsy 7.10) would be nice too.

I get the feeling that they're two roads leading to the same city, but...

Thanks in advance for any advice!

---

### Post by pay on 2007-12-28
Well neither support 3d afaik (well maybe the vmware workstation). Both will do what you want really. Vmware is proprietary and virtualbox is opensource (mostly) so maybe that will help you. Theres also qemu...

---

### Post by chris4585 on 2007-12-28
i like virtualbox it does what i want it to do... i've tried vmware but i dont think it had the same wow as virtualbox did for me i guess its opinion

---

### Post by Blinkiz on 2008-01-05
If you are going to have Windows XP within a virtual machine, Virtualbox will run it faster than VMWare Server.

Keep in mind not to enable hardware virtualization (VT-x) within Virtualbox. Virtualbox's own way to handle full virtualization is better.

---

### Post by A-dogg on 2008-01-05
cool -- thanks. vbox is what I ended up going with. with VT-x UNchecked.

---

### Post by dpj23 on 2008-01-06
VMware hands down...

---

### Post by fjgaude on 2008-01-06
I've tried both sids-by-side for weeks and as it is said, "VMware Server hands down".

---

### Post by unityofsaints on 2008-01-06
I had less problems with getting sound and shared folders working on virtualbox, for the basic win xp VM I would say it's the best option.

---

### Post by Mike'sHardLinux on 2008-01-06
When I tried VirtualBox a few months ago, networking was tricky, especially if your computer used wireless (which mine did.) I couldn't get it to work and stuck with VMware. Has this gotten better or easier?

---

### Post by jasonrandolph on 2008-01-10
The only problem I had was that I changed some of the defaults in networking when setting up XP.  After I reinstalled XP and left the defaults as-is, I had no wireless problems.  The big mistake I made was that I didn't read far enough in the VB user manual.

---

### Post by dotancohen on 2008-03-15
> **Blinkiz said:**
> Keep in mind not to enable hardware virtualization (VT-x) within Virtualbox. Virtualbox's own way to handle full virtualization is better.

Where is this option set? I cannot find it. Thanks.

---

### Post by Kiri on 2008-03-15
> **dotancohen said:**
> Where is this option set? I cannot find it. Thanks.

Preferences>General

I think its off by default though

---

### Post by Kiri on 2008-03-15
> **fjgaude said:**
> I've tried both sids-by-side for weeks and as it is said, "VMware Server hand down".

For those saying this, can you tell us why "VMware hands down"?
Is the performance better? easier to use?

---

### Post by fjgaude on 2008-03-15
> **Kiri said:**
> For those saying this, can you tell us why "VMware hands down"?
Is the performance better? easier to use?

Well, for a couple of months I ran both on my main box and laptop.

One thing that I required was copy, cut, and paste between Ubuntu and Windows. I got it reliably in vmware, not in vbox.

Another was ease of use and updating paths... I liked vmware the best.

Speed, quickness, hard to say, but both seemed to satisfy my graphic design needs using what you see in my signature below.

The "hands down" has to do with cut-copy-paste for me. For others, let them speak.

---

