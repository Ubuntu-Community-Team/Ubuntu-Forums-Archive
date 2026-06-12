---
title: "Is having a router the same as having a firewall?"
date: 2007-06-05
forum: The Cafe
---

### Post by aysiu on 2007-06-05
I'm not really a security expert, and I *think* I've read stuff hinting that this might be true, but I've never seen a straight answer.

So, to the security experts out there, is having a router the same as having a firewall? What's the difference? If it is the same thing, does IP tables become redundant if you have a router?

Please explain it to me as if I were a moron... because I am when it comes to security and networking.

---

### Post by jgrabham on 2007-06-05
Erm a firewall is software.  (I'm not an expert either) Routers can have firewalls built in.

---

### Post by aysiu on 2007-06-05
> **jgrabham said:**
> Erm a firewall is software.  (I'm not an expert either) Routers can have firewalls built in.
So a router *can* have a software firewall built into it, but it doesn't have to?

And does that then make IP tables redundant?

---

### Post by stimpack on 2007-06-05
Routers using NAT mean outside sources can't uninvitedly talk to your computer because they have no idea of your internal IP. 

So many hold that a firewall is redundant behind a router. I have no idea if it is a fully secure belief though.

---

### Post by matthinckley on 2007-06-05
yes a router will act as a firewall.. since it performs network address translation and does not allow traffic to pass from the outside to a device on the inside without setting up specific port forwards this would make iptables redundant.

EDIT: unless you are trying to block computers on the inside network access to the pc with iptables.. in this case you would need iptables as the router does not block any traffic on the inside.  for instance if you have a wireless network you may want to use iptables on your pc's so that in the event someone hacks your wireless network they will not have unrestricted access to your pc.

---

### Post by SishGupta on 2007-06-05
Software firewalls installed on a machine can prevent unwanted outward bound connections (from trojans or apps that don't ask before phoning home).
In this way it is beneficial.

Most routers have NAT + a firewall. You can tell the router to redirect externalip: port to internalip: port but the firewall will control if it actually happens or not. 
Firewall rules can stop NAT from working which is usually intentional. On my router i use NAT to do externalip:80 to internalserverip:80 but if I only want my webserver available 9am-5pm then I use the firewall on my router to block it from 5pm-9am.
Router firewalls can block IP's but NAT alone can not.

The reason there is confusion imho is because routers have combined firewalls, firewall filters and NAT into one or two tools on the router interface.

Edit: To answer your question more directly. A router with NAT can act as a rudimentary firewall (simple port blocking), but a firewall is more than just port blocking and that is why most routers have built in firewall software.

---

### Post by aysiu on 2007-06-05
Okay. I think that sort of answers my question, but a lot of those terms flew over my head.

---

### Post by SishGupta on 2007-06-05
> **aysiu said:**
> Okay. I think that sort of answers my question, but a lot of those terms flew over my head.

IMHO wikipedia is the best way to learn.

[http://en.wikipedia.org/wiki/Firewall](http://en.wikipedia.org/wiki/Firewall)
[http://en.wikipedia.org/wiki/Router](http://en.wikipedia.org/wiki/Router)

keep clicking terms that you dont understand and read those articles.

---

### Post by koenn on 2007-06-05
A router routes IP packets between subnets, i.e. it provides a route between subnets. 
Say you're on subnet 192.168.1.0 and google is on 208.69.XXX.XXX. You're computer can send IP packets directly to hosts on the same subnet. To go to a different subnet, you need a router. 
That's how routers connect your PC's at home to other networks, such as the internet. 

A firewall does the oposite. It blocks IP packets. Or it filters : let some packets through, block others - often based on source and destination addresses, and source and destination tcp or udp ports. 

So they're not the same at all, but routers for home use often combine both functions, for two reasons. 
1- they're mainly used for internet connections. The internet is to be considered untrusted. Therefore a firewall is in order. It makes sense to combine the two in one appliance. 
2- most routers for home use "network address translation" because it allows to connect a (home) network (multiple PC's)  to the internet, using only 1 (expensive) public IP address. A side-effect of this NAT is that it allows only connections in 1 direction  : from your home to the internet. Connections initiated from teh internet towards a host on your private network can not get through the NAT mechanism, wich thus functions as a simple but effective firewall. ( [http://users.telenet.be/mydotcom/library/network/nat.htm](http://users.telenet.be/mydotcom/library/network/nat.htm) )
So "NAT" routers function as rudimentary firewalls - and cause people to think a router is also a firewall

---

### Post by mips on 2007-06-05
> **aysiu said:**
> 
So, to the security experts out there, is having a router the same as having a firewall? 

Yes and No.

You could have just a router with no firewall software or a disabled software and then have another physical firewall box in front or behind the router.
Or you could have a router with built in firewall software that is enabled, this would essentially mean you have a firewall.
NAT/PAT in itself could also act as a 'firewall' although technically speaking it deals with address translation and not so much firewalling but it could be seen as a firewalling feature.

Your firewall does not render IP Tables useless. You can further refine your firewalling with IP Tables say for example if you have two lan cards and do internet connection sharing you could finely adjust traffic patterns between the two interfaces or even between your pc and the router

---

### Post by starcraft.man on 2007-06-05
> **aysiu said:**
> Okay. I think that sort of answers my question, but a lot of those terms flew over my head.

I got a better solution than reading the wikipedia entries. It's a podcast :p.

Its called [Security Now]("http://www.grc.com/securitynow.htm") and its pretty darn good :). Some topics are only windows, but most are about security in general.

Episode 3 in the list covers NAT Routers as a firewall and why its good.  Episode 42 covers NAT Traversal technology and 43 covers open ports. Those 3 should be enough to understand why its a very good idea to use a NAT firewall. I find its the smartest security move any user can make.

Oh and feel free to listen to more of the episodes a lot are informative like how the internet works series :).

Oh and one more thing, Everyone should leave on a personal closed firewall on every machine in the network. Networks can become compromised even with NAT routers (easiest way is letting a friend connect to it with an unknowingly infected machine).

---

### Post by mips on 2007-06-05
> **starcraft.man said:**
> 
Oh and feel free to listen to more of the episodes a lot are informative like how the internet works series :).


Is'nt it just a series of tubes ;)

"Ten movies streaming across that, that Internet, and what happens to your own personal Internet? I just the other day got... an Internet was sent by my staff at 10 o'clock in the morning on Friday, I got it yesterday. Why? Because it got tangled up with all these things going on the Internet commercially. [...] They want to deliver vast amounts of information over the Internet. And again, the Internet is not something you just dump something on. It's not a big truck. It's a **series of tubes**. And if you don't understand those tubes can be filled and if they are filled, when you put your message in, it gets in line and it's going to be delayed by anyone that puts into that tube enormous amounts of material, enormous amounts of material." - Senator Ted Stevens

---

### Post by starcraft.man on 2007-06-05
> **mips said:**
> Is'nt it just a series of tubes ;)

"Ten movies streaming across that, that Internet, and what happens to your own personal Internet? I just the other day got... an Internet was sent by my staff at 10 o'clock in the morning on Friday, I got it yesterday. Why? Because it got tangled up with all these things going on the Internet commercially. [...] They want to deliver vast amounts of information over the Internet. And again, the Internet is not something you just dump something on. It's not a big truck. It's a **series of tubes**. And if you don't understand those tubes can be filled and if they are filled, when you put your message in, it gets in line and it's going to be delayed by anyone that puts into that tube enormous amounts of material, enormous amounts of material." - Senator Ted Stevens

LOL!!! How we all love our brilliant representatives (got em up here too, they just speak a bit of French and badly :D) and their eloquent explanations of complex concepts. :)

Senator stevens should be listening to Security Now :p

---

### Post by goumples on 2007-06-05
Yea routers can have a firewall.. tis called a "hardware firewall". Sometimes this needs to be configured to work, but I'll go out on a limb and say that most modern routers probably have this built and working out of the box.  It's still a good idea to run a software firewall too..

---

### Post by prizrak on 2007-06-05
OK I think I'm going to jump in. Time to remember how I explain things to my family ;)
Packet - network communication is done via packets. They are basically pieces of information of a certain length (say 16bytes). So if you sent 160byte file it will be broken up into 10 packets and sent out. Packets don't have to got as continuous stream they just have to all arrive intact. This allows for switching and routing. 

Router - a device that routes packets BETWEEN networks, such as your home/office network and the internet. Think of an on ramp to southbound highway and northbound highway to put it simply the router will decide whether it goes south or north.

Switch - sends packets to specific computers on the network. All home routers have a built in switch, they send packets to the computer it is intended for. As in it knows that 192.168.1.102 is sitting on the left most port and will ONLY send those packets there. It changes in wireless networks as stuff has to be broadcasted.

Firewall - software/device that controls access to a network/computer. For instance if you have SSH open on your desktop and you only want your laptop to talk to it, you will set up your firewall to not allow anyone else. It can be done with the IP address, host name or the MAC (physical fixed as opposed to virtual that can change) address of the computer. It can also control port access, so for instance you want people to access your webserver but not your FTP server. So you will allow connections to port 80 but not 21. 

NAT (network address translation) Firewall - a very basic firewall that will simply hide your computers. Basically if I'm connecting from the outside of your network all I see is the gateway (that's the proper name not router) but not your internal network. It helps in the sense that no one from the outside can see what services you are running on your computer and be able to exploit any vulnerabilities. 

All home routers/gateways have a NAT firewall, that is what allows them to share in essence one IP address with a bunch of computers. Some newer routers have an SPI (stateful packet inspection) firewall, this is alot more advanced than a simple NAT firewall, it will allow for not only port blocking but will also inspect all the packets to make sure that they are what they say they are. So if a packet is disguised as legitimate traffic (say an HTTP packet) but is really something malicious the firewall will not let it through.

IPtables/ipchains is a local firewall as opposed to a global one. Your router/gateway will only protect from attacks from the internet. So if you say have a wireless network and someone connects to it, they will have full access to your home machines if they are not running their own firewall. To combat that some routers allow you to separate wireless and wired networks. This means that a firewall will inspect all the traffic that tries to get from the wireless to the wired side and vice versa. Also a WPA encrypted wireless network is pretty difficult to get onto (far as I know impossible in the sense that it would take a few years to break the code) so that would also protect you. If you do this you can keep your wired computers firewall free. 

In my experience Ubuntu doesn't need firewall enabled at all since it does not listen to any connections by default. Unless your wireless systems have some sort of a service that can allow remote connections running (such as SSH, Samba server, etc...) you will not need a firewall.

---

### Post by macogw on 2007-06-05
A lot of Linksys routers run a Linux kernel and therefore have iptables.

---

### Post by xpod on 2007-06-05
Good thread.

I`ve spent the last few months myself just wondering if we`re completely safe without one of those routers?
Not in a paranoid way of course but it`s still good to know for sure that your safe from all them naughtly little kids out there.;)
We do usually have 3 pc`s running in the evening but we also have two seperate ip addresses so all i had to do to get internet on the third machine is use a spare nic & crossover cable.....with firestarter of course.

I also use firestarter & hosts.allow/deny to allow nfs between the two connected machines and ssh between mine and my sons (which uses the second ip address) but the "no router" question is still there in the back of my mind usually,especially when i see all the stuff about routers being a better option when it come to a firewall.We dont need those services running in reality but it`s fun messing about with the things...ssh anyway:)

I can flick the icmp filter option on in FS and become invisible(@shields up)but then i`ve seen others mention that not being a good idea for various reasons.
The bottom line is i aint actually got a clue whats going on in these here pipes but i`d like to think we`re safe enough even without the router.

---

### Post by dead_end on 2007-06-11
I'm probly changing the topic a bit this thread was the closest thing I have found so far.
Let me make sure I understand this..

If I want to let my home server be accessed from the internet via ssh I :

1. install open-ssh
2. tell the router to forward the port that ssh uses to the ip that my home server uses
3. I log in to the server using the IP that the ISP has given my house. ???

is that correct?

Found the answer. I just needed to search  a bit more :)

---

### Post by Boomy on 2007-06-11
Most home "routers" don't actually "route" do they? ;) 

Maybe the new Cisco Linksys ones do. My D-Link doesn't. They are mainly a PAT device with a firewall. I think all home routers have firewalls built in that allow port forwarding, blocking etc. I wouldn't connect to the internet without one.

---

### Post by prizrak on 2007-06-13
> **Boomy said:**
> Most home "routers" don't actually "route" do they? ;) 

Maybe the new Cisco Linksys ones do. My D-Link doesn't. They are mainly a PAT device with a firewall. I think all home routers have firewalls built in that allow port forwarding, blocking etc. I wouldn't connect to the internet without one.

It's because they are not routers they are gateways.

---

