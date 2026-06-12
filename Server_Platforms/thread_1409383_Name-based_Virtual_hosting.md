---
title: "Name-based Virtual hosting"
date: 2010-02-17
forum: Server Platforms
---

### Post by programming.name on 2010-02-17
Hi,
I am curruntly setting up a web hosting server with ubuntu 9.10 desktop edition and the situation is as follows:

1. Ubuntu lamp server installed; both [http://127.0.0.1](http://127.0.0.1) and [http://localhost](http://localhost) work fine.
2. port-forward done and DNS resisterd.
3. got an purchased domain form a domain resistrar.

I am so confused right now becuase some info states that I need to copy and edit file(s) only in /etc/apache2/sites-available/ and others says httpd.conf or some also says apache2.conf as well as modyfing the hosts file.


 Unfortunately '2-day-googling' on virtual hosting gives me nothing at all. All I want is to create subdomain with name-based virtual host.

Please HELP! 

Thanks.

---

### Post by cdenley on 2010-02-17
In ubuntu, any vhost related configuration belongs in /etc/apache2/sites-available. You should not use httpd.conf. When you create new vhost configurations, you enable them with "sudo a2ensite name_of_my_new_site".

[http://ubuntuforums.org/showpost.php?p=8831431&postcount=2](http://ubuntuforums.org/showpost.php?p=8831431&postcount=2)

---

### Post by programming.name on 2010-02-17
Waht about hosts file? Do I need to edit it?

---

### Post by cdenley on 2010-02-17
> **programming.name said:**
> Waht about hosts file? Do I need to edit it?

Not really.

---

### Post by Mykle87 on 2010-02-17
[I think this is what you want.]("http://brucewampler.wordpress.com/2009/02/28/adding-virtual-hosts-to-ubuntu-apache/") I followed this guide and was able to host different web pages using different dynnds urls (such as mykle.dyndns.com and mykle2.dyndns.com) I had registered. I would assume this would work for your sub-domain. Good luck.

---

### Post by programming.name on 2010-02-17
I Found the answer myself. We DO need to edit etc/hosts file as well. Please see below:
127.0.0.1 mydomain.com
127.0.0.1 sub1.mydomain.com
that solved the problem. Thanks

---

### Post by Iowan on 2010-02-17
[Here]("http://httpd.apache.org/docs/2.0/vhosts/name-based.html")  is a link I've had bookmarked for awhile - hope it helps.

---

### Post by cdenley on 2010-02-17
> **programming.name said:**
> I Found the answer myself. We DO need to edit etc/hosts file as well. Please see below:
127.0.0.1 mydomain.com
127.0.0.1 sub1.mydomain.com
that solved the problem. Thanks

That will cause your server to resolve your domains to 127.0.0.1, which may be required to view your site from the server itself in certain situations depending on your network/router/DNS. However, this is NOT required for a functional web server with multiple sites. Editing your hosts file will not affect how apache serves your pages, only how your web browser (which doesn't belong on a web server anyway) connects to apache.

---

### Post by pirateghost on 2010-02-17
> **cdenley said:**
> That will cause your server to resolve your domains to 127.0.0.1, which may be required to view your site from the server itself in certain situations depending on your network/router/DNS. However, this is NOT required for a functional web server with multiple sites. Editing your hosts file will not affect how apache serves your pages, only how your web browser (which doesn't belong on a web server anyway) connects to apache.

bingo.  essentially all you did is tell your OS that when you call up mydomain.com or sub1.mydomain.com it points to localhost.

this does ZERO to create virtual name based servers

---

