---
title: "Mini-PCs are taking over a segment of the market, but little Linux Support"
date: 2016-07-31
forum: Ubuntu, Linux and OS Chat
---

### Post by mail-2o on 2016-07-31
The Bay and CherryTrail PCs, designed for Android and Win10 seem to be taking over a segment of the PC market but are not yet well supported by Ubuntu. Is this likely to change? 


I have battled with one, Cherry Trail 1.4Ghz/2GB RAM/32GB eMMC and now that I've overcome the over-heating problems that seem to be inherent in passively cooled Mini-PCs, have found it to be an excellent and stable workhorse. I can get around the lack of sound, don't need bluetooth nor WiFi but am asking if anyone else has succeeded in using Linux on these? 


A quick review of the current market shows a large number of makers of these computers at very good prices; ~£70-£150. Some are listed below:



[LIST=1]
[*]
[*]**    MINIX** NEO Z64-W, Intel Mini PC Windows 10 Edition.    Intel Z3735F
[*]**    GULEEK** i8S Pocket Mini PC Windows10 Android4.4    2GB/32GB, Bay Trail CR Z3735F, 1.33GHz, up to 1.83GHz
[*]**    Stoga** Umin SVJ001 Windows 10 mini PC with 2MP Camera,    Bay Trail Z3735F 1.8GHz, 2GB/32GB
[*]**    PowerLead** Ptox P1030 Windows 10 Mini PC Bay Trail    Z3735F 1.8GHZ 2GB/32GB 2MP Webcam
[*]**    DroidBOX** Wintel W8 PRO Windows10 Mini PC 1.84ghz CPU    Cherry Trail Z8300 2GB/32GB
[*]**    JUSTOP** G-PC i10 Windows 10 Mini PC Intel X5 Quad Core    Z8300 1.84Ghz 2GB/32GB Expandable With Extra SSD Bay
[*]**    Sumvision** Cyclone Mini Micro PC 2 Windows 10 Cherry    Trail Intel Quad Core x5-Z8300 up to 1.84Ghz burst 2GB/32GB USB3.0 Launched    Q2&#8217;15 4 Core
[*]**    Plater** Beelink BT3 MINI PC 4K Intel Atom x5-Z8300    2GB/&#8211;40GB Local Disk(D&#8211;20GB)
[*]**    Plater** Beelink BT7 Windows Intel Atom x7-Z8700r 2M    Cache DDR3 4GB/64GB
[/LIST]

---

### Post by oldos2er on 2016-07-31
Not really a support request; moved to Ubuntu, Linux and OS Chat.

---

### Post by Geoffrey_Arndt on 2016-07-31
I wonder if the market (e.g., folks that are interested in these devices) are aware . . . . that on the low-end re price continuum are the newer _**Raspberry Pi**_ devices, and on the higher end (but still not too costly) are devices such as _**Logic Supply's CL100**_ (easily obtainable in US, Europe, East Asia):   [https://www.logicsupply.com/](https://www.logicsupply.com/)
    
With the slightly higher end products you're getting devices that will last 10+ years versus 1-3.   With the CL100 for example, can run both Ubuntu OS  . . & Win 10.

PostScript:   I'm aware that the CL100 doesn't offer these particular chips, however, the Braswell based Celeron N3150 (@1.6GHz) offers excellent, low power/heat results with Ubuntu fully supported (OEM pre-install)

---

### Post by buzzingrobot on 2016-07-31
Intel is a strong and active community participant and, very likely, will, sooner or later, bring kernel and driver support for new chips into Linux.  Probably over at least a few kernel release iterations.

The Skylake chips were released late in 2015 and only, IMO, the mainline 4.6 and 4.7 kernels offer adequate support.

Windows support gets first attention because OEM's buy  Intel chips to sell in machines that must run Windows.

---

### Post by grahammechanical on 2016-07-31
It is the usual situation. Lots of adverts for Windows powered devices. No adverts for Linux powered devices. Now, if any of these suppliers are interested in producing and selling devices with Ubuntu pre-installed, then Canonical will surely enter into a partnership with them.

Do not expect Canonical to compete with Microsoft or Apple. 

Regards

---

