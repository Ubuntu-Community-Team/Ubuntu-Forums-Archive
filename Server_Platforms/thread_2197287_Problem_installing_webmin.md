---
title: "Problem installing webmin"
date: 2014-01-03
forum: Server Platforms
---

### Post by jv_rome on 2014-01-03
Hi I've been reading around forums and tried all solutions to try and solve this but to no avail. I am using ubuntu server and trying to download Webmin. 
First i run the command 

[COLOR=#333333][FONT=Lucida Console]wget [http://prdownloads.sourceforge.net/webadmin/webmin_1.660_all.deb](http://prdownloads.sourceforge.net/webadmin/webmin_1.660_all.deb)

then followed by 

[/FONT][/COLOR][COLOR=#333333][FONT=Lucida Console]dpkg --install webmin_1.660_all.deb 

to which i will get the following output

[/FONT][/COLOR]dpkg: dependency problems prevent configuration of webmin:
 webmin depends on libnet-ssleay-perl; however:
  Package libnet-ssleay-perl is not installed.
 webmin depends on libauthen-pam-perl; however:
  Package libauthen-pam-perl is not installed.
 webmin depends on libio-pty-perl; however:
  Package libio-pty-perl is not installed.
 webmin depends on apt-show-versions; however:
  Package apt-show-versions is not installed.
dpkg: error processing webmin (--install):
 dependency problems - leaving unconfigured
Processing triggers for ureadahead ...
Errors were encountered while processing:
webmin

I'm pretty new to ubuntu so please do be patient. Thank you. 


[COLOR=#333333][FONT=Lucida Console]

[/FONT][/COLOR]

---

### Post by andyfied on 2014-01-03
I believe Webmin is no longer compatible with Ubuntu. I managed to install it a few months back and it didn't really work properly.

If you still want to try it out though run: ```
sudo apt-get update && sudo apt-get upgrade
``` to see if that fixes it.

---

### Post by FiremanEd on 2014-01-03
Make sure that you have LAMP installed.  Follow the guide via [http://www.upubuntu.com/2011/09/how-to-install-webmin-on-ubuntu.html]("http://www.upubuntu.com/2011/09/how-to-install-webmin-on-ubuntu.html")
That's how I installed it more or less.

---

### Post by Bucky Ball on 2014-01-03
*Thread moved to **Server Platforms**.*

---

### Post by jv_rome on 2014-01-03
Hi thank you for the prompt replies. Really do appreciate it. Alright so I got to following the instructions on fireman's link, however i ended up with this output instead:

The following packages have unmet dependencies:
 webmin : Depends: libnet-ssleay-perl but it is not installable
          Depends: libauthen-pam-perl but it is not installable
          Depends: libio-pty-perl but it is not installable
          Depends: apt-show-versions but it is not installable
E: Unable to correct problems, you have held broken packages.

to which i tried to do a sudo apt-get -f install libnet-ssleay-perl to which i got 

Building dependency tree
Reading state information... Done
Package libnet-ssleay-perl is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source


E: Package 'libnet-ssleay-perl' has no installation candidate

What gives? :(

---

### Post by Chris of Arabia on 2014-01-04
I installed it just before Christmas on 13.10 without too much difficulty using this (admittedly dated) guide - [http://www.patrickjwaters.com/blog/2011-07-13/my-favorite-web-server-setup-ubuntu-server-lamp-webmin-and-virtualmin/3524](http://www.patrickjwaters.com/blog/2011-07-13/my-favorite-web-server-setup-ubuntu-server-lamp-webmin-and-virtualmin/3524)

i've not done the Virtualmin install, or used it to configure anything yet (been away), but it looks like it's doing as it should.

---

### Post by jv_rome on 2014-01-05
> **Chris of Arabia said:**
> I installed it just before Christmas on 13.10 without too much difficulty using this (admittedly dated) guide - [http://www.patrickjwaters.com/blog/2011-07-13/my-favorite-web-server-setup-ubuntu-server-lamp-webmin-and-virtualmin/3524](http://www.patrickjwaters.com/blog/2011-07-13/my-favorite-web-server-setup-ubuntu-server-lamp-webmin-and-virtualmin/3524)

i've not done the Virtualmin install, or used it to configure anything yet (been away), but it looks like it's doing as it should.


Hi thank you chris for the reply! First problem i ran into was when i ran tasksel to install LAMP i got 

tasksel: aptitude failed (100)

Is there something that's fundamentally wrong with my ubuntu server? Just a side note i am actually running ubuntu server on virtualbox. With netwrok 
attached to bridged adapter to my NIC card. Will that affect any of this?

---

### Post by Chris of Arabia on 2014-01-05
I'm not sure I've got the experience to answer any of those questions. Certainly you need the LAMP stack running to install Webmin on top of, but I've just been selecting that as I run though the server install and letting it sort itself out. Mine's just a home server for tinkering with a bit of webdev stuff really, so I don't get too in depth with it unless I'm absolutely pushed - my experience has been acquired somewhat grudgingly. ;)

---

