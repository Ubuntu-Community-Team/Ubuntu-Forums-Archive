---
title: "Webserver advice"
date: 2009-06-16
forum: Server Platforms
---

### Post by hardcoregenie on 2009-06-16
Please be patient guys and gals I am relatively new to ubuntu and just need some advice.
I am a web developer that has branched out on his own and therefore has suddenly the need for a internal webserver. 
I have used ubuntu desktop before but not too extensively and to this point I have simply installed xampp on my vista machine :(.
I have installed Ubuntu 9.04 server on a spare machine and have managed to give a static ip address, alter the hosts file and install manually the lamp components.
At this point I don't need anyone outside accessing it, it's just for me to work on and experiment with.
Have you made any changes to the default setup that would help a definite newbie.
I was thinking about moving the default documentroot etc for easier backup etc.
Any advice would be greatly appreciated.

---

### Post by ad_267 on 2009-06-16
I've installed Apache, PHP and MySQL on my desktop for testing websites, and haven't done anything more than what you have already. One thing to remember is to use "sudo a2enmod" to enable Apache modules rather than editing config files. You could also install phpmyadmin if you want an easy web interface for managing databases.

---

### Post by hardcoregenie on 2009-06-17
Thanks for the quick response. In setting up apache for virtual hosting, do I alter the line localhost *:80 and replace the * with the dedicated IP address of the server?
I am assuming that as you have set it up on your local machine you do not have to worry about altering that line.

---

### Post by ad_267 on 2009-06-17
I think you can leave the * there, I don't have a lot of apache configuration experience though so hopefully someone else can be more helpful.

---

