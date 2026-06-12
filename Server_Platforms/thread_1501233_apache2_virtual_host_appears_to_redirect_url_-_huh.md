---
title: "apache2 virtual host appears to redirect url - huh?"
date: 2010-06-04
forum: Server Platforms
---

### Post by urobb on 2010-06-04
Hi, 

My goal is a testing server with an apache virtual host for each site that I'm working on, with fairly painless setup for each new job.

For example, I want [http://site-a.mydomain](http://site-a.mydomain) to server this document root /home/client-a/site-a/public_html (or something to that effect)

Ideally, DNS will use a wildcard to point [http://anything-i-type.mydomain](http://anything-i-type.mydomain) to the testing server, and apache will have a dynamic virtual host definition that will do a little magic so that I won't have to mess with DNS records or add a new virtual host each time I add a new site for a client.  I'll worry about that when I get there, just put that out there in case anyone has any tips!  for now I just have one little problem that's hurting my mood-

It looks like I've got my DNS server working just fine, so yay there- BUT my first attempt at adding a virtual host isn't working quite how I expected- meaning that site-a.mydomain now serves up the correct document root, but when you put [http://site-a.mydomain](http://site-a.mydomain) into the browser's address bar, the address bar is then updated to [http://10.0.1.100/site-a/public_html](http://10.0.1.100/site-a/public_html) - bogus!!  I must be missing an option like "FunnyBusiness Off" - Can anyone think of what I might be doing wrong here? 

root@ubuntuvm:/etc/apache2/sites-available# vim client-a.mydomain
<VirtualHost *:80>
        UseCanonicalName Off
        ServerName site-a.mydomain
        DocumentRoot /home/client-a/site-a/public_html
</VirtualHost>

The computer wins tonight :(  
I sure would appreciate some tips!  Thanks in advance!

---

### Post by urobb on 2010-06-04
I guess I should also mention that the default virtual host's document root points to /home/client-a .  not part of the plan, just sayin.

---

### Post by urobb on 2010-06-04
Doh!  Don't be stupid like me!  When you are teaching yourself about virtual hosts, don't make your first attempt point to an existing site on your machine, just try pointing to a dummy folder first.  There was a php redirect happening in the open source software that I was pointing to that I wasn't expecting.  Since I wasn't familiar with virtual hosts I thought I was doing something wrong.

---

