---
title: "Installing Civic-CMS"
date: 2009-02-17
forum: Server Platforms
---

### Post by MrOreo on 2009-02-17
I have been attempting to install Civic CMS on my Ubuntu Server. Currently this is the error I receive upon going to the main page.

Warning: include(APPLICATION_HOME/html/sections/viewSection.php) [function.include]: failed to open stream: No such file or directory in /var/www/civic-cms/home.php on line 8

Warning: include() [function.include]: Failed opening 'APPLICATION_HOME/html/sections/viewSection.php' for inclusion (include_path='.:/usr/share/php:/usr/share/pear') in /var/www/civic-cms/home.php on line 8'

I have never installed a CMS or used PHP much so this is all new to me. If anyone has any advice or wants me to look into anything and post back, I am going to be checking this thread regularly.

Mr. Oreo

---

### Post by R.Bucky on 2009-02-17
Check out the file permissions on the /html/sections/viewSection.php file. Go into the directory and right-click the viewSection.php file. Set it to Read and Write for all. Then, try to install.

---

