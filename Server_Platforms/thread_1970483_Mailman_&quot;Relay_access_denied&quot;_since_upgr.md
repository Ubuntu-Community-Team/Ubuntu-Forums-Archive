---
title: "Mailman &quot;Relay access denied&quot; since upgrade from 10.04 to 12.04"
date: 2012-05-01
forum: Server Platforms
---

### Post by clement.analogue on 2012-05-01
Hi,

Since the upgrade from 10.04 to 12.04, I've got a problem with mailman. Only the mail with the same domain name (DN) than the list server can send message and only those can receive them. Why ? And how to solve the issue ?
The logs of postfix :

```
May  1 10:46:08 clement-desktop postfix/smtpd[17869]: warning: hostname ns.forumanalouge.fr does not resolve to address 192.168.1.11: No address associated with hostname
May  1 10:46:08 clement-desktop postfix/smtpd[17869]: connect from unknown[192.168.1.11]
May  1 10:46:08 clement-desktop postfix/smtpd[17869]: Anonymous TLS connection established from unknown[192.168.1.11]: TLSv1 with cipher ECDHE-RSA-AES256-SHA (256/256 bits)
May  1 10:46:08 clement-desktop postfix/smtpd[17869]: CCE521FCD0: client=unknown[192.168.1.11], sasl_method=PLAIN, sasl_username=clement
May  1 10:46:08 clement-desktop postfix/cleanup[17874]: CCE521FCD0: message-id=<4F9FA2CF.1000208@forumanalogue.fr>
May  1 10:46:08 clement-desktop postfix/qmgr[3072]: CCE521FCD0: from=<*******@forumanalogue.fr>, size=720, nrcpt=1 (queue active)
May  1 10:46:08 clement-desktop postfix/smtpd[17869]: disconnect from unknown[192.168.1.11]
May  1 10:46:09 clement-desktop postfix/pipe[17875]: CCE521FCD0: to=<****@mail.forumanalogue.fr>, relay=mailman, delay=0.38, delays=0.09/0.01/0/0.29, dsn=2.0.0, status=sent (delivered via mailman service)
May  1 10:46:09 clement-desktop postfix/qmgr[3072]: CCE521FCD0: removed
May  1 10:46:11 clement-desktop postfix/smtpd[17869]: warning: hostname localhost does not resolve to address ::1: No address associated with hostname
May  1 10:46:11 clement-desktop postfix/smtpd[17869]: connect from unknown[::1]
May  1 10:46:11 clement-desktop postfix/smtpd[17869]: NOQUEUE: reject: RCPT from unknown[::1]: 554 5.7.1 <*******@orange.fr>: Relay access denied; from=<***-bounces@mail.forumanalogue.fr> to=<*******@orange.fr> proto=ESMTP helo=<[127.0.1.1]>
May  1 10:46:11 clement-desktop postfix/smtpd[17869]: NOQUEUE: reject: RCPT from unknown[::1]: 554 5.7.1 <*******@hotmail.fr>: Relay access denied; from=<****-bounces@mail.forumanalogue.fr> to=<*******@hotmail.fr> proto=ESMTP helo=<[127.0.1.1]>
May  1 10:46:11 clement-desktop postfix/smtpd[17869]: 19B771FCD0: client=unknown[::1]
May  1 10:46:11 clement-desktop postfix/cleanup[17874]: 19B771FCD0: message-id=<4F9FA2CF.1000208@forumanalogue.fr>
May  1 10:46:11 clement-desktop postfix/qmgr[3072]: 19B771FCD0: from=<****-bounces@mail.forumanalogue.fr>, size=1768, nrcpt=1 (queue active)
May  1 10:46:11 clement-desktop postfix/smtpd[17869]: disconnect from unknown[::1]
May  1 10:46:11 clement-desktop postfix/local[17879]: 19B771FCD0: to=<*******@forumanalogue.fr>, relay=local, delay=0.22, delays=0.05/0.02/0/0.15, dsn=2.0.0, status=sent (delivered to maildir)
May  1 10:46:11 clement-desktop postfix/qmgr[3072]: 19B771FCD0: removed
```Configuration files :
```
$ postconf -n
alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases, hash:/var/lib/mailman/data/aliases
append_dot_mydomain = no
biff = no
broken_sasl_auth_clients = yes
config_directory = /etc/postfix
home_mailbox = Maildir/
inet_interfaces = all
inet_protocols = all
mailbox_command =
mailbox_size_limit = 0
mailman_destination_recipient_limit = 1
message_size_limit = 0
mydestination = mail.forumanalogue.fr, localhost.localdomain, localhost, forumanalogue.fr
myhostname = mail.forumanalogue.fr
mynetworks = 127.0.0.0/8, 192.168.1.0/24
myorigin = /etc/mailname
readme_directory = no
recipient_delimiter = +
relay_domains = mail.forumanalogue.fr
smtp_sasl_auth_enable = yes
smtp_sasl_password_maps = hash:/etc/postfix/sasl_passwd
smtp_sasl_security_options =
smtp_tls_note_starttls_offer = yes
smtp_tls_security_level = may
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
smtpd_sasl_auth_enable = yes
smtpd_sasl_local_domain =
smtpd_sasl_security_options = noanonymous
smtpd_tls_CAfile = /etc/ssl/certs/cacert.pem
smtpd_tls_auth_only = no
smtpd_tls_cert_file = /etc/ssl/certs/smtpd.crt
smtpd_tls_key_file = /etc/ssl/private/smtpd.key
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_security_level = may
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtpd_tls_session_cache_timeout = 3600s
smtpd_use_tls = yes
tls_random_source = dev:/dev/urandom
transport_maps = hash:/etc/postfix/transport
``````
$ cat transport
mail.forumanalogue.fr        mailman:
``````
postfinger - postfix configuration on Tue May  1 11:04:39 CEST 2012
version: 1.30

Warning: postfinger output may show private configuration information,
such as ip addresses and/or domain names which you do not want to show
to the public.  If this is the case it is your responsibility to modify
the output to hide this private information.  [Remove this warning with
the --nowarn option.]

--System Parameters--
mail_version = 2.9.1
hostname = clement-desktop
uname = Linux clement-desktop 3.2.0-24-generic #37-Ubuntu SMP Wed Apr 25 08:43:22 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

--Packaging information--
looks like this postfix comes from deb package: postfix-2.9.1-4

--main.cf non-default parameters--
alias_maps = hash:/etc/aliases, hash:/var/lib/mailman/data/aliases
append_dot_mydomain = no
biff = no
broken_sasl_auth_clients = yes
home_mailbox = Maildir/
mailbox_size_limit = 0
mailman_destination_recipient_limit = 1
message_size_limit = 0
mydestination = mail.forumanalogue.fr, localhost.localdomain, localhost, forumanalogue.fr
myhostname = mail.forumanalogue.fr
mynetworks = 127.0.0.0/8, 192.168.1.0/24
myorigin = /etc/mailname
readme_directory = no
recipient_delimiter = +
relay_domains = mail.forumanalogue.fr
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
smtpd_sasl_auth_enable = yes
smtpd_tls_CAfile = /etc/ssl/certs/cacert.pem
smtpd_tls_cert_file = /etc/ssl/certs/smtpd.crt
smtpd_tls_key_file = /etc/ssl/private/smtpd.key
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_security_level = may
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtpd_use_tls = yes
smtp_sasl_auth_enable = yes
smtp_sasl_password_maps = hash:/etc/postfix/sasl_passwd
smtp_sasl_security_options =
smtp_tls_note_starttls_offer = yes
smtp_tls_security_level = may
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
transport_maps = hash:/etc/postfix/transport

--master.cf--
smtp      inet  n       -       -       -       -       smtpd
pickup    fifo  n       -       -       60      1       pickup
cleanup   unix  n       -       -       -       0       cleanup
qmgr      fifo  n       -       n       300     1       qmgr
tlsmgr    unix  -       -       -       1000?   1       tlsmgr
rewrite   unix  -       -       -       -       -       trivial-rewrite
bounce    unix  -       -       -       -       0       bounce
defer     unix  -       -       -       -       0       bounce
trace     unix  -       -       -       -       0       bounce
verify    unix  -       -       -       -       1       verify
flush     unix  n       -       -       1000?   0       flush
proxymap  unix  -       -       n       -       -       proxymap
proxywrite unix -       -       n       -       1       proxymap
smtp      unix  -       -       -       -       -       smtp
relay     unix  -       -       -       -       -       smtp
    -o smtp_fallback_relay=
showq     unix  n       -       -       -       -       showq
error     unix  -       -       -       -       -       error
retry     unix  -       -       -       -       -       error
discard   unix  -       -       -       -       -       discard
local     unix  -       n       n       -       -       local
virtual   unix  -       n       n       -       -       virtual
lmtp      unix  -       -       -       -       -       lmtp
anvil     unix  -       -       -       -       1       anvil
scache    unix  -       -       -       -       1       scache
maildrop  unix  -       n       n       -       -       pipe
  flags=DRhu user=vmail argv=/usr/bin/maildrop -d ${recipient}
uucp      unix  -       n       n       -       -       pipe
  flags=Fqhu user=uucp argv=uux -r -n -z -a$sender - $nexthop!rmail ($recipient)
ifmail    unix  -       n       n       -       -       pipe
  flags=F user=ftn argv=/usr/lib/ifmail/ifmail -r $nexthop ($recipient)
bsmtp     unix  -       n       n       -       -       pipe
  flags=Fq. user=bsmtp argv=/usr/lib/bsmtp/bsmtp -t$nexthop -f$sender $recipient
scalemail-backend unix    -    n    n    -    2    pipe
  flags=R user=scalemail argv=/usr/lib/scalemail/bin/scalemail-store ${nexthop} ${user} ${extension}
mailman   unix  -       n       n       -       -       pipe
  flags=FR user=list argv=/usr/lib/mailman/bin/postfix-to-mailman.py
  ${nexthop} ${user}

-- end of postfinger output --
```Thank you !

