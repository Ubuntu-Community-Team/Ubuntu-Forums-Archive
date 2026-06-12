---
title: "VMware Player 2.5.1 Bridged wireless networking fix?"
date: 2009-02-18
forum: Virtualisation
---

### Post by daverab on 2009-02-18
Here's the deal. Vmware player 2.5.1 bridges my wireless internet connection on linux. I have to manually kill the vmware-networks service every time to make sure the host computer gets a working internet connection.

Is there any way of changing this in vmware-player? The 2.5.1 release does not have the good old vmware-config.pl command/program to do this.

Alternatively, how would I set up a script to run the following command on session login:

sudo (or gksudo) vmware-networks --stop

Thanks for any help.

---

### Post by daverab on 2009-02-24
So I found a workaround through a google search of the command.

For those that are interested and have a similar issue (wireless adapter being bridged to the vmware machine and host losing connection due to this setup), the solution is the following:

sudo gedit /etc/vmware/networking

Remove the lines associated with vmnet8

Save and close the file.

Restart the networking services with:
sudo vmware-networks --stop
sudo vmware-networks --start

---

