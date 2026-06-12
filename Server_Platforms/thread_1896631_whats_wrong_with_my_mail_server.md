---
title: "whats wrong with my mail server"
date: 2011-12-17
forum: Server Platforms
---

### Post by donsmouse on 2011-12-17
I have signed up with dyn email and have went through the guides, but i still cant send or recieve email externally only internaly
here are my main and master cf files:
 
 
Main CF:
 
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
readme_directory = no
# TLS parameters
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.
myhostname = smousecomputers.dyndns-server.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = $mydomain
mydestination = $myhostname, localhost.$mydomain, $mydomain
smtp_sasl_auth_enable = yes
smtp_sasl_password_maps = hash:/etc/postfix/sasl_passwd
smtp_sasl_security_options = noanonymous
smtp_tls_CAfile = /etc/postfix/cacert.pem
smtp_use_tls = yes
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +

 
Master Cf:
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
smtp      inet  n       -       n       -       -       smtpd
465        inet  n       -       n       -       -       smtpd  
#smtp      inet  n       -       -       -       1       postscreen
#smtpd     pass  -       -       -       -       -       smtpd
#dnsblog   unix  -       -       -       -       0       dnsblog
#tlsproxy  unix  -       -       -       -       0       tlsproxy
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
#628       inet  n       -       -       -       -       qmqpd
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
# ====================================================================
#
# Recent Cyrus versions can use the existing "lmtp" master.cf entry.
#
# Specify in cyrus.conf:
#   lmtp    cmd="lmtpd -a" listen="localhost:lmtp" proto=tcp4
#
# Specify in main.cf one or more of the following:
#  mailbox_transport = lmtp:inet:localhost
#  virtual_transport = lmtp:inet:localhost
#
# ====================================================================
#
# Cyrus 2.1.5 (Amos Gouaux)
# Also specify in main.cf: cyrus_destination_recipient_limit=1
#
#cyrus     unix  -       n       n       -       -       pipe
#  user=cyrus argv=/cyrus/bin/deliver -e -r ${sender} -m ${extension} ${user}
#
# ====================================================================
# Old example of delivery via Cyrus.
#
#old-cyrus unix  -       n       n       -       -       pipe
#  flags=R user=cyrus argv=/cyrus/bin/deliver -e -m ${extension} ${user}
#
# ====================================================================
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
scalemail-backend unix - n n - 2 pipe
  flags=R user=scalemail argv=/usr/lib/scalemail/bin/scalemail-store ${nexthop} ${user} ${extension}
mailman   unix  -       n       n       -       -       pipe
  flags=FR user=list argv=/usr/lib/mailman/bin/postfix-to-mailman.py
  ${nexthop} ${user}
:confused:

---

### Post by HermanAB on 2011-12-17
Does your ISP account allow you to run a mail server?  If not, then they may be blocking port 25 and then your mail server won't work.

---

### Post by donsmouse on 2011-12-17
no they block port 25 thats why i signed up for dyn email
 
here is what they say:
 
**What ports are blocked by XFINITY Internet?**


