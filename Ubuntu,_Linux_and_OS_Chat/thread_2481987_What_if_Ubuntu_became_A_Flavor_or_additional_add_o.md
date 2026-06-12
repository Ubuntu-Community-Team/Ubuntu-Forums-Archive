---
title: "What if Ubuntu became A Flavor or additional add on of Lubuntu?"
date: 2022-12-15
forum: Ubuntu, Linux and OS Chat
---

### Post by raderall on 2022-12-15
What if the two got merged? Say you could just install Lubuntu and Install Xubuntu Or Ubuntu Or Kubuntu as an add on side desktop? Imagine that. Both teams working together on one OS as opposed to two different but similar ones. Ubuntu would be for sporting extra packages or whatever that increase that flavors size, but allows better support for gaming and other more complex functions.

---

### Post by slickymaster on 2022-12-15
Not a support request

Thread moved to **Ubuntu, Linux and OS Chat**

---

### Post by lammert-nijhof on 2022-12-15
I the past I installed the Lubuntu or Xubuntu desktop in Ubuntu :)  In the past I did run in the Ubuntu terminal: "sudo apt install lubutu-desktop". As far as I remember, you can choose the desktop in the login menu.

---

### Post by grahammechanical on 2022-12-15
What you are talking about has been available for years. This link will should how to install 8 different desktop environments on Ubuntu and how to log in to them.

[https://linuxconfig.org/the-8-best-ubuntu-desktop-environments-20-04-focal-fossa-linux](https://linuxconfig.org/the-8-best-ubuntu-desktop-environments-20-04-focal-fossa-linux)

There is something people should be aware of. Additional desktop environments will cause complications when we upgrade to the next version of Ubuntu/Lubuntu (or any other flavour). Online upgrades work best when we have a default OS setup.

Regards.

---

### Post by QIII on 2022-12-15
I believe you have a significant misapprehension of the nature of the Ubuntu ecosystem.

Ubuntu is an OS distributed by Canonical, LTD.  Other communities maintain versions of Ubuntu, the "flavors", as compliments to "vanilla" Ubuntu that suit community tastes.  Through a process most mythical and arduous, those communities have been recognized as "official".  The flavors are not rivals nor competitors.  They are all team members.

[https://wiki.ubuntu.com/UbuntuFlavors](https://wiki.ubuntu.com/UbuntuFlavors)

---

### Post by raderall on 2022-12-16
Oh thanks I didn't know this! wow am I behind! only other thing I could think of that would be cool is if they made a version of lubuntu that's a SteamOS! or steam machine. It would be only a steam gaming app and web browser. Would make those two faster than the other os's that have to do alot at once right?

---

### Post by mikewhatever on 2022-12-16
This is the silliest idea ever, but I think I can outsilly it. Well, what if Ubuntu, systemd and linux merged into Ubsydnux...?

---

### Post by guiverc on 2022-12-16
I'm in the Lubuntu team, on the Lubuntu Council in fact (*which makes me a Product Manager for Lubuntu*), yet I consider my Lubuntu system a Ubuntu one.

All Ubuntu and *flavors* use the same repositories, with the only differences (*as I see it anyway*), being

- Flavors are community based, thus use packages from 'universe' where Ubuntu does not (*it needs to be enabled for Ubuntu installs*, refer [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu) for details on repositories)

- All ISOs are built from different *seeds* ; our (Lubuntu) current *lunar* seed being [https://people.canonical.com/~ubuntu-archive/seeds/lubuntu.lunar/desktop](https://people.canonical.com/~ubuntu-archive/seeds/lubuntu.lunar/desktop), where Xubuntu have their own *lunar* seed ie. [https://people.canonical.com/~ubuntu-archive/seeds/xubuntu.lunar/desktop](https://people.canonical.com/~ubuntu-archive/seeds/xubuntu.lunar/desktop), as do other *flavors* or Ubuntu Desktop & Ubuntu Server themselves.

All of Ubuntu ISOs are built by the same infrastructure with those *seed* files controlling the differences.

ie. to me Lubuntu is a Ubuntu system.

FYI:   I'm a *lover* of multiple desktops, and my primary PC (*dead currently due to PSU issue which I've not resolved, but I'll still use it as example*) has (*had*?) the Lubuntu desktop installed (ie. LXQt), Ubuntu Desktop (ie. GNOME), Xubuntu Desktop (ie. Xfce) plus Ubuntu-MATE (MATE) installed too.  I select which I use when I login, which most of the time is actually Lubuntu/LXQt (*hey I'm in heavily involved with that team*), but I'm also involved in QA with other *teams* too.  Ubuntu and the *flavors* are all part of the *wider* Ubuntu community   (*look at my user ID - it says Ubuntu Member, not Lubuntu*).

---

### Post by mIk3_08 on 2022-12-17
```
(*which makes me a Product Manager for Lubuntu*)
```
Oh. Congratulations guiverc. Good Luck and Hoping for the best in your team. Regards and cheers.

---

### Post by guiverc on 2022-12-17
Thanks @mlk3_08  & G'day.

---

### Post by mIk3_08 on 2022-12-18
> **guiverc said:**
> Thanks @mlk3_08  & G'day. Don't hesitate to contact me if you have any additional assignment for me in Lubuntu. Regards and cheers.

---

### Post by raderall on 2023-01-05
So you're saying Xubuntu and Lubuntu ARE still two different desktops? and not something you can easily switch between? or did I read wrong?

---

### Post by guiverc on 2023-01-05
> **raderall said:**
> So you're saying Xubuntu and Lubuntu ARE still two different desktops? and not something you can easily switch between? or did I read wrong?

I'm not sure who you were asking that question of, but

- Xubuntu uses the Xfce desktop; it's a GTK3 desktop

- Lubuntu (since 18.10) has used the LXQt desktop, which is a Qt5 desktop.

thus yes they are different desktops.

The system I'm using currently is a Lubuntu install only; however my more common machine will let me select at login which I want to use; offering choices of Ubuntu (GNOME), Lubuntu (LXQt), Xubuntu (Xfce), or Ubuntu-MATE (MATE) let alone a number of variations (eg. GNOME with Wayland/Xorg etc, Lubuntu-LXQt/LXQt/Openbox etc).  If I'm using a multi-desktop install, I can logout & return to the *greeter* (`sddm` is the DM I normally use as *greeter*) and login selecting a different desktop to use, and use that desktop for the new session.

If I was to do that on this *purely* Lubuntu install; I just have fewer options, ie. I can select

- LXQt session  (*a purer upstream offering of the LXQt desktop*)
- Lubuntu session  (*all the Lubuntu additions are available; this will match the Lubuntu manual found at [https://manual.lubuntu.me/stable/](https://manual.lubuntu.me/stable/)*)
- Openbox session  (*LXQt is a WM agnostic desktop, Lubuntu chooses to use openbox as the WM, so we allow users to use that by itself too, ie. no LXQt desktop is run*)

My multi-desktop install setups just have the additional options offered because I've added `xubuntu-desktop`, `ubuntu-desktop` and `ubuntu-mate-desktop` in my example[I].   (also FYI, my installs may not have started as Lubuntu either, some started as Ubuntu Desktop, some as Xubuntu installs, etc)

[/I]You can have multiple desktops installed, but only one will run at any given time. You select which runs in the greeter when you select your username and enter your password (*how this is done varies on the DM or display manager you're using; look for a dropdown selector, gear icon etc*).

---

