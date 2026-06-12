---
title: "Software updates"
date: 2017-12-11
forum: Ubuntu Development Version
---

### Post by cecilpierce on 2017-12-11
Doesn't show details, any reason or fix ?

---

### Post by ajgreeny on 2017-12-11
Is this a newly installed and as yet not updated system?

Try updating first time with terminal and see if that solves this as it did, if I remember correctly, in 16.04.
I have not seen this on my 18.04 installs but I always use terminal or synaptic which have both always been faultless.

---

### Post by cecilpierce on 2017-12-11
This is 18.04, terminal and Synaptic show details but this is automatic updates that pop up every few days.

---

### Post by flocculant on 2017-12-12
There was a bug for that on launchpad - iirc it was marked fix released.

Report it again - list the bug here - I can confirm that it happens. 

What I see is that you can see detail of the package - until you tell it to install - is that what you see?

---

### Post by flocculant on 2017-12-16
someone else reported it [lpbug]1738517[/lpbug]

---

### Post by Smask on 2017-12-17
Here's the thread I started during the Yakkety development phase:

[https://ubuntuforums.org/showthread.php?t=2334954](https://ubuntuforums.org/showthread.php?t=2334954)

---

### Post by flocculant on 2017-12-18
> **Smask said:**
> Here's the thread I started during the Yakkety development phase:

[https://ubuntuforums.org/showthread.php?t=2334954](https://ubuntuforums.org/showthread.php?t=2334954)

Yea - vaguely remember that thread, doesn't do anything more than say use something else though ;)

Of course you won't see it if you're in a terminal using apt/apt-get - the bug's elsewhere.

---

### Post by cecilpierce on 2017-12-18
Still the same, you can see text rushing by in the black line but can't read it.

---

### Post by mc4man on 2017-12-18
Works fine here, recent image, no modifications, screen

---

### Post by cecilpierce on 2017-12-18
> **mc4man said:**
> Works fine here, recent image, no modifications, screen

Very interesting. Wonder why mine is broke ???
It bugs me not to see whats going on !

---

### Post by mc4man on 2017-12-18
> **cecilpierce said:**
> Very interesting. Wonder why mine is broke ???
It bugs me not to see whats going on !
Best approach would be to get todays image & do a fresh install, then see how it behaves.
If it's ok  & then subsequently breaks you may be in a better position to think about your recent activities.
If it's broken from the get go then that's more useful to question of why me not you, ect.

---

### Post by cecilpierce on 2017-12-18
I wonder if its wayland making it do that ?

---

### Post by mc4man on 2017-12-18
> **cecilpierce said:**
> I wonder if its wayland making it do that ?

Wonder no more, absolutely a wayland issue. (I tend to switch to xorg & forget that there is a wayland session.

---

### Post by cecilpierce on 2017-12-18
> **mc4man said:**
> Wonder no more, absolutely a wayland issue. (I tend to switch to xorg & forget that there is a wayland session.

Thanks, I don't know why I didn't check that before, I'm on x11 now, see on the next automatic update. Thanks

---

### Post by flocculant on 2017-12-19
> **cecilpierce said:**
> I wonder if its wayland making it do that ?

> **mc4man said:**
> Wonder no more, absolutely a wayland issue. (I tend to switch to xorg & forget that there is a wayland session.

> **cecilpierce said:**
> Thanks, I don't know why I didn't check that before, I'm on x11 now, see on the next automatic update. Thanks

I see this in Xubuntu - no wayland here.

---

### Post by slickymaster on 2017-12-19
Just spinned today's image and Software Updater is working as expected

[ATTACH=CONFIG]277877[/ATTACH]

---

### Post by Chanath on 2017-12-19
> **slickymaster said:**
> Just spinned today's image and Software Updater is working as expected

[ATTACH=CONFIG]277877[/ATTACH]

It doesn't work on Ubuntu on Wayland. Xubuntu is a different matter.

---

### Post by slickymaster on 2017-12-19
> **Chanath said:**
> It doesn't work on Ubuntu on Wayland. Xubuntu is a different matter.

I'm aware of that. See [https://ubuntuforums.org/showthread.php?t=2379950&p=13722309&viewfull=1#post13722309](https://ubuntuforums.org/showthread.php?t=2379950&p=13722309&viewfull=1#post13722309), please

---

### Post by cecilpierce on 2017-12-19
x11 still the same ?
I'm going to try a fresh install and see if it changes, this bugs me !

---

### Post by cecilpierce on 2017-12-19
Todays iso same thing. 

Tried Budgie-Zesty, worked OK, Hmmm!

---

### Post by cecilpierce on 2017-12-20
Reinstalled update-manager, seems to work ok now !

Back to NO descriptions !!!

---

