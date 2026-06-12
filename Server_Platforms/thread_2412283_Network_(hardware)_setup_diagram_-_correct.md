---
title: "Network (hardware) setup diagram - correct?"
date: 2019-02-10
forum: Server Platforms
---

### Post by aljames2 on 2019-02-10
I am setting up an Ubunter server in my home network.  As you can see from the diagram, I'm not sure which router to plug my server in.  Plus, I want to make sure everything else is plugged in correctly?

My TP-Link router which is currently set up as my wireless access point, has the capability in the software to turn on OpenVPN with certificate generation.  I'd like some suggestions if this feature is recommended and any other thoughts.

Thanks to @TheFu for his helpful blog, in particular the article on WiFi router security checklist here [http://blog.jdpfu.com/pages/wifi-security](http://blog.jdpfu.com/pages/wifi-security)
I've gone through this on each router to double check each router's settings.  I'm not sure though how to enable only HTTPS for management of these routers.
I get unclear on when I need to purchase a domain to get the SSL certificates or if there is another way.

[ATTACH=CONFIG]282456[/ATTACH]

---

### Post by LHammonds on 2019-02-10
If your server does not have wireless, then you will have to plug into the router.

However, wireless is typically slower and prone to "air issues" which is why I always have my servers plugged into the fastest and most stable option possible.  In this case, a LAN cable direct to your internet router.

This also simplifies troubleshooting.  If a service is down, is it down on the server or the switch it is plugged into or the switch that switch is plugged into, etc.  Less points of failure the better.

LHammonds

---

### Post by aljames2 on 2019-02-11
Should I plug everything into my 2nd access point router?  The Verizon FiOS device is my modem/router combo device issued by Verizon.

Also. what are the advantages of using a switch device in a home network and where would it go in my diagram?

---

### Post by TheFu on 2019-02-11
I can't tell what you are trying to accomplish since no IPs or subnets are listed. If you are trying to do what I suggested (vpn-only access or ssh-tunnel) or not, I cannot tell.

I wouldn't put a printer where is was accessible over the internet, unless you don't mind it being hacked and printing lots and lots of pages you didn't request. Is the TPLink a router or an AP?  It matters.

I know nothing about verizon equipment or how they run their networking. Sorry.  That means you'll need to share that information to get good advice from anyone unfamiliar with it.

I can recommend taking a look at LHammonds' blog too. Good stuff there.

---

### Post by aljames2 on 2019-02-11
The TPLink is a router.  In the Firmware, it's static IP address is x.x.x.2 with DHCP off.  Currently, the _Internet Settings_ in this router is 0.0.0.0 for all this...(Internet IP, Subnet Mask, Gateway, Primary & Secondary DNS).  Connection type Dynamic IP.  The Wireless radio is on to handle WiFi in the home.  This router's firmware does have a VPN Server (OpenVPN) section that can be enabled...I guess where the router would handle my local VPN?

The Verizon FIOS Modem/Router device is the top-level device connected to the internet.  (I can see now I need to move the Server & Printer behind the TPLink)

Thanks for suggesting LHammonds blog.  I found his complete server setup & NextCloud tutorials. :D  This is where I'm headed with my setup.  I definitely like & understand the LVG methodology and will implement that.  However, I do prefer a VPN setup because it will be simpler for my users so they don't have to worry about configuring a browser or other application to access.  Also, better I think for when I travel and need to connect from hotels, airports, etc.

---

### Post by TheFu on 2019-02-12
Either the router is acting like a route/firewall with NAT or it is acting like a bridge. In bridge mode, it can't be a VPN server, but then the network is probably doing double-NAT.  This is why I asked for the IPs to be labelled.  The different subnets are critical and now is the time to fix them. The internal, non-routable, LAN subnet cannot be used by any location you visit if you want VPN access. This is required for routing to work.

BTW, I've never heard of LVG ... generally it is called LVM with PVs, VGs, and LVs. I think his use of LVG is normally called VGs, since everything is "logical" already. 

Beware that getting OpenVPN working isn't trivial.  It definitely isn't a checkbox-enable. OTOH, getting ssh working is almost as easy as running a non-secured HTTP server. Relatively bonehead.  VPNs are much easier for end users, once setup and working.

---

### Post by SeijiSensei on 2019-02-12
I have an Archer C7 router connected to the Verizon router.  I never use the Verizon router for anything other than interconnecting with their network.  I've even turned off the wifi in that router.  I have an Ethernet cable connecting one of the VZ LAN ports to the WAN port on the Archer.

If you take this route and put the TP-Link device behind the Verizon router, connect the server and printer to the TP-Link, and they should be visible to all users.

---

### Post by TheFu on 2019-02-12
But does the Verizon still do NAT or can it be setup in bridge mode?

---

### Post by aljames2 on 2019-02-12
I will get the diagram updated with IPs this evening.  I know currently the 2 routers are connected by 1 ethernet cable using LAN ports only.  WAN ports are empty.

---

### Post by aljames2 on 2019-02-12
Ok here is an updated diagram of how things are currently connected.  It  doesn't appear this is in bridge mode.  My TP-Link router (I mislabeled it as "Access Point") is  configured as a secondary router to handle wireless connections  in the home.
These are the instructions I had used a few years ago  when I set this all up ...if it helps.   [http://www.dslreports.com/faq/12506](http://www.dslreports.com/faq/12506)

[ATTACH=CONFIG]282492[/ATTACH]

---

### Post by aljames2 on 2019-02-12
Adding this: [http://www.dslreports.com/faq/16077](http://www.dslreports.com/faq/16077)
Breaks down the various connection scenarios using a 2nd router with the Verizon Actiontec modem/router.  Scenarios 3, 4, & 5 avoid the double NAT problem; however, 4 & 5 involves bridging.  
Option 3 which is what I have set up appears to use the Verizon router as primary (internet & routing) and my TP-Link router as a switch.
Selecting the correct configuration is the first step it seems.  I can buy additional equipment if needed.

---

### Post by SeijiSensei on 2019-02-13
> **TheFu said:**
> But does the Verizon still do NAT or can it be setup in bridge mode?

Both my routers use NAT.  The Archer has a DHCP connection to the LAN side of the Verizon router.

I don't see any advantage in using a bridged router.

---

### Post by TheFu on 2019-02-13
A flat network as shown provides little to zero security.
* subnet for "devices" - TVs, video players, all wifi stuff.  I treat this like it is internet/untrusted
* subnet for internet facing services, always wired.
* subnet for trusted services, always wired, 
* subnet for trusted desktops, always wired.

Setup exact firewall rules to allow only the required connection between these subnets for specific clients.
Devices using DHCP should be avoided, unless they are using IP reservations.  Any "guest devices" don't have any firewall access except to the internet.
Servers and desktops (non-portable devices) get static IPs on the correct subnet for their purpose.

If you get really secure and have lots of data, you might want a physically separate storage/admin network for backup and access only by trusted clients. Beware, this other connection may provide back-network access if it isn't handled correctly.

I would begin by making a detailed list of every device and every service you will run on each device.  Then assign them to a subnet. Services on a single device or VM that belong on multiple subnets need to be split apart.

And always remember that VLANs are just suggestions. They don't provide real security if the physical connections are shared.

The main reason to use the WAN router in bridge mode is to remove any belief that the ISP management provides **any** security.  Make no mistake, the ISP totally controls that box.  My ISP would reset any password I entered back to the default every night when they changed their WAN-admin password. They did that to prevent any fired techs or remote support people from having access more than their last day of work.  

They can see all the devices on that LAN from that 1 box.  But in bridge mode, they only see what YOUR WAN router allows.  Just something to consider.

---

### Post by aljames2 on 2019-02-14
Here is what I can imagine so far.  I'm not sure I have them in the right category but the "what I have" is correct.  Is it reasonable that the 3 trusted services I have listed could all run on 1 metal server box?  I've read elsewhere where some will use a separate physical server (Rasberry or other) to serve media or cloud...but I'm thinking my 1 box could handle it all?

* I may eventually set up an offsite backup server but that can wait.

Internet/Untrusted devices:
 

[LIST=1]
[*]Verizon Set top TV box (room 1) – Coax Connection to wall which leads to the Verizon ONT
[*]Verizon Set top TV box (room 2) – Coax Connection to wall which leads to the Verizon ONT
[*]Apple TV (wi-fi)
[*]Sony BluRay player (wi-fi)
[*]3 Personal laptops (wi-fi)
[*]3 iPhones (wi-fi)
[*]1 iPad (wi-fi)
[*]1  Corporate issued/owned laptop (wi-fi), uses it’s own software (Cisco  Any-connect) to connect via VPN to the corporate  intranet.
[/LIST]
 
Internet Facing Services (Wired)
 

[LIST=1]
[*]?
[/LIST]
 
Trusted Services (Wired)
 

[LIST=1]
[*]NextCloud Server (Ubuntu Server)
[*]Music Server (Ubuntu Server)
[*]Storage/Backup Server (Ubuntu Server)
[/LIST]
 
Trusted Desktops (Wired)
 

[LIST=1]
[*]Gaming Desktop PC (Windows 10)
[*]Daughter Desktop PC (Windows 10)
[/LIST]

I have learned recently about subnetting & available hosts in each range so I'm starting to visualize how the separate subnets would be addressed.

As for the routing, if I put my ISP modem/router in bridge mode and use my WAN router to control the networking (as in configuration #4 in my earlier verizon link), would there be any VPN related problems due to the bridge mode?


-------------
Unrelated, is it wise to do my first real install of Ubuntu Server using the version 18.04.1 or 18.04.2 (just released, newer kernel)?  I've read that some recomm. starting with version 16. as it's more seasoned.  I plan to set up the server this weekend.

Thanks to everyone for the help.  Much appreciated.  :)

---

### Post by reedgoossens on 2019-02-14
Today I taking a look at the home *networking hardware* and Understanding Home *Networking* Through *Network Diagrams*

---

### Post by LHammonds on 2019-02-14
> **aljames2 said:**
> is it wise to do my first real install of Ubuntu Server using the version 18.04.1 or 18.04.2
There is a much bigger difference setting up a 16.04 server verses 18.04 than between 18.04.1 and 18.04.2.

Personally, I would ALWAYS setup a server with the most current release and try and make that work first before going older.  Sure, there are a lot more tutorials out there for 16.04 than 18.04 and some applications require older libraries but you eventually will want to move into the current release so why not start there first.

On my site (in sig), I have detailed steps on installing a production-level server for 16.04 and 18.04 as well as how to install NextCloud and MariaDB for both versions.

Nothing you mentioned as far as I can tell would require the 16.04 version.  My servers were installed with the 1st version of 18.04 and have auto-updated (with my scheduled scripts) to 18.04.1 without any issue as well as recently going to 18.04.2 automatically without any issues at the OS or application level for what I am running.

Sticking with the LTS version "is" your stable option.  Using the in-between versions (odd numbers like 17.01 / 19.01) are not wise decisions for server scenarios unless there is a specific use case.

LHammonds

---

### Post by aljames2 on 2019-02-14
Thanks LHammonds, I will be referring to your tutorials very soon.

-----------------
I think this network configuration should work fine, similar to @SeijiSensei  suggests but since I also have the Verizon TV & features that  depends on the Verizon router I need a 2nd bridge:

Bridging  the Verizon Router passes all Internet WAN traffic through, making my TP-Link  router primary. Another internal bridge passes data from my router back  to the Verizon Router coax LAN for TV SetTopBox data.  Without this 2nd  bridge my TV's won't work right.

[ATTACH=CONFIG]282521[/ATTACH]

Tutorials I've read indicate the effects of this configuration to be:

PROS: 

[LIST]
[*]Bypasses the small NAT table in the Verizon Router. NAT limited by primary router, not Verizon Router. 
[*]TV VOD and guide data supported. 
[/LIST]

CONS: 

[LIST]
[*]May require a HARD reset of the Verizon Router to restore to factory defaults. 
[*]Not all configuration information saved to config file. Some bridging information lost on a power fail. 
[*]Switch ports on Verizon Router not available as LAN ports. 
[/LIST]

Other forums have support/steps on how to accomplish this in the routers.

My goal of all this here is to check with the server pros to see if this foundation is viable to build a home network with a VPN setup?

---

### Post by aljames2 on 2019-02-16
@TheFu, I have a few questions about your VPN WiFi Simplified diagram if you don’t mind.  I see the connection between the ISP router & lab router is LAN to WAN (not bridge mode I’m assuming), does this create a double NAT?  The wireless access point, if connected to the ISP router would require that the ISP router not be in bridge mode, correct?

If instead, the access point were connected to the lab router using a different subnet, would that provide adequate separation?

---

### Post by TheFu on 2019-02-19
> **aljames2 said:**
> @TheFu, I have a few questions about your VPN WiFi Simplified diagram if you don&#8217;t mind.  I see the connection between the ISP router & lab router is LAN to WAN (not bridge mode I&#8217;m assuming), does this create a double NAT?  The wireless access point, if connected to the ISP router would require that the ISP router not be in bridge mode, correct?

If instead, the access point were connected to the lab router using a different subnet, would that provide adequate separation?

You've lost me.  What diagram?  Link?  I've made hundreds (perhaps thousands) of diagrams. Maybe something like this to start? [http://blog.jdpfu.com/2010/06/16/wireless-bridging-with-security-in-a-home-or-small-business](http://blog.jdpfu.com/2010/06/16/wireless-bridging-with-security-in-a-home-or-small-business)

I don't have double-NAT in my setup, but from an unlabelled diagram, that might be guessed. I use pfSense for the WAN/core router, which does much more than typical home routers.  That router has a different port for different subnets, plus for wifi and untrusted guests, those connect to the ISP router's 10.1.10.x subnet.   My ISP router bridges my /29 public IPs to the pfSense box.  1 of the subnets it provides has just public servers.  The other port go to different subnets for non-servers (untrusted/trusted).
 
I am not on Verizon, but I would assume all their video offerings are on different logical networks that no customer can see with reserved bandwidth.

Subnetting provides a clear location for a locked down firewall.

---

### Post by aljames2 on 2019-02-19
Sry for the diagram missing.  I was looking at the diagram you have in your forum profile.  [https://ubuntuforums.org/album.php?albumid=2644](https://ubuntuforums.org/album.php?albumid=2644)
Your blog article is answering many of my questions.  Thanks!

I plan to put the Verizon router in Bridge mode to my main router  (Ubiquity ERX - non wireless router), and then subnet off that 3  networks (3 ports).  One of the networks will be to a wireless router  configured as an access point for guest access.

The verizon router is connected to the wall by Coax (MoCA).  This coax is the source for internet to their router (ISP).  TVs are plugged into Coax outlets throughout the house.  The only relevance their router has to my TVs is to deliver over Coax the Video on Demand (VOD) and TV Guide listings data.  I verified with Verizon yesterday that by putting their router in bridge mode I will lose these features (unless) I also connect one of my router LAN ports back into their router WAN port similar to the image I posted a few threads ago.  I hate that I have to waste a LAN port on my router to backfeed a signal to their router in order to keep the TV guide data on the Coax.  I'm learning.

Thanks again

---

### Post by TheFu on 2019-02-19
I don't trust any wifi without a full vpn.  Wifi is essentially "internet" traffic at this point.

---

### Post by aljames2 on 2019-03-18
Regarding my network & wireless...

I've done a lot of work to get to this point.  I ran an ethernet cable from my Verizon ONT in the garage through 2 stories to the attic, then dropped through target wall. This connection replaces my coax internet connection and I have removed the verizon router for internet and replaced it with a home built pfSense router/firewall.  Now I am working on separating my trusted/wired computers & NAS server from a wireless access point in the home.
 
 
  My pfSense router has 4 intel Gb ports.  Here are my current connections, all hardware, no VLANs involved.  

   
  INTERNET -> pfSense router/fw WAN (igb0)

                -> pfSense router LAN (igb1) -> unmanaged switch -> Trusted PC
                                                                                    -> Trusted PC
                                                                                    -> Ubuntu storage server
                                                                                    -> Wired printer

              -> pfSense router LAN (igb2) -> unmanaged switch -> Wireless Access point (separate subnet than everything on igb1)

1) What I haven't figured out yet is how to set up a VPN connection so that trusted laptops can use the Wireless Access Point to gain access to the trusted subnet?  
2) I also need to figure out how to separate out a "crap network" for untrusted devices, appliances, guests, etc.?
3) Wasn't sure about placement of the printer because some laptops might need to print remotely via the wireless access point?

---

### Post by TheFu on 2019-03-24
Wow. That's a bunch of work.

1) I run a VPN server inside the trusted server subnet. Different VPN logins have different credentials and are provided specific routes to other networks. I'm using openvpn, but might change to a newer VPN tool if it becomes included in the Linux kernel.  This VPN server is available from anywhere in the world (well, almost).

2) pfSense or your ubiquiti router(s) can do that on the port-basis.

