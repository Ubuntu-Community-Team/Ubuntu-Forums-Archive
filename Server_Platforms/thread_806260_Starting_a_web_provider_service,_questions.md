---
title: "Starting a web provider service, questions"
date: 2008-05-24
forum: Server Platforms
---

### Post by agillespie on 2008-05-24
Hi folks, I have recently been interested in becoming a web server provider to bring in some extra cash and maybe in the future, after all seems to be running well, become a web space provider full time. I successfully set up my own web server and can use it fine from any computer linked to the internet. So i know how to do this and i know how to configure Domain names to point to ip's etc. I am also looking into talking with ISP's to see if i could have multiple public ip's/multiple connections with good connections etc. My questions are as follows:

1. I'd like to enable disk quotas for each web space that i am providing. I know this is possible in ms windows using an NTFS partition, but how do i do this in ubuntu?

2. I have not as of yet found any tutorials of how to set up FTP and FTP accounts. does anyone know of any or can maybe list the steps so i can make a test on my current server?

3. Are there any better firewalls or any other software i should have installed on the servers? i am currently using one i quickly downloaded.

4. Are there any ways through the OS of limiting bandwidth usage?

5. For years before when i have bought webspace, i have been provided with cpanel. is there anything else i can use? or would this be recommended?

thanks in advance,
AGillespie

---

### Post by windependence on 2008-05-24
Go out to netcraft.com and look at what people are running web servers on. Although there are many Linux web servers by far and large you will find them running FreeBSD. there are many many reasons for this, security, light on resources, virtualizes well, etc. You may want to consider taking a look.

-Tim

---

### Post by nebben11 on 2008-05-24
[http://www.ispconfig.org/](http://www.ispconfig.org/) is a free webhosting control panel
Webmin is a web-based interface for system administration for Unix [http://www.ubuntugeek.com/webmin-installation-and-configuration-in-ubuntu-linux.html](http://www.ubuntugeek.com/webmin-installation-and-configuration-in-ubuntu-linux.html)
also [http://gaming.gwos.org/doku.php/udsf:serverguide](http://gaming.gwos.org/doku.php/udsf:serverguide) and [http://tldp.org/LDP/sag/html/index.html](http://tldp.org/LDP/sag/html/index.html)

---

### Post by agillespie on 2008-05-24
thanks very much for the info. i'll check them all out.

---

### Post by hyper_ch on 2008-05-25
look at [www.howtoforge.com](www.howtoforge.com) --> there you get perfect setups for usage with ispconfig... very simple, you just need to be able to copy'n'paste ;)

---

### Post by dmizer on 2008-05-25
> **agillespie said:**
> 2. I have not as of yet found any tutorials of how to set up FTP and FTP accounts. does anyone know of any or can maybe list the steps so i can make a test on my current server?
there is a fantastic ftp server howto located in my sig.

> **agillespie said:**
> 3. Are there any better firewalls or any other software i should have installed on the servers? i am currently using one i quickly downloaded.

linux (and bsd from what i recall) comes with a firewall by default.  it's called iptables.  here's lots of information on iptables: [http://iptables-tutorial.frozentux.net/iptables-tutorial.html](http://iptables-tutorial.frozentux.net/iptables-tutorial.html)

---

### Post by SHL on 2008-08-05
> **agillespie said:**
> 5. For years before when i have bought webspace, i have been provided with cpanel. is there anything else i can use? or would this be recommended?

I would recommend OpenPanel: [http://openpanel.com/](http://openpanel.com/)

I have made quite some research on this recently, and it all boiled down to that one. Other CP:s are either too expensive, too old and not well supported anymore or has architectural drawbacks (ISPConfig, which otherwise functions well, forces the use of cryptic numbers in folders and databases, et.c.)

OpenPanel seems very well designed architectually, is worked on actively, and has both a beatiful web interface and an very intuitive command-line client. And, it works on Ubuntu 8.04.

On fresh Ubuntu installs, you can install the cp with a single command (see [http://www.openpanel.com/download_control/](http://www.openpanel.com/download_control/) ). This will setup a complete webserver with Apache, PHP and MySQL, in addition to the control panel.

---

### Post by SHL on 2008-08-05
> **SHL said:**
> On fresh Ubuntu installs, you can install the cp with a single command (see [http://www.openpanel.com/download_control/](http://www.openpanel.com/download_control/) ). This will setup a complete webserver with Apache, PHP and MySQL, in addition to the control panel.

Please note that the software is **still in BETA**, and that you **should not** try this unless you have a fresh Ubuntu install, or a complete backup of all your data.

---

### Post by agillespie on 2008-09-17
I have to thank all of you for the replies, i've started using windows server 2003 for my webserver atm...even tho i'm qualified by microsoft, i dont really like MS...I never have liked companies that operate like they do. Where as Ubuntu, Excellent OS with so many people willing to help. if you have a problem, plonk it into google and include the word Ubuntu and there is always someone who's had the same problem and lots of other people replying with salutions.

anyway! i shall now be off to back up alot of data and get myself an ubuntu server up and running again with some of the ideas you guys have all gave me. thanks again :)
AGillespie

---

### Post by tomasq on 2008-09-17
> **dmizer said:**
> linux (and bsd from what i recall) comes with a firewall by default.  it's called iptables.  here's lots of information on iptables: [http://iptables-tutorial.frozentux.net/iptables-tutorial.html](http://iptables-tutorial.frozentux.net/iptables-tutorial.html)
OpenBSD and FreeBSD utilize OpenBSD's PF or IPFW. PF is arguably one of the best (and free) firewall apps, in my mind. I haven't spent terribly much time working with iptables.

---

### Post by windependence on 2008-09-17
As tomasq has said, pf is one if the best. If you want a gui interface for it, try pfsense for your firewall. Lots of great features and very simple to get working fast.

-Tim

---

