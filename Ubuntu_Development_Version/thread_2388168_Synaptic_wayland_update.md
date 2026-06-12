---
title: "Synaptic wayland update"
date: 2018-03-29
forum: Ubuntu Development Version
---

### Post by harry332 on 2018-03-29
There is a new synaptic version in proposed repo now.

synaptic (0.84.3) unstable; urgency=medium
  [ Michael Vogt ]
  * fix user-mode synaptic to not crash under wayland
  * add some more things to gitignore

---

### Post by exploder on 2018-03-29
I have been using it with the fix from the 17.10 release added to start up. It would be nice to have a version that just works though since wayland is working so nice now.:D

---

### Post by amano on 2018-03-29
Just add ```
**xhost +si:localuser:root**
```

to the automatic startup app in Ubuntu.

Done that, you can start synaptic with ```
**sudo synaptic**
```

every time and it will behave the same way as in the xorg session.

---

### Post by Frogs Hair on 2018-03-29
There is a new version in standard updates as well.

---

### Post by exploder on 2018-03-29
Just this in startup is all you need and it will work like it always has.

```
xhost +si:localuser:root
```

---

### Post by zika on 2018-03-30
> **amano said:**
> ```
**sudo synaptic**
``````
gksu(do) synaptic
```for reasons explained so many times especially after this previous priviledges change...

---

### Post by sudodus on 2018-03-30
There are problems with **gksu** and **gksudo** in Wayland (at least in Ubuntu 17.10).

I would recommend **sudo -H** for GUI application programs.

```
sudo -H synaptic
```

There are more details at this link,

[Why don't gksu/gksudo or launching a graphical application with sudo work with Wayland?](https://askubuntu.com/questions/961967/why-dont-gksu-gksudo-or-launching-a-graphical-application-with-sudo-work-with-w/961978#961978)

---

### Post by zika on 2018-03-30
> **sudodus said:**
> There are problems with **gksu** and **gksudo** in Wayland (at least in Ubuntu 17.10).
I would recommend **sudo -H** for GUI application programs.
```
sudo -H synaptic
```
There are more details at this link,
[Why don't gksu/gksudo or launching a graphical application with sudo work with Wayland?]("https://askubuntu.com/questions/961967/why-dont-gksu-gksudo-or-launching-a-graphical-application-with-sudo-work-with-w/961978#961978")Silly me ](*,)on a very busy morning but that is not a good enough excuse for me [IMG]https://ubuntuforums.org/images/smilies/icon_redface.gif[/IMG]... I've started, several minutes before finishing my post, writing with```
sudo -H
```like a Georgia on my mind and ended creating a vicious circle. Thank You for Your correction, mea culpa... My point was that vanilla sudo would not be a good choice...

---

### Post by sudodus on 2018-03-30
No worries @zika,

We are here to help each other. I have also made such mistakes, and somebody was there and helped getting it right :-P

---

