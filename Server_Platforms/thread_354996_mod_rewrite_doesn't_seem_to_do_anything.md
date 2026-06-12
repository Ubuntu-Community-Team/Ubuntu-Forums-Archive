---
title: "mod_rewrite doesn't seem to do anything"
date: 2007-02-06
forum: Server Platforms
---

### Post by Steve Smith on 2007-02-06
I've installed apache successfully.  I've enabled mod_rewrite with a2enmod rewrite, but I can't seem to make it do anything!

I've put htis at the bottom of apache2.conf and restarted apache:

```

RewriteEngine On
RewriteRule old\.html$ test.html [L]

```

Then I restart apache, go to [http://mysite.dyndns.org/old.html](http://mysite.dyndns.org/old.html) and just get a 404 (test.html does exist).

I've tried setting AllowOverride all, but it didn't work.  Though I don't think I need it anyway, as I'm putting the rewrite rules straight into apache2.conf.

Any thoughts?  Is my syntax right?
Steve

---

### Post by jtc on 2007-02-06
Since you are doing a very specific rewrite I'd say it belong inside the <Directory...> of your Documentroot. Try putting the same lines you are using inside it, and you should be fine.

(Of course, it is possible to have it as a general rule, but then you'll have to expand it some more. I guess it all depens on whatever you want all your old.html --> test.html or just the one in the the Dcoumentroot.)

---

### Post by Steve Smith on 2007-02-10
Sorry, I didn't make myself clear - that's just a simple test because I couldn't make it do anything!  What I'm actually trying to do is remove the ~s from user's directories and replace them with people/ eg /~steve becomes /people/steve.

Could you give me an example with Documentroot - I can't find where you mean.

Thanks!

---

### Post by jtc on 2007-02-10
Well, never mind the wording DocumentRoot, let me clarify the point I was, perhaps not very skillfully, trying to make. A Rewriterule, as any other apache-directive should be placed accordingly to what it is trying to affect. It could be the entire webbserver, or a <VirtualHost..>, a <Directory...> or something else.

I'd say this kind of ReWrite belongs inside the VirtualHost you are have the homedirs in. Unless you've made your own, and sticking with the original one, you'll find it in /etc/apache2/sites-available/default

There are two kinds of rules you can apply, depending on what behavior you want.

This first one leave the /people/username in the addressfield, and simply mapp the url to the users public_html-directory. In this crude example I've assumed the username only contains of the characters a to z.
```
RewriteRule ^/people/([a-z]+)/?(.+)?$          /home/$1/public_html/$2 [L]
```

Option number two does a Redirect from /people/username to ~username, and thereby also changing the value in the addressfield.
```
RewriteRule ^/people/(.+)$          http://your.domain/~$1 [R]
```

Again I'd like to point out that these are crude examples written in the spure of the moment. They could very well be perfectly sound, but I'm not giving any guarantees :)

Apache has some good documentation about mod_rewrite

[http://httpd.apache.org/docs/2.0/misc/rewriteguide.html](http://httpd.apache.org/docs/2.0/misc/rewriteguide.html)
[http://httpd.apache.org/docs/2.0/mod/mod_rewrite.html](http://httpd.apache.org/docs/2.0/mod/mod_rewrite.html)

---

### Post by Steve Smith on 2007-02-10
Thanks for the detailed instructions, that's brilliant!  Still can't make it work mind...  I couldn't make your first example work, so I tried the second.  Here's my /etc/apache2/sites-available/default:

```

NameVirtualHost *
<VirtualHost *>
        ServerAdmin webmaster@localhost

        DocumentRoot /var/www
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
                # Uncomment this directive is you want to see apache2's
                # default start page (in /apache2-default) when you go to /
                #RedirectMatch ^/$ /apache2-default/
                [COLOR="SeaGreen"]RewriteRule ^/people/(.+)$ http://myname.homelinux.org/~$1 [R][/COLOR]
        </Directory>

```

---

### Post by Steve Smith on 2007-02-10
I realised it should have gone under <document /> not /var/www, but it still doesn't work!

Also, now realised I don't have a RewriteEngine On, so I've put this in apache2.conf, immediately before # Include the virtual host configurations:
Include /etc/apache2/sites-enabled/[^.#]*

```

<IfModule mod_rewrite.c>
RewriteEngine On
</IfModule>

```

Is that the right place?

---

### Post by jtc on 2007-02-11
Actually, when I said it belonged inside the <Virtualhost ...> I meant it only belonged inside the Virtualhost. In other words, you should not have it inside any <Directory ...>.

Regarding your "RewriteEngine On" you should have in the same "scope" as your rewriterule(s), in other words, something like this.

```

RewriteEngine On
RewriteRule ^/people/(.+)$ http://myname.homelinux.org/~$1 [R]

```

Of course, this would have gone a lot quick if I had just given you a complete /etc/apache2/site-availible/default, but that way you wouldn't have learned as much :)

---

### Post by Steve Smith on 2007-02-11
It works!!  Thank you so much!

> **jtc said:**
> Of course, this would have gone a lot quick if I had just given you a complete /etc/apache2/site-availible/default, but that way you wouldn't have learned as much :)

Absolutely :).  And you're right you know, I've learned loads by poking around with that.

---

### Post by Steve Smith on 2007-02-13
I'm back, going up in the world of rewriting with any luck :).  I've now got a domain name pointing to my webserver.  I've set up a CNAME of steve.mydomain.co.uk, so I want to map that to /~steve.  I've got as for as:

```

RewriteRule ^([a-zA-Z0-9]+)\.mydomain\.co\.uk/?(.+)?$ /home/$1/www/$2 [L]

```

but it doesn't do anything, steve.mydomain.co.uk still serves the contents of /var/www.  Have I got the rule right, and if I have do I need to do something to stop /var/www being served on that address first, before I do the rewrite?

Of course, [www.mydomain.co.uk](www.mydomain.co.uk) still needs to server /var/www!

---

### Post by jtc on 2007-02-13
Well, you could use mod_rewrite to accomplish this, but I wonder if not [mod_vhost_alias]("http://httpd.apache.org/docs/2.0/mod/mod_vhost_alias.html") is the way to go? Now I assume steve is simply a placeholder for ANY username? Otherwise, a simple vhost would do the trick.

---

### Post by Steve Smith on 2007-02-13
Yes, steve is just a placeholder.

I'd prefer not to use vhosts for now.  I'm trying to learn Apache from the basics up, if that makes sense, so I'll get a better picture of how it works.  I've been looking at [http://blogs.warwick.ac.uk/tretout/entry/apache_mod_userdir/](http://blogs.warwick.ac.uk/tretout/entry/apache_mod_userdir/) where they've done what I want with rewrite, as far as I can tell, but I don't understand enough to be able to pull out the pieces I need - could you give me a hand?

Thanks again! :)

---

### Post by jtc on 2007-02-14
Well, I'm not sure if I would call this kinds of rewrites for basics, but I'll give you some pointers :-)

First of all, the reason why the following line doesn't work is because the RewriteRule has no idea what kind of hostname is involved. The basic input to the rule is simply the pathname of the address; such as /~username/index.html och /pictures/sun.jpg or something.

> **Steve Smith said:**
> ```

RewriteRule ^([a-zA-Z0-9]+)\.mydomain\.co\.uk/?(.+)?$ /home/$1/www/$2 [L]

```

If you want to do more advanced things with mod_rewrite just using RewriteRule won't do. Primarily it is RewriteCond which will be involved in the magic as well. Then, and here comes the trycky part, you'll have to understand how mod_rewrite "flows", in which order it does things, what is repeated, etc. That last part is, by the way, where I lack most.

Unless you already are familiar with regular expressions this is as good time as any time start looking closer at them.

---

### Post by Steve Smith on 2007-02-14
> **jtc said:**
> First of all, the reason why the following line doesn't work is because the RewriteRule has no idea what kind of hostname is involved. The basic input to the rule is simply the pathname of the address; such as /~username/index.html och /pictures/sun.jpg or something.

Since your last post I've been having a play with the example I mentioned a few posts ago, and got this far:

```

RewriteCond %{HTTP_HOST}%{REQUEST_URI} ^(.+)\.mydomain.co.uk/(.*)$
RewriteRule ^(.+) %{HTTP_HOST}$1 [C]
RewriteRule ^(.+)\.mydomain.co.uk/?(.*)$ http://www.mydomain.co.uk/~steve [L]

```

which doesn't quite work, but with a few various versions of it I've had it do odd things like repeating parts of the URL, so I'm getting there!  When I manage to get it goign I'll post back.  Thanks for your help!

---

### Post by jtc on 2007-02-14
Good luck! Looking forward to hear about your progress.

---

### Post by Steve Smith on 2007-02-15
I opted for pasting everything from the example and then commenting out a line at a time to work out what it was all doing!  I've now realised I needed all of it, more or less:

```

        # Handle missing trailing slashes for directories
        RewriteCond %{REQUEST_URI} !^/~
        RewriteCond %{REQUEST_URI} !^/icons/
        RewriteCond %{REQUEST_URI} !^/error/
        RewriteCond %{REQUEST_URI} !/$
        RewriteCond %{HTTP_HOST}%{REQUEST_URI} ^([^.]+\.)*([^.]+)\.(mydomain)\.co\.uk/(.*)$
        RewriteCond /home/%2/www/%4 -d
        RewriteRule ^(.+) %{HTTP_HOST}$1 [C]
        RewriteRule ^([^.]+\.)*([^.]+)\.(mydomain)\.co\.uk/(.*) http://$1$2.mydomain.co.uk/$4/ [R,L]

        # All requests that aren't for directories
        RewriteCond %{REQUEST_URI} !^/~
        RewriteCond %{REQUEST_URI} !^/icons/
        RewriteCond %{REQUEST_URI} !^/error/
        [COLOR="Navy"]RewriteCond %{HTTP_HOST} !^www\.mydomain\.co\.uk$[/COLOR]
        RewriteCond %{HTTP_HOST} ^([^.]+\.)*[^.]+\.(mydomain)\.co\.uk$
        RewriteRule ^(.+) %{HTTP_HOST}$1 [C]
        RewriteCond /home/$2/www -d
        RewriteRule ^([^.]+\.)*([^.]+)\.(mydomain)\.co\.uk/(.*) /~$2/$4 [PT,E=MEMBERS:1,L]

```

As it was it made [www.anything](www.anything) return 404, so I added [COLOR="Navy"]RewriteCond %{HTTP_HOST} !^www\.mydomain\.co\.uk$[/COLOR] to solve that.

The next thing to do is make steve.mydomain.co.uk/~steve return a 404, while still allowing [www.mydomain.co.uk/~steve](www.mydomain.co.uk/~steve) to work.  In can't use the method in [their example](http://blogs.warwick.ac.uk/tretout/entry/apache_mod_userdir/), as they descriminate by virtual hosts, and all of mine are on the same virtual host.  Any ideas?

---

### Post by jtc on 2007-02-15
Just a bit to much mod_rewrite for me to wrap my brain around right now :-P

---

### Post by Steve Smith on 2007-02-15
Haha, wrong end of the day for all those funny symbols, isn't it :)

---

### Post by tylerjwilk on 2007-07-26
In your 

       sites-enabled/default

under

       Directory /var/www

Change

        AllowOverride None

to

      AllowOverride All

Save config

     sudo /etc/init.d/apache2 restart

should have mod_rewrite working

---

