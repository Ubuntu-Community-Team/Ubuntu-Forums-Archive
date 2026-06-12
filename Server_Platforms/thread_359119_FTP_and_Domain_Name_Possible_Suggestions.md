---
title: "FTP and Domain Name Possible? Suggestions"
date: 2007-02-11
forum: Server Platforms
---

### Post by kramerkeller on 2007-02-11
Currently I can FTP both internally and externally with IP address both anonymous and login

Internal

[ftp://192.168.0.7](ftp://192.168.0.7)
[ftp://user:password@192.168.0.7](ftp://user:password@192.168.0.7)

External with port forward

[ftp://xxx.xxx.x.x](ftp://xxx.xxx.x.x)
[ftp://ftp://user:password@xxx.xxx.x.x](ftp://ftp://user:password@xxx.xxx.x.x)

Is there a way to tie a domain name to FTP so that people can go to

[ftp://createcandor.com](ftp://createcandor.com) and access the ftp

Furthermore is it possible to use the ftp login option with a domain name as shown below

[ftp://user:password@createcandor.com](ftp://user:password@createcandor.com)

---

### Post by kidders on 2007-02-11
Hi there,

Yes... ask your DNS service provider to point your domain name at your computer. If your IP isn't static, you will need to switch to a dynamic DNS service though.

---

### Post by jtc on 2007-02-11
The FTP-server doesn't care whatever you connect to it using a domainname or and ip-address. What you do have to do is register a domain and associate it with your ip.

---

### Post by kramerkeller on 2007-02-15
Currently my ip address is dynamic

However, it does not change that frequently, I have had it for 2 months and it hasn't changed yet

At some point I will set up dynamic dns

However, the above part.  I know it is supposed to be simple, but I am not having an easy time.  I registered my domain with 1&1.  I have tried both a frame redirect and an http redirect.  Both work fine when I jsut redirect to the IP.  however, when trying to do [ftp://createcandor.com](ftp://createcandor.com) it is not recognized.

Is this something I need to work out with 1&1 or should eitehr a frame redirect or http forward work?

Also, I would like ot be able to host multiple sites with a name.  Eventually I will get a static IP.  I have configured bind and apache for virtual hosting.  It randomly works.  Do I need to build my own DNS for this to work or can 1&1 or some other service do this for me so that the correct name produces the right site.  When using bind my understanding was I would resolve the site myself.  If this is the case, what do I put down for name servers in bind?  Do I just put by ip address?

Confused, and thanks.

---

### Post by Brazen on 2007-02-15
a frame redirect or http forward will not work.  The domain name MUST go directly to your ip address in order for ftp to work with that domain name.  You can register for a free dyndns subdomain name at dyndns.org.

I use a dyndns.org subdomain for my home with http, ftp, ssh, and it all works fine.

---