---

### Post by SeijiSensei on 2012-05-01
It seems to be having problems resolving names.  Is DNS set up correctly for hosts in 192.168.1.0/24?  Did the server's /etc/hosts file get rewritten?  The fact that the server can't even resolve the IPv6 address for "localhost" is disturbing.

> May  1 10:46:11 clement-desktop postfix/smtpd[17869]: warning: hostname localhost does not resolve to address ::1: No address associated with hostname

There may be other issues, but since mail services depend very directly on correct DNS resolution, I'd start there first.

---

### Post by elico on 2012-05-01
what is you hosts file content?

---

### Post by clement.analogue on 2012-05-01
> **SeijiSensei said:**
> It seems to be having problems resolving  names.

I noticed that.

> **SeijiSensei said:**
> Is DNS set up correctly for hosts in 192.168.1.0/24?

I guess. At least, it was for Ubuntu 10.04.
Some bind9 files :

```
$ cat db.192
;
; BIND reverse data file for local loopback interface
;
$TTL    604800
@    IN    SOA    localhost. root.localhost. (
                  2        ; Serial
             604800        ; Refresh
              86400        ; Retry
            2419200        ; Expire
             604800 )    ; Negative Cache TTL
;
@    IN    NS    ns.    
11    IN    PTR    ns.forumanalouge.fr.
``````
$ cat db.forumanalogue.fr
;
; BIND data file for local loopback interface
;
$TTL    604800
@    IN    SOA    ns.forumanalogue.fr. root.ns.forumanalogue.fr. (
             2012050101        ; Serial
             604800        ; Refresh
              86400        ; Retry
            2419200        ; Expire
             604800 )    ; Negative Cache TTL
;
@    IN    NS    ns.forumanalogue.fr.
ns    IN    A    192.168.1.11
@    IN    A    192.168.1.11
www    IN    A    192.168.1.11
mail    IN    A    192.168.1.11
lists    IN    A    192.168.1.11
@    IN    A    127.0.0.1
@    IN    AAAA    ::1
```(I cut the useless part)

