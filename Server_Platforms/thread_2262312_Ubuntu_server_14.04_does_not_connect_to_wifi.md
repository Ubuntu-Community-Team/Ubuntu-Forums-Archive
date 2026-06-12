---
title: "Ubuntu server 14.04 does not connect to wifi"
date: 2015-01-24
forum: Server Platforms
---

### Post by tomi5 on 2015-01-24
hi all. i`m newish to linux and i have a bug maybe while installing ubunutu server 14.04 x64. i have a lenovo ideapad s10-3t and since i`m not using the laptotp i thought i`d use it as a home mini server for web application development. i installed the desktop version first and i could connect to my router from setup, but since the laptop is really low on hardware and after install the system was really slow so i thought of installing the server edition. now my problem is that when i select wlan0 i keep getting back to the essid screen after i set the passphrase. so my question is this a bug or driver issue? while my wired connection works perfectly, i dont want to use a wired connection for this laptop... can you please help me? or the only solution would be to set up the connection after the installation is complete?
thank you
LE: i tried searching on google but no results for this kind of problem

---

### Post by mörgæs on 2015-01-24
Here's a similar thread which might be worth following:
[http://ubuntuforums.org/showthread.php?t=2262402](http://ubuntuforums.org/showthread.php?t=2262402)

---

### Post by SeijiSensei on 2015-01-25
If it's going to run as a server, just connect it to your router with an Ethernet cable and avoid all the wifi hassle.

---

### Post by tomi5 on 2015-01-25
@morgaes: yes same question after my post, which doesn`t explain the "bug/feature" (if i may call it that). as i told you before when i'm installing the desktop version wifi as my primary network works perfectly, its only in the server version that i`m in a loop since its not connecting wioth no proper error message. it`s really questionable why is it working on the desktop[ version and why not it the server version, becase wlan0 gets tetected in both installs.

@seijisensei: it`s going to run as a server but only for me, and my web app, so i`m going to be the only user and since i have cables it would be convienient to use the wifi, cuz i can than move around with my laptop.

-----
its really strange to me as in why in desktop version it works and server version doesn`t. and thank you all for the reply.

---

### Post by mörgæs on 2015-01-25
One of the ideas behind a secure server is having only the necessary packages installed. As most servers have a wired connection wifi packages are probably (not sure, just guessing here) left out. I would not call it a bug but a wise decision.

Solutions to your problem: Adding wifi packages to the present server setup or install a light desktop like Lubuntu and add server packages later.

---

### Post by tomi5 on 2015-01-25
maybe... idk... but if it were a disabled feature as you say i shouldn`t be able to select wlan from config section. well for now i will keep the wired connection, and put the laptop somehere where it doesnt get in my way. i installed openssh and will manage server remotely.

PS: i tried to use the wpasupplicant package to connect to my router, i keept failing as well, also i did all the stuff in the sticky posts in the section you mentioned, and still no luck... anyways i wasted to much time on wifi and didnt manage to setup server for my needs... so issue/feature unsolved for now

thank you for support.

---

