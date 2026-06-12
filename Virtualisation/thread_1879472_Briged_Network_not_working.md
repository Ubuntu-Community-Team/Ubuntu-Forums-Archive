---
title: "Briged Network not working"
date: 2011-11-11
forum: Virtualisation
---

### Post by sn8keyz on 2011-11-11
How's it going? Hopefully, someone here can help me with my issue.
 
I unable to get Ubuntu 64-bit Server 11.10 to accept a bridged connection from it's VM host. 
 
I have created a guest VM - Ubuntu desktop 64-bit and it works without a problem immediately after install.
 
When I initially installed Ubuntu Server "guest", I had NAT selected for the network and was able to connect to the internet with no issue. However, when I select "Bridged Networking" in the VM settings, whether it is VMWare or Virtualbox, it will not work.
 
I did attempt to take my Ubuntu desktop's /etc/network/interfaces config and duplicate the entries into the Ubuntu Server's /etc/network/interfaces file. However, that did not work either
 
I, also disabled the iptables, just in case there was a rule preventing such connection.
 
 
My config is below:
 
VMWare and/or Oracle Virtualbox
Host = Windows Professional 7.0
Guest = Ubuntu Server 11.10 64 bit
 
I have bloodied my fingers searching Google for an answer but am coming up short.
 
Can anyone here assist?
 
:confused::confused::confused:

---

### Post by dcstar on 2011-11-12
> **sn8keyz said:**
> How's it going? Hopefully, someone here can help me with my issue.
 
I unable to get Ubuntu 64-bit Server 11.10 to accept a bridged connection from it's VM host. 
 
I have created a guest VM - Ubuntu desktop 64-bit and it works without a problem immediately after install.
 
When I initially installed Ubuntu Server "guest", I had NAT selected for the network and was able to connect to the internet with no issue. However, when I select "Bridged Networking" in the VM settings, **whether it is VMWare or Virtualbox,** it will not work.
 
I did attempt to take my Ubuntu desktop's /etc/network/interfaces config and **duplicate the entries into the Ubuntu Server's /etc/network/interfaces file**. However, that did not work either
........
[LIST=1]
[*]You cannot have two different VM systems installed on the same machine.
[*]You cannot have two devices on the same network with the same IP address.
[/LIST]

---

### Post by sn8keyz on 2011-11-12
Thanks for the response, David.
 
However, I am not running multiple VM guests on my host at the same time. I, only created the Ubuntu desktop image to see if I would have same issue as Ubuntu Server...and I am not.
 
When I boot Ubuntu desktop, the O/S automatically picks up the IP, gateway and DNS of my router with no issue. However, with Ubuntu Server, with Bridged Networking enabled, it will not pick up any information - NAT does work immediately after I change the VM setting.
 
Per the suggestion of my co-worker, I modified the /etc/network/interfaces in the Ubuntu Server image file with the necessary information but I am running into a wall..a brick one. 
 
I did notice that Ubuntu desktop is not using the /etc/network/interfaces file to establish the ip settings as there is no entry in the file for eth0. I did a ifconfig to ensure that eht0 is being used to establish a network connection.
 
That leads me to ask if Ubuntu Server uses another file to establish the network interfaces.
 
If you need for me to post my interface file from my Ubuntu Server image, let me know.
 
PR

---

### Post by dcstar on 2011-11-17
> **sn8keyz said:**
> Thanks for the response, David.
 
However, I am not running multiple VM guests on my host at the same time. I, only created the Ubuntu desktop image to see if I would have same issue as Ubuntu Server...and I am not.
........

Your previous post says:

*whether it is VMWare or Virtualbox*

You **cannot** run two **VM managers** on a host, so which one is it?

---

