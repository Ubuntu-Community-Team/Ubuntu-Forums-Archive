---
title: "Web Server - Is this possible?"
date: 2007-03-28
forum: Server Platforms
---

### Post by TheGameAh on 2007-03-28
I'm not even sure if this is possible or not, but I wanted to get opinions.

I want to setup an Ubuntu webserver at my medium sized company.  I'd like to throw it in the DMZ.  I want internal users (192.168.0.x) to be able to access it, no problem.  I want people coming in from outside to have to login to access the default web site.

Am I off my rocker here?

I setup something similar on a 2003 Server.  However, I created a single name and password for users to access from the outside.  I'd like to have multiple names and passwords, hence my thinking about Ubuntu.  I figured it might be easier that route.

---

### Post by Jonne on 2007-03-28
You should be able to do that with mod_auth_mysql . It's not exactly easy to get working, but it's powerful when you do. Use Google to get some pointers.

---

### Post by az on 2007-03-28
> **TheGameAh said:**
> 
Am I off my rocker here?


Not at all.  Apache can handle any number of virtual hosts.  You would want to make one which serves requests from the outside world and one which serves requests from your LAN.  Depending on what level you do the authentification ( does your web application handle logging in or do you want the webserver to do it) there are more than one option for setting that up.

---

### Post by Frosty Cold Drink on 2007-03-28
> **az said:**
> Not at all.  Apache can handle any number of virtual hosts.  You would want to make one which serves requests from the outside world and one which serves requests from your LAN.  Depending on what level you do the authentification ( does your web application handle logging in or do you want the webserver to do it) there are more than one option for setting that up.

Doing this affords no security at all.

All you need to do is use the Satisfy directive with the any parameter. Apache has decent examples: [http://httpd.apache.org/docs/2.0/mod/core.html#satisfy](http://httpd.apache.org/docs/2.0/mod/core.html#satisfy)

---

### Post by az on 2007-03-28
> **Frosty Cold Drink said:**
> Doing this affords no security at all.

All you need to do is use the Satisfy directive with the any parameter. Apache has decent examples: [http://httpd.apache.org/docs/2.0/mod/core.html#satisfy](http://httpd.apache.org/docs/2.0/mod/core.html#satisfy)

The problem with letting Apache do the authentification is that it is not very flexible nor is it pretty.  

It all really depends on what web application we are talking about.  If this is something to be built from scratch, my point is that ther are a lot of ways to do it.  If you want to use a premade CMS, again, many of them can handle running multiple sites from the same instalation.  One way to accomplish what the original poster would want would be to set up two sites on the same host, one which serves the public and one which serves the private LAN.  Again though, I don't know what the exact details are.  Do both sites serve the same purpose?

As far as security, any LAMP web application will only ever be as secure as PHP itself.  I hear that php5 is loads better than php4 insofar as security, but I am not an authority on the topic.

---

### Post by TheGameAh on 2007-03-29
In terms of what this will be used for: just a brief history.

This is our intranet site.  Running on a 2003 server, for internal users only.  Then the request, "Well, can this be available for outside people as well?"

Eh, don't want to do it, but I add a DNS entry, and disable anonymous access.  So internal users are okay through the integrated logon.  Outside users key in a name and password (just a generic single username and password for ALL outside users).

Now the second request.  Can we have multiple name and passwords for everyone?

Bah, now I've hit the wall.  I won't create 50 usernames and password just for web use (don't have the CALs anyway).

I've been wanting to move away from 2003 for hosting and switch to Ubuntu anyway, due to the power of lamp (although for this simple intranet site, wouldn't really be using it to its fullest).  But I was hoping lamp would be easier in regards to this idea, which is just a simple intranet site.  Users inside the LAN get right into it.  Users outside the LAN have to put in a name and password.

---

### Post by nihilocrat on 2007-03-29
I would suggest implementing authentication within your webapp, especially if you want everyone to use the same username and password (which I think is bizarre if this is actually a non-trivial app that people outside the company will see, and perhaps insecure). The internal/external seperation should probably be done with vhosts, as suggested above. You could also do this from within your webapp with a few lines of code saying "if the user has a 172.20.x.x IP, let them in the internal side, otherwise external", but that might be insecure depending on how hard IP spoofing is (I have no experience in cracking).

---

### Post by wayne_za on 2007-03-29
I would recommend using a CMS PHP application like [**Joomla**]("http://joomla.com") or another like [**egroupware**]("http://www.egroupware.org") that will allow you to create user accounts or they can subscribe themselves.


See the demo of [**egroupware**]("http://www.opensourcecms.com/index.php?option=com_content&task=view&id=354") here it has a SiteMgr - Development application to generate webpages you can add a login section.

Good luck

---

### Post by Mr. C. on 2007-03-29
I'm going to step back from *solutions* for a moment, and ask that you focus first on your *requirements*.

The answer to your question is a resounding YES, you can absolutely do what you requested, with as much simplicity or complexity as you require to meet those requirements.

Moving to a new system is a lot of work.  I'd suggest you start with the simplest mechanism that meets your needs.  As you become more and more familiar with the system, add more features and complexity as required.  Too many admins get in over their heads and compromise their systems, or become wed to some particular solution-du-jour regardless of how well it is suited for a particular business case.

I hope this helps,
MrC

---

### Post by T.M on 2007-03-30
I think you can make it with apache htaccess. 
Maybe something like this will work. I did not test it (by the way) :) You can find good tutorials about htaccess & htpasswd.

.htaccess-file
-----------------------------
order deny,allow
deny from all
require valid-user
AuthName "Internet-site"
AuthUserFile /var/www/html/.passwd
AuthType Basic
allow from 127.0.0.0/255.0.0.0
#Internal-network
allow from 192.168.0.1/255.255.255.0
satisfy any

---

