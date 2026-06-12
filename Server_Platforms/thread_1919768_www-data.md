---
title: "www-data"
date: 2012-02-03
forum: Server Platforms
---

### Post by dwlamb on 2012-02-03
I am a newb to servers and Linux.  I have an Ubuntu system as a development environment for PHP web applications programming.  I am by no means well versed in networks and Apache.

Lately I have incurred a permisisons problem with files in /var/www.  While running install scripts for package installations such as OpenCart or Joomla directories or individual files in a directory have the owner changed to www-data.  Running the install packages is done in the browser using the installation scripts that the CMS includes.  It is also happening, though not frequently, if I copy the contents of an update patch from a temporary directory to a working site directory.  The source of the temporary patch is owned by my user name.  

This is not supposed to be the case according to any research I do or run the installation using another directory as the root of a new installation.  It is as though Apace is setting the user to www-data or some other unexpected change is taking place.

What can I do to avoid this?  I know the answer after it happens is to run chown as sudo or something similar, but I wish to prevent it in the first place.

---

