---
title: "Very Lost...Ubuntu Desktop 10.04 home Server- editing httpd.conf file...and my fails"
date: 2010-07-08
forum: Server Platforms
---

### Post by krack3rz on 2010-07-08
To make it clear: I turned my home PC running Ubuntu 10.04 into a server,

and so i am so lost, after reading like a 10-20 different guides and/or official docs, I am totally lost.

All I wanted was to create a custom 404 error page...I then realized all the guides are confuzing and all I gotfrom them was a headache...

i read about how people edited .htaccess files to customize error pages, i tried and failed
also, editing apache2.conf, I got lost and i dont wanna mess up everything
and also, how you're supposed to not touch either of those as its not how it should be done and instead you need to edit httpd.conf and i did and FAILED!!! again...

Can anyone help me untangle this mess? ](*,)

Also how do I make it so that I can make subdomain(s) on my site?
and wth is a name server and where do I get one?

Also I am noobish...go easy on me

---

### Post by jmsgz on 2010-07-08
If you are new to ubuntu and linux, setting up a server is harder that the desktop. As you know there is no default gui on ubuntu's server. U can use "Nano" a simple text editor to edit system and config files.
"sudo apt-get install nano" from terminal if not already installed.

FIRST determine what services you want on your server? 
WHAT is your server to be used FOR? Spend time doing this before proceeding. 

Then read the docs over throughly for those services you want to install. 
Read throughly the ubuntu server install guide until you feel comfortable. Pay attention to package management and post install configurations.  If you have two machines you can set up the server on one and a desktop on the other so that you can read online instructions while setting up the server on the other. You can use Ebox from the desktop to set up the server via internet once installed. Or, if you are familiar with the command line you can set it up locally, or via you desktop using SSH. 
 
Use you command line "man" and "info" commands to research what doc you have installed. Download and read Rute's Handbook and William E shots linux command line tutorial, all available online. For most newbies ubuntu server can be hard. Hang in there, ask questions and READ READ READ. Just try things, you cannot mess up, you can always re-install later. Trying things will get you the best experience.  

Linux is extremely powerful and has many many options. To get the most out of it you should have a good feel for the command line, command line options, using "man" and "info" commands, understanding where things are in the file system etc. Try midnight commander sudo apt-get install mc" to help you get around the file system and read docs. Once you begin to get proficient with it you will be amazed how great an OS it is. You can then focus on security, enhancing server or desktop systems and experimenting with making your system unique. As a newbie recently you can get overwhelmed easy, just step back and take a break.

GOOD LUCK!

---

### Post by kemra on 2010-07-09
jmsgz I don't think you answered any of the OP's questions at all, so I'm going to try and help instead:

krack3rz, you can create set a custom 404 error page by using the instructions here:

[http://ubuntuforums.org/showthread.php?t=1209280]("http://ubuntuforums.org/showthread.php?t=1209280")

Obviously first you need to create the error page just like any other html or php page and copy it to your apache doc root.

If you're worried about messing up a file you can back it up 1st by using the following example:

```
sudo mv /var/www/.htaccess /var/www/.htaccess.bak
```

So if you mess up at some point you can restore the original with:

```
sudo mv /var/www/.htaccess.bak /var/www/.htaccess
```

To host multiple sites on the same apache2 server you need to specify virtual hosts for each site, this guide should be what you need:

[http://www.debuntu.org/2006/02/22/7-virtual-hosting-using-apache-2]("http://www.debuntu.org/2006/02/22/7-virtual-hosting-using-apache-2")

As for DNS (Dynamic Naming Service) have a read of this to make sure you grasp what it is:

[http://en.wikipedia.org/wiki/Domain_Name_System]("http://en.wikipedia.org/wiki/Domain_Name_System")

Once you udnerstand what it is you need you either install dns (bind9) on your own machine if you intend to only use the site locally, or use your Web Address name supplier's DNS.

---

### Post by krack3rz on 2010-07-09
_To clarify_, i have an Ubuntu desktop and I installed apache,php,mysql, ...
Thereby turning it into a sever, its already connected to the internet via port 80 thru my router...

1. the first link is missing a link to some critical stuffs, but i already have a .htaccess file which says "ErrorDocument 404 /custom_errors/404.php" and I already had that 404.php file...
missing link: [http://compustorm.no-ip.org/2009/07/apache-and-wordpress-permalink-on-ubunutu/](http://compustorm.no-ip.org/2009/07/apache-and-wordpress-permalink-on-ubunutu/)

2. Thanx for the second link its exactly wat I need!

3. Also the last wiki page doesnt help me because i know that general stuff, i need to know how to connect my IP to a domain that I got for free from [www.co.cc](www.co.cc) and that requires a name server. i tried reading the server help docs[help.ubuntu.com], but I dont understand some things i'm stuck at: [https://help.ubuntu.com/8.04/serverguide/C/network-configuration.html](https://help.ubuntu.com/8.04/serverguide/C/network-configuration.html)

---

### Post by jmsgz on 2010-07-11
Hello kemra

     In hindsight (when all is 20/20) you r right the help i posted sucked!
But please limit your comments to helping the poster not judging other members "quality of help" as it is freely given in an attempt to "HELP"
Although totally missing the target i bet you that the poster has not read 
William shots command line book or Rute's as it is a great source of "HELP"
     In the future i will try to target my help in a more effective manner as to not offend the "Help" police! I also promise not to technically judge yours.
     And as far as the poster is concerned i hope i didn't cause any problems by missing the target and wish he/she has gotton the help needed. 
jmsgz

---

