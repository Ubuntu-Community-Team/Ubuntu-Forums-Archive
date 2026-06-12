---
title: "Problems setting up mail server (stuck trying to telnet into smtp)"
date: 2009-07-15
forum: Server Platforms
---

### Post by gilligan8 on 2009-07-15
I'm following falko's "howtoforge" page [http://www.howtoforge.com/virtual-users-domains-postfix-courier-mysql-squirrelmail-ubuntu8.04]("http://www.howtoforge.com/virtual-users-domains-postfix-courier-mysql-squirrelmail-ubuntu8.04").

Everything has been fine until I get to the top of [page 4]("http://www.howtoforge.com/virtual-users-domains-postfix-courier-mysql-squirrelmail-ubuntu8.04-p4").  When I telnet in it just stops there.

```
root@TheSun:/# telnet localhost 25
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
```

I then escape out and quit but obviously something isn't working.

Anyone know where to start looking to resolve this?  This is not my first server but is my first attempt at a mail server.

Thanks in advance,
Gilligan

---

### Post by littlegreiger on 2009-07-15
It looks like it's working, did you remember to type
```
ehlo localhost
```
You have to type this while you're still connected via telnet

---

### Post by gilligan8 on 2009-07-15
Sorry... you are right... I should have mentioned that when I type that it still just stays there doing nothing.  THEN I escape and quit.

Thanks for the quick response though!

---

### Post by gilligan8 on 2009-07-15
Ok, I think I figured out the problem, but I'm not sure which direction to go to fix it.

In my mail logs I have a lot of errors:

```
Jul 15 22:30:44 TheSun postfix/proxymap[7424]: fatal: /etc/postfix/mysql-virtual_forwardings.cf: bad string length 0 < 1: dbname =
Jul 15 22:30:45 TheSun postfix/cleanup[7234]: warning: private/proxymap socket: service dict_proxy_open: Success
Jul 15 22:30:45 TheSun postfix/smtpd[7302]: warning: private/proxymap socket: service dict_proxy_open: Connection reset by peer
Jul 15 22:30:45 TheSun postfix/master[7230]: warning: process /usr/lib/postfix/proxymap pid 7424 exit status 1
Jul 15 22:30:45 TheSun postfix/master[7230]: warning: /usr/lib/postfix/proxymap: bad command startup -- throttling

```

So looks like my database is empty... which I found was sort of the problem for someone else [here.]("http://ubuntuforums.org/showthread.php?t=1193019")  But it doesn't look like they are using mysql so I'd think it needs a different solution.

Gonna keep on looking but could definitely use some direction,
Gilligan

---

### Post by gilligan8 on 2009-07-16
bump for the AM people. ;)

---

### Post by gilligan8 on 2009-07-16
Here is `postconf -n` as requested by someone.

```
alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
broken_sasl_auth_clients = yes
config_directory = /etc/postfix
content_filter = amavis:[127.0.0.1]:10024
html_directory = /usr/share/doc/postfix/html
inet_interfaces = all
mailbox_size_limit = 0
mydestination = mail.<my real server name>.com, localhost, localhost.localdomain
myhostname = mail.<my real server name>.com
mynetworks = 127.0.0.0/8
proxy_read_maps = $local_recipient_maps $mydestination $virtual_alias_maps $virtual_alias_domains $virtual_mailbox_maps $virtual_mailbox_domains $relay_recipient_maps $relay_domains $canonical_maps $sender_canonical_maps $recipient_canonical_maps $relocated_maps $transport_maps $mynetworks $virtual_mailbox_limit_maps
readme_directory = /usr/share/doc/postfix
receive_override_options = no_address_mappings
recipient_delimiter = +
relayhost =
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_recipient_restrictions = permit_mynetworks, permit_sasl_authenticated, reject_unauth_destination
smtpd_sasl_auth_enable = yes
smtpd_sasl_authenticated_header = yes
smtpd_tls_cert_file = /etc/postfix/smtpd.cert
smtpd_tls_key_file = /etc/postfix/smtpd.key
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtpd_use_tls = yes
transport_maps = proxy:mysql:/etc/postfix/mysql-virtual_transports.cf
virtual_alias_domains =
virtual_alias_maps = proxy:mysql:/etc/postfix/mysql-virtual_forwardings.cf, mysql:/etc/postfix/mysql-virtual_email2email.cf
virtual_gid_maps = static:5000
virtual_mailbox_base = /home/vmail
virtual_mailbox_domains = proxy:mysql:/etc/postfix/mysql-virtual_domains.cf
virtual_mailbox_maps = proxy:mysql:/etc/postfix/mysql-virtual_mailboxes.cf
virtual_uid_maps = static:5000

```

---

### Post by janrikard on 2010-12-12
Gilligan8:

did you find a solution to the problem with bad string length?
 Jul 15 22:30:44 TheSun postfix/proxymap[7424]: fatal: /etc/postfix/mysql-virtual_forwardings.cf: bad string length 0 < 1: dbname =

/rikard

---

### Post by gilligan8 on 2010-12-12
Nope, I completely abandoned ship on this since I was getting no where. :(

---

### Post by HermanAB on 2010-12-12
Howdy,

Postfix is generally a big waste of time to set up.  Yes, it is much better than Sendmail, but I gave up with it years ago.  Life is too short.  

You can install Citadel in about 20 minutes using their Easy Install script and it Just Works (TM):
[http://citadel.org](http://citadel.org)

---

