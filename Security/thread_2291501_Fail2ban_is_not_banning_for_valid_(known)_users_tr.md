---
title: "Fail2ban is not banning for valid (known) users tries"
date: 2015-08-20
forum: Security
---

### Post by blitz2 on 2015-08-20
Hello all,

Last couple days i'm trying to figure out how to use fail2ban. I'm using virtualbox Ubuntu server 14.04 (dhcp-nat-ssh servers installed) and client is win7 with putty

It's working great for invalid user's tries but if i try to logon with root via ssh fail2ban is doing nothing although root is already locked.

Also i created a user called "test" but fail2ban is not banning wrong pass tries for test user's too.

When i edit /etc/ssh/sshd_config set MaxAuthTries 3  and trying wrong pass for test user "tail -f /var/log/auth.log" says;

"sshd[1947]: PAM service(sshd) ignoring max retries; 7 > 3"

Here is fail2ban jail conf for ssh;
[ssh]
enabled  = true
port     = ssh
filter   = sshd
logpath  = /var/log/auth.log
maxretry = 5

Still not banning for known users :( (valid users)

[ATTACH=CONFIG]263962[/ATTACH][ATTACH=CONFIG]263963[/ATTACH][ATTACH=CONFIG]263964[/ATTACH]

Does anyone know why? Is there a way to change this behavior?

---

### Post by Habitual on 2015-08-20
fail2ban out of the box bans ssh attempts > 6.
Why not try defaults?

After setting a/this/these rules, did you restart fail2ban?
What does /var/log/fail2ban.log say about these events, if anything?

---

### Post by blitz2 on 2015-08-20
I've already added 3 of pix about what was going on when i try to logon as a root. See fail2ban2.PNG=/var/log/auth.log, fail2ban3.PNG=/var/log/fail2ban.log, fail2ban.PNG=my login attemps. 

Yes i restarted ssh and fail2ban services in every single changes.

---

### Post by Habitual on 2015-08-21
What does ```
fail2ban-regex /var/log/auth.log /etc/fail2ban/filter.d/sshd.conf | tail
``` 'show'?
Looking for "[COLOR=#008000]Success[/COLOR], the total number of match is *[n]nn*".
or
"Sorry, no match" 

please.

Also, there is no need to restart ssh when making changes to fail2ban .conf files.

---

### Post by blitz2 on 2015-08-21
Ok here is the test's results;

fail2ban-regex /var/log/auth.log /etc/fail2ban/filter.d/sshd.conf | tail

Ignoreregex: 0 total

Date template hits:
|- [# of hits] date format
|  [1206] MONTH Day Hour:Minute:Second
`-

Lines: 1206 lines, 0 ignored, 128 matched, 1078 missed
Missed line(s):: too many to print.  Use --print-all-missed to print all 1078 lines


I dont really know but it looks like a bug because fail2ban is banning well for invalid user's tries or this feature does not exist. Just want to know why it doesn't ban when i type wrong password for a valid user via SSH

Here is my scenario;

_Virtualbox_
Ubuntu srv (DHCP-NAT-SSH-Fail2ban) user; test with root permission. Root is locked by default
Win7 client (PuTTy)

Win7 client ----> trying to connect with invalid user via SSH (for instance brute-force attack) -----> Fail2ban is banned after 3 time because i set maxretries = 3 ok!
Win7 client ----> trying to connect with valid user called test -----> Fail2ban is not banning.. I'm still trying over and over again
Win7 client ----> trying to connect with valid user root (although its locked) -----> Fail2ban is not banning.. I'm still trying over and over again

---

### Post by blitz2 on 2015-08-21
Finally!

I think I've found a solution 

First i added in etc/fail2ban/jail.local

#maxretry = 5
maxfailures = 5

I thought maxfailures is better idea than maxretry :) Well, worth to try

And this one;
[Link]("http://askubuntu.com/questions/539771/fail2ban-regex-ssh-will-not-match-auth-log-searched-everywhere-for-a-solution")

sed -i 's/RepeatedMsgReduction\ on/RepeatedMsgReduction\ off/' /etc/rsyslog.conf 
service rsyslog restart 
service fail2ban restart

I dont know which one was the right but it works PERFECT! 

Your suggestion guide me to find thank you Habitual

---

### Post by Habitual on 2015-08-21
Glad it worked out.

---

