---
title: "Postfix + mysql, no mailboxes"
date: 2010-11-01
forum: Server Platforms
---

### Post by inckiekage on 2010-11-01
Hello

i used this guide, to configure my mail system: [https://help.ubuntu.com/community/PostfixCompleteVirtualMailSystemHowto](https://help.ubuntu.com/community/PostfixCompleteVirtualMailSystemHowto)


when i try to login, i can see this error in /var/log/mail.log

```
Nov  1 11:32:38 infoserver authdaemond: received auth request, service=imap, authtype=login
Nov  1 11:32:38 infoserver authdaemond: authmysql: trying this module
Nov  1 11:32:38 infoserver authdaemond: authmysqllib: connected. Versions: header 50137, client 50141, server 50141
Nov  1 11:32:38 infoserver authdaemond: SQL query: SELECT username, password, "", '5000', '5000', '/home/vmail', maildir, concat(quota,'S'), name, "" FROM mailbox WHERE username = 'kh@decoit.dk'
Nov  1 11:32:38 infoserver authdaemond: password matches successfully
Nov  1 11:32:38 infoserver authdaemond: authmysql: sysusername=<null>, sysuserid=5000, sysgroupid=5000, homedir=/home/vmail, address=kh@decoit.dk, fullname=Kim Henriksen, maildir=kh@decoit.dk/, quota=0S, options=<null>
Nov  1 11:32:38 infoserver authdaemond: authmysql: clearpasswd=<null>, passwd=$1$60e339ce$ylZqh7I163UOitptHYPdl/
Nov  1 11:32:38 infoserver authdaemond: Authenticated: sysusername=<null>, sysuserid=5000, sysgroupid=5000, homedir=/home/vmail, address=kh@decoit.dk, fullname=Kim Henriksen, maildir=kh@decoit.dk/, quota=0S, options=<null>
Nov  1 11:32:38 infoserver authdaemond: Authenticated: clearpasswd=he6uwa6h, passwd=$1$60e339ce$ylZqh7I163UOitptHYPdl/
Nov  1 11:32:38 infoserver imapd: chdir kh@decoit.dk/: No such file or directory
Nov  1 11:32:38 infoserver imapd: kh@decoit.dk: No such file or directory
```

and my /home/vmail dir is empty, no mailboxes were created.

this is my main.cf 
```
# Virtual Mailbox Domain Settings

virtual_alias_maps = mysql:/etc/postfix/mysql_virtual_alias_maps.cf
virtual_mailbox_domains = mysql:/etc/postfix/mysql_virtual_domains_maps.cf
virtual_mailbox_maps = mysql:/etc/postfix/mysql_virtual_mailbox_maps.cf
virtual_mailbox_limit = 51200000
virtual_minimum_uid = 5000
virtual_uid_maps = static:5000
virtual_gid_maps = static:5000
virtual_mailbox_base = /home/vmail
virtual_transport = virtual

# Additional for quota support

virtual_create_maildirsize = yes
virtual_mailbox_extended = yes
virtual_mailbox_limit_maps = mysql:/etc/postfix/mysql_virtual_mailbox_limit_maps.cf
virtual_mailbox_limit_override = yes
virtual_maildir_limit_message = Sorry, the your maildir has overdrawn your diskspace quota, please free up some of spaces of your mailbox try again.
virtual_overquota_bounce = yes

# SMTP Authentication - SASL

smtpd_recipient_restrictions = reject_unauth_pipelining, permit_mynetworks, permit_sasl_authenticated, reject_non_fqdn_recipient, reject_unknown_recipient_domain reject_unauth_destination, check_policy_service inet:127.0.0.1:10023, permit
# modify the existing smtpd_sender_restrictions
smtpd_sender_restrictions = permit_sasl_authenticated, permit_mynetworks, reject_non_fqdn_sender, reject_unknown_sender_domain, reject_unauth_pipelining, permit
# then add these
smtpd_sasl_auth_enable = yes
broken_sasl_auth_clients = yes
smtpd_sasl_security_options = noanonymous
smtpd_sasl_local_domain =
```

vmail user:
```
kimse@infoserver:~$ id vmail
uid=5000(vmail) gid=5000(vmail) groups=5000(vmail)
```

```
kimse@infoserver:/home/vmail$ ls -la
total 20
drwxr-xr-x 2 vmail vmail 4096 2010-11-01 12:56 .
drwxr-xr-x 4 root  root  4096 2010-10-31 21:20 ..
-rw-r--r-- 1 vmail vmail  220 2010-04-19 04:15 .bash_logout
-rw-r--r-- 1 vmail vmail 3103 2010-04-19 04:15 .bashrc
-rw-r--r-- 1 vmail vmail  675 2010-04-19 04:15 .profile
```

---

### Post by inckiekage on 2010-11-02
Anyone?

---

### Post by inckiekage on 2010-11-03
> **vn_nguyenquang said:**
> I have a problem relate to posttfix.I want to mirgare postfix mail server to exchange 2010 mail server but I can't do it,u can help me.You can show me have to do configure postfix and exchange how to? thanks !

Dont use my thread, create your own!

---

### Post by HermanAB on 2010-11-03
Howdy,

I gave up with postfix years ago.  It works well, but configuring it is just too much work.  You need to go to the postfix project home page and read up, but once you are tired of it, go and install Citadel - it only takes about 20 minutes and it 'Just Works'.

---

