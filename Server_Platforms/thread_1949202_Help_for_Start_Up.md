---
title: "Help for Start Up"
date: 2012-03-29
forum: Server Platforms
---

### Post by ramin1 on 2012-03-29
Hi there this is Ramin r. Kamal and I was just wondering to know if you can please help me I dont know how to use Ubuntu's Server Forum Community and I am totally a begginer. I want to build a website but I was just wondering to know how can I combine Ubuntu with Drupal. and I also I tried to install Ubuntu's Server but it seems like it installed a operating system along side my windows vista 32 bit operating system. 
and also I was just wondering to know if Ubuntu has any security firewall to protect ourselves against hackers.
 
So please Help me I am a totall beginner and I need help big time Please and thank you.

also I was wondering to know what is xbuntu and others. all I need is to set up my own dedicated server.

---

### Post by josephmills on 2012-03-29
Hello there and welcome to Ubuntu Forums 

Ubuntu server is a Whole operating system in its own 

There are many many many options out there as far as firewalls. 
iptables 
ufw 
standalone boxs are also cool like ipcop or pfsense

There is something called openpanel that have a script built into it to install drupel please see [http://www.openpanel.com/openapp/](http://www.openpanel.com/openapp/)

If you are just starting out on this adventure, then you might want to install your ubuntu server on a virtualbox or some sorta virtual client. then you can run local and just play around until you got the hang of things. 


there are pleanty of good stickys  in the server section with tutorials. 

here is some of my fav tutorials 
[http://www.howtoforge.com/perfect-server-ubuntu-11.10-with-nginx-ispconfig-3](http://www.howtoforge.com/perfect-server-ubuntu-11.10-with-nginx-ispconfig-3)

thou I do not care that much for ispconfig 
[http://www.upubuntu.com/2011/10/how-to-install-drupal-79-on-ubuntu.html](http://www.upubuntu.com/2011/10/how-to-install-drupal-79-on-ubuntu.html)
[https://help.ubuntu.com/community/Servers](https://help.ubuntu.com/community/Servers)
[https://help.ubuntu.com/11.10/serverguide/C/index.html](https://help.ubuntu.com/11.10/serverguide/C/index.html) 
[http://www.youtube.com/watch?v=R1UiDF45tbs](http://www.youtube.com/watch?v=R1UiDF45tbs)


I hope that this helps in some sorta way.

---

### Post by TommyKlien on 2012-04-11
[B]APACHE WEB SERVER (http):
[/B]
Can I ask what your plans with this server are? Do you plan to serve your Drupal site to users on your local network or every one on the internet? 

Where will this server be located and ran from? If you plan to run it at your house and have it viewed by every one on the internet. You will need to talk to your ISP about getting a static IP address or use a dynamic IP DNS solutions such as no-ip.com, [http://dyn.com/dns](http://dyn.com/dns) ..etc. 

The No-IP client can be installed with a single command on Ubuntu (sudo apt-get install no-ip). If you don't care about the domain name and have something like MySite.no-ip.org you can use there free solution. If you want your own domain you will need to register the domain and get one of the paid solutions.   


To install Drupal on Ubuntu check out the tutorial on mixeduperic.com: 
[http://mixeduperic.com/ubuntu/how-to-setup-drupal-on-ubuntu-server.html](http://mixeduperic.com/ubuntu/how-to-setup-drupal-on-ubuntu-server.html)


One other tip: If you are running Ubuntu server without a graphical interface and don't feel comfortable at the command-line you may want to look at installing something like webmin to make things a little easier. (A Web Admin interface) [http://www.webmin.com/](http://www.webmin.com/) 


If you are up for trying another Linux distro that may be a little easier to manage without the command-line, take a look at [http://www.zentyal.org/](http://www.zentyal.org/). They have a very easy to use web admin interface.



**Security:**
You can use IP tables to open and close any ports you want on your system. This includes incoming as well as outgoing.



IPTables on Ubuntu:
[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

SELinux on Ubuntu:
[https://wiki.ubuntu.com/SELinux](https://wiki.ubuntu.com/SELinux)



Wish you the best on your new fun and exciting journey of Linux and open source software!

---

