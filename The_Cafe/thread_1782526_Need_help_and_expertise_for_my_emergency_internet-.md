---
title: "Need help and expertise for my emergency internet-in-a-box project! Critics welcome!"
date: 2011-06-14
forum: The Cafe
---

### Post by dizzysoul on 2011-06-14
Hello. I'm looking to develop a new technology for field deploying many internet nodes in an area and having them quickly interconnect to each other. I'm not looking to take a mesh networking approach, but rather something different. 

This project is going to develop a cheap and effective open-source solution for building and deploying a basic network infrastructure to provide internet access and basic networking tools in an emergency situation. The project will use as many cheap and on-the-shelf components as possible, simple assembly, and I'm looking to have the designs and software for the finished project released to the public for anyone to use. (like the RepRap project)

I've seen other projects developed with the same goal, and I have studied them, but I think I can offer a much better solution. 

I made this thread because I wanted to start a discussion on this project. 

I want people to ask me questions!
I want people to poke holes and point out flaws! 
I want people to offer suggestions, or even link articles to related projects!

I'm looking to get some expert opinions and advice on my idea. Critics and cynics are welcome here! I want to discuss what's practical, impractical, what works/doesn't work, what parts can be thrown out, elaborated on, and what can be improved. Please let me know what you think!

I'm 25 and I've been doing computer, low voltage and IT work for over 10 years. I've been interested in developing this system for humanitarian efforts because of disasters like Haiti and internet blackout situations like Egypt and Libya. Any and all advice is welcome, thank you!

> Smart Path Logic Internet Node for Tactical and Emergency Response (SPLINTER)

**Overview:**

SPLINTER is designed to be a fast, cheap, mass deploy-able internet-in-a-box. Each unit is equipped with dual-band WiFi, GPS, mobile broadband, dual-core computer, rechargeable battery and solar cell. Depending on the configuration, you can add disk storage, a satellite uplink, and more.

Each unit is designed to provide routing and internet access to existing infrastructure, or to nearby personal devices using its powerful built-in WiFi antennas. Each unit acts as a network node, using a second wireless channel to communicate and route traffic to other nearby units. With location-aware “Smart Path Logic” technology, each unit can build a geographical map of other units and use this information to trace efficient network routes across many different nodes, without using less effective brute-force methods and mesh networking protocols. 

Each unit also monitors the status of itself and other nearby nodes. Using a “push-pull” system, nodes can quickly relay changes to each other and across the network. This means the network is self-healing; being able to repair routes and adapt to constant changes in the network topography.

Each unit is equipped with a dual-core computer and a suite of network, internet and hosting software. This includes DNS, LAMP, POP/IMAP, SMB, CMS, and more. These services can be configured to activate dynamically based on the overall “health” of the network. If too many DNS servers go down, for example, other nodes can step in to pick up the workload, even if they are configured to do something else. Each unit comes with a limited amount of flash storage, with the option to add high capacity disk storage for web hosting and other media. 

The unit itself is rugged, shock proof and weather proof. It’s lightweight, and can be deployed via a number of methods, including airdrop. It contains a number of connection ports, including power, ethernet, and external antenna connectors. The box also contains basic indicators for battery level, signal strength, and network status. When not connected to external power, the box uses solar panels (and optional hand crank) to charge the internal battery. The unit can also carry additional extension poles and cables anchors (to be assembled on-site) allowing the unit to extend the antenna platform an additional 18 feet.

SPLINTER uses a simple, modular design to cut down on costs. Each unit is highly configurable to the needs of many different scenarios, from disaster relief, to nation building, to military applications. All software is Linux based; It can be audited and configured to meet specific security standards.

**How it works:**

Let's say you load 1,000 units into a squadron of aircraft, and you blanket a geographical area with these units (with a tight enough spread so they can interconnect, or some ground coordination to move units into optimal position) in order to build the initial network.

The units will behave as follows:

"Where am I?" - use it's GPS, and possibly other sensors, to find it's exact geographical location.
"Where are my friends?" - will broadcast it's location, and listen for other broadcasts, either using wifi or a more basic radio technology.
"Have you met any new friends?" - will consolidate a list of discovered units, and rebroadcast this list to nearby nodes. When a new unit is discovered, goes missing, or changes location, the list is updated and rebroadcast.

This basic logic will propagate very quickly, like a large game of marco-polo, until every units knows the geographical location of every other unit. This will create a realistic 'topography' of the entire network, realized by each and every device. When a change in the topography is detected, that change is "pushed" throughout the network using the above logic. Even if a "push" update is missed, units will periodically check-in with other nearby units, and "pull" any changes that result.

