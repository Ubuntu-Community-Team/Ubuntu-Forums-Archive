---
title: "If I want install Ubuntu 9.04 in a VirtualBox machine,I need a VirtualBox 2.2?"
date: 2009-04-29
forum: Virtualisation
---

### Post by rockrong on 2009-04-29
If I used a old vision of virtualbox(2.06),after installing Vboxadditions,the Ubuntu 9.04 will lost display driver~

---

### Post by andrew.46 on 2009-04-29
Hi rockrong,

> **rockrong said:**
> If I used a old vision of virtualbox(2.06),after installing Vboxadditions,the Ubuntu 9.04 will lost display driver~

I did not attempt to run Jaunty as guest with the older version so I cannot advise you on that but I *can* tell you that it runs fine with VirtualBox_OSE 2.2.0. The only problem I had, and I am not sure it is a 'known problem', is that I had to set the mouse in xorg.conf for mouse integration to work with the guest additions. Just for the record my successful settings were:

```

Section "InputDevice"
        Identifier  "vboxmouse"
        Driver          "vboxmouse"
        Option          "CorePointer"
        Option          "Device"        "/dev/input/mice"
EndSection

```

All the very best,

Andrew

---

### Post by rockrong on 2009-04-29
I have used a VBox 2.2.2's VBoxAdditions.iso do it~
I had a news for the problem:the old vision of Vboxaddition did not work for Ubuntu 9.04,because of the wrong setting for Xserver.
Ubuntu 9.04 used a new vision of Xserver.

---

### Post by andrew.46 on 2009-04-30
Hi rockrong,

> **rockrong said:**
> I have used a VBox 2.2.2's VBoxAdditions.iso do it~
I had a news for the problem:the old vision of Vboxaddition did not work for Ubuntu 9.04,because of the wrong setting for Xserver.
Ubuntu 9.04 used a new vision of Xserver.

My apologies I do remember that problem which required manual installation of the guest additions after modifying the install.sh file. As you have no doubt found this is no longer required and as well having just upgraded myself to 2.2.2 OSE I see that that modification to the xorg.conf file for mouse integration is no longer required :-).

All the best,

Andrew

---

