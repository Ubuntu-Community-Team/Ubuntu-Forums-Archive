---
title: "[SOLVED] Apache, SubDomains, and Virtual Hosts"
date: 2008-11-15
forum: Server Platforms
---

### Post by Mr_H on 2008-11-15
I'm having some fustrating issues setting up a subdomain on Virtual Hosts.  I've searched these forums and tried numerous solutions, as well as googled for possible answers and I'm still boggled.

Here's what I'm trying to do.  I'm running Ubuntu 8.04 server with Apache 2.2.8.  
My website **[www.example.com](www.example.com)** works.  I have it setup so you can access individual user directories via [www.example.com/~user](www.example.com/~user)  (It's in the users /home/user/public_html directory).
 I want to setup **subdomain.example.com**, which will point to the contents of /home/subdomain/user (essentially a users home directory, just with the subdomain name).  

First I set my dns so that a CNAME of subdomain points to subdomain.example.com. (My DNS is hosted at Godaddy.com and not my own server right now).

Then I did the virtual hosts.  I've done it two ways and both have caused problems.

**Method 1**:  /etc/apache2/sites-avaialble/example.com I added to the end the following:
<VirtualHost *:80>
	ServerName subdomain.example.com
	DocumentRoot /home/subdomain/public_html
</VirtualHost>

**Method 2**:  I created /etc/apache2/sites-avaialble/subdomain.example.com and added:
NameVirtualHost *:80
<VirtualHost *:80>
	ServerName subdomain.example.com
	DocumentRoot /home/subdomain/public_html
</VirtualHost>

Enabled the sites, reloaded apache, and both fail to bring up the different directory, instead they brought up the default root directory (The one that example.com would point to).

I'm really kind of stumped on this.  I'm sure I'm missing something simple, cause I know it's not supposed to be this difficult.  Any suggestions from folks out there on what I'm doing wrong?

Thanks muchly
H

---

### Post by BlackHero on 2008-11-15
hi =)

you need install ispconfig =)

---

### Post by Mr_H on 2008-11-15
Thanks for the suggestion...I was hoping o find a way to pull this off without installing another software package however (the rest of the software that ISPConfig seems to work with is operating just fine)  I know this has to be possible, just not sure why I'm failing at it :/

Thanks though:)

---

### Post by Philio on 2008-11-15
The NameVirtualHost needs to come first, I think, before any VirtualHost declarations.

I've not used them wildcarded, on my servers I have 1 config file per IP or per domain usually hence have them all the the format:

NameVirtualHost 1.2.3.4:80
VirtualHost 1
VirtualHost 2
etc

---

### Post by Mr_H on 2008-11-15
Thanks for the suggestions...but as it turned out, I had a DNS error:(  just a simple typo that I had overlooked.  I knew it was simple, oops :/

Thanks for taking the time to offer up help though, much appreciated:)

---

