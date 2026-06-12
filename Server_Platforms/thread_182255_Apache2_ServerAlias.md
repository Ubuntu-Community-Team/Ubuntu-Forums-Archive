---
title: "Apache2 ServerAlias"
date: 2006-05-25
forum: Server Platforms
---

### Post by el3ktro on 2006-05-25
Hello,

I've setup an apache server with multile domain, each domain has it's own file in sites-enabled directory. Such a file looks like this:

<VirtualHost *:80>
        ServerName      [www.mydomain.de](www.mydomain.de)
        DocumentRoot    /data/www/mydomain.de/htdocs
        CustomLog       /data/www/mydomain.de/log/access.log combined
        RewriteEngine on
        rewriteRule "^/statistik/?" /awstats/awstats.pl [L,R]
</VirtualHost>

This works fine, but I want to add a ServerAlias so that I can reach my site also with mydomain.de instead of [www.mydomain.de](www.mydomain.de) (I hate this www in front of it and never type it usually). But when I add such a ServerAlias, I can't reach the site anymore, instead it displays some of my other websites. Can anybody help me with this?

Tom

---

### Post by MJN on 2006-05-26
Do your other sites respond correctly by name?
 
What exactly happens when you put **ServerAlias mydomain.de** in? Can you still access the site by [www.mydomain.de]("http://www.mydomain.de")?
 
Presumably mydomain.de is not your actual domain? If so, why munge your real one? If you left it exactly as written, and included your other domains, then we can help fault-find - altering domains just makes the whole process nothing more than guesswork. If these sites are connected to the Internet then you've got nothing to hide by mentioning them!
 
You say your files are in sites-enabled, are they not actually in sites-available (and symlinked)? What are your filenames? Do you have the **NameVirtualHost *:80** directive in apache2.conf?
 
Mathew

---

### Post by el3ktro on 2006-05-26
[QUOTE=MJN]Do your other sites respond correctly by name?
 
What exactly happens when you put **ServerAlias mydomain.de** in? Can you still access the site by [www.mydomain.de]("http://www.mydomain.de")?
 
Presumably mydomain.de is not your actual domain? If so, why munge your real one? If you left it exactly as written, and included your other domains, then we can help fault-find - altering domains just makes the whole process nothing more than guesswork. If these sites are connected to the Internet then you've got nothing to hide by mentioning them!
 
You say your files are in sites-enabled, are they not actually in sites-available (and symlinked)? What are your filenames? Do you have the **NameVirtualHost *:80** directive in apache2.conf?
 
Mathew[/QUOTE]

Hmm I'm a bit stumpled now because I just tried it again and now it works. I have now 

ServerName mydomain.de
ServerAlias [www.mydomain.de](www.mydomain.de) [www.otherdomainforsamesite.de](www.otherdomainforsamesite.de)

This works. I've moved the NameVirtualHost which was in one of these files in sites-enabled (in sites-avaiable actually and symlinked) to apache2.conf.

Hmm now when I enter a domain which I have no file for, e.g. xyz.mydomain.de, then Apache shows the alphabetically first domain in sites-enabled, is that correct?

Tom

---

### Post by MJN on 2006-05-26
It is indeed correct - the 'default' site is as, you've discovered, the first file in sites-enabled. This is why the out-of-the-box configuration has the file **000-default** in sites-enabled (pointing to the default site) as this makes sure it goes first (unless you went and put 0000-default in there ;))
 
As you may have guessed, if you just put in your IP address (i.e. no name) to your browser then you will also get the 'default' site.
 
Mathew
 
P.S. Stop quoting other people's domains in your config - if you don't want to put yours in then why is it right to put in someone's elses?! (I'm talking about 'mydomain' specifically).

---

### Post by el3ktro on 2006-05-26
> **MJN]It is indeed correct - the 'default' site is as, you've discovered, the first file in sites-enabled. This is why the out-of-the-box configuration has the file **000-default** in sites-enabled (pointing to the default site) as this makes sure it goes first (unless you went and put 0000-default in there  said:**
> www.newtonnet.co.uk/anon[/URL]) to see why there's no point)

Ok thanks now everythings crystal-clear to me :-) Hmm another question though ... I've read about mod-deflate recently, how can I enable this? I didn't find a package with apt-cache ...

Tom

---

### Post by MJN on 2006-05-26
I'm afraid I'm not familiar with that module - sorry.
 
Mathew

---

### Post by el3ktro on 2006-05-26
[QUOTE=MJN]I'm afraid I'm not familiar with that module - sorry.
 
Mathew[/QUOTE]

I'll google for it then ... thanks anyway!

Tom

---

