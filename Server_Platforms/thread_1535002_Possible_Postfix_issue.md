---
title: "Possible Postfix issue?"
date: 2010-07-20
forum: Server Platforms
---

### Post by vmikalinis on 2010-07-20
I recently found out that my company is unable to email another domain (giantoil.com) that we do business with.  I do not seem to be having problems with other domains yet they claim there is no problem on their end.  

The bounce comes back "mail for giantoil.com loops back to myself" which in the past has indicated a problem finding their domain and has always been on the receiving end.  I tried "telnet giantoil.com 25" which times out "trying 24.73.195.242".  I then tried on a different T1 line and different server and it again times out.  It seems that it's not possible to telnet to giantoil.com from anywhere.

Then I decided to ssh to my home server and telnet and again it times out.  I then tried sending a test email from my home server and it was received by their company.  I'm now confused because I thought the server should always answer a telnet on port 25 in order to deliver mail.  I've always gotten a response and I can type HELO and send a test.  I'm hoping someone can help me to resolve this issue and determine if it is indeed somehow on my end.  :(

A dig of bigoil.com MX returns:

[I]; <<>> DiG 9.2.4 <<>> giantoil.com mx
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 11445
;; flags: qr rd ra; QUERY: 1, ANSWER: 7, AUTHORITY: 2, ADDITIONAL: 4

;; QUESTION SECTION:
;giantoil.com.                  IN      MX

;; ANSWER SECTION:
giantoil.com.           3600    IN      MX      200 atl2.aspmx.1.google.com.
giantoil.com.           3600    IN      MX      300 aspmx2.googlemail.com.
giantoil.com.           3600    IN      MX      300 aspmx3.googlemail.com.
giantoil.com.           3600    IN      MX      300 aspmx4.googlemail.com.
giantoil.com.           3600    IN      MX      300 aspmx5.googlemail.com.
giantoil.com.           3600    IN      MX      100 aspmx.1.google.com.
giantoil.com.           3600    IN      MX      200 atl1.aspmx.1.google.com.

;; AUTHORITY SECTION:
giantoil.com.           344     IN      NS      extns1.nuvox.net.
giantoil.com.           344     IN      NS      extns2.nuvox.net.

;; ADDITIONAL SECTION:
aspmx2.googlemail.com.  3437    IN      A       74.125.43.27
aspmx3.googlemail.com.  3437    IN      A       72.14.213.27
extns1.nuvox.net.       318     IN      A       64.89.70.4
extns2.nuvox.net.       318     IN      A       64.89.74.4

;; Query time: 47 msec
;; SERVER: 127.0.0.1#53(127.0.0.1)
;; WHEN: Tue Jul 20 09:59:40 2010
;; MSG SIZE  rcvd: 333[/I]

I checked my domain against spam block lists and it's clean on the 20 or more lists checked.....and again, we email all over the without any problems.

At this point I'm not sure what else to check.  A great big thanks to anyone who can assist me in solving this mystery.

---

### Post by cdenley on 2010-07-20
Well, when email goes to [email]anyuser@giantoil.com[/email], it is not delivered to port 25 on giantoil.com. It is delivered to a sever that matches an MX record for the domain. It looks like the three highest-priority MX records have invalid hostnames. I think a standards-compliant mail server would eventually try one of the valid servers, but I don't know off the top of my head.
```

nc -z -v -w 5 aspmx.1.google.com 25
nc -z -v -w 5 atl1.aspmx.1.google.com 25
nc -z -v -w 5 atl2.aspmx.1.google.com 25
nc -z -v -w 5 aspmx2.googlemail.com 25
nc -z -v -w 5 aspmx3.googlemail.com 25
nc -z -v -w 5 aspmx4.googlemail.com 25
nc -z -v -w 5 aspmx5.googlemail.com 25

```

---

### Post by vmikalinis on 2010-07-20
Thanks cdenley, I appreciate you pointing me in the right direction.  

So I guess it's safe to assume that my server is not looking at the 4th mx record and stopping after finding the first 3 (or possibly 1st) hostname incorrect?  I do see "reject_invalid_hostname" in my smtpd_sender_restrictions which I assume to be self explanitory.

Postconf -n shows:

[I]smtpd_client_restrictions = hash:/etc/postfix/access, check_client_access hash:/etc/postfix/rbl-whitelist, permit_mynetworks,         reject_unauth_pipelining, reject_rbl_client zen.spamhaus.org, reject_unauth_destination

smtpd_recipient_restrictions = permit_mynetworks, reject_non_fqdn_sender, reject_non_fqdn_recipient, reject_unauth_pipelining,        reject_unauth_destination,

smtpd_sender_restrictions = hash:/etc/postfix/access-sender, reject_unauth_pipelining, reject_non_fqdn_sender, reject_non_fqdn_recipient, **reject_invalid_hostname**[/I]

---

### Post by cdenley on 2010-07-20
> **vmikalinis said:**
> So I guess it's safe to assume that my server is not looking at the 4th mx record and stopping after finding the first 3 (or possibly 1st) hostname incorrect?  I do see "reject_invalid_hostname" in my smtpd_sender_restrictions which I assume to be self explanitory.


I would think that it would get through eventually. I'm not sure how postfix works exactly. Maybe it will keep trying MX records until it finds one it can resolve, then try sending it. Maybe it tries a different MX record after it retries sending it periodically, and a failure to resolve the hostname results in a failed delivery.

I'm pretty sure "reject_invalid_hostname" is related to incoming mail, not outgoing mail, as an anti-spam measure.

---

### Post by vmikalinis on 2010-07-21
Oh ok, well I guess my server is giving up after the first or second invalid host because the mail is definitely not making it over to them.  I was having a lot of difficulty in finding information on how many mx records postfix will try.  A first and second...fine.  A 3rd and then 4th...I'm not so sure.  I would think that ultimately, they have to fix their mx record misconfiguration.

---

