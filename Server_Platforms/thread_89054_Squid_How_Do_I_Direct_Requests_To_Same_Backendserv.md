---
title: "Squid: How Do I Direct Requests To Same Backendserver? Help."
date: 2005-11-11
forum: Server Platforms
---

### Post by bongobongo on 2005-11-11
Hi.

Found Squid a short while ago. Have looked trough the docs but could not find out how to do what I want: so I guess I need some help.....

I want to offer an online CMS system.

I want to promote the service through: [www.mysite.com](www.mysite.com) (fake name).

My customers should be able to at least use:

[www.customer-selected-domain-name.com](www.customer-selected-domain-name.com)

or if they want (if possible):

[www.mysite.com/customer-selected-dir](www.mysite.com/customer-selected-dir)

If I get a lot of customers I would like to be able to just install a new server and create the additional sites there.

I need to be able to direct an incoming request to the front-end (with Squid) to the same backend server (same backend server, allways, for same URI).

How do I configure that to work for:

a)
When my customers uses a domain-name like:
[www.customer-selected-domain-name.com](www.customer-selected-domain-name.com)

cool.gif
When my customers uses this:
[www.mysite.com/customer-selected-dir](www.mysite.com/customer-selected-dir)

d)
And..... Let say two of my customers want it this way:

customer 100:
[www.mysite.com/customer-100](www.mysite.com/customer-100)
are put on my first backend server.

(Note: now I do not want more customers on my first backend server because more customers here will make the server to slow, so I install a second backend server.)

Customer 101:
[www.mysite.com/customer-101](www.mysite.com/customer-101)
are put on my second backend server.

Can this be done using Squid.
Note that in example d) both customers want to use a subdir of:
[www.mysite.com/](www.mysite.com/)

but here the two subdirs are actually on two different servers.

e)
One last thing.
When I want to give a new user access to his site I guess I will have to
make some changes to the (squid)file where I map an URI to a specific backend server:
Where is this done and when this file changes how does it affect users that are online when the changes are done?

Are to use Linux, Apache, PHP and MySql.

How do I config Squid to make all or part of the above possible?

---

### Post by LordHunter317 on 2005-11-11
Why are you using Squid at all and not just Apache + Virtualhosts.  Apache can do exactly what you need, and you'll have to make use of that functionality anyway.  You should really read the documentation at apache.org on Name-Based virtual hosting very carefully, twice even, then come back and ask how to implement what you need to do.

---

### Post by bongobongo on 2005-11-11
Okay, got your message:

Is the thing below doable using only Apache?

*** From my first post: ***

And..... Let say two of my customers want it this way:

customer 100:
[www.mysite.com/customer-100](www.mysite.com/customer-100)
are put on my first backend server.

(Note: now I do not want more customers on my first backend server because more customers here will make the server to slow, so I install a second backend server.)

Customer 101:
[www.mysite.com/customer-101](www.mysite.com/customer-101)
are put on my second backend server.

Can this be done using Squid.
Note that in example d) both customers want to use a subdir of:
[www.mysite.com/](www.mysite.com/)

but here the two subdirs are actually on two different servers.

---

### Post by LordHunter317 on 2005-11-11
Apache can, via reverse proxying. In fact, it may be a better fit regardless of squid.  I certainly don't know to do it under Squid, to say the least.

At any rate, a much better solution would be to deploy a cluster of identical servers, with a hardware load-balancer or LVS server performing load-balancing in front of it.

Unless dynamic content makes this impossible, I think you'll find this is a better solution.

Why do you want the customers to show up as folders anyway?

---

### Post by bongobongo on 2005-11-12
I'm only using dynamic content.

Why I want to offer folder sites as well?

If I do that it means (some) of my customers can choose to have their site up and running in minutes, as well as being cheaper (not much), but cheaper than a unique domain name which they would have to register and wait a while before using.

And... I have looked a lot at apache and it would be fine except that I have not found how I could make it work if I wanted to start registering 
[www.mysite.com/customer-1](www.mysite.com/customer-1)    to
let say 
[www.mysite.com/customer-100](www.mysite.com/customer-100) 
on server1, 

and lets imagine that 100 sites was more than enough for that server to handle (depends on traffic for each of the sites).... then I would really like if it was possible to continue to register
[www.mysite.com/customer-101](www.mysite.com/customer-101)
and so on on server2..... and when that was full then server3 and so on.

And also I do not need load balancing, that is mainly because one customer data are to be put on one server only, and also because load balancing would require a lot of extra hardware and more complex setup, which is not what I want at this time.

Anyway

I found this software late yesterday:

