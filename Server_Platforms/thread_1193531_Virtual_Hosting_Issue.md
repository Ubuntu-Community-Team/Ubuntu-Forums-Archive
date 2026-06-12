---
title: "Virtual Hosting Issue"
date: 2009-06-21
forum: Server Platforms
---

### Post by buee on 2009-06-21
So after many hours of wrestling with Virtual Hosting, I've managed to get one of my websites up using the virtual hosting file.  I have 2 files (domain1.com & domain2.com) in /etc/apache2/sites-available/(file names).  I also have them symbolically linked to /etc/apache2/sites-enabled/(file names).  When I have domain1.com in sites enabled, and I browse to domain1.com, I get it.  When both domain1.com and domain2.com in sites-enabled and I browse to domain1.com, I get domain2.com and cannot get to domain1.com in the browser.  What am I missing?

There is one interesting piece of information that may bear on this config.  The server is sitting behind a firewall with a private IP of 10.0.0.11.  So I don't know if that works in to the equation or not.

/etc/apache2/sites-available/domain1.com
```

#
# domain1.com
#
<VirtualHost *>
  ServerName domain1.com
  ServerAlias www.domain1.com
  DocumentRoot /var/www/domain1
  CustomLog /var/www/logs/domain1.com-access.log combined
  ErrorLog /var/www/logs/domain1.com-error.log
</VirtualHost>

```

/etc/apache2/sites-available/domain2.com
```

#
# blog.domain2.com
#
<VirtualHost *>
  ServerName blog.domain2.com
  ServerAlias www.blog.domain2.com
  DocumentRoot /var/www/domain2
  CustomLog /var/www/logs/Blog.domain2.com-access.log combined
  ErrorLog /var/www/logs/Blog.domain2.com-error.log
</VirtualHost>

```

My brain is shot at the moment.  Anyone have any insights?

---

### Post by buee on 2009-06-22
> **buee said:**
> So after many hours of wrestling with Virtual Hosting, I've managed to get one of my websites up using the virtual hosting file.  I have 2 files (domain1.com & domain2.com) in /etc/apache2/sites-available/(file names).  I also have them symbolically linked to /etc/apache2/sites-enabled/(file names).  When I have domain1.com in sites enabled, and I browse to domain1.com, I get it.  When both domain1.com and domain2.com in sites-enabled and I browse to domain1.com, I get domain2.com and cannot get to domain1.com in the browser.  What am I missing?

There is one interesting piece of information that may bear on this config.  The server is sitting behind a firewall with a private IP of 10.0.0.11.  So I don't know if that works in to the equation or not.

/etc/apache2/sites-available/domain1.com
```

#
# domain1.com
#
<VirtualHost *>
  ServerName domain1.com
  ServerAlias www.domain1.com
  DocumentRoot /var/www/domain1
  CustomLog /var/www/logs/domain1.com-access.log combined
  ErrorLog /var/www/logs/domain1.com-error.log
</VirtualHost>

```

/etc/apache2/sites-available/domain2.com
```

#
# blog.domain2.com
#
<VirtualHost *>
  ServerName blog.domain2.com
  ServerAlias www.blog.domain2.com
  DocumentRoot /var/www/domain2
  CustomLog /var/www/logs/Blog.domain2.com-access.log combined
  ErrorLog /var/www/logs/Blog.domain2.com-error.log
</VirtualHost>

```

My brain is shot at the moment.  Anyone have any insights?

Is it possible that I need to forward DNS to this box.  Not sure how Virtual Hosting handles requests.

---

