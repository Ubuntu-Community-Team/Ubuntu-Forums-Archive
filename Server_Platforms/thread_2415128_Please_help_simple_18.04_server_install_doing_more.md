---
title: "Please help simple 18.04 server install doing more than wanted possibly?"
date: 2019-03-20
forum: Server Platforms
---

### Post by adrian-h on 2019-03-20
This is probably just me being a bit ignorant of the installation procedure?

Just downloaded the Ubuntu 18.04 server iso some 834 Meg.
transferred to a USB stick and installing from that.

I just wish to run a simple BBS system so will be installing the LAMP packages.
Steps are 
Englis
English UK for keyboard.
In the next stage there are three options 

Install ubuntu
Install MAAS bare-metal cloud (region)
Install MAAS bare-metal cloud (rack)

The first option is selected

It finds my network interface OK enp0s25
No proxy
Default mirror [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)
I use the entire disk
 which is only a small disk around 230 Gig

Add my name, name of server, username and password.

I check the box to install Openssh server

On the featured Server snaps I have nothing checked and go down to done.

it installs, a few messages about various curtain's? and the last few lines are

finalizing installation
configuring cloud-init
installing OpenSSH server 
cleaning up apt configuration

So I reboot the PC remove the usb stick and it reboots.

Within a minute it is back up and running and I get messages on terminal
about running cloud -init with the last two messages are Started Execute cloud user/final scripts.
Reached target cloud-init target.

What was all the cloud init doing is it just there to finish installation or have I installed something else connected to the cloud?

May be a dim question to many.

Adrian

ps the documentation here [https://tutorials.ubuntu.com/tutorial/tutorial-install-ubuntu-server#0](https://tutorials.ubuntu.com/tutorial/tutorial-install-ubuntu-server#0) and subsequent pages
does not mention anything about going into cloud-init at the end?

---

### Post by adrian-h on 2019-03-20
OK I have done some digging and it appears to be a way of installaing snaps?  preconfigured packages I guess, not that technical at this end  so I found and followed this article:-

[https://nucco.org/2018/05/ubuntu-18-04-chronicles-removing-cloud-init.html](https://nucco.org/2018/05/ubuntu-18-04-chronicles-removing-cloud-init.html)

Which seems to stop the unit going off and looking for these installation sources if I can call them this, when I get to my end result the computer will probably not be connected to the internet as it is just for me to learn stuff on on my home network.

Adrian
I was just surprised it was installed when i had not selected anything else other than ssh.

Confused

Adrian

---

