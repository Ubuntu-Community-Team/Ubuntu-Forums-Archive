---
title: "postfix configuration, can't send e-mail"
date: 2010-04-23
forum: Server Platforms
---

### Post by sakis_the_fraud on 2010-04-23
Hello!

New to ubuntu forums, but i have experience with ubuntu and generally Linux.

I am trying to make my elastix voip server to send and receive e-mails. It has built in Postfix mail server, and i tried to configure it.

I am not sure about some parameters, such as domain and hostname.

Either way, i will attach my config file and the errors that i get from log and mail queue as i get them from webmin.


etc/postfix/main.cf
```

queue_directory = /var/spool/postfix
command_directory = /usr/sbin
daemon_directory = /usr/libexec/postfix
mail_owner = postfix
myorigin = $mydomain
inet_interfaces = all
unknown_local_recipient_reject_code = 550
mynetworks = /etc/postfix/network_table
mailbox_transport = cyrus
debug_peer_level = 2
debugger_command =
     PATH=/bin:/usr/bin:/usr/local/bin:/usr/X11R6/bin
     xxgdb $daemon_directory/$process_name $process_id & sleep 5
sendmail_path = /usr/sbin/sendmail.postfix
newaliases_path = /usr/bin/newaliases.postfix
mailq_path = /usr/bin/mailq.postfix
setgid_group = postdrop
html_directory = no
manpage_directory = /usr/share/man
sample_directory = /usr/share/doc/postfix-2.2.2/samples
readme_directory = /usr/share/doc/postfix-2.2.2/README_FILES

virtual_alias_maps = hash:/etc/postfix/virtual

################################
#Ingresado por yb-webadmin
mydomain = datavision.gr
myhostname = elastix.datavision.gr

# SMTP relayhost
relayhost = [smtp.gmail.com]:587

## TLS Settings
smtp_tls_loglevel = 1
smtp_tls_CAfile = /etc/postfix/certs/CAcert.pem
smtp_tls_cert_file = /etc/postfix/certs/mycert.pem
smtp_tls_key_file = /etc/postfix/certs/mykey.pem
smtp_use_tls = yes
smtpd_tls_CAfile = /etc/postfix/certs/CAcert.pem
smtpd_tls_cert_file = /etc/postfix/certs/mycert.pem
smtpd_tls_key_file = /etc/postfix/certs/mykey.pem
smtpd_tls_received_header = yes
smtpd_use_tls = yes

# configuracion tls
smtp_use_tls = yes
smtp_sasl_auth_enable = yes
smtp_sasl_password_maps = hash:/etc/postfix/sasl_passwd
smtp_sasl_security_options = noanonymous
smtp_sasl_tls_security_options = noanonymous

# alias de mapeo interno a externo
smtp_generic_maps = hash:/etc/postfix/generic

canonical_maps = hash:/etc/postfix/canonical

```

/var/log/maillog

```
Apr 23 12:22:27 elastix postfix/postfix-script: refreshing the Postfix mail system
Apr 23 12:22:27 elastix postfix/master[6661]: reload configuration /etc/postfix
Apr 23 12:23:07 elastix postfix/pickup[15621]: 83B6C35985BF: uid=0 from=<root>
Apr 23 12:23:07 elastix postfix/cleanup[15630]: 83B6C35985BF: message-id=<20100423092307.83B6C35985BF@elastix.datavision.gr>
Apr 23 12:23:07 elastix postfix/qmgr[15623]: 83B6C35985BF: from=<root@datavision.gr>, size=295, nrcpt=1 (queue active)
Apr 23 12:23:07 elastix postfix/smtp[15632]: 83B6C35985BF: to=<sakis_the_fraud@yahoo.gr>, relay=none, delay=0.13, delays=0.1/0.03/0/0, dsn=4.4.3, status=deferred (Host or domain name not found. Name service error for name=smtp.gmail.com type=A: Host not found, try again)
```



Mail Queue
```
 	83B6C35985BF 	2010/04/23 12:23 	root@datavision.gr 	my-email@yahoo.gr 	295 bytes 	Host or domain name not found. Name service error for name=smtp.gmail.com type=A: Host not found, try again
```

I hope someone knows where is the problem...

Thanks in advance for your help!!! :D

---

### Post by noway2 on 2010-04-23
> ame service error for name=smtp.gmail.com type=A: Host not found, try again

Looks like a DNS problem.  Postfix (email) is very reliant on DNS capability.  Did you install a DNS server?  If not, Bind is pretty easy to set up and there are a large number of how-to documents that will show you simple to moderate configuration examples.

---

### Post by sakis_the_fraud on 2010-04-23
> **noway2 said:**
> Looks like a DNS problem.  Postfix (email) is very reliant on DNS capability.  Did you install a DNS server?  If not, Bind is pretty easy to set up and there are a large number of how-to documents that will show you simple to moderate configuration examples.

seems weird, i haven't seen anyone before to mention that you need a dns server in order to send and receive emails via postfix.

I have configured google dns on the server, but nothing changed at all...

Do you know if there is an option to install another EASIER TO CONFIGURE e-mail server?

if someone has a different opinion please let me know. ;)

---

### Post by dudumomo on 2010-04-23
You need DNS records yes, but you don't need a bind server. You can simply use the DNS of your registar.
It's what I did.
(PS: See my signature for a tutorial, it may help you)

---

### Post by cdenley on 2010-04-23
Can your server resolve DNS records?
```

host smtp.gmail.com
cat /etc/resolv.conf

```

---

### Post by sakis_the_fraud on 2010-04-26
> **cdenley said:**
> Can your server resolve DNS records?
```

host smtp.gmail.com
cat /etc/resolv.conf

```

no :(

```

> host smtp.gmail.com
bash: host: command not found

> cat /etc/hosts
# Do not remove the following line, or various programs
# that require network functionality will fail.
127.0.0.1        elastix.datavision.gr
127.0.0.1    elastix.datavision.gr

> cat /etc/resolv.conf
nameserver 195.170.0.1
nameserver 8.8.8.8

```

what should i do now?

---

### Post by cdenley on 2010-04-26
Is "elastix" a linux distribution? Are you running ubuntu?
```

lsb_release -a

```

If you don't even have the "host" command, and you're not using ubuntu, then it might be difficult to troubleshoot your problem. You're first DNS server in /etc/resolv.conf doesn't appear to be resolving hostnames, though. Try removing it, and just using 8.8.8.8.

---

### Post by sakis_the_fraud on 2010-04-26
> **cdenley said:**
> Is "elastix" a linux distribution? Are you running ubuntu?
```

lsb_release -a

```If you don't even have the "host" command, and you're not using ubuntu, then it might be difficult to troubleshoot your problem. You're first DNS server in /etc/resolv.conf doesn't appear to be resolving hostnames, though. Try removing it, and just using 8.8.8.8.
elastix is based on CentOS. ;)

I finally fixed this. i don't know why, but my default gateway was empty, i added my gateway, and rerun the script that adds google.com as a relay to postfix and  it worked!

thanks for your help!


Case closed ;)

---

