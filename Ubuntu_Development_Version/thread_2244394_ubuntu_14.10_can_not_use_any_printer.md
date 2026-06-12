---
title: "ubuntu 14.10 can not use any printer"
date: 2014-09-16
forum: Ubuntu Development Version
---

### Post by KOSKERS on 2014-09-16
When i click the print icon in Ubuntu-Setting-Center.
Nothing happened.
when i type the command   (system-config-printer)     in terminal.
It saidTraceback (most recent call last):File "/usr/share/system-config-printer/system-config-printer.py", line 57, in <module>import cupsImportError: No module named 'cups'

Hope someone can help me.

---

### Post by Elfy on 2014-09-16
*Thread moved to **Ubuntu Development Version**.*

---

### Post by Cavsfan on 2014-09-16
You didn't mention what printer you're trying to print to. I myself was surprised the other day when I could not print to my HP Photosmart C3180 all-in-one from Utopic.

I had to go through the instructions on this page: [http://hplipopensource.com/hplip-web/downloads.html](http://hplipopensource.com/hplip-web/downloads.html)

Then I could print with ease.

---

### Post by sammiev on 2014-09-16
For [Epson]("http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX") go here.

---

### Post by KOSKERS on 2014-09-17
Thank u so much.
Yes. i have installed. and it seems that i can print it normally. But it is only for HP printer.
If there is a Toshiba or another printer ? Need i install other seperate tools? such as toshibalip? 

Use ubuntu printer tools is a universe method for us to print something.
So,my question is why i can not open this ubuntu printer tools normally?
So my question is why

---

### Post by wgarcia on 2014-09-17
In one of my systems updated to Unicorn, I had to remove and reinstall cups because all my printer configuration had dissapeared.

---

### Post by Cavsfan on 2014-09-17
> **KOSKERS said:**
> Thank u so much.
Yes. i have installed. and it seems that i can print it normally. But it is only for HP printer.
If there is a Toshiba or another printer ? Need i install other seperate tools? such as toshibalip? 

Use ubuntu printer tools is a universe method for us to print something.
So,my question is why i can not open this ubuntu printer tools normally?
So my question is why

I'm not familiar with Toshiba printers but here's some searching on google that I hope will help. I searched for Ubuntu 14.04 as there's probably not much out there for 14.10 yet.
But, the directions for 14.04 should work for 14.10.

[https://www.google.com/webhp?as_q=&gws_rd=ssl#q=ubuntu%2014.04%20toshiba%20printing](https://www.google.com/webhp?as_q=&gws_rd=ssl#q=ubuntu%2014.04%20toshiba%20printing)

---

### Post by sammiev on 2014-09-17
What is the make and model of your printer?

---

### Post by KOSKERS on 2014-09-18
After u reinstall cups, all things go right?

---

### Post by wgarcia on 2014-09-18
In my case the problem was not configuring a new printer, but loosing all the printers I had configured after the upgrade to 14.10. Reinstalling cups restore my printer configuration.

---