Comcast is committed to providing a secure internet experience for all of our customers. For the protection of the network and our customers, certain ports are blocked by XFINITY and XFINITY Internet. The blocking of these ports protects against common viruses and worms, malicious intruders, and other security exploits.
[LEFT][LEFT][SIZE=-2]Port [/SIZE]
[SIZE=-2]Transport [/SIZE]
[SIZE=-2]Protocol [/SIZE]
[SIZE=-2]Inbound/ Outbound [/SIZE]
[SIZE=-2]Reason for block [/SIZE]
[SIZE=-2]XFINITY/
Comcast
Internet[/SIZE]
[SIZE=-2]XFINITY/
Comcast
WiFi[/SIZE]
[SIZE=-2]XFINITY
Internet2Go[/SIZE][/LEFT]
[CENTER][SIZE=-1]**25** [/SIZE]
[SIZE=-1]TCP[/SIZE]
[SIZE=-1]SMTP[/SIZE]
[SIZE=-1]Both[/SIZE][/CENTER]
[SIZE=-1]Port 25 is an unsecured port on a computer Botnet spammers can take control of to send spam - often without the user ever knowing his/her computer has been compromised. When spam from a compromised computer is detected, Comcast's anti-spam systems automatically apply a sending block and send an email notification to the affected subscriber's comcast.net email address. This block does not interrupt mail service for Webmail (e.g. Comcast webmail, Yahoo, Gmail, or Hotmail); however, this block does prevent email programs or clients (e.g. Outlook Express) from sending email. Client email programs will still receive email. Email clients should be reconfigured to use port 587, _[view more FAQs]("http://sitesearch.comcast.com/?q=port+587&cat=ccentral")_ to learn about configuring common email client programs. [/SIZE]
[CENTER][SIZE=-1]No. Case by case blocking.[/SIZE][/CENTER]
[SIZE=-1]Yes[/SIZE]
[CENTER][SIZE=-1]No[/SIZE]
[SIZE=-1]**68** [/SIZE]
[SIZE=-1]UDP[/SIZE]
[SIZE=-1]BOOTP, DHCP[/SIZE]
[SIZE=-1]Inbound[/SIZE][/CENTER]
[SIZE=-1]UDP Port 68 is used by customer computers to obtain dynamic Internet Protocol (IP) address information from the Comcast's dynamic host configuration protocol (DHCP) server that assigns IP addresses to customer computers. DHCP ports can be used for malicious attacks such as, for example, obtaining access to a customer's home computer or home network and its devices[/SIZE]
[CENTER][SIZE=-1]Yes[/SIZE]
[SIZE=-1]Yes[/SIZE]
[SIZE=-1]No[/SIZE]
[SIZE=-1]**135-139** [/SIZE]
[SIZE=-1]TCP/UDP[/SIZE]
[SIZE=-1]NetBios[/SIZE]
[SIZE=-1]Both[/SIZE][/CENTER]
[SIZE=-1]NetBios services allow file sharing over networks. When improperly configured, they can expose critical system files or give full file system access (run, delete, copy) to any malicious intruder connected to the network.[/SIZE]
[CENTER][SIZE=-1]Yes[/SIZE]
[SIZE=-1]Yes[/SIZE]
[SIZE=-1]No[/SIZE]
[SIZE=-1]**445** [/SIZE]
[SIZE=-1]TCP[/SIZE]
[SIZE=-1]MS-DS, SMB[/SIZE]
[SIZE=-1]Both[/SIZE][/CENTER]
[SIZE=-1]Security risks; vulnerable to attacks/exploits/worms such as the Sasser and Nimda worms..[/SIZE]
[CENTER][SIZE=-1]Yes[/SIZE]
[SIZE=-1]Yes[/SIZE]
[SIZE=-1]No[/SIZE]
[SIZE=-1]**520** [/SIZE]
[SIZE=-1]TCP/UDP[/SIZE]
[SIZE=-1]RIP[/SIZE]
[SIZE=-1]Both[/SIZE][/CENTER]
[SIZE=-1]Vulnerable to malicious route updates which provides several attack possibilities.[/SIZE]
[CENTER][SIZE=-1]Yes[/SIZE]
[SIZE=-1]Yes[/SIZE]
[SIZE=-1]No[/SIZE]
[SIZE=-1]**1080** [/SIZE]
[SIZE=-1]TCP[/SIZE]
[SIZE=-1]SOCKS[/SIZE]
[SIZE=-1]Inbound[/SIZE][/CENTER]
[SIZE=-1]Multiple vulnerabilities (Viruses, Worms, DoS attacks).[/SIZE]
[CENTER][SIZE=-1]Yes[/SIZE]
[SIZE=-1]Yes[/SIZE]
[SIZE=-1]No[/SIZE][/CENTER]
[/LEFT]

---

### Post by lisati on 2011-12-17
Even if you go through a service such as dyndns or no-ip.com, a block on port 25 by your ISP can still stop your email in its tracks.

One option is to ask your ISP for a static IP and getting them to unblock port 25. The downside is that if they're willing to do so, they might want you to pay for the service. 

Another option is to have people send your email to an email account somewhere else, use fetchmail to retrieve the mail, and relaying outgoing mail through your ISP's server.

---

### Post by donsmouse on 2011-12-17
i don't think they offer this service thats to bad, i really didnt want to relay through gmail
but if i have to how do i set this up?

---

### Post by moonpup on 2011-12-17
I use Dyn as well and to get things to work I paid for their Standard DNS service and for mail functionality I pay for the Dyn email gateway.

The dns handles the name of my mail server and mx records for my domain. The email gateway allows me to receive mail on alternate ports for when port 25 is blocked. Read up on these 2 services from Dyn for all the features and decide if you can justify the cost achieve your goal.

BTW, this setup works flawless for me and I love it.

---

### Post by donsmouse on 2011-12-17
i will buy the package then thank you so much

---

### Post by HermanAB on 2011-12-18
then you need to use the 'smarthost' feature of postfix, called relayhost in postfix speak.

Here is a kezample:
[http://www.jimmy.co.at/weblog/?p=53](http://www.jimmy.co.at/weblog/?p=53)

BTW, if you are seriously doing battle with postfix, then you should save yourself from a lot of grief and go to [www.postfix.org](www.postfix.org) and read the documentation...

---

### Post by donsmouse on 2011-12-18
Thank you so much

---

