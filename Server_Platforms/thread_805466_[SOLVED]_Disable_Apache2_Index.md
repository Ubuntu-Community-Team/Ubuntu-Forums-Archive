---
title: "[SOLVED] Disable Apache2 Index"
date: 2008-05-24
forum: Server Platforms
---

### Post by Phoenixzeus on 2008-05-24
Hello,
I have just set up a quick Ubuntu 8.04 LAMP Server. I have made a few minior security fixes to Apache2 and I am wondering how I turn off the Index browsing. For example if you type in /images (on the hosted website) it will take you to a index page listing all the files in the images folder. I have seen references to adding:
Options -Indexes
But I am unsure where to actually add this, be it the, httpd.conf or apache2.conf file or somewhere else.
Any suggestions would be much appreaciated.
-Phoenixzeus

---

### Post by ArrantSquid on 2008-05-24
you would put it in your httpd.conf within the directory you don't want indexed so if you're site is at /var/www/ and the images folder is at /var/www/images you would put it like this:

```

<Directory /var/www/images/ >
Options -Indexes
</Directory>

```

You should obviously put more options in there, but that would be one. You could also do this with an .htaccess file which would be specific to that site. This may be easier. To be honest I disable file listing for all pages because if I want to list the files I would have made a page out of it. So if you just put

```

Options -Indexes

```

into an .htaccess file it will read it for every directory. The nice part with this is that you don't need an apache reload if you change it. HTH


Also, I use these as a base rule for .htaccess files.

```

# First redirect everyone to index.php
<IfModule mod_rewrite.c>
RewriteEngine On
DirectoryIndex index.php index.html index.htm default.htm default.html
RewriteBase /
RewriteCond %(REQUEST_FILENAME) !-f
RewriteCond %(REQUEST_FILENAME) !-d
RewriteRule ./index.php [L]
</IfModule>

# set cache to be "non-existent"
RedirectMatch 400 /cache(/|$)

# if it fails to be non-existent then deny all access
<FilesMatch "\.cache$">
        Deny from all
</FilesMatch>

```

The third rule is redundant, but I like failsafes. Usually I'll deny access to a cache folder or log folders. Making them appear to be non-existent is nice because then if someone is trying to get in it's like, yo that doesn't even exist partner. Try again! You can also setup your error docs in your .htaccess like this.

```

# Now setup all error documents
ErrorDocument 400 /errors/badrequest.php
ErrorDocument 401 /errors/authreqd.php
ErrorDocument 403 /errors/forbid.php
ErrorDocument 404 /errors/notfound.php
ErrorDocument 500 /errors/serverr.php

```

again. hth

---

### Post by Phoenixzeus on 2008-05-24
Sorry for being thick on this matter, but I have just starting using LAMP servers and Apache this week.
For starters to get a basic disable fix working (for now, then I can add the rest of the code you suggested after) I would navigate to /var/www/ (as that is where my test website is stored and then type:
"touch .htaccess"
"sudo pico .htaccess"
and then add in "Options -Indexes"
This didn't work for me, Its obviously something I didn't catch, sorry :)
Thank you for your help

---

### Post by ArrantSquid on 2008-05-24
Don't sweat it. We all started out somewhere and the reason Ubuntu is what it is, is due to everyone learning and helping each other out. So no worries.

So what part of it didn't work? Is the file there? Post the output of:
```

ls -al

```

when it's run in /var/www/

also post this:
```

cat /etc/apache2/httpd.conf

```
and this:
```

ls /etc/apache2/sites-enabled/

```

---

### Post by Phoenixzeus on 2008-05-24
My website is actually in /home/user/public_html
(Apache has been setup to reflect that too)
So I went into /home/user/public_html/ and typed ls -al
.
..
.htaccess
images  (Blue as its a folder)
index.html

