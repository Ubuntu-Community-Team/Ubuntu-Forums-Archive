---
title: "Sending Mail From Multiple domains"
date: 2010-04-06
forum: Server Platforms
---

### Post by fortune2008 on 2010-04-06
I would like to how can i configure my server to send mails from about ten different domains i use google apps and want to know if its possible. Because it sends mail but all goes to spam and i have a static ip

---

### Post by dudumomo on 2010-04-06
Can you explain us a bit your configuration?

---

### Post by fortune2008 on 2010-04-06
The congfig i use is [Here]("http://www.marksanborn.net/linux/send-mail-postfix-through-gmails-smtp-on-a-ubuntu-lts-server/") but this only send mail from one account i want to send from my accounts and domains this should be possible. I did it before on windows using stunnel and fake php sendmail [old config]("http://www.projectpier.org/node/817")

---

### Post by cdenley on 2010-04-06
```

echo -e "Subject: test\n\ntest"|sendmail **-f sender@example.com** recipient@whatever.com

```

---

### Post by fortune2008 on 2010-04-06
I want to configure it so i can send from all my websites that use different scripts

---

### Post by cdenley on 2010-04-06
> **fortune2008 said:**
> I want to configure it so i can send from all my websites that use different scripts

Shouldn't be a problem. What kind of scripts?

---

### Post by mbehamin on 2010-04-06
Hi 
if you send the mails and it goes into Spam folder of gmail (or other public mail server), your mail server works properly and send your email from many domains. 
but mostly mail server redirect the mail from unregistered mail server into spam. therefore i highly recommend you to register your ip address as a MX record of all your domain with a reverse zone :) 

