---
title: "How to create a connecting drone to Linux?"
date: 2014-03-01
forum: The Cafe
---

### Post by Portaro on 2014-03-01
Im interest in know the method to conect a drone to an pc with Ubuntu.

Im read that i need Arduino and rasperry, anyone have an idea about this?

---

### Post by tgalati4 on 2014-03-01
A google search:

[http://www.engadget.com/2013/12/04/skyjack-parrot-drone-raspberry-pi/](http://www.engadget.com/2013/12/04/skyjack-parrot-drone-raspberry-pi/)

[http://diydrones.com/group/raspberry-pi-pilots](http://diydrones.com/group/raspberry-pi-pilots)

---

### Post by Portaro on 2014-03-03
THanks man I search on google but I find some pages, but nothing how to implement a cam or antena connected to buntu.

---

### Post by tgalati4 on 2014-03-03
Add [Ivideo ]telemetry[/I] to your search terms.  At the SCaLE12x conference there was an interesting talk on using Arduinos and XBee radios for high-altitude ballons.  They had telemetry--sending back data in real time during the flight.  [https://www.socallinuxexpo.org/scale12x/presentations/arduino-powered-balloon](https://www.socallinuxexpo.org/scale12x/presentations/arduino-powered-balloon)

[http://hackaday.com/2010/03/17/arduino-balloon-tracking/](http://hackaday.com/2010/03/17/arduino-balloon-tracking/)

[http://forum.arduino.cc/index.php/topic,8316.0.html](http://forum.arduino.cc/index.php/topic,8316.0.html)

Video requires a lot of bandwitdth to send real-time.  In theory you could simply run a RaspberryPi with Raspian (a form of Debian) with a USB video camera and stream through VLC using a wireless dongle and have a linux PC on the same wireless network to pick the the VLC stream.  That limits your range to WirelessG or 100m or so.

---

