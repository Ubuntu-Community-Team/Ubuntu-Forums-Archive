---
title: "[SOLVED] YAR, postfix on 7.10 default e-mail address"
date: 2008-02-18
forum: Server Platforms
---

### Post by Yamaboy on 2008-02-18
I've read up on these forums but I'm having a little trouble changing the default e-mail address that a PHP script generates. 

I've added a sender_canonical_map to the config and reloaded (as per [http://ubuntuforums.org/showthread.php?t=560442](http://ubuntuforums.org/showthread.php?t=560442)) but I still get the www-data@ showing up as the from: address.

Probably something simple is missing and I might be able to change the PHP code, but it would be better to change the Postfix config in case more scripts are added to the server.

Here are a couple pieces of info. This is strictly internal storage server to e-mail server on the same network.

Thanks everybody.

main.cf
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

# TLS parameters
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = vivaubuntu.xxx.edu
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
sender_canonical_maps = hash:/etc/postfix/sender_canonical_maps
mydestination = vivaubuntu, vivaubuntu.xxx.edu, localhost.localdomain, localhost
relayhost = 
mynetworks = 127.0.0.0/8
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
```

sender_canonical_maps
```
#
# /etc/postfix/sender_canonical_maps
#
www-data@vivaubuntu.xxx.edu donotreply@vivaubuntu.xxx.edu
www-data@localhost donotreply@vivaubuntu.xxx.edu
www-data@localhost.localdomain donotreply@vivaubuntu.xxx.edu
```


mail log
```
Feb 18 13:20:04 vivaubuntu postfix/master[16158]: terminating on signal 15
Feb 18 13:20:04 vivaubuntu postfix/master[16688]: daemon started -- version 2.4.5, configuration /etc/postfix
Feb 18 13:20:30 vivaubuntu postfix/pickup[16689]: 9E9C3104BBE: uid=33 from=<www-data>
Feb 18 13:20:30 vivaubuntu postfix/cleanup[16710]: 9E9C3104BBE: message-id=<20080218192030.9E9C3104BBE@vivaubuntu.xxx.edu>
Feb 18 13:20:30 vivaubuntu postfix/qmgr[16693]: 9E9C3104BBE: from=<www-data@vivaubuntu.xxx.edu>, size=1404, nrcpt=1 (queue active)
Feb 18 13:20:30 vivaubuntu postfix/smtp[16712]: 9E9C3104BBE: enabling PIX workarounds: disable_esmtp delay_dotcrlf for xxx.edu[10.22.9.15]:25
Feb 18 13:20:30 vivaubuntu postfix/smtp[16712]: 9E9C3104BBE: to=<xxx@xxx.edu>, relay=xxx.edu[10.22.9.15]:25, delay=0.1, delays=0.04/0.01/0.04/0.02, dsn=2.0.0, status=sent (250 Ok)
Feb 18 13:20:30 vivaubuntu postfix/qmgr[16693]: 9E9C3104BBE: removed
```

---

### Post by faulkes on 2008-02-18
PHP mail accepts two types of addresses.

The "From:" address i.e. From: root@localhost

and

The "Return-Path" address i.e. Return-Path: someuser@localhost

Even if you set the From: address portion in php, the majority of mailers will ignore it
and use the system account from which the mail is sent (i.e. www-data).

Look at the PHP mail function and set the Return-Path address and this should sort
out your problem.

Faulkes

---

### Post by Yamaboy on 2008-02-18
Good call faulkes. I had to go into the script and find this little snippet.
```

$execAsUser = posix_getpwuid(posix_geteuid());
    $from = sprintf("%s <%s@%s>",
              $this->_dboxName,
              $execAsUser['name'],
              $_SERVER['SERVER_NAME']);
    return mail($toAddr,$subject,$content,"From: $from\r\nReply-to: $from\r\n");
```

Just changed it to;

```
$execAsUser = posix_getpwuid(posix_geteuid());
    $from = sprintf("%s <donotreply@vivaubuntu.xxx.edu>",
              $this->_dboxName,
              $execAsUser['name'],
              $_SERVER['SERVER_NAME']);
    return mail($toAddr,$subject,$content,"From: $from\r\nReply-to: $from\r\n");
```

Works how I want it to now.

Thanks for the help. There's just some overlap between PHP and Postfix config that I needed some help with and this did the trick for the app.

---

### Post by cnschulz on 2008-02-22
Hey, 

I have the same problem.

I relay through my ISP. so mails has the sender address as 

[email]root@my.isp.com[/email]

thats not good!

i have many programs using postfix so its not a simple as setting the return path...

can i change this setting somewhere? can i run postfix as another user? 

if so how?

cheers

c.

---

