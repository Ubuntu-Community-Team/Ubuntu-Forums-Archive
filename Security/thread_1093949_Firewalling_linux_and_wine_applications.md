---
title: "Firewalling linux and wine applications"
date: 2009-03-12
forum: Security
---

### Post by cryogen on 2009-03-12
Has anyone ever attempted to do some application firewalling on linux?  I have a number of apps routinely running under wine and wish to install a couple more (mostly scientific).  The problem is, some of these apps are known to phone home.  On the windows workstations I've deployed ZoneAlarm to keep them at bay, but I'm becoming concerned about running them under wine routinely and not knowing or controlling what they're doing.  I already operate a default-deny iptables policy for in- and outbound traffic, but there are some ports I can't close (eg. ftp) that these apps use to phone home.

Please note that while I'm thinking about wine right now, this isn't specific to wine: I ultimately would like to firewall any userspace process running under linux if possible.

I've seen a couple projects that claim to be able to firewall individual apps, specifically tuxguardian and lafw (or something like that), but both of these are quite dead.  AppArmor might do the job, but I really don't want to make a profile for every single windows app running under wine if I can help it: especially since I might well miss an app that tries to connect to the network.  I've also seen something promising in bsd's systrace, and it also just got updated.  However, there was apparently some debate about the actual security of the systrace system a few years ago and I don't know the current status.

Any thoughts or comments?  Does anyone know of a way in linux to firewall applications as opposed to just ports and IPs?  

PS: I am not an expert on wine, so if this is irrelevant I would like to know.  On a whim I did attempt to install a couple windows application firewalls, but had no success.

PS2: I am pretty sure SELinux will do this, but I've never experimented much with it, and it seems kind of like using intercontinental ballistic missiles to kill mosquitoes.  Feel free to correct me if I'm wrong.

---

### Post by brian_p on 2009-03-12
> **cryogen said:**
> 

Any thoughts or comments?  Does anyone know of a way in linux to firewall applications as opposed to just ports and IPs?

Reject outgoing packets based on gid. Put wine applications in a group of your choice.

---

### Post by hyper_ch on 2009-03-12
what do you need to run in wine?

---

### Post by cryogen on 2009-03-12
> **brian_p said:**
> Reject outgoing packets based on gid. Put wine applications in a group of your choice.

Interesting idea: I've never seen that before.  I assume you're talking about the iptables --gid-owner option.  I'll give that a try.  Thanks!

I'd still like to know if there's some kind of firewall app available for fine-grained control of which app is allowed to connect.

> **hyper_ch said:**
> what do you need to run in wine?

The most immediate thing is an app called Noran System Six for analyzing [EDX]("http://en.wikipedia.org/wiki/Energy-dispersive_X-ray_spectroscopy") data.  I'm also going to deploy an app called Cary WinUV by Varian for analyzing uv-vis absorption data.

---

### Post by hyper_ch on 2009-03-12
no clue what does are. If you're not lucky with the above adise then you still have the option of a VM but with no network connection to the outside :)

---

### Post by bodhi.zazen on 2009-03-12
In general the route Linux has gone it Apparmor and SELinux.

Apparmor is default on Ubuntu , if yo uwant SELinux I suggest Fedora.

See the stickies at the top of these forums.

---

