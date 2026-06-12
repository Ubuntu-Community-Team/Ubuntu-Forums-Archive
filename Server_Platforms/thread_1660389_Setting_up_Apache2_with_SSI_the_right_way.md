---
title: "Setting up Apache2 with SSI the *right* way"
date: 2011-01-05
forum: Server Platforms
---

### Post by overmonk on 2011-01-05
So I've got a box running 10.04LTS Server, and on it is running the latest build of Apache2.  

It's a home box - a server set up for the sole purpose of experimenting and having fun with.  So far, the fun is mostly breaking it over SSH and then fixing it when I get home and can log into it via recovery.  Whee.  (no, it's still fun, just frustrating)

Anyhow.

What I really want to do is to get this box set up with Apache2 the way it seems like it was designed - with Apache2 serving web pages from its default file location (/var/www) but also being able to log in and upload/download new web page files to that directory over SCP or SFTP.  I keep hitting snags.

Here's what I've done so far:
1.  The server is set up in a DMZ at home and my router updates a Dynamic DNS record; so far I can SSH into it no problem.

2.  Apache is working.  I get my "it works!" page when I enter either the IP or the dyndns domain name.

3.  SFTP is sort of working.  I can log on using WinSCP and see the files and download them, but I can't upload to the default directory with my normal login.

Here's my issues:
1.  I want to set up Apache *correctly*.  To me, that means leaving it pointing to the default directory, but still being able to upload to that directory.  I have not (and probably will not) enable the root account.  I've set the permissions to 755.  I've tried chown'ing the directory, but then it seems I can't view the webpages.

As a workaround, I created a www folder in my default user home directory and pointed Apache2 there in the 'default' file in /etc/apache2/sites-available.  The changes read as follows: 

```
        DocumentRoot /home/username/www
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /home/username/www/>
                Options Indexes FollowSymLinks MultiViews Includes
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>
```

That gives me a workaround for the default directory SFTP issue, but I would rather learn what I need to do to have it set up and working with default values.

2.  You may notice I added Includes under the Options.  My goal is to get server-side includes working.  But they aren't.  I have some existing webpages my work has set up - I using these as a template to use to adapt a flash movie I made to a specific resolution, as well as to learn how to optimize my flash for a webpage.  Our webhost uses virtual hosting; I am not yet doing so.  I'm not sure what they've done to set up the server-side includes, but the files they are using are all html files - no shtml.  The include files themselves have either .htm or .html extensions.  All of the pages have .html extensions.

My reading said that I need mod_include installed in Apache2.  Where can I check to see that it is installed?  Where do I need to add the Includes under Options?  Is it in the right place?  And finally, where do I need to add XBitHack on to enable it?  This is the method that Apache suggests, but the documentation offers no clue as to where to put it.  Most of the documentation out there refers to apache.conf, but that's the Apache 1.3 way of doing things.

I really just want this to be set up according to the defaults as much as possible.  I want to have a good working knowledge of Apache and of how to set it up and configure it, but dang it if it isn't a frustrating process.  

Any tips would be much appreciated.

---

### Post by truant on 2011-01-05
Server-side includes?  Are you a time-traveller from 1995?  :)

Suggest you try to get a more modern solution working - php, python, something like that.  There's a slightly (only ever so slightly) steeper learning curve (tonnes of tutorials out there though) but you'll end up with much more useful skills to have in the long run.  Just a thought.

Anyway.  Enabling mod_include, like any other module, is done by symlinking it into /etc/apache2/mods-enabled, as described on this page: [http://www.debuntu.org/2006/06/15/66-how-to-enable-apache-modules-under-debian-based-system/2](http://www.debuntu.org/2006/06/15/66-how-to-enable-apache-modules-under-debian-based-system/2)

Easy!  :)

The probable reason you can't write to /var/www when logging in with SFTP is because you're not a member of the www-data group.  Add your username to the www-data line in  /etc/group (you'll need to edit that file as root - there is some other way to add yourself to a group but I always just edit /etc/group myself).  This is from memory, so may not entirely be right.  You can check:

If you do "ls -al /var/", which group owns the "www" directory?

Add your user to that group, and you should be sorted.

"XBitHack on" in your apache config should do the trick.  There's more on that here: [http://httpd.apache.org/docs/2.0/mod/mod_include.html#xbithack](http://httpd.apache.org/docs/2.0/mod/mod_include.html#xbithack)

Although as for running from /var/www being the "right" way to do it - not one of my many websites has ever run from there.  It's the default setting, that doesn't mean it's the "correct" one.  Much "better"- imo - to put each site under it's own uid and run it from it's own home directory (usually, I do /home/user/sites/site/ and /home/user/sites/logs/ and so on) - that way you have plenty of control, and can add more sites easily.  But who's to say what's "right" and "wrong" there's only - "works best for me"  :)

---

### Post by mdlueck on 2011-01-06
The last time I had to enable SSI on Ubuntu was for an 8.04 server. These are my notes about SSI from then...

To enable SSI
[http://ubuntuforums.org/showthread.php?t=586469](http://ubuntuforums.org/showthread.php?t=586469)

# sudo a2enmod include

---

### Post by James78 on 2011-01-06
> **truant said:**
> Anyway.  **Enabling mod_include, like any other module, is done by symlinking it into /etc/apache2/mods-enabled**, as described on this page: [http://www.debuntu.org/2006/06/15/66-how-to-enable-apache-modules-under-debian-based-system/2](http://www.debuntu.org/2006/06/15/66-how-to-enable-apache-modules-under-debian-based-system/2)
Which, can be done a much much easier way by using a2enmod (also listed in the link, but a good thing to list in this topic regardless). :)
```
sudo a2enmod include
```

Edit: D'oh, the person above me beat me to the exact same command. =D>

---

### Post by overmonk on 2011-01-06
> **truant said:**
> Server-side includes?  Are you a time-traveller from 1995?  :)

