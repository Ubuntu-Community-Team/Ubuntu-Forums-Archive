---
title: "Can access server locally, not over internet"
date: 2008-07-17
forum: Server Platforms
---

### Post by z.s.tar.gz on 2008-07-17
*I'm a bit of a noob when it comes to the internet, but thats why I built a server*

I'm running a LAMP server and hosting a website on it, but the problem is that I can get to it locally, but not remotely. I can't access the internet with it either. This is obviously a problem.

Can anywone Help me? I would post some info, but I dont know the right commands. I'll post ifconfig later, if it will help.
 

I will attach a diagram soon showing my setup.

```
eth0      Link encap:Ethernet  HWaddr 00:a0:cc:d6:ff:76  
          inet addr:10.150.7.226  Bcast:10.150.7.255  Mask:255.255.255.0
          inet6 addr: fe80::2a0:ccff:fed6:ff76/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11374 errors:1 dropped:0 overruns:0 frame:0
          TX packets:6665 errors:5 dropped:0 overruns:0 carrier:5
          collisions:0 txqueuelen:1000 
          RX bytes:14334970 (13.6 MB)  TX bytes:553920 (540.9 KB)
          Interrupt:10 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:61 errors:0 dropped:0 overruns:0 frame:0
          TX packets:61 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6123 (5.9 KB)  TX bytes:6123 (5.9 KB)

```

---

### Post by windependence on 2008-07-17
You need to forward your port 80 back to your server IP address. This is done on your router setup.

If you still can't access it after that, try going to canyouseeme.org and check if your port 80 is open. If not, your ISP may be blocking it. If that is the case, you will need to use a dynamic host like no-ip or get a static IP from your ISP (recommended).

-Tim

---

### Post by z.s.tar.gz on 2008-07-17
How do I forward port 80? I have no Idea.
Ill google it again, maybe I missed something.

---

### Post by windependence on 2008-07-17
Google "port forwarding" for your model and brand router.

-Tim

---

### Post by z.s.tar.gz on 2008-07-18
Thanks. I couldn't find it, so I unpluged the LAN while I was loading a website, and it gave me an error message with my Local IP as the domain.

