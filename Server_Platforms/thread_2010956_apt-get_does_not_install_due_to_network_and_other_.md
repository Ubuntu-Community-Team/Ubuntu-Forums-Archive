---
title: "apt-get does not install due to network and other installation issues"
date: 2012-06-26
forum: Server Platforms
---

### Post by jon80 on 2012-06-26
I have just installed Ubuntu 12.04 server (ubuntu-12.04-server-i386.iso), which runs as a VirtualBox 4.1.x virtual machine (guest), and, I am trying to install some UI to make it easier for me to install programs and download using sudo apt-get install, however, it would seem as though the servers do not have the software.

In brief, I need to install Oracle 11g Enterprise for training and application management and programming utilities which require an operating system with a user interface, has anyone carried out a similar installation?

Finally, it would seem as though the postgresql service which comes with the iso file does not start up, perhaps it conflicts some other service or port.

Internet connection exists - because I ping google.com.mt like there is no tomorrow, however it is noted that only the loopback adaptor (127.0.0.1), and, an IP address (10.0.2.15) were assigned to the virtual machine, which is unusual considering that the host machine seems to start off with 192.x.x.x.  I think that this is the way that VirtualBox 4.1.x network settings are configured.

I cannot copy and paste the results of ifconfig, and the command line, however, I have taken a snapshot and can reply to questions.

Does any company support apt-get installations services provided, please?  

I am only a nix-hobbyist doing training, please don't mention exorbitant fees.

---

### Post by rukiaEnix on 2012-06-26
Have you checked if those repos are online?

And about the VB network, if you have that IP assigned is because you are using NAT connection.
But you can change your VB network to Bridge Adapter and be in the same network as your hosting machine.

---

### Post by kennethconn on 2012-06-26
What command(s) are you typing and what message(s) are you getting returned?
 
Have you done sudo apt-get update first?
 
The VB config (NAT vs. Bridged) does not seem to be the problem at the moment as you said you can ping google.com.mt.

---

