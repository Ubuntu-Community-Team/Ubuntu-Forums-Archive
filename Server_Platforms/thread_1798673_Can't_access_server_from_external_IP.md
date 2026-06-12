---
title: "Can't access server from external IP"
date: 2011-07-06
forum: Server Platforms
---

### Post by Brad_J on 2011-07-06
Hi, I'm setting up a home web server using LAMP that I want to use to access files and practice coding, but I am very new to Linux and web servers. I currently have it so I can access phpMyAdmin and the test pages locally through my internal IP, but whenever I try to access it through the external IP I get this router management console that I don't know the password or username to. I know my router login and password and it's not the same as that. I've forwarded port 80 and when that didn't work I tried changing /etc/apache2/ports.conf to 8080 and I forwarded that port on my router with no luck too. It doesn't seem to matter if I have any ports forwarded, though, it still brings me to the same screen regardless. Also, I have set up a static IP on the server by modifying the /etc/network/interfaces file. I've attached a screenshot with the actual router management console screen. I'm really hoping I'm just dumb and missing something obvious rather than having to go through some long, arduous process to get this working, but I'm willing to do whatever it takes to solve this problem. Maybe you guys can help shed some light on this? Thanks.

-Brad

P.S. I won't have access to the server until later, but, if you require any output from the server I will be sure to post it as soon as I get home.

EDIT: I forgot to mention that I'm not using ubuntu for my webserver, but debian instead because ubuntu server had a whole bunch of problems with my PCMCIA network card. Ubuntu suggestions should work just fine, but I just thought I should clarify.

---

### Post by Brad_J on 2011-07-06
Forgot to attach the image...

---

### Post by ruffEdgz on 2011-07-06
So when you are on the external IP, you can confirm that the port is showing as open (ports 80, 8080. etc...)?

