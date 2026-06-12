---
title: "ubuntu server --&gt; home network?"
date: 2008-03-31
forum: Server Platforms
---

### Post by nok32 on 2008-03-31
hi, first post. i am trying to set up a largish home network (around 17 computers using a comcast cable modem). is there a tutorial geared towards this? i don't understand most of the technical terms, but i did at one point successfully install gentoo.. so i can at least read and follow directions. there's gotta be a tutorial for exactly this, right? link?

---

### Post by dmizer on 2008-03-31
what exactly do you want to do with your server?  or in other words, what "service" do you want your server to provide to your 17 +/- clients?

---

### Post by ryazkhan on 2008-03-31
I am sorry but you did not mention anything like what exactly you want to do, what you want to setup. You can setup Ubnuntu Server as server and then create a samba domain in it to share files or to make domain login enable. You can setup DHCP to assign IP addresses dynamically to your client you can do lot of things but you need to start from somewhere so please let us know where from you want to start and then we might be able to help you....:)   :confused:

---

### Post by Iowan on 2008-03-31
Check  [howtoforge.com]("http://www.howtoforge.com/howtos/linux/ubuntu") - they have several "perfect" server setups for Ubuntu.

---

### Post by nok32 on 2008-04-01
oops sorry, i should have explained better. currently we have a cable modem going to a wireeless router and then also a wireless repeater. as far as i know, the main router is managing all of our connections and it is too slow. i want to set up the server computer to handle all the internet traffic from the rest of the computers on the network in hopes that i can set a higher maximum limit on the number of connections. sharing files between computers would be a great thing, but the main concern right now is that the router can't handle all the connections at once. basically i am initiating this project because people are complaining about the internet being 'too slow' even though we pay for the highest premium bandwidth from comcast (for homes and not commerical).
i hope that description is clear enough to give you an idea of what i am trying to do. if i just knew the general approach i should be talking to this project, i could most likely follow whatever instructions, no problem. i just have zero experience with networking stuff.

[edit: iowan, thanks for the link. those tutorials look great but i am still at a loss when it comes to which one i should follow. ahhh, i'm feeling dumb. :blush: ]

---

### Post by dmizer on 2008-04-01
using ubuntu as a router/network hub will not increase local traffic speed for you.  you will need to purchase an additional piece of equipment called a network switch (not a hub).

a network switch allows all internal packets to stay inside the local network without having to pass them through the router.

[http://en.wikipedia.org/wiki/Network_switch](http://en.wikipedia.org/wiki/Network_switch)

---

### Post by ryazkhan on 2008-04-01
Get a switch from ebay or some and then Install ubuntu or any other flavor of Linux or you can stay with window if you are in love with it but I am talking about just your main server here not about you client machines. Setup DHCP, DNS, WINS etc  on that machine (server). Connect your main interenet connection to wireless router and connect your switch to your router as well. Now connect your all client to that switch. Let your DHCP (server) assign IPs to your client machines. You can do that from your router as well. This setup is pretty straight forward and since you already have router configured in you netword. Please let us know if you need any help with that. Just start and you will be fine!

---

### Post by nok32 on 2008-04-01
i don't know anything about network switches, but i don't think we generate that many 'internal' packets, if i understand what that would mean. i was under the assumption that i could use a program like webmin to handle the connections, taking the load off of the router that way. would this not work? why not? i will go research network switches a little better now..

---

### Post by ryazkhan on 2008-04-01
Webmin is just graphic tool fro server editions.

Ok let start you have 17 PC in your home network
how you connecting them all to internet? are they located in almost same place or different places? Do you have any router? wireless or other? does all your machines has wireless access capabilty? how many does? how you preffer to connect them to internet?

Please answer these question so I will have some betther idea about your requirement and will find something for you.

---

### Post by nok32 on 2008-04-01
sure thing.
the computers are spread out in different rooms in a large three-story house. there is currently no server computer. on the first floor is the comcast cable modem. this goes to a linksys wireless router. on the next floor is a linksys wireless repeater. all the computers connect to the router via wi-fi, just the most basic wireless setup possible.
with the router handling all the connections, i think we are getting unnecessary slow-downs. the internet habits of a number of the house occupants (bittorrent, etc) exceed the maximum number of connections the router can handle. i don't think it is a bandwidth issue.
i was hoping that if we set up a server computer and directly connected it to the modem and router, we could use ubuntu to manage the connections (instead of the router) and increase the maximum allowed connections, thus improving internet bandwidth. does this makes sense? have i misunderstood the potential of a server computer to do this?
will a network switcher help with this? i will definitely buy one, if this is the case-- but i don't see how it could work with a wireless set up.. thanks for any advice, or links!

---

### Post by nok32 on 2008-04-01
bump..

---

### Post by dmizer on 2008-04-01
you're right, it won't help with a wireless setup.

by using ubuntu, you are looking at an extremely complex solution to your problem.  what you're needing to do is called traffic shaping.  you can't really make your bandwidth larger with a server, but you can limit the bandwith consumed by BT or other protocols.  here's a little insite on what you may be up against by using ubuntu for traffic shaping: [http://ubuntuforums.org/showthread.php?t=26055](http://ubuntuforums.org/showthread.php?t=26055)

alternatively, you may want to look at a more expensive router which will allow you to configure traffic shaping at the gateway instead of through a server.  I believe the retail catch phrase for this is "Quality of Service" or QoS.

---

### Post by ryazkhan on 2008-04-02
Okay 
You have wireless networking pretty much and then you have repeater (access point). You definitly dont need switch or anything else your wireless network looks good. Bit-torrents and other programs like that eat bandwidth, so that is your bandwidth problem that is why you will notice that your internet remain slow oftenly because of download and upload or torrents. Try this ask your all users to stop their torrents programs and then notice the speed of internet it will be greate. I am not seeing anything else to make internet slow, however depending on wireless router your internet can be slow  and you will notice this difference when you connect directly to internet or connect any pc with ethernet direct in to your router. All basic wireless routers usually come with 4 ethernet port and when you plug direct into that port your router is acting as switch as well so you will get 100 MB speed or whatever your connection speed is but you will see while connecting through wireless it will be only 54 MB or less. I thing your are saying that because of router you running out of internet addressed this not just possible for your network since you have only 17 PCs and you can configure your router with any subnet mask. Usually /24 is the best option which support upto 254 connection so you can support upto 254 PC. I have very basic netgear wireless firewall router and I set it up for /24 and it can assign upto 254 IP addresses to clients. File sharing might be your problem, you can share files through every single computer but it sound nice to have server for these tasks. And if you decide to have server you can do more than that like you can setup DHCP, Samba Domain, DNS, WINs, PXE, TFTP, your own website (Apache2 ) etc. For that I would encourge you to think about ubuntu Linux. Please let me know if this explanation helped.

---

### Post by Deathrend on 2008-04-02
Part of the problem could also be wireless throughput.  I'm also guessing that you're using 802.11G, which has a max throughput of give or take 50 MB/s, that's peak performance, you start adding people on, then factor in distance, you're chopping this to bits.

[http://www.smallnetbuilder.com/component/option,com_wireless/Itemid,200/](http://www.smallnetbuilder.com/component/option,com_wireless/Itemid,200/) has some very nice charts for Routers/Wireless throughput, as well as reviews that talk about multiple PC's on the same wireless, and the effects it can have.

With 17 PC's on the same wireless, you're effectivly cutting your Wireless down to ~2MB/S, which would account for your slowww speeds.

Most cheap wireless routers aren't ment to support more than four to five people, that's why products like Cisco AirNet cost ~$600 compaired to a $40 Linksys WRT54G

---

