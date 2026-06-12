---
title: "Shall I upgrade?"
date: 2009-06-10
forum: The Cafe
---

### Post by amitabhishek on 2009-06-10
I am still on Hardy Heron 8.04 LTS and at the moment I am not getting a reason to upgrade. But since two versions are out I am wondering if I am missing something. Doing a fresh install is a real pain. Last time when I moved to Ubuntu from Daryna (Linux Mint) I had real trouble in configuring my sound card. I don't want to re-invent that wheel again...so is Intrepid Ibex or Jaunty Jackalope worthy upgrades or am better off with Hardy...

---

### Post by earthpigg on 2009-06-10
if you are happy with hardy, stick with it. or, wait a few months for the next LTS in october.

i always view LTS as 'mainstream' and the 6 month releases as 'for people that _**like**_ reinventing the wheel'

(i will mention that the boot time improvement with 9.04 is noticeable, and the new notification look is nice... only thing i have noticed since 8.04, to be honest.)

---

### Post by gn2 on 2009-06-10
> **amitabhishek said:**
> ~ I am not getting a reason to upgrade. ~

So don't upgrade. Simples.

---

### Post by The Real Dave on 2009-06-10
I upgraded from 8.04 to 9.04, and found considerable improvements, in speed and compatibility with my hardware, media player, and my Windows network. However, I did lose all my config of 8.04, and programs, as I did a clean install. 

One bit of advice I would give is not to make the same mistake as I did. I first tried moving my 8.04 /home dir to another partition, then taking a partimage of 8.04, clearing the / partition, and installing 9.04, with it point to the 8.04 /home dir. This was a huge mistake. I never deleted the program config files from 8.04, which caused serious problems in 9.04. Nothing was right. I ended up doing another install of 9.04. 

Also, if you install 9.04, make sure to point to your existing swap partition. I forgot to, and ended up with two. Nothing major, but just more partitioning and editing.

Overall, if your happy with 8.04, and it works well for you, stay with it. It wasn't for me, and thats why I upgraded. 

> ...or, wait a few months for the next LTS in october.


If you decided to stick with Hardy now, definately do upgrade to the next LTS.

---

### Post by pookiebear on 2009-06-10
Didn't make much of difference for me. But my laptop is 9 years old. I didn't upgrade however. I did a fresh re-install. Also ran the live CD of fedora 11 last night. Feels the same just blue. Sticking with xubuntu for now since both are blue. lol

---

### Post by ssam on 2009-06-10
one thing to bare in mind is that each new ubuntu version improves hardware support. what used to be a pain to set up may now be recognised and configured automatically.

i recommend that you try booting a live cd of the new version. if everything works automatically on the live cd, then you could upgrade.

also if you have made lots of tweaks to get sound working, then they may interfere with the upgrade process. a clean install may be best.

---

### Post by Sand &amp; Mercury on 2009-06-10
> **The Real Dave said:**
> One bit of advice I would give is not to make the same mistake as I did. I first tried moving my 8.04 /home dir to another partition, then taking a partimage of 8.04, clearing the / partition, and installing 9.04, with it point to the 8.04 /home dir. This was a huge mistake. I never deleted the program config files from 8.04, which caused serious problems in 9.04. Nothing was right. I ended up doing another install of 9.04. 
You can also just delete all the dot files inside your home dir, from the command line if need be. If no configs are found, the programs just generate new ones. Would've saved you a reinstall.

---

### Post by scottuss on 2009-06-10
You will find that doing a straight upgrade will break things. You are always better off to backup everything you need and do a clean install. I've heard tonnes of horror stories about upgrades going wrong or the system being sluggish afterwards.

---

### Post by TBOL3 on 2009-06-10
Wait, did you say next LTS in October?  I though it would be next April.

---

### Post by The Real Dave on 2009-06-10
> **Sand & Mercury said:**
> You can also just delete all the dot files inside your home dir, from the command line if need be. If no configs are found, the programs just generate new ones. Would've saved you a reinstall.

I realise that now, and in any case I wanted to keep them should I need to revert back to 8.04. Doesn't really matter anymore, their not archived and stored with my 8.04 image :D Hindsight is a terrible thing :P

---

### Post by amitabhishek on 2009-06-10
Thanks for the insights!!

Over a year I have downloaded lots of stuff through repos. I have Virtual Box running Sabayon. Then huge WINE collection including Safari, IE6 etc. So this entire quagmire of fresh install is scary.  

I am sure lot of members here would have upgraded from 8.10 to Jaunty. What could be those compelling reasons? I am sorry if I am sounding like a lawyer ;).

BTW while using the Jaunty's live CD; the speakers were dead silent!!!!

---

### Post by earthpigg on 2009-06-10
> **TBOL3 said:**
> Wait, did you say next LTS in October?  I though it would be next April.

[http://www.ubuntu.com/products/ubuntu/release-cycle](http://www.ubuntu.com/products/ubuntu/release-cycle)

you are correct, my mistake :P

10.04 will be LTS


the method i use to upgrade is clean install, as well.

i back up my /home, then _**selectively**_ restore settings for those applications i want - firefox, pidgin, and rhythmbox to start with then others as needed.

---

