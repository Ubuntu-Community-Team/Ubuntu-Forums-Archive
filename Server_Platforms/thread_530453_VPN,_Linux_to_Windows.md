---
title: "VPN, Linux to Windows"
date: 2007-08-20
forum: Server Platforms
---

### Post by TorchlightJay on 2007-08-20
So, break it down, I am setting up a VPN only to realize that I don't know the basic theory. Maybe someone can help me out. 

1) Do the clients and the server all have to be on the same domain in order to work? 

2) Do you HAVE to have some sort of DHCP setup on your VPN server? 

3) once connected, do you have to mount their user folder or does it automount?

Thanks all

---

### Post by rickyjones on 2007-08-20
Well, your post is going in a couple of different directions... I can help with the first two though.

1) No. A VPN is a Virtual Private Network created between two points. For example, I have a VPN Server at one location. I dial into this location from anywhere else in the world and I am now on that private network, so I can access all the computers on that network.

2) No, but it makes life a heck of a lot easier. For example, using RRAS in Windows Server 2003 I don't use DHCP but the VPN Services give dial-in clients specific IPs. Similar to DHCP but the service isn't running.

3) This doesn't seem specific to creating a VPN, but more with logging on from different locations?

I hope this information helps.

-Richard

---

### Post by TorchlightJay on 2007-08-20
Sorry, wasn't specific. Maybe I don't fully understand. 

All of my users have like a user folder and stuff on the server and directory. I was wondering, when you do connect to VPN, do you get access to your user folder. Does it mount as an individual folder, how does it work?

---

### Post by rickyjones on 2007-08-20
> **TorchlightJay said:**
> Sorry, wasn't specific. Maybe I don't fully understand. 

All of my users have like a user folder and stuff on the server and directory. I was wondering, when you do connect to VPN, do you get access to your user folder. Does it mount as an individual folder, how does it work?

Well, when you dial into a VPN it is just like plugging that computer into the private network with a cable... it's just on the network.

If you want their home folders to automount then they need to log into your network domain, or however it is authenticated, to get access to the resources.

For example: I use Windows on my laptop. The server, on the private network, is a Windows Server 2003 box running RRAS as a VPN server. When I connect the VPN between my laptop at home and the server, my laptop is given an address on the private network and I am able to ping and communicate with the server and other computers on the network. If I'd like to then I can map a drive from my computer to server computer (essentially mounting my home folder if I want to). Or, I can log into my server with remote desktop and have access to my files.

Point being that the VPN gets you onto the network. Something else has to happen to get to the next step.

I hope this helps clear it up!

-Richard

---

### Post by TorchlightJay on 2007-08-20
Cool, maybe you can help me in more detail now that I know you understand Windows SBS 2003.

So I am trying to run the RRAS and the server I am running has two NICs. Now you mentioned it not being necessary to have DHCP. So I don't have to set it to have two NICs? Like the tutorials I read online said to set it to use an internal NIC and set some IPs and Stuff. If that's the case, does that internal NIC need a live internet connection, that is do I need to plug it into my router?

I am able to connect to the VPN but when I do an ipconfig, I get an ip setup from my internet connect, as well as from the VPN. Well I go to network places and try to mount and I am told that I don't ahve any permissions to do so. What's the deal with that?

---

### Post by rickyjones on 2007-08-20
> **TorchlightJay said:**
> Cool, maybe you can help me in more detail now that I know you understand Windows SBS 2003.

So I am trying to run the RRAS and the server I am running has two NICs. Now you mentioned it not being necessary to have DHCP. So I don't have to set it to have two NICs? Like the tutorials I read online said to set it to use an internal NIC and set some IPs and Stuff. If that's the case, does that internal NIC need a live internet connection, that is do I need to plug it into my router?

I am able to connect to the VPN but when I do an ipconfig, I get an ip setup from my internet connect, as well as from the VPN. Well I go to network places and try to mount and I am told that I don't ahve any permissions to do so. What's the deal with that?

Sure thing - but first I'm going to describe the way my network is setup, as it sounds like you are using a bit of a different configuration.

