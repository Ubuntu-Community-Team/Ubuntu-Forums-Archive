---
title: "WoW - enter game world crash - ATI driver?"
date: 2009-08-27
forum: Wine
---

### Post by volatilesquirrel on 2009-08-27
WoW crashes seconds after play starts.  I installed using [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft) as a guide.  It crashed similarly before and after the config.wtf mods and registry key addition and during every combination of them.

The troubleshooting page ([https://help.ubuntu.com/community/WorldofWarcraft/Troubleshooting#ATI%20enter%20game%20world%20crash](https://help.ubuntu.com/community/WorldofWarcraft/Troubleshooting#ATI%20enter%20game%20world%20crash)) lead me to believe it's a problem with my ATI driver.  I tried to finagle my xorg.conf file but it doesn't exist.  This lead me to believe I don't even have the ATI driver.

The guide [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver) isn't working for me because the first step is to go to Hardware Drivers and enable the ATI Graphic Driver ... which doesn't exist in Hardware Drivers.

I've done many forum/google searches and still haven't figured out where to go from here.  Any help would be much appreciated.

---

### Post by ajgreeny on 2009-08-27
What video card have you got in your computer? There are several old ones that have no proprietary drivers and will only work with the OS ati/radeon driver.

---

### Post by volatilesquirrel on 2009-08-27
typing lspci into Terminal returned: 01:00.0 VGA compatible controller: ATI Technologies Inc M22 [Mobility Radeon X300]
I believe that makes Mobility Radeon X300 my video card (sorry I am a bit of a newb)

---

### Post by Kai Summers on 2009-08-27
What version of Wine are you running?

---

### Post by volatilesquirrel on 2009-08-27
I'm using the most recent version of Wine, I believe.  Wine 1.1.18

---

### Post by hikaricore on 2009-08-27
Latest is Wine 1.1.28

---

### Post by volatilesquirrel on 2009-08-29
I tried using a guide to updating wine but after I followed it and restarted wine's menu icons changed but the Wine Configuration's About still says 1.1.18 .... so I can't figure out how to update wine either apparently =/

---

