---
title: "Cannot get Postfix to relay mail."
date: 2014-12-21
forum: Server Platforms
---

### Post by PeterK2003 on 2014-12-21
```
Dec 21 20:10:01 King-Arthur postfix/pickup[4184]: 8C115966DA: uid=33 from=<www-data>
Dec 21 20:10:01 King-Arthur postfix/cleanup[4306]: 8C115966DA: message-id=<20141222011001.8C115966DA@King-Arthur.xxx.name>
Dec 21 20:10:01 King-Arthur postfix/qmgr[4185]: 8C115966DA: from=<www-data@xxx.name>, size=678, nrcpt=1 (queue active)
Dec 21 20:10:01 King-Arthur postfix/local[4308]: 8C115966DA: to=<peter@xxx.name>, relay=local, delay=0.03, delays=0.01/0/0/0.02, dsn=2.0.0, status=sent (delivered to command: procmail -a "$EXTENSION")
Dec 21 20:10:01 King-Arthur postfix/qmgr[4185]: 8C115966DA: removed

```


Not sure what is going on but it looks like it is trying to relay the mail to localhost?

In main.cf I have the relay set but it doesn't seem to be using it.

relayhost = relay.xxx.name

What am I missing?

Thanks,
Peter

---

### Post by TheFu on 2014-12-22
Who runs the relay?  Many ISPs require SASL authentication, so that would need to be setup.

 /etc/postfix/main.cf:
```
   
        smtp_sasl_auth_enable = yes
        relayhost = [mail.isp.example]
        # Alternative form:
        # relayhost = [mail.isp.example]:submission
        smtp_sasl_password_maps = hash:/etc/postfix/sasl_passwd

```
from [http://www.postfix.org/SOHO_README.html](http://www.postfix.org/SOHO_README.html)

---

### Post by PeterK2003 on 2014-12-22
I run the relay.  It requires no auth.  It accepts mail from any host on the subnet.

---

### Post by TheFu on 2014-12-22
Ok - try using the ip address to the relayhost, not the hostname.  I don't know why, but this makes a difference on my systems.  It wasn't always this way, but something happened about 2 yrs ago.  Yes, each satellite knows how to ping the relay by hostname, but it just doesn't work for email.

---

### Post by PeterK2003 on 2014-12-22
changed it to the IP.  Still saying "relay=local" which seems wrong to me.

---

### Post by TheFu on 2014-12-22
> **PeterK2003 said:**
> changed it to the IP.  Still saying "relay=local" which seems wrong to me.

Where is that message?
Did you reload postfix? We all forget that part. ;)

My main.cf file (hadar is the satellite, .43 is the main email server):
```
$ postconf -n
alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
config_directory = /etc/postfix
inet_interfaces = loopback-only
mailbox_size_limit = 0
mydestination = hadar.lan, hadar, localhost.localdomain, localhost
myhostname = hadar
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
myorigin = /etc/mailname
readme_directory = no
recipient_delimiter = +
relayhost = 172.22.22.43
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_tls_cert_file = /etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file = /etc/ssl/private/ssl-cert-snakeoil.key
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtpd_use_tls = yes

```

Also have /etc/aliases setup to forward ll local email to my userid, root, and any service accounts ... newaliases.

---

### Post by PeterK2003 on 2014-12-22
I am seeing it in the syslog.  My first post has the whole series of log entries.

yeah i started and stopped it.

My config looks almost the same.  Noticeably different is this line "mailbox_command"

What should i change in the alias file?  I don't think I touched that.


```

peterk2003@King-Arthur:~$ postconf -n
alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
config_directory = /etc/postfix
inet_interfaces = loopback-only
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
mydestination = xxx.name, King-Arthur, localhost.localdomain, localhost
myhostname = King-Arthur.xxx.name
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
myorigin = /etc/mailname
readme_directory = no
recipient_delimiter = +
relayhost = 192.168.1.224
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_relay_restrictions = permit_mynetworks permit_sasl_authenticated defer_unauth_destination
smtpd_tls_cert_file = /etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file = /etc/ssl/private/ssl-cert-snakeoil.key
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtpd_use_tls = yes

```

---

### Post by TheFu on 2014-12-22
Don't mix upper/lowercase in hostnames. Sometimes UNIX scripts are lazy and will break with mixed case stuff. All it takes is 1 bad script in the chain and that will break things.  I've never used a dash either, but that should be valid.

Does /etc/mailname have something correct? Mine is hadar.lan ... btw, I have about 30 satellite machines all setup to forward their email to the main server - they are all setup in this way using ansible.

Don't worry about the aliases. That is only needed if you want local daemons sending email to "root" to get forwarded to the main mail server [email]root@mail.domain.com[/email]

Just saw that you are trying to procmail - why? If it isn't working - I'd fix/remove it.  Should that run on the main email server, not any satellite?  I dunno.

---

### Post by PeterK2003 on 2014-12-22
removed the upper case.

mailname has xxx.name

i commented out the mailbox command.  I didn't put in in there.  I also uninstalled procmail not sure why it was installed.

This caused the log to change slightly but same results.

```
Dec 22 10:03:01 King-Arthur postfix/local[17941]: 6D815966E2: to=<peter@xxx.name>, relay=local, delay=0.01, delays=0.01/0/0/0.01, dsn=2.0.0, status=sent (delivered to mailbox)

```

---

### Post by TheFu on 2014-12-22
Whoa!  if xxx.name is the local email server and you are trying to send email to [email]peter@xxx.name[/email] exactly what did you think should happen?  It is working like it should.

 ```
mydestination = xxx.name, King-Arthur, localhost.localdomain, localhost 
```
should be
 ```
mydestination = King-Arthur.xxx.name, King-Arthur, localhost.localdomain, localhost
```
assuming the real email server is for xxx.name.

This is the problem.

---

### Post by PeterK2003 on 2014-12-22
I DON'T KNOW I DIDN'T EVEN KNOW THE MAILNAME FILE EXISTED UNTIL 2 MINS AGO!!!!

haha

What should be in that file?

---

### Post by PeterK2003 on 2014-12-22
the real server is relay.xxx.name but...

OMG it worked!  Thank you so much!

---

### Post by TheFu on 2014-12-22
> **peterk2003 said:**
> the real server is relay.xxx.name but...

Omg it worked!  Thank you so much!

solved?

---

### Post by PeterK2003 on 2014-12-22
yep thanks.

---

### Post by TheFu on 2014-12-22
Please **mark the threat as solved** so other people don't waste time visiting unless they have the same issue.

---

### Post by PeterK2003 on 2014-12-22
maybe one more question....now it is trying to forward mail to [email]root@xxx.name[/email] which I don't want to happen...how do i stop this?

---

### Post by TheFu on 2014-12-23
> **PeterK2003 said:**
> maybe one more question....now it is trying to forward mail to [email]root@xxx.name[/email] which I don't want to happen...how do i stop this?

Any email addressed to "xxx.name" will be relayed. THAT is the point. If you don't want that, then disable the relay OR change the TO address so it stays local.  I want all root email from each different system to be sent to a central mailbox so someone will actually see it.  Nothing is worse than having a server crash because /var is full from stupid root emails that nobody saw.

---

