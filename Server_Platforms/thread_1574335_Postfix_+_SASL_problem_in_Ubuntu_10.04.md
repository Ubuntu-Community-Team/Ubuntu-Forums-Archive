---
title: "Postfix + SASL problem in Ubuntu 10.04"
date: 2010-09-14
forum: Server Platforms
---

### Post by RohmanSama on 2010-09-14
Dear all, i'm trying to set up a Postfix + Courier-IMAP in my dedicated Ubuntu Server 10.04, I had been able to set everything up in a way that i can set up my account in a Mac OS X Mail app though IMAP and i'm able to receive email and send email to my own domain ONLY... but when i try to send email from the Mail APP to gmail.com ( for example ), i get a "Relay access denied" error... if i send the email from telnet in the server directly it works... only fails when i'm in a remote environment.

Some suggested to add the network IP range to my networks in Postfix... but that is not what i want, because i want to be able to receive and send email with my Mail APP from whenever i am independently from my location ( makes sense, right? )

I know the right answer is SASL, but until now i had no luck on configuring saslauthd... my login attempts are always denied... don't know what to do.

I'm not using databases ( i.e. mysql ) to store users, i'm using virtual aliases instead.

Here there are the steps i follow to set up my working Postfix + Courier-IMAP ( without SASL -> my missing part )

[ installing Postfix ]
> aptitude install postfix libsasl2-2 sasl2-bin libsasl2-modules procmail

[ adding user "rohman" for email testing ]
> useradd -m rohman
> passwd rohman

[ linking the email addresses to local users ]
> nano /etc/postfix/virtual
```

postmaster@mymail.com postmaster
rohman@mymail.com rohman

```

[ configuring Postfix ]
> nano /etc/postfix/main.cf
```

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no
append_dot_mydomain = no
readme_directory = no
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
myhostname = waikiki
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = mail.mymail.com, waikiki, localhost.localdomain, localhost
relayhost =
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_command =
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all
virtual_alias_domains = mymail.com
virtual_alias_maps = hash:/etc/postfix/virtual
home_mailbox = Maildir/

```

[ make the user database ]
> postmap /etc/postfix/virtual

> /etc/init.d/postfix restart

[ install Courier-IMAP ]
> aptitude install courier-imap-ssl

[ fixing the SSL certificate ]
> cd /etc/courier&#8232;> rm -f /etc/courier/imapd.pem
> nano /etc/courier/imapd.cnf
[...]
CN=mymail.com
[...]
> mkimapdcert

[ restart Courier-IMAP ]
> /etc/init.d/courier-imap-ssl restart

***
To that point, i can set up my account [email]rohman@mymail.com[/email] in my Mac's Mail APP and receive email, send email to [email]xxx@mymail.com[/email], but fails on sending email to [email]xxx@gmail.com[/email], etc...

can somebody help? is making me crazy
thank you very much

Rohman

---

