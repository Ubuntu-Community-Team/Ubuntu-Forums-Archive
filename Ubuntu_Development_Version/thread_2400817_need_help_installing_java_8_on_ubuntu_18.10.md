---
title: "need help installing java 8 on ubuntu 18.10"
date: 2018-09-10
forum: Ubuntu Development Version
---

### Post by idkwhatimdoing1.0 on 2018-09-10
Hello everyone I need help to install the full java jdk 8. For some reason every tutorial does not work. I have tried many things and my goal is to download and use Netbeans IDE 8.2 however it says I need the java 8 full jdk to code in the language I want. Every single thing won't work. I have tried setting the default java to 1.8 etc.. and have tried to change the config file of netbeans to the correct java however it still doesnt work. It used to work on Ubuntu 18.04 but it really doesnt work on Ubuntu 18.10. Someone please help me.

---

### Post by QIII on 2018-09-10
Moved to Ubuntu Development Version.

Hello!  18.10 is still in development and has not been released yet.

---

### Post by limax9s on 2018-09-15
[COLOR=#000000]After adding PPA repository we can move to installing java on Ubuntu. Executing apt search oracle-java command should now show multiple java versions available for install [/COLOR][URL="https://8ballpool.onl/"][COLOR=#000000][FONT=Arial]8 Ball Pool[/FONT]
[/COLOR][/URL][COLOR=#000000]
Namely they are java8 and java9 [/COLOR][URL="https://googlehangouts.ooo/"][COLOR=#000000][FONT=Arial]Google Hangout[/FONT]
[/COLOR][/URL][COLOR=#000000]
To install Java 8 execute:
$ sudo apt install oracle-java8-set-default
To install Java 9 execute [/COLOR][URL="https://omegle.onl/"][COLOR=#000000][FONT=Arial]Omegle[/FONT]
[/COLOR][/URL][COLOR=#000000][URL="https://omegle.onl/"]
[/URL][/COLOR][COLOR=#000000](see the below manual Java installation intructions if version 9 is unavailable and you need java version greater than 8.) :
$ sudo apt install oracle-java9-set-default[/COLOR]

---