[http://www.apsis.ch/pound/](http://www.apsis.ch/pound/)

It seams to be more lightweight than squid and perhaps more tuned against what I want to do, it was designed with "Reverse Proxy" and "Load Balancing" in mind, but I do not know yet if I can do all of what I want....

Regards

---

### Post by LordHunter317 on 2005-11-12
[QUOTE=bongobongo]If I do that it means (some) of my customers can choose to have their site up and running in minutes, as well as being cheaper (not much), but cheaper than a unique domain name which they would have to register and wait a while before using.[/quote]No, offer subdomains.  You do have DNS under your control right, where you can control the refresh times as well?

If not, get it.  If so, you can just offer 'customer-1.example.com', which is a far better solution IMO for people who don't want to pay for their own domainname.

> And... I have looked a lot at apache and it would be fine except that I have not found how I could make it work if I wanted to start registering 
[www.mysite.com/customer-1](www.mysite.com/customer-1)    to
let say 
[www.mysite.com/customer-100](www.mysite.com/customer-100) 
on server1, 

and lets imagine that 100 sites was more than enough for that server to handle (depends on traffic for each of the sites).... then I would really like if it was possible to continue to register
[www.mysite.com/customer-101](www.mysite.com/customer-101)
and so on on server2..... and when that was full then server3 and so on.As I said, look at mod_proxy and it's reverse proxying features.  You can, IIRC, proxy on a specific location lookup to a specific site.

---

### Post by bongobongo on 2005-11-15
Thanks for the tips of using subdomains.

That will probably solve it :D 

Best regards

---

### Post by bongobongo on 2005-11-15
Okay... one addon question I hope you can answer:

I'm having one fixed IP address.
Let say my site is:

[www.yoursite.com](www.yoursite.com)

I want to offer my customers either
a subdomain or
a unique domain name

I want to spread my customers on one or more servers within same fixed IP address:

Can I do the below using two separate servers using only one fixed IP address?
Note that I would like to be able to register (config in Apache) subdomains of
the site [www.yoursite.com](www.yoursite.com) on more than one server.
Note also that one customer will only exist on one server only. 

**** START CONFIG Server1: *****

Listen 80
NameVirtualHost *

<Virtual Host>
ServerName [www.yoursite.com](www.yoursite.com)
DocumentRoot /home/httpd/htdocs/
</VirtualHost>

<Virtual Host>
ServerName [www.customer1.yoursite.com](www.customer1.yoursite.com)
DocumentRoot /home/httpd/htdocs/customer1
</VirtualHost>

<Virtual Host>
ServerName [www.uniquename-customer-n.com](www.uniquename-customer-n.com)
DocumentRoot /home/httpd/htdocs/uniquename-customer-n
</VirtualHost>

**** END Server1: *****

**** START CONFIG Server2: *****

Listen 80
NameVirtualHost *

<Virtual Host>
ServerName [www.yoursite2.yoursite.com](www.yoursite2.yoursite.com)
DocumentRoot /home/httpd/htdocs/
</VirtualHost>

<Virtual Host>
# NOTE: that I would like to use yoursite and not yoursite2
ServerName [www.customer-n+1.yoursite.com](www.customer-n+1.yoursite.com)
DocumentRoot /home/httpd/htdocs/customer-n+1
</VirtualHost>

<Virtual Host>
ServerName [www.uniquename-customer-n+2.com](www.uniquename-customer-n+2.com)
DocumentRoot /home/httpd/htdocs/uniquename-customer-n+2
</VirtualHost>

*** END Server2 ***

Or do I have to register a new unique domain name e.g. like:
[www.yoursite2.com](www.yoursite2.com)

and in Server2 config above use this for the first virtual host:

<Virtual Host>
ServerName [www.yoursite2.com](www.yoursite2.com)
DocumentRoot /home/httpd/htdocs/
</VirtualHost>

and still be able to keep the other virtual hosts the same for Server2?

Would appreciate any suggestions.

---

### Post by LordHunter317 on 2005-11-15
You can do it the way you originally suggested.

One thing to note is the first VirtualHost on any given address is the "Default" VirtualHost.  Any requests Apache can't figure out the destination for will be redirected there.

As such, you should create a default virtualhost on all your servers besides the first and have it redirect to your main site, in case someone tries to do something unusual.

---

### Post by bongobongo on 2005-11-15
Do I understand you right when you say:

"You can do it the way you originally suggested."

that you mean the config for Server1 and Server2 in my previous post?

If so:

If a client enter:
[www.customer-n+1.yoursite.com](www.customer-n+1.yoursite.com)
which is on Server2

How does Server1 know that it is not supposed to reply to this request?

Or if I had let say 4 server set up similar:

How does the other three servers know it is not supposed to reply?

And how does Server2 know it has to reply?

---

### Post by LordHunter317 on 2005-11-15
[QUOTE=bongobongo]
that you mean the config for Server1 and Server2 in my previous post?[/quote]Yes, subject to the caveat I mentioned.


> How does Server1 know that it is not supposed to reply to this request?Because the DNS A/CNAME record for customer-n.example.come would point to server2, not server1.

Server1, for all intents and purposes, wouldn't even know that site exists.

> And how does Server2 know it has to reply?Because you've added a VirtualHost entry for it.  When someone enters that hostname, DNS will return the IP for server2, and that's what they'll connect to.

---

### Post by bongobongo on 2005-11-15
(I'm a newbie, and hopefully last one here)

"
Quote:
And how does Server2 know it has to reply?

Because you've added a VirtualHost entry for it. When someone enters that hostname, DNS will return the IP for server2, and that's what they'll connect to.
"

Does the above mean I have to have different (external) IP address for Server1 and Server2 or are you referring to different IP address within my LAN?

(I was hoping to get this to work with only one fixed IP address.)

Anyway, thanks for beeing patient and helpful!

---

### Post by LordHunter317 on 2005-11-15
You'll need multiple public IPs.

And if you're going to be hosting that many people, you'll have them.  You would never want a single address, and multiple IPs are cheap compared to having proper colocated rackspace and hardware to actually offer this sort of service.

---

### Post by majikstreet on 2005-11-15
I just wanted to put my input in... If you have 100 customers, you'd need 100 servers to make each customer on a seprate server....

Guess what? Hosting companies take a couple servers, and overload them with customers.

---

### Post by LordHunter317 on 2005-11-15
I'm confused as to who that's directed to, or how it's relevant here, seeing as all parties involved are already well aware...

---

