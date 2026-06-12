---
title: "Redirecting port 80 traffic to 443 with apache2"
date: 2006-03-09
forum: Server Platforms
---

### Post by nihilocrat on 2006-03-09
I just recently set up my apache2 server to accept SSL traffic. I want to restrict access to the webserver such that ALL traffic to this particular vhost is SSL enabled. Basically what I'm envisioning is that if someone types 'http://moodle.crazygonuts.edu' or 'http://moodle.crazygonuts.edu/somedir/somefile.php' it will automatically redirect that to https.

When I try enabling the vhost like so:
```

NameVirtualHost *
<VirtualHost *>
        ServerName moodle.crazygonuts.edu
        ServerAlias moodle

       .... other stuff ....
</VirtualHost>

```

When a user accesses moodle.guilford.edu at port 80, it will send them to a "Bad Request" page like this:

```

Bad Request

Your browser sent a request that this server could not understand.
Reason: You're speaking plain HTTP to an SSL-enabled server port.
Instead use the HTTPS scheme to access this URL, please.

    Hint: https://moodle.crazygonuts.edu/

```

Strangely, the redirect points to the right place, but no images or CSS stylesheet data (i.e. font colors, etc.) show up.

I tried using the rewrite module with this code, but it didn't seem to change the situation at all:
```

RewriteEngine   On
RewriteCond     %{SERVER_PORT} ^80$
RewriteRule     (.*)$  https://%{SERVER_NAME}/$1 [L,R]
RewriteLog      "/var/log/apache2/moodle-rewrite.log"
RewriteLogLevel 2

```

For the time being, it works fine if I set up a non-SSL vhost along with an SSL-enabled vhost with these parameters, with the non-SSL vhost listening to port 80:

```

NameVirtualHost *:443
<VirtualHost *:443>

```

The only reason I don't just disable the non-SSL vhost is a) it would probably be very difficult to get the users to change all their bookmarks to the new host and b) the ability for the SSL vhost to display pictures and CSS stylesheet data seems to be dependent on the non-SSL vhost being enabled.

So yeah, any help is appreciated!

---

