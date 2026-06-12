---
title: "Ubuntu Server 13.10 | Postfix 2.10.2 | Cyrus 2.4.16 | saslauthd 2.1.25"
date: 2014-03-09
forum: Server Platforms
---

### Post by Roswebnet on 2014-03-09
Hi, everyone

I have successfully setup the Cyrus IMAP in combination with Postfix. UNIX users after authentication can access mail server and sent or receive mails. 
I would like to create virtual users with virtual mailboxes and virtual domains. I did following steps and changed configurations and logs:
```

rm -rf /var/run/saslauthd
ln -s /var/spool/postfix/var/run/saslauthd  /var/run/saslauthd
chgrp mail /etc/sasldb2
```

/etc/default/saslauth
```
START=yes
MECHANISMS="sasldb"
MECH_OPTIONS=""
THREADS=5
OPTIONS="-c  -Vd -m  /var/spool/postfix/var/run/saslauthd"
```

/etc/imapd.conf
```
[...]
altnamespace:  yes
lmtp_downcase_rcpt: yes
admins: cyrus
allowanonymouslogin:  no
autocreatequota: -1
allowplaintext: yes
sasl_mech_list:  PLAIN
loginrealms: domain.tld
virtdomains: userid
defaultdomain:  domain.tld
sasl_pwcheck_method: auxprop
sasl_auxprop_plugin:  sasldb
lmtpsocket:  /var/run/cyrus/socket/lmtp
[...]

```
/etc/postfix/main.cf
```
[...]
mydomain=domain.tld
[...]
virtual_transport  = $mailbox_transport
virtual_mailbox_domains =  $mydomain
virtual_mailbox_maps =  hash:/etc/postfix/vmailbox
virtual_alias_maps =  hash:/etc/postfix/virtual
[...]
smtp_sasl_auth_enable =  yes
smtp_sasl_password_maps =  hash:/etc/postfix/sasl_passwd
smtp_sasl_security_options =  noanonymous
[...]
smtpd_sasl_auth_enable =  yes
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients =  yes
[...]

```
/etc/postfix/master.cf
```
[...]
smtp      inet  n        -       -       -       -       smtpd
[...]
submission inet  n        -       -       -       -       smtpd
[...]
local     unix  -        n       n       -       -       local
virtual   unix  -       n       n        -       -       virtual
lmtp      unix  -       -       n       -        -       lmtp
[...]

```
```
/etc/postfix/sasl/smptd.conf
pwcheck_method:  auxprop
auxprop_plugin: sasldb
mech_list: PLAIN LOGIN

```

```

[root@srv01]("wlmailhtml:{4FF7BDC0-5C32-4FDE-A677-21D8A4406F1E}mid://00000071/!x-usc:mailto:root@srv01"):~# sasldblistusers2
[cyrus@srv01]("wlmailhtml:{4FF7BDC0-5C32-4FDE-A677-21D8A4406F1E}mid://00000071/!x-usc:mailto:cyrus@srv01"): userPassword
[andrey@srv01]("wlmailhtml:{4FF7BDC0-5C32-4FDE-A677-21D8A4406F1E}mid://00000071/!x-usc:mailto:andrey@srv01"): userPassword
[info@domain.tld]("wlmailhtml:{4FF7BDC0-5C32-4FDE-A677-21D8A4406F1E}mid://00000071/!x-usc:mailto:info@domain.tld"):  userPassword

localhost.localdomain> lm
user.andrey  (\HasChildren)
user.andrey.Deleted Items  (\HasNoChildren)
user.andrey.Drafts (\HasNoChildren)
user.andrey.Junk  E-mail (\HasNoChildren)
user.andrey.Sent Items (\HasNoChildren)
user.info  (\HasNoChildren)
[user.info@domain.tld]("wlmailhtml:{4FF7BDC0-5C32-4FDE-A677-21D8A4406F1E}mid://00000071/!x-usc:mailto:user.info@domain.tld")  (\HasNoChildren)

[root@srv01]("wlmailhtml:{4FF7BDC0-5C32-4FDE-A677-21D8A4406F1E}mid://00000071/!x-usc:mailto:root@srv01"):~#  testsaslauthd -u info -r domain.tld -p Pa77w0rd
0: OK "Success."

[root@srv01]("wlmailhtml:{4FF7BDC0-5C32-4FDE-A677-21D8A4406F1E}mid://00000071/!x-usc:mailto:root@srv01"):~# testsaslauthd -u [info@domain.tld]("wlmailhtml:{4FF7BDC0-5C32-4FDE-A677-21D8A4406F1E}mid://00000071/!x-usc:mailto:info@domain.tld") -p Pa77w0rd
0: NO  "authentication failed"


```
auth.log:

