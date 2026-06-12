---
title: "Fingerprint reader not detected"
date: 2011-04-07
forum: System76 Support
---

### Post by Vadi on 2011-04-07
I followed steps in [http://ubuntuforums.org/showthread.php?t=1669245](http://ubuntuforums.org/showthread.php?t=1669245) to install fingerprint software, but even after a reboot, it does not detect that I have a fingerprint reader. I do, I'm using a serval laptop (model FL90). Can anything else be done for it?

---

### Post by isantop on 2011-04-07
Make sure you have the latest version of the System76 Driver (it's currently 2.6.1), then go to System > Administration > System76 Driver. Click on the Install Drivers tab, then click install.

Did that fix it?

---

### Post by Vadi on 2011-04-07
Nuh, says that I don't need any. [http://knowledge76.com/index.php/Serp3](http://knowledge76.com/index.php/Serp3) is my model.

---

### Post by isantop on 2011-04-07
What version of Ubuntu are you using?

---

### Post by Vadi on 2011-04-07
Ubuntu 10.10, 64bit.

---

### Post by isantop on 2011-04-07
When you ran the commands to enable the fingerprint reader, did any of them give you an error?

---

### Post by Vadi on 2011-04-07
Nuh, and it's all installed okay:

```
vadi@vadi-laptop:~$ sudo apt-get install fingerprint-gui policykit-1-fingerprint-gui libbsapi
[sudo] password for vadi: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
fingerprint-gui is already the newest version.
policykit-1-fingerprint-gui is already the newest version.
libbsapi is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
vadi@vadi-laptop:~$ 

```

---

### Post by Vadi on 2011-04-08
Same lack of detection on 11.04 beta as well, unfortunately :confused:

---

