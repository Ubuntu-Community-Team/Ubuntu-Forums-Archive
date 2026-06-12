---
title: "Apache2 and subdomains &quot;protection&quot;"
date: 2015-01-11
forum: Server Platforms
---

### Post by CrewDK on 2015-01-11
Well, i hope i can ask this question in this forum. :)

So, i have some VDS server with ubuntu 14.04 and Apache2 2.4.7 on board. Now I have on this VDS 1 working domain and several sub-domains for some kind of admin panels e.t.c.
For all sub-domains (existing or future) i have DNS record on hoster like: 
```
*.mysite.ru. A [IP]
```
Everything works fine, BUT anyone can try to open ANY non-existing sub-domains like blablabla.mysite.ru and it'll open! How can i "protect" my server so it'll open only existing domains and sub-domains? 

Well, for old apache 2.2.2 i had a solution, but it didn't worked for me here. 
For Apache 2.2.2 i added config "default_vhost" to my apache2.conf 

default_vhost
```
<VirtualHost *:80>
Redirect 404 /
</VirtualHost>
```

apache2.conf
```
....

# Include generic snippets of statements
Include conf.d/

Include default_vhost

# Include the virtual host configurations:
Include sites-enabled/
```

...and this way for apache 2.2.2 everything have been worked fine. But for Apache 2.4.7 this solution blocks any non-existing sub-domains AND my real existing domain! So, for example _sub.mysite.ru_ works fine, but _blablabla.mysite.ru_ and _mysite.ru_ - blocked! 

Now my default domain config looks like that: 

```
<VirtualHost *:80>
        ServerAdmin **********@gmail.com
        ServerName ***********.ru

        DocumentRoot /var/www/cms/www/
        <Directory />
                Options FollowSymLinks
                AllowOverride All
        </Directory>
        <Directory /var/www/cms/www/>
                Options FollowSymLinks MultiViews
                AllowOverride All
                Order allow,deny
                allow from all
        </Directory>

        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
        <Directory "/usr/lib/cgi-bin">
                AllowOverride All
                Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
                Order allow,deny
                Allow from all
        </Directory>

        ErrorLog /var/www/cms/logs/error.log

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn

        CustomLog /var/www/cms/logs/access.log combined

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride All
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

    Redirect 404 /favicon.ico
    <Location /favicon.ico>
       ErrorDocument 404 "No favicon"
    </Location>

<IfModule dir_module>
    DirectoryIndex  index.php index.html
</IfModule>

</VirtualHost>
```

