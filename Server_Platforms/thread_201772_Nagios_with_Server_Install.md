---
title: "Nagios with Server Install"
date: 2006-06-22
forum: Server Platforms
---

### Post by greeneagle on 2006-06-22
I have installed the server version of Ubuntu 6.06 for the sole purpose of running [Nagios]("http://nagios.org").  I have downloaded the lastest version of Nagios and when I go to compile it (run ./configure) I found out that I didn't have gcc on the machine.  So, I went and used aptitude to install gcc-4 and make.  After I did that, I get an error:
```
configure: error: no acceptable C compiler found in $PATH
```
I am not a developor, so I don't want to go through and set up a lot 

My question: What dev packages do I use that should let me complile Nagios out of the box?

PS - I am a redhat user, so I am familiar with rpms and such, and I thought I would give this Ubuntu (Debian) thing a try.

---

### Post by deuce868 on 2006-06-22
Did you log out/in between installing gcc and make? Your path is setup when you login so I'm not sure that adding the package would have ammended your current PATH. 

On side note, is there a reason you can't use the debian nagios packages? If you're used to rpms and such it seems you would first just run to apt-get install nagios-common, mysql, etc. 

apt-cache search nagios

---

### Post by DanielArdelian on 2006-06-22
```
 apt-get install build-essential 
```

[http://packages.ubuntu.com]("http://packages.ubuntu.com")

---

### Post by LordHunter317 on 2006-06-22
[QUOTE=deuce868]Did you log out/in between installing gcc and make? Your path is setup when you login so I'm not sure that adding the package would have ammended your current PATH.[/quote]It's installed in a PATH directory, so it's not an issue.

> On side note, is there a reason you can't use the debian nagios packages?The Ubuntu ones are a major version out of date.  Debian jsut recently started packaging nagios2.

That being said, you could probably pin in the right packages from etch if you wanted to.

---

### Post by deuce868 on 2006-06-22
Oops, you're right. I saw:
2:1.3-cvs.20050402-8ubuntu7: all

and thought it was the nagios 2 branch in the package list.

---

