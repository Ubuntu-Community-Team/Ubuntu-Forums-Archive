---
title: "SSH Server - Odd behaviour fixed by re-install, something to worry about?"
date: 2014-03-18
forum: Security
---

### Post by joshuarowley42 on 2014-03-18
Hi All,

I have been having some strange experiences with openss-server and just wanted to run them by you guys in the context of security, just to see if there is anything I should be worried about. 

A few weeks ago I was trying to login using public key authentication which was fine for my username and an additional user for backup tasks. I later had to change default user-groups around and as a result of running SSH in strict mode I was no longer able to login using public key auth (due to my primary group not being my username and not wanting my home directory to be owned by my primary group). I wasn't unduly bothered about this and understood the reasons so just left everything be, going back to logging in using a password. 

Two days ago however I suddenly could log in using public key auth and thought that this was very suspicious but hadn't got round to looking into it. Then my backup user account stopped being able to log in using public key, failing with the error:
```
protocol error: mtime.sec not delimited
```

I found nothing about this when googling so did:
```
sudo apt-get purge openssh-server
sudo apt-get install openssh-server
```

Which fixed the problem for the backup user. 


Should I be worried about any of this?

Thanks for your time everyone..

---

### Post by deadflowr on 2014-03-18
Oddly, I just read this
[http://thenextweb.com/insider/2014/03/18/operation-windigo-10000-infected-linux-servers-redirecting-half-million-visitors-malware-every-day/?utm_source=social&utm_medium=feed&utm_campaign=profeed#!Asah6](http://thenextweb.com/insider/2014/03/18/operation-windigo-10000-infected-linux-servers-redirecting-half-million-visitors-malware-every-day/?utm_source=social&utm_medium=feed&utm_campaign=profeed#!Asah6)

---

### Post by bashiergui on 2014-03-18
If you run ssh on port 22 open to the internet and you're using password authentication, then someone probably brute forced your password. Look in your auth logs during the time period you had password authentication only. You will probably see constant authentication attempts.

---

### Post by ant2ne on 2014-03-19
> **deadflowr said:**
> Oddly, I just read this
[http://thenextweb.com/insider/2014/03/18/operation-windigo-10000-infected-linux-servers-redirecting-half-million-visitors-malware-every-day/?utm_source=social&utm_medium=feed&utm_campaign=profeed#!Asah6](http://thenextweb.com/insider/2014/03/18/operation-windigo-10000-infected-linux-servers-redirecting-half-million-visitors-malware-every-day/?utm_source=social&utm_medium=feed&utm_campaign=profeed#!Asah6)I would definitely look into this particularly if this machine is internet facing and is a webserver.

---

### Post by joshuarowley42 on 2014-03-20
Thanks so much for your replies. Quite a thought provoking article by thenextweb. Strangely enough I was reading a script the other day which suggested changing from 22 which I will now do.

[http://wiki.metawerx.net/wiki/LBSA](http://wiki.metawerx.net/wiki/LBSA)


I don't think brute force was at fault here, there is only one login account facing the internet and the username is very obscure - I have observed auth log files in the past and never seen my username targeted (although it staggered me that there were ~50 attempts per hour..). I will however have a closer look and get back to you guys with more data..


Fairly sue I am just being paranoid.. :p

---

### Post by ant2ne on 2014-03-20
thenextweb's article states that this particular ssh trojan doesn't require a username or password or ssh keys. If you have that malware you are done.

changing the port from 22 is good idea, but it is still security through obscurity so be sure your other security practices are good.

---

### Post by unspawn on 2014-03-22
> **joshuarowley42 said:**
> Should I be worried about any of this?
Yes, for three reasons:
0) changing back to password auth,
1) not following up on errors immediately, 
2) "fixing things" by re-installing software.

0) Networking / SSH Best Practices exist for a reason. Any time you effectively degrade the machines security posture you need to think about better alternatives (not all solutions are equal) if any and implement measures to mitigate the weakness like adding an IP (range)  lockdown in the firewall and /etc/hosts.allow and the same plus command lockdown in that  users authorized_keys for example.
1) *Linux may be free to use but using Linux shouldn't be free of responsibilities.* Linux is the networked OS. Regardless of where the machine resides as admin you're responsible for keeping things safe and secure. Not only for you and the machines users but also for other 'net users (that's us). Your credentials (potentially) being leeched is one thing but we don't want to see your machine being used as a springboard to systems not under your control. Install Logwatch, have it mail you a daily report and *act on it*.
2) Use Linux the way it's supposed to be used. This means properly troubleshooting problems. If you don't know how then ask and *think before you act*. The reflex of killing processes and deleting entities is an unfortunate but common reflex found in both new and seasoned admins. Deleting "evidence" is the single best way to aid a cracker.


*That's not to say machines don't make mistakes but more often it's human users that do. Be aware of *Layer 8* problems ;-p

---

### Post by james114 on 2014-03-22
It is better to use a static IP address and set up your firewall only allows the IP.

I use this way for years, it is pretty safe.

---