Each node will have a unique subnet, and when combined with the topography map, this means network traffic will have a *sense of direction*. It's like having a navigation system in each packet of data; It knows where to go, it knows which paths to take, and even if it makes a wrong turn, it knows how to recalculate the route. The overall network can also be optimized using a 'hierarchy' algorithm. Based on flow of traffic, signal strength, signal overlap, and other factors, certain nodes can be ranked higher than others. This will create multi-tiered node clusers, and even network "superhighways" to handle larger volumes of traffic.

In other words, the network will work to organize itself into a system that mirrors what we use today, the world wide web.

**Potential issues:**

WiFi isn’t strong enough to properly interconnect between units. Either the power will have to be dramatically increased, possibly beyond FCC specifications and power availability through solar energy. Another solution is to add directional and (possibly) motorized antennas to the antenna cluster. Directional antennas can have a range of many miles under low power conditions. This means the units might require some elevation, optional pole extensions, and some level of on-the-ground assembly.

The solar panels might be inefficient, or require expensive and exotic materials to meet the power demands of the router equipment and computer. One solution is to limit transmission power, network bandwidth and processing power to conserve battery, but this would make it more difficult to interconnect nodes and host media (such as video and audio).

**Other features:**

The optional hand crank will use a large gear ratio to maximize the charging of the dynamo. The hand crank will be robust and detachable so that any kind of mechanism can spin the crankshaft.

All of the components inside of each unit are recyclable and can be salvaged or re purposed for other tasks. The computer and networking equipment can be flashed and programmed to serve other functions. The solar panels, dynamo, and battery will not be wired in-line with the power circuit, and can be removed as long as the unit is plugged into an external power source, much like how you can remove a laptop battery after it's plugged in.

---

### Post by Copper Bezel on 2011-06-14
So, like [_this_]("http://www.nytimes.com/2011/06/12/world/12internet.html?_r=2&pagewanted=1")?

I'm not certain that I understand the purpose of your post. Are you saying that you want ideas on how to start a business making these?

---

### Post by drawkcab on 2011-06-14
> **Copper Bezel said:**
> So, like [_this_]("http://www.nytimes.com/2011/06/12/world/12internet.html?_r=2&pagewanted=1")?

I'm not certain that I understand the purpose of your post. Are you saying that you want ideas on how to start a business making these?

I was gunna say that someone's already on this. ^^^

---

### Post by ki4jgt on 2011-06-14
> **dizzysoul said:**
> Hello. I'm looking to develop a new technology for field deploying many internet nodes in an area and having them quickly interconnect to each other. I'm not looking to take a mesh networking approach, but rather something different. 

This project is going to develop a cheap and effective open-source solution for building and deploying a basic network infrastructure to provide internet access and basic networking tools in an emergency situation. The project will use as many cheap and on-the-shelf components as possible, simple assembly, and I'm looking to have the designs and software for the finished project released to the public for anyone to use. (like the RepRap project)

I've seen other projects developed with the same goal, and I have studied them, but I think I can offer a much better solution. 

I'm looking to get some expert opinions and advice on my idea. Critics and cynics welcome! I want to discuss what's practical, impractical, what works/doesn't work, and what can be improved. 

I'm 25 and I've been doing computer, low voltage and IT work for over 10 years. I've been interested in developing this system for humanitarian efforts because of disasters like Haiti and internet blackout situations like Egypt and Libya. Any and all advice is welcome, thank you!

The amateur radio community has already accomplished this. Look into D-STAR radios and then read about a program for them called RATS-D (I think)

---

### Post by ki4jgt on 2011-06-14
Sorry, the program is called D-RATS and the WinLink gateway is what amateurs use to send email while they're in the middle of the ocean. So, yeah as long as your local radio club has D-STAR radios, they should have the capability to send and receive computer data. (including Internet) but according to regulations, they just can't encrypt ANYTHING so you won't be able to check your email, just browse the web.

---

### Post by dizzysoul on 2011-06-15
> **Copper Bezel said:**
> So, like [_this_]("http://www.nytimes.com/2011/06/12/world/12internet.html?_r=2&pagewanted=1")?


Quoted from the article:

> The group&#8217;s suitcase project will rely on a version of &#8220;mesh network&#8221; technology, which can transform devices like cellphones or personal computers to create an invisible wireless web without a centralized hub. In other words, a voice, picture or e-mail message could hop directly between the modified wireless devices &#8212; each one acting as a mini cell &#8220;tower&#8221; and phone &#8212; and bypass the official network.

Mr. Meinrath said that the suitcase would include small wireless antennas, which could increase the area of coverage; a laptop to administer the system; thumb drives and CDs to spread the software to more devices and encrypt the communications; and other components like Ethernet cables.

Their so-called "suitcase" is an attempt to, not only use a mesh network (which has many different scaling problems), but a network incorporating all sorts of different (likely antiquated) hardware. I don't think its even going to work, and even if they figured out some way to do it, it would be widely inefficient and unreliable. The whole thing would not work very well, if at all.

