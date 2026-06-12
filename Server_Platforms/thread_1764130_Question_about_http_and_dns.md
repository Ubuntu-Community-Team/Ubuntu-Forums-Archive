---
title: "Question about http and dns"
date: 2011-05-21
forum: Server Platforms
---

### Post by tapi0n on 2011-05-21
Good afternoon,

Now first of all let me say this is for a project at school. I know you're not supposed to help people with homework. But I don't want help since It's already done (so it seems, more about this later on) I just need some help to clarify some things.

First let me give a small idea of what's going on.

For our course system administration we need to set up a server on which we have to reach different 'milestones'. For example configuring ssh correctly, dns, http, https ... There is one central website where we can check our progress. This server runs cronjobs every 5 minutes to see if we completed the milestones required. On the website of this server there is a summary of every person taking the course, followed by V's or X's to tell if we completed a milestone.

I hope I didn't lose you so far.

Ok, carrying on. So one of these milestones is HTTP (apache2). For this milestone to receive a V on the checkpage we had to set up the following:

```
-A default web page showing 'welcome' when accessing www.sub.domain.tld
- A virtual host for www1.sub.domain.tld displaying 'www1' instead of 'welcome'
- A vritual host for www2.sub.domain.tld with a php page (I won't go into that)
- And a folder in the www1 subdomain which needs basic authentication with htacces
```Now after configuring all these steps and restarting everything required (apache and bind) I head over to the check page and see a nice green V under the http. Telling me I've completed this milestone and I can continue to the next one.

I can browse to [www.sub.domain.tld]("http://www.sub.domain.tld"). But when browsing to either www1.sub.domain.tld or www2.sub.domain.tld  I get a 'Server not found' message.

This is my entire httpd.conf

```
<VirtualHost *:80>
DocumentRoot /var/www/www
ServerName www.sub.domain.tld
</VirtualHost>

<VirtualHost *:80>
DocumentRoot /var/www/www1
ServerName www1.sub.domain.tld
</VirtualHost>

<VirtualHost *:80>
DocumentRoot /var/www/www2
ServerName www2.sub.domain.tld
</VirtualHost>
```and this is my entire db.sub.domain.tld which is the file mentioned in the named.conf.local file:
```

$TTL 1H
@        IN    SOA    ns.sub.domain.tld. root.sub.domain.tld. (
                2011051802    ;serial
                1H        ;refresh
                1H
                1H        ;expire
                1H)        ;minimum ttl

            NS    ns
            NS    ns.domain.be.

ns        IN    A    xxx.xxx.xxx.xxx
www        IN    CNAME    ns
www1        IN    CNAME     ns
www2        IN    CNAME     ns
test        IN     A    xxx.xxx.xxx.xxx (different ip then the one in ns)

```Now, when browsing to the site of a friend of mine (also taking the course) I can get to the www1 and www2 subdomain.

I know I overlooked something, but for the love of whatever is holy I can't figure it out.

Anyone who knows what I may be overlooking? 

Cheers,

A little ps. If by any chance I am violating the code of conduct (which I don't think I am because I already completed the milestone) please do tell. But I'm seriously lost on the subject and although I got this awesome V on the check site, I just can't get myself to start the next milestone without knowing what's wrong with this one.


EDIT: found out what was wrong, seems I forgot to update the serial in my dns record :)

---

