---
title: "Apache 2 display welcome page instead of virtual host's page"
date: 2014-08-02
forum: Server Platforms
---

### Post by Yves_Dawson on 2014-08-02
Hi,

I've setup a virtual host for a website and apache always display the "Apache 2 welcome page".

I verified my config again and again and can't find where i'm wrong.

Here's the virtual host config file:

DocumentRoot /var/www/domain.com
ServerName domain.com
<Directory "/var/www/domain.com">
allow from all
Options +Indexes
</Directory>
ServerAlias [www.domain.com]("http://www.domain.com")

I tried configuring the host to respond to any IP or the server's specific IP and got the same result.

I'm out of answers right now and need some help from "experts" ;)

---

### Post by cj13579 on 2014-08-03
I assume that your config is in a file called *domain.com* in /etc/apache2/sites-available. Have you enabled this site?

```
sudo a2ensite domain.com
```

Once you have done that you will need to reload your apache configuration:

```
sudo service apache2 reload
```

---

### Post by Yves_Dawson on 2014-08-03
The config file is at its place and the site is enabled.

Still not working

---

### Post by cj13579 on 2014-08-03
Can you post the whole of the config file? I don't want to comment on the obvious missing <VirtualHost> tags until we have seen the full file.

---

### Post by Yves_Dawson on 2014-08-03
Here's the full file:
> [COLOR=#000000]<VirtualHost 192.168.x.xxx:80>
[/COLOR]DocumentRoot /var/www/domain.com
ServerName domain.com
<Directory "/var/www/domain.com">
allow from all
Options +Indexes
</Directory>
ServerAlias [www.domain.com](www.domain.com)
[COLOR=#000000]</VirtualHost>[/COLOR]

The VirtualHost tag was the only thing I didn't posted before but it is there!

---

### Post by Yves_Dawson on 2014-08-03
Just found the solution:

As stupid as it may seems, it was just a folder's rights issue.

Now that my www folder have the good rights, the pages are served as supposed too.

But now I have another issue:

I created a second virtual host but when i try to access it, apache serve the file (index.html) from the first host.

I remember having read something about this on the net but I forgot what is causing that, any idea?

---

### Post by brent1975 on 2014-08-05
Make sure that your second virtual host is pointing to a different directory. website1 /var/www/site1  Website2 /var/www/site2. Do you see the second domain site in the enabled-sites? 
If not then you need to run the a2ensite to enable the site. Then of course you need to restart the apache server. Post your virtual host file for the second site if these options have been performed and not working.

---

### Post by Yves_Dawson on 2014-08-06
Thanks for your reply Brent,

Everything works fine now.  But now I'm really realizing at which point Windows and Linux environments are different!  On a windows server (which I was used to have) we don't need to restart (or reload) the web server to enable a new site. So that action never crossed my mind after I created the new site.

Now I will keep in mind to reload apache after every changes that I make if something's not working as expected!

---

