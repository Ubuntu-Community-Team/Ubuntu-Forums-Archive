---
title: "mails from gmail/.../etc not arriving to my postfix"
date: 2010-02-16
forum: Server Platforms
---

### Post by michalb82 on 2010-02-16
Hi,

1.
 I have Ubutnu 9.10 with latest updates.
 I have a server on foo-domain.com with IP 123.123.123.123 (just for this post example reference).

2. 
 I have setup my postfix as said in here:
 [https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix)

3. 
 My ISB blocks port 25 so I enabled 587 (see attached configuration below post).

4. 
When I login to my server (via SSH) I can send emails from one user to another without a problem (mail user2@localhost < /dev/null)

5. 
From outside my server (another network) I cannot telnet to port 25 since ISP in Poland block port 25, when I telnet to 587 I get 220 code from postfix (so everything is OK).

6. 
I have in domain registrator DNS MX records setup:
```

Pref    Hostname    IP Address    TTL        
10    foo-domain.com    123.123.123.123    60 min

```7. PROBLEMS:
When I send mail from gmail or whatever to [EMAIL="user2@foo-domain.com"]user2@foo-domain.com[/EMAIL] I dont recive that mail. The postfix logs show no connection attempts. Gmail shows no info of sending mail failure.

configuration:
```
root@wb-server-u804lts:~/tmp# cat /etc/postfix/master.cf 
#
# Postfix master process configuration file.  For details on the format
# of the file, see the master(5) manual page (command: "man 5 master").
#
# Do not forget to execute "postfix reload" after editing this file.
#
# ==========================================================================
# service type  private unpriv  chroot  wakeup  maxproc command + args
#               (yes)   (yes)   (yes)   (never) (100)
# ==========================================================================
smtp      inet  n       -       -       -       -       smtpd
#submission inet n       -       n       -       -       smtpd
#  -o smtpd_sasl_auth_enable=yes
#  -o milter_macro_daemon_name=ORIGINATING
#  -o smtpd_client_restrictions=
#  -o smtpd_helo_restrictions=
#  -o smtpd_sender_restrictions=reject_sender_login_mismatch,permit
#  -o receive_override_options=no_header_body_checks,no_address_mappings
#  -o smtpd_sender_restrictions=permit_sasl_authenticated,reject
#  -o smtpd_recipient_restrictions=reject_non_fqdn_recipient,reject_unknown_recipient_domain,permit_sasl_authenticated,reject
submission inet n       -       -       -       -       smtpd
  -o smtpd_tls_security_level=encrypt
  -o smtpd_sasl_auth_enable=yes
  -o smtpd_client_restrictions=permit_sasl_authenticated,reject
  -o milter_macro_daemon_name=ORIGINATING
smtps     inet  n       -       -       -       -       smtpd
  -o smtpd_tls_wrappermode=yes
  -o smtpd_sasl_auth_enable=yes
  -o smtpd_client_restrictions=permit_sasl_authenticated,reject
  -o milter_macro_daemon_name=ORIGINATING
#628      inet  n       -       -       -       -       qmqpd
pickup    fifo  n       -       -       60      1       pickup
cleanup   unix  n       -       -       -       0       cleanup
qmgr      fifo  n       -       n       300     1       qmgr
#qmgr     fifo  n       -       -       300     1       oqmgr
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
# When relaying mail as backup MX, disable fallback_relay to avoid MX loops
relay     unix  -       -       -       -       -       smtp
    -o smtp_fallback_relay=
#       -o smtp_helo_timeout=5 -o smtp_connect_timeout=5
showq     unix  n       -       -       -       -       showq
error     unix  -       -       -       -       -       error
retry     unix  -       -       -       -       -       error
discard   unix  -       -       -       -       -       discard
local     unix  -       n       n       -       -       local
virtual   unix  -       n       n       -       -       virtual
lmtp      unix  -       -       -       -       -       lmtp
anvil     unix  -       -       -       -       1       anvil
scache    unix  -       -       -       -       1       scache
#
# ====================================================================
# Interfaces to non-Postfix software. Be sure to examine the manual
# pages of the non-Postfix software to find out what options it wants.
#
# Many of the following services use the Postfix pipe(8) delivery
# agent.  See the pipe(8) man page for information about ${recipient}
# and other message envelope options.
# ====================================================================
#
# maildrop. See the Postfix MAILDROP_README file for details.
# Also specify in main.cf: maildrop_destination_recipient_limit=1
#
maildrop  unix  -       n       n       -       -       pipe
  flags=DRhu user=vmail argv=/usr/bin/maildrop -d ${recipient}
#
# See the Postfix UUCP_README file for configuration details.
#
uucp      unix  -       n       n       -       -       pipe
  flags=Fqhu user=uucp argv=uux -r -n -z -a$sender - $nexthop!rmail ($recipient)
#
# Other external delivery methods.
#
ifmail    unix  -       n       n       -       -       pipe
  flags=F user=ftn argv=/usr/lib/ifmail/ifmail -r $nexthop ($recipient)
bsmtp     unix  -       n       n       -       -       pipe
  flags=Fq. user=bsmtp argv=/usr/lib/bsmtp/bsmtp -t$nexthop -f$sender $recipient
scalemail-backend unix    -    n    n    -    2    pipe
  flags=R user=scalemail argv=/usr/lib/scalemail/bin/scalemail-store ${nexthop} ${user} ${extension}
mailman   unix  -       n       n       -       -       pipe
  flags=FR user=list argv=/usr/lib/mailman/bin/postfix-to-mailman.py
  ${nexthop} ${user}

```What do I check now? How to debug this more? Any help appreciated :)

