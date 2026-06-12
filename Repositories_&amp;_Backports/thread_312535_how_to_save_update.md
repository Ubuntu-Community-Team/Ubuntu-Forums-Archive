---
title: "how to save update?"
date: 2006-12-04
forum: Repositories &amp; Backports
---

### Post by jakonj on 2006-12-04
I updated my list of programs (sudo apt-get update) but i need to save this update (is this possible?). What files do i need to save (where are those updates stored)?

Tnx in advance

---

### Post by bapoumba on 2006-12-05
I am not sure this is quite the answer you are looking for.
```
dpkg --get-selections > my_packages.txt
```
will create the my_packages.txt file with all the packages (and dependencies) that are installed.

Additionnaly :
```
dpkg --set-selections < my_packages.txt
```
will install all the packages listed in the file. You can play with it, ie clone an installation on another computer, edit a handy list of packages to get if you are making a fresh reinstall ... You name it ;)

---

### Post by jakonj on 2006-12-05
i need to save update with all programs that are curently in my database os programs (updatet in synaptic) and i need possibility to when i do fresh install of Xubuntu that i dont need to go on net and do ``sudo apt-get update``. I have all my programs in one folder (with all dependencies and stuff) so I want to be able to install all those programs with ``apt-get install ...(name of the program)`` without net connection.

So: offline pc with all programs which is able to install programs with ``sudo apt-get instal ... (program)``

p.s. i tried this on ubuntu but i needed to update programs database (apt-get update). I puted all programs (and dependencies) in /var/cache/apt/archives/ and it worked. But i need to do this on offline PC. I want to expand my programs list but i need to set this firest (it`s to hard to do this manualy without apt-get)!

another p.s. dont look at my grammar errors :)

---

### Post by bapoumba on 2006-12-05
Okay, excuse me for misunderstanding ;)
So you what you need are packages on a CD that you are able to apt-get on an offline computer.
You probably can adapt [this]("http://www.batmat.net/apt-offline/index.html#abstract") to a CDrom.

Other links :
[http://cvs.lp.se/doc/apt-doc/offline.text.gz]("http://cvs.lp.se/doc/apt-doc/offline.text.gz")
[https://help.ubuntu.com/community/LocalAptGetRepository]("https://help.ubuntu.com/community/LocalAptGetRepository")

I have never done this myself ;)

---

