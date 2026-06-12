---
title: "Lampp Problem"
date: 2006-11-08
forum: Server Platforms
---

### Post by Clint Chance on 2006-11-08
Little note since this is my first post:
##########################
Let me start off by saying that this distro of linux has got me saying bye bye to Windows, and hello to Linux. I am trying to get my mom to use it but see wont do it. Keep up the great work UBUNTU!!!!!
#########################
Now my "Q":

I have recently instlled lampp on the machine. Every thing works but php. When i do go to a page that uses PHP it gives an error of this:

Warning: Unknown: failed to open stream: Permission denied in Unknown on line 0

Warning: Unknown: Failed opening '/opt/lampp/htdocs/index.php' for inclusion (include_path='.:/opt/lampp/lib/php:./include') in Unknown on line 0

As you can see i have been trying to fix it. But also no luck. ](*,) ](*,) So im hoping thaat this little post will get me the help i need :mrgreen: :mrgreen: :mrgreen: :mrgreen:

---

### Post by mssever on 2006-11-08
If you're trying to set up a LAMP server, it's generally best to install software from the repositories. Unless you have a reason to use lampp that I'm not aware of, I'd recommend uninstalling lampp. Then, open Synaptic and install PHP, php5-mysql (or php4-mysql, depending on which version of PHP you use), mysql, and phpmyadmin (you'll get Apache automatically). Then just install any PHP or Apache modules you need, and everything will work without errors--plus, you'll be automatically notified of security updates.

Basically, the Ubuntu way is to install software using Ubuntu's tools (synaptic, apt-get, etc.) as much as possible and only go outside that when absolutely necessary. You'll have a lot less trouble that way.

---

