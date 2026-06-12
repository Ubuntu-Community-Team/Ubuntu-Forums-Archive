---
title: "Security with mixed OS's"
date: 2012-03-10
forum: Security
---

### Post by williammanda on 2012-03-10
I was reading through the sticky threads and I still have a question.
If you have a mixed operating system home network (windows and linux) and if some hacker gets into a windows computer, what can the hacker do to the linux computer? Sorry for such a basic question.

---

### Post by uRock on 2012-03-10
Depends on how the Windows system is compromised and what services are running and how they are secured on the Linux system. With a default install install of ubuntu, there isn't much can be done to the ubuntu system.

---

### Post by williammanda on 2012-03-10
On the Ubuntu computer could conversations on skype be seen or any documents be read whether their programs were open or not?

---

### Post by uRock on 2012-03-10
That depends on the router's policies. If it is forwarding all packets to all host like a hub, then yes, the Windows PC will see the communication. However, that is not the default behavior of any router I have dealt with. There are DoS attacks which will make a router do this, but I have never heard of it being used against a home network.

---

### Post by williammanda on 2012-03-10
So if my router is setup normally would GUFW and apparmor cover the Ubuntu computer if the hacker is in the network on the windows computer?

---

### Post by amauk on 2012-03-10
Don't really know much about windows security (been out of the windows world for too long), but I'd err on the side of caution/paranoia.

I'd plan for anyone owning the windows box being able do anything that you would normally be able to do sitting directly at the windows box.

This includes:
- Access to any and all files the windows box can see (local and network shares)
- Putting the network interface into promiscuous mode enabling the capture all local network traffic

---

### Post by Dangertux on 2012-03-10
This thread is heading in a positive direction in terms of tiered security solutions. Despite what a lot of people say about Linux in and of itself having a linux box on the network is NOT a tiered security solution ;-)

Okay there we go my sarcasm is out of the way now... 

So check it out basically you're describing a scenario where you're operating in a mixed environment, which is most larger networks, as well as some home networks.

The basic answer to your question is -- If a Windows machine becomes compromised, it can be used to comrpomise any other machine on the network that is reachable (and some that aren't). Likewise a compromised Linux machine can be used to do the same.

So basically a decently constructed network will have "tiers". You'll have a border router, you might have an IPS or some sort of IDS device in the border too. Depending on the size of the network you may have internal routers or firewalls enforcing some sort of ACLs. Inside it you have all your systems which should have their own secure configurations at the host level.

So basically when you break it down you have security at 3 tiers, your border, your internal ACL's (smaller networks don't have these usually) and of course your host based solutions.

Which are things like host based firewalls (UFW/GUFW iptables etc..) , Apparmor, secure configurations etc...

Does that make more sense?

---

### Post by williammanda on 2012-03-10
Yes! I will look into setting up GUFW and apparmor.

---

### Post by Jonathan L on 2012-03-11
Hi Williammanda

> if some hacker gets into a windows computer, what can the hacker do to the linux computer?Of course you'd never see a Windows machine used as a router on one of Dangertux's elegantly designed networks, but ...

Other than Trojans dressed as horses and wolves dressed as sheep, most attacks require that a compromised machine C on the local network has to find a way to intercept the traffic of the target machine T.  If for whatever reason C _is already_ the router for T, it will be able to perform all kinds of meanie-in-the-middle wicknedness without any effort.

You quite often see it in little home networks where one person enables Internet Sharing on their Windows machine and the other people's Ubuntu machines use it.  ("I'll just use this second ethernet port and enable sharing.")  If this is the case, when the Windows machine gets hacked, the Ubuntu machine is at least very observable and any cleartext passwords, credit card information and email would be observable.

The situation above is of course one of the ways of attacking any target: compromise a machine local to T,  try to supplant T's router, discover T's owner's passwords, then steal T's owner's money.

Another thing to pay attention to is what kind of local network there is: as Amauk points out, the compromised C could see anything on a local wifi network.

A compromised machine on your local network is a ladder and a big box of tools left outside your house.

Kind regards,
Jonathan.

---

### Post by Dangertux on 2012-03-11
Since someone brought up man in the middle or meanie in the middle ( I like that btw). The compromised machine doesn't have to be the router, just on the same network segment as the target machine.

---

### Post by williammanda on 2012-03-11
I have seen alot of good information but for a newbie some of it is just alittle cverwhelming. What I would like to do is give you a setup and lets start from there.
The setup is as follows:
internet>modem>router>all computers
Mix of windows / linux computers.
Based on this setup I would like to get information on protection.

2nd topic...I have looked into both GUFW and Apparmor....I'm very overhelmed to say the least. GUFW seems the easier of the two but when I looked at the log...I saw a bunch of ports being used...tcp,udp, etc...How would one go about starting? Apparmor looks like I need to be a programmer to use it. Any ideas on how a novice can hit the ground running using both of these programs or possibly others? Also how can I tell when a hacker is in my system (whether or not they are doing anything)?

3rd topic...is there is any need to worry about appliance devices ie Roku, Wii that are connected to the network?

---

