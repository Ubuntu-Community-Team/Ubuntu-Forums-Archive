---
title: "Webmin &gt; Apache2 &gt; Virtual Hosts"
date: 2007-06-15
forum: Server Platforms
---

### Post by lindsay_keir on 2007-06-15
I had troubles using Apache2's Virtual Hosts so I thought I'd do a quick How-To to pass on my method. Really, the basic answer is to get an "Alias" defined in apache2.conf (httpd.conf). Anyway ...

**Apache2**
[LIST]
[*]Link [FONT="Courier New"]/etc/apache2/mods-available/alias.load[/FONT] => [FONT="Courier New"]/etc/apache2/mods-enabled[/FONT]
[/LIST]
[B]
Webmin > Apache > Module Configuration[/B]
[LIST]
[*]Change all [FONT="Courier New"]../apache/..[/FONT] files to [FONT="Courier New"]../apache2/..[/FONT]
[/LIST]
[LIST]
[*]Set (*) Path to httpd.conf or apache2.conf = [[FONT="Courier New"]/etc/apache2/apache2.conf[/FONT]]
[/LIST]
[LIST]
[*]Set (*) Directory to create links in for new virtual servers = [[FONT="Courier New"]/etc/apache2/sites-enabled[/FONT]]
[/LIST]

**Webmin > Apache > Define a Virtual Host ...**

[FONT="Courier New"]  Document Root [/myGlobal/www/testy1][/FONT]
[FONT="Courier New"]        [*] Allow access to this directory[/FONT]
[FONT="Courier New"]   Server Name [testy1][/FONT]
 [Create Now]

You will now have a **testy1.conf** site available and enabled, which looks like ...
[INDENT][FONT="Courier New"] <VirtualHost *>
 DocumentRoot "/myGlobal/www/testy1"
 ServerName testy1
 <Directory "/myGlobal/www/testy1">
 allow from all
 Options +Indexes
 </Directory>
 </VirtualHost>[/FONT][/INDENT]

[B][COLOR="Red"]This is the important part! [/COLOR]
A [FONT="Courier New"]<VirtualHost *>[/FONT] ignores the declarations for [FONT="Courier New"]DocumentRoot  ServerName Alias[/FONT] and will default to looking for the files under /var/www - So ...[/B]

**Edit [FONT="Courier New"]/etc/apache2/apache2.conf[/FONT]** - At the end put

[INDENT][FONT="Courier New"]  # Include the virtual host configurations:
  Include /etc/apache2/sites-enabled/
  Include /etc/apache2/virtualHosts[/FONT][/INDENT]

**Create [FONT="Courier New"]/etc/apache2/virtualHosts[/FONT]** and add your your Virtual Host(s) Alias item(s)

[INDENT][FONT="Courier New"]  Alias /testy1 "/myGlobal/www/testy1"[/FONT][/INDENT]

**Create [FONT="Courier New"]/myGlobal/www/testy1/index.html[/FONT]**

[INDENT][FONT="Courier New"] <html>
 <head>
 <title>testy1</title>
 </head>
 <body>
 <h2 align="center">This is http://localhost/testy1/</h2>
 <div align="center"><img src="/icons/apache_pb.gif" alt="" /></div>
 </body>
 </html>[/FONT][/INDENT]
[COLOR="Blue"]
:p[FONT="Courier New"]http://localhost/testy1[/FONT] [/COLOR]is now accessible

Add more Virtual Hosts as wanted - just don't forget to add their **Alias** to  **[FONT="Courier New"]/etc/apache2/virtualHosts[/FONT]**:p

