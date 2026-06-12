---
title: "internet services - i'm curious"
date: 2020-02-23
forum: The Cafe
---

### Post by Skaperen on 2020-02-23
i'm curious ... how many members and other people you know have internet service from *TWO* or more internet providers.

---

### Post by EuclideanCoffee on 2020-02-23
I get Internet from my phone company and my ISP, Internet Service Provider.

---

### Post by SeijiSensei on 2020-02-23
Smartphones provide a second Internet channel for millions of people. My service permits the phone to be used as a wifi access point. It's come in handy a few times when my main service had an outage.

---

### Post by him610 on 2020-02-23
> Smartphones provide a second Internet channel
Yes, that is my situation also.

---

### Post by TheFu on 2020-02-23
> **Skaperen said:**
> i'm curious ... how many members and other people you know have internet service from *TWO* or more internet providers.

Pretty common.  Home ISP and whatever cell data plan they have.  Both will fail after 4-12 hrs during region-wide disasters. Heck, my cable ISP can't handle a 2 min power outage without needing to reboot their equipment.  I have UPS equipment and handle 45+ min outages ... but the internet goes down.

More serious nerds or people with home businesses might get 2 business ISPs at home.  I know about 10 people with a dual business ISP setup. They have the router setup to prefer 1, but failover to the other. Most of these guys work in telecom infrastruture and networking.  The extra $150/month to not be disconnected is a minor business expense.

---

### Post by Skaperen on 2020-02-25
in that setup with a smartphone (or any other setup), can a desktop or laptop running some Ubuntu route one internet address/network through one ISP and route another internet address/network through the other ISP, concurrently?

what does it take to have a smartphone do that?  an app?  some routing/network commands?  i'm assuming it uses the wifi hardware in the phone as an access point.  if you do that with masquerading enabled can the phone company see that more than just the phone is using the internet?

---

### Post by Shibblet on 2020-02-25
Are you talking like home internet, and cell phone internet?

---

### Post by Skaperen on 2020-02-25
i'm talking about the kind of services referred to in posts #2 through #5 whether being used at home or in a small business or office.

---

### Post by mastablasta on 2020-02-26
work ISP
the company smartphone (different ISP)
home ISP

i don't own a smartphone myself, otherwise i might have 4 ISPs.

---

### Post by Skaperen on 2020-02-27
i'm interested in cases where 2 or more ISPs are in close enough proximity that a single computer can be connected to both of them by some means, such as distinct gateway routers on the LAN that computer is connected to, or separate wifi access points where support exists to use both at the same time as different logical interfaces over one wifi interface (the local wifi card would be channel or band flipping), or the like over ad-hoc, or possibly including tunnels, or multiple physical interfaces.  as long as that computer can control which CIDR-identified subnets go through which ISP (possibly by remote routing commands/tables).

---

### Post by Skaperen on 2020-03-09
the reason i am curious is that i wonder if anyone is combining multiple providers to increase internet performance and/or have a quick fallback in case of an outage in one of the providers.  i think i have come up with a way to do that in a situation where a Linux/BSD/Unix host can decide which ISP to send to different destination addresses.  i am wondering if this is already done or if i should proceed to develop it.

---

### Post by SeijiSensei on 2020-03-10
Isn't that handled by the "metric" keyword in routing statements?  You can have both networks connected simultaneously with different metrics.  Then if the primary connection dies, the router will use the next alternative.

I'm using a laptop with a wired connection.  My routing table looks like this:
```

$ ip route list
default via 192.168.100.1 dev eno1 proto dhcp metric 100 
default via 192.168.100.1 dev wlo1 proto dhcp metric 600 
169.254.0.0/16 dev eno1 scope link metric 1000 
192.168.100.0/24 dev eno1 proto kernel scope link src 192.168.100.53 metric 100 
192.168.100.0/24 dev wlo1 proto kernel scope link src 192.168.100.109 metric 600 

```
So here my laptop is using the wired connection on eno1 because it has the lowest metric.  Were I to disconnect the computer from the wired network, it would switch to using the wifi connection via wlo1.

(This is the default on Kubuntu 20.04.  I didn't do anything to set this up.)

---

### Post by TheFu on 2020-03-10
ISP failover is handled by routers already.  Just need to get a router that can connect to multiple WAN connections.  

Any pfSense/OpnSense install can do this assuming there are sufficient ethernet ports or room for a data card inside the device should wireless data be desired.  The router handles any failover between ISPs.  This is very common outside a home environment.

These are not expensive devices.

---

### Post by Skaperen on 2020-03-11
> **TheFu said:**
> ISP failover is handled by routers already.  Just need to get a router that can connect to multiple WAN connections.  

Any pfSense/OpnSense install can do this assuming there are sufficient ethernet ports or room for a data card inside the device should wireless data be desired.  The router handles any failover between ISPs.  This is very common outside a home environment.

These are not expensive devices.

can routers also merge the 2 bandwidths into 1 larger one?  how fast will they respond to upstream packet loss?  what if an ISP is having 50% packet loss?

---

### Post by Skaperen on 2020-03-11
> **SeijiSensei said:**
> Isn't that handled by the "metric" keyword in routing statements?  You can have both networks connected simultaneously with different metrics.  Then if the primary connection dies, the router will use the next alternative.

I'm using a laptop with a wired connection.  My routing table looks like this:
```

$ ip route list
default via 192.168.100.1 dev eno1 proto dhcp metric 100 
default via 192.168.100.1 dev wlo1 proto dhcp metric 600 
169.254.0.0/16 dev eno1 scope link metric 1000 
192.168.100.0/24 dev eno1 proto kernel scope link src 192.168.100.53 metric 100 
192.168.100.0/24 dev wlo1 proto kernel scope link src 192.168.100.109 metric 600 

```
So here my laptop is using the wired connection on eno1 because it has the lowest metric.  Were I to disconnect the computer from the wired network, it would switch to using the wifi connection via wlo1.

(This is the default on Kubuntu 20.04.  I didn't do anything to set this up.)

how does your system handle a "brief" (or longer) packet loss outage by the ISP's upstream provider where the local connections stay up?l

---

### Post by SeijiSensei on 2020-03-11
I'm talking about a desktop computer here.  Upstream I have just one provider, but the desktop machine can get to the router two different ways.  So I can't really answer your question.

---

### Post by Skaperen on 2020-03-11
if you did have 2 ISPs and you had either separate interfaces for each ISP or could set routing on a router to make certain IP addresses go via ISP 1 and certain other addresses go via ISP 2, then you probably have the means to use what i have dreamed up.  it might need to change any routes at startup or at other times, including on the machine itself if the ISPs are separate interfaces.

the technique is to run what will look like 2 VPNs in a cloud provider, operating as a single VPN.  a process at each end will filter packets selecting which ISP(s) each will go through.  received packets will be recombined for the single instance of OpenVPN at each end.  so your outgoing traffic can spread out over 2 or more ISPs and still go to addressed internet sites all with a single IP address (so you can have the bandwidth of multiple ISPs and be "from" a single IP address suitable for TCP connections and SCTP sessions.

---

