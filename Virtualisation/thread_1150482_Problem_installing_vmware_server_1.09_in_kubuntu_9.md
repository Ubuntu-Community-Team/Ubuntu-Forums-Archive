---
title: "Problem installing vmware server 1.09 in kubuntu 9.04"
date: 2009-05-06
forum: Virtualisation
---

### Post by Victor Warner on 2009-05-06
I would like to install vmware server 1.09 in kubuntu 9.04 and have tried to follow the procedure found at [http://ubuntuforums.org/showthread.php?t=1120414&page=1]("http://ubuntuforums.org/showthread.php?t=1120414&page=1"):

> # Vmware Server 1.0.9 - As usual VMWare takes a little effort

Basically follow the instructions here .

Extract the vmware archive. This will extract to a directory "vmware-server-distrib"

DO NOT run the install script (vmware-install.pl) ... yet

First download the patch for the 2.6.27 kernel (works on the 2.6.28 kernel as well) from here. Extract the archive (vmware-update-2.6.27-5.5.7-2) and save it inside the "vmware-server-distrib" directoy.

Now (assuming all this is in your home directory)

Code:

cd ~/vmware-server-distrib/vmware-update-2.6.27-5.5.7-2

and run the "runme.pl" as root.

Code:

sudo ./runme.pl

the "runme.pl" will call the installer and from there continue with the installation, including entering a serial number and configuring your keyboard. 

Having downloaded vmware-update-2.6.27-5.5.7-2, extracted it as suggested and gone to ~/vmware-server-distrib/vmware-update-2.6.27-5.5.7-2 and run "sudo ./runme.pl, I get the following error:

> Unable to open the installer database /etc/vmware/locations in read-mode.

Execution aborted.


There appears to be no /etc/vmware/locations folder on my computer. 

Help with this issue would be greatly appreciated.

Victor Warner.

---

### Post by moghovich on 2009-05-13
Follow the instructions you have to untar the vmware-server-distrib dir, and put the vmware-update-2.6.27-5.5.7-2 dir inside the vmware-server-distrib dir.

Then, against their instructions, cd into vmware-server-distrib and run "sudo ./vmware-install.pl".  Follow their instructions until it asks if you want to run vmware-config.pl, at this point say 'no'.

Then, cd into vmware-server-distrib/vmware-update-2.6.27-5.5.7-2 and run "sudo ./runme.pl".  It will go through it's own setup, and at the end it will ask if you want to run vmware-config.pl.  At this point you can say 'yes'.

After that was all done, I could run vmware and start up virtual machines.  I got one error like so:

kde4-config: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)

But, this didn't appear to affect the functionality of VMware.

cheers
  Jeff Breadner

---