:(**[COLOR="Blue"]VirtualDocumentRoot[/COLOR]**
I read up on VirtualDocumentRoot at [http://httpd.apache.org/docs/2.0/mod/mod_vhost_alias.html](http://httpd.apache.org/docs/2.0/mod/mod_vhost_alias.html) and it sure looks good, execpt, how do you use it?
I enabled mod_vhost_alias. and modified my testy1 declaration to ...
[INDENT][FONT="Courier New"]#DocumentRoot "/myGlobal/www/testy3"
ServerName testy3
<Directory "/myGlobal/www/testy3">
allow from all
Options +Indexes
</Directory>
UseCanonicalName Off
VirtualDocumentRoot /myGlobal/www/testy3[/FONT][/INDENT]
... and tried it - no luck; but it sure looks good. and I would like to use it.:(

---

### Post by lindsay_keir on 2007-06-15
[COLOR="Red"]**Well that was fun**[/COLOR]
It turns out that I was half right, half wrong. The **default** site was incorrect. I re-created it and uncommented the line **[FONT="Courier New"]RedirectMatch ^/$ /apache2-default/[/FONT]** and now [FONT="Courier New"]DocumentRoot[/FONT] works *without* needing the virtualHosts file / Alias items.
[LIST]
[*]You do NOT need [FONT="Courier New"]mod_vhosts_alias[/FONT]
[/LIST]
[LIST]
[*]Un-comment the default Virtual Server site's [FONT="Courier New"] RedirectMatch ^/$ /apache2-default/[/FONT] line. AND ensure that the default Virtual Server contains everything - and hasn't been "worked on".
[/LIST]
[LIST]
[*]The comments about [FONT="Courier New"]VirtualDocumentRoot [/FONT]not doing anything regarding a non-[FONT="Courier New"]/var/www [/FONT]directory hold true.
[/LIST]

---

### Post by hockey97 on 2007-06-15
I have have problems with apache 2 with webmin, I installed it and I got squid proxy installed and then I installed cvs server, 

I had apache working before but once I installed squid proxy and cvs server something happened,

I can stil access my apache server but with only my computer the one that has the server, not my other computer's.

Before I could go on my other computers and type my internal ip adress of the computer that has the server while that computer si on, would be able to connect to apache like view it as a webpage, and could get to my webpages ect.

Now I can't I don't know what happened, I think squid proxy ro cvs server config some files of apache and now it only works on the computer that is hosting it..

Do you got any I idea's on what might of  happened??

---

### Post by lindsay_keir on 2007-06-16
Maybe a security definition? ...
For example, your doc directory is only accessible as //http://localhost/doc and from nowhere else because of this definition in your VirtualHost default.
[INDENT][FONT="Courier New"]    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>[/FONT][/INDENT]

---

### Post by hockey97 on 2007-06-16
it looks like I am missing  /etc/apache2/access.conf 

How can I get this file again??

---

### Post by lindsay_keir on 2007-06-16
hockey97...
Ummm, I only have 3 days Apache2 experience. But ...

access.conf and srm.conf are legacy files that are "left-overs" from Apache1 - Same as httpd.conf has been replaced by apache2.conf

That said, I'm guessing you're installing Frontpage Extensions, so perhaps the commands that used to be in access.conf are now in apache2.conf (or maybe even httpd.conf).

You might try looking at this site - it's Apache / Frontpage orientated
[http://www.opensubscriber.com/message/apache-fp@lists.joshie.com/1153267.html](http://www.opensubscriber.com/message/apache-fp@lists.joshie.com/1153267.html)

And, if FrontPage, did you install from the apt? libapache-mod-frontpage-mirfak Or from source?

Sorry, that's it from me, Webmin and Mediawiki are pretty well the only non-apt packages I install (and ONLY because the latest friendliest and easiest control functions are in the latest versions - I'm not smart, just lazy and stubborn).

---

### Post by hockey97 on 2007-06-16
HI  I now reinstalled apache2 and installed apache, but apache2 dosne't have apache2.conf file and so now apache won't start, it say's that apache2 is not started, so n webmin I click start apache and then I get an error saying apache2 server is not running, when I try running it thought

terminal I get an error saying can't find apache2.conf no such file or dir.

but the funny thing is the error show's me that apache server is not running, but yet on my computer the one with the server I can still put my internal ip address and still see my webserver running.

I really need help, getting kinda frustrated.

I am not the only one with this problem I have seen people asking on the fourms with the same problems.

---

### Post by immeëmosol on 2008-05-02
Did you already enable mod_vhost_alias?
#a2enmod vhost_alias
[http://httpd.apache.org/docs/2.0/mod/mod_vhost_alias.html](http://httpd.apache.org/docs/2.0/mod/mod_vhost_alias.html)
Then in your config file wirte something like:
VirtualDocumentRoot /var/www/%0
Now if you go to [http://localhost/](http://localhost/) apache will look inside the directory /var/www/localhost/

---

