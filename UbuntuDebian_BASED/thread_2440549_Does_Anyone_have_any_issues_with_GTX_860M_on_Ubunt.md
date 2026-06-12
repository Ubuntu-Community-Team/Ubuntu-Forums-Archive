---
title: "Does Anyone have any issues with GTX 860M on Ubuntu 18.04 LTS?"
date: 2020-04-12
forum: Ubuntu/Debian BASED
---

### Post by whynvidia on 2020-04-12
Hello,

my setup is  Debian On  Y50-70 laptop with XFCE, im unsure whether my graphics card will works? (I want to experience pytorch/tensorflow It requires graphics card)
I want to know if anyone have GTX 860M and have any issues? And if not, how did you go through the installation and make nvidia drivers work?

I know how to install ubuntu but not sure about the installation of Nvidia Drivers.

If anyone have any tutorial I will appreciate it if you can link down.

Thanks

---

### Post by CelticWarrior on 2020-04-12
Installing Nivida drivers in Ubuntu is as easy or even easier than in Debian.
For GTX 860M the currently recommended version is 440.xx. In new UEFI systems is also recommended to disable Secure Bot as it prevents loading unsigned drivers, so, either disable it or sign the drivers yourself (hint: just disable Secure Boot).

---

### Post by howefield on 2020-04-12
Thread moved to the "Ubuntu/Debian BASED" forum.

---

### Post by whynvidia on 2020-04-12
> **CelticWarrior said:**
> Installing Nivida drivers in Ubuntu is as easy or even easier than in Debian.
For GTX 860M the currently recommended version is 440.xx. In new UEFI systems is also recommended to disable Secure Bot as it prevents loading unsigned drivers, so, either disable it or sign the drivers yourself (hint: just disable Secure Boot).
so, i am not sure if I have nvidia drivers installed atm on but im pretty sure i have bumblebee.
can you link a tutorial on installing nvidia drivers after installing ubuntu 18.04 LTS?
Are there any known issues related to nvida-drivers?

---

### Post by CelticWarrior on 2020-04-12
The only tutorial you need (after disabling Secure Boot):
[LIST]
[*]Open Additional Drivers, select & apply the recommended version, reboot when done.
[/LIST]

There are issues with any software, you need to be a lot more specific. And perhaps better to try the above and then ask about any eventual issue then asking about extremely vague hypotheticals.

---

