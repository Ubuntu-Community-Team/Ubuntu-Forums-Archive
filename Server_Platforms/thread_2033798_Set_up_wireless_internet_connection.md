---
title: "Set up wireless internet connection"
date: 2012-07-26
forum: Server Platforms
---

### Post by hesson on 2012-07-26
Hi, so I have ethernet running on my Ubuntu server, but I can't seem to figure out how to get my wireless network configured properly. First of all, I don't seem to have a wlan0 interface. During the actual installation of the server, it indicated that eth0 was the wireless interface. I tried to configure it during installation but it refused the details I provided. My router security is WPA/WPA2. I don't know if that's why it got rejected during installation. In any case, here are my details:

```
lspci
``` network details:
```

Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection
Ethernet controller: Broadcom Corporation BCM4401-B0 100BASE-TX

```

```
ifconfig
``` gives me eth1, lo. eth1 is my current connection to ethernet.

```
ifconfig -a
``` gives me eth0, eth1, lo.

```
iwconfig
``` gives me lo, eth1, eth0. lo and eth1 have ```
no wireless extensions.
```. etho says:
```

IEEE 802.11bg ESSID:off/any
Mode:Managed Channel:0 Access point: Not-Associated
Bit Rate:0 kb/s Tx-Power=20 dBm Sensitivity=8/0
Retry linit:7 RTS thr:off Fragment thr:off
Power Management:off
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

```

```
/etc/network/interfaces
```:
```

auto lo
iface lo inet loopback

iface eth1 inet static
     address 192.168.0.2
     netmask 255.255.255.0
     gateway 192.168.0.1
     dns-nameservers 209.197.128.2 209.195.95.95

```

```
/etc/resolv.conf
```:
```

nameserver 209.197.128.2
nameserver 209.195.95.95

```

Please let me know if you need more information.
Thank you!!

---

### Post by 2F4U on 2012-07-27
NetworkManager is designed to prefer a wired connection over a wireless connection. So if both are available, it would give the wired connection priority. Did you try to detach the network cable? It maybe needed to even reboot without a cable attached.

---

### Post by BkkBonanza on 2012-07-27
I presume you're not using NetworkManager since you have a manually edited interfaces file and you are running the server version.

Your posted info indicates eth0 is your wireless interface - which is a bit unusual but could be possible. Somehow it got named as though it's a wired interface.

Assuming eth0 is wifi then you need to add a config block to your interfaces file for it. Assuming it's not to be master-mode (act as an AP - which is another whole more difficult story) then you would want to config it for DHCP on your wifi network.

So your interfaces file needs something like this

```

auto eth0
iface eth0 inet dhcp

```

At this point it won't have an IP or associated network. Typically from the command line you'd use wpa_supplicant to get associated with an AP but I'm sure there are other ways too. I've always used mine with WPA2 and so wpa_supplicant was the way I've always done it.

For wpa_supplicant you edit your interfaces file like below,
```
auto eth0
iface eth0 inet dhcp
  pre-up wpa_supplicant -B -Dwext -ieth0 -c/etc/wpa_supplicant.conf
  post-down killall -q wpa_supplicant

```

and then create the /etc/wpa_supplicant.conf file. It's contents depend on what security you use with the AP. An example of mine using WPA2 is ,

```
ap_scan=1
ctrl_interface=/var/run/wpa_supplicant
network={
       ssid="BlueMonk"
       scan_ssid=1
       proto=WPA RSN
       key_mgmt=WPA-PSK
       pairwise=CCMP TKIP
       group=CCMP TKIP
       psk=<long hex string for shared key here>
}

```

An AP with no or other security settings would be different but you can see examples using **man wpa_supplicant.conf**. You need to insert your AP SSID and passphrase hex key in my example. I think **man wpa_supplicant** tells how to get that hex string IIRC. Also, you may need to **sudo apt-get install wpa_supplicant** if this was not installed already for you.

Then you need **sudo ifup eth0** to bring the interface up. If that has issues, and doesn't complete, then you can run the wpa_supplicant command manually in debug mode with,

wpa_supplicant -d -Dwext -ieth0 -c/etc/wpa_supplicant.conf

