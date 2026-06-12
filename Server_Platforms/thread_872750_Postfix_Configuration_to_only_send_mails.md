---
title: "Postfix Configuration to only send mails"
date: 2008-07-28
forum: Server Platforms
---

### Post by Brenda Watsen on 2008-07-28
Hi,

I installed a software for a Directory service.

I noticed that I don't have a mail program installed on my webserver.

I use webmin for the connection with my webserver.

After I established a connection I installed Postfix.



1) 
Does someone have an example of how to configure Postfix to send mails?

2)
What should the configuration be to make the server only send mails and not receiving mails?

3)
I must enter the path in the Directory configuration to make the Directory software send mails. What is the path of Postfix to send mails?

My Domain is                                  : mirrage.nl
My Hostname is (name of the webserver)        : cyber01
The IP of my server is                        : 192.168.50.100

Thank you

---

### Post by Phulerock on 2008-07-28
when you install postfix by apt-get command, the dialog box appear and you can entry yourdomain and you network .etc

If with this basic configuration, postfix only send email, don't received any thing.

You can send email by command mail:
mail - send and receive mail
SYNOPSIS
mail [-iInv ] [-s subject ] [-c cc-addr ] [-b bcc-addr ] to-addr...
mail [-iInNv -f ] [name ]
mail [-iInNv [-u user ] ]

---

### Post by Brenda Watsen on 2008-07-28
Hi,

Thank you for your reply and for your information that ubuntu sends email by default. 

I would like to know this.

I configure my network settings like below.
Can you tell me if this is correct?
I edit this but I don't know what I have done.
Because this can trouble the mail configuration. I am not sure.

127.0.0.1 localhost
127.0.1.1 cyber01.mirrage.nl cyber01
192.168.50.100 cyber01 [www.mirrage.nl](www.mirrage.nl)
# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

Thank you in advanced.

Diana

---

### Post by Phulerock on 2008-07-28
hi,this should be:
192.168.50.100 cyber01.mirrage.nl

now make sure postfix started: /etc/init.d/postfix start
test:
telnet 192.168.50.100 25
220 localhost.localdomain ESMTP Postfix (Ubuntu)
=>> postfix work !

---

### Post by Phulerock on 2008-07-28
and this is very basic configuration for send email only: find these line and configure it as below
```
# See /usr/share/postfix/main.cf.dist for a commented, more complete version

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

append_dot_mydomain = no

myhostname = cyber01.mirrage.nl
mydestination = mirrage.nl, localhost.mirrage.nl
mynetworks = 127.0.0.0/8 192.168.50.0/24
mailbox_command = procmail -a "$EXTENSION"

```
If you don't want another host on your network send email, change the line:
mynetworks = 127.0.0.0/8 192.168.50.100/32

---

