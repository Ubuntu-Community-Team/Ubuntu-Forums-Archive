---
title: "Remap .aspx extension"
date: 2009-11-13
forum: Server Platforms
---

### Post by WitchCraft on 2009-11-13
Question:

I use mono (.NET for Linux), and so my pages look in the user browser like:
[http://localhost/default.aspx](http://localhost/default.aspx)

Is it possible with apache/lighthttp/xsp/xsp2 to remap the extension ".aspx" to, for example, ".lol" ?

What I mean is that the users sees (for example):
[http://localhost/default.lol](http://localhost/default.lol)
instead...

Is that possible? If yes, how ?

---

### Post by mrsteveman1 on 2009-11-13
What you actually want is pretty urls, not rewriting the extension of an actual file.

If you take a look at some of the pages on my site, they all end in ".geek". That wasn't just apache rewrite though, Wordpress is actually responding to those urls with a trailing .geek, it's just rerouted to a php file using rewrite:

> # BEGIN WordPress
<IfModule mod_rewrite.c>
RewriteEngine On
RewriteBase /
RewriteCond %{REQUEST_FILENAME} !-f
RewriteCond %{REQUEST_FILENAME} !-d
RewriteRule . /index.php [L]
</IfModule>


Not sure if there's any way to do it without building it into your app. Are you using an existing .net software package or did you write this yourself?

---

### Post by directhex on 2009-11-13
Should be a simple htaccess job, surely?

---

### Post by WitchCraft on 2009-11-13
> **directhex said:**
> Should be a simple htaccess job, surely?

In htaccess or in httdp.conf, that's the question here ;-))



> **mrsteveman1 said:**
> 
What you actually want is pretty urls, not rewriting the extension of an actual file.

Not sure if there's any way to do it without building it into your app. Are you using an existing .net software package or did you write this yourself?


Write it myself of course.
And I said I want to [COLOR="Red"]remap [/COLOR]the extension, rewriting or changing it would probably break asp/mono.
I think there's most likeley a better solution then rewriting them myself.
I figured it was in httpd.conf, but might also be in htacces, but I don't know which setting ;-), and I don't have the time to RTFM, if I still want to do something else this weekend...

---

### Post by mrsteveman1 on 2009-11-13
Well, mod_Rewrite does appear to do mapping of that sort, i mean there isn't actually a file or url for any of the urls on my site, they're being transparently remapped. So you could surely match "/default" and rewrite to "/default.aspx".

However the rewrite syntax is...less than desirable and i've never written a custom rule before, sorry.

.htaccess + mod_rewrite (or maybe mod_perl if you know perl better) is what you want for now though.

---

### Post by WitchCraft on 2009-11-14
> **mrsteveman1 said:**
> Well, mod_Rewrite does appear to do mapping of that sort, i mean there isn't actually a file or url for any of the urls on my site, they're being transparently remapped. So you could surely match "/default" and rewrite to "/default.aspx".

However the rewrite syntax is...less than desirable and i've never written a custom rule before, sorry.

.htaccess + mod_rewrite (or maybe mod_perl if you know perl better) is what you want for now though.

Remapping html to php goes like that:
```

Options +FollowSymlinks
RewriteEngine on
RewriteRule ^(.*)\.htm$ $1.php [nc]

```

So I assume remapping aspx to .lol would go like this:
```

Options +FollowSymlinks
RewriteEngine on
RewriteRule ^(.*)\.aspx$ $1.lol [nc]

```

[nc] means not case sensitive.

Looks like regular expression syntax - which makes sense.

---

