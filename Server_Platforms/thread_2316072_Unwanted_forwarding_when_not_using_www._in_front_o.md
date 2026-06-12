---
title: "Unwanted forwarding when not using www. in front of site-link."
date: 2016-03-04
forum: Server Platforms
---

### Post by jonathan_3 on 2016-03-04
[FONT=arial narrow]Hey, I try to set up my ubuntu 14.04 server. [/FONT]

[FONT=arial narrow]For a while I had my second domain forwarding to my first one, but now I want to separate them. Which works great as long as I add the www. to the site. As long as I only write example002.com (without the www) it forwards to a total different link expample001.com. Both located at my server. [/FONT]

[FONT=arial narrow]I checked my settings at the domain shop and each of the DNS forwarding settings only lead to my IP address. There are no other settings in my www-forwarding settings either. [/FONT]

[FONT=arial narrow]I made a .conf file for each of the domains with each their different information leading to each their folder at the server. [/FONT]
[FONT=arial narrow]Each .conf file looks pretty much like this except with different pathways of course:[/FONT]
[FONT=arial narrow]
<VirtualHost *:80
[/FONT][FONT=arial narrow]ServerAdmin [email]webmaster@example.com[/email][/FONT]
[FONT=arial narrow]     ServerName example.com[/FONT]
[FONT=arial narrow]     ServerAlias [www.example.com](www.example.com)[/FONT]
[FONT=arial narrow]     DocumentRoot /var/www/html/example.com/public_html/[/FONT]
[FONT=arial narrow]     ErrorLog /var/www/html/example.com/logs/error.log [/FONT]
[FONT=arial narrow]     CustomLog /var/www/html/example.com/logs/access.log combined[/FONT]
[FONT=arial narrow]     <Directory /path/to/public/website/>[/FONT]
[FONT=arial narrow]        Require all granted[/FONT]
[FONT=arial narrow]     </Directory>[/FONT]
[FONT=arial narrow]</VirtualHost>
[/FONT]
[FONT=arial narrow]I should probably also ask about th[/FONT][COLOR=#333333][FONT=arial narrow]e "<Directory" line which path does not contain any files at my server. But which looks something like "/home/web/website" I only have my website files located in the DocumentRoot folder. Why are there two paths to public website in this file?[/FONT]

[FONT=arial narrow]Any help to solve any of this is very much appreciated! 

Thanks![/FONT][/COLOR]

---

