---
title: "Server Security"
date: 2008-04-13
forum: Server Platforms
---

### Post by dacool25 on 2008-04-13
Hey Everyone,

This is not a thread for asking how to hack a server or anything.  I'm just wondering what the most common attacks against a ubuntu server are.  Right now I have fail2ban in place to protect against brute force crackers, but what else should I be looking out for?

I have pretty much all of the LAMP stuff going on the server.  Apache, IMAP, Postfix, PHP, DNS, FTP.

Thanks

---

### Post by shane2peru on 2008-04-13
I would install denyhost and configure it to only allow those that you know should be accessing.  It will basically secure up the sshd part of your server.  I was getting hits like crazy.  Then if you only need incoming on the web port, you can install Firestarter it is just a front end to help people like me who know nothing of iptables get them set correctly.  Those are two quick and easy layers of security, then logwatch is a great thing to install so that you can monitor your logs very nicely, that is a must to know what is going on in your server.

That is my 2cents worth, I'm sure there is more valuable suggestions out there.


Shane

---

### Post by dacool25 on 2008-04-13
Logwatch sounds pretty cool, I'm always searching through my logs for the latest break in attempts.  The only problem I have with denyhost is how is it set up?  Does it go by IP address?  If so then I'll have to constantly keep up with my dynamic IP's from my ISP.

But I think with fail2ban I have the SSH part pretty secure.  Should I be worrying about mysql or anything like that?

---

### Post by shane2peru on 2008-04-13
> **dacool25 said:**
> Logwatch sounds pretty cool, I'm always searching through my logs for the latest break in attempts.  The only problem I have with denyhost is how is it set up?  Does it go by IP address?  If so then I'll have to constantly keep up with my dynamic IP's from my ISP.

But I think with fail2ban I have the SSH part pretty secure.  Should I be worrying about mysql or anything like that?

I'm not real familiar with fail2ban, however denyhosts you can sync it with a database of known attackers.  I only access my server from within my LAN, so I can safely block about everything from the outside.  It blocks by fail log in attempts, or you can set it up so that only certain ip's are allowed.  Since I set mine up, brute force attacks have come to a screaching holt!  I still get this in my logs:
```

Apr 13 16:33:01 serve CRON[24451]: pam_unix(cron:session): session opened for user www-data by (uid=0)
Apr 13 16:33:01 serve CRON[24123]: pam_unix(cron:session): session closed for user www-data
Apr 13 16:39:01 serve CRON[24132]: pam_unix(cron:session): session opened for user root by (uid=0)
Apr 13 16:39:01 serve CRON[24132]: pam_unix(cron:session): session closed for user root

```

where it seems that someone is trying to log in via ssh, however it doesn't appear they even get a chance!

Shane

---

### Post by dacool25 on 2008-04-13
Fail2ban pretty much does something along the same lines.  You can configure it so that after 3 or so failed login attempts it will block you out for a period of time.  It has served me pretty well so far.

---

### Post by MJN on 2008-04-14
> **shane2peru said:**
> Since I set mine up, brute force attacks have come to a screaching holt! I still get this in my logs:
```

Apr 13 16:33:01 serve CRON[24451]: pam_unix(cron:session): session opened for user www-data by (uid=0)
Apr 13 16:33:01 serve CRON[24123]: pam_unix(cron:session): session closed for user www-data
Apr 13 16:39:01 serve CRON[24132]: pam_unix(cron:session): session opened for user root by (uid=0)
Apr 13 16:39:01 serve CRON[24132]: pam_unix(cron:session): session closed for user root

```
 
where it seems that someone is trying to log in via ssh, however it doesn't appear they even get a chance!
 
They are not remote login attempts - they are signs of cron doing its business in running scheduled jobs.
 
Mathew

---

### Post by shane2peru on 2008-04-14
> **MJN said:**
> They are not remote login attempts - they are signs of cron doing its business in running scheduled jobs.
 
Mathew

Ha ha!  :lolflag:  You are right!  They all say cron on them.  :oops:  I checked my logs again, and there are NO ATTEMPTS at getting into my sshd.  Just the cron jobs doing their thing.  Before I did have sshd log in attempts (before setting up denyhosts).  Thanks for pointing that out Matthew. 

Shane

---

### Post by Deathrend on 2008-04-14
Overkills is my fix for everything.  I currently use a Cisco ASA5505 as my home network head end.  Behind it, everything is wide open, which may or may not be a good idea, but it does the job and then some.

It does work amazingly well for finding even the small details, I've watched it block quite a few "attacks" that I never would have expected, be it someone looking for Apache exploits, to another trying to brute force SSH (Which still boggles me, the server would havelocked it after several attempts).

I have a rather large home network however (Two Cisco Routers, Three Cisco Switches, One Cisco Access Server), so it suits my needs more so than anything else I could have ever found.  The SSL VPN is worth it's weight in gold, one of the first true install free SSL VPN's I've found.  Best Investment I've ever made.

---

### Post by HermanAB on 2008-04-14
Fail2ban and its ilk are quite unnecessary.  Instead of running a complex script, you can do better with a single line in iptables:

# General new connection rate limiting for DOS and Brute Force protection
iptables -I INPUT -p TCP -m state --state NEW -m limit --limit 30/minute --limit -burst 5 -j ACCEPT

That single line will protect your system against practically all abuse and is the ONLY rule in my web and mail server firewalls.

Cheers,

Herman

---

