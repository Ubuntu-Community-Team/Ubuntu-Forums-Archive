---
title: "[SOLVED] not so perfect &amp;quot;perfect server&amp;quot; help setting up home web server"
date: 2008-09-10
forum: Server Platforms
---

### Post by bikerjeg on 2008-09-10
I am trying to run a test web server from home with the configurations explained on howtoforge's walk through for ubuntu 8.04 found here [http://www.howtoforge.com/perfect-server-ubuntu8.04-lts](http://www.howtoforge.com/perfect-server-ubuntu8.04-lts)

Basically I have gone all the way through the basic installation of Ubuntu onto my box but I am having connectivity issues and thus I can't run any of the update functions since my server doesn't connect to the internet. I don't even think my server is connected locally since I cannot ping computers on my network.

My server is connected through a linksys wrt54gs but I am not sure if I am supposed to do any specific configurations to the router to let my server connect. Basically what I have done is given the server a static IP address as explained on step 7 on howtoforge

I have checked my physical connection and everything seems to be fine except I still can't connect the server.

I did try the DHCP configuration during the install of Ubuntu but my server was not able to connect to DHCP server. I am really not sure what to do to get my server to connect so I can finish the tutorial and get my webserver up. Does anybody have advice on configurations or troubleshooting I can try to resolve this issue?

I have already ran "ethtool eth0" and I did get "Link detected: yes" so I don't think my physical connection is a problem

---

### Post by Paul41 on 2008-09-10
Is the computer you are using to try to connect with getting assigned the same ip address as your static ip address? I had this problem when I first set mine up. I took the server's static ip out of the routers numbers for assigning DHCP addresses and that solved my problem.

---

### Post by Iowan on 2008-09-10
Post contents of **/etc/network/interfaces** and results of **ifconfig**

---

### Post by bikerjeg on 2008-09-10
**@Paul41:** I don't think DHCP is messing up the IP's since I only have two computers connected aside from the server and they both have been allocated different IP's from the server. I have tried setting the IP address that I gave the server to not be included in DHCP but since I flashed my router to DD-WRT firmware I am not sure where that setting is or how it works since I think it asks for a mac address and I'm not sure what that is for the server




**contents of /etc/network/interfaces:**

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).
# The loopback network interface
auto lo
iface lo inet loopback
# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.1.108
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1



**ifconfig results:**

eth0
Link encap: ethernet HWaddr (mac address)
inet addr:192.168.1.108 Bcast:192.168.1.255 Mask:255.255.255.0
inet6 addr: fe80::215:f2ff:fe08:37c3/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX byte:0 (0.0 B) TX bytes:0 (0.0 B)
Interrupt:17 Base address:0xdc00

lo
Link encap:Local Lookback
inet addr:127.0.0.1 Mask:255.0.0.0
inet addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:4 errors:0 dropped:0 overruns:0 frame:0
TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX byte:376 (376.0 B) TX bytes:376 (376.0 B)

---

### Post by cariboo on 2008-09-10
Can you ping your router:

```
ping 192.168.1.1
```

Jim

---

### Post by bikerjeg on 2008-09-11
no, pinging the routers ip address only results in failed attempts

---

### Post by windependence on 2008-09-11
Are you plugged in to the correct port on your router/switch?

Can you also post the contents of your /etc/resolv.conf?

-Tim

---

### Post by Krupski on 2008-09-11
> **bikerjeg said:**
> Basically I have gone all the way through the basic installation of Ubuntu onto my box but I am having connectivity issues and thus I can't run any of the update functions since my server doesn't connect to the internet. I don't even think my server is connected locally since I cannot ping computers on my network.

I ran into a problem like this a while back. I built a file server box running Ubuntu Server 64 bit - it worked great. Then, by accident I fried the motherboard in the server box (a screw fell into it while powered up and smoke crackled out of the board!).

Anyway, I pulled out the old motherboard and put in a new one (same kind). Everything booted up and worked great - EXCEPT that I had no network access.

Long story short... my router for some reason associated the MAC address of the old motherboard with the IP address. When I fired up the new motherboard, it obviously had a different MAC address and the router refused to talk to it!

I had to go into my router and manually delete the "MAC to IP address association" for the old MOBO.

Taa-daa! Now it worked!

Maybe you are having a similar problem?

