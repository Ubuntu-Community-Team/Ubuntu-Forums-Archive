---
title: "Enabling SSI in Apache"
date: 2005-11-13
forum: Server Platforms
---

### Post by Centrist on 2005-11-13
I'm trying to set up a web server on a computer running Ubuntu. I've installed apache 2 with no problems. Its working just fine with PHP and MySql, but I can't figure out how to get SSI to work. I went to Apache's site, but their docs are based on httpd.conf which I guess is the pre-2.0 setup.:confused: 

My installation is pretty much the default with my SSI pages in /var/www. What do I have to change to enable SSI with .shtml and .html?

Thanks.

---

### Post by Juzz on 2005-11-14
As far as I remember both apache 1 and 2 use httpd.conf - but my guess is that you might have to look at the files it includes if it isn't in the httpd.conf.

---

### Post by Centrist on 2005-11-16
This is what's in my httpd.conf in /etc/apache2/

```
# This is here for backwards compatability reasons and to support
#  installing 3rd party modules directly via apxs2, rather than
#  through the /etc/apache2/mods-{available,enabled} mechanism.
#
#LoadModule mod_placeholder /usr/lib/apache2/modules/mod_placeholder.so
```

All the regular config stuff in is apache2.conf. So did I download the wrong package? I added Options +Includes to the config, but it didn't work and I think I have it in the wrong place.

---

### Post by Centrist on 2005-11-20
OK, here's what I have:

In /etc/apache2/sites-enabled/000-default:

```

<Directory /var/www/>
	Options Indexes FollowSymLinks MultiViews +Includes
	AllowOverride None
	Order allow,deny
	allow from all
	AddType text/html .shtml
	AddOutputFilter INCLUDES .shtml

	# This directive allows us to have apache2's default start page
        # in /apache2-default/, but still have / go to the right place
        # Commented out for Ubuntu
        #RedirectMatch ^/$ /apache2-default/
</Directory>

```

And my include directive is:

```

<!-- #include virtual="/header.html" -->

```

I'm following the apache tutorial as close as I can because it sucks with details. What else can I look at?

---

### Post by herrpoon on 2005-11-20
Hi, from what I can tell, everything looks fine with regards to what you have in sites-enabled, the only thing I can think of is that you haven't restarted apache.

Edit:  It looks like you're using the wrong syntax!  You shouldn't have a space between the hash (#) and the last hypen (-) so it should be:

```
<!--#include virtual="/header.html" -->
```

Just tried it on my system and it doesn't work with the space :p

---

### Post by Centrist on 2005-11-20
Yeah, I was wondering if it could have been the space. I've tried to make this work with or without it. But now I know to keep it out. I am restarting the service, and I have even tried restarting the machine, but still no luck.

I had this site running on Win2k3/IIS6. Is there anything else I should change to get my pages working under Ubuntu/Apache2?

---

### Post by herrpoon on 2005-11-21
I assume you're following this guide: [https://wiki.ubuntu.com/ServerSideIncludes](https://wiki.ubuntu.com/ServerSideIncludes)

Are you getting any error messages at all in your apache log?

---

### Post by Centrist on 2005-11-23
Until you mentioned it, I hadn't seen that page on the wiki. I was reading the one on Apache's site which for some reason doesn't have anything about the symlink you need to make. It's working now, thanks for your help. ;)

---

### Post by herrpoon on 2005-11-23
Cool, good to see you got it working :p

---

