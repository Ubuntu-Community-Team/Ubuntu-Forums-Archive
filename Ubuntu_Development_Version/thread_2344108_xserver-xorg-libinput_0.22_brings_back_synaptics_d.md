---
title: "xserver-xorg-libinput 0.22 brings back synaptics driver"
date: 2016-11-22
forum: Ubuntu Development Version
---

### Post by fthx on 2016-11-22
Hi,

FYI, I installed (from proposed repos.) xserver-xorg-libinput 0.22, and xinput list-props shows that libinput is not loaded for my touchpad. Synaptics is shown instead.
How could I see an eventual bug ? I did not find any bug in Gnome logs.

---

### Post by mc4man on 2016-11-22
> **fthx said:**
> Hi,

FYI, I installed (from proposed repos.) 
How could I see an eventual bug ? I did not find any bug in Gnome logs.
When that package moves to main repo & same thing happens.

The only current bug I see is that both are currently installed, xserver-xorg-libinput takes precedence & for ubuntu session users it is crap. (no user facing options in system settings ..

---

### Post by fthx on 2016-11-23
ok, it's in main now.
A simple way to solve the issue is to remove xserver-xorg-input-synaptics (hope it's the real package name !), and then libinput does the job.
Odd behaviour, though.

---

### Post by mc4man on 2016-11-24
> **fthx said:**
> ok, it's in main now.
A simple way to solve the issue is to remove xserver-xorg-input-synaptics (hope it's the real package name !), and then libinput does the job.
Odd behaviour, though.
Not too sure it's odd, seems to be where it should be atm.
libinput 0.19 would take preference over synaptics, 0.22 doesn't. That's better for gnome & ubuntu sessions.

On the current ubuntu-gnome image only libinput package is included, I guess in works ok in a gnome session.
On the current ubuntu image both packages are provided & only synaptics works well in an ubuntu session so it should take precedence.

---

### Post by fthx on 2016-11-24
And, e.g., if you have Unity and Gnome ?
Anyway, IMHO, the changelog should contain this new behaviour.

---

### Post by mc4man on 2016-11-24
> **fthx said:**
> And, e.g., if you have Unity and Gnome ?
Anyway, IMHO, the changelog should contain this new behaviour.

Well in an ubuntu session with libinput atm in system settings > mouse & touchpad there would be pretty much no touchpad settings & no way to disable the touchpad. So  synaptics is currently best. Can you control & modify touchpad settings in a gnome session with the synaptics driver? If not then for a gnome session libinput is best. If they can get a ubuntu session to interface correctly with libinput then the synaptics package could be dropped

(- personal opinion is if one wants ubuntu/unity then use that (Ubuntu image), if they want gnome-shell then use that (Ubuntu-gnome image.

---

### Post by fthx on 2016-11-24
synaptics driver does not allow any touchpad setting in Gnome control center.
(As a side note, libinput (default since Yakkety ? Xenial ?) causes less precise touchpad use and, e.g., I can't succeed to manage to set three fingers tap to do a middle-click, including through terminal commands.)

---

