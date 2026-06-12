---
title: "SSHd connection refused"
date: 2008-10-02
forum: Server Platforms
---

### Post by NetSkay on 2008-10-02
hey guys, i have a server running win2k3 connected to a T1 line with a static public IP, no routers, no NATs, clear direct connection... 
i installed VMware gsx server and ubuntu server platform on the VM, ubuntu has a connection to the internet and everything, i set the network adapter to NAT...
i have SSH daemon running, when i connect on the local NAT ip from the host OS over SSH, ie putty-> 192.168.98.132, it works however when i enter the T1 IP and i try to connect from outside the internet from a different machine on a different ISP, it gives me connection refused, i disabled all software firewalls (windows builtin one) and the av, but it still refuses my connection

very wierd any ideas, i also tried changing hte port, but same difference

---

### Post by kevdog on 2008-10-03
run the ssh client with the -vvv (3 v's) flag so it gives debugging output and hopefully it will tell us where the problem is occuring.

---

### Post by lykwydchykyn on 2008-10-03
If my understanding is correct, using NAT mode makes the host OS like a router or gateway for the virtual guest.  So just like a "real router" you would need to configure some kind of port forwarding to the guest for this to work.  I haven't used vmware in a few years (using VirtualBox now), so while I seem to remember this can be done, I couldn't tell you exactly how.

Check the vmware documentation about forwarding ports to the guest.

---

