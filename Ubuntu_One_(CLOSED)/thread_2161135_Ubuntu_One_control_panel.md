---
title: "Ubuntu One control panel"
date: 2013-07-09
forum: Ubuntu One (CLOSED)
---

### Post by spazzeri on 2013-07-09
Hello,

After a system upgrade from 12.10 to 13.04 (64-bit), the Ubuntu One control panel displays 'Getting information, please wait' forever.

File changes in a synced folder seem to be picked up normally.

What might be wrong ?

---

### Post by spazzeri on 2013-07-10
This answer helps my U1 controlpanel sign-in issue: [http://askubuntu.com/a/297110/1780](http://askubuntu.com/a/297110/1780) 

 I had a more recent version (>= 0.4) of module oauthlib under /usr/local/lib/python2.7/;
I uninstalled it and then the U1 control panel sign-in process completed.

---

### Post by Hexxus on 2013-07-12
Like spazzeri recommended, If its still happening try removing it and re-installing it. I had an issue kind of similar when I did the upgrade from 12.04LTS to 12.10 to 13.04. Once I removed it - re-installed it and signed in things were good.

---

