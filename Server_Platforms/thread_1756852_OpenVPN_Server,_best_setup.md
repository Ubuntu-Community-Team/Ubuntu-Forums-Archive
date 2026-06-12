---
title: "OpenVPN Server, best setup?"
date: 2011-05-12
forum: Server Platforms
---

### Post by JoeGoalie on 2011-05-12
So, I think I can setup an OpenVPN server following guides, but I'm not sure if it will work correctly.  I'm a little bit "gun shy" so to say because I've had no luck setting up a Windows VPN solution.  I've searched and searched and it seems several other people have had my exact problem so I'm moving on.  Now, I'm experienced in setting up a more advanced network like this so I would like some input.  Right now my setup is like this:

ISP->Modem->Router(DHCP)->internal network including my server box and laptops

My server box is a PC running Ubuntu and I would like to virtualize the actual serving OS.  The host OS will be Ubuntu and the guest OS will be Ubuntu with OpenVPN setup and a "bridged" connection in Virtualbox so it gets it's own IP.  That box has a single NIC.  Can I run OpenVPN like this?  Or do I need to have it between the modem and the router with two NICs, another possibility is adding it to the DMZ on the router.

Thanks in advance

---

### Post by samosamo on 2011-05-12
Yes it will work virtualized. Don't be "gun shy." VPN is usually tough for beginners as it requires basic networking skills, but this forum is very helpful if and when you get stuck.

---

### Post by JoeGoalie on 2011-05-12
> **samosamo said:**
> Yes it will work virtualized. Don't be "gun shy." VPN is usually tough for beginners as it requires basic networking skills, but this forum is very helpful if and when you get stuck.

Will it work with the setup I have? The server being behind the router's NAT, DHCP, etc...? I understand that OpenVPN can be setup bridged or routing. What is the practical difference and what should I go for? 

Basic network knowledge is what I have. I'm a system admin in the USAF, but I'm only about a month out of tech school.

---

### Post by collisionystm on 2011-05-12
Make sure you find out what kind of port forwarding needs to happen in your router.

---

### Post by JoeGoalie on 2011-05-12
> **collisionystm said:**
> Make sure you find out what kind of port forwarding needs to happen in your router.

As far as I know, OpenVPN uses SSL. That port should be opened...

---

### Post by collisionystm on 2011-05-12
You should check ;)

---

### Post by JoeGoalie on 2011-05-12
> **collisionystm said:**
> You should check ;)

Good call... Port 1194. I would have seen it in the guides. :P

---

### Post by spynappels on 2011-05-13
Is there a specific reason you want to run OpenVPN on the virtualised guest OS?
You could run it on the Host machine and use it to route traffic to the guest VM.
Either way, I'd suggest using a non default subnet for your LAN subnet to avoid routing conflicts from remote clients and use OpenVPN in routed mode. 

I have set up quite a lot of these systems, so if you have questions, just ask.

---

### Post by JoeGoalie on 2011-05-13
> **spynappels said:**
> Is there a specific reason you want to run OpenVPN on the virtualised guest OS?
You could run it on the Host machine and use it to route traffic to the guest VM.
Either way, I'd suggest using a non default subnet for your LAN subnet to avoid routing conflicts from remote clients and use OpenVPN in routed mode. 

I have set up quite a lot of these systems, so if you have questions, just ask.
I want to run it virtualized for a couple reasons.  It's very easy to do a snapshot and recover to it also, I plan a hardware upgrade very soon and exporting to the new hardware should be easy if virtualized.

Would there be routing conflicts if I assigned it a different scope?  My router is assigning a scope of x.x.0.100-253, the VPN server could easly do x.x.0.50-99 and serve it's role.

---

### Post by JoeGoalie on 2011-05-13
To add to this, is there a way to have Ubuntu join a Windows domain?  I plan on using Windows Server 2008 as a domain controller with active directory.

---

### Post by spynappels on 2011-05-13
Ok, there is no issue running it virtualised, was just curious. 

Now on the routing issue. By default OpenVPN will hand out addresses in the 10.8.0.0 network, so that is no problem. The thing is that your home LAN uses the 192.168.0.0 network, which is a very common network subnet. Now imagine that you are in a remote location and you are connected to a local LAN using the 192.168.0.0 subnet. You fire up the VPN and you can ping the VPN server no problem on 10.8.0.1 but when you try to access something on your home LAN using your home LAN IP at 192.168.0.150 for example, you will have issues, as your computer will have no way of telling whether you want 192.168.0.150 on the network you are directly connected to or if you want 192.168.0.150 on your home LAN. 

