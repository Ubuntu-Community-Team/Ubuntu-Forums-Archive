---
title: "Mail Server tutorial for 14.04 isn't quite right, not sure what to do."
date: 2014-08-22
forum: Server Platforms
---

### Post by neltnerb on 2014-08-22
Sorry if this is super easy, I'm not very experienced with running a server.

I'm trying to get a mailserver running on my virtual server, but nothing is quite fitting together right. I have Ubuntu 14.04 installed, and was following this server guide to get it up and running.

[https://help.ubuntu.com/14.04/serverguide/postfix.html](https://help.ubuntu.com/14.04/serverguide/postfix.html)

Before starting, I did
```
apt-get purge postfix dovecot-core
apt-get --purge autoremove
```
in order to get a clean postfix configuration (it somehow has some memory of the last time I configured it, but the /etc/postfix directory is gone).

I've tried doing this using the full version, and also using the mail-stack-delivery version, but neither is quite working.

Using the full version, I get to the end and when I try to test it over telnet it connects for a moment and then reports
```
Escape character is '^]'.
Connection closed by foreign host.
```
The time to close varies from nearly immediate to 10 seconds or so. However, I can't find anything in /var/log/mail.log

I tried purging postfix again, and telnet instead never connects, so I figure postfix must be running but having some error after connection that breaks it.

When I try next to use the mail-stack-delivery option, I *am* able to connect to postfix through telnet as I should, but now ehlo doesn't return the 
```
250-AUTH LOGIN PLAIN
250-AUTH=LOGIN PLAIN
```
lines (it has 250-STARTTLS and 250 8BITMIME).

This is all rather confusing to me. Particularly that there are no log files or error messages indicating what could be happening. Does anyone have an idea for how to diagnose this and get it up and running?

contents of /etc/postfix/main.cf

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

readme_directory = no

# TLS parameters
smtpd_tls_cert_file = /etc/ssl/certs/server.crt
smtpd_tls_key_file = /etc/ssl/private/server.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

smtpd_relay_restrictions = permit_mynetworks permit_sasl_authenticated defer_unauth_destination
myhostname = navolta.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = navolta.com, localhost.localdomain, localhost
relayhost = 
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128 184.106.238.0/24
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = ipv4
smtpd_sasl_type = dovecot
smtpd_sasl_path = private/auth-client
smtpd_sasl_local_domain = 
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_sasl_auth_enable = yes
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
smtp_tls_security_level = may
smtpd_tls_security_level = may
smtp_tls_note_starttls_offer = yes
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes

```

---

### Post by TheFu on 2014-08-22
So - I looked at the DNS stuff - looks fine from here.

The mynetworks line looks incorrect - it is meant for internal IPs, not the public IPs.  It is a best practice NOT to place the real email server on a public network - use an email gateway that does most of the spam filtering/dropping and have it forward to the real email server on the internal network. You'll thank me for this.

If there isn't a connection being made, I would guess that there is a router or firewall blocking port 25 ... or the forwarding isn't working correctly. Can't tell from here.

I assume the certs in the config file are there and for the correct hostname?

Running **postconf -n** will show the actual settings. Helpful.

---

### Post by neltnerb on 2014-08-22
Thanks so much for taking a look!

I'm afraid I don't know what an email gateway is... this is my first time setting up a mail server that's not exclusively used locally. Is that intended to be a separate computer, or something like amavisd-new? I hadn't gotten quite that far in the installation yet.

There is a connection being made, at least when done from the server, it just disconnects rapidly. Fairly confident it isn't a firewall issue.

Would certificates cause the telnet connection on port 25 to drop? I think I did them correctly, but that's certainly a possibility; I haven't gotten far enough to test that.

Probably worth mentioning that I did first try this tutorial for 12.04:

[https://help.ubuntu.com/community/MailServer](https://help.ubuntu.com/community/MailServer)

With that I was able to get all the port 25 stuff working, and even got as far as reading mailboxes with IMAP, but sending mail never worked right so I upgraded to 14.04 and started over with the newer tutorial. There could be residue from that process, although I was pretty thorough with the apt-get purging afterwards.

Output of postconf -n

```
alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
broken_sasl_auth_clients = yes
config_directory = /etc/postfix
inet_interfaces = all
inet_protocols = ipv4
mailbox_size_limit = 0
mydestination = navolta.com, localhost.localdomain, localhost
myhostname = navolta.com
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128 184.106.238.0/24
myorigin = /etc/mailname
readme_directory = no
recipient_delimiter = +
relayhost =
smtp_tls_note_starttls_offer = yes
smtp_tls_security_level = may
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
smtpd_relay_restrictions = permit_mynetworks permit_sasl_authenticated defer_unauth_destination
smtpd_sasl_auth_enable = yes
smtpd_sasl_local_domain =
smtpd_sasl_path = private/auth-client
smtpd_sasl_security_options = noanonymous
smtpd_sasl_type = dovecot
smtpd_tls_cert_file = /etc/ssl/certs/server.crt
smtpd_tls_key_file = /etc/ssl/private/server.key
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_security_level = may
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtpd_use_tls = yes

```

---

### Post by TheFu on 2014-08-23
Going to 14.04 is probably smart at this point.  My main email server is still on 10.04, but we'll move to 12.04 this fall sometime.  The front-end server is on 12.04 - soon to be 14.04.

I tried to connect to your server - if any connection was made, it didn't look right from here. What do the log files show?

---

### Post by neltnerb on 2014-08-23
> **TheFu said:**
> Going to 14.04 is probably smart at this point.  My main email server is still on 10.04, but we'll move to 12.04 this fall sometime.  The front-end server is on 12.04 - soon to be 14.04.

I tried to connect to your server - if any connection was made, it didn't look right from here. What do the log files show?

Nothing whatsoever in the logs. The last message is from yesterday.

```
Aug 22 03:47:32 auth: Warning: Killed with signal 15 (by pid=1 uid=0 code=kill)
Aug 22 03:47:32 master: Warning: Killed with signal 15 (by pid=1 uid=0 code=kill)
Aug 22 03:47:32 ssl-params: Warning: Killed with signal 15 (by pid=1 uid=0 code=kill)
Aug 22 03:47:32 log: Warning: Killed with signal 15 (by pid=1 uid=0 code=kill)
Aug 22 03:47:32 auth-worker: Warning: Killed with signal 15 (by pid=1 uid=0 code=kill)
Aug 22 03:47:32 anvil: Warning: Killed with signal 15 (by pid=1 uid=0 code=kill)
```

which I believe is just from the last time I restarted postfix, though I don't know for sure.

---

### Post by TheFu on 2014-08-23
Every connection should be logged - assuming postfix is listening.
Is it running?  Or did exim get there first and grab the port?
**dpkg -l |grep exim** - you don't want 2 MTAs on a system.

Which log file?  Check the all, please.

---

### Post by neltnerb on 2014-08-23
Thanks for the ideas!

exim was installed, but I had previously disabled it. I purged all of the exim packages to be safe, but the problem with the telnet connection disconnecting after connecting continues.

That was mail.log.

None of the other mail log files (I have .err, .info, .warn) or their .1 versions have anything recent. That includes me successfully connecting via telnet to port 25 from localhost (after which it disconnected).

Perhaps postfix is putting log information elsewhere? Or maybe the verbosity is not high enough?

---

### Post by Doug S on 2014-08-23
Who is listening to port 25? Example:```
doug@doug-64:~$ [COLOR=#ff0000]sudo netstat -tlpn[/COLOR]
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      1423/mysqld
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN      1649/smbd
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      1592/apache2
tcp        0      0 192.168.111.1:53        0.0.0.0:*               LISTEN      1231/named
... deleted one unrelated line ...
tcp        0      0 127.0.0.1:53            0.0.0.0:*               LISTEN      1231/named
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      1090/sshd
[COLOR=#ff0000]tcp        0      0 0.0.0.0:25              0.0.0.0:*               LISTEN      1499/master[/COLOR]
tcp        0      0 127.0.0.1:953           0.0.0.0:*               LISTEN      1231/named
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN      1649/smbd
doug@doug-64:~$ [COLOR=#ff0000]ps aux | grep master[/COLOR]
root      1499  0.0  0.0  25112  1548 ?        Ss   Aug22   0:00 [COLOR=#ff0000]/usr/lib/postfix/master[/COLOR]
doug      4502  0.0  0.0   9388   892 pts/0    S+   09:01   0:00 grep --color=auto master
```When I connect to your server port 25, sometimes it disconnects right away and sometimes I am able to type stuff, but get no reply.

---

### Post by neltnerb on 2014-08-23
Hello Doug, thanks for the idea, I was wondering how to do that.

```
sudo netstat -tlpn
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:8080            0.0.0.0:*               LISTEN      3525/apache2    
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      3303/varnishd   
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      2998/sshd       
tcp        0      0 0.0.0.0:25              0.0.0.0:*               LISTEN      28574/master    
tcp        0      0 127.0.0.1:6082          0.0.0.0:*               LISTEN      3250/varnishd   

```

I'm afraid I don't know quite what to make of that.

---

### Post by neltnerb on 2014-08-25
I'm going to try setting this up again according to the tutorial to see at what step functionality breaks. Here is my report:

Before starting, I apt-get purge dovecot-core and postfix.

_Install Postfix_

```
apt-get install postfix
```
Set FQDN to navolta.com and "Internet Site". Reported warning "newaliases: warning: inet_protocols: disabling IPv6 name/address support: Address family not supported by protocol", but no errors. Similar repeated warnings for postalias, postmulti, and postfix immediately following.

Also reported warnings:
```
Processing triggers for ufw (0.34~rc-0ubuntu2) ...
WARN: Duplicate profile 'Apache', using last found
WARN: Duplicate profile 'Apache Secure', using last found
WARN: Duplicate profile 'Apache Full', using last found

```

Checking functionality:
```
telnet navolta.com 25
Trying 184.106.238.45...
Connected to saikoled.
Escape character is '^]'.
220 saikoled ESMTP Postfix (Ubuntu)
ehlo navolta.com
250-saikoled
250-PIPELINING
250-SIZE 10240000
250-VRFY
250-ETRN
250-STARTTLS
250-ENHANCEDSTATUSCODES
250-8BITMIME
250 DSN

```

_dpkg-reconfigure_

```
dpkg-reconfigure postfix
```
Options:
[LIST]
[*]System Mail name: [COLOR="#FF0000"]navolta.com[/COLOR]
[*]Root and postmaster mail recipient: [COLOR="#FF0000"]user account name[/COLOR]
[*]Other destinations to accept mail for: [COLOR="#FF0000"]navolta.com, localhost.localdomain, localhost[/COLOR]
[*]Force synchronous updates on mail queue?: [COLOR="#FF0000"]No[/COLOR]
[*]Local networks: [COLOR="#FF0000"]127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128 184.106.238.0/24[/COLOR] (Note: this is based on the comment in the tutorial that says to replace "192.168.0.0/24 with the actual network and class range of your mail server")
[*]Mailbox size limit: [COLOR="#FF0000"]0[/COLOR]
[*]Local address extension character: [COLOR="#FF0000"]+[/COLOR]
[*]Internet protocols to use: [COLOR="#FF0000"]ipv4[/COLOR] (changing to this eliminates the ipv6 warnings above).
[/LIST]

After this, output from telnet navolta.com 25 and ehlo navolta.com is unchanged.

_SMTP Configuration_

First I followed the instructions for [creating certificates using the certificate tutorial]("https://help.ubuntu.com/14.04/serverguide/certificates-and-security.html") which puts self-signed certificates into
```
/etc/ssl/certs/server.crt
/etc/ssl/private/server.key
```

Next, I follow the SMTP Authentication section of the tutorial. First it says to configure the following.
```
sudo postconf -e 'smtpd_sasl_type = dovecot'
sudo postconf -e 'smtpd_sasl_path = private/auth-client'
sudo postconf -e 'smtpd_sasl_local_domain ='
sudo postconf -e 'smtpd_sasl_security_options = noanonymous'
sudo postconf -e 'broken_sasl_auth_clients = yes'
sudo postconf -e 'smtpd_sasl_auth_enable = yes'
sudo postconf -e 'smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination'

```
and then it says to continue with the following, adjusted for my server.
```
sudo postconf -e 'smtp_tls_security_level = may'
sudo postconf -e 'smtpd_tls_security_level = may'
sudo postconf -e 'smtp_tls_note_starttls_offer = yes'
sudo postconf -e 'smtpd_tls_key_file = /etc/ssl/private/server.key'
sudo postconf -e 'smtpd_tls_cert_file = /etc/ssl/certs/server.crt'
sudo postconf -e 'smtpd_tls_loglevel = 1'
sudo postconf -e 'smtpd_tls_received_header = yes'
sudo postconf -e 'myhostname = navolta.com'
```

At this point, the /etc/postfix.main.cf file looks like this:
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

readme_directory = no

# TLS parameters
smtpd_tls_cert_file = /etc/ssl/certs/server.crt
smtpd_tls_key_file = /etc/ssl/private/server.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

smtpd_relay_restrictions = permit_mynetworks permit_sasl_authenticated defer_unauth_destination
myhostname = navolta.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = navolta.com, localhost.localdomain, localhost
relayhost = 
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128 184.106.238.0/24
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = ipv4
smtpd_sasl_type = dovecot
smtpd_sasl_path = private/auth-client
smtpd_sasl_local_domain = 
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_sasl_auth_enable = yes
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
smtp_tls_security_level = may
smtpd_tls_security_level = may
smtp_tls_note_starttls_offer = yes
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes

```
which is significantly different than what the tutorial says it should be, but I chalk it up to slight version differences.

[COLOR="#FF0000"]At this stage, connecting to the server via telnet navolta.com 25 causes the error seen before regarding the connection being established and then nearly immediately closing with no log messages.[/COLOR]

Comparing the instructions in the [14.04 Mail Server Guide]("https://help.ubuntu.com/14.04/serverguide/postfix.html") to the [Community Guide to Postfix]("https://help.ubuntu.com/community/Postfix") has some differences. For one, the official guide clearly has a typo on the smtpd_recipient_restrictions line, the backslash is not allowed in that command. 

In particular, the official guide has the following commands missing from the community guide for the first set of commands:
```
sudo postconf -e 'smtpd_sasl_type = dovecot'
sudo postconf -e 'smtpd_sasl_path = private/auth-client'
```
while the community guide has the added line
```
sudo postconf -e 'inet_interfaces = all'
```
with the explanation that the prior is to authenticate using SASL while the latter authenticates using Dovecot SASL.

The community guide then also instructs to edit /etc/postfix/sasl/smtpd.conf and add:
```
pwcheck_method: saslauthd
mech_list: plain login
```
which in the official guide instead says to only set the mech_list in ```
/etc/dovecot/conf.d/10-auth.conf
```.

The community guide also instructs to generate certificates for smtpd specifically, whereas the official documentation only mentions the main certificates:
```
touch smtpd.key
chmod 600 smtpd.key
openssl genrsa 1024 > smtpd.key
openssl req -new -key smtpd.key -x509 -days 3650 -out smtpd.crt # has prompts
openssl req -new -x509 -extensions v3_ca -keyout cakey.pem -out cacert.pem -days 3650 # has prompts
sudo mv smtpd.key /etc/ssl/private/
sudo mv smtpd.crt /etc/ssl/certs/
sudo mv cakey.pem /etc/ssl/private/
sudo mv cacert.pem /etc/ssl/certs/
```

The community guide instructions for the second set of commands is slightly changed from the official instructions, with the added lines:
```

sudo postconf -e 'smtpd_tls_auth_only = no'
sudo postconf -e 'smtpd_tls_key_file = /etc/ssl/private/smtpd.key'
sudo postconf -e 'smtpd_tls_cert_file = /etc/ssl/certs/smtpd.crt'
sudo postconf -e 'smtpd_tls_CAfile = /etc/ssl/certs/cacert.pem'
sudo postconf -e 'smtpd_tls_session_cache_timeout = 3600s'
sudo postconf -e 'tls_random_source = dev:/dev/urandom'
```
for which I assume the three certificate path changes are due to the production of the extra certificates.

In the interest of confirming the error, I removed these two lines from main.cf
```
sudo postconf -e 'smtpd_sasl_type = dovecot'
sudo postconf -e 'smtpd_sasl_path = private/auth-client'
```
I created the file /etc/postfix/sasl/smtpd.conf to have:
```
pwcheck_method: saslauthd
mech_list: plain login
```
and I made the permissions on the certificates root:website instead of root:root while removing o-r privileges to match the snakeoil certificate in the directory. I also added
```
smtpd_tls_CAfile = /etc/ssl/certs/cacert.pem
```
to match my CA certificate, which wasn't included before. I also ran
```
sudo service saslauthd start
```
to ensure that saslauthd was actually running.

After doing these changes, the server works again with telnet, showing:
```
telnet navolta.com 25
Trying 184.106.238.45...
Connected to saikoled.
Escape character is '^]'.
220 navolta.com ESMTP Postfix (Ubuntu)
ehlo navolta.com
250-navolta.com
250-PIPELINING
250-SIZE 10240000
250-VRFY
250-ETRN
250-STARTTLS
250-AUTH PLAIN LOGIN
250-AUTH=PLAIN LOGIN
250-ENHANCEDSTATUSCODES
250-8BITMIME
250 DSN

```
but I do not understand entirely why. It could have been the change in authentication service, or the change in permissions on the certificates. To narrow this down, I stopped the saslauthd service and verified that the telnet command still works. I next reset the ownership on the /etc/ssl/private/server.key and /etc/ssl/certs/server.crt to root:root and the telnet command still works.

Next, I re-executed the command:
```
sudo postconf -e 'smtpd_sasl_path = private/auth-client'
```
and now when I run the telnet check, it gives me:
```
telnet navolta.com 25Trying 184.106.238.45...
Connected to saikoled.
Escape character is '^]'.
220 navolta.com ESMTP Postfix (Ubuntu)

500 5.5.2 Error: bad syntax
ehlo navolta.com
250-navolta.com
250-PIPELINING
250-SIZE 10240000
250-VRFY
250-ETRN
250-STARTTLS
250-AUTH DIGEST-MD5 NTLM CRAM-MD5 PLAIN LOGIN
250-AUTH=DIGEST-MD5 NTLM CRAM-MD5 PLAIN LOGIN
250-ENHANCEDSTATUSCODES
250-8BITMIME
250 DSN

```
which is a slight change in that it now appears to allow additional authentication methods.

Finally, adding back in the command
```
sudo postconf -e 'smtpd_sasl_type = dovecot'
```
finally breaks the server. Now when I telnet back in I see the server disconnect.

So, I think I can guess with fair certainty that the issue is the "smtpd_sasl_type = dovecot" directive.

Upon reviewing the postfix documentation, I typed postconf -a to ensure that dovecot SASL is supported in the version of postfix I am using. It appears to be supported. I also noted in the documentation that dovecot SASL needs to be installed, which it possibly isn't. I ran 
```
apt-get install dovecot-core
```
to install dovecot. I note that this is different from the official guide which says I need to install dovecot-common. apt-get installed dovecot-core instead, so I assume this is a drop in replacement but this could be incorrect. An apt-cache search did not show any other obvious packages that look like a separated out SASL package.

At this point, I'm not entirely sure what the issue is, but it seems to involve the use of dovecot SASL. More information than this I am not sure how to collect.

---

### Post by neltnerb on 2014-08-25
I should further note that with this configuration, I am able to send mail through the telnet prompt.

```
telnet navolta.com 25
Trying 184.106.238.45...
Connected to saikoled.
Escape character is '^]'.
220 navolta.com ESMTP Postfix (Ubuntu)
HELO navolta.com
250 navolta.com
MAIL FROM: neltnerb@navolta.com
250 2.1.0 Ok
RCPT TO: neltnerb@mit.edu
250 2.1.5 Ok
DATA
354 End data with <CR><LF>.<CR><LF>
SUBJECT: test
test
.
250 2.0.0 Ok: queued as B8E7410C072

```
and this results in an email arriving in my inbox at [email]neltnerb@mit.edu[/email]. I am a little concerned that sending mail via the relay did not seem to actually require SASL authentication.

I should also note that telnet into navolta.com on port 25 from my other computer does not successfully connect. I am not sure if this is correct.

I checked the firewall, and running sudo ufw status gives:
```
WARN: Duplicate profile 'Apache', using last found
WARN: Duplicate profile 'Apache Secure', using last found
WARN: Duplicate profile 'Apache Full', using last found
ERROR: problem running iptables: modprobe: ERROR: ../libkmod/libkmod-index.c:821 index_mm_open() magic check fail: b007fa57 instead of b007f457
modprobe: ERROR: ../libkmod/libkmod.c:556 kmod_search_moddep() could not open moddep file '/lib/modules/2.6.35.4-rscloud/modules.dep.bin'
iptables v1.4.21: can't initialize iptables table `filter': Table does not exist (do you need to insmod?)
Perhaps iptables or your kernel needs to be upgraded.

```
which it did [COLOR="#FF0000"]not[/COLOR] say previously when using ufw in Ubuntu 12.04. I do not understand the nature of this error message. I will create a separate post about this behavior in ufw.

---

### Post by TheFu on 2014-08-25
I didn't re-read everything above, but something is jumping out at me.
The FQDN is normally system.domain.com - mail.example.com.  The MX record is used to tell other SMTP servers which host to send email at.  Don't know if it matters, but thought I'd mention it.

Why would sending email need authentication if the client is on MyNetworks?  

The iptables error seems to say that the kernel doesn't have it loaded. That is probably bad on an internet facing server of any sort. Having a firewall that can restrict the bad-servers out there is important - even if just to slow down their connections.  I realize this isn't helpful at this time.

Oh - and the reason I'm not just posting my config for you to copy - I have a front-end server that receives all email, then forwards to to a Zimbra server.  There are multiple domains involved with backup mail servers - things are complicated here.  I haven't used dovecot/courier-imap in about 8 yrs.

There is a good set of tutorials at howtoforge.com - that might be helpful.  Just know that working doesn't mean secured too. That is still your responsibility.

---

### Post by neltnerb on 2014-08-25
Thanks TheFu for your suggestion!

I am tracking down the possibility that the iptables issue is due to rackspace not having a current kernel running on the virtual server. It seems they automatically load the kernel from the host machine instead of the virtual machine, and since it only happened after I upgraded from 12.04 to 14.04, I suspect that the new version of iptables may be looking for a different version of the kernel module.

If I can get the ability to telnet into the machine on port 25 remotely, hopefully I will be unable to send email through telnet, but connect to it. Hopefully update shortly, rackspace tech support may have more information specific to their virtual servers that I don't know yet.

---

### Post by TheFu on 2014-08-25
Please re-read my last post - updated - however, I'd assumed the server was on a network you controlled, not at a remote hosting provider.  I've actually never run a full email server on someone else's network - just forwarding servers.

So about the iptables stuff - you need to know if the instance is Xen paravirtual or not. If it is, you can only run kernels they provide and only load modules they provide.  LXC or Docker has similar limitations - not so good when control over the network is needed. I know that rackspace can support full KVM VMs (they are a huge openstack shop; see them at the openstack meetings here), but don't know which you are on. 
The invoice should clearly say what you have - HVM or container or paravirtual or ... ? 

If you can telnet to port 25 - then use any client to send email.  I'd definitely want authentication mandatory or your domain will be marked as a spammer (open relay) very quickly and become useless.

---

### Post by nerdtron on 2014-08-25
I'm I late on suggesting an email server?

We used this on a production environment and is working very well. Complete with postfix, dovecot, amavisd, spamassassin with fail2ban and iptables. Up and running in less than 15 minutes and with very minimal configuration. I can't promote it well enough. It's worth a shot, just install it on a FRESH Ubuntu server (no extra packages installed).
[http://iredmail.org/install_iredmail_on_ubuntu.html](http://iredmail.org/install_iredmail_on_ubuntu.html)

---

### Post by neltnerb on 2014-08-25
Thanks nerdtron, that looks like a great solution... I've already got apache2 running several sites though, so it's not really a fresh server. It's actually been upgraded from 10.04 over the years. I'd definitely like to avoid reinstalling from scratch since I don't want to end up having to fix the webserver too :-D

---

### Post by Doug S on 2014-08-25
> **neltnerb said:**
> For one, the official guide clearly has a typo on the smtpd_recipient_restrictions line, the backslash is not allowed in that command. The backslash is supposed to mean to continue the command on the next line.> **neltnerb said:**
> So, I think I can guess with fair certainty that the issue is the "smtpd_sasl_type = dovecot" directive.For sure that is the difference between our two setups. I didn't do the SMTP Auth stuff, and I assume that if you do the tcp session is expecting some cypher exchange packets immediately after the connection is established and you would not get that with a telnet session.

It would be good to update the serverguide (which I can help with) as needed as and as result of your investigation.

---

### Post by neltnerb on 2014-08-25
I think at this point I'm going to try to switch things over to just using the google apps toolkit. Alas, this is just taking too much attention and I've got too many other things to take care of.

With regards to the "typo", yes, I realize that's what the backslash means. However, the command doesn't allow multi-line input, so the guide should have the whole command on one line so people copy/pasting will not run into trouble.

Before deciding that this is probably just too far beyond my level to be able to do securely and reliably, I was able to send emails locally through telnet as well as receive emails, so it might actually have been working once I got the iptables issue worked out. I'm going to try to figure that one out anyway since my firewall should be, well, operational regardless of whether it's running a mailserver, but I'll track that in the separate thread since it's not directly related to the original problem anymore.

I definitely think that the documentation needs a refresh; I'm no linux expert, but I have been using it regularly for over a decade and I wasn't able to get it to work. It's possible that it's related to having gone the upgrade route (10.04 to 12.04 to 14.04) instead of a fresh install, and it could also easily be related to the virtual hosting from rackspace having an outdated kernel. However, either way I think that some of the information is no longer accurate.

The most obvious one is that in the section "SMTP Authentication" it claims that the /etc/postfix/main.cf file should look a certain way. After executing those commands on a fresh postfix install, the file does not look that way. This is confusing, and would be good to update.

It might also be simpler to actually just have users start by installing mail-stack-delivery, and then provide guidance on modifying that seemingly pretty good basic configuration.

---

