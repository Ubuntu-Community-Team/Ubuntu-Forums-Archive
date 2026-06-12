---
title: "OS froze...in the middle of the upgrade!"
date: 2011-04-29
forum: Server Platforms
---

### Post by 98cwitr on 2011-04-29
Running Ubuntu Server 10.10 in virtualbox and was in the middle of the installation of the upgrade to 11.04 and my host OS (Ubuntu 10.10) complete froze. 

So now I get this:

> 
init: udevtrigger main process (259) terminated with status 1
init: udevtrigger post-stiop process (263) terminated with status 1
The disk drive for / is not ready yet of not present
...


So I hit M for manual recovery and get in as root...I can see the drive and contents...which is great but what do I do now?! How would I recover this or do I just need to get my data off and reinstall the OS? Really dont want to, this is my LAMP server :/

EDIT:

Tried to run dpkg --configure -a and got
> 
dpkg: error: parsing file '/var/lib/dpkg/updates/0000' near line 0: Field name *gibberish* must be followed by a colon

EDIT:

fixed!

had to run ```
dhclient eth0
``` to get my LAN back up
deleted everything out of /var/lib/dpkg/updates/
rebooted (now could log in with my own creds)
then ran
```
sudo dpkg --configure -a && sudo apt-get update && sudo apt-get upgrade
```

All is well :)

---

