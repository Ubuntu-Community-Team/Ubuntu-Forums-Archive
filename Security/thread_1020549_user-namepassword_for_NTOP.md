---
title: "user-name/password for NTOP"
date: 2008-12-24
forum: Security
---

### Post by nss0000 on 2008-12-24
Gents:

I've DLoaded NTOP and - and after some "permissions" issues with directories - installed the program. On my browser I can view various NTOP_outout at //localhost:3000  . There's pages of stuff.

What I can't do is assert the <configure>_tab cause I'm requested to enter <usrname/passwd> ... well I don't remember ever entering such values to the program and "my own" values are not accepted. 

Certainly I don't know if I need to :configure: anything since NTOP is apparently doing whatever it does without my help. But, NTOP seems to expect something I've never given it and this bothers me. Do I need to be concerned?

---

### Post by lemming465 on 2008-12-28
If you have vast experience running ntop and Debian derived distributions, you would intuit the need to consult /usr/share/doc/ntop/README.Debian, where they duely instruct you to run *sudo ntop -A* **before** running *sudo /etc/init.d/ntop start*.  "ntop -A" queries you for the administrative password, and initializes /var/lib/ntop with various files. Ordinary mortals just starting out with ntop may be forgiven for overlooking this.  It's probably the source of your directory and permissions issues, as a side effect.

The default settings for ntop are fairly good; if you have no need to tamper with them, be happy.  I'm not sure if you can re-initialize ntop easily after the fact.  If you are willing to reinstall it, which will lose the current DB contents, what I'd suggest is: ```
sudo -i
/etc/init.d/ntop stop
apt-get purge ntop
apt-get install ntop
ntop -A
/etc/init.d/ntop start
```

---

