---
title: "I think my server is breached"
date: 2014-12-08
forum: Security
---

### Post by ssamik2 on 2014-12-08
So I manage three webservers, all running Ubuntu 10.04.4 LTS

Lately my host have gotten some messages about abuse from one of my IP adresses. 

> 
**Subject: **[B][B]Attempts to crack our server
[/B][/B]
[B][B]
I am the sysadmin of Bobcat Open Systems
<[http://www.bobcatos.com](http://www.bobcatos.com)>.

Our morning log analyser reported that a user on your network tried to
crack our server.  The log exerpts follow.  Times are CST (UTC-0600).

On [mail3.bobcatos.com]("http://mail3.bobcatos.com") (208.101.214.41):
[Sat Dec 06 19:01:28 2014] [error] [client 80.65.61.162] File does not exist: /var/www/html/w00tw00t.at.blackhats.romanian.anti-sec:)
[Sat Dec 06 19:01:28 2014] [error] [client 80.65.61.162] client denied by server configuration: /usr/share/phpMyAdmin/scripts
[Sat Dec 06 19:01:28 2014] [error] [client 80.65.61.162] client denied by server configuration: /usr/share/phpMyAdmin/scripts
[Sat Dec 06 19:01:29 2014] [error] [client 80.65.61.162] File does not exist: /var/www/html/pma
[Sat Dec 06 19:01:29 2014] [error] [client 80.65.61.162] File does not exist: /var/www/html/myadmin
[Sat Dec 06 19:01:29 2014] [error] [client 80.65.61.162] File does not exist: /var/www/html/MyAdmin
[Sat Dec 06 19:01:30 2014] [error] [client 80.65.61.162] File does not exist: /var/www/html/3rdparty
[Sat Dec 06 19:01:30 2014] [error] [client 80.65.61.162] File does not exist: /var/www/html/admin
[/B][/B]

> 
Dec 5 12:01:24 omega sshd[1317]: SSH: Server;Ltype: Authname;Remote: 80.65.61.162-57645;Name: byte [preauth]
Dec 5 12:01:24 omega sshd[1317]: Invalid user byte from 80.65.61.162
Dec 5 12:01:24 omega sshd[1317]: Received disconnect from 80.65.61.162: 11: Bye Bye [preauth]
Dec 5 12:01:24 omega sshd[1321]: SSH: Server;Ltype: Version;Remote: 80.65.61.162-58016;Protocol: 2.0;Client: libssh-0.1
Dec 5 12:01:24 omega sshd[1321]: SSH: Server;Ltype: Kex;Remote: 80.65.61.162-58016;Enc: aes128-cbc;MAC: hmac-sha1;Comp: none [preauth]
Dec 5 12:01:24 omega sshd[1321]: SSH: Server;Ltype: Authname;Remote: 80.65.61.162-58016;Name: test [preauth]
Dec 5 12:01:24 omega sshd[1321]: Invalid user test from 80.65.61.162
Dec 5 12:01:24 omega sshd[1321]: Received disconnect from 80.65.61.162: 11: Bye Bye [preauth]
Dec 5 12:01:24 omega sshd[1323]: SSH: Server;Ltype: Version;Remote: 80.65.61.162-58445;Protocol: 2.0;Client: libssh-0.1
Dec 5 12:01:24 omega sshd[1323]: SSH: Server;Ltype: Kex;Remote: 80.65.61.162-58445;Enc: aes128-cbc;MAC: hmac-sha1;Comp: none [preauth]
Dec 5 12:01:24 omega sshd[1323]: SSH: Server;Ltype: Authname;Remote: 80.65.61.162-58445;Name: test [preauth]
Dec 5 12:01:24 omega sshd[1323]: Invalid user test from 80.65.61.162
Dec 5 12:01:24 omega sshd[1323]: Received disconnect from 80.65.61.162: 11: Bye Bye [preauth]
Dec 5 12:01:24 omega sshd[1326]: SSH: Server;Ltype: Version;Remote: 80.65.61.162-58806;Protocol: 2.0;Client: libssh-0.1
Dec 5 12:01:24 omega sshd[1326]: SSH: Server;Ltype: Kex;Remote: 80.65.61.162-58806;Enc: aes128-cbc;MAC: hmac-sha1;Comp: none [preauth]
Dec 5 12:01:25 omega sshd[1326]: SSH: Server;Ltype: Authname;Remote: 80.65.61.162-58806;Name: test [preauth]
Dec 5 12:01:25 omega sshd[1326]: Invalid user test from 80.65.61.162
Dec 5 12:01:25 omega sshd[1326]: Received disconnect from 80.65.61.162: 11: Bye Bye [preauth]
Dec 5 12:01:25 omega sshd[1329]: SSH: Server;Ltype: Version;Remote: 80.65.61.162-59200;Protocol: 2.0;Client: libssh-0.1
Dec 5 12:01:25 omega sshd[1329]: SSH: Server;Ltype: Kex;Remote: 80.65.61.162-59200;Enc: aes128-cbc;MAC: hmac-sha1;Comp: none [preauth]
[FONT=Verdana][/FONT]
So - where do I go from here? 
I've had servers running for close to ten years, and this is the first time anything like this have happended so I'm a bit lost. 


The breached server is up to date with all updates. 


All help and guidance are greatly appreciated!

---

### Post by TheFu on 2014-12-08
Well, what do you think was how they got into the machine?

Do you use passwords instead of keys for remote access over ssh?  Firewall? Denyhosts/fail2ban?

Do you run risky web-apps that haven't been maintained weekly for new attacks?  Java or Php or plain FTP?  Do these apps follow the OWASP application development checklist?

How many versioned backups for each server do you have 120 days?  If so, you would be able to look through the backup differences to see when anything important changed.

BTW - 10.04 server support ends in a few months, so it is time to move to either 14.04 or 12.04 servers.  I have 1 remaining 10.04 server here to which I need to migrate.

Now is the time for you to earn that paycheck.  I see phishing links in spam emails almost daily. Almost always, those links point back to compromised servers running some sort of php web-app with mysql.   I suppose the barrier to php programming is just too low - it is easy to get things working, but extremely hard to make it secure.  Security doesn't seem to be a consideration for 98% of the php programmers in the world and sadly, the language doesn't help as much as others do to create more security web-apps.

---

### Post by HermanAB on 2014-12-08
Log in, change the iptables rules to allow ONLY SSH on port 22 TCP, then start to fix it at your leasure.

---

