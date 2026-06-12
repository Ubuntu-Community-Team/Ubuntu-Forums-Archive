---
title: "Bonobo cpu temps how to"
date: 2012-06-11
forum: System76 Support
---

### Post by kend650 on 2012-06-11
I have a System 76 Bonobo and I would like to monitor the cpu temps.  What apps should be installed and what sensors does System 76 provide for monitoring cpu temps?

---

### Post by kend650 on 2012-06-14
Found a way to do this...

---

### Post by joe4ska on 2012-06-15
install lm-sensors and follow the instructions at [https://help.ubuntu.com/community/SensorInstallHowto]("https://help.ubuntu.com/community/SensorInstallHowto")

After that you can hunt down some applets to display the statistics like this one [http://www.omgubuntu.co.uk/2011/05/psensor-a-graphical-temperature-monitor-for-ubuntu/]("http://www.omgubuntu.co.uk/2011/05/psensor-a-graphical-temperature-monitor-for-ubuntu/")

---

### Post by brdmn on 2012-06-17
> **joe4ska said:**
> install lm-sensors and follow the instructions at [https://help.ubuntu.com/community/SensorInstallHowto](https://help.ubuntu.com/community/SensorInstallHowto)

After that you can hunt down some applets to display the statistics like this one [http://www.omgubuntu.co.uk/2011/05/psensor-a-graphical-temperature-monitor-for-ubuntu/](http://www.omgubuntu.co.uk/2011/05/psensor-a-graphical-temperature-monitor-for-ubuntu/)

I've been using Psensor (the applet mentioned above) with my lemu4, and it is quite good.  Does the basics and doesn't chew up too many resources.

I run Xubuntu, so I first tried xfce4-sensors-plugin.  However, I ran into issues with that plugin because it wants to run hddtemp, and that doesn't work right on my lemu4 (maybe because I have an SSD, which doesn't have some hardware that is present on standard drives?)

---

### Post by joe4ska on 2012-06-18
@brdmn Thanks for mentioning the xfce4-sensors I forgot about that. Also I just picked up a lemu4 with SSD so thanks again for mentioning the limitation on Hard Drive temp. I would have likely wondered if I did something wrong which broke the temp settings. :D

---

