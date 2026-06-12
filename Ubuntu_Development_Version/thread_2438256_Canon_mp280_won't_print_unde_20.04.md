---
title: "Canon mp280 won't print unde 20.04"
date: 2020-03-08
forum: Ubuntu Development Version
---

### Post by pop.horea on 2020-03-08
Until today i had 19.04 and my canon mp280 printer worked, bot printer and scanner. I've fresh installed 20.04 and gutenprint driver and added my printer but it doesn't print. It can't start printer. Tried to install driver from canon site but i get unmeet dependencies.
Please, if you know how to make it work, write here. Tomorrow i must print.

---

### Post by CelticWarrior on 2020-03-08
What drivers are you trying to install and what errors?

---

### Post by wildmanne39 on 2020-03-08
*Thread moved to **Ubuntu Development Version a more appropriate sub-forum**.*

---

### Post by pop.horea on 2020-03-09
I've manage to install depencie libtiff4, then install driver: cnijfilter-mp280series_3.40-1_amd64. I restarted PC and printer was added. I don't know if what I done or what development guys did.
It's printing fine.

---

### Post by dino99 on 2020-03-09
I also use a canon with 20.04, but mx475 here, and there is no need to install  a driver, Focal install them by default.
You might first check if the printer is found and reconized into System Settings Printers , and add yours if not yet done.
Then try using it and glance at 'journalctl -b' to find possible usefull error/warning

---

### Post by pop.horea on 2020-03-09
It's printing very fast. 
2 cd bag envelopes from 100 printed, jammed in printer.
After i finished, i added in printer settings at add another options: density 4. Maybe it will prin slower.
It has no option for slow printing.

---

### Post by dino99 on 2020-03-09
ink or laser jet printer ? Maybe find/watch canon forum too.

---

### Post by pop.horea on 2020-03-09
What i've done yesterday ? I tried to get joomla on localhost and uninstaled php from terminal. Result 19.04 was broken. After that i booted live 19.04 from dvd and had an usb external hdd. So downloaded 20.04 and for my suprise i could make usb external hdd as a start up disk. Installed 20.04 but i see when i make audio cds that root directory in k3b is not expanding. But i can add from open folder. Printer has no slow printing option. Nvidia video cards in number of 2 are working with proprietary driver and BOINC is computing on them. VLC is working. ViaCAD under wine is ok. Chromium browser is ok. I don't see any other problem.

---

### Post by pop.horea on 2020-03-09
ink

---

### Post by pop.horea on 2020-03-09
I've added in ppd those line below:

*OpenUI *cupsPrintQuality/Print Quality: PickOne
*OrderDependency: 10 AnySetup *cupsPrintQuality
*DefaultcupsPrintQuality: Normal
*cupsPrintQuality Draft/Draft: "3"
*cupsPrintQuality Normal/Normal: "4"
*cupsPrintQuality High/Photo: "5"
*CloseUI: *cupsPrintQuality

I tried replacing 3,4,5 with Draft, Normal, High.
It appears the dropdown list button with selecting betwhen Draft, Normal and Photo but the speed of printing is the same on Photo as it was before, very fast.

---

### Post by progers5 on 2020-05-06
I installed the Gutenprint package in my Ubuntu 20.04 installation using the following command and was then able to add a Canon mp280 printer that works fine for both printing and scanning.
"sudo apt install printer-driver-gutenprint"
Hope this helps.

---

### Post by slickymaster on 2020-05-06
20.04 has been released.

Thread closed.

---

