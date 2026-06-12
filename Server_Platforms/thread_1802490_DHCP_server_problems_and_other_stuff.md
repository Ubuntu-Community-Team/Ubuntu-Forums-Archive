---
title: "DHCP server problems and other stuff"
date: 2011-07-12
forum: Server Platforms
---

### Post by TBhX£2760R8@nK7§r on 2011-07-12
I used ClearOS for a bit as a router, but never really understood the differences between whatever it is, and ubuntu. So three days ago I decided to move to ubuntu server edition and just make it work like a router.

I followed the instructions provided here:
[https://help.ubuntu.com/community/Router](https://help.ubuntu.com/community/Router)

When I run 
```
sudo apt-get install dhcp3-server
```It says that it's already correctly installed.

Problems that I can see right now:
The DHCP server config at 
```
/etc/dhcp3/dhcpd.conf
```doesn't exist.
This thing doesn't exist:
```
/etc/init.d/dhcpd
```/etc/network/interfaces:
```
auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp


auto eth0
iface eth0 inet static
    address 192.168.0.1
    network 192.168.0.0
    netmask 255.255.255.0
    broadcast 192.168.0.255

```I currently have it plugged into a router so I can have internet to look up tutorials while I try to get it to work, but for some reason I can't ping it with the IP address the router assigns eth1. I also can't ping anything from the box. 
```
ifconfig
``` shows that eth1 has the IP address assigned to it by the router.

I set /etc/resolv.conf to 
```
search
```

I provided all the information I could think of that's relevant, if I missed anything that might help, please tell me.

So should I just reinstall and try again, or can this be salvaged?
Thanks for any and all help.

---

### Post by Bachstelze on 2011-07-12
Which version of Ubuntu are you using?

---

### Post by TBhX£2760R8@nK7§r on 2011-07-12
11.04
Sorry, I had meant to mention that.

---

### Post by Bachstelze on 2011-07-12
Then the Ubuntu Server Guide has a page about dhcpd [https://help.ubuntu.com/11.04/serverguide/C/dhcp.html](https://help.ubuntu.com/11.04/serverguide/C/dhcp.html)

---

### Post by TBhX£2760R8@nK7§r on 2011-07-12
The thing is, the config files that says you need to edit don't exist.

---

### Post by ruffEdgz on 2011-07-12
Can you do a search on your server about 'dhcp3' by running the following commands:
```

sudo updatedb

sudo locate dhcp

```
You don't need to reply back with everything it finds but if you see anything that would be helpful, it would be appreciated.

Also, since it says that it has dhcp3-server installed, lets check if it has a config:
```

sudo debconf-show dhcp3-server

```

Cheers!

---

### Post by Bachstelze on 2011-07-12
Okay yes, the files are at /etc/default/isc-dhcp-server and /etc/dhcp/dhcpd.conf. Easy enough to figure out, though...

---

### Post by TBhX£2760R8@nK7§r on 2011-07-13
> **Bachstelze said:**
> Okay yes, the files are at /etc/default/isc-dhcp-server and /etc/dhcp/dhcpd.conf. Easy enough to figure out, though...
I had found those, and configured them so they look like they should work, yet they didn't. So I assumed they just weren't the right configs.

```

sudo updatedb

sudo locate dhcp

```
I'm not really sure what would be helpful, but if needed I can copy out the result on a flash drive.

```

sudo debconf-show dhcp3-server

```
This returns nothing.


Also, if I plug a windows laptop into eth0, the thing that the DHCP server should be running on, it just claims that the cable is unplugged.

A) Should I just reinstall?
B) Internet seems to work if I plug the server directly into the modem, if I did that and gave someone SSH access, how bad a plan would that be?

---

### Post by TheDrew on 2012-01-11
> **Scuzzball said:**
> 
```

sudo debconf-show dhcp3-server

```
This returns nothing.




In Ubuntu 11.04, it has been changed to isc-dhcp-server, so try this instead:


```

sudo debconf-show isc-dhcp-server

```

---

