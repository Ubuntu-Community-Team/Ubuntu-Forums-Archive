---
title: "setting up perl and cgi to run on apache2"
date: 2009-07-15
forum: Server Platforms
---

### Post by kennedy7 on 2009-07-15
Hello all. I have been hosting a webserver for almost 2 years now. I host on Ubuntu 9.04 server edition. I have a mail server, a webserver, mysql server, snort network intrusion detecttion server, an irc server, php, and more. But i cant run cgi or perl scripts on my server. Any time i have tried enabling cgi as an apache module and then direct my browser to a cgi or perk script it either tries to download the file or just lets me view the script text. Basically all i want to be able to do is to be able to run perl and cgi scripts from any directory. 
Here is what a setup virtualhost looks like on my setup.

<VirtualHost *:80>
ServerName website.something.com
ServerAlias [www.website.something.com](www.website.something.com)
DocumentRoot /var/www/nameofsite
</VIrtualHost>
Do i need to add anything to the virtual host file? 
Or add something to my httpd or apache.conf?
Thanks guys

---

