---
title: "Fans never stop on Gazelle Professional"
date: 2013-11-10
forum: System76 Support
---

### Post by nomorevalley on 2013-11-10
I've got a Gazelle Professional, starting yesterday both fans came on at full speed and haven't stopped since (both CPU and GPU). They even do it before Ubuntu loads- as soon as the power comes on. I checked the temp using the sensors command - 41C. They are extremely loud and kind of pulse. Anyone got any idea what is causing this and how to fix it ?

---

### Post by isantop on 2013-11-11
Which version of Ubuntu are you using, and have you installed any available updates? 

If you're on 13.04 or later, be sure to install the correct Nvidia driver package from our repository by running these commands:

```
sudo add-apt-repository ppa:system76-dev/stable
sudo apt-get update
sudo apt-get install system76-driver system76-driver-nvidia
```

---

### Post by nomorevalley on 2013-11-11
I am running 12.04 with driver version 3.2.3 . I reset the System 76 driver to factory default and now it says driver version is 3.2.7 - no change with the fans. The Nvidia driver is version 319. I've attached a log file. The problem started yesterday 2 days ago sometime before 1pm.

---

### Post by benhill70 on 2013-11-12
1. Try cycling the fans, with Func+1
2. Get some compressed air cans, try cleaning the vents. Do not clean when the laptop is on, hibernate mode is ok. Otherwise, you might get condensation.

---

### Post by nomorevalley on 2013-11-12
I cleaned the vents a few days before this started -  and I cycled the fans just now. The fans still come on but not full blast. After monitoring the temperature for 15mins (down from 49 to 45) I'm going to say that this worked. Thanks !!! You are a Rockstar :guitar:

---

### Post by benhill70 on 2013-11-13
Glad to hear it. Though I would take the bottom plate off, there's one on my Bonobo and clean the fans carefully.

---

