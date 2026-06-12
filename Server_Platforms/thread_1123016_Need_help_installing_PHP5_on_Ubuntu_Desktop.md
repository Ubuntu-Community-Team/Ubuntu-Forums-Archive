---
title: "Need help installing PHP5 on Ubuntu Desktop"
date: 2009-04-11
forum: Server Platforms
---

### Post by SlaughterDog on 2009-04-11
I'm in a basic web development class and the first step is to get Apache and PHP installed on our systems. 

From the Ubuntu Synaptic Package Manager, I have these 3 packages installed:
libapache2-mod-php5
php5
php5-common

Now, the textbook we're working out of says to add this to Apache's httpd.comf to make it load php5:
LoadModule php5_module libexec/libphp5.so

However, there is no libexec directory in the Apache installation, and a file search for libphp5.so just turns up dry. 

Can anyone help me get php running?

---

