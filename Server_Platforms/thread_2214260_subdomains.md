---
title: "subdomains"
date: 2014-03-31
forum: Server Platforms
---

### Post by mrteach12 on 2014-03-31
Alright so I've searched and can't seem to find an answer.  

I was wondering if I was going to use a subdomain do I have to have all the files in the www directory or can I use other directories? If so how?

example 1:
wordpress.domain.com /var/www/wordpress/
wiki.domain.com /var/www/wiki/
domain.com /var/www/

example 2:
/var/wordpress/
/var/wiki/
/var/www/

Also is there any guides I can use to install both a wiki and wordpress?    And is there a way to auto-backup my site every x days?

---

### Post by lisati on 2014-03-31
You don't have to have all your files sitting in the /var/www directory. One option is be to use virtualhosts. 

I'm calling it a night; if you have further questions, someone else might be able to step in.

---

### Post by mrteach12 on 2014-03-31
Thanks, 
I did try the apache2 thing.  It didn't work.  Do I need to change something in my 'netfirms' account to set up the subdomains or can it all be done via ubuntu?

Also I was just playing around and it seems like my links show the ipaddress rather then the domain 
e.g.  [www.domain.com]("http://www.domain.com") with a link to /files/abc.html
it shows 111.222.333.444/files/abc.html instead of domain.com/files/abc.html (the url itself does not change however in the browser url bar it stays domain.com)

I also cannot access any subdirectories by typing domain.com/files/abc.html, if gives me a page not found but using the ip instead works.  

In netfirms I'm pointing to my ip address in stealth mode.  Not sure if thats what I'm suppose to do.

---

