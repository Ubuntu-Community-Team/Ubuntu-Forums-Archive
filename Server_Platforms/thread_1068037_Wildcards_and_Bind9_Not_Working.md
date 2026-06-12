---
title: "Wildcards and Bind9 Not Working"
date: 2009-02-12
forum: Server Platforms
---

### Post by etali on 2009-02-12
Thanks to the help on here I have Apache working with VirtualHosts.  I've since learned that my domain registrar doesn't allow wildcard CNAMEs, so I thought I'd set up Bind9 and run my own nameserver (I want the wildcards for subdomains on WordPress-MU).

The problem is, Bind9 doesn't seem to be working at all.

**My named.conf.local contains:**

zone "domain.com" {
        type master;
        file "/etc/bind/domain.com.hosts";
        };



**And domain.com.hosts contains**


$ttl 38400
domain.com. IN      SOA     servername. myemailaddy. (
                        1234461395
                        10800
                        3600
                        604800
                        38400 )
domain.com. IN      NS      servername.
*.domain.com.       IN      CNAME   domain.com.


When I check host domain.com localhost it gives the expected result (127.0.0.1), and when I check randomsub.domain.com I get:

randomsub.domain.com is an alias for domain.com.

Lynx shows the correct web site for domain.com, but can't find any subs.

Have I done something wrong?

Thanks in advance.

---

### Post by Maheriano on 2009-02-12
Don't mean to hijack your thread but if you've actually gotten bind9 to work, can you walk me through it? I set up everything from 3 different tutorials and it still doesn't work. Please let me know, thanks.

Carry on.

---

### Post by etali on 2009-02-12
It's comforting to read that I'm not the only person having trouble!

If someone helps with the issue I've got here, then I'd be happy to try to help with your problem, although I'm no expert.

---

### Post by paulororke on 2009-02-13
> **Maheriano said:**
> Don't mean to hijack your thread but if you've actually gotten bind9 to work, can you walk me through it? I set up everything from 3 different tutorials and it still doesn't work. Please let me know, thanks.

Carry on.

I just set up bind9 for internal name resolution.  I followed this: 
[https://help.ubuntu.com/community/BIND9ServerHowto](https://help.ubuntu.com/community/BIND9ServerHowto)
and also found this helpful: [http://www.bind9.net/manual/bind/9.3.2/Bv9ARM.html](http://www.bind9.net/manual/bind/9.3.2/Bv9ARM.html)

If you go through the first and still have troubles let me know and I'll see what I can do, though I'm by no means an expert I'll be happy to share what I did to get mine working.

---

### Post by HermanAB on 2009-02-13
You don't actually use a wildcard in the record definition.  Just leave out the hostname part:
example.com. IN A 192.168.1.1

Hope that helps!

Herman

---

### Post by etali on 2009-02-13
Thanks for all the responses.

I followed the guide / suggestions here, and I now have a working setup locally, at least.  I expect it will work for the wider web in a few hours when everything propagates... *fingers crossed*.

The troubleshooting section in the bind9.net link posted by paulororke was especially helpful - so if anyone reading this is in a similar position to me (Followed a book / some tutorials, really thinks it should be working, but can't see why it isn't) - check that troubleshooting section :)

Thanks again.

---

### Post by beatgr on 2009-02-15
I would also suggest for anyone setting up DNS to look here:
[http://lani78.wordpress.com/2008/08/09/setting-up-a-dns-for-the-local-network/](http://lani78.wordpress.com/2008/08/09/setting-up-a-dns-for-the-local-network/)

which is a condensed verison of Sam Davis's work on Ubuntu "How To" guides.
[http://www.zaphu.com/category/ubuntu/](http://www.zaphu.com/category/ubuntu/)

g. beat

---

### Post by Maheriano on 2009-02-20
> **beatgr said:**
> I would also suggest for anyone setting up DNS to look here:
[http://lani78.wordpress.com/2008/08/09/setting-up-a-dns-for-the-local-network/](http://lani78.wordpress.com/2008/08/09/setting-up-a-dns-for-the-local-network/)

which is a condensed verison of Sam Davis's work on Ubuntu "How To" guides.
[http://www.zaphu.com/category/ubuntu/](http://www.zaphu.com/category/ubuntu/)

g. beat
I followed that guide and got an error on the last line. Everything else is the same, any ideas?

```
deemar@Jurassic:~$ host 68.144.96.207
Host 207.96.144.68.in-addr.arpa not found: 2(SERVFAIL)

```

---

