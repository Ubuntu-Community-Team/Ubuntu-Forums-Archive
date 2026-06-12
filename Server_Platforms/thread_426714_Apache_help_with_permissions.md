---
title: "Apache help with permissions"
date: 2007-04-28
forum: Server Platforms
---

### Post by ladrao2007 on 2007-04-28
I am totally new to Linux and trying to get the hang of a LAMP setup.  I installed a fresh version of Linux 7.04 server, with all the added software. I also downloaded Webmin to manage everything.  I have it setup now to when I go to _[http://localhost](http://localhost)_ I see the apache2-default directory, however I cannot add any files to this folder.  The permissions of the folder reads drwxr-xr-x root root

I'm wanting to get to where I can add files to the /var/www folder.

Anyone have any suggestions what to do?

Again, I am totally new to the whole Linux world, I would appreciate any help

Thanks

---

### Post by az on 2007-04-28
You can run 

sudo nautilus

to open up a filemanger windows that can write to /var/www


[http://ubuntuforums.org/showthread.php?t=425000](http://ubuntuforums.org/showthread.php?t=425000)

---

### Post by satellite360 on 2007-04-29
If you are running Apache locally and just want to use it for testing sites etc you can save all your site development work in your home folder and point Apache to that folder.  See the guide here:
[ How to map URLs to folders outside /var/www/]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_map_URLs_to_folders_outside_.2Fvar.2Fwww.2F")

To make /var/www your own (non-secure!!)
```
sudo chown -R $USER:$USER /var/www
```

---

