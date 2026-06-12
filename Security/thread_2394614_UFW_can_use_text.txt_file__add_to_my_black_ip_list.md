---
title: "UFW can use text.txt file  add to my black ip list ??"
date: 2018-06-19
forum: Security
---

### Post by joehk2018 on 2018-06-19
Hello , 

I have many black list ip  , but if i can only one by one to add the ip address i will add very long time. 
How about can easy to add my text file list ?

Thank

---

### Post by Habitual on 2018-06-20
I don't think ufw can "read" a list of Ips.txt.

How are you adding a single IP?
Each line in file is single IP? 

Simple "for i" loop in terminal can do the job.

something *like*
```
for i in `cat file`; do ufw deny from $i ; done
```
Please have a gander at [https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW) and
[https://help.ubuntu.com/community/IptablesHowTo#Saving_iptables](https://help.ubuntu.com/community/IptablesHowTo#Saving_iptables) for reference.

Good luck

---

