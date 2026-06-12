---
title: "Virtualhost, more sites on 1 vps."
date: 2011-07-10
forum: Server Platforms
---

### Post by simolokid4 on 2011-07-10
Hi Ubuntuforums,

Since yesterday I bought a 2nd domain and figured it'd be good practise to try and host that on my vps aswell, shouldn't be much of a problem.

I was wrong! =[

I'm sure it's a minor mistake; these are the steps I've taken

currentdomain: domain i already have, and works.
newdomain: domain i newly bought.

DNS records:
newdomain.nl | TXT | "v=spf1 a mx ip4:ipadress_of_vps_here ~all"
[www.newdomain.nl]("http://www.newdomain.nl") | A | ipadress_of_vps_here
newdomain.nl | A | ipadress_of_vps_here
newdomain.nl | MX | mail.newdomain.nl | 10

/etc/hosts file contents:
127.0.0.1    localhost
178.18.94.98    currentdomain.nl
178.18.94.98    newdomain.nl
127.0.0.1    localhost    newdomain.nl

/etc/apache2/sites-available/default:   (Cut out a lot, just showing the interesting stuff)

This is to make sure the files are actually there, this subdomain works... simply pointing to the same folder :)
<VirtualHost *:80>
    DocumentRoot /var/www/the_directory
    ServerName [http://new_domain.currentdomain.nl](http://new_domain.currentdomain.nl)
    <Directory />
        AllowOverride All
    </Directory>
</VirtualHost>

And here the VirtualHost for the new domain
<VirtualHost *:80>
    DocumentRoot /var/www/the_directory
    ServerName newdomain.nl
    ServerAlias *.newdomain.nl
    <Directory />
        AllowOverride All
    </Directory>
</VirtualHost>


Then I read the following:
[http://adminspot.net/topic/2022-how-to-host-multiple-websites-on-one-server-without-any-panel/](http://adminspot.net/topic/2022-how-to-host-multiple-websites-on-one-server-without-any-panel/)

Which caused me to make the following file under /etc/apache2/sites-available/newdomain.nl

<VirtualHost *:80>
    ServerName newdomain.nl
    ServerAlias *.newdomain.nl
    DocumentRoot /var/www/the_directory
</VirtualHost>


All in all,
-  all ipadresses in the hosting service of the domain thing is pointing to the vps.
- Within the vps that servername is directed to the directory /var/www/the_directory
- That directory holds the actual website files. This is proven with the subdomain method.

Where in this mess did it go wrong? :O

Kind regards!

Simolokid

---

### Post by BkkBonanza on 2011-07-10
Why do you have this line in the first VirtualHost section above?

ServerName [http://new_domain.currentdomain.nl](http://new_domain.currentdomain.nl)

You should just have,

ServerName currentdomain.nl

If you have DNS setup as indicated then why are you adding entries in /etc/hosts - that is not needed.

Other than that it looks like settings are about right. It should be very easy to do this. You need to restart apache for changes to be loaded.

---

### Post by simolokid4 on 2011-07-10
> Why do you have this line in the first VirtualHost section above?

ServerName [http://new_domain.currentdomain.nl]("http://new_domain.currentdomain.nl/")

You should just have,

ServerName currentdomain.nlBecause the newdomain will point to the same directory.

Might be good to know what is no .nl extension in the new_domain in this case.

So its basicly [http://someacronym.currentdomain.nl](http://someacronym.currentdomain.nl) as development subdomain, which happens to be the directory the newdomain will be redirecting to aswell.

> If you have DNS setup as indicated then why are you adding entries in /etc/hosts - that is not needed.According to [http://adminspot.net/topic/2022-how-to-host-multiple-websites-on-one-server-without-any-panel/](http://adminspot.net/topic/2022-how-to-host-multiple-websites-on-one-server-without-any-panel/) its needed. This is my very first time doing this.. up untill now I've made subdomains and thats it. VirtualHost is kinda new to me.

So i should clean up /etc/hosts ?

> Other than that it looks like settings are about right. It should be  very easy to do this. You need to restart apache for changes to be  loaded.     Settings look right - yuy.
Should be very easy - it sure seemed that way when i started.
Restart apache - did that alot, but I just did it again, to no effect yet.

Going to keep trying.. 

Thanks for your answer tough :)

[edit]
Cleaned up /etc/hosts, to no avail.
[/edit

---

### Post by simolokid4 on 2011-07-10
Turns out, dns settings weren't in effect yet.

It worked when i came back from a small drink-break just now.

All working! Thanks a lot!

---