```

            [ INTERNET ]
                     |
                     |
                     |
  [ ROUTER - 192.168.10.1 ]
                     |
                     |
       ---------------------------------------
       |                                     |
       |                                     |
       |                                     |
[ SERVER - 192.168.10.2 ]               [ OTHERS ]


```

I have a Linksys router at the center of my network. Attached to it is the server and all my other computers.

The server is a custom built computer with a single NIC. It is running Windows 2003 Enterprise Edition.

It is assigned a static IP address of 192.168.10.2. It uses itself for DNS. It runs Active Directory. DHCP is installed to support the local network but RRAS is not configured to use it.

I enabled VPN in RRAS by "Configuring Routing and Remote Access" and selecting "VPN Server". Within RRAS I configured the VPN Server to hand out a certain selection of IP Addresses instead of using DHCP. I find this is just better security.

My server, being directly connected to the router, has internet access directly through the router (NAT).

If you have two NICs then you can easily go into a more complicated setup. I recommend when starting out to do the absolute basics.

1. Disable the second NIC - use only one.
2. Set a static IP address - this is important. If it's a server then this should be a natural instinct.
3. Apply all updates. Make sure the server is stable before continuing.
4. Configure RRAS to be a simple VPN Server using integrated Windows Authentication (I believe).
5. Create a new VPN connection from the server itself and see if it connects.

That is basically what I did about a year or so ago and it's been running stable ever since. I can't remember all the exact steps for configuring the RRAS as I can't VPN in when I'm at work.

Does this bring you closer to an answer by any chance?

-Richard

---

### Post by TorchlightJay on 2007-08-20
Close, we do have two NICs and I can disable one. We have a simple Linksys router that the server (amongst other computers) connect to. This is a custom built system but it has two NICs. We have Active Directory users and folder and stuff. 
I am not sure wheether it uses itself for DNS or not, is it necessary for it to do so? If it is, you know of any decent tutorials. 

Moving along, that is our setup. Our server is set to a static IP (of the router). I don't think we have DHCP nor do I know how to set that up. I think what you said makes sense. We can connet but I think there must be a share issue or something. 

So when you mention giving out a certain amount of IPs. Were those IPs you made up or IPs from the router? It for some reason wants me to setup a DHCP relay or something, not sure what that means. Maybe you can help me. 

Sometimes I cannot connect ever but sometimes i can. I don't know why or why not.

---

### Post by rickyjones on 2007-08-20
> **TorchlightJay said:**
> Close, we do have two NICs and I can disable one. We have a simple Linksys router that the server (amongst other computers) connect to. This is a custom built system but it has two NICs. We have Active Directory users and folder and stuff. 
I am not sure wheether it uses itself for DNS or not, is it necessary for it to do so? If it is, you know of any decent tutorials. 

Moving along, that is our setup. Our server is set to a static IP (of the router). I don't think we have DHCP nor do I know how to set that up. I think what you said makes sense. We can connet but I think there must be a share issue or something. 

So when you mention giving out a certain amount of IPs. Were those IPs you made up or IPs from the router? It for some reason wants me to setup a DHCP relay or something, not sure what that means. Maybe you can help me. 

Sometimes I cannot connect ever but sometimes i can. I don't know why or why not.

This gets us closer but I'm going to be honest and outright: You're going to need to get on this server/network and get some very specific information.

Information such as:
* IP address/subnet/gateway/DNS of the only NIC that should be active at this point. It should be a static IP and for Active Directory it NEEDS to be pointing to itself, or another Domain Controller.

* IP address of the router - this should be the Gateway for your server.

* Find out if your internet connection is a static IP or a dynamic IP. This affects the WAN (Wide Area Network, or Internet) side of the router.

* Find out if your router is handling DHCP requests or if it has DHCP disabled. If it is handing out addresses, and if it is a Linksys, then the default range should be 192.168.1.100 - 192.168.1.200 I think.

* If the router is handling DHCP you can leave it as is, but I highly recommend having DHCP on the domain controller (or another member server in the ideal situation). This way you can control everything that the clients receive. For instance, the router will give a client an IP and a gateway and a DNS - they only point to the router. You want the clients to look at your domain controller for DNS otherwise you will have a lot of issues on your network.

