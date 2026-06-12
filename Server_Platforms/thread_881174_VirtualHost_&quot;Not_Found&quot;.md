---
title: "VirtualHost &quot;Not Found&quot;"
date: 2008-08-05
forum: Server Platforms
---

### Post by coolaj86 on 2008-08-05
I'm trying to set up a site foo.bar.com and then redirect it to newbar.foo.com.

The "It Works" page did work with the [http://localhost](http://localhost), and now the redirection works as well, but [http://foo.bar.com](http://foo.bar.com) gets a "Not Found The requested URL / was not found on this server."



```
/etc/hosts:
127.0.0.1    localhost foo.bar.com
```

I do this to get rid of the common "[warn] NameVirtualHost *:0 has no VirtualHosts" error

```
sudo vim /etc/apache2/conf.d/virtual:
# added
NameVirtualHost *
```

```
sudo vim /etc/apache2/sites-available/default:
# commented out
#NameVirtualHost *
# Added further down
        <IfModule mod_rewrite.c>
                rewriteEngine On
                RewriteCond %{HTTP_HOST} ^localhost* [NC]
                RewriteRule .* http://newbar\.foo.com/ [R=301,NC]
        </IfModule>
```

```
sudo cp /etc/apache2/sites-available/default /etc/apache2/sites-available/foobar
```

Everything works great up to here, continuing:

```
sudo vim /etc/apache/sites-enabled/foobar
# Added
ServerName foo.bar.com
# Changed
                RewriteCond %{HTTP_HOST} ^foo\.bar.com.* [NC]
```
```

sudo a2ensite foobar
sudo apache2ctrl restart
```

I still get the "Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName" error, but it works, so that doesn't concern me.

If I visit [http://localhost](http://localhost) it directs me to [http://newbar.foo.com](http://newbar.foo.com)
If I visit [http://foo.bar.com](http://foo.bar.com) it says "Not Found" (that's from apache on the local server)

Of course, I don't really want to use foo.bar.com, but for the sake of this example I used these exact steps that I've posted and received these exact results.

---

### Post by spiderbatdad on 2008-08-05
```
/etc/hosts:
127.0.0.1    localhost foo.bar.com
```
This would not work.

This would:```
127.0.0.1  foo.bar.com
```

---

### Post by coolaj86 on 2008-08-05
Actually, it does work. Try it yourself.

---

### Post by spiderbatdad on 2008-08-05
> **coolaj86 said:**
> Actually, it does work. Try it yourself.

bleh...I knew that.:)

---

### Post by coolaj86 on 2008-08-06
It has something to do with these lines (which work):

```

    RewriteCond %{HTTP_HOST} ^foo.bar.com.* [NC]
    RewriteRule .* http://newbar\.foo.com/ [R=301,NC]

```

In the actual config I was using these lines (which doesn't work):
```

    RewriteCond %{HTTP_HOST} ^foo.bar.com.* [NC]
    RewriteRule .* http://newbar\.foo.com/ [R=404,NC,L]

```

I would like to redirect as a 404 rather than a 301, but for some reason it doesn't want me to do that.

I guess I lied that I wasn't doing it exactly as I did it on the example I was giving. Oops!

---

### Post by kihjin on 2008-08-06
I do like this:

```

# commented out

```

Very descriptive ;)

So you currently have localhost->newbar.foo.com working and you want foo.bar.com->newbar.foo.com ? 

Does this work?

```

RewriteEngine On
RewriteCond %{HTTP_HOST} ^localhost* [NC,OR]
RewriteCond %{HTTP_HOST} ^foo\.bar\.com* [NC]
RewriteRule ^/(.*) http://newbar\.foo\.com/$1 [R=301,NC]

```

Sorry at work now, can't really test it...

---

### Post by coolaj86 on 2008-08-06
by "# commented" out, I meant "# the line directly below this line I commented out"

Yes, what you have works. And my example works too. What the problem was that if I use [R=404] or [R=410] it stops and gives apache's "Not Found" or "Gone" page rather than redirecting.

Maybe this behavior is expected?

The real situation here is that the foo.bar.com site has been completely revamped and moved to newbar.foo.com and none of the pages correspond other than the homepage.

The ideal solution here would be to have the homepage issue a 301 and every other page to issue a 410 or 404.

---

