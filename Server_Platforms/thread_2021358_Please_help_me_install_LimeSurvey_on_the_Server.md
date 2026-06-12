---
title: "Please help me install LimeSurvey on the Server"
date: 2012-07-09
forum: Server Platforms
---

### Post by js9 on 2012-07-09
Hi, everyone.

I'm trying to install LimeSurvey on our website server, but I'm stuck and don't know what to do. I've followed with great strictness the instructions on installing Limesurvey as shown on [http://docs.limesurvey.org/tiki-index.php?page=Installation](http://docs.limesurvey.org/tiki-index.php?page=Installation). 

GoDaddy is hosting the website. 
Our website is running Linux.
I'm trying to install LimeSurvey v1.92+.

I'm stuck on Step 8 (Run the installation script), which says:

> Go to "http://your.domain.com/limesurvey/admin/install". If you configured everything correctly you will be asked to create the database and/or create the tables inside the database. Limesurvey then creates the needed tables in the database.

I've tried going to the following URLs:[LIST]
[*][http://mywebsite.com/limesurvey/admin/install](http://mywebsite.com/limesurvey/admin/install)
[*][http://mywebsite.com/limesurvey/admin/install/index.php](http://mywebsite.com/limesurvey/admin/install/index.php) 
[*][http://mywebsite.com/limesurvey/admin/index.php](http://mywebsite.com/limesurvey/admin/index.php)
[/LIST]
but all give me a 404_error Page_not_found page.

[http://[mywebsite.com]/limesurvey/index.php](http://[mywebsite.com]/limesurvey/index.php) gives
> Can't connect to LimeSurvey database. Reason: Can't connect to local MySQL server through socket '/var/lib/mysql/mysql.sock' (2)

I've already edited my .htaccess file in the root folder (/) to read:
> 
<IfModule mod_rewrite.c>
# Turn on the Rewrite Engine
RewriteEngine On

# If the file or directory exists, show it
RewriteCond %{REQUEST_FILENAME} -f [OR]
RewriteCond %{REQUEST_FILENAME} -d
RewriteRule ^(.+) - [PT,L]

# Blank queries get sent to the index
RewriteRule ^$ /index.php [L]

# All other queries get sent to the index as index.php/whatever
RewriteRule ^(.*)$ /index.php?/$1 [L]

</IfModule>

Please help me.  Thank you.

---

### Post by uRock on 2012-07-09
Moved to ***Server Platforms***.

---

### Post by lisati on 2012-07-09
It almost looks as if the "install" directory is missing or in the wrong place.

---

### Post by CharlesA on 2012-07-09
> **lisati said:**
> It almost looks as if the "install" directory is missing or in the wrong place.
Yep.

I would suggest setting up a local LAMP box and messing around with it before trying to set it up on your hosted server.

---

### Post by js9 on 2012-07-09
Lisati and CharlesA,
Thanks for your response. 
If "install" directory is missing or in the wrong place, how can I fix this? I have thought that the "install" directory is in proper place.

In Filezilla, it is:
> /limesurvey/admin/install/

---

### Post by CharlesA on 2012-07-09
I would still suggest setting up a local LAMP box and testing it there before uploading it to the webhost.

Could it be your rewrite rules messing with things?

---

### Post by js9 on 2012-07-09
charlesA,
What do you mean by "rewrite rules"? Where can I find those rules? I'd like to learn how to keep them from messing things up, if indeed they are the culprit.

---

### Post by CharlesA on 2012-07-09
> I've already edited my .htaccess file in the root folder (/) to read:
Quote:
<IfModule mod_rewrite.c>
# Turn on the Rewrite Engine
RewriteEngine On

# If the file or directory exists, show it
RewriteCond %{REQUEST_FILENAME} -f [OR]
RewriteCond %{REQUEST_FILENAME} -d
RewriteRule ^(.+) - [PT,L]

# Blank queries get sent to the index
RewriteRule ^$ /index.php [L]

# All other queries get sent to the index as index.php/whatever
RewriteRule ^(.*)$ /index.php?/$1 [L]

</IfModule> 
^

---

### Post by js9 on 2012-07-09
I'm a point-and-click non-technical newbie. If anyone doesn't mind providing some hand-holding and spoon-feeding in regard to fixing up the .htaccess file, I would appreciate it.

---

### Post by CharlesA on 2012-07-09
Is there a reason you are using the URL rewrite function of Apache? I didn't see anywhere in the limesurvey docs that required that.

I'm assuming you are using it for the fancy URL stuff:
> $modrewrite: If set to 1, it activates the fancy URL feature (Example: [http://survey.example.com/123456/lang-fr/tk-sdlfkjozeiru(external](http://survey.example.com/123456/lang-fr/tk-sdlfkjozeiru(external) link) instead of [http://survey.example.com/index.php?sid=123456&lang=fr&token=sdlfkjozeiru).(external](http://survey.example.com/index.php?sid=123456&lang=fr&token=sdlfkjozeiru).(external) link) Before you activate this, you must rename "htaccess.txt" file to ".htaccess". You need to run an Apache web server with correctly installed mod_rewrite module. 

[http://docs.limesurvey.org/Optional+settings&structure=English+Instructions+for+LimeSurvey#Language_amp_Time](http://docs.limesurvey.org/Optional+settings&structure=English+Instructions+for+LimeSurvey#Language_amp_Time)

---

### Post by js9 on 2012-07-09
CharlesA,

My one-click install of Wordpress through my hosting company GoDaddy seemed to have produced an .htaccess file. The .htaccess file before I made changes yesterday looked like this:


> # BEGIN WordPress
<IfModule mod_rewrite.c>
RewriteEngine On
RewriteBase /
RewriteRule ^index\.php$ - [L]
RewriteCond %{REQUEST_FILENAME} !-f
RewriteCond %{REQUEST_FILENAME} !-d
RewriteRule . /index.php [L]
</IfModule>

# END WordPress

If Wordpress would have automatically created that htaccess text above, does it mean that it is necessary?

Yesterday, someone thought I was having problems installing LimeSurvey because of my .htaccess file. He was the one who told me to change the .htaccess file to...

> <IfModule mod_rewrite.c>
    # Turn on the Rewrite Engine
    RewriteEngine On
    
    # If the file or directory exists, show it
    RewriteCond %{REQUEST_FILENAME} -f [OR]
    RewriteCond %{REQUEST_FILENAME} -d
    RewriteRule ^(.+) - [PT,L]
    
    # Blank queries get sent to the index
    RewriteRule ^$ /index.php [L]
    
    # All other queries get sent to the index as index.php/whatever
    RewriteRule ^(.*)$ /index.php?/$1 [L]

</IfModule>


---

### Post by js9 on 2012-07-15
Dear Charles and all,

When I didn't have any .htaccess file at all, our Wordpress-powered website had 404 error messages. The only page that worked was [http://ourwebsite.com](http://ourwebsite.com). All other pages (for example, [http://ourwebiste.com/contact](http://ourwebiste.com/contact), [http://ourwebiste.com/about](http://ourwebiste.com/about), etc) produced the 404 message. So it seems that the .htacess file is needed for our Limesurvey**-less** website.

But what should I do if I want to create a page that uses Limesurvey? How can I make Limesurvey work together with our website? 

Thank you.

---

### Post by CharlesA on 2012-07-15
I am not all that familiar with rewrite rules, but it looks like you have it written to use the site root.

Maybe that could be modified somehow, but I don't know.

---

### Post by Habitual on 2012-07-16
> **js9 said:**
> ...If anyone doesn't mind providing some hand-holding and spoon-feeding in regard to fixing up the .htaccess file, I would appreciate it.

Can do, will do. Shoot me a PM with some contact (email preferred), or a SkypeID, something more direct than this forum.

My skills are notoriously public [here...]("http://www.bournetoraiseshell.com/article.php/20120502142044810")
subscribed with interest...

---

### Post by CharlesA on 2012-07-16
> **Habitual said:**
> Can do, will do. Shoot me a PM with some contact (email preferred), or a SkypeID, something more direct than this forum.

My skills are notoriously public [here...]("http://www.bournetoraiseshell.com/article.php/20120502142044810")
subscribed with interest...
Thank you. :) Hope you guys are able to figure out what the issue is.

---

### Post by js9 on 2012-07-16
habitual,

Thank you so much for offering to help.

I've sent you a private message with my email address.

Can I ask why you prefer to take the communication out of the forum?

I think there are advantages to communicating through this forum:
1. Other technical experts like you can look over our communication and provide accountability.
2. Other newbies like me can learn from the instruction provide.

---

### Post by CharlesA on 2012-07-16
Sometimes it is easier to help in realtime.

---

### Post by Habitual on 2012-07-16
> **js9 said:**
> ...Can I ask why you prefer to take the communication out of the forum?...

Sure, let's say I don't play well with others and I need to work on my interpersonal skills...  :)

---

### Post by Habitual on 2012-07-16
for the benefit all of that may be concerned...

                 My experience at GoDaddy hosting is that you have to use their     Hosting Control Panel (HCP)
    to setup the mysql database. Are you familiar with that interface?     Do you have ssh access?
    
    What I could use is the actual domain name where this survey should     reside on and the location of the "DocumentRoot" where the LimeSurvey web files     were extracted to, or will reside in on the server.
    This should be like "/var/chroot/home/content/09/**[COLOR=Red]3142857[/COLOR]**/html"  but will vary     according to your GoDaddy details [COLOR=Red]**emphasized          like so**[/COLOR].
    
    the limesurvey directory can be anything _under_ the .../html     as the .../html directory probably contains your domain.com's "DocumentRoot".
    
    So the goal of this back-and-forth will be to walk you through 
* The     creation and/or verification of the database (db).
* Create and verify connection details to limesurvey db for the     installer.
    * Edit limesurvey/config.php and use those credentials for the     installer.
* run the installer at [http://domain.com/limesurvey/admin/install](http://domain.com/limesurvey/admin/install)
    
    These shortcut steps are clearly documented at [here...]("http://www.samundra.com.np/how-to-general-introduction-and-installation-of-limesurvey/1026")
    and the official install is [here...]("http://www.docs.limesurvey.org/tiki-index.php?page=Installation&structure=English+Instructions+for+LimeSurvey")     and cites
    
[LIST]
[*] **MySQL 4.1.0 or later** **OR** Microsoft SQL         Server 2000 or later **OR** Postgres 8.1 or later
[*] **PHP 5.1.2 or later** with the following modules/libraries         enabled:
[LIST]
[*] mbstring (Multibyte String Functions) extension library             (see also [Installation FAQ]("http://docs.limesurvey.org/tiki-index.php?page=Installation+FAQ#What_is_this_mbstring_Multibyte_String_Functions_library_")
[*] mysql5 or pgsql PHP library (which is standard with             hosting providers - if you have setup your own server make             sure it is installed)
[/LIST]
       
[/LIST]
     
    The issue with .htaccess "may" be because .htaccess works in a     top-down fashion, so any .htaccess in your .../html directory would     apply to all 
    program directories below it, causing all sorts of chaos, but that     is easily rectified.

    So an .htaccess in .../html would also apply or override any     .htaccess files in any directories, under (.../html/xyz... for     example)  the html directory.
    
    Please let me know...
    
    JJ

I'd like to point out at this time, that editing an .htaccess for LimeSurvey rewrites should be done AFTER the install.

---

### Post by js9 on 2012-07-23
The problem was with file permissions. Using Filezilla, I gave everything in /limesurvey/ a file permission of 755. That solved things.

---

### Post by Habitual on 2012-07-23
Glad it worked out!

---

