---
title: "Home Network Setup Log"
date: 2018-09-04
forum: Ubuntu, Linux and OS Chat
---

### Post by 1Waffle on 2018-09-04
Hopefully this is the correct place for this sort of thing...  I am not asking for support.  I will do my best to read all the man pages.  I plan to document my findings here.

My goal is to overhaul my home network.  I just wiped everything and am starting with a clean slate.  An image is attached with a crude drawing of my goal:
1. Connected to my home internet connection is a computer running Ubuntu Server 18.04 LTS. (It was a Dell haswell i5 w/ 16GB ram I picked up from a local auction.)  I added a USB3 Gigabit Ethernet adapter.  (The USB adapter connects to my modem.)

[LIST]
[*]This will serve as a router/firewall.
[LIST]
[*]Act as my home network's DHCP server. 
[*]Provide a route from my home network to the internet. 
[*]Provide a very controlled route from my home network to my VPN. 
[*]Act as my home network's DNS server.  Resolving hostname.mydomain.com 
[/LIST]
  
[*]It will also serve as a KVM host.
[LIST]
[*]Kimchi? 
[/LIST]
  
[/LIST]
2. I will rent a VPS.
[LIST]
[*]This will serve as an OpenVPN server.
[LIST]
[*]This should provide access from my cell phone to certain VM's on my local network. 
[/LIST]
  
[*]It will also serve as my personal certificate authority. 
[/LIST]
3. ...

---

### Post by TheFu on 2018-09-04
So ... I would strongly recommend against placing a virtual machine host directly on the internet like you are planning.  Firewalls and routers really need to be a separate device for security reasons. 

For running different LANs inside a protected network, knock yourself out using virtualization, but not for a WAN connection. You don't want to provide a beachhead for attackers to go crazy.  

Also, don't provide multiple ways into the network concurrently.  If you use a cell data connection, be certain it terminates OUTSIDE your firewall at home.  Don't trust wifi or cellular data security.

It is really too bad that the RateMyNetwork.net site is gone.  There were thousands of networks posted there with ratings by network professionals. Sadly, they used php to make grabbing a static site impossible, so even the way-back machine doesn't have a good image.

For managing the KVM stuff, I use virt-manager.  It uses ssh tunnels so management can happen from anywhere in the world.  IMHO, critical infrastructure  should never be available for modification through a web interface without demanding localhost-only connectivity (use an ssh-tunnel for that).

That USB3-to-GigE connection probably is overkill and will have not-so-great latency.  I have one for my chromebook and it works fine for that purpose, but I'd avoid USB network adaptors for something trying to be a router.  Intel PRO/1000. Accept nothing less.

And how do I say this nicely.   I can't.   In no way would I trust my infrastructure to 18.04 today.  NO FREAKIN' WAY!   16.04 until 18.04 gets stable, fixed, solved, network and security proven.   A KVM host needs multiple-month uptimes.  That just isn't possible with any release less than a year old.  Too many kernel patches coming.

But it is your network and your machine.  Only you can decide what is best.

---

### Post by 1Waffle on 2018-09-05
I understand that my stated setup is not even close to ideal.  I do not intend to leave it this way long term.  I am listening to router reviews/setups while I work, and plan to purchase a good one in a couple months.  (Currently I favor dongle sized pfsense box).  I am USB dongle, for the WAN connection because it is disposable.  

I had previously had a now disposed junk computer connected directly to my modem.  (Lightning killed its nic.)

In the next 10 years I expect to move at minimum 5 times.  In the 7-8 months (before I move), I want to get all of my home network gear (including my landline corded phone) into a portable musician's rack. Something like this: ([https://www.sweetwater.com/store/detail/GPro8--gator-g-pro-8u-19-pro-series-rack-case](https://www.sweetwater.com/store/detail/GPro8--gator-g-pro-8u-19-pro-series-rack-case)) This would include a small UPS.  But this for a thread for another day...


TLDR I am doing this more as an exercise of futility if nothing else.

---

