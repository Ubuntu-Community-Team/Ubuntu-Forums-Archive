---
title: "LAN on a town?"
date: 2013-01-02
forum: The Cafe
---

### Post by 3v3rgr33n on 2013-01-02
Hi

I understand that a LAN is a way of connecting pc's. sending data to and from without the internet.

I was just thinking, is possible to create a local access network for a small town. Area of about 34,74 sq. kilo metres (14.57 sq. miles). Population of about 8651. The stats are from Wikipedia, dated back to 2001.

I'm trying to focus on WLAN by the way.

Regards

---

### Post by haqking on 2013-01-02
> **3v3rgr33n said:**
> Hi

I understand that a LAN is a way of connecting pc's. sending data to and from without the internet.

I was just thinking, is possible to create a local access network for a small town. Area of about 34,74 sq. kilo metres (14.57 sq. miles). Population of about 8651. The stats are from Wikipedia, dated back to 2001.

I'm trying to focus on WLAN by the way.

Regards

Actually a LAN (Local Area Network) does not involve the Internet, a LAN can have access to the Internet, but i think you mean a WAN (Wide Area Network)

There is also a MAN (Metropolitan Area Network) and a CAN (Campus Area Network) and a few more.

See here for a MAN which is what you are after I believe [https://en.wikipedia.org/wiki/Metropolitan_area_network](https://en.wikipedia.org/wiki/Metropolitan_area_network)

And yes you can create Network for 1 user or 2 users, or 2000, or 2 billion or the World, it is all about TCP/IP, routers, switches, and know how.

Do you have a specific question relating to configuration ?

Peace

---

### Post by lykwydchykyn on 2013-01-02
Sure.  Some corporate and government networks are at least that size.

---

### Post by Calinou on 2013-01-02
You want to use a VPN (Virtual Private Network), no?

---

### Post by haqking on 2013-01-02
> **Calinou said:**
> You want to use a VPN (Virtual Private Network), no?

What has a VPN got to do with a city LAN/MAN ?

---

### Post by 3v3rgr33n on 2013-01-03
> **haqking said:**
> Actually a LAN (Local Area Network) does not involve the Internet, a LAN can have access to the Internet, but i think you mean a WAN (Wide Area Network)

There is also a MAN (Metropolitan Area Network) and a CAN (Campus Area Network) and a few more...


What you're speaking about seems to be what I need. I'm trying to build a system for a certain town. It's basically a way for the locals to distribute their material such as own produced music, software projects, school work for the kids,etc.

I was thinking of doing it through a central website of some sorts. I want it to be available to all people in the area, freely -- without data costs.

I'm a Java developer, I'm totally new to network and web related stuff. What's the best way to go about doing this?

---

### Post by Transhumanist on 2013-01-03
The best way to build a "LAN for a town" is to skip the existing infrastructure methods and just start from the outset with the goal of building a mesh network.

Mesh networks are far more resistant to things like damage, censorship, monopolistic behaviour, government intervention, snooping, etc, than the existing internetwork structures. Also, infrastructure costs are distributed amongst the nodes themselves, rather than users paying a fee to an ISP to connect to the network.

More here: [http://en.wikipedia.org/wiki/Mesh_networking](http://en.wikipedia.org/wiki/Mesh_networking)
And here: [http://en.wikipedia.org/wiki/Wireless_mesh_network](http://en.wikipedia.org/wiki/Wireless_mesh_network)

I would suggest looking at projects like Byzantium and the cjdns protocol.

Plenty of community/neighbourhood mesh networks have already been established, especially in Europe. Worth digging around to see how they've done things.

---

### Post by grahammechanical on 2013-01-03
> I was thinking of doing it through a central website of some sorts. I want it to be available to all people in the area, freely -- without data costs.

This sounds like you need to be an Internet Service Provider. Where I live we use existing telephone cables to connect to the Wide Area Network that is called the Internet. I have to pay monthly for my connection to the telephone network and then pay an Internet Service Provider to make connections to other computers.

Do the people in your town that you want to help have a connection to the telephone network? Can they afford to pay for a connection? Do you have the money to set up a cable network throughout the town?

It might be more practical to set up a shop or a market stall where people can come and buy/sell/excange.

Regards.

---

### Post by 3v3rgr33n on 2013-01-03
> **grahammechanical said:**
> This sounds like you need to be an Internet Service Provider. Where I live we use existing telephone cables to connect to the Wide Area Network that is called the Internet. I have to pay monthly for my connection to the telephone network and then pay an Internet Service Provider to make connections to other computers...

To be honest with you, if they have to pay to access what I'm offering---it's highly unlikely that they will care abt it. I'm also hoping that they won't need to 'coz otherwise I could just build a website and let people upload their stuff on it : in that case I won't need to build a network.

> **Transhumanist said:**
> The best way to build a "LAN for a town" is to skip the existing infrastructure methods and just start from the outset with the goal of building a mesh network.

Mesh networks are far more resistant to things like damage, censorship, monopolistic behaviour, government intervention, snooping, etc, than the existing internetwork structures. Also, infrastructure costs are distributed amongst the nodes themselves, rather than users paying a fee to an ISP to connect to the network.

More here: [http://en.wikipedia.org/wiki/Mesh_networking](http://en.wikipedia.org/wiki/Mesh_networking)
And here: [http://en.wikipedia.org/wiki/Wireless_mesh_network](http://en.wikipedia.org/wiki/Wireless_mesh_network)

I would suggest looking at projects like Byzantium and the cjdns protocol.

Plenty of community/neighbourhood mesh networks have already been established, especially in Europe. Worth digging around to see how they've done things.

I'll look into this as soon as possible. I'll get back to you if there is some confusion.

---

### Post by tgalati4 on 2013-01-03
Buy a 24-port ethernet switch and find a power source.  Then wire up your community with 24 wires (up to 100 meters).  At the end of those wires, put up some extender/repeaters to go another 100 meters.  The 24-port switch should be centrally located with consistent power.  Once the switch is installed the network will grow very quickly.  To cover more ground, you need to connect a fiber optic bridge between routers.  They can go for a few miles.  

Post a simplified map of the layout of the town and where your power is located.  That would be the quickest way to get suggestions for the best network topology.

---

### Post by audiomick on 2013-01-03
> **3v3rgr33n said:**
> 

I'm trying to focus on WLAN by the way.



Don't forget that radio, and WLAN is radio, is not magic. Your coverage depends directly on line of sight obstacles and transmitting power. The laws governing radio transmitters, and where WLAN lives in the great scheme of things, means you are not likely to get more than a couple of hundred metres in the very best of circumstances. What might work is WLAN access points in specific locations (cafes, clubs, whatever) that are networked together where people can come and log in (in a nice social atmosphere, and actually talk to each other about the music content they are sharing... ;) )

---

### Post by 3v3rgr33n on 2013-01-03
> **tgalati4 said:**
> Buy a 24-port ethernet switch and find a power source.  Then wire up your community with 24 wires (up to 100 meters).  At the end of those wires, put up some extender/repeaters to go another 100 meters.  The 24-port switch should be centrally located with consistent power.  Once the switch is installed the network will grow very quickly.  To cover more ground, you need to connect a fiber optic bridge between routers...
Thanx for the suggestion but I think I'll go with the Wireless mesh network idea.


> **audiomick said:**
> Don't forget that radio, and WLAN is radio, is not magic. Your coverage depends directly on line of sight obstacles and transmitting power. The laws governing radio transmitters, and where WLAN lives in the great scheme of things, means you are not likely to get more than a couple of hundred metres in the very best of circumstances. What might work is WLAN access points in specific locations (cafes, clubs, whatever) that are networked together where people can come and log in (in a nice social atmosphere, and actually talk to each other about the music content they are sharing... ;) )

You are not the first one to suggest that but I want people to able to access what I'm giving them from the comfort of their own homes. Isn't this wireless mesh network thingie better ?

---

### Post by chadk5utc on 2013-01-03
suggested google: WISP topology, MESH networking, there is some free firmware for this depending on what devices are available where your at. Their is also mapping software available to help map out the network for your area but youll have to search the net to find it, its been so long I no longer have any of it nor do I remember the name of it. This is quite a project, it can be done but will require much effort and planning not to mention some cost involved.

---

### Post by audiomick on 2013-01-03
> **3v3rgr33n said:**
>  Isn't this wireless mesh network thingie better ?

That looks interesting, although I really don't know much about it. Coverage is still the question. You either need a few transmitters that cover larger areas, or lots of transmitters that each do a small bit.

Whether you can use a few powerful ones is first and foremost dictated by the radio laws in your country, and then by the technology that is available for the task, and then by your budget.

Whether you can use lots of less powerful ones is dictated by the available technology, whether you can afford them, and if you can get places to set them up (which may come under the budget heading).

I don't want to discourage you, but remember that wireless has very definite physical limits.

---

### Post by DuckHook on 2013-01-03
> **Transhumanist said:**
> I would suggest looking at projects like Byzantium and the cjdns protocol.

Wonderful and fascinating project. I'd heard about mesh networking in some Euro communities, but this is the first FOSS mesh network project that I've been made aware of. The rest seem to be proprietary solutions.

I echo the other commentators who point out that this is a very involved and technically challenging project requiring a geek rating that is well off the charts of absolute beginners. Not that I'm complaining. This thread drift was totally unanticipated and the OP's post was quite valid. Glad that it exposed me to such a cool new area of FOSS-space.

I am curious though: is anyone aware of an established community, Euro or elsewhere, that has a demonstrably working and stable mesh network? Would love to see one in action. This seems to be one of those projects where old and otherwise obsolete equipment can be reclaimed for really cool uses. An old laptop coupled to an old wireless router (along with the right software) would seem to be all that's needed.

---

### Post by DuckHook on 2013-01-03
> **audiomick said:**
> ...you are not likely to get more than a couple of hundred metres in the very best of circumstances. What might work is WLAN access points in specific locations (cafes, clubs, whatever) that are networked together where people can come and log in (in a nice social atmosphere, and actually talk to each other about the music content they are sharing... ;) )

The sad irony is that it would work exceptionally well in average suburbia where house WIFIs problematically overlap anyway, but given the anti-communal prejudices here in North Am, I'm pretty sure that most users would decline to participate in any such project. To be fair, I would have to have solid reassurances for my privacy and security concerns too, but at least the idea is appealing. Imagine a competing network to the monopolies/oligopolies that constitute our current ISPs? The principle of network neutrality would have far better clout and protection if such an alternative were real and not just theoretical.

Man. Gotta stop tiltin' at them thar' windmills.:rolleyes:

---

### Post by chadk5utc on 2013-01-03
Heres a good link for anyone interested which gives some cost break down for such a project.
[http://forum.ubnt.com/attachment.php?attachmentid=13129&d=1349561141](http://forum.ubnt.com/attachment.php?attachmentid=13129&d=1349561141)
And also a forum for the same although they do assume you know what your doing.

---

### Post by 3v3rgr33n on 2013-01-03
Just looked at project Byzantium. WOW!

I still need to do a bit of digging. I think I can do this though. Thnx guys for your help.

---

### Post by mastablasta on 2013-01-04
awesome project. if you manage to complete this you have to post back with some usage data, costs. pictures and also what you had to go through to get it done...

---

### Post by Transhumanist on 2013-01-05
Yeah, this will be a big project. I'd love to setup a mesh in my own town, but it's quite an undertaking. But then, so is setting up a classical centralised network topology on such a scale.

You could try joining the #byzantium IRC channel on freenode, btw. The guys there might be able to give you hints and to point you in the right direction. One of the project founders mentioned on there at one point that a local makerspace in Finnland was convincing an ISP to use mesh networking to wire up a new town, to save on infrastructure costs. Apparently the talks had progressed quite far.

One of the goals of Byzantium is to be able to put a Byzantium live CD or USB in a computer with a wireless card, and then use that wireless card to broadcast as a node in a mesh network.

Here is a link to a rather excellent presentation by the Byzantium guys outlining their aims. I found it a nice introduction: [http://project-byzantium.org/presentations/HOPE_Byzantium_Presentation.pdf](http://project-byzantium.org/presentations/HOPE_Byzantium_Presentation.pdf)

I've heard that once certain requirements are met, they'll incorporate cjdns into Byzantium.

But both cjdns and Byzantium are alpha. They didn't exist 2 years ago. That gives you a feel for how new this area of technology is. The concept is old, the (attempt at) implementation in a robust, simple, standardised way is new.

I am currently running cjdns on a VPS as well as this current computer. It's a fascinating protocol. It is agnostic to the type of node you use. For instance, you can run cjdns over UDP on top of the existing Internet for encrypted communications, or you can run it over a physical mesh. And both types of nodes can be part of the same network. This makes the transition from the Internet to a mesh network a lot simpler, because you don't have to ditch the Internet to use mesh networking. Indeed you don't even need to ditch the Internet at all to take advantage of mesh networking - but it's probably a good idea. The Internet has not aged well in a world of censorship, espionage, natural disasters, and telecommunications company monopolies.

 The internetwork that is the equivalent of the Internet under cjdns is called Hyperboria. There's even a Hyperboria-only IRC server for it, as well as a bunch of Hyperboria-only websites.

cjdns aims to use local peer autodetection, too, similar to DHT. There's a git repository for it which you can look at. In fact, when installing it (just a few terminal commands - nothing too hard), you have to first pull the current source from git and run its make command.

More here: [http://cjdns.info/](http://cjdns.info/)

---

### Post by Transhumanist on 2013-01-05
Following on from the previous post (which mainly discussed cjdns and Byzantium): 

Here is a slightly old (one year) compilation of mesh networking links, including a list of communities using it: [http://emergentbydesign.com/2011/02/11/16-projects-initiatives-building-ad-hoc-wireless-mesh-networks/](http://emergentbydesign.com/2011/02/11/16-projects-initiatives-building-ad-hoc-wireless-mesh-networks/)

It's worth noting that the One Laptop Per Child project built its laptops so that they automatically mesh networked with eachother.

Serval is also an Australian project with some funding from Mark Shuttleworth which uses mesh networking to make phones calls between phones but WITHOUT centralised infrastructure like telecoms companies. Serval is also alpha, but it's also FOSS.

Serval: [http://www.servalproject.org/](http://www.servalproject.org/)

There is an ALPHA Serval app in the Google Play store. Don't expect much yet, but it's there for testing if you'd like.

Well, I hope I've inspired a few people to give mesh networking a serious look, and maybe even try and contribute to existing projects in some way. =)

---

### Post by 3v3rgr33n on 2013-01-05
These projects are amazing but is it possible to find out how these people are building these wireless mesh networks. I like the fact people there are many projects out there.

I need to find out their implementations so that I can compare them in terms of which is faster and which is inexpensive.

I also need to build a wireless mesh network by June.

---

### Post by tgalati4 on 2013-01-05
Good, Fast, Cheap.  Choose two.

---

### Post by DuckHook on 2013-01-05
> **tgalati4 said:**
> Good, Fast, Cheap.  Choose two.

You beat me to it...

---

### Post by tgalati4 on 2013-01-05
Somehow I think this wireless mesh is going to look like a MayPole of wires coming from one building.

---

### Post by Transhumanist on 2013-01-05
> **3v3rgr33n said:**
> These projects are amazing but is it possible to find out how these people are building these wireless mesh networks. I like the fact people there are many projects out there.

I need to find out their implementations so that I can compare them in terms of which is faster and which is inexpensive.

I also need to build a wireless mesh network by June.

As the others said: good, cheap, fast. Choose two.

I don't know of any network topology you can do in that time-frame. Wireless won't work unless it's a mesh network, because you'd basically need a huge broadcast tower, or lots of repeater nodes (in which case, why not just do mesh?).

And laying cables in that timeframe does not sound plausible. Or cheap.

I admire your enthusiasm, but it's a daunting task.

What are your specifics? How many people will connect to your network? What distance will they be from eachother? Are they willing to participate in the mesh network or are they non-techies? Are they willing to fund the network or is it all on you? What's your budget?

---

### Post by tartalo on 2013-01-05
I recently came across this project: [http://www.guifi.net/en/](http://www.guifi.net/en/)

It's an already working network, so they probably have already solved some of the challenges you will meet, their documentation it's mostly written in Catalan and Spanish, but given the open nature of the project I guess that you could approach them directly with punctual doubts.

---

### Post by 3v3rgr33n on 2013-01-06
> What are your specifics? How many people will connect to your network?  What distance will they be from eachother? Are they willing to  participate in the mesh network or are they non-techies? Are they  willing to fund the network or is it all on you? What's your budget?

The number of people is about 9000. No one is willing to fund the network yet --- I've approached a couple of government youth organizations though. They seem keen on the idea but their main concern however is makin' money off the network.

I don't think I'll get sponsorship to be honest. I'm still trying to evaluate the costs, which is why I want to know how these other projects were implemented. I'm still in the planning phase ---  I want to come up with an estimate in costs so that I can have effective pitch to my new targeted sponsors.

---

### Post by mips on 2013-01-06
> **3v3rgr33n said:**
> These projects are amazing but is it possible to find out how these people are building these wireless mesh networks. I like the fact people there are many projects out there.

I need to find out their implementations so that I can compare them in terms of which is faster and which is inexpensive.

I also need to build a wireless mesh network by June.

We have some pretty big wireless networks in South Africa doing exactly what you wanna do over a much greater area.

[http://www.wug.za.net/](http://www.wug.za.net/)
[http://www.ptawug.co.za/](http://www.ptawug.co.za/)
[http://en.wikipedia.org/wiki/Pretoria_Wireless_Users_Group](http://en.wikipedia.org/wiki/Pretoria_Wireless_Users_Group)
[http://www.ctwug.za.net/](http://www.ctwug.za.net/)
[http://www.pcn.za.net/](http://www.pcn.za.net/)
[http://www.scn.za.net/](http://www.scn.za.net/)
[http://www.dwc.za.net/](http://www.dwc.za.net/)
[http://wirelessafrica.meraka.org.za/wiki/](http://wirelessafrica.meraka.org.za/wiki/)
[http://www.fmfi.org.za/](http://www.fmfi.org.za/)
[http://en.wikipedia.org/wiki/South_African_wireless_community_networks#Cape_Town_Wireless_User_Group_.28CTWUG.29](http://en.wikipedia.org/wiki/South_African_wireless_community_networks#Cape_Town_Wireless_User_Group_.28CTWUG.29)

You should find plenty of info in the above links wrt to technical issues, equipment used mapped nodes on google maps, line of sight tools etc etc etc

---

### Post by 3v3rgr33n on 2013-01-06
mips, you are awesome!

---

### Post by mips on 2013-01-06
Lol I only noticed now that you are from SA.

You might already fall within the area of an existing WUG if not you can always try and link up to one (some run quite long wireless links).

You might also wanna check out this forum [http://mybroadband.co.za/vb/](http://mybroadband.co.za/vb/) as there are lots of locals with knowledge there, I'm a member there as well.

Keep in mind that WUGs are non-commercial entities and don't route internet traffic (these are legal requirements). If you wanna start a commercial venture then you need to start looking at WISPs (I think WISPA is the controlling/oversight body.)

---

### Post by 3v3rgr33n on 2013-01-07
I live in cape town, since 2011 --- I was surprised there's something goin' on there in this regard.

I'm tryna create the network somewhere else though --- in the Eastern Cape.

---

### Post by 3v3rgr33n on 2013-02-14
Hi

Is it possible to create a wireless network -- sorta like a mini-network over a large city?
The network should not need any internet connectivity whatsoever and should be totally free. Is that sorta of thing possible? 

Regards
Adeeb

---

### Post by |{urse on 2013-02-14
Yes, set up a CWAN and a ton of apache servers with your 'internet's' pages. Sounds easy, right?

Curious.. why would you want to do that? The real Internet has quite a head start on you.

---

### Post by 3rdalbum on 2013-02-14
> **3v3rgr33n said:**
> Hi

Is it possible to create a wireless network -- sorta like a mini-network over a large city?
The network should not need any internet connectivity whatsoever and should be totally free. Is that sorta of thing possible? 

Regards
Adeeb

There are several of these already. I think they are called Freenets, but it's been a long time since I've lived in range of one.

---

### Post by mips on 2013-02-15
Why do you keep asking the same question?

Here is your previous thread [http://ubuntuforums.org/showthread.php?t=2100739](http://ubuntuforums.org/showthread.php?t=2100739)

---

### Post by 3v3rgr33n on 2013-02-15
> **mips said:**
> Why do you keep asking the same question?

Here is your previous thread [http://ubuntuforums.org/showthread.php?t=2100739](http://ubuntuforums.org/showthread.php?t=2100739)

The Wireless mesh network idea seemed a lil' far-fetched for me.

---

### Post by ugm6hr on 2013-02-15
Threads merged.

---

### Post by mips on 2013-02-15
> **3v3rgr33n said:**
> The Wireless mesh network idea seemed a lil' **far-fetched** for me.

As opposed to what, telepathy?

---