(edit to add): I don't know how you do it with the Linksys WRT54GS - maybe select "Administration" and then "Reset to factory defaults"? I *think* what needs to happen (assuming this is the problem) is that the router's routing tables need to be flushed and re-made... and I don't know how to do it with your router. Sorry.

Good luck!

-- Roger

---

### Post by bikerjeg on 2008-09-11
**@windependence**
Yeah I think I'm plugged in the right port. I am just connected to one of the lines that any of the other computers would usually be connected to. I also tried connecting the server to the port where one of my computers used to be physically connected.

**My /etc/resolv.conf contents are as follows:**

search example.com
nameserver 192.168.1.1


**@Krupski**
I already tried clearing the router tables already and refreshed the dhcp server to clear and redistribute the IP's so I am not sure this could be the same problem you mention

---

### Post by Iowan on 2008-09-11
Firewall (**ufw** on server)?

---

### Post by bikerjeg on 2008-09-12
I ran ufw status and got "Firewall not loaded"

I don't think this would be a problem to begin with if it wasn't even communicating within the my lan, right?

---

### Post by cariboo on 2008-09-12
This is may be a dumb question, but have tried a different network cable?

One other thing to try, if you've got a livecd of some sort try it to see if you have network access

Jim

---

### Post by windependence on 2008-09-12
According to your /etc/network/interfaces, you have this set up with a static IP, so DHCP doesn't matter here.

When you are trying to ping other PCs on the network, are you pinging by IP address or server name?

At any rate, we should add some external DNS servers to your resolv.conf. Try adding them like this:

```
search localhost.localdomain
nameserver 192.168.1.1
nameserver 208.67.220.220
nameserver 208.67.222.222
```

Don't forget to restart the network after you make the changes:

sudo /etc/init.d/networking restart


Also, what is the IP address of your router? According to the way you have the server configured it should be 192.168.1.1. If it isn't, that's where the problem is.

Do check your cable though because Cariboo is right, it could be somethiing that simple.

-Tim

---

### Post by bikerjeg on 2008-09-12
yeah I checked the cable it seems fine I am using a cat5 patch cable I bought at the store. I already tested the cable with another computer and it worked perfectly.

Now as for running a live CD version of Ubuntu I downloaded the Desktop version of 8.04 and tried to give it a go. I am not getting a gui though and once the CD finished loading I am left with a command terminal. I did try to check for an internet connection through the terminal but no luck yet

@windependence I added your suggestions to my resolv.conf but I still haven't gotten a connection. I'm about to give up with this :mad:

---

### Post by volkswagner on 2008-09-12
> **bikerjeg said:**
> **@Paul41:** I don't think DHCP is messing up the IP's since I only have two computers connected aside from the server and they both have been allocated different IP's from the server. I have tried setting the IP address that I gave the server to not be included in DHCP but since I flashed my router to DD-WRT firmware I am not sure where that setting is or how it works since I think it asks for a mac address and I'm not sure what that is for the server




**contents of /etc/network/interfaces:**

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).
# The loopback network interface
auto lo
iface lo inet loopback
# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.1.108
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1



**ifconfig results:**

eth0
Link encap: ethernet HWaddr (mac address)
inet addr:192.168.1.108 Bcast:192.168.1.255 Mask:255.255.255.0
inet6 addr: fe80::215:f2ff:fe08:37c3/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX byte:0 (0.0 B) TX bytes:0 (0.0 B)
Interrupt:17 Base address:0xdc00

lo
Link encap:Local Lookback
inet addr:127.0.0.1 Mask:255.0.0.0
inet addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:4 errors:0 dropped:0 overruns:0 frame:0
TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX byte:376 (376.0 B) TX bytes:376 (376.0 B)

I followed the same setup.  I think you should have

network 192.168.1.1
       not
network 192.168.1.0

in the above mentioned file.

Well I am just comparing my setup.

---

### Post by windependence on 2008-09-12
> **bikerjeg said:**
> yeah I checked the cable it seems fine I am using a cat5 patch cable I bought at the store. I already tested the cable with another computer and it worked perfectly.

Now as for running a live CD version of Ubuntu I downloaded the Desktop version of 8.04 and tried to give it a go. I am not getting a gui though and once the CD finished loading I am left with a command terminal. I did try to check for an internet connection through the terminal but no luck yet

