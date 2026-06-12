---
title: "which GUI iptables for ubuntu?"
date: 2008-09-29
forum: Security
---

### Post by Grace.zhang on 2008-09-29
As far as I know, there're Firewall Builder and Firestarter, does anyone know which one is easier to install and use? Also, could you please give some useful link for these two tools? thank you!

---

### Post by airtonix on 2008-09-29
Best options are : firestarter and the ufw cli.

ufw is great for those ubuntu installations that have no monitor/screen.

here is how you enable access for port 80, which is something you would do for a webserver : 

$ sudo ufw allow 80

The strengths of firestarter over ufw is that it really simple to use...it also provides a internet connection sharing feature which is really easy to use(provided you have two network cards, one for the traffic to the internet one for the internal network)

In my opinion, all the others are more complicated, lack the features and are confusing for new users.

The only thing missing from linux is application based traffic control, application thumbprinting, and traffic anonmaly notifications which is something that Sygate Firewall 5.0 was great for. 

Many people like zonealarm, since its what gets pushed in their faces from novice pc websites and majority of pc magazines....

If your familiar with zonealarm then firestarter is nothing new.

Install Firestarter : 

1 - open up synaptic package manager, and enable the universe repository : 
 - settings -> repository : tick community maintained open source software (universe) 
 - then click close.
2 - reload the software list : click the reload button in the toolbar.
3 - search for 'firestarter' : click search, type firestarter and choose 'by name'
4 - right click the singular entry, and select 'mark for installation'
5 - click the apply button in the toolbar.

To allow traffic on port 80 with firestarter : 

1 - open firestarter : 
 system -> administration -> firestarter, gksudo will prompt you for your password
2 - goto the policy tab
3 - change the drop down menu to 'inbound policy'
4 - You will see three sections, hosts, ports and port forwarding, right click in the middle pane and select 'add rule'
5 - in the Port Field, type 80 (the name field will change to HTTP by itself)
6 - leave the 'When source is...' as anyone
7 - click ok
8 - click apply in the toolbar

Make sure you have portforwarding enabled for port 80 on your adsl-modem/router to the machine that this firewall is running on.

the same operation with ufw : 

$ sudo ufw allow 80

---

### Post by kevdog on 2008-09-29
There is also guarddog -- however does require some kdelibs since its a kde application.  It is more powerful than firestarter, and has a fairly good tutorial on how to use it on the home page website.

---

### Post by rustybronco on 2008-09-29
If you need a gui for ufw [http://www.ubuntugeek.com/gufw-simple-gui-for-ufw-uncomplicated-firewall.html](http://www.ubuntugeek.com/gufw-simple-gui-for-ufw-uncomplicated-firewall.html)

---

### Post by cariboo on 2008-09-29
There is a gui for ufw. It is available from the Intrepid repositories. You can download it from here:

[http://packages.ubuntu.com/intrepid/gufw](http://packages.ubuntu.com/intrepid/gufw)

Try it and see if it will work with hardy.

Jim

---

### Post by hyper_ch on 2008-09-30
do you really need to alter the default rules? In most cases there's no reason for to do that.

---

