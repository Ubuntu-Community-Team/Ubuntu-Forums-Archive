---
title: "SSH attack"
date: 2008-04-25
forum: Security
---

### Post by TuckLive on 2008-04-25
So the other day I checked my logs and I was being hammered on port 22.  I don't think they got in, but I see some things in the log I am not sure about.  Below is some samples of all the data.  


> Apr 23 06:25:01 computer CRON[16894]: pam_unix(cron:session): session opened for user root by (uid=0)
Apr 23 06:25:02 computer su[16925]: Successful su for nobody by root
Apr 23 06:25:02 computer su[16925]: + ??? root:nobody
Apr 23 06:25:02 computer su[16925]: pam_unix(su:session): session opened for user nobody by (uid=0)
Apr 23 06:25:02 computer su[16925]: pam_unix(su:session): session closed for user nobody
Apr 23 06:25:02 computer su[16927]: Successful su for nobody by root
Apr 23 06:25:02 computer su[16927]: + ??? root:nobody
Apr 23 06:25:02 computer su[16927]: pam_unix(su:session): session opened for user nobody by (uid=0)
Apr 23 06:25:02 computer su[16927]: pam_unix(su:session): session closed for user nobody
Apr 23 06:25:02 computer su[16929]: Successful su for nobody by root
Apr 23 06:25:02 computer su[16929]: + ??? root:nobody
Apr 23 06:25:02 computer su[16929]: pam_unix(su:session): session opened for user nobody by (uid=0)
Apr 23 06:26:03 computer su[16929]: pam_unix(su:session): session closed for user nobody
Apr 23 06:26:07 computer CRON[16894]: pam_unix(cron:session): session closed for user root



