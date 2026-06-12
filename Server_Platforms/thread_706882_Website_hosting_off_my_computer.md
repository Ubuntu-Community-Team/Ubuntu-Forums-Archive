---
title: "Website hosting off my computer"
date: 2008-02-24
forum: Server Platforms
---

### Post by Shanebob on 2008-02-24
Well, I have no idea how this happened, or what it means, but here goes.  I'll try and explain this as best as I can.

A while ago I set up my own localhost server; apache2, MySQL, PHP5, etc.  Today, an email account of mine apparently was hacked or phished, but it's an old one I don't use for anything except IM.  This would seem unrelated, but somehow a hate email got sent out denouncing Christianity.  I had also gotten an email in that account that said this:
```
To combat SPAM I use a whitelist service on my e-mail account.

Your message (attached) is not being delivered because the address
<mrshanebob@yahoo.com> has not yet been verified.

To verify, simply respond to this message using "RE".  In doing so,
you will verify that your e-mail is not SPAM.  Your e-mail will be
delivered and you will be added to my whitelist for future use.

You can add yourself to my whitelist without using "RE" by sending
a blank e-mail to:

  msmith+confirm+1203901508.16609.a4f179@foep.net

You should only have to confirm your address once.

If you do not respond to this confirmation request within
14 days, your message will not be delivered.

Thank you.


-----Inline Message Follows-----
--hate email denouncing Jesus here--
```
Curiosity getting the better of me, I go to the website, foep.net.  Lo and behold, I find the contents of my localhost server.  I changed the name of the folder I had in it to see, refreshed the page, and sure enough, it was my server.  Once I found this out, I stopped apache, so the site is not up now.

From there, I did a whois lookup, and it was registered through godaddy.com, but apparently by nobody.

As well as all this, my facebook account had been tampered with, saying things similar to the email that was sent, and changing the password.  I'm guessing all of this is related, but I don't know how, or why.  I'm thoroughly confused.  Can anyone offer me some insight?

---

### Post by Mr. C. on 2008-02-24
> **Shanebob said:**
> Well, I have no idea how this happened, ...
 but I don't know how, or why.  I'm thoroughly confused.  Can anyone offer me some insight?

If that email which appears to have come from your account didn't actually have a valid email address (from your server), it is likely just backscatter (aka: joe job).  You can ignore that.

Anyone can register a domain name, and point it at any host address they want.  Being able to reach your own site by some unfamiliar domain does not mean your accounts were hacked.  You can check the DNS A record(s) to determine the IP address, and if necessary, just block incoming requests that contain said domain's in the URL.

If your accounts were actually hacked...I've got some unpleasant news for you.  Its time to start from scratch and understand the fundamentals before installing, configuring and deploying these types of highly complex services.

[LIST]
[*]ASSUME that your passwords are now known.
[*]ASSUME that your account(s) and system(s) are compromised, likely in ways you won't be able to detect
[*]ASSUME that you need to reinstall.
[/LIST]

Let's hope its the former explanation, and not the latter.
MrC

---

### Post by Shanebob on 2008-02-24
> **Mr. C. said:**
> If that email which appears to have come from your account didn't actually have a valid email address (from your server), it is likely just backscatter (aka: joe job).  You can ignore that.

Anyone can register a domain name, and point it at any host address they want.  Being able to reach your own site by some unfamiliar domain does not mean your accounts were hacked.  You can check the DNS A record(s) to determine the IP address, and if necessary, just block incoming requests that contain said domain's in the URL.

If your accounts were actually hacked...I've got some unpleasant news for you.  Its time to start from scratch and understand the fundamentals before installing, configuring and deploying these types of highly complex services.

[LIST]
[*]ASSUME that your passwords are now known.
[*]ASSUME that your account(s) and system(s) are compromised, likely in ways you won't be able to detect
[*]ASSUME that you need to reinstall.
[/LIST]

Let's hope its the former explanation, and not the latter.
MrC

Well, my facebook account had the password changed multiple times, and information edited.  And the Yahoo email address had the password changed once.
I've figured out now that I get those emails in my account when I try and send out an email...To me that seems like my accounts were hacked...But I obviously don't know too much on this.

Also, why would someone register a domain name and point it to an IP address that they didn't have access to?

I sent godaddy an email about it, I hope that'll be of some help.  Can you elaborate a little more about the 'DNS A record(s)', please?  I'm not sure I follow...

---

### Post by Mr. C. on 2008-02-24
> **Shanebob said:**
> Well, my facebook account had the password changed multiple times, and information edited.  And the Yahoo email address had the password changed once.
I've figured out now that I get those emails in my account when I try and send out an email...To me that seems like my accounts were hacked...But I obviously don't know too much on this.

Ok, sounds like you need to start from a clean slate.  Make sure your passwords are *strong* passwords, and assume your systems have been hacked and compromised (eg. w/keyloggers, etc) until you satisify yourself that they are not.

> **Shanebob said:**
> 
Also, why would someone register a domain name and point it to an IP address that they didn't have access to?
They then control the domain name/URL of the host, which they can trivially change at their convenience to suit their zombie/bot scripts.  And if they've compromised your system, all those bot-infected systems are hitting your system.  When you've wised up and figured out that intrusion, and close the doors, the script deployers just change the hostname->IP address mapping in DNS - and voila, someone else's system then takes the heat.

> **Shanebob said:**
> 
I sent godaddy an email about it, I hope that'll be of some help.  Can you elaborate a little more about the 'DNS A record(s)', please?  I'm not sure I follow...

