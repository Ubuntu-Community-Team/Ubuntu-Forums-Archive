---
title: "ZTE EV-DO AC8700 USB Modem Connection in Ubuntu 10.10 solved"
date: 2011-04-02
forum: Testimonials &amp; Experiences
---

### Post by Tom Karam on 2011-04-02
After Long hours of hard work, I finally found out how to connect ZTE EV-DO AC8700 USB Modem supplied by BSNL, India. Here's what I did and what's to be done:- 

1) Download the linux driver for ZTE EV-DO AC8700 from [http://www.ztemt.com/ennewzte/uploadimages/1257081294661.zip](http://www.ztemt.com/ennewzte/uploadimages/1257081294661.zip) 

2) Extract it and then install the .deb package/app (CrossPlatformUI-V1.0.27-BSNL-i386-ubuntu.deb).

3) Install GNOME PPP (gnome dial up tool). This can be found from [ Applications - Ubuntu Software Centre and in search bar type GNOME PPP]. Obviously, you'll need Internet Connection for this download.

4) Now, u'll find the application (ZTEMT UI) in [Applications-Internet-ZTEMT UI].

5) Open it. Click Settings. Input phone number as #777,Username and then password. Click Connect and then Voila!!! Happy Now ?

---

### Post by Tamlynmac on 2011-04-02
This probably belongs [here]("http://ubuntuforums.org/forumdisplay.php?f=100").

---

### Post by ibo.ezhe on 2011-04-20
doesn't work for me. Installation of crossplatformui deb went with errors and ZTEMP UI application does not connect.

---

### Post by ibo.ezhe on 2011-04-20
After some time struggling find an appropriate solution for connecting Ubuntu 10.10 and ZTE 8700 ([http://korenkov.info/ubuntu-1010-and-zte-ac-8710]("http://korenkov.info/ubuntu-1010-and-zte-ac-8710")).

I have updated Network Manager from [https://launchpad.net/~network-manager/+archive/ppa]("https://launchpad.net/~network-manager/+archive/ppa") and used a modprobe command:
```
modprobe usbserial vendor=0x19d2 product=0xfffe
```

---

### Post by arunb on 2011-04-21
how is the connection with BSNL ??

---

### Post by Elfy on 2011-04-21
Please do not use this section for support questions, bug reports, or debate.

Closed

---