### Post by mail-2o on 2016-08-01
> **oldos2er said:**
> Not really a support request; moved to Ubuntu, Linux and OS Chat.I didn't make myself clear. This is a support request. I cannot get Bluetooth, sound nor WiFi to work on my [Cherry Trail Intel Quad Core x5-Z8300]("http://digitalanswers.info/2016/07/02/the-desktop/") nor have I found anyone else that has managed this. Is there any way I can do this?

---

### Post by mail-2o on 2016-08-01
> **Geoffrey_Arndt said:**
> I wonder if the market (e.g., folks that are interested in these devices) are aware . . . . that on the low-end re price continuum are the newer _**Raspberry Pi**_ devices, and on the higher end (but still not too costly) are devices such as _**Logic Supply's CL100**_ (easily obtainable in US, Europe, East Asia):   [https://www.logicsupply.com/](https://www.logicsupply.com/)I expect so, but the Raspberry Pi, as capable as it is and is a fine Kodi computer, falls short of PC performance in many areas. It just doesn't have enough power. The CL 100 is an expensive computer. The range of mini-PCs that I listed, are cheap, small, consume little power and are plentiful but are not supported yet. [Ian Morrison]("http://linuxiumcomau.blogspot.com/2016/07/dual-booting-ubuntu-and-windows-on.html") has had some success with the Intel compute stick but it sounds like he has had to work closely with Intel. I have tried his 14.04 and 16.04 ISOs on my Sumvision Cherry Trail Intel Quad Core x5-Z8300 but the ISOs wont even run from the USB stick even though it is a similar device to the compute stick.

---

### Post by mail-2o on 2016-08-01
> **buzzingrobot said:**
> Intel is a strong and active community participant and, very likely, will, sooner or later, bring kernel and driver support for new chips into Linux.  Probably over at least a few kernel release iterations.Thanks. It sounds like the answer then, is just to wait a while. I did this with an [Intel Mini-ITX dual core board]("https://ubuntuforums.org/showthread.php?t=2320221") aimed at the auto market and eventually compatibility arrived in 16.04.

---

### Post by mail-2o on 2016-08-01
> **grahammechanical said:**
> It is the usual situation. Lots of adverts for Windows powered devices. No adverts for Linux powered devices. Now, if any of these suppliers are interested in producing and selling devices with Ubuntu pre-installed, then Canonical will surely enter into a partnership with them. Do not expect Canonical to compete with Microsoft or Apple. RegardsYes. Thanks for all your replies. I understand the situation now. I wouldn't expect Canonical to try that. It's more likely to be the other way around.

---

### Post by help_me2 on 2016-08-01
> **grahammechanical said:**
> It is the usual situation. Lots of adverts for Windows powered devices. No adverts for Linux powered devices. Now, if any of these suppliers are interested in producing and selling devices with Ubuntu pre-installed, then Canonical will surely enter into a partnership with them.

Do not expect Canonical to compete with Microsoft or Apple. 

Regards
What's new, right? As mentioned before, Intel offers good support for Linux powered devices. My 5 yr old Dell Latitude still runs perfectly with Ubuntu. And blazing fast with 8gb RAM and an SSD. I couldn't be happier and not looking to upgrade my hardware anytime soon. 

Those seeking a linux PC need to do their homework or go to System 76 or Zareason for preinstalled options. I'm sure there are others too. The world actually runs on linux, when you consider every embedded device, server, android phone/tablet, etc...... just not on the traditional desktop. It's OK with me. I used to be one of those people that used to try and convert the world to linux, but no more. If someone has questions, I'll answer the best I can, but no more crusades for me. Use what works best for you. Chances are you're using Linux more than you think on a daily basis.

---

### Post by cariboo on 2016-08-01
If you need help with your device, I suggest you be more direct, post the blurtooth, wifi and audio chipsets, and what you have done already to try and solve the problem.

---

### Post by mail-2o on 2016-08-02
> **cariboo said:**
> If you need help with your device, I suggest you be more direct, post the blurtooth, wifi and audio chipsets, and what you have done already to try and solve the problem.Thanks. I'll try and find out, and then find the appropriate forum. 

I've found the chat most helpful and discovered that there is a lot of work going on with regard to the Intel Compute Stick, which is just one variant, albeit an expensive variant, of these mini-PCs. Eg at Linuxium and Liliputing.

---

### Post by mastablasta on 2016-08-04
there is a group on g+ about mini pc and from what i read in their news and user posts - mostly they seem to run on linux.

---

