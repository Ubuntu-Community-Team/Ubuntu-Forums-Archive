---
title: "rosetta stone in ubuntu (+microphone)"
date: 2010-06-24
forum: Virtualisation
---

### Post by prince.buster on 2010-06-24
*don't use wine!*

your microphone may work, but it probably won't. and the most attractive feature of rosetta stone is it's speech recognition facility. you want your microphone to work!

unfortunately rosetta has some convoluted microphone detection process, that doesn't work well with wine. you can find a [bug report _here_]("http://bugs.winehq.org/show_bug.cgi?id=14559"). registering, voting and commenting with your experience will help the speedy resolution of the bug by the wine developers.

in the meantime - are we going to give up on first try? no we are not!

rosetta stone runs perfectly, microphone and all in a virtual-box install of windows xp. and it isn't as much screwing around as you might think. setting this up is really easy.

1. ```
sudo aptitude install vboxgtk virtualbox-guest-additions
```
2. ```
virtualbox
``` or select VirtualBox OSE from the Accessories menu
3. create a new machine; fluff your way through the settings
4. legally obtain iso images for windows xp (microxp is very convenient though it's legal status is debatable) and rosetta stone 
5. attach the iso to your new machine and boot it, the install only takes a few minutes. you're now running windows from within ubuntu!
6. install the guest additions. the menu item is found in the devices submenu of your running virtual machine. this mounts an iso within the machine that you use to install the guest additions within windows xp.
7. attach the iso for rosetta and install as you normally would
8. you're done.
9. to skip a few mouse clicks each time, you can create a launcher for your virtual machine using the command ```
VBoxManage startvm machinenamehere
```
tip - instead of shutting your machine down each time, save the state. you can then load the entire running instance of windows xp and rosetta stone *faster* than you could in wine.

---

### Post by MMagoo1 on 2012-07-01
Best Solution is here: [http://askubuntu.com/questions/77210/how-to-change-the-default-audio-in-wine-to-alsa-only](http://askubuntu.com/questions/77210/how-to-change-the-default-audio-in-wine-to-alsa-only)

Just change Wine to Alsa and everything works fine.

---

### Post by SleepWalkerX on 2012-07-02
Changing the specific option in winetricks didn't help me.  Still not picking up on my onboard soundcard or microphone.  :(

---

### Post by SleepWalkerX on 2012-07-02
Ah, upgrading to wine1.5 fixed my problem.  Cheers!

[https://launchpad.net/~ubuntu-wine/+archive/ppa](https://launchpad.net/~ubuntu-wine/+archive/ppa)

---

