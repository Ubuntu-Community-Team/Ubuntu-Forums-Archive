---
title: "Apache2 return ip address instead of domain name"
date: 2007-02-06
forum: Server Platforms
---

### Post by deadairwaves on 2007-02-06
Hi,

I'm currently running apache2 at home on a Ubuntu 6.10 server.  The server's sit behind a Netgear router.  The server's internal IP address is 192.168.1.5.  I forward port 80 on the router to that address.  I use DNS2Go to map my dynamic external IP address to my registered domain name.  Everything works fine.  I can view my site from my internal network and from the outside.  

However, there's one annoying quirk.  As soon as I visit my site, the address bar in my browser shows my external ip address rather than my domain name.  It's kind of annoying.  I have a feeling that it's a simple setting in the Apache config, but I can't seem to figure it out. 

My /etc/hostname file has my FQDN in it, and my /etc/apache2/apache2.conf file has a ServerName directive in it with my FQDN.  

Any ideas?  I'm sure it's something simple that I'm missing, but I'm a bit stumped.  Thanks.

---

### Post by MJN on 2007-02-06
I stand to be corrected however I don't think Apache can cause an address change in the Address bar, not without a rewrite rule in place (which you would have to have put in).

What's the domain? Let's see what it looks like from here.

You haven't got DNS2Go set to *forward* the domain name to your IP address have you (as opposed to resolving the address via DNS)? I'm not familiar with DNS2Go's services...

Mathew

---

### Post by MJN on 2007-02-06
Thanks for the PM.

The problem is exactly as I suspected - DNS2Go are actually forwarding clients when they are requesting your site by its domain name to your IP address. 

They are doing this in two ways - the first (when clients don't specify a particular document) is by wrapping up your site inside a big frame hence why your name sometimes stays in the address bar. This is bad - it plays havoc with many search engines, might be completely inaccessible to some browsers, and is generally just a bit naff.

The second, when clients ask for specific documents (i.e. not just the root), is that they are stripping off your domain name and bolting what's left on the end of your IP. This is slightly better, however it does mean the address bar gets rewritten.

Hence, you need to configure DNS2Go not to use redirection/forwarding (or whatever they might call it) and actually use their raw DNS service to resolve your name directly to your IP address. I'm not familiar with the mechanics of doing this at DNS2Go (likely a control panel does it all) so perhaps someone else can chime in with the steps requires to do this. Or read whatever online help they've got available.

To summarise; it's not an Apache issue but rather how DNS2Go are managing your domain.

Mathew

---

### Post by yeuker on 2008-07-22
I am having the same problem.  When I navigate to my site using my domain name in the URL bar on the browser, it takes me to my site but the location switches from my domain name to my IP address. 

I am using Ubuntu 8.04 LAMP and zoneedit and do not have WebForward set up.  I only have an IP address (A) set up.  When I take my webserver down, zoneedit does not forward to the IP and my domain name stays in the location bar.  Can someone please help?

Thanks,

Cory

---

### Post by MJN on 2008-07-22
What's the URL?

---

### Post by yeuker on 2008-07-22
Ok, some more information:

My domain name is maksymchuk.com
I am using zoneedit for my dynamic dns service
I am using ddclient to update zoneedit

Stranger yet, when I type maksymchuk.com into firefox, it still redirects me to yesterday's old IP address.  

My current IP address on my home computer is: 142.161.88.128

I know this is correct because I can ssh into my home box.

Ping looks it up correctly. 

Z:\>ping maksymchuk.com

Pinging maksymchuk.com [142.161.88.128] with 32 bytes of data:

It also appears that my dns is set up properly:

[http://www.checkdns.net/quickcheck.aspx?domain=maksymchuk.com&detailed=1](http://www.checkdns.net/quickcheck.aspx?domain=maksymchuk.com&detailed=1)

I'm going crazy :-(.

Thanks again gurus.

---

### Post by yeuker on 2008-07-22
OK, more information. I just put in an index.html page with the words 'it works.' and everything works but I have wordpress running on apache so the index.php should work.  Try this ip address:

[http://www.maksymchuk.com/index.php](http://www.maksymchuk.com/index.php)

Somehow it redirects you to [http://142.161.93.11/](http://142.161.93.11/)

???? I dont get it.

---

### Post by yeuker on 2008-07-22
Update: Pretty sure wordpress may be at fault here.  I'll post back when find the solution.

---

### Post by yeuker on 2008-07-22
Took me forever.  Thought it was apache but it isnt.  Thought it was zoneedit but it wasnt.  Turns out it was wordpress!!!!

Here is the solution:

[http://www.tamba2.org.uk/wordpress/site-url/](http://www.tamba2.org.uk/wordpress/site-url/)

Thanks for the help folks.

Cory

---

