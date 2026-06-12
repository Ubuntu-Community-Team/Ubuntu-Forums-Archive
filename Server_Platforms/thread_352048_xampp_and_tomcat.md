---
title: "xampp and tomcat"
date: 2007-02-02
forum: Server Platforms
---

### Post by docetes on 2007-02-02
hi

is it possible to install xampp into a different directory thean opt?
I want to have tomcat for servlets and JSF and apache for php

Thanks,
Dave

---

### Post by neverett on 2007-02-02
When you do this command:

tar xvfz xampp-linux-1.5.5a.tar.gz -C /opt

/opt is the directory.  Change it to the directory you want to install it in.  Remember when starting xampp... the new command would be:

sudo <directory>/lampp/lampp start

Let me know if that works!

---

### Post by docetes on 2007-02-02
no i've tried that before. xampp tries to find files in in /opt/lampp 
i'df have to edit all the files

---

### Post by neverett on 2007-02-02
I'll see if I can find out from a friend.  Good luck though!!!

---

### Post by SemperNoob on 2008-01-27
I have installed Xampp for Linux in its default location and am also looking for Tomcat.  I started to set it up through synaptic but when I did so synaptic wanted to instal apache2 as well so it looks like synapic does not recognize Xampp.  Does anyone know if there is a reasonable install path for Tomcat into Xampp on an Ubuntu (desktop) machine or if Synapitc can be made to see a Xampp for linux installed lampp stack?  
(new to posting so let me know if this should have been a new thread.)
Thanks!

---

