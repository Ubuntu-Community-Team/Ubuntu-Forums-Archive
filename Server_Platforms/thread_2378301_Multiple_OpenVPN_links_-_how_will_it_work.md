---
title: "Multiple OpenVPN links - how will it work?"
date: 2017-11-22
forum: Server Platforms
---

### Post by wowiesy2 on 2017-11-22
Hi,

After setting up MultiWAN router at the satellite office, we experienced problems accessing applications at the main office (through Windows remote Desktop).  WinXP and Win7 clients had intermittent Remote Desktop connection to the main office.  The setup then was using Remote Desktop app directly to access the main office. I asked support from the main office to setup OpenVPN... and then we setup the WinXP and Win7 clients to be OpenVPN clients connecting to the main office.  This way.. somehow, the connections to the main office has stabilized.  

The next step will be to setup the OpenVPN on the MultiWAN router itself on the remote LAN.  This way, OpenVPN will be transparent from the windows clients. They just launch their Remote Desktop applications and the VPN has been provided by the LAN.  

Our concern now is bandwidth.  Even though we have 3 different internet links at the main office, each has limited bandwidth. With 4 users from the remote LAN (with more to come) trying to access the main office, at the current setup, wherein each Windows clients has their own OpenVPN client... each client's config file were setup to point to 3 different IP addresses of the main office, in effect doing load balancing in a way.  But, if the OpenVPN link is setup by the MultiWAN router, even though I can setup 3 config files for OpenVPN to get each file point to each IP address from the main office, when the client launches Remote Desktop, is there a way to control which OpenVPN link will this certain client use?  

this is the layout:

Main Office:
WAN IP1: xx.xx.xx.xx
WAN IP2: yy.yy.yy.yy
WAN IP3: zz.zz.zz.zz

Remote application is accessed through:
LAN IP1: 192.168.100.x
LAN IP2: 192.168.100.y

Remote Office (Multi Wan load balancing mode)
WAN Gateway1: 192.168.2.xyz
WAN Gateway2: 192.168.15.abc
LAN gateway: 192.168.111.1

Current Setup:
Each Client has OpenVPN client - pointing to a specific WAN IP of the Main office  -> stable remote desktop access

Planned Setup:
1. Transfer OpenVPN services (connection between Main Office and Remote office) to the MultiWan Router at the Remote office
    a. use 1 OpenVPN link to the Main Office  
          - multiple remote desktop access to main office -> may encounter bandwidth problems
    b. use 3 OpenVPN links to the Main Office
          - how to direct each Remote Office client to "use" a specific OpenVPN link   (to achieve load balancing) 

the fall back is the current setup.. where each client has their own OpenVPN client... they connect as needed.. 


any thoughts? thanks in advance.

---

### Post by wildmanne39 on 2017-11-22
*Thread moved to **Server Platforms for a more appropriate fit**.*

---

### Post by darkod on 2017-11-22
Hmmm, it's not a very elegant solution, but you could control this with static routes on each windows client that does the RD. The client has to know to route traffic for LAN IP1 and IP2 through the openvpn tunnel anyway.

So if you install 3 openvpn tunnels, on first group of clients you set up static route to send traffic destined for the RD over vpn1. On the second group to go over vpn2, and the third over vpn3.

That way each client RD will go through vpn tunnel that you select.

There might be a better solution but this is the first thing that occurred to me...

---

### Post by wowiesy2 on 2017-11-22
this is a solution worth thinking over... 

I thought of another... using iptables?  rdp (port) and forward to specific tun interface on the MultiWAN router?  like port forwarding or NAT in a way...   

but both these solutions (static routing and iptables) may get more complicated considering that the WAN links (WAN Gateway1 and WAN Gateway2 ) can be offline / online at certain times.. and the routing of the MultiWAN router itself has been configured for load balancing and failover as needed...   I recon that the solution on this (static route or iptables) should be able to follow the changes happening at the connection level...

---

