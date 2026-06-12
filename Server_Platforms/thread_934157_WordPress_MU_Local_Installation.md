---
title: "WordPress MU Local Installation"
date: 2008-09-30
forum: Server Platforms
---

### Post by FGazerro on 2008-09-30
Hello, 

I'm running Ubuntu Desktop and have been trying to perform a local install of WordPress MU. I currently have regular WordPress installed in /var/www and it works fine. I want to install WPMU in /var/www/wpmu. 

When I attempt to browse to the index.php for WPMU I don't even get the installation page. Instead, I get the following errors:
[I]
[INDENT]
Warning: constant() [function.constant]: Couldn't find constant VHOST in /var/www/wpmu/wp-settings.php on line 100
Warning: constant() [function.constant]: Couldn't find constant VHOST in /var/www/wpmu/wpmu-settings.php on line 33
No WPMU site defined on this host. If you are the owner of this site, please check Debugging WPMU for further assistance.[/INDENT][/I]

I'm pretty sure its a problem with setting up a virtual host. I have been through the WPMU ReadMe, other forums and read a bunch of HowTo articles and just can't seem to get anything to work. 

I'm very new to working with Apache2. So, if anybody could help or give me some instructions that a five year old could follow, that would be great. 

Thanks for your time.

Frank

---

