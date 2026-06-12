---
title: "Apache2 multiple users"
date: 2008-10-17
forum: Server Platforms
---

### Post by jayrix on 2008-10-17
Hi there..

I have a box running as server with Apache2,PHP,Mysql and everything is working as it should be.

But i just have some questions about apache2 and multiple users i.e . everone with ssh/ftp access have their own www directory like /home/user/public_html do i have to do that manually or do i need to reconf apache2 ?

And can those users use vhost ? for ex.. user1 has user1.test.com as public domain.. user2 has user2.test.com and apache will "know" the difference ?  I dont want test.com/~user1 directorys.. i want the domain to route to user if that's possible..


Can i set restrictions like quota and allowed filetypes on /home/user/* ? I.e  5gb usage and only jpg,html,htm,php,mp3 ?

I'll be happy for all answers, even a guide :) or some place to read about it

---

### Post by alienprdkt on 2008-10-18
Apache can be configured to support different user and group ID per virtual host as 
follows: 

1. Add the following lines to httpd.conf: 

ChildPerUserID 10 vh1user vh1group 
ChildPerUserID 10 vh2user vh2group 
The ChildPerUserdirective tells Apache to associate ten child processes 
(each being multiple threads that service requests) to user and group ID for 
the vhost1.domain.comsite. Similarly, the second line associates another 
ten child processes to user and group ID for the vhost2.domain.comsite. 

2. Create a <VirtualHost>container for each site: 
NameVirtualHost 192.168.1.100 
<VirtualHost 192.168.1.100> 
ServerName vhost1.domain.com 
AssignUserID vh1user vh1group 
# 
# Other directives go here 
# 
</VirtualHost> 
<VirtualHost 192.168.1.100> 
ServerName vhost2.domain.com 
AssignUserID vh2user vh2group 
# 
# Other directives go here 
# 
</VirtualHost> 
The AssignUserIDdirective used in each of the virtual host configuration 
tells Apache to associate each of the virtual hosts to appropriate user and 
group ID. Don’t forget to change the IP address as necessary. 

3. Restart the Apache server using the /usr/local/apache/bin/apachectl 
restartcommand and you are done.

---

### Post by megabuffen on 2011-05-06
I tried this on Ubuntu 11.04, but I simply get this error when trying to restart the server with the new configuration:
```
Invalid command 'ChildPerUserID', perhaps misspelled or defined by a module not included in the server configuration
```

If I remove the "ChildPerUserID" directive, leaving just AssignUserID, i get this:
```
Invalid command 'AssignUserID', perhaps misspelled or defined by a module not included in the server configuration
```

Why is this?

AssignUserID was working great on Ubuntu 10.04.

---

### Post by satanselbow on 2011-05-06
The apache documentation is pretty good ;)

[http://httpd.apache.org/docs/2.0/mod/perchild.html](http://httpd.apache.org/docs/2.0/mod/perchild.html)

Your error look like you either do not have the -mpm modules loaded/installed or you need to raise (or manually define) your ServerLimit. From what I remember (i'm not of my regular machine at the mo so can't immediately check) the -mpm modules do not get installed as standard unless you used tasksel / lamp_server to install apache as part of a LAMP stack. If you find that they are installed already they are probably not enabled by default - as they create extra load which would be unnecessary unless explicitly using them ;)

I have previously run a similar setup - but not in a long while and do not have any working examples or virtualhosts / apache2.conf to demonstrate.

This is defo more of a "apache expert" - rather than a "linux expert" type question so it might be worth doing a bit of reading on on the apacheforums as it is a pretty "hosting service" type setup you are looking at establishing ;)

---

### Post by megabuffen on 2011-05-06
I was just looking at that module, and it seems to do what I wan't. AssignUserID has been working before on 10.04. The question is, how do I install it? aptitude install apache2-mpm-perchild doesn't work.

---

### Post by satanselbow on 2011-05-06
Open Synaptic and type "apache2-mpm" in the search box and you'll get several options.

I really cannot help much further i'm afraid as this is beyond my current skillset ;)

good luck - and I would be interested to find out how you get on :popcorn:

---

### Post by megabuffen on 2011-05-08
Thanks for your help! I don't have a GUI, but a quick search on Google for "ubuntu 11.04 apache2-mpm" revealed [this page]("https://launchpad.net/ubuntu/natty/+package/apache2-mpm-itk") which describes the package "apache2-mpm-itk" in the latest Ubuntu release. It made sense that there was a better alternative than the nonfunctional perchild, since the most used web server in the world should be able to handle multiple sites.

All I had to do was to run this command, as root:
```
aptitude install apache2-mpm-itk
```

This immediately made the AssignUserID directive work:D

---

