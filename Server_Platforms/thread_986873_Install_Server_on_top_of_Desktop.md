---
title: "Install Server on top of Desktop?"
date: 2008-11-19
forum: Server Platforms
---

### Post by UranUtan on 2008-11-19
Hi,

I have Ubuntu Desktop 8.10 32 bits. I would like to practice phpBB3 which probably requires Ububtu Server. Can you please give me some guidelines:

Q1. Can I use Desktop and install the components required by phpBB3 (Apach, PHP, MySQL). 

Q2. If #1 is not OK, then can I upgrade Ubuntu Desktop to Server?

Q3. How will a Ubuntu Server look like? Is it GUI less system or does it still have the same GUI and applications like Desktop?

Thanks in advance for any help.

---

### Post by CrucifiedEgo on 2008-11-19
You can install the webserver components in the desktop version of ubuntu -- sudo apt-get install apache2 mysql5 php5 php5-mysql i think should do the trick.

The main difference between server and Desktop ubuntu is the lack of a GUI.  There are other differences of course, but that's the most obvious, and answers your question #3.

---

