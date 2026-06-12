---
title: "How to limit a user account even further"
date: 2006-04-13
forum: Server Platforms
---

### Post by ashrack on 2006-04-13
This is how the desktop looks like for the account STUDENT who bellongs to the following groups:
```
divjak@zavod1:~$ groups student
student : student adm cdrom floppy audio plugdev
```

[ATTACH]8285[/ATTACH]

Since this machine will be used by lots of students, I would like the following settings for the account STUDENT:
1. students are only allowed access to what is on the DESKTOP and nothing else.
2. students mustn't be allowed to change anything on the desktop itself(deleting, changing, rearanging icons)
3. their home directory should have a QUOTA set of 5GB

ps. if theres something more to add or U would like to change someting please tell me. I would like all the help I can get..

---

### Post by ubernoob on 2006-04-14
You should have a look at edubuntu. Thats a distro made for schools. Your security questions are quite system wide, so i guess you don't get annyone to write a book for you ;) 

Anyway: 

1. even if you remove every icon, people could still try ctrl+alt+f2 or other ways to execute a command. 
2. you can chown the home folder for students to root. And only allow read and excecute.
3. Search in google for "linux disk quota" and you will find tons of howtos.


but...

If this is for a school and you really are concerned about the security, i would suggest [paid support.]("http://www.ubuntu.com/support/supportoptions/paidsupport")

or have a look at [Secure Public Access Internet Workstations]("http://linuxgazette.net/issue25/singer.html")

---

### Post by ashrack on 2006-04-15
[QUOTE=ubernoob]
If this is for a school and you really are concerned about the security, i would suggest [paid support.]("http://www.ubuntu.com/support/supportoptions/paidsupport")[/quote]
It must be as free as possible. Since this school and even our country is almost M$ only. And it was hard enough to convince school leaders that we may try linux.

or have a look at [Secure Public Access Internet Workstations]("http://linuxgazette.net/issue25/singer.html")[/QUOTE]
looking at it right now. looks quite interesting.


btw. Could this tool be of any help, but it is designed for KDE and I use GNOME.
[http://extragear.kde.org/apps/kiosktool/](http://extragear.kde.org/apps/kiosktool/)

---

### Post by ubernoob on 2006-04-15
That looks like a very good tool, although i have never tried it. And i have actually never tried to lock down a computer before, so i can't give you much more advices, unless i start reading on the topic. But it should be easier and more secure with linux than windows to do what you are asking for.

One thing is to lock the user to not change the system. What might be more difficut is making one user not able to tamper with another users that logs in to the same pc and account.

---

### Post by ashrack on 2006-04-15
but will this tool also work on GNOME, since its apperantly designed for KDE

---

### Post by ubernoob on 2006-04-15
most of them will only work on KDE and not Gnome there might be some few options that works on both.

---

