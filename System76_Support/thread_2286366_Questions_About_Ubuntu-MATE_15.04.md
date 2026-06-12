---
title: "Questions About Ubuntu-MATE 15.04"
date: 2015-07-11
forum: System76 Support
---

### Post by wagb278 on 2015-07-11
On a System 76 Kudu running Linux Mint 17 (LTS) we're having problems with WiFi and other things.

So I am considering installing Ubuntu MATE with the newer kernel in hopes of getting solid WiFi connectivity in the home.  Am I correct that after installing the new system I still need to install the System76 driver using the apt-get sequence - and will the drivers install & work with MATE, not Unity. 

I just want a reliable MATE system with reliable WiFi on this computer.  The 3160 Intel WiFi can even just run 802.11 G because we have only 3.0 Mps DSL, I don't need N or AC modes the card supports. 

Thanks

---

### Post by Geoffrey_Arndt on 2015-07-12
Many things can cause network connectivity issues.   If you've connected to your wireless ssid already, then the current kernel & wifi  hardware works but there may be a configuration issue, or even issue with ISP, etc.   Regarding the Sys76 drivers, you will need to ensure you have the Sys76 official PPA enabled in your sources.    You can certainly try Ubuntu Mate, maybe the reinstall will fix any possible bad configs of the past.

---

### Post by Vladlenin5000 on 2015-07-12
[http://knowledge76.com/index.php/Restoring_Your_System](http://knowledge76.com/index.php/Restoring_Your_System)

The driver package you're supposed to install includes tweaks for WiFi.

---

