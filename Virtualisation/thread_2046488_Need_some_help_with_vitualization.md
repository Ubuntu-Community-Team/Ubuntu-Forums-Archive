---
title: "Need some help with vitualization"
date: 2012-08-23
forum: Virtualisation
---

### Post by intenzive on 2012-08-23
Hello guys!
First I'm glad I joined Ubuntu forums at last :) As I said in the title I need some help with virtualization and som eother stuff. I'm not quite sure this is the right section but please excuse me if not.
Now let's go the real part of the things. My idea is to virtualize about 5 physical machines with VMWare ESXi server ( or something else if you have better ideas) and start and run them though the already build LAN between them. So I'll have a server with the software for virtualization and the other physical machines which will be subscribers and connect to the server to start their OS. About the physical machines - i do not want to install any OS on them ( they will boot the OS through the network). My idea is to create a USB pendrive   for each computer with custom Ubuntu LiveCD with preinstalled VMWare player. The pendrives will work like keys and the holder of the key will be able to use any computer on the LAN to work on his own virtual machine.
I searched the internet to find something similar to help me but with no success. So if have any ideas i'll be glad to hear them :) At a leter time I'm considering to remove the big old PC's and put something like Raspberry Pi and use it only for interface to connect to the virtualization server and use it's hardware resources. 
Thanks in advance guys :)

P.S Please don't criticize me about my english :) It's not my mother language :)

---

### Post by dcstar on 2012-08-30
> **intenzive said:**
> 
............
Now let's go the real part of the things. My idea is to virtualize about 5 physical machines with VMWare ESXi server ( or something else if you have better ideas) and start and run them though the already build LAN between them. So I'll have a server with the software for virtualization and the other physical machines which will be subscribers and connect to the server to start their OS. About the physical machines - i do not want to install any OS on them ( they will boot the OS through the network). My idea is to create a USB pendrive   for each computer with custom Ubuntu LiveCD with preinstalled VMWare player. The pendrives will work like keys and the holder of the key will be able to use any computer on the LAN to work on his own virtual machine.
............

ESXi VMs can **only** be controlled by a Windows machine running the propriety Vsphere client - there is no Linux version of this tool.

You can have VMs autostart and running full time in ESXi and then connect to them via the standard remote desktop tools, these tools can be Windows of Linux based.

---

