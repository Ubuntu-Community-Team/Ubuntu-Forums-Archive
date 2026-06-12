---
title: "Good News: Ubuntu CE Karmic metapackage is ready for testing"
date: 2009-11-13
forum: Ubuntu Christian Edition
---

### Post by david_kt on 2009-11-13
I have uploaded ubuntu-ce metapackage for karmic. There are new and important changes in this version:

1. Easy internet sharing/ filtering sharing
I have added a function in dansguardian GUI to be able to share internect connection "Windows XP way", i.e. you just need to select which network card to share to and the rest are done automatically, using dhcp. The clien on the LAN just need to set to receive ip address from dhcp, and it would have internet connection with/without filtering ( depend on whether or not dansguardian is running)

If you only have one network card, it could also share internet filtering by being proxy for the LAN. I have given a special care to proxy only computer on the LAN so as it should be safe enough. But off course it is better if you put this box (act as LAN proxy) behind firewall.  

2. Dansguardian HTML log view for access denied

3. Use wine 1.0.1 version to avoid regression. The challenge is to install e-Sword using wine 1.0.1 and I have create a work around hopefully it works for you as well.


Upgrading from Jaunty:

1. Please follow the proper procedure to upgrade normal ubuntu jaunty to karmic.
2. 
64 bit:
```
sudo apt-get remove wine
sudo wget http://ubuntuce.com/repos/Ubuntu_CE/apt/sources.list.d/karmic_amd.list -O /etc/apt/sources.list.d/ubuntuce.list; sudo apt-get update && sudo apt-get install ubuntu-ce
```

32 bit:
```
sudo apt-get remove wine
sudo wget http://ubuntuce.com/repos/Ubuntu_CE/apt/sources.list.d/karmic_i386.list -O /etc/apt/sources.list.d/ubuntuce.list; sudo apt-get update && sudo apt-get install ubuntu-ce
```

Converting from normal Karmic:

64 bit:
```
wget -q http://ubuntuce.com/repos/Ubuntu_CE/apt/crosswire-launchpad-ppa.asc -O- | sudo apt-key add - && sudo wget http://ubuntuce.com/repos/Ubuntu_CE/apt/sources.list.d/karmic_amd.list -O /etc/apt/sources.list.d/ubuntuce.list; sudo apt-get update && sudo apt-get install ubuntu-ce
```

32 bit:
```
wget -q http://ubuntuce.com/repos/Ubuntu_CE/apt/crosswire-launchpad-ppa.asc -O- | sudo apt-key add - && sudo wget http://ubuntuce.com/repos/Ubuntu_CE/apt/sources.list.d/karmic_i386.list -O /etc/apt/sources.list.d/ubuntuce.list; sudo apt-get update && sudo apt-get install ubuntu-ce
```

Please help to test and feedback.

DK

---

