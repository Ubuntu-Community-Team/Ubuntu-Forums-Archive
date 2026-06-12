---
title: "[SOLVED] saslauthd won't work from other ip's"
date: 2008-01-24
forum: Server Platforms
---

### Post by yino on 2008-01-24
Hello:
I have a problem with postfix and sasl, if i login from the webmail there's no problem, but if I login from outlook at other computer it won't let me, log says this:

> Jan 24 16:39:23 infoweb postfix/smtpd[27365]: warning: SASL authentication failure: cannot connect to saslauthd server: Permission denied
Jan 24 16:39:23 infoweb postfix/smtpd[27365]: warning: unknown[172.17.83.13]: SASL LOGIN authentication failed: generic failure

---

### Post by MJN on 2008-01-24
Can you post your log showing the successful authentication by your webmail client? Are you sure it is authenticating with Postfix (webmail-based servers, if residing on the same server as Postfix, usually do not authenticate as they are 'trusted' given they authenticate the user themselves).

It is important we ascertain whether or not SASL authentication is indeed working for local clients.

How have you configured saslauthd?

The issue is likely that Postfix is running chrooted and hence cannot access saslauthd outside of its root.

Mathew

---

### Post by yino on 2008-01-25
Forget it, I got a hacked last night

> Jan 24 19:19:16 infoweb postfix/smtpd[28166]: warning: non-SMTP command from 122-116-17-133.HINET-IP.hinet.net[122.116.17.133]: GET [http://www.scanproxy.com:80/px_judge.php?p=25](http://www.scanproxy.com:80/px_judge.php?p=25) HTTP/1.0Now whenever i try to log in with the webmail i get this in the log

> Jan 25 11:35:42 infoweb postfix/smtpd[29279]: connect from 122-116-17-133.HINET-IP.hinet.net[122.116.17.133]
Jan 25 11:35:43 infoweb postfix/smtpd[29279]: NOQUEUE: reject: RCPT from 122-116-17-133.HINET-IP.hinet.net[122.116.17.133]: 504 5.5.2 <my.ip>: Helo command rejected: need fully-qualified hostname; from=<rurdhd@hotmail.com> to=<toxxx@mail2000.com.tw> proto=SMTP helo=<my.ip>
Jan 25 11:35:43 infoweb postfix/smtpd[29279]: lost connection after RCPT from 122-116-17-133.HINET-IP.hinet.net[122.116.17.133]
Jan 25 11:35:43 infoweb postfix/smtpd[29279]: disconnect from 122-116-17-133.HINET-IP.hinet.net[122.116.17.133]anyway, I know sasl is working for local
> 
# testsaslauthd -u user -p passwd
0: OK "Success."


---

### Post by MJN on 2008-01-25
> **yino said:**
> Forget it, I got a hacked last night
 
There's nothing from that log entry that suggests you were hacked - it was just an attempt (and a common one at that) to find an open proxy.
 
> Now whenever i try to log in with the webmail i get this in the log
 
That log is not you logging in via webmail (and it certainly has got nothing to do with last night's 'hack'). It is the connection from a remote MTA which did not announce a fully qualified HELO name. As this is a common spammers trait your mail server has rejected the connection. You configured Postfix to do this so there is no problem here.
 
> anyway, I know sasl is working for local
 
That only shows saslauthd is working for **you** - not that it will work for Postfix, running in a chroot jail.
 
Mathew

---

### Post by yino on 2008-01-25
> **MJN said:**
> There's nothing from that log entry that suggests you were hacked - it was just an attempt (and a common one at that) to find an open proxy.

Phew, that's a relief thanks
 

 > **MJN said:**
> That log is not you logging in via webmail (and it certainly has got nothing to do with last night's 'hack'). It is the connection from a remote MTA which did not announce a fully qualified HELO name. As this is a common spammers trait your mail server has rejected the connection. You configured Postfix to do this so there is no problem here.

But I get it everytime I try to connect from webmail, is too much concidence, but anyway here is me logging via webmail (webmail is with postfix and dovecot in the same computer)
> Jan 24 13:52:18 infoweb postfix/smtpd[25323]: connect from infoweb.domain[my.ip]
Jan 24 13:52:18 infoweb postfix/smtpd[25323]: 3E3139349A6: client=infoweb.domain[my.ip]
 

 > **MJN said:**
> That only shows saslauthd is working for **you** - not that it will work for Postfix, running in a chroot jail.
 
Sorry, but I'm new at this, how can I know it?.

---

### Post by MJN on 2008-01-25
> **yino said:**
> But I get it everytime I try to connect from webmail, is too much concidence, but anyway here is me logging via webmail (webmail is with postfix and dovecot in the same computer)
 
That log snippet is different to the one previously posted, and is entirely normal. The coincidence is likely just that you are being regularly bombarded with spam attempts.
 
> Sorry, but I'm new at this, how can I know it?.
 
There are so many ways to implement SASL authentication with Postfix that you really need to consult the guide you followed (which I assume you did?) to see what's gone wrong.
 
Mathew
 
P.S. Use [code] tabs (the # button) around bits of codes/logs/etc as opposed to quotes (otherwise when I quote you the snippets disappear)

---

### Post by yino on 2008-01-25
> **MJN said:**
> That log snippet is different to the one previously posted, and is entirely normal. The coincidence is likely just that you are being regularly bombarded with spam attempts.

This is what I get when I log in from the webmail after the "spam attempt"
```
Jan 25 13:08:54 infoweb postfix/smtpd[29815]: connect from 122-116-17-133.HINET-IP.hinet.net[122.116.17.133]
Jan 25 13:08:55 infoweb postfix/smtpd[29815]: NOQUEUE: reject: RCPT from 122-116-17-133.HINET-IP.hinet.net[122.116.17.133]: 504 5.5.2 <my.ip>: Helo command rejected: need fully-qualified hostname; from=<rurdhd@hotmail.com> to=<toxxx@mail2000.com.tw> proto=SMTP helo=<my.ip>
Jan 25 13:08:55 infoweb postfix/smtpd[29815]: lost connection after RCPT from 122-116-17-133.HINET-IP.hinet.net[122.116.17.133]
Jan 25 13:08:55 infoweb postfix/smtpd[29815]: disconnect from 122-116-17-133.HINET-IP.hinet.net[122.116.17.133]
```checking before the spam attempt, it didn't use postfix authentication, just imap, it made login to postfix just when sending or receiving a mail, I'm starting to get confused.
Anyway, I didn't have that problem when doing  **telnet localhost 25**

```
Jan 25 13:06:31 infoweb postfix/smtpd[29804]: connect from localhost[127.0.0.1]
```
and ehlo infoweb.mydomain says

```

ehlo infoweb.mydomain
250-infoweb.mydomain
250-PIPELINING
250-SIZE 102400
250-VRFY
250-ETRN
250-STARTTLS
250-AUTH PLAIN LOGIN
250-AUTH=PLAIN LOGIN
250-ENHANCEDSTATUSCODES
250-8BITMIME
250 DSN

```So I guess that saslauthd is working well

---

### Post by yino on 2008-01-25
I restarted postfix, and the problem is gone.
Thanks for all the support.

---

### Post by yino on 2008-01-25
Here's my saslauthd configuration file
```

START=yes

PWDIR="/var/spool/postfix/var/run/saslauthd"
PARAMS="-m ${PWDIR}"
PIDFILE="${PWDIR}/saslauthd.pid"

MECHANISMS="pam"

MECH_OPTIONS=""

THREADS=0

OPTIONS="-c"

```

---

### Post by yino on 2008-01-25
fixed it, changed the folloowing line in saslauthd configuration file
```

OPTION="-c -m /var/spool/postfix/var/run/saslauthd"

```

now outlook logs in

---

