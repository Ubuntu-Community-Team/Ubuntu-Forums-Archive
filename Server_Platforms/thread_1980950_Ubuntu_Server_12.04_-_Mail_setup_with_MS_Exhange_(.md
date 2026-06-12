---
title: "Ubuntu Server 12.04 - Mail setup with MS Exhange (Smarthost)"
date: 2012-05-16
forum: Server Platforms
---

### Post by vavr on 2012-05-16
Hi @ all.

i am new on the Linux Server installations and with some helpfull articles from the net i managed to set up an ubuntu server 12.04 with apache2, php, and mysql. Then a development team installed a wordpress site on that (let's say example.com).

 I have my own Microsoft Exchange server that manages this web site emails. DNS and MX records are all in place.


All i want to do is to have my web site's contact form to be able to send emails in the [EMAIL="info@example.com"]info@example.com[/EMAIL].

How can i do that? How can i tell in ubuntu that all the mails should go in my Exchange? Should i set up any mail system on the ubuntu server? Should i do it with smarthost?



I'd be grateful if someone could guide me to solve this.


thanks in advance.

---

### Post by SeijiSensei on 2012-05-16
Install Postfix and tell it to use the Exchange server as its relay host.  Edit /etc/postfix/main.cf and set:

```
relayhost = your.exchange.server
```

If you have DNS enabled you can use the server's FQDN in that directive, otherwise use its IP address or create an entry for the Exchange server in the Linux server's /etc/hosts file.

The Exchange server may need to have an "info" user created so it will accept messages with that From address.  I don't use Exchange, but I have clients that do, and it sometimes takes a bit of finagling to get Exchange to forward mail.

---

### Post by vavr on 2012-05-17
Hi, thanks for the reply.
is the command **apt-get install postfix** enough for what you are saying ? or do i need to install any additional things?

---

### Post by vavr on 2012-05-17
This is the config...Is it correct?

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
   
  myhostname = hostname.example.com
  alias_maps = hash:/etc/aliases
  alias_database = hash:/etc/aliases
  myorigin = /etc/mailname
  mydestination = hostname.example.com, localhost.example.com, localhost
  relayhost = (My Exchanges IP Address)               
  mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
  mailbox_size_limit = 0
  recipient_delimiter = +
  inet_interfaces = loopback-only
  inet_protocols = all
  [FONT=&quot] [/FONT]
  thanks :)

---

### Post by vavr on 2012-05-17
i believe the mydestination = hostname.example.com, localhost.example.com, localhost should be empty? 
They must got there by the postfix installation wizard. should i delete those entries?

---

### Post by vavr on 2012-05-17
I might be OK now.
I left empty the 'mydestination' and i also created a 'Recieve Connector' in my exchane.
From CLI i type sendmail [email]xxx@example.org[/email] and i received it in the xxx account webmail.
Now i must test the contact form to see if it is working too.

---

### Post by vavr on 2012-05-17
OK, Solved.

The contact form works perfect.

Thanks

---

### Post by vavr on 2012-05-22
how can i config the postfix send emails using the from [email]user@domain.gr[/email]?

---

### Post by SeijiSensei on 2012-05-23
There are two parts to this answer, only one of which I can help with.

There are two places that the From address shows up.  One is in the message itself as part of the header.  If you're trying to do this with a PHP script, you'd need to set "From: user@domain" as an additional header in the PHP mail() function.

```

mail($to,$subject,$message,'From: user@example.com');

```


However that's just half the issue.  The From address also appears during the SMTP exchange between your server and the receiver's.  Getting the machine to use the matching "user@domain" that you have in the message From is often a difficult task.  If you need to do this, you'll need to read up on how to open a socket to Postfix in PHP and pipe the message through it.  That's a pretty advanced topic on both the PHP and the Postfix sides.

---

