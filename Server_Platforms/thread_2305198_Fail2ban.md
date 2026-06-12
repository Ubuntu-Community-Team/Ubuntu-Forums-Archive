---
title: "Fail2ban"
date: 2015-12-03
forum: Server Platforms
---

### Post by nathanhawthorne12 on 2015-12-03
Evening folks,

Just installed fail2ban, so far it works just fine with password authentication but as soon as i set password authentication to no, fail2ban no longer adds ips to iptables

im pretty sure this is down to enabling ssh keys and since no password is entered its not counted as a failed login

```
 Received disconnect from 113.106.129.219: 11: Bye Bye [preauth]Dec 03 18:25:54 ********** sshd[3182]: Disconnected from 113.106.129.219 [preauth]
Dec 03 18:35:23 ********* sshd[3195]: Received disconnect from 43.229.53.56: 11:  [preauth]
Dec 03 18:35:23 ********* sshd[3195]: Disconnected from 43.229.53.56 [preauth]






```

can fail2ban be changed so it now includes the preauth as a failed login attempt?

---

### Post by Habitual on 2015-12-03
> **nathanhawthorne12 said:**
> as soon as i set password authentication to no, Where did you 'set' this?
please issue 
```
fail2ban-server --version | head -1 
``` output here please.

How was it installed?

Please spend some time getting comfortable with the *concepts* outlined in these documents:
[http://www.fail2ban.org/wiki/index.php/MANUAL_0_8#Configuration](http://www.fail2ban.org/wiki/index.php/MANUAL_0_8#Configuration)
[http://www.fail2ban.org/wiki/index.php/MANUAL_0_8#Jails](http://www.fail2ban.org/wiki/index.php/MANUAL_0_8#Jails)
[http://www.fail2ban.org/wiki/index.php/MANUAL_0_8#Filters](http://www.fail2ban.org/wiki/index.php/MANUAL_0_8#Filters)
[http://www.fail2ban.org/wiki/index.php/MANUAL_0_8#Actions](http://www.fail2ban.org/wiki/index.php/MANUAL_0_8#Actions) and
the actual /etc/fail2ban/jail.conf as it is excellently documented.

Stripped comment lines from /etc/fail2ban/jail.conf reveal these defaults
```
[DEFAULT]
ignoreip = 127.0.0.1/8
bantime  = 600
findtime = 600
maxretry = 3
backend = auto
usedns = warn
destemail = root@localhost
banaction = iptables-multiport
mta = sendmail
protocol = tcp
chain = INPUT
...
```

the [ssh] jail is enabled by default by the install when fail2ban is started.
```
[ssh]

enabled  = true
port     = ssh
filter   = sshd
logpath  = /var/log/auth.log
maxretry = 6
```

which shows that the /var/log/auth.log is being monitored.
maxretry and bantime values:
[COLOR=#ff0000]**maxtry = 3**[/COLOR] in the [default] section says "use maxretry = 3" everywhere no "maxretry = x"  is explicitly declared in a jail, **as the default.**
So in the above jail, if "maxretry = 6" did not exist in the jail, maxretry = 3 from [default] would be used.
**[COLOR=#ff0000]findtime = 600[/COLOR]** in the [default] section sets 10 minutes in seconds as the limit to to measure retries against, **as the default.**
It  will find all "authentication failure" entries in /var/log/auth.log for a 10 minute segment.

Example:
When maxtry = 10 and findtime = 600, this becomes
When the bad guy tries 10 ssh connects in 600s or less, he would be banned.

Values can be overwritten on a per jail basis by including a value other than what is [default]
bantime in [defaults] is 600 (seconds)
I like to discourage bad behavoir, so I increase my bantime to 1 year (again, in seconds) and the maxretry = 1
 like so:
```
[ssh]

enabled  = true
port     = ssh
filter   = sshd
logpath  = /var/log/auth.log
bantime  = 31556926
maxretry = 1
```

Quite restrictive.
1 bad ssh attempt and you're banned for a whole year.

Cautionary Notes:
```
[DEFAULT]
ignoreip = 127.0.0.1/8 xxx.xxx.0.0/16 xxx.xxx.xxx.0/24 xxx.xxx.xxx.xxx/32 192. 
```
**You should add your home computer's IP to this list. [COLOR=#ff0000]It prevents your home IP from being banned by fail2ban.[/COLOR]**
I've included the allowed IPv4 [CIDR]("https://en.wikipedia.org/wiki/Classless_Inter-Domain_Routing") formats in generic form.
IPv6 is currently not supported as far as I know.
A sole ip is /32

preauth is a red herring.

fail2ban's ssh filter scans /var/log/auth.log for "authentication failure" entries.
and I see this (among other Regular Expressions) in /etc/fail2ban/filter.d/ssh.conf
```
^%(__prefix_line)s(?:error: PAM: )?[[COLOR=#ff0000]aA[/COLOR]][COLOR=#ff0000]uthentication[/COLOR] (?:[COLOR=#ff0000]failure[/COLOR]|error) for .* from <HOST>( via \S+)?\s*$
```

If you have any questions, please check the provided links and if you're still stuck, reply here and I'll do my best to  answer them.

If this is your home computer and you have a router, fail2ban is unnecessary.
And I can't support your configuration if fail2ban is installed on your local machine and you are connecting from/to it.
There are other mechanisms that you could use (ufw/gUFW)  to secure port 22.

Where is fail2ban installed?

---

### Post by nathanhawthorne12 on 2015-12-04
Hello

Thanks for the reply.  Here goes

> [IMG]http://ubuntuforums.org/images/ubuntu-VB4/misc/quote_icon.png[/IMG][COLOR=#000000] Originally Posted by [/COLOR]**nathanhawthorne12**[[IMG]http://ubuntuforums.org/images/ubuntu-VB4/buttons/viewpost-right.png[/IMG]]("http://ubuntuforums.org/showthread.php?p=13401160#post13401160")[COLOR=#000000][I]as soon as i set password authentication to no,

[/I]
[/COLOR]
[COLOR=#000000]Where did you 'set' this?[/COLOR]

This is set in /etc/sshd ssh keys only, no root login etc

> [COLOR=#000000][FONT=Ubuntu Mono]fail2ban-server --version | head -1[/FONT][/COLOR]
[COLOR=#000000]output here please.[/COLOR]

fail2ban-server --version | head -1
Fail2Ban v0.9.3


The only jail i have is SSH

```
#
# JAILS
#


#
# SSH servers
#


[sshd]


port    = ssh
logpath = %(sshd_log)s
enabled = true



```


The other details like max retry maxban time etc are already defined in the global above the jails.  Since its systemd logpath will do what it needs to do without pointing to /var/log/***

Home PC along with work PC are both white listed, router and fail2ban are both required since access is from offsite. 
 So far it is banning just fine My wording is wrong in the first post it should have read more along the lines of (it is banning IP's but not Pre-auth) but as you said before 

> [COLOR=#000000]preauth is a red herring.[/COLOR]

this is where the problem lies as these are IP's i would like to ban also, if its not possible its not a problem

---

### Post by Habitual on 2015-12-04
Are you referring to 
```
PermitRootLogin no
...
PasswordAuthentication no

``` in /etc/ssh/sshd_config ?

One setting or both?

With "PasswordAuthentication no", the default output of 
ssh [EMAIL="user@domain.tld"]user@domain.tld[/EMAIL] is immediately Permission denied (publickey).

I wouldn't worrry about the preauth stuff, personally.

---

