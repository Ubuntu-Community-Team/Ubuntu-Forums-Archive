---
title: "Unverified tor package installation"
date: 2010-03-27
forum: Security
---

### Post by hihihi100 on 2010-03-27
Please take a looka at:
```
hihihi100@hihihi100-laptop:~$  sudo apt-get install tor tor-geoipdb
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libreadline5 socat
Suggested packages:
  mixmaster mixminion anon-proxy
The following NEW packages will be installed:
  libreadline5 socat tor tor-geoipdb
0 upgraded, 4 newly installed, 0 to remove and 3 not upgraded.
Need to get 2,629kB of archives.
After this operation, 6,648kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  tor tor-geoipdb
_Install these packages without verification [y/N]?_

```

How dangerous is it to download those packages? I got the information from

[https://help.ubuntu.com/community/Tor?action=show&redirect=TOR](https://help.ubuntu.com/community/Tor?action=show&redirect=TOR)

Regards

---

### Post by mkvnmtr on 2010-03-27
Looks like you forgot to download the key. Go back to the tor page and read the instructions for Ubuntu and you will find where you can cut and paste into the terminal the command to download the key. You can probably choose yes nad finish the installation but you will get that error every time you update if you do not get the key.

---

### Post by hihihi100 on 2010-03-27
k, I redid all the process.. thx

---

