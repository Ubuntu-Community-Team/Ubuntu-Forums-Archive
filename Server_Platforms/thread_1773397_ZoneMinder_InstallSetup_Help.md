---
title: "ZoneMinder Install/Setup Help"
date: 2011-06-02
forum: Server Platforms
---

### Post by Blair Cooper on 2011-06-02
Hi there,

Is there anyone here who has ever manager to get ZoneMinder Working on an Ubuntu Server?
I have been having issues even after searching the net for all solutions.

I have a x86 workstation and web cam: Logitech Pro 5000
Running Ubuntu 11.04 Server x86

Installed Linux Successfully.

I have Tried to install ZoneMinder successfully and can connect via [http://host/zm](http://host/zm)
I can camera's etc but cannot get anything through it.

I have tried to get some assistance here:
[http://www.linuxquestions.org/questions/newreply.php?do=newreply&noquote=1&p=4371800](http://www.linuxquestions.org/questions/newreply.php?do=newreply&noquote=1&p=4371800)

Bu not able to get this resolved and thought I wouldsee if anyone has ever manager to get this working on Ubuntu and can mentor me on this.

Really Appreciate any help you can provide.
Many thanks is advance.

Regards
Blair

---

### Post by Blair Cooper on 2011-06-02
Not an expert but have some basic knowledge of Linux/Ubuntu.
Is it actually possible to get this running on Ubuntu or should I be looking at another distro?

Cheers All.

---

### Post by rgl2020 on 2011-07-23
I have it running on 10.04 LTS server.  Haven't tried it on 11.04, but there are multiple guides on the Zoneminder documentation pages.  Here's a link to the Ubuntu guides.
[http://www.zoneminder.com/wiki/index.php/Ubuntu]("http://www.zoneminder.com/wiki/index.php/Ubuntu")

Also make sure your firewall isn't blocking you from trying to connect to the zoneminder server.

---

### Post by bo.vestergaard on 2011-08-05
I ran Zoneminder on Ubuntu 10.xx for years but I cannot get it working in 11.04. I know my camera works because I can use it in other apps but just not in ZM.

---

### Post by SquALeD on 2011-08-16
Hi mate did you get this working?

Been running ZM with no dramas for yonks on 10.04 LTS like others, not sure about 11 tho.

What probs do you get? Black monitor screens or what? 

Can you try with an ip cam instead of the webcam? ZM is a PITA to get running with a webcam IMO

---

### Post by dewmanstl on 2011-09-20
I know this thread is a little dated but I have been successful in getting zoneminder working with 11.04 x86 server. Took me a little bit to get it to work. However I did not use the debs from the repos. ( i did at first) 

I just finished creating it from source. Which for me was a learning experience. 

I followed this guide, however some of this I did not do. Maybe this will get you started 
[http://www.zoneminder.com/wiki/index.php/Ubuntu_Server_11.04_64-bit_with_ZoneMinder_1.24.x_from_SVN,_FFmpeg,_libjpeg-turbo,_Webmin,_Cambozola](http://www.zoneminder.com/wiki/index.php/Ubuntu_Server_11.04_64-bit_with_ZoneMinder_1.24.x_from_SVN,_FFmpeg,_libjpeg-turbo,_Webmin,_Cambozola)

I do have a .deb that I created after the install was complete and I have no idea if it will work or not.

---

### Post by ooseven on 2012-02-02
> **SquALeD said:**
> Hi mate did you get this working?

Been running ZM with no dramas for yonks on 10.04 LTS like others, not sure about 11 tho.

What probs do you get? Black monitor screens or what? 

Can you try with an ip cam instead of the webcam? ZM is a PITA to get running with a webcam IMO

Hey mate:-) I have been trying to get this to run on ubuntu 10.04/10.10/11.04/centos the
only one that can is arch linux. But the pictures where bad. I get the localhost where I can
go in and check things. But when I click on monitor it is blank, white some times then black
some time.

I really need help. I have Ubuntu 10.10 installed now but if you want me to I will install 10.04
So you can explain better. When they say change a file I have now idea how to do that.

Please help....

Thank You...
oosevn

---

### Post by aschmidtm on 2012-02-09
I had to:
```
sudo chown www-data.www-data /dev/video0
```

---

### Post by bayvista on 2012-07-07
I have installed Zoneminder on 11.10 OK. However, the webcam (Logitech) does not work. It works fine on Skype and Xawtv. The ZM Console shows "Monitor" in yellow and "Dev/Video (0)" in red. Any ideas?

SOLVED: I had specified the webcam address as "dev/video". It should have been "dev/video0". Working fine now.

---

### Post by zissshh on 2012-10-01
> sudhir@sudhir-desktop:~$ ./configure
bash: ./configure: No such file or directory
sudhir@sudhir-desktop:~$ sudo ./configure
sudo: ./configure: command not found
sudhir@sudhir-desktop:~$ 

i have installed zoneminder skipping the build step  according to zoneminder wiki,,,now how do i complete this step 
> 
To build ZoneMinder the first thing you need to do is run the included configure script to define some initial configuration.  If you are happy with the default settings for the database host  (‘localhost’), name (‘zm’), user (‘zmuser’) and password (‘zmpass’) then  you can just type 
 ./configure --with-webdir=<your web directory> --with-cgidir=<your cgi directory>  where **--with-webdir** is the directory to which you want to install the PHP files, and **--with-cgidir** is the directory to which you want to install CGI files. These directories could be **/var/www/html/zm** and **/var/www/cgi-bin** for example. 
If you want to override any of the default database values then  you can append them to the configure command, for example to use a  database password of ‘zmnewpass’ do 
 ./configure --with-webdir=<your web directory> --with-cgidir=<your cgi directory> ZM_DB_PASS=zmnewpass  and so on. The values you can use are ZM_DB_HOST, ZM_DB_NAME,  ZM_DB_USER and ZM_DB_PASS. Other than the database name, which is  substituted into the database creation script, these values can easily  be changed after this step. 


now pls help me

---

### Post by zissshh on 2012-10-04
> sudhir@sudhir-desktop:~$ service apache2 restart
 * Restarting web server apache2                                                /usr/sbin/apache2ctl: 87: ulimit: error setting limit (Operation not permitted)
[Thu Oct 04 22:16:42 2012] [warn] The Alias directive in /etc/apache2/sites-enabled/001-zoneminder at line 1 will probably never match because it overlaps an earlier Alias.
/usr/sbin/apache2ctl: 87: ulimit: error setting limit (Operation not permitted)
[Thu Oct 04 22:16:42 2012] [warn] The Alias directive in /etc/apache2/sites-enabled/001-zoneminder at line 1 will probably never match because it overlaps an earlier Alias.
(13)Permission denied: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs
Action 'start' failed.
The Apache error log may have more information.

pls explain this

---

### Post by zissshh on 2012-10-04
[HTML]http://1024bitez.blogspot.in/2011/01/setting-up-cgi-bin-in-apache-in-ubuntu.html[/HTML]i folowed this link for cgi bin,,,, but afterall steps and restart apache 2,,,i got
> 
sudhir@sudhir-desktop:~$ sudo /etc/init.d/apache2  restart
[sudo] password for sudhir: 
Syntax error on line 19 of /etc/apache2/sites-enabled/000-default:
Illegal option SetHandler
Action 'configtest' failed.
The Apache error log may have more information.
   ...fail!

> sudhir@sudhir-desktop:~$ ./configure --with-webdir=/home/sudhirgaikwad/public_html/--with-cgidir=/home/sudhirgaikwad/public_html/cgi-bin/
bash: ./configure: No such file or directory


SOMEBODY EXPLAIN THIS ,, I have shifted to ubuntu 1 year back with virtual assistance,,,

---

### Post by zissshh on 2012-10-05
i did all the steps for installing cgi directory in ubuntu and formed a cgi and php directory
restart but this comes

> sudhir@sudhir-desktop:~$  sudo service apache2 restart
 * Restarting web server apache2                                                [Fri Oct 05 14:31:33 2012] [warn] The Alias directive in /etc/apache2/sites-enabled/001-zoneminder at line 1 will probably never match because it overlaps an earlier Alias.
 ... waiting .[Fri Oct 05 14:31:35 2012] [warn] The Alias directive in /etc/apache2/sites-enabled/001-zoneminder at line 1 will probably never match because it overlaps an earlier Alias.

---

### Post by danickstr on 2012-11-20
I am trying to initialize ZM as well but also not sure what has been done by package install and where i am to begin...

the steps after an apt-get install are probably spelled out fine for advanced users but as a beginner I am not sure where to jump in.

---

