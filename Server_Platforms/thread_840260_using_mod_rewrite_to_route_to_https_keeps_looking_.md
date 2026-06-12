---
title: "using mod_rewrite to route to https keeps looking for index.html"
date: 2008-06-25
forum: Server Platforms
---

### Post by mrpeenut24 on 2008-06-25
I'm using mod_rewrite to reroute all traffic through ssl, but once it does so, it only looks for index.html in the directory.  In one of my sites, it uses a DirectoryIndex to tell it to find index.php, but I'd hate to have to modify every site for a specific hard-coded page.  Is there an easier way?

Here's a typical site:

```

<VirtualHost *:80>
ServerName blog.mydomain.com
DocumentRoot /usr/share/wordpress

<Directory /usr/share/wordpress>
       Options Indexes FollowSymLinks MultiViews
       AllowOverride None
       Order allow,deny
       allow from all
       <IfModule mod_rewrite.c>
         <IfModule mod_ssl.c>
           RewriteEngine on
           RewriteCond %{HTTPS} !^on$ [NC]
           RewriteRule . https://%{HTTP_HOST}%{REQUEST_URI}  [L]
         </IfModule>
       </IfModule>
</Directory>
</VirtualHost>

```and I've got a matching blog-ssl site that catches the redirect; the only differences being that the blog-ssl file has no mod_rewrite directive, and it turns on SSL.

When I go to [http://blog.mydomain.com](http://blog.mydomain.com) it redirects me to [https://blog.mydomain.com/index.html](https://blog.mydomain.com/index.html).  It doesn't look in the directory for .php, .htm, etc.  I'm not sure why it's choosing index.html.  Anyone got a clue?



EDIT:  also, if I just take off the index.html after it redirects (just go directly to [https://blog.mydomain.com/](https://blog.mydomain.com/)) it has no problem taking me to the correct page (index.php in this case).

---

### Post by slakkie on 2008-06-25
Edit: misread your post, my reply doesn't resolve anything for you.

Why don't you make a vhost config for port 80 and port 443?

Like this:

```

<VirtualHost _default_:80>
    ServerName server.domain.tld
    ServerAlias alias.domain.tld
    RedirectMatch ^/(.*) https://server.domain.tld:443/$1
</VirtualHost>

# Be compatible with old bookmarks and such
<VirtualHost _default_:8080>
    ServerName server.domain.tld
    ServerAlias alias.domain.tld
    RedirectMatch ^/(.*) https://server.domain.tld:443/$1
</VirtualHost>

<VirtualHost _default_:443>
#   General setup for the virtual host
DocumentRoot "/opt/apache/htdocs"
ServerName server.domain.tld
ServerAlias alias.domain.tld
ServerAdmin you@domain.tld
ErrorLog /opt/apache/logs/error_ssl_log
TransferLog /opt/apache/logs/access_ssl_log

# Rewrite rules for tickets
RewriteEngine on
# Only needed when you are debugging the rewrite
# Make sure the LogLevel is defined
#RewriteLog    /opt/apache/logs/rewrite.log
#RewriteLogLevel 9
RewriteCond   %{REQUEST_URI}   /ticket/.+
RewriteMap    ticket-rw        prg:/opt/remedy/mid-tier/perl/parse_ticket_id.pl
RewriteRule   ^/ticket/(.+)    ${ticket-rw:$1} [R,L]

RewriteCond   %{REQUEST_URI}   !^/arsys/.*
RewriteRule   .*               /arsys/ [R,L]

# Snip, scroll down, snip 
#   Server Certificate:
SSLCertificateFile /opt/apache/conf/ssl_keys/server.crt
#SSLCertificateFile /opt/apache/conf/server-dsa.crt

#   Server Private Key:
SSLCertificateKeyFile /opt/apache/conf/ssl_keys/server.key
#SSLCertificateKeyFile /opt/apache/conf/server-dsa.key

```

---

### Post by mrpeenut24 on 2008-06-25
Yeah, I've already figured out how to redirect to ssl, and I've got a separate file with the VirtualHost:443.  I'm just trying to stop it from automatically choosing index.html as the default page.

---

### Post by MJN on 2008-06-25
Whilst it's not clear exactly why you are seeing what you are[1], I do know that you could avoid the issue entirely by doing what Slakkie suggests. Specifically, given that you don't want to allow any non-HTTPS access to your blog (as an example) then configure the non-HTTPS 'version' of the blog as a barebones redirect-all as per the top of Slakkie's example.
 
To put it another way, why do in 18 lines what you can do in 3?
 
Mathew
 
[1] The cause could be down to the behaviour of the {REQUEST_URI} string that it catches the first match in DirectoryIndex when not specified in the browser request - you could prove this by browsing to [http://blog.mydomain.com/index.php](http://blog.mydomain.com/index.php) - if this redirects as desired then this is likely it.

---

### Post by mrpeenut24 on 2008-06-25
Sorry, you're right.  That worked.  Thanks slakkie, MJN.

---

### Post by MJN on 2008-06-26
That's excellent. For what it's worth your approach was still 'right' - it was just going a long(er) way round and falling in a hole in the process! ;)
 
Mathew

---

### Post by slakkie on 2008-06-26
No problemo dude :) Glad I could help.

---

