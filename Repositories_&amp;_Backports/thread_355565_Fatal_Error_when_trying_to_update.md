---
title: "Fatal Error when trying to update :|"
date: 2007-02-07
forum: Repositories &amp; Backports
---

### Post by dustman on 2007-02-07
Hello!


I have quite a problem...today  I started Ubuntu, it said that I had updates ready to be installed. I entered the update window, selected the desired packages, then pressed Install Updates, then Apply,  but I got this error: "E: Can't write /root/.synaptic/selections.proceed"...and I really don't know how to move around the root thing and all that :)...Any suggestions are most welcomed ...

---

### Post by bapoumba on 2007-02-07
Could you post the errors to **sudo aptitude update** ? This will not upgrade. If there is **NO ERROR**, you can proceed with **sudo aptitude upgrade**. Paste the error in the other case, along with the output to **cat /etc/apt/sources.list**.

---

### Post by dustman on 2007-02-07
The error is :"E: Can't write /root/.synaptic/selections.proceed",  I pasted it in the previous post too :)...anyway, these are the /etc/apt/source.list: 


[HTML]
deb http://ro.archive.ubuntu.com/ubuntu dapper main restricted
deb-src http://ro.archive.ubuntu.com/ubuntu dapper main restricted

## MAJOR BUG FIX UPDATES produced after the final release
deb http://ro.archive.ubuntu.com/ubuntu dapper-updates main restricted
deb-src http://ro.archive.ubuntu.com/ubuntu dapper-updates main restricted

## UBUNTU SECURITY UPDATES
deb http://ro.archive.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://ro.archive.ubuntu.com/ubuntu dapper-security main restricted

## UNIVERSE AND MULTIVERSE REPOSITORY
deb http://ro.archive.ubuntu.com/ubuntu dapper universe multiverse
deb http://ro.archive.ubuntu.com/ubuntu dapper-security universe multiverse
deb-src http://ro.archive.ubuntu.com/ubuntu dapper universe multiverse
deb-src http://ro.archive.ubuntu.com/ubuntu dapper-security universe multiverse

## BACKPORTS REPOSITORY
deb http://ro.archive.ubuntu.com/ubuntu dapper-backports main restricted
deb http://ro.archive.ubuntu.com/ubuntu dapper-backports universe multiverse
deb-src http://ro.archive.ubuntu.com/ubuntu dapper-backports main restricted
deb-src http://ro.archive.ubuntu.com/ubuntu dapper-backports universe multiverse

## dapper-commercial by Canonical
deb http://archive.canonical.com/ubuntu dapper-commercial main

## WINE
deb-src http://wine.budgetdedicated.com/apt dapper main


#AUTOMATIX REPOS START

deb http://people.ubuntu.com/~seb128/deb ./

deb http://www.getautomatix.com/apt dapper main

deb http://archive.ubuntu.com/ubuntu dapper-updates universe multiverse
#AUTOMATIX REPOS END
[/HTML]

Well I think this will be enough...I really don't know that's the problem...And I couldn't get to 
/root/.synaptic/selections.proceed, dunno why...."cd /root/.synaptic/selections.proceed" returns Permission denied, and "sudo cd /root/.synaptic/selections.proceed" returns sudo : cd : command not found...

---

### Post by bapoumba on 2007-02-07
Okay, from what I understood from your first post, this was an error from Synaptic. As I did not find anything about it in google, I just asked you to run ```
sudo aptitude update
```. Sorry to ask again, but is it the error you get with this command ?

---

### Post by dustman on 2007-02-08
Sorry about the misunderstanding, I was dead tired when replied with the second post :|....I was not clearly understanding what were you trying to tell me...Now I ran "sudo aptitude update", and no error was returned, I also tried "sudo apt-get update", and also nu error was returned....Now the thing is that whenever I try to update the system from synaptic, I get that error(from the 1st post)...As I noticed, there might be a problem with one of the update packages. I have there as an update, Rhythmbox 0.9.4.1-ubuntu1 ....and when I try to uncheck it and install the updates, just after I pressed Install Updates, I get the error I was talking about: "E:Can't write ....", and if I let it checked, I get to the point where I have to press Apply(in that window the Rhythmbox update is in the NOT AUTHENTICATED), and here I also get the same error...I'm clueless.....:(

PS. The application where I get the error is the Software Updates app.....anyway, I tried with synaptic but I get the same error...:P

---

### Post by bapoumba on 2007-02-08
Hello :)

Ok, if the update is fine, run  :
```
sudo aptitude update
sudo aptitude upgrade
```
Post here any error that comes out.

This may be a problem with synaptic, and not with the update in itself. that way we'll find out.

One more question : do you have any error if you run 
```
gksudo gedit
```
?

---

### Post by dustman on 2007-02-10
thanks for your help man....I  solved it finally. Wrote "sudo aptitide upgrade" and worked out fine....i owe u one ;)

Cheers!

Radu

---

### Post by dustman on 2007-02-10
oh, redarding "gksudo edit", well, it doesn't give me an error, but a warning :
[HTML](gedit:5626): GNomeUI-Warning **: While connecting to session manager: Authentication Rejected, reason : None of the authentification protocols specified are supported and host-based authentification failed.[/HTML]
 anyway, it opens gedit.

---

### Post by bapoumba on 2007-02-10
Yes, everyone has this warning. It's a very old bug and gedit will work okay ;)

---

### Post by techningeer on 2010-07-17
I just ran ```
sudo aptitude upgrade
``` and everything went smoothly. After installing the updates with Aptitude, I had to run ```
apt-get -f install
```. This finished the update. Synaptic and Update Manager work fine now.

P.S.- I am using Ubuntu 10.04 LTS

---