> Apr 24 09:39:00 waiter sshd[21395]: pam_unix(ssh:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=216-176-180-26.reverse.wowrack.com  user=root
Apr 24 09:39:01 computer CRON[21397]: pam_unix(cron:session): session opened for user root by (uid=0)
Apr 24 09:39:01 computer CRON[21397]: pam_unix(cron:session): session closed for user root
Apr 24 09:39:02 computer sshd[21395]: Failed password for root from 216.176.180.26 port 36302 ssh2


I never see a successful logon from a hostile IP before I see this, so could this be the box itself?  I'm not sure about the nobody user id.
> Apr 25 06:17:01 computer CRON[24760]: pam_unix(cron:session): session opened for user root by (uid=0)
Apr 25 06:17:01 computer CRON[24760]: pam_unix(cron:session): session closed for user root
Apr 25 06:25:01 computer CRON[24771]: pam_unix(cron:session): session opened for user root by (uid=0)
Apr 25 06:25:01 computer su[24802]: Successful su for nobody by root
Apr 25 06:25:01 computer su[24802]: + ??? root:nobody
Apr 25 06:25:01 computer su[24802]: pam_unix(su:session): session opened for user nobody by (uid=0)
Apr 25 06:25:01 computer su[24802]: pam_unix(su:session): session closed for user nobody
Apr 25 06:25:01 computer su[24804]: Successful su for nobody by root
Apr 25 06:25:01 computer su[24804]: + ??? root:nobody
Apr 25 06:25:01 computer su[24804]: pam_unix(su:session): session opened for user nobody by (uid=0)
Apr 25 06:25:01 computer su[24804]: pam_unix(su:session): session closed for user nobody
Apr 25 06:25:01 computer su[24806]: Successful su for nobody by root
Apr 25 06:25:01 computer su[24806]: + ??? root:nobody
Apr 25 06:25:01 computer su[24806]: pam_unix(su:session): session opened for user nobody by (uid=0)
Apr 25 06:25:03 computer su[24806]: pam_unix(su:session): session closed for user nobody
Apr 25 06:25:07 computer CRON[24771]: pam_unix(cron:session): session closed for user root
Apr 25 06:39:01 computer CRON[24921]: pam_unix(cron:session): session opened for user root by (uid=0)
Apr 25 06:39:01 computer CRON[24921]: pam_unix(cron:session): session closed for user root


If anybody successfully got in, would it show the IP address everytime?  Here is when I log in.
> Apr 24 12:35:34 computer sshd[22864]: Accepted password for myaccount from 192.x.x.x port 47600 ssh2
Apr 24 12:35:34 computer sshd[22867]: pam_unix(ssh:session): session opened for user myaccount by (uid=0

---

### Post by Patsoe on 2008-04-25
As far as I can see the successful sessions are cron jobs, not ssh logins. 

If you're worried about the ssh login attempts - there's a way to limit the number of attempts per given time frame. I think I shall want to look into that too.

---

### Post by tubezninja on 2008-04-25
ssh attacks happen all the time.  I get tons of them on my servers.  This is nothing new.  It's usually compromised servers, some running linux, that are seeking other servers with weak username-password combos.  Once they find out, they'll get in, try to escalate privileges and install rootkits and such.  Then they'll use your server is a Command/Control center for a botnet, or some other nefarious purpose.

The root instances in your auth.log isn't by itself a reason to be suspicious.  They  look like they're all being invoked by cron jobs, which is normal.  Things like log rotation, daemons and anything you've setup in a crontab will cause log entries like this.

The "nobody" user is interesting.  "nobody" is a common user for certain services on on some linux distros, but I have never seen it used in ubuntu.  And I've also never seen "nobody" successfully do an "su" to escalate privileges.

As for your last question: yes, auth.log should show the IP address of every successful login.  Of course, if a user has root access, they could just wipe their own log entry. 

I don't THINK anyone got in on your system, but I don't have the full logs to be sure.  You should check your /home directory to see if any users are there that you don't recognize.  You might also consider installing and running [rkhunter]("http://packages.ubuntu.com/hardy/rkhunter") to check for rootkits.

And, to help cut down on the ssh dictionary attacks, install [denyhosts]("http://packages.ubuntu.com/hardy/denyhosts").  This is a customizable python script that will effectively ban IP addresses for a while if they are found to repeatedly log in with improper usernames or passwords.  Just be careful with this script, and customize the /etc/denyhosts.conf file to your tastes, because in the default configuration, if you or a valid user on your system incorrectly types in their password too many times, you could find yourself locked out :)

---

### Post by hggdh on 2008-04-25
These seem to be internal processing at your box.

There are many automated attacks against SSH, most of them like brute force (some common accounts, and some common passwords).

There are some basic things you can do:

1. disable root login via SSH (of old, the default setting, but I do not know what you have). There is no reason to allow direct root logins in any form nowadays;
2. you could write a script to monitor the logs -- if you see some suspicious activity, you could, for example, drop the offending source IP via iptables, either forever or for a while;
3. you can set your SSH on  a non-standard port (a high-numbered one). Of course, this is not a real protection, mainly against a generic port scan, but it will take out a large portion of bots.

---

### Post by Patsoe on 2008-04-25
> **scaredpoet said:**
> And I've also never seen "nobody" successfully do an "su" to escalate privileges.


Doesn't it say the opposite? I thought this meant that root is executing something as user nobody?

> Apr 23 06:25:02 computer su[16927]: Successful su for nobody by root

---

### Post by Oldsoldier2003 on 2008-04-25
> **Patsoe said:**
> Doesn't it say the opposite? I thought this meant that root is executing something as user nobody?

Patsoe, you are correct. root su'd to user nobody to run the job

---

### Post by TuckLive on 2008-04-25
Thanks for the replies.  the nobody userid is what I was most concerned about.  I've taken further precautions to lock down the box.

---

### Post by movieman on 2008-04-25
Better yet, if you can, disable password login completely on SSH and use crypto keys instead. Cracking a 2048-bit RSA key is hard enough (i.e. currently probably impossible) even if you have the public key to factor, it's impossible if you don't know what the key is in the first place.

---

### Post by TuckLive on 2008-04-25
I'm using Webmin to manage the server.  Can anybody tell me or point me to a doc that shows you how to use keys instead of passwords using Webmin?

---

### Post by Oldsoldier2003 on 2008-04-25
> **movieman said:**
> Better yet, if you can, disable password login completely on SSH and use crypto keys instead. Cracking a 2048-bit RSA key is hard enough (i.e. currently probably impossible) even if you have the public key to factor, it's impossible if you don't know what the key is in the first place.

Disallow root logins,turn off password authentication in favor of public key, disable ssh1 protocol, and restrict ssh logins to users that have a valid reason and you have a very secure system. If you do this you don't even really need to move from port 22 or install DenyHosts or fail2ban.

@ OP: I don't use webmin so I don't have any tutorials for you. If you are comfortable with doing it over ssh on a terminal I can toss you a few links to look over.

---

### Post by Chayak on 2008-04-25
install fail2ban from the repositories.  It'll ban an ip that tries to brute force passwords after three tries.  That or just set your ssh service to a nonstandard port like 2222 or 2200 or whatever you want.  Most bots only look on the default port.

As for your logs, nothing out of the ordinary.

---

