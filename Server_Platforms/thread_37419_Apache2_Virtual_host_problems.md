---
title: "Apache2 Virtual host problems"
date: 2005-05-27
forum: Server Platforms
---

### Post by dallypost on 2005-05-27
I have a customer who's wen site is in a sub directory of my main site. Their address is [http://www,dallypost,com/pcpress](http://www,dallypost,com/pcpress). They also have a virtual domain (press-times.com) that is pointed to my server.

I added a file named press-times.com to /etc/apache2/sites-available by duplicating the default file and modifying the path in Document Root and Directories, as follows:

NameVirtualHost *
<VirtualHost *>
        ServerAdmin webmaster@localhost

        DocumentRoot /home/html/pcpress/
        <Directory />
                Options FollowSymLinks indexes Includes MultiViews ExecCGI
                AllowOverride None
        </Directory>
        <Directory /home/html/pcpress/>
                Options Indexes FollowSymLinks MultiViews Includes ExecCGI
                AllowOverride None
                Order allow,deny
                allow from all
                # This directive allows us to have apache2's default start page
                # in /apache2-default/, but still have / go to the right place
                # Commented out for Ubuntu
                #RedirectMatch ^/$ /apache2-default/
        </Directory>

I also added a symlink to etc/apache2/sites-enabled and it appears to be working correctly. When I restart the server I get the following warnings:

 * Forcing reload of web server  (Apache2)...
[Fri May 27 05:31:44 2005] [warn] NameVirtualHost *:0 has no VirtualHosts
[Fri May 27 05:31:46 2005] [warn] NameVirtualHost *:0 has no VirtualHosts                                             [ ok ]

I do not know what these mean or how to fix them. Please help.

