---
title: "I Trashed My Apache2 Webserver"
date: 2006-09-24
forum: Server Platforms
---

### Post by sauer on 2006-09-24
I wanted to set up virtual host, so I could run two websites.
I was reading how to do it, and I messed with my apache2.conf and my 000-default files.
And no, I didn't back them up first [-X 
Now nothing works.
Ok so I decided to go back to square one by uninstalling, and reinstalling apache.[-X 
Not a chance, it remembers all my screw-ups.
Apparently ,my computer doesn't know , I'm a dumb ***.
I even tryed uninstalling and putting the apache2 folder in the trash.And then reinstalling, that didn't work either.
Can anyone help me get back to square one ?

---

### Post by got_nix on 2006-09-24
check your conf files. httpd.conf and appache2.conf. if needs be go to the /etc/apache2/ and delete apache2.conf and httpd.conf if they still exist aftere you install and then install again 

lemme know if the problem still persist after that

---

### Post by sauer on 2006-09-24
Thanks I'll give it a shot.

---

### Post by sauer on 2006-09-24
Apache2.conf does not come back after install. (It's still in the trash)
Same thing with 000-default from sites enabled.
httpd.conf comes back as an empty file.
I don't think Ubuntu or DebIan use httpd.conf , but I could be wrong.
Maybe I could just paste someone elses file from a virgin install.:confused: 
Thanks for your help

---

### Post by etcpool on 2006-09-24
i don't have any ubuntu up for specification.,


but try removing it with the command like apt-get remove [all the packages you are unwanting] then run dpkg --purge to remove the configuration files...

then also [ the greatest part i remembered] to remove the some part of your apt configuration file describing about this (these) package(s)


that should cause your apt system to work like normal again (as you should move out your old config files).


hope u pass these well....


i should put the exact information to you if i could but. since my servers is in the mem-test progress for two of it... so,

i can't do anything with it... , and they still get hot :P



if you can't get through (sorry for my english) then i may post it back the howto when my machine gets ready in a few days.


hope u best luck :)





,etc

---

### Post by sauer on 2006-09-24
None of the files I purge come back after a reinstall.
I don't know why.
Maybe I'll check my Ubuntu CD for virgin files.:idea: 
Any suggestions would be of great help.

---

### Post by sauer on 2006-09-24
I fixed it with some help from this site.
[http://www.openfree.org/pet/index.php/Apache_2.0_-_Basic_-_on_Ubuntu_Linux](http://www.openfree.org/pet/index.php/Apache_2.0_-_Basic_-_on_Ubuntu_Linux)
Now everything works , including my virtual hosts.
Thanks to you all :biggrin: 
Paul

---

