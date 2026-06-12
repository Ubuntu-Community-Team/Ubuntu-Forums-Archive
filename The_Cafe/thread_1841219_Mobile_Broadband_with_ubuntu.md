---
title: "Mobile Broadband with ubuntu ?"
date: 2011-09-09
forum: The Cafe
---

### Post by Nisal on 2011-09-09
Do you guys ever had problem with mobile broadband connecting with ubuntu ? 


This is a problem that i had from several ubntu release's, most of the time ubuntu unable to recognize hspa dongal and even it does it used to get disconnected ,

any one facing the same issue ?

---

### Post by BlacqWolf on 2011-09-09
Nope. One time I went to a hotel that had pay-to-use Internet, so I plugged in my grandpa's Sprint cell adapter and after a few initial setup dialogs it was working OOTB.

---

### Post by NCLI on 2011-09-09
Nope, it's been rocksolid for a while now.

---

### Post by switch10 on 2011-09-09
I have been in Australia the past 3 months using an optus pre-paid mobile broadband usb stick, no problems at all...

---

### Post by 3rdalbum on 2011-09-09
Mobile broadband can be a bit flaky regardless of OS.

---

### Post by BeRoot ReBoot on 2011-09-09
It worked for me. The hardware was some generic Huawei 3g dongle given out by the provider. I just plugged it in, it asked me for the pin, it established the connection, and when I opened the browser, a page came up explaining how to set up the connection properly, which I did.

---

### Post by anaconda on 2011-09-09
Most 3G dongles work without problems

BUT All 3g Wlan dongles work flawlessly.
That is because ubuntu sees those 3g dongles as just another normal wlan-internet

---

### Post by LowSky on 2011-09-09
I can tether my phone just fine. But my carrier seems to think I should pay more for that capability so I don't do it.

---

### Post by ShodanjoDM on 2011-09-09
I have an EVDO usb dongle, it works fine since 9.10 although in 11.04 I have to plug it out and plug it back in after login otherwise Network-Manager can't detect it.

I hope that this small regression will get fixed in 11.10.

---

### Post by SecretCode on 2011-09-09
Before 9.04 I had quite a few problems. Since then - flawless and fast. With Huawei devices, ZTE devices and Android HTC phone tethering.

---

### Post by Nisal on 2011-09-11
> **ShodanjoDM said:**
> I have an EVDO usb dongle, it works fine since 9.10 although in 11.04 I have to plug it out and plug it back in after login otherwise Network-Manager can't detect it.

I hope that this small regression will get fixed in 11.10.

i have same problem. anyway is there any optional software like mobile manager to use instead of default "Network Manager" ?

---

### Post by lancest on 2011-09-11
Use a 3G MIFI now for tablet and laptop.

---

### Post by ashickur.noor on 2011-09-11
I have tried a few EDGE and 3G modem in my country. Only I find mobidata not to work with Linux. But other all works well then windows.

---

### Post by 3rdalbum on 2011-09-11
> **LowSky said:**
> I can tether my phone just fine. But my carrier seems to think I should pay more for that capability so I don't do it.

You need to get away from North America then :-)

---

### Post by anaconda on 2011-09-12
> **Nisal said:**
> i have same problem. anyway is there any optional software like mobile manager to use instead of default "Network Manager" ?

wicd is good. Sometimes even better than Network Manager. 
Wicd is in the repositories. 
Note. Installing wicd will uninstall network manager. And if you want to move back to NM, just installing Network manager will uninstall wicd

Just google: wicd ubuntu

---

### Post by Nisal on 2011-09-22
> **anaconda said:**
> wicd is good. Sometimes even better than Network Manager. 
Wicd is in the repositories. 
Note. Installing wicd will uninstall network manager. And if you want to move back to NM, just installing Network manager will uninstall wicd

Just google: wicd ubuntu

thank you, gonna try this

---

### Post by psrdotcom on 2011-09-22
I have tried with Huawei Modems and ZTE Modems .. those are working fine in INDIA ..

---

### Post by djheadley on 2011-09-22
I'm using VirginMobile and haven't had any trouble.  I live in an area where I don't get much signal in my house (mobile home) but I use an external antenna and get a really strong signal.

I dual boot with Win Vista and activated the VirginMobile modem there so don't know about activating in Ubuntu.

---