There are 2 main ways round this. 

1: Change your home LAN subnet. In my opinion this is the best long term solution. 
2: Run OpenVPN in bridged mode. Takes some more setting up and will not always work as expected on OSs which do not natively support bridging network adapters. 

On most small home LANs, changing the subnet to something like 192.168.45.0 is quite easy to do and gives more bombproof results.

---

### Post by spynappels on 2011-05-13
As for the domain question, I know it can be done, using LDAP or Samba IIRC, but I don't know enough about that to be of much use to you on that.

---

### Post by JoeGoalie on 2011-05-13
Excellent explanation on the IP thing. That change should be very easy. Why would OpenVPN use a different IP range though? Should I change it to match my normal IP range?

---

### Post by spynappels on 2011-05-13
No, you need to have the subnet of the VPN interface different to your main subnet. Do you want to post your server.conf file to check the settimgs on it?

---

### Post by JoeGoalie on 2011-05-13
> **spynappels said:**
> No, you need to have the subnet of the VPN interface different to your main subnet. Do you want to post your server.conf file to check the settimgs on it?
I haven't actually started building it yet.  It's going to be my weekend project I'm sure.  What is the reason the VPN server must be a different subnet? Is that just the server or the box its on (not the host box just the virtualized one)?

---

### Post by YesWeCan on 2011-05-14
OpenVPN emulates a new ethernet adaptor in your computer. You can't have two ethernet adapters using the same subnet. OpenVPN also provides a DHCP service on its subnet for connecting VPN clients and this would conflict with your router's DHCP function if it used the same subnet.

I use OpenVPN all the time. It is excellent, IMO. I don't run it in VB but I don't see any reason not to, other than some reduced performance.

---

### Post by YesWeCan on 2011-05-14
> **spynappels said:**
> 2: Run OpenVPN in bridged mode. Takes some more setting up and will not always work as expected on OSs which do not natively support bridging network adapters. 

On most small home LANs, changing the subnet to something like 192.168.45.0 is quite easy to do and gives more bombproof results.
Yes. I found it was also a problem in bridged mode if both subnets have devices with conflicting IP addresses, say both routers at 192.168.1.1. This confuses VPN and stops redirect gateway working. You may know some work-arounds I do not. So, since it is easy-peasy to make your server's LAN an unusual subnet range then do this.

---

### Post by YesWeCan on 2011-05-14
Oh, a quick tip while I remember. There is a problem with OpenVPN/Nautilus when doing large file transfers using the UDP/tun protocol. Sometimes they appear to hang up. No problem using sftp, tho. It took me ages to track this down and although I never figured out why this happens the fix is to add the line 'mssfix 1200' to the server and client config files.
[http://openvpn.net/index.php/manuals/427-openvpn-22.html](http://openvpn.net/index.php/manuals/427-openvpn-22.html)

---

### Post by JoeGoalie on 2011-05-15
I'm done messing with it for tonight, but I can't get it to connect. I believe I've setup everything correctly. Maybe it doesn't connect because I'm trying to connect the host OS to the guest OS? I just realized it could have to do with that IP scope issue... The dialog box gets all the way to mentioning ipv4 and then just stops. I'll post my server config, client config, and my dialog box tomorrow. Right now my brain needs sleep  :P

---

### Post by JoeGoalie on 2011-05-15
Ok, the server connects, but I can't get the client to connect.  Which might just be the issue that's its actually the host connecting to the guest, meaning they're already on the same network.

Client OpenVPN connection dialog box
```
Sun May 15 10:22:13 2011 OpenVPN 2.1.1 i686-pc-mingw32 [SSL] [LZO2] [PKCS11] built on Dec 11 2009
Sun May 15 10:22:13 2011 WARNING: No server certificate verification method has been enabled.  See http://openvpn.net/howto.html#mitm for more info.
Sun May 15 10:22:13 2011 NOTE: OpenVPN 2.1 requires '--script-security 2' or higher to call user-defined scripts or executables
Sun May 15 10:22:13 2011 LZO compression initialized
Sun May 15 10:22:13 2011 Control Channel MTU parms [ L:1542 D:138 EF:38 EB:0 ET:0 EL:0 ]
Sun May 15 10:22:13 2011 Data Channel MTU parms [ L:1542 D:1450 EF:42 EB:135 ET:0 EL:0 AF:3/1 ]
Sun May 15 10:22:13 2011 Local Options hash (VER=V4): '41690919'
Sun May 15 10:22:13 2011 Expected Remote Options hash (VER=V4): '530fdded'
Sun May 15 10:22:13 2011 Socket Buffers: R=[8192->8192] S=[8192->8192]
Sun May 15 10:22:13 2011 UDPv4 link local: [undef]
Sun May 15 10:22:13 2011 UDPv4 link remote: 173.217.***.***:1194
```Client config file
```
## client01.ovpn ##
client
dev tun
dev-node OpenVPN
proto udp
remote ******.dyndns.org 1194
resolv-retry infinite
nobind
persist-key
persist-tun
ca ca.crt
cert client01.crt
key client01.key
comp-lzo
verb 3
```Server config file
```
## server.ovpn ##
local 192.168.42.3
port 1194
proto udp
dev tun
dev-node OpenVPN01
ca ca.crt
cert mcserver.crt
key mcserver.key
dh dh1024.pem
server 10.8.0.0 255.255.255.0
ifconfig-pool-persist ipp.txt
push "route 192.168.42.0 255.255.255.0"
keepalive 10 120
comp-lzo
max-clients 11
persist-key
persist-tun
status openvpn-status.log
verb 3
```

---

### Post by spynappels on 2011-05-15
Hi Joe,

You are getting there! I think the issue you have here is that you are trying to connect to the OpenVPN server using your public IP address from inside your LAN. Many modem/routers do not allow you to do this. A better test would be to try to access your VPN from a remote location. 

I checked, and port 1194 is showing as closed on your public IP (which you might want to edit out in the error message;) )

