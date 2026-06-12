---
title: "Starting a website"
date: 2010-02-24
forum: Server Platforms
---

### Post by espressobeanie on 2010-02-24
Hi all,

I'm trying to start a website and fileserver on a rig of mine. I'm going to use Webmin to access my files and such, but if I want to do a website as well, I need help. I don't know how website processing works. Can I get it to pull up an html file when someone accesses a specifc port, or is there some way for a DynDns to redirect a "www.something.com" address to a file on my computer? I'd love to know. I'm good at HTML and CSS.

Thanks

---

### Post by JackRock on 2010-02-24
You need to have some sort of DNS registry to point the domain name ([www.something.com](www.something.com)) to your website's IP address.  Unless you change anything on your server AND the DNS entry, the default port will be 80 for HTTP traffic.

You'll need to set up LAME on your server to host any sites.  You configure them to use a specific directory, and that becomes your website's root.  Put in an "index.html" (or .htm) file in this directory, and that will be the default page any visitors pull up.  Any directory (or subdirectory) that does not have an Index.* page will simply show a listing of files in that folder when a user goes there...unless they click on a specific file within that directory.

It's advised to have an index file in every sub/directory nested within your site's root directory.

I'm not certain that DynDNS will do domain name registration and forwarding (which is what you need if you're hosting the files on your own machine), but a cursory glance shows me that it probably does.

---

### Post by NullHead on 2010-02-24
DynDNS does do free domain registration. For example, my website, [http://probably.doesntexist.com](http://probably.doesntexist.com), uses the *doesntexist.com domain. There are many to choose from. 

You need to register with a used email address, because every month, they'll email you asking you to renew your account. You'll need to have port 80 open on your router/firewall, and you'll need apache2 installed (sudo apt-get install apache). 

The default web root is in /var/www/, and as JackRock said, make sure to have an index.html file in every folder you make inside /var/www, otherwise visitors will be able to browse through all the files in /var/www without restriction.

---

### Post by bolla3 on 2010-02-24
First you need a server. as I understand from your post you already have that. 
As said before, dyndns provides free domain registration. all you need to do is choose a domain and write down your ip. Then you put the html/CSS/whatever in your /var/www folder.

---

### Post by Kiwi76 on 2010-02-27
> **JackRock said:**
> Any directory (or subdirectory) that does not have an Index.* page will simply show a listing of files in that folder when a user goes there...unless they click on a specific file within that directory.

It's advised to have an index file in every sub/directory nested within your site's root directory.Thanks for this advice! I have made this change to my server (two directories had no index.* file).

---

### Post by hessiess on 2010-02-27
If you are going to buy a domain name, you would be better off just using a shared hosting provider. Running your own server is going to cost a lot more in power and would also have very poor performance, due to the lousy upstream bandwidth provided by most home connections.

> 
The default web root is in /var/www/, and as JackRock said, make sure to have an index.html file in every folder you make inside /var/www, otherwise visitors will be able to browse through all the files in /var/www without restriction.


Or just disable directory listing, find a line like this in the Apache config file:

```

Options Indexes FollowSymLinks

```

Then take out the ``Indexes'' part.

---

### Post by NullHead on 2010-02-27
> **hessiess said:**
> If you are going to buy a domain name, you would be better off just using a shared hosting provider. Running your own server is going to cost a lot more in power and would also have very poor performance, due to the lousy upstream bandwidth provided by most home connections.



Or just disable directory listing, find a line like this in the Apache config file:

```

Options Indexes FollowSymLinks

```

Then take out the ``Indexes'' part.

I totally agree with the shared hosting idea. You might also consider hosting such as [http://linode.com](http://linode.com) for a VPS host (Virtual Private Server). These servers give you complete access to a machine running in an XEN virtual host, and you're free to change the OS, alter your apache config,what ever you would want to do with a regular home-grown server; just with loads more bandwidth and much better uptime. I personally have a home file server and a linode 360. The Linode 360 has way more than enough power to host a low traffic to moderate traffic website with out any problems at all. 

Yeah, removing Indexes will work too, but it's a whole lot easier to just ```
touch /var/www/folder/index.html
```

---

### Post by espressobeanie on 2010-02-27
It's cool. I don't want to do any hosting stuff, despite it being performance-wise better. I just graduated college and I don't have the dough to pay the monthly fee, but I have enough hardware and a line to make a basic sever for me. I just need something simple for me to upload and download files remotely, but for me only. It won't be running 24/7 either.

---

### Post by NullHead on 2010-02-27
You could always use sftp for file transfers. There's [winscp](http://winscp.net/eng/index.php), [filezilla](http://filezilla-project.org/) and if you're running linux on the remote computer, you could use rsync or scp; both linux commands.

---

### Post by Vegan on 2010-02-27
to fast way to get a web server up is with task select

```
sudo tasksel lamp
```

---

