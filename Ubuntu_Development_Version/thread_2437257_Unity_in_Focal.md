---
title: "Unity in Focal"
date: 2020-02-20
forum: Ubuntu Development Version
---

### Post by Yahoé on 2020-02-20
What is the better way to install Unity in Focal, installing unity-session and/or ubuntu-unity-desktop, else?
Do we still need to add the Ubuntu-Unity-19.04-Testing PPA?

---

### Post by deadflowr on 2020-02-20
>  What is the better way to install Unity in Focal, installing unity-session and/or ubuntu-unity-desktop, else?

I'd use the meta package (ubuntu-unity-desktop package)
> Do we still need to add the Ubuntu-Unity-19.04-Testing PPA?

Seeing that the ppa hasn't had any new updates for several months now and
there are no focal archives for it, I'd say don't add it.

---

### Post by mc4man on 2020-02-21
Decent way is to install synaptic and use it to install ubuntu-unity-desktop ( which would install synaptic anyway 
This gives you a easy readable history of everything installed plus  after install highlight ubuntu-unity-desktop > right click > check out all the recommended packages that where installed (or already installed..

Some may not be of value to you and can be removed. Here some of the new recommends are no use to me and I remove like xterm, geary, gdebi along with some others I've no use for.
Also in synaptic search unity > scroll down to the lens & scopes, there may be some you want inc. music, video & photos lens  which aren't installed by the meta package & any scopes of interest
(I find the manpages scope quite useful..

If on a laptop xserver-xorg-input-synaptics is useful  ( may disappear someday, never remove xserver-xorg-input-libinput  package..

---

### Post by Chanath on 2020-02-21
> **mc4man said:**
> Also in synaptic search unity > scroll down to the lens & scopes, there may be some you want inc. music, video & photos lens  which aren't installed by the meta package & any scopes of interest

Sometimes, lens video shows what's in the /home/Video, but neither the lenses music or photos show anything. Do you get those lenses working in your system, and how?

---

### Post by mc4man on 2020-02-21
> **Chanath said:**
> Sometimes, lens video shows what's in the /home/Video, but neither the lenses music or photos show anything. Do you get those lenses working in your system, and how?
Videos should show added after a new login.
Music & Photos aren't proactive so they need specific app to add to the db. In the case of photos it's shotwell, for music it's rhythmbox. 
Less than ideal but that's how they were designed way back when, dev stopped on them quite some time ago.

In the case of music RB just needs to be opened, for photos shotwell has to be told to import the 1st. time, then just opened thereafter if set to watch in it's preferences.
Neither app monitors in the background so they do have to be opened implicitly, usually don't show in lens till a fresh login..

---

### Post by Yahoé on 2020-02-21
Thank you deadflowr. :-)

---

### Post by Yahoé on 2020-02-21
> **mc4man said:**
> Decent way is to install synaptic and use it to install ubuntu-unity-desktop ( which would install synaptic anyway 
This gives you a easy readable history of everything installed plus  after install highlight ubuntu-unity-desktop > right click > check out all the recommended packages that where installed (or already installed..

Some may not be of value to you and can be removed. Here some of the new recommends are no use to me and I remove like xterm, geary, gdebi along with some others I've no use for.
Also in synaptic search unity > scroll down to the lens & scopes, there may be some you want inc. music, video & photos lens  which aren't installed by the meta package & any scopes of interest
(I find the manpages scope quite useful..

If on a laptop xserver-xorg-input-synaptics is useful  ( may disappear someday, never remove xserver-xorg-input-libinput  package..

Thank you mc3/4man, that’s what I was looking for. :-)

---

### Post by Chanath on 2020-02-22
> **mc4man said:**
> 

Its alright that they don't show up in the dash. Is there a way to rid those three; music, photos and videos icons (lens) appearing in the dash?

---

### Post by deadflowr on 2020-03-12
> **deadflowr said:**
> 

Seeing that the ppa hasn't had any new updates for several months now and
there are no focal archives for it, I'd say don't add it.
There have been new uploads to the ppa since i posted.
Whether or not to add it is ultimately a user choice.

---

### Post by jefflpearsonii on 2020-03-13
I had to add the ppa for Unity Tweak Tool to work.  The HUD works now also :-)

---