The other problem, is that this suitcase has a very limited scope of what it can do, which is creating a small, unrestricted intranet for a small cluster of people. It still requires the use of existing devices, and those devices still require existing power and network infrastructure.

The system I'm trying to design will use GPS to create location-aware network nodes that can actually map the most efficient routes between points, and will use powerful and robust hardware. The network will be able to heal itself if nodes are moved or disconnected, but overall the nodes will have a static location, allowing for greater reliability and throughput in the network.

You NEED some sort of location-aware system for a large scale mesh network, or else it's akin to telling a bunch of blind people to mingle in an airline hangar and pass messages from one end to the other. The only solution is a brute-force method which is highly impractical.

> I'm not certain that I understand the purpose of your post. Are you saying that you want ideas on how to start a business making these?

I wanted people to ask questions, poke holes and point out flaws, offer suggestions, or even link articles to related projects (like you did, thank you!). I'll update my original post to make this more clear.

---

### Post by Copper Bezel on 2011-06-15
Yeah, the "mesh network" sounds a lot like that OLPC project, so I know it's not new technology - I guess I'm trying to suss out what the difference is between that and what you're proposing. I'd assumed that a mesh network would prioritize on signal strength the way WiFi tries (and generally fails) to do. How would this location-aware system differ? 

And incidentally, what *is* the difference between either project and a mass ad-hoc network like the OLPC project used? (I mean, aside from the high-range directional antennae and the assumption that someone has a 3G connection somewhere in the network?)

---

### Post by dizzysoul on 2011-06-15
> **Copper Bezel said:**
> Yeah, the "mesh network" sounds a lot like that OLPC project, so I know it's not new technology - I guess I'm trying to suss out what the difference is between that and what you're proposing. I'd assumed that a mesh network would prioritize on signal strength the way WiFi tries (and generally fails) to do. How would this location-aware system differ? 

And incidentally, what *is* the difference between either project and a mass ad-hoc network like the OLPC project used? (I mean, aside from the high-range directional antennae and the assumption that someone has a 3G connection somewhere in the network?)

Good question! I went ahead and updated my post with new info!

**How it works:**

Let's say you load 1,000 units into a squadron of aircraft, and you blanket a geographical area with these units (with a tight enough spread so they can interconnect, or some ground coordination to move units into optimal position) in order to build the initial network.

The units will behave as follows:

"Where am I?" - use it's GPS, and possibly other sensors, to find it's exact geographical location.
"Where are my friends?" - will broadcast it's location, and listen for other broadcasts, either using wifi or a more basic radio technology.
"Have you met any new friends?" - will consolidate a list of discovered units, and rebroadcast this list to nearby nodes. When a new unit is discovered, goes missing, or changes location, the list is updated and rebroadcast.

This basic logic will propagate very quickly, like a large game of marco-polo, until every units knows the geographical location of every other unit. This will create a realistic 'topography' of the entire network, realized by each and every device. When a change in the topography is detected, that change is "pushed" throughout the network using the above logic. Even if a "push" update is missed, units will periodically check-in with other nearby units, and "pull" any changes that result.

Each node will have a unique subnet, and when combined with the topography map, this means network traffic will have a *sense of direction*. It's like having a navigation system in each packet of data; It knows where to go, it knows which paths to take, and even if it makes a wrong turn, it knows how to recalculate the route. The overall network can also be optimized using a 'hierarchy' algorithm. Based on flow of traffic, signal strength, signal overlap, and other factors, certain nodes can be ranked higher than others. This will create multi-tiered node clusers, and even network "superhighways" to handle larger volumes of traffic.

In other words, the network will work to organize itself into a system that mirrors what we use today, the world wide web.

I guess you could say that, physically, it's a mesh network, in the sense that's there's many nodes interconnected to each other. And in the beginning, it will partially behave like a mesh network, as the topography map is being built. However the system will work to build and reorganize itself in a more traditional way. The nodes will not have pseudo-locations, but physical, static ones. Data packets will take a direct route, and have a sense of direction, instead of being brute-forced across the network or constantly re-routed to find its destination. The network will develop into a tiered structure, and not all nodes will be created equal. Personal devices will connect through a node for access, and will not participate as a node themselves.

---

### Post by dizzysoul on 2011-06-15
> **ki4jgt said:**
> Sorry, the program is called D-RATS and the WinLink gateway is what amateurs use to send email while they're in the middle of the ocean. So, yeah as long as your local radio club has D-STAR radios, they should have the capability to send and receive computer data. (including Internet) but according to regulations, they just can't encrypt ANYTHING so you won't be able to check your email, just browse the web.

