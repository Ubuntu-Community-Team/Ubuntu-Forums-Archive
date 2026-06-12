---
title: "vmware install broke my networking : )"
date: 2008-08-04
forum: Virtualisation
---

### Post by thevoiceofalan on 2008-08-04
Hi All,

First post so ello too :)

I installed vmware server yesterday went through the install fine then setup some virtual machines Ubuntu, FreeBSD etc. everything working and communicating fine as expected....

Then today I boot my machine, login and cannot access any web pages looks like a bad cable or similar I then think I will try vmware just incase and low and behold my vm machines get internet access, ssh to remote hosts etc. so yes I am post this from within a virtual machine session :)

network is based around 192.168.1.* ip addresses, subnet 255.255.255.0 etc

Any ideas on where to start with this?

cheers

Alan

---

### Post by KatBuntu on 2008-08-04
Just reconfigure your net:

Set up the interface (In case it is down):
```
#ifconfig <INTERFACE> up
```
Set IP:
```
#ifconfig <INTERFACE> <YOURIP> broadcast <BROADCAST> netmask <NETMASK>
```
Set Gateway:
```
#route add default gw <YOURGATEWAY>
```

The data:
YOURIP: 192.168.1.*
BROADCAST: 192.168.1.255
YOURGATEWAY: 192.168.1.254
NETMASK: 255.255.255.0

If it reconfigures every time you reboot, make a init script with the commands above to configure with your network parameters. I had the same problem with debian etch and vmware workstation.

---

### Post by thevoiceofalan on 2008-08-04
Thanks for the help -  each line appeared to work except:

> #ifconfig <YOURIP> broadcast <BROADCAST> netmask <NETMASK>

where i got the error:

> SIOCSIFBRDADDR: No such device
192.168.1.*:ERROR while getting interface flags: no such device
SIOCSIFNETMASK: No Such device


I tried adding eth0 in to the above but no Joy :(

Still no networking for the host the vm's are fine however :)

---

### Post by KatBuntu on 2008-08-04
Ok, it seems like some <parameter> is incorrect. Access your gateway page, write in a browser: 192.168.1.254, and look which your real IP is. This is a silly question but, are you writing your IP as 192.168.1.*, with the *?

And i forgot the INTERFACE parameter, please forgive me!!

#ifconfig <INTERFACE> <YOURIP> broadcast <BROADCAST> netmask <NETMASK>

Please add the output of a 

```
#ifconfig
```

---

### Post by thevoiceofalan on 2008-08-04
My gateway is 192.168.1.1 I get no http connections or ssh at all

I can ping the gateway but trying to connect does nothing.  

:lolflag: no I didnt put in the *

I will grab the interface info from ifconfig  in a moment I need to figure out how to get that from the host to the guest.

Okay I cannot see away of getting the output of ifconfig from the host to the guest. It has three interface what do you want to know?

eth0
lo
vmnet1
vmnet8

---

### Post by KatBuntu on 2008-08-04
The interface that gives you the internet is eth0, the fact here is that you have a successful internet conection in your VM, that means that your Vmnet with NAT is working well. You set manually the IP adress for Vmnet8 during vmware-config.pl?

---

### Post by thevoiceofalan on 2008-08-04
I have no idea about setting up vmnet8 but inet addr is set to 172.16.206.1

I set up one set of ips etc that I remember.

Could this be the problem?

---

### Post by KatBuntu on 2008-08-04
Well you could have given the real IP to the NAT Vmnet8 IP, and that's why you're having trouble, even if you don't start the virtual machine, the vmnet8 starts when you boot. Try to reconfigure the NAT network with:
```
#vmware-config.pl
```
and let the wizard to search another subnet for vmnet8 and vmnet1.

Since you have internet on your VM, you can access your local gateway page from there, check if there's any visible problem.

---

### Post by thevoiceofalan on 2008-08-05
Okay thanks very much for your help I disabled the networking in vmware and everything is a okay now :)

I will have another go tonight at the routing.

---

