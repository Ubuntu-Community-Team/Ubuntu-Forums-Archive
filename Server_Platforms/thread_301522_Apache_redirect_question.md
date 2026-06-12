---
title: "Apache redirect question"
date: 2006-11-17
forum: Server Platforms
---

### Post by hagen00 on 2006-11-17
Hello

I'm having problems redirecting with apache2. 

I'm wanting that if people type in [http://mysite.com](http://mysite.com) that it redirects them to [http://www.mysite.com](http://www.mysite.com)

I've got the following into my virtual host:

ServerName [www.mysite.com](www.mysite.com)
ServerAlias mysite.com
Redirect 301 / [http://www.mysite.com/](http://www.mysite.com/)

But when I restart apache and try and load the page it doesn't come up. No errors, but it doesn't load. It's like it's trying to load but failing. 

Do I need to post other parts of my virtual host? What am I doing wrong. This should be simple. 

Help appreciated. 

H

---

### Post by twistedtwig on 2006-11-17
the way i did it was with Cname's set up with my dynamic dns provider.  requests for both example.com and [www.example.com](www.example.com) get sent to example.com.

I dont think you need to use virtual hosts for this.  

can you ping both of them? are they resolving to the right IP? if so then you know its at your server, if not then you need to set something up so it the dns servers know where to look

Twiggy

---

### Post by hagen00 on 2006-11-17
Hi Twiggy

I can ping both of them and both resolving properly. The thing is that currently [http://mysite.com](http://mysite.com) works and [http://www.mysite.com](http://www.mysite.com). However I don't want that, i want that for [http://mysite.com](http://mysite.com) that the URL rewrites to [http://www.mysite.com](http://www.mysite.com). 

This is for SEO purposes (Google does it like that). I don't want Google thinking I've got two sites with duplicate content. 

I also don't for the moment want to use mod_rewrite since it seems so much simpler just to use Redirect (if it would only work). 

H

---

### Post by twistedtwig on 2006-11-17
ok ic.. here is an example of my host file.. well not all of it but should hopefully show you what you need i think

> <VirtualHost *>
ServerName ponywars.com
ServerAdmin [email]admin@ponywars.com[/email]
DocumentRoot /var/www/root
<Directory />
Options FollowSymLinks
AllowOverride None
</Directory>

ErrorLog /var/log/apache2/error.log

# Possible values include: debug, info, notice, warn, error, crit,
# alert, emerg.
LogLevel warn

CustomLog /var/log/apache2/access.log combined
ServerSignature On
</VirtualHost>

######## charlottes own home page #############

<VirtualHost *>
ServerName charlotte.ponywars.com
ServerAdmin [email]admin@ponywars.com[/email]
DocumentRoot /var/www/charlotte
<Directory />
Options FollowSymLinks
AllowOverride None
</Directory>

ErrorLog /var/log/apache2/error.log

# Possible values include: debug, info, notice, warn, error, crit,
# alert, emerg.
LogLevel warn

CustomLog /var/log/apache2/access.log combined
ServerSignature On
</VirtualHost>


i think you would need to host files.. your default then copy it and add "www." infront of the server name.

think that shoudl work but there are far better people out there at this than me.. hope it helps

Twiggy

---

### Post by MJN on 2006-11-17
Go for mod_rewrite, it's perfect for this situation (and more besides). For this case, use:
 
```
RewriteEngine On
RewriteCond %{HTTP_HOST} !^www\.mysite\.com
RewriteRule ^/(.*) [http://www.mysite.com/$1](http://www.mysite.com/$1) [R=301,L]
```This will also work for any sub-folders/files of the domain URL (i.e. preserving the path).
 
Your initial solution was rather cyclical i.e. given it was non-conditional then it would keep redirecting to itself!
 
Mathew

---

### Post by hagen00 on 2006-11-17
Thanks Twiggy, but that doesn't really help. 

I wondering if there is something conflicting with my Redirect call. 

My <Directory> tag has 
Options Includes, FollowSymlinks, Multiviews
AllowOverride All
Order allow,deny
Allow from all

Pretty standard I think. 

Stumped.

---

### Post by twistedtwig on 2006-11-17
Hey Mathew,

how / where do you use that?  looks cool though.. so it take anything not like [www.mysite.com](www.mysite.com) and redirects to full url?

always the man with the plan :D

---

### Post by MJN on 2006-11-17
That's right - just stick it inside your VirtualHost container. Note that you'll need the mod_rewrite module installed.
 
Mathew

---

### Post by hagen00 on 2006-11-17
I think the problem might be this...

I call this 
Redirect 301 / [http://www.mysite.com/](http://www.mysite.com/)

And that then goes to the same virtual host and tries to call
Redirect 301 / [http://www.mysite.com](http://www.mysite.com) again

Which causes an infinite loop. Correct? If this is right, how do i stop this from happening?

---

### Post by hagen00 on 2006-11-17
Mathew...thanks, didn't see your reply before my post above. 

You said exactly what I assumed in my post above. It's cyclical. Anyway to prevent that without using mod_rewrite. 

Suppose I can use mod_rewrite, just seems like overkill. If no one can tell me how to do it with Redirect, I'll be using that mod_rewrite rule you posted there...thanks for that.

---

### Post by MJN on 2006-11-17
That's right... are you missing my posts? (I already pointed it out! ;))
 
As mentioned, your redirect rule needs to be conditional if you're treating both names within the same Virtualhost container. Here, mod_rewrite is your friend!
 
Mathew

---

### Post by MJN on 2006-11-17
We both ought to slow down... keep posting at the same time!
 
Why do you not want to use mod_rewrite? It's pretty much the standard solution to this sort of problem.
 
Mathew

---

### Post by hagen00 on 2006-11-17
hehe, sorry for missing your posts...i definitely need to slow down. 

Ok, so mod_rewrite it will be. I already have some sites that use mod_rewrite, so I'll have to modify your rule to not have a L (which i believe means if match no further processing).

Thanks mate. 

H

---

### Post by hagen00 on 2006-11-17
Ok, the rules from Mathew didn't work out of the box for me. Had to add a line. The below worked...It especially needed that second rewrite condition. 
   RewriteEngine On
   RewriteCond %{HTTP_HOST} !^www\.mysite\.co\.za [NC]
   RewriteCond %{HTTP_HOST} !^$
  RewriteRule ^.*$ http://www.mysite.co.za/$1 [R=301]

---

### Post by MJN on 2006-11-17
Out of interest, what was happening with my code? (I suspect it may have been the absence of the **RewriteEngine On** directive - I forgot that the module needs activating with this on a per-VirtualHost basis.)

Mathew

---

### Post by hagen00 on 2006-11-20
Hi Mathew

No, I did have RewriteEngine On set with your code. However it didn't rewrite. It's like it ignored the rule, so I'm suspecting there was an error in the conditions, possibly the absence of that second condition I put down. 

H

---

### Post by MJN on 2006-11-20
Works fine here!

Ho hum... at least you're sorted!

Mathew

---

### Post by hagen00 on 2006-11-21
Yeah, sorted..thanks to you. 

Cheers

---