EDIT:
I just recived Gmail notify:
```

(...)
Technical details of temporary failure:
The recipient server did not accept our requests to connect. Learn more at http://mail.google.com/support/bin/answer.py?answer=7720
[foo-domain.com. (10): Connection timed out]
(...)

```So the MX record is wrong?

---

### Post by cdenley on 2010-02-16
How do you expect gmail to know what port your mail server is listening on? It must accept connections on port 25.

---

### Post by michalb82 on 2010-02-17
> **cdenley said:**
> How do you expect gmail to know what port your mail server is listening on? It must accept connections on port 25.

Thanks for the reply! :)

I donk't know how does this work, but 25 is blocked in whole Poland by the ISPs, so how does that work with other servers? Shouldn't Gmial fallback to 587 when 25 is not open by default? Is that to be configured in the DNS MX records?

---

### Post by cdenley on 2010-02-17
> **michalb82 said:**
> Thanks for the reply! :)

I donk't know how does this work, but 25 is blocked in whole Poland by the ISPs, so how does that work with other servers? Shouldn't Gmial fallback to 587 when 25 is not open by default? Is that to be configured in the DNS MX records?

No. SMTP only relays messages between servers on port 25, as far as I know. There is nothing in an MX record to specify what port to use.

---

### Post by JSeymour on 2010-02-17
> **michalb82 said:**
> I donk't know how does this work, but 25 is blocked in whole Poland by the ISPs,
Well then, I guess nobody in Poland is going to receive email from anybody else in the world.  (In reality: One suspects it's non-business *residential* subscribers for whom port 25 is blocked, which is as it should be, IMO.)

> **michalb82 said:**
> so how does that work with other servers? Shouldn't Gmial fallback to 587 when 25 is not open by default? Is that to be configured in the DNS MX records?No and no.  SMTP happens between MTAs on port 25.  There is no "fallback port."

Btw: TCP port 587 is technically the "submission" port.  Tho it does speak "SMTP," it's really designed for message *submission*, not *message transfer*.  (Ref: RFC 2476).  There's also TCP port 465, SMTPS: SMTP over SSL.  (Contrary to what some say, that port is SSL, not TLS.)

JIm

---

### Post by Porter200el on 2010-02-17
> **JSeymour said:**
> 
No and no.  SMTP happens between MTAs on port 25.  There is no "fallback port."

Btw: TCP port 587 is technically the "submission" port.  Tho it does speak "SMTP," it's really designed for message *submission*, not *message transfer*.  (Ref: RFC 2476).  There's also TCP port 465, SMTPS: SMTP over SSL.  (Contrary to what some say, that port is SSL, not TLS.)

JIm


Jim is correct, plus is says in the documentation:

**Using Port 587 for Secure Submission**

 If you want to use port 587 as the submission port for SMTP mail rather than 25 (many ISPs block port 25), you will need to edit /etc/postfix/master.cf to uncomment the relevant line for port 587 there. 

Hope it helps!

---

### Post by mbehamin on 2010-02-19
most ISPs who banned the port 25, provide the rely service for their client. you should ask them to use their smtp even for your mail sending and receiving

---

