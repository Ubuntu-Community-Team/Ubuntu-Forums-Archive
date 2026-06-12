---
title: "BIND9 configuration"
date: 2012-07-28
forum: Server Platforms
---

### Post by Caleb7 on 2012-07-28
I have Apache 2 set up and working with Virtual Hosting.

Now, I'm looking for a little help with BIND9 configuration.  I want to create subdomains any time I need to, and point them to a new virtual directory. (such as some web hosts do that offer free subdomains)

Plan:
1. Have one DNS server manage the domain I purchased.
2. Add subdomains to my domain such as user1.mydomain.com, user2.mydomain.com, etc.
3. When people search *.mydomain.com, I want them to be querying my DNS server to get the address of whatever the subdomain was.  Currently I'm using the DNS servers over at Enom.  I want to use my own, and add many subdomains.

I've read multiple manuals and configured BIND9 a couple times in different ways.  I'm still not 100% sure exactly how to get it all working.  Right now I'm sitting on a fresh install and searching for more information.

Basically I want my DNS server to have complete control over my domain name.

I won't be using two servers for redundancy, as I'll only be using this for a demonstration, on web hosting and subdomain registration in a class project.

#-o

---

### Post by Caleb7 on 2012-07-28
Got it all figured out. Used this as a reference if anyone else is struggling: [http://www.howtoforge.com/two_in_one_dns_bind9_views](http://www.howtoforge.com/two_in_one_dns_bind9_views)

Explains the whole internal/external thing appropriately and the correct use of views, even though I chose not to use views.  Hope this helps others.

---

