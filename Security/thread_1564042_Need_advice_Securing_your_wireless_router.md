---
title: "Need advice: Securing your wireless router"
date: 2010-08-30
forum: Security
---

### Post by I_Want_To_Learn on 2010-08-30
Hello

I'm looking to buy a wireless router around the $50 range with security being the top reason. Never used a router. Never went wireless. Don't care about getting the fastest wireless speeds or greatest range since I'll hardly enable wireless. Can you link me to some recommended articles and/or give me some advise on the best way to secure a wireless router?

So far I've gathered I should: 

-Enable WPA2-AES Personal & use very strong key.
-Enable NAT & SPI Firewall (Block all incoming & keep ports closed).
-Change router default username & password.

Not sure if I should do these since various articles give conflicting information:

-Disable SSDI Broadcast
-Disable DHCP
-Enable MAC Filtering

Also every router should be compatible since they use web-based interfaces, right? I wouldn't have a problem upgrading the firmware in Linux?

Thank You

---

### Post by cariboo on 2010-08-30
You've got a pretty good start with the first three items. If you know how many computers are going to be connecting to the router, limit the number of dhcp addresses assigned. I have mine limited to 5 dhcp addresses. 

MAC filtering is a waste of time, as it's pretty easy to spoof a MAC address. I have no opinion about hiding the essid, it may be a little harder for the bad guys to find your router but if someone is determined they'll find it.

If you want to do some testing, I'd suggest giving [BT4]("http://www.backtrack-linux.org/downloads/") a try.

---

### Post by movieman on 2010-08-30
> **I_Want_To_Learn said:**
> 
-Disable SSDI Broadcast

Not a great benefit, and has the potential disadvantage that your computer will probably be broadcasting looking for the router instead, even if you've taken a laptop thousands of miles away.

> -Disable DHCP

Not a great benefit; anyone can pick their own IP address to use on the network.

> -Enable MAC Filtering

Mac addresses are trivial to forge.

All of these things might stop one of your neighbours from trying to use your network, but so will WPA2. None of them will stop a determined attacker, but WPA2 will if you have a decent, long passphrase.

---

### Post by CharlesA on 2010-08-30
movieman pretty much covered it. MAC filtering, etc just give you a false sense of security.

---

### Post by tubbygweilo on 2010-08-30
If not too much trouble I would suggest changing the wireless signon password every now and then but otherwise you seek OK.

---

### Post by mr-woof on 2010-08-30
As said, make sure you're using wpa2-aes with a long, complicated (upper/lower case, numbers etc) password, change the default admin password on the router, update the firmware :)

---

### Post by Sporkman on 2010-08-30
...also, make sure remote administration is disabled (i.e. being able to log into the router from the internet, rather than from within the local network). Should be off by default, but it's a good idea to verify that.

---

### Post by mr-woof on 2010-08-30
and take upnp off as well :)

---

### Post by BkkBonanza on 2010-08-31
All the above info is good.
For $50 you can usually pick up the classic Linksys WRT54GL, which runs Linux and has lots of flexibility since you can install DD-WRT, Tomato or other firmware that gives you more control and useful features. It's also well tested security wise.

---

### Post by tubbygweilo on 2010-08-31
I also run a Linksys WRT54GL with the latest Tomato and can vouch for such a setup.

---

### Post by Agent ME on 2010-09-02
> **mr-woof said:**
> and take upnp off as well :)
UPnP isn't really a problem. It can be used to forward ports to machines in your network, but the machines in your network should be secure themselves anyway.
An attacker can't even use UPnP unless he's already on within your LAN, and at that point they won't need to open any ports since they can just establish outbound connections.

---

### Post by CharlesA on 2010-09-02
> **Agent ME said:**
> UPnP isn't really a problem. It can be used to forward ports to machines in your network, but the machines in your network should be secure themselves anyway.
An attacker can't even use UPnP unless he's already on within your LAN, and at that point they won't need to open any ports since they can just establish outbound connections.

Tell that to the machines that have VNC enabled and set it up so that UPNP allows VNC to access the internet. Not exactly the fault of UPNP, but I fail to see how it is of any benefit when you can forward ports manually if you need to and I haven't had any problems running torrents with UPNP disabled.

---

### Post by Agent ME on 2010-09-03
An attacker can just have the VNC server initiate the connect to his client.

---

### Post by CharlesA on 2010-09-03
> **Agent ME said:**
> An attacker can just have the VNC server initiate the connect to his client.

That requires an attacker to gain access to the machine somehow, and since the default install of Ubuntu has no services listening on external interfaces, that would be difficult to do.

The problem is the way vino "configures the network automagically."

---

### Post by bodhi.zazen on 2010-09-03
> **I_Want_To_Learn said:**
> Hello

I'm looking to buy a wireless router around the $50 range with security being the top reason. Never used a router. Never went wireless. Don't care about getting the fastest wireless speeds or greatest range since I'll hardly enable wireless. Can you link me to some recommended articles and/or give me some advise on the best way to secure a wireless router?

So far I've gathered I should: 

-Enable WPA2-AES Personal & use very strong key.
-Enable NAT & SPI Firewall (Block all incoming & keep ports closed).
-Change router default username & password.

Not sure if I should do these since various articles give conflicting information:

-Disable SSDI Broadcast
-Disable DHCP
-Enable MAC Filtering

Also every router should be compatible since they use web-based interfaces, right? I wouldn't have a problem upgrading the firmware in Linux?

Thank You

IMO :

1. Use WPA

2. Turn wireless off when not in use.

The other measures, IMO, add little. IMO, if a cracker can break WPA , they are in.

The other option is to disable all security, allow your neighbors access, and consider your network insecure, meaning tunnel traffic over ssh and enable firewalls on all clients.

---

### Post by Agent ME on 2010-09-03
> **CharlesA said:**
> That requires an attacker to gain access to the machine somehow, and since the default install of Ubuntu has no services listening on external interfaces, that would be difficult to do.
The attacker needs to gain access to your machine in order to use UPnP. UPnP only listens for port forward requests inside the LAN, and will only approve port forward requests to the machine making the request.

---

### Post by CharlesA on 2010-09-03
> **Agent ME said:**
> The attacker needs to gain access to your machine in order to use UPnP. UPnP only listens for port forward requests inside the LAN, and will only approve port forward requests to the machine making the request.

Hence, why I mentioned vino.

---

