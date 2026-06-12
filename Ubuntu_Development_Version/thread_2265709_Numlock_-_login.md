---
title: "Numlock - login"
date: 2015-02-17
forum: Ubuntu Development Version
---

### Post by Elfy on 2015-02-17
Obviously I'm using Xubuntu and some of the lightdm files are slightly different.

But has anyone else recently (that is over the last couple of days) had numlock stop working.

I did have to add this to /etc/lightdm/lightdm.conf

#greeter-setup-script=/usr/bin/numlockx on

which appears to have been commented out, uncommenting that I get nvidia prime starting and stopping at boot - until I give up and recovery mode comment it again :)

Consequently no numlock at login - until I manually set it.

---

### Post by ajgreeny on 2015-02-17
I hve been running Xubuntu for a few years and Ubuntu/Kubuntu before that and have never had numlockx installed.

My system always boots with numlock in the state it was when I shutdown last time, this being the way it is set in the **Settings-manager ->Keyboard ->Behaviour **tab.

Is this a new problem for you just with vivid, or did you see it in 14.10 or 14.04 as well?  I have a VM in VBox of vivid which I'll look at later to see if I have the same problem.

EDIT:
I've just started the VM and numlock was enabled at boot just as it was when I shutdown, and the numlock key works fine to enable/disable.

---

### Post by Elfy on 2015-02-17
> **ajgreeny said:**
> I hve been running Xubuntu for a few years and Ubuntu/Kubuntu before that and have never had numlockx installed.

My system always boots with numlock in the state it was when I shutdown last time, this being the way it is set in the **Settings-manager ->Keyboard ->Behaviour **tab.

Is this a new problem for you just with vivid, or did you see it in 14.10 or 14.04 as well?  I have a VM in VBox of vivid which I'll look at later to see if I have the same problem.

EDIT:
I've just started the VM and numlock was enabled at boot just as it was when I shutdown, and the numlock key works fine to enable/disable.

Recently - that is vivid - more or less all cycle.

Keyboard is set to remember.

Had it before this install - which took place on new hardware, so neither of those affecting.

I wonder if maybe a conflict in one of the dev Xubuntu ppa's I have installed.

---

### Post by Elfy on 2015-02-17
Just to make sure we're talking about the same thing here.

Numlock remembers perfectly ok once past login, it's numlock at login which is giving me grief atm :)

edited thread title a bit :p

---

### Post by ajgreeny on 2015-02-17
So, are you saying that when you login, numlock is not always in the same state (enabled/disabled) as it was on logging out?

---

### Post by Elfy on 2015-02-17
At the beginning of the week - I had the numockx on command in that file.

Only way for me to get numlock at login screen

There was iirc an update to lightdm-gtk-greeter

That command now appears to be commented - no numlock at login

---

### Post by Ian_Worrall on 2015-02-18
Is numlock set to ON in BIOS/UEFI?

Does greeter turn it off if so set?

---

### Post by Elfy on 2015-02-18
yep - set on in bios

greeter appears to turn it off :)

I'm now dealing with some other issues I'm managed to cause - likely I'll be forgetting about till I do a Beta 1 clean install next week.

---

### Post by Elfy on 2015-02-20
and ... 

I couldn't wait for Beta next week so did it this morning.

No numlock at lightdm login.

---

### Post by Elfy on 2015-02-20
> **Elfy said:**
> Obviously I'm using Xubuntu and some of the lightdm files are slightly different.

But has anyone else recently (that is over the last couple of days) had numlock stop working.

I did have to add this to /etc/lightdm/lightdm.conf

#greeter-setup-script=/usr/bin/numlockx on

which appears to have been commented out, uncommenting that I get nvidia prime starting and stopping at boot - until I give up and recovery mode comment it again :)

Consequently no numlock at login - until I manually set it.

and in the way of things  - do a clean install and it works - even more so when you re-add it to 

/usr/share/lightdm/lightdm.conf.d/60-lightdm-gtk-greeter.conf

instead :p

---

