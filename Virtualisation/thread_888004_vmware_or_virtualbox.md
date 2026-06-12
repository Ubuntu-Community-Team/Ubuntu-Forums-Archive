---
title: "vmware or virtualbox"
date: 2008-08-12
forum: Virtualisation
---

### Post by SpikeyMike on 2008-08-12
hi, I recently installed vmware on hardy and have installed XP on it, it works but it seems quite slow, windows is quite jumpy and doesn't always respond. I am running an amd athlon 64 x2 dual 4200+ with 1gb ram so I it should work ok I think. Can anyone tell me if it might be better to use virtualbox

Spikey

---

### Post by bodhi.zazen on 2008-08-12
to be honest, I do not see much difference in terms of overall performance between VirtualBox and VMWare.

How much RAM did you give to Windows ?

---

### Post by fjgaude on 2008-08-13
> **SpikeyMike said:**
> hi, I recently installed vmware on hardy and have installed XP on it, it works but it seems quite slow, windows is quite jumpy and doesn't always respond. I am running an amd athlon 64 x2 dual 4200+ with 1gb ram so I it should work ok I think. Can anyone tell me if it might be better to use virtualbox

Spikey

Have you installed the Tools? That makes all the difference in the world regarding mouse and video quickness.

---

### Post by Blind Tiger on 2008-08-13
Agreed -- the key to both VMware and Vbox is installing the additional tool to allow for seamless integration.

I use both VMware 1.0.6 and Virtualbox 1.6 eaching running XP Pro as a guest OS.  Regarding performance, there are marginal differences in my opinion.  I believe it ultimately amounts to which interface you feel is more intuitive as their performance and feature sets are similiar in most ways.  Also, you may want to consider the availibility of package repository -- I believe Vbox is a bit more user friendly in this area.

---

### Post by Fzang on 2008-08-13
Always dedicate most of the RAM to the host OS, because that's the OS that pulls itself AND the VM.

If you dedicate too much to the VM the host will be slow because it doesn't have enough, and when host becomes slow the VM becomes slow..

---

### Post by SpikeyMike on 2008-08-15
> **bodhi.zazen said:**
> to be honest, I do not see much difference in terms of overall performance between VirtualBox and VMWare.

How much RAM did you give to Windows ?

Hi, thanks for your replies, I gave xp 384mb ram, I have now also installed server 2003 with the same amount of ram and that seems to work much better. I did install vmware tools on xp and also on server 2003. The only thing about vmware is that it isn't in the repositories for hardy, I installed it from a tar.gz file. does this really make any difference? how would I go about uninstalling it if I wanted to use virtualbox?

Spikey

---

### Post by EmmEff on 2008-08-15
You do not have to uninstall VMware if you don't want to...  simply disable it so it doesn't start at boot-time and continue on with your VirtualBox installation.

FWIW, I do not see any difference in performance between VMware Server and VirtualBox either...  I stick with VMware since the networking configuration is a bit smoother out of the box.

---

