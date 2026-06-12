---
title: "Trouble installing VMware server"
date: 2008-01-25
forum: Virtualisation
---

### Post by indianballer24 on 2008-01-25
Whenever I try to install WMware server, I get the following problem. I am running it as root. Can anyone help me?


root@indianballer24-laptop:/home/indianballer24# '/home/indianballer24/Desktop/vmware-server-distrib (2)/vmware-install.pl'
Creating a new installer database using the tar3 format.

Installing the content of the package.

In which directory do you want to install the binary files? 
[/usr/bin] 

What is the directory that contains the init directories (rc0.d/ to rc6.d/)? 
[/etc] 

What is the directory that contains the init scripts? 
[/etc/init.d] 

Unable to copy the source file ./installer/services.sh to the destination file 
/etc/init.d/vmware.

Execution aborted.

---

### Post by fjgaude on 2008-01-25
Beats me what is wrong... I've never installed from the desktop, always from /home/frank, that's me.

I've always cd to the vmware directory and then used ./vmware-install.pl

Think you have to be root to do all this.

---

### Post by dbqp on 2008-01-25
Try following this guide:

[http://www.ubuntugeek.com/how-to-install-vmware-server-in-ubuntu-710-gutsy-gibbon.html]("http://www.ubuntugeek.com/how-to-install-vmware-server-in-ubuntu-710-gutsy-gibbon.html")

---

### Post by indianballer24 on 2008-01-25
I have tried following that guide but I still get the same error. I have heard that there is a patch needed. Is that true?

---

### Post by dbqp on 2008-01-25
I didn't need a 'patch' and I am running VM Ware Server on 7.10

You could also try this guide, which I use all the time for new VM Ware installs:

[http://ubuntuforums.org/showthread.php?t=183209]("http://ubuntuforums.org/showthread.php?t=183209")

Don't mind that it discusses 6.06. I have never run into a problem using this guide for 6.06, 6.10, or 7.10

---

### Post by indianballer24 on 2008-01-25
I tried that tutorial but I still got the same error on the same step.

---

### Post by dcstar on 2008-01-27
> **indianballer24 said:**
> I tried that tutorial but I still got the same error on the same step.

What is wrong with the VMware server package in the Partner repo?

---

### Post by rosegarden78 on 2008-01-27
Sorry no luck VMware commercial product instruction confusing try downloading VirtualBox from the repositories instead it so easy!  [http://ubuntuforums.org/showthread.php?t=679884](http://ubuntuforums.org/showthread.php?t=679884)

---

### Post by DamagePlan on 2008-01-27
I had this same problem. The way I sorted out was bu going to system -> admin -> synaptic package manager,
Then search for vmware and select and install the software,

---

