---
title: "Hotlinkers"
date: 2009-10-04
forum: Server Platforms
---

### Post by BigTraz on 2009-10-04
Hello Ubuntu peeps.

I'm new to Linux and am loving it and learning about it pretty fast. I have a hot-linking problem though. How can I ban ip's and domains from accessing anything on my server? I do not want to use .htaccess. I want something that will be effective server-wide not per domain on the server. Any help would be greatly appreciated. 

Traz

---

### Post by windependence on 2009-10-04
What is it exactly that you are concerned about or afraid of? If your Apache is properly locked down, and you have a SEPARATE firewall installed in front of it, then you should be fine. Ignore all the script kiddies hitting your outside IP. If your properly locked down, they aren't getting in.

-Tim

---

### Post by BigTraz on 2009-10-04
The problem is that they are streaming videos off my server by embedding them on their site. Some of my videos are pretty large in file size and I don't want them to get scattered all over the place. I need a way to block the domains/ips that are pulling this data from my server. I hope this makes sense.

---

### Post by BigTraz on 2009-10-04
Also is there anyway to redirect certain geographical locations traffic elsewhere? I want to refuse traffic from about a dozen countries and want to divert that traffic to another site of mine.

---

### Post by BigTraz on 2009-10-04
Cmon guys. Theres 11000 people online and no one can help me with this? Pretty Please with a cherry on top!

---

### Post by BigTraz on 2009-10-04
Bump for the evening crowd.

---

### Post by cariboo on 2009-10-04
Please be patient, we are all volunteers here, the person that may be able to answer your questions may not have seen it yet. 

It is advisable to bump your thread only after 24 hours has elapsed.

---

### Post by BigTraz on 2009-10-04
Thanks Cariboo. Ill wait till tomorrow night before I bump again.

---

### Post by brettg on 2009-10-04
Apache has a module that allows you to allow or deny traffic by geographical IP

[http://www.maxmind.com/app/mod_geoip]("http://www.maxmind.com/app/mod_geoip")

---

### Post by koenn on 2009-10-05
> **BigTraz said:**
> The problem is that they are streaming videos off my server by embedding them on their site. Some of my videos are pretty large in file size and I don't want them to get scattered all over the place. I need a way to block the domains/ips that are pulling this data from my server. I hope this makes sense.
it's not the other servers/sites that are pulling the data from your server, it's the browsers that are visiting those other sites: they just "GET" whatever link, image, video that is linked to from these sites, be it on the same server, or an other one (e.g. yours).

Your web server would have to be able to distinguish those requests from requests triggered by links on *your own* site. 

You might be able to do that by having your site check referers ( [http://en.wikipedia.org/wiki/HTTP_referrer](http://en.wikipedia.org/wiki/HTTP_referrer) )

---

### Post by Lars Noodén on 2009-10-05
Apache's mod_rewrite is very powerful and can be used to redirect selected traffic.  

[http://httpd.apache.org/docs/2.2/misc/rewriteguide.html](http://httpd.apache.org/docs/2.2/misc/rewriteguide.html)
[http://httpd.apache.org/docs/2.2/mod/mod_rewrite.html](http://httpd.apache.org/docs/2.2/mod/mod_rewrite.html)

You can use the server environment variables or mod_authz to make sure that the visitors at least go to the trouble of forging the referrer header. ;) 

[http://httpd.apache.org/docs/2.2/env.html](http://httpd.apache.org/docs/2.2/env.html)
[http://httpd.apache.org/docs/2.2/mod/mod_authz_host.html](http://httpd.apache.org/docs/2.2/mod/mod_authz_host.html)

---

### Post by BigTraz on 2009-10-05
> **Lars Noodén said:**
> Apache's mod_rewrite is very powerful and can be used to redirect selected traffic.  

[http://httpd.apache.org/docs/2.2/misc/rewriteguide.html](http://httpd.apache.org/docs/2.2/misc/rewriteguide.html)
[http://httpd.apache.org/docs/2.2/mod/mod_rewrite.html](http://httpd.apache.org/docs/2.2/mod/mod_rewrite.html)

You can use the server environment variables or mod_authz to make sure that the visitors at least go to the trouble of forging the referrer header. ;) 

[http://httpd.apache.org/docs/2.2/env.html](http://httpd.apache.org/docs/2.2/env.html)
[http://httpd.apache.org/docs/2.2/mod/mod_authz_host.html](http://httpd.apache.org/docs/2.2/mod/mod_authz_host.html)

Thanks I'm trying to figure this out now.

---

