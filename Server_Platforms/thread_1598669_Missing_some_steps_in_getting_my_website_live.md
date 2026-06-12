---
title: "Missing some steps in getting my website live"
date: 2010-10-16
forum: Server Platforms
---

### Post by jshaw22 on 2010-10-16
hi guys:
Fished out my old linux computer from my closet and decided to get a website up and running. However, I cannot for the life of me figure this thing out and it's getting frustrating. I want to host my own website, this is more like a DIY experience rather than a money issue. 

I will attempt to outline and detail the steps I took, and I would appreciate it if the ubuntu community could point me in the right direction.

1.) I registered a domain name thru godaddy.com
2.) Because I am under a dynamic IP, I forwarded my IP to the freedns.afraid.org website. My nameservers are now NS1.afraid.org and NS2.afraid.org with my dynamic IP and domain attached to them. I then replaced the nameserver host in godaddy with this (yikes did I screw up here?)
3.) I installed LAMP thru a sudo tasksel, this seemed like the best way according to a quick search.  This is where I get confused. Where do I open it? :confused: How do I run this program? 

I already have a really basic index.php file ready to go. I just want to be able to see it when I type my domain in someone else's computer. I didn't realize it would be this hard :)

---

### Post by volkswagner on 2010-10-16
Assuming Apache2 is running, a basic test is needed.  Can you access your server by your external ip address?  Did you forward port 80 on your router to your server ip?  Did you confirm port 80 is not blocked by your isp using a site such as canyouseeme.org or shieldsup?

---

### Post by Ryan Dwyer on 2010-10-17
> Where do I open it? How do I run this program?

There is no graphical frontend to Apache. Assuming your server has a GUI (graphic interface), you can test it by opening a web browser and browsing to [http://localhost/](http://localhost/).

---

### Post by koenn on 2010-10-17
> **jshaw22 said:**
> 

1.) I registered a domain name thru godaddy.com
2.) Because I am under a dynamic IP, I forwarded my IP to the freedns.afraid.org website. My nameservers are now NS1.afraid.org and NS2.afraid.org with my dynamic IP and domain attached to them. I then replaced the nameserver host in godaddy with this (yikes did I screw up here?)
3.) I installed LAMP thru a sudo tasksel, this seemed like the best way according to a quick search.  This is where I get confused. Where do I open it? :confused: How do I run this program? 


2) test it by looking up your domain and/or your server - preferably on an other machine than your server, to avoid a local lookup
like so:
```
user@computer:~$ host ubuntuforums.org
ubuntuforums.org has address 91.189.94.12
ubuntuforums.org mail is handled by 10 mail.ubuntuforums.org.

```

Also consider volkswagner's questions



3) read [https://help.ubuntu.com/6.06/ubuntu/serverguide/C/httpd.html](https://help.ubuntu.com/6.06/ubuntu/serverguide/C/httpd.html)

---

### Post by James78 on 2010-10-18
1 and 2) To help you with BIND configuration (you'll need it if you're hosting your own nameservers, which I HIGHLY recommend for obvious reasons), check out [this]("http://ubuntuforums.org/showthread.php?t=1598245") topic.

P.S. ISP's HATE it when people host servers through a dynamic IP, which wasn't meant for servers. Sometimes they cut you off, etc. They can be pretty unforgiving. You should keep that in mind! And besides that fact, websites are really more suited to a static IP, as most dynamic IP's are automatically on blacklists (not because they spammed, but because they aren't supposed to be servers in the first place; speficially in spamhaus, which if it's not static, you're most likely on it, which can interfere with mail sending if people do RBL lookups to it. Also, hosts like Hotmail automatically deny mail sent from Dynamic IP's)

> **jshaw22 said:**
> ... I didn't realize it would be this hard :)
Yup! I self taught myself all of this.. Guess how long it took? At very least a couple of months. My first suggestion is, DON'T give up, because when you do, you'll never learn how to do it, but if you hang in there, you'll learn eventually if you keep trying. Google is your friend!

