---
title: "Getting from a Dynamic IP to domain name?"
date: 2008-11-18
forum: Server Platforms
---

### Post by basicxman on 2008-11-18
Hey y'all,
   If I have a Ubuntu server with apache and it's all set up.  What service can I use to get from dynamic IP to a domain name?  Something like godaddy.com?  How do I use these services? 

Thanks!

---

### Post by y@w on 2008-11-18
I've used no-ip.com and dyndns.org both and they work very well. Dyndns has support for most home routers. Then you can buy a domain from GoDaddy and point your domain to your no-ip or dyndns address as a CNAME. I've been doing that for years and it works pretty well.

---

### Post by basicxman on 2008-11-18
Is there a step by step guide to using those services for free?

---

### Post by CrucifiedEgo on 2008-11-18
I'll try my best to diagram the whole process, so you can break it down and figure out each piece (searching the forums and google are your friends).

Step 1: DNS Request
The first thing that's going to happen is the browser sends out a few requests to find out where the domain lives.  This eventually ends up at your registrar.  They can say "hey, it's over on ns1.otherhost.com and ns2.otherhost.com"(This is known as "delegating nameservers", they can say "it's at 123.45.6.78"(This is known as an A record) or they can say "it's at host.domain.com"(this is known as a CNAME).  if a CNAME is encountered, the browser starts the process over again, looking for the IP for host.domain.com.  So, if you use a CNAME to point yourdomain.com and [www.yourdomain.com](www.yourdomain.com) to yourname.dyndns.org, you can see that it will follow that "link" and end up at your dynamic IP.  

Personally, I recommend MyDomain.com for registrations.  The domains are as cheap as you generally can get, the DNS service is free, as is the email forwarding(even for domains you don't register there).  I used to work for them, they're good guys.

2: HTTP Request

Once the browser knows where the server is, it connects to that server on port 80 (or for https connections, port 443).  Obviously, you need to be reachable from the outside world on port 80, so you may need to open up a "port forward" on your router to the server you've setup.  Once connected, the browser asks it for the site.  It's going to send the URL that is being requested, so the Apache web server can send different content for webmail.yourdomain.com, [www.yourdomain.com](www.yourdomain.com), and files.yourdomain.com if you want it to.  This is known as virtual hosting.  

I hope this helps... Take the whole thing one step at a time.  Get it working with just the IP address within your network.  Then open up the router and try with your external IP.  Then setup dynamic DNS and make sure that works.  Lastly, set up your domain name with the CNAME to your dynamic dns provider, and you should be good to go.

---

### Post by volkswagner on 2008-11-18
The setup depends on many factors (router, dynamic DNS service, etc).  To get a comprehensive how-to may prove to be difficult.

You may want to start with your router model and dynamic DNS as a search.

The following was very helpful with my Linksys router.

[http://ubuntuforums.org/showthread.php?t=683270]("http://ubuntuforums.org/showthread.php?t=683270")

---

