---
title: "Is somebody in my server?"
date: 2009-09-15
forum: Security
---

### Post by Lori700698 on 2009-09-15
I can't think this is normal behavior for any system, why would root try to log into webmin for anything???

```
2009 Sep 15 21:47:30  Rule Id: 5503  level: 5
Location: my-server->/var/log/auth.log
User login failed.
Sep 15 21:47:29 my-server perl: pam_unix(webmin:auth): authentication failure; logname= uid=0 euid=0 tty= ruser= rhost= user=root
```

I didn't even have my computer on or use Webmin today, (and I never use root to log into anything)so what is this?  What baffles me is that is says the login attempt came from the server its self, not an outside IP.

Thanks for looking!
Lori

---

### Post by ndefontenay on 2009-09-15
Any script requesting a root access?
Any root password change recently?

---

### Post by Lori700698 on 2009-09-15
This is the entire piece from my logs on 9-7-09 and it's the exact same today.  I'm still looking, I think I did see some type of request for a password change for root, but I can't exactly remember.  I will post it as soon as I track it down.

```
Sep  7 13:54:35 my-server su[2940]: Successful su for root by root
Sep  7 13:54:35 my-server su[2940]: + ??? root:root
Sep  7 13:54:35 my-server su[2940]: pam_unix(su:session): session opened for user root by (uid=0)
Sep  7 13:54:37 my-server su[2940]: pam_unix(su:session): session closed for user root
Sep  7 13:56:45 my-server sshd[4395]: Server listening on :: port 22.
Sep  7 13:56:46 my-server sshd[4395]: Server listening on 0.0.0.0 port 22.
Sep  7 13:56:54 my-server su[4832]: Successful su for clamav by root
Sep  7 13:56:54 my-server su[4832]: + console root:clamav
Sep  7 13:56:54 my-server su[4832]: pam_unix(su:session): session opened for user clamav by (uid=0)
Sep  7 13:57:00 my-server su[4832]: pam_unix(su:session): session closed for user clamav
Sep  7 13:57:00 my-server su[5022]: Successful su for clamav by root
Sep  7 13:57:00 my-server su[5022]: + console root:clamav
Sep  7 13:57:00 my-server su[5022]: pam_unix(su:session): session opened for user clamav by (uid=0)
Sep  7 13:57:00 my-server su[5022]: pam_unix(su:session): session closed for user clamav
Sep  7 13:57:15 my-server perl: pam_unix(webmin:auth): authentication failure; logname= uid=0 euid=0 tty= ruser= rhost=  user=root
Sep  7 13:57:18 my-server webmin[5416]: Webmin starting 
```

---

### Post by lvlint67 on 2009-09-16
just fathoming a guess here but it looks like a configuration problem with webmin.
Webmin trys to gain root access before starting which leads me to believe that it's just the daemon malfunctioning and not a hacker.

---

### Post by Lori700698 on 2009-09-16
> **lvlint67 said:**
> just fathoming a guess here but it looks like a configuration problem with webmin.
Webmin trys to gain root access before starting which leads me to believe that it's just the daemon malfunctioning and not a hacker.

Well this makes sense, now I feel silly...my paranoia is getting the better of me!  I have a few other errors I have to hunt down and figure out what they are, I will add this to my to do list.  I have one more alert I don't fully understand, I don't think it's serious but it hit's #8 on OSSEC.  I think it's snort doing something, but what is it doing?  Thank you for the help in understanding all of this!

```
 2009 Sep 16 12:00:09  Rule Id: 5104  level: 8
Location: my-server->/var/log/messages
Interface entered in promiscuous(sniffing) mode.
Sep 16 12:00:07 my-server kernel: [51236.731292] device eth0 entered promiscuous mode

2009 Sep 16 12:00:03 Rule Id: 1002 level: 2
Location: my-server->/var/log/syslog
Unknown problem somewhere in the system.
Sep 16 12:00:02 my-server snort[19124]: Check for Bounce Attacks: YES alert: YES
```

---

### Post by Lori700698 on 2009-09-16
Found it!  It looks more like something internal than somebody tinkering with changing the root or am I wrong (which seems to be a lot lately)

```
 2009 Sep 16 21:09:07  Rule Id: 5502  level: 3
Location: my-server->/var/log/auth.log
Login session closed.
Sep 16 21:09:06 my-server su[24119]: pam_unix(su:session): session closed for user root

2009 Sep 16 21:09:07 Rule Id: 5501 level: 3
Location: my-server->/var/log/auth.log
Login session opened.
Sep 16 21:09:06 my-server su[24119]: pam_unix(su:session): session opened for user root by (uid=0)

2009 Sep 16 21:09:07 Rule Id: 5303 level: 3
Location: my-server->/var/log/auth.log
User successfully changed UID to root.
Sep 16 21:09:06 my-server su[24119]: + ??? root:root

```

---

### Post by __p1n__ on 2009-09-16
The snort output is simply listing events and more should not be inferred imho.  Check your auth log if you want to see actual authorization requests and results.

---

### Post by Lori700698 on 2009-09-16
Logs show exact same thing, no more no less information.  I haven't had any luck google searching either on these couple of alerts.  I think it's ok, I'm just not 100% sure and I've been looking around for information for a week now.

---

