---
title: "Re: How to config Postfix and Dovecot to receive mail from external server"
date: 2016-11-07
forum: Server Platforms
---

### Post by fabioescabrita on 2016-11-07
Hello guys,

I am not being able to receive mails in my local accounts, i can only send mails from multi local accounts (@remote.A) to multi external accounts (@A). I can send to every domain (e.g. gmail).


Till now after several tests, i notice that when i send mails without SMTP AUTH, i receive a message from my ISP mail server, saying that SMTP AUTH is activated and i must activated to pass through that server. If i try to send mail in the external server between accounts of my domain, i dont receive any mail in my local server. If i try to send mail in my local server between local accounts, i will receive mail locally, it will not pass through my external server as expected. 


In my external server, i have cpanel, where i create external email accounts. There i have config email routing for the domain that i just want to use in my local mail server. I have set MX records with a secondary priority (in first i have the domain of my email by default). It is config as auto to deal with mail brought also by default(*). The secondary priority is a link (a subdomain of the email domain) for my static IP. I already search if i had my IP blocked and from a big list i only had 1 blocking me.
I have also configured SPF of my external server to auth sends from my local server.


(*)

[LIST]
[*]Automatically Detect Configuration : (Local)
[*]Mail Exchanger local
[*]Mail Exchanger de backup
[*]Mail Exchanger remote
[/LIST]

