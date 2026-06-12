---
title: "Apache2 with wordpress"
date: 2017-05-01
forum: Server Platforms
---

### Post by rgraze on 2017-05-01
My issue is I created a virtual host and created a simple web site. I have a domain from godaddy, rgraze.com. I setup the DNS to point to my Ubuntu 16.04 server. I tested it and got my simple page that stated success it works. I then installed wordpress. Got that up and running locally. I have been using digital ocean guides for most of this. The issue is the wordpress page open fine on my LAN, but remotely it does not. It does seem to hit my server I get an https cert error but it then I believe redirects to my local LAN ip for the site which does not work outside my network. Im sure when I was trouble shooting an issue I must have put my LAN ip in some file but cant remember where.

---

### Post by SeijiSensei on 2017-05-02
Did you create a file in /etc/apache2/sites-available for the Wordpress virtual host?  If so, please post it here inside [noparse]```

```[/noparse] tags.

Did you use one name for the site while testing and a different name while in production?  If so, you'll need to [configure WordPress to use the new name]("https://mediatemple.net/community/products/dv/204405334/how-can-i-change-the-domain-name-for-my-wordpress-site") if it does not do so now.  Changing the name only in Apache will not work because of the redirections WP uses.

---

### Post by rgraze on 2017-05-02
I created an rgraze.com.conf that then directs to my var/www/html which is where wordpress is located.
<VirtualHost *:80>
	ServerAdmin [email]rgraze@yahoo.com[/email]
        ServerName rgraze.com
        ServerAlias [www.rgraze.com](www.rgraze.com)
	DocumentRoot /var/www/html/
	#LogLevel info ssl:warn
	ErrorLog ${APACHE_LOG_DIR}/error.log
	CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>



I also under wordpress settings have rgraze.com althoug another issue is i rebooted the server and now can not access the wordpress dashboard wp_admin etc
Being very new to this I dont know what post inside code code tags mean. sorry about that

---

### Post by rgraze on 2017-05-02
So my [https://rgraze.com](https://rgraze.com) seems to be working so I set up a redirect in my rgraze.com.conf 

<VirtualHost *:80>
	
        


        Redirect permanent "/" "https://rgraze.com/"


        
</VirtualHost>

Yet when I go to a remote PC I put in rgraze.com it still seems to be looking for my local server IP

---

### Post by slickymaster on 2017-05-02
*Thread moved to **Server Platforms**.*

---

### Post by SeijiSensei on 2017-05-02
> **rgraze said:**
> So my [https://rgraze.com](https://rgraze.com) seems to be working so I set up a redirect in my rgraze.com.conf 

You need a server name here
```

<VirtualHost *:80>
	ServerName www.rgraze.com
        ServerAlias rgraze.com
        Redirect permanent "/" "https://rgraze.com/"   
</VirtualHost>

```

Apache keys on the value of the ServerName and ServerAlias directives to determine which virtual host configuration to use.

Nice planters by the way.

---

### Post by rgraze on 2017-05-03
Thanks for the help its up and running. Part of the issue I had also is I had to clear my browser cache. Also oddly rgraze.com wont open on my chrome but if I put in [https://rgraze.com](https://rgraze.com) that will open even though when it fails rgraze.com it states it can not connect to [https://rgraze.com](https://rgraze.com).

---

