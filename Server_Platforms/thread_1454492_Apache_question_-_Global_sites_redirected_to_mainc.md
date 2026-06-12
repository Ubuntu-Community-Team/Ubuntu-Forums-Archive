---
title: "Apache question - Global sites redirected to main/country"
date: 2010-04-14
forum: Server Platforms
---

### Post by derelict888 on 2010-04-14
we have a main site;

domain.com

and 4 global sites;

domain.es
domain.fr
domain.co.uk
domain.co.au

I need to get the 4 global sites to redirect like this;

domain.co.uk  --->  domain.com/uk

All 5 sites are were created with wordpress and are in the same directory /var/www/domain.com

I already have a virtual host setup for domain.com, and I would like to add the redirects for all the global sites to it, but I don't know if thats how it works or not. I have control over the DNS of all sites and I'd like to just point all sites to the same IP (if this isn't the best way let me know)

Unfortunately my apache experience is too low for this, I've searched around online but I haven't been able to get a redirect working. I'd like to setup a permanent redirect (301), can someone help? Thanks

---

### Post by derelict888 on 2010-04-14
Ok I've got it figured out.

I have virtual hosts for all domains, and setup the redirect like this;

```
<Directory />
   RedirectPermanent  /  http://www/domain.com/[country]
```

If there is an easy way to do this with just one virtual host let me know, otherwise I'm good. Going to mark this as solved. Good work everyone.

---

### Post by volkswagner on 2010-04-14
I think you should create 301 redirects with .htaccess in the main directory.


You will want something like this for your .htaccess.  Understand the leading ^ will point any request with or without www or any subdomain.  So if you want separate sites for www or additional subdomains, loose the ^.  This can also be helpful to point you main domain non www requests to [www.domain.com](www.domain.com) (which is what the first condition does).  You will need to continue the pattern for remaining sites. 

```

Options +FollowSymlinks
RewriteEngine on
rewritecond %{http_host} ^domain.com [nc]
rewriterule ^(.*)$ http://www.domain.com/$1 [r=301,nc]
rewritecond %{http_host} ^domain.co.au [nc]
rewriterule ^(.*)$ http://www.domain.com/au/$1 [r=301,nc] [r=301,nc]
rewritecond %{http_host} ^domain.co.uk [nc]
rewriterule ^(.*)$ http://www.domain.com/uk/$1 [r=301,nc]
```

I also had to set the permissions to 755 for .htaccess

You can search around for 301 redirect apache2 .htaccess for more resouces.

You will need to modify your vhost file if it has

```
AllowOverride None
```

change to

```
AllowOverride All
```

Also add to httpd.conf I added

```
RewriteEngine On


```


Please understand I am no expert.  These are just the steps I had to take today to get a very similar setup going.  I am not using directories, so for your RewriteRule I added your subdirectory and kept the wildcard "/$1" so it should work for all urls under the /uk directory.

I found it very difficult to come up the the setup, with all the varying information available.

---

