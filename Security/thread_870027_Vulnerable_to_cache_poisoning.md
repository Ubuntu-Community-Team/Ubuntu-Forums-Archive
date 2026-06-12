---
title: "Vulnerable to cache poisoning?"
date: 2008-07-25
forum: Security
---

### Post by n3r0 on 2008-07-25
Hello. I was recently reading about the DNS vulnerabilities circling the net. I visited the following website ( [http://www.doxpara.com/](http://www.doxpara.com/) )to check out if I was vulnerable. Turns out I am!

```
Your name server, at X>X>X>X, appears vulnerable to DNS Cache Poisoning.
All requests came from the following source port: 55008

```

When I run the test again they then all come from a different port but with the same vuln. Anyone know how to fix? I ran apt-get to update but it didnt find any new security patches. I am capable of installing from source with some basic instructions so that I dont break dns. Im using ubuntu LTS 2.6.15-51-server #1 SMP Tue Feb 12 17:12:18 UTC 2008 i686 GNU/Linux


thanks

---

### Post by brian_p on 2008-07-25
> **n3r0 said:**
> 

Anyone know how to fix?

Unless you are running BIND on your machine the report will be for your ISP's nameserver.

---

### Post by n3r0 on 2008-07-25
I am most definitely running bind9, authoritative for several domains.

```
;; ANSWER SECTION:
version.bind.           0       CH      TXT     "9.3.2-P2.1"

```

---

### Post by vloose on 2008-07-25
I updated to 9.3.2-P2.1 using the package manager and that tool you listed is declaring my machine clean.  I did have to statically assign the dns server I wanted to check on my PC because the tool seems to check the DNS server that your PC is querying.

I am having a lot of trouble finding good documentation on what exactly needs done to patch the systems properly but I suspect we will be seeing more about it over the next couple days.

Hopefully the good answers won't come too late.

---

### Post by n3r0 on 2008-07-27
looks like its clean now... not sure what i did

---

