---
title: "server keeps getting hacked"
date: 2017-10-05
forum: Security
---

### Post by micahpage on 2017-10-05
I had an issue with my server being hacked. Luckily i have snapshots to restore the server to a previous state, but whatever vulnerability was there remains. I rejected the hackers IP address as he kept logging into IRC, reset root pass, and updated. But im not sure what else to do?
Is there a linux kernel vulnerability going on recently?

---

### Post by QIII on 2017-10-05
Hello!

There could be many vulnerabilities, but we know nothing about how you have set up your server or what you have done to secure it.  Is this a web server?  Where is it deployed?  Is it hosted?  What actions have you taken to harden your server?

---

### Post by micahpage on 2017-10-05
It servers the website  [https://python-forum.io/index.php](https://python-forum.io/index.php)
Its hosted as a VPS
I run system updates about once a month. We have a few trusted users with SSH login credentials with root privileges. Its using Apache with a basic firewall. 


The server was hacked last November, and currently today, both by Russian IP addresses.

---

### Post by QIII on 2017-10-05
What have you done to harden the server?  What was the attack vector?

---

### Post by micahpage on 2017-10-05
i started going along this guide
[https://www.thefanclub.co.za/how-to/how-secure-ubuntu-1604-lts-server-part-1-basics](https://www.thefanclub.co.za/how-to/how-secure-ubuntu-1604-lts-server-part-1-basics)
I have done about 1-10 so far. 

For #7 there was no file [COLOR=#000000][FONT=Monaco]/etc/bind/named.conf.options
[/FONT][/COLOR]

Im not sure what their method of entry was or what their intention was. Here is a screenshot of before i restored the server.
[https://imgur.com/a/dEiRu](https://imgur.com/a/dEiRu)

---

### Post by QIII on 2017-10-06
Are you using Fail2Ban for your SSH access?  LogWatch?  LogCheck?  Have you reviewed your auth.log?  What rules have you set in iptables?

---

### Post by micahpage on 2017-10-06
I did fail2ban for ssh and set it to ssh and sshd for my the new port, the others i have not done.


if i check auth.log i have stuff like this from 5 days ago
```
Oct  1 07:30:06 python-forum sshd[19214]: Failed password for root from 58.218.198.165 port 25401 ssh2Oct  1 07:30:06 python-forum sshd[19214]: Received disconnect from 58.218.198.165: 11:  [preauth]
Oct  1 07:30:06 python-forum sshd[19214]: PAM 2 more authentication failures; logname= uid=0 euid=0      tty=ssh ruser= rhost=58.218.198.165  user=root
Oct  1 07:30:06 python-forum sshd[19219]: Failed password for root from 189.80.37.69 port 39318 ssh2
Oct  1 07:30:07 python-forum sshd[19219]: Received disconnect from 189.80.37.69: 11: Bye Bye [preauth]
Oct  1 07:30:09 python-forum sshd[19221]: pam_unix(sshd:auth): authentication failure; logname= uid=0    euid=0 tty=ssh ruser= rhost=189.80.37.69  user=root
Oct  1 07:30:11 python-forum sshd[19221]: Failed password for root from 189.80.37.69 port 41586 ssh2
Oct  1 07:30:12 python-forum sshd[19221]: Received disconnect from 189.80.37.69: 11: Bye Bye [preauth]
Oct  1 07:30:14 python-forum sshd[19223]: pam_unix(sshd:auth): authentication failure; logname= uid=0    euid=0 tty=ssh ruser= rhost=189.80.37.69  user=root
Oct  1 07:30:17 python-forum sshd[19223]: Failed password for root from 189.80.37.69 port 44122 ssh2
Oct  1 07:30:17 python-forum sshd[19223]: Received disconnect from 189.80.37.69: 11: Bye Bye [preauth]
Oct  1 07:30:18 python-forum sshd[19225]: pam_unix(sshd:auth): authentication failure; logname= uid=0    euid=0 tty=ssh ruser= rhost=189.80.37.69  user=root
Oct  1 07:30:20 python-forum sshd[19225]: Failed password for root from 189.80.37.69 port 46878 ssh2
Oct  1 07:30:20 python-forum sshd[19225]: Received disconnect from 189.80.37.69: 11: Bye Bye [preauth]
Oct  1 07:30:22 python-forum sshd[19227]: pam_unix(sshd:auth): authentication failure; logname= uid=0    euid=0 tty=ssh ruser= rhost=189.80.37.69  user=root
Oct  1 07:30:24 python-forum sshd[19227]: Failed password for root from 189.80.37.69 port 48726 ssh2
Oct  1 07:30:24 python-forum sshd[19227]: Received disconnect from 189.80.37.69: 11: Bye Bye [preauth]
Oct  1 07:30:26 python-forum sshd[19229]: pam_unix(sshd:auth): authentication failure; logname= uid=0    euid=0 tty=ssh ruser= rhost=189.80.37.69  user=root
Oct  1 07:30:29 python-forum sshd[19229]: Failed password for root from 189.80.37.69 port 50714 ssh2
Oct  1 07:30:29 python-forum sshd[19229]: Received disconnect from 189.80.37.69: 11: Bye Bye [preauth]
Oct  1 07:30:31 python-forum sshd[19231]: pam_unix(sshd:auth): authentication failure; logname= uid=0    euid=0 tty=ssh ruser= rhost=189.80.37.69  user=root
Oct  1 07:30:34 python-forum sshd[19231]: Failed password for root from 189.80.37.69 port 53132 ssh2
Oct  1 07:30:34 python-forum sshd[19231]: Received disconnect from 189.80.37.69: 11: Bye Bye [preauth]
Oct  1 07:30:35 python-forum sshd[19233]: pam_unix(sshd:auth): authentication failure; logname= uid=0    euid=0 tty=ssh ruser= rhost=189.80.37.69  user=root
Oct  1 07:30:38 python-forum sshd[19233]: Failed password for root from 189.80.37.69 port 55746 ssh2
Oct  1 07:30:38 python-forum sshd[19233]: Received disconnect from 189.80.37.69: 11: Bye Bye [preauth]
Oct  1 07:30:41 python-forum sshd[19235]: pam_unix(sshd:auth): authentication failure; logname= uid=0    euid=0 tty=ssh ruser= rhost=189.80.37.69  user=root



```
and
```

Oct  1 07:38:51 python-forum sshd[19594]: Received disconnect from 189.80.37.69: 11: Bye Bye [preauth]
Oct  1 07:38:52 python-forum sshd[19591]: Failed password for root from 58.218.198.165 port 22368 ssh2
Oct  1 07:38:52 python-forum sshd[19596]: Invalid user zabbix from 189.80.37.69
Oct  1 07:38:52 python-forum sshd[19596]: input_userauth_request: invalid user zabbix [preauth]
Oct  1 07:38:52 python-forum sshd[19591]: Received disconnect from 58.218.198.165: 11:  [preauth]
Oct  1 07:38:52 python-forum sshd[19591]: PAM 2 more authentication failures; logname= uid=0 euid=0      tty=ssh ruser= rhost=58.218.198.165  user=root
Oct  1 07:38:53 python-forum sshd[19596]: pam_unix(sshd:auth): check pass; user unknown
Oct  1 07:38:53 python-forum sshd[19596]: pam_unix(sshd:auth): authentication failure; logname= uid=0    euid=0 tty=ssh ruser= rhost=189.80.37.69 
Oct  1 07:38:55 python-forum sshd[19596]: Failed password for invalid user zabbix from 189.80.37.69 port 38610 ssh2

```

a lot of stuff from these 2 IP addresses which none were the hackers IP

However that was 5 days ago. The last 200 lines for example look normal of stuff i was doing. But that was also before the hacker got in due to me restoring the server to a previous state.

---

### Post by QIII on 2017-10-06
There are a lot of server hardening guides that you should peruse and do just about everything.  Then, you should continue reading every document you find and continually refine your security.  It's not a "one and done" proposition.  It's a process.

A few good resources.  Take all of the advice given into consideration:

Digital Ocean has a lot of things:

Introductory basics:  [https://www.digitalocean.com/community/tutorials/an-introduction-to-securing-your-linux-vps](https://www.digitalocean.com/community/tutorials/an-introduction-to-securing-your-linux-vps)
Some further reading:  [https://www.digitalocean.com/community/questions/best-practices-for-hardening-new-sever-in-2017](https://www.digitalocean.com/community/questions/best-practices-for-hardening-new-sever-in-2017)

nixCraft Server Hardening tips:  [https://www.cyberciti.biz/tips/linux-security.html](https://www.cyberciti.biz/tips/linux-security.html)

[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

[https://wiki.centos.org/HowTos/Network/IPTables](https://wiki.centos.org/HowTos/Network/IPTables)

[http://www.pontikis.net/blog/tag/fail2ban](http://www.pontikis.net/blog/tag/fail2ban)

For starters.


Are you using a content management system?  Which one?  Have you read up on hardening it?  WordPress is notorious for breaches.

I'd suggest re-imaging your vps and applying a lot more hardening.  Then carefully monitor all the logs.  If you have password ssh access, don't leave it that way.  Use key pairs.  Deny root login.  Set up LogCheck and LogWatch and have your server email you when that sort of stuff is happening.

Someone is brute-forcing you.

---

### Post by micahpage on 2017-10-06
Thank you for the links. I will read up on them.

As for your last question. I am only using MyBB to handle a forum as that is the only purpose of the server. And i have read up and modified that to handle hacking through that beforehand.

I think somethign is wrong with my fail2ban as when i restart it i get an error
```

$ sudo service fail2ban restart
 * Restarting authentication failure monitor fail2ban                                                    WARNING 'actionstart' not defined in 'Definition'. Using default one: ''
WARNING 'actionstop' not defined in 'Definition'. Using default one: ''
WARNING 'actioncheck' not defined in 'Definition'. Using default one: ''
ERROR  No file(s) found for glob /var/log/sshd.log
ERROR  Failed during configuration: Have not found any log file for ssh-route jail
                                                                                                  [fail]

```

---

### Post by SeijiSensei on 2017-10-06
>  rejected the hackers IP address as he kept logging into IRC

Is the server running ircd?  If so, why haven't you turned that off?

---

### Post by micahpage on 2017-10-06
No the server is not running IRC. Its on freenode. Its our chat for the forum, and the hacker jumped in to gloat at us for taking down the site as that is where everyone goes if the forum goes down.

I meant i seen him jump in IRC within a 5 hour period with the same IP address

---

### Post by HermanAB on 2017-10-08
They probably get in through a bad configuration of MyBB and one of your users with a too short password.

Anyhoo, your best protection is to always use very long passwords and you also have to force your users to use very long passwords, by making a little change in the PAM configuration.

As for SSH, run it on a different port, not port 22 and only allow connection from a small range of IP addresses.

---

### Post by micahpage on 2017-10-08
Thanks i changed the latter, now working on the PAM config.

---

### Post by kevsin on 2017-10-18
Have you had any further problems with this? I currently host all my ubuntu machines on digitalocean and bluehost vps's. Had some problems with ovh, where I had them hosted before. Attacks, downtimes, you name it.

---

### Post by micahpage on 2017-10-24
Not since. But i was hacked in nov 2016, and sept 2017. So it appears to be on a routine of once a year. Other than that, i have never had any downtime. I dont believe its an issue with digital ocean but my admin skills at hardening the server. 

I ended up locking myself out somehow trying to do whitelisting of IP's in ssh, and had to revert to a previous snapshot just to access the server.

---

