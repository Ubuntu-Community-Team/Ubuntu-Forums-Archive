---
title: "Graphic glitch after interrupted apt upgrade?"
date: 2018-02-09
forum: Ubuntu/Debian BASED
---

### Post by ondrej-janecek on 2018-02-09
[IMG]https://ibb.co/h4RLox[/IMG][IMG]https://ibb.co/h4RLox[/IMG]Hi all,
I'm new to this forum, so sorry for any mistakes..
Today I booted my Elementary OS into this (see the screenshot). Blurred or missing texts, no text in menus...
The problem is probably corrupted apt upgrade process. Yesterday I experienced a power blackout when apt was finishing the upgrade process. One of the packages were some mesa packages.
I tried to re-install them and reboot, but nothing happened.
How can I find out the real cause of this graphic glitch to solve it properly?
Thanks
[IMG]https://image.ibb.co/nqwyac/Workspace_1_007.png[/IMG]

---

### Post by coffeecat on 2018-02-09
Not an Ubuntu flavour.

*Thread moved to **Ubuntu/Debian BASED**.*

---

### Post by ondrej-janecek on 2018-02-09
oh sorry, I think I've seen some elementary os questions here. Any idea where should I ask my question?

---

### Post by coffeecat on 2018-02-09
You are very welcome to ask questions in this section, but there may not be many forum members who have experience of Elementary OS. The support page that the Elementary OS people provide is here:

[https://elementary.io/support](https://elementary.io/support)

---

### Post by cruzer001 on 2018-02-09
Try

```
sudo dpkg --configure -a && sudo apt-get -f install
```

---

### Post by ondrej-janecek on 2018-02-09
> **cruzer001 said:**
> Try

```
sudo dpkg --configure -a && sudo apt-get -f install
```

Hmm, tried that, everything seems ok - it didn't help. Maybe I should only configure the drivers somehow, change the drivers?

---

### Post by cruzer001 on 2018-02-09
Did "apt-get -f install" produce any errors?

Did you try continuing the upgrade process?

```
sudo apt-get update && sudo apt-get dist-upgrade
```

Please post any errors.

What kind of graphic processor do you have and what driver?

```
sudo lshw -c display
```

If you need a better screen to work with you can switch to TTY (text only screen).

Ctrl + Alt + F1

To switch back to GUI.

Ctrl + Alt + F7

Also (as coffeecat said) a good idea to post in the elementary forum.  Elementary OS  is similar to Ubuntu, but there are still differences in how they are built.

---

