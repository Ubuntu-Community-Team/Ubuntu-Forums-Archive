---
title: "Server showing wrong URL / Name based Virtual hosting"
date: 2008-10-26
forum: Server Platforms
---

### Post by eddie67 on 2008-10-26
I have a problem with URL's showing wrong.

I use 6.06 LTS server. 

My first domain, located in /var/www is showing OK. 
So [www.myfirstdomain.com](www.myfirstdomain.com) is all good.

My second domain, located in /var/www/seconddomain.com is showing as [www.myfirstdomain.com/myseconddomain.com](www.myfirstdomain.com/myseconddomain.com) in the browser. :confused:

I wonder, where do I look to fix this?

I am not using any DNS on my server, I use the DNS of my registrar pointing both domains to my static IP. Could that be the problem?

Any idea?

My settings look like this: 

Default: 

NameVirtualHost my.ip.adre.ss:80
<VirtualHost my.ip.adre.ss:80>
	ServerAdmin [email]mymail@gmail.com[/email]
	ServerName my.ip.adre.ss
	DocumentRoot /var/www
....
</Virtualhost>


myfisrstdomain.com:

NameVirtualHost *:80
<VirtualHost *:80>
	ServerAdmin [email]mymail@gmail.com[/email]
	ServerName myfirstdomain.com
  ServerAlias [www.myfirstdomain.com](www.myfirstdomain.com)
	DocumentRoot /var/www
...
</Virtualhost>


seconddomain.com:

NameVirtualHost *:80
<VirtualHost *:80>
	ServerAdmin [email]mymail@gmail.com[/email]
	ServerName seconddomain.com
        ServerAlias [www.seconddomain.com](www.seconddomain.com)
	DocumentRoot /var/www/seconddomain.com
....
</Virtualhost>

Thank you for your time for reading this.

Regards
Eddie.

---

### Post by volkswagner on 2008-10-26
What are the names for the files in /etc/apache2/sites-enabled?

I think best results occur if they are the actual "named" server name.

---

### Post by eddie67 on 2008-10-26
I have tried different, both myfirstdomain.com and also myfirstdomain.com.conf but there seems to be no difference.

Regards
Eddie.

---

### Post by volkswagner on 2008-10-26
Is the folder structure as you posted it, /var/www/seconddomain.com?

Just a shot in the dark here.  Try to eliminate the .com in the folder name.

You could also try adding a trailing / after the document root.  Like this.
```

seconddomain.com:

NameVirtualHost *:80
<VirtualHost *:80>
ServerAdmin mymail@gmail.com
ServerName seconddomain.com
ServerAlias www.seconddomain.com
DocumentRoot /var/www/seconddomain/
```

EDIT:  Just to be sure....Restart apache2 after making changes and clear the cache on the machine you are browsing from, before testing results.

You could also pm me the address if you want an outside test, providing you don't have a way to test it yourself.

---

### Post by eddie67 on 2008-10-26
Thank you.

But I'm afraid it did not make any difference.

Tried rebooting my server also.

Regards
Eddie

---