> **SeijiSensei said:**
> Did the  server's /etc/hosts file get rewritten?

I don't think so. But, since I use bind, this file is not relevant, it isn't ?

```
~$ cat /etc/hosts
127.0.0.1    localhost
127.0.1.1    clement-desktop

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```> **SeijiSensei said:**
> The fact that the server can't  even resolve the IPv6 address for "localhost" is disturbing.

Agree.

Is it helpful ?

---

### Post by pot_roast on 2012-05-02
It's your /etc/hosts file.

Notice that the 12.04 upgrade has added the following lines:

::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

--

If you comment them out, things will work again. I just had this exact same problem, just with Squirrelmail.

---

### Post by clement.analogue on 2012-05-02
It works !
Thank you a lot, pot_roast !!!

---

### Post by sparklyprgs on 2012-05-19
Yes, thanks too pot_roast. I also saw this subtle bug since moving to 12.04. Commenting out those lines worked fine. Who uses IPv6 on small networks anyhow?!? :-)

---

### Post by paulschreiber on 2012-07-19
I had the same problem, and editing /etc/hosts worked around the problem for me.

An alternate fix is to edit main.cf so mynetworks knows about IPv6:
mynetworks = 127.0.0.0/8 [::1]/128

---

### Post by clement.analogue on 2012-09-13
Thanks paulschreiber, it works too. It looks like a better solution for the IPv6 resolution.

---

### Post by james_xxx on 2013-02-15
Just now upgrading a Mailman server to Precise, and this thread bailed me out.

Many Thanks!

---

