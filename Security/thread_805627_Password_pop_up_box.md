---
title: "Password pop up box"
date: 2008-05-24
forum: Security
---

### Post by king2042 on 2008-05-24
Hi all,

   As a new convert from XP to Ubuntu I am very impressed with what I have seen so far apart from one small issue concerning passwords.
 
   My problem is when I start any application requiring my user password (add/Remove etc) the application freezes waiting for me to enter the said password, but no box pops up for me to enter it in, until I start the app again "over" the already running/frozen original. Then the box will pop up and everything is back to normal and I can carry on with what I was doing.   

I hope this makes sense to you all as I'm still getting my head around the terminoligy in Linux.:confused:

Thanks in advance.
Dave

---

### Post by lswest on 2008-05-24
if you open a terminal and do this ```
sudo apt-get install --reinstall gksu gksudo
``` it might solve the problem, as gksu and gksudo are the programs in charge of prompting you for a password, and if they seem to have a problem, re-installing it might help.

---

### Post by king2042 on 2008-05-24
> **lswest said:**
> if you open a terminal and do this ```
sudo apt-get install --reinstall gksu gksudo
``` it might solve the problem, as gksu and gksudo are the programs in charge of prompting you for a password, and if they seem to have a problem, re-installing it might help.

Amazing! Thanks for the very quick and **Successful** solution.

Thanks for the helping hand.:)
Regards
Dave

---

### Post by lswest on 2008-05-24
No problem at all, glad i was able to help ^^ and if you want, you can click the blue medal on the bottom right of my post to "thank" me ;)  </vanity> :P  Hope you enjoy your Ubuntu experience, and welcome to the forums :)

*edit* haha, thanks for the thanks :)

---

