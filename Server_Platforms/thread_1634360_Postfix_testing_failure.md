---
title: "Postfix testing failure"
date: 2010-11-30
forum: Server Platforms
---

### Post by navaneethan on 2010-11-30
In my uubntu server i have to verify the postfix server which is installed already in my server just i need to test whether the server working in its localhost

so here i wanna to toest this postfix server 


[B]ubuntu@ip-10-204-43-33:~$ sudo /etc/init.d/postfix start
 * Starting Postfix Mail Transport Agent postfix                                                                                                                 [ OK ] 
ubuntu@ip-10-204-43-33:~$ telnet localhost 25
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
[/B]


I don't know where is the problem is? help me

> .......
...........
...
mailbox_command = /usr/bin/procmail
myorigin = /etc/mailname
mydestination =  localhost
mydomain = $myhostname
mydestination = $myhostname localhost.$mydomain localhost $mydomain
#relayhost = 
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all

smtpd_delay_reject =no
smtpd_helo_required = no

#smtpd_helo_restrictions =
  #      reject_non_fqdn_hostname,  (#commented)
 #       permit

#smtpd_sender_restrictions =
   #     reject_non_fqdn_sender,
  #      reject_unknown_sender_domain,
 #       permit

......
.....


please if you need any information question it.

---

