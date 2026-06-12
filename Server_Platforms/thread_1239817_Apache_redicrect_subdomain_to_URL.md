---
title: "Apache redicrect subdomain to URL"
date: 2009-08-13
forum: Server Platforms
---

### Post by Soley on 2009-08-13
Ok, so I've searched google & here & haven't been able to find a decent way...well, a way that works, to do this.

I want to take a subdomain from my domain and redirect it to a URL that's NOT on my server.

For example:

subdomain.domain.com -> [www.example.com](www.example.com)

I've tried editing my virtual hosts & putting redirects in my httpd.conf file, but nothing seems to work.

Any ideas?


Nevermind. I thought 2 hours was long enough for a forward to work, but I guess it wasn't. Anyway, it's working now. Mods, feel free to lock this thread.

OR we can keep it going. What's your favorite color?

---

### Post by JGarrido on 2009-12-12
Mine is royal blue  :-)

So how is it done anyway? I need to do something like forward subdomain.domain.com to subdomain.domain.com:8080.

---

### Post by Jekshadow on 2009-12-13
Why not go into your Domain Name Provider's DNS config and just set up a CNAME entry pointing subdomain.domain.com to example.com?

---

### Post by kevin11951 on 2009-12-13
> **Jekshadow said:**
> Why not go into your Domain Name Provider's DNS config and just set up a CNAME entry pointing subdomain.domain.com to example.com?

is it even possible to setup cnames to point to a domain, and not an IP?

---

### Post by HighCommander540 on 2009-12-13
> **kevin11951 said:**
> is it even possible to setup cnames to point to a domain, and not an IP?

Yes, it is actually. The only thing that can't be setup to point to a domain is an ANAME. Which is really lame. I have all of my CNAMEs set to a domain, because I have a dynamic IP.

---

### Post by BkkBonanza on 2009-12-13
CNAMEs always do point to a name not an IP. CNAME means Canonical Name (ha ha, Ubuntu get it), which is mapping one name to another.

I've used CNAMEs to map my domains onto image servers run by Amazon S3. Works great.

Doing this type of mapping through Apache is the wrong way unless there is some additional need like logging or filtering data.

---

### Post by slakkie on 2009-12-13
You could do it like this (assuming DNS is already setup propperly):

[http://ubuntuforums.org/showpost.php?p=5258724&postcount=2](http://ubuntuforums.org/showpost.php?p=5258724&postcount=2)

---

