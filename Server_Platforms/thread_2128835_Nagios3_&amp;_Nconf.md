---
title: "Nagios3 &amp; Nconf"
date: 2013-03-24
forum: Server Platforms
---

### Post by Gareth_2007 on 2013-03-24
Good afternoon,

I'm currently following this guide on installing nagios3 & nconf [Click Me]("http://community.spiceworks.com/how_to/show/1802-install-nagios-on-ubuntu-10-04-with-nconf")

Both nagios & nconf are running, but when i get to step 10

```

10

Almost there. Using sudo, open up /var/www/nconf/ADD-ONS/deploy_local.sh and make the following changes to paths:

OUTPUT_DIR="/var/www/nconf/output/"
NAGIOS_DIR="/etc/nagios3/"
...
/etc/init.d/nagios3 reload
```

And run - /etc/init.d/nagios3 reload

i get an error - 

```
 * Reloading nagios3 monitoring daemon configuration files nagios3              
Nagios Core 3.4.1
Copyright (c) 2009-2011 Nagios Core Development Team and Community Contributors
Copyright (c) 1999-2009 Ethan Galstad
Last Modified: 05-11-2012
License: GPL

Website: http://www.nagios.org
Reading configuration data...
Error: Cannot open resource file '/etc/nagios3/resource.cfg' for reading!
Error in configuration file '/etc/nagios3/nagios.cfg' - Line 472 (Check result path is not a valid directory)
   Error processing main config file!



***> One or more problems was encountered while processing the config files...

     Check your configuration file(s) to ensure that they contain valid
     directives and data defintions.  If you are upgrading from a previous
     version of Nagios, you should be aware that some variables/definitions
     may have been removed or modified in this version.  Make sure to read
     the HTML documentation regarding the config files, as well as the
     'Whats New' section to find out what has changed.

 * errors in config!
                                                                         [fail]
```

Line 472 reads - check_result_path=/var/lib/nagios3/spool/checkresults

Any suggestions?

cheers

---

### Post by Gareth_2007 on 2013-03-24
Sorry to waste a thread,

While in nagios.cfg and looking at line 472 this was displayed above -

# Note: Make sure that only one instance of Nagios has access
# to this directory!

so 
sudo /etc/init.d/nagios3 stop
sudo /etc/init.d/nagios3 start

and everythings fine :)

---

