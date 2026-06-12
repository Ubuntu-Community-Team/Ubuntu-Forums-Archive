---
title: "Ubuntu Server"
date: 2009-07-08
forum: Server Platforms
---

### Post by georgerobbo on 2009-07-08
I'm considering whether to install Ubuntu server. I currently use IIS 7, 3.5 net Framework, PHP and MS SQL on a seperate machine as a temporary development server. But since Visual Studio has a http server built in with .net and SQL support I no longer need it. 
 
The setup on Ubuntu server looks rather simple, although I have not used it before. I just have a few issues:
 
_Network Setup_
 
I do not use a DHCP server because my router is unreliable, so how easy is it to setup manual IP address, subnet mask and DNS server settings? 
 
I have had issues with Samba before in the past when using a desktop edition of Ubuntu and my Windows machines were constantly denied access to certain directories despite setting all the permissions. Is the Samba and File Sharing Server easy to setup and install? 
 
_LAMP_
 
I have read many topics when people have said that the default installation of LAMP is not suitable for external access, only in house development. Is it the case with Ubuntu Server, if so, how do you configure LAMP to be secure for external access?
 
Does the default installation of LAMP include PHPMYADMIN? If not, how can I install it and configure it.
 
_Maintainance_
 
Does Ubuntu server automatically download and install updates, or is it a process which must be done via the command line?
 
I've also heard a lot about webmin, does it work very well? Is it easy to install and setup. 
 
 
 
 
I know this is a bit of a tall order for you to answer, but any replies would be great.

---

### Post by TwiceOver on 2009-07-08
I'll do my best, but I don't consider myself a pro or anything.

Networking - Setting up a static IP is very easy, do a google search for ubuntu server static IP and you'll find the instructions.  It is as simple as editing a conf file and changing a few lines.  EDIT:  You'll also want to remove the dhcp3-client package as there has been a flaw since 8.x where DHCP overwrites the static address.

Samba - Can get kinda tricky.  I've never really had a problem with file permissions, a little research will go a long way to helping you understand Samba better

LAMP - As far as I know the LAMP install in Ubuntu's tasksel process (launched at the end of the server install) is the preferred method to get Apache, MySQL, PHP up and running.  I've never had a problem with any of my LAMP servers.

PHPMyAdmin - Is not installed with LAMP.  The install is fairly easy.  Download PHPMyAdmin, extract to the web directory you want to use, edit your php.ini to allow for higher memory usage.  Good to go.  There's probably instructions out there somewhere.

Maintenance - Look for instructions on apt-get update and apt-get upgrade.  The first refreshes your repository listings and the second runs all of the updates.  There are also ways to update single packages, you'll want to do some research on this.  Also look into rotating your logs.  You'll want to create a cron job to rotate your logs so you have some real history without huge log files.

Webmin - Is great.  Easy to set up, can administrate multiple tasks of your ubuntu server right from a web console.  I still prefer the command line, but it does come in handy every now and again.  Also useful for setting up Samba, and I use it rather than PHPMyAdmin.

Hope that helps.

---

### Post by georgerobbo on 2009-07-08
Thats great help. Thanks very much. =)

---

