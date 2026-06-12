---
title: "Help setting up my very first network"
date: 2008-09-08
forum: Server Platforms
---

### Post by mgiaff on 2008-09-08
Hi!

I have to premise that I never worked with networks and with servers.





I tried to "draw" the network configuration:


```

 -------------NET1------------- ----------NET2-----------
|  __________                  |                         |
| |          |__               |                         |
| | client01 |_ \              |                         |
| |__________| \ \             |                         |
|               \ \            |                         |
|  __________    \ \           |                         |
| |          |__  \ \          |                         |
| | client02 |_ \ | |      ____|____                     |
| |__________| \ \| |     |    |    |                    |
|               \   |_____|    |    |____ _ _ _          |
|  __________   /    _____  [COLOR="Red"]SER[/COLOR]|[COLOR="Red"]VER[/COLOR] |____ _ _ _ internet |
| |          |_/ /| |     |    |    |                    |
| | client03 |__/ | |     |____|____|                    |
| |__________|    / /          |                         |
|                / /           |                         |
|  __________   / /            |                         |
| |          |_/ /             |                         |
| | clientxy |__/              |                         |
| |__________|                 |                         |
|                              |                         |
 ------------------------------ -------------------------

```

The only thing that I cannot change is that 'NET2' requires that every client's MAC Address has to be allowed by NET2's administrator (and he will allow SERVER's MAC).



Infos about 'SERVER':
* Runs Ubuntu Server Edition 8.04.1
* Has 2 network cards installed

Infos about clients:
* They are already configured with dual-boot: Ubuntu 8.04 Desktop Edition and Windows XP Professional

I have root privileges on 'SERVER' and on clients.





What I want to do is to set up a local network ('NET1'). Requirements:
* 'SERVER' has to be a DHCP server
* Clients have to support both server authentication and local access [Windows has authenticate to the domain too - I read that this requires a service called SAMBA]
* Some IPs have to be reserved to a list of MAC Addresses, so that fixed clients has fixed IPs [IPs has to change with the change of OS - for example, client01 with Ubuntu has IP 192.168.3.1, but with Windows the IP should change to something like 192.168.3.101]
* Clients of 'NET1' have to access to the internet ('NET2') through 'SERVER' [they aren't clients of 'NET2']
* There should be the possibility to plug other clients to network, allowing access to some predefined shared folders and to the internet

Possible expansions:
* Add a WIRELESS router to access to shared folders and to the internet with laptops and mobiles





I hope that someone can guide me.
Thanks a lot for helping me!

---

### Post by MunkyJunky on 2008-09-08
I'm a little confused - are you wanting help to se tup a network as shown above? 

I think you'd probably have to buy a router or switch to connect net1 into net2 - Otherwise you'll have to have an NIC per computer on your server, which could be annoying to do. My advise would be get a 5 port router. The 4 LAN ports would connect into your clients, and the WAN port would connect into the server. 

You'll need Samba - its a service to provide windows shares on linux, so it's important to have that if you want shares on your server accessible from Windows.

---

### Post by mgiaff on 2008-09-08
I don't think I'll need a router... I read something about IP masquerading that should allow to change the headers of TCP/IP packets...

The problem is that I don't know how to start. Perhaps I have to start from the DHCP... But I don't know how to set it. I mean which files? Which options?

If some parts are unclear I'll try to provide a more detailed description...:)

---

### Post by MunkyJunky on 2008-09-08
Just of the top of my head, I saw something in Add/Remove programs on my desktop that allows you to set up your computer to distriute IP's via DHCP. Just go into add/remove and search 'DHCP' under the System tools tab I think it was. Make sure your searching all avaliable applications, too.

I'm not at home at the moment though, so I can't get on Ubuntu to have a check. When I'm back on mine, I'll have a look. 

That may get you some way to getting your clients connected to the server. Also, a friend of mine administers the local college network, which runs around 3 servers and 100+ desktops. I can have a chat with him and ask him for some pointers if you like.

---

### Post by mgiaff on 2008-09-08
Thank you!
I really need help to know which files to edit and which options to enable...

If anyone else has suggestions, please feel free to post.

I think that this discussion has to be moved to the "Server" forum...

---

### Post by p_quarles on 2008-09-08
Moved to Server Platforms at user's request.

---

### Post by Iowan on 2008-09-08
[This]("https://help.ubuntu.com/community/Internet/ConnectionSharingDHCP3") looks like it might help.  Also, check [howtoforge.com]("http://www.howtoforge.com/taxonomy_menu/1/1/50") for "Perfect server" articles.

---

### Post by mgiaff on 2008-09-09
Wow, thanks a lot, this is a wonderful beginning.
I'll work on the network and then I'll report my results!

---

### Post by schettj on 2008-09-09
This seems like a standard linux router setup with NAT. There are literally millions of pages on how to do this in linux. You're looking for "Linux router howto" in google (w/o quotes.)

You're in for some interesting (but in the end fun) times ahead.

---

### Post by mgiaff on 2008-09-10
Today I obtained the ability to connect to NET2 and it works.

Now I'm home, trying to set a valid DHCP configuration file.




DNS are given automatically from NET2's server... This is what NET2's administrator said to me. I don't know how to set this, so I'll wait for your suggestions :D
```

#ddns-update-style ad-hoc;

```

I think that the following piece of code is ok... Please, check if something is missing.
```

option subnet-mask 255.255.255.0; # Subnet mask
option broadcast-address 192.168.13.255; # Broadcast
option routers 192.168.13.254; # This should be the IP address of SERVER
option domain-name MYNETWORK; # Network domain name
option domain-name-servers 192.168.13.254; # This should also be SERVER's IP address

```

I don't know if these two following parameters are ok... Do you believe that I have to change them??
```

default-lease-time 600;
max-lease-time 7200;

```

I didn't understand very well what's the effect of the following option
```

authoritative;

```

In the following lines everything should be ok...
```

subnet 192.168.13.0 netmask 255.255.255.0 {
	range 192.168.13.200 192.168.13.250; # These are the IP Addresses that I reserve to clients that are plugged occasionaly, like laptops
}

```

The following is an example to assign fixed addresses to certain MAC ADDRESSES.
I don't know how to get if the PC01 is connected with Windows or with Ubuntu.
I named Ubuntu installations with a postfix "-UBU" and Windows installations with the postfix "-WIN"...
So PC01 possible names are: PC01-UBU and PC01-WIN. I wanted, for example, to have a setup like: if PC01-UBU, then IP: 192.168.13.1; else, if PC01-WIN, then IP: 192.168.13.101
The problem is that if I use the same ethernet card for Ubuntu and Windows, both will have the same MAC address, right?
```

host PC01 {
	hardware ethernet 00-50-8D-F9-7C-95;
	fixed-address 192.168.13.1;
}

host PC02 {
	hardware ethernet 00-49-5H-O5-1A-67;
	fixed-address 192.168.13.2;
}

```



After the configuration of the DHCP server, I'll work on the internet connection to have all NET1 PCs connected to the Internet thanks to NET2's connection.

---

### Post by mgiaff on 2008-09-23
Ok, I set up the DHCP server and the bind9 package (DNS).

Now I need to know how to set up the domain part. I need to know which package do I have to install and configure to set up the domain. I heard names such as LDAP and NIS...
Can you help me please???

Thanks a lot

---

### Post by Iowan on 2008-09-23
You passed me, already.  I've yet to set up my "domain".  Besides the howtoforge.come articles, check [this]("http://http://ubuntuforums.org/showthread.php?t=640760") thread, and [https://help.ubuntu.com**[/B]/community/LDAPClientAuthentication"]this]("**[B) help file.  There are several LDAP articles on [https://help.ubuntu.com]("https://help.ubuntu.com")

---

