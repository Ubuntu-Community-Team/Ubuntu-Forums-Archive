---
title: "Security on dual boot"
date: 2009-10-26
forum: Security
---

### Post by Amethyst05 on 2009-10-26
Hi,

I am very new to Linux but I am loving Ubuntu. I run it on various computers with various configurations. 

On my main computer I have Ubuntu running in VirtualBox with Vista as the host. I have a testing web server running in it, download email, browse the internet etc and everything is running very well without any problems.

However, one of my other computers is a netbook. This has a dual boot configuration with XP and Ubuntu. This computer is used mainly for leisure, for example, reading ebooks, browsing the internet via Firefox and other non-internet things. No email is downloaded on this computer and no software is installed on the XP partition except for the basic things which came with the netbook. P2P is never used either. 

The XP partition has been running McAfee anti-virus and firewall and then Avast with Comodo as the firewall. However, it is continually being attacked by various trojans. I reformatted and reinstalled XP and Ubuntu and I'm back to using McAfee but it seems that as soon as I boot into Ubuntu the XP partition is infected with trojans. I can only think that these trojans are coming from the Ubuntu partition. I do not really want to remove the Ubuntu partition but is there any way I can secure things more in Ubuntu to stop it infecting the XP partition apart from removing the XP partition? I have tried running Avast in Ubuntu but that does not seem to help.

Thank you for any help or links to further information which will help me secure my Ubuntu installation.

---

### Post by ApEkV2 on 2009-10-26
Are you positively sure the infections happen during an Ubuntu session?
McAfee has proven to be the "***best***" in infection prevention (kidding).

---

### Post by piankhi on 2009-10-26
Is your ubuntu partition accessible from windows & vice versa?

---

### Post by cariboo on 2009-10-26
Think about this. If you are running a dual boot system, only one OS is running at a time, so it is pretty near impossible for XP to get any viruses when you are running Ubuntu.

The only way I could see this happening is if you have have you xp partition mounted when running Ubuntu and caching Firefox's temp files on the XP partition, which is pretty near impossible.

If you are constantly getting trojans and viruses, I would suggest you have a look at your internet usage habits.

---

### Post by ApEkV2 on 2009-10-26
> **piankhi said:**
> Is your ubuntu partition accessible from windows & vice versa?

Windows can't see ext3

---

### Post by Amethyst05 on 2009-10-26
All the signs seem to indicate that it is happening after a Ubuntu session.

I do not like McAfee either which is why I changed the anti-virus and firewall programs but the netbook is only a few weeks old and came with McAfee as default. I re-installed the operating systems yesterday and hence now have the default factory configuration in XP again.

---

### Post by Amethyst05 on 2009-10-26
> **piankhi said:**
> Is your ubuntu partition accessible from windows & vice versa?

Yes, Ubuntu can see the XP partitions and I can access them but XP cannot see the Ubuntu partitions.

> **cariboo907 said:**
> 

If you are constantly getting trojans and viruses, I would suggest you have a look at your internet usage habits.

Well, this is what I cannot understand because, being a 'mature' woman (i.e not a teenager), my internet habits are **very** conservative and my internet habits are the same as on the other computer with Ubuntu running in VB and this computer is not, and has never been, attacked by trojans.

---

### Post by piankhi on 2009-10-26
> **ApEkV2 said:**
> Windows can't see ext3

it can if you install a small utility under windows.

---

### Post by piankhi on 2009-10-26
> **Amethyst05 said:**
> Yes, Ubuntu can see the XP partitions and I can access them but XP cannot see the Ubuntu partitions.

Well i'm no expert, but i would suggest you keep your XP partition unmounted while using ubuntu. 

I would also suggest looking at your vista desktop, if its networked with your netbook. I think chances of getting a virus over the LAN from your desktop are higher.

---

### Post by Sarmacid on 2009-10-26
It is very unlikely that the attacks are coming from Ubuntu. Are you using noscript when you surf on Windows? A site that may seem harmless maybe the one responsible for the malware. 

However it is also possible that other computers in the network are infecting it or maybe if you use usb drives, they might have undetected malware.

---

### Post by phillw on 2009-10-26
> **Amethyst05 said:**
> Hi,

I am very new to Linux but I am loving Ubuntu. I run it on various computers with various configurations. 

On my main computer I have Ubuntu running in VirtualBox with Vista as the host. I have a testing web server running in it, download email, browse the internet etc and everything is running very well without any problems.

However, one of my other computers is a netbook. This has a dual boot configuration with XP and Ubuntu. This computer is used mainly for leisure, for example, reading ebooks, browsing the internet via Firefox and other non-internet things. No email is downloaded on this computer and no software is installed on the XP partition except for the basic things which came with the netbook. P2P is never used either. 

The XP partition has been running McAfee anti-virus and firewall and then Avast with Comodo as the firewall. However, it is continually being attacked by various trojans. I reformatted and reinstalled XP and Ubuntu and I'm back to using McAfee but it seems that as soon as I boot into Ubuntu the XP partition is infected with trojans. I can only think that these trojans are coming from the Ubuntu partition. I do not really want to remove the Ubuntu partition but is there any way I can secure things more in Ubuntu to stop it infecting the XP partition apart from removing the XP partition? I have tried running Avast in Ubuntu but that does not seem to help.

Thank you for any help or links to further information which will help me secure my Ubuntu installation.


Hi, I wrote these a while back for XP (They work on my dual booting vista unit as well)
The stuff is in the stickies sections at the top. They're pretty well documented and explained.

[http://www.vpolink.com/forumdisplay.php?f=254](http://www.vpolink.com/forumdisplay.php?f=254)

Avast can be asked to do a 'boot' check in XP, although I'd use BitDefender from ubuntu to actually scan the windows partition.

The installation of Bitdefender is also within that area.

The missing bit that you may not have is SpyBot Search & Destroy for your windows installation, the installation and use of it in safe mode is in the stickies in the above link.

Regards,

Phill.

---

### Post by Amethyst05 on 2009-10-26
> **piankhi said:**
> Well i'm no expert, but i would suggest you keep your XP partition unmounted while using ubuntu. 

I would also suggest looking at your vista desktop, if its networked with your netbook. I think chances of getting a virus over the LAN from your desktop are higher.

piankhi, that sounds like a good solution. I just need to find out how to stop Ubuntu from mounting them automatically. 

The computers are not networked, by the way.

> **phillw said:**
> Hi, I wrote these a while back for XP (They work on my dual booting vista unit as well)
The stuff is in the stickies sections at the top. They're pretty well documented and explained.

[http://www.vpolink.com/forumdisplay.php?f=254](http://www.vpolink.com/forumdisplay.php?f=254)


Thanks for this, Phil. I've just installed a better anti-virus and firewall on the XP netbook again and doing a complete scan so it will be a while before I can check this out but it looks like you have some interesting information there.

---

### Post by Sarmacid on 2009-10-26
> **Amethyst05 said:**
> I just need to find out how to stop Ubuntu from mounting them automatically.
Check out the documentation for fstab [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by fraserstaple on 2009-10-27
Hey Amethyst.
  	 	 	 	 	 	  I am Fraserstaple and I read your entire pasting. You are using two Operating System. I am suggesting to you that Linux OS and Ubuntu OS have it's inbuilt software to run operating system. If you want any accessories in it, you have to download the software as the same configuration of OS. Anyways Thanks.

---