That will give some clues as to why it can't associate, authenticate or obtain an IP address.

If the ifup command completes (it can be slow) then you should use **ifconfig** to see if eth0 is up and has an IP, and **iwconfig** to see if eth0 is associated and what signal strength and data rate you have.

If you plan to use the wifi interface as a gateway to the net then you will need to do a few further config changes involving iptables and ip_forwarding. Post here if you have trouble or need further details.

---

### Post by hesson on 2012-07-27
Hi BkkBonanza,

I followed your instructions and I have not established a wireless connection successfully yet, but it definitely did exactly what it was supposed to do as **ifconfig** indicates that **eth0** has been assigned an ip of **192.168.0.195**, and **iwconfig** shows that **eth0** has a Bit Rate of **54 Mb/s**. Also, the wifi led on my laptop is on whereas it had been flashing before so all signs are pointing to an established connection with my router. Of course, the internet works with the ethernet cable connected (largely thanks to your help of course :)) but when I disconnect the cable and try to **ping google.com**, nothing happens, the cursor just sits there flashing. When I **ping 192.168.0.1**, my router, it says:
```
From 192.168.0.2 icmp_seq=1 Destination Host Unreachable
``` which is interesting because **192.168.0.2** is the static ip configured with my ethernet connection. Recall that **eth0** was assigned **192.168.0.195**. So, I'm guessing while the wireless connection is up and running, it still thinks I'm using ethernet and fails to connect because my cable is disconnected. As for the passkey, I ran 
```
wpa_passphrase <myssid> <mypassphrase>
``` and got a 64 hex string and plugged that in where you told me, but when I ran **wpa_supplicant** in debug mode as you suggested it showed error that it was expecting 8-63 characters instead of the 64 provided, so I just changed the psk back to the original passphrase string. I should mention that I had manually set this passphrase on the router's page before, so i don't know if that makes a difference in terms of how I should input that value.

> If you plan to use the wifi interface as a gateway to the net then you will need to do a few further config changes involving iptables and ip_forwarding. Post here if you have trouble or need further details.

Do you mean to ask if I want to configure the server as a router? No, I would just like to configure **eth0**, my wireless connection, as my main internet connection, and not my ethernet connection. Would that require additional work?

Thanks so much for your help.

---

### Post by BkkBonanza on 2012-07-27
This sounds correct. If you pull the plug on the wired connection you won't automatically start getting stuff via wifi. The routing table has to be changed/updated. If ifconfig says you have an IP then you did manage to assoc/auth/get_ip from your AP. 

(However, if the signal is weak you will find it continually will break off and re-assoc/re-auth again and again - which simply means you need to be closer or have better wifi antenna etc. The IP sticks even when no traffic can flow.)

There is only one default gateway and that is the way it finds unknown/non-local addresses.

So try **route -n**. Check what interface the default gateway goes thru. Alter that to change how you connect to the net.

eg. my router/gateway box has,
```
route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.4.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
192.168.3.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
192.168.2.0     0.0.0.0         255.255.255.0   U     0      0        0 wlan1
0.0.0.0         192.168.2.1     0.0.0.0         UG    100    0        0 wlan1

```

Dest 0.0.0.0 is the default gateway, it has the G flag. Each line states which interface packets will be sent to for that network range. 0.0.0.0 means "default", when it is not in one of the other ranges.

How to alter? Try something like this but with your values,

[B]sudo route del default gw 192.168.2.1
sudo route add default gw 192.168.3.1[/B]

This changes the gw to go thru a different interface/network. To make this stick after reboot I'm not too sure. Perhaps the eth0 position in the interfaces file affects which will get the default route. Or a "post-up" command could be added to force the route. 

Regarding whether you need to do iptables and ip_forwarding - that would be if this computer is going to act as a gateway for others, ie. a router. If it only handles traffic for itself then what you have is enough. If you hooked the eth1 to a local LAN with other systems and all of them wanted to get internet via the wifi on this computer then you would need iptables to do NAT and ip_forwarding enabled to allow packets to pass via the computer.

