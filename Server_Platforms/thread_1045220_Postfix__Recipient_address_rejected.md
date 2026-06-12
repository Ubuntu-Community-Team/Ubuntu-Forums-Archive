---
title: "Postfix:  Recipient address rejected"
date: 2009-01-20
forum: Server Platforms
---

### Post by scruff on 2009-01-20
Hi all. I am developing an email utility for a client and am having some prbs getting postfix working correctly. Customer uses Mac OSX which has postfix available by default so I installed postfix on my machine. When trying to send email from my machine to my personal gmail account I get:

**550 5.1.1 <***@gmail.com>: Recipient address rejected: gmail.com**

It is making me nuts as I've already been all over google. I've also been up all night though so I'm sure I'm missing something stupid. Here is configuration details:

```

root@thinkpad:/etc/postfix# postconf -n
alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
config_directory = /etc/postfix
default_transport = error
inet_interfaces = loopback-only
inet_protocols = all
mailbox_size_limit = 0
mydestination = localhost, mydomain.com
mydomain = mydomain.com
myhostname = mail.mydomain.com
mynetworks = 127.0.0.0/8
myorigin = /etc/mailname
readme_directory = no
recipient_delimiter = +
relay_transport = error
relayhost = 
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_tls_cert_file = /etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file = /etc/ssl/private/ssl-cert-snakeoil.key
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtpd_use_tls = yes

```

