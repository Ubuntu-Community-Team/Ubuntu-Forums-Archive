---
title: "my isp uses NAT, can I access my server from another location?"
date: 2007-08-14
forum: Server Platforms
---

### Post by girard on 2007-08-14
Hi. I'm a newbie to setting up networks and connecting stuff. i have done quite some readings, but i'm sure they're still not enough.

After a couple of days trying to setup an ssh server on my 7.04, we came across the fact that my ISP is using NAT, which according to my readings and tech support, would not allow me to be accessed from the outside. i was successful at connecting to a server via ssh though.

My question is whether this only applies to ssh protocol? Or for that matter, if you are with an ISP that uses NAT, how can you setup a server  or whatever system, so that you can access your files remotely from another computer, in another location. will FTP work?

I don't have a router, so only one pc is connected to the internet. when i want to share files between my linux desktop and xp notebook, i use my samba p2p via crossover cables, and sacrifice internet connection. it works well. i also tried using ssh between the two, and it's good, but for my needs, p2p works better as far as connecting the two pc's at home is concerned.

so basically, what i want is to be able to access my files on this linux desktop when i am away. is there a way for me to do that? how?

thanks in advance!

---

### Post by lavinog on 2007-08-14
who is your isp?
what kind of isp is it? (dial-up, dsl, cable, t1)

I have seen some modems (mostly dsl) that had built in router capibilities...In which case you can log in to them with your web browser and configure it.

find your gateway ip address using ifconfig

then in your web browser go to that ip address

if you get a login screen then this is the right direction.
If you don't you may need to contact your isp

As far as using a crossover cable. get a router, it will save you the trouble and both computers can be connected at the same time...plus you can get a wireless router so you can use your laptop wirelessly

---

### Post by bjarneh on 2007-08-14
yes you probably only have a nat-address, but with DSL one usually gets a real IP for that one (this often changes from time to time, so some dynamic dns stuff is required to make this work the other way around ,ie. to contact your home machine from the outside). as you say the nat-address is not worth much on the internet so somewhere along the way a real IP has to be in place. checkout [http://whatismyip.com](http://whatismyip.com) for details :-)
to contact your machine from the outside you have to have some sort of IP forwarding to your machine with the nat address, i think this is a very common scenario, and there are a lot of howto's on it, just have to know some keywords, and i think they are all here :-)

---

### Post by mohnkern on 2007-08-14
If you're able to ssh into your box (and you aren't actually sshing into the router which is doing nat) you should be able to SFTP into your box.

---

### Post by lavinog on 2007-08-14
> **mohnkern said:**
> If you're able to ssh into your box (and you aren't actually sshing into the router which is doing nat) you should be able to SFTP into your box.


He would need to setup port forwarding though in order to connect to his box using ssh from another location (he was only able to use ssh with crossover is what i gathered)

also I have come across some routers don't allow you to forward port 22, in which case you have to setup your ssh-server to use a different port (better protection from hackers anyway)

---

### Post by girard on 2007-08-14
> 
(he was only able to use ssh with crossover is what i gathered)

that's right. communication between both system while at home is ok. 

my concern at the moment is how to access my desktop when i am not at home.

> 
you have to setup your ssh-server to use a different port (better protection from hackers anyway)


i think i've tried this already, but still, my test client couldn't establish a connection.

> 
but with DSL one usually gets a real IP


i already contacted my ISP. they said that i had a private ip. and that a public ip (which i know is the solution to all of this) is something beyond my paying capacity <searching for new ISP> :)

> 
bjarneh
so some dynamic dns stuff is required to make this work the other way around ,ie. to contact your home machine from the outside

lavinog
As far as using a crossover cable. get a router,


so are you guys saying that it is possible to access a pc with a private IP from an  ISP that uses NAT? that it is not IMPOSSIBLE?

what the tech support told me is that i needed a public IP to access my server (home pc) from another location (well of course i know they're trying to sqeeze some more dough from me). is this true?

would the router suggestion fix this problem? i mean, simply having a router at home would allow me to access my home server from a remote location (anywhere in the world)?

---

### Post by lavinog on 2007-08-14
> **girard said:**
> that's right. communication between both system while at home is ok. 

my concern at the moment is how to access my desktop when i am not at home.



i think i've tried this already, but still, my test client couldn't establish a connection.



i already contacted my ISP. they said that i had a private ip. and that a public ip (which i know is the solution to all of this) is something beyond my paying capacity <searching for new ISP> :)



