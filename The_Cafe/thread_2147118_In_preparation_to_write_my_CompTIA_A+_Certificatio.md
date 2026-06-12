---
title: "In preparation to write my CompTIA A+ Certification...."
date: 2013-05-20
forum: The Cafe
---

### Post by Drone4four on 2013-05-20
I intend to write my CompTIA A+ Certification in the next few weeks.  In preparation, I have come across some questions I can&#8217;t answer by my self.  A few of the questions are Windows specific, so I will spare asking you folks these questions.  I was hoping that you Ubuntu people could field some of my questions that are platform agnostic.  Here they are:

1.  My textbook claims, in the context of wireless device standards:

> Another issue is the standard supported by each device.  If possible, for each wireless network installation, select NICs and WAPs that comply with the exact same Wi-Fi standard.  Even though 802.11g, which is faster than 802.11b, is downward compatible with the slower standard, even a singly 802.11b device on the wireless network will slow down the entire WLAN.
(Holcombe, 2012:  803) 

If I connect my slow Kyocera RISE smartphone to my home WLAN, would that bring down/drag down all the download speeds of all the laptops?  I&#8217;m not sure exactly what the Wi-Fi standard is of my smart phone device and I don&#8217;t know how fast my wireless router is, neither do I know what standard the laptops are on my WLAN.  What I know for sure is that my cell is really slow (1Mbps down) and my laptops consistently download at 12Mbps.  Accessing the WLAN with my cell doesn't slow down my laptops.  What is my textbook referring to when it claims that 802.11b devices will slow down all the 802.11n devices connected to a network?

2.  Let&#8217;s say I have 3 laptops on my home network with these IP addresses:
```
192.168.1.0
192.168.2.0
192.168.3.0
```
Are these addresses unique compared to all the other 4.2+ Billion devices on the global IPv4 internet?  That can&#8217;t be true because 192.168.1.0 is a common ip address I have seen on many computers.  How can every ip address assigned using a dhcpd service on the global internet be unique and yet devices on home networks be duplicated hundreds of thousands of times over and over, as in my example?  

3. Are FTP/HTTP/IRC/BitTorrent protocols built on top of more basic protocols such as TCP/IP and UDP?

4. Practice review question # 3 for chapter # 1 says:  &#8220;I plan to replace the power supply in a computer.  What is the most important safety measure I should take to protect myself? The incorrect answer is to ground yourself by wearing an anti-static wrist band.&#8221;  The correct answer is to NOT ground yourself.  Why is that? Holcombe&#8217;s text on page 14 seems to contradict itself.  The text book claims, &#8220;Touching a grounded portion of your computer&#8217;s chassis will work to some extent, but for complete safety, us an ESD wrist strap with a ground wire attached to the computer frame.&#8221;  WTF?  Is wearing an anti-static wrist strap a good idea or not?

