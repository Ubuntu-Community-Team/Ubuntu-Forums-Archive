---
title: "Deploying an Ubuntu VM"
date: 2012-08-16
forum: Virtualisation
---

### Post by petebrew on 2012-08-16
I would like to deploy a server application as a VirtualBox virtual machine.  The problem I have is that many of my users are novices with no experience of Linux so they are a little daunted by an Ubuntu command line.  I'm therefore trying to make this as point-and-clicky as possible.

At the moment the VM runs a simple bash script on first boot to ask the user for various inputs.  The thing is that most of these questions are the same ones that are normally asked during the Ubuntu installation e.g. language, keyboard, time zone, http proxy, username, password etc.  Rather than reinvent the wheel is there any way I can re-run the relevant stages of the Ubuntu installation wizard?  

For the installation steps unique to my software, can I use the same command line gui questioning toolkit?  What is this called anyway!?!

Thanks

Peter

---

### Post by CharlesA on 2012-08-16
Do an OEM install - boot from a liveCD and select it from the options before installing.

[http://askubuntu.com/questions/36671/how-do-i-pre-install-ubuntu-for-someone-oem-install](http://askubuntu.com/questions/36671/how-do-i-pre-install-ubuntu-for-someone-oem-install)

This is for the desktop edition, of course. If this is for a server, you are on your own.

---

