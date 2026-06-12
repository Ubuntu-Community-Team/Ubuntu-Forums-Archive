---
title: "Mailman install help"
date: 2008-06-03
forum: Server Platforms
---

### Post by robbrandt on 2008-06-03
Severely confused and frustrated. I want to do a mailman installation that will be used by any of the virtual hosts I am going to be adding.  I've found a variety of howtos on the ubuntu sites, and none of them are working for me.  Most lately I am getting 403 Forbidden when I try and access the mailman URL.  I am using postfix for mail.

Does anyone have a howto that works for my purposes?  I am on 8.04.  I'm not after an installation that only works on one particular subdomain.

Thanks.

---

### Post by heebus on 2008-06-03
When you compile mailman make sure you put the gid of your web user.  Since you're using postfix you'll want to give the mail gid as well.  

One of my many mailman installs gave me a bunch of permission issues, this should clear it up.  Please note, I did this on a Solaris 10 box, but I don't really see much changing.  


 mkdir /usr/local/mailman
 chown -R mailman:mailman /usr/local/mailman
 cd /usr/local/mailman
 chgrp mailman .
 chmod a+rx,g+ws .
 cd ~/mailman-2.1.9/
./configure --with-mail-gid=postfix --with-cgi-gid=web; make; make install

Once its compiled and installed you should run the check-perms binary.  
~mailman/bin/check-perms -f

Apache:
 pico /etc/apache2/httpd.conf
 ScriptAlias /mailman /usr/local/mailman/cgi-bin/
 <Directory /usr/local/mailman/cgi-bin/>
     AllowOverride None
     Options ExecCGI
     Order allow,deny
     Allow from all
 </Directory>
 Alias /pipermail /usr/local/mailman/archives/public/
 Alias /icons  /opt/csw/apache2/share/icons  ** This will depend on your apache config.  

As for some postfix configs with mailman

 pico /usr/local/mailman/Mailman/Defaults.py
 MTA = 'Postfix'
 DEFAULT_EMAIL_HOST = 'hostname'
 DEFAULT_URL_HOST = 'hostname'
 POSTFIX_ALIAS_CMD = '/sbin/postalias' * Just confirm their locations with a which postalias
 POSTFIX_MAP_CMD = '/sbin/postmap'

---

### Post by robbrandt on 2008-06-03
I was really hoping to stick with the ubuntu mailman deb, as that would get updates automatically from apt-get upgrade.  Or maybe that's my problem?!  Is there any other way than compiling my own?

---

### Post by heebus on 2008-06-03
I find somethings are better to compile on your own.

Run the check-perms -f

---

