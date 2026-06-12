---
title: "Virtual machine in VMWare on Strato-rootserver not connectable from Internet"
date: 2009-08-11
forum: Virtualisation
---

### Post by rpw on 2009-08-11
Hallo,

I've installed VMWare Server 2 on a Strato (german hoster) rootserver, and installed one virtual machine from the VMWare webinterface. The network for this virtual machine uses NAT from VMWare. In this webinterface there is a console for the virtual machine, from which I can access the internet, do updates, etc. So the virtual machine can connect to the internet. On both system Ubuntu server 8.04.3 is running.

Then I configured iptables on the rootserver.

I don't want to tell the real IP-address of the rootserver, so I will use xx.xxx.xxx.xxx instead. The virtual machine gets the internal IP-address 192.168.137.128 from NAT of the VMWare server.

Then I did the following.

1) activatet IP-forwarding:
echo '1' > /proc/sys/net/ipv4/ip_forward
Entry in "/etcsysctl.conf" for reboot of the rootserver

2) Routing incoming traffic from TCP-port 6501 on Rootserver to port 22 of the virtual machin:
iptables -t nat -A PREROUTING -p tcp -d xx.xxx.xxx.xxx --dport 6501 -i eth0 -j DNAT --to-destination 192.168.137.128:22

3) Routing all outgoing traffic of the vitual machine to rootserver:
iptables -t nat -A POSTROUTING -s 192.168.137.128 -o eth0 -j SNAT --to xx.xxx.xxx.xxx

4) iptables -L -n -t nat now show the follwing:
Chain PREROUTING (policy ACCEPT)
target     prot opt source               destination
DNAT       tcp  --  0.0.0.0/0            xx.xxx.xxx.xxx      tcp dpt:6501 to:192.168.137.128:22
- - - - - - - - - - - - - - - - - -
Chain POSTROUTING (policy ACCEPT)
target     prot opt source               destination
SNAT       all  --  192.168.137.128      0.0.0.0/0           to:xx.xxx.xxx.xxx
- - - - - - - - - - - - - - - - - -
Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

5) Installed ssh-server on the virtual machine using VMWare-Console from the webinterface. Did not change default ssh-port 22 here in this virtual machine.

Now the following things work:
1) I can login to the rootserver using ssh (of course).
2) I can login to the virtual machine using the console from the webinterface of VMWare.
3) Virtual machine can connect to the internet, installing programs and other things works.
4) When I'm logged into the rootserver via ssh I can login to the virtual machine using again ssh. So there is a connection from the rootserver to the virtual machine and back.

But I can not connect to the virtual machine directly from the internet. When I try to login via ssh to the rootserver and use port 6501 (which should be redirected to port 22 of the virtual machine), I get the error message "connection refused".

Any idea what's wrong here, or what I have to do/change, to make this work?

Gruß,

rpw

---