Suggest you try to get a more modern solution working - php, python, something like that.  There's a slightly (only ever so slightly) steeper learning curve (tonnes of tutorials out there though) but you'll end up with much more useful skills to have in the long run.  Just a thought.

Anyway.  Enabling mod_include, like any other module, is done by symlinking it into /etc/apache2/mods-enabled, as described on this page: [http://www.debuntu.org/2006/06/15/66-how-to-enable-apache-modules-under-debian-based-system/2](http://www.debuntu.org/2006/06/15/66-how-to-enable-apache-modules-under-debian-based-system/2)

Easy!  :)

The probable reason you can't write to /var/www when logging in with SFTP is because you're not a member of the www-data group.  Add your username to the www-data line in  /etc/group (you'll need to edit that file as root - there is some other way to add yourself to a group but I always just edit /etc/group myself).  This is from memory, so may not entirely be right.  You can check:

If you do "ls -al /var/", which group owns the "www" directory?

Add your user to that group, and you should be sorted.

"XBitHack on" in your apache config should do the trick.  There's more on that here: [http://httpd.apache.org/docs/2.0/mod/mod_include.html#xbithack](http://httpd.apache.org/docs/2.0/mod/mod_include.html#xbithack)

Although as for running from /var/www being the "right" way to do it - not one of my many websites has ever run from there.  It's the default setting, that doesn't mean it's the "correct" one.  Much "better"- imo - to put each site under it's own uid and run it from it's own home directory (usually, I do /home/user/sites/site/ and /home/user/sites/logs/ and so on) - that way you have plenty of control, and can add more sites easily.  But who's to say what's "right" and "wrong" there's only - "works best for me"  :)
I do all of my personal coding using PHP - what I'm doing here is accommodating existing web pages coded by an outside organization.  I'm going to work a Flash presentation I did into their format so that it will match the existing web framework exactly.  It already works as expected in the *live* site, but I wanted to get my personal server to function in the same way for the purposes of continuity.

Thanks for the link folks - I used a2enmod and added 'include' and restarted apache.  Given that the includes are still htm and html files, they aren't showing up yet, but I think once I enable XBitHack, they should, yes?

A final/follow-up:  The "Apache config" is too vague - do I edit the default file in sites-available?  Do I edit apache.conf?  It used to be pretty straightforward, but I confess - it's gotten so convoluted I'm still not sure where XBitHack on needs to be placed.

But I'm going to back up my default file and go nuts trying things.  

Thanks all for the tips.

---

### Post by mdlueck on 2011-01-06
> **overmonk said:**
> Given that the includes are still htm and html files, they aren't showing up yet, but I think once I enable XBitHack, they should, yes?

Oh, I forgot the other piece to making SSI work on that Ubuntu 8.04 box.

In the .htaccess in the web-root directory of that paticular site that needed SSI, I needed to add:

```
# .htaccess
# Add Apache SSI support to the .shtml file extention
AddType text/html .shtml
AddOutputFilter INCLUDES .shtml
Options +Includes  

```

So enable SSI for what ever file extensions you have SSI in. For us they were all .shtml files.

---

### Post by overmonk on 2011-01-06
> **mdlueck said:**
> Oh, I forgot the other piece to making SSI work on that Ubuntu 8.04 box.

In the .htaccess in the web-root directory of that paticular site that needed SSI, I needed to add:

```
# .htaccess
# Add Apache SSI support to the .shtml file extention
AddType text/html .shtml
AddOutputFilter INCLUDES .shtml
Options +Includes  

```

So enable SSI for what ever file extensions you have SSI in. For us they were all .shtml files.
Two things:

1.  Do I need to use a .htaccess file if I'm not using any sort of virtual hosting?  I mean, I can, but is it a workaround or something that must *always* be used?

2.  I don't have any shtml file; I want to enable XBitHack so that it will parse files with the execute bit set, and not every html file I post to it.  I don't have that many, but I'm trying to set it up 'right.'  I don't really want to enable the parsing of all html files - the Apache pages suggest that can be a strain (in theory), and suggest XBitHack.  I just don't know where, precisely, I need to put XBitHack on to enable it.

---

### Post by mdlueck on 2011-01-06
No idea on either of your questions. This I had stashed away in my KB from a client who moved from shared web hosting to a VPS environment, and we needed to retain SSI for a while to support legacy code.

That should at least give you a starting point of what to research, since that is the extent of what we needed to do to support the legacy SSI code.

---

### Post by truant on 2011-01-07
> **overmonk said:**
> A final/follow-up:  The "Apache config" is too vague - do I edit the default file in sites-available?  Do I edit apache.conf?

Apache, iirc, reads apache.conf, then sites-available/*, then .htaccess in that order.  Directives can go anywhere[1], but it's probably best to put potentially risky stuff like xBitHack into either sites-available/whatever or .htaccess

[1] some directives aren't allowed in .htaccess.  I forget which these are, but some of the more security-risky ones.

Anything in apache.conf will apply to all virtual hosts.  Anything in sites-available/host1 will only apply to 'host1', and /host1/.htaccess the same.  Some shared hosting setups don't allow you to modify sites-available, and .htaccess is useful there.  You can also use .htaccess in subdirectories of a virtual host - the most common would be to have a siteroot/private/.htaccess which limits access to the "private" directory.  So htaccess isn't a workaround, as such, it's a slightly different way of applying directives.  If all your pages want xBitHack, use sites-available, if you just want one directory, .htaccess is probably better.

hope this helps.

---

