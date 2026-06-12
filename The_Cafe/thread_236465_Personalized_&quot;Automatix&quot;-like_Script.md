---
title: "Personalized &quot;Automatix&quot;-like Script"
date: 2006-08-14
forum: The Cafe
---

### Post by aleska on 2006-08-14
I was wondering whether anyone could point me to a tutorial on how to create your own Automatix-like or Easy Ubuntu-like scripts to install just the apps you want.  Basically, I'm talking about creating a personalized script that includes all those programs I want (even those not included in Automatix) so that I can install on multiple pcs without having to hunt and peck each time with each setup.

I'm sure this has been covered somewhere in the forums, but I'm having no luck in my search results.
    
Thanks!

---

### Post by cstudent on 2006-08-14
The guts of Automatix is nothing more that a bash script. You can start to learn about bash scripting with this website:

[http://www.tldp.org/LDP/abs/html/](http://www.tldp.org/LDP/abs/html/)

The graphics for Automatix are done using Zenity. Unless you want the graphics, there would really be no need for it. You can learn more about Zenity here:

[http://www.linuxmanpages.com/man1/zenity.1.php](http://www.linuxmanpages.com/man1/zenity.1.php)

You can also download the .deb file for Automatix and extract it with the archive manager like you would a tar.gz file. This would not install Automatix, but it would let you be able to study the scripts it has inside.

---

### Post by Imexius on 2006-08-14
Or you could just write bash scripts ie:

#! /bin/bash
cat mysources.list > /etc/apt/sources.list
sudo apt-get update
sudo apt-get install blah blah blah blah

---

### Post by richbarna on 2006-08-15
> **cstudent said:**
> The guts of Automatix is nothing more that a bash script. You can start to learn about bash scripting with this website:

[http://www.tldp.org/LDP/abs/html/](http://www.tldp.org/LDP/abs/html/)

The graphics for Automatix are done using Zenity. Unless you want the graphics, there would really be no need for it. You can learn more about Zenity here:

[http://www.linuxmanpages.com/man1/zenity.1.php](http://www.linuxmanpages.com/man1/zenity.1.php)

You can also download the .deb file for Automatix and extract it with the archive manager like you would a tar.gz file. This would not install Automatix, but it would let you be able to study the scripts it has inside.

Nice links Cstudent, thanks :)

---