* Now, if the router is doing DHCP then you can still configure the VPN service to hand out it's own IP address range - just make sure that they don't reside in the same range as the DHCP server. For example, you'd give the VPN server control over the IP addresses of 192.168.1.201 - 210. That would work just fine.

----

Now, did you setup this server in the first place or did somebody else set this up? If it was someone else then I highly recommend pinging them for their notes (they should have notes when they installed it all ). This will give you more information about how it was all configured.

If you're new-ish to an admin role on a Windows network I highly recommend becoming friends with Microsoft Technet. ([http://technet.microsoft.com/en-us/default.aspx](http://technet.microsoft.com/en-us/default.aspx)). There is a lot of good information there including whitepapers that you can follow.

Now, I'm not a huge fan of SBS (Small Business Server) because it breaks a lot of rules (don't put all your eggs in one basket)... but it does work in a pinch. I highly recommend finding documentation specific to it as some things differ between it and a standard Server 2003.

Am I filling in any more gaps for you yet? We need to get some more information about your environment but I think you and I can get this working.

-Richard

---

### Post by TorchlightJay on 2007-08-20
Yes I set this one up myself (built and installed OS) but I am a newbie. 

The ISP gave us a static IP and of course two DNS server. The Router gives out about 15 IPs. 192.168.1.105 is the one our server is using. We set the server to static and put in that IP. The router is 192.168.1.1 and is our gateway naturally. Subnet is 255.255.255.0. The DNS I put down for the server is the same DNS the ISP gave us. The Router is handling DHCP right now. 

When you say make sure it doesn't lie in the same range as the DHCP server. Are we talking about my Windows Server or the Router? I have run into a part of the setup of VPN that asks for either DHCP or IP range. What would be a good idea for IP range. Hopefully I gave you all the info here. 

Let me know if you need more. Thanks.

---

### Post by rickyjones on 2007-08-20
> **TorchlightJay said:**
> Yes I set this one up myself (built and installed OS) but I am a newbie. 

The ISP gave us a static IP and of course two DNS server. The Router gives out about 15 IPs. 192.168.1.105 is the one our server is using. We set the server to static and put in that IP. The router is 192.168.1.1 and is our gateway naturally. Subnet is 255.255.255.0. The DNS I put down for the server is the same DNS the ISP gave us. The Router is handling DHCP right now. 

When you say make sure it doesn't lie in the same range as the DHCP server. Are we talking about my Windows Server or the Router? I have run into a part of the setup of VPN that asks for either DHCP or IP range. What would be a good idea for IP range. Hopefully I gave you all the info here. 

Let me know if you need more. Thanks.

I should be able to work with that. :)

1. Set the server to use itself (192.168.1.105) as it's DNS server. That will make AD play a little nicer usually.

2. The VPN setup is asking for a range? Try giving it 192.168.1.230 - 192.168.1.235. This will give you 4 client connections I do believe, which should be fine for the time being.

That should get you started I think.

I'll remote into my server tonight and spin off some screenshots to help you out if you'd like me to.

I highly recommending moving the DHCP server to your domain controller or a member server if possible. This way your clients will have a better time with AD. Unless you have static IPs set on your clients. But that is a whole different topic. :)

Thanks,

-Richard

---

### Post by TorchlightJay on 2007-08-20
I would appreciate that greatly. Real quick, how do you setup DHCP. Like I go into the settings to setup DHCP, I choose to add a server, and I am stuck. What numbers do I have to use? Do I make them up?

---

### Post by rickyjones on 2007-08-20
I don't believe you click "Add Server" - that would let you add an existing DHCP server. I'll go through my setup and see what I can find out. Your server should be listed there already - you should be able to right click it and say "add scope" or "create scope" - the numbers (IP Addresses) have to be able to work on your network, so the 192.168.1.x range must be used, but beyond that just make them up and make sure that nothing already exists there.

Example: If the router is 192.168.1.1 and the server is 192.168.1.105, then don't make a range of 192.168.1.1 - 192.168.1.200. Instead make a range of 192.168.1.150 - 192.168.1.170.

You WILL want to DISABLE the DHCP server on your router BEFORE you enable your DHCP scope on the router... otherwise bad things can happen. Play it safe, make sure no one is on the network and disable the router's DHCP server first, then play with DHCP on your server.

