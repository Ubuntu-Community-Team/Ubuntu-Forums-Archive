---
title: "bind9 MX records"
date: 2008-07-22
forum: Server Platforms
---

### Post by Geran on 2008-07-22
Hi,

I'm trying to set up and MX record on my DNS server to point to a system that I don't manage, google. 

The setup tells me that I have to create and MX record with the name of the server, and then have an A record with it. But I don't control the A records for this server, is there someway to create an MX record without an A record?

Maybe someone can give me an example of how to do this, the server I'm trying to point my MX record to...

aspmx.l.google.com

Pointers, ideas?

Thanks

---

### Post by windependence on 2008-07-22
Unless you have 100s of computers on your network and are a large enterprise, I don't see any reason for you to set up your own DNS server. It can only work internally anyway. To run an authoratative DNS server on the net, you need permission from certain to do this. 

If you own your own domain, you just need to use your registrar's DNS control panel to point your A record and MX record at your server. Running DNS on your local network will not help you here.

-Tim

---

### Post by Geran on 2008-07-22
I could just point my registrar's MX record to the needed server, but I also need to be able to host certain hosts within my domain. For example, instead of having only

"mydomain.com"

I need to be able to impliment

"myhost.mydomain.com"

I don't see how I can do this without running my own DNS server.

---

### Post by Fire_Chief on 2008-07-22
Are you talking about a local LAN domain setup similar to an Active Directory domain? If so, you should not use the external DNS name (mydomain.com) but instead should choose a non public top level domain such as mydomain.local or mydomain.prv, etc. This way you can have dns resolution for your local LAN and not run into conflicts trying to resolve names on the Internet.

Cheers!

---

### Post by Geran on 2008-07-22
No, not exactly like that.

Thanks for the help, I have found a good solution to this problem.

---

### Post by windependence on 2008-07-23
It would be nice, Geran if you would have posted the solution for the rest of the board. This helps the community.

-Tim

---

### Post by MJN on 2008-07-23
> **Geran said:**
> The setup tells me that I have to create and MX record with the name of the server, and then have an A record with it. But I don't control the A records for this server, is there someway to create an MX record without an A record?
 
All you need to do is put the MX records in - the A records for these MX records are held by Google.
 
> Maybe someone can give me an example of how to do this, the server I'm trying to point my MX record to...
 
aspmx.l.google.com
 
That's all you need to do - **example.com IN MX 10 aspmx.l.google.com**. The A record for aspmx.l.google.com is held by Google.
 
Mathew

---

### Post by songshu on 2008-07-23
maybe i mis the point here,

but what are you trying to accomplish here? why would you point a MX record to google? 

setting up a MX record (or A record) for google.com is the job of the owner of the domain google.com, and i doubt you are ;)

if you have all the mails for yourdomain.com directed to mail.google.com they would be bounced because google does not accept mail for [email]you@yourdomain.com[/email].

if you want all the mail sent to [email]you@yourdomain.com[/email] to end up at [email]you@google.com[/email] you would have to set up the mx record for yourdomain.com to your mailserver and then have your mailserver send it to [email]you@google.com[/email]



setting up the dns records can be done with your registrar or you could have the registrar make your own DNS server authorative for that domain.



but i might be wrong of course

---

### Post by MJN on 2008-07-23
> **songshu said:**
> why would you point a MX record to google? 
 
Google provides e-mail hosting as part of its Google Apps service.
 
Mathew

---

### Post by songshu on 2008-07-23
> **MJN said:**
> Google provides e-mail hosting as part of its Google Apps service.
 
Mathew

really??

you have a link?

---

### Post by MJN on 2008-07-23
There's some stuff about it [here](http://www.google.com/a/help/intl/en/users/gmail.html).
 
Mathew

---

### Post by windependence on 2008-07-23
Thanks, MJN, I never could figure out why people were trying to do this. OK but if they are provding mail hosting then why have your own server? I mean, my server receives mail for me and sends it directly from my box here to the recipient. Why would I want to do the Google thing?

-Tim

---

### Post by MJN on 2008-07-23
Choice I guess!

---

### Post by Geran on 2008-07-23
> **windependence said:**
> It would be nice, Geran if you would have posted the solution for the rest of the board. This helps the community.

-Tim

Yes, sorry, should have done that.

My solution was ALMOST mentioned here.

Simply create the MX record like so.

```


yourdomain.com. IN MX 10 aspmx.l.google.com.


```
Note the dots at the end of the domain name, the 10 is the priority of the server for receiving mail.

Cheers!

---

### Post by Geran on 2008-07-23
> **windependence said:**
> Thanks, MJN, I never could figure out why people were trying to do this. OK but if they are provding mail hosting then why have your own server? I mean, my server receives mail for me and sends it directly from my box here to the recipient. Why would I want to do the Google thing?

-Tim

Google provides pretty much one of the best web mail clients out there, possibly the best. Also, using g-mail you can integrate it with some of google's other apps, it's very useful.

Basic e-mail set-up is not that difficult, but getting a good web based client can be. That's why I'm on google right now.

---

### Post by Geran on 2008-07-23
One last note, discovering this solution was very useful to me, and it might be useful to others, perhaps this should be included in the references guide on help.ubuntu.com?

The same goes for CNAME records, I had some trouble with those too.

Example, trying to get something.yourdomain.com to point to destination.someotherdomain.com would be...

```


something.yourdomain.com. IN CNAME destination.someotherdomain.com.


```
It took me a while to dig that up.

---

