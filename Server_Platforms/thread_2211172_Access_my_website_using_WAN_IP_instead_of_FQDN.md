---
title: "Access my website using WAN IP instead of FQDN"
date: 2014-03-14
forum: Server Platforms
---

### Post by Loan_Refi on 2014-03-14
Alright I"m having a brain *art.

I need to access my website using IP address both from WAN & LAN but I can't figure out how to do it. 

My website is working and accessible via FQDN example.com

Here is my current setup:

Ubuntu Server 13.10 64bit
I have Drupal 7 installed, multisite configuration

Problem is I cannot access my website via Public IP X.X.X.X. If I try to access my website using the Public IP I get the Apache default page:

"It works!
This is the default web page for this server.
The web server software is running but no content has been added, yet."

Here is my VirtualHost configuration for /etc/apache2/sites-avilable/mydomain.com.conf

<VirtualHost *:80>
ServerName mydomain.com
ServerAlias *.mydomain.com [www.mydomain.com](www.mydomain.com)
DocumentRoot /var/www/drupal
<Directory "/var/www/drupal>
Options FollowSymlinks
AllowOverride All
</Directory>
</VirtualHost>

My Drupal install is located:
/var/www/drupal

My website folder I need to access is located:
/var/www/drupal/sites/mydomain.com

and my other websites are there too /var/www/drupal/sites/example1.com example2.com etc...

So again what I need to accomplish is:

WAN IP X.X.X.X example.com but I only access the Apache default "It Works" page.
Same with Private IP. which is fine I guess since I have a multisite 

My Ubuntu Serve /etc/hosts file:
127.0.0.1	example.com	WebSRV	localhost
127.0.0.1	WebSRV
X.X.X.X	example.com	webSRV localhost  <-----This is my WAN IP
127.0.1.1	WebSRV
::1	WebSRV.example.com	WebSRV	localhost

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters


So can someone please help me with this? My guess is probably adding the WAN IP in VirtualHost file??

---

### Post by SeijiSensei on 2014-03-14
"Name-based" virtual servers are exactly what they sound like.  Apache uses the server's hostname to determine which site's content should be transmitted.  If you use an IP address in a URL, there can be no matching by server name, so you end up with the default site in /var/www.

---

### Post by Loan_Refi on 2014-03-14
U R 100% correct! I rushed back here to post. Like I said I was having a brain *art so didn't think..

Because I have a multisite Drupal install someone question me about our IP address coming up with "It Works..." and was told to fix it which is why I posted my question.

But what I'm going to do, no, what we want done is to direct all default traffic to 1 specific domain. That's all. Apache is great! It's Friday and I made things difficult.

Thank you for your reply.
Happy Friday!

---

