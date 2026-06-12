---
title: "Access all areas: Wifi and routing"
date: 2013-04-13
forum: Server Platforms
---

### Post by RhinosoRoss on 2013-04-13
I've just had to download and install the latest server and start again after updates ran out of /boot, then 'something' happened and I couldn't access anything :-(
I tried installing desktop and the 12.4.2 LTS server but 12.10 was the only one that would install.
Let me know if I should make posts about what happened, but for this thread I need to get my head around joining two networks with WiFi...

The ADSL Router is now wired to one network which we can ignore here.
The Ubuntu Server's network is physically separate, so it links to the Internet via the ADSL Router through WiFi with settings I'll list in a moment.
The computers on that network have their gateway set to the Ubuntu Server's internal IP.
The Ubuntu Server's network need to access the Internet through the server.

Problem 1) I need to join the Server's eth0 to wlan0 but I don't understand if that is IP routing, IP Tables, a Bridge etc. or how to do it in a way that also allows the following...

Laptops access the Internet directly to the ADSL router's WiFi.
Problem 2) Those laptops need to also be able to access the Ubuntu Server via Wifi (and Samba, already set up)...

Thanks in advance to those who know; here's the setup as it is at the moment:

#lsb_release -a says (amongst other things):```
  Description: Ubuntu 12.10
  Codename: quantal

```



Wifi card = Intel WiFi Link 5300; Model 533AN_MMW
# lshw -C network
says (amongst other things):```
  product: Ultimate N Wifi Link 5300
  capabilities: pm msi pciexpress bust_master cap_list ethernet physical wireless
  configuration: broadcast=yes driver=iwlwifi driverversion=3.5.0-17-generic firmware=8.83.5.1 build 33692 [...] multicast=yes wireless=IEEE 802.11abgn

```

/etc/network/interfaces:```
auto eth0
iface eth0 inet static
address 192.168.2.2
  netmask 255.255.255.0
  broadcast 255.255.2.255
auto wlan0
iface wlan0 inet dhcp

wpa-conf /etc/wpa_supplicant.conf
/etc/wpa_supplicant.conf
network={
ssid="MySSID"
  proto=RSN
  key_mgmt=WPA-PSK
  pairwise=CCMP TKIP
  group=CCMP TKIP
  psk="MyKey"

}
```

---

### Post by darkod on 2013-04-13
If you want the ubuntu server to route traffic for the 192.168.2.x network, first open /etc/sysctl.conf and find the line saying like #net.ipv4.ip_forward=1. Remove the # symbol to activate the option. Save and close the file. Restart the server.

Check if the computers on the 192.168.2.x have internet access. They shouldn't.

Now on the server run:
```
sudo iptables -t nat -A POSTROUTING -o wlan0 -s 192.168.2.0/24 -j MASQUERADE
```

After running that command check if the computers have internet access. Now they should.

If that worked, you need to make that iptables rule run on start together with other iptables rules that you want/need to use. But we can talk about it later, first check if running it manually helps the routing.

---

### Post by RhinosoRoss on 2013-04-13
Many thanks, darkod (and lisati for standardising me), that did exactly as you expected - I certainly wouldn't have worked that out myself.

I attempted to figure out the save alone using [https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo) but it refers to "the interface that I'm using" without saying which it means when you have a WiFi interface too...
So I guessed at eth0 and did the following:
```
#iptables-save > /etc/iptables.rules

``` also adding the following line to the end of the eth0 interface definition in /etc/network/interfaces
```
pre-up iptables-restore < /etc/iptables.rules

```

I restarted the server to make sure it worked and it does (though there may be more I'm  supposed to do for reasons that I don't know)!
The page in the link above didn't explain why I'd want the counters ([FONT=courier new]iptables-save -c[/FONT] option) so I've not used it...

Which leaves me with getting laptops to be able to browse files on the server via WiFi...

---

### Post by darkod on 2013-04-13
Yeah, that is the correct procedure. The iptables-save saved the current rules in a file, and the iptabes-restore reads the file and applies the rules on each boot.

So, if it works as you expect it, that should be it. Note that you need to specify which DNS the clients to use. Unless you have some sort of dns service running on the server (like dnsmasq or bind), then the clients need to use another dns server, like from your ISP or any other public dns.

The routing part seems finished, the dns part is much easier.

---

### Post by RhinosoRoss on 2013-04-13
The DNS is working, thanks - now I just need to get the second problem sorted: the laptops need to access files on the server through the WiFi card (details in first post). Currently the wifi card's mode is managed - I guess it should be Master mode to let the laptops talk to it - but that would mess up the server accessing the ADSL router... so it this what Mesh mode is for? Or is what I'm trying to do simply not possible?

---

### Post by darkod on 2013-04-13
If the laptops are joined to the ADSL router wi-fi network there should be no problem accessing the server from them. But I'm confused, do you have toher machines that use the eth0 of the server as gateway? If the clients that use the server as gateway are wi-fi you should have configured it the other way around, to connect the server to the router using wired cable, and the clients to the server on its wi-fi interface.

But with laptops in the same wi-fi network you should access any machine in the same network, including the server, unless a firewall is stopping you. Do you have a firewall active on the server that might block the laptops accessing it?

---

### Post by RhinosoRoss on 2013-04-13
This is how it's configured at the moment:
```

 +------+
 | ADSL |__WiFiMaster   _             +-------+
 |Router|       \    \_/ \_WiFiSlave__|Roaming|
 +--+---+       /                     |Laptops|
    |           \         +------+    +-------+
