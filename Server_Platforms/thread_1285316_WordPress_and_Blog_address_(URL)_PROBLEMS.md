---
title: "WordPress and Blog address (URL) PROBLEMS"
date: 2009-10-07
forum: Server Platforms
---

### Post by jeffsa12 on 2009-10-07
I installed WordPress 2.8.4 on my Ubuntu 8.04 lamp server. I have a simple website up on the server, and wanted to add WordPress.

The install it in my servers /var/www/blog and all was good, had things working on my local network. I wanted to make it available on the www, so I changed the WordPress and Blog address URL's in the General Settings page.

I changed them from [http://192.168.0.4/blog](http://192.168.0.4/blog) to [http://www.jeffstory.org/blog](http://www.jeffstory.org/blog).

I tried to access it through [http://www.atunnel.com/](http://www.atunnel.com/) and can't get to my WordPress, [http://www.jeffstory.org/blog](http://www.jeffstory.org/blog). I realized that once I changed the URL from local to www, I wouldn't be able to access it unless I went out out, then back in using atunnel. Same thing if I try to goto [http://www.jeffstory.org](http://www.jeffstory.org) from within my local network.

If I point my (local) browser to my server's local ip, I can get my web page as normal. If I click my "home" or "blog" links, I get redirected to my router log in which is normal...

How to correct what I've messed up?? Do I have to get into the database and change things, or an easier fix??

How do I correctly set up wordpress to be reachable from www?

---

### Post by cdenley on 2009-10-07
Wordpress is accessible.
[http://www.jeffstory.org/blog](http://www.jeffstory.org/blog)
Works for me. I was a little confused about what you tried, but if you try accessing your WAN IP (68.180.151.74), which is what your domain should resolve to, from inside your LAN, some routers will not follow your port forwarding rules and route it back to your server. You would have to use your server's LAN IP from within your LAN.

---

### Post by jeffsa12 on 2009-10-07
Thanks cdenley

I believe you're seeing my website and not my blog. I'm at work now, and can't access my blog from here. 

When I go to [http://www.jeffstory.org/blog](http://www.jeffstory.org/blog) It's the same as going to [http://www.jeffstory.org](http://www.jeffstory.org), which is my website.

68.180.151.74 is a yahoo ip...I signed up for a free website (template) account at yahoo that I don't use, and just use the service to forward [www.jeffstory.org](www.jeffstory.org) to my dynamic WAN IP  97.113.58.211 (at the moment) router, then to the lamp server on my local network. I get by without paying my ISP for a static IP that way.

My router does not let me get to my WAN ip from within my local home network (LAN). Before I changed WordPress URL's I could access it via [http://192.168.0.4/blog](http://192.168.0.4/blog). Now I only get an HTML version, and can't get logged into WordPress, as I get directed back to my router log in when I enter my UN & PW.

To check my website from home, I use a free proxy server [http://www.atunnel.com](http://www.atunnel.com) or [http://kproxy.com](http://kproxy.com) to go through, then back to my server. I can access my website from within my local network using the local ip, but I can't check the links that lead to my home page. 

Thats what I was trying to explain I had done to check my WordPress in my first post.

---

### Post by cdenley on 2009-10-08
I see now. You have an external site which sticks your real site in a frame, hiding the actual URL. The problem is your frames page ignores what document is being requested, and simply sticks your home page in the frame. In other words, [http://www.jeffstory.org/blog](http://www.jeffstory.org/blog) puts [http://97.113.58.211](http://97.113.58.211) in the frame, not [http://97.113.58.211/blog](http://97.113.58.211/blog). It doesn't forward the request. Did you create the frameset page yourself, or is it a redirection service? Do they offer a dynamic DNS service instead?

```

cdenley@ubuntu:~$ wget -q -O - [COLOR="Red"]**http://www.jeffstory.org/blog**[/COLOR]
<html><head><title>jeffstory.org</title>
<meta name="keywords" content="jeff story,jeffrey a story,jeffstory,Shelton,Wa,LAMP,LAMP server,linux,apache,apache2,httPHP,Python,ubuntu server,ubuntu,debian,hybrid gas,hybrid diesel,economy,Apache2,httpd,GNU,open source,wordpress,AMD quad core,amd phenom,home server,hardware,software">
</head>
<frameset rows="100%" scrolling="yes" border="0">
<frame src="**[COLOR="Red"]http://97.113.58.211[/COLOR]**">
<frame src="http://webhosting.yahoo.com/forward.html" marginwidth="0" marginheight="0"  scrolling="no" frameborder="0"></frameset></html>

```

---

### Post by jeffsa12 on 2009-10-08
No I didn't create a frameset page, it's a domain forwarding service.

I don't see an option for dynamic DNS service. They do have the following:

> Manage Advanced DNS Settings
Create or modify advanced domain name records (such as MX records).

and 

> 
A and CNAME Records
Use A and CNAME records to manipulate host names.
Add Record

MX Records
MX records specify the servers that power your email service.
Change MX Records

Name Servers
Your name servers specify the location of your web site and email repository
Unlock Domain


If I go to  [http://97.113.58.211/blog](http://97.113.58.211/blog) from [http://www.atunnel.com](http://www.atunnel.com), I get what looks like an HTML only version of my wordpress blog.

---

### Post by cdenley on 2009-10-08
You don't see any styling because it is trying to pull your stylesheet from [http://www.jeffstory.org/blog/wp-content/themes/default/style.css](http://www.jeffstory.org/blog/wp-content/themes/default/style.css), which will return your "domain forwarding" frames page.

Can you add an A record so your domain resolves to 97.113.58.211, instead of yahoo's server with the "domain forwarding" frames page? You don't want to use "domain forwarding", you want that domain to resolve to your IP, not yahoo's.
```

host www.jeffstory.org

```

---

### Post by jeffsa12 on 2009-10-08
OK,

I made the following changes in my Yahoo control panel.
These changes eliminated my domain forward. 
Now [http://www.jeffstory.org](http://www.jeffstory.org) ... I just get my Yahoo template webpage.

Would these changes possibly take some time to "activate"?

```

Type:	           Source:	        Destination:	  Actions:
A Record	*.jeffstory.org	        97.113.58.211   Edit | Delete
A Record	jeffstory.org	        97.113.58.211   Edit | Delete
A Record	mail.jeffstory.org	97.113.58.211	Edit | Delete
A Record	www.jeffstory.org	97.113.58.211	Edit | Delete

```

---

### Post by jeffsa12 on 2009-10-08
OK,

Now it's working!!!

Just needed to wait a few minutes.

---

### Post by cdenley on 2009-10-08
> **jeffsa12 said:**
> Would these changes possibly take some time to "activate"?


Yes. The TTL appears to be 600 seconds, so it can take up to 10 minutes for changes to propogate.

It appears to be working correctly for me.

---

### Post by jvin248 on 2011-09-27
That timing is key to note!  

The OP problem description has many of the details I was experiencing. I have a LAN mounted Virtual Machine server hosting wordpress and I want it externally linked, plus be able to edit it from the LAN side.  Doing the steps below skips the need for the 'atunnel.com' proxy server.

Just in case I get here after googling for this problem again .. accessing a local wordpress instance from an externally accessible URL (again) ..also called "changing site url" on some other posts .. here are the steps:

-$ nano /var/www/books/wp-content/themes/twentyeleven/functions.php
-add lines just after >php?
     update_option('siteurl','http://your.site.url:port/yourblog');
     update_option('home','http://your.site.url:port/yourblog');
-refresh your web browser using your external url
    [http://your.site.url:port/yourblog](http://your.site.url:port/yourblog)
-$ nano /var/www/books/wp-content/themes/twentyeleven/functions.php
-remove those lines you just added (or comment them out)
-go get into your router (these steps are for pfSense, other routers should have similar settings to look for/watch out for)
-add to firewall/nat
         wan/tcp/port/LAN.server.IP/80
-add to firewall/rules
         tcp/*/port/LAN.server.IP/port/*
-uncheck the box at System/advanced/network address translation/Disable NAT Reflection 
        "Disables the automatic creation of NAT redirect rules for access to your public IP addresses from within your internal networks. Note: Reflection only works on port forward type items and does not work for large ranges > 500 ports."

Then go do something for ten minutes and when you get back see if the external url from a lan browser brings the page up correctly.

YMMV

---

### Post by jvin248 on 2011-09-27
That timing is key to note!  

The OP problem description has many of the details I was experiencing. I have a LAN mounted Virtual Machine server hosting wordpress and I want it externally linked, plus be able to edit it from the LAN side.  Doing the steps below skips the need for the 'atunnel.com' proxy server.

Just in case I get here after googling for this problem again .. accessing a local wordpress instance from an externally accessible URL (again) ..also called "changing site url" on some other posts .. here are the steps:

-$ nano /var/www/books/wp-content/themes/twentyeleven/functions.php
-add lines just after >php?
     update_option('siteurl','http://your.site.url:port/yourblog');
     update_option('home','http://your.site.url:port/yourblog');
-refresh your web browser using your external url
    [http://your.site.url:port/yourblog](http://your.site.url:port/yourblog)
-$ nano /var/www/books/wp-content/themes/twentyeleven/functions.php
-remove those lines you just added (or comment them out)
-go get into your router (these steps are for pfSense, other routers should have similar settings to look for/watch out for)
-add to firewall/nat
         wan/tcp/port/LAN.server.IP/80
-add to firewall/rules
         tcp/*/port/LAN.server.IP/port/*
-uncheck the box at System/advanced/network address translation/Disable NAT Reflection 
        "Disables the automatic creation of NAT redirect rules for access to your public IP addresses from within your internal networks. Note: Reflection only works on port forward type items and does not work for large ranges > 500 ports."

Then go do something for ten minutes and when you get back see if the external url from a lan browser brings the page up correctly.

YMMV

---

