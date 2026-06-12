---
title: "Subdomains problem - easy"
date: 2008-10-07
forum: Server Platforms
---

### Post by wattaman on 2008-10-07
So, I've added the *easy *word because I think is easy to fix - by someone who knows a little linux.
K. That's the problem: my subdomains refuses to display anymore; in browser, I mean. I got only > Navigation to the webpage was canceled on all of them.
Now, all the new subdomains I create are working just fine (that's why I believe is easy to fix).
So, in the etc/apache2/ all the subdomains config files looks like:
> <VirtualHost 123.123.123.123.:80>
SuexecUserGroup "#1001" "#1002"
ServerName sub.domain.com
ServerAlias [www.sub.domain.com](www.sub.domain.com)
ServerAlias webmail.sub.domain.com
ServerAlias admin.sub.domain.com
DocumentRoot /home/username/domains/sub.domain.com/public_html
ErrorLog /home/username/domains/sub.domain.com/logs/error_log
CustomLog /home/username/domains/sub.domain.com/logs/access_log combined
ScriptAlias /cgi-bin/ /home/username/domains/sub.domain.com/cgi-bin/
DirectoryIndex index.html index.htm index.php index.php4 index.php5
<Directory /home/username/domains/sub.domain.com/public_html>
Options -Indexes IncludesNOEXEC FollowSymLinks
allow from all
AllowOverride All
</Directory>
<Directory /home/username/domains/sub.domain.com/cgi-bin>
allow from all
</Directory>
RewriteEngine on
RewriteCond %{HTTP_HOST} =webmail.sub.domain.com
RewriteRule ^(.*) [http://sub.domain.com:20000/](http://sub.domain.com:20000/) [R]
RewriteCond %{HTTP_HOST} =admin.sub.domain.com
RewriteRule ^(.*) [https://sub.domain.com:10000/](https://sub.domain.com:10000/) [R]
</VirtualHost>


I suppose I could delete the subdomains and create them again to work. However, I'd like to understand the issue just in case will happen again.
_So, what can I do to fix this?_ (*please explain in asy terms, don't know much linux*)
_Is there any sollution or I must delete them after all?_
I have Ubuntu 8.04, created domains in virtualmin and now I'm hosting 2 domains - on both of them the subdomains are not working.
Thanks for your help!

You know, the funny thing is that I don't remember anything that could cause this problem :)

---

### Post by alastair on 2008-10-07
> Navigation to the webpage was canceled 

Browser errors are one thing - but what error does the web server see? Perhaps more important and helpful.

Where are the web server logs?

And what appears in them when you see a browser error like above?

Cheers,

Alastair

---

### Post by MJN on 2008-10-07
Don't hide your true domain name(s). Chances are that's where you've screwed up and if we can't see the raw config files we could end up wasting our time trying to work out what's wrong.

If you don't want the whole world seeing your website(s) then put appropriate access controls in place, don't obfuscate the name as it is not providing you with any real security.

Mathew

---

### Post by wattaman on 2008-10-08
alastair: the subdomain error logs only show only styff like: favicon is missing, link is missing etc. Nothing special.
MJN: didn't knew how important is for you, guys, I was concerned not to spam the forum with links.
Anyway, now one of the subdomains is working (I didn't do nothing, btw) and all the others are not.
MJN, if you that's not much to ask you can see them at bx.atat.ro (*easybanner script*- working) and top.atat.ro (*aardvark script* - not working). OThe main domain is, like I've said, working fine... unless I'm not changing something to the site when you'll visit it.
Thanks for the support!

---

### Post by wattaman on 2008-10-09
I've deleted yesterday two virtual servers (from virtualmin) and rebuild them and they worked.
Now I've noticed that, again, none of the subdomains are working.
Not even those that worked yesterday.
I guess I'll have to create them everyday, lol.

---

### Post by wattaman on 2008-10-15
I've just made another discovery: though the subdomains are not opening the site, just the > Navigation to the webpage was canceled message, if I use proxy.org to browse them, then they show up. And sometimes, after I open them in proxy.org they also open normally (othertimes they still don't).
How is this possible and most important, how to fox it?
I still believe it might be something wrong with the server configuration, but I don't know what can it be. I thought is the ISP, first, but then why the domains are working all the time? Only the subdomains don't show to me.

---

