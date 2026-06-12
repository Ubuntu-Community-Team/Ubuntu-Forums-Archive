---
title: "Brother MFC-9840CDW Scanner On UBUNTU 16.04 and 18.04"
date: 2018-10-20
forum: Tutorials
---

### Post by hindutool2 on 2018-10-20
1) Install xsane and libusb from repositories - THIS MUST BE DONE FIRST!  (I tried for 3 hours to install with the below commands before realizing I didn't have xsane installed)
```
$sudo apt-get install xsane
```
```
$sudo apt-get install libusb-0.1-4
```
2) First get the brscan3 package from [here]("https://support.brother.com/g/s/id/linux/en/download_scn.html"), which installs the brsaneconfig3 tool and install it (_**NOTE:**_ download the correct brscan for your printer/scanner):
```
$sudo dpkg -i --force-all brscan3-0.2.13-1.amd64.deb
```
3) Then (_**critical bit**_) create these links - for some reason the 32 bit and 64 bit compatibility scripts have fallen down here (probably due to the non-standard nature of the Brother deb packages):

UBUNTU 16.04:
```
$sudo mkdir /usr/lib/sane
```
```
$sudo ln -sf /usr/lib64/libbrscandec3.so* /usr/lib
```
```
$sudo ln -sf /usr/lib64/sane/libsane-brother3.so* /usr/lib/sane
```

UBUNTU 18.04:
```
$sudo ln -sfr /usr/lib64/libbrscandec* /usr/lib/x86_64-linux-gnu
```
```
$sudo ln -sfr /usr/lib64/sane/libsane-brother* /usr/lib/x86_64-linux-gnu/sane
```

OR You can copy the files manually:

```
$sudo cp /usr/lib64/libbrscandec3.so.1.0.0 /usr/lib && cp /usr/lib64/sane/libsane-brother3.so.1.0.7 /usr/lib/sane && cp /usr/lib64/sane/libsane-brother3.so.1 /usr/lib/sane && cp /usr/lib64/sane/libsane-brother3.so /usr/lib/sane && cp /usr/lib64/libbrscandec3.so /usr/lib && cp /usr/lib64/libbrscandec3.so.1 /usr/lib
```

5) Then define the scanner on your system (note, no spaces allowed in the values assigned... and capitalisation seems important) - to find the IP you might need to go to the scanner, hit "Menu" and find the network TCP/IP settings.
```
$brsaneconfig3 -a name=SCANNER model=MFC-9840CDW ip=Your-printer-IP
```

6) This should result in a scanner definition - confirm it here (should be at the bottom of the list in a separate section, probably number 0) (Note: it creates a signature for the device in /usr/local/Brother/sane/brsanenetdevice3.cfg - you can check it here to make sure it's right...):

```
$brsaneconfig3 -q
```

7) If that doesn't do it, you might need to add your user to the "scanner" group. Check the groups you're in by running

```
$groups
```

at the command line when you're logged in. If you add yourself to the new group, you'll have to run "newgrp" or log out and in again to get the group membership to take effect.

```
$sudo adduser <user> scanner
```

8) You can run the following diagnostics to see if the scanner is recognized:

```
$brsaneconfig3 -q
```

9) If you mess up, you can remove any of them with

```
$brsaneconfig3 -r SCANNER
```

Other Resources:
[Brother Support:]("https://support.brother.com/g/s/id/linux/en/index.html?c=us_ot&lang=en&comple=on&redirect=on") 
[MFC Scanner Article:]("http://egressive.com/article/getting-a-brother-mfc-scanner-working-via-the-network-with-64-bit-ubuntu-and-linux-mint")
[Ubuntuforum threads on brother scanner:]("https://ubuntuforums.org/showthread.php?t=2390815")
[Another MFC Scanner Article:]("https://alephnull.uk/content/ubuntu-brother-printer-scanner-network-setup")
[Brother Scanner on Ubuntu 12.04:]("http://blog.axisrev.com/articles/2013/10/16/easy-install-brother-mfc-scanner-driver-ubuntu-1204-linux")
[Brother Scanner Linux Driver Depository:]("http://support.brother.com/g/s/id/linux/en/download_scn.html#brscan3")

NOTE: I have read posts where the above will work with other Brother printers. Make sure you find out which category your brother printer is in: brscan4, brscan3, brscan2, brscan, etc - The brother website section on linux drivers will be able to assist you.

PROFIT!

System: Supermicro CSE-826 X9DRi-LN4F+. 2x Intel® Xeon(R) CPU E5-2697 v2 @ 2.70GHz × 48 cores, 256 GB RAM, Ubuntu 18.04.1 LTS, Gnome 3.28.2, 96 TB RAID6, Brother MFC-9840CDW local network

---

