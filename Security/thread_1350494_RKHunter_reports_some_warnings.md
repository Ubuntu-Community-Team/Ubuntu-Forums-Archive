---
title: "RKHunter reports some warnings"
date: 2009-12-09
forum: Security
---

### Post by dacoman on 2009-12-09
Hello,

Since Dec 2nd, the rkhunter on my server Ubuntu 8.04 started reporting several warnings here they are: 

```
Warning: Network TCP port 1524 is being used by /usr/sbin/portsentry. Possible rootkit: Possible FreeBSD (FBRK) Rootkit backdoor
         Use the 'lsof -i' or 'netstat -an' command to check this.
Warning: Network TCP port 6667 is being used by /usr/sbin/portsentry. Possible rootkit: Possible rogue IRC bot
         Use the 'lsof -i' or 'netstat -an' command to check this.
Warning: Network TCP port 31337 is being used by /usr/sbin/portsentry. Possible rootkit: Historical backdoor port
         Use the 'lsof -i' or 'netstat -an' command to check this.
Warning: Application 'gpg', version '1.4.9', is out of date, and possibly a security risk.
Warning: Application 'openssl', version '0.9.8g', is out of date, and possibly a security risk.
Warning: Application 'php', version '5.2.6', is out of date, and possibly a security risk.
Warning: Application 'sshd', version '5.1p1', is out of date, and possibly a security risk.
```


Is this something I should worry about or is just rkhunter being overzealous?

Thank you,
-D

---

### Post by styxcoverbnd on 2009-12-09
I created a [thread](http://ubuntuforums.org/showthread.php?t=1342508) with similar rkhunter questions a week ago. Rkhunter recently released a new version 1.3.6. Hardy is still using version 1.3, but a new .dat definiton file (for 1.3.6) was pushed down and is causing these warnings in 1.3. 

If your system is up to date there is nothing to really worry about. The warnings state: 'is out of date, and possibly a security risk', but they are not really a security risk. An LTS release is going to use an older stable version of a program so the the 'possibly security risk' makes it sound insecure when it really is not

---

### Post by brendankehoe on 2009-12-10
I've modified /etc/rkhunter.conf to do

   APP_WHITELIST="gpg:1.4.9 openssl:0.9.8g sshd:5.1p1"

to make it not complain about the three specific programs I've got under Ubuntu 9.10.

Hopefully that'll hush it up. :D

---

### Post by FuturePilot on 2009-12-10
> **brendankehoe said:**
> I've modified /etc/rkhunter.conf to do

   APP_WHITELIST="gpg:1.4.9 openssl:0.9.8g sshd:5.1p1"

to make it not complain about the three specific programs I've got under Ubuntu 9.10.

Hopefully that'll hush it up. :D

Great! Thanks. I didn't notice that option in rkhunter.conf before. I'm tired of getting emails from my servers about this. Grrrrr :x

---

### Post by yaddoshi on 2010-01-30
Is there a way to disable the Portsentry related warnings?

---

### Post by unspawn on 2010-01-31
> **yaddoshi said:**
> Is there a way to disable the Portsentry related warnings?
See rkhunter.conf, "PORT_WHITELIST".

---

### Post by sibaz on 2010-02-01
I've got a similar problem.  I've got Ubuntu 8.04 LTS running on one of our servers, and having fixed everything else, I'm getting these errors every day:-

```
Error: Invalid display - language keyword cannot be found: Display line: display --to LOG --type PLAIN --result OK --log-indent 4 ROOTKIT_ADD_SUCKIT_LINK
Error: Invalid display - language keyword cannot be found: Display line: display --to LOG --type INFO STARTUP_FOUND_LOCAL_RC_FILE /etc/rc.local
Error: Invalid display - language keyword cannot be found: Display line: display --to LOG --type INFO STARTUP_FOUND_LOCAL_RC_FILE /etc/rc.local
Error: Invalid display - language keyword cannot be found: Display line: display --to SCREEN+LOG --type PLAIN --color GREEN --result FOUND --log-indent 2 --screen-indent 4 STARTUP_LOCAL_RC_FILE
Error: Invalid display - language keyword cannot be found: Display line: display --to SCREEN+LOG --type PLAIN --color GREEN --result NONE_FOUND --log-indent 2 --screen-indent 4 STARTUP_CHECK_LOCAL_RC
Error: Invalid display - language keyword cannot be found: Display line: display --to LOG --type INFO STARTUP_CHECK_SYSTEM_RC_FOUND /etc/init.d
Error: Invalid display - language keyword cannot be found: Display line: display --to SCREEN+LOG --type PLAIN --result NONE_FOUND --color GREEN --log-indent 2 --screen-indent 4 STARTUP_CHECK_SYSTEM_RC
```

I'm assuming it's down to the mismatch of .dat files also.  Is there anyway I can make it stop?

Simon

---

### Post by unspawn on 2010-02-01
> **sibaz said:**
> I'm assuming it's down to the mismatch of .dat files
Might be two mixed installations: easiest would be to remove both then install.

---

### Post by yaddoshi on 2010-02-05
> **unspawn said:**
> See rkhunter.conf, "PORT_WHITELIST".

Thanks!:popcorn:

---

