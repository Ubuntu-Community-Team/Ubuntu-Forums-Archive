---
title: "Secure mount information"
date: 2009-05-17
forum: Security
---

### Post by terrrorr on 2009-05-17
Hi,

Couple days ago i was interested about to create bash script which is able to check if shared directory is already mounted. I was surprised when i found my mount parameters and info from /etc/mtab

---
//192.168.x.x/Tem**t /home/<home directory>/Mount/Tem**t cifs rw,username=[COLOR="Cyan"]<my account>[/COLOR],password=[COLOR="Cyan"]<my password>[/COLOR],iocharset=utf8,file_mode=0777,dir_mode=0777,uid=1000 0 0
--- 

I'm open for suggestion how I can secure /etc/mtab 

- Terrrorr

---

### Post by terrrorr on 2009-05-21
hmm...

Is there any implications if I just change its (/etc/mtab) access rights (chmod 700 /etc/mtab). In my opinion, this is quite crucial thing if you need to deploy Linux servers in multi platform environment. 

- Terrrorr

---

### Post by uupreti on 2009-05-21
you can install encrypting program and keep it safe and I saw couple of days ago about truecrypt for ubuntu.

---

### Post by albinootje on 2009-05-21
> **terrrorr said:**
> 
I'm open for suggestion how I can secure /etc/mtab 


Interesting. Can you check on [http://launchpad.net](http://launchpad.net) whether a bug report is already filed ?
If not, file a bug report.

And you can of course test whether chmod 600 /etc/mtab works or not.

---

### Post by terrrorr on 2009-05-25
Hi,

Here is some status information if you are interested this case:

This is so called "feature" which needs to be fixed. I created a bug report, so we need to just wait and see what will happen.

I did found another "similar" case:

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=298725](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=298725)

- Terrrorr

---

