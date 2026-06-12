---
title: "Post fix can´t receive outside emails"
date: 2015-04-27
forum: Server Platforms
---

### Post by rhandy2 on 2015-04-27
Hello

First of all, I pass hours reading and reading.

I found this thread, and I try everything.

[http://ubuntuforums.org/showthread.php?t=2176051&page=2](http://ubuntuforums.org/showthread.php?t=2176051&page=2)

Yesterday I have postfix configured with Virtualmin, I dont receive outside emails, but I forget open ports in router, after that this morning I have all emails, I realy dont know if I change anything, because I´m trying to adjust some postfix config, I enable Dovecot, I have some error in permissions, I add "mail" group in dovecot config.

First ports are open

NMAP

> Discovered open port 25/tcp on XXX.XXX.XXX.XXX 
Discovered open port 143/tcp on XXX.XXX.XXX.XXX 
Discovered open port 995/tcp on XXX.XXX.XXX.XXX 
Discovered open port 80/tcp on XXX.XXX.XXX.XXX 
Discovered open port 110/tcp on XXX.XXX.XXX.XXX

TELNET MYDOMAIN.COM 25
> Escape character is '^]'.
220 MYDOMAIN.COM ESMTP Postfix (Ubuntu)


DIG MX 

> 
;; ANSWER SECTION:
mydomain.gq.           38400   IN      MX      5 mail.mydomain.com.
;; AUTHORITY SECTION:
mydomain.com.           38400   IN      NS      ns01.mydomain.com
mydomain.com           38400   IN      NS      ns02.mydomain.com
;; ADDITIONAL SECTION:
mail.mydomain.com.      38400   IN      A       XXX.XXX.XXX.XXX
ns01.mydomain.com     38400   IN      A       XXX.XXX.XXX.XXX
ns02.mydomain.com     38400   IN      A       XXX.XXX.XXX.XXX
;; Query time: 0 msec
;; SERVER: 127.0.0.1#53(127.0.0.1)
;; WHEN: Mon Apr 27 16:40:43 WEST 2015
;; MSG SIZE  rcvd: 161



Its a litle office server and is running under NAT and Dynamic IP.

I use internal DNS SERVER BIND9.

I realy don´t know, what I can make more. 

I dont have logs for incoming emails?

I try to see in /var/log/mail.log and /var/log/mail.err

---

### Post by TheFu on 2015-04-27
To get email from the world, a few things are mandatory.
a) Registrar with a domain that you know
b) Public DNS that can be accessed by anyone in the world to connect their SMTP server to yours using a public IP
c) MX DNS record at the same Public DNS server - that's 2 or 3 DNS records - A, CNAME, MX (usually)
d) Internet provider who allows (i.e. does not block) SMTP traffic on port 25/tcp
e) SMTP daemon listening on port 25 (called an MTA) which can receive SMTP from the public IP that the MX record correlates with.
f) any firewall issues removed for the public IP on port 25/tcp.

Perhaps I missed it, but it reads to me like you have an internal DNS, but haven't necessarily setup the public DNS.

```
Registrar --> public DNS --> ServerIP
```

Hope that is clear.  It appears to me that you've probably connected the dots correctly already.  However, testing the telnet connection from "inside" doesn't prove that the ISP allows SMTP connections from outside. 

**userid@mydomain.gq** is the email address space you want to use? I don't see the MX record for [email]userid@mydomain.com[/email] - could that be the issue?

The dynamic IP will be an issue. Most other email servers will not accept email from dynamic subnets - spam comes from those places.  Also, you probably want the DNS update period to be shorter 5-15 minutes, so when the IP does change, you aren't stuck waiting .... about 10 hrs for other systems to update the DNS cache for the domain.

Are ```

mydomain.com 38400 IN NS ns02.mydomain.com
```
missing trailing dots?
```

mydomain.com. 38400 IN NS ns02.mydomain.com.
```

---

### Post by rhandy2 on 2015-04-27
Hello TheFu

One strange thing happens! I receive emails this morning but I´m not receiving now.

 I have 3 free domains registered of freenom. for testing.

I put 1 of them on AFRAID.  only with ns01.domain1.tk IN A xxx.xxx.xxx.xxx ( my dinamic ip) and ns02.domain1.tk xxx.xxx.xxx.xxx my internal ip for both.
And I PUT NAME SERVER ON REGISTRAR WITH MY NS.01.DOMAIN.TK FOR Other 2 domains. 

