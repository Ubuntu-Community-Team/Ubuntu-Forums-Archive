---
title: "root questions"
date: 2005-11-12
forum: Server Platforms
---

### Post by kris kincaid on 2005-11-12
If I were to say "In order to install a program in Linux, you need to have root access to the filesystem." would that be an accurate statement? This all pertains to a viruses ability to infect Linux, or specifically Ubuntu.

Thanks! :smile:

---

### Post by teaker1s on 2005-11-12
'sudo' works for most things- installing as this gives root permissions
fakeroot on some installs I believe but this can and has killed systems I've read posts on here

secondly most programs are repositories -so no risk of virus and thirdly 

./configure 
make
make install

will install and 'make uninstall' reverse the process

 binaries could cause a problem but who just installs any old junk and most just unpack and put a link to run

---

### Post by DJ_Max on 2005-11-12
A better term would be needing *proper permissions*.

---

### Post by 23meg on 2005-11-12
Take a look at this: [http://wiki.ubuntu.com/RootSudo](http://wiki.ubuntu.com/RootSudo)

---

### Post by LordHunter317 on 2005-11-12
[QUOTE=kris kincaid]If I were to say "In order to install a program in Linux, you need to have root access to the filesystem."[/quote]If you mean in the system directories, yes.  If you mean anywhere, no.

---

### Post by oskude on 2005-11-12
hi,

as far i know, you need root access only if you want to "integrate" (make install) your compiled programs system-wide (or if its a program than needs root access to run)  just compile as normal user and dont do  "sudo make install", you can run the program directly from where you compiled it (like home dir).

but with package managers like "apt-get install" you need root user access.

there are many ways to "install" a program on linux. but if you only use the distributions package manager and install only from official reposities the change of getting a virus is like 0.

other ways to get viruses would be "bugs" in system to allow attacks through net. and ofcourse noobs giving sudo/root password for a script that he/she got form a funny mail ;)

cheers
osku[de]

---

### Post by kris kincaid on 2005-11-12
Thanks for all the great info. I sorta knew the answer, but I could not properly articulate it. I wonder what people did to get information before forums like this? :D

---

### Post by DJ_Max on 2005-11-12
[QUOTE=kris kincaid]Thanks for all the great info. I sorta knew the answer, but I could not properly articulate it. I wonder what people did to get information before forums like this? :D[/QUOTE]
Long nights on Google.

---

