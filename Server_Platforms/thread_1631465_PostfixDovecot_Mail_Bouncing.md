---
title: "Postfix/Dovecot Mail Bouncing"
date: 2010-11-26
forum: Server Platforms
---

### Post by Briffy on 2010-11-26
Hey everyone,

I've recently decided to set up mail on my server. I followed a guide that I can't find anymore to set up Postfix/Dovecot.

It all seems to working fine, except for aliases/virtual users. I've got multiple domains on the box. I have the user "rhys" set up and any mail sent to [email]rhys@domain1.co.uk[/email] and [email]rhys@domain2.co.uk[/email] go to that user. However, I want mail to [email]rhys@domain1.com[/email] to go to a dfferent user than [email]rhys@domain2.com[/email].

I created the users [email]rhys@domain1.com[/email] and [email]rhys@domain2.com[/email] and set it up in the virtusertable to send mail to each. However, the mail still continues to be delivered to the rhys user. I've tried deleting that user and then mail just bounces saying that the user is unknown.

If you need any logs or configs, let me know.

Any help would be super appreciated. :D


Edit: It would seem that postfix is reading the virtusertable... If I change it to:

```
rhys@domain1.com rhys@domain1.com@localhost
```

Then it bounces back with this:

```
<"rhys@domain1.com"@localhost> (expanded from
   <rhys@domain1.com>): Host or domain name not found. Name service
   error for name=localhost type=AAAA: Host not found
```

This is driving me insane. :(

---

### Post by SeijiSensei on 2010-11-27
The error suggests domain1.com doesn't exist in the Domain Name Service.  Does it?  If it does, does the primary MX record for the domain point to your server?  Is Postfix configured to accept mail for the domain?

---

### Post by Briffy on 2010-11-27
Thanks for the reply, SeijiSensei.

I believe domain1.com is set up properly and I have created MX records for it. Seeing as I can get mail delivered to the domain, just to the wrong user, wouldn't that suggest the domain is set up correctly and Postfix can receive mail for it?

I'm thinking it might be something to do with my hosts file but I'm not sure how that should look, to be honest. I know there were errors for NIS lookup at one point. I stopped that by getting Postfix to use the local hosts file though. 

I'll see if changing the hosts file helps any while I wait for a reponse.

---

### Post by windependence on 2010-11-27
For a mailserver to work properly, DNS must be absolutely correct. 
 
Please post the output of :
 
```
 
sudo hostname

``` 
and 
 
```
dig domain1.com any
```
 
 
I'm assuming your domain is not really domain1. If so, you will have problems because there are no real DNS records for it.
 
-Tim

---

### Post by Briffy on 2010-11-27
Here's what those commands give me:

```
root@localhost:~# hostname
localhost
root@localhost:~# dig briffscomputers.co.uk any

; <<>> DiG 9.7.0-P1 <<>> briffscomputers.co.uk any
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 11406
;; flags: qr rd ra; QUERY: 1, ANSWER: 5, AUTHORITY: 2, ADDITIONAL: 2

;; QUESTION SECTION:
;briffscomputers.co.uk.         IN      ANY

;; ANSWER SECTION:
briffscomputers.co.uk.  10800   IN      A       66.197.135.210
briffscomputers.co.uk.  10800   IN      MX      10 mail.briffscomputers.co.uk.
briffscomputers.co.uk.  10800   IN      SOA     ns.heartinternet.co.uk. hostmaster.mainnameserver.com. 2010102382 86400 604800 2419200 10800
briffscomputers.co.uk.  10800   IN      NS      ns2.heartinternet.co.uk.
briffscomputers.co.uk.  10800   IN      NS      ns.heartinternet.co.uk.

;; AUTHORITY SECTION:
briffscomputers.co.uk.  10800   IN      NS      ns.heartinternet.co.uk.
briffscomputers.co.uk.  10800   IN      NS      ns2.heartinternet.co.uk.

;; ADDITIONAL SECTION:
mail.briffscomputers.co.uk. 10800 IN    A       66.197.135.210
ns.heartinternet.co.uk. 9499    IN      A       79.170.40.2

;; Query time: 106 msec
;; SERVER: 66.96.208.21#53(66.96.208.21)
;; WHEN: Sat Nov 27 17:47:41 2010
;; MSG SIZE  rcvd: 250

```

---

### Post by windependence on 2010-11-27
OK looks like your DNS and MX records are good. You may want to set up reverse DNS at your registrar or ISP because some mail servers will not talk to you if they cannot resolve your IP to a domain name.
 
Now we need to know the output of:
 
```
 
hostname -f

``` 
Please post the output for us.
 
-Tim

---

### Post by Briffy on 2010-11-27
Here's what I've got:

```
root@localhost:~# hostname -f
hostname: Name or service not known
```

---

### Post by windependence on 2010-11-27
Sorry, my bad, should be:
 
```
 
hostname --fqdn

```
 
-Tim

---

### Post by Briffy on 2010-11-27
I get exactly the same message back. :S

---

### Post by windependence on 2010-11-27
Can you post the contents of your /etc/hostname file?
 
-Tim

---

### Post by Briffy on 2010-11-27
Here you go:

```
root@localhost:/etc/postfix# cat /etc/hostname
briffynet.com

```

---

### Post by windependence on 2010-11-27
You need to change this to mail.briffscomputers.co.uk
 
-Tim

---

