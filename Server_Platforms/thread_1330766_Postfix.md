---
title: "Postfix"
date: 2009-11-18
forum: Server Platforms
---

### Post by Darth Arturito on 2009-11-18
Hello there!

I have a problem with Postfix configuration in Ubuntu. I cannot establish connection on port 25 from anywhere else apart from the localhost. 

Things I did:

1. I have configured and installed it according to that document:
[https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix) and configured mx records.

2. Checked netstat -an|grep 25

tcp        0      0 0.0.0.0:25             0.0.0.0:*               LISTEN
tcp6       0      0 :::25                   :::*                    LISTEN

3. Opened port 25 on the router. 

And that should be it. 

Now wheather I try to connect from outside or even from the LAN
by simply telneting on port 25 I always get connection timed out.

Anyone has an idea what could be problem?

mail.log  and mail.err show nothing related to the problem. 


Here is my main.cf


```
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no
append_dot_mydomain = no
readme_directory = no

# TLS parameters
smtpd_tls_cert_file = /etc/ssl/certs/smtpd.crt
smtpd_tls_key_file = /etc/ssl/private/smtpd.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache


myhostname = mail.domain.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = mail.domain.com,domain.com, localhost
relayhost =
mynetworks = 127.0.0.0/8
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all
home_mailbox = Maildir/
mailbox_command =

smtpd_sasl_local_domain =
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
smtp_tls_security_level = may
smtpd_tls_security_level = may
smtpd_tls_auth_only = no
smtp_tls_note_starttls_offer = yes
smtpd_tls_CAfile = /etc/ssl/certs/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom
```

Ubuntu´s ip : 192.168.99.10

Ubuntu's version: hardy

---

### Post by ductiletoaster on 2009-11-18
hi there... i to am having a similiar problem.
I can telnet using this 
```
telnet localhost 25
```
according to the tutorial im fallowing when i send the msg and quit telnet the mysql.log should show some sort of activitiy but it doesnt.

here is the tutorial im using maybe it will help u 
[http://flurdy.com/docs/postfix/]("http://flurdy.com/docs/postfix/")
Im on the section that says **TEST**

---

### Post by ductiletoaster on 2009-11-18
Ok so do me a favor and do this in a separate terminal
```
sudo tail -f /var/log/mysql/mysql.log 
```
and then ( just fallow the cmds... anything with > before it represents something being displayed and make sure u replace any relevent info with ur own)
```

# Lets try and send a message to xandros@lala.com 
# (replace with your own user in this setup, or use postmaster@localhost) telnet localhost 25 
# reponse back: 
> 
> 
> 
# then open the hand shake with ehlo and the server name you are connecting from... 
EHLO mail.domain.tld 
> 
> 
> 
# then say who is the sender of this email 
MAIL FROM: <your@address.com> 
> 250 Ok 
# then say who the mail is for 
RCPT TO: <xandros@lala.com> 
> 250 Ok data 
> 354 End data with <CR><LF>.<CR><LF></LF></CR></LF></CR> 
# enter message bodyand end with a line with only a full stop. blah blah blah more blah . 
> 250 Ok; queued as QWKJDKASAS 
# end the connection with quit 
> 221 BYE

```

amd then watch the mysql.log if something new shows up in it then post it. repeat this with another telnet process such as from a remote computer.

---

### Post by ductiletoaster on 2009-11-18
Sorry to keep replying but i just realized two things.... first you ```
relayhost =
```
is blank... now this is ok if your goin to be ur own out bound mail server and u probably were goin to be... however alot of ISPs block port 25 and if thats the case then ur screwed enlest you set 
```
relayhost =smtp.youisp.net
```
most isps have there own smtp server and you can just use it like so!

This will do two things.... should allow u to email beyond ur localhost and also should take some strain off your server...Hope this helps

If you could help me out i was wondering how did u set up your mysql tables?

---

### Post by wyldfury on 2009-11-19
Sounds like a network problem. If Ubuntu is downloading packages alright then I'd guess at something like iptables on the machine or a smart switch/router dropping packets to port 25.

---

### Post by Darth Arturito on 2009-11-19
In my case port 25 isn't blocked by isp because to the same router I have hooked up windows server with exchange which is communicating with the outside world just fine. (2nd WAN)

I doubt it is a routers fault as it does work for windows machine. I can't establish connection within intranet and that might be something to do with iptables as wyldfury mentioned.

---

### Post by Darth Arturito on 2009-11-19
Solved it!
My server on the intranet has ip 192.168.99.10

I applied these commands:

iptables -A INPUT -p tcp -s 0/0 --sport 1024:65535 -d 192.168.99.10 --dport 25 -m state --state NEW,ESTABLISHED -j ACCEPT

iptables -A OUTPUT -p tcp -s 192.168.99.10 --sport 25 -d 0/0 --dport 1024:65535 -m state --state ESTABLISHED -j ACCEPT

and now I can establish connection without any problem.

(I blocked ssh access now but that's something to solve later) :-)

Thank you all!

---

