---
title: "unity8 apps install"
date: 2016-09-06
forum: Ubuntu Development Version
---

### Post by MRubunt on 2016-09-06
Vidéo unity 8 apps install : 
[https://www.youtube.com/watch?v=vIgCfourJfY](https://www.youtube.com/watch?v=vIgCfourJfY)

---

### Post by ventrical on 2016-09-06
I have debian desktop apps working great but to install apps from the apps store I just get the install button doing nothing. How did you install your apps?

Regards..

---

### Post by mc4man on 2016-09-06
Supposedly something like - 
sudo apt install packagekit-plugin-click

---

### Post by ventrical on 2016-09-06
> **mc4man said:**
> Supposedly something like - 
sudo apt install packagekit-plugin-click

Tried that ... got:

```

ventrical@ventrical-System-Product-Name:~$ sudo apt-get install packagekit-plugin-click
[sudo] password for ventrical: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package packagekit-plugin-click is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'packagekit-plugin-click' has no installation candidate
ventrical@ventrical-System-Product-Name:~$ 


```

so it must be from ppa which I do not have installed (or proposed).

I'll try on install with ppa.

But here is bug reported by apport on my machine:  [URL="https://bugs.launchpad.net/ubuntu/+source/ubuntu-system-settings-online-accounts/+bug/1620759"]https://bugs.launchpad.net/ubuntu/+source/ubuntu-system-settings-online-accounts/+bug/1620759


[/URL]

---

### Post by ventrical on 2016-09-06
Tried on an  install with ppa and proposed.. still get deferred.

```

ventrical@ventrical-MS-7850:~$ sudo apt-get install packagekit-plugin-click
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package packagekit-plugin-click is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'packagekit-plugin-click' has no installation candidate

```

---

### Post by ventrical on 2016-09-06
I already have it install on one install with xenial set. I don't think that is the bug .. I'll get back..

---

### Post by ventrical on 2016-09-06
> **mc4man said:**
> Supposedly something like - 
sudo apt install packagekit-plugin-click

locks right up..

---

### Post by mc4man on 2016-09-06
That package install is what's on the comment on the youtube page, no other context provided. 
(- what this has to do with 16.10 is debatable as package is not available & the usability of these packages on the Desktop  is certainly suspect

---

### Post by ventrical on 2016-09-06
> **mc4man said:**
> That package install is what's on the comment on the youtube page, no other context provided. 
(- what this has to do with 16.10 is debatable as package is not available & the usability of these packages on the Desktop  is certainly suspect

Agreed.  I want to stay away from the ppa(s) and just wait until those packages trickle down to the yakkety repos.  That package is certainly not available on yakkety and the OP didn't gives us any information really.

Regards..

---

### Post by mc4man on 2016-09-06
> **ventrical said:**
> Agreed.  I want to stay away from the ppa(s) and just wait until those packages trickle down to the yakkety repos.  That package is certainly not available on yakkety and the OP didn't gives us any information really.

Regards..
I don't think that package will  be on 16.10 from anywhere

---

