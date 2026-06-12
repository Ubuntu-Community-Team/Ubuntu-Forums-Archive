---
title: "denyhosts vs fail2ban"
date: 2008-09-22
forum: Security
---

### Post by CaptSaltyJack on 2008-09-22
Subject says it all... thoughts?

---

### Post by hyper_ch on 2008-09-22
what do you think?

---

### Post by CaptSaltyJack on 2008-09-22
Dunno man, that's why I posted :)  I have no experience with fail2ban.  denyhosts is nice but it only works with ssh, whereas fail2ban works with other services (which ones exactly? any of them? even SVN?), so that's cool.

But I wanted to hear from people who have experience with both.

---

### Post by hyper_ch on 2008-09-22
denyhosts doesn't only work with ssh

---

### Post by CaptSaltyJack on 2008-09-22
Oh.  I thought it was ssh only.

From the denyhosts man page:

>        DenyHosts  is a python program that automatically blocks ssh attacks by
       adding entries to /etc/hosts.deny.

From the APT description:

> an utility to help sys admins thwart ssh hackers
    DenyHosts is a program that automatically blocks ssh brute-force attacks by
    adding entries to /etc/hosts.deny. It will also inform Linux administrators
    about offending hosts, attacked users and suspicious logins.

So I dunno, that sounds like it's for ssh protection only.

---

### Post by hyper_ch on 2008-09-22
have a look at its config.

---

### Post by CaptSaltyJack on 2008-09-22
Ok, so there's this:

```


#######################################################################
#
# BLOCK_SERVICE: the service name that should be blocked in HOSTS_DENY
#
# man 5 hosts_access for details
#
# eg.   sshd: 127.0.0.1  # will block sshd logins from 127.0.0.1
#
# To block all services for the offending host:
BLOCK_SERVICE = ALL
# To block only sshd:
#BLOCK_SERVICE  = sshd

```

But that only instructs denyhosts how to write hosts into /etc/hosts.deny.  So, my hosts.deny looks like this:

```

ALL: 88.55.220.189
ALL: 64.5.159.15
ALL: 75.34.53.169
ALL: 66.120.181.28
ALL: 194.204.212.253
ALL: 62.128.130.94
ALL: 83.222.195.178
ALL: 85.15.207.111
ALL: 58.211.78.204

```

But that doesn't mean that denyhosts will watch for suspicious logins on services other than ssh.  It just means once someone tries to break in via ssh, it blocks that IP for ALL services.

Incidentally, I don't know what the heck services pay attention to /etc/hosts.deny.  Apache sure doesn't.  Not sure if my mail server does.  So I'm wondering what good /etc/hosts.deny is besides blocking ssh access?

---

### Post by hyper_ch on 2008-09-22
denyhosts will check the auth.log were user login is logged... if you hit the limit then that IP will be added to /etc/hosts.deny... depending on what is in there (ssh/all) it will just block those remote IPs from ssh or from all services...

so, if an IP is blocked in /etc/hosts.deny and is set to "ALL" then this IP cannot acces, for example, your apache server on that computer. Connection will be dropped immediately when it tries to "access" that computer in anway.

---

### Post by CaptSaltyJack on 2008-09-22
> **hyper_ch said:**
> so, if an IP is blocked in /etc/hosts.deny and is set to "ALL" then this IP cannot acces, for example, your apache server on that computer. Connection will be dropped immediately when it tries to "access" that computer in anway.

Actually, my apache2 server will allow anyone in.  Apache does not look at /etc/hosts.deny.  Try it yourself, you'll see (unless you have Apache configured differently than how it gets installed/configured from the Ubuntu repository).

---

### Post by hyper_ch on 2008-09-22
yeah, apache was a bad example :)

---

### Post by CaptSaltyJack on 2008-09-22
So the question is, which services DO actually look at /etc/hosts.deny besides ssh?

---

### Post by HermanAB on 2008-09-22
The better solution is to use new connection rate limiting in iptables.  That protects against all kinds of net abuse.

---

### Post by CaptSaltyJack on 2008-09-22
> **HermanAB said:**
> The better solution is to use new connection rate limiting in iptables.  That protects against all kinds of net abuse.

Cool..where can I read up on that? (something a little more engaging and helpful than the man page for iptables which happens to be extremely long) :)

---

### Post by kevdog on 2008-09-22
Here is one post describing the use of the rate limiting module:

[http://www.linux-noob.com/forums/index.php?showtopic=1829](http://www.linux-noob.com/forums/index.php?showtopic=1829)

If you google iptables rate limiting it will come up with a bunch of links.

Here is another example:

[http://www.steveglendinning.com/2008/01/27/protecting-against-ssh-brute-force-password-attacks/](http://www.steveglendinning.com/2008/01/27/protecting-against-ssh-brute-force-password-attacks/)

It compares various methods.

---

### Post by dgar on 2009-06-19
Rate limiting in Jaunty and above:

ufw limit 80
ufw limit 443
ufw limit 22

Careful with limits on webservers, would a pipelineing browser trip it?

---

### Post by bodhi.zazen on 2009-06-20
> **dgar said:**
> Rate limiting in Jaunty and above:

ufw limit 80
ufw limit 443
ufw limit 22

Careful with limits on webservers, would a pipelineing browser trip it?

That is a nice feature of ufw. I do this with iptables as once you learn the syntax it is quite easy. I allow many more connections for http/https and limit ssh. Take care with ssh, if you are using scp or svn+ssh (especially svn+ssh) each file can be a new connection, so you may need to be more liberal if you want to allow commit (svn) or scp over ssh.

---

### Post by darkblackcorner on 2010-11-20
So from what I understand:

 - denyhosts detects ssh abuse and can ban all services using tcp-wrappers, though not all services are compatible with tcp-wrappers.

 - fail2ban detects abuse on all services and can ban all services...does it use iptables?

Are there any other options for similar functionality?

---

### Post by CharlesA on 2010-11-20
Necro. Closed.

---

