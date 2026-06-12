---
title: "sendmail and rkhunter"
date: 2011-11-30
forum: Security
---

### Post by mikegior on 2011-11-30
Hello all,

I recently installed rkhunter and during the apt-get installation sendmail was installed as a requirement (for reporting via email I suppose), which didn't give me a good vibe but I let it go.

I was playing around with security and decided to nmap myself. I saw that port 25 was open for sendmail, obviously. Upon seeing that, I decided to telnet into port 25 and just see if SMTP relay was possible. 

```

michael@eternity:~$ telnet localhost 25
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
220 eternity ESMTP Postfix (Ubuntu)
ehlo localhost
 250-eternity
250-PIPELINING
250-SIZE 10240000
250-VRFY
250-ETRN
250-STARTTLS
250-ENHANCEDSTATUSCODES
250-8BITMIME
250 DSN
mail from:root@localhost
 250 2.1.0 Ok
rcpt to:mail@localhost
250 2.1.5 Ok
data
354 End data with <CR><LF>.<CR><LF>
Test
.
250 2.0.0 Ok: queued as 52AAB6C0D93
 quit
221 2.0.0 Bye
Connection closed by foreign host.

```I then ran 'sudo su' to get a root shell and moved into /var/spool/mail and ran 'car root' and saw that test message I sent to root@localhost. Mind you this was all local on my machine. If I, however, attempt to telnet to port 25 on my Ubuntu box from another machine the connection fails. Does this mean that my Ubuntu box is denying connection to the sendmail daemon? If so, then I understand there's no way for this SMTP relay to be taken advantage of remotely.

At the same time, I would prefer if sendmail was not running and/or installed on my machine as I see no practical use for sendmail given what I do, but I would still like rkhunter too and I'm not sure if removing sendmail will effect this. The best (ongoing) way to ensure a system is LESS vulnerable is to ensure there are no unnecessary services running that are exploitable.

---

### Post by Dangertux on 2011-11-30
> **mikegior said:**
> Hello all,

I recently installed rkhunter and during the apt-get installation sendmail was installed as a requirement (for reporting via email I suppose), which didn't give me a good vibe but I let it go.

I was playing around with security and decided to nmap myself. I saw that port 25 was open for sendmail, obviously. Upon seeing that, I decided to telnet into port 25 and just see if SMTP relay was possible. 

```

michael@eternity:~$ telnet localhost 25
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
220 eternity ESMTP Postfix (Ubuntu)
ehlo localhost
 250-eternity
250-PIPELINING
250-SIZE 10240000
250-VRFY
250-ETRN
250-STARTTLS
250-ENHANCEDSTATUSCODES
250-8BITMIME
250 DSN
mail from:root@localhost
 250 2.1.0 Ok
rcpt to:mail@localhost
250 2.1.5 Ok
data
354 End data with <CR><LF>.<CR><LF>
Test
.
250 2.0.0 Ok: queued as 52AAB6C0D93
 quit
221 2.0.0 Bye
Connection closed by foreign host.

```I then ran 'sudo su' to get a root shell and moved into /var/spool/mail and ran 'car root' and saw that test message I sent to root@localhost. Mind you this was all local on my machine. If I, however, attempt to telnet to port 25 on my Ubuntu box from another machine the connection fails. Does this mean that my Ubuntu box is denying connection to the sendmail daemon? If so, then I understand there's no way for this SMTP relay to be taken advantage of remotely.

At the same time, I would prefer if sendmail was not running and/or installed on my machine as I see no practical use for sendmail given what I do, but I would still like rkhunter too and I'm not sure if removing sendmail will effect this. The best (ongoing) way to ensure a system is LESS vulnerable is to ensure there are no unnecessary services running that are exploitable.


The sendmail service installed with rkhunter is not installed as an open relay, as it is tcp wrapped. Optionally if it makes you feel more comfortable you can remove sendmail.

```

sudo apt-get remove sendmail

```

This will however break the email functionality of rkhunter, though it will still store logs in /var/log/rkhunter.log

Alternatively you can use iptables (or your front end of choice) to create firewall rules that close it off from external access, though this is already accomplished with tcp wrappers.

---

### Post by mikegior on 2011-11-30
I uninstalled sendmail, but the SMTP server is still present. I noticed postfix is still listed in /etc/init.d  and that's the mail server, correct? Is that normally installed with Ubuntu 11.10 (desktop) out of the box or could have rkhunter installed this in conjunction with sendmail?

---

### Post by mikegior on 2011-11-30
Also, after doing 'sudo service postfix stop' and attempting to telnet to port 25 the connection is then refused and unable to connect.

---

### Post by Dangertux on 2011-11-30
> **mikegior said:**
> Also, after doing 'sudo service postfix stop' and attempting to telnet to port 25 the connection is then refused and unable to connect.


Hey sorry I didn't get back to this sooner -- but sendmail and postfix are both MTAs. Generally speaking sendmail does not run in daemon mode when installed by an application. Perhaps something else you installed along the way installed postfix as well (which usually will run daemonized).

Hope this helps.

---

### Post by mikegior on 2011-12-01
Since I have no practical use for a mail daemon to be running, can I do 'sudo apt-get remove postfix'?

---

### Post by Dangertux on 2011-12-01
> **mikegior said:**
> Since I have no practical use for a mail daemon to be running, can I do 'sudo apt-get remove postfix'?


So long as nothing depends on it to function -- You might consider finding out what application installed , or you could just remove it and see what breaks (if anything).

Hope this helps.

---

