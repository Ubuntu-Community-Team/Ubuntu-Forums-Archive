---
title: "blocking postfix SASL hacking attempts"
date: 2020-05-05
forum: Security
---

### Post by robbo007 on 2020-05-05
Hi all,
I'm getting constant SASL hacking attempts from various IPS. I've installed fail2ban but can't seem to find a good document on configuring it for these type of attacks. Could someone suggest how to configure it?

May  5 12:19:18 mydomainname.com postfix/smtpd[7628]: warning: unknown[46.38.144.32]: SASL LOGIN authentication failed: Uxxxxxxxxxxxx

thanks,

---

### Post by EuclideanCoffee on 2020-05-05
I found this. Does it work for you?

[https://www.howtoforge.com/community/threads/fail2ban-sasl-problem-and-solution.51349/](https://www.howtoforge.com/community/threads/fail2ban-sasl-problem-and-solution.51349/)

/etc/fail2ban/filter.d/sasl.conf

```

[sasl]
enabled = true
port = smtp
filter = sasl
logpath = /var/log/mail.log
maxretry = 5

```

/var/log/mail.log

```

# Fail2Ban configuration file
#
# Author: Yaroslav Halchenko
#
# $Revision: 728 $
#

[Definition]

# Option: failregex
# Notes.: regex to match the password failures messages in the logfile. The
#          host must be matched by a group named "host". The tag "<HOST>" can
#          be used for standard IP/hostname matching and is only an alias for
#          (?:::f{4,6}:)?(?P<host>[\w\-.^_]+)
# Values: TEXT
#
failregex = (?i): warning: [-._\w]+\[<HOST>\]: SASL (?:LOGIN|PLAIN|(?:CRAM|DIGEST)-MD5) authentication failed(: [A-Za-z0-9+/]*={0,2})?$

# Option:  ignoreregex
# Notes.:  regex to ignore. If this regex matches, the line is ignored.
# Values:  TEXT
#
ignoreregex = 


```

change in /etc/fail2ban/filter.d/sasl.conf:

```

failregex = (?i): warning: [-._\w]+\[<HOST>\]: SASL (?:LOGIN|PLAIN|(?:CRAM|DIGEST)-MD5) authentication failed(: [A-Za-z0-9+/]*={0,2})?$

```

to

```

failregex = (?i): warning: [-._\w]+\[<HOST>\]: SASL (?:LOGIN|PLAIN|(?:CRAM|DIGEST)-MD5) authentication failed: \w

```

Restart.

systemctl restart fail2ban

---

### Post by robbo007 on 2020-05-05
Thanks for the reply. I just tried this and does not seem to catch them. Heres my config. Any ideas? (sorry could not find the code tool to paste correctly).

```
/etc/fail2ban/filter.d/sasl.conf
# Fail2Ban configuration file
#
# Author: Yaroslav Halchenko
#
# $Revision: 728 $
#


[Definition]


# Option: failregex
# Notes.: regex to match the password failures messages in the logfile. The
#          host must be matched by a group named "host". The tag "<HOST>" can
#          be used for standard IP/hostname matching and is only an alias for
#          (?:::f{4,6}:)?(?P<host>[\w\-.^_]+)
# Values: TEXT
#
failregex = (?i): warning: [-._\w]+\[<HOST>\]: SASL (?:LOGIN|PLAIN|(?:CRAM|DIGEST)-MD5) authentication failed: \w
# Option:  ignoreregex
# Notes.:  regex to ignore. If this regex matches, the line is ignored.
# Values:  TEXT
#
ignoreregex = 
```


```
/etc/fail2ban/jai.conf:




[sasl]
enabled = true
port = smtp
filter = sasl
logpath = /var/log/mail.log
maxretry = 5

```

```
/var/log/mail.log:


May  5 21:04:30 sosaria postfix/smtpd[15785]: connect from unknown[185.234.216.178]
May  5 21:04:31 sosaria postfix/smtpd[16453]: lost connection after AUTH from unknown[185.143.74.49]
May  5 21:04:31 sosaria postfix/smtpd[16453]: disconnect from unknown[185.143.74.49] ehlo=1 auth=0/1 rset=1 commands=2/3
May  5 21:04:32 sosaria postfix/smtpd[15785]: warning: unknown[185.234.216.178]: SASL LOGIN authentication failed: UGFzc3dvcmQ6
May  5 21:04:32 sosaria postfix/smtpd[15785]: lost connection after AUTH from unknown[185.234.216.178]
May  5 21:04:32 sosaria postfix/smtpd[15785]: disconnect from unknown[185.234.216.178] ehlo=1 auth=0/1 commands=1/2
May  5 21:04:36 sosaria postfix/smtpd[15786]: warning: unknown[45.142.195.6]: SASL LOGIN authentication failed: UGFzc3dvcmQ6
May  5 21:04:36 sosaria postfix/smtpd[15786]: disconnect from unknown[45.142.195.6] ehlo=1 auth=0/1 rset=1 quit=1 commands=3/4
May  5 21:04:36 sosaria postfix/smtpd[15783]: connect from unknown[45.142.195.7]
May  5 21:04:43 sosaria postfix/smtpd[15783]: warning: unknown[45.142.195.7]: SASL LOGIN authentication failed: UGFzc3dvcmQ6
May  5 21:04:44 sosaria postfix/smtpd[15783]: disconnect from unknown[45.142.195.7] ehlo=1 auth=0/1 rset=1 quit=1 commands=3/4
May  5 21:04:48 sosaria postfix/smtpd[16453]: connect from unknown[46.38.144.179]
May  5 21:04:51 sosaria postfix/smtpd[15786]: connect from unknown[46.38.144.32]
May  5 21:04:55 sosaria postfix/smtpd[16453]: warning: unknown[46.38.144.179]: SASL LOGIN authentication failed: UGFzc3dvcmQ6
May  5 21:04:56 sosaria postfix/smtpd[16453]: disconnect from unknown[46.38.144.179] ehlo=1 auth=0/1 rset=1 quit=1 commands=3/4
May  5 21:04:58 sosaria postfix/smtpd[15786]: warning: unknown[46.38.144.32]: SASL LOGIN authentication failed: UGFzc3dvcmQ6
May  5 21:04:58 sosaria postfix/smtpd[16750]: connect from unknown[185.143.74.49]
May  5 21:04:59 sosaria postfix/smtpd[15786]: disconnect from unknown[46.38.144.32] ehlo=1 auth=0/1 rset=1 quit=1 commands=3/4
May  5 21:05:01 sosaria postfix/smtpd[16453]: connect from unknown[185.143.74.73]
May  5 21:05:07 sosaria postfix/smtpd[16453]: warning: unknown[185.143.74.73]: SASL LOGIN authentication failed: UGFzc3dvcmQ6
May  5 21:05:07 sosaria postfix/smtpd[16453]: disconnect from unknown[185.143.74.73] ehlo=1 auth=0/1 rset=1 quit=1 commands=3/4
May  5 21:05:09 sosaria postfix/smtpd[15785]: connect from unknown[185.143.74.108]
May  5 21:05:15 sosaria postfix/smtpd[15785]: warning: unknown[185.143.74.108]: SASL LOGIN authentication failed: UGFzc3dvcmQ6
May  5 21:05:15 sosaria postfix/smtpd[15785]: disconnect from unknown[185.143.74.108] ehlo=1 auth=0/1 rset=1 quit=1 commands=3/4
May  5 21:05:19 sosaria postfix/smtpd[16750]: warning: unknown[185.143.74.49]: SASL LOGIN authentication failed: UGFzc3dvcmQ6
May  5 21:05:27 sosaria postfix/smtpd[16453]: connect from unknown[45.142.195.7]
May  5 21:05:28 sosaria postfix/smtpd[15785]: connect from unknown[46.38.144.202]
May  5 21:05:34 sosaria postfix/smtpd[15785]: warning: unknown[46.38.144.202]: SASL LOGIN authentication failed: UGFzc3dvcmQ6
May  5 21:05:34 sosaria postfix/smtpd[16453]: warning: unknown[45.142.195.7]: SASL LOGIN authentication failed: UGFzc3dvcmQ6
May  5 21:05:34 sosaria postfix/smtpd[16453]: disconnect from unknown[45.142.195.7] ehlo=1 auth=0/1 rset=1 quit=1 commands=3/4
May  5 21:05:34 sosaria postfix/smtpd[15785]: disconnect from unknown[46.38.144.202] ehlo=1 auth=0/1 rset=1 quit=1 commands=3/4
May  5 21:05:34 sosaria postfix/smtpd[15786]: connect from unknown[45.142.195.6]
May  5 21:05:41 sosaria postfix/smtpd[15783]: connect from unknown[185.143.74.133]
May  5 21:05:48 sosaria postfix/smtpd[15783]: warning: unknown[185.143.74.133]: SASL LOGIN authentication failed: UGFzc3dvcmQ6
May  5 21:05:48 sosaria postfix/smtpd[16750]: disconnect from unknown[185.143.74.49] ehlo=1 auth=0/1 rset=1 quit=1 commands=3/4
May  5 21:05:48 sosaria postfix/smtpd[15783]: disconnect from unknown[185.143.74.133] ehlo=1 auth=0/1 rset=1 quit=1 commands=3/4
May  5 21:05:51 sosaria postfix/smtpd[15785]: connect from unknown[185.143.74.93]
May  5 21:05:55 sosaria postfix/smtpd[15785]: warning: unknown[185.143.74.93]: SASL LOGIN authentication failed: UGFzc3dvcmQ6
May  5 21:05:55 sosaria postfix/smtpd[15785]: disconnect from unknown[185.143.74.93] ehlo=1 auth=0/1 rset=1 quit=1 commands=3/4

```

Testing:


```
fail2ban-regex /var/log/mail.log /etc/fail2ban/filter.d/sasl.conf


Running tests
=============


Use   failregex filter file : sasl, basedir: /etc/fail2ban
Use         log file : /var/log/mail.log
Use         encoding : UTF-8




Results
=======


Failregex: 7268 total
|-  #) [# of hits] regular expression
|   1) [7268] (?i): warning: [-._\w]+\[<HOST>\]: SASL (?:LOGIN|PLAIN|(?:CRAM|DIGEST)-MD5) authentication failed: \w
`-


Ignoreregex: 0 total


Date template hits:
|- [# of hits] date format
|  [23469] {^LN-BEG}(?:DAY )?MON Day %k:Minute:Second(?:\.Microseconds)?(?: ExYear)?
`-


Lines: 23469 lines, 0 ignored, 7268 matched, 16201 missed
[processed in 4.05 sec]


Missed line(s): too many to print.  Use --print-all-missed to print all 16201 lines
```

---

### Post by EuclideanCoffee on 2020-05-05
```

Lines: 23469 lines, 0 ignored, 7268 matched, 16201 missed

```

It appears they are matching in this test.

Could you confirm that it is missing in some other test?

Maybe try cutting the mail log.

---

### Post by robbo007 on 2020-05-06
Just one thing before I check that. Is this normal? Shouldn't I get a status of it running here? 

# fail2ban-client status Failed to access socket path: /var/run/fail2ban/fail2ban.sock. Is fail2ban running?

I can't see it in the PS list either? Strange. I've restarted the service too.

---

### Post by SeijiSensei on 2020-05-06
I'd just block connections from 185.143.74.0/24, 45.142.195.0/24, and 46.38.144.0/24 for starters.

```

sudo iptables -I INPUT -s 185.143.73.0/24 -j REJECT
sudo iptables -I INPUT -s 45.142.195.0/24 -j REJECT
sudo iptables -I INPUT -s 46.38.144.0/24 -j REJECT

```
Use the "-I" switch to put these rules at the top of the chain.  That way they will block the traffic in case some rules further down the chain permits it.

---

### Post by EuclideanCoffee on 2020-05-06
I typically block things from the /var/log as well using a parsing script with a whitelist.

---

### Post by robbo007 on 2020-05-06
> **SeijiSensei said:**
> I'd just block connections from 185.143.74.0/24, 45.142.195.0/24, and 46.38.144.0/24 for starters.

```

sudo iptables -I INPUT -s 185.143.73.0/24 -j REJECT
sudo iptables -I INPUT -s 45.142.195.0/24 -j REJECT
sudo iptables -I INPUT -s 46.38.144.0/24 -j REJECT

```
Use the "-I" switch to put these rules at the top of the chain.  That way they will block the traffic in case some rules further down the chain permits it.

Thanks I was going to do something like this next until I can get fail2ban working correctly. I don't want to start blocking too much of a subnet just in case I need real traffic from there. I see im the time I've blocked those IP ranges they are now using more. God these guys are persistent.

---

### Post by robbo007 on 2020-05-07
Right they seemed to have given up after blocking more of the subnets. I'll have to investigate fail2ban further to see why the rule was not working and why it reports it not running even though the daemon is loaded. Very strange indeed.

---

### Post by EuclideanCoffee on 2020-05-07
I wish I understood this sentence.

> 
rule was not working and why it reports it not running even though the daemon is loaded.


What do you mean that fail2ban is loaded but not working? Could you provide stdout that leads you to this conclusion along with trimmed logs that timely report what is happening?

---

### Post by SeijiSensei on 2020-05-07
> **robbo007 said:**
> Thanks I was going to do something like this next until I can get fail2ban working correctly. I don't want to start blocking too much of a subnet just in case I need real traffic from there. I see im the time I've blocked those IP ranges they are now using more. God these guys are persistent.
You can just block port 25 and leave everything else untouched.
```

sudo iptables -I INPUT -p tcp --dport 25 -s 185.143.73.0/24 -j REJECT
sudo iptables -I INPUT -p tcp --dport 25 -s 45.142.195.0/24 -j REJECT
sudo iptables -I INPUT -p tcp --dport 25 -s 46.38.144.0/24 -j REJECT

```

---

### Post by kevdog on 2020-05-10
Does UFW have some GeoIP block option?  Seems like that is what is needed.

---

### Post by robbo007 on 2020-05-11
Right I've got fail2ban working and its blocking the **** who keeps attacking.. I think this is now going to work :) I don't know why fail2ban was not working. Seemed it was not loading for some reason. Its now responding. :)

Status for the jail: sasl
|- Filter
|  |- Currently failed:	0
|  |- Total failed:	15
|  `- File list:	/var/log/mail.log
`- Actions
   |- Currently banned:	3
   |- Total banned:	3
   `- Banned IP list:	185.143.75.81 185.143.75.157 45.142.195.7

---

### Post by EuclideanCoffee on 2020-05-11
So all you did was enable it? Glad to hear it's working. Good job.

---

