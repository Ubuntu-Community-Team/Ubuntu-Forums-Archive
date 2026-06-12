---
title: "Do I need the server edition to run a LAMP stack and install drupal?"
date: 2015-02-01
forum: Server Platforms
---

### Post by hspecimen on 2015-02-01
Hi, I noticed that alot of the instructions online for setting up a LAMP stack say on Ubuntu Server, or they say a LAMP server.  Are the instructions basically the same?  Can I sucessfully set this up with the desktop version?  I have worked very hard for days to figure this out, and its still not working, and in the interest of not bogging down other questions I have posted online, could someone re-assure me that I can use the desktop version.  

Also, real quick.  I don't need hosting service to be able to see localhost/phpmyadmin/ ?  what about to edit a drupal file?  

I think the answers will be Yes, No, NO, but I am checking because I have struggled for so long.

---

### Post by nerdtron on 2015-02-01
> Hi, I noticed that alot of the instructions online for setting up a LAMP stack say on Ubuntu Server, or they say a LAMP server.  Are the instructions basically the same? Can I sucessfully set this up with the desktop version?
Technically yes, as long as your desktop have the same version of the server like 12.04 or 14.04. Although some server packages can sometimes mess up with the GUI. Or when you edit the /etc/network/interfaces file and you'll see the network manager GUI to be grayed out (disabled)
 
>    I have worked very hard for days to figure this out, and its still not working, and in the interest of not bogging down other questions I have posted online, could someone re-assure me that I can use the desktop version.  
What guide are you using? up to what part have you gone? do you see some errors? Don't mix different guides you found on the net, as this could make things difficult to troubleshoot.


> Also, real quick.  I don't need hosting service to be able to see localhost/phpmyadmin/ ?  
You can view that on your local web browser.

> what about to edit a drupal file?  
Haven't used drupal but most config files needs to be edited (depending on your setup).

---

### Post by mörgæs on 2015-02-01
The LAMP stack is easy to install:
```
sudo apt-get install lamp-server^
```

Works for both servers and desktops.

---

### Post by mastablasta on 2015-02-03
mind oyu if oyu need to develop or to try it out a better way is to install inside virtualbox or to use preinstalled image (you then just load the image in virtualbox and connect to it form browser). take a look at bitnami stack images (ubutnu based9 or turnkey Linux images (debian based). you just unpack and load in virtualbox and start it up. no setup needed ;-)

then you connect via browser try, test break and if something is wrong you just create and then restore previous snapshot.

---

