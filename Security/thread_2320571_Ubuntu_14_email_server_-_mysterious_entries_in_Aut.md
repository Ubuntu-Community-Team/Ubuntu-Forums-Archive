---
title: "Ubuntu 14 email server - mysterious entries in Auth log"
date: 2016-04-15
forum: Security
---

### Post by Icarusbop on 2016-04-15
I have an Ubuntu 14 email server using postfix, mysql, amavisd,courier, spamassassin, clam av and SASL.
All seems to be working Ok, but I have noticed some dodgy looking entries in my Auth.log. Here is a clip from the authlog (abridged)
```
Apr 15 14:19:55 vps postfix/smtpd[2931]: sql plugin create statement from userPassword [COLOR=#ff0000]energy vps.MyDomain.co.uk[/COLOR]
Apr 15 14:19:55 vps postfix/smtpd[2931]: sql plugin: no result found
Apr 15 14:19:55 vps postfix/smtpd[2931]: sql plugin trying to open db 'maildb' on host '127.0.0.1'
Apr 15 14:22:35 vps postfix/smtpd[2933]: begin transaction
Apr 15 14:22:35 vps postfix/smtpd[2933]: sql plugin create statement from userPassword [COLOR=#ff0000]enrique vps.MyDomain.co.uk[/COLOR]
Apr 15 14:22:35 vps postfix/smtpd[2933]: sql plugin: no result found
Apr 15 14:22:35 vps postfix/smtpd[2933]: commit transaction
Apr 15 14:22:35 vps postfix/smtpd[2933]: sql plugin Parse the username enrique
Apr 15 14:22:35 vps postfix/smtpd[2933]: sql plugin try and connect to a host
Apr 15 14:22:35 vps postfix/smtpd[2933]: sql plugin trying to open db 'maildb' on host '127.0.0.1'
Apr 15 14:23:49 vps postfix/smtpd[2933]: sql plugin Parse the username [EMAIL="acer@mydomin.co.uk"][COLOR=#ff0000]acer@mydomin.co.uk[/COLOR][/EMAIL]
Apr 15 14:23:49 vps postfix/smtpd[2933]: sql plugin try and connect to a host
Apr 15 14:23:49 vps postfix/smtpd[2933]: sql plugin trying to open db 'maildb' on host '127.0.0.1'
Apr 15 14:23:49 vps postfix/smtpd[2933]: begin transaction
Apr 15 14:23:49 vps postfix/smtpd[2933]: sql plugin create statement from userPassword acer MyDomain.co.uk
Apr 15 14:23:49 vps postfix/smtpd[2933]: sql plugin: no result found
```

None of the names seen in the log are in the system and the system is currently not in use. I did a check for active connections and found this:
```
Proto Recv-Q Send-Q Local Address           Foreign Address         State
tcp        0      0 localhost:56632         localhost:mysql         TIME_WAIT
tcp        0      0 localhost:56633         localhost:mysql         TIME_WAIT
```

(I have removed known connections) I think these are the MySQL connections that are causing the entries in the auth.log, but I have no (known) software running and the names are vaguely alphabetical.
This is still happening, so it is current not historical, I get an entry in the log approx. every 3 mins. The names are now up to "[EMAIL="joyce@vps"]joyce@vps[/EMAIL]..."
So - it looks like the unknown connection is from inside my server, not external. Does anyone know what may be causing this? I suspect I have a virus(the firewall is on), but it took me three weeks to build the server so am hoping there is a less upsetting answer...
Thanks.

---

### Post by Doug S on 2016-04-15
Readers: See some progress on this one over on [ask]("http://askubuntu.com/questions/757683/ubuntu-14-mysterious-entries-in-auth-log").

---

### Post by T.J. on 2016-04-15
Without seeing your Postfix setup,  knowing if you have a static IP or redirected dynamic IP, your firewall configuration. and if you are using LDAP or just a database, I can't say for sure what this is. I simply need more information.  

What it looks like is that your Postfix is configured to use a SQL database, and someone is trying to connect, probably a spammer looking for a free relay.  If you are going to run your own mail service and allow for incoming transfers, you are going to be eventually inundated by spammers.  As a former systems administrator, I can tell you that it's part and parcel to the whole business, and you might as well get used to it.  It's been some time (years) since I left the business, and the techniques have probably changed, so take my advice under advisement only.

If you can't limit your connections to certain hosts or need to manage a general email server accessible worldwide, I'd suggest that you consider implementing a greylist and/or SPF.  I would combine that with a firewall or router solution to deny connections from an IP after too many failed attempts.

---

### Post by Icarusbop on 2016-04-15
Hello:  I found this entry in the postfix logs. warning: unknown[185.125.4.196]: SASL LOGIN authentication failed.
The entry times match up with the auth log times.
I have blocked the IP range (Poland) in UFW and it's gone quiet now.
 I'll need to investigate a more robust anti-brute force solution.

Thanks for your rely - I am investigating a Greylist but last time I switched it on none of my emails arrived. Please can you clarify what an SPF is?

---

### Post by Seb_Boffen on 2016-04-15
I'd advise to install fail2ban on your server.

---

### Post by T.J. on 2016-04-15
> **Icarusbop said:**
> Thanks for your rely - I am investigating a Greylist but last time I switched it on none of my emails arrived. Please can you clarify what an SPF is?


SPF is Sender Policy Framework.   [https://en.wikipedia.org/wiki/Sender_Policy_Framework](https://en.wikipedia.org/wiki/Sender_Policy_Framework)

SPF essentially checks the header of the message against the DNS MX (Mail Exchange) records of the sending host to see if the message originated at the domain's mail server or if the header has been faked.  It it has, the message is usually discarded or marked as spam rather than processed further. For example, an email with a header claiming to come from google.com would have the sending IP checked to see if the IP actually is one of Google's mailservers. 

 If it is not done correctly, it can annoy other administrators by generating extra traffic to their servers.  Personally, I consider it the best tool to kill off spammers, as 80-90% of spam mail uses faked headers. I should say, "It used to be." as I have been out of the business for about 6 years or more.

---

