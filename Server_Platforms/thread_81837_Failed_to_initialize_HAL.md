---
title: "Failed to initialize HAL"
date: 2005-10-25
forum: Server Platforms
---

### Post by pizzipie on 2005-10-25
Hi all;

I previously had this question in the beginners forum. I guess that is the wrong place as I didn't get any responses. I'll try again here even though this doesn't have to do with servers, does it?
 
 I have a dell D800 running 5.04. Recently I began getting two error messages:
 1. Failed to initialize HAL
 2. Can't access ACPI events in /var/run/acpid.socket. Make sure ACPI subsystem is working and the acpid daemon is running.
 
 What is HAL, ACPI events and acpid daemon. What do they do?? Where can you read about them?
  
 After 2:23 min laptop beeps twice! (I've timed this several times and it is consistant)
 
 I am using a US Robotics modem which does not work prior to the beeps. But does after. So I do know the modem is affected
 
 RP

---

### Post by jasmuz on 2005-10-26
HAL: Hardware Abstraction Layer, it serves as a compability layer between hardware and programs in your system.

You can solve the issue by typing in a command line, sudo apt-get install hal

ACPI: Advanced Configuration and Power Interface, serves to control the power management in your machine. and the daemon does that for linux.

I recommend you reinstall your ACPI subsystem, with sudo apt-get install acpi

---

### Post by pizzipie on 2005-10-26
Thanks jasmuz,

I tried reinstalling hal and acpi with Synaptic pkg mgr. I then re-booted the machine and got the same errors. I then tried apt-get install with both of these and the message was that I had the latest  versions of both pkgs.

I then thought I would un-install all of hal and acpi. Synaptic wanted to  remove  gnome-desktop and a whole lot more of  serious stuff and I chickened out. 

Any other ideas?

---

### Post by pizzipie on 2005-10-27
After probing around I found that after 2-1/2 min or so hald.pid is in /var/run/hal/ and acpid.socket is in /var/run.

Any one know why the 2-1/2 minute delay in getting these to work??

---

