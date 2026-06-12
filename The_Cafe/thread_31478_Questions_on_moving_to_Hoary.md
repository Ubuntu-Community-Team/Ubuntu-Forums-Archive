---
title: "Questions on moving to Hoary"
date: 2005-05-03
forum: The Cafe
---

### Post by jwb on 2005-05-03
I'm still on Warty, and I wondered if anyone had upgraded to Hoary using apt-get? How did that go? What is the CLI command to do that? Anything break?

---

### Post by UbuWu on 2005-05-03
To upgrade:

edit /etc/apt/sources.list and replace warty everywhere with hoary
then in a terminal windows type:
sudo apt-get update
sudo apt-get dist-upgrade

Worked great for me. There are some small things that don't work as well as on a fresh install, don't remember what they were though, so probably not a big problem to most people.

---

### Post by poofyhairguy on 2005-05-03
[QUOTE=jwb]Anything break?[/QUOTE]

Crossover Office broke for me, and the Nvidia drivers needed to be turned on again. Thats it...

---

### Post by WildTangent on 2005-05-03
Xorg got messed up for me, was stuck at 640x480 resolution, and running the config program for it didnt work. so i just downloaded the ISO and did a clean install

-Wild

---

### Post by jwb on 2005-05-04
Cool!

Worked like a charm..... no problems at all. Thanks for the input.

Dang, that was easy. Way to go Ubuntu!

---

