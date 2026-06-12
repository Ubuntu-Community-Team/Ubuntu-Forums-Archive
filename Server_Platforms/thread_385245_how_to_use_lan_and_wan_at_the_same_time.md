---
title: "how to use lan and wan at the same time"
date: 2007-03-15
forum: Server Platforms
---

### Post by mihaisofti on 2007-03-15
I have a Ubuntu box set up as a PDC.  I connect to it from an XP pro box though 2 Ipcop boxes, that are set up to connect using VPN.  All of this works just fine.  The Ubuntu box has 2 nics.  One for the lan (192.168.2.5) and the other for Internet (192.168.100.50.  Both of them work fine, but not at the same time.  If I enable them both, I cannot connect to the Internet and have a properly functioning network at the same time.
I have a feeling that this is some sort of security feature within Ubuntu, and that the solution is something  to do with port forwarding, although I'm not sure.

Can someone please help me with this?  I would like to be able to connect to the lan, and have Internet access at the same time, and available to all machines on the lan.

thanks for any help.

mihai

---

### Post by Mr. C. on 2007-03-15
Check output of

```
netstat -rn
```

when both NICs are configured.  You probably have two default routes.  Eliminate the one that does not go to the internet.

MrC

---

### Post by mihaisofti on 2007-03-17
When you say "default routes" do you mean "gateway"?

Mihai

---

### Post by mihaisofti on 2007-03-17
I assume that you meant gateway, and acting on your suggestions above, I have removed the gateway for the lan, and of course, the network has stopped working.  Perhaps my original post was not clear.

On the server, I need to have the internet nic working and the lan nic working so that I can access the internet and share this internet connection to the clients on the network.  In other words, when clients log on to the network, they will be able to access the internet through the server.

I would be most grateful for any help anyone can give me on this one.  I feel it may be something to do with port forwarding.

Mihai

---

### Post by Mr. C. on 2007-03-17
No, I meant default routes, as in the routing table.

See this post:

[http://ubuntuforums.org/showthread.php?t=381399&highlight=mrc+netstat](http://ubuntuforums.org/showthread.php?t=381399&highlight=mrc+netstat)

and look at the netstat -rn output, noticing the two 0.0.0.0 entries under Destination.  Review the comments in that article, and note the second route table shown.

If you are trying to make your system act as a router for other systems connected, see this post:
[http://ubuntuforums.org/showthread.php?t=383990&highlight=ip_forward+router](http://ubuntuforums.org/showthread.php?t=383990&highlight=ip_forward+router)

MrC

---

### Post by mihaisofti on 2007-03-27
Thanks for all the links you sent me, but I am still unclear what I need to do.  Here's the netstat -nr output:
Kernel IP routeing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.20.0    0.0.0.0         255.255.255.0   U         0 0          0 eth1
192.168.2.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
0.0.0.0         192.168.2.1     0.0.0.0         UG        0 0          0 eth0
0.0.0.0         192.168.20.254  0.0.0.0         UG        0 0          0 eth1

This seems right to me, but I am still unable to access the internet from either the client or the server without disabling the interfaces for the lan.

I am at a complete loss, but thanks for all the leads you have given me.

Mihai

---

### Post by didijeeeke on 2007-03-27
add your default gateway manualy



sudo route add default gw YOUR_IPCOP_BOX_IP

---

### Post by didijeeeke on 2007-03-27
add your default gateway manualy



sudo route add default gw YOUR_IPCOP_BOX_IP

EDit why you have 2 difrend default gateways remove one you should use one gateway to redirect the 0.0.0.0 not 2

oeps double post :oops:

---

### Post by Mr. C. on 2007-03-27
With Network Manager (System->Administration->Network), you *cannot* have more than 1 interface enabled at a time.  Uncheck the one you do not want enabled.

I did not provide you with the links for my health.  I provided them because they contain the instructions as to what you need to do to eliminate the problem.  You actually have to read them, and follow the instructions.

Your route table still has two default routes.

```
0.0.0.0 192.168.2.1 0.0.0.0 UG 0 0 0 eth0
0.0.0.0 192.168.20.254 0.0.0.0 UG 0 0 0 eth1
```

Eliminate one of them; the one that does not provide a path to your active broadband connection.  The previous poster is incorrectly suggesting that you need to add the default route - you already have two, and that is one too many.  You can manually delete the route with the route command, or follow the instructions I've provided on the links (post #5).

MrC

---

### Post by mihaisofti on 2007-03-29
I've read the posts, removed the gateway entry to the Internet, and rather predictably, I have no Internet connection.  This is not the desired outcome.  I am not sure that you understood my original post.  You say:
"With Network Manager (System->Administration->Network), you *cannot* have more than 1 interface enabled at a time. Uncheck the one you do not want enabled."
If this is the case, how is my Internet connection AND Lan ever going to work together?

---

### Post by GoBieN on 2007-03-29
> **mihaisofti said:**
> I've read the posts, removed the gateway entry to the Internet, and rather predictably, I have no Internet connection.  This is not the desired outcome.  I am not sure that you understood my original post.  You say:
"With Network Manager (System->Administration->Network), you *cannot* have more than 1 interface enabled at a time. Uncheck the one you do not want enabled."
If this is the case, how is my Internet connection AND Lan ever going to work together?

If eht0 is your LAN and eth1 is your WAN, you should change it to this:

192.168.2.0 192.168.2.1 0.0.0.0 UG 0 0 0 eth0
0.0.0.0 192.168.20.254 0.0.0.0 UG 0 0 0 eth1

If you want your clients to get internet access trough your server's broaband connection, you need to set up your machine as a router. If this is the case perhpas take a look (i mean READ) the link Mr.C gave you: 
[http://ubuntuforums.org/showthread.php?t=383990&highlight=ip_forward+router](http://ubuntuforums.org/showthread.php?t=383990&highlight=ip_forward+router)

---

### Post by Mr. C. on 2007-03-29
I understood your post perfectly.

You do not understand that there can be only ONE default route.  I advise you to eliminate one of them, the one that does NOT go to your broadband.

Your configuration was not explicitly clear.  I asked if you were trying to make the system a router (for which you did not reply).

You need 1 default route, 1 gateway route per NIC, 1 routing entry to route between LAN1 and LAN2, and 1 setting to enable forwarding.

Do not use Network Manager to attempt to configure a dual-NIC routing system.

MrC

---

### Post by mihaisofti on 2007-03-29
Dear Mr C

Sorry if my questions are causing you some irritation.  Clearly, I don't fully understand (which is why I'm here and asking) the implications of what I am doing.  I suppose that I need the server to perform some kind of routing function, in that I want it to connect to the Internet using eth1, and allow clients (which logon to the server through eth0) to use that Internet connection.  So I assume that the server is functioning as a router (amongst other things). 

Removing the superfluous default route (the one to the broadband connection) has resulted in the default internet gateway vanishing.  I haven't used the gui network manager to do this, just to view it.  When I add it back in, it appears in the output from netstat -nr.

Thanks

---

### Post by Mr. C. on 2007-03-29
No irritation, no problem.  I can give you a fishing pole and a lesson, or I can give you a fish.  Its seems you're not sure which you want.

If you want the fish, show me all your LAN IP information for both NICs, and your router/broadband (this is IP, netmask, broadcast, and your broadband's address).

if you want the pole and the lesson, print out the materials referenced (esp. the lab!), and work through the process.  It really is not that difficult.

MrC

---

### Post by marianlibrarian on 2007-03-30
This is what worked for me.

The only way you can have eth0 and eth1 active at the same time is if you have two network cards. I don't and you probably don't either.

Replace instances of eth1 with eth0:1

I asked the same question. 
[http://forums.debian.net/viewtopic.php?p=59674#59674](http://forums.debian.net/viewtopic.php?p=59674#59674)

I hope this helps!

---

### Post by eentonig on 2007-03-30
Some people do have 2 NIC's. I have my wireless and Wired in this laptop.

And at home, I have an old desktop with 4 (four) NIC's connected.

---

### Post by marianlibrarian on 2007-03-30
If you only have "one" NIC then the post above "sudo aptitude install brains" will work. I took me a long time to get the answer on how to do this with only one NIC. Maybe he should try it with just one NIC.

---

### Post by mihaisofti on 2007-04-23
Ok.  I definitely need the pole and lesson.  I have read through all the posts that you indicated, but still feel unsure as to what I am doing.
In answer to other posts, I DO have two physical ethernet cards in my server, and the out put from netstat -nr is as follows:
Destination     Gateway     Genmask             Flags   Mss Window   irtt  Iface
192.168.2.0   0.0.0.0        255.255.255.0    U            0   0            0     eth0
0.0.0.0           192.179.2.1 0.0.0.0               UG          0   0            0     eth0

Eth0 has ip 192.168.2.5/255.255.255.0 GW 192.168.2.1
Eth1 has ip 192.168.20.5/255.255.255.0  GW 192.168.20.254

I have enabled port forwarding.  Something is obviously missing still.  Thanks for all your help.

Mihai

---

### Post by Mr. C. on 2007-04-23
Your route table is missing a route for the 192.168.20/24 network. It should look like:

```
192.168.2.0 0.0.0.0 255.255.255.0 U 0 0 0 eth0
192.168.20.0 0.0.0.0 255.255.255.0 U 0 0 0 eth1
0.0.0.0 192.179.2.1 0.0.0.0 UG 0 0 0 eth0
```

A route table entry is required for each interface.  When bringing up the interface, the ifup command adds this route.  So if the route is missing, either you did not bring up the interface, or you removed that route.

Two things are required to route packets:
1) ip forwarding must be enabled
2) there must be a route for each network interface you want enabled as destinations

MrC

---

### Post by mihaisofti on 2007-04-24
Sorry! There was a typo in my last message.  The last line of output should have read:
0.0.0.0    192.168.2.1    0.0.0.0 UG     0 0 0 eth0

I am looking into the other matters, and will post again.

In the meantime thanks for your patience and assistance,

Mihai

---

### Post by mihaisofti on 2007-04-29
ok, I finally have a handle on default routes.  I now have only one default route - the one pointing to the lan side, ie 192.168.2.1 from server Ubuntu at 192.168.2.5.  It reads as follows

0.0.0.0 - 192.168.2.1 - 0.0.0.0 - UG - 0 - 0 - 0 - eth0

With both interfaces enabled on the server I can login to the server (Ubuntu) from my xp laptop with only some of the user accounts (but this is another problem). I think I have enabled port forwarding on the server, which I did by editing /etc/rc.local, but there is another rc.local at /etc/init.d/rc.local.  Is there a command line to check if it is enabled?  With only eth1 enabled, I can connect to the internet from the server, but not with both enabled.  Is this right?

Thanks again

Mihai

---

### Post by Mr. C. on 2007-04-30
IP forwarding state can be view with:

 ```
cat /proc/sys/net/ipv4/ip_forward
```

It is a 0 or 1, indicated if forwarding is enabled.

Your IP forwarding server's default route should point to your internet connection's router IP address.  If you default to the LAN, how can traffic for unknown IP address (eg. all that are NOT your LANs) ever find their way to the internet ?

Default route means "if I don't know where to route this packet, which system can I send it to, to take care of it for me".

MrC

---

### Post by mihaisofti on 2007-05-07
Yes, of course.  I now have the correct default route, and only one.  My server is now capable of dealing with logon requests and connecting to the Internet at the same time, however the client machine is not able to connect to the Internet through the server's connection.  I have tried defining the client's default gateway, in turn, as the server's ip address for both eth0 and eth1, but to no avail.  Port forwarding is enabled. In order to make things simpler, I have removed the 2 ipcop boxes, and changed the server's ip address accordingly.
On the server side, eth0 has ip 192.168.1.5/255.255.255.0 gw 192.168.1.10
eth1 192.168.20.5/255.255.255.0 gw 192.168.20.254
and output from netstat -nr is:
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.20.0    0.0.0.0         255.255.255.0   U         0 0          0 eth1
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0
0.0.0.0         192.168.20.254  0.0.0.0         UG        0 0          0 eth1

According to a recent post, the spurious entry beginning 169...  should have no ill effect and can be left there.  Is this correct?

have you any ideas as to where I am going wrong?

tia

---

### Post by Mr. C. on 2007-05-07
Port forwarding is set on which machine ?

Your client machine must use the server's LAN interface address as it default gateway.

The 169 address is not spurious, it is a local-link address, used as a last resort for connecting a system with no IP settings available.  It is harmless.

What hardware has the address listed in your default gateway on the server (192.168.20.254/24) ?

Show your client IP info as well.
MrC

---

### Post by mihaisofti on 2007-05-09
Thanks for your reply.  
 	> Port forwarding is set on which machine ?
On the server 192.168.1.5/24

> What hardware has the address listed in your default gateway on the server (192.168.20.254/24) ?
This is the lan address of a netgear rp114 router

and this is the Windows IP Configuration

        Host Name . . . . . . . . . . .. : D610
        Primary Dns Suffix  . . .  . . : 
        Node Type . . . . . . . . . . . . : Unknown
        IP Routing Enabled. . . .  . . : No
        WINS Proxy Enabled. . . . . . : Yes



Ethernet adapter Wireless Network Connection:

        Media State . . . . . . . . . .  : Media disconnected
        Description . . . . . . . . . . . : Intel(R) PRO/Wireless 2200BG Network Connection
        Physical Address. . . . . . . .: 00-13-CE-83-4D-7F


Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . : 
        Description . . . . . . . . . . . : Broadcom NetXtreme 57xx Gigabit Controller
        Physical Address. . . . . . .  : 00-14-22-C0-EB-BA
        Dhcp Enabled. . . . . . . . . . : No
        IP Address. . . . . . . . . . . . : 192.168.1.10
        Subnet Mask . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . .: 192.168.1.5
        DNS Servers . . . . . . . . . . : 158.43.240.4
                                                 158.43.240.3

        Primary WINS Server . . . .  : 192.168.1.5

Are there any glaring faults here.  

Many thanks for your time,

Mihai

---

### Post by Mr. C. on 2007-05-09
Something does not make sense here.

You have your default route being on the 192.168.20/24 network.  Yet you say that your netgear router is on that network.  Its IP address is 192.168.1.10, which is on the 192.168.1/24 network !

Draw yourself a box picture of each piece of hardware, and connect lines between each interface that represent their physical connections.  Label each line with the network it represents, and the endpoints of each line with an IP address.  So you should have a box for your laptop, a box for your server (with two interfaces), a box for your router, and possible a box for your broadband modem (if that isn't your linksys).  Either way, also draw a line that is your WAN ip connection and show its addresses.

You should have clear, non-overlapping networks, and each endpoint can only belong to one single 1 network.

MrC

---

### Post by mihaisofti on 2007-05-10
Yes, of course.  Silly me.

Thanks

---

### Post by mihaisofti on 2007-05-11
I have corrected  the errors, and now have no overlapping networks.
code as follows:
netstat -nr
Kernel IP routeing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.20.0    0.0.0.0         255.255.255.0   U         0 0          0 eth1
192.168.2.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0
0.0.0.0         192.168.20.254  0.0.0.0         UG        0 0          0 eth1


ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0E:A6:1D:AD:F7  
          inet addr:192.168.2.5  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:a6ff:fe1d:adf7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:152 errors:0 dropped:0 overruns:0 frame:0
          TX packets:126 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:13045 (12.7 KiB)  TX bytes:16188 (15.8 KiB)
          Interrupt:21 

eth1      Link encap:Ethernet  HWaddr 00:05:1B:00:65:91  
          inet addr:192.168.20.5  Bcast:192.168.20.255  Mask:255.255.255.0
          inet6 addr: fe80::205:1bff:fe00:6591/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:511 errors:0 dropped:0 overruns:0 frame:0
          TX packets:518 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:592456 (578.5 KiB)  TX bytes:61971 (60.5 KiB)

The xp client output for route print is:

===========================================================================

Interface List

0x1 ........................... MS TCP Loopback interface
0x2 ...00 14 22 c0 eb ba ...... Broadcom NetXtreme 57xx Gigabit Controller - Packet Scheduler Miniport
0x3 ...00 13 ce 83 4d 7f ...... Intel(R) PRO/Wireless 2200BG Network Connection - Packet Scheduler Miniport
===========================================================================

===========================================================================

Active Routes:

Network Destination        Netmask          Gateway       Interface  Metric

          0.0.0.0          0.0.0.0      192.168.2.5    192.168.2.10	  20

        127.0.0.0        255.0.0.0        127.0.0.1       127.0.0.1	  1

      192.168.2.0    255.255.255.0     192.168.2.10    192.168.2.10	  20

     192.168.2.10  255.255.255.255        127.0.0.1       127.0.0.1	  20

    192.168.2.255  255.255.255.255     192.168.2.10    192.168.2.10	  20

        224.0.0.0        240.0.0.0     192.168.2.10    192.168.2.10	  20

  255.255.255.255  255.255.255.255     192.168.2.10    192.168.2.10	  1

  255.255.255.255  255.255.255.255     192.168.2.10               3	  1

Default Gateway:       192.168.2.5

===========================================================================

Persistent Routes:

and iconfig is 
Windows IP Configuration





        Host Name . . . . . . . . . . . . : D610


        Primary Dns Suffix  . . . . . . . : 


        Node Type . . . . . . . . . . . . : Unknown


        IP Routing Enabled. . . . . . . . : No


        WINS Proxy Enabled. . . . . . . . : Yes





Ethernet adapter Local Area Connection:





        Connection-specific DNS Suffix  . : 


        Description . . . . . . . . . . . : Broadcom NetXtreme 57xx Gigabit Controller


        Physical Address. . . . . . . . . : 00-14-22-C0-EB-BA


        Dhcp Enabled. . . . . . . . . . . : No


        IP Address. . . . . . . . . . . . : 192.168.2.10


        Subnet Mask . . . . . . . . . . . : 255.255.255.0


        Default Gateway . . . . . . . . . : 192.168.2.5


        DNS Servers . . . . . . . . . . . : 158.43.240.4


                                            158.43.240.3


        Primary WINS Server . . . . . . . : 192.168.2.5





Ethernet adapter Wireless Network Connection:





        Media State . . . . . . . . . . . : Media disconnected


        Description . . . . . . . . . . . : Intel(R) PRO/Wireless 2200BG Network Connection


        Physical Address. . . . . . . . . : 00-13-CE-83-4D-7F



Thanks again,

Mihai

---

### Post by mihaisofti on 2007-05-13
What I forgot to say was that I am still unable to connect to the Internet through the server from xp client. 
I am able to ping eth0 and eth1 from xp client, but cannot ping the router at 192.168.20.254.  I am able to ping the lan and wan sides of the router from the server, 

Am I making an obvious error still?

Thanks for your assistance

Mihai

---

### Post by Mr. C. on 2007-05-16
Sorry for the delay - I've been out of town.
The configuration looks correct.  Do  you have ip_forwarding still enabled ?

Also, have you configured your router at 192.168.20.254 to know about your server acting as a router ?  Without that, how will it know where to send packets for the 192.168.2.0/24 network ?  You'll most likely have to create a static route on your router with a route indicating how to get to the 192.168.2.0/24 network.

MrC

---

### Post by mihaisofti on 2007-05-17
That's done it!  Thanks very much for your assistance over the past weeks.  I really appreciate it.

Mihai

---

### Post by Mr. C. on 2007-05-17
I'm glad to hear you have it working.  Thanks for the update.

Regards,
MrC

---

### Post by mihaisofti on 2007-05-17
There is only one thing that still bothers me, and that is how to stop the additional default route from appearing at every reboot.  I have to delete it each time I start the server.  Do you know why it appears, and what I can do to either automatically delete it on reboot, or stop it appearing in the first place?
Should I be posting this in a new thread?

Mihai

---

### Post by Mr. C. on 2007-05-17
The Network Manager doesn't work very well with a multi-homed system.  As you've discovered, it blindly adds multiple default routes, one for each interface.

Review my last post here:

[http://ubuntuforums.org/showthread.php?t=397576&highlight=default+route+%2Fetc%2Fnetwork%2Finterfaces](http://ubuntuforums.org/showthread.php?t=397576&highlight=default+route+%2Fetc%2Fnetwork%2Finterfaces)

and follow the link mentioned.

MrC

---

### Post by mihaisofti on 2007-05-30
Thanks for the advice.  Having read this and several other posts on the matter, I decided to add the following line to /etc/rc.local:

route del default gw 192.168.2.10

and this seems to work very well.  The server starts up normally as before, but without the additional default route.  Is there any reason I shouldn't use this method?

Thanks again,

Mihai

---

### Post by Mr. C. on 2007-05-30
Deleting the incorrectly added default route is fine.

---

### Post by mihaisofti on 2007-05-31
Thanks for your considerable help over the past several weeks.

regards,

Mihai

---

