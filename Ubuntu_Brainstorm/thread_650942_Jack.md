---
title: "Jack?"
date: 2007-12-27
forum: Ubuntu Brainstorm
---

### Post by pavel989 on 2007-12-27
Just an idea, but, with so many apps using jack, why not just install it as part of the distro? make it standard. Also, that should make it easier to use, since installing wouldn't be a problem. i understand ubuntuStudio should be able to do that, but even in Studio, i had a hard time installing and setting it up.

---

### Post by 23meg on 2007-12-27
[QUOTE=pavel989]with so many apps using jack[/QUOTE]

What apps in the Main component use it? I don't think there's a strong use case for the default installation. 

[QUOTE=pavel989]but even in Studio, i had a hard time installing and setting it up.[/QUOTE]

How exactly did you try installing it and what problems did you face?

---

### Post by pavel989 on 2007-12-28
well first i tried getting it to work with alsa for a long time, which didn't work, so i got it to work with oss. and i dont know about main repos, but theres many editing apps that use it,

---

### Post by zettberlin on 2007-12-28
Jack is installed by default with Ubuntu Studio, it can be installed with a few clicks in Ubuntu-standard. I guess, what you mean is not, that installation is complicated but setup is.

To run jack with qjackctl your sound hardware must be supported OK by alsa or freebob (if you have a firewire-soundcard). By your writing I get the impression, that your sound solution is not supported by alsa - that is the absolute exception. 90% of all recent hardware works good with alsa if you are on I386. Some problems with the performance can be solved by configuring jack. Many USB-soundcards only work OK if you set Periods/Buffer to 3 instead 2. Please check also, if this file is set correctly:

 /etc/security/limits.conf

it should contain something like that on its end:

@audio - rtprio 99
@audio - memlock 920000


What hardware do you use? Maybe there are some HOWTOS especially for your setup...


> **23meg said:**
> What apps in the Main component use it? I don't think there's a strong use case for the default installation. 


Audio-editing is one of the basic things modern computers can do. Mac/Win offers such capabilities by default since the last century. So no matter if most users do not edit/make music on their box - if they choose to do such things next week they should be able to do so without hassle in Ubuntu.

Plus: Jack is not that fearsome beast it used to be 2-3 years ago. If the distros would offer Xinelib and gstreamer with proper jack support switched on, the average user would not even notice, that jack is running. And he/she would not run into trouble, if they choose to try out ZynaddSubFX or Ardour.

It is quite strange, that xinelib from universe does not support jack - I built it myself with it and it was a piece of cake. And it works just great.

---

### Post by Drunky on 2007-12-28
good post zettberlin

---

### Post by 23meg on 2007-12-28
[QUOTE=zettberlin]Audio-editing is one of the basic things modern computers can do. Mac/Win offers such capabilities by default since the last century. So no matter if most users do not edit/make music on their box - if they choose to do such things next week they should be able to do so without hassle in Ubuntu.[/QUOTE]

In what way does moving JACK to main make things easier? The apps that users will need aren't installed by default, and are in Universe. So is JACK. It gets installed when it's needed. Why have it installed by default when nothing will be using it? 

And even if something is to use it by default, the advantages of it using JACK have to be weighed carefully against the potential impact. Basic audio editing tasks don't really require JACK, and the main hassle with it is actually setting it up for your hardware. Default installation doesn't improve things on that front either.

---

### Post by Steveway on 2007-12-28
Instead of installing it by default, it would be better that all apps that can have jack-support should be compiled with it.
Take Zetterberlins example; Xine.
Jack is awesome, there is nothing comparable on Windows or Mac (Though, I heard Jack can run there but most apps they use don't support it so...).
In terms of sound-apps we are far ahead, Amarok, Jack also my favourite IDJC (See my Signature)...
Just get everything to work properly together and we are happy.

---

### Post by zettberlin on 2007-12-28
> **Steveway said:**
> Instead of installing it by default, it would be better that all apps that can have jack-support should be compiled with it.

Absolutely: Having Jack installed by default would mean, that audio on Ubuntu is jacks domain whatsoever. This WOULD be nice but  would mean a lot of new work to do.

So having everything jack-aware in the background would be a big and easy step ahead. Once a user installs Ardour, his/her multimedia-desktop should *not* collide with the new jack-environment and vice-versa.

As in the following scenario:

Jim installs Ardour to produce a radio-feature.

Jack/qjackctl and some more audio-stuff is installed automagically as well. Synaptic asks Jim also, if he wants to install an RT-Kernel and configure his system for RT-audio.

Jim needs to restart the computer to enable the new kernel. An informative Bootsplash tells him, that everything starts up just fine.

As Jim then starts up Ardour, he is notified, that jackd must run with ardour. Qjackctl starts up and kills everything that hugs the sounddevice. If there is more than one Soundcard, it asks Jim, which one shall be used.

Now qjackctl starts Jack and all the apps killed before as jack-clients.

Everything (systemsounds, video-player, internet-radio etc.) feels the same as before, Ardour starts up and runs whithout hickups.

Everybody is happy :-)

---

### Post by pavel989 on 2007-12-29
zettberlin-
yea your right, not installing but setting up,
although i dont neccessarly mean having it default, but that would be kool.

---

