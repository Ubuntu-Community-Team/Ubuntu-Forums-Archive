---
title: "phpmyadmin Tracking: Disabled, please help"
date: 2010-10-23
forum: Server Platforms
---

### Post by feelexit on 2010-10-23
after I login phpmyadmin, i see this warning message at the bottom of hte page.

"The additional features for working with linked tables have been deactivated. To find out why click here."

$cfg['Servers'][$i]['tracking'] ... 	not OK [ Documentation ]
Tracking: Disabled

I edit /etc/phpmyadmin/config.inc.php file, and added this line ($cfg['Servers'][$i]['tracking'] = 'pma_tracking';)

I checked my database, i have "phpmyadmin" database and I have "pma_tracking" table in that database.

after I reboot my server, that warning message still there.  anybody knows how to fix it.

if i m not able to fix it, is it gonna cause problems?

---

### Post by paulsp on 2010-10-23
I've had this message for years. Never bothered to find out what it meant; never experienced any problems because of it. I would not worry about this.

---

### Post by abackstrom on 2011-01-27
Assuming you want actually use these features, make sure you [create the necessary PMA tables]("http://www.phpmyadmin.net/documentation/#linked-tables") and run [these GRANT statements]("http://www.phpmyadmin.net/documentation/#authentication_modes"), plus add the config settings ([FONT="Courier New"]$cfg['Servers'][$i]['pmadb'[/FONT]] et al) to your config.inc.php.

Also note that the settings are cached in your session, so you may have to re-login to see the changes take effect.

---

### Post by davecgs on 2012-01-17
I spent a few hours on this and I know more about this functionality than I ever wanted to know including some of the codebase in phpmyadmin.  PhpmyAdmin could not have made this situation more miserable to deal with.  

In any case, the error you are getting is because the default installation does not include the statement for the tracking field so you can uncomment all day long and set up tables all day long and setup the pma user until you turn blue in the face -- or red in my case -- and check endless helpless users forums and get nowhere fast. 


Anyway. you need to add this statement to the etc/phpmyadmin/config.inc.php
This is because your installation did not include the statement in the default file.  Not nice. 

$cfg['Servers'][$i]['tracking'] = 'pma_tracking';

THis will enable the all trivial tracking feature to allow you to create separate versions of the same table to compare changes.  Joy -- all that for this feature:)

These advanced features really are annoying.  The fact that you have to create a table structure, add the pma user and then modify a config.inc.php file is nothing shore of sloppy development.  There is no need to go through this much headaches for a few features IMHO and I am not a newbie by any means.

---

