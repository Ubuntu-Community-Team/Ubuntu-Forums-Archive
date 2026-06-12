---
title: "[SOLVED] I broke .php"
date: 2008-11-15
forum: Server Platforms
---

### Post by volkswagner on 2008-11-15
After running through the install of linPHA, I used Webmin to edit some php configuration.  Webmin originally "said" it was not setup to configure .php.  I allowed the following files to be used.  

```

PHP Configuration 	
Configuration file 	Purpose 	Actions
/etc/php5/apache2/php.ini 	Configuration for mod_php 	
/etc/php5/cli/php.ini 	Configuration for command-line scripts 
```	


Originally the Webmin paths were incorrect (referred to php4).  There was another file listed that I could not find, so I eliminated it.  Everything was working for a few days.  I even added photos and directories to linPHA.  I had linPHA running for a few days.  I am not sure what caused the problem.

Currently the only site that works is running only HTML code.  I have several other virtual hosts that time out.  They all run .php (punBB, Twiki, SquirrelMail, SQL-Ledger) so I think that is the problem.

I did not find any relevant errors in apache error log.  I am not sure where else to look.  

I even tried a reboot to see if an update needed to reboot.  The same problem exists, all php sites are timing out.

I manually edited /etc/php5/apache2/php.ini to change the max memory usage to 32megs from 8megs.

One other thing I need to check is SQL-ledger activity.  I did set someone loose to play with it.  I will check with them to see if it stopped working during a session.

Apache2 error log:

```

[Sun Nov 09 06:25:41 2008] [notice] suEXEC mechanism enabled (wrapper: /usr/lib/apache2/suexec2)
[Sun Nov 09 06:25:44 2008] [notice] Apache/2.0.55 (Ubuntu) PHP/5.1.2 mod_ssl/2.0.55 OpenSSL/0.9.8a mod_perl/2.0.2 Perl/v5.8.7 configured -- resuming normal operations
[Mon Nov 10 12:42:06 2008] [error] [client 69.206.148.66] File does not exist: /usr/lib/sql-ledger/images, referer: http://ledger.volkswagner.com/login.pl
[Mon Nov 10 12:42:27 2008] [error] [client 69.206.148.66] File does not exist: /usr/lib/sql-ledger/images, referer: http://ledger.volkswagner.com/am.pl?login=vaughn&sessionid=1226338945&action=company_logo&path=bin/mozilla
[Mon Nov 10 12:59:01 2008] [error] [client 71.246.183.105] File does not exist: /usr/lib/sql-ledger/images, referer: http://ledger.volkswagner.com/login.pl
[Mon Nov 10 13:00:10 2008] [error] [client 71.246.183.105] File does not exist: /usr/lib/sql-ledger/images, referer: http://ledger.volkswagner.com/am.pl?login=vaughn&sessionid=1226340008&action=company_logo&path=bin/mozilla
[Mon Nov 10 18:35:22 2008] [notice] Graceful restart requested, doing restart
[Mon Nov 10 18:35:24 2008] [notice] Apache/2.0.55 (Ubuntu) PHP/5.1.2 mod_ssl/2.0.55 OpenSSL/0.9.8a mod_perl/2.0.2 Perl/v5.8.7 configured -- resuming normal operations
[Mon Nov 10 18:44:07 2008] [notice] Graceful restart requested, doing restart
[Mon Nov 10 18:44:08 2008] [notice] Apache/2.0.55 (Ubuntu) PHP/5.1.2 mod_ssl/2.0.55 OpenSSL/0.9.8a mod_perl/2.0.2 Perl/v5.8.7 configured -- resuming normal operations
[Mon Nov 10 19:06:07 2008] [notice] Graceful restart requested, doing restart
[Mon Nov 10 19:06:08 2008] [notice] Apache/2.0.55 (Ubuntu) PHP/5.1.2 mod_ssl/2.0.55 OpenSSL/0.9.8a mod_perl/2.0.2 Perl/v5.8.7 configured -- resuming normal operations
identify: no decode delegate for this image format `/home/eric/photos/linpha-1.3.4/README'.
identify: no decode delegate for this image format `/home/eric/photos/linpha-1.3.4/README'.
[Tue Nov 11 11:03:50 2008] [error] [client 71.246.183.105] File does not exist: /usr/lib/sql-ledger/images, referer: http://ledger.volkswagner.com/login.pl
[Tue Nov 11 11:05:04 2008] [error] [client 71.246.183.105] File does not exist: /usr/lib/sql-ledger/images, referer: http://ledger.volkswagner.com/login.pl
[Tue Nov 11 11:05:35 2008] [error] [client 71.246.183.105] File does not exist: /usr/lib/sql-ledger/images, referer: http://ledger.volkswagner.com/am.pl?login=vaughn&sessionid=1226419532&action=company_logo&path=bin/mozilla
[Tue Nov 11 11:07:43 2008] [error] [client 71.246.183.105] File does not exist: /usr/lib/sql-ledger/images, referer: http://ledger.volkswagner.com/am.pl?login=vaughn&sessionid=1226419532&action=company_logo&path=bin/mozilla
[Tue Nov 11 11:34:47 2008] [error] [client 71.246.183.105] File does not exist: /usr/lib/sql-ledger/images, referer: http://ledger.volkswagner.com/login.pl
[Tue Nov 11 11:35:11 2008] [error] [client 71.246.183.105] File does not exist: /usr/lib/sql-ledger/images, referer: http://ledger.volkswagner.com/am.pl?login=vaughn&sessionid=1226421309&action=company_logo&path=bin/mozilla
[Sat Nov 15 08:16:52 2008] [notice] Graceful restart requested, doing restart
[Sat Nov 15 08:16:55 2008] [notice] Apache/2.0.55 (Ubuntu) PHP/5.1.2 mod_ssl/2.0.55 OpenSSL/0.9.8a mod_perl/2.0.2 Perl/v5.8.7 configured -- resuming normal operations
[Sat Nov 15 08:51:53 2008] [notice] caught SIGTERM, shutting down
[Sat Nov 15 08:55:31 2008] [notice] suEXEC mechanism enabled (wrapper: /usr/lib/apache2/suexec2)
[Sat Nov 15 08:55:36 2008] [notice] Apache/2.0.55 (Ubuntu) PHP/5.1.2 mod_ssl/2.0.55 OpenSSL/0.9.8a mod_perl/2.0.2 Perl/v5.8.7 configured -- resuming normal operations
[Sat Nov 15 09:30:30 2008] [notice] caught SIGTERM, shutting down
[Sat Nov 15 09:30:33 2008] [notice] suEXEC mechanism enabled (wrapper: /usr/lib/apache2/suexec2)
[Sat Nov 15 09:30:34 2008] [notice] Apache/2.0.55 (Ubuntu) PHP/5.1.2 mod_ssl/2.0.55 OpenSSL/0.9.8a mod_perl/2.0.2 Perl/v5.8.7 configured -- resuming normal operations
```

