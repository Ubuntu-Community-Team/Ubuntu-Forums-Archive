---
title: "Just starting setup"
date: 2009-05-16
forum: Server Platforms
---

### Post by japtar10101 on 2009-05-16
I've just started setting up an Ubuntu server on this very old E-machine T1090 I got from the recycling bin (hey, it's free!).  I've managed to install the operating system with no troubles.  Furthermore, I opened up a DynDNS account, setup a hostname, and installed the ddclient based on the output of ifconfig.

Unfortunately, I couldn't connect to it.  I've also tried a different ip address from [http://checkip.dyndns.com:8245/](http://checkip.dyndns.com:8245/), but links couldn't connect to it.

So what do I have to do, in both DynDNS.org and on the Ubuntu Server, to get this working?  Currently, I have 4 computers connected to a switch, which in turn, is connected to a Verizon DSL modem.

Also, to make it easier to post some text from the terminal, is there a Ubuntu's equivalent of wgetpaste or a program to send email?  Thank you for your help.

Edit:
Did a little more research.
First off, the modem.  The Modem is a Westell Model 6100 sent by Verizon themselves.  According to this website, I'm supposed to access the "launchmodem" or "192.168.1.254" to get into the modem interface and make some configuration, but I got nothing on my browser:
[http://www.dslreports.com/faq/6658](http://www.dslreports.com/faq/6658)

Furthermore, I've found both my external and internal ip addresses, and according to DynDNS, I'm supposed to use the external ip address.  That I did, and I found all of my 4 PCs seems to share this same address.  Is that due to the switch?  I doubt it'll be a problem, but worth mentioning.

Finally, I've been using this blog post as reference for setting up the computer:
[http://mexpolk.blogspot.com/2008/01/ubuntu-gutsy-dyndns-client-setup.html](http://mexpolk.blogspot.com/2008/01/ubuntu-gutsy-dyndns-client-setup.html)
As such, my /etc/ddclient.conf looks as follows:
```
ssl=yes
daemon=300
pid=/var/run/ddclient.pid
protocol=dyndns2
use=web, web=checkip.dyndns.com/, web-skip='IP Address'
server=members.dyndns.org
login=japtar10101
password=(secret)
japtar10101.homelinux.com
```

And /etc/default/ddclient looks like:
```
run_ipup="false"
run_daemon="true"
daemon_interval="300"
```

DynDNS settings, of course, is as follows:
```
hostname = japtar10101.homelinux.com
* Create wildcard alias for "*.host.domain.tld"
* Host with IP address
(external ip address)
```
I'm pretty much under the impression that the modem is killing it, yet I have no idea how to access it.

---

### Post by japtar10101 on 2009-05-16
> **japtar10101 said:**
> According to this website, I'm supposed to access the "launchmodem" or "192.168.1.254" to get into the modem interface

My mistake, the ip was "192.168.1.1".  Now that I'm here...what am I supposed to configure?

---

### Post by ugm6hr on 2009-05-17
What services do you intend to be able to access from outside your local network?  e.g. FTP, SSH, webserver etc.

Can you access the server from within your local network?

In simple terms, you have to forward ports using a router (not sure whether a switch will achieve this).  Else, the server needs to be connected to the modem (and act as DHCP server), and the switch connected to a second ethernet card within the server.

---

### Post by cariboo on 2009-05-17
The switch shouldn't make any difference, depending on which service you want to forward, the setting in the modem/router would be to forward for example if you want to enable ssh, forward port 22 to the ip address of the server. Hopefully you have a static ip address setup on the server, as with dhcp the ip address could change after a reboot.

---

### Post by japtar10101 on 2009-05-19
Sorry, I meant to mark this as fixed, but didn't know how...

---