```
Mar  9 23:26:28 srv01  saslauthd[9066]: cache_get_rlock : attempting a read 
lock on slot:  950
[This is strange!] => Mar  9 23:26:28 srv01 saslauthd[9066]:  cache_lookup 
: [login=info] [service=domain.tld] [realm=imap]: not found,  update pending
Mar  9 23:26:28 srv01 saslauthd[9066]: cache_un_lock   :  attempting to 
release lock on slot: 950
Mar  9 23:26:28 srv01  saslauthd[9067]: get_accept_lock : acquired accept 
lock
Mar  9 23:26:28  srv01 saslauthd[9066]: cache_get_wlock : attempting a write 
lock on slot:  950
Mar  9 23:26:28 srv01 saslauthd[9066]: cache_commit    : lookup  committed
Mar  9 23:26:28 srv01 saslauthd[9066]: cache_un_lock   : attempting  to 
release lock on slot: 950
Mar  9 23:26:28 srv01 saslauthd[9066]:  do_auth         : auth success: 
[user=info] [service=imap]  [realm=domain.tld] [mech=sasldb]
Mar  9 23:26:28 srv01 saslauthd[9066]:  do_request      : response: OK
Mar  9 23:26:58 srv01 saslauthd[9067]:  rel_accept_lock : released accept 
lock
Mar  9 23:26:58 srv01  saslauthd[9067]: cache_get_rlock : attempting a read 
lock on slot:  681
Mar  9 23:26:58 srv01 saslauthd[9067]: cache_lookup    :  
[login=info@roshost.tk] [service=] [realm=imap]: not found, update  pending
Mar  9 23:26:58 srv01 saslauthd[9067]: cache_un_lock   : attempting  to 
release lock on slot: 681
Mar  9 23:26:58 srv01 saslauthd[9068]:  get_accept_lock : acquired accept 
lock
Mar  9 23:26:58 srv01  saslauthd[9067]: do_auth         : auth failure: 
[user=info@domain.tld]  [service=imap] [realm=] [mech=sasldb] 
[reason=Unknown]
Mar  9 23:26:58  srv01 saslauthd[9067]: do_request      : response: NO

```

mail.log 

```
Mar  9 23:29:42 srv01 cyrus/imaps[9496]:  badlogin: [192.168.1.1] plaintext 
info SASL(-13): user not found: checkpass  failed
```

I  cannot login from Windows live mail with username [EMAIL="info@domain.tld"]info@domain.tld[/EMAIL]. The unix user andrey can login, auto create mailboxes and 
special folders.

What is wrong? :(

Thank you.

---

### Post by Roswebnet on 2014-03-13
Solved
 
 in /etc/imapd.conf comment
 ```

 [...]
 # The default domain for virtual domain support
 # If the domain of a user can't be taken from its login and it can't
 # be determined by doing a reverse lookup on the interface IP, this
 # domain is used.
 # defaultdomain: domain.tld
 [...]
 
```
 
 in /etc/postfix/main.cf comment
 ```

 [...]
 mailbox_transport = lmtp:unix:/var/run/cyrus/socket/lmtp
 [...]
 virtual_transport = $mailbox_transport
 virtual_mailbox_domains =  domain2.tld domain3.tld
 virtual_mailbox_maps = hash:/etc/postfix/vmailbox
 virtual_alias_maps = hash:/etc/postfix/virtual
 [...]
 
```
 
 Attention! I got never working  *mailbox_transport = lmtp:inet:localhost *which is a most recent version of lmtp. However, 1000-2000 accounts with a *lmtp mailbox_transport = lmtp:unix:/var/run/cyrus/socket/lmtp* should work without any problem.
 
 P.S.: All emails are in the /var/spool/cyrus/mail
P.P.S.: Here is really great tutorial how to configure Postfix and SASL: [http://rene.bz/setting-smtp-authentication-over-tls-postfix/#SASL_and_Postfix](http://rene.bz/setting-smtp-authentication-over-tls-postfix/#SASL_and_Postfix)
P.P.S.: Got other problem, Postfix does not  read smptd.conf. But this will be asked in other topic.

---

