---
title: "Apache vitual host setup confusion"
date: 2006-08-07
forum: Server Platforms
---

### Post by Enforcer83 on 2006-08-07
Alright I am new to Ubuntu in general and editing configuration files without someone who is willing to take me through it step by step specifically.  I am using the desktop version of Ubuntu.  I installed apache, mysql, and php5.  I have read the server guide but I am still confused.  So maybe one of you guys would be nice and help me out.

I want to setup my server so that it will look at this location
[COLOR="Red"]/home/<username>/www/public_html/[/COLOR]
for the site but also look at this location
[COLOR="Red"]/home/<username>/www/cgi-bin/[/COLOR]
for perl and cgi scripts.

What lines do I need to edit in the
[COLOR="Red"]/etc/apache2/sites-available/default[/COLOR]
file to change this?

---

### Post by chrisfay on 2006-08-08
add to /sites-anabled/000-default:

<VirtualHost *>
DocumentRoot "/home/<username>/www/public_html/"
ServerName "yourdomainname.tld"
ServerAlias "www.yourdomainname.tld"
<Directory "/home/<username>/www/public_html/">
allow from all
</Directory>

Then, at the bottom of your apache2.conf add:

ScriptAlias /cgi-bin/ /home/<username>/www/cgi-bin/

At least that's how I have it, I'm sure you could configure it differently.

---

### Post by Enforcer83 on 2006-08-08
How do I change the size of the database for mysql?
and where do i set the location of the database

---