yesterday it works. Today I only receive emails for my first domain registered and added on AFRAID. 

Note: I don´t have any MX record on Afraid. Only on my internal DNS.

I know I could not register my DNS to public, because if IP change I Can´t Dynamic  (UPTADE)change on Registrar. oR IF i COULD i JUST DON´T KNOW.

Thanks

---

### Post by TheFu on 2015-04-27
I don't understand "AFRAID" - is that an ISP?

You can have either a daemon monitor your public IP and update a dynamic DNS service provider or many home routers have support for the most popular dynamicDNS providers.

Without an MX record on the public IP+DNS record, nobody can send you email. It is that simple. My email servers will never accept any email from your server because it is in a DHCP address range. That is a very common setting -perhaps 90% of internet mail servers do this. Sorry.

If you just want systems under your control do send/receive email with a central server, the MX record is less important - you'll just want to configure 1 as the main MTA and all the others as "satellite" MTA systems.

Assuming I understand what you are attempting to do.

---

### Post by rhandy2 on 2015-04-27
TheFu

AFRAID is free dynamic dns server. [http://freedns.afraid.org](http://freedns.afraid.org), like [www.no-ip.com]("http://www.no-ip.com")
I`m trying to have my personal server for my webhost and mail.

> you'll just want to configure 1 as the main MTA and all the others as "satellite" MTA systems
Could you be more specifc please, I dont have many experience, just have  a litle formation on Linux Network.

---

### Post by rhandy2 on 2015-04-27
Oh!!! my God!!! I can´t beleive ! I pass 10 hours! And I Forget to Open Again Port #53 Router! 
Bad Bad Bad Day !!!

---

### Post by TheFu on 2015-04-27
> **rhandy2 said:**
> Could you be more specifc please, I dont have many experience, just have  a litle formation on Linux Network.

Postfix is my MTA of choice. I install it on every server I run as a satellite (this is a question during the install of the package). A satellite system will not accept any email, but locally originated emails will be forwarded to the main email server for the domain - assuming the config forwards emails to the main email server for the domain. 

Then you pick one server to be the main email box - it needs the MX record and needs to allow the "satellite" boxes to send email - all email will be sent there regardless of where it is going either internal OR external. The only hard part is of the satellite server(s) don't have static IPs.  Mine are all on the same LAN segment or come from static internet IPs that we can specify as "trusted" in the main email server postfix config file.

It all sounds more complex than it is.

Are you sure you want to run a DNS server that is available on the internet?  I've been hacked twice - once was DNS back in 2002. It was ugly. $30/yr removes that risk and it is easier to pay professionals to run DNS (which is still commonly hacked) than to do it myself.  Sure, I run an internal-only DNS for the company, but not for external use.  There are many subtle things to running a secure DNS server - like only having secondary servers on the internet, keep the master off the internet!  I'll look for DNS best practices ... couldn't find the thread I'd hoped. Sorry.

---

### Post by rhandy2 on 2015-04-28
TheFu, Many Thanks for all!!

You said > Are you sure you want to run a DNS server that is available on the internet?  I've been hacked twice - once was DNS back in 2002. It was ugly. $30/yr removes that risk and it is easier to pay professionals
$30 is in AFRAID.com???

Now i´m having another strange problem, maybe you can help me.
**_I can login to DOVECOT pop3_, but not on POSTFIX **

I see this tutorial [https://help.ubuntu.com/community/PostfixDovecotSASL](https://help.ubuntu.com/community/PostfixDovecotSASL)


MASTER.CF
> 
#a
# Postfix master process configuration file.  For details on the format
# of the file, see the master(5) manual page (command: "man 5 master" or
# on-line: [http://www.postfix.org/master.5.html](http://www.postfix.org/master.5.html)).
#
# Do not forget to execute "postfix reload" after editing this file.
#
# ==========================================================================
# service type  private unpriv  chroot  wakeup  maxproc command + args
#               (yes)   (yes)   (yes)   (never) (100)
# ==========================================================================
smtp      inet  n       -       -       -       -       smtpd
#smtp      inet  n       -       -       -       1       postscreen
#smtpd     pass  -       -       -       -       -       smtpd
#dnsblog   unix  -       -       -       -       0       dnsblog
#tlsproxy  unix  -       -       -       -       0       tlsproxy
submission inet n       -       -       -       -       smtpd
#  -o syslog_name=postfix/submission
#  -o smtpd_tls_security_level=encryp
   -o smtpd_sasl_auth_enable=yes
   -o smtpd_client_restrictions=permit_sasl_authenticated,reject
#  -o smtpd_reject_unlisted_recipient=no
#  -o smtpd_client_restrictions=$mua_client_restrictions
#  -o smtpd_helo_restrictions=$mua_helo_restrictions
#  -o smtpd_sender_restrictions=$mua_sender_restrictions
#  -o smtpd_recipient_restrictions=
#  -o smtpd_relay_restrictions=permit_sasl_authenticated,reject
#  -o milter_macro_daemon_name=ORIGINATING
#smtps  inet  n       -       -       -       -       smtpd
#  -o syslog_name=postfix/smtps
#  -o smtpd_tls_wrappermode=yes
#  -o smtpd_sasl_auth_enable=yes
#  -o smtpd_reject_unlisted_recipient=no
#  -o smtpd_client_restrictions=$mua_client_restrictions
#  -o smtpd_helo_restrictions=$mua_helo_restrictions
#  -o smtpd_sender_restrictions=$mua_sender_restrictions
#  -o smtpd_recipient_restrictions=
#  -o smtpd_relay_restrictions=permit_sasl_authenticated,reject
#  -o milter_macro_daemon_name=ORIGINATING
#628       inet  n       -       -       -       -       qmqpd
pickup    unix  n       -       -       60      1       pickup
cleanup   unix  n       -       -       -       0       cleanup
qmgr      unix  n       -       n       300     1       qmgr
#qmgr     unix  n       -       n       300     1       oqmgr
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








POSTFIX MAIN.CF
> # See /usr/share/postfix/main.cf.dist for a commented, more complete version

# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
#myorigin = /etc/mailname
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no
# appending .domain is the MUA's job.
# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h
readme_directory = no
# TLS parameters
smtpd_tls_cert_file = /etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file = /etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.
smtpd_relay_restrictions = permit_mynetworks permit_sasl_authenticated defer_unauth_destination
myhostname = 5starhost.tk
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = mysmtpdomainserver.tld, localhost.localdomain, localhost
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_protocols = all
virtual_alias_maps = hash:/etc/postfix/virtual
sender_dependent_default_transport_maps = hash:/etc/postfix/dependent
smtpd_sasl_path = /var/spool/postfix/private/auth-client
allow_percent_hack = no
smtpd_sasl_auth_enable = yes
smtpd_tls_auth_only = yes
smtpd_sasl_security_options = noanonymous noplaintext
smtpd_recipient_restrictions = permit_sasl_authenticated permit_mx_backup permit_mynetworks permit_inet_interfaces



Telnet does not show > [250-AUTH PLAIN LOGIN/QUOTE]
[QUOTE]


Last login: Tue Apr 28 11:25:08 2015 from 192.168.10.5
nuno@xxxxxxxxxx:~$ telnet localhost 25
Trying ::1...
Connected to localhost.
Escape character is '^]'.
220 mysmtpdomainserver.tld ESMTP Postfix (Ubuntu)
ehlo localhost
250-mysmtpdomainserver.tld
250-PIPELINING
250-SIZE 10240000
250-VRFY
250-ETRN
250-STARTTLS
250-ENHANCEDSTATUSCODES
250-8BITMIME
250 DSN

[QUOTE]
ls -al /var/spool/postfix/var/run/saslauthd
total 976
drwx--x--- 2 root sasl   4096 Abr 28 16:22 .
drwxr-xr-x 3 root root   4096 Abr 28 16:20 ..
-rw------- 1 root root      0 Abr 28 16:22 cache.flock
-rw------- 1 root root 986112 Abr 28 16:22 cache.mmap
srwxrwxrwx 1 root root      0 Abr 28 16:22 mux
-rw------- 1 root root      0 Abr 28 16:22 mux.accept
-rw------- 1 root root      6 Abr 28 16:22 saslauthd.pid



[/QUOTE]

Log
>  postfix/smtpd[3898]: message repeated 2 times: [ warning: 111.111.111.111.rev.xxxxxx.zz[111.111.111.111]: SASL CRAM-MD5 authentication failed: authentication failure]


NOTE i´m using virtual domains created by VIRTUALMIN and users use ----  [EMAIL="name@domain.tld"]name@domain.tld[/EMAIL] and password for autentication

---

### Post by rhandy2 on 2015-04-28
SOLVED AFTER read this [http://xmodulo.com/enable-user-authentication-postfix-smtp-server-sasl.html](http://xmodulo.com/enable-user-authentication-postfix-smtp-server-sasl.html) , make changes to config files and change PERMISSIONS on /var/spool/postfix/private/auth -  because postfix dont have permissions.

RETURNING TO DNS QUESTION

You said 
                            > Are you sure you want to run a DNS server that is available on the internet?  I've been hacked twice - once was DNS back in 2002. It was ugly. $30/yr removes that risk and it is easier to pay professionals                    


**$30 is in AFRAID.com???**

---

### Post by rhandy2 on 2015-04-28
[FONT=arial black][B][COLOR=#000000]I have duplicated permissions

 smtpd_client_restrictions=permit_sasl_authenticate  d,reject -  in master.cf and  in main.cf - - this disallow outcomig emails.

I remove from master.cf, and its working now[/COLOR][/B][/FONT]

---

### Post by rhandy2 on 2015-05-02
Hello

I realy don´t know what´s wrong, I have everythig working good, I don´t know what I do wrong, I have all email bounced.
I replace all config files from one "working" backup configurations and I still have same error!
[B]
PROCMAIL BOUNCE ALL EMAILS, INCLUDE INTERNAL EMAIL.[/B]

Hello

I realy don´t know what´s wrong, I have everythig working good, I don´t know what I do wrong, I have all email bounced.
I replace all config files from one "working" backup configurations and I still have same error!
[B]
PROCMAIL BOUNCE ALL EMAILS, INCLUDE INTERNAL EMAIL.[/B]

> May  2 15:12:13 example.com postfix/pickup[12117]: 25CAE1E1227: uid=0 from=<[EMAIL="nuno2@example.com"]nuno2@example.com[/EMAIL]>
May  2 15:12:13 example.com postfix/cleanup[12296]: 25CAE1E1227: message-id=<[EMAIL="1430575933.12269@example.com"]1430575933.12269@example.com[/EMAIL]>
May  2 15:12:13 example.com postfix/qmgr[12118]: 25CAE1E1227: from=<[EMAIL="nuno2@example.com"]nuno2@example.com[/EMAIL]>, size=589, nrcpt=1 (queue active)
May  2 15:12:13 example.com postfix/local[12298]: 25CAE1E1227: to=<[EMAIL="nuno-example.com@example.com"]nuno-example.com@example.com[/EMAIL]>, orig_to=<[EMAIL="nuno@example.com"]nuno@example.com[/EMAIL]>, relay=local, delay=0.13, delays=0.08/0/0/0.05, dsn=5.3.0, status=bounced (Command died with status 126: "procmail -a "$EXTENSION"". Command output: sh: 1: procmail: Permission denied )
May  2 15:12:13 example.com postfix/cleanup[12296]: 3BF6E1E17A0: message-id=<[EMAIL="20150502141213.3BF6E1E17A0@example.com"]20150502141213.3BF6E1E17A0@example.com[/EMAIL]>
May  2 15:12:13 example.com postfix/bounce[12301]: 25CAE1E1227: sender non-delivery notification: 3BF6E1E17A0
May  2 15:12:13 example.com postfix/qmgr[12118]: 3BF6E1E17A0: from=<>, size=2510, nrcpt=1 (queue active)
May  2 15:12:13 example.com postfix/qmgr[12118]: 25CAE1E1227: removed
May  2 15:12:13 example.com postfix/local[12298]: 3BF6E1E17A0: to=<[EMAIL="nuno2-example.com@example.com"]nuno2-example.com@example.com[/EMAIL]>, orig_to=<[EMAIL="nuno2@example.com"]nuno2@example.com[/EMAIL]>, relay=local, delay=0.08, delays=0.04/0/0/0.03, dsn=5.3.0, status=bounced (Command died with status 126: "procmail -a "$EXTENSION"". Command output: sh: 1: procmail: Permission denied )
May  2 15:12:13 example.com postfix/qmgr[12118]: 3BF6E1E17A0: removed

---

