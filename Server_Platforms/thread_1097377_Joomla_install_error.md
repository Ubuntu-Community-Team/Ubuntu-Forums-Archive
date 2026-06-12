---
title: "Joomla install error"
date: 2009-03-15
forum: Server Platforms
---

### Post by lakelovers on 2009-03-15
I followed the Joomla CMS, install for Ubuntu that I found on [www.blog.highub.com](www.blog.highub.com), which has a number of success comments. Everything seems to go okay until I got to the final step to install Joomla on my local host by addressing it in the Firefox address line ([http://localhost/joomla/](http://localhost/joomla/)) at which point I got the following errors:

Warning: require_once(/var/www/joomla/includes/defines.php) [function.require-once]: failed to open stream: No such file or directory in /var/www/joomla/index.php on line 21

Fatal error: require_once() [function.require]: Failed opening required '/var/www/joomla/includes/defines.php' (include_path='.:/usr/share/php:/usr/share/pear') in /var/www/joomla/index.php on line 21

What step did I get wrong? Or, how do I correct it?

---

### Post by machinakias on 2009-03-17
> **lakelovers said:**
> I followed the Joomla CMS, install for Ubuntu that I found on [www.blog.highub.com](www.blog.highub.com), which has a number of success comments. Everything seems to go okay until I got to the final step to install Joomla on my local host by addressing it in the Firefox address line ([http://localhost/joomla/](http://localhost/joomla/)) at which point I got the following errors:

Warning: require_once(/var/www/joomla/includes/defines.php) [function.require-once]: failed to open stream: No such file or directory in /var/www/joomla/index.php on line 21

Fatal error: require_once() [function.require]: Failed opening required '/var/www/joomla/includes/defines.php' (include_path='.:/usr/share/php:/usr/share/pear') in /var/www/joomla/index.php on line 21

What step did I get wrong? Or, how do I correct it?

first of all,did it finish the installation ok? any errors during the install? 
second,did you deleted the "installation" folder? you have to...

third, try to reinstall everything from scratch....foolow joomla.org instructions....

and then,try to ask the joomla team....

double check the permissions,the file names,the paths etc....

hope it helps....

---

### Post by daboroe on 2009-03-17
that file it is trying to include does not exist. that is your issue.

---

### Post by bsmith1051 on 2009-03-26
Where did you unpack the Joomla ZIP, e.g. did you put it in /var/www/joomla?  If you point the Ubuntu Archive Manager at /var/www and then click extract it won't automatically create the 'joomla' sub-folder.  Instead it will put it in the root folder, /var/www, and so you would need to open [http://localhost/](http://localhost/) instead of [http://localhost/joomla/](http://localhost/joomla/)

---

