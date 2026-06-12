---
title: "connecting the Ubuntu server to the internet"
date: 2012-10-30
forum: Server Platforms
---

### Post by archieburden9 on 2012-10-30
hey, i have a server but i have no idea how to connect to the internet on it, can anyone tell me please? i know my WEP key etc, i just dont know how to connect to it on the server


im on 12.10

---

### Post by papibe on 2012-10-30
Hi archieburden9.

The easiest way is to use a cable to connected to the router. Then restart your server.

If you 'have to' connect it through wireless, the solution depends if you are using the proper server edition or the desktop edition.

Regards.

---

### Post by archieburden9 on 2012-10-30
i downloaded the ubuntu server off the website, is the desktop on the GUI one? because mine is a proper server with DOS

---

### Post by papibe on 2012-10-30
Could you post the result of these commands?
```
ifconfig -a

cat /etc/network/interfaces
```
Regards.

---

### Post by archieburden9 on 2012-10-30
let me get my camera, i cant connect with putty and i cant write all that out. 

by the way it provides information about my network cards, ip addresses and gateways etc.

---

### Post by archieburden9 on 2012-10-30
[img]http://gyazo.com/d770cab0a52264af7c48d593f71e82b4.png?1351630100[/img]

this good enough? i can go get my camera

---

### Post by archieburden9 on 2012-10-30
more
[img]http://gyazo.com/2b08a314be8ed97b915e9ba56167c1c1.png?1351630272[/img]

---

### Post by papibe on 2012-10-30
That'll do (missing part of the 2nd command though).

I believe you have some sort of connection using p4p1 (working as a Ethernet device).

Could you explain a little bit how is your LAN? 
Do you have a router?
Are you using a cable?

Could you post the result of these commands?
```
route -n

nslookup ubuntu.com

dig google.com
```

Regards.

---

### Post by archieburden9 on 2012-10-30
my internet speed is pretty good and im using a router, no cable though. do you want me to post the rest of the last command?

[img]http://gyazo.com/01f0af8fc91ddb3be57d84f1a50301ff.png?1351631182[/img]

as you can see it also coems up with "err" when i try to update

---

### Post by AlexDudko on 2012-10-30
You can configure your wireless network interface in terminal executing this command:
> iwconfig wlan0 essid NAME_OF_YOUR_ACCESS_POINT
If there is a password protection, then:
> iwconfig wlan0 essid NAME_OF_YOUR_ACCESS_POINT key PASSWORD
You can scan for available networks with:
> iwlist wlan0 s
When the connection is configured just execute 
> dhclient
to try to connect

---

### Post by papibe on 2012-10-30
It would be much easier if you try using an ethernet cable and set your /etc/network/interfaces to look like this:
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto p4p1
iface p4p1 inet dhcp

```
And then restart your network:
```
sudo service networking restart
```
If that is not possible for you, change your /etc/network/interfaces so it looks like this:
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# wireless interface
auto wlan0
```
Then restart your network:
```
sudo service networking restart
```

For the next part: What kind of wireless security do you have? WEP or WPA?

Regards.

---

### Post by archieburden9 on 2012-10-30
sorry for the long reply but i have turned off the wireless and i cant get it back on.

i clicked the button to turn off all networking and everything, just to make sure it wasnt off in the 1st place but it came up with the red light, and after i pinged google.com it said failed, so i tried clicking the button back on and its not going blue again. how do i turn it back on

---