### Post by PartisanEntity on 2014-03-31
Have you checked what you have listed under ServerName under /etc/apache2/sites-available/* ?

---

### Post by Lars Noodén on 2014-03-31
Each subdomain needs its own virtual host configuration.  They go under /etc/apache2/sites-available/ with one file per vhost.  What you are looking to do is set up name-based virtual hosts.  Remember that each new vhost needs to be enabled (a2ensite) before it can actually be used.  That only needs to be done once.  When you make changes to the vhost configurations, for the changes to take effect.  That has to be done any time you make changes.  
 
As to where they go, I'd consider a variant of example 1:

wordpress.domain.com /var/www/wordpress/
wiki.domain.com /var/www/wiki/
domain.com /var/www/domain/

---

### Post by SeijiSensei on 2014-03-31
Have you read [this part](https://help.ubuntu.com/lts/serverguide/httpd.html) of the Ubuntu Server Guide?  How about [this](http://httpd.apache.org/docs/2.2/vhosts/) and [this](http://httpd.apache.org/docs/2.2/vhosts/name-based.html) from the Apache documentation?

---

### Post by mrteach12 on 2014-03-31
Yes I have done those things (enabled using a2ensite and have reloaded).  Perhaps my vhost is wrong
this is what I have right now for the wordpress one (I have activated it).  I get forbidden when I try it. wordpress.domain.com.

> <VirtualHost *:80>
ServerName wordpress.domain.com
ServerAlias wordpress.domain.com
DocumentRoot /var/wordpress
</VirtualHost>
<Directory /var/wordpress/>
                Options -Indexes FollowSymLinks MultiViews
                AllowOverride All
                Order allow,deny
                allow from all
</Directory>


My Default is this

> <VirtualHost *:80>
        ServerAdmin webmaster@localhost

        DocumentRoot /var/www
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>

        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
        <Directory "/usr/lib/cgi-bin">
                AllowOverride None
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>

        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
        <Directory "/usr/lib/cgi-bin">
                AllowOverride None
                Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
                Order allow,deny
                Allow from all
        </Directory>

        ErrorLog ${APACHE_LOG_DIR}/error.log

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn

        CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>

---

### Post by mrteach12 on 2014-03-31
I did try changing the default to the wordpress directory and it worked ([www.domain.com](www.domain.com)) went to the wordpress directory.  I changed it back.  

I'm thinking it might be something with my domain...  This was my first domain purchase, but I am assuming all I need to do from the domain purchase site is point it to the ip of my host?

I'm wondering why the links show up as [ip]/images/hello.jpg instead of [www.domain.com/images/hello.jpg](www.domain.com/images/hello.jpg)

---

### Post by mrteach12 on 2014-03-31
Seems like default is handling all the connections if I try asfasd.domain.com it uses the default and not my wordpress [site-avaliable] (vhost)

---

### Post by brent1975 on 2014-03-31
[COLOR=#282828][FONT=helvetica]Hello, Bellow is my notes that I have on my forums when I need to create sub-domains Feel free to take a look on your own. [Click Here]("http://forums.kc-linux.com/")     

Hope this helps!!!

sub-domains is a good way to organize your website.  example.com is what we will call the parent domain. You could have many different parts to  your website. For example you could have forums, books, music, really anything. so instead of having all your components to your website lay in the same directory /var/www  you could go a step further and organize it. Here is an example of how you could structure /var/www using sub-domains[/FONT][/COLOR]
[COLOR=#282828][FONT=helvetica] [/FONT][/COLOR]
[COLOR=#282828][FONT=helvetica]/var/www/example.com   { Main domain }[/FONT][/COLOR]
[COLOR=#282828][FONT=helvetica]/var/www/forums              { forums }[/FONT][/COLOR]
[COLOR=#282828][FONT=helvetica]/var/www/music                {if you have a music site or streaming}[/FONT][/COLOR]
[COLOR=#282828][FONT=helvetica]/var/www/books                { digital books site}[/FONT][/COLOR]
[COLOR=#282828][FONT=helvetica] [/FONT][/COLOR]
[COLOR=#282828][FONT=helvetica] [/FONT][/COLOR]
[COLOR=#282828][FONT=helvetica] [/FONT][/COLOR]
[COLOR=#282828][FONT=helvetica]By using this type of structure to set up sub-domains all your website components eg: forums, music, books wont have to all be in the root directory of the website. Do you like [www.example.com/forums?](www.example.com/forums?) or would you rather see forums.example.com? [/FONT][/COLOR]
[COLOR=#282828][FONT=helvetica] [/FONT][/COLOR]
[COLOR=#282828][FONT=helvetica]Here is how we accomplish this.[/FONT][/COLOR]
[COLOR=#282828][FONT=helvetica] [/FONT][/COLOR]
[COLOR=#282828][FONT=helvetica][COLOR=#000000] We need to navigate to[/COLOR][/FONT][/COLOR]
cd [COLOR=#666600]/[/COLOR]etc[COLOR=#666600]/[/COLOR]apache2[COLOR=#666600]/[/COLOR]sites[COLOR=#666600]-[/COLOR]available[COLOR=#666600]/[/COLOR]
 [COLOR=#282828][FONT=helvetica] [/FONT][/COLOR]
[COLOR=#282828][FONT=helvetica] [/FONT][/COLOR]
[COLOR=#282828][FONT=helvetica]Now we are going to create our sub-domain file.[/FONT][/COLOR]
sudo nano forums[COLOR=#666600].[/COLOR]example[COLOR=#666600].[/COLOR]com
 [COLOR=#282828][FONT=helvetica] [/FONT][/COLOR]
[COLOR=#282828][FONT=helvetica] [/FONT][/COLOR]
[COLOR=#282828][FONT=helvetica] [/FONT][/COLOR]
[COLOR=#282828][FONT=helvetica]We will use a virtual host here is what it will look like.[/FONT][/COLOR]
[COLOR=#000088]<VirtualHost[/COLOR] *:80[COLOR=#000088]>[/COLOR]
ServerName forums.example.com
ServerAlias [www.forums.example.com](www.forums.example.com)
DocumentRoot /var/www/forums/
[COLOR=#000088]</VirtualHost>[/COLOR]
[COLOR=#000088]<Directory[/COLOR] [COLOR=#666600]/[/COLOR][COLOR=#660066]var[/COLOR][COLOR=#666600]/[/COLOR][COLOR=#660066]www[/COLOR][COLOR=#666600]/[/COLOR][COLOR=#660066]forums[/COLOR][COLOR=#000088]/>[/COLOR]
                Options -Indexes FollowSymLinks MultiViews
                AllowOverride All
                Order allow,deny
                allow from all
[COLOR=#000088]</Directory>[/COLOR]
 [COLOR=#282828][FONT=helvetica] [/FONT][/COLOR]
[COLOR=#282828][FONT=helvetica] [/FONT][/COLOR]
[COLOR=#282828][FONT=helvetica] [/FONT][/COLOR]
[COLOR=#282828][FONT=helvetica]Next we will need to enable the site with apache2.[/FONT][/COLOR]
sudo a2ensite forums[COLOR=#666600].[/COLOR]example[COLOR=#666600].[/COLOR]com
 [COLOR=#282828][FONT=helvetica] [/FONT][/COLOR]

[COLOR=#282828][FONT=helvetica]Now we need to reload apache for the changes to take place.[/FONT][/COLOR]
sudo [COLOR=#666600]/[/COLOR]etc[COLOR=#666600]/[/COLOR]init[COLOR=#666600].[/COLOR]d[COLOR=#666600]/[/COLOR]apache2 reload
 [COLOR=#282828][FONT=helvetica] [/FONT][/COLOR]
[COLOR=#282828][FONT=helvetica]Now all you need to do is create a folder in /var/www called forums eg; /var/www/forums[/FONT][/COLOR]
[COLOR=#282828][FONT=helvetica] [/FONT][/COLOR]
[COLOR=#282828][FONT=helvetica]In order for you to be able to access the forums.example.com you will need to modify DNS and add an A record. You Can go to the registar where you got the domain and register the sub-domain and point it to your server, you could use a third party dns such as zoneedit to handle all your dns needs for your domain [/FONT][/COLOR]

---

### Post by mrteach12 on 2014-03-31
Hmm That might be my problem... I wasn't modifying any DNS but just using something called pointing... and I think that is purely for redirecting domains like if I owned apple.com and apple.net.  apple.net would redirect to apple.com
Thanks this is probably what I needed.

When I ping my site I should be getting the host IP right? (the same one I'm sshing on)

---

### Post by mrteach12 on 2014-03-31
It works!!! =)

---

### Post by brent1975 on 2014-03-31
> **mrteach12 said:**
> Hmm That might be my problem... I wasn't modifying any DNS but just using something called pointing... and I think that is purely for redirecting domains like if I owned apple.com and apple.net.  apple.net would redirect to apple.com
Thanks this is probably what I needed.

When I ping my site I should be getting the host IP right? (the same one I'm sshing on)

Correct - regardless if you ping domain.com or forums.domain.com or wordpress.domain.com you should get the same IP address assuming that you have the sites on the same server. Yes, at the registar you will need to point those sub-domains to your own DNS server(s) or a third party DNS provider. I use zoneedit.com for all my DNS needs. Which I personally think is easier. You will just login and add the domain and sub-domains and IP address that you use to SSH to server off network.  Take note once you create the DNS records it can take up to 48 - 72 hours for all top level DNS servers to replicate across the internet. I have had it take longer for my ISP DNS to update.

---

