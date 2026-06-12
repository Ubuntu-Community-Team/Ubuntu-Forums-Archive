---
title: "HOW TO: Increasing fonts size Google Earth 5.x"
date: 2010-03-21
forum: Tutorials
---

### Post by Francewhoa on 2010-03-21
**Issue**
In Google Earth 5.x interface the default fonts are too small.

**Requirements**
Ubuntu 8.04.x LTS Desktop Edition 32 bits
Google Earth 5.x

**Steps**
Type in the following command in TERMINAL.
```
sudo apt-get install qt4-qtconfig
```TERMINAL will ask for your password. You must type in you administrator password.

Type in the following command in TERMINAL.
```
qtconfig
```Go to "Fonts" tab.

Go to "Point Size".

Click on the dropdown menu. Change "9" for "14".

Navigate the the menu FILE > SAVE.

Navigate the the menu FILE > EXIT.

Open Google Earth 5. To do so navigate to the following Ubuntu menu APPLICATIONS > INTERNET > GOOGLE EARTH.

---

### Post by teach2carter on 2010-07-26
Thank you Onopoc. I am using 10.04 LTS and your fix worked like a charm.

Props to you...

---

### Post by wcradar on 2010-07-27
> **teach2carter said:**
> Thank you Onopoc. I am using 10.04 LTS and your fix worked like a charm.

Props to you...

they do provides a number of 3D viewer settings too

---

### Post by JamJim on 2010-08-09
I had to delete the qt4 libs that came with GoogleEarth.
Then it worked.
I guess it used system libraries in lieu.

---

### Post by felixcorrales on 2010-08-22
I had to set fonts size to 48.  System> Preferences> QT 4 Settings> Fonts> Point Size> 48.

 /32 inch monitor, HD.
/ubuntu 10.04.
/nvidia gt220.
/google earth linux 5.2.1.1547 bin file.

---

### Post by Drate on 2011-08-28
WOOHOO! Used the qt4-config, set the font to about 36.

This worked on 11.04 32-bit.

Thank you so much!

---

### Post by Charlie Tame on 2012-06-11
10.04 LTS here, worked great thank you. I had tried all kinds of things suggested by others in the GE .conf file but it seemed to ignore anything related to font size. My eyesight was never great but has deteriorated with age and following a quad bypass surgery about 5 years ago I have become a little dyslexic, so your assistance has been a great help as I can read the garbage I am typing BEFORE submitting it for directions :)

Thanks again,

Charlie

---

### Post by jerryrice on 2012-09-28
Thanks, this is the only method I could find that worked to fix the small fonts. using 12.04 with a 2560x1600 monitor.

fyi, google earth was working OK with very readable fonts in my initial 12.04 install and using google earth 6.2.2.6613 , after update manager finished loading about 100 files and the latest kernel , then the tiny font problem started, reloading google earth and trying other fixes floating on the net did not help. using qtconfig worked great .

---

### Post by Statia on 2012-10-09
The problem is not that the font in Google Earth is too small, the problem is it looks ugly. I think it looks like there is no anti-aliasing.  Can this be fixed with the same hack as well?

---

### Post by Statia on 2012-10-09
Changed the font as per instructions.
Opened Google Earth: nothing changed.
Opened qtconfig again: font settings are the same as before!

Maybe this only works on non-KDE systems?
I am using Kubuntu, I'd guess KDE overrides this somewhere?

---

