---
title: "How to paste text  into command line guest (no xserver installed)"
date: 2008-05-20
forum: Server Platforms
---

### Post by fervilla on 2008-05-20
I have installed vmware workstation in a ubuntu 8.04 and a JeOS 8.04 guest on it. In order to configure LAMP in my guest I am reading the followin tutorial:

[https://help.ubuntu.com/community/JeOS](https://help.ubuntu.com/community/JeOS) 

The tutorial ask me to copy the code for a index.php file into my guest just to test the apache configuration. The tutorial only says:

* open the file /opt/sample-app/index.php using sudo with your text editor of choice 
* paste the above page content in the text editor, save and exit 

My problem is that since the JeOS 8.4 does not come with xserver, I dont know how to copy and paste between a host graphical enviroment to a guest command line enviroment? :(



Thanks. :KS

---

### Post by windependence on 2008-05-20
Install VMware tools and you should be able to cut and paste into the terminal. Otherwise you could ssh into the box from another machine and you can then paste into the terminal that way. From Windoze you can use PuTTY.

-Tim

---

