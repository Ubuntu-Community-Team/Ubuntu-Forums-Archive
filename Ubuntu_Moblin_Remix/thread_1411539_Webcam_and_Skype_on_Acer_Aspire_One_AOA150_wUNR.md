---
title: "Webcam and Skype on Acer Aspire One AOA150 w/UNR"
date: 2010-02-20
forum: Ubuntu Moblin Remix
---

### Post by pmains on 2010-02-20
Hi,

  I have an Acer Aspire One that came with a trial version of Windows 7. The trial expired, and so I decided to try Moblin 2.1 and UNR Karmic. I had trouble getting sound to work with Moblin, and decided that installing packages with apt-get in Ubuntu was easier than installing with YUM (simply for the auto-completion feature).

  So, I switched to UNR Karmic, and now my webcam isn't recognized in Cheese -- which it was in Moblin.

  Not only that, but my reading has led me to believe that Skype 2.1 and Pulseaudio don't play well together. In 2.0, you could select your input and output (e.g., hw:0) and get Skype and Pulseaudio working. Unfortunately, 2.0 is no longer available. Does anyone know how to configure Pulseaudio to work with Skype, or should I be using jackd or some other technology? Or is it possible to just kill pulseaudio and have Skype interact directly with ALSA?

Thanks in advance.

---

### Post by fballem on 2010-02-20
> **pmains said:**
> Hi,

  Not only that, but my reading has led me to believe that Skype 2.1 and Pulseaudio don't play well together. In 2.0, you could select your input and output (e.g., hw:0) and get Skype and Pulseaudio working. Unfortunately, 2.0 is no longer available. Does anyone know how to configure Pulseaudio to work with Skype, or should I be using jackd or some other technology? Or is it possible to just kill pulseaudio and have Skype interact directly with ALSA?

Thanks in advance.

I am currently running Skype 2.1.0.81 with PulseAudio with no problems. I was able to select PulseAudio (see screenshot below). I don't know if this will work in your specific configuration, but it has been working well in mine.

Hope this helps,

---

### Post by pmains on 2010-02-20
Ah. Removing the "Allow Skype to automatically adjust my mixer levels" checkbox worked.

So that just leaves the webcam. Any ideas of how to troubleshoot that? I don't see it when I run lspci.

```

00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
03:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
04:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller
04:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller
04:00.3 System peripheral: JMicron Technology Corp. MS Host Controller
04:00.4 System peripheral: JMicron Technology Corp. xD Host Controller
```

---

### Post by pmains on 2010-02-20
The answer is found in this thread:

[http://ubuntuforums.org/showthread.php?t=1389994]("http://ubuntuforums.org/showthread.php?t=1389994")

I just needed to reboot for my camera to be recognized.

---

