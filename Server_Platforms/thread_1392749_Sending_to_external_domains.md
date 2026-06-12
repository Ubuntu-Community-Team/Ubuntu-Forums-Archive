---
title: "Sending to external domains"
date: 2010-01-28
forum: Server Platforms
---

### Post by kusumoto on 2010-01-28
I've done a lot of searching on this and can't seem to find a straight answer. It seems like it should be such a simple answer to such a simple question.

I have a working dovecot/postfix mysql server on karmic.
It can receive mail from any domain, but only send mail to it's own domain.

How do I allow postfix to send to an external domain?

---

### Post by dalitso on 2010-01-28
Relay your mail to your ISP's smtp server.

```
nano /etc/postfix/main.cf
```

find the line that says
relayhost =

and put the smtp server of your ISP

realayhost = smtp.isp.com (replace smtp.isp.com with your ISP's smtp server)

Then save your configuration (ctrl + O) "y" for yes to save
and exit (ctrl + X)

---

### Post by kusumoto on 2010-01-28
This is an external server with a registered domain on the internet.
Shouldn't I be able to send to other domains without relaying through someone elses smtp server?

I have a working MX record in our primary DNS server that points to this server.

---

### Post by dalitso on 2010-01-29
In that case, yes. You should be able to send mail without a relay server. Sorry, I assumed you are using a dynamic ip address.

I believe posting your /etc/postfix/main.cf and your email log file and errors that are sent to a user sending the mail might be helpful. I have only been using ubuntu server for a year now, so if not me, then others will find the above helpful in helping you out sorting the problem.

---

### Post by lisati on 2010-01-29
To get my server sending and receiving emails externally, I had to:
[LIST=1]
[*]Set up forwarding of port 25 on my router
[*]Ask my ISP to unblock port 25 (they block port 25 by default)
[*]Arrange for a static IP address with my ISP before the port 25 stuff took effect (which wasn't mentioned on their page about port 25 filtering, it was on their page about static IPs, d'oh!)
[/LIST]

Apart from the above, I use a fairly standard installation, with a bit of spam filtering I've added in via header checks and body checks.

(My email server has only been active a few days, there are still a few tweaks I need to do. Might be interesting to compare notes.)

---

### Post by kusumoto on 2010-01-29
I have it set up like that. I know the ISP doesn't block 25. 25 is open on my router. I have an MX record to this server in my primary DNS server. 
I get this error when I try to send to a domain  other than the one hosted on this server (it's also a web server).

*An error occurred while sending mail. The mail server responded:  5.7.1 <furiousmonkeyman@hotmail.com>: Relay access denied. Please check the message recipient [email]furiousmonkeyman@hotmail.com[/email] and try again.*

Here's my main.cf file.

[I]# See /usr/share/postfix/main.cf.dist for a commented, more complete version


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
#smtpd_tls_cert_file = /etc/ssl/certs/ssl-mail.pem
#smtpd_tls_key_file = /etc/ssl/private/ssl-mail.key
#smtpd_use_tls = yes
#smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
#smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = mail.baldtel.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = localhost 
relayhost = 
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
#home_mailbox = Maildir/
#smtpd_sasl_auth_enable = yes
#smtpd_sasl_type = dovecot
#smtpd_sasl_path = private/dovecot-auth
#smtpd_sasl_authenticated_header = yes
#smtpd_sasl_security_options = noanonymous
#smtpd_sasl_local_domain = $myhostname
#broken_sasl_auth_clients = yes
#smtpd_recipient_restrictions = reject_unknown_sender_domain, reject_unknown_recipient_domain, reject_unauth_pipelining, permit_mynetworks, permit_sasl_authenticated, reject_unauth_destination
#smtpd_sender_restrictions = reject_unknown_sender_domain
#mailbox_command = /usr/lib/dovecot/deliver -c /etc/dovecot/dovecot-postfix.conf -n -m "${EXTENSION}"
#smtp_use_tls = yes
#smtpd_tls_received_header = yes
#smtpd_tls_mandatory_protocols = SSLv3, TLSv1
#smtpd_tls_mandatory_ciphers = medium
#smtpd_tls_auth_only = yes
#tls_random_source = dev:/dev/urandom

virtual_minimum_uid = 150
virtual_uid_maps = static:150
virtual_gid_maps = static:8
virtual_mailbox_base = /var/vmail
virtual_transport = dovecot
dovecot_destination_recipient_limit = 1

virtual_alias_maps = proxy:mysql:/etc/postfix/my_alias_maps.cf
virtual_mailbox_limit = proxy:mysql:/etc/postfix/my_mailbox_limits.cf
virtual_mailbox_domains = proxy:mysql:/etc/postfix/my_domains_maps.cf
virtual_mailbox_maps = proxy:mysql:/etc/postfix/my_mailbox_maps.cf

[/I]

I don't recall setting up any DNS on this server though.
I have an MX and A record on the DNS server this one uses in resolv.conf, but nothing on this server.
Could that be a problem?
It looks like it's trying to use a relay host.
I need to make it stop trying to do that.

---

### Post by ICEB3AR on 2010-01-29
Did you set up a reverse DNS entry? 

Maybe the other MTA tries to check if the ip really belongs to the domain which you assigned yourself. Postfix does this e.g. and didn't get an answer so he didn't transfer the message

---

### Post by dalitso on 2010-01-29
If you are sending these emails using another PC on your network via imap or pop then I suggest you specify a range of IP address for your LAN.

You do that in your postfix/main.cf
on the line 

mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128

if am not mistaken it should look like this:

mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128 192.168.1.0/24

Replace 192.168.1.0 with your IP range on your LAN

---

### Post by kusumoto on 2010-01-29
> **dalitso said:**
> If you are sending these emails using another PC on your network via imap or pop then I suggest you specify a range of IP address for your LAN.

You do that in your postfix/main.cf
on the line 

mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128

if am not mistaken it should look like this:

mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128 192.168.1.0/24

Replace 192.168.1.0 with your IP range on your LAN

I tried this and I still get a relay access denied message when I try sending.

---

### Post by kusumoto on 2010-01-29
I commented out *relayhost =* in my main.cf and it always gives the relay access denied message.
How can I make it stop trying to use a relay host?
I just want to send mail directly to the internet.

---

### Post by dalitso on 2010-01-30
> **ICEB3AR said:**
> Did you set up a reverse DNS entry? 

Maybe the other MTA tries to check if the ip really belongs to the domain which you assigned yourself. Postfix does this e.g. and didn't get an answer so he didn't transfer the message

So your server is also running DNS and all the DNS records are set (forward and reverse)? DNS port forwarded to your server on your router?

---

### Post by kusumoto on 2010-02-01
The mail server isn't running a DNS server on it. There are DNS records pointing to this server from our primary DNS server though.
Do I need to also host DNS on this server?

---

### Post by dalitso on 2010-02-01
Well, am not an expert on this, but am sure with a setup like yours, you do not need to host DNS on this mail server. The records pointing to it should do fine.

I have never setup up a mail server with a static/public IP address before. Mine uses dynamic IP and I relay mail to another smtp server.

Like ICEB3AR suggests, it should be a matter of failure to resolve the domain to the IP address. Did you setup this mail server using commands or you have a control panel like webmin or ISPconfig? 
Such programs help in setting up alot of stuff and makes it easy to setup DNS. All you need to type in is a domain name and all the DNS records will be setup appropriately.

---

### Post by kusumoto on 2010-02-01
I set up the mail server using commands. I did not configure the DNS server. It is hosted by someone else. I can use the mail server externally by name, so I would think the DNS records are working.
Whenever I try to send to another domain I get the error "Relay access denied."
I have nothing set in the relayhost field in my main.cf and even have it commented out. I need this message to stop.
It seems to me that the issue is that the server doesn't even try to send messages to the internet.

---

### Post by dalitso on 2010-02-01
Can I send you a PM?

---

### Post by kusumoto on 2010-02-01
Yeah, any help would be great.

---

### Post by kusumoto on 2010-02-01
I now have functional DNS on the mail server as well as the secondary nameserver of the mail server.

I still get a relay access denied error when trying to send to anything but the domain the server hosts.

---

### Post by kusumoto on 2010-02-10
Any ideas on why it might be still trying to use relay?

---

