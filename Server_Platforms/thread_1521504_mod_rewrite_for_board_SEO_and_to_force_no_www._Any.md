---
title: "mod_rewrite for board SEO and to force no www. Any tips?"
date: 2010-06-30
forum: Server Platforms
---

### Post by theRick on 2010-06-30
I used to use the following code on my website to force all traffic to use no www in the URL.

```
RewriteEngine On
RewriteCond %{HTTP_HOST} ^www.ncaastrategies\.com$
RewriteRule ^(.*)$ http://ncaastrategies.com/$1 [R=301,L]
```

ipBoard calls for me to add the following information to my .htaccess file.

```
<IfModule mod_rewrite.c>
Options -MultiViews
RewriteEngine On
RewriteBase /utopia/
RewriteCond %{REQUEST_FILENAME} !-f
RewriteCond %{REQUEST_FILENAME} !-d
RewriteRule . /utopia/index.php [L]
</IfModule>

```

Using both snippets in my .htaccess file like so does not provide the result I would hope for. Instead of redirecting to the same URL minus the www - it instead redirects to the forum directory.

```
<IfModule mod_rewrite.c>
Options -MultiViews
RewriteEngine On
RewriteBase /utopia/
RewriteCond %{REQUEST_FILENAME} !-f
RewriteCond %{REQUEST_FILENAME} !-d
RewriteRule . /utopia/index.php [L]
</IfModule>

RewriteEngine On
RewriteCond %{HTTP_HOST} ^www.ncaastrategies\.com$
RewriteRule ^(.*)$ http://ncaastrategies.com/$1 [R=301,L]
```

Could someone please help me in making it so that the ipBoard rule works in tandem with a no www redirect?

Thanks!

---

### Post by Ryan Dwyer on 2010-07-01
Try this:

```

<IfModule mod_rewrite.c>
Options -MultiViews
RewriteEngine On

RewriteCond %{HTTP_HOST} ^www.ncaastrategies\.com$
RewriteRule ^(.*)$ http://ncaastrategies.com/$1 [R=301,L]

RewriteBase /utopia/
RewriteCond %{REQUEST_FILENAME} !-f
RewriteCond %{REQUEST_FILENAME} !-d
RewriteRule . /utopia/index.php [L]
</IfModule>

```

---

### Post by theRick on 2010-07-01
Perfect. Thank you, sir.

---

### Post by theRick on 2010-07-03
This fix worked perfectly, thank you again for that. I have one sub-directory though that requires its own rule per my ipBoard setup.

```
<IfModule mod_rewrite.c>
RewriteEngine On
RewriteBase /portal
RewriteCond %{REQUEST_FILENAME} !-f
RewriteCond %{REQUEST_FILENAME} !-d
RewriteRule . /portal/index.php [L]
</IfModule>
```

I tried the following...

```
<IfModule mod_rewrite.c>
RewriteEngine On
RewriteBase /portal

RewriteCond %{HTTP_HOST} ^www.ncaastrategies\.com$
RewriteRule ^(.*)$ http://ncaastrategies.com/$1 [R=301,L]

RewriteCond %{REQUEST_FILENAME} !-f
RewriteCond %{REQUEST_FILENAME} !-d
RewriteRule . /portal/index.php [L]
</IfModule>
```

Copying the example above. But that did not work.

Unfortunately it seems I still don't quite understand exactly what the fix did.

May I get some help in getting this final directory running?

Thanks in advance!

---

### Post by Ryan Dwyer on 2010-07-03
Move RewriteBase below the first rule, like this:

```

<IfModule mod_rewrite.c>
RewriteEngine On

RewriteCond %{HTTP_HOST} ^www.ncaastrategies\.com$
RewriteRule ^(.*)$ http://ncaastrategies.com/$1 [R=301,L]

RewriteBase /portal
RewriteCond %{REQUEST_FILENAME} !-f
RewriteCond %{REQUEST_FILENAME} !-d
RewriteRule . /portal/index.php [L]
</IfModule>

```

In the first fix, it was about the order of the rules. The first rule (with REQUEST_FILENAME in the conditions) will redirect to /utopia/index.php if the file they asked for doesn't exist. The [L] in that rule (L = last) means if the rule matches, it will not process any more rewrites.

---

