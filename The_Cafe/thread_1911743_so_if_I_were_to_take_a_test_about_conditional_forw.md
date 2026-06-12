---
title: "so if I were to take a test about conditional forwarding..."
date: 2012-01-19
forum: The Cafe
---

### Post by imachavel on 2012-01-19
d.n.s. zones, etc. and here is my setup:

hostname
*****-Dimension-4700
danel@danel-Dimension-4700:~$ domainnam
No command 'domainnam' found, did you mean:
 Command 'domainname' from package 'hostname' (main)
domainnam: command not found
danel@danel-Dimension-4700:~$ domainname
(none)
danel@danel-Dimension-4700:~$ dnsdomainname
danel@danel-Dimension-4700:~$ nisdomainname
nisdomainname: Local domain name not set
danel@danel-Dimension-4700:~$ ypdomainname
ypdomainname: Local domain name not set


hahahahaha, do you think I'd pass the test?? :popcorn: Haha tests are weird, because people pass them but then don't know what an etho adapter driver is or how to share files between computes. It surprises me that they would understand i.p. config or if config and pass tests. Some times things look pretty but get you no where :lolflag:

---

### Post by Icehuck on 2012-01-19
> **imachavel said:**
> d.n.s. zones, etc. and here is my setup:


hahahahaha, do you think I'd pass the test?? :popcorn: Haha tests are weird, because people pass them but then don't know what an etho adapter driver is or how to share files between computes. It surprises me that they would understand i.p. config or if config and pass tests. Some times things look pretty but get you no where :lolflag:

I don't know what a etho adapter driver is, but I know what a driver for a NIC is. I also know that eth0 is the label assigned to NIC, but this could also be em0, dc0, or plip0, depending on the system you are using.

---

### Post by imachavel on 2012-01-19
sorry I didn't specify. Your network interface card or network interface adapter, has a etho i/o port. You can hard wire it, or you can put a usb wireless device into a usb hub. Now that the usb wireless device is in the usb hub, you can use it, or if standard straight through ethernet is connected to the computer, use the hard wired ethernet cable. Network interface adapter(NIC) just sends and receives packets via i.p. protocol

I know so little about the network interface adapter, I'm not even sure it's architecture beyond what it can process, 10 mbps/100 mbps/1000 mbps

:popcorn:

but recieving i.p. addresses and sending them are different. Require different set up, but I believe both use same .net library framework, no matter what OS. Remember, despite the file system(fat32, ntfs, ex2, hfs) most programs are different but browsers are the same, google chrome, firefox, etc. We could get nerdy about it, but let's just say there are things beyond what happens when you open Internet Explorer

when you connect to a domain, you are using the internet, and I believe connecting to a d.n.s. address, private domains I believe use dhcp, but probably at one time used d.n.s. Either way a domain address must be set up to pool and hand out i.p. addresses. This I'm weak on. A router can hand out dhcp, and having access to network programs and applications might be very simple as knowing the network address of the computer you are serving the applications on,  what takes up a lot of processing power is multiple connections through the router and server giving away i.p. addresses using dhcp or dns. Anyway, some networking protocols and applications might get a little more intense. The best thing in a network is to have healthy functioning computers with good amount of ram and hdd storage etc.

It's not ALL software, a lot of hardware will bottle neck if not adequate, but just to be clear, traffic going in and out of a router or server, usually is not the main cause of bottleneck, although with WANs yes it is more then anything. In a small network, what slows down a server is how many people access a server to get files, to download, or access accounts and upload, then the traffic definitely slow down. Many pings in smaller or even somewhat larger networks won't slow down much, but file transfers will, the servers and routers deciding what ports to use, all the decisions between the processor and N.I.C. will slow down many things when packets are being transferred for large file decisions. Obviously a computer by itself will slow down quite a bit for things on it's own, fps drop with graphic applications, hard drive space it taken up, processor over cached, low ram, old old hdd rpm. I don't want to say in a network it's an entirely different concept, it's the same exact concept. But now you are taking into account connection processes.

I can't say I know too much beyond that. I try not to talk out of my *** from things I've read. Experience goes so much further. I'm not saying you can't learn things in school, but experience is the only true way to test what someone can handle or not. I could 'read' things all day on how to partition a drive and install an OS and get drivers, but if I've never done even a few times, would you really trust me?
On an unrelated note I don't believe that my router has vlan forwarding capabilities lol:

[http://reviews.cnet.com/routers/d-link-dir-601/4507-3319_7-33925092.html](http://reviews.cnet.com/routers/d-link-dir-601/4507-3319_7-33925092.html)

---

### Post by grahammechanical on 2012-01-19
Some people are able to learn something that is written down and then answer questions on what they have read. This is a lot easier to do if the questions are of the multiple choice type.

Course providers are paid to get people through the course and would not get work if most students failed their tests.

I have been trained as a fire, health and safety officer. I have qualifications in this subject. I remember what one tutor said at the end of one of the courses that I attended. He was confident that we would pass the test. He said that we would get a qualification but we had to go back to our places of employment and prove ourselves to be health and safety practitioners.

Putting what we learn into practice is very different from passing a test and being able to explain the subject to others is a different level entirely.

Regards.

---

### Post by imachavel on 2012-01-19
very true. thanks for the great advice.

---

