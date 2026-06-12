---
title: "PureFTP and fail2ban"
date: 2007-03-16
forum: Server Platforms
---

### Post by LLigetfa on 2007-03-16
First off, I'm a noob to this board so I hope I'm posting to the right forum.

I have PureFTP installed on Edgy along with fail2ban.  Not sure where I made a wrong turn but I cannot seem to get the magic formula for the failregex to actually trigger a ban.

PureFTP is logging to /var/log/messages
I was gettting some entries with DNS lookups like the following:
> Mar 11 00:33:50 lligetfa-laptop pure-ftpd: (?@222.200.161.13) [WARNING] Authentication failed for user [administrator]

Mar 11 20:09:49 lligetfa-laptop pure-ftpd: (?@wifi-ff-66-225-75-90.vianet.ca) [WARNING] Authentication failed for user [Tim]

I figured I should disable the DNS lookup feature in PureFTP with the --DontResolve switch so that now I get only IP.
I'm really weak on my RegEx stuff so I asked for help on another forum and it was suggested that I give the following regex a go:
> failregex = pure-ftpd.*\(\?@<host>\).*Authentication failed
It doesn't work and I've yet to stumble upon one that does.  It seems like the <host> tag plays an important part but not sure what.  If I take it out and try to use a simple "old style" regex, the log fills up with warnings.  Makes it tough to find the magic combo.

Anyone know if fail2ban can parse /var/log/messages log?
If so, any advise on the right failregex syntax?

Please help!

---

### Post by LLigetfa on 2007-03-17
Hmmm... no takers yet huh...
Perhaps I should have mentioned that I installed version 0.6.1-8 [http://packages.ubuntu.com/edgy/net/fail2ban](http://packages.ubuntu.com/edgy/net/fail2ban) and in reading the changelog, ver. 0.6.2 (2006/12/11) is the latest stable.  One of the noted changes is:> Added named group "host" for "failregex"
I have no idea where to get .0.6.2 and how to install it on Edgy or if it would even solve my problem.

Anyone?

---

### Post by LLigetfa on 2007-03-19
Nevermind... found my answer elsewhere.

---