### Post by wowiesy2 on 2017-11-22
> **darkod said:**
> Hmmm, it's not a very elegant solution, but you could control this with static routes on each windows client that does the RD. The client has to know to route traffic for LAN IP1 and IP2 through the openvpn tunnel anyway.

So if you install 3 openvpn tunnels, on first group of clients you set up static route to send traffic destined for the RD over vpn1. On the second group to go over vpn2, and the third over vpn3.

That way each client RD will go through vpn tunnel that you select.

There might be a better solution but this is the first thing that occurred to me...


so.. right now... say.. my MultiWAN router has these interfaces:

WAN1=enp1s0
WAN2=enp3s0
LAN=enp2s0

if I setup OpenVPN (assuming 3 links), these will be added:
tun0 ->  link1
tun1 -> link2 
tun2 -> link 3 

each link will have their own IP address (even though there are three WAN IP addresses to connect to, the setup may be just the routers / modems routing the 3 WAN IPs to a single OpenVPN server IP and port at the main office, hence we can have a scenario where the 3 links will have their own IP addresses all in the same VPN subnet)  

or would it be better to have 3 OpenVPN servers listening in on different ports, that way I can have each server be on separate VPN subnet? 

is it possible to check how many active rdp sessions per openvpn link are there so a script can check to use which vpn link? 

of course the best way is still to buy more bandwidth at the main office... =)

---

### Post by SeijiSensei on 2017-11-22
I use different ports for each tunnel.  I have one server that functions as a router for a number of hosts connected using OpenVPN over [static tunnels]("http://openvpn.net/static.html").  Each configuration file has a unique port address.  I don't know how well that would work in a Windows setting though.

---

### Post by darkod on 2017-11-22
Depending how much of the bandwidth is used currently, buying more might definitely be the best option. And use wan1 only as primary and wan2 only as secondary.

Because all other solutions get too complicated too fast... Especially if you also want to keep connection number stats, etc.

If you have two hosts with the application and two wan links at the remote office, you can also try limiting one host to one wan link. If the hosts are accessed evenly more or less... But again, you will need to use static routes. It will be more efficient if you can set up static routes on the default router instead of each client. That way you use the router to help you route traffic to lan1 over wan1/tun1, and traffic to lan2 over wan2/tun2.

---

### Post by wowiesy2 on 2017-11-28
In connection with the above setup...  after 1 week in use.. we are getting mixed feedback from the users.  Mostly it seems bandwidth related - both on the main office side.. and also possibly here at the remote office side.

I would like to optimize the settings here at the remote site so as to be able to isolate purely bandwidth issues on the Main office site...   although my first hunch is that it is really an issue on the bandwidth here at the Remote site.. but it could be both.. or more... 

so.. again.. from here inside the Remote office, where we have  Multi Wan setup:

WAN1 gateway: 192.168.15.1
WAN2 gateway: 192.168.2.1

router interfaces:
WAN1:192.168.15.254
WAN2: 192.168.2.254
LAN: 192.168.111.1

source based policy routing is implemented to achieve load balancing / failover with gwping script

OpenVPN at the main office setup:
1. Server machine
2. 3 routers (from each Internet link) forwarding to this OpenVPN machine
3. IP range offered by this OpenVPN Server to the clients:  10.0.5.0/24
4. Uses TAP adapters on the Windows Clients connecting to the OpenVPN Server

OpenVPN itself is able to connect..

 it was observed that when RDP was disconnected on some clients, OpenVPN link is still active  -> not sure where this information leads me though..  

my questions:
1. although the clients are able to access the RDP service at the main office, I am thinking maybe there are route settings I can setup here at the Remote office LAN multi WAN router to help out and optimize?  do I need to make entries in the routing tables at the Remote office Router?  they are all just clients connecting to the server (as per my understanding, the routes need to be set up on the server side - but I could be wrong) 

2. I am looking at implementing traffic shaping at the Remote site as the intermittent RDP connections is observed during times when there are other field staff at the remote office accessing Internet as well...  perhaps I can implement traffic shaping to prioritize traffic from the clients using RDP over the other "plain internet" users... 

comments please? 

thanks in advance.

---