---

### Post by koenn on 2010-10-18
> **James78 said:**
> 
P.S. ISP's HATE it when people host servers through a dynamic IP, which wasn't meant for servers.  ... 

small small aside:

What most ISPs actually hate is when people run servers on residential connections. That those happen to have dynamic addresses is irrelevant in that perspective.


Most network admins and server admins prefer servers to have static addresses because for servers, dynamic addresses often require workarounds (like constant polling what the current address is), which add unnecessary complexity and increase the probability of things going wrong.

Mail server admins don't trust (other) mail servers on dynamic addresses because they know most of net/server admins prefer static addresses. So mail servers with dynamic addresses are more likely to be run by amateurs (and possibly more prone to exploits) or spammers, or are in fact spam bots running on PC's with a residential internet connection. That's why a lot of mail servers refuse to talk to them.

---

### Post by James78 on 2010-10-18
> **koenn said:**
> small small aside:

What most ISPs actually hate is when people run servers on residential connections. That those happen to have dynamic addresses is irrelevant in that perspective.
...
That's actually what I meant. I just didn't put it into words that correctly. ;)

---

### Post by SeijiSensei on 2010-10-18
> **koenn said:**
> What most ISPs actually hate is when people run servers on residential connections. That those happen to have dynamic addresses is irrelevant in that perspective.

Most residential ISP contracts forbid servers as part of the Terms of Service.

> [M]ail servers with dynamic addresses are more likely to be run by amateurs (and possibly more prone to exploits) or spammers, or are in fact spam bots running on PC's with a residential internet connection.

Nearly all of them fall into the spambot category.  The probability that a residential user will have any clue about how to run a local mailserver approaches zero.  If you ask nicely, some ISPs will allow you to send mail over port 25, because simply asking the question places you in the category of more informed users.  Still if you accept inbound mail, you're probably again violating your Terms of Service.

I routinely block all mail from machines with dynamic addresses and have for years.  From experience this policy has rarely led to false positives.  False positives have become progressively fewer as time goes on, since most ordinary users have migrated to free mail services or connect through their workplaces.

---

### Post by James78 on 2010-10-19
> **SeijiSensei said:**
> ... I routinely block all mail from machines with dynamic addresses and have for years.  From experience this policy has rarely led to false positives.  False positives have become progressively fewer as time goes on, since most ordinary users have migrated to free mail services or connect through their workplaces.
I'm interested in the configuration you have for that. :P

---

### Post by jshaw22 on 2010-10-19
Update. Okay, so I got my website live but I still don't know how to use that nameserver stuff.

What I did was just use my dynamic IP and put it into the Total DNS control. I guess as long as i don't shut down my computer it's all good. 

I then put my index.html along with some other files in the 'htdocs' file in my Apache software. I just wanted to view my website live from another computer and got what I achieved. Thanks for all the help. Hopefully my ISP doesn't catch me hosting... :P

BTW related question, and dunno if this belong's here or a new topic: How can I get email? Any quick-n-dirty methods? like [email]admin@example.com[/email]

thanks!

---

