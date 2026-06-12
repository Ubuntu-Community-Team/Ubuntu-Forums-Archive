---
title: "Sub Domains sub.domain.com"
date: 2006-10-17
forum: Server Platforms
---

### Post by twistedtwig on 2006-10-17
Hi guys,

I was hoping someone would be able to point me in the right direction or tell me how to do sub domains on my server.

ie... example.com coudl have sub as a sub domain

sub.example.com

i have no idea how to do this, had a quick search and found virtual hosting with apache which is cool and something i will look into later but not what i want.

any thoughts please.

thx :)

Twiggy

---

### Post by _AA_ on 2006-10-17
<VirtualHost *:80>
        ServerName sub.domain.com
        ServerAdmin [email]email@address.com[/email]
        DocumentRoot /var/www/htdocs/sub
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

---

### Post by woorzel on 2006-10-17
hello

can you explain further what you're trying to achieve?
what is this sub-domain going to be pointing to - the same server? what services should be available on it?

---

### Post by twistedtwig on 2006-10-17
at this point i only want to have sub domains for the kids etc.  possibly one might be a wap domain nothing too exciting really

Cheers :)

Twiggy

---

### Post by _AA_ on 2006-10-17
[http://www.uplinkzero.com/apache-virtual-hosting-howto]("http://www.uplinkzero.com/apache-virtual-hosting")

There really is not much to it.

---

