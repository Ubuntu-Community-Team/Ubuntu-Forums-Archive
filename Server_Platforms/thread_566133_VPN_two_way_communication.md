---
title: "VPN two way communication"
date: 2007-10-03
forum: Server Platforms
---

### Post by twistedtwig on 2007-10-03
Hi all,

I am not 100% sure how the workings of VPN happen.  Please let me explain my situation to try and make it clearer.

I am preping a computer for my granddad to have (lives 45min drive away), it is an old XP box.  What I want to do is have a way of remotely accessing it if he needs some help.

He will have a NAT netgear modem router and I don't really want to have to open a port, for example to allow vnc in, perminently due to the security risk that could have.

He is not good enough to be able to open and close ports when required.

I had a go with hamachi but could not get it to work at all.  I dropped every filter on my firewall on the server to make sure it was not being blocked there.  I turned the windows firewall off, zone alarm off but it still didn't work.  By that I mean it would connect, but even when joining their test room I could not ping or chat to the user in there.  Also tried creating my own room and having another computer in my network connect but they could not connect to each other at all.

What I want to know / be able to do really is have a vpn server at mine that he can dial into and then I can VNC onto his computer as he is in the local network.  Does VPN work this way?  Does it allow for communications to go both ways, or can see, ping, and connect to local computers but not the other way round?

Thanks for the advice in advance

---

### Post by bluenova on 2007-10-03
Why don't you just set the port on the router to only accept incoming from your ip address?

---

### Post by twistedtwig on 2007-10-03
I have a dynamic IP address from my ISP.  would the router see my LAN ip or the public IP?

---

### Post by sonofusion82 on 2007-10-03
i personally like openvpn. relatively easy to setup for one to one connections.
you will probably need to enable port forwarding on your server side router but no need for you client side.

---

### Post by KCPokes on 2007-10-03
You may want to just look into running VNC over SSH

