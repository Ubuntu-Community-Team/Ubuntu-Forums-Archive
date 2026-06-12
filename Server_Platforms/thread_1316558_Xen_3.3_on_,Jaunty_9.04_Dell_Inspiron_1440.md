---
title: "Xen 3.3 on ,Jaunty 9.04 Dell Inspiron 1440"
date: 2009-11-06
forum: Server Platforms
---

### Post by tapas_mishra on 2009-11-06
I am testing XEN on Ubuntu Jaunty 9.04 as Dom0 
 I am new to xen so after some googling and playing around I had been able to install Xen on my machine 
as per the instructions given on this page 
[http://www.howtoforge.com/installing-xen-3.3-with-kernel-2.6.27-on-ubuntu-8.10-x86_64](http://www.howtoforge.com/installing-xen-3.3-with-kernel-2.6.27-on-ubuntu-8.10-x86_64)
[http://blog.codefront.net/2007/06/26/installing-xen-on-ubuntu-feisty-fawn-the-complete-newbies-guide/](http://blog.codefront.net/2007/06/26/installing-xen-on-ubuntu-feisty-fawn-the-complete-newbies-guide/)

On this blog 
[http://www.infohit.net/blog/post/running-xen-on-ubuntu-intrepid-and-jaunty.html](http://www.infohit.net/blog/post/running-xen-on-ubuntu-intrepid-and-jaunty.html)
following is mentioned
 
"Getting Dom0 networking running The key to getting the network running is removing the Ubuntu network manager   
     sudo apt-get remove network-manager"my issue is I have a wifi network available with me with no LAN over here.
If I uninstall the network-manager then the wifi driver also gets uninstalled which i have tested.
I need to access intenet for obvious reasons which will not be possible if I uninstall network-manager. To be able to complete rest of the method to setup the network on XEN as mentioned on the above blogs or many other forums which I have read.

 When I installed Ubuntu on my machine there had been a message about the broadcom drivers which Ubuntu uses if I can know how to re enable the same network-manager which Jaunty 9.04 is using after above experiments my time is saved or the files which I need to take backup so that my wi fi driver is saved and I can bring the card up again so what should I do and how to proceed.

  I had tried and since got disconnected with my network my issue is to be able to search on internet my questions I need an internet connection I want to run XEN on the same machine from where I am posting where can I find the right driver file/module which current setup of Ubuntu on my machine so that I take a backup of the wifi drivers on my machine and keep on doing with my experiments.
Since I am new to this thing so when I had uninstallled network manager from my machine I had to re install every thing to get my wifi working or is there a simple solution to this problem.Any help would be appreciated.
The PCI ID of wifi card is 14E4:4315 it uses a Broadcom chip 
product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
and while installing Ubuntu Jaunty 9.04 I got a message that it uses Broadcom STA copyrighted driver 
wanted .How does Ubuntu support this hardware that is what I want to know since in many other distributions I tried inspite of using ndiswrapper and other methods described I failed to successfully bring up the above mentioned card only in Ubuntu I got the answer for ths problem.
Any help here would be appreciated.

---

### Post by tapas_mishra on 2009-11-08
Initially when I had posted this question I was not clear with a few things but now I think I have found  a solution 
here 

[ http://packages.ubuntu.com/jaunty/net/network-manager-gnome]("http://packages.ubuntu.com/jaunty/net/network-manager-gnome")

---

### Post by tapas_mishra on 2009-11-12
I have finally got some luck in trying over Xen there are supported Operating System and some Operating Systems do not support 
I had been googling since I was getting a lot of errors as I had tried to install Xen or say compile a Dom0 kernel on it from jeremy repository on the unsupported OS,
and since from my post it is absolutely clear that I am a novice as far as Xen is concerned 
I came across a good book about XEN 
A hands on guide to the art of virtualization Jeanna Mathews
[http://www.amazon.ca/Running-Xen-Hands-Guide-Virtualization/dp/0132349663/ref=sr_1_3/189-9122115-5316947?ie=UTF8&s=books&qid=1258034980&sr=1-3](http://www.amazon.ca/Running-Xen-Hands-Guide-Virtualization/dp/0132349663/ref=sr_1_3/189-9122115-5316947?ie=UTF8&s=books&qid=1258034980&sr=1-3)

I am posting the above link so that if some one like me is searching for a lot of basic questions among documentations etc does not get confused by the blogs on internet everything available for free does not leads to the right solution.But still it has a lot of support on the community and a good place to ask questionbs is [http://gmane.org]("http://gmane.org/") the mailing list about xen users it is here 
[http://lists.xensource.com/xen-users](http://lists.xensource.com/xen-users)

A relevant thing to search on internet will be 
CONFIG_XEN_PCI
CONFIG_NETXEN_NIC
Initially they appear to be jargons but if you keep googling and reading you will answers.

---