Just a tip for anyone who has an undocumented generic router.
(please correct me if I'm wrong)

But, I can't access the internet from my server.
Like, I can't install updates or software. Or browse the web with lynx.
Could my problem be from my setup?

---

### Post by Titan8990 on 2008-07-18
Many ISPs block port 80 unless you are paying for business services. Look around your router config pages for port forwarding or virtual server options.

What model router is it?

---

### Post by sp0nge on 2008-07-18
Port forwarding should set this straight. Look through the router control panel to to this. I have always been one to dive into the controls and learn by doing. As usual, Google is your friend!

---

### Post by z.s.tar.gz on 2008-07-18
Ok. I'm almost certain I can't use port 80. However:

I should be able to use almost any port I want as long as I configure apache and add it to the IP, correct? Are there any ports I shouldn't use, as I do not want to clobber up the internet for everyone in my house.

If it helps, I use a ZyXEL 660.

Edit: Would port fowarding really help with not connecting to the internet?

---

### Post by issih on 2008-07-18
Port forwarding is nothing to do with your problem of connecting to the internet from the server...

Port forwarding is entirely about getting to the server from the internet. In essence you need to tell the router to send any incoming requests on port 80 to the server's local ip address, it will be configured somewhere in your routers config web interface.

As to why you can't access the internet, I'm not entirely sure from what I've seen so far.

You appear to be have an ip address that looks sensible (10.150.7.226), but really it depends on how your local network is set up.

Are ip's assigned statically or by dhcp?
What is your router's local ip address?
Can you ping your router from the server pc?

---

### Post by z.s.tar.gz on 2008-07-18
ok.

1. The server is supposed to be static while all other comps in house should be dhcp.

2. If you mean I can get to my website by [http://localhost/](http://localhost/) then yes, but I have no Idea what you mean.

3. I can't ping the router. I get:
ping: unknown host [http://192.168.2.1/](http://192.168.2.1/)
Does this have to do with going through the wireless router?
I can access it over wireless network, and desktop next to it, but not from internet.

---

### Post by chuck jessup on 2008-07-18
> **z.s.tar.gz said:**
> ok.

1. The server is supposed to be static while all other comps in house should be dhcp.

2. If you mean I can get to my website by [http://localhost/](http://localhost/) then yes, but I have no Idea what you mean.

3. I can't ping the router. I get:
ping: unknown host [http://192.168.2.1/](http://192.168.2.1/)
Does this have to do with going through the wireless router?
I can access it over wireless network, and desktop next to it, but not from internet.

*note please read the whole post. you may find it helpful.*
i had a simular issue...who made your router? netgear and linksys are default 192.168.0.1, if you type 192.168.2.1 do you get a login interface? if so that is the network ip for your router. your desktop should be 192.168.2.2 and the server should be 192.168.2.3 and so on and so fourth. now your modem, if you are useing dsl on dhcp, you can bypass a firmware firewall in the modem (generally for home users) by loging into the modem and setting it up for PPPoE. this now makes the modem a dumb box. the router needs to be set up with your user name and password. your router will then be the connection instead of the modem. then by typeing in the dsl service ip address in the address bar you should see the website. 

now this should be done with extreame caution. make sure that your user name and password are correct. 

can you access the server via your desktop? [http://192.168.2.3](http://192.168.2.3) , this should display the site. if so see what the ip address of the service is and type it into the address bar [http://xxx.xxx.xxx.xxx:80](http://xxx.xxx.xxx.xxx:80) and  for instance [http://76.236.31.147/index.html](http://76.236.31.147/index.html) is my site. you should be able to see it via your computer by typing that address in your desktop and if so your external computers should see it (if your isp blocks port 80 then you may need to get a static (strongly agree with the others, call the provider and ask them. they will tell you) do this befor editing the modem's mode... although you should be able to reset the modem (via a reset button or other trick.) back to the original setting. again do with extreame caution.

Best Reguards
Jesse Fender

---

### Post by issih on 2008-07-18
Ok, I'm going to explain how all this works, and hope you can fill in the blanks yourself.

Your wireless router is the central element here.

In essence, it has two IP addresses, an external one and an internal one.

The internal one is where it can be reached on your local (home) network. This address will be whatever ip address you type in to a web browser to get the routers admin web interface, from what you've said I presume that is 192.168.2.1.

The external ip address will be whatever your isp assigns to it (be that by dhcp or statically and is the address you see if you go to a "what is my ip" type website.

The router effectively keeps these two identities separate and routes any data, passed to it from the local network, intended for the internet out to the external interface, and vice versa. It uses a technique called NAT to be able to provide individual connections for individual pc's on the local network (this functions by picking a unique non default port to send out http requests on for each pc).

To be able to get to the internet from the server you simply need to be connected to the local network. To do this you must assign the server an ip address on the correct subnet (THIS IS WHERE YOU ARE GOING WRONG) the ip address must match the router's internal one in the first three sections, i.e. 192.168.2.xxx. The value of xxx must be less than 255, and you must ensure it is unique on the local network, to which end you must ensure it is outside of the range of addresses the router might assign using dhcp.

After that set the subnet mask to 255.255.255.0 and the gateway address to the routers ip 192.168.2.1.

At that point you should be able to connect to the internet from the server. Connecting the other way will need you to use port forwarding, this is required because the router doesn't know which pc to send the data to. Port forwarding allows you to specify which pc on the local network will handle requests on a specific port. 

Hope that helps

---

### Post by chuck jessup on 2008-07-18
opps ... also your server should probably be teh same setup as teh service provider allows. if the service is dhcp then the server should also probably be dhcp- and visa-versa... correct me if i am incorrect...

Jesse Fender

---

### Post by issih on 2008-07-18
Nope, the server's ip is on the local network and the isp's ip is on the external one.

Th only things that care about the isp's set up in this case are the cable modem, and potentially the router, nothing else ever really knows anything about the isp, the router handles all the details.

The isp can provide the ip assigned to your modem/router either via dhcp or you can have a static address (static ip's usually cost more money though). Because of this most people have dhcp addresses from the internet (external) side. Consequently the actual ip address you need to type to connect to your router from the internet can vary from day to day. To get around this you can use a dynamic dns provider such as dyndns or noip, which basically provide a web service to keep track of your routers changeable ip address and provide easy access to it via a domain name. These services both operate for free if you accept certain restrictions.

The method by which you assign your server an ip address on your local network is entirely up to you, you can do it any way you wish, however, if you wish to use port forwarding its easiest to use a static ip.

---

### Post by z.s.tar.gz on 2008-07-18
Ok. I think I didn't make this clear earlier.
192.168.2.1 gets me to the admin page for my modem, which I seem to have called the router.

Also, both the modem and wireless router are from the same company, ZyXEL, and both seem to have the same config ip adress. How can I change that?

But I see what you are saying, that its all in the ip address.

---

### Post by chuck jessup on 2008-07-18
well i have att dsl and dhcp provided ip as i am too poor to be able to afford the static arrangement, however because the dsl modem was ment for home use the manufacture /att have a firmware firewall that blocks external ip's from quering past your modem, this provides clients a basic protection aginst hacklers. however it blocks anything wanting to view the server from doing so. you have to disable the firmware firewall and allow the router to foward the ports. as i noted my problem was only simular... and i suggested that he try the things suggested by you and others first. includeing suggesting that the fellow call his provider and ask if they block port 80.  dhcp is a pain to have with out a dns service... again i know this as i am doing it... when the fires were rageing the power would go out every time this happends for a  certain time the ip address changes.  static addresses tend to not be too much more expencive than basic service. it depends on the provider. 
im my situation i could view it on the internal network but i couldnt view it from the outside world... i did what my providfer and fellow coworkers told me to do to bipass the firewall in the modem... not all modems have this i know... 

is your router and modem one unit or two seperate ones?

Jesse Fender

---

### Post by issih on 2008-07-19
The advice about the modem having a firewall of its own is very useful...I've not come across that trick before, but then mostly I've been using adsl. Obviously any firewall in the system must be configured to let the appropriate port through, or you are going to be totally stuck :)

@chuck jessup...First up, I get the impression I upset you, sorry about that, I wasn't trying to be rude :s..you really should look into dynamic dns, it will save you lots of heartache. It basically is a little application that sits on your pc (or if your router is clever as part of its frmware) and periodically sends a message to the dynamic dns server. This allows the dynamic dns servers to update their records of the ip address assigned to your systems. You then access your home network by using a special domain name, which maps through the dynamic dns servers to find out what your dhcp address is today..It ought to make your life a lot easier..

@z.s.tar.gz...hmmn having two identical ip's the same on a network is bad news. I actually doubt you do, as I wouldn't really expect anything to work properly if this was the case, but lets find out...

Try unplugging the modem from the router, that way the only thing with that ip address connected to the network should be the router. Now go into the router's admin web interface (which should be accesible as it is now the only possible device at that ip address) and ferret about until you find a way to change its base ip address...In order to minimise the disruption only change the last number of the four, that way your subnet is unchanged.

Hope that helps

---

### Post by z.s.tar.gz on 2008-07-19
OK. My modem is ip.1, while my router is ip.2.

I used port forwarding on both to forward 80 to my server.
I only have 2 problems left. My isp blocks 80, and I have to switch back to dhcp.

Both of these should be able to be corrected if I sign up for a dynamic DNS, and use a different port. Right?

Does anyone know of a good free DNS service?

Edit: Can I use any port, or are there any I should avoid? I was thinking of using 6551 or something in that range.

---

### Post by windependence on 2008-07-19
I would use no-ip. I didn't even realize until I went to someone's page the other day that dyndns puts a stupid bar across the top. Who the heck wants that? You won't get that with no-ip, even with the free account. You'll just need to mask the URL to look like yours.

-Tim

---

### Post by totalnub on 2008-07-19
z.s.tar.gz, I have a similar setup that you are describing, although my router is a D-Link. I am assuming you are using embarq since i see you in FL? just a guess. anywho, i've set my router to Access point mode so it doesnt do any additional NAT. I set the server to receive DHCP from the 660. I then went into the zyxel 660 and forwarded all ports to the address on my server (which happens to have the internal IP of 192.168.2.8). That is what i did to allow my server to work. Also, make sure you don't have iptables or ipchains running on your server. /etc/init.d/iptables status.

The result, [http://tfl.homelinux.com](http://tfl.homelinux.com)

oh, i used the dyndns client in the 660 so i don't have to manually update with any new IP that i get from my ISP.

---

### Post by chuck jessup on 2008-07-19
> **issih said:**
> The advice about the modem having a firewall of its own is very useful...I've not come across that trick before, but then mostly I've been using adsl. Obviously any firewall in the system must be configured to let the appropriate port through, or you are going to be totally stuck :)

@chuck jessup...First up, I get the impression I upset you, sorry about that, I wasn't trying to be rude :s..you really should look into dynamic dns, it will save you lots of heartache. It basically is a little application that sits on your pc (or if your router is clever as part of its frmware) and periodically sends a message to the dynamic dns server. This allows the dynamic dns servers to update their records of the ip address assigned to your systems. You then access your home network by using a special domain name, which maps through the dynamic dns servers to find out what your dhcp address is today..It ought to make your life a lot easier..


no dude im sorry- it was a misunderstanding along with my own frustrations with problems both with the server and in life in general... as i have the understanding taht if the modem is on then the ip shouldnt really change it is when the modem loses power it resets... 
PPPoE is just one way around the issue, i did it cause nothinmg else worked, when i did it was viewable to all. so i offered up the suggestion as a possable last ditched thing that some one could do... but it can be a hastle setting the router to dial out and retreive the ip address, so i suggested that he talk with his service provider.

the missunderstanding was your reply to a second post, i mistook it as a general reply... i felt like an idiot. :) 

Jesse Fender

---

### Post by z.s.tar.gz on 2008-07-19
OK. This is everything I know:

I set my server to dhcp and it can now connect to the internet for updates, etc.

I am signed up for both no-ip, and dynDNS. no-ip works, but I havn't tested dynDNS yet because I havn't set up the software.

I can log on my server remotely using my no-ip hostname.
I log on from my laptop on my home network.

Modem: Embarq 660
Config @ 192.168.2.1
Supports DynDNS only(I don't know what that's all about though.)

Router: ZyAIR B2000
Config @ 192.168.2.2
(Seems to have less settings than modem, but I havn't explored it as much)

I have port-forwarded the following ports, all of which have failed:
80
1755
6551
I also configured apache to listen for each of these ports.

I put in: 192.168.2.35 in for both accounts, as that was what ifconfig told me at the moment.

I can access my web page from my laptop on wireless, and from my desktop.

For some reason though, I still can't access it from off the network.
I have also disabled router firewalls completely to get rid of that variable.

Please say there's something I'm missing, because I don't want to give up on this project.

---

### Post by windependence on 2008-07-20
> I can log on my server remotely using my no-ip hostname.
For some reason though, I still can't access it from off the network.

OK so which is it? You can either acces it from the outside or you can't. If you can reach the server from the no-ip domain name then you have an open connection from the outside. HOW are you able to access it? The web page? An ssh prompt? How? 

The problem here is that, no offense but you guys were changing stuff right and left at the same time and you can't troubleshoot that way. You need to do only one thing at a time and then see if it works and if not, put it back the way you found it, then go on to the next thing.

-Tim

---

### Post by issih on 2008-07-20
Ok, the advice above to troubleshoot by changing one variable at a time is bang on...I'm assuming you'd do that bit all by yourself, which might be foolish :s

Anyway, possible areas of trouble.
1) your server is now assigned its ip via dhcp, unless your port forwarding works at the mac address level or you have specified that the servers mac is always assigned a certain ip, then your port forwarding may not be working, as the router won't necessarily know which ip belongs to your server, as they change.

2) How are you attempting to log in remotely? at one point you stated that your isp blocks port 80 on incoming connections..if that is so, then you need to specify the port after the noip domain name...I'm guessing you know that bit as you are configuring apache, but it seemed worth mentioning.

---

### Post by z.s.tar.gz on 2008-07-20
Ok. This is my fault for not saying this.

I log onto my server from my laptop at home via ssh, as I don't have extra monitors/keyboards. However, I could get some if I really needed them.

Doesn't it work like:

user on internet types in my url
no-ip/dyndns translates to ip
(Problem 1. How do I include port?)
my modem forwards port X to server 
(Problem 2. Should this go to router?)
my router forwards port X to server
server sends out index.html
(problem 3. I havn't installed dyndns software, but I don't have an option for any other DNS in my router config pages.)

It should work like that right?
Or am I missing something?

---

### Post by issih on 2008-07-20
You are pretty much correct with your analysis of what should happen.

I'm not 100% sure if the modem should forward to the router then let the router forward to the server, or if the modem can forward to the server directly, you'll just have to try both.

To specify the port you want to access on you just make a url like this:

domainname:port

e.g. [http://www.google.com:2345](http://www.google.com:2345)

would try to access google on port 2345. so if your isp does block port 80 you will have to use one of the others you have set up.

Finally the dyndns bit in the router...You can use any dynamic dns provider with ny router, if you install the little client on one of the pcs attached to it which is on all the time.

Routers that have dynamic dns built in effectively have the little client application built into their firmware for certain dynamic dns providers. In your case it sounds like yours does dyndns.

If you fill out your accout details for dyndns in the appropriate section of your router's config web pages, it should just work without having to install any client software on the pc.

Hope that helps

---