If you need it the test website is [http://phoenixzeus.homelinux.org](http://phoenixzeus.homelinux.org)
Many thanks again

---

### Post by ArrantSquid on 2008-05-24
Alright. Go into your httpd.conf file and add this:
```

<Directory /home/user/public_html>
 Options -Indexes
 AllowOverride All
 Order allow,deny
 Allow from all
</Directory>

```

then give a good 'ol restart to apache
```

/etc/init.d/apache2 restart

```
and see if that changes it.

---

### Post by Phoenixzeus on 2008-05-24
I added that to the httpd.conf file inside of /etc/apache2/
Is that right or was I supposed to make a httpd.conf file inside of /home/user/public_html
I modified the file inside /etc/apache2 wrote out and restarted apache with to avail :( Sorry

Added: Before I added this to the httpd.conf file, it was empty. Does that sound about right?
I'm not supposed to add something into the Index.html file to reflect any of this am I, I am really new to HTML coding and Apache.

---

### Post by ArrantSquid on 2008-05-24
No you put it in the right place.... Now i'm sitting here like wtf am I doing wrong? This same setup has always worked for me. Normally you only need one or the other, not both and right now neither works! I just did the same test on my server and it works perfectly...

lotek.homelinux.com

now try to go to lotek.homelinux.com/images

all i did was add an .htaccess file to it and add Options -Indexes

What does your apache2.conf look like?

```

cat /etc/apache2/apache2.conf | grep ht

```

---

### Post by Phoenixzeus on 2008-05-24
Yeah if I type /images on your site it tells me where to go...

I had to |more to read it start of it, but it was the usual comment out stuff, the uncomment lines read (in order)
AccessFileName .htaccess
#The following lines prevent .htaccess and .htpasswd files from being
<Files ~ "^\.ht">
Include /etc/apache2/httpd.conf
#ErrorDocument 404 Missing.html
**And then the rest are all ##ErrorDocument 403, etc. If you need all of this commented out info let me know and I will type it out :)

---

### Post by ArrantSquid on 2008-05-24
are you using anything to manage your websites? like a control panel or anything? (webmin, virtualmin, ispconfig, etc.) if not, have you done a full reboot? I'm lost. Like truly lost. I'll keep on keepin' on with you until we get it fixed, but I am corn-fused right now.

---

### Post by Phoenixzeus on 2008-05-24
Nope, Its my linux server box beside me, clean install last night. Tried with it a bit at work this week and wanted to start learning. So there is nothing managing my websites (to my knowledge, unless LAMP 8.04 does something like that as default these days, but I am sure its just Apache doing its thing, I did read my apache2.conf file again after seeing the "#The following lines prevent .htaccess and .htpasswd files from" bit again and found:

# The following lines prevent .htaccess and .htpasswd files from being
# Viewed by web clients.
#
<Files ~ "^\.ht">
   Order allow,deny
   Deny from all
</Files>

Is that useful mate? Sorry to be such a pain :).
Edit: And yes I performed a complete reboot 5 minutes ago when I was thinking about it, however I will try another now.

---

### Post by ArrantSquid on 2008-05-24
Yeah I was actually having you check that to see that that was in there. =) Did you do the reboot? Would you rather use jabber or something to try to hammer this out?

---

### Post by Phoenixzeus on 2008-05-24
Yes, I did. Completed it just then. Tested and no success :(

---

### Post by Phoenixzeus on 2008-05-24
I just went to jabber.org, had a bit of a look around and didn't get a clear indication on what it is. Is it an IM program in which you speak to people from Jabber about server issues? Or is it an opensource individually hosted IM client to speak to other clients?

---

### Post by ArrantSquid on 2008-05-24
ok... Let's try this since I didn't think of it...

```

sudo a2enmod rewrite
sudo apache2ctl -l

```

now post the output of the last command...

Jabber is the IM protocol that Gmail uses. We can keep doing it like this if that's easier. I was just trying to make things flow quicker (esp. since it's 2:00 am here).


also, post the output of this:
```

ls /etc/apache2/sites-enabled/

```

---

### Post by Phoenixzeus on 2008-05-24
First command added fine. I force re-loaded Apache like it said, didn't make a difference. 
I also init.d/apache2 restart and it didn't make a difference.
Second command listed:
Compiled in Modules:
core.c
mod_log_config.c
mod_logio.c
prefork.c
http_core.c
mod_so.c

---

### Post by ArrantSquid on 2008-05-24
Ok. We're gonna do two things and THIS WILL WORK or I'll do something extreme. I'll figure out what that is later.

First do this:
```

ls /etc/apache2/mods-enabled/ | grep re

```
it should tell you that rewrite.load is there.

Next do this:
```

sudo pico /etc/apache2/sites-enabled/000-default

```

In that file you need to change every instance of it saying AllowOverride None to AllowOverride All (capital A because apache is fickle).

Then do a /etc/init.d/apache2 force-reload and it should do it! (i hope)


I'll eat my shirt if it doesn't work... Not extreme, but since I'm recovering from a second surgery it'll do... Ooooo i know. I'll start recommending windows! LoL! =0)

---

### Post by Phoenixzeus on 2008-05-24
Something extreme, I know that feeling.

Mate,
ls /etc/apache2/mods-enabled/ | grep re
responded with rewrite.load being there (yay)
sudo pico /etc/apache2/sites-enabled/000-default (opened a new file because there wasn't one there)
I then navigated to /etc/apache2/sites-enabled and there was only a file called "mysite"
I am as of now doing a complete find for 000-default

---

### Post by ArrantSquid on 2008-05-24
Nonono... Don't bother. I thought that maybe the default file was there... I should have had you output that first. Edit your mysite file and edit those lines I said before...

---

### Post by Phoenixzeus on 2008-05-24
YES! You legend that finally got it.
Man for a Tech I really was bad on that one. Thanks again mate, I'd give you multiple thanks if I could :) I really appreaciate it.

So for future reference do I need to go through the mysite file again, or was that just a once off.
Do I usually just block things with that .hpaccess file in the web folder?

---

### Post by ArrantSquid on 2008-05-24
I'm just glad that it's working now.... It's always stupid stuff that you wouldn't think of ya know. And I mean it took me this long to get that one so that's definitely a bad on me. Again, glad it works and I'll keep an eye out on that site...

OH! You may want to change your ServerSignature to off and your ServerTokens to Prod and put TraceEnable off into your httpd.conf. All of those are just little things to help out with advertising as little information about your OS as possible. The TraceEnable disables the Trace/Track protocol which is used maliciously sometimes. HTH and if you have any other questions, feel free to PM me. =)

[edit]
both ServerSignature and ServerTokens are in your apache2.conf
[/edit]

---

### Post by Phoenixzeus on 2008-05-24
Thanks mate, I was half way through turning them off when I hit this issue in the first place, so I shall continue finishing it. Thanks for the suggestions, I didnt think of the TraceEnable bit.

---

### Post by ArrantSquid on 2008-05-24
No problem. Again, glad I could help.

---

