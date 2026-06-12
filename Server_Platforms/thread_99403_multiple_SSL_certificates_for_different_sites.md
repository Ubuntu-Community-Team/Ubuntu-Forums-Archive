---
title: "multiple SSL certificates for different sites?"
date: 2005-12-05
forum: Server Platforms
---

### Post by OneSeventeen on 2005-12-05
I have a server with a static IP, an a-name, and like 5 c-names.
I want the a-name and one of the c-names to have a secure certificate.

so, let's say I have:
foo.a.com  (host name)
bar.a.com  (alias/c-name)
baz.a.com  (alias/c-name)

Now, I have ssl keys from a few old servers (foo.a.com and bar.a.com were both on different servers, and I've consolidated them to this one big server), I have all the files associated with them, and they were working on the old servers.

Is it possible for me to copy all of the key files over to the new server, and just change the config file for each site in /etc/apache2/sites-available/ with the ssl details?

(I'm about to try this on my own, but I thought I'd ask, since I'm not sure how to enable the apache2 ssl module anyway, a2enmod I think, but not sure)

---

### Post by OneSeventeen on 2005-12-06
Okay, I have followed the tutorial over at: [https://wiki.ubuntu.com/forum/server/apache2/SSL](https://wiki.ubuntu.com/forum/server/apache2/SSL)

But that is assuming I have 1 certificate file on the computer to cover all virtual hosts.

This is not the case for me. The certificates I own only cover one subdomain a piece, which means if my default site is: foo.example.com, then if I go to [https://foo.example.com](https://foo.example.com) then all is well, I go to the site, and it is going through a secure connection.

If I type in [https://bar.example.com](https://bar.example.com) I get a message stating that the certificate was issued for foo.example.com, would I still like to continue?  If I say yes, then it directs me to the Document root of foo.example.com, **not** bar.example.com

This is a big problem for me.


So what I want, is to have a site file (virtual host) that is ***Only*** for one virtual host on port 443.  Then I want another site file (virtual host) that is ***Only*** for a different virtual host on port 443.

I also want a few other virtual hosts to have https:// disabled, automagically redirecting them to the http:// equivalent of their own host.

As of now, all https:// requests to my server, reguardless of URL go to the Document Root of the default site, which is not what I want it to do.

---

### Post by OneSeventeen on 2005-12-06
I was just told in an apache IRC channel that I have to have a different IP for each SSL site.

So if I do have multiple VirtualHosts, all non-SSL'd ones will share one IP, then *each* site with an SSL version will have to have their own IP.

so I'm thinking problem solved, but I'll post back when I get more IP's as to whether or not this works.

---

### Post by OneSeventeen on 2005-12-06
I just got a new IP address, and now I'm getting:
> 
mixing * ports and non-* ports with a NameVirtualHost address is not supported,


I changed all the NameVirtualHost's from * to their respective IP and that's the error I got...

---

### Post by OneSeventeen on 2005-12-06
Well, it turns out because you can only use SSL on dedicated IP's you really shouldn't set a VirtualName for those SSL sites.

I took the NameVirtualHost 1.2.3.4 out of the file for the SSL-encrypted site, and all was well. :)

---

### Post by LordHunter317 on 2005-12-06
You only need a NameVirtualHost directive for sites that are doing named-virtual hosting.  That is *impossible* for SSL unless you have a wildcard DNS entry.

Also, if you have new IPs for your server, convert your CNAME RRs to A RRs at the new IP addresses and make sure your RNDS is up-to-date as well.  Just, FWIW.

---

### Post by OneSeventeen on 2005-12-06
Thanks, that makes sense, except one thing....
RNDS?  what's that?

I'm slowly having the tech team at work change my c-names to a-names of new IPs, but since I have like 5 of them I am trying to space it out so they don't get upset at me making them go back and forth.  (I just finished consolidating multiple servers onto the same machine... should have just used the existing IP's, huh? :p )

Oh well, it's nice working at a place where I can just send an email and have a static IP within an hour for free :D

---

