---
title: "Ubuntu one cant authitificate"
date: 2012-07-27
forum: Ubuntu One (CLOSED)
---

### Post by rohezal on 2012-07-27
Hi guys,

I installed Ubuntu one on my Laptop like this guy said: 

[http://ubuntuforums.org/showthread.php?t=1949533](http://ubuntuforums.org/showthread.php?t=1949533)

I can't authentificate. The right password (checked on same laptop via website access) and email address did not work. 

If I try to register a new account he cant load the capture image. I think something is wrong with internet connection (no firewall is active, just a normal nat router). 

I installed and reinstalled everything twice, all files in /home/user are owned by user and I deleted ~/.cache/ubuntu one. 

Not sure what I can do. Any Ideas?

---

### Post by uzumakifahim on 2012-07-30
Are you able to login to your account @ one.ubuntu.com? If the answer is yes then your problem is on your Desktop side.

---

### Post by rohezal on 2012-07-30
Yes I can login via the web interface. I think its on my desktop site. I just wanted to ask if you can help to fix it :). Any ideas?

---

### Post by tigerente on 2012-08-09
Exactly the same problem here!  

I have to laptops, both new clean installs. While laptop 1 runs ubuntu one without a problem, laptop 2 has the exact same problem discribed here.  

I found out one difference: while laptop 1 has a ubuntu one token in the "Passwords and Keys" (seahorse), laptop 2 shows no token for ubuntu one.  

Might this be the problem? And how to solve it?

---

### Post by oscarivera9 on 2012-08-11
> **tigerente said:**
> Exactly the same problem here!  

I have to laptops, both new clean installs. While laptop 1 runs ubuntu one without a problem, laptop 2 has the exact same problem discribed here.  

I found out one difference: while laptop 1 has a ubuntu one token in the "Passwords and Keys" (seahorse), laptop 2 shows no token for ubuntu one.  

Might this be the problem? And how to solve it?

Same exact problem here!  Any help would be awesome.

---

### Post by wsilk on 2012-08-12
I'm getting the same issue.  I had installed Ubuntu 12.04 and I could login just fine.   I reinstalled with lubuntu 12.04, installed all the packages as listed in the linked thread, and now I get an authentication error.   

I've been searching and trying many different things, but nothing seems to work.

---

### Post by masticate on 2012-08-15
Please check my response to a similar issue and see if that works for you

[http://ubuntuforums.org/showthread.php?p=12173674#post12173674]("http://http://ubuntuforums.org/showthread.php?p=12173674#post12173674")

---

### Post by tigerente on 2012-08-15
> **masticate said:**
> Please check my response to a similar issue and see if that works for you

[http://ubuntuforums.org/showthread.php?p=12173674#post12173674]("http://http://ubuntuforums.org/showthread.php?p=12173674#post12173674")

  The support team of Ubuntu One just talked (emailed) me through the procedure you describe in your link. Worked for me.  

Roman Yepishev from Ubuntu One wrote: "... this ca-certificates problem is not reproducible currently so we are trying to find the reason the upgrade/update failed during system-wide installation or upgrade."

---

