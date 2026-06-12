---
title: "LAMPerl? + Which Version?"
date: 2007-04-26
forum: Server Platforms
---

### Post by skelooth on 2007-04-26
I need to set up an intranet site and was considering ubuntu server edition. I have set up lamp on ubuntu before, but I am going to need perl and mod_perl to be up and functioning. Unfortunately I have no idea how to do that :) There seems to be a giant maze of seemingly related packages in the repositories.

Also curious, should I be using the LTS edition? I will not be around to maintain the software/server, and want to leave behind something rock solid as possible.

---

### Post by skelooth on 2007-04-27
anyone?

---

### Post by rsermilik on 2007-04-28
Hopefully the stability is the same on both versions!
7.04 is supported until 2008 and 6.06 LTS until 2011. Thats a big issue in production!
Do you need facilities from 7.04 that is not included in 6.06 LTS?

Try take a look on the Apache homepage [www.apache.org](www.apache.org). There you'll find all the documentation .

---

### Post by skelooth on 2007-05-04
That's a good point, no, I do not need anything from fiesty that is not already in LTS. LTS it is :)

I will be back with questions if i can't get LAMPerl working the way I want

---

### Post by tr333 on 2007-05-05
perl is included in ubuntu by default.  mod_perl can be installed with the "libapache2-mod-perl2" package for apache2 or "libapache-mod-perl" for apache1.  you will then need to enable the module with "sudo a2enmod".  you can disable it later with "sudo a2dismod".

---