5.Can you use a loopback plug to test whether or not a switch port is functioning? (Ch16Q#1)
Do you use nslookup as an alternative or substitute for a DHCP daemon to obtain an ip address for the localhost so it can access the internet?  Could you furthermore use, ipconfig /renew as an alternative?

6. If a default gateway is down, I would think that I wouldn&#8217;t be able to communicate on LAN and access the internet, rather than only be able to access the global internet. (Ch15Q#13)

---

### Post by misterbiskits on 2013-05-21
I'm not an expert but:
#2: 192.168.x.0 are unique on the LAN side of the internet. The WAN side knows nothing about these adresses.  The router has its own unique WAN IP address.  The LAN IP  requests things from the router, and the router then requests from the internet.  The router receives the data and relays it to the requesting LAN address.  As I said not an expert but does that sound correct?

---

### Post by coldraven on 2013-05-21
4. The power supply has two sides. On the input side there are high, possibly lethal, voltages. On the output side you have low (12volt, 5volt) voltages.
Also, inside the power supply there are large capacitors that could retain a high voltage even when turned off.



If you were, say, adding memory to the motherboard you would wear a wrist-strap to eliminate static electricity from your body by shorting it to ground.
(The static could be caused by your synthetic clothing)
Static voltages can be high but the total amount of electrical charge is very low so it is dissipated in a microsecond. 
But you would have disconnected the mains supply so that there was no chance of electrocution.

However, if you were wearing a grounded wrist-strap and touched a high voltage item with the other hand you would get a shock right across your heart.
Even as little as 100volts will stop your heart in this situation. (Much higher charge - see [http://en.wikipedia.org/wiki/Coulomb](http://en.wikipedia.org/wiki/Coulomb))

An old electricians tip was to keep one hand in your pocket when fiddling with live equipment. If you get a shock it will go down your legs to ground and miss your heart. OK you will still jump, but your chances of living are higher.

---

### Post by Drone4four on 2013-05-21
> **coldraven said:**
> 4. The power supply has two sides. On the input side there are high, possibly lethal, voltages. On the output side you have low (12volt, 5volt) voltages.
Also, inside the power supply there are large capacitors that could retain a high voltage even when turned off.



If you were, say, adding memory to the motherboard you would wear a wrist-strap to eliminate static electricity from your body by shorting it to ground.
(The static could be caused by your synthetic clothing)
Static voltages can be high but the total amount of electrical charge is very low so it is dissipated in a microsecond. 
But you would have disconnected the mains supply so that there was no chance of electrocution.

However, if you were wearing a grounded wrist-strap and touched a high voltage item with the other hand you would get a shock right across your heart.
Even as little as 100volts will stop your heart in this situation. (Much higher charge - see [http://en.wikipedia.org/wiki/Coulomb](http://en.wikipedia.org/wiki/Coulomb))

An old electricians tip was to keep one hand in your pocket when fiddling with live equipment. If you get a shock it will go down your legs to ground and miss your heart. OK you will still jump, but your chances of living are higher.

I am still wrestling with the analysis for my question #4.  But thanks to **coldraven**, I think I am beginning to understand.  Can someone please verify that I understand this correctly?  From what I gather from **coldraven**’s post, it is a good idea to wear an anti static wrist strap when handling smaller hardware in a PC, like RAM, because it's conceivable that electrostatic build up could transfer from my clothes to the RAM, rendering the RAM permanently damage.  By wearing a strap, I am proactively avoiding damage to said computer components.  But when handling more sensitive higher voltage electrical components, like a power supply, wearing an anti static wrist strap could be lethal -- if 100 volts are discharge from the PSU, it could potentially stop the heart of a given technician.  The difference between the first instance of ESD is a minor transfer of electricity from my clothes to the RAM, meanwhile the other instance of ESD is a huge transfer of 100+ volts from the PSU to the heart.  This is why it's a good idea to wear a an anti static strap when replacing RAM, but a bad idea to wear such a strap when replacing a PSU.  Is this accurate?

---

### Post by Drone4four on 2013-05-21
> **misterbiskits said:**
> I'm not an expert but:
#2: 192.168.x.0 are unique on the LAN side of the internet. The WAN side knows nothing about these adresses.  The router has its own unique WAN IP address.  The LAN IP  requests things from the router, and the router then requests from the internet.  The router receives the data and relays it to the requesting LAN address.  As I said not an expert but does that sound correct?

So **misterbiskits**, are you basically saying that the address assigned to devices on a SOHO are unique only to that LAN?  So can I infer that a DHCP service hosted by my ISP will assign a unique address to the chief router of my LAN, enabling that router to serve as the gateway to the global WAN for all the devices under it on my SOHO LAN?  ...and therefore each default gateway should be among the unique ~4.2 billion IPv4 addresses?  I suppose that these 4.2+ Billion address are either (1) other default gateways, (2) devices which directly access the internet (like smartphones) or (2) servers resolved by a DNS?  

I think this explanation is relevant to one of my other question (#6).  My textbook says that if my default gateway is down, I should only be able to communicate with the global internet *and* unable to communicate with the other devices on my LAN.  I’m all like, wtf?  I would think that if my default gateway was down, I wouldn’t be able to communicate with the other devices on my LAN *and* I also wouldn’t have access to the global WAN.  Can someone please clarify?

---

### Post by lykwydchykyn on 2013-05-21
> **Drone4four said:**
> So **misterbiskits**, are you basically saying that the address assigned to devices on a SOHO are unique only to that LAN?  So can I infer that a DHCP service hosted by my ISP will assign a unique address to the chief router of my LAN, enabling that router to serve as the gateway to the global WAN for all the devices under it on my SOHO LAN?  ...and therefore each default gateway should be among the unique ~4.2 billion IPv4 addresses?  I suppose that these 4.2+ Billion address are either (1) other default gateways, (2) devices which directly access the internet (like smartphones) or (2) servers resolved by a DNS?  

You want to read up on NAT and private IP ranges.  There are several IP ranges designated as private ranges, and they will not route across the internet.  192.168.x.x is the most commonly used in consumer equipment, but there are a couple others.    What you're saying is basically correct, though.

> 
I think this explanation is relevant to one of my other question (#6).  My textbook says that if my default gateway is down, I should only be able to communicate with the global internet *and* unable to communicate with the other devices on my LAN.  I&#8217;m all like, wtf?  I would think that if my default gateway was down, I wouldn&#8217;t be able to communicate with the other devices on my LAN *and* I also wouldn&#8217;t have access to the global WAN.  Can someone please clarify?

Your textbook is wrong.  If your gateway (and ONLY the gateway) is down, you can still communicate with devices on the same subnet (LAN, basically, though it's possible to set up a LAN with multiple subnets).  You won't be able to communicate outside the subnet.

> 
3. Are FTP/HTTP/IRC/BitTorrent protocols built on top of more basic protocols such as TCP/IP and UDP?

This gets into different layers of the OSI stack.  I think this is more Network+ stuff rather than A+, but basically IP is one layer (logical addressing), TCP/UDP are another layer up (transport layer), and those other protocols are on top of that (application layer).

---

### Post by CharlesA on 2013-05-21
You might see some basic stuff on the OSI model on the A+, but it's unlikely. When I took the A+, it was super easy to figure out which answer was the right one and the version I took was probably 75% customer service questions.

---

### Post by coldraven on 2013-05-21
Re:4
I think you have understood it correctly. 
I did not make clear the danger of AC electricity. Rather simplified, think of your heart as a fuse. Which do you think would blow first, your heart or the fuse in the circuit?
Good luck with your exams.

---

### Post by Drone4four on 2013-05-27
Thank you, **lykwydchykyn **, for replying to my questions for clarification.  

And thanks, **coldraven**, for your follow up post.

I have come across a practice question in the Network Basics chapter.  I read the in depth answer key and looked up the corresponding material in the companion textbook but I still can't figure out why the correct answer is correct.  Here is the question transcribed from the textbook, along with my analysis of the answer choices. 

> 
#4
For a client’s SOHO, all the devices need to have their network addressing information configured using static, rather than dynamic, addressing.  Of the following, what addressing information can you configure for the computer? (Choose three.)
               **A.**  The computer’s IP address and subnet mask
               **B.**  The address of the default gateway
               **C.**  The address of the preferred DHCP server
               **D.**  The address of the preferred DNS server

I am inclined to cross off **D**, because my understanding of the Domain Name Service is that it’s basically a centralized database of IP addresses of web servers resolved to human readable words or phrases.  The IP, ‘173.194.64.99’, is resolved to Google.com by America’s centralized Domain Name Service servers that are hosted at FCC headquarters in Washington DC.  Right now every country has a DNS like this one.   The wingnuts on Slashdot chime in whenever authoritarian governments like Russia, China or Iran push to have a global centralized location so they can control by rendering inaccessible certain websites that offend the morals of the state.  Is this all a fair assessment of how DNS’es work?  Getting back to answer choice **D** in the question, small home office networks don’t have to use a DNS because DNS is only used by servers in the cloud.  A sysadmin for a SOHO can manually set the computers’ IP addresses and subnet masks, along with default gateways, if s/he were so inclined to do so.  So I circled **A** and **B**.  I have to circle one more.  As I have discussed, DNS is a centralized FCC thing, so a sysadmin for a SOHO isn’t going to specify a DNS server.  By process of elimination, **C** should be the other correct answer choice, even though DHCP is a program you use to request IP addresses from your ISP -- again, something a sysadmin has no control over.  I looked up the in depth answer key at the end of this chapter and from what I can tell, it says mostly the same things I have talked about except for some reason it says that a SOHO sysadmin can specify the preferred DNS server.  How and why is that possible?  

Can someone clarify how and why a sysadmin can specify a preferred DNS server?

---

### Post by CharlesA on 2013-05-27
DNS is used for name resolution. That doesn't mean it is limited to strictly web servers or web traffic. Depending on how your network is set up, you can either use broadcast for name resolution (messy on large networks) or have a server holding a catalog of all the hosts on the network and forwarding requests to external DNS servers if they do not have a record othe host being accessed.

If you have a static IP, you would need to configure the DNS servers, otherwise the machine won't know who to talk to to resolve host/domain names.

In Linux, it depends on your flavor. I use the interfaces file, but I think Ubuntu defaults to network manager.

In Windows, network connections. :p

No idea where it is in OSX, but it's probably similar to Linux.

The answer is A,B, D. You cannot use DHCP on a static address.

---

### Post by Drone4four on 2013-05-27
> **CharlesA said:**
> DNS is used for name resolution. That doesn't mean it is limited to strictly web servers or web traffic. Depending on how your network is set up, you can either use broadcast for name resolution (messy on large networks) or have a server holding a catalog of all the hosts on the network and forwarding requests to external DNS servers if they do not have a record other host being accessed.
So default gateways have both a unique IP address along with a unique domain name in human readable format like websites on the www?  Do ISPs have DNS servers assigning human readable addresses resolved to each unique IP address to every device below every default gateway (on every subnet of a given LAN) that access the greater global WAN?  

On FreeNode some users have scripts running to mask the identification associated with their domain name. In place of their domain name they have [user]/unaffiliated/.  What am I talking about? Is this relevant?  

> If you have a static IP, you would need to configure the DNS servers, otherwise the machine won't know who to talk to to resolve host/domain names.

The IP address of a localhost is either dynamic (requested with dhcpcd on Linux) or static (entered by the sysadmin manually). The same is true for default gateways and subnet masks.  Is that accurate?

---

### Post by Paqman on 2013-05-27
> **Drone4four said:**
> This is why it's a good idea to wear a an anti static strap when replacing RAM, but a bad idea to wear such a strap when replacing a PSU.  Is this accurate?

No, you should always wear an anti-static wrist strap when handling electronics. You shouldn't be touching any live high voltage components whether you're wearing a strap or not. The straps however do contain a large resistor in series so that they don't expose you to the risk of a nasty shock should something go wrong.

The **absolutely crucial** point that the original question was hinting at is that you should always double-check that you have unplugged a machine before diving into its innards. ESD is not the main risk here, it's a mains-voltage electric shock you need to protect yourself from. In the case of highly capacitive components you should also wait a few minutes in between powering off and unplugging, to give the stored charge in the caps time to leak away. Those suckers can bite.

---

### Post by CharlesA on 2013-05-27
> **Drone4four said:**
> So default gateways have both a unique IP address along with a unique domain name in human readable format like websites on the www?  Do ISPs have DNS servers assigning human readable addresses resolved to each unique IP address to every device below every default gateway (on every subnet of a given LAN) that access the greater global WAN? 

A gateway is just a router, which as the name says routes packets to their destination. They usually have an ip address and domain name, but as they are just moving packets from one network to another, they aren't normally accessible via your web browser or whatnot.

ISPs host their own DNS servers, and there are third party DNS such as Google's DNS, or OpenDNS that you can use. They all should pull from the same set of records.

> On FreeNode some users have scripts running to mask the identification associated with their domain name. In place of their domain name they have [user]/unaffiliated/.  What am I talking about? Is this relevant?  

That has nothing to do with internet routing or DNS. It is a "cloak" set by one of the freenode staff to hide the public address a user is connecting from. Helps with privacy (or it should, at least).

[quote]The IP address of a localhost is either dynamic (requested with dhcpcd on Linux) or static (entered by the sysadmin manually). The same is true for default gateways and subnet masks.  Is that accurate?

Yes. Usually DHCP will assign the ip address, subnet mask, default gateway and whatever dns servers are configured. If you are setting a static IP, you would need to configure those as well.

---

### Post by Drone4four on 2013-06-06
I'm back looking for some additional clarifications.  I wholeheartedly appreciate all the feedback I have already received.  

**Chapter 15, Question #10** reads as follows:
> You are running Ethernet cable for a business customer in a building under construction. The cabling on the floor you&#8217;re working on is being brought down from the plenum space through a column in the center of the room as shown in the accompanying illustration (**see attached**). The floor you are working on is 600 × 600 feet. You know that Ethernet cable has a length limitation before you have to start using switches or repeaters. Assuming the column is the starting point, how many repeating devices will you need to sufficiently cable this floor so that all of the cubicle areas in the diagram will be able to be sufficiently wired?

**A.**  Zero. If you&#8217;re starting the cabling at the center of the room, each cable length from the center should be sufficient.

**B.**  Two. Cable lengths to the two areas on the right should be sufficient, but the two areas on the left are too far away.

**C.**  Four. Although cable lengths seem sufficient, remember, you&#8217;ll be routing cables into numerous different individual cubicles, so the length won&#8217;t be straight end-to-end.

**D.**  Eight. You&#8217;ll need two switches or repeaters in each cubicle area, since the maximum effective length of each Ethernet cable segment is only 50 metres.
I understand how ethernet cables have length limitations.  The 802.11 Wi-Fi standard has an estimated outdoor range of ~125 metres and an indoor range of ~50 metres.  But this question in particular isn&#8217;t about Wi-Fi ranges.  The question is about Ethernet cabling.  All my companion book by Holcombe says about the limitations of Ethernet cabling is that &#8220;An Ethernet NIC will need to connect to the LAN using UTP CAT5/5e/6 cabling that has RJ-45 connectors and does not exceed the 100 metre distance limit between the computer and the switch for UTP and STP.&#8221;  Pyles&#8217; In-Depth answer verifies Holcombe&#8217;s statement that the maximum effective cable length for Ethernet is 100 metres. What I don&#8217;t understand is how in **C** there apparently will be cables routed &#8220;into numerous different individual cubicles, so the length won&#8217;t be straight end-to-end.&#8221;  If this is true, then the Ethernet cables wired into each room will sometimes be curved or bent, meaning that some Ethernet cables won&#8217;t be able to reach the cubicles placed at the farthest corner of a given room.  Does that mean that switches or repeaters should be deployed? If this is true, then **D** seems more correct than **C** on that assumption, HOWEVER **D** can&#8217;t be true because factually speaking, Ethernet cable segments are 100 metres, not 50.  Therefore, all the answers choices are wrong by my judgement.  The In-Depth answers go into detail about how **C** is the correct answer.  Here is exactly what the In-Depth answers say about **C** being correct: 

> The maximum effective cable length for Ethernet cable is 100 metres, or about 328 feet, and if you are running cable from the centre of the room to the edges, you shouldn&#8217;t need repeaters or switches, but you will also be using a lot of cable length conforming to the position and shape of all of the individual cubicles in each area.  Accordingly, you&#8217;ll likely need one device per major quarter of the floor to make sure all of the cubicles can be networked.

What is the author of this practice answer trying to say here?  What device? A device such as a host, like a computer with a NIC? I should hope so.  Connecting devices to the WAN through the LAN is the whole purpose of the project described in this question.  Why does this In-Depth answer indicate such a trivial thing (that you&#8217;ll need one device per major quarter of the floor to make sure all of the cubicles can be networked)?  Is this device that the author speaks of here the switch/repeater that I spoke of earlier?  Is the author out to lunch? If not, then what am I missing?

---

### Post by CharlesA on 2013-06-06
Sounds like they are saying you might need to use one switch per area because of the way the cubicles are set up.

I have always tried to explain the 100 meter limit is from power to power. Anything that provides power - router, switch, hub, computer can extend that range.

---

### Post by Drone4four on 2013-06-09
> **CharlesA said:**
> I have always tried to explain the 100 meter limit is from power to power. Anything that provides power - router, switch, hub, computer can extend that range.
Thanks, Charles.  I think this tip about how power is the limiting factor when it comes to distance.

Now here is a question I came across in Chapter 16 (Troubleshooting Networks)

Question #2:
> You have just installed a new network printer in a customer’s office. You connect your laptop to the printer using a USB cable, and it prints fine. However, when your customer attempts to connect and print over the network, he can’t do so. You check the computer’s network configuration and physical network connections, and everything is fine. You check the IP address you’ve given the printer as well as its physical connections, and they are correct. You try to ping the printer’s IP address from the customer’s computer, but the request times out. Of the following, what could be wrong?
**A.**  The printer is configured to use the wrong DHCP server.
**B.**  The printer is configured to use the wrong DNS server.
**C.**  The printer is configured to use the wrong NAT server.
**D.**  The printer is configured to use the wrong subnet mask.
I picked **C** because I didn’t really know what NAT was. According to the In-Depth answers: > A subnet mask defines the specific network to which an IP address belongs.  It is expressed similarly to the way an IPv4 address is expressed.  A common subnet mask is 255.255.255.0.  If this setting is missing or entered incorrectly onto a device that has a manual network configuration, the device will not be able to to be reached over the network. So what would be the solution if I were troubleshooting this problem with a printer that was having difficulty connecting to a linux box? If the problem is that the subnet mask isn’t set to 255.255.255.0 (let’s say it’s incorrectly set to 0.0.0.1), would the solution be for the technician to manually set it to 255.255.255.0?  If this is what needs to be done, which configuration file and where would you enter this information using Linux?  The In Depth answers furthermore say that > DHCP doesn’t assign addresses to printers.  So where do I go to manually assign a printer its IP address?

---

### Post by CharlesA on 2013-06-09
I haven't run into any devices that do not work with DHCP. That includes, servers, workstations, smartphones, printers, and retail gear.

But yeah, the subnet mask is the correct answer, but most techs are smart enough to know what the network's subnet is supposed to be set to so they shouldn't make that mistake in the first place.

---

### Post by Drone4four on 2013-06-10
> **CharlesA said:**
> But yeah, the subnet mask is the correct answer, but most techs are smart enough to know what the network's subnet is supposed to be set to so they shouldn't make that mistake in the first place.  Most techs know what the network's subnet is.  But where and how do they set this for a printer?

---

### Post by ppv on 2013-06-10
> [COLOR=#000000]*Another issue is the standard supported by each device. If possible, for each wireless network installation, select NICs and WAPs that comply with the exact same Wi-Fi standard. Even though 802.11g, which is faster than 802.11b, is downward compatible with the slower standard, even a singly 802.11b device on the wireless network will slow down the entire WLAN.*[/COLOR]
[COLOR=#000000][/COLOR]
This says that if there is one device which is of a lower WLAN standard, then all devices would tend to use the lower standard thus reducing the throughput on the entire WLAN. The Wi-Fi standards have increasing speeds with each versions a/b/g/n. Even if they are downward compatible but then, one slower standard device would cause other faster (higher) standard devices to run with the slower device's speed.

---

### Post by Drone4four on 2013-06-10
> **ppv said:**
> [COLOR=#000000][/COLOR]
This says that if there is one device which is of a lower WLAN standard, then all devices would tend to use the lower standard thus reducing the throughput on the entire WLAN. The Wi-Fi standards have increasing speeds with each versions a/b/g/n. Even if they are downward compatible but then, one slower standard device would cause other faster (higher) standard devices to run with the slower device's speed.

So if I connect my slow Kyocera RISE smartphone to my home WLAN, would that bring down/drag down all the download speeds of all the laptops? 

I’m not sure exactly what the Wi-Fi standard is of my smart phone device and I don’t know how fast my wireless router is, neither do I know what standard the laptops are on my WLAN. What I know for sure is that my cell is really slow (1Mbps down) and my laptops consistently download at 12Mbps. Accessing the WLAN with my cell doesn't slow down my laptops.

---

### Post by mips on 2013-06-10
This thread just confirms how useless these certs are. I'm not trying to be nasty or burst any ones bubble but really?

---

### Post by CharlesA on 2013-06-10
> **Drone4four said:**
> Most techs know what the network's subnet.  But where and how do they set this for a printer?

Depends if they are setting a static IP or using DHCP with a reservation. The static IP is configured on the printer, while a reservation is configured on the DHCP server.

> **mips said:**
> This thread just confirms how useless these certs are. I'm not trying to be nasty or burst any ones bubble but really?

Indeed. All they do is prove you know some things, most of which could be found in a book or on the internet.

---

### Post by lykwydchykyn on 2013-06-13
> **CharlesA said:**
> All they do is prove you know some things

That's kind of the point of a certification, is it not?

---

### Post by CharlesA on 2013-06-13
> **lykwydchykyn said:**
> That's kind of the point of a certification, is it not?

Depends on who you ask. Most of the time they are just Resume/CV food to impress people in HR.

Unless the format for the CompTIA certs has changed, it is all book knowledge, no practical experience needed in order to pass the exam.

---

### Post by lykwydchykyn on 2013-06-13
> **CharlesA said:**
> Depends on who you ask. Most of the time they are just Resume/CV food to impress people in HR.

Unless the format for the CompTIA certs has changed, it is all book knowledge, no practical experience needed in order to pass the exam.

Yeah, I won't disagree with that.  But it at least demonstrates an ability to grasp and process basic technical concepts, so it's not entirely useless.  I would not discourage someone from getting a certification if he was looking for work in IT.

---

### Post by CharlesA on 2013-06-14
> **lykwydchykyn said:**
> Yeah, I won't disagree with that.  But it at least demonstrates an ability to grasp and process basic technical concepts, so it's not entirely useless.  I would not discourage someone from getting a certification if he was looking for work in IT.

Agreed. It is still something to get if you are going to be working in IT, even if it is just to say you are certified.

---

### Post by Drone4four on 2013-06-14
I&#8217;m not really sure what specifically mips was referring to with respect to his comment about how useless certs are based on what he read in this thread.

I have encountered three further points of clarification in the networking material.

**#1**
The 1st, 2nd, 3rd octets of an IP address is the network ID. The 4th octet is the host ID.
But devices are usually assigned two of these addresses: First, an IP address and second, a subnet mask.  A device with a DHCP client installed on a host could receive, as an example, both of the following from a DHCP server:
```
192.168.1.41 (IP)
255.255.255.0 (subnet mask)
```
The network ID for the IP is 192.168.1 and the host ID is 41.  The network ID for the subnet mask is 255.255.255 and the host Id is 0. Is this accurate?  

The principle reason why devices on networks are usually assigned IPs and masks is because, so the internet&#8217;s architects reasoned, it would be mathematically impossible for every device to have a unique address because there are more devices than are available IP addresses:

```
(16,000,000×127)+(65,000×16,000)+(254×2,000,000) = 3,580,000,000
```

The multiplication in the first set of brackets represent Class A, the second set represents Class B and the third, Class C.  Class D is multicast and E is reserved.  CIDR and IETF in 1993 introduced IPv4, among other things, including subnet masking for the purposes of providing billions of additional address combinations to accommodate for the more than 3.5 billion devices/servers/gateways demanded by consumers, businesses and governments.  

Is all that accurate?

**#2**
After installing an all-in-one printer/fax/copier, does it use an APIPA address until the network admin assign it a more permanent address using the gateway router&#8217;s firewall firmware?  And please correct me if I am wrong, but most all-in-one printer/fax/copiers usually don&#8217;t have a DHCP client installed to use to exchange a lease agreement.  This means that a network admin has to assign it a static IP.  Is that accurate?

**#3**
Wikipedia says that IANA is responsible for the global coordination of the DNS Root, IP addressing, and other Internet protocol resources. *Is IANA the body (which would be many years ago now) that decided that FTP would use port 21, http use port 80, and irc port 194? *Is it also possible that Valve software, for their first multiplayer game they wrote (Half-Life) back in 1997, was told by IANA to use port 27015?


Some of you might be thinking, &#8216;why is this person asking CCNA/Network+ questions when he is preparing to write his A+ exams&#8217;?  There are 3 chapters in both of my A+ texts devoted to networking.  These chapters in particular I struggled with the most, compared to all the other chapters on PC repair and such.  I am working on my weakest link by trying to understand these basic network concepts....

---

### Post by Bandit on 2013-06-14
@OP,
While I hope the best to you on your Cert. I have the A+ from CompTIA. I will say if you asking these questions 2 weeks form taking your exam. Your not going to pass unless your very lucky.. There is two parts to the exam and you must pass the first part before moving on to the second. I recommend you purchase one of the Sybex study guides and take the practice test it offers over and over.  Other then those helpful thoughts, I am not allowed to assist you any further due to the regulations on the exams.. Good luck..

Joe..

---

### Post by Drone4four on 2013-06-14
> **Bandit said:**
> @OP,
I will say if you asking these questions 2 weeks form taking your exam. Your not going to pass unless your very lucky.. There is two parts to the exam and you must pass the first part before moving on to the second. I recommend you purchase one of the Sybex study guides and take the practice test it offers over and over. 

I initially planned to write my exam the first week of June (2 weeks ago).  But nearing the end of May I began trying to answer the questions in the McGraw Hill (not Sybex) book titled, 'CompTIA A+ Certification Practice Exams' (there are 1000 of them in total).  I was scoring about 50% correct.  At that point in May I realized I had a lot of review and further reading to do.  The half a dozen or so questions that I found confusing I copied out from this book and shared them in this forum for clarification.  You are right, I wasn't ready to write my exam then.  I have a lot more studying to do. I hope to write in the fall.  

> I am not allowed to assist you any further due to the regulations on the exams.. 
If you are not allowed to help me, are there other rules prohibiting the discussion I am having in this thread?  What regulations specifically are you referring to?

---

### Post by mips on 2013-06-14
> **Drone4four said:**
> I&#8217;m not really sure what specifically mips was referring to with respect to his comment about how useless certs are based on what he read in this thread.

I'm referring to the fact that I've seen so many people with certs in my life that don't have a clue as to what's actually going on and asking the questions the OP asked should be general knowledge in a IT environment. It's not something you should have to study from a book, its something you should know. That test tells you absolutely zero about your knowledge.

I was forced to go on A+ training with about 60 colleagues many many years ago, we were correcting the lecturer, 3 days into the course we all left. I read through the books the morning before the exams I scored almost 100%, all my colleagues also passed with flying colours. The same goes for all the Cisco exams I did, my experience came in great but at the same time I had to deal with some new staff that did the same exams (CCNP) and they literally knew jack, they passed the exams but I would not give them anything but read level access on the network, that's how bad they were. Yet according to the certification they achieved they were competent to work on a live 10 000 router/switch network. I (and my team) had to do internal exams which were 10x harder than writing the Cisco exams and trust me I failed one of those. We had those internal exams every 6 months just to keep us on our toes. You cannot allow people that don't know what's going on onto a production network affecting millions of clients and the companies SLA's/bottom line.

The thing people don't realise is this field is very much about aptitude, you either get it or you don't in which case you follow a tick sheet to solve problems. There are plenty of people working in the field that simply do not have the aptitude and it's not something you can train them on. Simple things like logical reasoning, deduction, methodology etc do not come into play for a lot of people. They simply cannot function outside of a tick sheet.

EDIT: People should be mature and realise what they are good at. Me for example would love to be concert pianist or a great musician but I know that I suck at it. We all have certain ideals but we have to be realistic. If you grew up taking your toys apart 5 mins after getting them then you would probably end up in the science or engineering fields. I recall kids drawing awesome paintings in primary school while I drew stick figures. Do what you are good at and don't simply go work in a field where you don't have the aptitude because you think there is money in that field. Yes you could probably get by earning money but you will never rise to the top. Every year we have local salary surveys and you always see people biatching because they don't earn halve of what others in their field earn, it's simply because you are not good at what you do, the mere fact that you work in IT does not mean you measure up.

---

### Post by lykwydchykyn on 2013-06-14
> **Drone4four said:**
> I’m not really sure what specifically mips was referring to with respect to his comment about how useless certs are based on what he read in this thread.

I have encountered three further points of clarification in the networking material.

**#1**
The 1st, 2nd, 3rd octets of an IP address is the network ID. The 4th octet is the host ID.
But devices are usually assigned two of these addresses: First, an IP address and second, a subnet mask.  A device with a DHCP client installed on a host could receive, as an example, both of the following from a DHCP server:
```
192.168.1.41 (IP)
255.255.255.0 (subnet mask)
```
The network ID for the IP is 192.168.1 and the host ID is 41.  The network ID for the subnet mask is 255.255.255 and the host Id is 0. Is this accurate?  

Not really.  The subnet mask is the key that deciphers which part of the IP is network address and which part is host address.  So I can have an address that's 10.10.20.1 with a mask of 255.255.0.0, and there the network id is 10.10.0.0 and the host id is 20.1.  If I change the mask to 255.255.255.0, the host id is now just .1 and the network is 10.10.20.0.
It doesn't have to break on the octet either; for example, the network I'm on now has a subnet mask of 255.255.252.0.

Another way you'll see this notated is called CIDR notation, which looks like 10.10.20.0/24.  The "24" is equivalet to 255.255.255.0, because it means the first 24 bits of the IP is the network.  My subnet mask of 255.255.252.0 would be /22 in CIDR notation.

> 
The principle reason why devices on networks are usually assigned IPs and masks is because, so the internet’s architects reasoned, it would be mathematically impossible for every device to have a unique address because there are more devices than are available IP addresses:

```
(16,000,000×127)+(65,000×16,000)+(254×2,000,000) = 3,580,000,000
```

The multiplication in the first set of brackets represent Class A, the second set represents Class B and the third, Class C.  Class D is multicast and E is reserved.  CIDR and IETF in 1993 introduced IPv4, among other things, including subnet masking for the purposes of providing billions of additional address combinations to accommodate for the more than 3.5 billion devices/servers/gateways demanded by consumers, businesses and governments.  

Is all that accurate?


The way we currently accomodate billions of connected devices is by putting the vast majority of them on a private IP range behind a NAT.  Getting an actual public IP usually involves some expense, and we're running out of them.  This is why you'll see people pushing for ipv6, which adds a lot more addresses and does away with the need to NAT and do private addressing.
> 
**#2**
After installing an all-in-one printer/fax/copier, does it use an APIPA address until the network admin assign it a more permanent address using the gateway router’s firewall firmware?  And please correct me if I am wrong, but most all-in-one printer/fax/copiers usually don’t have a DHCP client installed to use to exchange a lease agreement.  This means that a network admin has to assign it a static IP.  Is that accurate?


Actually most network-connected devices these days *does* have a dhcp client built in; I'd say most printers I've seen for at least the last decade can do DHCP.  It's probably a good idea to assign a static IP so you know where to send your print jobs, though.

> 
**#3**
Wikipedia says that IANA is responsible for the global coordination of the DNS Root, IP addressing, and other Internet protocol resources. *Is IANA the body (which would be many years ago now) that decided that FTP would use port 21, http use port 80, and irc port 194? *Is it also possible that Valve software, for their first multiplayer game they wrote (Half-Life) back in 1997, was told by IANA to use port 27015?

Only if it is an officially registered port number.  See [https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers)

> 
Some of you might be thinking, ‘why is this person asking CCNA/Network+ questions when he is preparing to write his A+ exams’?  There are 3 chapters in both of my A+ texts devoted to networking.  These chapters in particular I struggled with the most, compared to all the other chapters on PC repair and such.  I am working on my weakest link by trying to understand these basic network concepts....

If you want to go into IT (I don't know why you'd want an A+ if you didn't), it's best to get these concepts straight whether or not they're on the exam.  Every computer is networked these days, there isn't much point in a tech who doesn't understand networking.

---

### Post by CharlesA on 2013-06-14
CIDR really threw me for a loop before I actually understood why it was used for (custom subnetting ftw!). ;)

---

### Post by mips on 2013-06-14
> **CharlesA said:**
> CIDR really threw me for a loop before I actually understood why it was used for (customer subnetting ftw!). ;)

We would have run out of IP addresses way before NAT came along if it was not for CIDR.

---

### Post by CharlesA on 2013-06-14
Aye, classful subnetting was a waste of addresses. :shock:

---

### Post by Drone4four on 2013-06-15
@lykwydchykyn: Thanks for the clarifications on IANA and on printers.  Give me a few days to reply to what you said about NAT, subnetting, and CIDR notation.

---

### Post by Drone4four on 2013-06-17
Wikipedia uses [this]("http://en.wikipedia.org/wiki/Subnetwork#IPv4_subnetting") example: 

> IP address: 192.168.5.130
Subnet mask:  255.255.255.0
Network prefix:  192.168.5.0
Host part:  0.0.0.130

Wikipedia uses the expression, ‘host part’.  Is this the same as, ‘host ID’?   And is ‘network prefix’ the same as ‘net id’? I’ll assume it is until someone corrects me.  Here is the example I initially used, but reorganized into the categories described in **lykwydchykyn**’s post and on Wikipedia:

> IP address: 192.168.1.41
Subnet mask: 255.255.255.0
Network ID: 192.168.1.0
Host ID: 0.0.0.41

Likewise, in both examples, the CIDR notation would be the IP address, with /24 to indicate the subnet mask in shorthand. 

After receive feedback from you folks a few days ago I found [a guide on CIDR notation]("http://whatismyipaddress.com/cidr") in the knowledge base section on whatismyipaddress.com. After reading it over a few times, I did my best to practice by making up some address combinations and trying to reformat the subnet masks into shorthand CIDR notation.  Here it is below:

IP: 192.168.1.41, subnet mask: 3.128.46.1,my CIDR notation: 192.168.1.41 /0
IP: 192.168.1.41, subnet mask: 129.190.6.12, my CIDR notation: 192.168.1.41 /1
IP: 192.168.1.41, subnet mask: 219.0.255.3.9, my CIDR notation: 192.168.1.41 /3
IP: 192.168.1.41, subnet mask: 0.128.46.1, my CIDR notation: 192.168.1.41 /0
IP: 192.168.1.41, subnet mask: 0.0.46.1, my CIDR notation: 192.168.1.41 /0
IP: 192.168.1.41, subnet mask: 0.10.46.1, my CIDR notation: 192.168.1.41 /0
IP: 192.168.1.41, subnet mask: 255.128.46.1, my CIDR notation: 192.168.1.41 /9
IP: 192.168.1.41, subnet mask: 255.255.46.1, my CIDR notation: 192.168.1.41 /16
IP: 192.168.1.41, subnet mask: 255.255.253.1, my CIDR notation: 192.168.1.41 /22
IP: 192.168.1.41, subnet mask: 255.255.124.1, my CIDR notation: 192.168.1.41 /16

After my study session practicing with this exercise I came to the conclusion that it was all wrong.  But here I am a few days later and I can’t see what’s wrong with it.  Can someone please enlighten me?

The purpose of dividing networks up into subnets below a NAT gateway router (along with addresses with CIDR notations) is to allow for devices to access the internet while managing the scarcity of IPv4 addresses.  With respect to NATs, I found [a badass entry on the Azureus wiki]("http://wiki.vuze.com/w/What_is_NAT").  I don’t understand it completely.  After reading that article I began to draw a similarity between NATs and proxies.  They sorta seemed the same, but I have since discovered some major differences.  One difference is that NAT is transparent, meaning that the destination from outside the network can see the source.  Whereas the purpose of a proxy server is to conceal the identity from which information is being requested from.  The external address being navigated to is convinced that the proxy IS the authentic source of the information request.  NATs are a little more honest.  With NATs, it’s possible that the external address being navigated can determine the true source.  Proxies hide the source address.  NATs don’t.If all that is true, then why does SAM’s Teach Yourself TCP/IP authored by Joe Casad claim the reverse is true? Joe Casad says, “A NAT device obscures all details of the local network and, in fact, hides the existence of the local network.”  Here is a few paragraphs so you have the complete context:

> Some experts began to notice that, if a DHCP server is providing the client with an IP address, there is no real reason why this address has to be an official, unique “legal” Internet address. As long as the router itself has an Internet-ready address, it can act as a proxy for clients on the network—receiving requests from clients and translating the requests to and from the Internet address space. Many router/DHCP devices today also perform a service known as Network Address Translation (NAT).

...

A NAT device improves security because it can prevent an outside attacker from finding out about the local network. To the outside world, the NAT device looks like a single host connected to the Internet. Even if an attacker knew the address of a computer on the local network, the attacker would not be able to open a connection with the local network because the local addressing scheme is not contiguous with the Internet address space. 

Do all gateway routers act as NATs?

---

### Post by mips on 2013-06-17
> **Drone4four said:**
> 
IP: 192.168.1.41, subnet mask: 3.128.46.1,my CIDR notation: 192.168.1.41 /0
IP: 192.168.1.41, subnet mask: 129.190.6.12, my CIDR notation: 192.168.1.41 /1
IP: 192.168.1.41, subnet mask: 219.0.255.3.9, my CIDR notation: 192.168.1.41 /3
IP: 192.168.1.41, subnet mask: 0.128.46.1, my CIDR notation: 192.168.1.41 /0
IP: 192.168.1.41, subnet mask: 0.0.46.1, my CIDR notation: 192.168.1.41 /0
IP: 192.168.1.41, subnet mask: 0.10.46.1, my CIDR notation: 192.168.1.41 /0
IP: 192.168.1.41, subnet mask: 255.128.46.1, my CIDR notation: 192.168.1.41 /9
IP: 192.168.1.41, subnet mask: 255.255.46.1, my CIDR notation: 192.168.1.41 /16
IP: 192.168.1.41, subnet mask: 255.255.253.1, my CIDR notation: 192.168.1.41 /22
IP: 192.168.1.41, subnet mask: 255.255.124.1, my CIDR notation: 192.168.1.41 /16

After my study session practicing with this exercise I came to the conclusion that it was all wrong.  But here I am a few days later and I can’t see what’s wrong with it.  Can someone please enlighten me?

No idea as we have no idea as to how you arrived at those results. Maybe go back to the basics and start over.

---

### Post by CharlesA on 2013-06-17
> **Drone4four said:**
> Wikipedia uses [this]("http://en.wikipedia.org/wiki/Subnetwork#IPv4_subnetting") example: 



Wikipedia uses the expression, &#8216;host part&#8217;.  Is this the same as, &#8216;host ID&#8217;?   And is &#8216;network prefix&#8217; the same as &#8216;net id&#8217;? I&#8217;ll assume it is until someone corrects me.  Here is the example I initially used, but reorganized into the categories described in **lykwydchykyn**&#8217;s post and on Wikipedia:

Same thing. As long as you can tell which part of the IP is the host part and which is the network part, you are ok.



> Likewise, in both examples, the CIDR notation would be the IP address, with /24 to indicate the subnet mask in shorthand. 

After receive feedback from you folks a few days ago I found [a guide on CIDR notation]("http://whatismyipaddress.com/cidr") in the knowledge base section on whatismyipaddress.com. After reading it over a few times, I did my best to practice by making up some address combinations and trying to reformat the subnet masks into shorthand CIDR notation.  Here it is below:

IP: 192.168.1.41, subnet mask: 3.128.46.1,my CIDR notation: 192.168.1.41 /0
IP: 192.168.1.41, subnet mask: 129.190.6.12, my CIDR notation: 192.168.1.41 /1
IP: 192.168.1.41, subnet mask: 219.0.255.3.9, my CIDR notation: 192.168.1.41 /3
IP: 192.168.1.41, subnet mask: 0.128.46.1, my CIDR notation: 192.168.1.41 /0
IP: 192.168.1.41, subnet mask: 0.0.46.1, my CIDR notation: 192.168.1.41 /0
IP: 192.168.1.41, subnet mask: 0.10.46.1, my CIDR notation: 192.168.1.41 /0
IP: 192.168.1.41, subnet mask: 255.128.46.1, my CIDR notation: 192.168.1.41 /9
IP: 192.168.1.41, subnet mask: 255.255.46.1, my CIDR notation: 192.168.1.41 /16
IP: 192.168.1.41, subnet mask: 255.255.253.1, my CIDR notation: 192.168.1.41 /22
IP: 192.168.1.41, subnet mask: 255.255.124.1, my CIDR notation: 192.168.1.41 /16

That doesn't look right.

192.168.1.0/24 = 255.255.255.0
192.168.1.0/25 = 255.255.255.128

Have a read here:
[http://www.tcpipguide.com/free/t_IPCIDRAddressingExample.htm](http://www.tcpipguide.com/free/t_IPCIDRAddressingExample.htm)

It also helps to break the notation down into it's binary form. That's how I learned CIDR.

> Do all gateway routers act as NATs?
I don't know for sure, but I doubt it. Depends on the device.

---

### Post by lykwydchykyn on 2013-06-17
You are never going to have a subnet mask like 0.0.46.1.  The point of a subnet mask is to tell you how many bits starting on the left define the network address (which is why we can just abbreviate it to a single number between 0 and 32).  So in binary it's always going to look like a certain number of 1's followed by a certain number of 0's.  So a netmask octet won't just be any arbitrary number from 0-255.  

NAT and proxying operate on different layers; NAT on the logical addressing layer, proxying on the application layer.

---

