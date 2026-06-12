---
title: "PTR for dynamic IP and Postfix's hostname setting"
date: 2008-07-26
forum: Server Platforms
---

### Post by skunkbad on 2008-07-26
Ubuntu Server 8.04
Postfix

I finally got "The book of postfix", and within the first night of reading I already discovered potential problems for my postfix installation. One potential problem was that my hostname was set to "localhost", which isn't a FQDN. I was also reading that my WAN IP needs to have a PTR equal to the same FQDN, so I digged my IP address, looked at the PTR, and since I am on a dynamic IP, it is something like:

234-34-54-101.myispdomain.com

so I was wondering if this is what I should set as my hostname? How are others setting their hostname for dynamic IP email servers? I know in the real world of email servers, people don't have dynamic IPs, but I'm just learning with what I've got.

Thanks

---

### Post by skunkbad on 2008-08-01
I'm still seeking an answer to this question. If any postfix gurus can answer the question, i'd be very happy.:)

---

### Post by windependence on 2008-08-01
Well Brian, I have a static IP address and own my domain but if it helps here is how mine is set up:

myhostname = tiburon.dominicanstotheusa.com

If you are only using your server to send mail out, you can use your own made up domain name as long as all your network stuff, DNS, hosts file, etc are set to the same thing. For exapmle:

myserver.mydomain.nix

should work for just sending mail out. It just has to be the real FQDN of the server.

I'm not sure what a PTR is so if you could spell that one out for the acronym challenged I might be able to help you with that.

Still no luck with a static IP huh?  Where do you live?

-Tim

---

### Post by windependence on 2008-08-01
Never mind on thr PTR, seems that's just reverse DNS. That needs to be set up with your ISP and since you can't do that some mail servers aren't going to accept your mail.

Another good argument for a static IP. You should have one anyway if you are in the web design biz. ;)

-Tim

---

### Post by StickyStyle on 2008-08-01
How are you sending your mail?  It it going though a relay host, or are you trying to deliver mail directly to the destination server?  With one scenario (relay host), not having reverse DNS and naming your machine localhost doesn't matter.  In the other scenario it does matter.

Post the output of ```
$postconf -n
```

---

### Post by windependence on 2008-08-01
> **StickyStyle said:**
> How are you sending your mail?  It it going though a relay host, or are you trying to deliver mail directly to the destination server?  With one scenario (relay host), not having reverse DNS and naming your machine localhost doesn't matter.  In the other scenario it does matter.

Post the output of ```
$postconf -n
```

Exactly.

Sticky, I think he is sending directly. I could never see any use for relaying mail. Why not just directly use their smtp server and get it over with? ;)

-Tim

---

### Post by skunkbad on 2008-08-01
OK, I see what you guys are saying. I am just trying to learn all aspects of linux web server/email server. I am relaying my own mail, and it makes it through to google and yahoo, which are the only ones I've tested. Right now my PTR shows my dynamic IP with ISP, and not $mydomain, so I'm sure that some email would not get through.

I know the answer is to get a static IP, but I was just interested to see if it could be done with a dynamic IP.

Thanks for the replies.

---

### Post by StickyStyle on 2008-08-01
The thing with reverse DNS is the creation of the PTR records is in the hands of your ISP, not something you can do on your own.  I can pretty much guarantee that your ISP will never create a PTR record for your domain while on a dynamic IP address, sometimes they make it a pain while on a static IP.  

Quite honestly your **so much** better off just setting your relay host config option in postfix to relay your mail through your ISP rather than directly sending it to the recipient because many mail servers (mine for sure) will reject your mail if it is coming from a dynamic IP block since 9 times out of 10 that mail is going to be from a zombie windows box trying to spam me.

Also, since I'm guessing the question will come next...If you want to setup your own domain to **recieve** mail while on your dynamic IP address, look into the dynamic dns servers like [http://www.dyndns.com/](http://www.dyndns.com/) to host your DNS.

