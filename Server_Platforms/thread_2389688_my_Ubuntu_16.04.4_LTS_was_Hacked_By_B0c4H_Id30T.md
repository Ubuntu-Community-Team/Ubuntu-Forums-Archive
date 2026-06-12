---
title: "my Ubuntu 16.04.4 LTS was Hacked By B0c4H_Id30T"
date: 2018-04-20
forum: Server Platforms
---

### Post by surdet on 2018-04-20
I install Ubuntu 16.04.4 LTS for a web server with virtual host enable. My web server is a private IP with web port mapping from a web proxy server. Today, I found there are many you.htm files in many folders in /var and subfolders with root owner. Hacker was also installed minergate-cli. It hacked my server at around 12 April 17:56.  Please guide me to avoid this hack in my new server. Are they hack my server through apache service?

Thank you.

---

### Post by TheFu on 2018-04-20
Is it a static website or some webapp that wasn't properly secured?

Also, please copy/paste text using code tags here. No images.  Please.

---

### Post by LHammonds on 2018-04-20
Let me guess...this Ubuntu web server is actually a desktop with a GUI and you browse the web on this machine?  The Minergate is a trojan that gets hold of your system by exploiting web browsers....not typically web servers.

Did you enable "root" to login or did you do "sudo su" to be logged in as root?

On Ubuntu, Apache defaults to a low-rights www-data user so anything that goes through your web service cannot "gain" root access thru the www-data account unless you have seriously compromised and flawed setup.

If your server is actually a dedicated server, is your PC able to auto-connect to it with root access such as through WinSCP, Filezilla, Samba mount, etc.?

Do you have any software that is installed on Ubuntu that did not come from the official repositories?

LHammonds

---

### Post by surdet on 2018-04-23
Thank you for your reply. I have to enable root login for a backup script purpose. So it may be a weakness point. Thank you again for your advice.

---

### Post by surdet on 2018-04-23
[COLOR=#000000]Thank you for your reply. It quite hard to identify which websites are not secured. Maybe I enabled root login is a cause to be hacked.[/COLOR]

---

### Post by TheFu on 2018-04-23
For backups, there are different methods to make it workable.
Most F/LOSS backup tools work over ssh and ssh can be locked down to allow only 1 program to be run, only with ssh-keys for authentication and only from specific IPs.
[http://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures](http://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures) has some techniques.

---

### Post by surdet on 2018-04-24
> **TheFu said:**
> For backups, there are different methods to make it workable.
Most F/LOSS backup tools work over ssh and ssh can be locked down to allow only 1 program to be run, only with ssh-keys for authentication and only from specific IPs.
[http://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures](http://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures) has some techniques.

The link is very useful. I found somethings from auth.log, My server can access from outside by ssh protocol and hacker activities.
```

Apr 12 17:49:39 ubuntu sshd[42925]: Did not receive identification string from 182.162.90.203
Apr 12 17:52:48 ubuntu groupadd[43663]: group added to /etc/group: name=pelor, GID=1005
Apr 12 17:52:48 ubuntu groupadd[43663]: group added to /etc/gshadow: name=pelor
Apr 12 17:52:48 ubuntu groupadd[43663]: new group: name=pelor, GID=1005
Apr 12 17:52:49 ubuntu useradd[43667]: new user: name=pelor, UID=1005, GID=1005, home=/home/pelor, shell=/bin/bash
Apr 12 17:52:54 ubuntu passwd[43674]: pam_unix(passwd:chauthtok): password changed for pelor
Apr 12 17:52:59 ubuntu chfn[43675]: changed user 'pelor' information
Apr 12 17:53:11 ubuntu passwd[43680]: pam_unix(passwd:chauthtok): password changed for www-data
Apr 12 18:05:41 ubuntu sshd[56894]: Received signal 15; terminating.
Apr 12 18:05:41 ubuntu sshd[44031]: Server listening on 0.0.0.0 port 2222.
Apr 12 18:05:41 ubuntu sshd[44031]: Server listening on :: port 2222.
Apr 12 18:09:01 ubuntu CRON[44090]: pam_unix(cron:session): session opened for user root by (uid=0)
Apr 12 18:09:01 ubuntu CRON[44090]: pam_unix(cron:session): session closed for user root

```

Thank you for your suggestion.

---

### Post by TheFu on 2018-04-24
Cron runs as root, so that isn't too odd.
pelor?  If that isn't your normal userid and you didn't change the password on 4/12 about 17:52, then you definitely have a problem.

Allowing a service account to have a shell is poor security.  No shell. No password and definitely no login.  www-data is a service account.

ssh should only allow remote connections from known IPs, to specific known accounts (never root) and only with ssh-keys over the internet.

OTOH, it is your box and you can do whatever you like.  Just know that there are security implications.

---

### Post by mastablasta on 2018-04-25
how to not get hacked? follow some advice on hardening. for example: [https://www.digitalocean.com/community/questions/best-practices-for-hardening-new-sever-in-2017](https://www.digitalocean.com/community/questions/best-practices-for-hardening-new-sever-in-2017)

also read about security: [https://help.ubuntu.com/community/Security](https://help.ubuntu.com/community/Security)

with server connected to web, you open parts of your computer to the outside world. which is why it is important to harden access to it's root account and limit access to other parts of it as much as possible. 

and of course to have a **_good backup strategy_**.

---

