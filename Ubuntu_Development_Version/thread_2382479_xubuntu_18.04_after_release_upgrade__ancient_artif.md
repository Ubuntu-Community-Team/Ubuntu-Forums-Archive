---
title: "xubuntu 18.04 after release upgrade : ancient artifacts on startup"
date: 2018-01-13
forum: Ubuntu Development Version
---

### Post by holiday2 on 2018-01-13
After release upgrade to 18.04, this is what I see before the first gui splash or on logging in via ssh. 

I cannot login through the gui. I have to open a teminal (altCtlF1), login as a different user than the default, and then issue the startx command. 

I could re-install and takeover the whole disk but I'd rather find out what's going on and fix it. Any ideas?

```
Welcome to Ubuntu Bionic Beaver (development branch) (GNU/Linux 4.13.0-25-generic x86_64)
 
 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Supp,,ort:        https://ubuntu.com/advantage

 * Ubuntu Updates for the Meltdown / Spectre Vulnerabilities
   - https://ubu.one/uMelt

0 packages can be updated.
0 updates are security updates.


You have packages from the Hardware Enablement Stack (HWE) installed that
are going out of support on 2016-08-04.
        
To upgrade to a supported (or longer-supported) configuration:

* Upgrade from Ubuntu 14.04 LTS to Ubuntu 16.04 LTS by running:
sudo do-release-upgrade 

OR

* Switch to the current security-supported stack by running:
sudo apt-get install 

and reboot your system.
Last login: Sat Jan 13 15:20:24 2018 from 192.168.0.140
stephen@vaio:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu Bionic Beaver (development branch)
Release:    18.04
Codename:    bionic

```

---

