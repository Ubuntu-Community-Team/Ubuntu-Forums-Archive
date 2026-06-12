---
title: "Help:::how to setup the apache server config file on linux ubuntu ?"
date: 2007-06-28
forum: Server Platforms
---

### Post by a_kalash on 2007-06-28
Hello,

I am using Linux (Ubuntu7.04 Desktop Edition) as an operating system and i did the installation of apache server 2.2.4 to create a local web server and it's running <it works> but i don't have any idea about the instructions or commands that must be change in the config file of apache in order to let the server share the file from the appropriate directory (where the data is exicted)??

If anyone knows how to set up this config file and can provide it to me i will appreciate his or her help!!

Thanks

---

### Post by silverglade00 on 2007-06-28
I'm not sure if this is what you are asking, but your website files should go into /var/www/html. That way, going to your website will load /var/www/html/index.html. If you are trying to change the folder that it looks for the website folders, I'm not sure exactly, but you could try looking at apache.conf for that folder.

---

