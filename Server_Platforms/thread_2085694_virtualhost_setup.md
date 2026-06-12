---
title: "virtualhost setup"
date: 2012-11-18
forum: Server Platforms
---

### Post by spillage2 on 2012-11-18
Thought I would see if anyone can help with this apache2 set up running on ubuntu server 12.04.

I have set up my virtualhost files as:

<virtualHost *:80>

ServerAdmin [email]webmaster@mysite.com[/email]
ServerName  [www.mysite.com](www.mysite.com)
ServerAlias  mysite.com

DocumentRoot /var/www/myfiles

</VirtualHost>

I have tried to reverse the Name and Alias but cannot connect using www. only on mysite.com.

Just get server not found when using the full [www.mysite.com](www.mysite.com).

I have spent hours checking an searching but have hit a brick wall and any help would be appreciated.

Cheers,

Spill.

---

### Post by Doug S on 2012-11-18
How are you doing internal DNS for your network? ( /etc/hosts file or dnsmasq or bind9? ). You need some way to resolve [www.mysite.com](www.mysite.com) to the desired IP address, similar to how mysite.com must be resolving if it that name is working.

---

### Post by spillage2 on 2012-11-19
Hi,

No I have not setup my /host folder as I can connect externally. Just odd that external connections work only without the www.

---

### Post by kevinwincott on 2012-11-19
do you get a reply from the same IP if you ping both mysite.com and [www.mysite.com?](www.mysite.com?)

here is one of my files:

<VirtualHost *:80>
	ServerAdmin webmaster@xxxxx
	DocumentRoot /var/www/xxxxx
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


	ErrorLog /var/log/apache2/error.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn

	CustomLog /var/log/apache2/access.log combined

</VirtualHost>

---

### Post by pkadeel on 2012-11-19
> **spillage2 said:**
> Thought I would see if anyone can help with this apache2 set up running on ubuntu server 12.04.

I have set up my virtualhost files as:

<virtualHost *:80>

ServerAdmin [EMAIL="webmaster@mysite.com"]webmaster@mysite.com[/EMAIL]
ServerName  [www.mysite.com]("http://www.mysite.com")
ServerAlias  mysite.com

DocumentRoot /var/www/myfiles

</VirtualHost>

I have tried to reverse the Name and Alias but cannot connect using www. only on mysite.com.

Just get server not found when using the full [www.mysite.com]("http://www.mysite.com").

I have spent hours checking an searching but have hit a brick wall and any help would be appreciated.

Cheers,

Spill.
Do the following if you are using the site locally.
```

gksu gedit /etc/hosts

```
Add following lines to it
```

127.0.0.1           mysite.com
127.0.0.1           www.mysite.com

```
save and close the file and try to browse again.

---

### Post by spillage2 on 2012-11-19
I will ping the [www.mysite.com](www.mysite.com) address when I get home later but am wanting to access the site externally.

setting up hosts on a local machine works fine and externally is all ok as long as the www. is removed from the address.

just can understand why this would be the case.

will have another poke around later on.

spill.

---

### Post by pkadeel on 2012-11-19
> **spillage2 said:**
> I will ping the [www.mysite.com]("http://www.mysite.com") address when I get home later but am wanting to access the site externally.

setting up hosts on a local machine works fine and externally is all ok as long as the www. is removed from the address.

just can understand why this would be the case.

will have another poke around later on.

spill.
Externally (through internet) only mysite.com works because you would have assigned mysite.com to your IP address. For alias ([www.mysite.com](www.mysite.com)) to work you need DNS server setup. You can either setup your own DNS server for sites hosted on your webserver or if your domain name provider offers this service then use that one. In the end you will create a CNAME record for the alias in the DNS server whichever you use.

---

### Post by spillage2 on 2012-11-19
Ok thanks.

I have got my web address from dnsdynamic and checking my account show this address pointing to my router ip.

It was all working fine on my previous server setup and as far as i can tell have done everything the same as i did not set up a dns server on the first one.

---

