---
title: "Postfix stopped working"
date: 2005-08-05
forum: Server Platforms
---

### Post by azrail on 2005-08-05
So this is a problem I have no idea how it started.  One day my postfix server is working fine, then today it just stopped delivering mail.

mailq reports that there are 239 queued messages and that it can't deliver email because:  

B62B1E3B14     3890 Thu Aug  4 14:23:48  [email]ubuntu-devel-bounces@lists.ubuntu.com[/email]
                (delivery temporarily suspended: unknown mail transport error)
                                         [email]dave@mudsite.com[/email]

The strange thing, that I think goes hand-in-hand with this problem is that user level authentication to the mail server has stopped working.  A quick overview of my machines:

Server A - HTTP/FTP/NIS/NFS
Server B - IMAP/SMTP
Server C - Kerberos

Servers A and B both use Server C for user authentication.  Server C allows only 1 non-priv user access to the machine.  The password file is shared from Server A to Server B over NIS, as well as /home from NFS.  Both pam.d settings are the same for Server A and B.  Doing a `ypcat passwd` from server B I am able to see the users shared over NFS.

Server B's /etc/nsswitch.conf:
passwd:         compat
group:          compat
shadow:         compat

hosts:          files dns
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis

Mind you, that no config changes had been made in about 2 weeks, so I am not sure why this problem would spring up in an afternoon.  Any thoughts?

Thanks a-lot!

--
Dave ](*,)

---

### Post by azrail on 2005-08-05
I forgot to mention just a snip from my /var/log/mail.log:

Aug  5 04:47:46 dwalker2 postfix/qmgr[3969]: 54DCEE3C21: from=<mnzulvclzzetep@joymail.com>, size=1021, nrcpt=1 (queue active)
Aug  5 04:47:46 dwalker2 postfix/local[4969]: fatal: gethostbyname: Success
Aug  5 04:47:47 dwalker2 postfix/qmgr[3969]: warning: premature end-of-input on private/local socket while reading input attribute name
Aug  5 04:47:47 dwalker2 postfix/qmgr[3969]: warning: private/local socket: malformed response
Aug  5 04:47:47 dwalker2 postfix/qmgr[3969]: warning: transport local failure -- see a previous warning/fatal/panic logfile record for the problem description
Aug  5 04:47:47 dwalker2 postfix/master[3959]: warning: process /usr/lib/postfix/local pid 4969 exit status 1


--- AND --- 

Aug  5 04:40:59 dwalker2 postfix/qmgr[3969]: 7AEDEE3A42: to=<postmaster@mudsite.com>, relay=none, delay=89038, status=deferred (delivery temporarily suspended: unknown mail transport error)
Aug  5 04:40:59 dwalker2 postfix/qmgr[3969]: 9CCF1E3A4C: to=<postmaster@mudsite.com>, relay=none, delay=87377, status=deferred (delivery temporarily suspended: unknown mail transport error)
Aug  5 04:40:59 dwalker2 postfix/qmgr[3969]: 47FE2E3A6A: to=<postmaster@mudsite.com>, relay=none, delay=79368, status=deferred (delivery temporarily suspended: unknown mail transport error)
Aug  5 04:40:59 dwalker2 postfix/qmgr[3969]: DD3FCE3B87: to=<postmaster@mudsite.com>, relay=none, delay=40998, status=deferred (delivery temporarily suspended: unknown mail transport error)
Aug  5 04:40:59 dwalker2 postfix/qmgr[3969]: warning: premature end-of-input on private/local socket while reading input attribute name
Aug  5 04:40:59 dwalker2 postfix/qmgr[3969]: warning: private/local socket: malformed response
Aug  5 04:40:59 dwalker2 postfix/qmgr[3969]: warning: transport local failure -- see a previous warning/fatal/panic logfile record for the problem description
Aug  5 04:40:59 dwalker2 postfix/qmgr[3969]: warning: premature end-of-input on private/local socket while reading input attribute name

---

### Post by LordHunter317 on 2005-08-05
You're having DNS lookup issues on the box.

---

### Post by azrail on 2005-08-05
Where would I start looking why DNS resolution has suddenly stopped working.  Because another machine on the same subnet is not having this problem.

---

### Post by reid on 2005-08-08
I would start with traceroute, but you probably already knew that.

---

