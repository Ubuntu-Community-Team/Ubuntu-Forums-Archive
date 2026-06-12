---
title: "How to point my domain, to my DNS."
date: 2013-07-03
forum: Server Platforms
---

### Post by The Titan on 2013-07-03
I am trying to set up a DNS for my domain, which well then handle all of my domains.  I am currently stuck because I do not know how to point ns1.mydomain.com and ns2.mydomain.com to the DNS server ip address.

if I set up *ns1.mydomain*.com and *ns2.mydomain.com* for the nameservers for *mydomain.com* obviously that isn't going to work because it will never resolve (unless there is something that I am missing).

My registrar is GoDaddy, and a bit(or a ton) of Googling led me to this: [http://support.godaddy.com/help/article/668/registering-your-own-nameservershosts](http://support.godaddy.com/help/article/668/registering-your-own-nameservershosts)

I have done what it asked, but I am still confused about it.  Is setting the *hosts *in GoDaddy going to completely bypass the GoDaddy DNS.  The reason I ask is because it states that it will automatically create the A records, which (unless I am completely lost) shouldn't be necessary because any sort of necessary A record would have to be done on my end with my DNS server.

Thanks in advance for breaking this down for me,
Daniel

---

### Post by CharlesA on 2013-07-03
Doesn't godaddy have a way to manage DNS records? There shouldn't be any reason to run your own name servers.

Read this:
[http://support.godaddy.com/help/article/680/managing-dns-for-your-domain-names](http://support.godaddy.com/help/article/680/managing-dns-for-your-domain-names)

---

### Post by The Titan on 2013-07-03
They do and it works fine.  But I want to run my own DNS.

---

### Post by CharlesA on 2013-07-03
> **The Titan said:**
> They do and it works fine.  But I want to run my own DNS.

Any reasons for wanting to do it yourself?

---

### Post by sandyd on 2013-07-03
> **The Titan said:**
> I am trying to set up a DNS for my domain, which well then handle all of my domains.  I am currently stuck because I do not know how to point ns1.mydomain.com and ns2.mydomain.com to the DNS server ip address.

if I set up *ns1.mydomain*.com and *ns2.mydomain.com* for the nameservers for *mydomain.com* obviously that isn't going to work because it will never resolve (unless there is something that I am missing).

My registrar is GoDaddy, and a bit(or a ton) of Googling led me to this: [http://support.godaddy.com/help/article/668/registering-your-own-nameservershosts](http://support.godaddy.com/help/article/668/registering-your-own-nameservershosts)

I have done what it asked, but I am still confused about it.  Is setting the *hosts *in GoDaddy going to completely bypass the GoDaddy DNS.  The reason I ask is because it states that it will automatically create the A records, which (unless I am completely lost) shouldn't be necessary because any sort of necessary A record would have to be done on my end with my DNS server.

Thanks in advance for breaking this down for me,
Daniel

The hosts that godaddy asked you to setup are known as a glue record.

Glue records are served by a non-authorative nameserver so that it does not result in an impossible condition (i.e. using the dns servers for the domain to lookup a nameserver on the same domain).

Essentially, they point towards the IP Addresses that you set in the godaddy tutorial

---

### Post by The Titan on 2013-07-03
> **CharlesA said:**
> Any reasons for wanting to do it yourself?
Mainly just to learn about how it all works.  I have always found, that for myself anyways, it is the best way to learn.  I have the *means* I just need to *knowhow*.  Surely some can relate.

> **sandyd said:**
> The hosts that godaddy asked you to setup are known as a glue record.

Glue records are served by a non-authorative nameserver so that it does not result in an impossible condition (i.e. using the dns servers for the domain to lookup a nameserver on the same domain).

Essentially, they point towards the IP Addresses that you set in the godaddy tutorial

Thank you SandyD.  Just to be clear, that does solve my problem.  By setting the *glue records* to the IP of my DNS and setting the DNS for my domain to my name servers I should be set, correct?

---

### Post by sandyd on 2013-07-03
> **The Titan said:**
> Mainly just to learn about how it all works.  I have always found, that for myself anyways, it is the best way to learn.  I have the *means* I just need to *knowhow*.  Surely some can relate.



Thank you SandyD.  Just to be clear, that does solve my problem.  By setting the *glue records* to the IP of my DNS and setting the DNS for my domain to my name servers I should be set, correct?

If your running your own DNS server, make sure you aren't creating an open relay.

If you are talking about pointing the domain towards the DNS servers, yes.

You will also need to set a A record in the domain's DNS for the nameservers

---

### Post by Bachstelze on 2013-07-03
To check that everything is fine you can use a tool like [ZoneCheck](http://www.zonecheck.fr/demo/), just put your domain name in the "Zone" field and click "Check".

---

### Post by The Titan on 2013-07-03
> **Bachstelze said:**
> To check that everything is fine you can use a tool like [ZoneCheck]("http://www.zonecheck.fr/demo/"), just put your domain name in the "Zone" field and click "Check".

I am still waiting for it to work.  I did it a about 5-6 hours ago, and I know things like that can take a long time.  GoDaddy estimates 24-48 hours, but they say that about changing DNS servers too and it has never taken that long for me.

---

### Post by sandyd on 2013-07-05
> **The Titan said:**
> I am still waiting for it to work.  I did it a about 5-6 hours ago, and I know things like that can take a long time.  GoDaddy estimates 24-48 hours, but they say that about changing DNS servers too and it has never taken that long for me.

what domain is this? (pm or post in thread)

---

### Post by The Titan on 2013-07-05
I did end up getting it working, I had done everything correctly.  I just had to wait for the name servers to propagate  .  Marking as solved, thanks everyone for the help

---

### Post by SeijiSensei on 2013-07-05
If you are running a local nameserver, restarting it will clear the cache so you can check the new zones without having to wait for propagation.

---

### Post by The Titan on 2013-07-05
> **SeijiSensei said:**
> If you are running a local nameserver, restarting it will clear the cache so you can check the new zones without having to wait for propagation.

That ended up being how I figured out that I had the nameserver configured incorrectly, solving yet another issue that I had.  But checking the log files got me going.

---

