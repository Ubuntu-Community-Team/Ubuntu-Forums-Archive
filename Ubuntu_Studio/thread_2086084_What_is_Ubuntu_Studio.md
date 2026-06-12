---
title: "What is Ubuntu Studio ?"
date: 2012-11-19
forum: Ubuntu Studio
---

### Post by axiom301 on 2012-11-19
I am a beginner and get confused.
I want to make it clear the basic relationships between U.S. and those words bellow.


**gnome** : a name of widespread Desktop system for linux, some parts are used in U.S.
CORRECT ?

**Kfce** : a name of light Desktop for linux, 'ubuntu studio session' is another version of Kfce.
CORRECT ?

**Xubuntu** : is one of ubuntu derivative, a core system of U.S.
CORRECT ?

**KDE** : is a community provides KDE Desktop, not so much related to U.S.
CORRECT ?

so,
**Ubuntu Studio** : is a mixture of Xubuntu, Kfce, APPs for AV and a bit of gnome utilities. 
CORRECT ?


Some APPs designed for gnome or KDE are not working fully on my U.S.
Although there are no APP 'for Ubuntu Studio'
Where shoud I go ?



thank you.
Do not say my English is NOT CORRECT !

---

### Post by Bucky Ball on 2012-11-19
Welcome.

[QUOTE=Axiom301]**Kfce** : a name of light Desktop for linux, 'ubuntu studio session' is another version of Kfce.
CORRECT ?[/QUOTE]

Incorrect. There is no such desktop environment as kfce. Xubuntu and Ubuntu Studio use _**Xfce**_ desktop environment. You can try that by installing xfce4, log out, choose from the 'Sessions' pop up.

KDE is used by Kubuntu and is NOT lightweight.

You could see it this way; Ubuntu is a base install. You've got the kernel. All the flavours use the basic Ubuntu kernel. You then add a desktop environment to this. If you want Kubuntu, that will add KDE and all appropriate software/apps related to Kubuntu. Ubuntu Studio will use xfce4 desktop environment, as will Xubuntu, and drag in all apps appropriate to US, many specific to audio/visual work.

With this in mind, an example might be:  if you are using Ubuntu straight (Unity, which you missed) and want to use Xubuntu apps, just install them! They are all there in the repos. If you want the whole shebang, install xubuntu-desktop and that will drag in xfce4 and ALL apps associated. This will leave you will all the Ubuntu default apps AND the Xubuntu defaults in your menus. Can get messy. ;)

Make the distinction that there are three components to this: the kernel, the desktop environment and the default apps associated with a particular flavour. 

Lubuntu (lxde) and Xubuntu are the lightest of the Ubuntu bunch and your list refers to four desktop environments followed by a question about Ubuntu Studio, a Ubuntu flavour that uses xfce as its DE. 

As for your problem with the apps not working correctly, KDE apps can be problematic in anything but KDE, but not always! In Studio, you should find a toggle setting somewhere that lets you 'Start Gnome Services at boot' or something like that. Try that.

Hope that helps.

---

### Post by offgridguy on 2012-11-19
Thank you Bucky Ball for this concise explanation.

---

### Post by Bucky Ball on 2012-11-19
> **offgridguy said:**
> Thank you Bucky Ball for this concise explanation.

Pleasure. ;)

I omitted that what makes this very clear is a minimal install. With the mini.iso, you install everything manually after the base system is in. So, it installs the base kernel, then you install the desktop environment and any software you want to use. A completely custom system and more or less your very own Ubuntu flavour!

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

You can also select from a bunch of default systems to install.

---

### Post by axiom301 on 2012-11-20
Thank you Bucky Ball so much, for quick and comprehensible lecture !


> Incorrect. There is no such desktop environment as kfce. Xubuntu and Ubuntu Studio use _**Xfce**_ desktop environment. You can try that by installing xfce4, log out, choose from the 'Sessions' pop up.Yes, I made mistake...:(


> I omitted that what makes this very clear is a minimal install. With the  mini.iso, you install everything manually after the base system is in.  So, it installs the base kernel, then you install the desktop  environment and any software you want to use. A completely custom system  and more or less your very own Ubuntu flavour!

[https://help.ubuntu.com/community/In...tion/MinimalCD]("https://help.ubuntu.com/community/Installation/MinimalCD")Absolutely yes !:guitar:

I decided to learn more about linux not only for ubuntu studio.
Next weekend, I will try to install it with Minimal CD to another PC.

Thank you everyone.

---

### Post by Bucky Ball on 2012-11-20
All good. Please mark thread as Solved from Thread Tools if you think it is.

It is a good idea to make a list of basic things to install for the minimal install as remember, you are installing the kernel ONLY! Everything else is up to you. ;)

Good luck, enjoy the learning curve, the OS and the forums and don't forget to post a new thread with a descriptive title for any future questions/problems.

---