the other reason is more complex and it may that your ip address is registered as a spammer! it happens because you have not blocked other spammers to use your server as a mail server! just tail your mailq and check how many email are sent by your mail server if too many, you are faced with a problem. 
for preventing other to missus of your mail server i recommend you to look my blog becuase its too long story :) 
[http://blog.mehdibehamin.com/?p=80](http://blog.mehdibehamin.com/?p=80)

regards

---

### Post by fortune2008 on 2010-04-07
ok well my server isn't registered as a mail server because i use google's server to send mail so are saying i should install my own mail server so i i install my own and fix the dns good everything will work good.

---

### Post by lisati on 2010-04-07
> **mbehamin said:**
> 
the other reason is more complex and it may that your ip address is registered as a spammer! it happens because you have not blocked other spammers to use your server as a mail server! just tail your mailq and check how many email are sent by your mail server if too many, you are faced with a problem. 
for preventing other to missus of your mail server i recommend you to look my blog becuase its too long story :) 
[http://blog.mehdibehamin.com/?p=80](http://blog.mehdibehamin.com/?p=80)


Good point about possibly being registered as a spammer - the information in your blog will be useful for people setting things up to avoid their system being misused by those "rascals".

I sometimes use the following websites to check that I haven't been reported as a spammer myself, and to learn about suspect incoming emails:

[http://www.blacklistalert.org/](http://www.blacklistalert.org/)
[http://www.debouncer.com/](http://www.debouncer.com/)
[http://whatismyipaddress.com/](http://whatismyipaddress.com/) (there is a "blacklist check" option)

---

### Post by fortune2008 on 2010-04-07
here what i'm going to do disable the google apps and set up my own mail server on the webserver i'm going to use a guide from howto forge

---

### Post by fortune2008 on 2010-04-07
by the way my ip isn't not blacklisted i checked

---

### Post by lisati on 2010-04-07
> **fortune2008 said:**
> here what i'm going to do disable the google apps and set up my own mail server on the webserver i'm going to use a guide from howto forge

Cool! Before you begin and end up frustrated when a perfectly configured email server that doesn't seem to be working, it might be a good idea to find out if your ISP blocks port 25, as this can affect some of your configuration choices.

Feel free to ask questions - there are others besides myself on the forum who have successfully installed email servers.

---

### Post by fortune2008 on 2010-04-07
nope with my isp i'm free to do what i want thats in the agreement :P is that cool or what

---

### Post by fortune2008 on 2010-04-07
or i want to make things easy one my side i want to manage a few accounts or example it will have like 30-40 different email address from all my domain but i would like to manage like all the admin emails from all the admin accounts forward to one admin box and so on for the rest how can i do that

---

### Post by lisati on 2010-04-07
> **fortune2008 said:**
> or i want to make things easy one my side i want to manage a few accounts or example it will have like 30-40 different email address from all my domain but i would like to manage like all the admin emails from all the admin accounts forward to one admin box and so on for the rest how can i do that

I have Postfix on my server as my MTA. Email forwarding is possible. On my server I created a user for each email address that I wanted to have (the email address is <username>@<mydomain>). Each user has a folder in /home. In the home folder of the user, I can create a file named ".forward", without the quotes, a simple text file that contains the intended destination email address.

---

### Post by fortune2008 on 2010-04-07
I'm Getting and error 

```
[COLOR=#cc0000]**ERROR:**[/COLOR]** ERROR: Connection dropped by IMAP server.**
 
```

The guide i used is [Here]("http://www.howtoforge.com/virtual-users-domains-postfix-courier-mysql-squirrelmail-ubuntu-9.10")

---

### Post by fortune2008 on 2010-04-07
Or i also came across another problem the smtp server isnt work when i telnet is just shows ```
Trying ::1...
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.

```

---

### Post by fortune2008 on 2010-04-07
the smtp responded with this error [CODE]502 5.5.2 Error: command not recognized

421 4.4.2 mail.chatalker.com Error: timeout exceeded
/CODE]

---

### Post by fortune2008 on 2010-04-07
This The code i added on to my main.cf ```
myhostname = mail.chatalker.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = mail.chatalker.com, localhost, localhost.localdomain
relayhost = 
mynetworks = 127.0.0.0/8
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
## TLS Settings
#
smtp_tls_CAfile = /etc/postfix/cacert.pem
smtp_tls_cert_file = /etc/postfix/FOO-cert.pem
smtp_tls_key_file = /etc/postfix/FOO-key.pem
smtp_tls_session_cache_database = btree:/var/run/smtp_tls_session_cache
smtp_use_tls = yes
smtpd_tls_CAfile = /etc/postfix/cacert.pem
smtpd_tls_cert_file = /etc/postfix/smtpd.cert
smtpd_tls_key_file = /etc/postfix/smtpd.key
smtpd_tls_received_header = yes
smtpd_tls_session_cache_database = btree:/var/run/smtpd_tls_session_cache
smtpd_use_tls = yes
tls_random_source = dev:/dev/urandom
#
## SASL Settings
# This is going in to THIS server
smtpd_sasl_auth_enable = yes
# We need this
smtp_sasl_auth_enable = yes
smtp_sasl_password_maps = hash:/etc/postfix/sasl_passwd
smtpd_sasl_local_domain = $myhostname
smtp_sasl_security_options = noanonymous
#smtp_sasl_security_options =
smtp_sasl_tls_security_options = noanonymous
smtpd_sasl_application_name = smtpdhtml_directory = /usr/share/doc/postfix/html
inet_protocols = ipv4
virtual_alias_domains = 
virtual_alias_maps = proxy:mysql:/etc/postfix/mysql-virtual_forwardings.cf, mysql:/etc/postfix/mysql-virtual_email2email.cf
virtual_mailbox_domains = proxy:mysql:/etc/postfix/mysql-virtual_domains.cf
virtual_mailbox_maps = proxy:mysql:/etc/postfix/mysql-virtual_mailboxes.cf
virtual_mailbox_base = /home/vmail
virtual_uid_maps = static:5000
virtual_gid_maps = static:5000
broken_sasl_auth_clients = yes
smtpd_sasl_authenticated_header = yes
smtpd_recipient_restrictions = permit_mynetworks, permit_sasl_authenticated, reject_unauth_destination
transport_maps = proxy:mysql:/etc/postfix/mysql-virtual_transports.cf
virtual_create_maildirsize = yes
virtual_maildir_extended = yes
virtual_mailbox_limit_maps = proxy:mysql:/etc/postfix/mysql-virtual_mailbox_limit_maps.cf
virtual_mailbox_limit_override = yes
virtual_maildir_limit_message = "The user you are trying to reach is over quota."
virtual_overquota_bounce = yes
proxy_read_maps = $local_recipient_maps $mydestination $virtual_alias_maps $virtual_alias_domains $virtual_mailbox_maps $virtual_mailbox_domains $relay_recipient_maps $relay_domains $canonical_maps $sender_canonical_maps $recipient_canonical_maps $relocated_maps $transport_maps $mynetworks $virtual_mailbox_limit_maps
content_filter = amavis:[127.0.0.1]:10024
receive_override_options = no_address_mappings

```

---

### Post by KB1JWQ on 2010-04-07
Allow me to make your life simpler.

Using gmail to send as different users doesn't work, from what I recall.

Please paste the output of postconf -n.

The name that appears in the From field is client dependent; the MTA doesn't touch that.

And verify that the PTR for your IP matches the A record-- forward confirming reverse DNS is important to avoiding the spam bin.

---

### Post by fortune2008 on 2010-04-07
thats the  postconf -n output

```
postconf: invalid option -- '.'
postconf: fatal: usage: postconf [-a (server SASL types)] [-A (client SASL types)] [-b (bounce templates)] [-c config_dir] [-d (defaults)] [-e (edit)] [-# (comment-out)] [-h (no names)] [-l (lock types)] [-m (map types)] [-n (non-defaults)] [-v] [name...]
```

---

### Post by fortune2008 on 2010-04-07
just is the real conf i was getting problem

```
alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
broken_sasl_auth_clients = yes
config_directory = /etc/postfix
content_filter = amavis:[127.0.0.1]:10024
inet_interfaces = all
inet_protocols = ipv4
mailbox_size_limit = 0
mydestination = mail.chatalker.com, localhost, localhost.localdomain
myhostname = mail.chatalker.com
mynetworks = 127.0.0.0/8
myorigin = /etc/mailname
proxy_read_maps = $local_recipient_maps $mydestination $virtual_alias_maps $virtual_alias_domains $virtual_mailbox_maps $virtual_mailbox_domains $relay_recipient_maps $relay_domains $canonical_maps $sender_canonical_maps $recipient_canonical_maps $relocated_maps $transport_maps $mynetworks $virtual_mailbox_limit_maps
readme_directory = /usr/share/doc/postfix
receive_override_options = no_address_mappings
recipient_delimiter = +
relayhost =
smtp_sasl_auth_enable = yes
smtp_sasl_password_maps = hash:/etc/postfix/sasl_passwd
smtp_sasl_security_options = noanonymous
smtp_sasl_tls_security_options = noanonymous
smtp_tls_CAfile = /etc/postfix/cacert.pem
smtp_tls_cert_file = /etc/postfix/FOO-cert.pem
smtp_tls_key_file = /etc/postfix/FOO-key.pem
smtp_tls_session_cache_database = btree:/var/run/smtp_tls_session_cache
smtp_use_tls = yes
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_recipient_restrictions = permit_mynetworks, permit_sasl_authenticated, reject_unauth_destination
smtpd_sasl_auth_enable = yes
smtpd_sasl_authenticated_header = yes
smtpd_sasl_local_domain = $myhostname
smtpd_tls_CAfile = /etc/postfix/cacert.pem
smtpd_tls_cert_file = /etc/postfix/smtpd.cert
smtpd_tls_key_file = /etc/postfix/smtpd.key
smtpd_tls_received_header = yes
smtpd_tls_session_cache_database = btree:/var/run/smtpd_tls_session_cache
smtpd_use_tls = yes
tls_random_source = dev:/dev/urandom
transport_maps = proxy:mysql:/etc/postfix/mysql-virtual_transports.cf
virtual_alias_domains =
virtual_alias_maps = proxy:mysql:/etc/postfix/mysql-virtual_forwardings.cf, mysql:/etc/postfix/mysql-virtual_email2email.cf
virtual_gid_maps = static:5000
virtual_mailbox_base = /home/vmail
virtual_mailbox_domains = proxy:mysql:/etc/postfix/mysql-virtual_domains.cf
virtual_mailbox_limit_maps = proxy:mysql:/etc/postfix/mysql-virtual_mailbox_limit_maps.cf
virtual_mailbox_limit_override = yes
virtual_mailbox_maps = proxy:mysql:/etc/postfix/mysql-virtual_mailboxes.cf
virtual_maildir_extended = yes
virtual_maildir_limit_message = "The user you are trying to reach is over quota."
virtual_overquota_bounce = yes
virtual_uid_maps = static:5000

```

---

### Post by KB1JWQ on 2010-04-07
Hmm.  Is there anything interesting in /var/log/mail.log?

---

### Post by fortune2008 on 2010-04-07
Thanks everyone i fix the prob so far with the smtp error whe i create the .cf files it didn't have the right permissions i say that in the log file

---

### Post by fortune2008 on 2010-04-07
or i came across this error 

```
[COLOR=#cc0000]**ERROR:**[/COLOR]** ERROR: Connection dropped by IMAP server.**
 
```

when trying to use squirrelmail

---

