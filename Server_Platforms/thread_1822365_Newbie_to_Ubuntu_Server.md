---
title: "Newbie to Ubuntu Server"
date: 2011-08-10
forum: Server Platforms
---

### Post by Ant01 on 2011-08-10
I need help in pointing me in the right direction. 

I've purchased a small HP Proline server machine and want to learn how to set up and run a server to host some of my websites. 

I have a limited knowledge and would appreciate if someone can direct me to where I can read up on how to set up a server and what each of the components. I've briefly looked at the Ubuntu server guide but would like to start at something more idiot proof.

I've been running a ubuntu desktop machine but am new to the server side.

Appreciate any feedback.

---

### Post by kgatan on 2011-08-10
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

Its a little messy but all is there.

---

### Post by dinu90 on 2011-08-11
Here's another short easy howto:
[http://www.howtoforge.com/ubuntu_lamp_for_newbies](http://www.howtoforge.com/ubuntu_lamp_for_newbies)

[**java tutorials**]("http://www.java-forums.org/java-tutorial/")

---

### Post by Ant01 on 2011-08-11
I am looking at setting up the server using Ubuntu Desktop version. Can someone advise if this is advisable or if I should rather use the Server version. I am used to Ubuntu Desktop and am worried about using the linux bcommand line structures, not sure if the server has the sam GUI as the desktop.

What packages should I download for this? I have set up a test server with my windows machine using apache2 and MSQL which I test my websites before uploading.

---

### Post by arrrghhh on 2011-08-11
> **Ant01 said:**
> I am looking at setting up the server using Ubuntu Desktop version. Can someone advise if this is advisable or if I should rather use the Server version. I am used to Ubuntu Desktop and am worried about using the linux bcommand line structures, not sure if the server has the sam GUI as the desktop.

What packages should I download for this? I have set up a test server with my windows machine using apache2 and MSQL which I test my websites before uploading.

If you're not comfortable without a GUI, I would say the Desktop Edition is a good idea.

Tools like WebMin help on GUI-less servers (web-based UI for administration) but it's not a complete solution.

If you're hardware can handle it, by all means install the Desktop Edition.  All the same services can run on the Desktop Edition.  The benefits of running the Server Edition are no GUI - there's no unnecessary packages to update, and it runs very lean.  I like it because it "forced" me to learn the CLI.  If you don't want to learn the CLI, by all means go for the Desktop Edition ;).

---

### Post by stlsaint on 2011-08-11
I have never been a fan of GUI's on any of my servers. You need to take into consideration your needs for this server. Since you say it is a small hp then i will assume you have 2GB or less ram in which that will get used primarily just off your websites getting hosted (apache loves ram!!). Then with having a desktop environment you must worry about even more updates which could further your chances of something breaking which could take your server/websites down for unecessary maintenance. My best advice would be to just setup ssh on your server and use your ubuntu desktop machine to handle management of the server. You can use the already setup gui on your desktop machine to handle all config files and settings for your server. That way the only cli you really are required to do directly on the server is setup ssh OR you could just install webmin! (again i am against it but its better then installing a full blown DE!!)

---

### Post by Ant01 on 2011-08-11
Thanks for the quick response, I am going to install both systems and learn CLI on the server version as I go along, can you direct me where I can learn the CLI. I have 3 gig ram and can add up to 8gig

---

### Post by stlsaint on 2011-08-11
There are way too many resources to try and list here. I would just suggest googling: linux command line 
or something and go from there.

---

### Post by robgr85 on 2011-08-12
> **Ant01 said:**
> Thanks for the quick response, I am going to install both systems and learn CLI on the server version as I go along, can you direct me where I can learn the CLI. I have 3 gig ram and can add up to 8gig



I think, that for server working on the internet You need only required packages - when everyone can access Your system from outside, security is a must. Installing GUI will bring lot of packages that might rise security problems sooner or later. 

Firstly try without GUI, and if there will be point of no return install some lightweight GUI with apt-get. 

If the server is strictly for the webpages don't wait much and look at cPanel or DirectAdmin software (if You work with websites its web interface is familiar to You - if not, its intuitive and easy!). They don't cost that much and are probably the most comfortable/easy ones to manage hosted websites. If You are thinking about lot of websites, or some with higher traffic go in direction of DirectAdmin - it does not eat as much resources as cPanel do.

---

### Post by Ant01 on 2011-08-12
> **robgr85 said:**
> I think, that for server working on the internet You need only required packages - when everyone can access Your system from outside, security is a must. Installing GUI will bring lot of packages that might rise security problems sooner or later. 

Firstly try without GUI, and if there will be point of no return install some lightweight GUI with apt-get. 

If the server is strictly for the webpages don't wait much and look at cPanel or DirectAdmin software (if You work with websites its web interface is familiar to You - if not, its intuitive and easy!). They don't cost that much and are probably the most comfortable/easy ones to manage hosted websites. If You are thinking about lot of websites, or some with higher traffic go in direction of DirectAdmin - it does not eat as much resources as cPanel do.

Hi robgr85

Thanks for the advice, I am familiar with cpanel, where can I purchase/download a copy of cpanel and DirectAdmin. I installed Webmin last night but still have to play around and see what it is.

I also need advice how to progress from setting up a local host server to a live webserver. I know I have to something via DHCP but not sure where to start.

Thanks again

PS I got some excellent help via Utube to all the newbies in my position and looking at learning I suggest have a look at the following utube links;
Installing LAMP Server on Ubuntu Desktop 10.10  [http://www.youtube.com/watch?v=5pYUZQmM8Bk](http://www.youtube.com/watch?v=5pYUZQmM8Bk)

Install Webmin in Ubuntu 10.10 - Linux
[http://www.youtube.com/watch?v=7NSaeW4hARY](http://www.youtube.com/watch?v=7NSaeW4hARY)

Ubuntu 10.10 PhpMyAdmin Installation 
[http://www.youtube.com/watch?v=s9GK_qdcXR4](http://www.youtube.com/watch?v=s9GK_qdcXR4)

---

### Post by robgr85 on 2011-08-12
> **Ant01 said:**
> Hi robgr85

Thanks for the advice, I am familiar with cpanel, where can I purchase/download a copy of cpanel and DirectAdmin. I installed Webmin last night but still have to play around and see what it is.

I also need advice how to progress from setting up a local host server to a live webserver. I know I have to something via DHCP but not sure where to start.

Thanks again

PS I got some excellent help via Utube to all the newbies in my position and looking at learning I suggest have a look at the following utube links;
Installing LAMP Server on Ubuntu Desktop 10.10  [http://www.youtube.com/watch?v=5pYUZQmM8Bk](http://www.youtube.com/watch?v=5pYUZQmM8Bk)

Install Webmin in Ubuntu 10.10 - Linux
[http://www.youtube.com/watch?v=7NSaeW4hARY](http://www.youtube.com/watch?v=7NSaeW4hARY)

Ubuntu 10.10 PhpMyAdmin Installation 
[http://www.youtube.com/watch?v=s9GK_qdcXR4](http://www.youtube.com/watch?v=s9GK_qdcXR4)

Webmin is web interface for general server configuration & administration tasks. I'm not sure if it will helpful at webhosting server  (not sure, because I never used it longer than 5 minutes ;) ). cPanel & DirectAdmin were created with webhosting in mind. Webmin will help You in configuring other services on Your server (samba shares, printing, vpn, ssh etc) wheras those two are only  for things connected with webhosting server.

cPanel & DirectAdmin can be found at:
cpanel.net
directadmin.com

You can find a lot of useful information there (for eg. requirements!), and try demo/trial in both cases :-)

---

### Post by Ant01 on 2011-08-14
> **Ant01 said:**
> Hi robgr85

Thanks for the advice, I am familiar with cpanel, where can I purchase/download a copy of cpanel and DirectAdmin. I installed Webmin last night but still have to play around and see what it is.

I also need advice how to progress from setting up a local host server to a live webserver. I know I have to something via DHCP but not sure where to start.

Thanks again

PS I got some excellent help via Utube to all the newbies in my position and looking at learning I suggest have a look at the following utube links;
Installing LAMP Server on Ubuntu Desktop 10.10  [http://www.youtube.com/watch?v=5pYUZQmM8Bk](http://www.youtube.com/watch?v=5pYUZQmM8Bk)

Install Webmin in Ubuntu 10.10 - Linux
[http://www.youtube.com/watch?v=7NSaeW4hARY](http://www.youtube.com/watch?v=7NSaeW4hARY)

Ubuntu 10.10 PhpMyAdmin Installation 
[http://www.youtube.com/watch?v=s9GK_qdcXR4](http://www.youtube.com/watch?v=s9GK_qdcXR4)

Can someone dierect me to the which DirectAdmin software to use for running a webserver. I'm having difficulty in getting started, set up php,apache2 and mysql but I think it will be easier if I had a sript that encompasses everything. I would like to host a number of sites and need to ensure the security and set up cpanels for each site.

Thanks

---

### Post by faroutliving on 2011-08-14
> Webmin is web interface for general server configuration &  administration tasks. I'm not sure if it will helpful at webhosting  server  (not sure, because I never used it longer than 5 minutes :wink:  ). cPanel & DirectAdmin were created with webhosting in mind.  Webmin will help You in configuring other services on Your server (samba  shares, printing, vpn, ssh etc) wheras those two are only  for things  connected with webhosting server.What you want then is virtualmin (and usermin) which give you comparable features (but without the cost), and they run on top of webmin. Virtualmin includes an installer script which is supposed to take care of most everything.

Deron

---

### Post by Ant01 on 2011-08-14
> **faroutliving said:**
> What you want then is virtualmin (and usermin) which give you comparable features (but without the cost), and they run on top of webmin. Virtualmin includes an installer script which is supposed to take care of most everything.

Deron

Can I install Virtualmin on top of Ubuntu desktop 11.04 or is it a new installation. I would like to use the same machine for playing around on ubuntu and run my websites. How do I install Virtualmin?

---

### Post by Tangopdx on 2011-08-14
> **Ant01 said:**
> Can I install Virtualmin on top of Ubuntu desktop 11.04 or is it a new installation. I would like to use the same machine for playing around on ubuntu and run my websites. How do I install Virtualmin?

What about:

[http://www.howtoforge.com/perfect-server-ubuntu-11.04-ispconfig-3](http://www.howtoforge.com/perfect-server-ubuntu-11.04-ispconfig-3)

If you already have an Ubunto install, the go to the ISPconfig 3 site and learn how to install it on top.

---

### Post by Tangopdx on 2011-08-14
> **Ant01 said:**
> Can I install Virtualmin on top of Ubuntu desktop 11.04 or is it a new installation. I would like to use the same machine for playing around on ubuntu and run my websites. How do I install Virtualmin?

What about:

[http://www.howtoforge.com/perfect-server-ubuntu-11.04-ispconfig-3](http://www.howtoforge.com/perfect-server-ubuntu-11.04-ispconfig-3)

If you already have an Ubunto install, the go to the ISPconfig 3 site and learn how to install it on top.

---

