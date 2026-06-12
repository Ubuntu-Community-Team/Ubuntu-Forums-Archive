---
title: "modify cryptsetup message on boot splash screen ubuntu 10.04"
date: 2011-10-30
forum: Security
---

### Post by H43S on 2011-10-30
Hi all, any idea how to change/modify the message asking for harddisk encryption on boot splash screen?

Usually the message will show something like "Unlocking device with uuid <dev><uuid>. Enter Passphrase:" I encrypted the harddisk using cryptsetup on ubuntu 10.04

---

### Post by H43S on 2011-11-01
anyone can help me :confused:

---

### Post by bodhi.zazen on 2011-11-01
My guess is you would need to recompile cryptsetup.

You might be able to write a custom initramfs, extract yours and take a look at it.

---

### Post by H43S on 2011-11-01
Thanks for the advice, will look into it :)

---

