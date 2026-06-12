---
title: "Wifi woes script."
date: 2006-07-14
forum: The Cafe
---

### Post by Adamant1988 on 2006-07-14
This is an app made my LinuxNIT for Elive but he's pointed me to it when I told him about all the wifi problems people are having in Ubuntu.  Hopefully this could help some...

[http://www.elivedev.org/linuxnit/files/index.php?dir=&file=wifi-wiz-v2-2.deb](http://www.elivedev.org/linuxnit/files/index.php?dir=&file=wifi-wiz-v2-2.deb)

It hasn't been thoroughly tested for Ubuntu systems but LinuxNIT says that it *should* work fine... any feedback would be great... I'll make sure he sees this thread to watch how people are doing with the ap.

---

### Post by slimdog360 on 2006-07-14
what does it do?

---

### Post by Adamant1988 on 2006-07-14
it's supposed to automatically configure all of the settings and such for connecting to wifi networks.. but I could ask him for a more specific definition

[quote=LinuxNIT]<LinuxNIT> ;)
<LinuxNIT>  Wifi-Wiz is a GUI to assist Linux users in finding and connection to wireless networks. It scans for networks, allows you to set the essid wep key channel mode. displayes current connection status
<LinuxNIT> allows you to connect with dhcp or static ip
<LinuxNIT> can remember saved networks and pull up the information if a saved network is found during the scan
<LinuxNIT> hows that?[/quote]

---

### Post by GuitarHero on 2006-07-14
downloaded it and it says dependency is not satisfiable: dhcp-client

---

### Post by Adamant1988 on 2006-07-14
he uploaded a new one that should fix your dependancy issue.

---

### Post by GuitarHero on 2006-07-14
same link?

---

### Post by Adamant1988 on 2006-07-14
yep same link.. he just replaced it

---

### Post by GuitarHero on 2006-07-14
just tried it and it gave me the same error.....

---

### Post by Adamant1988 on 2006-07-14
hrmm well I linked him to this thread
maybe he'll figure out what's going on =\

---

### Post by David B. on 2006-07-14
hey this is LInuxNIT... do you have pump installed? it needs either pump or dhclient(dhcp-client)
i can install on my system with the .deb with pump installed and no 
dhcp-client
i appreciate your feedback as i would like this to work on as many systems as possilbe
thanks
David

---

### Post by David B. on 2006-07-14
oh yeah if you could paste the out put from dpkg -i wifi-wiz-v2-2.deb that would be nice :D

---

### Post by ubuntu_demon on 2006-07-14
Here's a link to the directory so you can see when a new version is up :
[http://www.elivedev.org/linuxnit/files/index.php](http://www.elivedev.org/linuxnit/files/index.php)

---

### Post by Adamant1988 on 2006-07-14
the dependancy problem is that it needs either pump or Dhcp-client installed... I guess installing PUMP is the best option to get it working.

---

### Post by David B. on 2006-07-14
i have made a new .deb that looks for dhcp3-client or pump. dhcp3-client should be installed on ubuntu already. the .deb worked on ubuntu livecd.
Feel free to try it. if the deb does not work for you there is the .tar.gz file with a install script.
Hope you enjoy the app.
David(linuxNIT)

---

### Post by GuitarHero on 2006-07-15
i had dhcp-client, guess ill try pump

---

### Post by Adamant1988 on 2006-07-15
are you using gdebi to install this deb?

---

### Post by GuitarHero on 2006-07-16
yes i am using gdebi.  where do i get PUMP.  I have DHCP-client, but its saying dependency is not satisfiable.  PUMP is not in the pckg manager.

---

### Post by Adamant1988 on 2006-07-17
I found pump inside of synaptic (just search Pump)

---

### Post by David B. on 2006-07-17
well man i dunno this is the first .deb i have made. You could use the install script from the tar.gz file. I have a small chat room on freenode #Wifi-wiz. As long as you have a program called dhclient (command line name) or pump (command line name) it will work. The install script would probably be better. Like i said im new to makeing .debs.

---

### Post by Iandefor on 2006-07-17
Installed pump, and wifi-wiz installed without complaint. There's an executable called wifi-wiz inside /usr/bin, which returns this when I run it:
```
Traceback (most recent call last):
  File "/usr/bin/wifi-wiz", line 279, in ?
    inFile = open ("/etc/wifi-wiz/netlist.txt").readlines()
IOError: [Errno 13] Permission denied: '/etc/wifi-wiz/netlist.txt'
``` Running with sudo returns:```
['eth0  ']
Traceback (most recent call last):
  File "/usr/bin/wifi-wiz", line 394, in ?
    update()
  File "/usr/bin/wifi-wiz", line 163, in update
    return update2()
  File "/usr/bin/wifi-wiz", line 178, in update2
    curentipstat.set('Local IP:    ' +line[line.index('addr:')+5:line.index('  B')])
ValueError: substring not found
```

EDIT: Woops! Missed that the wireless card wasn't plugged in. Now it seems to work, but in order to be sure, I need a wireless network :rolleyes:.

---

### Post by Adamant1988 on 2006-07-17
I also found that error when I ran sudo, but I don't have a wireless card and I attributed it to that...

---

### Post by ubuntu_demon on 2006-07-17
Here's a related thread :

WirelessClient specification - users feedback request
[http://www.ubuntuforums.org/showthread.php?t=200701](http://www.ubuntuforums.org/showthread.php?t=200701)

---