-Richard

---

### Post by TorchlightJay on 2007-08-20
okay, quick question, if I do disbale DHCP on the router, how will my other computers get IP addresses. Maybe i don't understand the theory, will the DHCP then be through the server and then I connect to a HUB or something. Oh I also port forwarded 1723 to 192.168.1.105 on the router, though it may help. Also, I set most of the computers to static and they get 192.168.1.x (from 101-106). 

Any thoughts. Also, how do I set the DNS to itself. Like do I go under the interfaces to do that of do I go to DNS under Administration Tools. If I do the latter, what do I do next? 

Again, thanks for all your help

---

### Post by rickyjones on 2007-08-20
> **TorchlightJay said:**
> okay, quick question, if I do disbale DHCP on the router, how will my other computers get IP addresses. Maybe i don't understand the theory, will the DHCP then be through the server and then I connect to a HUB or something. Oh I also port forwarded 1723 to 192.168.1.105 on the router, though it may help. Also, I set most of the computers to static and they get 192.168.1.x (from 101-106). 

Any thoughts. Also, how do I set the DNS to itself. Like do I go under the interfaces to do that of do I go to DNS under Administration Tools. If I do the latter, what do I do next? 

Again, thanks for all your help

The other computer will get their IPs from the server. The server is plugged into one of the four switch ports on the router. Your other computers are plugged into the other ports, or are wireless. If so, then yes, they will now get their IPs from the server.

That port forward is good - that is the L2TP port I do believe for the VPN.

If your client computers are already static then you can skip DHCP as it might complicate things if you are not used to it. Make sure that each client has their primary DNS set to the IP address of your server.

To set the DNS entry correctly on the server you will do it under the interface, just like any other IP settings. Where it says primary DNS and secondary DNS you can go ahead and put the server IP in for the primary and leave the secondary blank, or set the secondary to 127.0.0.1.

I hope that clears it up for ya!

-Richard

---

### Post by rickyjones on 2007-08-20
Here is a PDF of some screenshots that might help you out. I hope they do!

