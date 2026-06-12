---
title: "Apache VirtualHost Config Question"
date: 2010-10-13
forum: Server Platforms
---

### Post by retspoox on 2010-10-13
I hava a ubuntu server on a private network serving php scripts from the default config using sub-directories for the different programs.  The problem is I want to serve a new program from a different document root.  From my research it seems that virtual host are the way to go but the examples use different domain names for each site(document root).  I really don't think I'll be allowed to create my own domains on the network I was lucky to get a static ip.  Can I use ServerName with an ip/dir ?  Am I thinking along the right lines here?

---

### Post by ed12348 on 2010-10-13
am I right in thinking you want [http://ipaddress/folder](http://ipaddress/folder) to open files outside the current apache web root folder. If so just create a symlink in the current apache web root that points to the second location, then use the address [http://ipaddress/sysmlinkname](http://ipaddress/sysmlinkname)

---

### Post by dapperdanny77 on 2010-10-13
checkout the Alias directive
with Alias you can map directories outside the document root into your urlspace.

[http://httpd.apache.org/docs/current/mod/mod_alias.html]("http://httpd.apache.org/docs/current/mod/mod_alias.html")

---

### Post by retspoox on 2010-10-13
Thanks for the reply.  When looking at that possibility (symlinks) I was discouraged by possible security/permissions issues.  Although, this is site is not a high risk target I would like to understand the alternatives.  In my digging around I haven't been able to find anything that addresses my question about using VirtualHosts without domain names.

---

### Post by dapperdanny77 on 2010-10-13
virtual hosts are distinguished by the hostname typed into the browser

e.g.

[www.domain.com](www.domain.com)
host1.domain.com
host2.domain.com

this hostname is part of the http request.
when the request hits apache apache is comparing this hostname with the configured vhosts - if it's not found the first vhost configured is used

so - vhosts are used when you need different hosts and/or domains served by one apache server

this applies basically to name based vhosts

---

### Post by windsxs on 2010-10-13
Maby this would help you:
in /etc/apache2/sites-available there is document called default. You copy it, name it the site name you want (e.g. sub.domain.com (o anything else, but this makes it more clear to remember)).
Then, you open this file and edit:
ServerName, ServerAliases to the address you want (this case subdomain.domain.com), then DocumentRoot to the root to the actual site files or site.
To enable this site on apache2 server do command 
```
a2ensite <name of your copied and configured file> 
```
a2ensite goes like apache2 enable site :)
and thats it. you can write your chosen address in url, and you get that site you link in DocumentRoot

---

### Post by retspoox on 2010-10-14
So, will the following vhost config work?
[FONT=monospace]
[/FONT]NameVirtualHost ***10.0.1.33***

<VirtualHost *:80>
ServerName ***10.0.1.33***
    DocumentRoot ***"root/***www"
</VirtualHost>

<VirtualHost *:80>
 ServerName ***test.10.0.1.33***
    DocumentRoot ***"opt/test***"
  </VirtualHost>

---

### Post by SeijiSensei on 2010-10-15
I don't think that will work, though it's easy enough to try it out, right?

How many clients are accessing this server?  If it's just one, you can create hostname entries in /etc/hosts and use those to access the various virtual hosts.

/etc/hosts
```

myhost1     10.0.1.33     myhost2 myhost3

```

The entries after the address are aliases for the main hostname, myhost1.

Now if you define virtual hosts with "ServerName myhost1", "ServerName myhost2", etc., you should be able to use URLs like [http://myhost1/](http://myhost1/), [http://myhost2](http://myhost2), etc., to access the various virtual hosts.

If you have multiple clients, you'll need to replicate /etc/hosts on each machine.  The other option is to use a DNS server, but it doesn't sound like you have sufficient permissions to do that.  If there is a DNS server on the network, and you can convince the admin to create a couple of entries for you, that's by far the best way to go.  You'd need an "A" record for one host name mapped to 10.0.1.33, and "CNAME" records for each of the aliased virtual hosts like myhost2 above.  Then the URLs will have "fully-qualified domain names" like "myhost1.example.com", "myhost2.example.com", etc.

---

### Post by retspoox on 2010-10-19
Thanks everyone, got things working and leaned a lot in the process (per-usual).
 
Two things, I did get the two dns entries mentioned above and after a virtual host was configured my _default domain_ had to be configured as a _virtual domain_.  There is pretty good web site config tutorial at YoLinux.com that helped on that.

---