3) Printer placement is a judgement call. I don't have any directly networked printers. My two printers (& scanner/fax) connect to a print server via USB.  To print, clients on the wifi network must run the VPN client and connect to my VPN server.  If the printer were wifi, I wouldn't loose much sleep over it being connected to the untrusted wifi network, still inside the ISP router.  Clearly, I don't know anything about verizon's stuff. "ONT?" Huh?  A few other terms that I don't understand.

Have you considered using backgroun shading to show which subnets each device is on? Draw a big box around all the devices on the "server subnet", put it behind everything else in the Z-axis. Fill in the rectangle with a light-blue.  Use other colors for other subnets.  I showed something like this in my blog diagram.  You may also note that I label the WAN IP and LAN subnet for each router for clarity.

---

### Post by aljames2 on 2019-03-26
Thanks for the diagraming tips, I will post a new diagram here once I’m done.  For now I’m working my punchlist of new things.

I have a 1 router setup (pfSense) on the edge accepting WAN.  Working on learning about the various IDS/IPS options and IP blocking packages in pfSense to improve security monotoring/filtering.  Considering Snort & pfBlocker here.

For the OpenVPN remote access I’m trying to decide if I need to pay for a DDNS service or find a free one, since my ISP does change my public IP occasionally?

To me VPN has 3 scenarios of use, which I’m trying to learn how to implement each:

1). VPN in (remote access),  I’m thinking pfSense can handle this via OpenVPN.
2). VPN out (privacy on the web) ??
3). VPN laterally (between subnets), pfSense can do this...unless a second router is better for this?

Enough to make me feel like another year of college, or more is needed. :)

---

### Post by aljames2 on 2019-04-09
updated home network diagram.  Currently 2 Subnets each on separate interfaces.  No VLANs or VMs.  No bridges.  The wireless access point is actually a TP-Link router configured as an Access Point with DHCP disabled.  All DHCP handled by the pfSense box.  The 1 laptop outside the secure zone...I haven't figured out yet how to allow it un-wired access into the secure server.  I know how to set firewall rules to allow it access but since it's wireless I'm thinking a VPN tunnel between the subnets is best?  I have been reviewing how to configure the pfSense device as an OpenVPN server.

I have an extra interface on the pfSense network card so I am considering placing the Verizon MoCA adapter and it's downline devices (Set Top Boxes) on a separate subnet to keep all the verizon traffic off my other 2 networks.

[ATTACH=CONFIG]283000[/ATTACH]

---

