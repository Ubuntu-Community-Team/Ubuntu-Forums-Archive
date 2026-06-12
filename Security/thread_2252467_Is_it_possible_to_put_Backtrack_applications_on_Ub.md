---
title: "Is it possible to put Backtrack applications on Ubuntu?"
date: 2014-11-12
forum: Security
---

### Post by cal1j on 2014-11-12
Hi guys,

I'd love to have all of the backtrack applications on my Ubuntu 14.04 laptop without having to chase them down one by one or dual boot, place in VM or whatever. Is this possible, easy, or advisable?

Thanks

---

### Post by TheFu on 2014-11-12
a) backtrack is old. Kali is the replacement.
b) visit the kali download page  [https://www.kali.org/downloads/](https://www.kali.org/downloads/) and follow the instructions at the bottom.

I've never done this, but the instructions seem easy enough - for certain values of "easy".

It is advisable?  Nope. Most of those tools run as root and are not designed to be secure. They are a liability on a normal desktop and make it more hackable.

In short, I wouldn't.

---

### Post by bashiergui on 2014-11-12
TheFu answered whether it's possible or easy. As to whether it's advisable: If all you do with this laptop is penetration testing then yes. If you use it for normal day to day stuff then no. Running all kali's services as root while on public wifi is a lot like running a honeypot.

---

### Post by cal1j on 2014-11-13
Good to know. Thanks guys

---

### Post by mastablasta on 2014-11-13
also Backbox Linux is penetration testing stuff on Ubuntu.

Kali is based on Debian.

---

### Post by Slave2Metal on 2014-11-17
Wifislax is another one to check out, based on slackware.  Just make a live usb using the dd command of any of these distros mentioned.  A lot safer than introducing the programs to a daily use machine.

---

