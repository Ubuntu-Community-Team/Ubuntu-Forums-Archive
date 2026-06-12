---
title: "Preventing OS re-install"
date: 2011-05-24
forum: Security
---

### Post by Mirddyn on 2011-05-24
Hi,

Well, I'm writing this right after my phone was stolen and I can't to anything to get it back and well... I'm scared for my laptop now a bit.

I have a plan to make a program, so that every time my laptop starts, a log will be sent to remote server with some info so I could trace my PC back + a backdoor so I could control it remotely a bit...

Anyway, there is always the risk, that they would re-install OS. Is there a way to prevent re-installing OS without knowing some password?

Thanks all!!!

---

### Post by bodhi.zazen on 2011-05-24
If someone has physical access they can do what they will with the machine.

---

### Post by Megaptera on 2011-05-24
mirddyn
You may be interested in this [http://preyproject.com/](http://preyproject.com/)

---

### Post by Lars Noodén on 2011-05-25
**wget** could be run in a script and used to post or just plain access a URL.  It won't prevent a reinstall, you'd have to lock down the BIOS (e.g. no boot from USB or CD) and Grub to make that harder, but could help track the location.

---

### Post by Mirddyn on 2011-05-25
Awesome!!! Thanks all!!! I think I will lock down the bios and grub :) Adds extra layer of security, even tho its not 100% secure :)

And thanks for the preyproject!!!!

Thanks again very much!!!!

---

