---
title: "Expert Webserver Assistance Needed!"
date: 2010-03-30
forum: Server Platforms
---

### Post by Datamac on 2010-03-30
To those of you that have been watching me struggle with setting up a web server can now watch me struggle setting up access to it.  I now probably need the help of an expert that can instruct me as to how to view and have ftp access to 3 web servers sitting behind one ip address.  Of course the 3 web servers are actually virtual host on one machine.  I want them viewed from the internet.  I am not yet ready to register them with the main dns databases as yet.  I don't have content ready. Content development is the next step.  I need help setting up some sort of host file configuration or other means that will allow me to distinctly view and access each host site.  Please help.  I will be looking for documentation to attempt to help myself but would like to accomplish this as soon as possible.

---

### Post by terazen on 2010-03-30
I use vsftp for ftp access.

This guide is a bit old, but it shows some of the options available.
[http://ubuntuforums.org/showthread.php?t=518293](http://ubuntuforums.org/showthread.php?t=518293)

---

### Post by Datamac on 2010-03-30
Thank you.  That helps to begin to resolve the problem of establishing ftp access.  Any thoughts on the distinctive host viewing using one public ip address? At the URL line I would like to enter the IP address followed by a "/" (slash) and the hostname.  Any ideas on making this logic work?

---

### Post by Sporkman on 2010-03-31
> **Datamac said:**
> Thank you.  That helps to begin to resolve the problem of establishing ftp access.  Any thoughts on the distinctive host viewing using one public ip address? At the URL line I would like to enter the IP address followed by a "/" (slash) and the hostname.  Any ideas on making this logic work?

Since this is on the same machine, could you instead use one host & simply serve three different subdirectories (where the names of the three directories are the "hostnames")? That would work as you describe above.

---

### Post by Datamac on 2010-03-31
That is exactly what I am trying to do but just not sure how to get it done and verify that I have it working.

---

### Post by Iowan on 2010-03-31
Second time today I've used [this]("http://ubuntu-tutorials.com/2008/01/09/setting-up-name-based-virtual-hosting/") link. Hope I'm not mis-interpreting your question...

---

### Post by lisati on 2010-03-31
I was researching something similar earlier today and came across this: [http://www.debian-administration.org/articles/412](http://www.debian-administration.org/articles/412)

---

### Post by Sporkman on 2010-03-31
> **Datamac said:**
> That is exactly what I am trying to do but just not sure how to get it done and verify that I have it working.

Then you do not need multiple virtual hosts - just a single host (i.e. a single item in /etc/apache2/sites-available & /etc/apache2/sites-enabled).

Then, in the web site's root directory (The default is /var/www/ I think?), create the directories with the names you want. Make sure they are readable by everybody. In each directory, then, create an index.html file that you'd see to verify that the setup is working for you.

---