On your system, enter:

```
dig A *thebogusFQDN*
```

where *thebogusFQDN* is the fully qualified hostname you found you could use to access your site.  It will return the IP address.  If it is yours, you've confirmed what we've been discussing.  If it is someone else's, then either you were mistaking originally in your test, or it has been changed (and you can look at the last change time of that resource in DNS too).

MrC

---

### Post by Shanebob on 2008-02-24
> **Mr. C. said:**
> Ok, sounds like you need to start from a clean slate.  Make sure your passwords are *strong* passwords, and assume your systems have been hacked and compromised (eg. w/keyloggers, etc) until you satisify yourself that they are not.
Alright, which passwords are you talking about, system or website passwords?  I believe I've changed all the passwords for any website I've used that had been gotten into, but if I need to change my system password, I can do that.

> **Mr. C. said:**
> They then control the domain name/URL of the host, which they can trivially change at their convenience to suit their zombie/bot scripts.  And if they've compromised your system, all those bot-infected systems are hitting your system.  When you've wised up and figured out that intrusion, and close the doors, the script deployers just change the hostname->IP address mapping in DNS - and voila, someone else's system then takes the heat.
I'm guessing I would go about doing that by changing passwords?

> **Mr. C. said:**
> On your system, enter:

```
dig A *thebogusFQDN*
```

where *thebogusFQDN* is the fully qualified hostname you found you could use to access your site.  It will return the IP address.  If it is yours, you've confirmed what we've been discussing.  If it is someone else's, then either you were mistaking originally in your test, or it has been changed (and you can look at the last change time of that resource in DNS too).

MrC
Alright, I did that, and this is what I got
```
; <<>> DiG 9.4.1-P1 <<>> A foep.net
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 33954
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 2, ADDITIONAL: 2

;; QUESTION SECTION:
;foep.net.                      IN      A

;; ANSWER SECTION:
foep.net.               7083    IN      A       0.0.0.0

;; AUTHORITY SECTION:
foep.net.               7083    IN      NS      ns7.zoneedit.com.
foep.net.               7083    IN      NS      ns8.zoneedit.com.

;; ADDITIONAL SECTION:
ns7.zoneedit.com.       720     IN      A       216.122.7.155
ns8.zoneedit.com.       24949   IN      A       75.125.10.187

;; Query time: 47 msec
;; SERVER: 192.168.2.1#53(192.168.2.1)
;; WHEN: Sun Feb 24 22:18:02 2008
;; MSG SIZE  rcvd: 122
```
I don't know what to make of it, though...But I do know that my IP address is not in there.

EDIT: Minor correction...The IP address after 'SERVER' is my wireless router's IP...I don't know if that makes a difference or not.  Also, (again, not certain if this matters), it's an open network.

---

### Post by Mr. C. on 2008-02-25
> **Shanebob said:**
> Alright, which passwords are you talking about, system or website passwords?  I believe I've changed all the passwords for any website I've used that had been gotten into, but if I need to change my system password, I can do that.

I can't answer that question, as there is some element of closing the barn door after the cows gone out.   Rather, I can give you something to consider, only which you can answer for your own comfort level.  How do you: a) know which system or service was hacked/infiltrated, b) know how it was compromised, and c) ensure that there is no more malicious presence (eg. no backdoors, rootkits, keyloggers, etc.).

> **Shanebob said:**
> 
I'm guessing I would go about doing that by changing passwords?
I'm not following your question here.  I answered your question "why would someone want to..." point their domain name at my server's IP address.  I'll reiterate with an illustrative example.  Bad Guy creates a bot script that is placed on infected systems worldwide. Script essentially downloads Trojan files from hackedsite1.com, hackedsite2.com, etc., all domain names owned by Bad Guy.  Bad Guy finds weak systems, infiltrates them, and then just changes the IP address associated with hackedsite1.com, etc, so that they point to hacked systems.  Scripts all over the internet are now downloading from distributed, ever changing hacked servers.  When a server's hole is closed, Bad Guy just changes the DNS A record for the now closed server.

> **Shanebob said:**
> 
Alright, I did that, and this is what I got
```
; <<>> DiG 9.4.1-P1 <<>> A foep.net
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 33954
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 2, ADDITIONAL: 2

;; QUESTION SECTION:
;foep.net.                      IN      A

;; ANSWER SECTION:
foep.net.               7083    IN      A       0.0.0.0

;; AUTHORITY SECTION:
foep.net.               7083    IN      NS      ns7.zoneedit.com.
foep.net.               7083    IN      NS      ns8.zoneedit.com.

;; ADDITIONAL SECTION:
ns7.zoneedit.com.       720     IN      A       216.122.7.155
ns8.zoneedit.com.       24949   IN      A       75.125.10.187

;; Query time: 47 msec
;; SERVER: 192.168.2.1#53(192.168.2.1)
;; WHEN: Sun Feb 24 22:18:02 2008
;; MSG SIZE  rcvd: 122
```
I don't know what to make of it, though...But I do know that my IP address is not in there.

EDIT: Minor correction...The IP address after 'SERVER' is my wireless router's IP...I don't know if that makes a difference or not.  Also, (again, not certain if this matters), it's an open network.

So you can see the A record for that domain has the "this network" address of 0.0.0.0.  It is currently useless.  But it has a very short Time To Live, and so DNS resolvers around the world will re-lookup the A record very soon.  But it could have been pointing at your web server previously - no way for you to know.

MrC

---

