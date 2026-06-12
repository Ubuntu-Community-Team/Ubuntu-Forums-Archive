---
title: "Need help with network config please"
date: 2008-05-19
forum: Server Platforms
---

### Post by chua0177 on 2008-05-19
Hi I am a 1st time ubuntu user. Currently I have installed Ubuntu Server 7.04. Installation seemed to go smoothly (ie, DHCP network autoconfiguration was successful). I am using a clean, minimal installation, meaning no DNS or LAMP Server options.

However, the server can't seem to connect to the network at all!

When I open /etc/network/interfaces, this is what i get:

     # The loopback network interface
     auto lo
     iface lo inet loopback

     # The primary network interface
     auto eth0
     iface eth0 inet dhcp 

When I use route, I get:

     Kernel IP routing table
     Destination Gateway Genmask Flags Metric Ref Use Iface

When I use ifconfig, I get:

eth0      Link encap:Ethernet  HWaddr 00:1D:7D:71:D2:OE
          inet6 addr: fe80::21d:7dff:fe71:d20e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:4294967291 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


However, when I use ifup eth0, I get:

     ifup: interface eth0 already configured 

I am at a loss of what to do now, and havebeen working on this problem for weeks. I am currently using dual booting, and on Windows my internet works fine, so it cant be a problem with my internet.

Any help would really be appreciated. Thank you for your time.

---

### Post by solcott on 2008-05-19
eth0 is trying to get an IP address from a DHCP server but the DHCP server (if there is one for the server to try connecting to) is not giving an IP address to it.

If you know what IP address the server is going to use you could try doing this:
```

sudo ifconfig eth0 1.2.3.4
sudo /etc/init.d/networking restart

```

---

### Post by windependence on 2008-05-19
This doesn't have anything to do with your problem I don't think but you should probably turn off IPV6 support as you don't need it and it's a security risk.

-Tim

---

### Post by cdtech on 2008-05-19
Are you running a single NIC on your server? What do you get with:
route -n

sudo route add default gw 192.168.1.1 - Example of how to set the default gateway to 192.168.1.1

sudo pico /etc/resolv.conf this is where you want to put DNS servers associated with network connections (from your provider)

With your interfaces set as "iface eth0 inet dhcp" and the above settings, you should get connected.

Hope this helps.....

P.S.
Why are you running a Server for a dual boot system but not using it as a server? :confused:

---

### Post by koenn on 2008-05-19
> **cdtech said:**
> Are you running a single NIC on your server? What do you get with:
route -n

sudo route add default gw 192.168.1.1 - Example of how to set the default gateway to 192.168.1.1

sudo pico /etc/resolv.conf this is where you want to put DNS servers associated with network connections (from your provider)

With your interfaces set as "iface eth0 inet dhcp" and the above settings, you should get connected.

Hope this helps.....

the op's interfaces already has that "iface eth0 inet dhcp" but is not getting an IP address. SO adding a route and name servers isn't going to help.

> **windependence said:**
> This doesn't have anything to do with your problem I don't think but you should probably turn off IPV6 support as you don't need it and it's a security risk.

How is IPv6 a security risk ? 

> **solcott said:**
> eth0 is trying to get an IP address from a DHCP server but the DHCP server (if there is one for the server to try connecting to) is not giving an IP address to it.

If you know what IP address the server is going to use you could try doing this:
```

sudo ifconfig eth0 1.2.3.4
sudo /etc/init.d/networking restart

```
This should work (with a good ip address to replace 1.2.3.4)


Assuming you have a working DHCP on your LAN (as you say it worked during installation of the OS), just run
```
sudo dhclient
```
you will either see your computer get an ip address, or get feedback about dhcp not working.
Post back with the output so we can decide on the next step.

---

### Post by windependence on 2008-05-20
> **koenn said:**
> 

How is IPv6 a security risk ? 

IPV6 is hardly in use in North America. Most network equipment and software doesn't even support it, e.g. firewalls so this makes your network vulnerable to attacks you won't even know about. there are already quite a few countries where these attacks are coming from, including china and Romania to name a few. If you have IPV6 enabled, you have little or no protection from these and for what? You don't need this service turned on, it's of absolutely no value here. Why risk it?

-Tim

---

### Post by chua0177 on 2008-05-20
Thanks for all the replies!

After using the following:

   sudo ifconfig eth0 192.168.1.11
   sudo /etc/init.d/networking restart
   sudo dhclient

This is the response I get:

   Listening on LPF/eth0/00:1d:7d:71:d2:0e
   Sending   on LPF/eth0/00:1d:7d:71:d2:0e
   Sending on Socket/fallback
   DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
   DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
   DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
   No DHCPOFFERS received.
   No working leases in persistent database - sleeping.
 
When I type route -n, I get:

   Kernel IP routing table
   Destination   Gateway   Genmask   Flags Metric Ref   Use Iface


Btw, I do not know how to disable the IPv6. Also, I only need to connect to the ISP to download a file for a program to run on the Ubuntu Server; I am not setting up an actual server. In a worst case scenario, would it be possible to download a file from the internet into a thumb-drive, and load the file into the Ubuntu Server from the thumb-drive? However, I do no know of any commands which will allow me to access/retrieve files from the USB ports... And even if I did, I would also need commands to untar this file.

---

### Post by koenn on 2008-05-20
you're not getting any dhcp offers - you'll have to figure out why not (what did you change on your network lately ...?)

you could forget dhcp for a while and make a static configuration. 
first, make /etc/network/interfaces look something like this :
```

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.1.11
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1
 

```
make sure the values (address, mask, gateway, ...) make sense on your network.

Then restart the network, and check the output of ifconfig
```
/etc/networking/restart
ifconfig eth0
```

---

### Post by Iowan on 2008-05-20
Per **koenn**'s suggestion, I'd try a static address (makes sense for a server anyway) if for no other reason than to try pinging other machines - the DHCP server in particular.

Except networking may restart via **sudo /etc/init.d/networking restart**
(Like **solcott** mentioned)

---

### Post by eniacpx on 2008-05-20
Are you plugged directly into your modem right now? 

If so, you will most likely have to power cycle before you will get a DHCP response. Sorry if this is basic but...

- Unplug your Ubuntu box from the modem
- Unplug the power from your modem, wait 10 seconds
- Plug the power back in
- Wait for modem to get sync (2-4 minutes)
- Plug ethernet cable back into your Ubuntu box 

Now you should get a DHCP response. If not, just reboot and see how it goes.

This hasn't been mentioned and we forget the basics all too often. :)

---

### Post by atryus28 on 2008-06-10
I don't see any resolution on this and I am having an issue with Ubuntu server not picking up a DHCP address.  I am on the company network and all other machines (windows and nix) get addresses just fine.  It is only ubuntu server (ubuntu desktop works fine) that will not get an IP addy with a physical machine or with VMware.

What is the server doing wrong to try and get an IP?  It does not work during installation nor does it work after adding the eth0 info and restarting the machine or using sudo /etc/init.d/networking restart.

Any advice here would be much appreciated as I am not able to use a static IP right now.  Though if I manually setup the NIC with a static IP etc, it works fine. 

Thanks in advance

I also do not see anyone answer how to turn off IPV6

---

