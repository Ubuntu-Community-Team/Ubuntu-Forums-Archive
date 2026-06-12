---
title: "Need to use server to host many domains with one IP address"
date: 2015-05-07
forum: Server Platforms
---

### Post by rieka2 on 2015-05-07
Many years ago I managed to do this successfully, but don't have any documentation on details. I think it was back in the days of Bind 8 and Apache1, so many things have changed.

As I recall, Bind must be properly setup with all the domain names as zones before Apache can switch to the appropriate virtual server.

Documentation on this process is hard to come by, as Bind tutorials all seem to focus on other topics. 

I know Bind is very fussy about syntax, etc. so I must have done something wrong somewhere. 

Here is what I've created so far in the named.conf.local file:
```
zone "xyz.net" {
 type master;
 file "/etc/bind/zones/xyz.net.db";
 };

 zone "abc.com" {
 type master;
 file "/etc/bind/zones/abc.com.db";
 };

 zone "bcd.org" {
 type master;
 file "/etc/bind/zones/bcd.org.db";
 };

 zone "1.1.10.in-addr.arpa" {
 type master;
 file "/etc/bind/zones/rev.1.1.10.in-addr.arpa";
 };
```

I made a xyz.net.db file that looks like this:
```
 ; BIND data file for xyz.net
 ;
 $TTL 14400
 @ IN SOA ns1.xyz.net. tuv.xyz.net. (
 201505061 ; Serial
 7200 ; Refresh
 120 ; Retry
 2419200 ; Expire
 60480) ; Default TTL
 ;
 xyz.net. IN NS ns1.xyz.net.
 xyz.net. IN NS ns2.xyz.net.

 xyz.net. IN MX 10 mail.xyz.net.
 xyz.net. IN A 10.1.1.33

 ns1 IN A 10.1.1.33
 ns2 IN A 10.1.1.33
 www IN CNAME xyz.net.
 mail IN A 10.1.1.33
 ftp IN CNAME xyz.net.
 xyz.net. IN TXT "V=spf1 ip4:10.1.1.33 a mx ~all"
 mail IN TXT "V=spf1 a -all"
```

And the file bcd.org.db that looks like this:
```
; BIND data file for bcd.org
 ;
 $TTL 14400
 @ IN SOA ns1.xyz.net. tuv.xyz.net. (
 201505061 ; Serial
 7200 ; Refresh
 120 ; Retry
 2419200 ; Expire
 60480) ; Default TTL
 ;
 bcd.org. IN NS ns1.xyz.net.
 bcd.org. IN NS ns2.xyz.net.

 bcd.org. IN MX 10 mail.bcd.org.
 bcd.org. IN A 10.1.1.33

 ns1 IN A 10.1.1.33
 ns2 IN A 10.1.1.33
 www IN CNAME xyz.net.
 mail IN A 10.1.1.33
 ftp IN CNAME bcd.org.
 xyz.net. IN TXT "V=spf1 ip4:10.1.1.33 a mx ~all"
 mail IN TXT "V=spf1 a -all"
```

Is there some other file someplace else that needs to be modified?

Is there some switch in Apache that must be set?

---

### Post by Lars Noodén on 2015-05-07
> **rieka2 said:**
> 
Is there some other file someplace else that needs to be modified?

Is there some switch in Apache that must be set?

Are you managing your own DNS?  If not, then all that matters is that the CNAME or A names resolve to the IP number of the server.  

Then on Apache2's side of things set up a [name-based virtual host](http://httpd.apache.org/docs/2.4/vhosts/name-based.html).

---

### Post by rieka2 on 2015-05-07
I'm using a DNS hosting provider and the only reason to have Bind on my server is so the server knows where to internally route the information.

Apache is already set up as a name based virtual host.

---

### Post by rieka2 on 2015-05-07
I'd like to point out that Apache no longer uses the [NameVirtualHost]("http://httpd.apache.org/docs/2.4/upgrading.html") directive as of 2.4  so this is not a solution

---

### Post by SeijiSensei on 2015-05-07
> **rieka2 said:**
> I'd like to point out that Apache no longer uses the [NameVirtualHost]("http://httpd.apache.org/docs/2.4/upgrading.html") directive as of 2.4  so this is not a solution

In 2.2, you would specify IP:port combinations with NameVirtualHost and reference them in <VirtualHost> containers.   In 2.4 it's no longer necessary to specify the IP:port explicitly.  According to the documentation you linked to "Any address/port combination appearing in multiple virtual hosts is implicitly treated as a name-based virtual host."

