---
title: "What's the code for the terminal to install KDE in ubuntu CE?"
date: 2007-01-02
forum: Ubuntu Christian Edition
---

### Post by spainmiami on 2007-01-02
Hi all:) I've searched in the CE forums and have come up short. Or perhaps I might have missed it, but please correct me if I'm wrong:

The Ubuntu CE runs in Gnome, correct?  

I want to add the Kde desktop environment in ubuntu CE, so I can install more apps/games that are only work in Kde.

Thanx in advance everybody.

---

### Post by k1001001 on 2007-01-02
Maybe try sudo aptitude install kubuntu-desktop.

---

### Post by spainmiami on 2007-01-02
> **k1001001 said:**
> Maybe try sudo aptitude install kubuntu-desktop.

I've done that in the past in other pc (not my 9 year old niece's) and it will install but, if I'm not mistaken it will install Ubuntu but not CE:(

I cannot afford to lose all those Parental Filtering built in CE.

Unless if I'm missing something here, please correct me.

---

### Post by doobit on 2007-01-02
> **spainmiami said:**
> I've done that in the past in other pc (not my 9 year old niece's) and it will install but, if I'm not mistaken it will install Ubuntu but not CE:(

I cannot afford to lose all those Parental Filtering built in CE.

Unless if I'm missing something here, please correct me.

I think you need to install the KDE desktop first, if you don't have it, then install the convert script for your version of Ubuntu from the Ubuntu CE website.

---

### Post by mhancoc7 on 2007-01-02
> **spainmiami said:**
> Hi all:) I've searched in the CE forums and have come up short. Or perhaps I might have missed it, but please correct me if I'm wrong:

The Ubuntu CE runs in Gnome, correct?  

I want to add the Kde desktop environment in ubuntu CE, so I can install more apps/games that are only work in Kde.

Thanx in advance everybody.

I would suggest that you go to System>Administration>Ubuntu Christian Edition Installer and install the Ichthux desktop. It is another Christian OS based on Kubuntu. This will give you KDE and Gnome. KDE is used by Ichthux and Gnome by Ubuntu CE.
 
Your parental controls will continue to work in both.

Jereme

---

### Post by konect on 2012-04-30
user@ubuntu:~$ sudo sh
[sudo] password for user: 
# su
root@ubuntu:/home/user# apt-get install kubuntu-desktop

This is how you do it

---

