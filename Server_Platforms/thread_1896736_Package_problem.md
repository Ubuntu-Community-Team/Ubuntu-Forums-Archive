---
title: "Package problem"
date: 2011-12-17
forum: Server Platforms
---

### Post by AndreaFred on 2011-12-17
Hi there!
I'm sorry about my bad english but I'm not english. I hope you'll understand me because I've a little problem with Ubuntu Server 11.04.3 (this is the first time i use Ubuntu server).

I have to make a Cloud, so I tried to install Eucalyptus but when i wrote on CLI (logged as root) "apt-get install [package name]" it returned: "E: unable to locate package [package name]". What's wrong? 
I've checked the Internet connection and is it ok. 

Thanks to all! :)

---

### Post by drmrgd on 2011-12-17
Are you sure you typed the package name correctly?  When I look, all of the Eucalyptus packages have a lowercase "e".  If you type:

```
sudo apt-get install euca
```

and then hit the tab key twice right after it, you should see a list of the relevant packages.  See if one of those is the one you want.

---

### Post by AndreaFred on 2011-12-17
Thanks for the answer.

i've tryed to do that but the package name is correct. Maybe could be possible a wrong or inexistent proxi? Because when i was installing Ubuntu Server, it asked me if i wanted to use a proxi...i left the space, naively, empty... could be that te cause of my problem?

---

### Post by crashed111 on 2011-12-17
Does an "apt-get update" run with no issues?

---

### Post by AndreaFred on 2011-12-18
No...it return errors... but if i "ping" to any host it perfectly works.

---

### Post by AndreaFred on 2011-12-18
Solved! I had to change the proprieties of sources.list.

Thanks to all! ;)

---

