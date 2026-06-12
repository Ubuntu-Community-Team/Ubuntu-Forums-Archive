---
title: "Postfix/SASL problem"
date: 2006-11-11
forum: Server Platforms
---

### Post by Wallace on 2006-11-11
I'm trying to get a mail server up and running with 6.10 Edgy Eft. I carefully worked my way through flurdy's HOWTO ([here](http://www.ubuntuforums.org/showthread.php?t=185913) and [here](http://flurdy.com/docs/postfix/)) and it seems almost everything is working fine.

I've got Postfix and Courier IMAP working. Courier authenticates against MySQL. I think they both work work with TLS and SSL too.

The only thing that doesn't work is authentication with Postfix. It just seems that SASL isn't working right and doesn't even touch the MySQL database. The errors in auth.log and mail.log looks like it keeps falling back on using sasldb2 when I want it to use auxprop and SQL.

Can anyone help me fix this?

---

### Post by Wallace on 2006-11-12
I've done some more digging.

Before I installed 6.10 on the PC, I tested things out using VMWare on my Windows PC. But I tested my setup using 6.06, then decided to use 6.10 for the real thing. I used the same Howto on both setups. I even copied some of the config files over.

On 6.06 with Postfix 2.2.10, everything works, and the mech_list setting in smtpd.conf controls the AUTH response from Postfix.

But on 6.10 with Postfix 2.3.3, Postfix just seems to ignore smtpd.conf completely. It doesn't matter what mech_list I enter, it always responds with "250-AUTH LOGIN PLAIN NTLM DIGEST-MD5 CRAM-MD5"

Does anyone know what I have to do to get this working with 6.10 and Postfix 2.3.3?

I've been pulling my hair out for a couple of days over this :(

---

### Post by Wallace on 2006-11-12
Isn't it often the way that explaining something gives you an idea...

I *think* I might have fixed it. And in case anyone else has the same issues, here's what I had to do.

In flurdy's Howto, it says you need this line in main.cf:

```
smtpd_sasl_path = /etc/postfix/sasl:/usr/lib/sasl2
```

That seems to mess everything up on Postfix 2.3.3.

Removing the line entirely or replacing it with the following (which is the default in 2.3.3 I think) got SASL working.

```
smtpd_sasl_path = smtpd
```

So now I've got Postfix working with SASL and TLS, and it's still chrooted :)


On to the next task...

---

### Post by hecchan on 2006-11-30
thanks for that wallace,

still one thing, i can use postfix and courier-imap with tls cram-md5 from kmail.
But from evolution the tls negotiation with imap fail
here is the output of mail.log

Nov 30 22:24:51 cian imapd: couriertls: connect: error:1408F10B:SSL routines:SSL3_GET_RECORD:wrong version number

are you using evolution?

---

### Post by lgarfiel on 2006-12-01
Wallace, I'm having the exact same issue you were.  Unfortunately, that fix doesn't work. :-(  I've tried that, and setting that parameter to some other value, and moving the file to various other places and updating that value.  It's just not picking up.  

Are you sure you didn't change anything else?  I'm stumped.

---

### Post by chrisfay on 2006-12-02
You definately need this in your main.cf file regardless:
```
smtpd_sasl_path = smtpd
```

Couple things to check:

What auth_mech are you using in smtpd.conf? As far as I'm aware, you can't use MD5 with sasl's mysql module. If you are using MD5, drop it to 'plain'.

Double check your query in your smtpd.conf file. Mine was wrong for a while and had me stumped until I found that was the cause for the failed auth. 

What do you have set for:
```
sql_hostnames: 127.0.0.1
```

If you have it set to 'localhost', try changing it to 127.0.0.1.

Here is my working /etc/postfix/sasl/smtpd.conf file as a reference if it would help:

```
########## smtpd.conf - SASL with mysql plugin - ##############
pwcheck_method: auxprop
auxprop_plugin: sql
mech_list: plain login
sql_engine: mysql
sql_hostnames: 127.0.0.1
sql_user: mysqluser
sql_passwd: mysqlpassword
sql_database: email_admin
sql_select: select clearpasswd from users where userid='%u@%r' and active = 'y'
```

Also, in your main.cf file, do you have the smtp config options enabled?

```
####### SMTPD sasl for authenticating clients for relaying mail through my server (without manually adding ips) ######
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
smtpd_sasl_local_domain = $myhostname
smtpd_sasl_application_name = smtpd
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = 
permit_sasl_authenticated, 
permit_mynetworks, 
reject_unauth_destination
```

Just some ideas.....

---

### Post by Wallace on 2006-12-02
> **lgarfiel said:**
> Are you sure you didn't change anything else?  I'm stumped.
I'm sure that was the only significant change I made to the HOWTO. The only other difference I can remember is one of the packages has changed (I had to install courier-authlib-mysql instead of courier-authmysql).

I spent ages at one point trying to get Postfix to work only to find I'd made a spelling mistake in main.cf.


To chrisfay, I'm using auxprop/sql and MD5 seems to be working fine. I think its saslauthd that doesn't support CRAM-MD5 and DIGEST-MD5.


To hecchan, I've never used evolution sorry. I'm only using Thunderbird (on Windows).

---