@windependence I added your suggestions to my resolv.conf but I still haven't gotten a connection. I'm about to give up with this :mad:

To bring the GUI up when you get a command prompt like that just type startx.

-Tim

---

### Post by many_miles on 2008-09-13
Your TX and RX byte counts are 0.  That indicates some very low level problem.  I am pretty sure it is not a DNS or network configuration issue.

If your IP/DNS/Gateway, etc, were wrong, you would see a higher count than 0.

I am leaning to a driver configuration issue or a hardware problem.

I think your best bet, like others have mentioned, is to get some Live CD booted and running and see if that resolves it.  If you do, that will at least prove that the hardware in the PC itself is fine.  Further, since Ubuntu is possibly causing the problem, I would be inclined to try booting some other Live CD OS, like Knoppix, or something.

Next, or first, I would try to rule out the connection between the server and the WRT54G.  Yes, I know it works with other existing PCs, but, it could be an issue specifically between this PC and the WRT54G.  It's probably a quick check and will put/keep you on the correct troubleshooting path.

Assuming your broadband device is a DHCP-configured, no authentication required device, you should be able to reconfigure your server for DHCP, shut down the PC, connect the PC directly to the broadband device, reboot the broadband device, then fire up the PC again.

If you are able to surf the web/ping/etc thereafter, you can be sure that the issue is an issue specifically between the WRT54G and the OS.  If not, you can be sure that the issue is a driver or hardware issue with the PC.

Post the results of such a test.

Good luck.

---

### Post by hyper_ch on 2008-09-13
change your interfaces to:

```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).
# The loopback network interface
auto lo
iface lo inet loopback
# The primary network interface
auto eth0
iface eth0 inet dhcp
#iface eth0 inet static
#address 192.168.1.108
#netmask 255.255.255.0
#network 192.168.1.0
#broadcast 192.168.1.255
#gateway 192.168.1.1

```

and then run

```

sudo /etc/init.d/networking restart

```

Then run
```

ifconfig

```
to find out what the gateway is and then try to ping it.

If pinging works. post the output of ifconfig here.

---

### Post by bikerjeg on 2008-09-15
Thanks for all the advice everybody. First off let me say that I have been trying to load a live CD for ubuntu 8.04 desktop version but cannot get the gui to work. I tried startx but all it did was hop to grey screen then load a terminal which prompted ubuntu@ubuntu:$

In that case I fiddled around trying to load the live cd and loaded it in safe graphics mode while that didn't do much I noticed that when I gave the command for the computer to shutdown I was prompted with a menu for fixing an error which I was not sure what it was about but I clicked it anyways. After this the computer started loading files from a source on ubuntu.com which confirmed that the computer was in fact able to get an internet connection. I also looked at my dhcp tables on my router and the computer had been given an ip address. So now that that is settled I guess I will try for another version of ubuntu and see if that's compatible if not I think I will head towards centos or another linux OS. Thanks for all the help in troubleshooting. I will post back results as soon as I get the iso's downloaded and booted on the server.


**@ hyper_ch:** As far as trying to figure out the gateway with the method you mentioned I was not able to reconfigure to DHCP. When I edited my interfaces and reloaded the configuration the server was not able to detect DHCP and I was given a "No working leases in persistent database -sleeping." error. So no luck on that either

---

### Post by bikerjeg on 2009-01-02
Don't mean to bump the thread but I wanted to clear this up for anyone else experiencing similar problems. I went ahead and just purchased a new cheepo ethernet card from Fry's and went ahead and installed it. It worked flawlessly with Ubuntu 8.04 and I was easily able to configure the ethernet interface. Definately worth it if you're racking your brains from problems which a simple hardware upgrade will fix ;)

---

### Post by windependence on 2009-01-03
> **bikerjeg said:**
> Don't mean to bump the thread but I wanted to clear this up for anyone else experiencing similar problems. I went ahead and just purchased a new cheepo ethernet card from Fry's and went ahead and installed it. It worked flawlessly with Ubuntu 8.04 and I was easily able to configure the ethernet interface. Definately worth it if you're racking your brains from problems which a simple hardware upgrade will fix ;)

FWIW, the hardware may have "solved" your problem, but I don't think it "was" your problem. The machine simply detected a new card and set up a new configuration for it that works.

-Tim

---

