---
title: "Need help on LiveCD"
date: 2018-04-23
forum: Ubuntu, Linux and OS Chat
---

### Post by yondonjamts on 2018-04-23
Hi guys, I wanted to create installation ISO file from Custom LiveCD. And I could not find from google, stackexchange and many more. The last hope is ubuntu forum.
Any advise will be very thankful for me :KS

---

### Post by mastablasta on 2018-04-24
if you already have the CD made, then you can use various CD burning software to create the iso file. clonezilla would also work.

---

### Post by yondonjamts on 2018-04-24
Actually no sir, I have liveCD iso image. [https://wiki.gnuradio.org/index.php/GNU_Radio_Live_SDR_Environment](https://wiki.gnuradio.org/index.php/GNU_Radio_Live_SDR_Environment) from GNURadio. And this ISO image is like PLUG-N-PLAY. It is not installation disk. The thing that I wanted to do is modify this ubuntu image with pre-installed GNURadio to installation ISO. Sorry for my poor English skill :KS

---

### Post by mastablasta on 2018-04-25
> **yondonjamts said:**
> Actually no sir, I have liveCD iso image. [https://wiki.gnuradio.org/index.php/GNU_Radio_Live_SDR_Environment](https://wiki.gnuradio.org/index.php/GNU_Radio_Live_SDR_Environment) from GNURadio. And this ISO image is like PLUG-N-PLAY. It is not installation disk. The thing that I wanted to do is modify this ubuntu image with pre-installed GNURadio to installation ISO. Sorry for my poor English skill :KS

so you want to create your own version of Ubuntu?

then you need to look at remastersys AKA Linux Respin: [http://www.remastersys.org/](http://www.remastersys.org/)

other options are: 
1. distroshare ubuntu imager: [https://github.com/Distroshare/distroshare-ubuntu-imager](https://github.com/Distroshare/distroshare-ubuntu-imager)

2. customizer: [https://github.com/kamilion/customizer](https://github.com/kamilion/customizer)

---

### Post by spbhalekar on 2018-04-28
You need to add preseed.cfg file in ISO. Add your requirement in late_command section of preseed.cfg file.
Refer below link:
[https://codeghar.wordpress.com/2011/12/14/automated-customized-debian-installation-using-preseed/](https://codeghar.wordpress.com/2011/12/14/automated-customized-debian-installation-using-preseed/)

---

