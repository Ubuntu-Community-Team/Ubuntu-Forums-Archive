---
title: "Is my postfix secure?"
date: 2007-08-13
forum: Server Platforms
---

### Post by maxbear on 2007-08-13
I am running postfix on my server. This server is used by me only Here is what I want to do for this server:

1. Receive email: I want to receive emails for some of my virtual domains host in this server

2. Check mail: I check email by using  a web client which install in the server

3. Send mail: I send email by using a web client which install in the server.

4. Don't want to let any remote user to send email through my server.

Here is my config:

alias_database 	 hash:/etc/aliases
mynetworks_style 	 host
myorigin 	$mydomain
inet_interfaces 	all
mail_owner 	postfix
mydestination 	$myhostname, localhost.$mydomain, localhost
mydomain 	example.com
myhostname 	mail.example.com
queue_directory 	/var/spool/postfix
setgid_group 	postdrop
unknown_local_recipient_reject_code 	550
virtual_alias_domains 	 somevirtualdomains.com
virtual_alias_maps 	hash:/etc/postfix/virtual

Is my server secure enough? Can people spam email through my server?

I see people suggest to use smtp auth or pop before smtp to increase the security, Do you think it's necessary to do so in my case? Thanks a lot.

---

### Post by Mr. C. on 2007-08-14
There is not enough data to know if your server is secure; your question is too broad and unspecific.

Show output of postconf -n (which shows changes from default values).

By default, your postfix mail server will not allow outsiders to relay mail through your server.

If you only send mail via web client, there is no reason to use SMTP AUTH.  Don't bother with pop before SMTP.  Just be sure your web client is secure.

MrC

---

### Post by maxbear on 2007-08-14
Thanks a lot. Here are the values:

alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
command_directory = /usr/sbin
config_directory = /etc/postfix
daemon_directory = /usr/libexec/postfix
debug_peer_level = 2
html_directory = no
inet_interfaces = all
mail_owner = postfix
mailq_path = /usr/bin/mailq.postfix
manpage_directory = /usr/share/man
mydestination = $myhostname, localhost.$mydomain, localhost
mydomain = example.com
myhostname = mail.example.com
mynetworks_style = host
myorigin = $mydomain
newaliases_path = /usr/bin/newaliases.postfix
queue_directory = /var/spool/postfix
readme_directory = /usr/share/doc/postfix-2.2.10/README_FILES
sample_directory = /usr/share/doc/postfix-2.2.10/samples
sendmail_path = /usr/sbin/sendmail.postfix
setgid_group = postdrop
smtpd_recipient_restrictions = permit_sasl_authenticated, permit_mynetworks, reect_unauth_destination
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
unknown_local_recipient_reject_code = 550
virtual_alias_domains = example1.com example2.com example3.com
virtual_alias_maps = hash:/etc/postfix/virtual

---

### Post by maxbear on 2007-08-14
I just want to know can remote user use my smpt to spam email to other hosts? I don't want my mail server open relay. As far as I remember, postfix only allow smpt to trust network only.

Is it good to use the following option?

# Allow connections from trusted networks only.
smtpd_client_restrictions = permit_mynetworks, reject

---

### Post by Mr. C. on 2007-08-14
Your postfix install is only trusting mynetworks and mynetworks_style=host, so it only trusts those hosts.  You'll have to look at postconf -d | grep mynetworks to see the actual default value.

Only  those hosts listed in mynetworks (and any SASL authenticated hosts) can use your mail server as a relay.

You don't need to add those values to smtpd_client_restrictions, as your smtpd_recipient_restrictions already has the values you need, and you have smtpd_delay_reject = yes, which allows later smtpd_*_restrictions to be used.

MrC

---

### Post by maxbear on 2007-08-14
Thanks a lot :-)

---

### Post by ocdude on 2007-08-20
sorry for thread-jacking, but I'm having a similar issue. I think someone is using my box as an smtp relay...here's the output of my postfix -n:
```

alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
broken_sasl_auth_clients = yes
config_directory = /etc/postfix
inet_interfaces = all
inet_protocols = all
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
mydestination = /etc/postfix/local-host-names, mydomain.org
myhostname = mydomain.org
mynetworks = 127.0.0.0/8
myorigin = /etc/mailname
recipient_delimiter = +
relayhost = 
smtp_tls_note_starttls_offer = yes
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache
smtp_use_tls = yes
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination,reject_rbl_client zen.spamhaus.org
smtpd_sasl_auth_enable = yes
smtpd_sasl_local_domain = 
smtpd_sasl_security_options = noanonymous
smtpd_tls_CAfile = /etc/postfix/ssl/cacert.pem
smtpd_tls_cert_file = /etc/postfix/ssl/smtpd.crt
smtpd_tls_key_file = /etc/postfix/ssl/smtpd.key
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtpd_tls_session_cache_timeout = 3600s
smtpd_use_tls = yes
tls_random_source = dev:/dev/urandom

```

---

### Post by Mr. C. on 2007-08-20
Not likely given that configuration.  Why do you believe your server is being used as a relay ?  Show evidence.

MrC

---

### Post by ocdude on 2007-08-20
Well, I'm getting about 30 to 40 bounce back e-mails a day whose headers say they originated on my box...:confused:

However, the headers do not have my box's IP address, only domain name. It could also be that someone is spoofing my domain as well.

---

### Post by Mr. C. on 2007-08-20
I asked for evidence so that I could explain to you how to interpret.  Without evidence, we can only guess.

Show a sample from your mail log.

MrC

---

### Post by ocdude on 2007-08-20
from the mail log:
```
Aug 20 20:28:20 donquixote postfix/smtpd[19922]: connect from i07m-89-86-66-74.d4.club-internet.fr[89.86.66.74]
Aug 20 20:28:21 donquixote postfix/smtpd[19922]: 27D6D2F6C3F: client=i07m-89-86-66-74.d4.club-internet.fr[89.86.66.74]

```

Now, I know that none of the people that have access to the server to send would send to that domain, nor would any legitimate mail in be coming from there.

---

### Post by Mr. C. on 2007-08-20
The entire set of log lines for the transaction is required to diagnose.

Those two lines tell you a client connected, but that's normal for an MX.  This doesn't indicate a relay problem.

The remainder of the log lines for that transaction will indicate who the recipient is.  If the recipient is for one of your domains, then by definition, mail is not being relayed through your server (since it is the final destination).  If the recipient is not in one of your domains, and postfix relays the message to some other unauthorized MTA, then you can start worrying.

MrC

---

