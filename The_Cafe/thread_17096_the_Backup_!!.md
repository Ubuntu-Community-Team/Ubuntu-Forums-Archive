---
title: "the Backup !!"
date: 2005-02-25
forum: The Cafe
---

### Post by dejavu on 2005-02-25
i used Synaptic for updates and download goodies but what i need to know is where all the downloads are kept and alll the dependencies along with it ... 

my ubuntu system got corrupted and i had to install it again ... i was not able to save any of the downloads and updates i did from Synaptic .... so i need to know a way as welll to save all the downloads in a folder of my choice so that if the system crashes again i might be able to atleast save all the data that i downloaded and then just simply run it again !

---

### Post by TravisNewman on 2005-02-26
all downloaded packages are saved to /var/cache/apt/archives/
you can also backup and restore a list of installed packages by doing

dpkg --get-selections >> make.up.a.filename

and back up the file you made using a floppy or some other device that won't get formatted.
Then when you install the new Ubuntu system do:

dpkg --set-selections << the.filename.you.made.up

and then use dselect to install the software you wanted.

---

### Post by adbak on 2005-02-26
Alternatively, the next time you install Ubuntu, you can set up a separate partition for /var and also for /home.  That way when you have to reinstall, your /var and /home partitions will remain untouched.  Ideally.

---