### Post by James78 on 2010-10-19
I'd suggest you use Webmin. It's like CPanel, except it's better, and the free GPL version isn't that slimmed down compared to the pro version (it's nearly the same actually). It'll setup a lot of this for you automatically, and the rest you can configure a lot more easily because it has a web interface.

---

### Post by SeijiSensei on 2010-10-19
> **James78 said:**
> I'm interested in the configuration you have for that. :P

I use an ancient store-and-forward SMTP proxy called [Obtuse SMTPD]("http://www.netsw.org/net/ip/firewall/proxy/smtpd/").  It has the ability to accept or deny SMTP connections based on the sender and recipient addresses and the sending SMTP server.  I have rules that block any mail from servers whose hostnames contain strings like "ppp" or "dhcp" or "dynamic".  I also have rules that require mail from places like paypal.com to come from an SMTP server in the paypal.com domain.  This cuts down on phishing attacks.

My current ruleset runs over 2,000 lines (including both whitelist and blacklist entries) yet it does not slow down SMTP exchanges much at all.

[Spamassassin]("http://wiki.apache.org/spamassassin/Rules/RCVD_IN_SORBS_DUL") also has rules for handling messages from servers with dynamic addresses.  Any system using [DNSBL blocklists](http://www.sorbs.net/) can implement this as well.

---

### Post by James78 on 2010-10-19
Heh, ya, I already made my own configuration. I haven't seen a single spam email get past the first filter lol. Ya gotta love these RBL's. (I took dnsbl.sorbs.net off, because it was rarely rejecting authentic email, for example, from Hotmail, but these rules should reject 90% of spam anyways)
```
# Security related config
smtpd_helo_required = yes
disable_vrfy_command = yes
smtpd_helo_restrictions =
    permit_mynetworks,
    reject_non_fqdn_hostname,
    reject_invalid_hostname
smtpd_recipient_restrictions =
    permit_mynetworks,
    permit_sasl_authenticated,
    reject_unauth_destination,
    reject_invalid_hostname,
    reject_unauth_pipelining,
    reject_non_fqdn_hostname,
    reject_non_fqdn_sender,
    reject_unknown_sender_domain,
    reject_non_fqdn_recipient,
    reject_unknown_recipient_domain,
    reject_rbl_client bl.spamcop.net,
    reject_rbl_client zen.spamhaus.org,
    reject_rbl_client combined.njabl.org,
    reject_rbl_client bhnc.njabl.org,
    reject_rhsbl_client rhsbl.sorbs.net,
    reject_rbl_client dul.dnsbl.sorbs.net,
    reject_rbl_client web.dnsbl.sorbs.net
    reject_rbl_client zombie.dnsbl.sorbs.net
    reject_rbl_client dnsbl.ahbl.org,
    reject_rhsbl_client rhsbl.ahbl.org
    permit
```

---

### Post by James78 on 2010-10-19
> **jshaw22 said:**
> Update. Okay, so I got my website live but I still don't know how to use that nameserver stuff.

What I did was just use my dynamic IP and put it into the Total DNS control. I guess as long as i don't shut down my computer it's all good. 

I then put my index.html along with some other files in the 'htdocs' file in my Apache software. I just wanted to view my website live from another computer and got what I achieved. Thanks for all the help. Hopefully my ISP doesn't catch me hosting... :P

BTW related question, and dunno if this belong's here or a new topic: How can I get email? Any quick-n-dirty methods? like [email]admin@example.com[/email]

thanks!
Use Postfix (mail server) for emailing and Dovecot (imap, pop3, etc) for client access. You'll probably want to use a relay for Postfix, because, like I said earlier, sending mail from a dynamic IP isn't a good idea. I'm sure dyndns allows MX records.. But you might have to pay for that specific service :/ . Anyways, that link I gave you about BIND is very helpful for when trying to understand how to setup DNS, in fact, it practically gives you the instructions on how to make a domain name point to you, although remember that if you're on a dynamic IP, and it keeps changing, then you'd have to keep changing the IP with your domain name provider, of course, places like DynDNS have programs that'll automatically update your IP to their DNS, and keep it pointing to you, but that's not a "real" domain name then again :(

You could point godaddy to your automatic updating DNS, but I can't live with thinking it's not going directly too me, performance stuff keeps going through my head. Anyways, there's many options, it'd take too long to list them all! A bottom line is, you really don't need to do BIND if you're not using your own domain name, e.g. letting DynDNS take care of the DNS for you. Some of these services even let you buy a domain name with them, and they host the DNS for you. I'm sure you'll find what best fits you.

P.S. Sorry for the long post. Oh, and somehow I got stuck on DynDNS even though you clearly stated it's totalDNS, >.<

---

