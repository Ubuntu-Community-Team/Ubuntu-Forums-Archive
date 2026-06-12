---
title: "Port forwarding and vmware server"
date: 2008-03-16
forum: Virtualisation
---

### Post by Zalbor on 2008-03-16
I have a Windows XP guest in vmware-server, with an Ubuntu 7.10 host. The connection type I chose was "NAT" which, unless I'm mistaken, gives the guest OS the same IP as the host OS.

I need a port to be open in the guest OS, so I've set up port forwarding for that port giving the host's IP. If I test from the host OS the port is open, but programs in the guest OS report it to be closed.

What am I doing wrong?

---

### Post by ruibernardo on 2008-03-16
> **Zalbor said:**
> I've set up port forwarding for that port giving the host's IP.
Hi zarbor, where did you «set up port forwarding for that port giving the host's IP»?

---

### Post by Zalbor on 2008-03-17
On my router's virtual server, like I've done for another computer on my network and for this one's host OS. It works fine for these two.

---

### Post by ruibernardo on 2008-03-17
/etc/vmware/vmnet8/nat/nat.conf?

---

### Post by Zalbor on 2008-03-17
Aha, I didn't know about that. Thanks.
I figured that in the virtual network between host and guest everything would be open.

---

### Post by ruibernardo on 2008-03-18
The NAT interface has a virtual router that makes the NAT to the outside and makes the guests inaccessible from there. To make a virtual http guest server from the outside, edit the nat.conf file

```
sudo nano /etc/vmware/vmnet8/nat/nat.conf
```

And in the incomingtcp section, forward the host port to the guest port:

```
[incomingtcp]
80 = 192.168.15.128:80
```

Just like in a real hardware router. Shutdown all the VM, close vmware and restart the vmware service with (changes will not take effect until you do this):

```
sudo /etc/init.d/vmware-server restart
```

---

### Post by fjgaude on 2008-03-18
The restart command:

```
sudo /etc/init.d/vmware-server restart
```

can be that but if you downloaded the server program from vmware.com the vmware-server is simply vmware.

I know there are slight differences between the vmware server program that we get from the Ubuntu dipository versus the one we get from vmware web site. Strange.

---

### Post by sgopal on 2011-04-23
[FONT=Verdana]Hello,
I have a question on the same lines as this thread. Below is my set-up

Host: Ubuntu 8.0
Vmware Server : 2.0
Number of VM Images on VmWare Bridge Network = 3
Number of VM Images on VmWare NAT Network = 1

Objective is to have a network communication going between VM machines of the Bridge Network and VM Machines of the NAT network. How do I achieve the same? The Host machine is able to ping both VMnet1  and VMnet8. 

I'm in need of much more than just web service. I'm simulating an Exchange 2010 environment with some servers internal to the Enterprise and one server on DMZ for handling e-mails from the Internet. The Server on DMX must be able to talk to the servers in the Private network for LDAP and E-mail Synchs. How should I update the 'nat.conf' this case?

Also I'm unable to restart vmware with the command listed on the thread, is it okay to run the vmware-config.pl instead?

root@LahiriMahashaya:~# route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     1      0        0 eth0
192.168.181.0   *               255.255.255.0   U     0      0        0 vmnet1
172.16.149.0    *               255.255.255.0   U     0      0        0 vmnet8
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
root@LahiriMahashaya:~# 

I'd really appreciate on any inputs/directions that you can provide,

Thanks in advance
sgopal
[/FONT]

---

### Post by rich-york on 2011-04-25
[COLOR=#000000][FONT=Times New Roman][COLOR=#333333][FONT=Lucida Grande]Lovely site! I am loving it!! Will be back later to read some more. I am taking your feeds also

Richard
[/FONT][/COLOR][/FONT][/COLOR]

---

### Post by Kissell on 2011-08-26
> **epimeteo said:**
> The NAT interface has a virtual router that makes the NAT to the outside and makes the guests inaccessible from there. To make a virtual http guest server from the outside, edit the nat.conf file

```
sudo nano /etc/vmware/vmnet8/nat/nat.conf
```

And in the incomingtcp section, forward the host port to the guest port:

```
[incomingtcp]
80 = 192.168.15.128:80
```

Just like in a real hardware router. Shutdown all the VM, close vmware and restart the vmware service with (changes will not take effect until you do this):

```
sudo /etc/init.d/vmware-server restart
```

You guys seem to have this working....  can you help me out?  I configured the nat.conf file and restarted vmware, but I still can't connect.  I run "nmap localhost" and nothing is open on port 80...  shouldn't port 80 be open and listening if this worked?

---