I've been reading up on D-RATS, and it sounds fascinating! Information is limited, but I'm assuming it uses a more powerful RF spectrum (for emergency communications) to transmit data like a mobile cell tower?

I found some good information [here.]("http://www.icomamerica.com/en/products/amateur/dstar/dstar/DRATSBrochure.pdf") (PDF file)

There some things I can't find information on. For example, what is the bandwidth? What is the range? How much power does it take to transmit that range? Can it transmit normal TCP traffic? What about different (http, ftp, pop/imap) protocols?

The part about encryption not being allowed is a problem as well. However, in an emergency situation (especially overseas), I think the FCC rules are flexible.

---

### Post by Dustin2128 on 2011-06-15
> **ki4jgt said:**
> Sorry, the program is called D-RATS and the WinLink gateway is what amateurs use to send email while they're in the middle of the ocean. So, yeah as long as your local radio club has D-STAR radios, they should have the capability to send and receive computer data. (including Internet) but according to regulations, they just can't encrypt ANYTHING so you won't be able to check your email, just browse the web.

Bit off topic, but why aren't you allowed to use cryptography with packet radio? I'm guessing that's an older regulation? Cause it doesn't make much sense now with so much traffic being encrypted by default, not to mention wifi network encryption. Why should one frequency be different than another?

---

### Post by dizzysoul on 2011-06-18
The biggest technology hurdle with this project is the WiFi connectivity. According to various sources (such as Hawking Technology), I can expect up to 2 miles radius with a 15db omni-directional antenna in perfect conditions.

Since the 15db isn't achieved using full power, I can boost the antenna gain to 4 watts (maximum FCC allowance for 2.4ghz spectrum) to guarantee a mile-range connectivity. If parabolic or directional antennas were to be used, a distance of 20 miles could easily be achieved.

I'm looking into the possibility of using WiMax technology, since it has the signal strength of 3G cellular technology, while using packet delivery similar to WiFi.

The unit itself should be no bigger than a netbook in size. In fact, this unit would be something similar to a stripped-down netbook, with dual-band wireless adapters, GPS, WWAN, battery, etc. (minus screen, keyboard, etc.) in a rugged case with solar panels and dynamo.

WiMax is a new technology, and I've made some inquiries to a few companies that supply WiMax equipment about the cost and viability. If anyone has any other suggestions, or would like to offer me any ideas, or simply tell me why this concept ins't practical or wouldn't work, I'd like to hear it!

---

### Post by mips on 2011-06-19
> **dizzysoul said:**
> ...(maximum **FCC** allowance for 2.4ghz spectrum)

Other countries feel squat for the FCC and usually have their own regulations, something to keep in mind when outside US borders.

I don't think wifi is the way to go, you would require to many units to 'carpet' an area and then it's also finicky.

I was looking a Wimax pricing a while ago and it's very expensive compared to wifi.

---

### Post by tekoholix on 2011-12-10
Is there any status on this project / idea?  I'd be interested in testing for you...

Currently, I'm using openwrt routers and batman-adv to mesh 3 nodes.  I'm attempting to get it working with Ubuntu as well, so that all our netbooks and vehicle PC's can become nodes as well, instead of just clients...

I am a Ham Radio operator, so I can offer SOME advice in that regard:  Don't use it in this fashion, except in an ACTUAL emergency.  It won't be legal in nearly ANY nation's borders (AFAIK), due to the fact that UN-licensed users' traffic would be passed over licensed freq's.  There are other reasons as well, but this is one of the main ones.  I'd suggest staying radio-agnostic with software, permitting ANY radio hardware to be attached / installed, dependent upon the users' environment, needs, licensing status, etc...

---

### Post by dizzysoul on 2012-02-01
> **tekoholix said:**
> Is there any status on this project / idea?  I'd be interested in testing for you...

Currently, I'm using openwrt routers and batman-adv to mesh 3 nodes.  I'm attempting to get it working with Ubuntu as well, so that all our netbooks and vehicle PC's can become nodes as well, instead of just clients...

I am a Ham Radio operator, so I can offer SOME advice in that regard:  Don't use it in this fashion, except in an ACTUAL emergency.  It won't be legal in nearly ANY nation's borders (AFAIK), due to the fact that UN-licensed users' traffic would be passed over licensed freq's.  There are other reasons as well, but this is one of the main ones.  I'd suggest staying radio-agnostic with software, permitting ANY radio hardware to be attached / installed, dependent upon the users' environment, needs, licensing status, etc...

I didn't know somebody had replied to this thread recently! I thought it died. :-)

A lot of this stuff is being fleshed out and developed over at reddit.com/r/darknetplan. The recent brouhaha over SOPA/PIPA/OPEN/ACTA/etc. has accelerated a lot of interest in ways to protect the internet and the free flow of information.

---

