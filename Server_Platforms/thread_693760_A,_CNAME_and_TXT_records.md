---
title: "A, CNAME and TXT records"
date: 2008-02-11
forum: Server Platforms
---

### Post by ade234uk on 2008-02-11
I have purchased myself a cheap dedicated server for some of my sites.

I am trying to set up the domain name through 123reg to point to the server.

I am trying to point to gnulinux.co.uk using dns settings.

I have changed the dns settings in 123 for [www.gnulinux.co.uk](www.gnulinux.co.uk) to the following

Name	Type	      Content	                     
@ 	  TXT	        CONTROL-BY:123-reg
@         A	          212.241.183.56
ftp        CNAME       gnulinux.co.uk.
www    A	       212.241.183.56

I have set up an account on the server called gnulinux and entered the domain name gnulinux.co.uk, this is mapped to the account gnulinux

Now I presume this should work, but when I enter [www.gnulinux.co.uk](www.gnulinux.co.uk), I get 123 holding page.
What am I doing wrong?

I have always set the nameservers, but I wanted to try a different way of doing things.
I tried the ftp and this works.

---

### Post by faulkes on 2008-02-11
From dig:

;; QUESTION SECTION:
;[www.gnulinux.co.uk](www.gnulinux.co.uk).            IN      A

;; ANSWER SECTION:
[www.gnulinux.co.uk](www.gnulinux.co.uk).     52926   IN      A       194.154.164.90

I would contact your domain registrar, it is entirely possible the zone hasn't fully updated since the last change (although I did query directly and got the same result).  

It would be helpful to see the actual full zone file as well although I doubt there is much chance of this, it is also entirely possible that they are doing some layer 4 activities which havent updated themselves yet.

Faulkes

---

### Post by ade234uk on 2008-02-11
So I am doing nothing wrong?

I should just wait.

---

### Post by faulkes on 2008-02-11
I would contact the registrar anyways, you paid for the domain and any support they offer so it isn't going to hurt you.

Again, the options I listed are only possiblities and don't account for possible errors on your entries or by the registrar or anything
which the registrar themselves have running.

Faulkes

---

### Post by ade234uk on 2008-02-11
Thank you for your help. I will contact the people that I bought the dedicated server from first, to see what is happening.

Who knows by tommorow morning It may link up. However using the dns I presume it should be instant.

I am learning so much in these last few days. I document all my stuff I learn through my site.

---

### Post by faulkes on 2008-02-11
> **ade234uk said:**
> Thank you for your help. I will contact the people that I bought the dedicated server from first, to see what is happening.


That would be the best route

> 
Who knows by tommorow morning It may link up. However using the dns I presume it should be instant.


DNS entires have a TTL (time to live) attached to them so it is possible it could be that, however, experience has taught me, especially when dealing with service providers to never assume anything.

Faulkes

---

### Post by astrotech226 on 2008-02-11
The IP I get back is pretty close:

```
$ nslookup www.gnulinux.co.uk

Non-authoritative answer:
Name:   www.gnulinux.co.uk
Address: 212.241.183.57
```

If I go to the website, I do not see a 123 holding page but what looks to be your website.  Depending on what OS you are currently on, maybe you need to flush your DNS cache?

---

### Post by ade234uk on 2008-02-11
Cool, I forgot about nslookup. Thank you.

---

### Post by MJN on 2008-02-11
Use 'dig' instead. nslookup has been deprecated now as it can give some right quirky results if you're not careful (or even if you are for that matter).

Mathew

---

