---
title: "Hacker's  warning."
date: 2006-03-21
forum: Server Platforms
---

### Post by Darkness3477 on 2006-03-21
Say, for some instance that I've gained the knowledge that one particular person is trying to hack into my system. The know that I run a Linux OS, but they don't know whcih one. Of course, that is fiarly easy to find out. What things would I need to do to secure my computer fully, considering I have no ports open that are not needed, and that I am running a firewall? I also have a relitively fresh install, with nothing but Apache and MySQL installed on it that I can see as being some sort of a security weakness.

ANy input will be welcomed, as I'm quite sure alot of you will have something to say. Also, do you think that having Apache and MySQL installed will be some sort of a weakness?

---

### Post by red_shrike on 2006-03-21
I guess you might set your firewall on maximum security, change your passwords into more complicated (IjTDCD787m) and change folder user security on max (like, not allow "other" users to do anything, or even the whole group). I know, this is a bit paranoid, but if there is anything valuable on ur PC than u might even want to do a backup of everything).

---

### Post by Darkness3477 on 2006-03-21
There isn't anything exactly 'valuable' on my computer, but there are some personal files about myself, my friends and certain projects, that I don't want other people to see. 

And of coruse, I like my privacy, so I don\t want some JackArse coming in and looking through my stuff.

---

### Post by red_shrike on 2006-03-21
Have you considered setting up passwords for individual folders? Or setting up a safe partition?

---

### Post by towsonu2003 on 2006-03-22
check out google for encrypted partitions and stuff.. I believe there is a howto in the forum as well -for ubuntu..

---

### Post by nanotube on 2006-03-29
certainly, apache and mysql, if they are accessible from the outside, would increase your risk dramatically. if you want to seriously protect your system, and you dont /need/ to have those running (or at least not available to the outside), you should stop them or block them off with the firewall.

generally, the more services you have running that are world-accessible, the more open you are to attack.

---

### Post by Patrick-Ruff on 2006-03-29
what kind of warning? infiltration warning by a firewall? some ******* online trying to scare you? close off all the stuff they say and all that. passwords and whatnot. becides, hes probably some ***** windows hacker who hasen't hacked Linux much and hasent a clue how it works. either way, hes probably a fake.

---

### Post by frodon on 2006-03-29
[QUOTE=towsonu2003]check out google for encrypted partitions and stuff.. I believe there is a howto in the forum as well -for ubuntu..[/QUOTE]yes here : [http://doc.gwos.org/index.php/Encrypter_Decrypter_Script](http://doc.gwos.org/index.php/Encrypter_Decrypter_Script)

---

