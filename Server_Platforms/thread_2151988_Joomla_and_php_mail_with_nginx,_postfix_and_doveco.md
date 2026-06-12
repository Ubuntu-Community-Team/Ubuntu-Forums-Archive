---
title: "Joomla and php mail with nginx, postfix and dovecot"
date: 2013-06-06
forum: Server Platforms
---

### Post by pavar on 2013-06-06
I am running a VPS with ubuntu 12.04 , Nginx, mysql, php which I set up using this [guide]("http://www.howtoforge.com/perfect-server-ubuntu-12.04-lts-nginx-bind-dovecot-ispconfig-3") .
I run multiple domains on it without any issue. Most domains contain a Joomla 2.5 installation which works fine with a small exception.
No matter what I do, I cannot send mails. I have configured Joomla to use the php mail function, however somewhere along the way, the message get lost.
Here is a syslog extract from the moment I clicked submit in the mail form.  I have edited the emails for privacy's sake.


```

Jun  6 11:14:01 server1 CRON[23772]: (root) CMD (/usr/local/ispconfig/server/server.sh > /dev/null 2>> /var/log/ispconfig/cron.log)
Jun  6 11:14:02 server1 pure-ftpd: (?@::1) [INFO] New connection from ::1
Jun  6 11:14:02 server1 pure-ftpd: (?@::1) [INFO] Logout.
Jun  6 11:14:02 server1 postfix/smtpd[22409]: warning: hostname localhost does not resolve to address ::1: No address associated with hostname
Jun  6 11:14:02 server1 postfix/smtpd[22409]: connect from unknown[::1]
Jun  6 11:14:02 server1 postfix/anvil[1950]: statistics: max connection rate 2/60s for (smtp:::1) at Jun  6 11:05:01
Jun  6 11:14:02 server1 postfix/anvil[1950]: statistics: max connection count 1 for (smtp:::1) at Jun  6 11:05:01
Jun  6 11:14:02 server1 postfix/anvil[1950]: statistics: max cache size 1 at Jun  6 11:05:01
Jun  6 11:14:02 server1 postfix/smtpd[22409]: lost connection after CONNECT from unknown[::1]
Jun  6 11:14:02 server1 postfix/smtpd[22409]: disconnect from unknown[::1]
Jun  6 11:14:02 server1 dovecot: pop3-login: Disconnected (no auth attempts): rip=::1, lip=::1, secured
Jun  6 11:14:02 server1 dovecot: imap-login: Disconnected (no auth attempts): rip=::1, lip=::1, secured
Jun  6 11:14:42 server1 postfix/pickup[23607]: 0EA1DCF01862: uid=5006 from=<pavar@somewhere.gr>
Jun  6 11:14:42 server1 postfix/cleanup[23785]: 0EA1DCF01862: message-id=<7f58fd7910211e5bbc3ffb9c9aec5803@ihidthis.com>
Jun  6 11:14:42 server1 postfix/qmgr[734]: 0EA1DCF01862: from=<pavar@hidden.com>, size=891, nrcpt=1 (queue active)
Jun  6 11:15:01 server1 CRON[23792]: (root) CMD (/usr/local/ispconfig/server/server.sh > /dev/null 2>> /var/log/ispconfig/cron.log)
Jun  6 11:15:01 server1 CRON[23793]: (getmail) CMD (/usr/local/bin/run-getmail.sh > /dev/null 2>> /dev/null)
Jun  6 11:15:01 server1 pure-ftpd: (?@::1) [INFO] New connection from ::1
Jun  6 11:15:01 server1 pure-ftpd: (?@::1) [INFO] Logout.
Jun  6 11:15:01 server1 postfix/smtpd[22409]: warning: hostname localhost does not resolve to address ::1: No address associated with hostname
Jun  6 11:15:01 server1 postfix/smtpd[22409]: connect from unknown[::1]
Jun  6 11:15:01 server1 postfix/smtpd[22409]: lost connection after CONNECT from unknown[::1]
Jun  6 11:15:01 server1 postfix/smtpd[22409]: disconnect from unknown[::1]
Jun  6 11:15:01 server1 dovecot: imap-login: Disconnected (no auth attempts): rip=::1, lip=::1, secured
Jun  6 11:15:01 server1 dovecot: pop3-login: Disconnected (no auth attempts): rip=::1, lip=::1, secured
Jun  6 11:15:01 server1 pure-ftpd: (?@::1) [INFO] New connection from ::1
Jun  6 11:15:01 server1 pure-ftpd: (?@::1) [INFO] Logout.
Jun  6 11:15:01 server1 postfix/smtpd[22409]: warning: hostname localhost does not resolve to address ::1: No address associated with hostname
Jun  6 11:15:01 server1 postfix/smtpd[22409]: connect from unknown[::1]
Jun  6 11:15:01 server1 postfix/smtpd[22409]: lost connection after CONNECT from unknown[::1]
Jun  6 11:15:01 server1 postfix/smtpd[22409]: disconnect from unknown[::1]
Jun  6 11:15:01 server1 dovecot: pop3-login: Disconnected (no auth attempts): rip=::1, lip=::1, secured
Jun  6 11:15:01 server1 dovecot: imap-login: Disconnected (no auth attempts): rip=::1, lip=::1, secured
Jun  6 11:15:12 server1 postfix/smtp[23787]: connect to gmail-smtp-in.l.google.com[2a00:1450:400c:c00::1a]:25: Connection timed out
Jun  6 11:15:12 server1 postfix/smtp[23787]: 0EA1DCF01862: to=<pavargr@somewhere.com>, relay=gmail-smtp-in.l.google.com[173.194.78.26]:25, delay=31, delays=0.03/0.01/30/0.32, dsn=2.0.0, status=sent (250 2.0.0 OK 1370531712 lo8si28528702wjb.46 - gsmtp)
Jun  6 11:15:12 server1 postfix/qmgr[734]: 0EA1DCF01862: removed



```