Also, when I go to [http://www.press-times.com](http://www.press-times.com), it takes me to the document root for my web site instead of the one indicated in the virtual host file.

Thanks

Lance Earl

---

### Post by LordHunter317 on 2005-05-27
NameVirtualHost can only appear once in the entire Apache configuration.  It should occur once in 000-default and no where else.  The warning is because you have it showing up multiple times.

---

### Post by dallypost on 2005-05-27
I commented out the NameVirtualHost line and it took care of the warnings I get while restarting apache2. I still have the problem that when goint to [www.press-times-com](www.press-times-com), I am taken to the home page of [www.dallypost.com](www.dallypost.com) which is at /home/htm/ instead of /home/html/pcpress.

Can anyone out there help with this?

Lance Earl

---

### Post by LordHunter317 on 2005-05-27
Your virtualhost is lacking a ServerName directive and is as such, invalid for Name-Based virtualhosting.  Please fix that and go read the VirtualHost documenation at httpd.apache.org before proceeding any further.  If you have any questions about what you read, ask them.  

It'll give a better understanding then the short notes I've posted here before, which you're welcome to read if you can dig them up in past threads.

---

### Post by dallypost on 2005-05-28
Thanks for the good help, the problem is solved

---

### Post by Shibumi on 2005-12-16
> Your virtualhost is lacking a ServerName directive and is as such, invalid for Name-Based virtualhosting.

Could you elaborate a bit more on this.  I have the same problem with my server not resolving the host name and always going to the /var/www folder.

I have everything setup according to the above instructions.  I also read a previous post by you suggesting not to use the httpd.conf file for <virtualhost *> and yet [http://httpd.apache.org/docs/2.1/vhosts/name-based.html]("http://httpd.apache.org/docs/2.1/vhosts/name-based.html") says I should do just that.  Kinda confused as to the proper setup.

Currently I just have apache2 installed and nothing else.  I would like to get the Virtualhost solved before installing php and mysql.

Thanks for any help you may have.

---

### Post by LordHunter317 on 2005-12-17
[QUOTE=Shibumi]Could you elaborate a bit more on this.  I have the same problem with my server not resolving the host name and always going to the /var/www folder.[/quote]Sure, but the documentation is a better reference, really.

In order to do name-based virtual hosting, you need a few things:[list][*]A NameVirtualHost line for every Listen directive that will do name-based virtual hosting.  Debian and Ubuntu put them in sites-enabled/000-default (for Apache 2 anyway).  They really belong in ports.conf and I tend to move them, as they are tied to a Listen directive, not a host.[*]A VirtualHost section for every site you want to host, with a ServerName directive.  The interface of the VirtualHost must match the NameVirtualHost directive.  The first VirtualHost listed for any interface is the *default* virtual host, which is where requests go when Apache can't figure out where to send them.[*]Working DNS listing all of the hostnames in question.  A /etc/hosts file is a sufficent subtitute for testing or internal development.[/list]

Anyway, the way it works is when you connect to a website, your webbrowser sends a directive called a Host directive, that looks something like this:```
Host: www.ubuntuforums.org
```  Under name-based virtual hosting, Apache looks at that line and uses that to determine what site to serve.

The two directives it uses to do this are ServerName and ServerAlias.  ServerName should be the DNS A RR (i.e., the primary name of the site) and ServerAlias should be any CNAMEs used to access the site.

Without those directives, Apache cannot match the Host part of the request, and won't serve other sites.

> I also read a previous post by you suggesting not to use the httpd.conf file for <virtualhost *> and yet [http://httpd.apache.org/docs/2.1/vhosts/name-based.html]("http://httpd.apache.org/docs/2.1/vhosts/name-based.html") says I should do just that.  Kinda confused as to the proper setup.Debian/Ubuntu are different.  See /usr/share/doc/apache2/README.Debian (maybe Ubuntu, I forget and my desktop is down).

This is something you should do all the time when you see something odd, it very well might be on purpose.

---

### Post by Shibumi on 2005-12-18
:) This was my first clue:
> A NameVirtualHost line for every Listen directive that will do name-based virtual hosting. Debian and Ubuntu put them in sites-enabled/000-default (for Apache 2 anyway). They really belong in ports.conf and I tend to move them, as they are tied to a Listen directive, not a host.

I was confused on this and had only one listed on my default virtual host like this:

NameVirtualHost *
<VirtualHost *>
	ServerAdmin webmaster@localhost
	DocumentRoot /var/www/
        ...................

But because my ISP is blocking my port 80 I forward to a different one.  Once I set up my default file as shown below, all worked excellent.

NameVirtualHost *:80
NameVirtualHost *:443
NameVirtualHost *:2061
<VirtualHost *:80>
	ServerAdmin webmaster@localhost
	DocumentRoot /var/www/apache2-default/
        ...............................

Now I understand why you choose to place the NameVirtualHost in the ports.conf file rather than with the hosts.

Thanks for all your help

---

### Post by LordHunter317 on 2005-12-18
Yes.  You have one NameVirtualHost per *Listen* port directive, typically.  You don't have to, for example, this is legal:```
Listen *:80
NameVirtualHost 192.0.0.2:80
```Which would cause Apache to listen on all interfaces on the computer but do name-based virtual hosting on 192.0.0.2 only.  

It's perfectly legal to do name-based virtual hosting on only a select number of interfaces, and do ip-based on others.

Generally for clarity's sake however, I recommend a one-to-one mapping so there's no confusion.

Also, you can't do name-based virtual hosting on SSL (443), so you can remove that directive.

---

### Post by Shibumi on 2005-12-19
> Also, you can't do name-based virtual hosting on SSL (443), so you can remove that directive.

Which leads me to my next question...

Can I use port 443 for one site exclusive but still host other multiple sites using thier own ports as suggested above?  All these sites would share one IP address, however, and I am not sure that is legal with SSL.

---

### Post by LordHunter317 on 2005-12-19
Yes, you can, but it's bad form. 
Consider what happens when you host both of these sites on port 80:[list][*][www.example1.com](www.example1.com)[*][www.example2.com](www.example2.com)[/list]Now, on the same IP, you host only www.example1.com's SSL site.  If I type into my browser: [https://www.example2.com](https://www.example2.com), I'll get example1.com's SSL.  That's undesirable.

There's one situation where this can be made to work, and that's wildcard SSL certs.  But you won't get one for a TLD, so it'd only work for situations of the form:[list][*]one.example.com[*]two.example.com[/list]

---

### Post by rapha on 2006-01-05
[http://httpd.apache.org/docs/2.0/vhosts/examples.html#port](http://httpd.apache.org/docs/2.0/vhosts/examples.html#port)

---

