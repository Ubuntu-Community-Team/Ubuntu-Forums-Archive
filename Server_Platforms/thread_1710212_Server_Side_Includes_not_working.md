---
title: "Server Side Includes not working"
date: 2011-03-19
forum: Server Platforms
---

### Post by freebeer on 2011-03-19
Hi!

I'm setting up a new web server on a Virtual Private Server (Ubuntu Server 10.04 32-bit).  I need to rely on Server Side Includes for many of my pages (I include my navigation menu and footer so I just have to change it in one place.)  

So testing with the current default page, the page serves up just fine, but it won't include/observe the include directive.  The small test snippet of code isn't included in the served page.

You can see the page [here]("http://smart-rooms.org") if you're so inclined. :)

I'm using the [XbitHack technique]("http://httpd.apache.org/docs/2.0/howto/ssi.html#configuring") which I know to work on my other hosted site, so I'm guessing that I just don't have Apache2 configured properly.

I can verify that the execute bit has been set on the page, I have the +Includes set for both the httpd.conf file AND in .htaccess.  I noticed that mod_include wasn't part of mods-available in the default set up, so I used a2enmod to enable that module.  And, of course, I've restarted apache2 several times through all of this.  There's nothing in the error log that would indicate what the problem might be.  Any suggestions as to where I should be looking next?

As an aside, I noticed that the default ownership for /var/www/ was root.  Shouldn't that be www-data?  I have confirmed that apache2 is running as user and group www-data and so I chown'ed the folders to www-data (I did this after trying to get SSI to work with ownership as root.)  Basically I think I've tried every combination I could think of that would be preventing the includes from happening.

---

### Post by falko on 2011-03-19
I'm using the other method

```
AddType text/html .shtml
AddOutputFilter INCLUDES .shtml
```

and never had any problems with it. Can you try that?

---

### Post by freebeer on 2011-03-19
Thanks for the reply. :D

I prefer not to go the route of shtml.  It's rather non-standard these days and it would require renaming all my files (not that big of a deal) but a *lot* of my inbound links are to .html.  Sure, I could use 301 redirects, but that just adds more mess.

I do know the XHack method works.  It works just fine on my currently hosted site (which is just a basic web hosting service).  I want to migrate the contents on that site to my new server which gives me greater flexibility in what I can do.  Once I figure out how to get the configuration on the new site sorted out, of course.  :P

---

### Post by freebeer on 2011-03-19
Ok, I think I figured it out.  Still a few more tweaks to go, but it appears to be working.

falko's suggestion of adding or explicitly specifying (slightly modified)

```

AddType text/html .html
AddHandler server-parsed .html

```

seems to have made the difference.  I didn't have to do that on my other site, but perhaps that's because the hosting provider already had it configured that way.  (It's only a shared hosting service, so I don't have access to the apache config files to confirm.)

Anyway, it appears to be working atm. :)

I'll marked this as resolved, but I'd appreciate hearing about my other question: should the ownership of the /var/www/ folder (and below) be root or www-data?

Thanks!  [IMG]http://www.freebeer.is-a-geek.org/graphics/thumbsup.gif[/IMG]

---

