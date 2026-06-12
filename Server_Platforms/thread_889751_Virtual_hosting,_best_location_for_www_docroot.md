---
title: "Virtual hosting, best location for www docroot?"
date: 2008-08-14
forum: Server Platforms
---

### Post by 2smooth on 2008-08-14
I've read several tutorials on setting up virtual hosting.

Some use the /var/www/... as the docroot and some use /home/user/www

Which one is better/easier to maintain/more secure?

What should be the acces rights/ownerships of these directories?

---

### Post by windependence on 2008-08-14
Well, people have their own opinions but /var actually stands for  "variable" and is usually where changing content is kept. IMHO home directories are not a good idea for keeping web sites. 

You should leave the ownership of /var/www as root. You don't want the Apache user owning it because if someone compromises your user they can do a alot of damage.

-Tim

---

### Post by 2smooth on 2008-08-14
> **windependence said:**
> 
You should leave the ownership of /var/www as root. You don't want the Apache user owning it because if someone compromises your user they can do a alot of damage.
-Tim

How do you set the accesrights properly for eg php scripts which needs write acces to certain files?

---

### Post by windependence on 2008-08-15
Are they actually writing to the document root or are they just writing to the database? Most times they don't actually write to the html templates, they just pull data from the database and plufg it into the template for display. the writes are usually on the DB server.

-Tim

---

### Post by 2smooth on 2008-08-15
> **windependence said:**
> Are they actually writing to the document root or are they just writing to the database? Most times they don't actually write to the html templates, they just pull data from the database and plufg it into the template for display. the writes are usually on the DB server.

-Tim

For example in Joomla when you changed something to the configuration it somethimes need to write acces to certain config files on the file system.

---

### Post by Kolipoki on 2008-08-15
> **2smooth said:**
> For example in Joomla when you changed something to the configuration it somethimes need to write acces to certain config files on the file system.

It's because Joomla is a Content Management application so it will definitely need some writable directories. Same goes for image/media galleries and such.

On the other hand, besides some cache functions, I'm not too sure how much Joomla actually writes in its own directory as part of its operation. Folders of images, includes, components and others, need to be writable mostly for your uploading and probably admin preferences. By the way... Joomla has just released  version 1.5.6, with an important security fix, so that's the one you should install :)

Still, at least as far as I've seen on this forum, seems that the best practice is to leave /var/www chowned to root and make subdirectories for everything else you want to publish. Then, the subfolders can be chowned to www-data, which is the Apache user.

These 2 discussions elaborate a bit on this subject:

[http://ubuntuforums.org/showthread.php?p=5529187#post5529187](http://ubuntuforums.org/showthread.php?p=5529187#post5529187)
[http://ubuntuforums.org/showthread.php?p=5529242#post5529242](http://ubuntuforums.org/showthread.php?p=5529242#post5529242)

Hoping this helps... /thumbs up

EDIT: I got curious, so just reinstalled Joomla in my remotely hosted site. Almost all directories of Joomla were installed by default with permissions to 755, which means groups and others can read and execute, but can't write, only the owner can. Sorry for pouring some weight on the Joomla subject, but probably will be useful soon.

I also recalled that some image galleries php applications, recommend to move the image folder out of the publishing directory.

---

### Post by windependence on 2008-08-16
Most CMS, like Joomla, set permissions when they are installed. I haven't used Joomla so I can't say but most of the other ones I used have set their own.

-Tim

---

### Post by 2smooth on 2008-08-16
> **Kolipoki said:**
> Sorry for pouring some weight on the Joomla subject, but probably will be useful soon.

No problem, i like these 'daily life' examples. :-)

---

### Post by mbeach on 2008-08-17
> **windependence said:**
> IMHO home directories are not a good idea for keeping web sites. 

I'm glad you said that T.  I know that I often recommend the opposite, pointing the documentRoot to a folder in a home directory.  I personally set it up this way to avoid calls/requests from users asking me to deal with issues for a file they've placed in their subfolder in /var/www folder.  I used to keep everything there, with a structure like /var/www/user1, /var/www/user2 etc.  I've found that suggesting to have a www folder in their home folder gives them pretty good control over what they can do, with me managing the apache conf files in sites-available.  I thought it was a good idea to take this approach since the user_mod seems to use a similar structure with the public_html folder in the home folder.  I figured, having a virtual host point to a www folder there instead would be ideal.  I don't rent/sell webspace etc, its all for related company colleagues (mostly competent) so perhaps I have some flexibility over others.  Many are using Windows at home and have a drive mapped to their home folder (openvpn) which provided me one more reason to stick with this method.

I find that that its often easier for new users to be able to easily edit the files they are creating in their /home/user/www/ folder using gedit or whatever without gksudo/sudo.  I think its easier to change the group to www-data for those files than to point them to /var/www.  I know these are not strong points, and have easy ways around.

This is by no means a flame, just always looking for a better/more efficient/easier to manage way to set stuff up for the next box I end up putting together.  Its not what I do for a living, just happen to be the defacto guy that takes care of it all for the company (I'm by no stretch an expert, novice at best).

---

### Post by windependence on 2008-08-17
In your situation under the conditions you have outlined, I agree with you 100% from an administrative standpoint. 

My recommendation relates to a production web site where you are running a business or service 24/7/365. Unlike most people who use a co-located shared hosting solution for their sites, I don't use ftp to check out and put files. I use scp or a solution like WinSCP with Windoze or Fugu with my Mac, but I am the only admin in my datacenter so if there are permission problems or whatever, I can fix them and get the files on the server root. This is not always possible in all situations especially for a hobby web server. I usually have the fault of thinking always in production mode which I realize is not what everybody does with their server. Sometimes I have to remember I am not on the *BSD forums. ;)

-Tim

---

### Post by 2smooth on 2008-08-20
I've read several threads on this topic, but it's still not completely clear to me how to set the file permissions and owner for the different directories:

In the setup below /var/www is the document root for default
/var/www/mysite/www the document root for mysyite.com

Is this directory setup correct and what should be the ownership and and permissions for these directories?

```

/var/www
     |- mysite
        |-www
        |-php-sessions


```

---

### Post by mbeach on 2008-08-20
I don't like it because from the default site you can get to the 'mysite's php-session files - Yikes.

if it looked more like
```

/var/www/
     |- defaultsite
     |- mysite
        |- www
        |- any other non web accessible stuff

```
I'd say root should own /var/www, /var/www/defaultsite.  www-data will likely own the files in defaultsite.  Depending on who is responsible for 'mysite' they should own its contents.  I tend to set permissions to allow all to read the files within the documentroot, unless for some reason some script needs write access, in which case you can take a couple of approaches - either change the ownership of that particular file to www-data or make it writable by all.

---

### Post by 2smooth on 2008-08-21
> **mbeach said:**
> I don't like it because from the default site you can get to the 'mysite's php-session files - Yikes.

if it looked more like
```

/var/www/
     |- defaultsite
     |- mysite
        |- www
        |- any other non web accessible stuff

```


If i'm gonna be the only one who's gonna maintain the sites
Who should be the owner of? 
mysite/www
mysyte/any other non web accessible stuff

---

### Post by windependence on 2008-08-21
Basically, your files should be set to 755, and your ownership shouuld be anything other than the Apache user. Many people set the ownership of the web files to their own user so that they can  upload and modify files. Files that need to be written to, need to have their permissions and/or ownership set to allow the Apache user to read and write to them. There are many ways to do this, but I do not recommend making anything world writable unless you want your site hacked.

-Tim

---

