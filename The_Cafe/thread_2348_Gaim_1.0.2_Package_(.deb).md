---
title: "Gaim 1.0.2 Package (.deb)"
date: 2004-10-27
forum: The Cafe
---

### Post by oddabe19 on 2004-10-27
In my spare time... well... mainly cause i was bored.  I created a Gaim 1.0.2 deb package from source because i wanted 1.0.2 and it wasn't in universe yet.
so here it is if anyone needs/ wants it. (3.3 megs)

[http://home.comcast.net/~amsilveira/gaim-1.0.2_1_ubuntu_i386.deb](http://home.comcast.net/~amsilveira/gaim-1.0.2_1_ubuntu_i386.deb)

---

### Post by nuopus on 2004-10-28
[QUOTE=oddabe19]In my spare time... well... mainly cause i was bored. I created a Gaim 1.0.2 deb package from source because i wanted 1.0.2 and it wasn't in universe yet.
 so here it is if anyone needs/ wants it. (3.3 megs)
 
 [http://home.comcast.net/~amsilveira/gaim-1.0.2_1_ubuntu_i386.deb]("http://home.comcast.net/%7Eamsilveira/gaim-1.0.2_1_ubuntu_i386.deb")[/QUOTE] Ya I made my own too. Only problem now is that when I try to upgrade the world it will try to downgrade it to what is in the repos because of the version number. Ubuntu is 1:1.0 and the deb I made is 1.0.2. I think apt thinks that 1:1.0 is a higher version? I dunno .... so I just compiled it and let paco manage the source I have installed.
 
 If you have never seen paco ... it logs all files created during a build and puts it into a list. You can then remove it with paco and it just removes all added files in the make install. Very cool!

---

### Post by kamstrup on 2004-10-28
[QUOTE=nuopus]Ya I made my own too. Only problem now is that when I try to upgrade the world it will try to downgrade it to what is in the repos because of the version number. Ubuntu is 1:1.0 and the deb I made is 1.0.2. I think apt thinks that 1:1.0 is a higher version? I dunno .... so I just compiled it and let paco manage the source I have installed.
 
 If you have never seen paco ... it logs all files created during a build and puts it into a list. You can then remove it with paco and it just removes all added files in the make install. Very cool![/QUOTE]
 It might be worth mentioning that your package does /not/ support msn ;-P

---

### Post by im_ka on 2004-10-28
[QUOTE=kamstrup]It might be worth mentioning that your package does /not/ support msn ;-P[/QUOTE]

msn is not worth mentioning :D

---

### Post by nuopus on 2004-10-28
[QUOTE=kamstrup]It might be worth mentioning that your package does /not/ support msn ;-P[/QUOTE]
 My package works with MSN because I use it to chat with my family in another state. If you want you can leave an email for me to send it to .... the ONLY problem I am having with 1.0.2 is that the package name is 1.0.2 and not 1:1.0.2 I guess, so when you apt-get install upgrade it tries to download to the one in the repos.

---