[http://ubuntuforums.org/showthread.php?t=383053](http://ubuntuforums.org/showthread.php?t=383053)

Will give you the security of only opening one port, SSH, along with remote access.

---

### Post by twistedtwig on 2007-10-03
sonofusion82, possibly a silly question but whats the main difference between openvpn and pptpd.  

As far as I understand pptpd is designed to minic windows vpn stuff to allow easy interactions.  Is there any large differences that would mean when he VPN's into my network it would work differently?

Does OpenVPN need to have openssl with it?  seemed to find a few guides doing both last night.  Don't want to have to deal with client keys, makes it a little less portable for the way I want to use it, (remote problem solving for friends mainly).

I have no problem opening a port for it, my issue is I don't understand it, and don't know how to install / configure it correctly (naturally don't like to open a port before I know what I am opening and ok that its not a bad idea).



KCPokes, 

I maybe missunderstanding you but doesn't what you suggest allow people to connect to only my network.  Rather than allow them to connect to my network then me take over their box.

my goal is to take over my granddads xp box remotely without leaving a port always open on his router... thought was he vpn's into my network so has a local IP I can then VNC (vnc server installed on his comp) onto his comp and show him now to fix it.

Or does the fact that they have SSH'd into the server they can now be connected to... don't think it works like that but could be wrong. (don't know SSH that well).

---

### Post by KCPokes on 2007-10-03
> **twistedtwig said:**
> I maybe missunderstanding you but doesn't what you suggest allow people to connect to only my network.  Rather than allow them to connect to my network then me take over their box.

my goal is to take over my granddads xp box remotely without leaving a port always open on his router... thought was he vpn's into my network so has a local IP I can then VNC (vnc server installed on his comp) onto his comp and show him now to fix it.

Or does the fact that they have SSH'd into the server they can now be connected to... don't think it works like that but could be wrong. (don't know SSH that well).

Essentially you'd be connecting to your Grandfather's machine via SSH, then tunnelling VNC over SSH which would allow you remote control of that machine.  I do it from work to my home machine all the time.  The only port that is required to be open is port 22, for SSH.

---

### Post by netlogic on 2007-10-03
I agree with a statement said about OpenVpn. Openvpn is easier to setup with a  nat traversal.

---

### Post by twistedtwig on 2007-10-03
So to do the SSH version I would need to install some kind of SSH server for windows on his computer?

I think I am going to read up more on OpenVPN, it sounds like it could be a wider (more complex) solution.

any recommendations on sites etc to read up on would be grand.

---

### Post by KCPokes on 2007-10-03
You can install OpenSSH on Windows; nothing really to it, other then ensuring that Windows users get set up in the server.  

I've not messed with OpenVPN, but just glancing at the documentation it looks like fun.  Still going to require you to punch some holes for access and set up Remote Desktop, or an equivalent, to take over control once you are on the same "subnet".

---

### Post by twistedtwig on 2007-10-04
The problem (I think) I have with openvpn is that it requires a client program to be installed.  This is ok for just my granddads computer but if I want to connect from anywhere randomly I would have to install stuff.

Or want to help a friend it would be an issue.

I found a page that mentioned that I might be able to get pptp to work if I manually bridge the two connections when it connects.  Not really sure how or if it would work yet but will give it a go.

ideally I need a solution that gives me access to their system without them installing stuff... i.e. uses windows native programs.  Normally will be windows as my linux buds know what they are doing ;)

---

### Post by steve.horsley on 2007-10-06
If you only wanted to do the remote control from your place (I assume you have a static IP), I would have suggested using openvpn, initiated from his side when he needs help. Then you could connect a VNC session to him over the VPN without worrying what IP address he has at the moment.

If you want to control him from anywhere, I would suggest tunneling VNC over SSH. You can set teh VNC to listen on 127.0.0.1 only, so it can't be connected to directly from the internet. I suggest you use certificates rather then username/pasword - it's more secure. You will need to know his IP address of course, so it might be an idea to bookmark a web site that tells you your public IP so he can easily find it and tell you over the phone.

---

### Post by James79 on 2007-10-06
To keep things simple, here's how I solve it.

[LIST]
[*] Install VNC
[*] On his router enable port forwarding for VNC.
[*] Setup VNC to *NOT* autostart (set the service to "manual" startup type). This takes care of the security risk aspect.
[*] On his desktop (or start menu, whichever you prefer), create 2 shortcuts.

Start Remote Desktop: %windir%\system32\net.exe start "VNC Server"
Stop Remote Desktop:  %windir%\system32\net.exe stop "VNC Server"

Verify that the service is indeed called "VNC Server". I believe that's correct but confirm to be sure.
[/LIST]

This will allow him to easily start/stop the service. Instruct him to click on start when needed, and stop when done! This solution is simple and easy :)

---

### Post by elvis on 2007-10-07
Nobody's seemed to answer these directly, so I'll have a go:

> **twistedtwig said:**
> sonofusion82, possibly a silly question but whats the main difference between openvpn and pptpd.  
Most VPN solutions require information to be tunneled over a non TCP/UDP protocol.  

See [http://en.wikipedia.org/wiki/IP_protocol](http://en.wikipedia.org/wiki/IP_protocol)

PPTP uses GRE (Protocol 47), and IPSec implementations like FreeSWAN/OpenSWAN use Protocol 53 from memory.  Again, these are not TCP/UDP ports (as many seem to confuse them with).  They are entirely different protocols.  This adds complexity to the setup because you need to open up these protocols on your firewall (or use "VPN passthrough" on cheaper routing devices, which sometimes doesn't support the protocol you want).

OpenVPN bypasses all of this difficulty by tunneling all information over a single UDP port.  This makes both firewall setup as well as NAT traversal mind-numbingly easy.

OpenVPN also uses tried and true open source security methods such as SSL and TLS to secure transmission.  This is the same level of security used by https servers, and is more than good enough for VPN use.

> **twistedtwig said:**
> As far as I understand pptpd is designed to minic windows vpn stuff to allow easy interactions.  Is there any large differences that would mean when he VPN's into my network it would work differently?
In it's simplest form, a VPN provides you with a virtual network point into another network.  Whether you use PPTP, L2TP, IPSec, Cisco VPN, Citrix, or OpenVPN (or any of the other dozens of VPN systems) it all works much the same.  You get a virtual network adapter appearing on your system that gives you an IP address that can talk through an encrypted tunnel to an entire network somewhere else.

If you use the provided OpenVPN client for Windows, Linux or MacOSX, you will get access to the remote site much like any other VPN system.  This is completely application-transparent.  Windows applications don't work any better with OpenVPN than they do with PPTP.  This is all network-layer stuff, and totally independent of the operating system and it's applications in terms of performance.

> **twistedtwig said:**
> Does OpenVPN need to have openssl with it?  seemed to find a few guides doing both last night.  Don't want to have to deal with client keys, makes it a little less portable for the way I want to use it, (remote problem solving for friends mainly).
I think you're confusing two separate items.

OpenVPN can be configured without client keys.  You can set it up so that it uses a very simple user/password challenge.  It sill uses SSL to encrypt the session, but this is all handled from the server side, rather than the standard way where each side provides a key.

> **twistedtwig said:**
> I have no problem opening a port for it, my issue is I don't understand it, and don't know how to install / configure it correctly (naturally don't like to open a port before I know what I am opening and ok that its not a bad idea).

When testing initially, open a port only to a known address.

So say your local machine is on public internet IP 1.1.1.1, and the remote is on public internet 2.2.2.2 - open UDP port 1194 (OpenVPN default) on 1.1.1.1 to allow only the single IP address 2.2.2.2 in.  This way while you are testing, you are not opening your potentially insecure system to the whole world.

---

