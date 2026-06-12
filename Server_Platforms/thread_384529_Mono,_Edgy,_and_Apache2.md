---
title: "Mono, Edgy, and Apache2"
date: 2007-03-14
forum: Server Platforms
---

### Post by qwert231 on 2007-03-14
So I found a few walk-throughs on google about installing Mono on linux/ubuntu. I've gotten to the point where I can put in this address:
[http://localhost/test/1.1/asp.net/browsercaps.aspx](http://localhost/test/1.1/asp.net/browsercaps.aspx)

And see a rendered page. GREAT!

Now, if I put an .aspx page in the folder for one of my sites ([www.greatwhitedata.com](www.greatwhitedata.com)) Firefox asks to download it, and Internet Explorer gives me an error.

Obviously mod_mono is not processing the request. I looked in \etc\apache2\mods-available and \etc\apache2\mods-enabled, but mod_mono is in neither. I do have mod_mono.conf in \etc\apache2\ but I don't think this is where it should be.

Any thoughts?

---

### Post by Nikron on 2007-03-14
Umm...  I think your page is working...  It's susposed to show client browser information, right?

---

### Post by qwert231 on 2007-03-14
Hmm... well, that is the test page. I want to have this page work:
[http://www.greatwhitedata.com/cSharpDemoData.aspx](http://www.greatwhitedata.com/cSharpDemoData.aspx)

---

### Post by qwert231 on 2007-03-14
Should I get this:

mark@linux800:/etc/apache2$ sudo apt-get install libapache2-mod-mono
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libapache2-mod-mono: Depends: mono-apache-server (< 1.1.14) but it is not going to be installed or
                                mono-apache-server2 (< 1.1.14) but 1.1.17.1-2 is to be installed
E: Broken packages

mark@linux800:/etc/apache2$ sudo a2enmod mod_mono
This module does not exist!

---

### Post by Nikron on 2007-03-14
Don't worry, it's a broken package.  It did that for me too.  Unless my system is similarly broken..

---

### Post by qwert231 on 2007-03-15
So, for now, I'm trying to get my ASP.Net page to work in a virtual folder, here:
[http://www.greatwhitedata.com/mono/cSharpDemoData.aspx](http://www.greatwhitedata.com/mono/cSharpDemoData.aspx)
(BTW, I also have BlueDragon and PHP running on my site, you can look here: [http://www.greatwhitedata.com/samples.php](http://www.greatwhitedata.com/samples.php))

I'm trying to use this Virtual Hosts file:
#
#  [www.greatwhitedata.com](www.greatwhitedata.com) (/etc/apache2/sites-available/www.greatwhitedata.com)
#
<VirtualHost *>
        ServerAdmin [email]qwert231@yahoo.com[/email]
        ServerName  [www.greatwhitedata.com](www.greatwhitedata.com)
        ServerAlias greatwhitedata.com

        # Indexes + Directory Root.
        #DirectoryIndex index.php
        DocumentRoot /web/GreatWhite/

        <Directory /web/GreatWhite/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride All
                Order allow,deny
                Allow from all
                DirectoryIndex index.html index.php index.htm
        </Directory>



Alias /mono "/web/GreatWhite/mono"
AddMonoApplications default "/mono:/web/GreatWhite/mono"
<Location /mono>
   SetHandler mono
</Location>

        ScriptAlias /bin/ /web/GreatWhite/mono/bin/
        <Location /bin>
                SetHandler mono-ctrl
        </Location>

        # Logfiles
        ErrorLog  /home/www/GreatWhite/logs/error.log
        CustomLog /home/www/GreatWhite/logs/access.log combined
</VirtualHost>

---

