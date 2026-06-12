---
title: "postfix Deferred Issue"
date: 2010-03-19
forum: Server Platforms
---

### Post by pcrumm on 2010-03-19
Hello,

I've managed to get postfix/dovecot working, however I am now experiencing a slightly different issue. The server appears to accept the messages, however mail.log displays ```
Mar 20 00:19:49 (SERVER NAME) postfix/error[15849]: D02C6C252: to=<(ADDRESS)@comcast.net>, relay=none, delay=393, delays=393/0.03/0/0.01, dsn=4.3.0, status=deferred (mail transport unavailable)

```and the message is not delivered. Below is my master.cf and main.cf. Any ideas?
master.cf: ```
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
#submission inet n       -       -       -       -       smtpd
#  -o smtpd_tls_security_level=encrypt
#  -o smtpd_sasl_auth_enable=yes
#  -o smtpd_client_restrictions=permit_sasl_authenticated,reject
#  -o milter_macro_daemon_name=ORIGINATING
#smtps     inet  n       -       -       -       -       smtpd
#  -o smtpd_tls_wrappermode=yes
#  -o smtpd_sasl_auth_enable=yes
#  -o smtpd_client_restrictions=permit_sasl_authenticated,reject
#  -o milter_macro_daemon_name=ORIGINATING
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
#smtp      unix  -       -       -       -       -       smtp
45678	inet 	n	-	-	-	-	smtpd -v	
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
scalemail-backend unix	-	n	n	-	2	pipe
  flags=R user=scalemail argv=/usr/lib/scalemail/bin/scalemail-store ${nexthop} ${user} ${extension}
mailman   unix  -       n       n       -       -       pipe
  flags=FR user=list argv=/usr/lib/mailman/bin/postfix-to-mailman.py
  ${nexthop} ${user}

```
main.cf (postconf -n)
```
broken_sasl_auth_clients = yes
config_directory = /etc/postfix
inet_interfaces = all
inet_protocols = ipv4
mailbox_size_limit = 0
mydestination = wolfire.net, localhost, localhost.localdomain
myhostname = wolfire.net
mynetworks = 127.0.0.0/8
myorigin = /etc/mailname
recipient_delimiter = +
relayhost = 
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
smtpd_sasl_auth_enable = yes
smtpd_sasl_authenticated_header = yes
smtpd_sasl_path = private/auth-client
smtpd_sasl_type = dovecot

```

---

### Post by jrssystemsnet on 2010-03-19
Does the server have outbound port 25 access?

Test by shelling into the server and doing this:

```
you@box:~$ telnet mx1.comcast.net 25
```

If Comcast's MX does not answer and give you a banner, then that's your problem right there.

Note that if you are on a residential network, you may be firewalled off by your ISP from doing ANY connections to outbound port 25, and even if you are not, pretty much nobody is going to be willing to talk to you anyway (because they will recognize your IP as residential).

In either of the above cases, the answer is to use the **relayhost** directive to relay all outbound mail through your ISP's outbound server.

---

### Post by pcrumm on 2010-03-19
Yes, it seems to be working fine. I'm actually running the server on a Slicehost slice and am using SMTP on an alternate port (45678) though I am keeping the server on port 25 running for legacy reasons for the time being. That being said, there was an interesting result of that
```
root@wolfire:/etc/postfix# telnet mx1.comcast.net 25
Trying 76.96.62.116...
Connected to mx1.comcast.net.
Escape character is '^]'.
554 imta07.westchester.pa.mail.comcast.net comcast 173.203.194.210 found on one or more DNSBLs, see http://help.comcast.net/content/faq/BL000001
Connection closed by foreign host.

```

---

### Post by jrssystemsnet on 2010-03-19
> **pcrumm said:**
> ```
root@wolfire:/etc/postfix# telnet mx1.comcast.net 25
Trying 76.96.62.116...
Connected to mx1.comcast.net.
Escape character is '^]'.
554 imta07.westchester.pa.mail.comcast.net comcast 173.203.194.210 found on one or more DNSBLs, see http://help.comcast.net/content/faq/BL000001
Connection closed by foreign host.

```I am not positive, but I believe getting 554'ed before you even HELO will result in Postfix thinking there is no transport available.  You may not have a lot of luck getting many places to accept mail from Slicehost, for hopefully obvious reasons.

Hit up the multi-RBL checker at robtex.org and see if your IP is on any of the public RBLs as well as Comcast's private one; if so, you're going to have to get that cleared up before you can ever get mail delivered anywhere else anyway.

---

### Post by jrssystemsnet on 2010-03-19
> **pcrumm said:**
> using SMTP on an alternate port (45678)

Incidentally, this is completely irrelevant - your concern is delivery elsewhere, which means you're concerned with you contacting destination port 25.  Period.

What ports you're *listening* on have nothing to do with it. :)

---

### Post by pcrumm on 2010-03-19
> **jrssystemsnet said:**
> Incidentally, this is completely irrelevant - your concern is delivery elsewhere, which means you're concerned with you contacting destination port 25.  Period.

What ports you're *listening* on have nothing to do with it. :)
I did not imply that it was relevant, I simply stated it as an aside in order to ensure that it was clear if necessary. ;)

I've gone ahead and done a few DNSBL checks and it appears the only one it's listed on is Spamhaus' opt-out PBL -- I've filed a removal request from that so will try again shortly after it's had some time to propagate.

---

### Post by pcrumm on 2010-03-19
It looks as if the restriction has been removed given I can now telnet Comcast's server. That being said, it appears that the issue persists. Ideas?

---

### Post by jrssystemsnet on 2010-03-19
You commented out the smtp entry in master.cf:

> ```
#smtp      unix  -       -       -       -       -       smtp

```

No smtp entry in master.cf == no smtp transport == deferral == I think you owe me an internet. :)

---

### Post by pcrumm on 2010-03-19
> **jrssystemsnet said:**
> You commented out the smtp entry in master.cf:



No smtp entry in master.cf == no smtp transport == deferral == I think you owe me an internet. :)

You are a god amongst men. Many thanks :P

---

