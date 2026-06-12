---
title: "Possible work from home coming up. What do I need?"
date: 2020-11-02
forum: Server Platforms
---

### Post by Tadaen_Sylvermane on 2020-11-02
My wife is looking to start working from home. She has been told they use Genesis for VoIP. I'm assuming they will do some type of setup but I'm thinking I'd like to do a custom router as I would like to load balance 2 wans using pf sense for more overall bandwidth + redundancy for her work. Thinking Ubuntu for the base with pf sense in a KVM virtual machine. Anyone have any suggestions, or experience to offer with this type of deployment? Can it be done with just Ubuntu and not a vm?

---

### Post by TheFu on 2020-11-03
WAN routers need to be on real, physical, hardware.  You know I LOVE, LOVE, LOVE, VMs and KVM in particular, but I'd never put a WAN router inside a VM. Too many security issues with the most likely network setup. If you use the typical bridge networking setup to share the NICs withother VMs inside the KVM setup, there are hacks where other VMs can see all the traffic.  

The idea to bond two internet connections is common, but unless the upstream ISPs support it (there is a specific protocol), it won't work.  The best you can do is to have failover or simply keep two LANs using each different ISP connection.

You can use Ubuntu as a router if you like.  I know people who do.  I use OPNSense for my WAN router on dedicated hardware and I use OPNSense inside a VM (KVM) to manage separate LANs inside the network.  Previously, I used pfSense, but decided to change when the last pfSense update forced a re-install anyway.  They are very similar.  I don't regret the change.

As for VoIP, I've had that at home since around 2004.  The main thing is to keep the latency and jitter low. I'd guess there's really nothing special about the VoIP setup these days. You can probably use any VoIP client that you like - software, hardware, etc. The trick is to get settings that work and translate those into the different devices you use. I'm not a fan of software-based VoIP solutions for primary needs because computers lock up all the time and people are so tempted to use WiFi internet connections.  Wifi is bad for latency and jitter of VoIP.

When I worked from home, I'd spend 6+ hrs a day on conference calls.  I miss my plantronics headset. The company provided it, so when I moved on, I returned it.  Too bad. I still miss that headset and they don't make it anymore. I just looked on Amazon. It is the type that uses tubes for the mic and ear, no foamy ear stuff and has an external amp. The sound quality from that thing was amazing while being comfortable for hours and hours of use.

---

### Post by Tadaen_Sylvermane on 2020-11-03
Ok. I will look into OPNSense then. I have no real purpose for the box other than a dedicated gateway as everything else is already handled on my server. Will have to check on bonding and that's it I guess. I'd like to use Ubuntu but I don't trust myself enough with iptables directly so a web gui is likely best for me.

*EDIT*

Since I really only need some type of failover would something like this be more appropriate? Simpler anyway. [https://www.pcquest.com/creating-failover-router/](https://www.pcquest.com/creating-failover-router/)
Older article but I'm guessing it would still apply.

---

### Post by TheFu on 2020-11-03
> **Tadaen_Sylvermane said:**
> Ok. I will look into OPNSense then. I have no real purpose for the box other than a dedicated gateway as everything else is already handled on my server. Will have to check on bonding and that's it I guess. I'd like to use Ubuntu but I don't trust myself enough with iptables directly so a web gui is likely best for me.

*EDIT*

Since I really only need some type of failover would something like this be more appropriate? Simpler anyway. [https://www.pcquest.com/creating-failover-router/](https://www.pcquest.com/creating-failover-router/)
Older article but I'm guessing it would still apply.

You can do failover with 1 or 2 routers. The routers need to support something like VRRP/CARP for the LAN connections and each desktop would need redundant ethernet connections - 1 for each router.  This is beyond what you probably want to setup.

For the WAN connection, I'd just have 2 cables and 2 ports assigned to the WAN ISPs.  Then use the routing metric number to change priorities. That's just 1 extra port used on the router and clients don't need any changes.

BSD doesn't use iptables and the pf firewall works on a completely different set of ideas.  pfsense and opnsense both have guides for redundant wan connections. Just follow one of those.

Stay wired Ethernet for the voip stuff.

---

### Post by Tadaen_Sylvermane on 2020-11-03
Ok. Will do. At the moment I'm still experimenting. It's looking like she will get the job, just trying to get figured out so I can jump on it as fast as possible if needed.

---

### Post by TheFu on 2020-11-03
pfSense/opnsense have special settings for VoIP if the PBX is external. Unfortunately, allowing those opens the network to some crafty attacks through javascript.  [https://www.theregister.com/2020/11/02/application_level_gateway_flaw/](https://www.theregister.com/2020/11/02/application_level_gateway_flaw/)

[LIST]
[*]Don't trust just the built-in javascript protections in any browser
[*]Only allow Javascript from sites you trust. Yes, this is a hassle.
[*]Only allow WebRTC when needed and always highly constrained. WebRTC is how most of those video conferencing and voice conferencing websites work.
[*]Use a different browser for daily use. Separate from webRTC needs.
[*]The WebRTC browser should be highly constrained, perhaps with a firejail sandbox and "private" overlay file system.
[/LIST]
For unknown parts of the internet, try using a browser that doesn't support any javascript capabilities at all.

I hate to say this, but for myself, I have 4 different browser launchers (actually more), depending on the security needs. I have no idea how to explain that to someone less technical. Perhaps simplify it to 2 different buttons instead of my 4+?  
[LIST=1]
[*]Safe stuff
[*]Not safe stuff and video conferencing
[/LIST]
IDK.

---

### Post by LHammonds on 2020-11-04
HINT: Any site on the Internet that pulls in 3rd-party ads = Never safe.   Hackers/Crackers LOVE marketing sites because if they can break into them, they can reach a large audience...thus if you trust sites like yahoo which are pulling in content from that marketing site, it gets safely delivered to you.

LHammonds

---

### Post by mastablasta on 2020-11-06
wow. i just took the work laptop home and the biggest issues were/are ergonomical ones.

got a 15 EUR "gaming" laptop stand with fans (i am not running them), put a pillow under my behind, so that back lines up better with kitchen chair. got a K120 logitech keyboard that i bought with discount and i already had headphones. wife spoils me with awesome food while i work, fridge with no suggar ice tea is close. i am good to go. 

the only thing i think might really need is better keyboard (at office as well). and i am dreaming for about 2 years about it. it's a process while i decide if i should really spend 120 EUR on a keyboard (that has better keys but the layout is not local) or not. maybe a better chair would also be good.

---

