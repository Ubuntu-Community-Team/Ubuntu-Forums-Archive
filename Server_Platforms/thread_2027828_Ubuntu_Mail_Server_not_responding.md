---
title: "Ubuntu Mail Server not responding"
date: 2012-07-17
forum: Server Platforms
---

### Post by Nixforce on 2012-07-17
I have recently setup a server for my websites, and battling a bit with the mail side of thing, in the past i was always running a hosting plan with Plesk, but no root access. The mail server was then setup by the hosting company.

I have installed my Ubuntu Server, got my apache, tomcat on my hosting running, but battling with the mail server. I have tried a few guides, but seem to fail. I need the server to accept for a few domains. 

I have just tested to see if the port is open, and it passed. Can anyone help?

---

### Post by Nixforce on 2012-07-17
OOpps.. i didnt mention i have install postfix .. i have also install webmin with the postfix addon to try and manage and set it up.

---

### Post by d4m1r on 2012-07-17
What are the errors you are seeing? How do you know it's failing and at what stage?

---

### Post by Nixforce on 2012-07-18
This is the error i get in my mail client.

554 5.7.1 <glenn@gamblingdungeon.com>: Relay access denied.

Its another email of mine, which is currently on my old hosting. It gives me the error when connecting to the server before sending.

---

### Post by ephmanjmm on 2012-07-18
Can you post the main.cf file?  Also have you configured the relay_domains and transport files?

---

### Post by Nixforce on 2012-07-18
Hi,

Here is the config file: 
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
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = govps1
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = go-systems.co.za, govps1, localhost.localdomain, localhost
relayhost = 
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all



```

I have not done any of the rest i dont think.. Sorry im new at running a full nix based box, been mainly on windows

---

### Post by SeijiSensei on 2012-07-18
> mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128


I don't know if you're trying to send mail to this box from outside, but this line limits the server to listening on the "localhost" interface.  

You need to start by reading [http://www.postfix.org/SMTPD_ACCESS_README.html](http://www.postfix.org/SMTPD_ACCESS_README.html) and [http://www.postfix.org/postconf.5.html#smtpd_recipient_restrictions](http://www.postfix.org/postconf.5.html#smtpd_recipient_restrictions).

---

### Post by SeijiSensei on 2012-07-18
> mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128


I don't know if you're trying to send mail to this box from outside, but this line limits the server to accepting only mail that comes from the "localhost" interface (127.0.0.1).  Mail from other locations, in particular mail sent to the machine's public IP interface, will be rejected. 

You need to start by reading [http://www.postfix.org/SMTPD_ACCESS_README.html](http://www.postfix.org/SMTPD_ACCESS_README.html) and [http://www.postfix.org/postconf.5.html#smtpd_recipient_restrictions](http://www.postfix.org/postconf.5.html#smtpd_recipient_restrictions).

---

### Post by Nixforce on 2012-07-18
Hi,

Thanks!! is it possible to accept from all, as my IP changes.

Would it then require username and password hopefully, so i dont get the IP blocked?

Thanks

---

### Post by sandyd on 2012-07-18
> **Nixforce said:**
> Hi,

Thanks!! is it possible to accept from all, as my IP changes.

Would it then require username and password hopefully, so i dont get the IP blocked?

Thanks
Setup users/passwords, then 
```

mynetworks = 0.0.0.0/0

```
make sure your users/passwords are SECURE.
Otherwise, you will be setting up an OPEN RELAY.

Something like
```

smtpd_recipient_restrictions =     permit_mynetworks     check_client_access hash:/etc/postfix/access_clients    reject_unauth_destination

```

---