Can you double check those two things and report back?

---

### Post by JoeGoalie on 2011-05-15
> **spynappels said:**
> Hi Joe,

You are getting there! I think the issue you have here is that you are trying to connect to the OpenVPN server using your public IP address from inside your LAN. Many modem/routers do not allow you to do this. A better test would be to try to access your VPN from a remote location. 

I checked, and port 1194 is showing as closed on your public IP (which you might want to edit out in the error message;) )

Can you double check those two things and report back?
Oops, good call on editing out, lol.  I did in the config file, but forgot the stupid error.

I just checked my router, the 1194 port is forwarded to the correct IP.  Maybe it's a firewall issue on that box? [edit: added 1194 udp exception to my firewall]

I'm trying to setup my Android phone as a client (CM7 supports this), I'm just creating my .p12 cert now.  That is really the only way I can test a remote IP right now.

---

### Post by YesWeCan on 2011-05-15
Or just change the IP in client.conf to be the local LAN IP of the server.

---

### Post by JoeGoalie on 2011-05-15
> **YesWeCan said:**
> Or just change the IP in client.conf to be the local LAN IP of the server.
Nice, this worked.  So, I'm assuming since I'm showing connections on both client and server, if I set it back to the external IP, when I'm at a remote location it should work?  Is there any other way of testing from here?

Now I'm having issues making this stupid .p12 file that Android requires...  When I tried to use my client02.crt just on it's own it said there wasn't a certification!  When I tried the ca.crt it worked... Wtf, is it possible my client02.crt file got fubar'ed?

---

### Post by spynappels on 2011-05-15
> **YesWeCan said:**
> Or just change the IP in client.conf to be the local LAN IP of the server.

That is true, but then he could get a whole bunch of routing errors as per my earlier post. It would check the authentication between server and client though.

---

### Post by spynappels on 2011-05-15
> **JoeGoalie said:**
> Nice, this worked.  So, I'm assuming since I'm showing connections on both client and server, if I set it back to the external IP, when I'm at a remote location it should work?  Is there any other way of testing from here?

Now I'm having issues making this stupid .p12 file that Android requires...  When I tried to use my client02.crt just on it's own it said there wasn't a certification!  When I tried the ca.crt it worked... Wtf, is it possible my client02.crt file got fubar'ed?

Ok, we posted at the same time.....

Is your Android rooted? I've had issues with OpenVPN on a non-rooted phone.

---

### Post by JoeGoalie on 2011-05-15
> **spynappels said:**
> Ok, we posted at the same time.....

