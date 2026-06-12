---
title: "sudo: unable to resolve host Lair"
date: 2008-06-10
forum: Security
---

### Post by Fenris_rising on 2008-06-10
hi all

when using terminal im getting this message 

sudo: unable to resolve host Lair

when i do something like;
 
i.e. sudo gedit /etc/samba/smb.conf

it doesnt seem to effect whatever i am doing, but, what is it and why has it suddenly begun to occur?

---

### Post by Dr Small on 2008-06-10
Post the result of these two commands, please:
```
cat /etc/hosts
cat /etc/hostname
```

---

### Post by HalPomeranz on 2008-06-10
You might want to check out this thread:

[http://ubuntuforums.org/showthread.php?t=807171](http://ubuntuforums.org/showthread.php?t=807171)

Sounds like you're having the same issue.

---

### Post by Hotadesu on 2008-06-11
This just happened to me.

Write in the terminal:

sudo gedit /etc/hosts

Then, add the following line at the beginning:

127.0.0.1 denise

(In my case, "denise" is my computer's name... change it for your computer's name) and save.

---

### Post by Fenris_rising on 2008-06-11
```
fenris@Lair:~$ cat /etc/hosts
127.0.0.1 localhost
127.0.1.1 Lair.TOTSVILLE

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
fenris@Lair:~$ cat /etc/hostname

```

i have changed the top line as follows;
```
127.0.0.1 Lair
127.0.1.1 Lair.TOTSVILLE
```
now i get this in terminal when i close i.e. gedit /etc/*****
```
Usage:program_name [address][:port]Usage:program_name [address][:port]Usage:program_name [address][:port]fenris@Lair:~$ sudo gedit /etc/hosts
```

@Hal looked at the thread you indicated and have adjusted my host file in a similar fasion. result sorted ;)
now im not sure i can assist in why it suddenly began but here goes. my hostname was picked during install.
samba was installed later and i had to add a line to gain permission to create shares, i also changed the 'group'
from the default.

 workgroup = TOTSVILLE       << changed from the default 'workgroup'
 usershare owner only = False<< added this whole line

at the time nothing occured. BUT the latest updates requested if i wanted to keep my current smb.conf or install the newer 1. i opted for the newer one, last time i refused a similar offer it caused severe problems later, and of course i had to go back in to smb.conf to re-edit as before. this is the only thing that was done after the latest updates and emmediately before it started throwing the message up. thanks for all your help guys, clicking your thanks ;)

---

