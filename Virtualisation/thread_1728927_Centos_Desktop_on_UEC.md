---
title: "Centos Desktop on UEC"
date: 2011-04-14
forum: Virtualisation
---

### Post by shahin on 2011-04-14
Greetings
  I have a centos desktop image on my cloud controller, but I can not spin new VMs.  The new VM only runs for a few minutes and then terminates.  Can you point me to validated procedures for this or point me to the right log to find out what is going wrong please?
I saw a comment at the bottom of this link about VM crashing at boot about encrypted file system.  I do not know how to verify this.  Here is the link:
[https://help.ubuntu.com/community/UEC/CreateYourImage]("https://help.ubuntu.com/community/UEC/CreateYourImage")

---

### Post by shahin on 2011-04-14
I found what the issue was.  It has to do with one of my servers not supporting Hardware Actualization.  The issue is documented here: [https://bugs.launchpad.net/ubuntu/+source/vm-builder/+bug/445253]("https://bugs.launchpad.net/ubuntu/+source/vm-builder/+bug/445253")  
One other interesting piece of information I like to share is the nc.log, which is on the node controller  I use the logs a lot when I troubleshoot, and assumed that all the logs I need would be on the cloud controller.  But I found my problem in the nc.log, so I do not want others to make the same mistake.  Happy cloud computing :-)

---

