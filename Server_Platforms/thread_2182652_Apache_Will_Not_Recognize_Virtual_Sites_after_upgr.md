---
title: "Apache Will Not Recognize Virtual Sites after upgrade to 13.10"
date: 2013-10-21
forum: Server Platforms
---

### Post by Martin_Corrigan on 2013-10-21
I am running Apache v2.4.6.  I had it configured to run two sites, the default, plus a second site [www.testmwtdb.com](www.testmwtdb.com).  I have been using this setup for minimally 6 months with no issues.  I upgraded the Ubuntu to v13.10 tonight.  Now the Apache software will not recognize any of my sites.  

In the /etc/apache2/sites-available there are the same 3 files from before the upgrade:
   000-default.conf
   default-ssl.conf
   testmwtdb.com

In the etc/apache2/sites-enabled directory there are also the same 2 files from before the upgrade:
   000-default.conf
   testmwtdb.com

However, whether I enter localhost or [www.testmwtdb.com](www.testmwtdb.com), I get to the default index file in the var/www directory, not the site located at var/www/testmwtdb directory.  

Additionally, the command "a2dissite testmwtdb.com" returns the error message "ERROR: site testmwtdb.com does not exist!"

I get the same error message if I use the command a2ensite to try to enable the additional site.

Did this upgrade zap some of my Apache files?  Has anyone else had this same issue?

---

### Post by Martin_Corrigan on 2013-10-22
I figured it out.  Part of the upgrade to the 13.10 upgraded my Apache from 2.2 to 2.6.  With this version of Apache, Virtual Hosts files must end with .conf.  

I changed the name of my file in the "sites-available" directory from "testmwtdb.com" to "testmwtdb.conf", then removed the redirect link from the "sites-enabled" directory.  After that, the en2site command worked with no error and after doing a service reload, I can now access my alternate site.

---

### Post by SeijiSensei on 2013-10-22
You can revert to the previous behavior if you care by editing the Include directive at the bottom of apache2.conf.  It now reads:

```
# Include the virtual host configurations:
IncludeOptional sites-enabled/*.conf

```

If you remove the ".conf" from that directive and restart Apache it will recognize any file in sites-enabled.

---

### Post by wblogan2 on 2013-10-22
The release upgrade to 13.10 from 13.04 and from Apache2.2 to 2.4 positively "zapped" my configuration of enabled sites so that I am forbidden from accessing the pages. Something other than the solutions already mentioned and the group owner and permissions changed. I have even done a purge and re-install of LAMP on one of my machines and still can not find how to enable virtual sites. When I first copied and modified 000-default.conf in sites-available, then ran the a2 commands it would not enable the available site. I had already attempted ommitting the .conf extension from 000-<mysite>.conf, so I altered the apache.conf file as recommended, and now it enables the site (putting the symlink in the sites-enabled folder), but after reloading the service I still get the forbidden error when I attempt to access the site. Furthermore, I can find nothing in the Apache2.4.6 documentation that even gives me a clue what has changed. If I knew how to fallback to Apache2.2.22(Ubuntu) I would at this point. Can anyone give me advice on doing that?

---

### Post by SeijiSensei on 2013-10-22
I think the bigger problem is the definition of the default file.  In earlier versions like 12.04LTS, it had a much more extensive set of directives.  Try replacing the contents of 000-default.conf with this block taken from the 12.04 default configuration:

```

<VirtualHost *:80>
        ServerAdmin webmaster@localhost

        DocumentRoot /var/www
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>
</VirtualHost>

```

I run CentOS on all my servers, since RedHat is very conservative about making changes.  I don't see any reason to use something other the 12.04LTS Server Edition on Ubuntu servers for the same reason.

---

### Post by wblogan2 on 2013-10-22
> **SeijiSensei said:**
> Try replacing the contents of 000-default.conf with this block taken from the 12.04 default configuration:

Tried it with the configuration running on a machine running 13.04 which has not been upgraded to 13.10 and has been running Xubuntu since a fresh install of 12.04 (and is the same configuration I am running under Ubuntu 13.04 and Linuxmint 15). I get the same "Forbidden" error. The apache2 error logs say that the client was denied due to server configuration. Not very helpful.

Thanks for the suggestion.

---

### Post by Dread Knight on 2013-10-24
This apache version is so uber crap. I simply can't get symlinks to work so far, wasted a lot of hours instead of doing actual work *sigh* Really disappointed.

---

### Post by wblogan2 on 2013-10-24
Check out [http://www.linuxquestions.org/questions/showthread.php?p=5051629#post5051629](http://www.linuxquestions.org/questions/showthread.php?p=5051629#post5051629). HTH.

---

