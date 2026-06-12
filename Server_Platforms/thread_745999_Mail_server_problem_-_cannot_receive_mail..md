---
title: "Mail server problem - cannot receive mail."
date: 2008-04-05
forum: Server Platforms
---

### Post by sarugaku on 2008-04-05
Hi there,
I've been searching this forum for answer quite a long time, but it seems that other topics are related to similar problems, but dont cope with my acctual one. I have set up an email server and im using ISPConfig and Uebimiau for webmail, I can send my emails correctly to other domains but other people cannot send me an email. They receive something like 550 error user cannot be found from mailer deamon so emails wont even reach my server (so it's a safe bet that ports are ok) I guess the problem lies within configuration of a domain (somehow it cant resolve a name [email]user@mydomain.com[/email]) 
Best regards,
Tom

---

### Post by gombadi on 2008-04-05
Are there any messages in the mail logs of the server?
Have a look in /var/log/mail.log

That should show you what errors the mail server is giving and why it is giving them.

---

### Post by sarugaku on 2008-04-06
Nope the logs are clear, nothing about messages undelivered can be read - they just disappear in the way to my serv ;/
I have configured my domain - mydomain.pl to point to my server's ip number (static) 1.2.3.4. When i send an email from squirrelmail on my server from mail [email]user@mydomain.pl[/email] to i.e. gmail.com account everything goes fine, but when i try to send message from gmail.com (or any other mail provider) i just get nothing. No error logs in mail.log (the error about user has been fixed - my domain pointed to the wrong ip address). I cant figure it out myself i guess...

---

### Post by mhmjr on 2008-04-06
This sounds like a DNS problem to me. 

From a shell run: dig yourdomain.pl mx

In the 'answer section' you should see the hostname mail servers will be looking when searching for a mail server on your domain. You should see the IP address that hostname resolves to in the 'additional section'. If that is not the IP of the machine you are checking your mail on, then there's your problem. If the IP doesn't match, you need to change the 'A' record for the hostname the mx record points to to have the IP of your mail server.

-mhmjr

---

### Post by sarugaku on 2008-04-07
Hey, thanks fro reply mhmjr.

When i did dig mydomain.pl and dig mydomain.pl MX i received in Answer section sth like this:
mydomain.pl IN A [myipnumber]
while digging MX
mydomain.pl IN MX 10 mydomain.pl [i had no 'additional section']

How to improve on that?

---

### Post by sarugaku on 2008-04-07
Ok i improved my DNS settings - now i get sth like this:

;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 37259
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 1, ADDITIONAL: 2

;; QUESTION SECTION:
;;mydomain.pl.              IN      MX

;; ANSWER SECTION:
mydomain.pl.       38400   IN      MX      10 mail.mydomain.pl.

;; AUTHORITY SECTION:
mydomain.pl.       38400   IN      NS      ns1.mydomain.pl.

;; ADDITIONAL SECTION:
mail.mydomain.pl.  38400   IN      A       192.168.1.5
ns1.mydomain.pl.   38400   IN      A       192.168.1.5

;; Query time: 0 msec
;; SERVER: 192.168.1.5#53(192.168.1.5)
;; WHEN: Mon Apr  7 13:26:38 2008
;; MSG SIZE  rcvd: 105

Unfortunately mails still appear to get lost in the wide Internet.

---

### Post by sarugaku on 2008-04-13
I marked the topic as solved. I did some research over the net and studied a couple of interesting articles. It turned out that my mail server was not operational behind router, so i changed a bit its structure by introducing two network cards -> one for WAN / one for LAN - now i am able to send/receive mails all over the Net. Thanks for you suggestions, though!

---

