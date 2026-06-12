---
title: "Can't access Virtual Server from outside LAN Virtualbox"
date: 2011-06-15
forum: Virtualisation
---

### Post by roundhay on 2011-06-15
I have installed virtualbox 4.0 on a Ubuntu 10.4 Server host and have installed a 10.4 Server VM as a guest.

The guest was set up with bridged network connect following this guide

[http://www.howtoforge.com/vboxheadless-running-virtual-machines-with-virtualbox-4.0-on-a-headless-ubuntu-11.04-server]("http://www.howtoforge.com/vboxheadless-running-virtual-machines-with-virtualbox-4.0-on-a-headless-ubuntu-11.04-server")

I have also given the VM a fixed IP and have installed the zoneminder CCTV package.

I can access the VM over my LAN and can see the zoneminder page by going to 
[http://192.168.1.BBB/zm]("http://192.168.1.XXA") in a browser.

However I cannot access the apache 'It Works!' page or the zoneminder page from outside of my LAN. I have set my router to forward port 80 to the VM IP 192.168.1.BBB

If I set the router to forward port 80 to the host IP 192.168.1.AAA then I can access the apache 'It Works' page and can also access the torrentflux page.

I'm not sure if I have missed something during the set up or if there is an issue with the router.

Any / all suggestions welcome

---

### Post by rothux.j on 2011-06-15
I seriously have no idea here, this isn't my area...
But are you 100% that you are forwarding over the correct port? I wouldn't think it would matter in this case though...

---

### Post by roundhay on 2011-06-16
I have solved the problem, not sure exactly what caused it but I noticed a difference in the output on the following command when run on the host and guest:

On Host
```
:~$ route
          Kernel IP routing table
          Destination     Gateway         Genmask         Flags Metric   Ref    Use Iface
localnet        *               255.0.0.0       U     0      0        0 eth0
default         192.168.1.1     0.0.0.0         UG    100    0        0 eth0
```

On guest
```
:~$ route
          Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
localnet        *               255.0.0.0       U     0      0        0 eth0

```

The second 'default' line was missed, I change some of the settings and the netmask in /etc/network/interfaces re ran route and got the same output as the host system and can now access wed pages on the virtual machine.

---

