---
title: "Configuration file for pure-ftpd?"
date: 2005-03-10
forum: Server Platforms
---

### Post by pinnockio on 2005-03-10
Hello,

I just switched from gentoo to ubuntu and I wonder where I can set the configuration for pure-ftpd as I can't seem to find any configuration file where I can put variables such as
$SERVER $MAX_CONN $MAX_CONN_IP $DAEMON $DISK_FULL $USE_NAT $AUTH,... .

Kind regards,


Maurits

btw.: how are script generally configured in ubuntu/debian any way (and I mean how you set the configuratin for those scripts, not how to add a script to a bootlevel).

---

### Post by lildude on 2005-04-25
Hi Maurits

I too used to use Gentoo and was also stumped by this exact question... where's the config file for pure-ftpd?  Well, I eventually found this out by trawling through the scripts, starting with the RC script.  It seems Ubuntu starts pure-ftpd by calling a wrapper script (/usr/sbin/pure-ftpd-wrapper).  This wrapper script implements the require options.  Now before you rush off to edit this file... don't... all this file does is runs through each file in /etc/pure-ftpd/conf and reads in the settings.  Unfortunately, that means for every setting that you wish to implement, you need to create a file with the name of the option and the setting you want.  If the option is to just add a flag (eg -N), then the file will contain "yes".

So, if you wish to implement "$SERVER" from gentoo, you need to create /etc/pure-ftpd/conf/Bind and put "<port>" (eg 21)  or "<ip>,<port>" (eg 192.168.0.1,21) into the file.  You will need to do this for all the settings.

Have a look through the wrapper script to see what filenames it looks for and what values it expects to find in the file. 

HTH

---

