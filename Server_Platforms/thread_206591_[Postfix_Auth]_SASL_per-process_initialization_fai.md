---
title: "[Postfix Auth] SASL per-process initialization failed"
date: 2006-06-30
forum: Server Platforms
---

### Post by Kurdt on 2006-06-30
Hi all guys :)

Well, i am in the process of replacing a mail server and i followed this [excellent guide]("http://www.ubuntuforums.org/showthread.php?t=185913") by flurdy.
Everything works like a charm =D>  but when i enable SASL auth i get this error on /var/log/mail.log:

> Jun 30 10:44:19 pc009 postfix/smtpd[9829]: fatal: SASL per-process initialization failed
Jun 30 10:44:20 pc009 postfix/master[4987]: warning: process /usr/lib/postfix/smtpd pid 9829 exit status 1
Jun 30 10:44:20 pc009 postfix/master[4987]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling


Postfix main.cf sasl section:
> 
smtpd_sasl_auth_enable = yes
broken_sasl_auth_clients = yes
smtpd_sasl_path = /etc/postfix/sasl:/usr/lib/sasl2
smtpd_sasl_security_options = noanonymous
smtpd_sasl_local_domain =

If i disable sasl in main.cf like this

> #smtpd_sasl_auth_enable = yes

SMTP works perfectly, but i really need smtp with authentication.
I followed the guide step by step, i am using Ubuntu 6.06 LTS Dapper Drake and the last version of all components of the guide.

Maybe you can tell me how can i get more detailed log information for SASL, or someone did this before.

**Many thanks in advance.**

---

### Post by Kurdt on 2006-07-01
Anyone? Please ?? :(

---

### Post by MJN on 2006-07-02
Best ask Flurdy as (s)he's the author!
 
That's always the problem with blindly following HowTo's (hey, we're all guilty of it from time to time so not having a pop at you) because you learn very very little out of the whole thing. Sure, you will hopefully end up with exactly what you wanted (assuming your requirements exactly align with those of the author) but you learn diddly-squat with the consequence that you haven't got a chance in hell of customising/fixing it later.
 
Even worse, from a quick glance at that HowTo it looks to be tackling over 10 different fundamental areas, each of which could be an entire series of HowTo's by themselves.
 
Sorry that this is of no use, however it may indicate why responses are thin on the ground - noone is likely to want to unravel the rats nest of someone else's HowTo to see where you've slipped up.
 
Mathew :)
 
P.S. Just noticed your signature... you ought to know better! Blind HowTo following is akin to debugging someone else's sloppy code!

---

### Post by Kurdt on 2006-07-03
:oops: i fixed it, it was a typo in sasl's smtpd.conf file. Sorry.

---

### Post by ChantCd_com on 2006-10-24
What was the typo? I'm having the same problem.

---

### Post by Kurdt on 2006-10-27
I don't really remember now, but this is my smtpd.conf file:

> pwcheck_methd: auxprop
auxprop_plugin: sql
mech_list: plain login cram-md5 digest-md5
sql_engine: mysql
sql_hostnames: 127.0.0.1
sql_user: mail
sql_passwd: ****
sql_database: maildb
sql_select: select clear from users where id='%u@%r' and enabled = 1
log_level: 7


Let me now if it works for you.

---

### Post by Blairboy on 2006-10-27
Ok, this is what I get from syslog.

localhost postfix/smtpd[24021]: warning: SASL: Connect to /etc/postfix/sasl:/usr/lib/sasl2 failed: No such file or directory
localhost postfix/smtpd[24021]: fatal: no SASL authentication mechanisms

I'm very confused as to why it's saying that those directories don't exist.  I also tried making it just /etc/postfix/sasl or just /usr/lib/sasl2 in the config file, and it still said that those directories didn't exist.  Anybody seeing something I'm not?



here's my /etc/postfix/main.cf

smtpd_sasl_auth_enable = yes
broken_sasl_auth_clients = yes
smtpd_sasl_type = dovecot
smtpd_sasl_path = /etc/postfix/sasl:/usr/lib/sasl2
smtpd_sasl_security_options = noanonymous
smtpd_sasl_local_domain = 

smtpd_use_tls = yes
smtpd_tls_cert_file = /etc/postfix/postfix.cer
smtpd_tls_key_file = /etc/postfix/postfix.key 
smtpd_data_restrictions = reject_unauth_pipelining


here's my /etc/postfix/sasl/smtpd.conf

pwcheck_method: auxprop
auxprop_plugin: sql
mech_list: plain login cram-md5 digest-md5
sql_engine: mysql
sql_hostnames: 127.0.0.1
sql_user: mail
sql_passwd: pass
sql_database: maildb
sql_select: select password from users where name='%u' and enabled = 1

---

### Post by Fíona on 2006-10-29
I'm having trouble getting this to work as well.
Followed the howto: ([https://help.ubuntu.com/community/Postfixhttps://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfixhttps://help.ubuntu.com/community/Postfix))
openssl genrsa -des3 -rand /etc/hosts -out smtpd.key 1024
Then I get smtpd.key: permission denied. 4267 error....system library:fopen: permission denied:bssfile.c:352:fopen 'smtpd.key','w'
4267:error:20074002:BIO rouotines:File_ctrl:system lib:bss file.c:354.

I don't understand this at all.

Can anyone point me in the right direction?

Thanks

---

### Post by MJN on 2006-10-29
I'm not familiar with the HowTo, but do you need to run the opensll command with **sudo**?

---

### Post by Fíona on 2006-10-29
> **MJN said:**
> I'm not familiar with the HowTo, but do you need to run the opensll command with **sudo**?

Yes, and I forgot to do that! Dumb!
Thanks

---

### Post by Blairboy on 2006-11-04
So does anyone have any ideas on my problem?

---

### Post by Kurdt on 2006-11-04
> **Blairboy said:**
> So does anyone have any ideas on my problem?

Maybe you should check all steps from the guide again.

Which user is running postfix ?

---

### Post by dejf.org on 2008-01-28
> **ChantCd_com said:**
> What was the typo? I'm having the same problem.

It sasl's "parameter: value" instead of "parametr = value" that is used in main.cf
I stuck at this for some time today :)

---

### Post by dejf.org on 2008-01-28
> **Blairboy said:**
> So does anyone have any ideas on my problem?

Maybe there is a part of postfix/sasl that is not installed, but required

---