Here is some log output (email addys sub'd) in case this is helpful:

tail -n100 /var/log/mail.info | awk -F']' '{ print $2 }' 
```

: >>> CHECKING RECIPIENT MAPS <<<
: ctable_locate: leave existing entry key ****@gmail.com
: maps_find: recipient_canonical_maps: ****@gmail.com: not found
: match_string: gmail.com ~? localhost
: match_string: gmail.com ~? mydomain.com
: match_list_match: gmail.com: no match
: maps_find: recipient_canonical_maps: @gmail.com: not found
: mail_addr_find: ****@gmail.com -> (not found)
: maps_find: canonical_maps: ****@gmail.com: not found
: match_string: gmail.com ~? localhost
: match_string: gmail.com ~? mydomain.com
: match_list_match: gmail.com: no match
: maps_find: canonical_maps: @gmail.com: not found
: mail_addr_find: ****@gmail.com -> (not found)
: maps_find: virtual_alias_maps: ****@gmail.com: not found
: match_string: gmail.com ~? localhost
: match_string: gmail.com ~? mydomain.com
: match_list_match: gmail.com: no match
: maps_find: virtual_alias_maps: @gmail.com: not found
: mail_addr_find: ****@gmail.com -> (not found)
: NOQUEUE: reject: RCPT from localhost[127.0.0.1
: > localhost[127.0.0.1

```

Any advice is appreciated!

---

### Post by volkswagner on 2009-01-20
Comparing your file vs. mine, it appears you are missing mynetwork_style directive.

You should have been asked this by the package config tool.

Here is a portion of my config.

```
mynetworks_style = host
inet_protocols = ipv4
smtpd_sasl_local_domain = 
smtpd_sasl_auth_enable = yes
```

Can you send mail to any outside address?

Do you have a static IP from your ISP?  If you don't gmail and many other hosts will reject the mail.  That of course will be a different error.  To get around this using your ISP's smtp server works a great work around.

---

### Post by hyper_ch on 2009-01-20
gmail would complain about the sender and not recipient email address. Please post the whole log of what gmail complains and also your complete main.cf.

---

### Post by scruff on 2009-01-20
> **volkswagner said:**
> Comparing your file vs. mine, it appears you are missing mynetwork_style directive.

Can you send mail to any outside address?

Do you have a static IP from your ISP?  If you don't gmail and many other hosts will reject the mail.  That of course will be a different error.  To get around this using your ISP's smtp server works a great work around.

No, I can't seem to send mail anywhere. My IP is DHCP provided.

---

### Post by scruff on 2009-01-20
> **hyper_ch said:**
> gmail would complain about the sender and not recipient email address. Please post the whole log of what gmail complains and also your complete main.cf.

Really? My research gave me the impression that postfix was rejecting the address. Here is the info you asked for:

Main.cf:
```

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
mydomain = skstech.com
myhostname = mail.skstechconsulting.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
mydestination = localhost, skstech.com
#relayhost = 
mynetworks = 127.0.0.0/8
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = loopback-only
default_transport = error
relay_transport = error
inet_protocols = all
myorigin = /etc/mailname

```

mail.err with debug cranked up:
```

Jan 20 08:40:20 thinkpad postfix/smtpd[29299]: resolve_clnt: `' -> `****6119@gmail.com' -> transp=`error' host=`gmail.com' rcpt=`****6119@gmail.com' flags= class=default
Jan 20 08:40:20 thinkpad postfix/smtpd[29299]: ctable_locate: install entry key ****6119@gmail.com
Jan 20 08:40:20 thinkpad postfix/smtpd[29299]: extract_addr: in: <****6119@gmail.com>, result: ****6119@gmail.com
Jan 20 08:40:20 thinkpad postfix/smtpd[29299]: send attr request = rewrite
Jan 20 08:40:20 thinkpad postfix/smtpd[29299]: send attr rule = local
Jan 20 08:40:20 thinkpad postfix/smtpd[29299]: send attr address = double-bounce
Jan 20 08:40:20 thinkpad postfix/smtpd[29299]: private/rewrite socket: wanted attribute: flags
Jan 20 08:40:20 thinkpad postfix/smtpd[29299]: input attribute name: flags
Jan 20 08:40:20 thinkpad postfix/smtpd[29299]: input attribute value: 0
Jan 20 08:40:20 thinkpad postfix/smtpd[29299]: private/rewrite socket: wanted attribute: address
Jan 20 08:40:20 thinkpad postfix/smtpd[29299]: input attribute name: address
Jan 20 08:40:20 thinkpad postfix/smtpd[29299]: input attribute value: double-bounce@skstech.com
Jan 20 08:40:20 thinkpad postfix/smtpd[29299]: private/rewrite socket: wanted attribute: (list terminator)
Jan 20 08:40:20 thinkpad postfix/smtpd[29299]: input attribute name: (end)
Jan 20 08:40:20 thinkpad postfix/smtpd[29299]: rewrite_clnt: local: double-bounce -> double-bounce@skstech.com
Jan 20 08:40:20 thinkpad postfix/smtpd[29299]: >>> START Recipient address RESTRICTIONS <<<
Jan 20 08:40:20 thinkpad postfix/smtpd[29299]: generic_checks: name=permit_mynetworks
Jan 20 08:40:20 thinkpad postfix/smtpd[29299]: permit_mynetworks: localhost 127.0.0.1
Jan 20 08:40:20 thinkpad postfix/smtpd[29299]: match_hostname: localhost ~? 127.0.0.0/8
Jan 20 08:40:20 thinkpad postfix/smtpd[29299]: match_hostaddr: 127.0.0.1 ~? 127.0.0.0/8
Jan 20 08:40:20 thinkpad postfix/smtpd[29299]: generic_checks: name=permit_mynetworks status=1
Jan 20 08:40:20 thinkpad postfix/smtpd[29299]: >>> CHECKING RECIPIENT MAPS <<<
Jan 20 08:40:20 thinkpad postfix/smtpd[29299]: ctable_locate: leave existing entry key ****6119@gmail.com
Jan 20 08:40:20 thinkpad postfix/smtpd[29299]: maps_find: recipient_canonical_maps: ****6119@gmail.com: not found
Jan 20 08:40:20 thinkpad postfix/smtpd[29299]: match_string: gmail.com ~? localhost
Jan 20 08:40:20 thinkpad postfix/smtpd[29299]: match_string: gmail.com ~? skstech.com
Jan 20 08:40:20 thinkpad postfix/smtpd[29299]: match_list_match: gmail.com: no match
Jan 20 08:40:20 thinkpad postfix/smtpd[29299]: maps_find: recipient_canonical_maps: @gmail.com: not found
Jan 20 08:40:20 thinkpad postfix/smtpd[29299]: mail_addr_find: ****6119@gmail.com -> (not found)
Jan 20 08:40:20 thinkpad postfix/smtpd[29299]: maps_find: canonical_maps: ****6119@gmail.com: not found
Jan 20 08:40:20 thinkpad postfix/smtpd[29299]: match_string: gmail.com ~? localhost
Jan 20 08:40:20 thinkpad postfix/smtpd[29299]: match_string: gmail.com ~? skstech.com
Jan 20 08:40:20 thinkpad postfix/smtpd[29299]: match_list_match: gmail.com: no match
Jan 20 08:40:20 thinkpad postfix/smtpd[29299]: maps_find: canonical_maps: @gmail.com: not found
Jan 20 08:40:20 thinkpad postfix/smtpd[29299]: mail_addr_find: ****6119@gmail.com -> (not found)
Jan 20 08:40:20 thinkpad postfix/smtpd[29299]: maps_find: virtual_alias_maps: ****6119@gmail.com: not found
Jan 20 08:40:20 thinkpad postfix/smtpd[29299]: match_string: gmail.com ~? localhost
Jan 20 08:40:20 thinkpad postfix/smtpd[29299]: match_string: gmail.com ~? skstech.com
Jan 20 08:40:20 thinkpad postfix/smtpd[29299]: match_list_match: gmail.com: no match
Jan 20 08:40:20 thinkpad postfix/smtpd[29299]: maps_find: virtual_alias_maps: @gmail.com: not found
Jan 20 08:40:20 thinkpad postfix/smtpd[29299]: mail_addr_find: ****6119@gmail.com -> (not found)
Jan 20 08:40:20 thinkpad postfix/smtpd[29299]: NOQUEUE: reject: RCPT from localhost[127.0.0.1]: 550 5.1.1 <****6119@gmail.com>: Recipient address rejected: gmail.com; from=<****@skstechnology.com> to=<****6119@gmail.com> proto=ESMTP helo=<thinkpad>
Jan 20 08:40:20 thinkpad postfix/smtpd[29299]: > localhost[127.0.0.1]: 550 5.1.1 <****6119@gmail.com>: Recipient address rejected: gmail.com
Jan 20 08:40:20 thinkpad postfix/smtpd[29299]: smtp_get: EOF
Jan 20 08:40:20 thinkpad postfix/smtpd[29299]: match_hostname: localhost ~? 127.0.0.0/8
Jan 20 08:40:20 thinkpad postfix/smtpd[29299]: match_hostaddr: 127.0.0.1 ~? 127.0.0.0/8
Jan 20 08:40:20 thinkpad postfix/smtpd[29299]: lost connection after RCPT from localhost[127.0.0.1]
Jan 20 08:40:20 thinkpad postfix/smtpd[29299]: disconnect from localhost[127.0.0.1]
Jan 20 08:40:20 thinkpad postfix/smtpd[29299]: master_notify: status 1
Jan 20 08:40:20 thinkpad postfix/smtpd[29299]: connection closed
Jan 20 08:40:25 thinkpad postfix/smtpd[29299]: proxymap stream disconnect
Jan 20 08:40:25 thinkpad postfix/smtpd[29299]: auto_clnt_close: disconnect private/tlsmgr stream
Jan 20 08:40:25 thinkpad postfix/smtpd[29299]: rewrite stream disconnect
Jan 20 08:42:00 thinkpad postfix/smtpd[29299]: idle timeout -- exiting


```

Thanks for the help!

---

### Post by hyper_ch on 2009-01-20
(1) can you ping gmail.com ?

(2) add this to your main.cf

```

smtp_sasl_auth_enable = yes
smtp_sasl_security_options = noanonymous
smtp_sasl_password_maps = hash:/etc/postfix/saslpasswd
smtp_always_send_ehlo = yes
relayhost = [your_isp_stmp_address]:587

```
If you don't have to specify it, just add it like this:
```

relayhost = [your_isp_smtp_address]:587

```

Then create the file /etc/postfix/saslpasswd and add this:
```

your_isp_smtp_address     your_login:your_password

```
don't add a port there... if the login is a full email address, then use it.

Save and exit the file, then run

```

cd /etc/postfix
sudo postmap saslpasswd

```

and finally restart the server
```

sudo /etc/init.d/postfix restart

```

That should work and you relay the email now through your ISP.

---

### Post by scruff on 2009-01-20
hyper_ch,

I could do that, but isn't that defeating the purpose of a local mail server? It's been a few years since I've personally ran one at home, but back when I did I had no trouble sending mail to gmail. I used to send backups from my webserver to my gmail account on a weekly basis...

---

### Post by hyper_ch on 2009-01-20
not really, you send it to your mail server, the email server is sending it then out relaying through your ISP. All email is still stored... and furthermore the receiving of email is directly done with your server.

Most email servers nowadays won't accept email from servers not on a static IP as email spamming from home computers is quite usual.

---

### Post by scruff on 2009-01-20
I see your point... The client has only moments ago (finally) provided me with the login details to his actual server at the hosting company he uses so I think I may set up an account on it and just have my program authenticate itself there for sending mail. That should eliminate most spam filter issues.

Thanks again.

---

### Post by brunojcm on 2012-04-27
I got the same error several times, and I fixed it commenting the following lines:

#default_transport = error
#relay_transport = error

I was following the instructions here:

[http://serverfault.com/questions/119278/configure-postfix-to-send-relay-emails-gmail-smtp-gmail-com-via-port-587](http://serverfault.com/questions/119278/configure-postfix-to-send-relay-emails-gmail-smtp-gmail-com-via-port-587)

---