### Post by williammanda on 2012-03-11
While playing around with GUFW, I started off just turning the firewall on which it denied all incoming and allowed all out going. So it would seem that I need to go through all the software that I want to use and add rules for them? If so, then I will need to know all the ports they use?

---

### Post by Thewhistlingwind on 2012-03-11
> **williammanda said:**
> While playing around with GUFW, I started off just turning the firewall on which it denied all incoming and allowed all out going. So it would seem that I need to go through all the software that I want to use and add rules for them? If so, then I will need to know all the ports they use?

Basically.

Theres a few ways to determine this. You can look up the ports your application uses with a search engine. Or turn them all on and port scan yourself. I remember there being a trick involving netstat. etc etc.

---

### Post by williammanda on 2012-03-11
Is there a way in GUFW that an ip address can be blocked without having to enter a port?

---

### Post by williammanda on 2012-03-11
A question in theory...once a port is allowed by the firewall, does that create a possible security risk or access for a hacker?

---

### Post by Dangertux on 2012-03-11
> **williammanda said:**
> A question in theory...once a port is allowed by the firewall, does that create a possible security risk or access for a hacker?


Not necessarily. Allowing communication to a port means nothing in and of itself. If there is no service running that binds to that port, the port will essentially still be "closed".

However, where the security issue comes in is if you're running a vulnerable service on the port you allowed. For instance an unpatched FTP or Samba server. This could allow a remote attacker access to the system.

Hope this helps.

---

### Post by williammanda on 2012-03-11
> **Dangertux said:**
> However, where the security issue comes in is if you're running a vulnerable service on the port you allowed. For instance an unpatched FTP or Samba server. This could allow a remote attacker access to the system.

So if I have a samba share that a windows computer has unrestricted access...then this would qualify?

---

### Post by Dangertux on 2012-03-11
Yes and no... How secure is the Windows machine? Is the Samba share accessible from the internet? Is the Windows machine?

These are all factors that come into play...

Hopefully this helps.

---

### Post by williammanda on 2012-03-12
> **Dangertux said:**
> Yes and no... How secure is the Windows machine? Is the Samba share accessible from the internet? Is the Windows machine?

These are all factors that come into play...

Hopefully this helps.

The windows computer has the standard firewall and none of the computers are accessible from the internet and neither is the samba share. This is just a home network.

---

### Post by williammanda on 2012-03-12
I'm trying to better understand how / what a hackers does or goes through to get into a normal home network. 1st they would need to know the ip address of the modem but then what? Would someone explain typically what happens?

---

### Post by Ms. Daisy on 2012-03-12
> **williammanda said:**
> I'm trying to better understand how / what a hackers does or goes through to get into a normal home network. 1st they would need to know the ip address of the modem but then what? Would someone explain typically what happens?
I had the exact same questions when I started using Ubuntu. Home use is the main focus of the basic security wiki, read it over and see if it helps. It has lots of links to additional resources.
 
[https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity) 
 
More answers can be found in the security sticky in this forum.

---

### Post by Dangertux on 2012-03-12
> **williammanda said:**
> I'm trying to better understand how / what a hackers does or goes through to get into a normal home network. 1st they would need to know the ip address of the modem but then what? Would someone explain typically what happens?

There really is no "typical" scenario. There are a variety of ways in which this can happen.

The most "well known" and least understood would be what I refer to as the nmap it netcat it method. This is simply discovering a service via a port scan (either targeted or picking out random IP's). Discovering that the service is vulnerable in some way (There are many ways a service can be vulnerable, but most of them stem from unsanitized input of some type.) Once they discover this they can exploit the service to remotely execute code on the system, this usually comes in the form of a shell , or returning the contents of some valuable file (passwd , shadow, whatever..)  . These types of attacks are best mitigated by keeping systems up to date, building strong firewall policies , and implementing strict discretionary , role based, and mandatory access controls. Additional mitigation can be achieved by utilizing the memory protection features in newer kernel versions (NX , ASLR, stack canaries, position independent executables etc..)

The most popular, and probably least understood method of compromise is via cross site scripting or cross site request forgery. These are newer tactics which target web platforms , and sometimes vulnerable browsers. They usually start by targeting a vulnerable website. If the website is vulnerable it will allow an attacker to insert custom code into the site itself. Doing so will allow them to execute that code against visitors who go to that site. This code could do anything from harvesting individual user credentials to attempting to execute traditional exploit code against a vulnerable browser. 

Secondary to this style of attack is a technique called sql injection. This is used often times to facilitate the compromise of the original website, though it can be used to compromise the server the site is running on. It's also important to note that applications (not just web type) can be vulnerable to SQL injection. ProFTP is a common example of a service that is often configured in such a manner that allows sql injection.

From the end user perspective the best method for mitigating these types of attacks are addons like NoScript for firefox (Not Scripts for Chrome) and mandatory access control policies with Apparmor / SELinux / Apparmor.

Then there is another very broad category that we lump a lot of things into. Some call it social engineering some just call them client side attacks. In any case these are basically attacks that get you to perform an action, either by sending you an email, having you click a link, visit some site.. Whatever. When you do this some type of payload will be executed, most commonly these are browser (or third party addon for browsers like flash) exploits, or simply trojans or remote access tools. The best defense against this is common sense.

Hopefully this helps.

---

