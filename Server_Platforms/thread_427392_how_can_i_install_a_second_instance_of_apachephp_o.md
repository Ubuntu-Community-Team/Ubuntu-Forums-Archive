---
title: "how can i install a second instance of apache/php on a same computer?? server version"
date: 2007-04-29
forum: Server Platforms
---

### Post by envis on 2007-04-29
if i was using a desktop version of linux localy, i can think of many simple simple ways to achieve that, like setting up and running a vmware or quemu to run the second server..

but i can only axs my server remotely with ssh... and its a server version..

im a bit confused about how i could run a second server on that same box..

ive already lost so much time on this but it didnt work... i tried to make a chroot! following basically this guide:
[http://danieldandrada.blogspot.com/2006/09/ubuntu-chroot-environments.html](http://danieldandrada.blogspot.com/2006/09/ubuntu-chroot-environments.html)
and i was succesful in creating a working chroot, in which i was able to apt-get apache and php successfuly. set the port of that chrooted apache to 88 and restarted it... but i was not able to connect to it...

when i restarted apache actually it said nothing!... no error, no messages... normally it should say something...
same thing when restarting networking on the chroot... 
i noticed /etc/network/interfaces was empty! maybe its normal in the way the chroot is installed, not sure! i was able to ping stuff from chroot environment, does that mean anything?

anyways, i copied the "/etc/network/interfaces" from the main environment, was able to get error message about /var/run on networking restart.. copied stuff about network and apache from main environment to chroot, was then able to get success messages when restarting networking and apache, and main server was still running! (well second time, when i had understood that chroot should not have other ip on same eth, it changed the ip of the main server...).. anwyways.. the chrooted apache then really seemed to work and was on port 88 but still... no way to reach it at all....

was there something i was missing to be able to run a second server in a chroot?

can i maybe achieve that with vmware or qemu instead? how can i use those with my server version of ubuntu? only command line...?

---

### Post by gombadi on 2007-04-29
VMWare server will install fine over an ssh command line only link.

Once it is installed you start VMWare on you local machine and tell it to connect to the remote machine. It uses port 902 so make sure that is open from your location (may pay to firewall off from the rest of the world). 

I have two vmware installs running on remote machine - one on the other side of the room and the other on the other side of the world and after it is installed i have had no problems with it.

Check the forums for instructions on getting VMware installed.

Of course if you want to get a more efficient method of creating virtual servers then I would suggest [http://www.openvz.org]("http://www.openvz.org")
You may be able to find a kernel package but it may require you to compile your own kernel to get it working.
I have some random notes that I should cleanup and make into a howto some day. [http://www.gombadi.com/openvz.txt]("http://www.gombadi.com/openvz.txt")

---

