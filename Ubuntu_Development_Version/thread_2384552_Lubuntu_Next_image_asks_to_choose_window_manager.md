---
title: "Lubuntu Next image asks to choose window manager"
date: 2018-02-08
forum: Ubuntu Development Version
---

### Post by kansasnoob on 2018-02-08
I've never messed with Lubuntu Next before so I'm trying the Bionic daily and while booting the live image it asks me to choose window managers, only offering the "Other" option. From there it navigates to a listing of everything you'd see in the file manager and I have no idea what to choose. So color me confused :confused:

---

### Post by cruzer001 on 2018-02-08
I haven't tried it yet.

LXQT is suppose (one day) to replace LXDE, but all you get is the file manager lookin thingy.  Sound like you hit on the first snafu.  Wonder if TTY would let you use startx.

---

### Post by kansasnoob on 2018-02-08
> **cruzer001 said:**
> I haven't tried it yet.

LXQT is suppose (one day) to replace LXDE, but all you get is the file manager lookin thingy.  Sound like you hit on the first snafu.  Wonder if TTY would let you use startx.

I couldn't call up a tty at all. I did seem to get it installed selecting ubiquity, but there was an initramfs-utils error at the end and it's not possible to boot any session afterwards - not even plain old openbox. So I think it's safe to say it's borked ATM.

---

### Post by VMC on 2018-02-08
I just choose "open box". Here is bug report:
[https://bugs.launchpad.net/lubuntu-next/+bug/1739959](https://bugs.launchpad.net/lubuntu-next/+bug/1739959)

---

### Post by kansasnoob on 2018-02-08
> **VMC said:**
> I just choose "open box". Here is bug report:
[https://bugs.launchpad.net/lubuntu-next/+bug/1739959](https://bugs.launchpad.net/lubuntu-next/+bug/1739959)

Thanks, I me too-ed and subscribed.

---

### Post by vasa1 on 2018-02-11
I tried the current Lubuntu Next in a virtual machine without installing it. So maybe that's why I didn't get "it asks me to choose window managers, only offering the "Other" option." but there were a couple of notifications about power management or battery which went away.

After that a "conventional" desktop appeared. They seem to be going with Qupzilla as the included browser.

---

### Post by kansasnoob on 2018-02-13
> **vasa1 said:**
> I tried the current Lubuntu Next in a virtual machine without installing it. So maybe that's why I didn't get "it asks me to choose window managers, only offering the "Other" option." but there were a couple of notifications about power management or battery which went away.

After that a "conventional" desktop appeared. They seem to be going with Qupzilla as the included browser.

I noticed in my email that the related bug was fixed but haven't checked to see if the fix made it into the daily images or not. I assume that it did based on what you're saying.

Last I checked KDE (or maybe Kubuntu) was taking over development of Qupzilla. Suits me fine :)

We have a lot of really fine choices right now regarding flavors and/or desktop environments, and it just keeps getting better.

---

### Post by vasa1 on 2018-02-14
> **kansasnoob said:**
> ...
Last I checked KDE (or maybe Kubuntu) was taking over development of Qupzilla. Suits me fine :)
...
I saw that as well. From what I remember, I think KDE (?) would be extending some sort of infrastructural support.

[http://blog.qupzilla.com/2017/08/qupzilla-is-moving-under-kde-and.html](http://blog.qupzilla.com/2017/08/qupzilla-is-moving-under-kde-and.html)
[https://clivejo.com/falkon-new-browser-under-the-kde-umbrella/](https://clivejo.com/falkon-new-browser-under-the-kde-umbrella/)

Re. the window manager choice, both you and VMC went for an actual install. I just tried the live session. So, I'm not sure if things are fixed or not.

---

