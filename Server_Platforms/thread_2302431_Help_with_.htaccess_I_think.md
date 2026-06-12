---
title: "Help with .htaccess I think"
date: 2015-11-10
forum: Server Platforms
---

### Post by Mike_Ramsey on 2015-11-10
So I have my server up and it has been going for a few years. I use it for a learning / experimenting environment.  I have my web directory set up similar to this:

var/www/[INDENT=2]mysite.com
[/INDENT]
[INDENT=3]sitefiles[/INDENT]
[INDENT=2]sub-domain[/INDENT]
[INDENT=3]sub-domain files[/INDENT]
[INDENT=2]other directory[/INDENT]
[INDENT=3]other directory files
[/INDENT]

I have the site configuration pointing to the document root of /var/www/mysite.com

What I am trying to do is use [http://www.mysite.com/other](http://www.mysite.com/other) directory so I can use my domain name to still navigate to other sub-directories of the root www directory. It really has been a couple of years of experimentation etc and I actually just bought a real domain name so things are kind of a mess but rather than start over I would like to at least try to get it re worked. i think it needs to be done via htaccess but i could be wrong.

---

### Post by SeijiSensei on 2015-11-10
The .htaccess file is disabled by default.  If you have control over the service, you should put any directives you would use in an .htaccess file in a <Directory> container in the .conf file for the virtual host.

So can you see the /sub-domain URI but not /other?  Is /var/www/other readable by the www-data user? What do you see in /var/log/apache2/access.log and error.org when you try to connect to the /other URI?

---

### Post by Mike_Ramsey on 2015-11-13
> **SeijiSensei said:**
> The .htaccess file is disabled by default.  If you have control over the service, you should put any directives you would use in an .htaccess file in a <Directory> container in the .conf file for the virtual host.

So can you see the /sub-domain URI but not /other?  Is /var/www/other readable by the www-data user? What do you see in /var/log/apache2/access.log and error.org when you try to connect to the /other URI?

Sorry for the delayed reply its been a busy week.  When I set the document root of the  virtual host on :80 to /var/www/mysite the site works but I lose access to the root www directories. When I set the document root back to /var/www then it works as it always has. The other directories are all readable to the www-data user. I am just looking for a way to specify what directory the home page is located in but retain the navigation to the other directories.

What directives should I use in the .conf file? I think that is what I am missing.

---

### Post by SeijiSensei on 2015-11-13
I'm not sure I really understand your problem.

If you set the DocumentRoot to /var/www/mysite, then you will not be able to see /var/www from [www.mysite.com](www.mysite.com).   That's how things should be so your server isn't open to browsing of directories outside the root.

It sounds to me like you are trying to support multiple virtual hosts with one configuration file.  While that's possible, the Ubuntu default is to put a separate .conf for each virtual host in /etc/apache2/sites-available/ and "activate" them with "sudo a2ensite sitename" where "sitename" matches the name of a conf file.  In each file you would have separate ServerName and DocumentRoot directives.  So the "mysite.com" file would have
```

ServerName      www.mysite.com
DocumentRoot   /var/www/mysite
<Directory "/var/www/mysite">
     Options +Indexes FollowSymLinks
</Directory>

```
with the content of what you would have placed in .htaccess inside the <Directory> stanza.  If you call this file "mysite.conf" you would then use "sudo a2ensite mysite" to activate it.  Similarly if you now have a new domain name, "example.com," you would have another .conf file with
```

ServerName     www.example.com
DocumentRoot  /var/www/example
[etc.]

```

Does that make things clearer?

---

### Post by Mike_Ramsey on 2015-11-14
Sort of.  I am using multiple Vhosts and only one domain however  i have one for :80, :443, and two sub-domains. Currently I only have single index page in my root www directory with a whole bunch of other directories in the root www directory. One of those directories is mysite.com which I want as the home page. i can get that working just fine. From my web browser [www.mysite.com](www.mysite.com) works as it should as do subdomain.mysite.com sites. the problem is that some of the other directories that are in the root www directory are not sub domiains but they are still directories that I would like to access from [www.mysite.com/otherdirectories](www.mysite.com/otherdirectories).

So for example if I browse to [www.mysite.com/test](www.mysite.com/test) it would have to redirect to the var/www/test directory because test does not exist within /var/www/mysite.com.  I know it can be done but the difficulty i am having articulating the issue is obviously why my searches were fruitless.

---

### Post by SeijiSensei on 2015-11-14
Use an [alias]("https://httpd.apache.org/docs/2.4/mod/mod_alias.html") in the VirtualHost specification:
```

ServerName     www.mysite.com
DirectoryRoot  /var/www/mysite

Alias  /otherdirectory  /var/www/otherdirectory
[etc.]

```

You may need a <Directory "/var/www/otherdirectory"> stanza as well.

These directories need not reside under /var/www as long as the www-data user has read privileges to the aliased directory.

---

