---
title: "Postfix - a couple questions"
date: 2007-08-16
forum: Server Platforms
---

### Post by KevinM1 on 2007-08-16
Unfortunately, I didn't see until now that there was a specific/special package of Postfix that could be installed that had authentication pre-installed (described here: [https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix)).  Can I upgrade without having to uninstall/reinstall my current version?

Regardless, I have my current Postfix working, but I'd like to change the name that's given for where the e-mail is from.  My e-mails will be sent primarily via PHP scripts.  As such, right now the sender name is [email]www-data@mydomain.com[/email].  Is there a way for me to change the www-data part?

---

### Post by HermanAB on 2007-08-16
Yes, and yes - however, you have to go and read up yourself at postfix.org.  The documentation is search-able - you'll have the answer in no time.

Cheers,

Herman

---

### Post by KevinM1 on 2007-08-17
> **HermanAB said:**
> Yes, and yes - however, you have to go and read up yourself at postfix.org.  The documentation is search-able - you'll have the answer in no time.

Cheers,

Herman

I'm reading the documentation, but I can't make heads or tails about what I should be looking for.  Specifically, I believe my username question falls under address rewriting, but I'm not sure what flavor to use.  I've tried to use smtp generic mapping, but that didn't work.  On the surfance, local aliasing looks promising on the surface, but documentation makes it seem like it's for incoming mail.  Since I only want to use my server for outgoing mail, that doesn't seem like the direction to go in.

Are there any Postfix forums I could ask these questions on?  I've searched Google for one, but no luck.

---

### Post by KevinM1 on 2007-08-21
New question: I'd like to change my SMTP port to 587, as is suggested by the documentation here ([https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix)), but I can't find the relevant line in my master.cf file.  There's nothing that jumps out at me as having to do with that port.  Anyone mind supplying the line in question?

---

### Post by Mr. C. on 2007-08-21
A generics table entry will help:

```
    /etc/postfix/main.cf:
        smtp_generic_maps = hash:/etc/postfix/generic

    /etc/postfix/generic:
        www-data@*mydomain.com*        *desiredname@desireddomain.com*
```

The email address on the right is the email address that will be seen in the From header and MAIL FROM envelope. 

The 587 port is the **submission** port.  

```
grep submission /etc/postfix/master.cf
grep submission /etc/services
```

I'm not sure about your package upgrade question.

MrC

---

### Post by KevinM1 on 2007-08-22
> **Mr. C. said:**
> A generics table entry will help:

```
    /etc/postfix/main.cf:
        smtp_generic_maps = hash:/etc/postfix/generic

    /etc/postfix/generic:
        www-data@*mydomain.com*        *desiredname@desireddomain.com*
```

The email address on the right is the email address that will be seen in the From header and MAIL FROM envelope.

I just tried this, but it's not working.  In fact, no mail is being sent at all now.  I added the smtp_generic_maps line to the end of main.cf (obviously I'm not using mydomain.com as my actual domain):

```

# See /usr/share/postfix/main.cf.dist for a commented, more complete version


# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
#myorigin = /etc/mailname

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

# TLS parameters
smtpd_tls_cert_file = /etc/postfix/ssl/smtpd.crt
smtpd_tls_key_file = /etc/postfix/ssl/smtpd.key
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = mydomain.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = mydomain.com,localhost.mydomain.com,localhost
relayhost = 
mynetworks = 127.0.0.0/8
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
smtpd_sasl_local_domain = 
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions =  permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
smtpd_tls_auth_only = no
smtp_use_tls = yes
smtp_tls_note_starttls_offer = yes
smtpd_tls_CAfile = /etc/postfix/ssl/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom
inet_protocols = all
**smtp_generic_maps = hash:/etc/postfix/generic**
```

And my generic file has just the following line:

```

www-data@mydomain.com		webmaster@mydomain.com

```

> 
The 587 port is the **submission** port.  

```
grep submission /etc/postfix/master.cf
grep submission /etc/services
```

So, if I'm reading you correctly, I'm supposed to uncomment the line in master.cf found in the first command?

> I'm not sure about your package upgrade question.

MrC

That's okay.  Thanks for the help! :D

---

### Post by Mr. C. on 2007-08-22
Show output from

```
postconf -n
```

and contents of /etc/mailname

Yes, you uncomment the submission port.

MrC

---

### Post by KevinM1 on 2007-08-22
> **Mr. C. said:**
> Show output from

```
postconf -n
```

and contents of /etc/mailname

Output from postconf -n:
```

alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
broken_sasl_auth_clients = yes
config_directory = /etc/postfix
inet_interfaces = all
inet_protocols = all
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
mydestination = rextrader.com,localhost.rextrader.com,localhost
myhostname = rextrader.com
mynetworks = 127.0.0.0/8
myorigin = /etc/mailname
recipient_delimiter = +
relayhost = 
smtp_generic_maps = hash:/etc/postfix/generic
smtp_tls_note_starttls_offer = yes
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache
smtp_use_tls = yes
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
smtpd_sasl_auth_enable = yes
smtpd_sasl_local_domain = 
smtpd_sasl_security_options = noanonymous
smtpd_tls_CAfile = /etc/postfix/ssl/cacert.pem
smtpd_tls_auth_only = no
smtpd_tls_cert_file = /etc/postfix/ssl/smtpd.crt
smtpd_tls_key_file = /etc/postfix/ssl/smtpd.key
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtpd_tls_session_cache_timeout = 3600s
smtpd_use_tls = yes
tls_random_source = dev:/dev/urandom
```

Contents of /etc/mailname:

```

rextrader.com

```

> Yes, you uncomment the submission port.

MrC

Cool, thanks! :)

---

### Post by Mr. C. on 2007-08-22
Hmmm, no generic's table in your postconf output.  I understand it was not working for you, but we can't diagnose what went wrong without actually seeing postfix working with the configuration, and the log entries showing a complete mail transaction.

Your myhostname parameter really should be a fully qualified hostname, not a domain name.

MrC

---

### Post by KevinM1 on 2007-08-23
> **Mr. C. said:**
> Hmmm, no generic's table in your postconf output.  I understand it was not working for you, but we can't diagnose what went wrong without actually seeing postfix working with the configuration, and the log entries showing a complete mail transaction.

Your myhostname parameter really should be a fully qualified hostname, not a domain name.

MrC

Please bear with me as I'm a total newbie who has no real server administrator experience.

1. Where/how would I obtain the log entries?

2. What's the difference between a fully qualified hostname and a domain name?

