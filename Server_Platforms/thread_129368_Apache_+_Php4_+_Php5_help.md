---
title: "Apache + Php4 + Php5 help"
date: 2006-02-13
forum: Server Platforms
---

### Post by djvishnu on 2006-02-13
I need to install php5 for some new functions it can provide, but i also need to keep php4 installed.

I dont think this is such a big case, just parse the .php through php4 and .php5 through php5. What im wondering about is how to do this with ubuntu, is it possible use use the php5 packages provided in the repos for this? (maybe force it through somehow? And how do i set different config files for php5?)

I can't imagine beeing the first to want to do this, anyone got any tips?

---

### Post by djvishnu on 2006-02-15
I have now gotten this far on my own:

I am using the php4 apache mod debs from the repos, and have compiled php5 and made a deb (with checkinstall) that installs to /opt/php and config files to /etc/php5-conf

I feel i am getting closer to what i want, but the only thing i dont know how to do is some of the apache configuration.

The Apache config for php4 is like this:
LoadModule php4_module /usr/lib/apache2/modules/libphp4.so
AddType application/x-httpd-php .php

If i just load php5 like this:
LoadModule php5_module /usr/lib/apache2/modules/libphp5.so
how do i tell apache (through a AddType diective?) to use php5 for the .php5 files?

Any help would be greatly appreceated!
Thanks

---