The link below will test if it can see a certain ip or host port open:
[http://www.dyndns.com/support/tools/openport.html](http://www.dyndns.com/support/tools/openport.html)

You might want to make sure you port forwarding on the router is pointing to the correct internal IP address and port. It sounds like the IP/Host you are trying to contact is just pointing to your router IP (something like 192.168.0.1 instead of the server's internal IP).

If you want to take a screen shot of your router config, that would be helpful and what is the make/model of your router.

Cheers!

---

### Post by Brad_J on 2011-07-07
> **ruffEdgz said:**
> So when you are on the external IP, you can  confirm that the port is showing as open (ports 80, 8080. etc...)?

The link below will test if it can see a certain ip or host port open:
[http://www.dyndns.com/support/tools/openport.html](http://www.dyndns.com/support/tools/openport.html)

You might want to make sure you port forwarding on the router is  pointing to the correct internal IP address and port. It sounds like the  IP/Host you are trying to contact is just pointing to your router IP  (something like 192.168.0.1 instead of the server's internal IP).

If you want to take a screen shot of your router config, that would be helpful and what is the make/model of your router.

Cheers!
Sorry for the late reply, I looked into what you were saying and I think that I've found the problem. My modem doubles as a router and we have a wireless-n router attached to it, it's just that I don't have the password to access the modem/router and that's what the router management console comes from. The ports also aren't forwarding because I'm not able to forward them through the modem/router without a password. Now that I know the problem I should be able to find the password and fix it. Thank you for your help.

-Brad

---

### Post by Brad_J on 2011-07-08
I'm going to bump this back up because what I did didn't fix my problem. I now have access to the modem/router that was causing the problem before but I'm very confused. I thought that each individual computer had its own external IP for accessing the internet, is this not the case? Because I'm getting the same external IP results on all computers on my network. I have forwarded the correct port (80) using UDP and TCP for the server's internal IP (192.168.1.80) and I have modified the /etc/apache2/ports.conf to reflect this, but it still doesn't show that they are forwarded on [http://www.dyndns.com/support/tools/openport.html]("http://www.dyndns.com/support/tools/openport.html"). The server has a static IP and access to the internet, but I can't access it externally at all and I have no idea what to do next. Please help!

Also, the model of my router, if it's any help, is a Dlink DVA-G3810BN-TL.

-Brad

---

### Post by msandoy on 2011-07-08
I'm a bit confused about your hardware setup, but if I understand correctly, you have a modem from your ISP, taking care of the normal network features like port forwarding and DHCP. Then you have a wireless router connected to the modem. For this to work, you need to have the modem connected to one of the LAN ports on your wireless router, NOT the WAN port. The DHCP function in your wireless router will have to be switched off, to avoid conflicts. 
On the other hand, if the modem is connected to the WAN port of your router, the router have got an IP address from the modem, this address needs to receive all port forwarding from your external IP. Then in the router, you will have to forward to the correct local IP in your network.
And just to clarify to you, Your modem has your ONLY external IP address, as it is acting as a router, it will distribute internet access to local IP addresses as needed. In order to have multiple external IP addresses, you would need multiple lines in to your house, and multiple modems.

---

### Post by Dangertux on 2011-07-09
Long story short -- When using NAT you can't actually connect to your external IP  from within the network if it's port forwarded to a server on your local network. The routing table doesn't really support this and will always direct you to your modem's configuration which is what looks like is happening here.

Now if I or someone else external to your network were to visit the server via your external IP I have a feeling it would work. The reasoning behind this is how NAT handles routing. What you are experiencing is normal.

There are a variety of workarounds for this -- however, outside of getting a separate line you will never REALLY connect to anything except the local address while you are local.

---

### Post by Brad_J on 2011-07-09
> **msandoy said:**
> I'm a bit confused about your hardware setup, but if I understand correctly, you have a modem from your ISP, taking care of the normal network features like port forwarding and DHCP. Then you have a wireless router connected to the modem. For this to work, you need to have the modem connected to one of the LAN ports on your wireless router, NOT the WAN port. The DHCP function in your wireless router will have to be switched off, to avoid conflicts. 
On the other hand, if the modem is connected to the WAN port of your router, the router have got an IP address from the modem, this address needs to receive all port forwarding from your external IP. Then in the router, you will have to forward to the correct local IP in your network.

To avoid confusion, I have plugged the ethernet from the server directly into the modem. My knowledge of networking is pretty terrible, however, and I'm curious as to why I would plug the modem into a LAN port for the router as opposed to the WAN port? If nothing is plugged into WAN wouldn't that mean that the router wouldn't be assigned to a network, making it impossible to connect to the internet? Also, would I really need to disable DHCP on my wireless router if it has an internal IP format of 192.168.0.xx where my modem is 192.168.1.xx?
> **msandoy said:**
> And just to clarify to you, Your modem has your ONLY external IP address, as it is acting as a router, it will distribute internet access to local IP addresses as needed. In order to have multiple external IP addresses, you would need multiple lines in to your house, and multiple modems.
I've always thought that each computer had a corresponding external IP, I'm more confused about port forwarding now I guess. If you forward a port for an internal IP, how is the specific computer accessed with only one external IP? Are the internal IPs just listening on all forwarded ports and anything that passes through any of those ports gets a response? How could someone have multiple websites on one modem if that's the case? Different ports?

Sorry for all of the questions, I really don't understand a lot about networking and I'm interested in learning.

Also, would I put my internal or external IP into [http://www.dyndns.com/support/tools/openport.html](http://www.dyndns.com/support/tools/openport.html) to figure out if port 80 is forwarded?

---

### Post by Brad_J on 2011-07-09
> **Dangertux said:**
> Long story short -- When using NAT you can't actually connect to your external IP  from within the network if it's port forwarded to a server on your local network. The routing table doesn't really support this and will always direct you to your modem's configuration which is what looks like is happening here.

Now if I or someone else external to your network were to visit the server via your external IP I have a feeling it would work. The reasoning behind this is how NAT handles routing. What you are experiencing is normal.

There are a variety of workarounds for this -- however, outside of getting a separate line you will never REALLY connect to anything except the local address while you are local.

I no longer get directed to my modem's configuration when doing it, I just get no response, is this still normal behavior?

---

### Post by msandoy on 2011-07-09
> **Brad_J said:**
> To avoid confusion, I have plugged the ethernet from the server directly into the modem. My knowledge of networking is pretty terrible, however, and I'm curious as to why I would plug the modem into a LAN port for the router as opposed to the WAN port? If nothing is plugged into WAN wouldn't that mean that the router wouldn't be assigned to a network, making it impossible to connect to the internet? Also, would I really need to disable DHCP on my wireless router if it has an internal IP format of 192.168.0.xx where my modem is 192.168.1.xx?

I've always thought that each computer had a corresponding external IP, I'm more confused about port forwarding now I guess. If you forward a port for an internal IP, how is the specific computer accessed with only one external IP? Are the internal IPs just listening on all forwarded ports and anything that passes through any of those ports gets a response? How could someone have multiple websites on one modem if that's the case? Different ports?

Sorry for all of the questions, I really don't understand a lot about networking and I'm interested in learning.

Also, would I put my internal or external IP into [http://www.dyndns.com/support/tools/openport.html](http://www.dyndns.com/support/tools/openport.html) to figure out if port 80 is forwarded?

Ok, I will try to make a suggestion for a setup here. Connect the modem to the router via the WAN port. This make the modem assign an internal IP address to the router. In the modem, in order to redirect all traffic to your router, activate DMZ for the IP address of your router. This will send all traffic to it.

In your Router, make sure the internet settings are correct, and use the NAT function to redirect the various ports to the correct internal IP address. 

Now you have one cable going from the wall to the modem, and one from the modem to the WAN port of the router. Do not connect your server directly to the modem, since this makes the setup a bit harder to configure.

On your server, make sure the firewall is off, by doing a "sudo ufw disable".

This should make the server available from the outside.

And if you want to use utilities online to test for open ports, you have to give them your external IP. From the outside, none of your internal addresses are visible.

To try to explain how to run more than one server on one IP address, I have one win2k3 server and one Ubuntu server in my network, I run different services on those two machines. But there is only two services open to the internet. When my external IP receives a request on the port number for TS3 server, my router directs all traffic on that port to my win2k3 server. When my external IP address receives a request on the port for SSH, it redirects all that traffic to my ubuntu server. All other traffic is dropped, since my router does not have any other NAT rules.

Hope this can clarify a little.

---

### Post by Brad_J on 2011-07-11
> **msandoy said:**
> Ok, I will try to make a suggestion for a setup here. Connect the modem to the router via the WAN port. This make the modem assign an internal IP address to the router. In the modem, in order to redirect all traffic to your router, activate DMZ for the IP address of your router. This will send all traffic to it. 

In your Router, make sure the internet settings are correct, and use the NAT function to redirect the various ports to the correct internal IP address. 

Now you have one cable going from the wall to the modem, and one from the modem to the WAN port of the router. Do not connect your server directly to the modem, since this makes the setup a bit harder to configure.

On your server, make sure the firewall is off, by doing a "sudo ufw disable".

This should make the server available from the outside.

And if you want to use utilities online to test for open ports, you have to give them your external IP. From the outside, none of your internal addresses are visible.

To try to explain how to run more than one server on one IP address, I have one win2k3 server and one Ubuntu server in my network, I run different services on those two machines. But there is only two services open to the internet. When my external IP receives a request on the port number for TS3 server, my router directs all traffic on that port to my win2k3 server. When my external IP address receives a request on the port for SSH, it redirects all that traffic to my ubuntu server. All other traffic is dropped, since my router does not have any other NAT rules.

Hope this can clarify a little.

Sorry I haven't responded for a while, my internet at home has been really awful the past couple days and I haven't been able to access the forums for any length of time long enough to post.

Thank you for your response, I'll give your suggestions a try. I was wondering, though, why it's easier to plug into the router rather than the modem? The modem doubles as a router and has most of the same functionality of the router, I just feel like it would be easier to plug directly into the modem so I don't have to work through two firewalls.

Also, I discovered another problem with my server which might explain a few things; trying to ssh to my server for the first time in a while told me that port 22 was being blocked when it wasn't being blocked before. Upon running netstat I found out that no ports are actually being forwarded through the firewall and "sudo ufw disable" doesn't work because I'm running Debian. I was trying to look up the Debian equivalent last night but since my internet was being so terrible, I didn't get the chance until today. I found that stopping the iptables might work but I have yet to try it, I'll try to post about it if I can get on the forums when I get home.

-Brad

---

### Post by msandoy on 2011-07-11
To answer your question regarding modem vs router, If you connect the server directly to the modem, you will have the server on a different subnet as the computers connected to the router. This makes it harder to reach the server from any of them. By the way, this might be actually what you want for security reasons. If this is the case, you need to configure all the port forwarding in the modem, and not in the router. From what I understand, you have a web server at port 80 and a ssh server at port 22. If you forward those to the IP of your server in your modem configuration, you should be up and running as soon as you find out how to port those trough IPtables. I'm sorry to say, my IPtables skills are severely limited, so I can't help you there.

If you try this, please remove the DMZ configuration mentioned in my last post.

Edit: If you open up port 22 to the world, I suggest you make sure your password is properly secure. Also, I would suggest installing either Denyhosts or fail2ban to stop some of the script kiddies out there from crippeling your connection.

---

### Post by Brad_J on 2011-07-12
I'm starting to get pretty frustrated with this whole thing, I seem to have tried everything to get this to work and it still won't recognize that the ports are being forwarded... I have flushed all rules from my server's iptables and set the firewall to accept all input on any port. I've set my server to have a static IP and configured apache to port 80 and ssh to port 22. I've tested the server on both routers and set each to accept both TCP and UDP on port 80 and 22. I've double checked everything and to the best of my knowledge, everything should work, but it doesn't.

I'm starting to consider the possiblity that my ISP is just blocking those ports. Are there any tell tale signs that I could look for to see if this is the case? Telus' normal customer support kind of sucks and their tech support is usually worse. I'm probably going to give them a call tomorrow to ask but I want to know if there's anything that I can check to see for sure if this is or is not the case.

-Brad

---

### Post by romand on 2011-08-19
Telus blocks port 80 on consumer DSL.  You cannot run a web server on the consumer offerings.:( There are workarounds but the do cost.  Send me a email if you would like more info on them.

Romand

---