EDIT: Here's a log with what I just tried.  I dunno if it'll be helpful:
```

Aug 23 11:57:15 rex-desktop postfix/master[6248]: daemon started -- version 2.3.8, configuration /etc/postfix
Aug 23 11:57:15 rex-desktop postfix/qmgr[6250]: 97205C3C164: from=<www-data@rextrader.com>, size=404, nrcpt=1 (queue active)
Aug 23 11:57:15 rex-desktop postfix/smtp[6252]: fatal: open database /etc/postfix/generic.db: No such file or directory
Aug 23 11:57:16 rex-desktop postfix/master[6248]: warning: process /usr/lib/postfix/smtp pid 6252 exit status 1
Aug 23 11:57:16 rex-desktop postfix/master[6248]: warning: /usr/lib/postfix/smtp: bad command startup -- throttling
Aug 23 11:57:28 rex-desktop postfix/pickup[6249]: 23EB7C3C166: uid=33 from=<www-data>
Aug 23 11:57:28 rex-desktop postfix/cleanup[6262]: 23EB7C3C166: message-id=<20070823155728.23EB7C3C166@rex-desktop.localdomain>
Aug 23 11:57:28 rex-desktop postfix/qmgr[6250]: 23EB7C3C166: from=<www-data@rextrader.com>, size=424, nrcpt=1 (queue active)
Aug 23 11:57:41 rex-desktop postfix/postfix-script: stopping the Postfix mail system
Aug 23 11:57:41 rex-desktop postfix/master[6248]: terminating on signal 15
Aug 23 11:58:29 rex-desktop postfix/postfix-script: starting the Postfix mail system
Aug 23 11:58:29 rex-desktop postfix/master[6368]: daemon started -- version 2.3.8, configuration /etc/postfix
Aug 23 11:58:29 rex-desktop postfix/qmgr[6370]: 23EB7C3C166: from=<www-data@rextrader.com>, size=424, nrcpt=1 (queue active)
Aug 23 11:58:29 rex-desktop postfix/qmgr[6370]: 97205C3C164: from=<www-data@rextrader.com>, size=404, nrcpt=1 (queue active)
Aug 23 11:58:29 rex-desktop postfix/smtp[6373]: fatal: open database /etc/postfix/generic.db: No such file or directory
Aug 23 11:58:30 rex-desktop postfix/master[6368]: warning: process /usr/lib/postfix/smtp pid 6373 exit status 1
Aug 23 11:58:30 rex-desktop postfix/master[6368]: warning: /usr/lib/postfix/smtp: bad command startup -- throttling
Aug 23 11:58:33 rex-desktop postfix/postfix-script: refreshing the Postfix mail system
Aug 23 11:58:33 rex-desktop postfix/master[6368]: reload configuration /etc/postfix
Aug 23 11:58:33 rex-desktop postfix/qmgr[6381]: 23EB7C3C166: from=<www-data@rextrader.com>, size=424, nrcpt=1 (queue active)
Aug 23 11:58:33 rex-desktop postfix/qmgr[6381]: 97205C3C164: from=<www-data@rextrader.com>, size=404, nrcpt=1 (queue active)
Aug 23 11:58:40 rex-desktop postfix/pickup[6382]: 75033C3C167: uid=33 from=<www-data>
Aug 23 11:58:40 rex-desktop postfix/cleanup[6391]: 75033C3C167: message-id=<20070823155840.75033C3C167@rex-desktop.localdomain>
Aug 23 11:58:40 rex-desktop postfix/qmgr[6381]: 75033C3C167: from=<www-data@rextrader.com>, size=424, nrcpt=1 (queue active)
Aug 23 11:58:51 rex-desktop postfix/postfix-script: stopping the Postfix mail system
Aug 23 11:58:51 rex-desktop postfix/master[6368]: terminating on signal 15
```

---

### Post by southernman on 2007-08-23
One newcomer to another:

I think the logs would be in /var/log/mail but thats a SWAG (scientific wild a** guess).

I think the FQH should be something like mail.rextrader.com replacing mail as you need it to be setup.