Is your Android rooted? I've had issues with OpenVPN on a non-rooted phone.
Of course ;).  I've been using (and rooting) Android since the G1, I currently have a N1 with CM7 installed (waiting on the Samsung Galaxy SII for my next phone).  CyanogenMod has had built in support for OpenVPN since CM6.  So, there are guides, I'm using this one:

[http://blog.attomsoft.com/android/134/how-to-configure-openvpn-on-android-cyanogenmod](http://blog.attomsoft.com/android/134/how-to-configure-openvpn-on-android-cyanogenmod)

I'm just having some difficulties getting that .p12 file.  When I go to import it in Android it tells me my password is wrong.  I don't know if it's asking for the export password I made or the storage password I made on Android.  Neither password works though.  That's when I tried the ca.crt and client02.crt separately and it said the client02.crt didn't have a certificate.  I'm going to go back to my original easy-rsa/keys folder and grab a copy of the client02.crt and try again.

---

### Post by JoeGoalie on 2011-05-15
Hmm, second try with that and the .p12 password still isn't right appareantly (and this time I set the export password as the same password I'm using for credential storage...). Does anyone know a better way to make a .p12 cert?

Also, the client02.crt "No certificate to install" is a normal Android thing it appears.
[http://forum.cyanogenmod.com/topic/17418-vpn-openvpn-issue-cant-install-user-certificates/](http://forum.cyanogenmod.com/topic/17418-vpn-openvpn-issue-cant-install-user-certificates/)

---

### Post by spynappels on 2011-05-15
Ok, I don't have any experience in getting it to actually work with Android, so I can't help you there. But it sounds like you have the OpenVPN end sorted out. Well done!

---

### Post by JoeGoalie on 2011-05-15
> **spynappels said:**
> Ok, I don't have any experience in getting it to actually work with Android, so I can't help you there. But it sounds like you have the OpenVPN end sorted out. Well done!
Maybe you can help decipher this for me? This was another way to create the .p12 file.
```
openssl pkcs12 -export -in *usercert.pem* -inkey *userkey.pem* \
                -out *your-new-packed-cert.p12*
```Four files were created when I made the client02 cert.

client02.crt
client02.key
client02.csr
03.pem

There is only one .pem file, what is the usercert.pem and the userkey.pem?  I'm thinking the usercer.pem is the 03.pem and the userkey.pem is actually the client02.key.

---

### Post by JoeGoalie on 2011-05-15
Never mind, apparently the password didn't like having a ! in it.  My phone is now connected on a remote IP.  I still have to try and connect it to a program on my VPN or something to test it out.

I noticed my client won't stay connected to the server.  The connection eventually drops and it only reconnects if I manually tell it to (it tries to auto reconnect, but doesn't make it pass the ipv4 thing in the dialog box).  I'll be able to test it out remotely at work tomorrow.

---

### Post by JoeGoalie on 2011-05-15
So, even though my server shows connected, my host OS shows connected (client01), and my Android shows connected (client02), nobody can ping anything on the network.  It's connected, but nothing is getting sent back and forth?  I tried to ping (from client01) my router 192.168.42.1 - timed out, server 192.168.42.3 - timed out, vpn assigned IP server ping 10.8.0.1 - timed out, client02 10.8.0.10 - timed out...  What gives?  All show connected?

---

### Post by spynappels on 2011-05-15
To allow you to ping other clients, you need to have the ```
client-to-client
```
line in your server.conf file.

To be able to access resources on your LAN, you also need to enable ipv4 forwarding in sysctl, I cant remember the syntax exactly but a quick google should help there.

I'm not sure why you cannot ping the VPN server though, as that should work unless you have disabled it using the firewall, you may need to check that all tun0 traffic is allowed in your firewall.

---

### Post by JoeGoalie on 2011-05-15
> **spynappels said:**
> To allow you to ping other clients, you need to have the ```
client-to-client
```line in your server.conf file.

To be able to access resources on your LAN, you also need to enable ipv4 forwarding in sysctl, I cant remember the syntax exactly but a quick google should help there.

I'm not sure why you cannot ping the VPN server though, as that should work unless you have disabled it using the firewall, you may need to check that all tun0 traffic is allowed in your firewall.
Added that line to the config file, made sure my router was not protecting the tap and I still can't ping anything on the network.  I'm done for today, too frustrating and too nice a day to not go enjoy it.  I've tried windows VPN's and now OpenVPN, it seems I just can't get one to work.  It's really disappointing.

---

### Post by spynappels on 2011-05-15
Hang in there, it will work for you, we just need to find the right buttons and push them.

