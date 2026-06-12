---
title: "[SOLVED] set up apache virtual hosts now nothing works"
date: 2008-10-02
forum: Server Platforms
---

### Post by chriswebb18 on 2008-10-02
Alright, so i finally had my server where i wanted it with deflate and cachefile mods working how i wanted, when i decided to add a second site to my server.  server only has one nic, if that's relevant at all.  i am using ubuntu server 8.04 lts, with the creconfigured lamp server.  the only adjustments were adding mod_deflate, mod_cache_file, these virtual hosts, and a change in the document root for default site.  the apache2.conf(.txt) is the same as the default installation except for the document root change, which has worked since i first set it up.  al of my changes were put in httpd.conf(.txt as attached), so that if i screwed things up, i could fix it more easily.  i did the a2ensite.  i also modified the innovationow file in sites-enabled to reflect the correct servername, serveralias, documentroot. and added these changes to httpd.conf.

#Virtual Hosts config

NameVirtualHost *:80

<VirtualHost *:80>
   ServerName [www.minnickart.com](www.minnickart.com)
   ServerAlias minnickart.com *.minnickart.com
   DocumentRoot /var/www/chis-pc
</VirtualHost>

<VirtualHost *:80>
   ServerName [www.innovationow.com](www.innovationow.com)
   ServerAlias innovationow.com *.innovationow.com
   DocumentRoot /var/www/innovationow
</VirtualHost>

Should i not have added that to the httpd.conf since it has the same info as the site file?

i almost forgot to give you the errors im getting, im trying to be as complete as possible, let me know if there is any other info i can give you to help you help me...

after /etc/init.d/apache2 restart, i get these errors:

warning: document root [/var/www/chris-pc] does not exist
[error] virtualhost *:80 -- mixing * ports and non-* ports with a namevirtualhost address is not supported, proceeding with undefined results
[error] virtualhost *:80 -- mixing * ports and non-* ports with a namevirtualhost address is not supported, proceeding with undefined results
[warn] namevirtualhost *:0 has no virtualhosts
[warn] namevirtualhost *:80 has no virtualhosts


it repeats those errors 4 times and finishes command.  apache process is still runnig, but obviously if it says there are no vhosts and it can no longer find the doc root for the default site, it wont serve anything.  Any help would be much appreciated.  thank you all


***updated***
i removed the innovationow site from sites-enabled and commented out the virtual hosts configurations in my httpd.conf file.  server works fine for default site (with /var/www/chris-pc as doc root), but, of course that still does not help me get the second site up and running.

**attachments removed**

---

### Post by chriswebb18 on 2008-10-02
OK, so I am just an idiot, apparently.  I tried to add those virtualhost entries into httpd.conf when all i needed to do was the a2ensite and modify the site file to have the correct servername and alias and docroot.  making more work for myself than i need to.  I guess i'm just too used to windows, where you have to check 20 different places for settings.  i do still have one issue.  i did the a2ensite and enabled the second site.  now both are working, but i get this:

/etc/init.d/apache2 reload
[DATE] [warn] NameVirtualHost *:0 has no VirualHosts
                                             [ OK ]

things work fine, but why is it giving that error, i dont see anywhere that port 0 is specified.  not too urgent since it works, but does anyone know why it's doing this?

---

### Post by randyks on 2008-10-02
> **chriswebb18 said:**
> O  now both are working, but i get this:

/etc/init.d/apache2 reload
[DATE] [warn] NameVirtualHost *:0 has no VirualHosts
                                             [ OK ]


[http://ubuntuforums.org/archive/index.php/t-312916.html](http://ubuntuforums.org/archive/index.php/t-312916.html)

---

### Post by chriswebb18 on 2008-10-02
thanks for the help there, i had marked it solved since i wasnt "really" having any issues.  i appreciate it, though.  looking into that link now...

---

