---
title: "Network interface configuration in shell"
date: 2008-10-11
forum: Server Platforms
---

### Post by nadalizadeh on 2008-10-11
I've installed a fresh server edition and didn't configure the network interfaces in the setup procedure. Now I want to set ip, gateway, etc and can't find any utility to do this like what we have in redhat ones (setup) or netcardconfig and so (except editing /etc/network/interfaces by hand)

Any helps ?

---

### Post by lucaspr on 2008-10-11
I too a little suprised with the fact that there is no program for this like netcardconfig (although it can be installed with apt-get)

For myself using the following lines was sure easy enough!

sudo nano / vi / pico / whatever /etc/network/interfaces
sudo /etc/init.d/networkking restart

---

### Post by barrycom on 2008-10-12
This reply is going to come too late I bet... but here it is anyway 8)

On Ubuntu (other versions are similar but may have files in different places)  the network configuration is in /etc/network .

Just edit the interfaces file and add the following...

Edit the interfaces file and add / change the following depending on your setup.

For DHCP assigned addressing

iface eth0 inet dhcp

For Static IP 

iface eth0 inet static
address 192.168.15.1
netmask 255.255.255.0
network 192.168.15.0
broadcast 192.168.15.255
gateway 192.168.15.100


Once configured ifup eth0 should bring it up just fine.

---

### Post by nadalizadeh on 2008-10-20
Thanks for the response, but actually I said except editing /etc/network files by hand, I myself could do this and knew these parameters, but my question was not just for this case.
I mean ubuntu with all its simplicity shouldn't leave such a thing without an interface, and when I'm going to tell someone how to configure his ip info I should say, Hey ! start editing bla bla and remember these words (netmask, address, ...)

If it wasn't required other distros didn't try to make one !

I even didn't find any utility in the repository too. :(

---

### Post by cariboo on 2008-10-20
IF you feel that a function is missing please start a bug report here:

[https://bugs.launchpad.net/](https://bugs.launchpad.net/)

You will have to create an account. If the devs don't know there is a problem, they can't fix it.

Jim

---

### Post by lykwydchykyn on 2008-10-21
Personally, I've always thought editing the file was pretty easy.  If it were properly commented with some examples and syntax, it'd be perfect.  Just my opinion.

---

