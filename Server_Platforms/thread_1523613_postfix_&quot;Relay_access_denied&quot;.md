---
title: "postfix &quot;Relay access denied&quot;"
date: 2010-07-03
forum: Server Platforms
---

### Post by rekahsoft on 2010-07-03
Hi all, i have been working on setting up an email server over a ddns. All seems to be working (i can email [email]me@my_ddns_domain.com[/email] to [email]me@my_ddns_domain.com[/email]) except that when i try and send to another email address (some_other_me@other_host.com) i get the error "5.7.1 Relay access denied". The way i tested this is as follows:```
me@my_ddns_domain:~/$ netcat my_ddns_domain.com 25
220 my_ddns_domain.com ESMTP Postfix (Ubuntu)
ehlo localhost
250-my_ddns_domain
250-PIPELINING
250-SIZE 10240000
250-VRFY
250-ETRN
250-STARTTLS
250-AUTH PLAIN LOGIN
250-AUTH=PLAIN LOGIN
250-ENHANCEDSTATUSCODES
250-8BITMIME
250 DSN
mail from: me@my_ddns_domain.com
250 2.1.0 Ok
rcpt to: some_other_me@some_other_host.com
554 5.7.1 <some_other_me@some_other_host.com>: Relay access denied
quit
221 2.0.0 Bye
``` Is this my isp doing something funky or is it something wrong with my setup? Thanks for readin! :)

---

### Post by DJYoshaBYD on 2010-07-03
that sounds like 2 things

1 - your ISP doesnt support DNS relay

2 - you dont have a static IP with reverse DNS set up

---

### Post by rekahsoft on 2010-07-03
> **DJYoshaBYD said:**
> that sounds like 2 things

1 - your ISP doesnt support DNS relay

2 - you dont have a static IP with reverse DNS set up

nope no static ip..i am going it through ddns...so basically my linksys router is running dd-wrt and is using a dynamic dns...thus every time rogers changed my dhcp assigned ip the regestrar is updated...as for the no dns relay..how can confirm this? do i have any options?

---

### Post by DJYoshaBYD on 2010-07-03
for the server relay, no.. you cannot get them to change that.. that is a global setting on their servers, and thats that.. lol.. i can say 100% they will not change it.. which sucks, but blame that **** on spammers.. thats why we have to lock down our mail and dns servers.. lol

for the other thing.. do this.. ask your ISP for a static IP.. I think its only an extra 10 per month, so something like that.. if even that.. VZN sucks.. i deal with them multiple times per day.. :(

so, here is what you do

get a static IP

tell them you need a reverse DNS record, or PTR, on your IP.. 

for instance

"hello.. this is verizon.. we suck.. how can we try to help?"

you - "yes.. i would like you to but a reverse DNS record on my IP please. I need mydomain.com pointed to my static IP, which is x.x.x.x"

thats pretty much it.. if you have a static, they can hook you up with rDNS, then you will be allllllllll good for mail..

PM me if they give you any guff.. lol

---

### Post by DJYoshaBYD on 2010-07-03
ps

DD-WRT FTW!!!!!!!!!

---

### Post by lisati on 2010-07-03
In the smtpd_recipient_restrictions entry of postfix's main.cf file, do you have "permit_mynetworks" listed?

---

### Post by DJYoshaBYD on 2010-07-03
how would that cause a server relay error?

a server relay error would come from the ISPs DNS servers, which are DHCPd to the end-user.. i could see that happening with a dynamic IP, and dynamic DNS.. 

im not disagreeing.. I am just asking..

---

### Post by lisati on 2010-07-03
I've had "relay access denied" on my fully-functioning copies of postfix when I've messed up the contents of the recipient restrictions and then tried to send email. :)

Another idea to consider, which might be closer to what's happening: I also get "relay access denied" when I've tried a plain smtp connection from Thunderbird or Evolution and I've forgotten something in the settings like enabling TLS/SSL/whateve.

---

### Post by rekahsoft on 2010-07-03
dd-wrt is great :) i always look to buy routers that support it :P..that or openwrt..and really the only way to do it is get a static ip? i can't manage it through my ddns setup? Can you explain why DJYoshaBYD? feel free to go into great detail..i really would prefer it :P

---

### Post by DJYoshaBYD on 2010-07-03
ok.. lol.. for sure..

i was confused, cause i do that stuff at work, and its usually us.. haha

i have seen issue where ssl and whatnot will cause that, but usually i see SSl and all that coming back as either "protocol not supported" or "connection denied" or something like that..

for sure, check that stuff as well...

---

### Post by rekahsoft on 2010-07-03
> **lisati said:**
> In the smtpd_recipient_restrictions entry of postfix's main.cf file, do you have "permit_mynetworks" listed?

yes i do..so thats not the issue :S

---

### Post by DJYoshaBYD on 2010-07-03
> **rekahsoft said:**
> dd-wrt is great :) i always look to buy routers that support it :P..that or openwrt..and really the only way to do it is get a static ip? i can't manage it through my ddns setup? Can you explain why DJYoshaBYD? feel free to go into great detail..i really would prefer it :P

**takes deep breath**

ok.. so the fact of the matter is, that most email servers will require the IP address to resolve to a PTR with a URL of a server.. for instance

when you go to a website, this happens

type your URL

yahoo.com

goes to the DNS server, and gets the IP

1.1.1.1 (just for example)

then you get the page..

reverse DNS does exactly the opposite..

it takes an IP address and binds it to a host name.. like

lets say your dynamic IP address is 1.2.3.4

your rDNS for that (on the ISPs side) would be something kinda like

4.3.2.1.arpa.net

or something like that.. every ISP does it different, following a certain convention.. (this is just explanation.. dont worry about that part too much)

Servers like DNS and EMAIL servers, if they have whatever spam protection they have running (too many to list), will not accept email from IP addresses that do not have rDNS entries (which is why you need a static, unchanging IP)...

again, all that **** is for spam protection through networks.. you would not believe how big of an issue spam is on our side (the ISP/Security guys).. haha

I hope this kinda clears it up..

check that file like the admin told you, and if you are good there, then you need rDNS.. im willing to bet that is it...

:D

**passes out, bluefaced**

---

### Post by DJYoshaBYD on 2010-07-03
ps.. you no longer need DynDNS if you have a static.. lol

I actually use [http://freedns.afraid.org/](http://freedns.afraid.org/)

usually, when you make actual ZONE file changes to your DNS records with your ISP, it will take up to 24 hours to propagate out to the rest of the world, as most ISPs DNS servers dont update on the fly.. theirs does.. i see changes as soon as they are submitted.. WAY less than 1 minute

---

### Post by rekahsoft on 2010-07-04
** attempts to revive DJYoshaBYD **

one last question for you..why wouldn't i have a rDNS if i have a dynamic ip?

---

### Post by DJYoshaBYD on 2010-07-04
because a rDNS entry is tied directly to an IP address...

check it..

run the following command in the terminal of your choice

```
whois 4.2.2.2
```

if you look through that, it will tell you who owns that IP address..

now, you have to think about this

email and dns servers need to know that your IP of your server (1.2.3.4), is ACTUALLY YOU.. if they put an rDNS record on this IP for you, it will break as soon as your IP changes..

the common way that all ISPs rDNS their stuff, is so that it points to THEM (the ISP), not you, the End User..

With a static, the ISP acutally KNOWS and has record of who is using that IP, because it is tied to your domain..


sooooooooo


if you start spamming from your server, which is imadick.com, and someone reports it, they can track it down to the IP, and eventually the EU.. most of the time..

sad thing is, its all done because of spammers.. its just a security thing, and that is how you get around it :(

---

