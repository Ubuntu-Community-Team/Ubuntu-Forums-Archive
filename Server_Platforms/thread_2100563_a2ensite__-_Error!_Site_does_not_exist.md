---
title: "a2ensite  - Error! Site does not exist"
date: 2013-01-02
forum: Server Platforms
---

### Post by Toriku on 2013-01-02
when I run a2ensite with "a2ensite www.example.com"I get the error

> ERROR: Site [www.example.com](www.example.com) does not exist!


I've added a file in the sites-enabled folder in /etc/apache2/sitesenabled
I've added a site in /var/www/www.example.com/

I've even tried running a2ensite in each of the folders...
running a2ensite and pointing it to the file in the enabled-sites folder
> a2ensite /etc/apache2/sites-enabled/www.example.com

gives the error:
> ERROR: No site found matching /etc/apache2/sites-enabled/www.example.com!


This is my [www.example.com](www.example.com) file in sites-enabled:
> 
<VirtualHost *>
        ServerAdmin [email]webmaster@example.com[/email]
        ServerName  [www.example.com](www.example.com)
        ServerAlias example.com

        # Indexes + Directory Root.
        DirectoryIndex index.html
        DocumentRoot /var/www/www.example.com/
</VirtualHost>


Where have I gone wrong?

---

### Post by lisati on 2013-01-02
I believe that /etc/apache2/sites-available is the default for containing the relevant configuration files, and then a2ensite creates the proper link/files in /etc/apache2/sites-enabled

---

### Post by Toriku on 2013-01-02
I just tried moving it over and running it again, but I get the same error

---

### Post by volkswagner on 2013-01-02
What is the output of the following:

```
ls -l /etc/apache2/sites-available
```

If you have a file called "www.example.com", then simply run:

```
sudo a2ensite www.example.com
```

You should not need to point a2ensite at the entire directory tree, Apache2 will specifically look in /etc/apache2/sites-available.

---

### Post by dapleh on 2013-08-06
I know this thread is a little bit older...

but I had the same problem and came to this place. Renaming the file to example.conf did the job for me; so the .conf extension seemed to be necessary...

---

### Post by DarkDisaster on 2013-10-18
> **dapleh said:**
> I know this thread is a little bit older...

but I had the same problem and came to this place. Renaming the file to example.conf did the job for me; so the .conf extension seemed to be necessary...

Never too old, thanks :)

---

### Post by SeijiSensei on 2013-10-18
That's because the files in sites-enabled are included in the configuration by this directive in /etc/apache2/apache2.conf:

```

# Include the virtual host configurations:
IncludeOptional sites-enabled/*.conf

```

It only reads files matching *.conf.

---

### Post by cppege-david-9ei9ny on 2013-11-25
This seems to be quite a recent change in Ubuntu and caused me quite a bit of head-scratching. If you are on 12.10 then the virtual host file does not have to end in .conf but by 13.10 it does.

---

### Post by Warren_Parker on 2014-05-24
I kinda feel compelled to make mention of this because I have been helped by this thread on more than one occasion.

It's May 2014 and Ubuntu 14.04 has been out for a little while.  Navigate to /etc/apache2/sites-available and see what's there.  In the past the default website file has just been named "default" while later it was "default.conf" yet now it is "000-default.conf."  

"sudo a2dissite 000-default.conf" disables the default web site, allowing you to promote another one in its place.

Hope this helps!

Warren

---

### Post by stratoscape on 2014-06-12
> **Warren_Parker said:**
> 
"sudo a2dissite 000-default.conf" disables the default web site, allowing you to promote another one in its place.


Thank you for leaving this update, everyone left "000-" part out of the instructions (...ugh)
I also needed to add the .conf extension to promote the other site that I replaced it with "sudo a2ensite exampleAltSite.conf"

thanks for posting this

---

