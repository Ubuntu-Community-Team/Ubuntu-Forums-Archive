---
title: "sasauthd error, using SMTP RelayHost, do I need sasauthd?"
date: 2009-03-15
forum: Server Platforms
---

### Post by volkswagner on 2009-03-15
I know I should leave well enough alone.

I have been searching log entries from auth.log.

```
Mar 15 16:30:58 atom postfix/smtpd[10177]: sql_select option missing
Mar 15 16:30:58 atom postfix/smtpd[10177]: auxpropfunc error no mechanism available 
Mar 15 16:30:58 atom postfix/smtpd[10177]: _sasl_plugin_load failed on sasl_auxprop_plug_init for plugin: sql 
```

While searching the above I find solutions using "/etc/postfix/sasl/smtp.conf", which I have no such file.  I am using Postfix/courier/squirrelmail using imap, virtual domains, all while using my ISP's smtp server.

So, do I just stop the log entries by turning off logging for smtp_tls inside main.cf?  Do I need

```
smtpd_sasl_auth_enable = yes

```  
if I am using my ISP's smtp-server?

Should I leave well enough alone (ignore the log entries)?  My mail server is working fine.  I followed the [flurdy]("http://flurdy.com/docs/postfix/") how-to.

---

### Post by askreet on 2009-03-17
If it all works, I wouldn't worry about it.  Looks like some sasl plugin is failing to load for one reason or another...

"If it ain't broke, don't fix it."

:)

---

### Post by volkswagner on 2009-04-16
Well, I was wrong.  All is not well.  I can't connect to mail server from outside of my LAN. Squirrel mail also fails to send outside of my LAN.

I can receive mail on the road, but I can't send.

Nothing in mail.err.

From mail.info:
```
Apr 16 07:11:44 atom postfix/smtpd[32302]: connect from unknown[166.209.93.45]
Apr 16 07:11:45 atom postfix/smtpd[32302]: warning: SASL authentication failure: cannot connect to saslauthd server: No such file or directory
Apr 16 07:11:45 atom postfix/smtpd[32302]: warning: unknown[166.209.93.45]: SASL LOGIN authentication failed: generic failure
Apr 16 07:11:47 atom postfix/smtpd[32302]: NOQUEUE: reject: RCPT from unknown[166.209.93.45]: 554 5.7.1 <name@friendsmail.com>: Relay access denied; from=<eric@volkswagner.com> to=<name@friendsmail.com> proto=ESMTP helo=<[166.209.93.45]>
Apr 16 07:11:47 atom postfix/smtpd[32302]: disconnect from unknown[166.209.93.45]

```

The above occurred while trying to send mail from my phone.

smtpd.conf seems to be pretty bare.
 ```
cat /etc/postfix/sasl/smtpd.conf
pwcheck_method: saslauthd
mech_list: plain login
```

Googling my errors yielded [this]("http://www.howtoforge.com/forums/showthread.php?p=43183") but I don't have /var/run/saslauthd/mux, nor do I have the setting listed in smtpd.conf. 

> and I had to enable chroot in the /etc/postfix/master.cf file

As you can see mine is also not chrooted.  I may be onto something but, I don't know how to go about the repair.

Thanks in advance.

---

### Post by volkswagner on 2009-04-19
Anyone?

Can anyone point me where I should look for information?

Do you think the error and the ability to send mail remotely are related?

---

### Post by volkswagner on 2009-04-22
where is all the love?  

Can anyone advise why so many of my threads get no response?

---

### Post by volkswagner on 2009-04-25
Maybe I am not asking the right question.

I may have multiple problems.  An issue with my cell phone may be compounding my symptoms.  The issues I mentioned earlier may not be true.

Let me ask this:

I am using my isp's smtp-server to send all mail.  Is it possible to use an email client when I am away from home to send mail?  I can receive mail no problem.  I don't want to rely on Squirrel mail since it is web based.  It becomes inconvenient when trying to reply to mail or responding/sending mail from other websites, which launch my email client automatically.

So is the following portion of main.cf what I should be looking into editing?  Is the saslauth actually the issue?

```
mynetworks = 127.0.0.0/8
``` 

or

```
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
```

---

### Post by volkswagner on 2009-07-01
Hmn,

A whole thread of me talking to myself.

