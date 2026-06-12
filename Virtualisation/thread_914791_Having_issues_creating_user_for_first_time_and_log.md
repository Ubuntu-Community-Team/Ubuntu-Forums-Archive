---
title: "Having issues creating user for first time and logging back in.  Server 2.0 RC2"
date: 2008-09-09
forum: Virtualisation
---

### Post by chootarlaal on 2008-09-09
anyone have issues with Server 2.0 RC2, creating a user for the first time?  i run VMWare as root and then try to create a user, but it keeps erroring out.  this was with konqueror, when i tried with firefox, it worked.

i managed to create a user "user1" which is my regular username under kubuntu.  when i create the "user1" as an administrator, how do u set the password?  because when i log out of root and try to log back in with "user1", it asks for the password.  i tried the password i use when i log into kubuntu and also the root password, neither works.

do i have to close firefox and restart or just log out.  neither is working when i try to log in with "user1", i get teh error message:
"you do not have permissions to login to the server" (if i use my kubuntu passwd)
"login failed due to a bad username or password" (if i use the root password)

im running Server 2.0 RC2 build 110948.

---

### Post by dark_phantom on 2008-09-09
Both times I installed RC1 and RC2, I added my id as an administrator while installing VMware.  I used sudo instead of su to root both times as well.

---

### Post by chootarlaal on 2008-09-10
im sure im doing it as root and the id is an admin.  im not sure how sudo differs from su, ill try it again, thanks for the hint.

edit:  actually i did use the directions on this thread listed below and it uses sudo.  i still cant figure out whats wrong.
[http://ubuntuforums.org/showthread.php?t=779934](http://ubuntuforums.org/showthread.php?t=779934)

---

### Post by bodhi.zazen on 2008-09-10
Well, you are running a beta version ...

Although I did not have your exact problem, I had significant issues with the beta version and do not advise running it for anything other then beta testing.

log into the web tool as root. Make a new user, give the new user any password you like.

log off the web tool and log in as the new user. The password you set in the web tool has nothing to do with your login password, sudo, or your root password.

---

### Post by chootarlaal on 2008-09-10
server RC2 is beta, just realized that. 

but there is the problem that im having, the tool NEVER asks me to set a password for the new user.

---

