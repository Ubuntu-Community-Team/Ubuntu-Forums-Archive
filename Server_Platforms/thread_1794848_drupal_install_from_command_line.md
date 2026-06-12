---
title: "drupal install from command line"
date: 2011-07-01
forum: Server Platforms
---

### Post by bigmonmulgrew on 2011-07-01
Hi guys

Im currently learning to scrip on a ubuntu 11.04 server vm
As you may have noticed  if you have seen my recent posts.

Is it possible to complete a drupal installation and change the configuration from the comman line or a script.

Id like to be able to automate the process of  installing and configuring drupal.
I should say that this is quite a bit beyond me. Ive not long started learning scripting.

---

### Post by rudelgurke on 2011-07-04
Don't think it's possible because Drupal expects various user input (site name / URL / admin mail etc.)

But you maybe can do a basic installation, export the DB and then change values at the exported DB dump to match your needs if you want to do a mass installation.
Should be possible to do this from command line with some "mysql -u ... -p ... -e 'source script.sql' " commands.
Then distribute the Drupal files and correct the configuration in the settings file.
Though - leaves the problem of passwords (admin & DB login) not that each site you're setting up uses the same login data.

---

### Post by tgalati4 on 2011-07-04
Drupal installation is semi-automatic.  You copy the Drupal directories to the correct places (/var/www/myDrupalsite for instance) then log into the web page and start the installation process.  There are several tutorials on the web.  The installation process is a series of scripts already written.  I suppose you could run them manually at the command line.  There are efforts to make Drupal installation more automated, but each installation requires customization that may be beyond the capability of a simple install script.

---

