---
title: "starling 10.04 netbook edtion wireless gone :("
date: 2010-05-15
forum: System76 Support
---

### Post by superfrogman94 on 2010-05-15
Ever since i installed the system 76 driver wireless is gone, i had it before installing the driver... I tried installing gcc but i get a error that it could not find the package :( 

Please help!

---

### Post by superfrogman94 on 2010-05-16
Guys? 



Iv also recently had issues connecting to wired :(

EDIT: 70 views? Am i not giving enough info?

---

### Post by superfrogman94 on 2010-05-16
hmmm.. doing lshw i was able to find this

  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan1
       serial: 00:17:c4:91:b8:3c
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=802.11b/g

how can i enable it? :confused:

---

### Post by jdb on 2010-05-16
> **superfrogman94 said:**
> hmmm.. doing lshw i was able to find this

  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan1
       serial: 00:17:c4:91:b8:3c
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=802.11b/g

how can i enable it? :confused:

It sounds like the wireless switch is turned off.

This quote:

Your wireless LED now should be on, and you should be able to see wireless access points. If you cannot, there is a spring-loaded toggle switch on the right-hand side of the leading edge of your Starling. Toggle it *ONCE* to the right, and then release it. Now, reboot your computer. 

Is from this post:

[http://ubuntuforums.org/showthread.php?t=1330531&highlight=starling+wireless+switch]("http://ubuntuforums.org/showthread.php?t=1330531&highlight=starling+wireless+switch")

jdb

---

### Post by superfrogman94 on 2010-05-16
thanks!

im back in business :D

---

### Post by JollyGreenDragon on 2010-05-20
Same issue, but switch flipping does nothing.

Lshw shows -network DISABLED

Wireless works (poorly) off fresh 10.04 install.  I can get it working after one reboot with a 76 driver (which makes the wireless work great!)  But then... another reboot and I get 'Networking disabled'.  And no amount of threats of bodily harm seems to work! :confused:

I also have an issue where, whether or not I install the 76 drivers, running Ubuntu Updater and, well, updating my system does the same thing.  Has since 8.04.

I like your company, and I like you Thomas, especially since my first name is your last name, but I am starting to be at my wits end with the Starling.  Please help [PHP][/PHP]

---

### Post by superfrogman94 on 2010-05-20
try it again a few times (it took me about 4 tries of Toggling the switch and rebooting).

make sure you only toggle it once and then reboot i don't think it works if you do it more than once without a restart.

also maybe instead of rebooting you could try turning the system off then turning it back on.

---

### Post by thomasaaron on 2010-05-20
First, run this command... (you'll need a wired connection)...

```
sudo apt-get install build-essential
```

Please download and run the latest System76 Driver (2.4.9) from...

[http://planet76.com/repositories](http://planet76.com/repositories)  #Second link from the bottom.

If, after rebooting, your wireless light isn't on, do the toggle-switch thing.

---

