---
title: "Need some direction and help..."
date: 2006-05-18
forum: Server Platforms
---

### Post by Shadowline on 2006-05-18
I decided to try out Ubuntu Center today and everything went good up until I went to start the web based installer portion, when I open [http://127.0.0.1/center](http://127.0.0.1/center) Firefox try's to download a phtml file. Obviously this isn't supposed to happen. I posted about this problem in the Ubuntu Center section and TTT travis (the developer of Ubuntu Center) suggested that it was a problem with php and apache2 not working correctly together. Any one got any idea's ?   ](*,) 

link to original post: [http://ubuntuforums.org/showthread.php?t=178788](http://ubuntuforums.org/showthread.php?t=178788)

---

### Post by kokiri on 2006-05-18
just generally off the top of my head you'll probably need mod_apache_php or mod_apache2_php5 depending on which version of php you have installed otherwise apache won't know that php is installed or how to talk to it

edit and yes, you can "sudo apt-get install mod_apache2_php" or "sudo apt-get install mod_apache2_php5" to install them I believe

if those are installed, you will need to declare php and phtml as php handled file types in the apache config file, [http://ubuntuforums.org/showthread.php?t=128777&highlight=php+handling+apache]("http://ubuntuforums.org/showthread.php?t=128777&highlight=php+handling+apache") has specifics on how to do this

---

### Post by Shadowline on 2006-05-18
Ok, that was quick.. I had libapache2-mod-php5 installed (which is what I think you meant for me to install.) I followed that link you gave me and now instead of a dialog asking to download a phtml file I get a blank page. I can now see 127.0.0.1 but I can't even access the apache-default which also go's to a blank page. :confused:

---

### Post by Shadowline on 2006-05-18
Ok, nevermind...works now after a reboot. Thanks for the help

---

