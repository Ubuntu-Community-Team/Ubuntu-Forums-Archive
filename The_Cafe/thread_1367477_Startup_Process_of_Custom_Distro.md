---
title: "Startup Process of Custom Distro"
date: 2009-12-29
forum: The Cafe
---

### Post by GreenDance on 2009-12-29
Hi, I've received a custom distro of DSL from an ex-college who I no longer see, when I boot the custom distro it says "starting (his name)'s distro, please wait", how can I find out what is starting up, basically see if anything is starting up that is hidden from view.

---

### Post by autora on 2009-12-29
ctrl+alt+f1 when booting

---

### Post by dragos240 on 2009-12-29
Try editing his grub conf. And deleting quiet if it's there.

---

### Post by GreenDance on 2009-12-29
> **autora said:**
> ctrl+alt+f1 when booting

nothing happens :(

> **dragos240 said:**
> Try editing his grub conf. And deleting quiet if it's there.

can't seem to find it :(

---

### Post by RiceMonster on 2009-12-29
> **GreenDance said:**
> nothing happens :(



can't seem to find it :(

/boot/grub

look at menu.lst

---

### Post by Crunchy the Headcrab on 2009-12-29
ex-**colleague**?

---

### Post by Xbehave on 2009-12-29
most distros start up using by running the scripts in /etc/rc4.d/ that start with S (it might not be rc4, you can find out which it is by running runlevel)

---