+--------+     WifiSlave__|Ubuntu|
|  Wired |                |Server|
| Network|                +------+
|  No.1  |                    |
+--------+                +--------+
                          |  Wired |
                          | Network|
                          |  No.2  |
                          +--------+

```
The laptops can access the Internet through the ADSL router, but they need to access the Ubuntu Server files (and possibly use it as the gateway instead).
Given that the Ubuntu Server isn't a Master (yet) they can't connect to it.
The Ubuntu Server's WiFi card must have to be both a master and slave... is that what mesh mode is?
Perhaps I need two WiFi adapters, but I'm hoping that's unnecessary, the traffic is low.

---

### Post by darkod on 2013-04-13
They won't be able to use it as a gateway, but they should be able to access it.

What is the private IP of the server on the wlan0 interface? I noticed from your config file that wlan0 is set for dhcp which is usually not a good idea for servers. You want static IPs for them.

I don't know which subnet you are using from the ADSL router, but if the IP of the server is for example 192.168.1.100 then the laptops would also have an IP in the range 192.168.1.x (the source is the same, the router), and they should be able to access 192.168.1.100 without any problems.

Try pinging the server IP from any of the laptops.

---

### Post by RhinosoRoss on 2013-04-14
Great: I can ping the server :-)

I've a little problem in that the ADSL router has no reserved pool:
It's a Sky (DLink) DSL-2640S-2.X DSL router (For future readers, username:admin,password:sky) and I can see from the settings that the dhcp pool is maximal (.2 to .254, with it's own address at .1) so I have three choices: add an address reservation without asking Sky, get Sky involved, or use a high number on the server like 192.168.0.200... Since there's never likely to be more than 30 devices I guess that's safe?

I've added wlan0 to samba.conf's interfaces line in the [global] section and restarted samba but the laptops still see no shares...
[Edited to add] if I comment out the line
bind interfaces only = yes
then the laptops see the shares! Phew!
But is this safe? Is there a better way?
I feel it should have worked without removing that...

---

### Post by RhinosoRoss on 2013-04-14
..oh... it seems that static ip on wlan0 doesn't work [http://ubuntuforums.org/showthread.php?t=1487321](http://ubuntuforums.org/showthread.php?t=1487321)
although that threads old - it won't work for me either.

I tried changing /etc/network/interfaces from
```
iface wlan0 inet dhcp

```to 
```
iface wlan0 inet static
  address 192.168.0.2
  netmask 255.255.255.0
  broadcast 192.168.0.255

```it won't connect.
I tried moving the starting IP for dhcp on the ADSL router
and I've tried adding the IP as a reserved IP on the ADSL router
after each change I've tried restarting networking, and also restarting the whole server.
It always works with dhcp, though.

The above link implies that I have to stay with DHCP but reserve an IP on the router for the server's MAC.
I don't like having to hack their box to do this, but it's all that seems to leave me with a reliably static IP...

So at the moment it seems like I still need advice on static IPs for wlan and how to get samba interfaces to work without removing:
[CODE]bind interfaces only = yes[CODE]

---

### Post by darkod on 2013-04-14
If that is the interface the server uses for internet, you need to specify the gateway too. You don't need the broadcast option, it's calculated automatically. But for static IP on the interface that goes to the internet router, you would need:
```
address 192.168.0.2
netmask 255.255.255.0
gateway 192.168.0.1
```

I guess you can always use dhcp with a reservation, but the above should work for setting up a static IP. Juts don't use the .2 in case it gets assigned to some of the laptops. Use for example 192.168.0.100.

---

### Post by RhinosoRoss on 2013-04-17
Yes that works - though it took two more evenings of pain (courtesy of Windows) to figure out that it worked.
Darkod's awesomeness at saving me days was matched by Micrsoft's ssenemosewa...

For others reading this and trying the same thing:
 The Windows laptops don't cope well with the Ubuntu Server network being restarted. Samba appears to need to be restarted too (at least on the versions of everything that I'm using). Even after restarting everything, Windows doesn't find the server. In Windows Exploder, click on Network Neighbourhood, then press F5 to get it to refresh and it won't find it. Type the Server IP in the address bar and it searches for ages, then appears to give up... but in Windows 7, after another minute or so, up pops a dialog box about detecting network errors. It correctly diagnoses something and finds the server in its own time.

This huge delay made me very unsure whether each configuration change I made had worked or not!

Fortunately ping and nslookup give instant responses,
Tip: ping and nslookup the IP 8.8.8.8 - very easy to remember (google'g public DNS server)
but there were times when I could ping and nslookup but the web browsers wouldn't play. Sometimes Chrome would deny there was a connection and Explorer would work. In Chrome Settings, [Advanced][Proxy] takes you to the Internet options page. Make sure that [Connections Tab][LAN Settings] has [Automatically Detect Settings] checked! - don't close that dialog yet...
After using the Explorer browser to check that the Internet was working, one PC became unusably slow. Back to the Internet Options Dialog: [Content Tab][Feeds and Slices] (whatever they are) Uncheck the top and bottom tick boxes and the PC is functioning normally again.

So now I have a network setup that I originally thought wouldn't be possible but with the knowledge of Darkod, turned out to be pretty straightforward. Many thanks.

---

