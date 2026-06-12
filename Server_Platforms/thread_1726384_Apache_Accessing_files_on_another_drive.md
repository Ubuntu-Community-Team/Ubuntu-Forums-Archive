---
title: "Apache: Accessing files on another drive"
date: 2011-04-11
forum: Server Platforms
---

### Post by skclewis on 2011-04-11
I've searched other forums and message archives but can't seem to find a situation like mine.  I'm a relative newbie to Ubuntu server and Apache so bear with me.

Having retired I decided to get back into doing some web development work.  So I decided to set up a development environment without access to the Internet.  I had a box with Ubuntu Maverick already installed so I decided to "pimp" it up to use as my server. The box had 2 500MB SATA drives and since it is also used by the family I compromised and left Windows 7 running on its own drive, while I installed Ubuntu Maverick on its own drive but still have grub so I can boot to either OS.  To make my server, I installed a 3rd SATA 500MB drive and an additional 2GB RAM.  Following the information from this site and others, I installed Ubuntu Server on top (or is it under:confused:) my Ubuntu desktop.  I installed Apache, MySQL and PHP and all went well.  My issue is that I want to use the third drive to hold the website development files as well as other environments such as Wordpress, Drupal, and Joomla without having to put them under /var/www.  I tried that with Wordpress as that is their install instructions but I could not access the files to modify them without logging in as root.  Is there a way I can put some type of reference so when I access localhost via the brower it will point to the directory on my other drive?

---

### Post by Ryan Dwyer on 2011-04-11
Assuming your other drive is mounted at /other, you can edit /etc/apache2/sites-available/default and change the DocumentRoot to something like /other/www.

You'll need to use sudo to edit the config file. If you're not familiar with using the command line then you'll want to learn that before you start running servers.

---

### Post by skclewis on 2011-04-17
Thanks Ryan I'll give it a try.  I am familiar with sudo so no problem there. :D

---

