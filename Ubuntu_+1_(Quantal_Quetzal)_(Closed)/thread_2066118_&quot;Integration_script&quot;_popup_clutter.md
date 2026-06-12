---
title: "&quot;Integration script&quot; popup clutter"
date: 2012-10-03
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by jerrylamos on 2012-10-03
How do I stop the popup clutter from Ubuntu "Integration scripts"?  (No, I'm not going to take the bait.)

---

### Post by effenberg0x0 on 2012-10-03
> **jerrylamos said:**
> How do I stop the popup clutter from Ubuntu "Integration scripts"?  (No, I'm not going to take the bait.)

I believe this is the package:
```

sudo apt-cache show xul-ext-unity | grep -i "Source"
Source: unity-firefox-extension

```
```

sudo apt-cache showpkg **xul-ext-unity**
Package: xul-ext-unity
Versions: 
2.3.3-0ubuntu2 (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_quantal_main_binary-amd64_Packages) (/var/lib/dpkg/status)
 Description Language: 
                 File: /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_quantal_main_binary-amd64_Packages
                  MD5: e4b53d72615feaed2201e5bdbe48e5b0
 Description Language: en
                 File: /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_quantal_main_i18n_Translation-en
                  MD5: e4b53d72615feaed2201e5bdbe48e5b0


Reverse Depends: 
  libunity-webapps0:i386,xul-ext-unity 2.3-0quantal1
  unity-webapps-common,xul-ext-unity 0.3.1
  ubuntu-desktop,xul-ext-unity
  libunity-webapps0,xul-ext-unity 2.3-0quantal1
Dependencies: 
2.3.3-0ubuntu2 - firefox (2 10.0) libunity-webapps0 (2 1.8.0+r699) libufe-xidgetter0 (5 2.3.3-0ubuntu2) xul-ext-websites-integration (0 (null)) firefox (3 10.0) firefox:i386 (3 10.0) firefox (0 (null)) 
Provides: 
2.3.3-0ubuntu2 - firefox-unity 
Reverse Provides: 
```


Removing seems safe:

```
sudo apt-get remove **-s** **xul-ext-unity**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  xul-ext-unity
0 upgraded, 0 newly installed, **1 to remove** and 47 not upgraded.
Remv xul-ext-unity [2.3.3-0ubuntu2]

```

Regards,
Effenberg

---

### Post by jerrylamos on 2012-10-04
I tried removing and got this:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  xul-ext-unity
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Remv xul-ext-unity [2.3.3-0ubuntu2]

Doesn't seem to remove?  Anyway, integration script clutter still there after reboot.

Thanks for the suggestion.  Maybe I didn't know how to do it.

---

### Post by arpanaut on 2012-10-04
The "-s" flag is for simulate, a testing parameter.
To actually remove the package you must use the regular apt-get command without the flag.

---

### Post by jerrylamos on 2012-10-04
Tried it.  Removing the -s the command worked.

I still get the "integratio script" clutter even after rebooting.

I'm not the target market.  I like clean efficiency, so "all things for everyone all the time" is not my preference.

Gave up on the "integration script" and a number of other B2 "feetures".  Running my 12.04.1 2D partition right now.  Tired of the myriad B2 anklebiters.  Yes I still have a B2 updated partition to try updates on.

---

### Post by effenberg0x0 on 2012-10-04
Sorry, I forgot to remove the 's' arg after cut&paste from term to here.

Regards,
Effenberg

---

### Post by mc4man on 2012-10-04
You could also remove 
xul-ext-websites-integration

There is also a unity-chromium-extension, ect.

---

### Post by serdotlinecho on 2012-10-05
If you disable this two addons in firefox, do you still get a popup?

---

### Post by jerrylamos on 2012-10-12
Thanks, I think that worked.

---

