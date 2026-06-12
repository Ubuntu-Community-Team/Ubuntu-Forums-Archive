---
title: "Error installing Nagios3 on 8.10"
date: 2009-01-09
forum: Server Platforms
---

### Post by mercerm on 2009-01-09
I just installed 8.10 and upgraded the repositories. I then installed Nagios3 and when i go to chech the install i get this error:
root@lbhweb1:/home/administrator# nagios3 -v nagios.cfg

Nagios 3.0.2
Copyright (c) 1999-2008 Ethan Galstad ([http://www.nagios.org](http://www.nagios.org))
Last Modified: 05-19-2008
License: GPL

Reading configuration data...

Error: Cannot open main configuration file '/home/administrator/nagios.cfg' for reading!

***> One or more problems was encountered while processing the config files...

     Check your configuration file(s) to ensure that they contain valid
     directives and data defintions.  If you are upgrading from a previous
     version of Nagios, you should be aware that some variables/definitions
     may have been removed or modified in this version.  Make sure to read
     the HTML documentation regarding the config files, as well as the
     'Whats New' section to find out what has changed.

root@lbhweb1:/home/administrator# Error: Cannot open main configuration file '/home/administrator/nagios.cfg' for reading!
bash: Error:: command not found


Any ideas?

Thanks

---

### Post by mercerm on 2009-01-09
Figured it out!

Forgot the sudo command ](*,) I figured since i already typed sudo su after i logged in i wouldn't need it. I am such a noob!!

---

### Post by ginda.armada on 2009-01-14
hi can you teach me how to configure and save a *.cfg files for nagios in terminal? whats the command line? thanks

---

### Post by kid23lopez on 2009-02-18
I'm running the command using sudo and am still getting the "... cannot open configuration.." message. 
Any ideas?

---