You can accomplish having your own domain sending and receiving mail without spending the extra $$ on a static IP with a little ingenuity.

---

### Post by skunkbad on 2008-08-02
StickyStyle,

I wasn't trying to get the ISP to change the PTR, but as I was reading the book of Postfix, it was making a big deal about PTR, but didn't mention what to do for a dynamic IP.

I've got Postfix running with multiple domains, multiple users, and all is well. I just have some questions as I read this book. For instance, if a user was on a business trip, and at a hotel, and trying to relay an email through my server to external_domain.net, my current Postfix installation won't allow that email to be relayed because the hotel's IP isn't listed in mynetworks. I'm not trying to hijack my own thread, but I do have questions like this that have not been answered while reading the book of Postfix.

I already use zoneedit.com to handle the DNS/MX. The only issue with DNS seems to be within my server itself. While everything seems to work, Apache2 does send me an email that says that it can't find a fully qualified domain name and is using localhost as servername. This really doesn't cause the server itself to have any problems, so I'm not concerned so much with this.

Windependence,

I'm not going to ask my ISP for a static IP, because it costs $10 a month extra, and I really am only testing this server. It only has parked/advertising domains on it, and all of the users are myself. Just trying to learn, and having fun with it!

Thanks.

---

### Post by windependence on 2008-08-02
Well you can see the hassles involved with using dynamic IPs for production work, so I think you did learn something already. My ISP only charges $4.95 a month for one and $14.95 for 8 IPs. Too bad you can't get a deal like that (well maybe of you changed ISPs). :)

-Tim

---

### Post by StickyStyle on 2008-08-02
> **skunkbad said:**
> 
I wasn't trying to get the ISP to change the PTR, but as I was reading the book of Postfix, it was making a big deal about PTR, but didn't mention what to do for a dynamic IP.

Yeah, the reason that it wasn't mentioned for dynamic IP's is there is nothing you can do about it ;)  That's one reason I suggested to relay your mail though your ISP where its PTR record will resolve properly.

> **skunkbad said:**
> 
I've got Postfix running with multiple domains, multiple users, and all is well. I just have some questions as I read this book. For instance, if a user was on a business trip, and at a hotel, and trying to relay an email through my server to external_domain.net, my current Postfix installation won't allow that email to be relayed because the hotel's IP isn't listed in mynetworks. I'm not trying to hijack my own thread, but I do have questions like this that have not been answered while reading the book of Postfix.

Skim ahead in your book looking for SMTP-AUTH and SASL, that's what you want.  An example setup with both is also in the server guide for postfix [http://doc.ubuntu.com/ubuntu/serverguide/C/postfix.html](http://doc.ubuntu.com/ubuntu/serverguide/C/postfix.html) talking about SMTP-AUTH

---

### Post by rytec on 2009-05-13
> **skunkbad said:**
> StickyStyle,

I wasn't trying to get the ISP to change the PTR, but as I was reading the book of Postfix, it was making a big deal about PTR, but didn't mention what to do for a dynamic IP.

I've got Postfix running with multiple domains, multiple users, and all is well. I just have some questions as I read this book. For instance, if a user was on a business trip, and at a hotel, and trying to relay an email through my server to external_domain.net, my current Postfix installation won't allow that email to be relayed because the hotel's IP isn't listed in mynetworks. I'm not trying to hijack my own thread, but I do have questions like this that have not been answered while reading the book of Postfix.

I already use zoneedit.com to handle the DNS/MX. The only issue with DNS seems to be within my server itself. While everything seems to work, Apache2 does send me an email that says that it can't find a fully qualified domain name and is using localhost as servername. This really doesn't cause the server itself to have any problems, so I'm not concerned so much with this.

Windependence,

I'm not going to ask my ISP for a static IP, because it costs $10 a month extra, and I really am only testing this server. It only has parked/advertising domains on it, and all of the users are myself. Just trying to learn, and having fun with it!

Thanks.

How can you activate the reverse lookup in postfix ? so it also will check the senders fqdn ?

---

