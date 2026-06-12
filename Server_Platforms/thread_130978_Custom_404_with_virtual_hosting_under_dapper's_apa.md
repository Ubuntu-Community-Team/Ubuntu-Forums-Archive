---
title: "Custom 404 with virtual hosting under dapper's apache 2 config"
date: 2006-02-15
forum: Server Platforms
---

### Post by siefkencp on 2006-02-15
I've been looking i haven't found anything yet so I thought I'd ask... How do I set one up for just a particular virtual host under the site.conf ?

Thanks in advance
Chris

---

### Post by jinacio on 2006-02-16
i think it's as easy as adding the ErrorDocument directives to your virtualhost section:

```

<VirtualHost *>
  DocumentRoot /home/example/public_html
  ServerName example.com
  ServerAlias www.example.com
  ServerAdmin webmaster@example.com
  ErrorLog /home/example/logs/error_log
  CustomLog /home/example/logs/access_log common
  # other possible settings
  ...
  # now add the ErrorDocument directives
  ErrorDocument 403 /403.html
  ErrorDocument 404 /404.html
</VirtualHost>


```

---

### Post by siefkencp on 2006-02-16
You are correct, however now I have a different problem... Internet explorer does not pick up the error page, it simply just does it's IE thing and displays what it wants to for the 404.  :confused: 

Any ideas on this? Ideally I want to run a PHP script which examines what was typed in to get the 404 and redirect from there.

---

### Post by jinacio on 2006-02-16
hmm that works for me...

remember, ErrorDocument is relative to your virtualserver document root, so in my previous example you would need to have a file "404.html" in "/home/example/public_html"

edit: not tested with IE but it *should* work for all browsers

---

### Post by siefkencp on 2006-02-16
It works great in Firefox--- exactly as expected, IE gives me it's own message not the one i'm pointing too.... 

My path is set as you pointed out.

---

### Post by ExMachina on 2006-08-01
IE does that. Its has a default 404 message ti alwasy displays. Not sure why.

So were in apache2.conf do you put the virtual stuff?

---

### Post by dwapple on 2006-08-16
> **siefkencp said:**
> Internet explorer does not pick up the error page, it simply just does it's IE thing and displays what it wants to for the 404.  :confused: 
> **ExMachina said:**
> IE does that. Its has a default 404 message ti alwasy displays. Not sure why.

I think it has something to do with the page size. If i'm not mistaken, IE replaces error pages less than 512 bytes with it's own stupid page. Try putting a few more lines in the source.

---