As always I could not leave well enough alone.  Actually things are not well enough.  I am trying to solve a second issue which is not related.  I know it is not related as I have fixed the errors above.

From the following thread I have adapted for Ubuntu 8.04, as file locations are slightly different.

[http://ubuntuforums.org/showthread.php?t=1075599](http://ubuntuforums.org/showthread.php?t=1075599)

> Hi,

Think I have resolved the problem with postfix/smtpd.conf

pwcheck_method: saslauthd auxprop
mech_list: plain login
allow_plaintext: true
auxprop_plugin: mysql
sql_hostnames: localhost
sql_user: some_dbase
sql_passwd: password
sql_database: some_dbase
sql_select: select password from users where email = '%u'

logcheck gives now:
postfix/smtpd: sql auxprop plugin using mysql engine

I hope falco can confirm...

I have adjusted the above with my pertinent info.  The file is actually 
```
/etc/postfix/sasl/smtpd.conf
```

I hope this can help someone else, as I believe many have followed the same [how to]("http://flurdy.com/docs/postfix/").

---

### Post by Dr Small on 2009-07-02
Here, check out this thread:
[http://ubuntuforums.org/showthread.php?t=990582](http://ubuntuforums.org/showthread.php?t=990582)

---

### Post by volkswagner on 2009-07-02
thanks Dr. small.  I was reading your thread last night.  I am not sure if your method needs to be modified for my setup.  I was trying to get Mysql to provide the password table.

---

### Post by volkswagner on 2009-07-03
I tried to follow Dr. Small's HowTo.  I have run into a couple snags.

When I enable 
```
smtpd_tls_auth_only = yes
```

I don't get and results for the two following fields during "telnet localhost 25".
```
250-AUTH PLAIN LOGIN
250-AUTH=PLAIN LOGIN
```

If I choose **NO** for "smtpd_tls_auth_only" I do get results for the above fields.

Even after changing smtpd.conf, I still get the following during "telnet localhost 25":

```
250-AUTH DIGEST-MD5 NTLM CRAM-MD5 LOGIN PLAIN
250-AUTH=DIGEST-MD5 NTLM CRAM-MD5 LOGIN PLAIN
```

Any help is appreciated.  I am not sure if this all up to Postfix at the moment, or if Courier IMAP comes into play.  I have attached pertinent files and here is a little more info.

```
ls -alt /etc/postfix/ssl
total 28
-rw-r--r-- 1 root root 1277 2009-07-03 09:57 cacert.pem
-rw-r--r-- 1 root root  951 2009-07-03 09:57 cakey.pem
drwxr-xr-x 2 root root 4096 2009-07-03 09:57 .
-rw-r--r-- 1 root root  887 2009-07-03 09:56 smtpd.key
-rw-r--r-- 1 root root  940 2009-07-03 09:55 smtpd.crt
-rw-r--r-- 1 root root  773 2009-07-03 09:54 smtpd.csr
drwxr-xr-x 4 root root 4096 2009-07-01 22:31 ..

```

```
ls -alt /var/spool/postfix/var/run/saslauthd
total 980
drwxr-xr-x 2 root sasl   4096 2009-07-03 10:56 .
-rw------- 1 root root      0 2009-07-03 10:56 cache.flock
-rw------- 1 root root 986112 2009-07-03 10:56 cache.mmap
srwxrwxrwx 1 root root      0 2009-07-03 10:56 mux
-rw------- 1 root root      0 2009-07-03 10:56 mux.accept
-rw------- 1 root root      5 2009-07-03 10:56 saslauthd.pid
drwxr-xr-x 3 root root   4096 2008-12-21 10:48 ..

```

Every time I restart saslauthd the permissions are reset to look like above.  Is this the proper permissions?

The following command from the how to I though would change the permissions, but It just sets the directory not the contents.

```
sudo dpkg-statoverride --force --update --add root sasl 755 /var/spool/postfix/var/run/saslauthd
```

Although this is probably not the issue, I am curious.

I just can't seem to get Mysql and SASL to play.

The email client complains of bad response and prompts for new password.  I don't see any error in mysql.log.  Actually It appears not to be reaching Mysql, hence the error in auth.log.

After several attempts at self signed keys, I still get an untrusted warning and also, bad signature message with evolution and also my Nokia.

Would Citadel take care of (reduce) these headaches, and how easy would it be to implement after having a semi functioning system via the Flurdy how to?

---

