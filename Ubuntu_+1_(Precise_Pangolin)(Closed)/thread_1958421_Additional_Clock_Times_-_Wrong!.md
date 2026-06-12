---
title: "Additional Clock Times - Wrong!?"
date: 2012-04-14
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by anejo on 2012-04-14
Has anyone else noticed that some of the cities display wrong times?
My setting currently show--for example--incorrect times for Perth and Singapore!

---

### Post by ubuntu27 on 2012-04-14
I just added "Singapore" on my Clock. Currently, it is displaying Sunday 9:33 AM.

And, according to Google it is also 9:33. So it is the right time: 

[https://encrypted.google.com/#hl=en&output=search&sclient=psy-ab&q=Singapore+time&oq=Singapore+time&aq=f&aqi=g4&aql=&gs_l=hp.3..0l4.524l1822l0l1969l14l8l0l4l4l0l260l1247l0j6j2l11l0.frgbld.&pbx=1&bav=on.2,or.r_gc.r_pw.r_qf.,cf.osb&fp=1272a89de59f0446&biw=1215&bih=708](https://encrypted.google.com/#hl=en&output=search&sclient=psy-ab&q=Singapore+time&oq=Singapore+time&aq=f&aqi=g4&aql=&gs_l=hp.3..0l4.524l1822l0l1969l14l8l0l4l4l0l260l1247l0j6j2l11l0.frgbld.&pbx=1&bav=on.2,or.r_gc.r_pw.r_qf.,cf.osb&fp=1272a89de59f0446&biw=1215&bih=708)

---

### Post by bdarb on 2012-04-14
> **anejo said:**
> Has anyone else noticed that some of the cities display wrong times?
My setting currently show--for example--incorrect times for Perth and Singapore!

Showing the correct time for those locations here aswell, are you using UTC or localtime for your hwclock?

---

### Post by anejo on 2012-04-15
How do I determine whether it's UTC or localtime?
'Time and Date' settings doesn't reference those options. The first time I added locations I recall UTC being there...

---

### Post by dino99 on 2012-04-15
12.4 default installation is using indicator-applet-complete, which is a bad choice, better to remove it and then:
- Alt+right-click on top bar & select "add to panel" then choose "clock"

That one is more customizable, you can set seconds, weather, location ; where you cant do that with indicator-applet-complete

---

### Post by anejo on 2012-04-16
> **dino99 said:**
> Alt+right-click on top bar & select "add to panel" then choose "clock"
Ummm... there is no 'Alt+right-click' happening on that panel.

[This install is 12.04 + Unity][SIZE=1][/SIZE]

---

### Post by anejo on 2012-04-16
Ok... found this helpful link
[https://help.ubuntu.com/community/UbuntuTime](https://help.ubuntu.com/community/UbuntuTime)
 
 To tell Ubuntu that the hardware clock is set to 'local' time: 
$ edit /etc/default/rcS
add or change the following section 
# Set UTC=yes if your hardware clock is set to UTC (GMT)
UTC=no

Conversely, it's interesting that there's a Windows reg tweak--if you dualboot--that can get it to understand UTC.
However... other than this method, **are there other methods for determining what the clock is using?**

---

### Post by shadowfirebird on 2012-04-16
> **anejo said:**
> Has anyone else noticed that some of the cities display wrong times?
My setting currently show--for example--incorrect times for Perth and Singapore!

Wait... you're supposed to enter the names of locations in that dialogue?  Since the only working entry is "UTC" on my install, I assumed I had to enter "GMT+4", etc, and that didn't work...  

The dialogue is lacking in tells somewhat.

I've now got a timezone set up for Houston.  It seems correct.

---

