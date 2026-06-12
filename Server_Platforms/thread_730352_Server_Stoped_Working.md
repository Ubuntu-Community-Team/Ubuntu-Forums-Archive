---
title: "Server Stoped Working"
date: 2008-03-20
forum: Server Platforms
---

### Post by dethredic on 2008-03-20
My server was working fine, and then my power went out this afternoon.

Now my server does not seem to work. I noticed my local IP changed, even though it is set to static.
apache is running
Internet works on the machine

website is [http://www.hatchseadgroup.com/]("http://www.hatchseadgroup.com/")

---

### Post by tubezninja on 2008-03-21
I would suggest checking /etc/network/interfaces to see what the configuration looks like there.  If you have a static IP address and it's properly configured there, then your IP should not have changed.

If, however, you see a line like

```
iface eth0 inet dhcp
```

Then your server is NOT set up for a static IP, and is asking a dhcp server on your subnet for an IP address.

[This link]("http://www.cyberciti.biz/tips/howto-ubuntu-linux-convert-dhcp-network-configuration-to-static-ip-configuration.html") gives a quick 'n dirty overview of what you should be seeing in /etc/network/interfaces.

---

### Post by dethredic on 2008-03-21
It is static, and always has been. My IP had never changed until now. It was always 192.168.1.137, but it changed to 192.168.1.101. I changed it back to .137 in the file.

> 
#Ts file describes the network interfaces available on your system
# # and how to activate them. For more information, see interfaces(5).
#
# # The loopback network interface
auto lo
iface lo inet loopback
#
# # The primary network interface
# auto eth0
# iface eth0 inet static
#         address 192.168.1.137
#         netmask 255.255.255.0
#         network 192.168.1.0
#         broadcast 192.168.0.255
#         gateway 192.168.1.1


Wow, I just noticed something

> 
root@server1:/home/phil# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0D:56:F6:8B:7D  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:56ff:fef6:8b7d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:25453 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17025 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:36997624 (35.2 MB)  TX bytes:1417571 (1.3 MB)
          Base address:0xecc0 Memory:fe3e0000-fe400000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

root@server1:/home/phil# 


My local IP is still wrong

---

### Post by rickyjones on 2008-03-21
After you change it in the file you'll need to restart your networking subsystem in order for the change to take effect.

sudo /etc/init.d/networking restart

-Richard

---

### Post by dethredic on 2008-03-21
I tried that, but it doesn't change it

> 
root@server1:/home/phil# /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                   [ OK ] 
root@server1:/home/phil# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0D:56:F6:8B:7D  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:56ff:fef6:8b7d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:32964 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22165 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:47448216 (45.2 MB)  TX bytes:1874325 (1.7 MB)
          Base address:0xecc0 Memory:fe3e0000-fe400000 


---

### Post by rickyjones on 2008-03-21
```

#Ts file describes the network interfaces available on your system
# # and how to activate them. For more information, see interfaces(5).
#
# # The loopback network interface
auto lo
iface lo inet loopback
#
# # The primary network interface
# auto eth0
# iface eth0 inet static
# address 192.168.1.137
# netmask 255.255.255.0
# network 192.168.1.0
# broadcast 192.168.0.255
# gateway 192.168.1.1

```

Is that your entire /etc/network/interfaces file?

If so then the problem is that you have all your eth0 static information commented out! Uncomment everything so it looks like this:
```

#Ts file describes the network interfaces available on your system
# # and how to activate them. For more information, see interfaces(5).
#
# # The loopback network interface
auto lo
iface lo inet loopback
#
# # The primary network interface
auto eth0
iface eth0 inet static
address 192.168.1.137
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.0.255
gateway 192.168.1.1

```

Then try restarting your networking subsystem.

-Richard

---

### Post by dethredic on 2008-03-21
wow, thanks man. How did I not nitice that. Do you have any idea how that happened?

EDIT: My site loads on my Server comp, but not my main desktop. Can you check it to confirm it works?

---

### Post by rickyjones on 2008-03-21
> **dethredic said:**
> wow, thanks man. How did I not nitice that. Do you have any idea how that happened?

Are you using any other programs, like network manager, to manage your network connections? That could be the cause.

Beyond that I'm not sure.

You're welcome! Have a good day!

-Richard

---

### Post by dethredic on 2008-03-21
Ok, i just needed to restart Bind9, now it works well.

---

