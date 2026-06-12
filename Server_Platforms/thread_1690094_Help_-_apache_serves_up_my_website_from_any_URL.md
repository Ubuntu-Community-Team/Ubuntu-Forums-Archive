---
title: "Help - apache serves up my website from any URL"
date: 2011-02-17
forum: Server Platforms
---

### Post by MountainX on 2011-02-17
I'm running Ubuntu 10.04 with apache, rails, mysql, etc.

My rails site is running at [www.example.com](www.example.com). I'm intending to use named-based virtual hosting and I have a virtual hosts file configured/enabled for [www.example.com](www.example.com). My site is hosted on Amazon EC2.

The problem is that if I set up a new DNS record -- say test.example.com -- and browse to that, my site [www.example.com](www.example.com) is served up! That's without configuring any new virtual hosts.

And the same is true if I go to my DNS records and define test2.example.com, etc. Without touching my server, these new URLs serve up my website. 

That's not what I want! I want to use name-based virtual hosting and host different sites for each subdomain.

Where could my problem be?

Here's my virtual hosts file:
```
ServerSignature Off
ServerTokens Prod
#NameVirtualHost *:80 - this is defined in a default config file already.

<VirtualHost *:80>
	ServerAdmin webmaster@example.com
	UseCanonicalName On

	ServerName www.example.com
	DocumentRoot /home/ubuntu/example/public
	ErrorLog /home/ubuntu/example/log/error.log

	<Directory /home/ubuntu/example/public/>
		   AllowOverride all
		   Options -MultiViews 
	</Directory>

</VirtualHost>
```

---

### Post by volkswagner on 2011-02-17
```
VirtualHost *:80
```


This is a wild card.  Therefore **any** request directed at this server, that is **not** explicitly handled by another server/host file will have contents of this host file honored.

I'm not a programmer so forgive my poor writing...

So I think all is working.

You should create the host, before the DNS entry if you dont want this behavior.

---

### Post by MountainX on 2011-02-17
As I understand it, <VirtualHost *:80> in this file has to match what is defined elsewhere. The default debian/Ubuntu ports.conf has this defined:
NameVirtualHost *:80
Listen 80

Therefore, each virtual hosts file should be defined with <VirtualHost *:80> to avoid a warning like this:

[Fri Feb 18 00:37:23 2011] [warn] NameVirtualHost *:80 has no VirtualHosts

Furthermore, if I redefine <VirtualHost *:80> to something more restrictive in my virtual hosts file, I get an internal server error response.

---

### Post by volkswagner on 2011-02-17
Perhaps we need a new approach.

What would you like to happen when navigating to a subdomain with no virtual host?

---

### Post by MountainX on 2011-02-17
> **volkswagner said:**
> Perhaps we need a new approach.

What would you like to happen when navigating to a subdomain with no virtual host?

Thanks. My problem is partly that I don't know enough to ask the right question.

I have a site set up and it is running ([www.example.com](www.example.com)). Now I want to set up test.example.com on the same server with the same IP address. So I need name-based virtual hosting.

To create test.example.com, I make a copy of the virtual host file pasted above, edit the ServerName, DocumentRoot, etc. I also make the new site in the new DocumentRoot and I create the DNS record. I enable the new virtual host, check with apache2ctl -t (response "Syntax OK"), run /etc/init.d/apache2 graceful. At this point, both test.example.com and [www.example.com](www.example.com) should be available. But test.example.com is not available ("can't find server") and the original site [www.example.com](www.example.com) goes down too!

The only way I have found to "fix it" is to revert all the setup for test.example.com and restart apache. Then the first site comes back up.

I have read all the virtual hosts docs. I can't see any problems anywhere in my config. But something is obviously very wrong.

---

### Post by MountainX on 2011-02-17
Solved! Unbelievable... The problem was incorrect permissions on the log directory of the 2nd site. I never would have believed this would bring both sites down, so I was not looking for something like that. I was looking for something general to both sites.

Thanks for your help volkswagner!

---

### Post by volkswagner on 2011-02-17
After creating the new apache2 host file did you enable it?
....
EDIT:

Glad you got it working!


Sounds like Apache2 did not restart.  It can be picky that way...LOL

Also if you restart apache2 without the graceful, you may see the error in the terminal or at least notice if apache actually restarted.

sudo /etc/init.d/apache2 restart

---

