---
title: "Has anyone else noticed all the wifi problem?"
date: 2011-06-12
forum: The Cafe
---

### Post by irv on 2011-06-12
Has anyone else taken notice of all the posts out here about wifi problems? I know every release has them, but this one to me seem to have more then usual. Is this because of 11.04 or is it a problem in the newer kernel? I also had problems with my wifi, but I do with every release. I have a Broadcom card and they don't play well with Linux.

---

### Post by Spr0k3t on 2011-06-12
I haven't seen any more than usual.  However, there are a few changes coming down the pipeline with the Broadcom finally pulling their heads out of their *clouds* and opening the drivers for a selection of the 43xx chipsets.  I still won't purchase a wireless card that uses any Broadcom chipset though, too much hassle.  If the chipset does not work out of the box, it's not worth supporting.

---

### Post by Ichtyandr on 2011-06-12
I have Atheros and was hit by this bug on natty:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/768836](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/768836)
it was a kernel thing apparently

---

### Post by apollothethird on 2011-06-12
> **irv said:**
> Has anyone else taken notice of all the posts out here about wifi problems? I know every release has them, but this one to me seem to have more then usual. Is this because of 11.04 or is it a problem in the newer kernel? I also had problems with my wifi, but I do with every release. I have a Broadcom card and they don't play well with Linux.

Hi, Irv.  I don't notice more issues with wifi with this version than any other.  Also I have 5 computers in my shop running Ubuntu 11.04.  I've setup others and delivered to customers.  Two include Laptops.  I didn't experience any problem with any of the adapters, wireless, wifi, builtin NIC, or a Broadband modem I purchased from Cricket for my trip to Florida.

I plugged it up and it saw the Cricket provider and was able to click on connect problem free.

It had to load special drivers for the broadband modem and the wireless modems to work in the Windows machine.  But all the adapters I have was ready recognised by Ubuntu 11.04 and worked just by plugging them in.

I'm probably lucky with the adapter manufactorers that I have I have happened to have purchased.  But I  never have any problems with the adapters being recognised.

You might want to find out if another Broadband modem will work with the company you're trying to use.  

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

---

### Post by timZZ on 2011-06-12
Both my IBM Wi-Fi and DLINK Wi-Fi worked great - right away - on the initial installation.

In my opinion it is getting better ... version 9 ... nothing worked wirelessly out of the box. (obviously this is relative to the brands I was purchasing etc.)

---

### Post by irv on 2011-06-13
The reason I started this thread is because of all the people I have tried to help out here who seem to be having so many issues with wifi not working. The Broadcom 43xx seems to be the big one. But there are others also. Many dell products use the Broadcom card.

---

### Post by el_koraco on 2011-06-13
Yeah, the ath5 and ath9 kernel regressions have kicked in again, Broadcom cards have been a mess due to the opensourcing of the 43xx drivers, and Realtek hards which have worked for years have been hit by strange problems. Otoh, a lot of users have reported the Broadcom series to work out of the box for the first time.

---

### Post by TBABill on 2011-06-13
Tons more wireless complaints on Mint as well, particularly because so many left Ubuntu after Natty released. Broadcom broke for the BCM4311 and BCM4313 from what I can gather from posts and assistance I have tried to provide. My BCM4312 had no regressions so all is well with mine, but it seems a couple cards don't work right now with the STA driver where they did in 10.10 and earlier. Seems they work ok with the b43, but a user wouldn't know that if they always use the other driver on other distros or Ubuntu versions.

---

### Post by coffeecat on 2011-06-13
> **TBABill said:**
> Broadcom broke for the BCM4311 and BCM4313 from what I can gather from posts and assistance I have tried to provide.

BCM4313 breaks if you make the mistake of installing the STA driver, if what I read is anything to go by. But...

> **el_koraco said:**
> Otoh, a lot of users have reported the Broadcom series to work out of the box for the first time.

I'm one of them. BCM4313 works ootb with the open source driver on an HP Mini. I ignored Jockey pestering me to install the STA driver, and I'm glad I did so. I can only speak for my experience of the BCM4313, but I think most of the problem of that card is down to documentation saying that the STA driver supports it and Jockey quite unnecessarily prompting you to install it

---

### Post by MasterNetra on 2011-06-13
The problem with the broadcoms for Natty is with the bcmwl-kernel-source package. However if you install Maverick's version of it, then it purrs like a kitten. Just remember to use synaptic to lock version to stop it from "upgrading" back to natty's version of it. Though if or when you decide to distro upgrade into 11.10 remember to unlock it before doing the distro upgrade (unless its still broke in 11.10...). Hopefully it will be resolved and the broadcoms can finally all if not almost all can work from vanilla.

---

### Post by Irihapeti on 2011-06-13
Other way round for me. I have an EeePC 900 with the ath5k driver (forget what the exact chip name is), and in Natty I don't have to install wireless backports, for the first time.

---

### Post by Khakilang on 2011-06-13
I have no issue with the wifi USB adapter which uses rt73usb firmware. Just plug and it play. But I haven't try PCI card though.

---

### Post by Thewhistlingwind on 2011-06-13
I just tried a wireless device which wouldn't work in 10.4.

Guess what! In 10.10 it works!

Call me optimistic, but that's progress.

---

### Post by apollothethird on 2011-06-14
> **Thewhistlingwind said:**
> I just tried a wireless device which wouldn't work in 10.4.

Guess what! In 10.10 it works!

Call me optimistic, but that's progress.

This seems to indicate that some devices works and some don't.  Some work for some users and some don't work for some users.  This is the way it appears to have always been, as far as I can see from having explored the Internet for network support over the years.  It appears to me that with each generation of Linux it keeps getting easier... especially for me.

I wish I had the devices that people are having problems with so that I could test them in my environment.  I have lots of devices, especially network devices.  All the network adapters (NIC's, USB Wireless adapters, usb broadband modems) have worked right out of the box for me with Ubuntu 11.04.

For me, so far, I had a problem with a Hiro USB modem.  I did research and read someone say it worked by the winbound configuration, not like normal/standard serial support.  I only spent a few minutes with it since I had other modems in my shop.  I replaced it and the the other worked perfectly.  I'll explore to see if I can make that one work later.  But the same modem didn't work in Windows without specific drivers from the company.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

---

### Post by murderslastcrow on 2011-06-14
There are certain very old USB wireless dongles that have had their drivers blacklisted in favor of new ones that don't actually work out of the box without firmware, so that may be part of the issue.

But I honestly think it might be due to more attention/people using 11.04 due to Unity. I've seen a lot of people around here get more interested in it without me even saying anything, so I assume something caught peoples' attention.

Of course, there is also the issue of the new network indicator.

---

### Post by Legendary_Bibo on 2011-06-14
> **Spr0k3t said:**
> I haven't seen any more than usual.  However, there are a few changes coming down the pipeline with the Broadcom finally pulling their heads out of their *clouds* and opening the drivers for a selection of the 43xx chipsets.  I still won't purchase a wireless card that uses any Broadcom chipset though, too much hassle.  If the chipset does not work out of the box, it's not worth supporting.

I am actually waiting for this, my other computer has a broadcom 43-something card, and I tried everything for a week to get it to work. According to Ubuntu the driver is installed, but it doesn't work at all. Oh well it's running Win7 just fine.

---

### Post by irv on 2011-06-14
> **Legendary_Bibo said:**
> I am actually waiting for this, my other computer has a broadcom 43-something card, and I tried everything for a week to get it to work. According to Ubuntu the driver is installed, but it doesn't work at all. Oh well it's running Win7 just fine.

If it's a 4311 I can tell you how I got mine going.

---

