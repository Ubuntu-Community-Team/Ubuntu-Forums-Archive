---
title: "Help with installing mod_python with LAMP"
date: 2010-05-04
forum: Server Platforms
---

### Post by Mitzukai on 2010-05-04
Hey Guys,

End of my first week after using ubuntu.
I have setup LAMP for the purposes of my own coding education, place to run php and python scripts.

LAMP seems to be setup fine and working - I even got php5 working with it - however I am having a lot more trouble getting python to work in much the same manner.

I have downloaded the mod_python from [http://www.modpython.org/](http://www.modpython.org/), unzipped it, tried to run ./configure and it said apxs was not installed.

After some reading it turns out I had to remove some apache-fork something and install apache-devfork (please forgive lack of exact names). 

After doing this the ./configure on mod_python passed the "finding apxs" test but then said it can't find apache2 at /sbin/apache2 and again aborted the configure.

I am not even sure if the way I am trying to install it is correct, but if anyone could throw any help my way I would greatly appreciated it.

running 10.4 (lucid)

---

### Post by Mitzukai on 2010-05-05
Hey all,

I have managed to fix my issue.
For anyone having trouble getting python working with apache2 (in ubuntu) there is an amazing helpful guide here: [http://www.howtoforge.com/embedding-python-in-apache2-with-mod_python-debian-etch](http://www.howtoforge.com/embedding-python-in-apache2-with-mod_python-debian-etch)

---

