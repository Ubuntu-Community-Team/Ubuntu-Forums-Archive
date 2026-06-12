---
title: "Vmware server WONT FREAKIN WORK!"
date: 2007-12-23
forum: Virtualisation
---

### Post by gubemton on 2007-12-23
I need help please.Vmware Wont Launch anymore  so I decided to uninstall it then install it again but that didn't work so Ill Show you the output:

 > **@*****:~$ sudo apt-get install vmware-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
vmware-server is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking, 0B of additional disk space will be used.
Setting up vmware-server (1.0.4-1gutsy2) ...
invoke-rc.d: unknown initscript, /etc/init.d/vmware-server not found.
dpkg: error processing vmware-server (--configure):
 subprocess post-installation script returned error exit status 100
Errors were encountered while processing:
 vmware-server
E: Sub-process /usr/bin/dpkg returned an error code (1)


Now it just wont work! Im really Tired and Mad because Vmware wont work and Virutalbox  wont connect to the internet! HELP PLEASE!:confused::confused:

---

### Post by K.Mandla on 2007-12-25
Moved to Virtualization.

---

### Post by fjgaude on 2007-12-25
It seems you need to completely remove everything associated with vmware before you can re-install it. Use Synaptic to do this.

Click on Status, then do Search for vmware, after it shows, click on Completely remove configs, etc., to get it all off your machine.

Then try the re-install. It should go through without errors.

Merry Christmas.

---

