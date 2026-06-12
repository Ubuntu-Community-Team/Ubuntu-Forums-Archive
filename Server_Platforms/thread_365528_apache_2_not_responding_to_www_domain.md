---
title: "apache 2 not responding to www domain"
date: 2007-02-19
forum: Server Platforms
---

### Post by shawnlogic on 2007-02-19
Hey Everyone,

Hope some of you may know the answer to this problem.
I've setup my server, and I bought a domain name to point to it.

The issue occurs in the browser.
When I type in [http://www.mydomain.com](http://www.mydomain.com) -> I get a server error
When I type in [http://mydomain.com](http://mydomain.com) -> I get my server

Could this be a virtual host issue?

All the config files for apache2 are still set to defaults.

Thanks for the help in advance.

---

### Post by Koybe on 2007-02-20
What about your dns? Does [www.mydomain.com](www.mydomain.com) binds to the same ip as mydomain.com?

---

### Post by MJN on 2007-02-20
What exactly is the error?
 
As Krobe says, it could be the DNS. Alternatively it could be that you require a **ServerAlias ****[www.mydomain.com](www.mydomain.com)** directive in your config however if you've only got the one virtual host then it should work for any name that resolves to your IP.
 
Beyond that it's impossible to say - if you hide your domain name from us then I'm afraid we're stabbing in the dark.
 
Mathew

---

### Post by shawnlogic on 2007-02-20
Hey,
thanks for the responses.

My domain is [http://colorcoded.org](http://colorcoded.org)

The exact error is Problem Loading Page when I type [www.colorcoded.org](www.colorcoded.org) into my browser.
I added a ServerName [www.colorcoded.org](www.colorcoded.org) to the host
 

Should I try an ServerAlias?

---

### Post by jtc on 2007-02-20
I believe we have found the source of your problems

> 
andreas@mauddib:~$ host colorcoded.org
colorcoded.org has address 74.117.89.75
andreas@mauddib:~$ host [www.colorcoded.org](www.colorcoded.org)
Host [www.colorcoded.org](www.colorcoded.org) not found: 3(NXDOMAIN)


You need a DNS-entry for [www.colorcoded.org](www.colorcoded.org)

---

### Post by d.j.schroeder on 2007-02-20
In /etc/apache/sites-enabled there should be 000-default below the ServerName directive you can add

ServerAlias *.colorcoded.com

---

### Post by shawnlogic on 2007-02-20
> **d.j.schroeder said:**
> In /etc/apache/sites-enabled there should be 000-default below the ServerName directive you can add

ServerAlias *.colorcoded.com

Thanks for the fast replies.  I add the directive as you said, but it's still not pointing there, do I need to configure the resolv.conf for the dns entry?

---

### Post by d.j.schroeder on 2007-02-20
Well for one thing I put .com when you said your domain was .org.  Hopefully, you noticed my mistake.  In my Apache setup I have only added and modified things in the sites-enabled directory and that is all I've had to do. 

If you ping colorcoded.org and ping [www.colorcoded.org](www.colorcoded.org) do they have the same numeric ip address?

---

### Post by jtc on 2007-02-20
The suggestion from d.j.schroeder has nothing to do with your DNS-entries.

Unless you run your own DNS-server, you'll have to ask whoever is doing that to add a new entry.

It seems as if your domain-name is handled by dynadot.com? Perhaps they have a Web-GUI where you can managed your DNS-settings?

---

### Post by d.j.schroeder on 2007-02-20
Yep JTC is definitely correct.  The problem is with your DNS.  I tried pinging both, [www.colorcoded.org](www.colorcoded.org) DNS entry was not found.  Once you get that straight you should be good to go with the alias in your Apache setup.

---

### Post by shawnlogic on 2007-02-21
Thanks guys for all your help.
You were correct, I did need a DNS entry for [www.colorcoded.org](www.colorcoded.org)

I had always assumed that they automatically gave me www subdomain.

Thanks again!

---

