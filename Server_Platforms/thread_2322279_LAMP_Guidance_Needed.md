---
title: "LAMP Guidance Needed"
date: 2016-04-27
forum: Server Platforms
---

### Post by kerrybabercrombie on 2016-04-27
I recently Reformatted my old computer to Ubuntu 16.04 LTS in order to work on the development for my my business Site. 

My Host Server uses LAMP, so I am trying to set up LAMP on my computer to do my Coding and Testing before Migrating to Host server. 

I Followed this Guide for Installing [http://www.unixmen.com/how-to-install-lamp-stack-on-ubuntu-16-04/](http://www.unixmen.com/how-to-install-lamp-stack-on-ubuntu-16-04/)

php was unable to locate *php7.0 libapache2-mod-php7*

Apache is working Properly
MySQL installed properly
PHP when i ran the test Document, a document opened but I was given an Error in trying the test lines then incapable of typing after that.

If someone could help me 1 on 1 getting this Set up functioning properly, I'd be grateful

---

### Post by Irihapeti on 2016-04-27
*Thread moved to **Server Platforms**.*

---

### Post by Doug S on 2016-04-27
On that link, did you realize that this:```
sudo apt-get install php7.0-mysql php7.0-curl php7.0-json php7.0-cgi 
php7.0 libapache2-mod-php7
```Is really all one line and should be entered as:```
sudo apt-get install php7.0-mysql php7.0-curl php7.0-json php7.0-cgi php7.0 libapache2-mod-php7
```?

Note that on my server I do not have a package called "php7.0" and what your link called "libapache2-mod-php7" is actually "libapache2-mod-php7.0". I think you also need "libapache2-mod-php".

Try [the Ubuntu Serverguide]("https://help.ubuntu.com/lts/serverguide/index.html") as a reference (although work is still needed to fully update it for 16.04).

---

### Post by mörgæs on 2016-04-28
The command ```
sudo apt-get install lamp-server^
``` installs everything in one go. Notice the caret at the end.
After that a restart and you should be all set.

---

