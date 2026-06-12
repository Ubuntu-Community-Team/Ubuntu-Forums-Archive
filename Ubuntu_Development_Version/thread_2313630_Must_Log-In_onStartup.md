---
title: "Must Log-In onStartup"
date: 2016-02-14
forum: Ubuntu Development Version
---

### Post by Clifford_Sarokoff on 2016-02-14
I did a clean install of Ubuntu 16.04.  I checked the box to have auto-logon.  After the install I was asked for password to log on.  I went to User and changed the setting to unlock. I still require the password.  Is it a bug or am I doing something wrong?
CliffordS

---

### Post by kansasnoob on 2016-02-18
> **Clifford_Sarokoff said:**
> I did a clean install of Ubuntu 16.04.  I checked the box to have auto-logon.  After the install I was asked for password to log on.  I went to User and changed the setting to unlock. I still require the password.  Is it a bug or am I doing something wrong?
CliffordS

I'm seeing the same behavior with a freshly installed Ubuntu GNOME 20160218 amd64. I haven't found a bug report yet but I'm still looking.

---

### Post by kansasnoob on 2016-02-18
I filed a bug report against gdm3:

[https://bugs.launchpad.net/ubuntu/+source/gdm3/+bug/1547297](https://bugs.launchpad.net/ubuntu/+source/gdm3/+bug/1547297)

But AFAIK Ubuntu uses lightdm. I even installed Ubuntu 20160218 and auto login worked OK there so apparently ATM only Ubuntu GNOME is affected?????

---

### Post by sammiev on 2016-02-18
> **kansasnoob said:**
> I filed a bug report against gdm3:

[https://bugs.launchpad.net/ubuntu/+source/gdm3/+bug/1547297](https://bugs.launchpad.net/ubuntu/+source/gdm3/+bug/1547297)

But AFAIK Ubuntu uses lightdm. I even installed Ubuntu 20160218 and auto login worked OK there so apparently ATM only Ubuntu GNOME is affected?????

Tried it on gnome 16.04 and added myself to your bug report.

---

### Post by kansasnoob on 2016-02-18
> **sammiev said:**
> Tried it on gnome 16.04 and added myself to your bug report.

Thanks.

---

### Post by MikeMecanic on 2016-02-18
Works fine here Ubuntu 20160216.  For Gnome, I stop trying this option a long, long time ago.

---

### Post by claudiuchc on 2016-05-14
> **MikeMecanic said:**
> Works fine here Ubuntu 20160216.  For Gnome, I stop trying this option a long, long time ago.
 Yeah it's from Ubuntu Gnome 13 that i've been trying every version, making all updates and every time hoping the issue will be fixed, but seems even after 3 years issue is still there... who will fix the unfixable?

---

### Post by mc4man on 2016-05-14
> **claudiuchc said:**
> Yeah it's from Ubuntu Gnome 13 that i've been trying every version, making all updates and every time hoping the issue will be fixed, but seems even after 3 years issue is still there... who will fix the unfixable?
It's shown as fixed in Ubuntu-Gnome 16.04
[https://bugs.launchpad.net/ubuntu/+source/gdm3/+bug/1547297](https://bugs.launchpad.net/ubuntu/+source/gdm3/+bug/1547297)
&
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1571415](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1571415)

So this thread is likely over & done, if so should be closed.

---

### Post by QDR06VV9 on 2016-05-14
As 16.04 development is over.
Thread Closed.
If you need to start a help thread related to your problem

---