I know that this:  ```
warning: hostname localhost does not resolve to address ::1: No address associated with hostname 
```
 has to do with IPv6, which I don't use, but either something is re-adding it, or I am trying to comment it out in the wrong place.

Among other things, I have not found yet a satisfactory guide for multi-domain emailing. I would like the sender email from the form to be part of the specific domain, i.e. if the form was at example.com/contact , I would like the email to be sent from info @ example.com .
Any help would be appreciated.  This is my first VPS, I managed most of what I needed by myself with some guides and a lot of logic, but this one baffles me.  I guess I don't have enough process infrastructure background to figure it out.

---

### Post by SeijiSensei on 2013-06-06
Is there an entry in /etc/hosts for localhost that points to 127.0.0.1?  If not, add one and see if that helps.

---

### Post by pavar on 2013-06-06
> **SeijiSensei said:**
> Is there an entry in /etc/hosts for localhost that points to 127.0.0.1?  If not, add one and see if that helps.

Yes, there is

```
127.0.0.1 localhost.localdomain localhost


```

---

### Post by pavar on 2013-06-06
on the other hand, I found and removed (again) ```
#::1 localhost
```

---

### Post by CharlesA on 2013-06-06
Are you able to send mail from the command line?

```
echo "Test" | mail -s "Test" emailaddress@domain.com
```

---

### Post by pavar on 2013-06-07
hmmm, i get
```
-bash: mail: command not found

```

---

### Post by CharlesA on 2013-06-07
You probably need to install the mailutils package:

```
sudo apt-get install mailutils
```

---

### Post by pavar on 2013-06-07
> **CharlesA said:**
> You probably need to install the mailutils package:

```
sudo apt-get install mailutils
```

Thanks, that did the trick. Everything works fine :)

---

### Post by pavar on 2013-06-13
I discovered 2 more issues today.  I cannot receive email, which is weird, since I had tested it and I cannot send from an email in my server to an email in my server.
in the first case, I get an "user unknown in local recipient table" response from the server, while in the second scenario I get an error "mail loops back to myself". 
Any help would be appreciated.

---

### Post by CharlesA on 2013-06-13
Are you using virtual mail accounts or does each person have an account on the physical server?

---

### Post by pavar on 2013-06-13
virtual, I think.  I created the email accounts through ispconfig3 interface.  Each email is NOT a login user

---

### Post by CharlesA on 2013-06-13
Verify the email accounts exist and make even create a test email and see if it works.

---

### Post by pavar on 2013-06-13
the email accounts are recognised by roundcube.  I can login on it (it is set to not create new accounts on login, so theoretically they should already be active for it to login). How else can I verify? Thanks

---

### Post by lisati on 2013-06-13
Postfix usually puts up a "mail loops back to myself" message when there is a DNS entry for a domain that points to your server, and Postfix hasn't been configured to recognise that domain as a one it processes.

If you're using "standard" system accounts, you'll need to add your domain to the [mydestination]("http://www.postfix.org/postconf.5.html#mydestination") line in main.cf.

For virtual domains, I don't have a short and easy "one size fits all" answer, it can depend on how you've set things up. Having said that, the process is similar. Some information can be found at [http://www.postfix.org/VIRTUAL_README.html](http://www.postfix.org/VIRTUAL_README.html)

---

### Post by pavar on 2013-06-13
thanks, I'll have a look at virtual domains via postfix. I'll reply as soon as I get a handle on things

---