edited to add:
Note also, if your interfaces overlap in network address space you could have some weird problems. Typically you would use different network ranges for each interface. The DHCP one is likely to behave well but if your static interface has 255.255.255.0 for it's netmask then that means all addresses 192.168.0.* are on that interface. So if the other interface is also using one in that range then the routing tables can't uniquely define which way to route for that IP. More correctly youe eth1 (static) should be given a range like 192.168.1.* (eg. addr 192.168.1.1 netmask 255.255.255.0) so that the two interfaces don't overlap. Another less simple way is to reduce the range the netmask defines.

---

### Post by hesson on 2012-07-28
I ran
```
sudo route add default gw 192.168.0.1 eth0
```
and it executed successfuly. Then I ran **route -n**, and you can see that it successfully configured the gateway:
```

Destination  Gateway      Genmask  Flags  Metric  Ref  Use  Iface
0.0.0.0      192.168.0.1  0.0.0.0  UG     0       0    0    eth0
0.0.0.0      192.168.0.1  0.0.0.0  UG     100     0    0    eth1
192.168.0.0  0.0.0.0      0.0.0.0  U      0       0    0    eth1
192.168.0.0  0.0.0.0      0.0.0.0  U      0       0    0    eth0

```
Still, the ping results are the same as they were before.
I'm actually running this server as a web server. I've set up port forwarding to free ports 80 for http and 22 for ssh so that anyone else outside my LAN can access it via the following WAN IP, [http://216.58.60.131/](http://216.58.60.131/) . The webpage is only displayed with ethernet cable connected. Perhaps you could visit the site and confirm that it is visible to the outside world?

Thanks

---

### Post by hesson on 2012-07-28
Hold on, I'm trying your edited suggestions.

---

### Post by BkkBonanza on 2012-07-28
> **hesson said:**
> I ran
```
sudo route add default gw 192.168.0.1 eth0
```
and it executed successfuly. Then I ran **route -n**, and you can see that it successfully configured the gateway:
```

Destination  Gateway      Genmask  Flags  Metric  Ref  Use  Iface
0.0.0.0      192.168.0.1  0.0.0.0  UG     0       0    0    eth0
0.0.0.0      192.168.0.1  0.0.0.0  UG     100     0    0    eth1
192.168.0.0  0.0.0.0      0.0.0.0  U      0       0    0    eth1
192.168.0.0  0.0.0.0      0.0.0.0  U      0       0    0    eth0

```
Still, the ping results are the same as they were before.
I'm actually running this server as a web server. I've set up port forwarding to free ports 80 for http and 22 for ssh so that anyone else outside my LAN can access it via the following WAN IP, [http://216.58.60.131/](http://216.58.60.131/) . The webpage is only displayed with ethernet cable connected. Perhaps you could visit the site and confirm that it is visible to the outside world?

Thanks

Your routing table indicates that the ping you tried will go to eth1. Recall the default route is only for addresses that it doesn't know. But the route table knows 192.168.0.1 and the first definition of it is to go to eth1.

Also, the route table indicates netmasks of 0.0.0.0 for your networks when they should be 255.255.255.0 or even more restricted in your case if you want the same network on both interfaces. 0.0.0.0 indicates no restrichtion, or, "any", which means any address right now goes to eth1. You should perhaps read up on [netmasks]("http://en.wikipedia.org/wiki/Netmask") at wikipedia to know which mask is needed. 

How to correctly resolve that depends on what you actually want to do here. How do you want to use the wifi vs. wired connections? If you just are testing the wifi then I'd perhaps just manually alter your routing table. Remove the eth1 network range and leave the eth0 one. But if you have a more long term plan here then there are better ways to set the netmasks and have both interfaces useful.

BTW I tried the IP you gave and at that moment there was no response, so maybe it was down then.

---

### Post by hesson on 2012-07-28
Hi BkkBonanza,

You are my hero. :D
After several failed attempts yesterday, I just shut down the server and went to sleep. But when I woke up today, I added the default gateay for eth0 again, and this time it worked, both with and without the cable. As for the Genmask in route table, I simply copied that wrong when I posted it to the forum. The latter two rows do in fact have a netmask of 255.255.255.0. Changing the address of eth1 to 192.168.1.1 worked like a charm, it simply never updated while I was trying yesterday (even after running **sudo /etc/init.d/networking restart** which is odd) but it updated when I booted it today, and so it is working now. I had initially set up port-forwarding for ports 80 and 22 on my router for static ip 192.168.0.2, but now that my new ethernet ip is 192.168.1.1, i tried updating that on my router's page, but I was denied with an error message: *IP address for 'ubuntusrvr' should be within LAN subnet (192.168.0.0)*. 'ubuntusrvr' is my hostname. In any case, I think I need to configure my eth0 IP as static so I can set up port-forwarding for my eth0 IP. When I booted up my server today, **ifconfig** shows assigned IP's of 192.168.0.194 and 192.168.1.1 for eth0 and eth1 respectively. I set up port forwarding of 80 and 22 on my new eth0 IP, 192.168.0.194, and my webserver [http://216.58.60.131/](http://216.58.60.131/) works in the web browser with the server running on wi-fi only, however I know this isn't a permanent solution, as the dynamic IP could change frequently. As for **sudo route add default gw 192.168.0.1 eth0**, I'm guessing I wouldn't need to run that command every time I reboot if I were to configure a static IP like I did with eth1, right?
Also, it makes sense that the webserver was unresponsive yesterday when you tried it as I had the ethernet cable unplugged most of the time while I was testing wi-fi, and eventually turned off the server. It'll likely be running if you try again.
Once again, thanks for helping me setting up my network.

**Edit**: I just researched the error I got on my router's page saying that it only accepted port forwarding IP's with a LAN subnet of 192.168.0.0, and it seems that it is simply a limitation of my router and that I would need to upgrade to a better router that can handle multiple LAN subnets to solve this problem. I also configured eth0 as a static IP through etc/network/interfaces so eth0 looks like this now:
```

auto eth0
iface eth0 inet static
  pre-up wpa_supplicant -B -Dwext -ieth0 -c/etc/wpa_supplicant.conf
  post-down killall -q wpa_supplicant
  address 192.168.0.2
  netmask 255.255.255.0
  gateway 192.168.0.1
  dns-nameservers 209.197.128.2 209.195.95.95

```
Then, I restarted the network, it clearly said *Could not bring up eth1*, which is not surprising considering my router cannot handle the LAN subnet associated with eth1's IP, but eth0's static IP was successfully configured. I finally changed the port forwarding IP for eth0 from the original 192.168.0.194 that I had to the new static 192.168.0.2, and as expected the webserver was visible through the browser again. So now my wi-fi is up and running perfectly, and I know what to do if I ever needed to run it on ethernet instead of wi-fi. I think I might try experimenting now to see if I configure both eth0 and eth1 with an address of 192.168.0.2 in my interfaces file, what will happen. I'm guessing that if only one of eth0 or eth1 can be exchanging information with the router at any given time, then maybe my router will tolerate my server if it has the same IP from both ethernet and wi-fi. I'll post back if I get positive results.

---

### Post by hesson on 2012-07-28
OK, so my experimenting results were not successful. When I tried to configure eth0 and eth1 with the same IP (192.168.0.2), followed by a network restart, eth0 failed. Same thing happened if I configured them with different IP's that had the same LAN subnet. So for now, I'll settle with just running wi-fi. I decided to comment the code for eth1 in my interfaces file, so my server doesn't take forever to boot since it tries to configure eth1 every time but it doesn't work cause it has a LAN subnet that the router can't handle. Now the boot-up runs smoothly as well. :)

---

### Post by BkkBonanza on 2012-07-28
You could also see if your router supports "static leases" for DHCP. Most do have that, at least I know the better ones do. With a static lease you add the MAC address for your server and it will always keep the same IP even when using DHCP. 

This would allow using either interface with DHCP simply by bringing it up/down. You can leave eth0 as "auto", and configure eth1 as "manual". Then if eth0 goes down you simply bring up eth1 manually, config'd with DHCP, so no editing or mucking about.

Also, there are more sophisticated ways of setting up both interfaces as round-robin, aggregated or failover. I looked into it once but right now I can't recall the tools needed for that. It wasn't too hard but a bit obscure docs wise.

Anyway, sounds like you're getting it figured out. And your IP loaded fine from here with FF just now.

---

