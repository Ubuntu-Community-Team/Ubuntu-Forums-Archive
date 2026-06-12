---
title: "Why is this so unpopular?"
date: 2010-11-18
forum: The Cafe
---

### Post by ki4jgt on 2010-11-18
Hey guys,
I posted an idea to Brainstorm and have only gotten about 6 votes per solution(3). I was wondering why it was such a bad idea. What was wrong with it. What I could do to make it better.

[http://brainstorm.ubuntu.com/idea/26437/](http://brainstorm.ubuntu.com/idea/26437/)

---

### Post by 3Miro on 2010-11-18
> It goes through the Internet or the LAN searching for other computers which have it installed.

Have you thought about how you are going to implement this?

I want to see your idea for the technology will do that without a centralized server.

---

### Post by ki4jgt on 2010-11-18
The technology would be the same as Alliance P2P wouldn't it? Or, is there something different involved?

---

### Post by pookiebear on 2010-11-18
1. the user would either have to know how to open ports on a firewall so it would work. Or the OS would have to be hardy enough to withstand having a public IP address. Or pieces of the managment of the "net" would have to go around a firewall like logmein does. 

2. 90% of what you are proposing can be done with a cloud based storage area like google docs or hotmail livedrive. And you don't have to go through # 1 to get there. 

3. Banks would need to accept the encryption of this type of system as viable for their Credit Card processing. IF you can make it hardy enough to withstand that scrutiny then it could be implemented in business environments. 


It's not unpopular. It just has a lot of IFs and the firewall manufacturers are going to be marketing hard against you. As you are basically replacing VPNs. Cross platforms will need to be in play. It won't make a splash if you just implement it with ubuntu.

---

### Post by 3Miro on 2010-11-18
> **ki4jgt said:**
> The technology would be the same as Alliance P2P wouldn't it? Or, is there something different involved?

So you don't search for available networks, you either create a network or use an already existing one. There is a difference.

I also don't see how you can bypass IP or DNS at some point.

At any rate, why don't you just run your own DC++ hub. You can set it up on your desktop machine at home and getting a free DNS is easy. This will give you pretty much all that you want from your description. (sharing a cap is tricky, you need to have the computers on some sort of a network inside the cab before they can talk to each other)

---

### Post by endotherm on 2010-11-18
this sounds a lot like gnuttella (the network Lime/Frostwire use)

---

### Post by ki4jgt on 2010-11-18
> Lastly, A and B share a cab. They want to share the presentation. They establish an adhoc between each other

Yes, you either create a network or use an existing one. It doesn't search for networks. That would replace the Internet altogether. (Not what I was intending.)

The point being, it would be more user friendly creating one of these. Plus, getting a DNS requires constanly updating you IP if you're behind a static IP address.

This doesn't. It just looks for the nearest computer with the encryption.

---

### Post by 3Miro on 2010-11-18
> **ki4jgt said:**
> 
This doesn't. It just looks for the nearest computer with the encryption.

There are only two ways to connect to another computer on the Internet, IP and DNS (the second being nothing more than a server that converts the string name like google.com to an IP). There is no such concept like "nearest computer". You can have somewhat of an exception on a local network, where the total number of possible IP addresses is very limited, then you can scan for one at a time (samba an windows networking does something like that).

Getting a DNS is not that hard. I have a computer on a dynamic IP and here is what I use (I have it on the router, you can install it on your computer). You can use that to setup a server at your home and then you can connect to your own server from anywhere.

[http://www.dyndns.com/index2.html](http://www.dyndns.com/index2.html)

---

### Post by ki4jgt on 2010-11-18
> **3Miro said:**
> There are only two ways to connect to another computer on the Internet, IP and DNS (the second being nothing more than a server that converts the string name like google.com to an IP). There is no such concept like "nearest computer". You can have somewhat of an exception on a local network, where the total number of possible IP addresses is very limited, then you can scan for one at a time (samba an windows networking does something like that).

Getting a DNS is not that hard. I have a computer on a dynamic IP and here is what I use (I have it on the router, you can install it on your computer). You can use that to setup a server at your home and then you can connect to your own server from anywhere.

[http://www.dyndns.com/index2.html](http://www.dyndns.com/index2.html)

I've tried DynDNS. Q: if the concept does not exist, then how does freenet and Alliance use it? They do not use any form of central server what so ever. The guy who invented Alliance even said, he has no idea how many people use the service, b/c he has no central server to keep count. The network is created and hosted entirely by it's users, who only have the software. DNS is not required! Meaning static IPs can be used. Can you explain what they are using if they're not pinging through the Internet.

---

### Post by fatality_uk on 2010-11-18
Maybe I am dense but are you suggesting that your app would search all 4 billion IP addresses (assuming that the relevant port was open on each connected PC) at say 1 second round trip per "ping" to search if it has this app?

---

### Post by ki4jgt on 2010-11-18
Alliance and Freenet may also be used on a LAN. There can't be a server except for the one's on each computer. They are VIRTUALLY impossible to block. If there were a server, it would be blockable. That is why I want this idea implemented. It would allow all computers to connect if a path between them exists.

---

### Post by ki4jgt on 2010-11-18
Am I suggesting? No, that was merely my idea of how Alliance and Freenet may do business. I understand now, that it wouldn't work, but somehow they are pulling it off! So to deny that would be even worse then not considering what I was suggesting. Because to deny that would be to deny reality.

---

### Post by 3Miro on 2010-11-18
From what I understand, in the case of Alliance and Freenet, when you create a network, you become the server (or that function is distributed between the computers involved). There is no centralized server that can be blocked, there are a bunch of smaller servers that cannot be individually tracked down. However, in order to connect to an existing network, you will have to connect to at least one of the other computers on that network and you will need an IP from somewhere (note that once a connection is established, the IP can change, unless everyone simultaneously changes their IP, computers will be bale to still find each other).

For networks that cannot be blocked or controlled, look at DC++ and BitTorrent.

---

### Post by ki4jgt on 2010-11-18
Yes, I get that, but the question is, how does your server get the IP? If it connected to a single place to get it, then your server would be compromised and the entire network would be blockable.

---

### Post by 3Miro on 2010-11-18
> **ki4jgt said:**
> Yes, I get that, but the question is, how does your server get the IP? If it connected to a single place to get it, then your server would be compromised and the entire network would be blockable.

You get your IP from your ISP (Internet Service Provider). I have a modem that is connected to Comcast ISP and I get an IP from them. Then I can run any software that I want and other people can connect to me if I tell them the IP (or DynDNS).

---

### Post by ki4jgt on 2010-11-18
- I start my Freenet server
- It doesn't have central server to connect to to find out the other IPs on the network. If it did, then it could be blocked. (So how does it know where to connect to?)

---

### Post by ki4jgt on 2010-11-18
In other words: Taking a step by step computer approach:
> 
1 - User launches freenet program
2 - freenet tries to connect (Can't connect to a specific ip or it could be block)
3 - The question now, is how does freenet get the IP to connect to? If it can't go through a central (specifi) server.
My idea was to ping, but earlier this idea was proven to be slow. How would it work then?


---

### Post by ki4jgt on 2010-11-18
It would be faster, if multiple computers could tell you other computers which were already connected.

So, my Ubuntu machine pings computers 0 - 9
computer 1 - 8 say no!
computer 9 says yes, and I can give you the connections to the rest of the network, along with IPs so you can connect to them also, until you find your computer.

Computer 9 connects you to computer 14, 15 and 20.

You now have a network of you, 9, 14, 15, and 20 and whoever they're connected to.

If you add encryption: Then the network is still networked, but has a VPN within it.

---

### Post by 3Miro on 2010-11-18
Abe, Bill and Cliff decide to get together on a network. They are all at home and each of them gets an IP from their ISP.

```
 Abe IP 1
Bill IP 2
Cliff IP 3

```

Then Abe starts the program and tells his IP to both Bill and Cliff, which then connect to Abe. Abe's computer compiles a list of IP addresses and then sends it over to Bill and Cliff.

```
 Abe IP 1, knows Bill 2 and Cliff 3
Bill IP 2, knows Abe 1 and Cliff 3
Cliff IP 3, knows Abe 1 and Bill 2

```

The three of them then can share files/talk or whatever. Then Abe decided to go to the gym and Cliff to the library. Once there, Abe and Cliff get new IP addresses from whatever ISP is available at those locations and they get IP addresses 4 and 5.

```
 Abe IP 4, knows Bill 2 and Cliff 3
Bill IP 2, knows Abe 1 and Cliff 3
Cliff IP 5, knows Abe 1 and Bill 2

```

Note that at his stage, Abe and Cliff cannot communicate directly, however, they can both connect to Bill and synchronize their lists to the correct:

```
 Abe IP 4, knows Bill 2 and Cliff 5
Bill IP 2, knows Abe 1 and Cliff 3
Cliff IP 5, knows Abe 4 and Bill 2

```

Then the evil NTFS (Nazi Terrorist Fascist Soviet) government decides to raid Bill's house and take Bill's computer down. Then Abe and Cliff can still talk to each other.

Yes, if Bill suffers power outage at the time when Abe and Cliff are driving to the gym and library, the network will fall apart. However, if you have a lot of people, this is unlikely to happen, furthermore, while laptops move around and change their IP constantly, static desktops will rarely do that. I used to know the IP for my desktop and while I was using a dynamic IP, it wound't change more than once a month.

---

### Post by 3Miro on 2010-11-18
> **ki4jgt said:**
> It would be faster, if multiple computers could tell you other computers which were already connected.

So, my Ubuntu machine pings computers 0 - 9
computer 1 - 8 say no!
computer 9 says yes, and I can give you the connections to the rest of the network, along with IPs so you can connect to them also, until you find your computer.

Computer 9 connects you to computer 14, 15 and 20.

You now have a network of you, 9, 14, 15, and 20 and whoever they're connected to.

If you add encryption: Then the network is still networked, but has a VPN within it.

You have a network with 100 computers and 4 billion possible IP addresses. Unless you know which IP to ping, you will have to ping on average 4000000000/100 = 40 million computers, before you get a hit. This is not a good number. 

Also, why would your protocol scan my computer and generating traffic and slowing my connection? If you are looking for someone, you wouldn't start knocking randomly on people's doors, this is rude at best.

---

### Post by ki4jgt on 2010-11-18
The question is, if there is NO CENTRAL SERVER to connect to how does abe tell bill and cliff his IP? Forget telephones, or IMs or any other protocal. If you use one of these to find out the IP, then it can be blocked! So, if all you have is the freenet program installed on your computer. You don't have AIM, yahoo, or MSN.

How does abe tell bill hey, this is my IP?

---

### Post by ki4jgt on 2010-11-18
NOTE: this is just what I was proposing earlier. LOL I was just building on it.

The original idea, is to do what Freenet and Alliance are doing only for a VPN.

The entire question here is: How does A get the IPs of B and C without connecting to a central network and without asking for it from B and C With that in mind:

no! You wouldn't have to ping every IP on the internet. Just a few, and they would relay you to IPs they've already pinged and had success in networking to.

It's like knocking on your neighbors doors and asking if they have a friend who's a contractor.

EDIT:This is essentially how the internet and networking in General works.

---

### Post by 3Miro on 2010-11-18
Have you actually used Freenet or Alliance over the Internet?

---

### Post by ki4jgt on 2010-11-18
Whether I have or not is irrelevant. (The only possible relevance it could provide, is to allow you to explain things better.)

What is relevant is the question I've been posing:

Mike just installed Freenet.
Freenet has never connected to any computer before (If it was programmed to connect to an individual computer upon first run. That computer or those computers could be blocked and it can not legally carry the title "Virtually unblockable" Furthermore, They would not rewrite the source code every time one of these computers was discovered, so they couldn't add any more to the program.

My Question: IF THE PROGRAM can not CONNECT TO A certain COMPUTER or network of computers, HOW does it know what network to connect to.

What you're saying is, comparable to saying: Bob and charlie are a million miles away from civilization the only communication they have is CB. Without asking what channel they are supposed to meet on and without scanning the channels and asking on each channel if the other is there. They are magically supposed to know what channel each other is on. They can't tell each other before hand. Your computer doesn't tell all the other computers in the factory "Hey, I'm going to be on IP 185.234.0.5. Call me sometime. There is no set channel. If there were, then that channel could be blasted with noise to interfere with their transmission.

And yes, I've used Alliance and Freenet both.

***EDIT: I haven't went into detail on how they work, which is why I've been asking the same question from you for the last however many times I've asked how A knows b and c's IP

---

### Post by 3Miro on 2010-11-18
> **ki4jgt said:**
> 
And yes, I've used Alliance and Freenet both.

Good, so you can explain exactly how does it work. Is it only one network or multiple networks and you get to pick which one you want to connect to, or do you have to enter a piece of information "connect here".

Theoretically you can scan, however, the question will be "how long does it take?" 4 billion IP addresses with, if say 1000 people are on line, then you will need an average 4 million pings, times 64 bytes (this is just a ping, I don't know if it is enough to scan the protocol or is it just the port) that means 256MB of information that needs to be send. I can do that in about an hour, which is not that bad, it is just wasteful, impractical and "rude". However, you are assuming that you know exactly the right port and you don't have IPv6, each one of those will multiply the number by a few thousands.

On top of the network, you also want to have encryption. Unless you want to allow random people to connect to the network (which makes encryption pretty much meaningless), you will need a way to authenticate "new comers". The idea of VPN is that you want to allow access only to selected individual, the only way to recognize another person over the Internet is via either a password or a pre-shared key (which really is a more complicated computer password).

Look, I don't want to flame you. You as why the idea is not popular, I am answering that it sounds nether practical, nor even possible.

---

### Post by ki4jgt on 2010-11-18
No no no LOL :-) I am not flamed!

I'm just asking,It logically makes no sense to me. if it is unblockable, and decentralized, Then it can't start at any particular IP. Correct? So my question is, as has been how does it know what IP to start at to get all the other IPs and if it starts at one particular IP, how does it work on LANs?

My Idea's popularity is a different matter. I want it implimented but I am siply discussing how right now.

I know it's multiple nets. and I know you enter the connection key (Don't know what it's called haven't used it in over a year)

As for it's practicality: It connects networks without depending on IP's remaining the same and without requiring the user to register for a DDNS. Posibility, is the question of the hour. How does Freenet or Alliance do it. It needs to connect both Locally and over the Internet.

Sorry for offending you. I'm just asking HOW.

---

### Post by 3Miro on 2010-11-18
> I know it's multiple nets. and I know you enter the connection key (Don't know what it's called haven't used it in over a year)

That is how it works. The connection key contains the first IP (the one that Abe has in the beginning). Once the connection is established, it will be broken only if all of the clients simultaneously change their IPs (or go offline). This can be kept alive for a long time with only a handful of Desktops, while laptops can roam around freely. This network is virtually unstoppable, because you need to take down almost all computers.

So to have something like that implemented with encryption capabilities will be nice. However, this will not be a Ubuntu thing. You can ask for Freenet or Alliance to make a FOSS version of their software for Linux and add encryption, or get someone else to implement something similar. The thing is that the program should be a general Linux program, not a specific Ubuntu feature (like Ubuntu Software Center or using UTC vs localtime).

---

### Post by ki4jgt on 2010-11-18
OK, couldn't Ubuntu do that and set the standard for any OS. Let it link all Ubuntu machines (With the user's permissiion of course) and then everyone who had an encryption to a particular network of computers would be allowed to link those computers? Just saying. . .

***EDIT: Sorry LOL don't mean to keep throwing around the same topic :-)
Thanks very much for your answer. IDK, just trying to pull together some improvements for the OS. I think it would be really cool. But anyway, it would be even cooler to somehow impliment something that wouldn't rely on IPs. I would love that!

---

### Post by Ultra Cronic on 2012-07-23
> **ki4jgt said:**
> Hey guys,
I posted an idea to Brainstorm and have only gotten about 6 votes per solution(3). I was wondering why it was such a bad idea. What was wrong with it. What I could do to make it better.

[http://brainstorm.ubuntu.com/idea/26437/](http://brainstorm.ubuntu.com/idea/26437/)
IT's NOT unpopular at all, most want more of it though.

They already have it in a way it's called Freenet / Darknet underground software 
Go here:  [https://freenetproject.org/](https://freenetproject.org/)

It's an extreme and because of that I am setting it up on a separate computer.
The learning curve is steep and long, and it seems to be geared to the Government Big Brother is Spying on me Paranoia types like myself.   Don't expect this to be another Kazaa or LimeWire but probably even worse in the Morals department, I am sure their are too many underground websites that are selling something you don't want to talk about in here let alone Buy. Google more about Dark Nets and read up, if you believe freedom of speech is worth the cost of some gross stuff staring at you in the face by accident sometimes then this is for you. Unless you are a techno-phobe and hate complicated computing then forget it, join an onion network instead some security other then the bullet proof like freenet but less scummy patrons too. I'm an advocate on freedom no matter what the cost and believe in no government making laws to protect me from myself, therefore freenet is attractive to me but be warned if you want censorship free  internetting you cannot wine and complain that all the criminals out there want it to and you will meet them their. From Good Christian underground groups to pedo's all sharing the same net. Tor networks aren't as bad but that's because the network is penatrateable and sharing too many of those mp3's could get you whacked by NIAA but seems as though they arn't looking for it rather they snooping for the real perverted stuff so study Dark net Freenet and "Deep Peep"  in google and you will have plenty of decision making to do.
There is 300,000 terrabytes of info available to the "Do Good" general public google for instance has a record of them, the dark nets and freenets have 10 times that amount of information available to the "Deep Net" witch google does not reference it's users to.
 Ubuntu and other linux distros are the better choice for these networks because the source is open making problem solving so much easier.  Windows version setup is easier but if it TANKS!!! you can't fix closed source problems.:guitar::popcorn:

---

### Post by oldos2er on 2012-07-23
Old thread closed.

---