[http://www.rrcomputerconsulting.com/files/some_screenshots_to_help_you_out.pdf](http://www.rrcomputerconsulting.com/files/some_screenshots_to_help_you_out.pdf)
```
http://www.rrcomputerconsulting.com/files/some_screenshots_to_help_you_out.pdf
```

-Richard

---

### Post by TorchlightJay on 2007-08-20
SO real quick question. Now that I have DHCP on the server, do i just leave it then? Like is there anything I need to do to the server or router to where it will give the DHCP to all other computers on the network? I have one working NIC so I don't know what all I am going to have to do to get the computers to use DHCP from the server. I mean is there a setting on either device?

Thanks for all your help. I am going to try everything we've talked about up to now

---

### Post by rickyjones on 2007-08-20
Once DHCP is setup on the server then all you need to do is set your clients to use DHCP to retrieve an IP address. No more configuration needs to be done on the router - this all works with one NIC. Lots of traffic can flow from that port :P

I wish you well in your endeavor. Good luck!

-Richard

---

### Post by TorchlightJay on 2007-08-20
Sweet, I think I am on the right path. So I set my DHCP server and it worked after I rebooted to server. However, once I logged onto the server, it stopped working. My clients and server weren't able to get internet access. Maybe you have an idea of what's going on. I have one scope and it's from 106-229. What's a good idea for a scope, does it matter. LIke what does a scope entail, does it mean that that is the ammount of IPs the DHCP server will give out or does it mean something completely different. DO I have a setting wrong to where none of the computers work when Administrator is logged on?

Also, I noticed that computer off of the LAN work with VPN. Like one of these notebooks has a Sprint Aircard and I was able to connect (but no folders worked, go figure). I think this may all play into security on the VPN side. Any ideas how to fix that as well? 

I think these are the last major problems, once we get them, everything will fall into place. Thanks.

---

### Post by rickyjones on 2007-08-21
> **TorchlightJay said:**
> Sweet, I think I am on the right path. So I set my DHCP server and it worked after I rebooted to server. However, once I logged onto the server, it stopped working. My clients and server weren't able to get internet access. Maybe you have an idea of what's going on. I have one scope and it's from 106-229. What's a good idea for a scope, does it matter. LIke what does a scope entail, does it mean that that is the ammount of IPs the DHCP server will give out or does it mean something completely different. DO I have a setting wrong to where none of the computers work when Administrator is logged on?

Also, I noticed that computer off of the LAN work with VPN. Like one of these notebooks has a Sprint Aircard and I was able to connect (but no folders worked, go figure). I think this may all play into security on the VPN side. Any ideas how to fix that as well? 

I think these are the last major problems, once we get them, everything will fall into place. Thanks.

From the server open a command prompt and type "nslookup" and hit enter... paste the results here.

It sounds like you didn't include any DHCP options in the scope. You need options such as Router and DNS. Check the clients - I bet that they only have an IP and a Subnet Mask. DHCP needs to be told what to push out in terms of the gateway and DNS addresses. Check Microsoft Technet and there should be a configuration guide for DHCP.

Here is a link to a technet article about installing and configuring DHCP Server:
[http://technet2.microsoft.com/windowsserver/en/library/10112946-1204-4ff4-b52c-599c303135d11033.mspx?mfr=true](http://technet2.microsoft.com/windowsserver/en/library/10112946-1204-4ff4-b52c-599c303135d11033.mspx?mfr=true)
```
http://technet2.microsoft.com/windowsserver/en/library/10112946-1204-4ff4-b52c-599c303135d11033.mspx?mfr=true
```

Hope this helps! 

-Richard

---

### Post by TorchlightJay on 2007-08-21
So I THINK I've figured it out, sorry I am not at the server yet and I think it disconnected but once I deleted the previous configuration I did on routing & remote services, everything began to work. I think I did something with the scope. Since I am not at the server, I am going to speak from memory.

The server is 192.168.1.105 and I gave it a scope from 106-229. I gave the remote service a range of 110-115. Is VPN meant to only be accessible when you are out of the LAN? Just checking. Also, I was able to connect to the VPN with this one computer however, it had a different subnet. The subnet that Sprint uses on it's aircard is different than that of the server and network in the office. Does that make a difference? If so how do I fix it cause I certainly can't account for every subnet, or maybe I can. 

Anyway, I think we have some progress, the DHCP seems to work but every now and again it craps out. The computers may be set to DHCP cause only one computer in the office is there all the time, the others are laptops. Of course the server is there all the time too. Should i put that one desktop on the same domain? 

Sorry, getting ahead of myself, let's just get this VPN. I will try the commands you said when I get to the server but for right now, that's where I left, so the only thing setup the same around here is that DHCP setting. Now I tried pinging the static that the ISP gave us, no luck. Let me know what you think so far. Thanks.

---

### Post by rickyjones on 2007-08-21
It would be wise to make the VPN scope different from the DHCP scope, otherwise you will have a conflict in the future. 

Yes, VPN is meant to be used when you are not in the office - it is a way to connect two different networks together.

That sprint card /should/ be on a different subnet. That is OK. You want to VPN in through the internet TO your local network. That is the point of VPN.

Check on the router and see if "Block WAN Request" is set to Enabled. If so then you will not get a response when you ping your static internet address. The router is not responding.

Man, I'm almost thinking it might be worth moving to email and setting up a time for me to remote desktop in to see if I can show you a couple of things. :)

-Richard

---

### Post by TorchlightJay on 2007-08-21
OKAY, I did nslookup and this is what I have

***Can't find server name for address 192.168.1.105: Non-existent domain 
Default Server: UnKnown
Address: 192.168.1.105

Make any sense, I am going to try that setup you sent me. Thanks

---

### Post by rickyjones on 2007-08-21
Yup - the message you received is normal when you do not have a Reverse Pointer Record defined in DNS for your server. I see it all the time.

Let me know if that guide helps you out!

-Richard

---

### Post by TorchlightJay on 2007-08-21
Okay, so is that a good thing or a bad thing. If bad, how do I fix it, or is it in the guide, I am still at the first few parts of the guide so I don't know. Hopefully it's a pretty painless fix.

---

### Post by rickyjones on 2007-08-21
It's not bad. It's annoying, but not bad. DNS isn't broken, everything will still work. :)

The guide I gave you is for installing and configuring DHCP services. The "nslookup" was in regard to how your DNS is configured (I wanted to make sure that your server was indeed pointing to itself and whether or not it was responding to a DNS query).

You can fix it by creating a Reverse DNS Zone for your IP range. I recommend researching this BEFORE thinking about implementation. It'll make your job a whole heck of a lot easier! :)

Once again, Technet is a wonderful resource for this.

I hope all this advice is helping!

-Richard

---

### Post by TorchlightJay on 2007-08-21
Ya, I really appreciate you helping me, I am about ready to pull my hair out lol. 

I will log into technet. I think I know what my problem is now. Let me know if any of this sounds right. 

I think I need to create multiple DHCP scopes to account for the various subnets that exist out there and that will be used by people trying to connect to the server. Each Scope will ahve it's own IP range and it would be wise not to have these ranges overlay. Once I get all that setup, I can hop on over to the VPN setup. 

This is where it's falling apart for me, I need to create a range of IPs but do they get their own range separate from all of the others. Do I need to create different ranges to account for the subnets. Does it even matter if they overlay each other when I create scopes. Ex. can I create a scope for subnet 255.255.255.0 with the IP 192.168.1.107 in it and create another scope with the same IP?

Thanks

---

### Post by rickyjones on 2007-08-21
> **TorchlightJay said:**
> Ya, I really appreciate you helping me, I am about ready to pull my hair out lol. 

I will log into technet. I think I know what my problem is now. Let me know if any of this sounds right. 

I think I need to create multiple DHCP scopes to account for the various subnets that exist out there and that will be used by people trying to connect to the server. Each Scope will ahve it's own IP range and it would be wise not to have these ranges overlay. Once I get all that setup, I can hop on over to the VPN setup. 

This is where it's falling apart for me, I need to create a range of IPs but do they get their own range separate from all of the others. Do I need to create different ranges to account for the subnets. Does it even matter if they overlay each other when I create scopes. Ex. can I create a scope for subnet 255.255.255.0 with the IP 192.168.1.107 in it and create another scope with the same IP?

Thanks

Woah there! What you'll need is only ONE DHCP Scope - this is for your local network only.

It doesn't matter what the remote subnet is that your VPN users will dial in FROM. When they dial in a new virtual adapter will exist on their computer and it will be given an IP address on your LOCAL NETWORK. This IP address is handed out from your VPN Server configuration.

For example:
Your DHCP server could be configured to hand out the following information: Addresses 192.168.1.200 - 220. It gives a gateway of 192.168.1.1 and a subnet of 255.255.255.0.

Example Part 2:
Your VPN server will give dial-in customers the following information: IP: 192.168.1.225 - 235. A gateway of say 192.168.1.225 (because they talk to the VPN IP address on the server, which is different from the normal IP address, and is AUTOMATICALLY configured for you). 

It doesn't matter /where/ the clients come from - that is the point of VPN. You won't be handing out an IP in their own range as they are coming into YOUR network, so they need to be IN your network.

Does that make a little more sense?

Real world example using my setup:
The network at the church is 192.168.10.xxx.
My laptop is at home, on a 192.168.1.xxx network.
My main server at church has an IP address of 192.168.10.2
My laptop uses DHCP at home, but lets just say that it has an IP of 192.168.1.102.
I connect the VPN - using the VPN dialer in Windows XP Professional I connect to the IP address that the church ISP gives me to use. It connects.
I now have two network connections in my system tray. One is my wired connection, the other is the PPP VPN adapter.
As a client I have an IP address on my local network and on the remote network.
I can now connect to computers on either network - local or remote.

Does that clear it up?

-Richard

---

### Post by TorchlightJay on 2007-08-21
I think so. So I just create a range of IPs for my single scope that I want my router to give out. 

Let's say that I wanted my server to give out 192.168.1.150-192.168.1.200 so I created a scope with that range. Once that's all setup, I just move straight to the VPN. 

So I create a range for the VPN, does it need to be within or outside the scope that I just created? In your example it seemd like it was separate but I wanted to be sure I didn't miss anything. 
So for example: 192.168.1.220-192.168.1.230 for the VPN (It's completely separate from the scope just made)

Once that is done, all I have to do is go to my users in Active Directory and give them permissions for VPN/Remote Access. Then I set it up on the clients and connect?

Sounds easy enough. Let me know if I got anything wrong?

---

### Post by rickyjones on 2007-08-21
> **TorchlightJay said:**
> I think so. So I just create a range of IPs for my single scope that I want my router to give out. 

Let's say that I wanted my server to give out 192.168.1.150-192.168.1.200 so I created a scope with that range. Once that's all setup, I just move straight to the VPN. 

So I create a range for the VPN, does it need to be within or outside the scope that I just created? In your example it seemd like it was separate but I wanted to be sure I didn't miss anything. 
So for example: 192.168.1.220-192.168.1.230 for the VPN (It's completely separate from the scope just made)

Once that is done, all I have to do is go to my users in Active Directory and give them permissions for VPN/Remote Access. Then I set it up on the clients and connect?

Sounds easy enough. Let me know if I got anything wrong?

That should do it. And yes, the VPN scope should be different from the DHCP scope. Still in the same network, but a different range of IP addresses. You are correct in your example.

Remember that you need to add specific options to your DHCP scope. That document should have outlined those for you. Please let me know if you need more instruction on that. Otherwise your clients will have an IP but won't know who the DNS server is or who the gateway is...

But it sounds like you are on the right track. :)

-Richard

---

### Post by TorchlightJay on 2007-08-21
I am so close I can feel it lol. I think the problem is in the routing now. When I setup the VPN portion with the RRAS, routing stops working. Like I guess it stops sending IPs to the clients on the local network. I was wondering if maybe I didn't set something up right. It seems to go through an either or type of thing. Either the clients get DHCP service or the VNC users do. I did follow that guide to setup one scope with one range of IPs so I think that's all setup fine. Maybe you know what I did wrong. 

I did set up a different range of IPs with VPN than I did with the DHCP scope.

---

### Post by rickyjones on 2007-08-21
> **TorchlightJay said:**
> I am so close I can feel it lol. I think the problem is in the routing now. When I setup the VPN portion with the RRAS, routing stops working. Like I guess it stops sending IPs to the clients on the local network. I was wondering if maybe I didn't set something up right. It seems to go through an either or type of thing. Either the clients get DHCP service or the VNC users do. I did follow that guide to setup one scope with one range of IPs so I think that's all setup fine. Maybe you know what I did wrong. 

I did set up a different range of IPs with VPN than I did with the DHCP scope.

So the DHCP service is running, and local workstations can get an IP/Subnet/Gateway/DNS, correct?

But then when a remote client, using the VPN, tries to connect, everything breaks?

That is what I'm reading - just wanted to make sure that I am correct.

If so may I offer assistance in taking a look at the configuration remotely? If you'd like I can remote in and take a look at how your server is configured to see if I can see anything that might be causing this.

Good luck! Keep reading and trying. :)

-Richard

---

### Post by TorchlightJay on 2007-08-21
You're right so far. It's not so much when a VPN client connects, it's just when I setup the VPN setup. The second I set that up, it goes to hell. If I delete the VPN setup completely (disable), then the DHCP service goes back to normal. 

I will have to check with the higher ups about remote connection really quick like when they come by.

---

### Post by rickyjones on 2007-08-21
> **TorchlightJay said:**
> You're right so far. It's not so much when a VPN client connects, it's just when I setup the VPN setup. The second I set that up, it goes to hell. If I delete the VPN setup completely (disable), then the DHCP service goes back to normal. 

I will have to check with the higher ups about remote connection really quick like when they come by.

That sounds good (remote access). 

If it all goes to hell when the VPN services go up then there is definitely a configuration issue going on, just not sure on /what/ it is.

-Richard

---

### Post by TorchlightJay on 2007-08-21
We have VNC setup, so we may be able to do it. Ya I think it's DHCP that's messing up, maybe not. It works otherwise. Find a way to PM me (no sense in broadcasting this IP and password to the whole world.)

---

### Post by rickyjones on 2007-08-21
Check your PM.

---

