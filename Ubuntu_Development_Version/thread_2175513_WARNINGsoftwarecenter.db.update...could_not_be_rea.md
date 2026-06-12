---
title: "WARNING:softwarecenter.db.update...could not be read correctly"
date: 2013-09-19
forum: Ubuntu Development Version
---

### Post by VMC on 2013-09-19
This is an [ancient bug]("https://bugs.launchpad.net/ubuntu/+source/gnome-do/+bug/731002"), that was fixed under Natty. It just re-appeared for me using **ubuntu-gnome 13.10**. It has half a dozen duplicates attached, all from 2011.

I was installing nvidia_173, when it reared its head. Nvidia was installed ok, but the first time I've seen this warning.
 
Anyone else installing nvidia seeing this warning? 

```
WARNING:softwarecenter.db.update:
The file: '/usr/share/app-install/desktop/sonic-visualiser:x-sonicvisualiser-layer.desktop'
 could not be read correctly. The application associated with this file will not be included in the software catalog. 
**Please consider raising a bug report** for this issue with the maintainer of that application
```

---

### Post by mc4man on 2013-09-19
It actually started up in raring & likely is not going to be fixed though I don't remember seeing the warning of late.
Those 2 .desktops are of a Type=MimeType & of absoluetly no current  value if one was going to install sonic-visualizer anyway.
bug specific to s-v
[https://bugs.launchpad.net/ubuntu/+source/sonic-visualiser/+bug/1161283](https://bugs.launchpad.net/ubuntu/+source/sonic-visualiser/+bug/1161283)

At least in raring the message was more likely if sonic-v was installed though did show sometimes  if not

---

### Post by ventrical on 2013-09-19
> **VMC said:**
> This is an [ancient bug]("https://bugs.launchpad.net/ubuntu/+source/gnome-do/+bug/731002"), that was fixed under Natty. It just re-appeared for me using **ubuntu-gnome 13.10**. It has half a dozen duplicates attached, all from 2011.

I was installing nvidia_173, when it reared its head. Nvidia was installed ok, but the first time I've seen this warning.
 
Anyone else installing nvidia seeing this warning? 

```
WARNING:softwarecenter.db.update:
The file: '/usr/share/app-install/desktop/sonic-visualiser:x-sonicvisualiser-layer.desktop'
 could not be read correctly. The application associated with this file will not be included in the software catalog. 
**Please consider raising a bug report** for this issue with the maintainer of that application
```

  I get that on all my update/upgrade on 2 saucy installs on two different machines with nVidia GeForce 210/218 adapter cards...

AMD64 II Athlon X2 5000 and an Intel machine.

---

### Post by mc4man on 2013-09-19
If it really bugs you you could try fixing the 2 .desktops - 

```
desktop-file-validate /usr/share/app-install/desktop/sonic-visualiser:x-sonicvisualiser.desktop
```

or just go ahead & delete them..

---

### Post by ventrical on 2013-09-19
> **mc4man said:**
> If it really bugs you you could try fixing the 2 .desktops - 

desktop-file-validate /usr/share/app-install/desktop/sonic-visualiser:x-sonicvisualiser.desktop

or just go ahead & delete them..

Thanks.

No .. they don't bug me. I am just contributing to the OPs original report. I'm used to them  by now. :)

Affects SandyBridge also.

```

Updating software catalog...this may take a moment.
INFO:softwarecenter.db.pkginfo_impl.aptcache:aptcache.open()
WARNING:softwarecenter.db.update:The file: '/usr/share/app-install/desktop/sonic-visualiser:x-sonicvisualiser.desktop' could not be read correctly. The application associated with this file will not be included in the software catalog. Please consider raising a bug report for this issue with the maintainer of that application

```

---

### Post by ventrical on 2013-09-19
> **mc4man said:**
> If it really bugs you you could try fixing the 2 .desktops - 

desktop-file-validate /usr/share/app-install/desktop/sonic-visualiser:x-sonicvisualiser.desktop

or just go ahead & delete them..

```

ventrical@ventrical-MS-7798:~$ desktop-file-validate /usr/share/app-install/desktop/sonic-visualiser-sonicvisualiser.desktop
/usr/share/app-install/desktop/sonic-visualiser-sonicvisualiser.desktop: file does not exist
ventrical@ventrical-MS-7798:~$ 

```
MSi-B75MA-P45/SandyBridge

---

### Post by VMC on 2013-09-19
Just the fact that it pops up with a Warning and suggests creating a bug report is reason enough for it to be fixed.
Some unsuspecting soul comes along and creates another duplicate bug report. I guess that's why we have 1/2 a dozen already.

Its doesn't bother me either.

---

### Post by mc4man on 2013-09-19
> **VMC said:**
> Just the fact that it pops up with a Warning and suggests creating a bug report is reason enough for it to be fixed.
Some unsuspecting soul comes along and creates another duplicate bug report. I guess that's why we have 1/2 a dozen already.

Its doesn't bother me either.
Months later it seems no one is interested in fixing the package
(i'd remove those 2 .desktops & fix the actual application .desktop


ventrical - it seems this forum **can** add a simile for : if not in a code box

---

### Post by VMC on 2013-09-19
> **mc4man said:**
> Months later it seems no one is interested in fixing the package
(i'd remove those 2 .desktops & fix the actual application .desktop


ventrical - it seems this forum **can** add a simile for : if not in a code box

I got the smilie also when I messed up a code tag. Then on correct tags it was gone.

---

### Post by ventrical on 2013-09-20
> **mc4man said:**
> Months later it seems no one is interested in fixing the package
(i'd remove those 2 .desktops & fix the actual application .desktop



How?  Remove ubuntu-desktop? Or do fresh install??
Could you give me a proceedural list please.

Thanks ! :)

---

### Post by mc4man on 2013-09-20
> **ventrical said:**
> How?  Remove ubuntu-desktop? Or do fresh install??
Could you give me a proceedural list please.

Thanks ! :)
ubuntu-desktop isn't  involved here.

If the 2 .desktop files can't be read then - 
either try to make them readable & or of any use
or
just go to /usr/share/app-install & delete the 2 .desktop files in question

(to restore them if need be just re-install the "app-install-data" package

---

