---
title: "Problem installing nagios 2.7"
date: 2007-02-23
forum: Server Platforms
---

### Post by tai.san on 2007-02-23
Hi people, 

     i have a problem installing Nagios 2.7 on ubuntu 6.10 feist. When i run configuration checker send me this error...

> 
user@localhost:/etc/nagios/bin$ sudo ./nagios -v /etc/nagios/etc/nagios.cfg 

Nagios 2.7
Copyright (c) 1999-2007 Ethan Galstad ([http://www.nagios.org](http://www.nagios.org))
Last Modified: 01-19-2007
License: GPL

Reading configuration data...

Error: Could not find any contact matching 'nagcmd'
Error: Could not expand member contacts specified in contactgroup (config file '/etc/nagios/etc/localhost.cfg', starting on line 122)

***> One or more problems was encountered while processing the config files...

     Check your configuration file(s) to ensure that they contain valid
     directives and data defintions.  If you are upgrading from a previous
     version of Nagios, you should be aware that some variables/definitions
     may have been removed or modified in this version.  Make sure to read
     the HTML documentation regarding the config files, as well as the
     'Whats New' section to find out what has changed.


Please tell me what i can do?

Regards.

---

