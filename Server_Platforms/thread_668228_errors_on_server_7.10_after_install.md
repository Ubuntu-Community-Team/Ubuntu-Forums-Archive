---
title: "errors on server 7.10 after install"
date: 2008-01-15
forum: Server Platforms
---

### Post by strip21 on 2008-01-15
I have installed the server and i have also install Gnome (yes i know)

But now when i install services or apps after the install has finnished i get 

E: acpid: subprocess post-installation script returned error exit status 1 
E: acpi-support: dependency problems - leaving unconfigured 
E: powermanagement-interface: dependency problems - leaving unconfigured 
E: ubuntu-desktop: dependency problems - leaving unconfigured 
E: netatalk: subprocess post-installation script returned error exit status 1 

What can be done as this is playing on my mind, Its also the live server thats giving me these errors

The server is 
Dell PowerEdge
ubuntu 7.10 Server (Gnome)

---

### Post by crouton on 2008-01-17
You could try something like 'sudo apt-get check' or 'sudo apt-get check -f'.  Those should check broken dependencies, the latter should force an attempt to fix it automatically.

Off the cuff it could be that the PowerEdge isn't reporting ACPI information in the expected format?

---

### Post by strip21 on 2008-01-18
I have tried the .......

**sudo apt-get check -f**

and i got

[B]reading package - done
building dependency tree
reading state info - done[/B]

when i installed something i still get the errors

---

### Post by strip21 on 2008-01-22
Is there anything else i could try to sort this out

---

### Post by az on 2008-01-22
sudo apt-get -f install


sudo apt-get install ubuntu-desktop

You may also need the desktop kernel to run all your desktop hardware:

sudo apt-get install linux-generic

---

### Post by strip21 on 2008-01-22
when i try and uninstall netatalk i get this 

**E: netatalk: subprocess post-installation script returned error exit status 1**

i have installed all the libc6 files and then downloaded the new 

**netatalk_2.0.3-7ubuntu1_i386.deb**

when i then try and install this deb package i get 
[B]
Status : Error: Dependency is not satisfiable: libc6[/B]

can someone tell me how to install netatalk or is this linked to the other problems ?

---

### Post by strip21 on 2008-01-22
Thank you for getting back to me 

when i do 

**sudo apt-get -f install**

i get

[B]Reading packages lists ..... Done
Building dependency tree
Reading state information ....Done
0 upgraded, 0 newly install, 0 to remove and 1 not upgraded.
5 not fully installed or removed.
E: Could not get lock /var/cache/apt/archives/lock – open (11 Resource temporarily unavailable)
E: Unable to lock the download directory[/B]

is this something to do with file / directory permissions?

---

### Post by strip21 on 2008-01-24
If i do 

[B]sudo apt-get install ubuntu-desktop

You may also need the desktop kernel to run all your desktop hardware:

sudo apt-get install linux-generic[/B]

As this is on a live server will this stop people from accessing the system, is there any chance that it will stop the server from working?

---

