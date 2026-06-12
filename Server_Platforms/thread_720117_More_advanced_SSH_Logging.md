---
title: "More advanced SSH Logging"
date: 2008-03-09
forum: Server Platforms
---

### Post by dacool25 on 2008-03-09
Hello, 

On one of my webservers SSH is constantly trying to be broken into.  Now I periodically look into the auth.log, but there isn't too much information besides their IP address.

In /etc/ssh/sshd_config there is an option to put in more logging, What does more logging entail?

Thansk

---

### Post by Oldsoldier2003 on 2008-03-09
> **dacool25 said:**
> Hello, 

On one of my webservers SSH is constantly trying to be broken into.  Now I periodically look into the auth.log, but there isn't too much information besides their IP address.

In /etc/ssh/sshd_config there is an option to put in more logging, What does more logging entail?

Thansk
set up DenyHosts, granted it wont give you more logging, but it will block the brute force attacks.

edit: in addition to denyhosts you can also set up publickey authentication and jailkit your users to tighten up security even more. For the most part changing the listening port for ssh is only going to stop the script kiddies, beacuse a port scan will reveal where ssh listens anyhow.

---

### Post by Dr Small on 2008-03-09
I too am also curious to know this.
I read this from the sshd_config man page:
>      LogLevel
             Gives the verbosity level that is used when logging messages from
             sshd.  The possible values are: QUIET, FATAL, ERROR, INFO, VER&#8208;
             BOSE, DEBUG, DEBUG1, DEBUG2 and DEBUG3.  The default is INFO.
             DEBUG and DEBUG1 are equivalent.  DEBUG2 and DEBUG3 each specify
             higher levels of debugging output.  Logging with a DEBUG level
             violates the privacy of users and is not recommended.


But it doesn't tell much... :|

---

### Post by dacool25 on 2008-03-09
Well I already have something called fail2ban which will block after about 3 failed logins (I think my password will take more than 3 tries).  But I will look into those.

But yes where I originally found out was from the ssh man page.  Does anyone know what else is included if you use something with a little more umph in it?

Also is there any more configuring you must do with this, for example with your syslog config file?

Thanks

---

### Post by netlogic on 2008-03-10
Isn't it easier to use public/private key and keep your keys in an encrypted volume?

---

### Post by Dr Small on 2008-03-10
I found out that the LogLevels which are defined in the man page show up in your authlog. If you edit your sshd_config file and set the LogLevel to DEBUG for example, and then restart ssh, now all your logs in the auth.log are now in DEBUG mode (for ssh).

Then to view them, you can do:
```
tail -f /var/log/auth.log | grep ssh
```

And the log format will be in DEBUG mode.

Dr Small

---

### Post by dacool25 on 2008-03-10
Thanks Dr. Small,

The only thing that concerns me about that is that I run fail2ban which uses the log to judge who it blocks out, So if I change that I don't want fail2ban to stop working.

---

### Post by MJN on 2008-03-10
> **dacool25 said:**
> Hello, 
 
On one of my webservers SSH is constantly trying to be broken into. Now I periodically look into the auth.log, but there isn't too much information besides their IP address.
 
What more do you want to know? I thought that by default the log gives remote IP address and attempted username - is there anything else you actually want/need?
 
be very careful increasing verbosity of logs as you can end up being drowned in unnecessary 'information' serving no real purpose and thus risk missing what's actually important.
 
Mathew

---

### Post by Oldsoldier2003 on 2008-03-10
> **MJN said:**
> What more do you want to know? I thought that by default the log gives remote IP address and attempted username - is there anything else you actually want/need?
 
be very careful increasing verbosity of logs as you can end up being drowned in unnecessary 'information' serving no real purpose and thus risk missing what's actually important.
 
Mathew

yep, by default you get ip address and attempted username

---

### Post by lespaul_rentals on 2008-03-10
> **MJN said:**
> What more do you want to know? I thought that by default the log gives remote IP address and attempted username - is there anything else you actually want/need?
 
be very careful increasing verbosity of logs as you can end up being drowned in unnecessary 'information' serving no real purpose and thus risk missing what's actually important.
 
Mathew

This is exactly correct.  I'm not sure what kind of information you would need other than time and date of connection attempt, attempted username, and source IP address, which you already have.

What username are they trying to use to get into your server?  I'm guessing it's something like "administrator," "guest," or "root," am I right?  So long as you have no users that match those names on your server (and you disable root login like a good server administrator) you should be fine.  Just check the logs every now and then and ban them.

---

### Post by Oldsoldier2003 on 2008-03-10
> **lespaul_rentals said:**
> This is exactly correct.  I'm not sure what kind of information you would need other than time and date of connection attempt, attempted username, and source IP address, which you already have.

What username are they trying to use to get into your server?  I'm guessing it's something like "administrator," "guest," or "root," am I right?  So long as you have no users that match those names on your server (and you [COLOR="Red"]disable root login[/COLOR] like a good server administrator) you should be fine.  Just check the logs every now and then and ban them.

edit roots entry in etc passwd to make its shell /bin/false and disable root logins in /etc/ssh/sshd_config

changing the shell prevents an interactive sudo, but if you need it you can always redeit the passwd file for the time you need an sudo root session.

denyhosts can automate the banning process. jail your untrusted ssh users and edit sudo permissions and you're pretty much rock solid.

---

