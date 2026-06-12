---
title: "strange vsftpd behaviour"
date: 2005-03-17
forum: Server Platforms
---

### Post by Wusel on 2005-03-17
First I want to thank the Ubuntu-Team. Ubuntu is really really great.

Let us come to my question.

I installed vsftpd
and then created some local users with their home-directorys and some mount-bind stuff 
but when I try to log in as them it doesn't work.

The Problem is that my account works with no problem.
But when I try to log in as them it always goes to the password conformation, take some time and print "login incorrect"  #-o 


Anybody can help me to solve it

wu-ftpd make the same problem.
maybe it has something to do with the user-authentification in linux not in the ftpd

on the other hand login as another users works normally

 :arrow: I got it
the prob was that the home of the users has to be in /home and not in 
for example /home/xxx/

---