---

### Post by JoeGoalie on 2011-05-15
> **spynappels said:**
> Hang in there, it will work for you, we just need to find the right buttons and push them.

I'm at a loss for what to do next though. :/

---

### Post by YesWeCan on 2011-05-15
sudo -i
echo 1 > /proc/sys/net/ipv4/ip_forward

For security reasons the kernel disallows packet forwarding by default. To enable this on each boot you need to uncomment a line in /etc/sysctl.conf.

---

### Post by spynappels on 2011-05-16
> **YesWeCan said:**
> sudo -i
echo 1 > /proc/sys/net/ipv4/ip_forward

For security reasons the kernel disallows packet forwarding by default. To enable this on each boot you need to uncomment a line in /etc/sysctl.conf.

Thanks YesWeCan that's what I could not remember off the top of my head. I tend to just edit sysctl.conf

---

### Post by YesWeCan on 2011-05-16
> **JoeGoalie said:**
> I'm at a loss for what to do next though. :/
Have you read the section "Expanding the scope of the VPN to include additional machines on either the client or server subnet." here: [http://openvpn.net/index.php/open-source/documentation/howto.html#scope](http://openvpn.net/index.php/open-source/documentation/howto.html#scope)

> First, you must advertise the 10.66.0.0/24 subnet to VPN clients as being accessible through the VPN. This can easily be done with the following server-side config file directive:

push "route 10.66.0.0 255.255.255.0"
Next, you must set up a route on the server-side LAN gateway to route the VPN client subnet (10.8.0.0/24) to the OpenVPN server (this is only necessary if the OpenVPN server and the LAN gateway are different machines).

Make sure that you've enabled IP and TUN/TAP forwarding on the OpenVPN server machine.

Note that your VPN client packets source IP will be the VPN IP of that client. You may want to think about how a PC on your server's LAN replies to this address.

I recommend these directives in both server and client configs:
user nobody
group nogroup
mssfix 1200

---

### Post by YesWeCan on 2011-05-16
> **spynappels said:**
> Thanks YesWeCan that's what I could not remember off the top of my head. I tend to just edit sysctl.conf
This originally kept me stumped for days as I recall. :P

---

### Post by YesWeCan on 2011-05-16
BTW JoeGoalie, as you are a System Admin you may want to discover the Wireshark application (it's in the Ubuntu Software Centre"). Very useful. :)

---

### Post by JoeGoalie on 2011-05-16
I guess I have to make a little confession. After looking up ways to add Ubuntu to a Windows Domain and Active Directory I decided to try using Windows Server 2008 R2 to setup the VPN (I'm a sysad or the USAF and we use a lot of Windows, it's what I'm used to). I think I'm going to have to abonden that route and instead try it back in Ubuntu where this extra help is relevant. I used to be a big Ubuntu user and prefer it, but the drivers on my laptop don't work quite right (to the point where I would like to buy a new laptop so I can run Ubuntu again). I'm not really sure how to setup user permissions and what not Ubuntu. It's easy in Windows I can just right click the file/folder and go to the security tab. I'm thinking now I should rebuild the VPN server on an Ubuntu platform (shouldn't be hard, just more practice :p) and then run another virtual box with Windows as my file server. They'd both be virtualized on the same box so it should in theory work nicely.
 
I guess I know what I'm doing this afternoon after work, lol.

---

### Post by JoeGoalie on 2011-05-16
> **YesWeCan said:**
> BTW JoeGoalie, as you are a System Admin you may want to discover the Wireshark application (it's in the Ubuntu Software Centre"). Very useful. :)
 Not sure that's allowed to be used on USAF secret networks...  I have wanted to try it on my phone though.  I know there is an app in the market that does about the same thing and you can use the phone as an unsecured wifi hotspot...  Sounds like fun to me. ;)

---

### Post by collisionystm on 2011-05-18
> **JoeGoalie said:**
> I guess I have to make a little confession. After looking up ways to add Ubuntu to a Windows Domain and Active Directory I decided to try using Windows Server 2008 R2 to setup the VPN (I'm a sysad or the USAF and we use a lot of Windows, it's what I'm used to). I think I'm going to have to abonden that route and instead try it back in Ubuntu where this extra help is relevant. I used to be a big Ubuntu user and prefer it, but the drivers on my laptop don't work quite right (to the point where I would like to buy a new laptop so I can run Ubuntu again). I'm not really sure how to setup user permissions and what not Ubuntu. It's easy in Windows I can just right click the file/folder and go to the security tab. I'm thinking now I should rebuild the VPN server on an Ubuntu platform (shouldn't be hard, just more practice :p) and then run another virtual box with Windows as my file server. They'd both be virtualized on the same box so it should in theory work nicely.
 
I guess I know what I'm doing this afternoon after work, lol.

Before you completely give up... look at [www.zentyal.com](www.zentyal.com)

It is all web based. Makes VPN setup a piece of cake.

AND...makes integrating with windows a piece of cake.

It is the J.C. of ubuntu. And its based on 10.04 server ;)

---

### Post by JoeGoalie on 2011-05-18
> **collisionystm said:**
> Before you completely give up... look at [www.zentyal.com]("http://www.zentyal.com")
 
It is all web based. Makes VPN setup a piece of cake.
 
AND...makes integrating with windows a piece of cake.
 
It is the J.C. of ubuntu. And its based on 10.04 server ;)
 Dang, can't go to the site from work... I'll check it out either when I get off today or tomorrow.  Thanks.

---

### Post by collisionystm on 2011-05-18
I use it as my windows pdc. And file server at work. There is updated anti virus and technical support for it..... its a very nice product. Make sure you use Firefox 3.6 with it. Its not completely Firefox 4 compatible yet

---

### Post by JoeGoalie on 2011-05-18
> **collisionystm said:**
> I use it as my windows pdc. And file server at work. There is updated anti virus and technical support for it..... its a very nice product. Make sure you use Firefox 3.6 with it. Its not completely Firefox 4 compatible yet
 On the machine setting it up?  Or just connecting to it in general?  Does it not connect like a normal VPN?  My main goal is to connect Android to it.  Having my own cloud to my phone would be great.  The other goal is of couse, Windows.  It would be nice to connect to my home network from anywhere (especially when I get deployed).

---

### Post by qaniklab on 2011-05-19
Yes, you can easily run OpenVPN in this configuration.
You'll just have to forward the 1194 UDP port to your server and enable the bridge, the best way to authenticate a client in your case is to use CA and certificates.

I work for a company that configures VPNs server so I can refer you to a tutorial we wrote: [http://www.serverubuntu.it/openvpn-bridged-configuration](http://www.serverubuntu.it/openvpn-bridged-configuration)

---

### Post by collisionystm on 2011-05-19
> **JoeGoalie said:**
> On the machine setting it up?  Or just connecting to it in general?  Does it not connect like a normal VPN?  My main goal is to connect Android to it.  Having my own cloud to my phone would be great.  The other goal is of couse, Windows.  It would be nice to connect to my home network from anywhere (especially when I get deployed).

The machine connecting to it. It is managed through the web interface... 

The VPN function is built into it. You just set it up and add clients.

You can connect an Android.

---

### Post by JoeGoalie on 2011-05-19
> **qaniklab said:**
> Yes, you can easily run OpenVPN in this configuration.
You'll just have to forward the 1194 UDP port to your server and enable the bridge, the best way to authenticate a client in your case is to use CA and certificates.

I work for a company that configures VPNs server so I can refer you to a tutorial we wrote: [http://www.serverubuntu.it/openvpn-bridged-configuration](http://www.serverubuntu.it/openvpn-bridged-configuration)
Website could not be found.
> **collisionystm said:**
> The machine connecting to it. It is managed through the web interface... 

The VPN function is built into it. You just set it up and add clients.

You can connect an Android.
I figured that out after I got some time to look into what it was.  It looks perfect, easy gui and an IDS.  That's pretty cool, I'm downloading it right now.

---

### Post by collisionystm on 2011-05-19
> **JoeGoalie said:**
> Website could not be found.

I figured that out after I got some time to look into what it was.  It looks perfect, easy gui and an IDS.  That's pretty cool, I'm downloading it right now.

Yeah I am sure you will like it. EVERYTHING is so easy on there

---

### Post by collisionystm on 2011-05-19
Oh and you may want to look at this if you decide to do more with it..

[http://trac.zentyal.org/wiki/Document/Documentation/ZentyalDesktop](http://trac.zentyal.org/wiki/Document/Documentation/ZentyalDesktop)

It lets you easily add Ubuntu to the Zentyal LDAP system so you can login with a domain account on ubuntu.

And for the windows part, it installs  a few other things.

Make sure you use firefox 3.6 with Zentyal. You are okay with 4 until you try to do a backup or restore. You will see stuff like 'object not found'. its because 4 isnt compatible yet

---

### Post by JoeGoalie on 2011-05-19
> **collisionystm said:**
> It lets you easily add Ubuntu to the Zentyal LDAP system so you can login with a domain account on ubuntu.
 I'm not sure I want to do anything that complicated now though. I think I might setup a host OS with two guest OS'es.  One guest being my VPN server (possibly this Zentyal), and the other being a Windows box that I can just setup a simple workgroup.  I'm not an enterprise, I just want secure access to my own stuff abroad.  I think a workgroup would be suffecient.  Unless there is a way that I can just setup the Zentyal to have a VPN and share a drive and control access to it with username/password (which I plan on doing with the workgroup).  I don't necessarily want everyone on my VPN seeing all my files and I don't really want to see theirs.  I know how to do that in Windows, I'm just not as familiar with Linux stuff.
 
On a side note.  Yesterday when I went to work I found out I'm getting sent to get some additional Unix training for some of our servers here.  That's pretty cool.  Maybe I'll be a little more knowledgable then? lol.  I guess my new goal is to have this up and running before going to training so I can access all my stuff. That would be cool. :)

---

### Post by collisionystm on 2011-05-19
> **JoeGoalie said:**
> I'm not sure I want to do anything that complicated now though. I think I might setup a host OS with two guest OS'es.  One guest being my VPN server (possibly this Zentyal), and the other being a Windows box that I can just setup a simple workgroup.  I'm not an enterprise, I just want secure access to my own stuff abroad.  I think a workgroup would be suffecient.  Unless there is a way that I can just setup the Zentyal to have a VPN and share a drive and control access to it with username/password (which I plan on doing with the workgroup).  I don't necessarily want everyone on my VPN seeing all my files and I don't really want to see theirs.  I know how to do that in Windows, I'm just not as familiar with Linux stuff.
 
On a side note.  Yesterday when I went to work I found out I'm getting sent to get some additional Unix training for some of our servers here.  That's pretty cool.  Maybe I'll be a little more knowledgable then? lol.  I guess my new goal is to have this up and running before going to training so I can access all my stuff. That would be cool. :)

That would be pretty awesome!

If by 'workgroup'  you mean a domain? Yes, you can do that with Zentyal. Are you using Windows XP or 7? the reason I ask is you have to apply a registry fix to 7 in order to Join.

Sharing drives in Zentyal and making the domain in general is something you cane easily do.

You will Build you server, name your 'Workgroup' or Domain, TEST for example.

Setup the DNS on your Box, and enable WINS. Now just point the WINS of your laptop to the Zentyal and join the domain.

Use the File sharing in Zentyal to name a share and add it. You can create user accounts for the workgroup and GROUPS to restrict which user can access what share.

You should be able to VPN from a cell phone such as android and access the shares by just punching in your username and password.



By the way, here is the registry file you need for Windows 7 ( so you dont have to hunt for it) just name it samba.reg or something

Windows Registry Editor Version 5.00

```

Windows Registry Editor Version 5.00

[HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\LanManWorkstation\Parameters]
"DNSNameResolutionRequired"=dword:00000000
"DomainCompatibilityMode"=dword:00000001

```

---

### Post by collisionystm on 2011-05-19
Oh and really, you dont need to join your computer to the domain... when you go to access files you just punch in your username. 

With a Samba Domain, the domain name isn't even used in authentication for file shares. Its just the username and passcode

For instance, I have a domain called TRASH on zentyal

I dont have to put TRASH\myself or myself@trash to login to a file share

I just use

myself
<passcode>


So yes, maybe thats what you meant by work group? Either way you can still make separate user accounts, groups etc....

---

### Post by JoeGoalie on 2011-05-19
No, a workgroup is not a domain.  In a workgroup all computers are peers and it's a peer to peer connection.  So each connection must log in with credintials on each computer.  For a small network like mine (share drive, my laptop, my phone, wife's laptop, wifes phone, possible remote client) it would be fine.  Really the only place that would need to be managed is where the chared hard drive is being hosted.  That computer would have to have a user account created for the person connecting to it.  Since there really is only one place that I'm wanting to log on to, it works fine because that is only one computer to manage accounts on.
 
Domains are your typical server feeding clients connection.  Where you have a domain controller with active directory that manages all user accounts, computers, groups, etc... from the central point.  While cool, and definitely better for a larger network, I'm not sure it's necessary for my personal network.  I would like the connection to be as seamless as possible for my wife's connection.  When you add a computer to the domain, it even changes the look of the login.
 
I just thought of something...  If I make it a domain, when you're remote, how would you access the domain?  The PC won't see the domain to log into so you'd have to log in locally and start the VPN.  Then getting out of the local account and back onto the domain without closing the VPN is going to be tricky...  I don't know how that all works.  These are reasons I think the Workgroup could be easier for my particular situation.
 
And yes, all my machines are running Windows 7.
 
[Difference between domain and workgroup](http://windows.microsoft.com/en-US/windows7/What-is-the-difference-between-a-domain-a-workgroup-and-a-homegroup)

---

### Post by JoeGoalie on 2011-05-19
Looking at some tutorials, the domain controller stuff is a different set of stuff than the one that comes with VPN.  Can I install the Zentyal UTM for the VPN and IDS, and then add the other modules needed for domain controlling after?
 
I have a three day weekend starting tomorrow.  I'm going to take this on as this weekend's project.  I feel I learned a lot lost weekend when I tried setting up OpenVPN.  This just looks like a simplified version of that setup.

---

### Post by collisionystm on 2011-05-20
Well even in a domain you can still log into the pc without a connection. If roaming profiles are turned off. But its only the one user account that is always used on the pc. If you log on as yourself all the time, its cool because windows will cache the domain authentication on itself and let you log in... but you just can switch users to someone else on the domain. It has to be the last person to log on at the time it was connected to the domain.

Once your connected to vpn all you do is set the dhcp to hand out a wins address of Zentyal. Then the computer can operate as if you were there...as far as adding user permissions with leap directory search...etc.....

I have domain users that are mobile with laptops 24x7 and only plug into my network once in a while. ( sales guys )

---

### Post by JoeGoalie on 2011-05-20
> **collisionystm said:**
> Well even in a domain you can still log into the pc without a connection. If roaming profiles are turned off. But its only the one user account that is always used on the pc. If you log on as yourself all the time, its cool because windows will cache the domain authentication on itself and let you log in... but you just can switch users to someone else on the domain. It has to be the last person to log on at the time it was connected to the domain.

Once your connected to vpn all you do is set the dhcp to hand out a wins address of Zentyal. Then the computer can operate as if you were there...as far as adding user permissions with leap directory search...etc.....

I have domain users that are mobile with laptops 24x7 and only plug into my network once in a while. ( sales guys )

Nice, sounds perfect. At work we must have roaming profiles turned on or something then. If we have no network connection, you can't log in at all. 

This is part of the reason I do these "projects". I love the learning. Thanks for the help so far. I'm going to try and set it up today most likely.

---

### Post by JoeGoalie on 2011-05-21
Well, using Zentyal to setup the VPN was amazingly simple.  I'm remotely connected to my VPN right now... However, I'm back in the same boat.  I can't see other computers on my home LAN.  I can ping the server at 192.168.160.1, but I can't ping my router at 192.168.42.1.  I check boxed enable client-to-client and I setup 192.168.42.0/24 as an advertized network.  Any suggestions?

---

### Post by JoeGoalie on 2011-05-21
> **collisionystm said:**
> That would be pretty awesome!

If by 'workgroup'  you mean a domain? Yes, you can do that with Zentyal. Are you using Windows XP or 7? the reason I ask is you have to apply a registry fix to 7 in order to Join.

Sharing drives in Zentyal and making the domain in general is something you cane easily do.

You will Build you server, name your 'Workgroup' or Domain, TEST for example.

Setup the DNS on your Box, and enable WINS. Now just point the WINS of your laptop to the Zentyal and join the domain.

Use the File sharing in Zentyal to name a share and add it. You can create user accounts for the workgroup and GROUPS to restrict which user can access what share.

You should be able to VPN from a cell phone such as android and access the shares by just punching in your username and password.



By the way, here is the registry file you need for Windows 7 ( so you dont have to hunt for it) just name it samba.reg or something

Windows Registry Editor Version 5.00

```

Windows Registry Editor Version 5.00

[HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\LanManWorkstation\Parameters]
"DNSNameResolutionRequired"=dword:00000000
"DomainCompatibilityMode"=dword:00000001

```
If I go through setting all this up, do I change the settings for the OpenVPN TAP adapter to got to the DNS and WINS server?

---

