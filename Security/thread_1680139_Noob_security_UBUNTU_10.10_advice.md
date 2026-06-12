---
title: "Noob security UBUNTU 10.10 advice"
date: 2011-02-02
forum: Security
---

### Post by Jim Hornet on 2011-02-02
Hi there I am new to the world of Linux and enjoying it.

I have a dual boot system with XP & Ubuntu 10.10.

I still have my Windows paranoia when it comes to surfing the net and security.

I need advice: so far I have:

OS: Activated my Firewall and added Firestarter for logging

Firefox: added NoScript to block flash and java attacks, Web of Trust for phising and Adblock Plus to stop popups and malware.

I have read the Security Sticky but don't yet fully comprehend SSH, HIDS , NIDS Apache, Apparmor etc etc or is that too much for personal PC and aimed at server configs??

My main use of the net is for Gaming/Sports forums, news, facebook, the occasional torrent download etc.

Is there anything else I can add - eg Proxy server for anonymity etc

I am actually enjoying the learning curve more than the premise of being secure - its all very interesting and enjoying much - should I worry about SSH 

I am concerned about open ports for when downloading torrents etc -is my firewall enough to deter most intrusions.


Thanks

---

### Post by mikewhatever on 2011-02-02
I'd say, get rid of Firestarter (it's been deprecated for quite some years) and the firewall, cause there is nothing to firewall by default - no open ports. Keep the system updated, and don't install stuff from outside the repositories.

---

### Post by The Cog on 2011-02-03
> **mikewhatever said:**
> I'd say, get rid of Firestarter (it's been deprecated for quite some years) and the firewall, cause there is nothing to firewall by default - no open ports. Keep the system updated, and don't install stuff from outside the repositories.
Exactly. Use synaptic and mark it for complete removal (this also removes the config files). 

I know it's not the answer that windows users expect, but really, Ubuntu doesn't have all those open ports that windows does, so a default install has no need of a firewall. And looking at firestarter logs will just keep you worried all day long - jumping at shadows.

It is worth reading up on SSH.

Don't enable remote desktop access in gnome - that's a very good way to get unwanted visitors. Similarly, don't install the SSH server unless everyone has strong passwords.

Be wary about javascript on web sites. Consider appArmour for firefox.

---

### Post by killfall on 2011-02-03
If you are dual booting windows with ubuntu you may want to look into ClamAV to keep your windows partition clean. It won't affect your ubuntu install much but it can sort out some problems that are easier fixed when windows isn't loaded. Especially if system files are infected.

But then again you seem very security conscious and so your windows if probably very fortified.

---

### Post by Jim Hornet on 2011-02-05
> Be wary about javascript on web sites. Consider appArmour for firefox.Thanks Cog, atm I am using NoScript for Firefox - is appArmour already built into Ubuntu 10.10 or do I have to download it from Ubuntu software centre or Firefox Addons - is it easy to run? 


> If you are dual booting windows with ubuntu you may want to look into  ClamAV to keep your windows partition clean. It won't affect your ubuntu  install much but it can sort out some problems that are easier fixed  when windows isn't loaded. Especially if system files are infected.

But then again you seem very security conscious and so your windows if probably very fortified.     Thanks Killfall, yes I am dual booting so I will give ClamAV a go, thanks for tip - for my windows I use AVG and Malwarebytes. Edit is ClamAV same as KlamAV?

> I'd say, get rid of Firestarter (it's been deprecated for quite some  years) and the firewall, cause there is nothing to firewall by default -  no open ports. Keep the system updated, and don't install stuff from  outside the repositories.     Thanks Mikewhatever I have taken your advice Thanks.

Thanks for replies - I will look into SSH but I have to get my head around it first anymore tips or experiences most welcome.


Also is there way to make getting into my other partition drives password protected in UBUNTU10.10. I have seen a Printscreen of someones UBUNTU  desktop and they had little Paddlock icons on their desktop shortcuts (which included HDD and software programs)?

---

### Post by cariboo on 2011-02-05
> Also is there way to make getting into my other partition drives password protected in UBUNTU10.10. I have seen a Printscreen of someones UBUNTU desktop and they had little Paddlock icons on their desktop shortcuts (which included HDD and software programs)?

You are misunderstanding what you are seeming, the padlock just means that the drive is owned by someone else, and that user  that has the icons on their  desktop doesn't have the proper permissions to access them.

If you don't want others to access other partitions/drives, disable automount, for a howto, have a look [here]("https://help.ubuntu.com/community/Mount/USB"), and manually mount them when you need them.

---

### Post by Jim Hornet on 2011-02-05
> **cariboo907 said:**
> You are misunderstanding what you are seeming, the padlock just means that the drive is owned by someone else, and that user  that has the icons on their  desktop doesn't have the proper permissions to access them.

If you don't want others to access other partitions/drives, disable automount, for a howto, have a look [here]("https://help.ubuntu.com/community/Mount/USB"), and manually mount them when you need them.

Thanks Cariboo907 for clearing that up

Would anyone here use a proxy for extra security eg to stop people pinging you or is that overkill - my Belkin router has a built in firewall (dont know how effective it is) I often download mods for games from torrent sites which I guess opens my ports to other users -

I have my remote access disabled.

---

### Post by cariboo on 2011-02-05
If you are behind a router, most of your security problem are already solved, the router does all the work, blocking things from the internal network.

Who cares if someone ping your router, nobody can tell whats behind it. The one thing I would suggest is to make sure Upnp is turn off, so you don't open any ports by accident.

---