I renamed the above README file to README.txt, and added the images directory  /usr/lib/sql-ledger/images.  But the problem still persists.

Thanks in advance.

---

### Post by Vegan on 2008-11-15
I have never touched php.ini at all, because it was not important.

You post suggests you installed the mono package nes't pas?

:guitar:

---

### Post by volkswagner on 2008-11-15
> **Vegan said:**
> 

You post suggests you installed the mono package nes't pas?

:guitar:

I have no idea what this means.  I have only heard the reference "mono".  Other than the kissing disease I have no clue.  I am checking google now.

---

### Post by rustutzman on 2008-11-15
Try going into your php.ini file and enable logging and give the log a file name and directory to go into. The php.ini file is pretty well self documented. You might even want to create an empty log file to begin with, 

LinPHA has it's own interface for configuring that's pretty good. I stick to using it.

After enabling logging restart apache and then look for errors. I think at this pooint I'd consider reinstalling php5. Make a backup copy of vital files first.

Russ

---

### Post by volkswagner on 2008-11-16
Thanks for the replies.

I made some changes to php.ini for logging and created the log file.  There was no activity after restarting apache2 and trying to access the sites.

First I should ask how can I be sure the issue is due to php?  

As I mentioned earlier, the sites were all working after making the changes.  It was some time (a few days) later when the sites broke.

Unfortunately I did not make a note of the old directories before making the following changes (see screenshot).

I commented out the cgi reference since I could not find a suitable location.  This may be the problem if the sites can no longer run cgi-scripts.

Where should I point this config to?

---

### Post by volkswagner on 2008-11-16
I think I know what is happening.  Since before the change (within Webmin), php config was not handled by Webmin.  I made the change to allow Webmin to handle the config.  I think this is one of those things where people say "weird things can happen when using Webmin".  This is especially true when the user is a newbie, like me  :) .

Anyway I think I need to config each site individually or revert back to not allow webmin to handle the config.  I don't know how to disallow webmin to handle the config. I also don't know what parameters to add in each virtual host.

Please let me know what I can put in the following (see screen shot).  This will let me test one site to see if I am correct.

---

### Post by rustutzman on 2008-11-16
I think it's just a matter of not using webmin and using the applications own tools to do the configuration. I'm sure your forums have their own configuration page. Is there a reason you're not using that to reconfigure them?

Russ

---

### Post by volkswagner on 2008-11-16
> **rustutzman said:**
> I think it's just a matter of not using webmin and using the applications own tools to do the configuration. I'm sure your forums have their own configuration page. Is there a reason you're not using that to reconfigure them?

Russ

I believe it is a system wide issue.  Perhaps I will take a gander over a Webmin. 

I figured since many people use/recommend Webmin on this forum, they may share some insight.

---

### Post by volkswagner on 2008-11-18
I did not get any replies from the Webmin forum.

I tried reinstalling php5.  No joy there.

I am fearful in reinstalling Webmin.  I am afraid much more will break.

Can anyone tell me how to disable Webmin from handling php config?   

Can anyone tell me where to start?  How can I be sure it is a php issue?

---

### Post by volkswagner on 2008-11-19
Well I removed Webmin.  No joy.

I don't know where to go from here.

Where do I look?

How do I get to the basic route?  How do I confirm what is actually broken?

EDIT-SOLVED:

Boy do I feel stupid.  The only thing that the sites had in common were .php.  Well that was not the issue at all.  It is an issue with DYNdns service.  All of my hostnames were not updated.  The only one that updated was the first or main url.  I must have set something up wrong at DynDns.  I tried to access the sites using my internal address and they WORKED.

Well, thats why they call it DOPE!  What an idiot.

---

