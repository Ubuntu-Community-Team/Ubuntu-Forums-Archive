---
title: "Citadel mailserver probs"
date: 2011-01-16
forum: Server Platforms
---

### Post by ivanflo on 2011-01-16
Hi,
First I'm from belgium, trying te write english, so I do appligize for my writting errors.
 
I installed a ubuntu LAMP server 10.10
Afterwords I instelled a Citadel server.
I can send and recieve mail in my own LAN. I can send mail towards an extern mailadres.
Anybody can send mails towards my mail address.
 
Now the big riddle:
I recieve a mail, I read it in mthe citadel browser, I want to repley.
The text that I wrote is gone! The other person recieves HIS mail only with an RE: messagetitle as sublect, but not the body or message.
 
Whan I lok in the sent Items I see the mail as the reciever can read it: no contence from me.
 
To put additional info: I live in Belgium, my provider is TELENET.
This ISP blocks all ports to 1024. (my webserver runs on port 8080, and my citadel runs at port 2080) the ports for recieveing en sending mail (25 and 110 are in the blocked zone)
My citadelserver is directly connected to the internet (without a firewall, not even in the mailserver. this is for test purposes
 
As soon it works as it should be, ik will place it behind a firewall. With all the nessecary redirects.
 
To be short, whan I repley from a mail, I don't see anythin in my send items neither sees the other person the contents if the mail.
 
Thanks in advance

---

### Post by ivanflo on 2011-01-17
on the [http://www.aeronetworks.ca/howtos/citadel-basics.html](http://www.aeronetworks.ca/howtos/citadel-basics.html) I found tose commands:
Test the DNS settings with dig:
Forward:# dig example.comMX:# dig example.com MXReverse:# dig example.com PTRHere are my results, 'caus I cannot make any sence out of them (Yes, i'm a noob, trying to find my way ...)
 
> 
 
dig hetmosterdzaadje.be PTR && dig hetmosterdzaadje.be MX && dig hetmosterdzaadje.be
gives me
[EMAIL="root@mailbuntu"]root@mailbuntu[/EMAIL]:~# dig hetmosterdzaadje.be PTR && dig hetmosterdzaadje.be MX && dig hetmosterdzaadje.be
; <<>> DiG 9.7.1-P2 <<>> hetmosterdzaadje.be PTR
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 15695
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 0, ADDITIONAL: 0
;; QUESTION SECTION:
;hetmosterdzaadje.be.           IN      PTR
;; Query time: 19 msec
;; SERVER: 195.130.130.133#53(195.130.130.133)
;; WHEN: Mon Jan 17 10:27:02 2011
;; MSG SIZE  rcvd: 37

; <<>> DiG 9.7.1-P2 <<>> hetmosterdzaadje.be MX
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 25468
;; flags: qr rd ra; QUERY: 1, ANSWER: 2, AUTHORITY: 0, ADDITIONAL: 0
;; QUESTION SECTION:
;hetmosterdzaadje.be.           IN      MX
;; ANSWER SECTION:
hetmosterdzaadje.be.    10800   IN      MX      50 mx.backup.mailprotect.be.
hetmosterdzaadje.be.    10800   IN      MX      10 mx.mailprotect.be.
;; Query time: 19 msec
;; SERVER: 195.130.130.133#53(195.130.130.133)
;; WHEN: Mon Jan 17 10:27:02 2011
;; MSG SIZE  rcvd: 94

; <<>> DiG 9.7.1-P2 <<>> hetmosterdzaadje.be
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 46321
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0
;; QUESTION SECTION:
;hetmosterdzaadje.be.           IN      A
;; ANSWER SECTION:
hetmosterdzaadje.be.    2583    IN      A       194.150.224.122
;; Query time: 9 msec
;; SERVER: 195.130.130.133#53(195.130.130.133)
;; WHEN: Mon Jan 17 10:27:02 2011
;; MSG SIZE  rcvd: 53

 

 
Those are acual reading

---