Right now i have in my main.cf from local server Postfix this:
[http://pastebin.com/KsEDzD4T](http://pastebin.com/KsEDzD4T)

I have been trying to reroute received external mails to local accounts in my local server through virtual_alias_maps but i think thats not the problem right now, since i am unable to push mail from the external server. Received mail are being stack in that server.


I think that i have made the correct steps with cpanel, but i dont have a clue on how can i set Postfix and Dovecot to receive/push mails from my external server. This is my first time trying to do these and i need some expert advise :confused:

After looking at my external IP, i notice that i am unable to connect to it:

```
emote:postfix root# telnet remote.X.pt 25
Trying 93.108.222.X...
telnet: connect to address 93.108.222.X: Connection refused
telnet: Unable to connect to remote host
remote:postfix root# 

```

After add my server to the DMZ of my router, just to test, i continue to be unable to connect from outside, i am able just to connect from localhost. 

Then i look for a local firewall, and is off by default.

I have no clue in where is the source of this problem =/

---

### Post by SeijiSensei on 2016-11-07
Take a look at the mynetworks directive in main.cf.  By default it is set only to accept mail on the localhost (127.0.0.1) interface.  

Please read [https://help.ubuntu.com/community/PostfixBasicSetupHowto](https://help.ubuntu.com/community/PostfixBasicSetupHowto) and also [http://www.postfix.org/SMTPD_ACCESS_README.html](http://www.postfix.org/SMTPD_ACCESS_README.html)

---

### Post by fabioescabrita on 2016-11-08
> **SeijiSensei said:**
> Take a look at the mynetworks directive in main.cf.  By default it is set only to accept mail on the localhost (127.0.0.1) interface.  

Please read [https://help.ubuntu.com/community/PostfixBasicSetupHowto](https://help.ubuntu.com/community/PostfixBasicSetupHowto) and also [http://www.postfix.org/SMTPD_ACCESS_README.html](http://www.postfix.org/SMTPD_ACCESS_README.html)

Thanks for the reply SeijiSensei.

I will do that and i will say the result here. Dont know if it is relevante but after thinking a while about the IP that i am using i dont know if that is not the source. I am using an dynamic IP who change very rarely(with a DNS name with reverse DNS), till now i have the same for almost 2 weeks, and i dont know if my ISP is not blocking ports by default for this kind of services of income mail.

I have tried with no mynetworks entry and:

> mynetworks = 127.0.0.0/8, a.b.c.d/e



I did the first one to see if it sets the best suitable option, as it says at postfix. The other one just saw somewhere saying that would allowed requests from every IP.

And same result, no income mail and connections refused at 143 and 993. I didnt found a way also to check incoming mail queue, i have just used the mailq to check mail sends, dont know if it will shows there the incoming mail.

---

### Post by SeijiSensei on 2016-11-08
To receive mail from all addresses use
```
mynetworks = 0.0.0.0/0
```

Mailq checks the outbound queue.  

I'm a bit unclear on how the server is configured.  Do you not have a router between the server and the Internet?  If so, then the router has the public IP address, and the server likely has a different, private address.  If that is the arrangement, then you need to configure "port forwarding" on the router so that traffic arriving on external ports like 25 or 143 are forwarded back to the server.  The method for configuring forwarding varies from router to router.

---

### Post by fabioescabrita on 2016-11-08
> **SeijiSensei said:**
> To receive mail from all addresses use
```
mynetworks = 0.0.0.0/0
```

Mailq checks the outbound queue.  

I'm a bit unclear on how the server is configured.  Do you not have a router between the server and the Internet?  If so, then the router has the public IP address, and the server likely has a different, private address.  If that is the arrangement, then you need to configure "port forwarding" on the router so that traffic arriving on external ports like 25 or 143 are forwarded back to the server.  The method for configuring forwarding varies from router to router.


I have changed mynetworks to 0.0.0.0/0 and same result.

I have my server connected to a router. I have an external IP who is public and dynamic (almost static, 2 weeks in a row with the same IP), and i have a different one in my private network who is a static. I have not set a port forwarding in my router for now because i am testing with DMZ.

Right now i have a mail web service installed in this server, and is already working with port forwarding. I have access from outside of this network through the DNS name associated with this IP.

If was a port forwarding problem i could avoid that when i was using DMZ for test right?

If you need any extra info just ask.

Since i have no clue yet, here it goes the DNS table in this server:

[http://prntscr.com/d4l4ai](http://prntscr.com/d4l4ai)

The idea is, the domain A is hosted in a external server, who is my mail domain, and in the subdomain remote.A will be my internal server. Remote.A will be accepting and sending mails from my external server A.

Process's per port:

SMTP:
```
remote:Postfix root# netstat -tnlp tcp | grep '\.25 '
remote:Postfix root# netstat -tnlp tcp | grep '\.2525 '
remote:Postfix root# netstat -tnlp tcp | grep '\.465 '
```

POP3:
```
remote:Postfix root# netstat -tnlp tcp | grep '\.110 '
remote:Postfix root# netstat -tnlp tcp | grep '\.995 '
```

IMAP:

```
remote:Postfix root# netstat -tnlp tcp | grep '\.143 '
tcp4       0      0  192.168.1.1.143        192.168.1.1.50825      ESTABLISHED
tcp4       0      0  192.168.1.1.50825      192.168.1.1.143        ESTABLISHED
remote:Postfix root# netstat -tnlp tcp | grep '\.993 '
tcp4       0      0  192.168.1.1.993        192.168.1.1.49455      ESTABLISHED
tcp4       0      0  192.168.1.1.49455      192.168.1.1.993        ESTABLISHED
tcp4     143      0  192.168.1.1.65235      192.168.1.1.993        CLOSE_WAIT 
tcp4       0      0  192.168.1.1.993        192.168.1.1.54435      ESTABLISHED
tcp4       0      0  192.168.1.1.54435      192.168.1.1.993        ESTABLISHED
tcp4       0      0  192.168.1.1.993        192.168.1.1.50955      ESTABLISHED
tcp4       0      0  192.168.1.1.50955      192.168.1.1.993        ESTABLISHED
tcp4       0      0  192.168.1.1.993        192.168.1.1.50944      ESTABLISHED
tcp4       0      0  192.168.1.1.50944      192.168.1.1.993        ESTABLISHED
tcp4       0      0  192.168.1.1.993        192.168.1.1.50874      ESTABLISHED
tcp4       0      0  192.168.1.1.50874      192.168.1.1.993        ESTABLISHED
tcp4       0      0  192.168.1.1.993        192.168.1.1.50852      ESTABLISHED
tcp4       0      0  192.168.1.1.50852      192.168.1.1.993        ESTABLISHED
```

And i was thinking well about what port is used when we are pushing mail from an external server to a local server, through a MX record and i am not sure what protocol is used, but i believe that it could be SMTP since is a connection from a MTA to another MTA. I am telnetting for both IMAP and SMTP, and even POP3 ports, for my public IP and no connection is made.

**UPDATE1:**

DNS lookup to my mail domain (the 1º pref remote.A is pointed to my local server, that i IP i think that belongs to external mail server):
[IMG]http://image.prntscr.com/image/431b10bb09ea44bea470d8868bf34033.png[/IMG]

UPDATE2:

The authentication part of my external server:

[IMG]http://image.prntscr.com/image/47c860d64e8349d6928cd1a980190a44.png[/IMG]

**UPDATE2:**

I have used the wrong DNS name (before, now i have already updated this thread), i have two DNS names, one is directly pointed to my external IP, and with the other i am just able to connect to my local website (port 80), and it is not pointed to my external IP. I ask to my ISP for a DNS name to my public IP and this was what they gave me, is something that i have to change. I just want one DNS name to my external IP pointed to my external IP.

**UPDATE3:**

SMTP port used: 25

telnet to SMTP from localhost:
```

Trying 192.168.1.1...
Connected to remote.X.pt.
Escape character is '^]'.
220 remote.gfe-tec.pt ESMTP Postfix
^Z^X
quit
Connection closed by foreign host.
```

telnet to SMTP from external IP:
```

Trying 93.108.222.X...
telnet: connect to address 93.108.222.X: Connection refused

```

[B]UPDATE4:

[/B]After i add an entry in the firewall of my router to accept connections from my mail external server, i tried again to telnet at port 25 and i was able to connect, i have tried also to telnet from outside of my private network and was able to enter. I didnt expect that i could do this because i have set just to accept connections from my external server IP (not all IPs):

[IMG]http://image.prntscr.com/image/faf1f68d5d98470d9308346b05715635.png[/IMG]

And still, i have not received any mail while i had this port forwarding activated.

Now i am more convinced that this is being caused by my IP provider, because i am using a dynamic IP. I have already contact my ISP for info about this issue. I will leave here the response when i have it.

---

### Post by SeijiSensei on 2016-11-08
I have never used a DMZ.  I'd just configure port forwarding and leave it at that.

---

### Post by fabioescabrita on 2016-11-09
> **SeijiSensei said:**
> I have never used a DMZ.  I'd just configure port forwarding and leave it at that.

Ah yes, it was just for testing several ports at once during a short period of time. It is very dangerous to do this with mail servers from what i have notice, there are a lot of mail exploiters out there.

Now about my ISP IP provider (vodafone), they didnt confirm if that could be the issue behind i am not receiving mail. They just check if i had my IP blacklisted, and it was just in one from a big list. So i continue to dont know after all. I have also ask to change my contract to support an static IP, and i will see there if it solves this problem, if not, at least i will know that the problem is in my ISP mail provider or it could be from my local server.

---

### Post by fabioescabrita on 2016-11-10
I was able to avoid this problem through getmail, it seems very good, it is possible to use IMAP or POP3, with or without SSL, to retrieve mail from external server, and then it is possible to send to local postfix, through sendmail, and then i will receive mails in my local user accounts. It is a powerfull tool! 

Now i am trying to use it like the old fetchmail, to be executed at a certain period of time, till now i was not able to set it. I am only able to retrieve mail when i execute getmail manually.

---

