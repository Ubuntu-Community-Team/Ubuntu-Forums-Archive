---
title: "using custom domain with blogger help"
date: 2009-09-29
forum: The Cafe
---

### Post by joey-elijah on 2009-09-29
I must evidently suck at this. I managed to set up a domain with tumblr.com fine, but i cannot get one to work with blogger.

Has anyone done this successfully and willing to point out the mistake i'm making? 

I changed A  and C Name in my domain control panel as per the blogger help, waited a few days - it redirected to a google 404. Wonderful i thought! Time to update my blogger settings and it'll all work dandily.

Changed my blogger to use custom domain... but all i get is a 404... still..

Domain DNS settings: -
[IMG]http://img84.imageshack.us/img84/8637/screenshot014.png[/IMG]

---

### Post by v8YKxgHe on 2009-09-29
Why is your 'www' CNAME set to ghs.google.com.? CNAME in basic terms is an alias, I assume you're wanting 'www.example.com' to be the same as 'example.com'? If so, that is your answer.

Also, why many duplicate entries?

---

### Post by Bachstelze on 2009-09-29
Did you ask Canonical for permission to use the ubuntu name in your URL?

---

### Post by joey-elijah on 2009-09-29
> **AlexC_ said:**
> Why is your 'www' CNAME set to ghs.google.com.? CNAME in basic terms is an alias, I assume you're wanting 'www.example.com' to be the same as 'example.com'? If so, that is your answer.

Also, why many duplicate entries?

They're look similar but they're not duplicate. They're entered as per the Blogger Help on setting up DNS with Blogger. 

The two steps i followed were: -

Create a CNAME record for your blog's address, which should be a subdomain of the form [www.example.com](www.example.com)

> To create a CNAME record for your domain with the DNS, associating your domain with ghs.google.com. 

Four separate 'A' Names using your naked domain: - 

216.239.32.21
216.239.34.21
216.239.36.21
216.239.38.21

---

### Post by v8YKxgHe on 2009-09-29
You need to set the CNAME to 'omgubuntu.co.uk.', then [www.omgubuntu.co.uk](www.omgubuntu.co.uk) and omgubuntu.co.uk will point to the same thing. I assume the 194. IP address is your current one that you're moving away from? If so, you'll need to change that for this to work.

---

### Post by joey-elijah on 2009-09-29
> **Bachstelze said:**
> Did you ask Canonical for permission to use the ubuntu name in your URL?

No, and i'm sure they wouldn't be overly worried about an Ubuntu "fan" blog using it in the same way most major corporations/companies/etc don't mind their products or services being referenced by fan sites.

E.g.: -