so are you guys saying that it is possible to access a pc with a private IP from an  ISP that uses NAT? that it is not IMPOSSIBLE?

what the tech support told me is that i needed a public IP to access my server (home pc) from another location (well of course i know they're trying to sqeeze some more dough from me). is this true?

would the router suggestion fix this problem? i mean, simply having a router at home would allow me to access my home server from a remote location (anywhere in the world)?

I access all of my computers using the dynamic IP addresses (I don't pay extra for it).
You should go to [www.whatismyip.com](www.whatismyip.com) and figure out what your public IP address is. If your computer is saying that its IP address is the same as the ip address given by whatismyip.com then you should have no problems

If it is different then you have to setup port forwarding on the device that is assigning your ip address. 

also many ISPs do try and sell you static ip addresses by saying that it is the only way to do remote connections which is entirely untrue. I use [www.dyndns.com](www.dyndns.com) to turn dynamic ip addresses into usable urls. I do this for all of my family computers also so i can do remote maintenance. Each computer has a client program that updates the dns entry if the ip address changes.

What kind of isp are you using?
Maybe you can ask them how to forward a port (tell them that you are using a program that is requiring a port to be forwarded) if they say that they won't let you, then find a better isp. (What do you pay for your internet connection may I ask?)

---

### Post by girard on 2007-08-14
> 
if your computer is saying that its IP address is the same as the ip address given by whatismyip.com then you should have no problems


they are not the same. the output of ifconfig for inet addr is different from what websites say my IP is.

> 
If it is different then you have to setup port forwarding on the device that is assigning your ip address.


by device you mean my ISP? meaning i have to forward the port for ssh to them?

i also created a DNS there for experimentation, but i haven't totally gone over it. i'd have to read on how to forward first before i try. i also have the update client as suggested in their website.

actually, i don't really have an immediate use for what i want to figure out at the moment. nothing related to work or anything. i just wanted to set it up. you know how you only find use for things later on.

i'll try the forward thing first.

EDIT: just making sure. i can do the port forwarding even if i don't have a router?

---

### Post by lavinog on 2007-08-14
> **girard said:**
> 
by device you mean my ISP? meaning i have to forward the port for ssh to them?

Did your Isp supply you with some sort of device?
DSL companies give you a dsl modem, cable companies give you a cable modem...etc
What do you plug your computer into?


> **girard said:**
> 
actually, i don't really have an immediate use for what i want to figure out at the moment. nothing related to work or anything. i just wanted to set it up. you know how you only find use for things later on.


I am the same way...It usually comes in handy to have the experience before you actually need it.

---

### Post by girard on 2007-08-14
> **lavinog said:**
> Did your Isp supply you with some sort of device?
DSL companies give you a dsl modem, cable companies give you a cable modem...etc
What do you plug your computer into?

now i realize i don't know the difference between a dsl and cable internet. my subscription is for a wireless broadband connection. what i know is that there is an antenna on our roof, a cable from there, going into the house where it attaches to a small box, which doesn't look like a modem to me... lol. and then from there, it's connected to the LAN on my desktop (rj45). here's their webpage:

[http://www.smart.com.ph/SmartBro/Products/]("http://www.smart.com.ph/SmartBro/Products/")

i'm guessing this is... well i don't know.

i googled it, and i think it's dsl.

as for your question about my internet usage, well i'm just an average home user. but i do need broadband since i talk to my wife via yahoo's pc-to-pc calls. well on ubuntu i use skype and gyache for webcam. which is also another reason why i'm not yet getting a router - i'm due to leave for canada already.

---

### Post by girard on 2007-08-14
it says [here]("http://www.smart.com.ph/SmartBro/Products/Residential.htm")
that "once the antenna is CABLED"... so it might be cable. i'm so sorry i don't know this.

---

### Post by koenn on 2007-08-14
> **girard said:**
> tso are you guys saying that it is possible to access a pc with a private IP from an  ISP that uses NAT? that it is not IMPOSSIBLE?

what the tech support told me is that i needed a public IP to access my server (home pc) from another location (well of course i know they're trying to sqeeze some more dough from me). is this true?

would the router suggestion fix this problem? i mean, simply having a router at home would allow me to access my home server from a remote location (anywhere in the world)?

From what i gather from this thread, you have a private IP address, and the translation to a public, routable adress is done at the ISP's site. Therefore, the only connection you can establish from 'outside' is to that router, and unless your ISP sets up forwarding for you, your PC will be unaccessible. 
getting yourself a router won't help, because - all else being the same -  that router at your home will get a private, non-routable adress and would still depend on forwarding at the ISP's location to receive incoming connections. 
The Tech was right : this is not going to work, and getting a router of your own will not get you anywhere.
You need at least 1 publically accessible IP adress at your end to set up some sort of ecternal address. 

The only other possibility is that you would implement some form of source routing to force the ISP's router to route trafiic towards your private address - that means as much as writing your own ssh / ftp / ... programs to support source routing, and even then, source routing is often blocked by routers.

---

### Post by koenn on 2007-08-14
OK, I see now - you're on your ISP's private wireless network and they connect you to (the rest of) the internet. 
Anyway, what i said in my previous post still holds : unless you have either
- a public IP adress, or
- portforwarding at the nearast router  with a public address (i.e; your ISP)
you can not set up a connection towards your PC. 

It might be possible to connect to your PC from another one on the same wireless network - that depends on how the network is layed out.

---

### Post by j2fraser on 2007-08-14
If it is true that your ISP uses [[COLOR="Red"]Network Address Translation[/COLOR]]("http://en.wikipedia.org/wiki/Network_address_translation") (NAT), you should seriously consider moving to another ISP (see foregoing link)! If not, the NAT is probably occurring in a router which you have connected to your ISP's modem, through which you are accessing the Internet.

You need to arrange a dynamic DNS account and client. I know that at least some router manufacturers (e.g. Netgear) have clients built-in that report Dynamic IP changes to dyndns.org, or other Dynamic DNS providers. If you are not connecting through a router, or your router does not support such a feature, you can configure your system to do it. You may find [[COLOR="Red"]this how-to thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=247563&highlight=dynamic+dns+forwarding") informative.

If, like 90% of Internet users, you connect to your ISP's modem through a router, it is most likely your router where you need to arrange port forwarding. You should be able to login to your router as administrator and configure this. The purpose of arranging port forwarding iis essentially to allow inbound traffic (destined for a certain port) through, to a system you have designated, in your home network (e.g. connected to your router). That's what you want -- to access a specific box from "outside."

---

### Post by koenn on 2007-08-14
> **j2fraser said:**
> 
If, like 90% of Internet users,  ...
He's on a wirless network, with his NIC hooked up directly to an antenna (presumably with a built-in tranceiver). Read The Fancy Manual at [http://www.smart.com.ph/smartbro/SmartBRO%20-english%20FA.pdf](http://www.smart.com.ph/smartbro/SmartBRO%20-english%20FA.pdf) (1.2 MB) - p. 33
Basically, that makes his network card a wireless NIC connecting to an access point + router (presumably managed by his ISP)

The only chance at doing his own portforwarding is if that antenna also has a built-in router, that router supports NAt and portforwarding, and the OP has sufficient access to it to set it up. Nothing in the User Guide suggests this might be possible.

---

### Post by merkur2k on 2007-08-14
It has been my experience that wireless ISPs generally do use NAT on their border router (All of them do in my area, I used to work for one of them).
There really is no workaround, unless you have a willing and accessible 3rd party machine somewhere else on the net that can be used as a vpn endpoint or something similar (thats how I do it). Your best bet is to get something other than wireless if it is available, although i am betting it is not. Wireless internet is by nature much more expensive than the alternatives, mostly because theres alot of equipment costs involved in serving what ends up to be very few users (usually VERY rural). People use it only because its their only option.
The piece of hardware on the roof (CPE or customer premesis equipment) is usually a small single board computer with a standard pcmcia wifi card (attached to an external antenna), usually running linux. It itself often also does NAT, mostly to secure the users from each other on the wireless network.

---

### Post by j2fraser on 2007-08-14
> **koenn said:**
> He's on a wirless network, with his NIC hooked up directly to an antenna...
Oops! I should read a bit more carefully. Fully agree with the last two posts. That's a sticky spot.

---

### Post by girard on 2007-08-15
thanks a lot for the info. i'm going to try clarify things a little bit though.

my clients from the outside world cannot connect to this server because they connect to my external/public IP. but that IP is only to reference me to my ISP, which assigns me a different, internal/private IP as it forwards information/data to my computer when they pass their network. so there's no way for the protocol of the client to know what the public IP is supposed to be changed into (the private IP) as it passes through the ISP's NAT (which actually functions as a router).

i'm thinking about this though. 

i got a DNS from DynDns (gotdns), and gave them my public IP. hence: [email]mylinuxusername@dyndnsusername.gotdns.org[/email] is directed towards my public IP. but then, it's not forwarded to my private IP 

> 
ifconfig = inet addr: this.ip.add.ress


because my ISP is not directing it towards that address inside it's network.

is it not possible for them to specify that connections being done with my DNS is supposed to be translated as connections aimed at my private IP address? such that:

> 
outside client<--DNS (public IP)-->ISP<--translates to private IP-->linux server


or is there some technical impossibility here? (aside from ISP's wanting to charge more for that service)

well if this doesn't work at all, at least i know now to look for an ISP that offers public IP's.

---

### Post by koenn on 2007-08-15
network applications (mail, web browsing, ssh, ... whatever service you want to provide) connect to ip-adresses and ports, not DNS names. DNS names are mainly for human use - the applications take the name and lookuip the corresponding address. 
That's what DNS does : give an adress. After that, only the address is used. 

So all your ISP sees is connections  (packets) coming to isp.public. ip.address. They have no way of knowing which ones of all those packets are to be routed to your.private.ip.address - at least for new connections. For packets that are in reply to connections that you've set up, the NAT router has remembered which ip-adress and tcp/udp port they came from, and sendfs the replies back to that adres/port.

What you need is - eg to run a webserver is something like
```

outside client        -->   isp NAT router                  -->  your linux srv
connects to                  translates                                apache
ISP.public.ip.addr:        ISP.public.ip.addr: xxx            listening on
port xxx                        to                               tcp port 80
                          your.priv.ip.addr : 
                          port 80 tcp

```

If your ISP is willing to do that, they mlight as well give you a public address, way easier for them to set up and maintain.

---

### Post by girard on 2007-08-15
i guess there really is nothing i can do. i removed openssh-server from my system already.

at least i now what to look for an ISP. i'll check out the others for public IP's, then maybe i'll post here again - if i still don't get that one to work.

---

### Post by paulg on 2007-08-15
I know of one program that is known to work well in NAT scenarios but given your situation in dealing with clients, probably more hassle than it's worth.

The application is [Hamachi]("https://secure.logmein.com/products/hamachi/vpn.asp?lang=en") and it provides secure tunnelling between two or more PC's, will tunnel through some NAT routers and some firewalls, installs on windows, mac and linux, effectively gives an instant [near] 0 configuration secure VPN. I have it installed on all my home computers and while travelling use my laptop to securely access an http proxy, NFS shares, samba shares and any other server (ssh, slimserver...) I may miss while away from home. There are free and premium clients, I use the free one.

As I said, it may not be ideal/practical to install on client's systems but may be a workable solution for you. There is a free service in addition to the pay service. The pay service adds a few features and gives you a proxy fall back where direct tunnel cannot be made.

There's lots of information on their [website]("https://secure.logmein.com/products/hamachi/support.asp") and in the [hamachi forums]("http://forums.hamachi.cc/"). I am not in any way affiliated with LogMeIn or Hamachi, just a satisfied (free client) user.

If anyone has any questions I'll try to answer but anything beyond the basic security/networking provided in Hamachi is beyond me.

---

### Post by girard on 2007-08-16
i checked it out. it looks promising. is this what merkur2k was referring to in this quote:

> 
here really is no workaround, unless you have a willing and accessible 3rd party machine somewhere else on the net that can be used as a vpn endpoint or something similar (thats how I do it).


one thing i didn't get in their website though, is whether the same application should be installed on all clients for them to establish a connection. (well that would really be just me you know... lol).

my wife is going to kill me as i'm using her notebook as a test client.. had her install winscp.. and now this one...   :roll:

---

### Post by koenn on 2007-08-16
You will probably have to install at least something on the private-address server, some piece of software that connects to a LogMeIn-server. That's the only way you can work around the private adress problem : because the connection is initiated by your server, the NAT router at your ISP can route back to it - and it's quite similar in concept to what merkur2k  suggested. 

I couldn't find much info on how it works at their website, just a lot of marketing blahblah about how easy it is, so I can't actually tell if it will work for you, how exposed your server wil be, and so on.

---

### Post by paulg on 2007-08-16
A little more info... (this is a hobby for me so my security/networking terminology may be a little weak):

Most of my information comes from the [Security Now!]("http://www.grc.com/securitynow.htm") podcasts (episodes 19 and 20 are relevant - and looks like they discuss the buyout by LogMeIn which I haven't actually listened to yet).

Hamachi assigns everyone a 5-point IP (that is 5.x.x.x). Anyone intimately familiar with networking knows that the 5-point IP range is unassigned - and it's not - unless you're on the Hamachi network. The software creates a virtual device using tun/tap drivers. The device is ham# (ham0 under normal installs) for Linux and Mac.

In my [rudimentary] understanding, everyone installs the same client/server software. Only the Windows client has a GUI (and a few extra features as a result I believe). Everyone connects to the Hamachi server which stores the location of every client and returns the *real* IPs to clients of the same network. The Hamachi (/LogMeIn) servers only mediate the connection between two clients and no data is actually transfered. As I understand it, if you have the premium version you can use the Hamachi servers as a proxy. I have no idea if they limit data or not. 

Connections between clients occur on the Hamachi interface and only clients allowed on the private network you create can connect to that interface. All connections between clients are encrypted (off the top of my head 256-bit RSA ... Not sure about that). On top of that you have all the normal security measures in your servers. So you want to run an SSH server? Bind it to your Hamachi device and only computers on your secured network will be able to connect! Connections between clients are on UDP but services like SSH that use TCP/IP can be tunnelled through the connection. 

I have networks for my home network, to my brother's network, and to a friend's network. I can go on-line or off-line on any of the networks. If I am online all of them then my brother does not see my friends LAN, only the computers he and I share. So if you had multiple clients that need some privacy you can set up separate networks for them and you clients would not be able to connect to each other, only you. If you set up a network for your system and your wife's laptop she will not see your client's computers. My passwords are 60+ random characters long (same as WPA wireless security) so it's not like someone could just arbitrarily guess the network passwords and gain access to my servers. It _could_ happen I suppose, but it is such an extremely low probability that it's not worth my time worrying about it. If I were, I could change the passwords more often.

I am behind a NAT router and so are the majority of the systems I connect to. I do not forward any of the ports on my NAT router and have no trouble accessing computers hundreds of kilometres away that are also behind NAT routers also with no ports forwarded. I have my parents Windows boxen setup behind a linux hardware firewall and they cannot connect to me. This is the only time I have experienced this with Hamachi. If I opened some ports and forwarded them it might work but ALL ports on the firewall are stealthed (and it's more important to me to keep it that way than to try to make a Hamachi connection).

That's all my information. If you need more information I recommend listening to the Security Now podcasts mentioned above. The podcasts do a great job of explaining it in terms lay people (and technical people) can understand. If it's piqued your interest try installing the client on a couple machines and I am sure it will become much clearer!

---

### Post by paulg on 2007-08-16
I should also mention that as with anything you shouldn't take the security for granted and should monitor the Hamachi/LogMeIn site for updates. Don't just take my word for it, educate yourself about it before you commit to using it.

---

### Post by girard on 2007-08-17
> **paulg said:**
> I should also mention that as with anything you shouldn't take the security for granted and should monitor the Hamachi/LogMeIn site for updates. Don't just take my word for it, educate yourself about it before you commit to using it.

thanks a lot, but it didn't quite work for me. the webcam plus application they have doesn't have a version for linux, and it doesn't work with wine either (or i might not configured wine properly?) thanks anyway. i've given up on remote access with this ISP already. i won't be with them for long though.. so it's okay...

thanks a lot to all you guys who help out. i did learn quite a few regarding this issue.

---

### Post by koenn on 2007-08-17
it turned out to be an interesting problem. Thanks for bringing it up  :)

---

### Post by lavinog on 2007-08-19
I know that this isn't exactly what you would want to do, but it shows that there is hope
[http://www.uvnc.com/addons/nat2nat.html]("http://www.uvnc.com/addons/nat2nat.html")

UltraVNC has a NAT-to-NAT connector for similar situations
it takes advantage of an external server on the internet to connect the two computers

It is for windows, but it should work with wine

It also may take some scripting to keep the connection alive.
You can also set it up so that it is only active during times that you are out of the house.

on a side note: you may be able to use a network switch so that you don't have to disconnect cables every time.

EDIT: UltraVnc provides access to transfer files, and offers some encryption too

---

