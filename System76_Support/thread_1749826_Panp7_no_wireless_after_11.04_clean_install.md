---
title: "Panp7 no wireless after 11.04 clean install"
date: 2011-05-04
forum: System76 Support
---

### Post by edochan3 on 2011-05-04
Hi all.  Long-time lurker, first-time poster.

I performed a clean install on my Panp7 (purchased Dec 2010) and now the system doesn't even see the wireless card.  I had to rebuild GRUB (according to the instructions [here]("http://www.knowledge76.com/index.php/Restore_Grub")), but then booted fine - except no wireless.  I also performed a System76 restore and rebooted - still no wireless.  Here's my lspci output as proof:

```
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 18)
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 18)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06)
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 06)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
02:00.0 VGA compatible controller: ATI Technologies Inc M92 [Mobility Radeon HD 4500 Series]
02:00.1 Audio device: ATI Technologies Inc RV710/730
06:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller (rev 80)
06:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller (rev 80)
06:00.3 System peripheral: JMicron Technology Corp. MS Host Controller (rev 80)
06:00.5 Ethernet controller: JMicron Technology Corp. JMC250 PCI Express Gigabit Ethernet Controller (rev 03)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 05)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 05)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 05)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 05)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 05)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 05)
```

I cannot find a wireless device in there, but please correct me if I'm wrong.  The wireless radio LED lights up (green) and Fn-F11 turns the status LED on/off.  Also, when booting from the Live CD (x64) to perform the clean install, the wireless worked fine.  But now booting from the same disc results in no wireless device as well.  I'm really hoping this isn't a hardware issue, so will appreciate any input to resolve this through software.

Thanks!

---

### Post by isantop on 2011-05-05
As  odd as this sounds, try connecting to a different access point. I had a user a while ago with your exact problem, and it turned out to be an issue with their router.

---

### Post by edochan3 on 2011-05-29
UPDATE:

Sorry for the slow reply, but I've got it all working again.  The first thing I tried was to boot from a Mint 10 live cd - wireless worked flawlessly from the Mint live environment.  Then, it stopped working once I actually installed Mint 10.  It worked better than Ubuntu 11.04, because I could at least see various wireless APs - it just wouldn't connect.  So, I started poking around in my router settings.  I changed my wireless security from "WPA2 Personal Mixed" to "WPA2 Personal" (running DD-WRT).  That fixed the connection issues.  Then, for good measure, I re-installed Ubuntu 11.04 x64 and can confirm that everything works fine now.

Thanks for the help!

@isantop, Sorry I didn't try your advice, but it looks like the problem did have something to do with my router settings - so you pointed me in the right direction.  I'm still not convinced there wasn't (isn't) something else going on and I believe it's a software issue.  I can't accept that my wireless security settings worked fine for several months and then just stopped working upon upgrade to Ubuntu 11.04 (other wireless devices in my network continued working throughout).  That being said, I'm willing to live with what I've got and I'm open-minded enough to realise that a 6-month release cycle may not always provide the most stable environment.  :P

---