[http://www.sirpepsi.com](http://www.sirpepsi.com) - Unofficial Pepsi site. Pepsi is a trademark.
[http://www.sarahconnorchronicles.org](http://www.sarahconnorchronicles.org) - Unofficial SCC fan site. T:TSCC's is a trademark.
[http://googlesystem.blogspot.com](http://googlesystem.blogspot.com) - Unofficial Google news blog - Google is a trademark. 

And so on.

I have a disclaimer that my site is not endorsed, affiliated nor in anyway connected to Canonical which i feel is more than enough. if any potential users think my garishly decorated and exaggeratedly-named blog is an official site then should they even be using a computer, let alone a Linux distro?! 

If you want to be *isshy* then feel free to rat on the other gazillion following Ubuntu "fan" sites that reference "Ubuntu" in their URL's/titles/domains, too.  It's difficult to run a "fan" site if you're forbidden from mentioning what you're a fan of.

"That debi.. oops i mean that linux distro based on that other name i can't mention for fear of pedants unofficial news and resource site.co.uk." hardly has the same ring to it. 

ubuntu-art.org would have to be "a-certain-linux-distro-art.org", ubuntuhq.com "a-specific-linux-distro-hq.com", etc. 

My blog does nothing to harm, infringe or otherwise on the reputation of Ubuntu or Canonical and in-fact probably does the opposite. Articles from my site have featured on Lifehacker, how-to-geek, endgadget, gizmodo, front page of digg tech, etc

---

### Post by Bachstelze on 2009-09-29
> **joey-elijah said:**
> No, and i'm sure they wouldn't be overly worried about an Ubuntu "fan" blog using it in the same way most major corporations/companies/etc don't mind their products or services being referenced by fan sites.


The Trademark Policy states that you must ask for permission before using "ubuntu" in a domain name. No exceptions.

---

### Post by joey-elijah on 2009-09-29
> **AlexC_ said:**
> You need to set the CNAME to 'omgubuntu.co.uk.', then [www.omgubuntu.co.uk]("http://www.omgubuntu.co.uk") and omgubuntu.co.uk will point to the same thing. I assume the 194. IP address is your current one that you're moving away from? If so, you'll need to change that for this to work.

Can i delete it without issue do you think? I don't have e-mail set up with my domain provider and the @ is, presumably, for e-mail... The Google help site didn't mention/reference changing anything to do with it so i left it but if it should be removed then i shall.

Thanks for the help btw, the instructions i followed were a bit ambiguous to me hence the confusion.

---

### Post by joey-elijah on 2009-09-29
> **Bachstelze said:**
> The Trademark Policy states that you must ask for permission before using "ubuntu" in a domain name. No exceptions.

Then i shall revert to using an "ubuntu" free domain. Quite why my blog should be punished when a gazillion others can use "ubuntu" in their domains i don't know. 

So much for community spirit... wonder what Fedora's looking like these days...

---

### Post by Bachstelze on 2009-09-29
> **joey-elijah said:**
> Then i shall revert to using an "ubuntu" free domain. Quite why my blog should be punished when a gazillion others can use "ubuntu" in their domains i don't know. 

So much for community spirit... wonder what Fedora's looking like these days...

Who said your blog would be "punished"? Just ask, they will give it. But you must ask. The others probably asked, too.

---

### Post by v8YKxgHe on 2009-09-29
> **joey-elijah said:**
> Can i delete it without issue do you think? I don't have e-mail set up with my domain provider and the @ is, presumably, for e-mail... The Google help site didn't mention/reference changing anything to do with it so i left it but if it should be removed then i shall.

Thanks for the help btw, the instructions i followed were a bit ambiguous to me hence the confusion.

No, the '@' in your name column refers to the domain 'omgubuntu.co.uk', for example an entry in BIND9 (a DNS server) would be:

> @			A	127.0.0.1

For mail, it would be an MX record and not an A record.

---

### Post by joey-elijah on 2009-09-29
> **Bachstelze said:**
> Who said your blog would be "punished"? Just ask, they will give it. But you must ask. The others probably asked, too.

Aside from not having a clue how you contact Canonical's legal team to clear use of the name, i probably can't afford the fees.

---

### Post by Bachstelze on 2009-09-29
> **joey-elijah said:**
> Aside from not having a clue how you contact Canonical's legal team to clear use of the name, i probably can't afford the fees.

Who said you would have to pay anything? [https://forms.canonical.com/trademark/](https://forms.canonical.com/trademark/)

---

### Post by joey-elijah on 2009-09-29
> **Bachstelze said:**
> Who said you would have to pay anything? [https://forms.canonical.com/trademark/](https://forms.canonical.com/trademark/)

Oops! My bad! I assumed it would be some drawn-out complex legal-wrangle type affair. 

Thanks for the link! :smile:

---

### Post by joey-elijah on 2009-09-29
> **AlexC_ said:**
> No, the '@' in your name column refers to the domain 'omgubuntu.co.uk', for example an entry in BIND9 (a DNS server) would be:



I'm incredibly dumb; i've no idea how i managed to set up every DNS prior to this one. I can't find reference to an @ IP for blogger... am i barking up the wrong tree?

---

### Post by v8YKxgHe on 2009-09-29
You've already got the IPs, the 216.x.x.x ones. There is no such thing as a '@ IP', it is simply an IP, and you're using that to point your domain to.

---

### Post by joey-elijah on 2009-09-29
> **AlexC_ said:**
> You've already got the IPs, the 216.x.x.x ones. There is no such thing as a '@ IP', it is simply an IP, and you're using that to point your domain to.

Si leave the @ A 194... as it is, then? 

Sorry for not understanding - i've only had 3 hours sleep and DNS must stand for Do Not Simplify...

---

### Post by v8YKxgHe on 2009-09-29
Everyone has to learn at some stage, so don't worry you're doing nothing wrong. Doesn't help I'm half alive here my self as well.

No ... well, sort of. You can simply change the IP address of that entry to the first 216.x.x.x IP address, then remove all overs in there (including the CNAME). Then add the remaining 3 'A' entries, giving them either a blank name, or entering in '@' (depending on what that control panel will accept). That will set you up with the 4 'A' records for the domain 'omgubuntu.co.uk' (note the lack of 'www.').

You then setup a CNAME (which is basically an alias) of 'www.omgubuntu.co.uk' to 'omgubuntu.co.uk', then you can access the website via [www.omgubuntu.co.uk](www.omgubuntu.co.uk) as well as omgubuntu.co.uk

**however**, I've just checked what DNS settings you're currently using and, as can be seen by:

```
$ dig a www.omgubuntu.co.uk

; <<>> DiG 9.6.1 <<>> a www.omgubuntu.co.uk
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 49082
;; flags: qr rd ra; QUERY: 1, ANSWER: 4, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;www.omgubuntu.co.uk.           IN      A

;; ANSWER SECTION:
www.omgubuntu.co.uk.    85907   IN      A       216.239.38.21
www.omgubuntu.co.uk.    85907   IN      A       216.239.34.21
www.omgubuntu.co.uk.    85907   IN      A       216.239.32.21
www.omgubuntu.co.uk.    85907   IN      A       216.239.36.21
```
'www'omgubuntu.co.uk' is already pointing to those IP addresses. So, issue on blogger side for you regarding that. Sure you set it up correctly?

---

