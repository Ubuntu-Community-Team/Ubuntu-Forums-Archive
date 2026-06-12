---
title: "VMWare on 7.04"
date: 2007-11-24
forum: Virtualisation
---

### Post by AnimalMagic on 2007-11-24
I've installed the windows installer version and am trying to get VMWare 6 to run. It installed OK, but when I attempt to open a VM I get a message 'Failed to allocate page for guest machine'. This occurs on a new VM before even attempting to load an OS and on a downloaded virtual appliance...

I'm relatively inexperienced with Linux, so simple suggestions welcomed :-) 

Regards

---

### Post by dpj23 on 2007-11-25
O.K., I will try and help as much as I can...

1st., Let me ask about your configuration....  I assuming Linux (Ubuntu) is the host operating system and Windows XP is your guest operating system... Is this correct...

2nd., your trying to install VM workstation 6 for Linux, Is this correct???

---

### Post by AnimalMagic on 2007-11-25
Thanks for the response.

1. Yes, Ubuntu 7.10 and 7.04 as host (tried both) and winXP and Ubuntu as guest. Same issue - it doesn't get as far as installing the guest. I've also tried to load some downloaded appliances and it always dies with the same error.

2. I have tried both 5.5 and 6, same result.

Regards

---

### Post by dpj23 on 2007-11-25
I referenced the workstation guide to come up with solution: I had to do this a couple of times when I was running the beta and it re-configured vmware to run...

1. log on as root or a open terminal and escalate privileges...

2. the command to configure or re-configure vmware is "vmware-config.pl"

3. this should go through your set-up and make or correct any problems that may have happened for you...

****note this is a manual way of correcting the problem, so you could be answering/responding to about 100 questions in the command prompt...  However, there is a end in sight and this has work great for me in the past...

below is what I copied from the manual....

So my suggestion would be to config the software using this command and lets see where we are at...

------------------------------------------------------------------------------------------



Configuring Workstation with** vmware-config.pl**

This section describes how to use vmware-config.pl to configure your 
installation of VMware Workstation.

Required Configuration Changes
Configuration with vmware-config.pl is required in the following circumstances:
1.  When you install VMware Workstation the first time.
2.  When you upgrade your version of Workstation.
3.  When you upgrade your host operating system kernel. (It is not necessary to reinstall Workstation after you upgrade your kernel.)

To reconfigure the networking options for Workstation—for example, to add or
remove host&#8208;only networking.
Location of vmware-config.pl

The installer places vmware-config.pl in /usr/bin. If /usr/bin is not in your
default path, run the program with the following command:
/usr/bin/vmware-config.pl

NOTE If you run the RPM installer, you need to run this program separately from the command line. If you install from the tar archive, the installer offers to 
launch the

configuration program for you. Answer Yes when you see the prompt.

---

