---
title: "problem in my monitor"
date: 2011-12-15
forum: Sudan Team
---

### Post by GeoLinux on 2011-12-15
Al salam alaykom
I have a problem with my monitor as follows:
when I decided to install Ubuntu first time the monitor displayed:
"out of range" and then became black;
I searched the internet and used these parameters in the startup of the installer:
xdriver=vesa nomodeset
it works to me and I installed ubuntu (version 11.04) but the problem that it works using the vesa driver (so no 3d acceleration and therefore no unity) and the other problem is that the maximum resolution was 640x480. Again searched this forum and other websites and also used the manual pages for editing xorg.conf file and I got either black screen or unstable screen with some invisible windows.
I tried so hard with xorg.conf using vesa and my intel as a driver but all have the same problem.
also I tried to use system>> preferences>>monitors and didn't find other resolution available than 640x480, but after two months of using ubuntu I found others available:
800x600 and 1024x768 and don't know how it happened,but my problem is that I still using vesa but not my driver intel 82865G integrated graphics controller with graphics memory 96Mb(from the driver info window in windows).
Can one help me to use my intel driver?
thank you all.

---

### Post by suspect x on 2012-05-02
I don't know if am a help but try
```
sudo apt-get update
```
and then
```
sudo apt-get upgrade
```
to upgrade all your drivers and packages ,
BTW we seem to have the same motherboard !
[link]http://www.asrock.com/MB/overview.asp?Model=775i65G[/link]

---

### Post by yasir.elsharif on 2012-05-06
Hello Mr [GeoLinux]("http://ubuntuforums.org/member.php?u=1511930"), 
you can go to:[U]
[/U][https://launchpad.net/~xorg-edgers/+archive/ppa]("https://launchpad.net/%7Exorg-edgers/+archive/ppa")
and add their PPA to your sources and give it a try, how to is included.
I wish you luck
Cheers 
Yasir

---

### Post by GeoLinux on 2013-01-21
thanks all for responding.
after months of searching I found this solution:
1- burned the distro (12.04)on flash memory using "universal usb installer".
2- reboot and select live option BUT don't press enter, rather you have to press "tab" to edit boot parameters by adding:
          xdriver=vesa nomodeset 
    and press enter
3- you will get an "out of range message" then:
       press alt+ctrl+F2 (or F3 or...or F6)
4- you will get a terminal-like screen then write the command:
      sudo nano /etc/X11/xorg.conf

5- add these lines (the numbers value are differ from monitor to
    other, you can obtain them from the manual comes with   
    monitor):

Section "Device"
    Identifier    "Device0"
    Driver        "vesa"
    Screen        0
EndSection

Section "Monitor"
    Identifier    "Monitor0"
    HorizSync     30-56
    VertRefresh   50-120
EndSection

Section "Screen"
    Identifier    "Screen0"
    Monitor       "Monitor0"
    Device        "Device0"
EndSection

6- save and exit by pressing:
      ctrl+o    to save
      ctrl+x    to exit

7- reboot
8- again select live option and add the parameters:
    xdriver=vesa  nomodeset
9- enjoy it!

---

