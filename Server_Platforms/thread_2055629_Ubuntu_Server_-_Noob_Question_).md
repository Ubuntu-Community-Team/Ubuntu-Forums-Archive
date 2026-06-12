---
title: "Ubuntu Server - Noob Question :)"
date: 2012-09-09
forum: Server Platforms
---

### Post by jayaq32 on 2012-09-09
I am new to Ubuntu (desktop) and will never go back to win/mac. Thank you ;)

I am also new to Ubuntu Server. I have an oldie-but-goody dual xeon [Gateway 9510]("http://support.gateway.com/s/Servers/COMPO/Cases/WME866319/WME866319nv.shtml") server ([link to product page]("http://support.gateway.com/s/Servers/COMPO/Cases/WME866319/WME866319nv.shtml")) that had Windows 2000 installed.

I'd like to install Ubuntu desktop onto the box and just use it as workstation and local file server, but the drives are not recognized during the installation. I suspect it has something to do with the raid card configuration or drivers (?)

On the flip-side, I don't seem to have an issue installing Ubuntu Server.  Would it be possible to install the desktop GUI + Office on the Ubuntu Server installation? If so, how to proceed?

Lastly, are there any practical steps that I can take to 'secure' a new installation when using an Ubuntu Server + GUI setup?

I want to prevent my box getting accessed from the 'outside' without my knowledge. 

Again, I'd like to use the box as a workstation; prefer a desktop environment, but will take what I can get.

Thank you!

FYI: I am pretty much open to any other simple Linux solutions that will get a desktop up and running on this box.

---

### Post by jerome1232 on 2012-09-09
> **jayaq32 said:**
> 
On the flip-side, I don't seem to have an issue installing Ubuntu Server.  Would it be possible to install the desktop GUI + Office on the Ubuntu Server installation? If so, how to proceed?


I have a gut feeling that if the Server install worked, then the Ubuntu Alternate installer would work as well, but no need to reinstall, getting a full fledge desktop install is as easy as: 

```
sudo apt-get install ubuntu-desktop
```

A base install of Ubuntu is pretty secure, maybe use a host based firewall (Ubuntu uses UFW by  default) to restrict access to service to your lan only. Really so long as your not forwarding ports from your router no services will be exposed anyways.

You can always check out the stickies in the security section of this forum for some reading.
[http://ubuntuforums.org/forumdisplay.php?f=338](http://ubuntuforums.org/forumdisplay.php?f=338)

---

### Post by Bashing-om on 2012-09-09
hardware raid: from some little time back, some cards do have problems with ubuntu. Guides are available to assist.... Some suggest in many cases the software raid is even a better option. Lots of advise is available.

[INDENT]hth <==BDQ

[/INDENT]

---

### Post by jayaq32 on 2012-09-10
> **jerome1232 said:**
> I have a gut feeling that if the Server install worked, then the Ubuntu Alternate installer would work as well, but no need to reinstall, getting a full fledge desktop install is as easy as: 

```
sudo apt-get install ubuntu-desktop
```A base install of Ubuntu is pretty secure, maybe use a host based firewall (Ubuntu uses UFW by  default) to restrict access to service to your lan only. Really so long as your not forwarding ports from your router no services will be exposed anyways.

You can always check out the stickies in the security section of this forum for some reading.
[http://ubuntuforums.org/forumdisplay.php?f=338](http://ubuntuforums.org/forumdisplay.php?f=338)

Wonderful. I will install the GUI on Ubuntu Server using your tip. 

It sounds as if you're saying that a typicall Ubuntu Server install is pretty secure by default? Does this mean I am relatively safe to use it as a workstation box (Office, Web Browsing, etc.).

Curious, if you were me, what would you do to secure your system after installing Ubuntu Server on a Gateway 9150? 

Would you start by configuring the firwall (UFW)? Is UFW configured via CLI or GUI by default? 

If I left the server install "as-is"default after installation (w/GUI) will my system be totally exposed?

I've installed Ubuntu Server but I've really never used it or have much experience with it. Are there services running by default after install?

---

### Post by 2F4U on 2012-09-10
> It sounds as if you're saying that a typicall Ubuntu Server install is  pretty secure by default? Does this mean I am relatively safe to use it  as a workstation box (Office, Web Browsing, etc.).

This is correct. Neither Ubuntu desktop nor server by default have any open ports. However, naturally, it depends on what you install and how you configure it.

Personally, I configure a firewall (ufw) on a server and also on a workstation, but that is just personal preference. UFW can be configured through the terminal, but there are also GUI tools available in the repositories.

---

### Post by d3v1150m471c on 2012-09-10
> **2f4u said:**
> this is correct. Neither ubuntu desktop nor server by default have any open ports. However, naturally, it depends on what you install and how you configure it.

Personally, i configure a firewall (ufw) on a server and also on a workstation, but that is just personal preference. Ufw can be configured through the terminal, but there are also gui tools available in the repositories.

+1

---

### Post by jerome1232 on 2012-09-10
Yes, Ubuntu security is great for your average user, most of the software you'll ever need can be installed through Ubuntu's package management system, Ubuntu Software Center, or apt-get.

Really the main thing to look at is your browser, especially if you have java and/or flash. Both browser plugins have a terrible, terrible security history. I would create an apparmor profile for my firefox and call it a day. Apparmor is a security feature which can restrict what applications can do even more so than our linux style permissions can, effectively sandboxing your browser and it's plugins so that they only have access to what is absolutely necessary for them to run. It's not for the faint of heart but we have some decent tutorials and some preconfigured profiles floating around to get you started. I urge you to check out the Wiki entry about [apparmor]("https://help.ubuntu.com/community/AppArmor")

I've been meaning to lock down my firefox but I just haven't gotten around to doing it yet. 

Setting ufw to block incoming connections can be a good idea, but I don't think it's necessary if your behind a router.

---

### Post by jayaq32 on 2012-09-10
> **jerome1232 said:**
> Yes, Ubuntu security is great for your average user, most of the software you'll ever need can be installed through Ubuntu's package management system, Ubuntu Software Center, or apt-get.

Really the main thing to look at is your browser, especially if you have java and/or flash. Both browser plugins have a terrible, terrible security history. I would create an apparmor profile for my firefox and call it a day. Apparmor is a security feature which can restrict what applications can do even more so than our linux style permissions can, effectively sandboxing your browser and it's plugins so that they only have access to what is absolutely necessary for them to run. It's not for the faint of heart but we have some decent tutorials and some preconfigured profiles floating around to get you started. I urge you to check out the Wiki entry about [apparmor]("https://help.ubuntu.com/community/AppArmor")

I've been meaning to lock down my firefox but I just haven't gotten around to doing it yet. 

Setting ufw to block incoming connections can be a good idea, but I don't think it's necessary if your behind a router.

Gotta love this community! You guys answered the h*#@ outta those questions for me. I am newly enlightened. Cost? $0. I swear, Open Source is such a wonderful microcosm showing the potential of humanity working in harmony together .

Thank you soo much :)

---

### Post by SeijiSensei on 2012-09-10
Are you still having problems with the RAID card?  If the motherboard has standard IDE or SATA ports, I'd just pull the RAID and use those.  Some "fake RAID" hardware requires special drivers that may only have a Windows version.

---

