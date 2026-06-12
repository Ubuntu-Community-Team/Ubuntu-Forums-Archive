---
title: "Setting up Ubuntu as an Intranet Webserver"
date: 2006-01-27
forum: Server Platforms
---

### Post by linsanity on 2006-01-27
Unfortunately I'm a stonecold noob when it comes to Linux.  I have a couple of problems that I need help with:  

1)  How do I go about setting up Ubuntu as an intranet webserver?  What I want to do is to set up a server from which XP clients can access the Moodle learning management system as an internal website.

2)  I've also had incredible trouble installing Moodle using Synaptic.  The package downloads but when it installs everything, php5 locks up.  When I try and launch the php.ini file using sudo gedit, the page comes up blank.  When I type in **localhost/moodle/install.php **in the web browser I get a blank page but when I type **//localhost **apache2 is very much alive.  What gives?:confused: 

Ubuntu also installs the Moodle folder in var/lib instead of var/www as specified in the Moodle installation documentation.  Any idea what might be causing this? Or is this the correct configuration for Ubuntu? 

Thanks in advance

---

### Post by ]Nbx*cmD[ on 2006-01-27
Have you installed apache? You can get it by simply apt-get install apache
You'll have to put the websites at /var/www/yourwebdir directory and they'll be accessible by [http://yourserverip/yourwebdir](http://yourserverip/yourwebdir).
To access from other computers you can use ftp yourserverip (first you have to do apt-get install pro-ftpd in the server)

---

### Post by ]Nbx*cmD[ on 2006-01-27
Here's an example of a webserver working: [http://80.25.162.189](http://80.25.162.189)
This is my server's ip, and i can access it in my lan by [http://192.168.2.4](http://192.168.2.4)

---

### Post by linsanity on 2006-01-27
Hi,

Thanks for the info.  I'll give it a go!

---

### Post by LordHunter317 on 2006-01-27
You webserver is installed and working, ignore him.

Try reinstalling moodle on the command-line, using apt-get.  Post any errors that appear (or the whole session).  Post your sources.list as well.

---