Please help me. What i did wrong? :(

Sry for my English btw. It's not my native language and i have been learned it too many years ago :)

---

### Post by nerdtron on 2015-01-11
The DNS entry with wildcard could be wrong here since it points any subdomain (existing or non-existnig) to the IP Address of the server. Basically any subdomain resolves to the IP of the server. You need to make dns entries for each currently existing subdomain only.

---

### Post by CrewDK on 2015-01-12
Thnx for your advice. But why than it worked fine for old apache?

---

### Post by volkswagner on 2015-01-12
> **CrewDK said:**
> Thnx for your advice. But why than it worked fine for old apache?

I don't have any experience with 14.04.

The only significant changes I'm aware of are requirement to have .conf extension for vhost files.

I'm not sure if your issue is requiring mod_rewrite, which means the vhost would need to have AllowOverride enabled.
The default I believe is:

```
AllowOverride None
```

Which would need to be changed to "AllowOverride All" or something less permissive.

I would take a simple approach to creating a static "page not found" called index.html in /var/www.
Once you get expected behavior try messing with your redirect.

---

### Post by volkswagner on 2015-01-12
** duplicate post **

---

### Post by CrewDK on 2015-01-15
Thnx. But both my hosts (on new and on old apache) already has "AllowOverride All" option in their host's config. 
Or i doesn't understand your advice?

---

### Post by volkswagner on 2015-01-15
According to your original post...

This is the contents of your default_virtual host:

```
<VirtualHost *:80>
Redirect 404 /
</VirtualHost>
```

I don't see any directory reference nor any text containing "Allow".

The AllowOverride is a per host per directory stanza setting.

Perhaps you should post your entire default_host file for examination.

---

### Post by CrewDK on 2015-01-16
OK. First i want to thank you for your help. 
Here is my full hosts and configs list: 

Default domain.

cat /etc/apache2/sites-enabled/default.conf

```
<VirtualHost *:80>
        ServerAdmin crewdk@gmail.com
        ServerName school371.ru

        DocumentRoot /var/www/cms/www/
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/cms/www/>
                Options FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>

        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
        <Directory "/usr/lib/cgi-bin">
                AllowOverride None
                Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
                Order allow,deny
                Allow from all
        </Directory>

        ErrorLog /var/www/cms/logs/error.log

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn

        CustomLog /var/www/cms/logs/access.log combined

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

    Redirect 404 /favicon.ico
    <Location /favicon.ico>
       ErrorDocument 404 "No favicon"
    </Location>

<IfModule dir_module>
    DirectoryIndex  index.php index.html
</IfModule>
```

1st sub-domain.

cat /etc/apache2/sites-enabled/nod.conf

```
<VirtualHost *:80>
        ServerAdmin crew@cwork.ws
        ServerName nod.school371.ru
        DocumentRoot /var/www/nod/www/

        <Directory />
                Options all
                AllowOverride All
                Order allow,deny
                Allow from All
        </Directory>

        <Directory /var/www/nod/www/>
                Options all                                                         
                AllowOverride All                                                   
                Order allow,deny                                                    
                Allow from All                                                      
        </Directory>                                                                
                                                                                    
        ErrorLog /var/www/nod/logs/error.log                                        

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn
        CustomLog /var/www/nod/logs/access.log combined
</VirtualHost>
```

"Patch" for closing non-existing sub-domains.

cat /etc/apache2/conf-enabled/default_vhost.conf

```
<VirtualHost *:80>
Redirect 404 /
ErrorDocument 404 "Page Not Found"
</VirtualHost>
```

As I said before this working great on Apache 2.2.2 (Loading domains, sub-domains and bloking non-existing sub domains), but doesn't working on Apache 2.4.7 (loading only sub-domains, but blocking main domain and non-existing sub-domains) and i don't understand why! 

What else can I show you?

---

### Post by volkswagner on 2015-01-17
I'm sorry, but I'm not sure if you have enough info in default_vhost.conf. I thought you'd at least need
the basics like where to find the files and enable "AllowOverride" etc. If this was working in earlier versions
perhaps the function was dropped.  If the following is not the issue, I suggest following the default apache vhost template
with directory stanzas and all.

The way Apache "decides" which site to display is first check servername requested against all vhost files. If no match is found, it returns
the first alpha-numeric file in /etc/apache2/sites-enabled.

When you do:

```
ls -l /etc/apache2/sites-enabled
```
Which file comes up first? It should be the equivalent link to  /etc/apache2/sites-available/default_vhost.conf

Not /etc/apache2/sites-available/default.conf

In other words the content of /etc/apache2/sites-enabled/000-default.conf should be your redirect 404 (if in fact that limited file does have enough info for Apache to serve the 404) .

---

### Post by CrewDK on 2015-01-26
OK. Looks like i found solution. Looks like in my config i only had to add setting like: 

```
ServerName bla-bla-bla
```

Looks like all working right: i can open "main" domain (NOT default), existing sub-domain and non-existing sub-domains requests are blocking. Am I correct or I'm missing something again?

But now i have new question. I noticed that in ANY error logs there arent ANY errors. I mean that even in default error log i have just: 

```
[Mon Jan 26 16:31:10.381251 2015] [mpm_event:notice] [pid 2388:tid 140304366208896] AH00491: caught SIGTERM, shutting down
[Mon Jan 26 16:31:11.442591 2015] [mpm_event:notice] [pid 2510:tid 140714554083200] AH00489: Apache/2.4.7 (Ubuntu) configured -- resuming normal operations
[Mon Jan 26 16:31:11.442754 2015] [core:notice] [pid 2510:tid 140714554083200] AH00094: Command line: '/usr/sbin/apache2'
[Mon Jan 26 16:32:21.374693 2015] [mpm_event:notice] [pid 2510:tid 140714554083200] AH00491: caught SIGTERM, shutting down
[Mon Jan 26 16:32:22.455120 2015] [mpm_event:notice] [pid 2623:tid 140432517535616] AH00489: Apache/2.4.7 (Ubuntu) configured -- resuming normal operations
[Mon Jan 26 16:32:22.455345 2015] [core:notice] [pid 2623:tid 140432517535616] AH00094: Command line: '/usr/sbin/apache2'
```

but where are all "bad" requests errors like in old apache2? I'm saying about 

```
tail -5 ./error.log 
[Sat Jan 24 18:38:05 2015] [error] [client 37.187.252.181] script '/var/www/cms/www/admin.php' not found or unable to stat
[Mon Jan 26 11:57:10 2015] [error] [client 93.80.81.116] script '/var/www/cms/www/wp-login.php' not found or unable to stat
[Mon Jan 26 11:57:10 2015] [error] [client 93.80.81.116] File does not exist: /var/www/cms/www/administrator
[Mon Jan 26 11:57:10 2015] [error] [client 93.80.81.116] script '/var/www/cms/www/admin.php' not found or unable to stat
[Mon Jan 26 15:30:46 2015] [error] [client 95.167.186.2] File does not exist: /var/www/cms/www/askjhfbkjsadbhfksf
```

... and so on.

---

### Post by CrewDK on 2015-01-26
Started new topic for my last question. [Link]("http://ubuntuforums.org/showthread.php?t=2262688&p=13216298#post13216298")
I think it would be better.

---