I did a Google to see and here is one specific site that looked informative:
[http://leafnode.sourceforge.net/doc_en/README-FQDN.html]("http://leafnode.sourceforge.net/doc_en/README-FQDN.html")

The search I ran is at:
[http://www.google.com/search?q=fully+qualified+hostname&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a]("http://www.google.com/search?q=fully+qualified+hostname&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a")

I don't intend to step on anyones toes or to misinform. That being said take my advice with a grain of salt. Though I hope it helps anyway

---

### Post by KevinM1 on 2007-08-23
> **southernman said:**
> One newcomer to another:

I think the logs would be in /var/log/mail but thats a SWAG (scientific wild a** guess).

Yeah, I just found them there myself when your message appeared.  I edited my last message with what the logs say.

> I think the FQH should be something like mail.rextrader.com replacing mail as you need it to be setup.

I did a Google to see and here is one specific site that looked informative:
[http://leafnode.sourceforge.net/doc_en/README-FQDN.html]("http://leafnode.sourceforge.net/doc_en/README-FQDN.html")

The search I ran is at:
[http://www.google.com/search?q=fully+qualified+hostname&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a]("http://www.google.com/search?q=fully+qualified+hostname&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a")

I don't intend to step on anyones toes or to misinform. That being said take my advice with a grain of salt. Though I hope it helps anyway

Thanks, I'll look through the links! :)

---

### Post by KevinM1 on 2007-08-23
Well, this is odd.  My boss is the one who installed the OS.  Apparently he chose 'rex-desktop' as the hostname upon installation, as that's the value that's in /ect/hostname.

---

### Post by southernman on 2007-08-23
> **KevinM1 said:**
> Well, this is odd.  My boss is the one who installed the OS.  Apparently he chose 'rex-desktop' as the hostname upon installation, as that's the value that's in /ect/hostname.
Easy enough to change by doing 

sudo nano /etc/hosts (edit as needed and save)
sudo nano /etc/hostname (same as above)

sudo /etc/init.d/networking restart

check if the changes took hold by doing

hostname
hostname -f

You may need to completely reboot the system if the returns from the last two commands aren't correct (eg shows the modified changes).

PS. I saw that in the logs you posted on page one (last post) and thought it strange too.

---

### Post by KevinM1 on 2007-08-23
> **southernman said:**
> Easy enough to change by doing 

sudo nano /etc/hosts (edit as needed and save)
sudo nano /etc/hostname (same as above)

sudo /etc/init.d/networking restart

check if the changes took hold by doing

hostname
hostname -f

You may need to completely reboot the system if the returns from the last two commands aren't correct (eg shows the modified changes).

PS. I saw that in the logs you posted on page one (last post) and thought it strange too.

What should I change the hostname to?  Can it be anything?  Or are there specific ones to look at?  Will it effect my Apache setup, which is currently working?

Before I do that, though, from what the logs say it appears the problem is stemming from the generic aliasing/mapping I'm trying to do.  I changed the name of the file from /etc/postfix/generic to /etc/postfix/generic.db, as the log errors kept saying that the generic.db file didn't exist.  Upon doing that, the error changed to (I've made the appropriate line bold):

```

Aug 23 12:18:08 rex-desktop postfix/postfix-script: starting the Postfix mail system
Aug 23 12:18:08 rex-desktop postfix/master[7147]: daemon started -- version 2.3.8, configuration /etc/postfix
Aug 23 12:18:08 rex-desktop postfix/qmgr[7149]: 23EB7C3C166: from=<www-data@rextrader.com>, size=424, nrcpt=1 (queue active)
Aug 23 12:18:08 rex-desktop postfix/qmgr[7149]: 75033C3C167: from=<www-data@rextrader.com>, size=424, nrcpt=1 (queue active)
Aug 23 12:18:08 rex-desktop postfix/qmgr[7149]: 97205C3C164: from=<www-data@rextrader.com>, size=404, nrcpt=1 (queue active)
Aug 23 12:18:08 rex-desktop postfix/qmgr[7149]: 0A3E7C3C168: from=<www-data@rextrader.com>, size=400, nrcpt=1 (queue active)
**Aug 23 12:18:08 rex-desktop postfix/smtp[7151]: fatal: open database /etc/postfix/generic.db: Invalid argument**
Aug 23 12:18:09 rex-desktop postfix/master[7147]: warning: process /usr/lib/postfix/smtp pid 7151 exit status 1
Aug 23 12:18:09 rex-desktop postfix/master[7147]: warning: /usr/lib/postfix/smtp: bad command startup -- throttling
Aug 23 12:18:15 rex-desktop postfix/pickup[7148]: 279F6C3C169: uid=33 from=<www-data>
Aug 23 12:18:15 rex-desktop postfix/cleanup[7161]: 279F6C3C169: message-id=<20070823161815.279F6C3C169@rex-desktop>
Aug 23 12:18:15 rex-desktop postfix/qmgr[7149]: 279F6C3C169: from=<www-data@rextrader.com>, size=400, nrcpt=1 (queue active)
Aug 23 12:18:37 rex-desktop postfix/postfix-script: refreshing the Postfix mail system
Aug 23 12:18:37 rex-desktop postfix/master[7147]: reload configuration /etc/postfix
Aug 23 12:18:37 rex-desktop postfix/qmgr[7177]: 23EB7C3C166: from=<www-data@rextrader.com>, size=424, nrcpt=1 (queue active)
Aug 23 12:18:38 rex-desktop postfix/qmgr[7177]: 279F6C3C169: from=<www-data@rextrader.com>, size=400, nrcpt=1 (queue active)
Aug 23 12:18:38 rex-desktop postfix/qmgr[7177]: 75033C3C167: from=<www-data@rextrader.com>, size=424, nrcpt=1 (queue active)
Aug 23 12:18:38 rex-desktop postfix/qmgr[7177]: 97205C3C164: from=<www-data@rextrader.com>, size=404, nrcpt=1 (queue active)
Aug 23 12:18:38 rex-desktop postfix/qmgr[7177]: 0A3E7C3C168: from=<www-data@rextrader.com>, size=400, nrcpt=1 (queue active)
Aug 23 12:18:43 rex-desktop postfix/pickup[7176]: AC062C3C16A: uid=33 from=<www-data>
Aug 23 12:18:43 rex-desktop postfix/cleanup[7184]: AC062C3C16A: message-id=<20070823161843.AC062C3C16A@rex-desktop>
Aug 23 12:18:43 rex-desktop postfix/qmgr[7177]: AC062C3C16A: from=<www-data@rextrader.com>, size=400, nrcpt=1 (queue active)
Aug 23 12:18:54 rex-desktop postfix/postfix-script: stopping the Postfix mail system
Aug 23 12:18:54 rex-desktop postfix/master[7147]: terminating on signal 15
```

My generic.db file is simply:
```

www-data@rextrader.com		webmaster@rextrader.com

```

So I'm a bit stumped as to why there would be an error there.

---

### Post by Mr. C. on 2007-08-23
Ok. I can see from:

> Aug 23 11:57:15 rex-desktop postfix/smtp[6252]: fatal: open database /etc/postfix/generic.db: No such file or directory

that you did not 
```

postmap /etc/postfix/generic
```

and do 

```
postfix reload

```

for immediate update.

after creating the table.  That is required whenever you change a database-style map in postfix.  Fix that, and try again.

A fully qualified host name is one that contains a hostname + domain name, as in mail.rextrader.com.  The name **mail** alone would not fully qualified.  While rextrader.com is a domain name, it isn't the name of any host - it is the domain name for all hosts that live in rextrader.com.  Change myhostname to rex-desktop.rextrader.com and add an appropriate entry in /etc/hosts for that as well.

MrC

---

### Post by KevinM1 on 2007-08-23
> **Mr. C. said:**
> Ok. I can see from:


that you did not 
```

postmap /etc/postfix/generic
```

and do 

```
postfix reload

```

for immediate update.

after creating the table.  That is required whenever you change a database-style map in postfix.  Fix that, and try again.

Ah, thanks.  It works, sorta.  I'm sending the test messages to my gmail account, so now the username appears as **www-data *<webmaster@rextrader.com>*** instead of **www-data *<www-data@rextrader.com>***...I'm not sure if this is a gmail issue, or if the sender name is still having issues.

> A fully qualified host name is one that contains a hostname + domain name, as in mail.rextrader.com.  The name **mail** alone would not fully qualified.  While rextrader.com is a domain name, it isn't the name of any host - it is the domain name for all hosts that live in rextrader.com.  Change myhostname to rex-desktop.rextrader.com and add an appropriate entry in /etc/hosts for that as well.

MrC

Will do, and thanks again! :)

EDIT: question about the hosts file.  I currently have:
```

127.0.0.1 localhost
127.0.1.1 rex-desktop

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

Should I just add:
```

127.0.0.1 (or) 127.0.1.1 rex-desktop.rextrader.com
```

---

### Post by Mr. C. on 2007-08-23
Postfix is not adding the bold (user name) portion:
[B]
www-data[/B]<webmaster@rextrader.com>

Your script is doing that.  Check your PHP scripts to see how the FROM header is being specified.

Use:

127.0.0.1 rex-desktop.rextrader.com

Now, just so you're clear, should email you send be later bounced by some remote site, they will bounce to webmaster.rextrader.com.  The remote site should be able to deliver mail to rextrader.com, so you a) should have and MX record for rex-trader.com, and b) have a reverse domain name (a PTR) record as well, or your mail server will get many rejects when you attempt to send email (many remote MTAs refuse to accept SMTP mail from incorrectly configured MTAs).

MrC

---

### Post by KevinM1 on 2007-08-23
> **Mr. C. said:**
> Postfix is not adding the bold (user name) portion:
[B]
www-data[/B]<webmaster@rextrader.com>

Your script is doing that.  Check your PHP scripts to see how the FROM header is being specified.

Use:

127.0.0.1 rex-desktop.rextrader.com

Great, thanks! :)

> Now, just so your clear, should email you send be later bounced by some remote site, they will bounce to webmaster.rextrader.com.  The remote site should be able to deliver mail to rextrader.com, so you a) should have and MX record for rex-trader.com, and b) have a reverse domain name (a PTR) record as well, or your mail server will get many rejects when you attempt to send email (many remote MTAs refuse to accept SMTP mail from incorrectly configured MTAs).

MrC

:confused:

Should I be able to do this through the company where our business partner purchased the domain name?  Or does this mean I'll have to dig through something like BIND and do it manually?

---

### Post by Mr. C. on 2007-08-23
Your question really is asking who must be authoritative for your zone rextrader.com.  The answer is, it doesn't matter.  As long as the appropriate records exist.  If you plan on receiving email at rextrader.com, you need to have the two basics I indicated earlier.  Your name service provider probably has a website where you can add the record.

I see there is no MX record,  but you do have an A record (assuming 65.175.139.109 maps to your mail server). 

```
$ host rextrader.com
rextrader.com has address 65.175.139.109
```

An A record alone is OK, but causes additional DNS lookups.  Add an MX record.

I can see that your registrar is register.com, but you may be using one of their numerous partners.

```
$ dig soa rextrader.com           

; <<>> DiG 9.4.1-P1 <<>> soa rextrader.com
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 61539
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 2, ADDITIONAL: 2

;; QUESTION SECTION:
;rextrader.com.                 IN      SOA

;; ANSWER SECTION:
rextrader.com.          14400   IN      SOA     dns11.register.com. root.register.com. 2006072715 28800 7200 604800 14400

;; AUTHORITY SECTION:
rextrader.com.          11917   IN      NS      dns11.register.com.
rextrader.com.          11917   IN      NS      dns12.register.com.

;; ADDITIONAL SECTION:
dns12.register.com.     81764   IN      A       216.21.226.76
dns11.register.com.     81764   IN      A       216.21.234.76

;; Query time: 108 msec
;; SERVER: 192.168.3.200#53(192.168.3.200)
;; WHEN: Thu Aug 23 10:19:34 2007
;; MSG SIZE  rcvd: 153

$ whois 216.21.226.76

OrgName:    Register.com, Inc 
...

```


MrC

---

### Post by KevinM1 on 2007-08-23
> **Mr. C. said:**
> Your question really is asking who must be authoritative for your zone rextrader.com.  The answer is, it doesn't matter.  As long as the appropriate records exist.  If you plan on receiving email at rextrader.com, you need to have the two basics I indicated earlier.  Your name service provider probably has a website where you can add the record.

I see there is no MX record,  but you do have an A record (assuming 65.175.139.109 maps to your mail server).

This is still pretty Greek to me, so I'm still a bit confused.  All I know is that my boss purchased a static IP address from our ISP for the server's use.  So, that address is probably being used for everything.

EDIT: I'm not sure exactly what to add for the MX record.  The form is setup with:

*hostname textfield*.rextrader.com *priority pulldown menu* *mail server textfield*

EDIT 2: I'm going to be leaving work momentarily, so I may not be able to follow your instructions until tomorrow.  Thanks again, though, for all your help to this point! :D

---

### Post by Mr. C. on 2007-08-23
I understand.  It will become more clear over time and with some study.  I highly recommend if you are going to manage the mail server that you pick of The Book of Postfix : [http://www.postfix-book.com/](http://www.postfix-book.com/) .  A mail is far more complicated than one would imagine.

Before you go setup the MX record, you should consider your hostname.  Do you really want the world to know your mail server as :

   rex-desktop.rextrader.com

Or would you prefer something like any of these:

   mail.rextrader.com
   srv1.rextrader.com
   buzzard.rextrader.com

They de-focus the "desktop" aspect of your name.

Decide now, before you publish the record.  Consider what happens when additional machines are added to the mix.

MrC

---

### Post by KevinM1 on 2007-08-24
> **Mr. C. said:**
> I understand.  It will become more clear over time and with some study.  I highly recommend if you are going to manage the mail server that you pick of The Book of Postfix : [http://www.postfix-book.com/](http://www.postfix-book.com/) .  A mail is far more complicated than one would imagine.

Before you go setup the MX record, you should consider your hostname.  Do you really want the world to know your mail server as :

   rex-desktop.rextrader.com

Or would you prefer something like any of these:

   mail.rextrader.com
   srv1.rextrader.com
   buzzard.rextrader.com

They de-focus the "desktop" aspect of your name.

Decide now, before you publish the record.  Consider what happens when additional machines are added to the mix.
with
MrC

Before I change the hostname, I have a question.  This Ubuntu box is being used for everything - web hosting and e-mail.  Will changing the hostname mess up my Apache2 setup, which, amazingly, I actually got to work (seemingly) correctly?

---

### Post by Mr. C. on 2007-08-24
You will have to change names for any service that uses name-based resolution relying on your current name (such as any apache virtual hosts).  But this is trivial.

MrC

---

### Post by KevinM1 on 2007-08-27
Hi, sorry for bumping this thread after the long delay.

I've managed to set my hostname to mail.rextrader.com.  I'm uncertain of what to add into Register.com's MX record, though.  It asks for both the hostname and the name/address of the mail server.  Would I just put mail.rextrader.com in both fields?  Or is there another piece to the puzzle that I'm missing?

Thanks! :)

EDIT: Upon your suggestion I've ordered the Postfix book.  Unfortunately, it'll take a few days to arrive.

---

### Post by Mr. C. on 2007-08-27
An MX record is a FQDN mapping to an IP address.  So, your mail.rextrader.com is the FQDN and your IP address is its public IP.

Once that is setup, you can use the "host" or "dig" commands to query nameservers to show the DNS entries:

```
$ host rextrader.com
rextrader.com has address 65.175.139.109
```

After your MX record is created, that will turn into :
```
$ host rextrader.com
rextrader.com has address 65.175.139.109
rextrader.com mail is handled by 10 mail.rextrader.com.

```

The numeric value 10 above is the priority; it is the relative priority of your MXs, useful when you have more than one MX server.

MrC

---

### Post by KevinM1 on 2007-08-27
> **Mr. C. said:**
> An MX record is a FQDN mapping to an IP address.  So, your mail.rextrader.com is the FQDN and your IP address is its public IP.

Once that is setup, you can use the "host" or "dig" commands to query nameservers to show the DNS entries:

```
$ host rextrader.com
rextrader.com has address 65.175.139.109
```

After your MX record is created, that will turn into :
```
$ host rextrader.com
rextrader.com has address 65.175.139.109
rextrader.com mail is handled by 10 mail.rextrader.com.

```

The numeric value 10 above is the priority; it is the relative priority of your MXs, useful when you have more than one MX server.

MrC

I just tried putting the IP address in the last field (mail server), and it came back with an error stating it can't use an IP address.  Needless to say, I'm confused.

---

### Post by Mr. C. on 2007-08-27
Sorry, I should have been more clear.

You need one A record that maps the hostname mail.rextrader.com to an IP address.  And you need one MX record that specifies mail.rextrader.com and priority (eg. 10).

MrC

---

### Post by KevinM1 on 2007-08-27
> **Mr. C. said:**
> Sorry, I should have been more clear.

You need one A record that maps the hostname mail.rextrader.com to an IP address.  And you need one MX record that specifies mail.rextrader.com and priority (eg. 10).

MrC

So, I can use the same IP address for two A records?

EDIT: a screenshot of what Register.com's MX record screen looks like for reference: [http://www.rextrader.com/screenshot.png](http://www.rextrader.com/screenshot.png)

---

### Post by Mr. C. on 2007-08-27
You absolutely can have as many A records as you want, mapping to any IP address.

In your screen shot, you might be able to leave the first field (hostname) blank, which would mean the entire domain.  In the mail server field, that would be mail.rextrader.com.  I believe they are trying to make it easier for users to create the records.  See:

[http://help.register.com/cgi-bin/register_help.cfg/php/enduser/std_adp.php?p_faqid=1106&p_created=1095171854&p_sid=ANU_1dKi&p_accessibility=0&p_lva=&p_sp=cF9zcmNoPTEmcF9zb3J0X2J5PSZwX2dyaWRzb3J0PSZwX3Jvd19jbnQ9MTQmcF9wcm9kcz0mcF9jYXRzPSZwX3B2PSZwX2N2PSZwX3BhZ2U9MSZwX3NlYXJjaF90ZXh0PW14&p_li=&p_topview=1](http://help.register.com/cgi-bin/register_help.cfg/php/enduser/std_adp.php?p_faqid=1106&p_created=1095171854&p_sid=ANU_1dKi&p_accessibility=0&p_lva=&p_sp=cF9zcmNoPTEmcF9zb3J0X2J5PSZwX2dyaWRzb3J0PSZwX3Jvd19jbnQ9MTQmcF9wcm9kcz0mcF9jYXRzPSZwX3B2PSZwX2N2PSZwX3BhZ2U9MSZwX3NlYXJjaF90ZXh0PW14&p_li=&p_topview=1)

You do not need a CNAME ( that's just an alias, and you don't want your MX to be a CNAME, as it causes extra DNS lookups for clients ).

MrC

---

### Post by KevinM1 on 2007-08-27
> **Mr. C. said:**
> You absolutely can have as many A records as you want, mapping to any IP address.

In your screen shot, you might be able to leave the first field (hostname) blank, which would mean the entire domain.  In the mail server field, that would be mail.rextrader.com.  I believe they are trying to make it easier for users to create the records.  See:

[http://help.register.com/cgi-bin/register_help.cfg/php/enduser/std_adp.php?p_faqid=1106&p_created=1095171854&p_sid=ANU_1dKi&p_accessibility=0&p_lva=&p_sp=cF9zcmNoPTEmcF9zb3J0X2J5PSZwX2dyaWRzb3J0PSZwX3Jvd19jbnQ9MTQmcF9wcm9kcz0mcF9jYXRzPSZwX3B2PSZwX2N2PSZwX3BhZ2U9MSZwX3NlYXJjaF90ZXh0PW14&p_li=&p_topview=1](http://help.register.com/cgi-bin/register_help.cfg/php/enduser/std_adp.php?p_faqid=1106&p_created=1095171854&p_sid=ANU_1dKi&p_accessibility=0&p_lva=&p_sp=cF9zcmNoPTEmcF9zb3J0X2J5PSZwX2dyaWRzb3J0PSZwX3Jvd19jbnQ9MTQmcF9wcm9kcz0mcF9jYXRzPSZwX3B2PSZwX2N2PSZwX3BhZ2U9MSZwX3NlYXJjaF90ZXh0PW14&p_li=&p_topview=1)

You do not need a CNAME ( that's just an alias, and you don't want your MX to be a CNAME, as it causes extra DNS lookups for clients ).

MrC

Ah, great, it went through.  Am I right in assuming that it'll take 24 hours or so for it to situate itself?

Just to recap, this will now allow me to receive e-mail, correct?  

While I've got you "on the line" so to speak, are there any security tips/settings/procedures you could recommend?  I've already followed the postfix info here describing how to setup SASL authentication.

---

### Post by Mr. C. on 2007-08-27
How long it takes before the records are setup on your registrar's DNS depends on how they do their updates.  The delays they give are generally typical or worst case.

You can always test to see when the record becomes live on *their* DNS server(s):

```
$ dig mx [COLOR="Blue"]@dns11.register.com.[/COLOR] rextrader.com     

; <<>> DiG 9.4.1-P1 <<>> mx @dns11.register.com. rextrader.com
; (1 server found)
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 11660
;; flags: qr aa rd; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0
;; WARNING: recursion requested but not available

;; QUESTION SECTION:
;rextrader.com.                 IN      MX

;; ANSWER SECTION:
[COLOR="Blue"]rextrader.com.          14400   IN      MX      0 mail.rextrader.com.[/COLOR]

;; Query time: 85 msec
;; SERVER: 216.21.234.76#53(216.21.234.76)
;; WHEN: Mon Aug 27 10:38:04 2007
;; MSG SIZE  rcvd: 52
```

Note your record is already on at least one of their DNS servers; I chose to query dns11.register.com.

So, now I test my DNS server to see if your record is available:

```
$ dig mx rextrader.com

; <<>> DiG 9.4.1-P1 <<>> mx rextrader.com
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 64181
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 0

;; QUESTION SECTION:
;rextrader.com.                 IN      MX

;; AUTHORITY SECTION:
rextrader.com.          6580    IN      SOA     dns11.register.com. root.register.com. 2006072715 28800 7200 604800 14400

;; Query time: 1 msec
;; SERVER: 192.168.3.200#53(192.168.3.200)
;; WHEN: Mon Aug 27 10:41:28 2007
;; MSG SIZE  rcvd: 87

```

There is no ANSWER section, so your record is not currently available to me at this moment.   Until your records are available in general, sending MTAs may or may not know where to send mail.

Let me answers your question:

> Just to recap, this will now allow me to receive e-mail, correct? 

with a little clarification.

The MX record allows other MTAs to know where to deliver email for your domain.  Until those MTAs receive your MX as an answer to their queries (eg. who handles mail for rextrader.com ?), mail won't reliably be relayed to mail.rextrader.com.  It would then be up to your MTA (postfix) to accept the email delivery attempts.

As for security / configuration tips, my first recommendation would be to gain as much understanding about your mail system and mail systems in general.  Mail servers are highly complex, and it takes time to build up the knowledge required to manage your system reliably and confidently.

I will recommend that you *only* accept email for valid users, and avoid catchall addresses.  Otherwise, you absolutely will be flooded with a) spam, and b) backscatter non-delivery reports.  And I mean in the 10's of thousands.  Only accept email for valid users.

SASL authentication is only useful to you at this point to allow your remote users to relay email via your server.  You have little reason to use SASL for internal LAN email.

MrC

---

### Post by KevinM1 on 2007-08-28
> **Mr. C. said:**
> The MX record allows other MTAs to know where to deliver email for your domain.  Until those MTAs receive your MX as an answer to their queries (eg. who handles mail for rextrader.com ?), mail won't reliably be relayed to mail.rextrader.com.  It would then be up to your MTA (postfix) to accept the email delivery attempts.

As for security / configuration tips, my first recommendation would be to gain as much understanding about your mail system and mail systems in general.  Mail servers are highly complex, and it takes time to build up the knowledge required to manage your system reliably and confidently.

I'm definitely going to be reading up on this.  The book is on its way.

> I will recommend that you *only* accept email for valid users, and avoid catchall addresses.  Otherwise, you absolutely will be flooded with a) spam, and b) backscatter non-delivery reports.  And I mean in the 10's of thousands.  Only accept email for valid users.

SASL authentication is only useful to you at this point to allow your remote users to relay email via your server.  You have little reason to use SASL for internal LAN email.

This is one of my concerns/questions.  The site will basically be 'userless.'  While I'll get e-mails for technical issues, and the owner will get them for business inquiries/complaints/whatever, I was planning on using a contact form that would use PHP to mail the user's comments/issues to our personal, offsite addresses.  I really only wanted a catch-all for the bounce-back, either automated by ISPs or sent manually by people who accidentally think whatever e-mails we **send** from the site should be responded to, that you mentioned in post 18 of this thread.  Is there a graceful way for me to deal with this sort of thing?

You mentioned something about (I believe) a PTR record in an earlier message.  Do I need one?  If so, what is it for?

Thanks again! :)

---

### Post by Mr. C. on 2007-08-28
Your mail system is never user-less; rather, you create a list of email addresses that your system will either relay, or accept for final delivery.  A catchall degenerates to accepting mail for any email addressed to your domain.

Your web form will include a Envelope Sender.  This is the address used for bounces.  So you need this address listed in your valid recipients list.  Since the users on your server are not local users, you create a virtual alias that maps to your external email address(es).

A PTR record does the opposite of an A record.  It maps your IP address back to a host name.  Mail servers obtain your IP address when your server connects.  They then reverse map the IP address back to a host name, and then check once again to determine that the host name maps back to the IP address.  Each mail server decides whether or not do perform these lookups.  They are to avoid spam and other bogus mail servers that have no valid business sending email directly.  If you don't look like an *official* MTA, other MTAs are likely to reject email from you.

MrC

---

### Post by KevinM1 on 2007-08-28
> **Mr. C. said:**
> Your mail system is never user-less; rather, you create a list of email addresses that your system will either relay, or accept for final delivery.  A catchall degenerates to accepting mail for any email addressed to your domain.

Okay, so I'll actually have to create a webmaster address then, right?

> Your web form will include a Envelope Sender.  This is the address used for bounces.  So you need this address listed in your valid recipients list.  Since the users on your server are not local users, you create a virtual alias that maps to your external email address(es).

I'm not sure what you mean by this.  I was basically planning to do something like this (pseudo-code):
```

<?php

if(isset($_POST['webmaster'])){
   mail($webmaster, 'Technical Problem', $message, $headers);
}

else{
   mail($businessPartner, 'Business Stuff', $message, $headers);
}

?>

```

Would I need to put Envelope Sender in the PHP itself, or set it up on the backend in Postfix?

> A PTR record does the opposite of an A record.  It maps your IP address back to a host name.  Mail servers obtain your IP address when your server connects.  They then reverse map the IP address back to a host name, and then check once again to determine that the host name maps back to the IP address.  Each mail server decides whether or not do perform these lookups.  They are to avoid spam and other bogus mail servers that have no valid business sending email directly.  If you don't look like an *official* MTA, other MTAs are likely to reject email from you.

Ah, okay.  I'll see what I can do through Register.com to set one up.

EDIT: The PTR stuff is more complicated than I thought.  Register.com is looking for *something*.arpa.  The *something* is a blank text field.

---

### Post by Mr. C. on 2007-08-28
Yes, create the webmaster address.  Any email address you use for outgoing email, should be allowed for incoming mail so that bounces can come back to you.   In addition, there are RFC-required addresses, such as root, mailer-daemon, postmaster,  abuse, webmaster if you run a website, and possibly others.

See: [http://us3.php.net/manual/en/function.mail.php](http://us3.php.net/manual/en/function.mail.php) for an explanation of envelope senders and php's mail command.

Assuming 65.175.138.109 is your IP, the PTR record for your rextrader.com name would be 

   109.139.175.65.in-addr.arpa.

A PTR record is just the reverse of the IP with .in-addr.arpa. added to it.

See DNS notes for week 8 here: [http://cis68c2.mikecappella.com/](http://cis68c2.mikecappella.com/)

MrC

---

### Post by KevinM1 on 2007-08-29
> **Mr. C. said:**
> Yes, create the webmaster address.  Any email address you use for outgoing email, should be allowed for incoming mail so that bounces can come back to you.   In addition, there are RFC-required addresses, such as root, mailer-daemon, postmaster,  abuse, webmaster if you run a website, and possibly others.

Okay, thanks.  I'll do that once I get the Postfix book.

> See: [http://us3.php.net/manual/en/function.mail.php](http://us3.php.net/manual/en/function.mail.php) for an explanation of envelope senders and php's mail command.

Ah, thanks.  The PHP manual says that sendmail's list of trusted users is at /etc/mail/trusted-users.  Where's Postfix's list?  Or would I create that in main.cf?

> Assuming 65.175.138.109 is your IP, the PTR record for your rextrader.com name would be 

   109.139.175.65.in-addr.arpa.

A PTR record is just the reverse of the IP with .in-addr.arpa. added to it.

See DNS notes for week 8 here: [http://cis68c2.mikecappella.com/](http://cis68c2.mikecappella.com/)

MrC

Great, thanks!  I've added the PTR record, but it needs time for DNS to do its thing.  Thanks for the link to class notes, too.  I only had one "survey of IT" class in college, years ago, so my knowledge regarding this kind of thing is severely limited (as you could no doubt tell).  I'm a website developer forced into the role of server administrator, so a lot of this is Greek to me.

---

### Post by Mr. C. on 2007-08-29
I'd need to see how your postfix is configured.  Show output of:

```
postconf -n
```

MrC

---

### Post by KevinM1 on 2007-08-29
> **Mr. C. said:**
> I'd need to see how your postfix is configured.  Show output of:

```
postconf -n
```

MrC

Output:
```

alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
broken_sasl_auth_clients = yes
config_directory = /etc/postfix
debug_peer_list = 127.0.0.1
inet_interfaces = all
inet_protocols = all
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
mydestination = rextrader.com,localhost.rextrader.com,localhost
myhostname = mail.rextrader.com
mynetworks = 127.0.0.0/8
myorigin = /etc/mailname
recipient_delimiter = +
relayhost = 
smtp_generic_maps = hash:/etc/postfix/generic
smtp_tls_note_starttls_offer = yes
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache
smtp_use_tls = yes
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
smtpd_sasl_auth_enable = yes
smtpd_sasl_local_domain = 
smtpd_sasl_security_options = noanonymous
smtpd_tls_CAfile = /etc/postfix/ssl/cacert.pem
smtpd_tls_auth_only = no
smtpd_tls_cert_file = /etc/postfix/ssl/smtpd.crt
smtpd_tls_key_file = /etc/postfix/ssl/smtpd.key
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtpd_tls_session_cache_timeout = 3600s
smtpd_use_tls = yes
tls_random_source = dev:/dev/urandom

```

---

### Post by Mr. C. on 2007-08-29
Your postfix installation is configured to only accept real addresses (not virtual alias or virtual mailbox).  In this case, you would add your entries to the /etc/passwd file and aliases to /etc/aliases or /etc/postfix/aliases (see output of **postconf -d local_recipient_maps** to determine in your setup where these databases reside).

MrC

---

### Post by KevinM1 on 2007-08-29
> **Mr. C. said:**
> Your postfix installation is configured to only accept real addresses (not virtual alias or virtual mailbox).  In this case, you would add your entries to the /etc/passwd file and aliases to /etc/aliases or /etc/postfix/aliases (see output of **postconf -d local_recipient_maps** to determine in your setup where these databases reside).

MrC

Interesting.  So, in passwd I'd add an entry along the lines of:
```

webmaster:x:999:999:webmaster:/etc/aliases

```
?

---

### Post by Mr. C. on 2007-08-29
Not if you want webmaster mail to go to some remote site.  If you add the entry to /etc/passwd, then mail will stay local, stored either in an mbox or Maildir.  If you want mail to be remote, create a webmaster alias in the aliases database.  There is no reason to create entries in /etc/passwd if you are going to forward mail offsite anyway.

MrC

---

### Post by KevinM1 on 2007-08-29
> **Mr. C. said:**
> Not if you want webmaster mail to go to some remote site.  If you add the entry to /etc/passwd, then mail will stay local, stored either in an mbox or Maildir.  If you want mail to be remote, create a webmaster alias in the aliases database.  There is no reason to create entries in /etc/passwd if you are going to forward mail offsite anyway.

MrC

Ah.  Hmm... so, just to be clear, would I have to create seperate user accounts for these RFC required addresses?  Or how else could/should I handle the aliases?

---

### Post by Mr. C. on 2007-08-29
No, just aliases.  Eg:
```

$ cat /etc/postfix/aliases
# Basic system aliases -- these MUST be present.
mailer-daemon:  postmaster
postmaster:     root
# additional
hostmaster:     root
www:            root
webmaster:      root
root:           someemail@example.com
...

```

It is generally not a good idea to forward all of root's email to a single remote address, as important notification emails may not be delivered if there are mail problems.  Better to also maintain a copy locally as well:

```
root:          root@localhost, someemail@example.com
```

MrC

---

### Post by KevinM1 on 2007-08-30
> **Mr. C. said:**
> No, just aliases.  Eg:
```

$ cat /etc/postfix/aliases
# Basic system aliases -- these MUST be present.
mailer-daemon:  postmaster
postmaster:     root
# additional
hostmaster:     root
www:            root
webmaster:      root
root:           someemail@example.com
...

```

It is generally not a good idea to forward all of root's email to a single remote address, as important notification emails may not be delivered if there are mail problems.  Better to also maintain a copy locally as well:

```
root:          root@localhost, someemail@example.com
```

MrC

I've added the aliases you mentioned, so I think I'm ready to test it out.  What should I use for the pop3 host if I want to receive mail from my Postfix server?  Would it just be mail.rextrader.com?

---

### Post by Mr. C. on 2007-08-30
I don't recall, and didn't notice earlier in this thread, that you'd installed a POP server.

Postfix is an MTA, not a POP/IMAP server.  You can use courier, dovecot, or other.

Have you installed and configured courier ?  Provided you have a POP server already running, then you can use the IP address of your POP server, or whatever DNS name maps to your server name.

MrC

---

### Post by KevinM1 on 2007-08-30
> **Mr. C. said:**
> I don't recall, and didn't notice earlier in this thread, that you'd installed a POP server.

Postfix is an MTA, not a POP/IMAP server.  You can use courier, dovecot, or other.

Have you installed and configured courier ?  Provided you have a POP server already running, then you can use the IP address of your POP server, or whatever DNS name maps to your server name.

MrC

Ah, good to know.  I thought Postfix was an all-in-one deal.  My plan was to test root@localhost's e-mail.

---

### Post by KevinM1 on 2007-08-30
So, the aliases are, in part, akin to forwarding, correct?  So something like:
```

# Added by installer for initial user -- original just had root: rex
root:	         root@localhost, myemail@gmail.com

#Basic system aliases -- these MUST be present.
mailer-daemon:   postmaster
postmaster:      root

#Additional
hostmaster:      root
www:             root
webmaster:       root
```

Would mean that an e-mail sent to [email]webmaster@rextrader.com[/email] (or mail.rextrader.com) should be forwarded to [email]myemail@gmail.com[/email], right?

During my tests, I get a bounceback with the following message (I tried both hostnames in the same message to see if at least one variation would work):
```

The original message was received at Thu, 30 Aug 2007 12:57:46 -0400
from static-65-175-139-109.metrocast.net [65.175.139.109]

   ----- The following addresses had permanent fatal errors -----
<webmaster@mail.rextrader.com>
    (reason: 550 Host unknown)
<webmaster@rextrader.com>
    (reason: 550 Host unknown)

   ----- Transcript of session follows -----
550 5.1.2 <webmaster@rextrader.com>,<webmaster@mail.rextrader.com>... Host unknown (Name server: mail.rextrader.com.: host not found)
```

The mail server was running at the time (I say this only because I like to leave it off right now out of security concerns).  Knowing me, I'm probably just completely confused with what should actually be happening vs. what I *think* should be happening.

---

### Post by Mr. C. on 2007-08-30
The contents of the mail bounce is not as useful as the log entries.  They will show exactly what went wrong.

Don't think of aliases as forwarding.  Think of them instead as re-writing the email address, and then passing that email to the appropriate Postfix component for delivery.

Let's see the log entries for that email or a new one.  Here's a technique to help you debug.  In a command window, run:

tail -f /var/log/maillog

and highlight the last line.  Then, while that is running, send your email (either via your client, or command line).  All the log lines produced below the highlighted line will be from that email message (because you're currently the only one using the system). 

MrC

---

### Post by KevinM1 on 2007-08-30
> **Mr. C. said:**
> The contents of the mail bounce is not as useful as the log entries.  They will show exactly what went wrong.

Don't think of aliases as forwarding.  Think of them instead as re-writing the email address, and then passing that email to the appropriate Postfix component for delivery.

Let's see the log entries for that email or a new one.  Here's a technique to help you debug.  In a command window, run:

tail -f /var/log/maillog

and highlight the last line.  Then, while that is running, send your email (either via your client, or command line).  All the log lines produced below the highlighted line will be from that email message (because you're currently the only one using the system). 

MrC

This is the damnest thing...

When I tried restarting postfix, I got the following warning:
```

warning: /var/spool/postfix/etc/hosts and /etc/hosts differ
```

So, I edited them both to be:
```

127.0.0.1 localhost mail.rextrader.com
127.0.1.1 mail

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

Then, I got another warning:
```

warning: /var/spool/postfix/etc/hosts~ and /etc/hosts~ differ
```

So, again, I edited them to be the same:
```

127.0.0.1 localhost
127.0.0.1 mail.rextrader.com
127.0.1.1 mail

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

It started up without any warnings.  So, I tried doing the 'tail' command, like you suggested, but nothing happened after it displayed the last log of the system starting:
```

Aug 30 13:23:32 mail postfix/postfix-script: starting the Postfix mail system
Aug 30 13:23:32 mail postfix/master[16633]: daemon started -- version 2.3.8, configuration /etc/postfix
```

There's nothing below that, even after I sent mail.

There's nothing in the error logs that's interesting.  Indeed, this is all there is, which came from me trying to start an already running Postfix server:
```

Aug 30 12:50:25 mail postfix/postfix-script: fatal: the Postfix mail system is already running
Aug 30 12:50:36 mail postfix/postfix-script: fatal: usage: postfix start (or stop, reload, abort, flush, check, set-permissions, upgrade-configuration)
```

---

### Post by Mr. C. on 2007-08-30
Postfix always logs its transactions. If there is nothing in the logs, then postfix was not used.

How are you sending the email?
Have you verified your connection to postfix 

```
$ telnet localhost 25
EHLO examxple.com
QUIT

```
(change localhost above with the correct hostname or IP)

MrC

---

### Post by KevinM1 on 2007-08-30
> **Mr. C. said:**
> Postfix always logs its transactions. If there is nothing in the logs, then postfix was not used.

How are you sending the email?
Have you verified your connection to postfix 

```
$ telnet localhost 25
EHLO examxple.com
QUIT

```
(change localhost above with the correct hostname or IP)

MrC

Ah, duh, I'm an idiot.  I was still sending it via our ISP's mail.  Unfortunately, I'm at home now, so I won't be able to test it until tomorrow.

---

### Post by KevinM1 on 2007-08-31
I just tested my setup my sending a message to [email]webmaster@rextrader.com[/email] through a PHP script.  Nothing was forwarded to my gmail account.  Here's the log.  I've highlighted a line that may be part of the problem:
```

Aug 31 12:02:15 mail postfix/pickup[26622]: 70EC6C3C550: uid=33 from=<www-data>
Aug 31 12:02:15 mail postfix/cleanup[29965]: 70EC6C3C550: message-id=<20070831160215.70EC6C3C550@mail.rextrader.com>
Aug 31 12:02:15 mail postfix/qmgr[16635]: 70EC6C3C550: from=<www-data@rextrader.com>, size=445, nrcpt=1 (queue active)
**Aug 31 12:02:15 mail postfix/local[29967]: warning: database /etc/aliases.db is older than source file /etc/aliases**
Aug 31 12:02:15 mail postfix/local[29967]: 70EC6C3C550: to=<webmaster@rextrader.com>, relay=local, delay=0.24, delays=0.12/0.09/0/0.03, dsn=5.1.1, status=bounced (unknown user: "webmaster")
Aug 31 12:02:15 mail postfix/cleanup[29965]: 9F528C3C552: message-id=<20070831160215.9F528C3C552@mail.rextrader.com>
Aug 31 12:02:15 mail postfix/qmgr[16635]: 9F528C3C552: from=<>, size=2176, nrcpt=1 (queue active)
Aug 31 12:02:15 mail postfix/bounce[29968]: 70EC6C3C550: sender non-delivery notification: 9F528C3C552
Aug 31 12:02:15 mail postfix/qmgr[16635]: 70EC6C3C550: removed
Aug 31 12:02:16 mail postfix/local[29967]: 9F528C3C552: to=<www-data@rextrader.com>, relay=local, delay=1.1, delays=0.03/0/0/1.1, dsn=2.0.0, status=sent (delivered to command: procmail -a "$EXTENSION")
Aug 31 12:02:16 mail postfix/qmgr[16635]: 9F528C3C552: removed

```

Would I have to do a postmap or something to get aliases.db resynched with the source file?

---

### Post by Mr. C. on 2007-08-31
Run:

```
newaliases
```

MrC

---

### Post by KevinM1 on 2007-08-31
> **Mr. C. said:**
> Run:

```
newaliases
```

MrC

Awesome!  Works like a charm. :)

---

