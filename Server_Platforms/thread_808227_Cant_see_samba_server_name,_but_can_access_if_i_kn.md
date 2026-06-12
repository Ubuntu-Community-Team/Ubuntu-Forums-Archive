---
title: "Cant see samba server name, but can access if i know the ip address"
date: 2008-05-26
forum: Server Platforms
---

### Post by rslrdx on 2008-05-26
This is one of those little stupid things we missed in the configuration I`m sure.

I cant see the samba server when i go to Places>>Network, but if I type the ip address of the server, I can see the share and access it without a problem. 

So, my question is, How can i fix this little thing? i just want it to "broadcast" the server name. 

Network config

The share is on 192.168.2.XXX (all servers are on 192.168.2.XXX network)

Desktops are on 192.168.1.XXX (all desktoos are on 192.168.2.XXX network)

i cant see the server name in either networks.

thanks,
Rodrigo.

---

### Post by thefunnyman on 2008-05-26
I think you need to modify your /etc/hosts file to specify what names get associated with a particular IP address.

```

127.0.0.1       localhost
192.168.2.xxx   comp-name

```

kind of a pain if you have a bunch of machines, but that's how I've always done it.  If you're running a domain server, you might have other options, but I don't know anything about DNS servers.

Hope this helps

---

### Post by volkswagner on 2008-05-26
I had the same problem.  I did not know I needed to change /etc/hosts on both machines though.  Just a heads up.  Now I always add machine names to all my networked pc'c /etc/host file.  Works great so I can ssh with the host name rather than ip.

---

### Post by inportb on 2008-05-26
AFAIK, you're looking at two different subnets. Broadcasts do not work across subnets, because otherwise the Internet would be full of them. You can bridge them into a VPN ;p

---

### Post by rslrdx on 2008-05-26
vpn? its all on the same location (same office) just that one subnet (where servers are) can be accessed from outside and the other (where desktops are) can not.

Any other options? 

using this on a computer shop, the samba share is used for backups, while it works great with just the ip address, it would be better if i could just see it.

thanks for the imput

---

### Post by barichardson5727 on 2008-05-27
It could just be that the share is not browseable in the config file. I have had multiple occasions where using the gui misconfigures the smb.conf file causing this exact same problem. The computer cannot be seen by the name in the network browser but can still be accessed by ip when this is misconfigured.

Check your samba configuration file for the following and restart samba: (/etc/samba/smb.conf)

Example of working configuration:
```

       [share]
	comment = share
	path = /media/hdd/share
	writeable = yes
	browseable = yes
	valid users = xbox


```

This is the configuration that the gui creates, this does not work. You can see that the browseable entry has been commented out.
```

       [share]
	comment = share
	path = /media/hdd/share
	writeable = yes
;	browseable = yes
	valid users = xbox


```

To restart samba run this command:
```
sudo /etc/init.d/smb restart
```

---

### Post by rslrdx on 2008-05-27
tried that... still no go, maybe i do have to bridge the subnets, but i guess vpn is not or at least should not be my first option if its a local network...

---

### Post by NateMan on 2008-05-27
I'm almost sure that it is due to the separate subnets of 192.168.1.xxx and 192.168.2.xxx. What sort of router are you using between them? I imagine that you could setup some sort of port forwarding between them, as I've done on wifi networks in the past to enable wireless users to access fileshares on servers with their own subnet. I know for a fact that my pfsense box can do this using two separate subnets. Not sure about most other hardware.

---

