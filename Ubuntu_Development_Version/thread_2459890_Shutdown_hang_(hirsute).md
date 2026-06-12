---
title: "Shutdown hang (hirsute)"
date: 2021-03-29
forum: Ubuntu Development Version
---

### Post by MyMurry on 2021-03-29
Hello!

My System hangs for a few seconds at shutdown. Which program to blame?

---

### Post by cmcanulty on 2021-03-29
This worked for me on that issue

You need to delete the "splash" entry in the grub menu. It helped me.

in terminal:

```
    sudo pluma /etc/default/grub
    Remove "splash" entry,save: Ctrl+o Enter,Ctrl+x and
    sudo update-grub
```

Also helped, I am running xubuntu 20.04

```
sudo apt-get purge xfce4-screensaver
```

---

### Post by MyMurry on 2021-03-29
> **cmcanulty said:**
> This worked for me on that issue

You need to delete the "splash" entry in the grub menu. It helped me.



This disable plymouth, right?

---

### Post by ajgreeny on 2021-03-29
It should mean that you see a scrolling text boot and may be able to see what is attempting to be done when the delay happens.

You can do this for a single boot without making it permanent by hitting "E" at the grub menu (for edit) and then delete ***quiet splash*** from the kernel line then Cttrl+X (I think) to boot.
The edit will not last beyond that one boot but can, of course, be repeated if you need to.

---

### Post by MyMurry on 2021-04-12
[https://bugs.launchpad.net/bugs/1923335](https://bugs.launchpad.net/bugs/1923335)

---

### Post by zebra2 on 2021-04-13
Sounds like unattended updates. It can do the same thing during boot. If it is no inconvenience I suggest  let it do it's thing.

---