Apache 2.4 in Ubuntu still has virtual host definitions in /etc/apache2/sites-available and links to the active hosts in /etc/apache2/sites-enabled.  Place your virtual host configuration files in /sites-available/ as hostname.conf and use "sudo a2ensite hostname" to enable them.  The .conf extension is mandatory; they are referenced in this statement
```
# Include the virtual host configurations:
IncludeOptional sites-enabled/*.conf

```
at the end of /etc/apache2/apache2.conf.

I suggest reading the Ubuntu Server Guide: [https://help.ubuntu.com/lts/serverguide/httpd.html#http-configuration](https://help.ubuntu.com/lts/serverguide/httpd.html#http-configuration)

Apache doesn't use BIND at all to determine which virtual host to display.  It matches on the hostname specified in the URL.  If the server needs to handle requests for [http://www.example.com/](http://www.example.com/), then there needs to be a <VirtualHost> container that includes a ServerName or ServerAlias directive like:
```
ServerName     www.example.com
```
or 
```
ServerName     myserver.example.com
ServerAlias    www.example.com
```

You can have your DNS hosted anywhere.  Just make "www.example.com" point to the IP address of your server.  Do that for all the domains you manage.  The easiest method is to use a "master" domain that contains the server's A record, and CNAME records that point to it for all the other domains.

---

### Post by rieka2 on 2015-05-07
I've got all that but a browser request to any of the domains always shows the same default /var/www/html/index.html page! 
Apache is not able to switch to the correct directory at /var/www/someotherdirectory/html/index.html.

---

### Post by SeijiSensei on 2015-05-07
Show us a file in /sites-available/ that contains the specifications for a virtual host other than the default in 000-default.conf.  Make sure it's a file that has a corresponding symlink in /sites-enabled/.

---

### Post by rieka2 on 2015-05-07
Here is one of the files:

```
<VirtualHost *>
DocumentRoot "/var/www/www-guzinta/web"
ServerName www.guzinta.org
ServerAlias guzinta.org
<Directory "/var/www/www-guzinta/web">
allow from all
Options None
Require all granted
</Directory>
TransferLog /var/log/www/guzinta.log
</VirtualHost>
```

The stuff between <Directory> and </Directory> all came from the apache2.conf master, the only items I've changed were to add the ServerAlias and TransferLog lines, and point to the directory location outside of /var/www/html.

I've even looked at permissions of the /var/www file structure - the user/group www-data owns everything.

What I fear most is that there is some little syntax error somewhere, like a missing period or a / that should not be there.

From the error log, the .htaccess files now all have the following code for ModRewrite but that is not a mod enabled in Apache2.
```
<IfModule mod_rewrite.c>
  RewriteEngine on
  RewriteCond %{REQUEST_FILENAME} !-f
  RewriteCond %{REQUEST_FILENAME} !-d
  RewriteRule ^(.*)$ / [L,QSA]
</IfModule>
```

When I enabled it, the error log showed [Thu May 07 16:37:01.080673 2015] [rewrite:error] [pid 23572] [client 50.196.158.93:50995] AH00670: Options FollowSymLinks and SymLinksIfOwnerMatch are both off, so the RewriteRule directive is also forbidden due to its similar ability to circumvent directory restrictions : /var/www/www-30hours/web/

This sounds like a problem... Now that url shows a flat version of the page (which was a WordPress site before copying from old server) that might be from some cache - rather than the default page in /var/www/html.

**NowI've found that it is really necessary to make the top line of the .conf file say <VirtualHost *:80> instead of the default <VirtualHost *> in order to make the thing work!**

---

### Post by SeijiSensei on 2015-05-07
I was just about to mention that.  Actually <VirtualHost *:80> has been the default for quite a while, even with Apache 2.2 on Ubuntu 12.04 or before.  You need to specify both an IP or a wildcard like * and a port. For secure servers you need to use <VirtualHost *:443>, but managing virtual secure servers is complex.  I've only ever run HTTPS servers on their own unique IP addresses.

To enable rewriting, you have to activate mod_rewrite.  Use the command
```
sudo a2enmod rewrite
```
and restart the server as directed. See if rewriting works now.

You can browse the list of available modules in /etc/apache2/mods-available/.  Ones that are activated with a2enmod create symlinks in /mods-enabled/ to .load files in /mods-available/.  The file rewrite.load looks like this:
```
LoadModule rewrite_module /usr/lib/apache2/modules/mod_rewrite.so
```
Some modules have a .conf file as well that is linked with a2enmod.

I don't understand why mod_rewrite is not activated by default.  I've used it myself.  I run CentOS on servers where mod_rewrite and many others are enabled by default.

---

### Post by rieka2 on 2015-05-07
Thanks for bearing with my process... Now all I have to do is get the Wordpress sites up and running again!

---

