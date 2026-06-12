---
title: "redmine on Ubuntu 9.10"
date: 2009-11-04
forum: Server Platforms
---

### Post by spylvas on 2009-11-04
Hi

I am trying to set up redmine to run on my ubuntu 9.10 server.
And managed to get it running, but cant get it running after boot. 

I have followed instruction from these two sites:

[http://drinkingbird.net/blog/articles/2008/02/27/setting-up-a-redmine-site-on-ubuntu]("http://drinkingbird.net/blog/articles/2008/02/27/setting-up-a-redmine-site-on-ubuntu")

[http://ubuntuforums.org/showthread.php?t=674598]("http://ubuntuforums.org/showthread.php?t=674598")

and I was able to get it up and running, but when i reboot my server port 8000 stopped to responding again. When i try to manually run */etc/init.d/mongrel_cluster start* it will give me this error:

!!! Path to log file not valid: log/mongrel.log
mongrel::start reported an error. Use mongrel_rails mongrel::start -h to get help.

I have been able to start it again by going to folder were redmine is installed and running *mongrel_rails cluster::start*, but even that doesnt work everytime

I am totally lost with this one and dont know where to look next...

---

### Post by cariboo on 2009-11-05
The path to the log file should be in the configuration file. Most log files are located in /var/log.

---

### Post by gamels on 2010-05-13
how the redmine works.. somebody left the redmine on a very crush site.. i need help on how this works. if you can send me step-by-step guide, i will be glad to read it...

---