### Post by Iowan on 2009-06-22
[Here]("http://ubuntu-tutorials.com/2008/01/09/setting-up-name-based-virtual-hosting/") is an interesting-looking tutorial (which I've only scanned briefly) that looks like it should touch on your topic.

---

### Post by mbeach on 2009-06-22
how are you browsing to the sites? Are you typing the url, or using the ip? The only other thing since it appears you are replacing content for the purposes of posting is to keep in mind that the sites are loaded in alphabetical order - I only mention that in case you have some other directives in there. Are you restarting the service after making changes?
sudo /etc/init.d/apache2 reload

You may also want to check your access log to see what is being requested as that may reveal why you are not getting the site you think you should be.

---

### Post by buee on 2009-06-22
> **mbeach said:**
> how are you browsing to the sites? Are you typing the url, or using the ip? The only other thing since it appears you are replacing content for the purposes of posting is to keep in mind that the sites are loaded in alphabetical order - I only mention that in case you have some other directives in there. Are you restarting the service after making changes?
sudo /etc/init.d/apache2 reload

You may also want to check your access log to see what is being requested as that may reveal why you are not getting the site you think you should be.


I am browsing via the domain name.  Yes, I have been reloading apache after each change.  

My access logs for domain2 (the one that doesn't pull up the actual domain2 site, it pulls domain1):
```
127.0.0.1 - - [21/Jun/2009:17:10:27 -0500] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.6 with Suhosin-Patch (internal dummy connection)"
```


My access logs for domain1 (the one that comes up no matter what site I try to go to:
```

192.168.10.1 - - [22/Jun/2009:20:50:45 -0500] "GET / HTTP/1.1" 200 4568 "-" "Mozilla/5.0 (Windows; U; Windows NT 6.0; en-US; rv:1.9.0.11) Gecko/2009060215 Firefox/3.0.11 (.NET CLR 3.5.30729)"
192.168.10.1 - - [22/Jun/2009:20:50:45 -0500] "GET /Images/baymont_janesville-sm.jpg HTTP/1.1" 200 12661 "http://domain1.com/" "Mozilla/5.0 (Windows; U; Windows NT 6.0; en-US; rv:1.9.0.11) Gecko/2009060215 Firefox/3.0.11 (.NET CLR 3.5.30729)"
192.168.10.1 - - [22/Jun/2009:20:50:45 -0500] "GET /Images/hi_rockford-sm.jpg HTTP/1.1" 200 11251 "http://domain1.com/" "Mozilla/5.0 (Windows; U; Windows NT 6.0; en-US; rv:1.9.0.11) Gecko/2009060215 Firefox/3.0.11 (.NET CLR 3.5.30729)"
192.168.10.1 - - [22/Jun/2009:20:50:45 -0500] "GET /Images/baymont_rockford-sm.jpg HTTP/1.1" 200 13057 "http://domain1.com/" "Mozilla/5.0 (Windows; U; Windows NT 6.0; en-US; rv:1.9.0.11) Gecko/2009060215 Firefox/3.0.11 (.NET CLR 3.5.30729)"
192.168.10.1 - - [22/Jun/2009:20:50:45 -0500] "GET /Images/hi_lovespark-sm.jpg HTTP/1.1" 200 11971 "http://domain1.com/" "Mozilla/5.0 (Windows; U; Windows NT 6.0; en-US; rv:1.9.0.11) Gecko/2009060215 Firefox/3.0.11 (.NET CLR 3.5.30729)"
192.168.10.1 - - [22/Jun/2009:20:50:45 -0500] "GET /Images/staybridge-sm.jpg HTTP/1.1" 200 19520 "http://domain1.com/" "Mozilla/5.0 (Windows; U; Windows NT 6.0; en-US; rv:1.9.0.11) Gecko/2009060215 Firefox/3.0.11 (.NET CLR 3.5.30729)"
192.168.10.1 - - [22/Jun/2009:20:50:45 -0500] "GET /favicon.ico HTTP/1.1" 404 334 "-" "Mozilla/5.0 (Windows; U; Windows NT 6.0; en-US; rv:1.9.0.11) Gecko/2009060215 Firefox/3.0.11 (.NET CLR 3.5.30729)"
192.168.10.1 - - [22/Jun/2009:20:50:48 -0500] "GET /favicon.ico HTTP/1.1" 404 334 "-" "Mozilla/5.0 (Windows; U; Windows NT 6.0; en-US; rv:1.9.0.11) Gecko/2009060215 Firefox/3.0.11 (.NET CLR 3.5.30729)"
127.0.0.1 - - [22/Jun/2009:20:51:06 -0500] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.6 with Suhosin-Patch (internal dummy connection)"
192.168.10.1 - - [22/Jun/2009:20:52:35 -0500] "GET / HTTP/1.1" 200 4568 "-" "RPT-HTTPClient/0.3-3E"
192.168.10.1 - - [22/Jun/2009:20:53:08 -0500] "GET / HTTP/1.1" 200 4568 "-" "RPT-HTTPClient/0.3-3E"
192.168.10.1 - - [22/Jun/2009:20:54:35 -0500] "GET / HTTP/1.1" 200 4568 "-" "RPT-HTTPClient/0.3-3E"

```

It all looks like it belongs.  It doesn't appear to be kicking to the second domain at all.  The requests all come in on port 80 only right?  It doesn't mess with DNS at all?

---

### Post by buee on 2009-06-22
> **Iowan said:**
> [Here]("http://ubuntu-tutorials.com/2008/01/09/setting-up-name-based-virtual-hosting/") is an interesting-looking tutorial (which I've only scanned briefly) that looks like it should touch on your topic.

That's actually the tutorial I used to set it up on a virtual machine, which worked.  Then I used a different tutorial the first time, then I used this one the second time.  Thanks anyway.

---

### Post by samosamo on 2009-06-22
Why do it manually?  Use Virtualmin.

---

### Post by buee on 2009-06-22
> **samosamo said:**
> Why do it manually?  Use Virtualmin.

I would really like to avoid Webmin at all costs.

---

### Post by mbeach on 2009-06-23
It looks like you may be going to domain1.com, forgetting about the www. This is ok as your servername handles that, but you may want to add something like *.domain.com to your serveralias. Out of curiosity when you are browsing to domain2.com, are you using "http://domain2.com" because as I see it, you'd be directed to whichever host file is loaded first since you are not handling domain2.com. You are handling [www.blog.domain2.com](www.blog.domain2.com) and blog.domain2.com. Again, perhaps something like 
ServerAlias [www.blog.domain2.com](www.blog.domain2.com) *.domain2.com
would be in order.

another good little tool which may help you out is 
[https://launchpad.net/rapache](https://launchpad.net/rapache)
I've played with it and it seems to work well, but most of my stuff is done remotely anyway, and just easier to edit the hosts files with editor of choice.

---

### Post by buee on 2009-06-23
> **mbeach said:**
> It looks like you may be going to domain1.com, forgetting about the www. This is ok as your servername handles that, but you may want to add something like *.domain.com to your serveralias. Out of curiosity when you are browsing to domain2.com, are you using "http://domain2.com" because as I see it, you'd be directed to whichever host file is loaded first since you are not handling domain2.com. You are handling [www.blog.domain2.com](www.blog.domain2.com) and blog.domain2.com. Again, perhaps something like 
ServerAlias [www.blog.domain2.com](www.blog.domain2.com) *.domain2.com
would be in order.

another good little tool which may help you out is 
[https://launchpad.net/rapache](https://launchpad.net/rapache)
I've played with it and it seems to work well, but most of my stuff is done remotely anyway, and just easier to edit the hosts files with editor of choice.

I will try that and reply with results.

One thing that concerns me is that you've mentioned hosts files and in all the tutorials I've looked at, they mention host files.  On the VM using localhost, it was successful.  I wouldn't have to change anything in the host file to get these to be externally accessible, would I?  That would make absolutely no sense to me at all.

---

### Post by buee on 2009-06-23
> **mbeach said:**
> It looks like you may be going to domain1.com, forgetting about the www. This is ok as your servername handles that, but you may want to add something like *.domain.com to your serveralias. Out of curiosity when you are browsing to domain2.com, are you using "http://domain2.com" because as I see it, you'd be directed to whichever host file is loaded first since you are not handling domain2.com. You are handling [www.blog.domain2.com](www.blog.domain2.com) and blog.domain2.com. Again, perhaps something like 
ServerAlias [www.blog.domain2.com](www.blog.domain2.com) *.domain2.com
would be in order.

another good little tool which may help you out is 
[https://launchpad.net/rapache](https://launchpad.net/rapache)
I've played with it and it seems to work well, but most of my stuff is done remotely anyway, and just easier to edit the hosts files with editor of choice.

Unfortunately, this didn't work.  I added the *.domain2.com after the [www.blog.domain2.com](www.blog.domain2.com) in the vhost config under ServerAlias and reloaded apache, still ends up going to domain1.com.

In my DNS, I have an A record for domain1.com point to the same IP address as the A record for domain2.com.  Just mentioning it in case I did something stupid.

---

### Post by buee on 2009-06-24
I just took another look at the logs and found that when I get the "URL / could not be found on this server" error, every request seems to tack /blog to the end of the path.

---

### Post by R.Bucky on 2009-06-24
I host 3 domains with my server at home and wrote a tutorial on the install with all the relevant info here [http://buckycomputing.net/blog/hosting-2-domains-with-1-server/]("http://buckycomputing.net/blog/hosting-2-domains-with-1-server/")

During my configuration, I forgot to configure my /etc/hosts.

---

### Post by buee on 2009-06-24
> **R.Bucky said:**
> I host 3 domains with my server at home and wrote a tutorial on the install with all the relevant info here [http://buckycomputing.net/blog/hosting-2-domains-with-1-server/]("http://buckycomputing.net/blog/hosting-2-domains-with-1-server/")

During my configuration, I forgot to configure my /etc/hosts.

Pardon my confusion, but wouldn't editing the hosts file just work for my machine?  I'm trying to get them externally accessible and don't see the relevance of the host file.

---

### Post by R.Bucky on 2009-06-24
You need to tell your machine how to route incoming requests with your specific internal ip address. A box with DNS may be different. Give it a quick shot.

---

### Post by buee on 2009-06-24
> **R.Bucky said:**
> You need to tell your machine how to route incoming requests with your specific internal ip address. A box with DNS may be different. Give it a quick shot.

I did not do the a2ensite, but from what I understand that's does the same as create a symbolic link to sites-enabled.  

I do not have any internal DNS, I'm using everydns.net for my A records.

---

### Post by buee on 2009-06-24
> **R.Bucky said:**
> I host 3 domains with my server at home and wrote a tutorial on the install with all the relevant info here [http://buckycomputing.net/blog/hosting-2-domains-with-1-server/]("http://buckycomputing.net/blog/hosting-2-domains-with-1-server/")

During my configuration, I forgot to configure my /etc/hosts.

I checked over your tutorial and will give a go sometime in the very near future.  For the most part, it looks the same as what I've already done.  I do have one question though.  When you edited the apache2.conf file to include the ServerName IP Address, I am putting the internal address even though it will be externally accessible, correct?

---

### Post by buee on 2009-06-24
> **buee said:**
> I checked over your tutorial and will give a go sometime in the very near future.  For the most part, it looks the same as what I've already done.  I do have one question though.  When you edited the apache2.conf file to include the ServerName IP Address, I am putting the internal address even though it will be externally accessible, correct?

Yep, that worked.  Now they route properly and each domain pulls up the correct web site.  However, Wordpress is not displaying properly at all.  Probably not an issue for this forum but perhaps someone knows something.  It looks like there's no PHP possibly going on there.  It just looks like a really crappy website.

---

### Post by R.Bucky on 2009-06-24
I assume that your browser is only displaying the text of your site, without any of the CSS elements? If so, do you have a DNS server configured and installed?

Since WP requires use of the domain name when viewing, rather than the internal ip, it only displays the elements on the page from your database (e.g. text).

---

### Post by buee on 2009-06-24
> **R.Bucky said:**
> I assume that your browser is only displaying the text of your site, without any of the CSS elements? If so, do you have a DNS server configured and installed?

Since WP requires use of the domain name when viewing, rather than the internal ip, it only displays the elements on the page from your database (e.g. text).

No DNS server.  I have actually resolved this by removing Wordpress and reinstalling it.

---

