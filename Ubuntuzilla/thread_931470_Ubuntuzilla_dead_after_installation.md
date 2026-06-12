---
title: "Ubuntuzilla dead after installation"
date: 2008-09-27
forum: Ubuntuzilla
---

### Post by birkopf on 2008-09-27
Hi,

I messed up a little bit my firefox. Please help.
I have Kubuntu, 64bit, Hardy 8.04

I had firefox2 and I wanted firefox3 so I launched Adept and unchecked version2 and checked box for version 3 to be installed. Than I applied. 

Firefox after clicking on icon was starting for 10min and than freezing (crashing). I had uninstalled it and installed 3.0.2 from package from mozilla webpage. It wasn't working either. During installation I had probably broken some packages but I don't know which one. I uninstalled this one. 

I had than installed ubuntuzilla and firefox3 is starting now, but when I am entering any address nothing happens and any other function is not working. 

Can you help me with finding those broken packages (probably standard ones) or pointing in right direction to solve this ?

---

### Post by nanotube on 2008-09-29
Hi,
it could be a profile problem - ff3 sometimes can't swallow an ff2 profile. so back up your current firefox profile, (it's in your ~/.mozilla directory), and start with a fresh one, see if that solves your issues.

---

### Post by birkopf on 2008-09-29
> **nanotube said:**
> Hi,
it could be a profile problem - ff3 sometimes can't swallow an ff2 profile. so back up your current firefox profile, (it's in your ~/.mozilla directory), and start with a fresh one, see if that solves your issues.
I thought it will work because when I was installing ff3 on ff2 I should backup old profile, but I didn't do that, but unfortunately it didn't help.

I noticed now, I have automatically made backup file from the day of installation as well.
 
I had similar strange problem with Firestarter. I had installed it months ago, and uninstalled (from console). Than about 2 weeks ago I wanted to check something so I installed it again, and it was behaving same way as firefox3.

I had used command ```
sudo aptitude purge firefox-3.0
```

and that's what came out from konsole

```
The following packages are BROKEN:
  ubufox
The following packages will be REMOVED:
  firefox-3.0{p}
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 3744kB will be freed.
The following packages have unmet dependencies:
  ubufox: Depends: firefox but it is not installable or
                   firefox-3.0 but it is not installable or
                   firefox-2 but it is not installable
Resolving dependencies...
The following actions will resolve these dependencies:

Install the following packages:
firefox-2 [2.0.0.17+1nobinonly-0ubuntu0.8.04.1 (hardy-updates, hardy-security)]

Score is 41

Accept this solution? [Y/n/q/?] y 
```

I decided to give it a try:

```
 The following NEW packages will be automatically installed:
  firefox-2
The following NEW packages will be installed:
  firefox-2
The following packages will be REMOVED:
  firefox-3.0{p}
0 packages upgraded, 1 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B/10.5MB of archives. After unpacking 28.7MB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
dpkg: firefox-3.0: dependency problems, but removing anyway as you request:
 ubufox depends on firefox | firefox-3.0 | firefox-2; however:
  Package firefox is not installed.
  Package firefox-3.0 is to be removed.
  Package firefox-2 is not installed.
(Reading database ... 125317 files and directories currently installed.)
Removing firefox-3.0 ...
Purging configuration files for firefox-3.0 ...
Selecting previously deselected package firefox-2.
(Reading database ... 125222 files and directories currently installed.)
Unpacking firefox-2 (from .../firefox-2_2.0.0.17+1nobinonly-0ubuntu0.8.04.1_amd64.deb) ...
Setting up firefox-2 (2.0.0.17+1nobinonly-0ubuntu0.8.04.1) ...
Please restart any running Firefoxes, or you will experience problems.

Processing triggers for libc6 ...
ldconfig deferred processing now taking place

```

After that - I have firefox2 and it's working! 

1) How to update to latest ff3 version now? 
2) And by the way - How to backup this working ff2 just in case something will go wrong again ?

---

