---
title: "Apache : Virtual hosts on a per user basis?"
date: 2010-04-30
forum: Server Platforms
---

### Post by ElofTurtle on 2010-04-30
This is my first thread, so I really hope I got the placement right :)

I've been searching this for a couple of days:

OS: Ubuntu Server 9.10

I'd like to give each user a virtual host instead of the ~/username thing. Is there some way to use regular expressions when defining virtual hosts, or will I have to script a new section for each of the users I add?

So instead of declaring one virtual hosts for everyone: /home/joe/html -> joe.example.com; /home/jeff -> jeff.example.com I'd like to do something like : /homr/*/html -> "username".example.com in ServerName (?) declaration.

Any ideas? I know this is easilly scripted, but I'm curious and I know there are a lot of geniouses here  n_n

---

### Post by cdenley on 2010-04-30
Maybe with mod_rewrite you can internally redirect subdomains to user directories. Something like
```

RewriteCond %{REQUEST_URI} !^/~
RewriteCond %{HTTP_HOST} !^www\.mydomain\.com$
RewriteCond %{HTTP_HOST} ^(.*)\.mydomain\.com$
RewriteRule /(.*) /~%1/$1 [PT]

```

---

### Post by ElofTurtle on 2010-05-03
```

<IfModule rewrite_module>
        RewriteEngine on

        RewriteCond %{HTTP_HOST} ! ^(.*)\.localhost$
        RewriteCond %{HTTP_POST}   ^(.*)\.localhost$
        RewriteRule /(.*) /~%1/$1 [L]
</IfModule>

```Does not work :-/
According to lynx it tries stuff like [http://username.localhost.com](http://username.localhost.com) instead of redirecting internally. This could, however, be a /etc/hosts matter. Will also try to make another redirect to "fixed path" site not in hosts to check.

It would be nice if it wasn't, since then this would eventually work without any per-user configurations...

By the way - the %! and $1 - what does these point to and how do you know?

---

### Post by cdenley on 2010-05-03
You didn't copy it correctly, but I also needed to make a few corrections as I hadn't actually tested that configuration since I was just trying to point you in the right direction. I tested this, and it seems to work.
```

<VirtualHost *:80>
	ServerName example.com
	ServerAlias *.example.com
	UserDir public_html
	RewriteEngine on
	RewriteCond %{REQUEST_URI} !^/~
	RewriteCond %{HTTP_HOST} !^www\.example\.com$
	RewriteCond %{HTTP_HOST} ^(.*)\.example\.com$
	RewriteRule /(.*) /~%1/$1 [PT]
</VirtualHost>

```

For RewriteRule, "$" followed by a number refers to the text within parenthesis in the matching pattern. $1 means the first perenthesis, which is basically the entire URI. "%" works the same, except with the matching pattern for the last RewriteCond directive used. In this case, it would be the subdomain, which is also the username of the user's site being accessed. These are called "back-references".
[http://httpd.apache.org/docs/2.2/mod/mod_rewrite.html#rewriterule](http://httpd.apache.org/docs/2.2/mod/mod_rewrite.html#rewriterule)

---

