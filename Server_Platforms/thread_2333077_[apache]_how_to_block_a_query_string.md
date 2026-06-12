---
title: "[apache] how to block a query string"
date: 2016-08-06
forum: Server Platforms
---

### Post by joshuaa001 on 2016-08-06
Hello

I'm trying to block any incoming hits to this string:

[07/Aug/2016:00:56:14 +0300] "GET /?r=3
[07/Aug/2016:00:56:54 +0300] "POST /?r=3

there are other characters after 3 so i'll have to use a wildcard string.

any ideas? thank you!

---

### Post by Vegan on 2016-08-06
no much you can do, web servers get trash with bizarre gets etc all the time

---

### Post by SeijiSensei on 2016-08-06
You might try using a redirect.  Something like this:
```

<VirtualHost *:80>
ServerName     www.example.com
Redirect /?r=3  http://www.example.com/goaway.html

[etc.]
</VirtualHost>

```
That might work for GETs.  I don't know what to use for POSTs.

Are these coming from a lot of machines, or just a few?  It might be easier to block the machines themselves with iptables rules like this:
```

/sbin/iptables -A INPUT -s ip.addr.bad.host -j REJECT

```
using as many rules as needed to cover all the bad IPs.

---

### Post by joshuaa001 on 2016-08-07
thank you for your answer.

iptables isn't very effective as there are new requests from other ips every hour. and there are a lot of them:

cat /var/log/apache2/access.log | grep "/?r=3" | wc -l
537

based on a few hours of google search, i've found out that i can use an if directive, something like this:

<If "%{QUERY_STRING} =~ /?=r3*/">
   Require all denied
</If>

but i think it's not written properly because if i add that to the virtualhost and restart, it crashes httpd:

AH00526: Syntax error on line 5 of /etc/apache2/sites-enabled/second.conf:
Cannot parse condition clause: Failed to compile regular expression
Action 'restart' failed.

also, i've seen that there is a way to use .htaccess with

RewriteCond %{REQUEST_URI}
RewriteRule

but i just can't understand how to write it so it uses a wildcard 

thank you!

---

### Post by SeijiSensei on 2016-08-07
I don't know if this will help, but the ? in the regex should probably be escaped:
```

<If "%{QUERY_STRING} =~ /**\**?=r3*/">

```
If the string really is exactly "?=r3" then I might use this regex
```

<If "%{QUERY_STRING} =~ /**\**?=r3**$**/">

```

Where are you putting this?  I believe it should be inside the <Directory> stanza for the DocumentRoot:
```

DocumentRoot /var/www/html
<Directory "/var/www/html">
    <If "%{QUERY_STRING} =~ /\?=r3$/">
     Require All Denied
    </If>
    [stuff]
</Directory>

```

Also when you have control over the server configuration, you should avoid using .htaccess.  That's a kludge for ISPs that host sites.  Any directives you would put in an .htaccess file should be moved to the corresponding <Directory> stanza in the Apache configuration file for the virtual host.

---

