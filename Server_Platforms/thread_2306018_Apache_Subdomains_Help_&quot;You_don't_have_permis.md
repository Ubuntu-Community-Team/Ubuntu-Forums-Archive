---
title: "Apache Subdomains Help &quot;You don't have permission to access /&quot;"
date: 2015-12-11
forum: Server Platforms
---

### Post by Nargren on 2015-12-11
Hi!

I have a VPS and try to set up a website there using apache. I have a domain registered ad domain.com, "mydomain.com". I wish to have 2 subdomains in addition so in total I want apache to serve: 
[LIST]
[*]mydomain.com
[*]cloud.mydomain.com
[*]wordpress.mydomain.com
[/LIST]

I  have 3 directories
[LIST]
[*]/var/www/mydomain.com
[*]/var/www/cloud.mydomain.com
[*]/var/www/wordpress.mydomain.com
[/LIST]
for the 3 sites.

As far as I understood this is done by VirtualHosts in /etc/apache2/sites-available/. (If so, then what is the use of the "subdomains" I can register and point to places at domain.com's domain central?) Here I have 3 .conf files set up for the respective 3 sites that I want to  serve, however still only "mydomain.com" is availble, the other two give me a  403 error of "You don't have permission to access / on this server" when trying to access them from my browser.

The error.log gives no warning/error that would help me to troubleshoot.

I am suspecting some kind of permission or settings error, I have tried changing directory permissions etc., but no success so far. Therefore I'd like to get some tips what may be wrong.
The /etc/apache2/sites-allowed/cloud.mydomain.com.conf is here [http://pastebin.com/pYnXaE7E ]("http://pastebin.com/pYnXaE7E")
The other subdomain has the same issue most likely, so if I can get the 2nd one to work, the 3rd one should be fine as well.

Thank you in advance!

---

### Post by darkod on 2015-12-11
And what are the permissions of /var/www/cloud.mydomain.com?

I assume you compared them to /var/www/mydomain.com?

---

### Post by Nargren on 2015-12-11
All 3 directories in /var/www have the same and were chowned to www-data
```
drwxrwxr-x 14 www-data www-data 4096 Dec 10 19:26 cloud.mydomain.com
drwxrwxr-x  7 www-data www-data 4096 Dec 10 19:52 mydomain.com
drwxrwxr-x  3 www-data www-data 4096 Dec 10 22:55 wordpress.mydomain.com
```

---

### Post by Doug S on 2015-12-11
Your cloud.mydomain.com.conf file looks odd, some hybrid of stuff that should be in /etc/apache2/apache2.conf and an ssl version and the mostly copy of the /etc/apache2/sites-available/000-default.conf version. I would focus there using [this]("https://help.ubuntu.com/lts/serverguide/httpd.html#http-configuration") reference.

---

### Post by Nargren on 2015-12-11
OK, so I removed unnecessary stuff from my cloud.mydomain.com.conf and made sure those defaults are available in either /etc/apache2/apache2.conf or /etc/apache2/sites-available/000-default.conf.
Now it looks like [URL="http://pastebin.com/GJJ0YEY9"]http://pastebin.com/GJJ0YEY9
[/URL]
No luck yet.

Another question, is the subdomain managed *_alone_* by apache virtualhosts **OR** do I have to set up something where my domain name is registered with DNS and subdomains?

---

### Post by darkod on 2015-12-11
Of course the domain and subdomains need to have correct A records in the DNS servers of that domain. Apache only does the part to open the correct page (directory root) when it receives the request from the client (browser).

Apache is not a DNS service.

---

### Post by Nargren on 2015-12-11
> **darkod said:**
> Of course the domain and subdomains need to have correct A records in the DNS servers of that domain. Apache only does the part to open the correct page (directory root) when it receives the request from the client (browser).

Apache is not a DNS service.

Ok, so on DNS subdomain entry page it says "*Subdomain Pointing Manager allows you to point a subdomain related to any subdirectory of your site*".

Doesn't this mean that I should have a /var/www/mydomain.com directory with my subdomains inside these directories? Aka, put the two subdomain directories within the main site's directory?

---

### Post by SeijiSensei on 2015-12-11
It doesn't really matter where the sites reside as long as the DocumentRoot points to the proper directory, and it has the correct permissions.  All my sites reside under /home/someuser/sites, for instance.

What does matter is that you have either an A or a CNAME record for each virtual host in your DNS.  It should look something like this:
```

[stuff]
@         IN     SOA   (stuff)
          IN     A     ip.addr.of.server
cloud     IN     A     ip.addr.of.server
wordpress IN     CNAME cloud
[stuff]

```
Because you are using domain.name as the primary identifier for the site, you need an A record at the top of DNS to point that name to the server.  The other two examples would come later and show two alternatives.  The first line uses the same A record information for cloud.domain.name; the second uses a CNAME record that identifies "wordpress.domain.name" as an alias for "cloud.domain.name".

---

### Post by Nargren on 2015-12-11
I have an A record for my main domain "mydomain.com" and in addition of this I want two additional subdomains. These should _not_  redirect back to anything else (!), but display a different site, so I  assume I don't need a CNAME right? As far as I read about that its more  like an alias.

---

### Post by Doug S on 2015-12-11
> **Nargren said:**
> I have an A record for my main domain "mydomain.com" and in addition of this I want two additional subdomains. These should _not_  redirect back to anything else (!), but display a different site, so I  assume I don't need a CNAME right? As far as I read about that its more  like an alias.Seiji, was just trying to provide a complete answer, in that you could use an A record or a  CNAME record.
Regardless, you ***must*** have them, in your case all pointing to the same IP address. Thereafter the apache web server will decide what content to deliver based on the URL and your configuration files.

---

### Post by Nargren on 2015-12-12
Thank you all for your explanations, the combined info helped me to understand how domains and virtualhosts work! I have added another A level domain for "cloud" and now apache handles it nicely. **Thanks!**

Another issue though that came up last night is that mydomain.com now actually shows a directory list by default and not the landing page stored in /var/www/mydomain.com. If I want to reach the "main landing page" I have to go to mydomain.com/mydomain.com (domain name + directory)
However, the DocumentRoot is still /var/www as previously and apache should serve the contents of the directory /var/www/mydomain.com as previously. I am not sure what has changed.

If I have not touched the virtualhosts conf file for the "main landing page", shouldn't it still be served first?

Actually, I have a letsencrypt certificate so mydomain.com so far redirected to https:/ /mydomain.com. It doesn't do this any more, but typing https:// mydomain.com still gives access.

---

### Post by Nargren on 2015-12-12
Ok, so I'm not sureif it is the right solution, but I worked around the issue by adding to /etc/apache/sites-available/000-default.conf the following:
```
#### Redirect to port 443 ###
RewriteEngine on
ReWriteCond %{SERVER_PORT} !^443$
RewriteRule ^/(.*) https://%{HTTP_HOST}/$1 [NC,R,L]
#### End of Redirection configuration ###
```

Now it works.
Subdomains redirect to subdomains, and mydomain.com actually calls https:// mydomain.com, which does redirect properly to the directory /var/www/mydomain.com.

Is there perhaps a better way to do it? Aka, have all traffic go to mydomain.com get redirected by apache to the proper directory?

---

