---
title: "After Local IP Address change on reboot, server no longer available"
date: 2006-12-16
forum: Server Platforms
---

### Post by dbqp on 2006-12-16
I ask anyone who can assist:

I built a 6.10 web server using the ever popular HowToForge "Perfect Setup",

Worked great, I had a hangup with accessing it internally, but it always connected perfectly externally. You can see my previous post here with [this issue]("http://www.ubuntuforums.org/showthread.php?t=303168").

I have a [speedstream 6520]("http://www.databankqp.com/65xxug.pdf") (pdf) wireless DSL modem/router from my ISP. I had to set up my port mapping (FTP, DNS, HTTP, SMTP, port 5800/5900) to redirect to the local IP address (192.168.2.11) of the server for everything to work correctly.  Obviously, when my server received a new IP address on reboot, this would affect everything I set up with the port mapping.

I am registered with DynDNS.org and have a confirmed, actively working domain and refresh of dynamically assigned IP update.

This led me to review my hosts, httpd.conf, intefaces, and resolv files. This change of IP address has affected these as well.

I tried changing all the items affected above to the new severs local IP address: modem/router. and files listed above.  I rebooted (ensuring the IP address remained unchanged - 198.168.2.15) and never would the server come online to be accessible internally or externally. 

What went wrong and how can this be corrected? I don't want to change this information every time the server changes IP addresses locally. 

Any help or direction would be appreciated.

:-k

---

### Post by chrisfay on 2006-12-16
So which IP changed? Your external WAN IP or your local network IP?

If your LAN IP changed, you have configured the server on your internal network to recieve its IP via DHCP which is obviously a bad idea. Everytime it changes, you have to manually update your port mapping.

If your WAN IP changed, all you need to do is update your DynDNS.org account with the new one. Although, since you said your DynDNS.org account is dynamically updated (and functioning correctly?), I'm assuming its your LAN IP that has changed.

Is your network interface on the server configured 'static' or DHCP?

> I don't want to change this information every time the server changes IP addresses locally. 

It won't, if you configure it with a static IP in your */etc/network/interfaces* file.

---

### Post by dbqp on 2006-12-16
> Is your network interface on the server configured 'static' or DHCP?

Thanks - quick reply!

Where would I see this setting? Would it be the interfaces file? I set up the server as shown on [this page]("http://howtoforge.com/perfect_setup_ubuntu_6.10_p3").

I originally had the following when I did the initial install:

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.2.11
        netmask 255.255.255.0
        network 192.168.2.1
        broadcast 192.168.2.255
        gateway 192.168.2.1

Is it anything to do wit the set up on my router? Is there a way to always make one particular connection a certain IP address? Just wondering...

---

### Post by chrisfay on 2006-12-16
> Where would I see this setting? Would it be the interfaces file?

Yes. In:
```
/etc/network/interfaces
```
If it is still configured the way you have listed, it is static and should 'never' change.

This line:
```
...
iface eth0 inet static
...
```
...is responsible for setting it either static or DHCP. It looks good.

I'm still not clear on which IP changed....Can you list what it was before, and what it is now?

---

### Post by dbqp on 2006-12-16
> I'm still not clear on which IP changed....Can you list what it was before, and what it is now?

Original Install: 192.168.2.11

After reboot and reset of router: 192.168.2.15

It was assigned a new IP from my router, I guess.  I since tried changing the IP listed in interfaces file to the new IP, but no go.

---

### Post by chrisfay on 2006-12-16
> It was assigned a new IP from my router, I guess. I since tried changing the IP listed in interfaces file to the new IP, but no go.

Did you restart your networking services after updating the file? I would start over and:

```
sudo vi /etc/network/interfaces
``` 
Double check that the information for eth0 matches:

```
# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.2.11
netmask 255.255.255.0
gateway 192.168.2.1
```

Restart:
```
sudo /etc/init.d/networking restart
```

Then see if it sticks....

---

### Post by dbqp on 2006-12-16
> **chrisfay said:**
> Did you restart your networking services after updating the file? I would start over and:

```
sudo vi /etc/network/interfaces
``` 
Double check that the information for eth0 matches:

```
# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.2.11
netmask 255.255.255.0
gateway 192.168.2.1
```

Restart:
```
sudo /etc/init.d/networking restart
```

Then see if it sticks....

Well, see I changed all of the files listed in the above post to the new IP address: 192.168.2.15 changing interfaces as well. Should I go back and change all  of these files to 192.168.2.11 again as the original install? Then reboot?

---

### Post by chrisfay on 2006-12-16
No...thats fine. But post your current interfaces file:

```
sudo cat /etc/network/interfaces
```

That's the only file you need to mess with to change your local ip settings.

---

### Post by dbqp on 2006-12-16
> **chrisfay said:**
> No...thats fine. But post your current interfaces file:

```
sudo cat /etc/network/interfaces
```

That's the only file you need to mess with to change your local ip settings.

```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.2.15
        netmask 255.255.255.0
        network 192.168.2.1
        broadcast 192.168.2.255
        gateway 192.168.2.1

```

---

### Post by chrisfay on 2006-12-16
> Should I go back and change all of these files to 192.168.2.11 again as the original install?

I just re-read this, you're saying the original install assigned your IP statically, you didn't manually configure it originally? That doesn't make sense. The defaul is DHCP

I would restart your network:

```
sudo /etc/init.d/networking restart
```

and try and reproduce the ip change by resetting your router...

---

### Post by dbqp on 2006-12-17
> **chrisfay said:**
> I just re-read this, you're saying the original install assigned your IP statically, you didn't manually configure it originally? That doesn't make sense. The defaul is DHCP

I would restart your network:

```
sudo /etc/init.d/networking restart
```

and try and reproduce the ip change by resetting your router...

Let me clarify. In the Perfect Setup, I changed the interfaces file to my local IP address as cureently assigned at that present point in time. This was 192.168.2.11

During the Perfect Setup process, As directed, I assigned all the changes and variables to 192.168.2.11

After I noticed in my router settings that my local IP address to this machine was now 192.168.2.15 (and wasn't able to view it internally or externally) I changed my files to this new IP address as shown in my routers Control Panel.

I always restart after any changes to files related to networking.

---

### Post by chrisfay on 2006-12-17
> After I noticed in my router settings that my local IP address to this machine was now 192.168.2.15

Where in your router did you see this? Generally, you don't have to define routes in your router, they are either assigned by the router using the included DHCP server or provided 'to' the router by the configuration directives in your /etc/network/interfaces file. 

When you define the static settings on your server, the IP designation should be completed by the server, not the router.

---

### Post by dbqp on 2006-12-17
> When you define the static settings on your server, the IP designation should be completed by the server, not the router.
Reply With Quote

So then why did my router display a new IP address (192.168.2.15) when my server and router rebooted? Was it just a "glitch" and I should have restarted both?

---

### Post by chrisfay on 2006-12-17
> So then why did my router display a new IP address (192.168.2.15) when my server and router rebooted?

What you're describing sounds more like the 'routers' IP changed, something completely seperate from your server entirely. When you log into your router, what does it say is the IP address for the router itself? 

Is it still 192.168.2.1?

If not, I'm still confused on where you're getting a list of IP addresses connected to certain machines in your router....Unless you manually created routes within the router itself.

---

### Post by dbqp on 2006-12-17
> When you log into your router, what does it say is the IP address for the router itself?

I always log into my router at 192.168.2.1

These are the devices connected:

Connected Devices Summary
 	
Host Name	                Domain Name	IP Address	Attached By	Physical Address
EN133	                              MSHOME	         192.168.2.14	Ethernet	00:02:A5:78:57:65
ZDP	                                 NETPC	              192.168.2.10	Ethernet	00:14:2A:8F:54:A3
DBQP-SWEAXA3QU4 	NETPC	             192.168.2.15	Ethernet	00:80:C6:EF:A8:F1
DAVID	                                NETPC	             0.0.0.0	Disconnected	00:09:6B:06:54:83

---

### Post by chrisfay on 2006-12-17
> Host Name Domain Name IP Address Attached By Physical Address
EN133 MSHOME 192.168.2.14 Ethernet 00:02:A5:78:57:65
ZDP NETPC 192.168.2.10 Ethernet 00:14:2A:8F:54:A3
DBQP-SWEAXA3QU4 NETPC 192.168.2.15 Ethernet 00:80:C6:EF:A8:F1
DAVID NETPC 0.0.0.0 Disconnected 00:09:6B:06:54:83

I see.....

Couple more questions. When you noticed in your router that the IP listed for your server had changed to 192.168.2.15, did your interfaces file still have the old IP listed?

When you changed your interfaces file to reflect the new ip address, where you able to again view your machine?

---

### Post by dbqp on 2006-12-17
> Couple more questions. When you noticed in your router that the IP listed for your server had changed to 192.168.2.15, did your interfaces file still have the old IP listed?

When you changed your interfaces file to reflect the new ip address, where you able to again view your machine?

Firstly, my interfaces file was still the old IP listed. As no files were changed until this was realized by looking at my routers Control Panel.

Secondly, after changing the files and router redirects listed in the original post to the new IP address, I was still unable to see internally (SSH) or externally (tested with external parties).

---

### Post by chrisfay on 2006-12-17
Interesting, your router definately should not be reassigning a new IP to your server with your current configuration. The router is acting as if you have set your server to DHCP. Furthermore, the fact that your server retained the old IP while the router listed it differently leads me to believe it's something to do with your router's configuration and not your server's.

Your server's static IP doesnt fall within the range you've set for your router's DHCP pool right?

And since you still don't have connectivity, can you post the output of:

```
route
```
and 
```
ifconfig
```

---

### Post by dbqp on 2006-12-17
Route:

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0   *               255.255.255.0   U     0      0        0 eth0
default         192.168.2.1     0.0.0.0         UG    0      0        0 eth0

```

ifconfig:

```
eth0      Link encap:Ethernet  HWaddr 00:02:A5:78:57:65  
          inet addr:192.168.2.15  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::280:c6ff:fee9:c48b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:4305 dropped:0 overruns:0 carrier:4305
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:177 Base address:0xb000

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:9152 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9152 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1150721 (1.0 MiB)  TX bytes:1150721 (1.0 MiB)

```

Thank you for your help tonight. My eyes are crossed and need some rest. If you get a chance, please check back for replies as it is appreciated.

---

### Post by chrisfay on 2006-12-17
> Thank you for your help tonight. My eyes are crossed and need some rest. If you get a chance, please check back for replies as it is appreciated.

Sure will....

Everything looks good with your routing table and interface configuration. I am fairly certain it has something to do with your router/gateway. The only reason I can think that your router would attempt to reassign your server's IP is if your server requested it. And the only way for your server to request it is to set it to DHCP in your interfaces file. Otherwise, again, its not your router handing down the IP, but essentially your server handing 'up' the IP to the router.

Here's a quote from your routers documentation:

> DHCP Server Support
Dynamic Host Configuration Protocol (DHCP) provides a dynamic, &#8220;upon request,&#8221; IP address to
computers and other networked devices. Your SpeedStream Gateway can act as a DHCP Server for
devices on your local network.

Notice the 'upon request' portion of that description. For some reason, your router thinks its getting a request for a new IP after resetting. 

If this is the issue,  you could try completely disabling the DHCP option in your router and force static IP's on your clients, at least for testing purposes. Do some resets and see if it still attempts change the ip listed in the router.

As far as your lack of connectivity, I'm somewhat stumped. Since you already adapted your IP on the server to match what the router 'thinks' it should be, you theoretically should be able to see the machine.  Since you can't, there must be an internal routing issue within the router itself.  

When you are attempting to access the server from another client on your network, are you using the IP or a hostname you've mapped?

Anyone else have suggestions?

---

### Post by rickyjones on 2006-12-18
I may be late to the party, but here's my 2 cents...

It looks like you statically assigned everything during install - good. You say that when you looked at the router, you noticed your server listed as a different IP, so you updated port mappings to match. Maybe that was /leftover/ from when you were installing? By default, during the install, Ubuntu uses DHCP to get an address, so it would be listed in your router as such.

Verify the local IP on your server. Set up port forwarding in the router to match. Powercycle the router. Verify connectivity from the outside.

Shouldn't be any harder than that.

-Richard

---

### Post by dbqp on 2006-12-20
Thanks!

My apologies for not replying - life just keeps us (at least me!) too busy sometimes...;) 

I have resorted to changing everything I touched from this initial problem, back to the original install IP: 192.168.2.11

I have rebooted the server and router. I checked the server and all is showing what should be. hostname and IP addres as listed above. Does it matter if the server or router is powered on first?

The router, however, is still assigning the server 192.168.2.15.

When I try to access my DynDNS.org "domain" (not IP via :443) it takes me to my routers control panel where it requests username and password.  I am now assuming I have port forwarded to 192.168.2.11 on too many items.  I currently am port forwarding HTTP, DNS, FTP, SMTP, port 5800 and 5900 to 192.168.2.11

Could this be the issue?

](*,)

---

### Post by punx45 on 2006-12-20
I dont know if this will help, but i read the entire thread and didnt see it mentioned (unless i saw it and forgot!)

what is the range for DHCP assigned addresses?   perhaps you are setting the server statically at xxx.11 and the DHCP has already assigned xxx.11 to another computer on the network?

try setting DHCP to start assigning IPs at xxx.20 or whatever gives you space to  assign static IPs below that range.

---

### Post by dbqp on 2006-12-20
> **punx45 said:**
> I dont know if this will help, but i read the entire thread and didnt see it mentioned (unless i saw it and forgot!)

what is the range for DHCP assigned addresses?   perhaps you are setting the server statically at xxx.11 and the DHCP has already assigned xxx.11 to another computer on the network?

try setting DHCP to start assigning IPs at xxx.20 or whatever gives you space to  assign static IPs below that range.

Ahhhhh...when I get home, I will try that first thing.

My router is assigning IP range via DHCP from 192.168.2.10 to 100

So if I start assigning it from 192.168.2.12 to 100, this would free up IP 192.168.2.11?

So does my port forwarding listed above look inline with what it should be?

---

### Post by chrisfay on 2006-12-20
> I dont know if this will help, but i read the entire thread and didnt see it mentioned (unless i saw it and forgot!)

> **chrisfay said:**
> Your server's static IP doesnt fall within the range you've set for your router's DHCP pool right?

....no response though

> My router is assigning IP range via DHCP from 192.168.2.10 to 100

This could very well be the issue after all...You can't asign static IP's within the range you have set for DHCP.

---

### Post by dbqp on 2006-12-20
> Quote:
Originally Posted by chrisfay  
Your server's static IP doesnt fall within the range you've set for your router's DHCP pool right? 

....no response though


My apologies chrisfay.  I wasn't trying to discount your reply - I just FINALLY had a chance to sign back on to ubuntuforums and noticed someone had left another reply, which I responded to, then someone left another reply, which I then responded to...The light just never went "on" when you mentioned that previously. Again, I did not mean to **not** respond to your original reply - you helped me a great deal and I wouldn't want to create that impression...

I should be back online again tonight after assigning the DHCP to a different "pool" of IP addresses.

Thank you to all that have been posting and assisting!

---

### Post by chrisfay on 2006-12-20
> I wasn't trying to discount your reply

No worries...:p 

Just hope it gets you  up and run'n again!

---

### Post by dbqp on 2006-12-20
Okay, I tried unsuccessfully to change my DHCP to not include my servers static address. I changed the pool to  192.168.2.13 thru 192.168.2.99

My servers static IP is 192.168.2.11

I have included a [screenshot]("http://www.dbqp.com/IPNetwork.png") of this configuration. Is there something I am missing?

I have also attached a [screenshot]("http://www.dbqp.com/portmapping.png") of my port mapping - anything there?

Now, my router doesn't even show the server (Device) as connected. I can't ping to this machine from another PC on the network. I can't ping a machine from the server. nor ping any internet site.

My server is connected to a 16 port switch, since my router (4 port) is also my DSL modem, should I plug the server directly into the modem/router???

---

### Post by dbqp on 2006-12-20
Okay I bypassed the switch and connected straight to the router (and modem) and 192.168.2.11 now appears as a connected device, but can't identify the host name or the domain name. It does show the machines IP and how it is connected.

I can ping back and forth on the network between server and desktop, both ways.

I just checked the internet site and it appears to be working!

So in the end, I had to adjust the DHCP IP address pool to not include the servers static IP address and bypass the switch and go directly to my 4 port DSL/router.

I haven't checked externally, but will be doing this very soon...

Thank you to all who assisted me on resolving this issue.  Hopefully I haven't just placed a "band-aid" over the core problem and it reappears down the road.

:D

---

### Post by dbqp on 2006-12-20
> I haven't checked externally, but will be doing this very soon...

Just had someone check externally and all is working!

Thanks again!

---

### Post by chrisfay on 2006-12-20
> Just had someone check externally and all is working!

Glad to hear it....:mrgreen: 

Just curious, do you have any other devices connected to your switch successfully?

---

### Post by dbqp on 2006-12-20
> Just curious, do you have any other devices connected to your switch successfully?

Yes, all of my networked PC's (1 Linux, 1 Win2K, 1 Winxp MCE) and when my DHCP was calling the server the address I assigned it at the very beginning, it was working through the switch as well.

I am also using a second ethernet card in my server, but I don't believe I have set it up in my interfaces file...it is going to the switch.

Why do you ask?

---

### Post by chrisfay on 2006-12-20
> So in the end, I had to adjust the DHCP IP address pool to not include the servers static IP address and bypass the switch and go directly to my 4 port DSL/router.

I was just wondering why you where successful only when bypassing the switch. You should be able to run the server behind it just as easily as plugging it directly into the gateway.

But it's irrelevant since your network configuration is functioning now.:p

---

### Post by dbqp on 2006-12-20
> You should be able to run the server behind it just as easily as plugging it directly into the gateway.

But it's irrelevant since your network configuration is functioning now.

EXACTLY - which is why I am concerned that I have just placed a "band-aid" on the issue.  I would like to be on the switch as well.

FYI - my Devices listed within my router control panel shows 192.168.2.11 (server) as disconnected, but can still access it internally and externally...just a curious point...hmmmm

---

### Post by dbqp on 2006-12-20
> FYI - my Devices listed within my router control panel shows 192.168.2.11 (server) as disconnected, but can still access it internally and externally...just a curious point...hmmmm
Edit/Delete Message

And now it shows it as connected...

---

### Post by chrisfay on 2006-12-20
> which is why I am concerned that I have just placed a "band-aid" on the issue

IMO, your not band-aiding your system in any way by plugging the server directly into the gateway. Without the ability to view the setup its difficult to pinpoint where the break in communication is occurring with regards to the switch but, you're not in any way cutting corners.  

As long as the connection directly to the gateway isn't limiting the physical layout of your configuration there's no harm in it.

---

### Post by dbqp on 2006-12-20
> As long as the connection directly to the gateway isn't limiting the physical layout of your configuration there's no harm in it.

That is good to know. Thank you.

When you said gateway on this reply it logged my memory on another issue I was reading the other day. It was talking about a [conflict with using 2 NICs]("http://www.ubuntuforums.org/showthread.php?t=312499&highlight=two+ethernet+cards+in+server") and how the gateways are assigned. Could this be why I can't go through the switch?

My gateway IP in the interfaces file is 192.168.2.1 - which is my modem/router

---

### Post by chrisfay on 2006-12-21
> Could this be why I can't go through the switch?

It shouldn't be. Unless you have the second nic configured on the same subnet with a different gateway, or not configured at all. I think packets sent or received from your server in this case would get lost when trying to decide which route to take. 

How do you even have a second nic directed at your switch without defining its' properties in the interfaces file?

---

### Post by dbqp on 2006-12-21
> How do you even have a second nic directed at your switch without defining its' properties in the interfaces file?


Well, I did check and I have not set up this second NIC in my interfaces file. Could this actually be the reason the active NIC in the server couldn't go through the switch?

IF you have any thoughts on how to set up this second NIC properly, please let me know as I would love to discuss this further in a new thread.

Thanks as always!

---

### Post by chrisfay on 2006-12-21
Just happened to be on right when you posted this...:p 
> 
Could this actually be the reason the active NIC in the server couldn't go through the switch?

I'm not really sure. I would think that not setting up your second nic would cause problems with that interface only, but I'm not really sure why it would mess anything up on your active nic. Connecting your server to the switch shouldn't require any special steps unless the switch itself has some specific configuration settings that's causing problems. 

The settings you specified for the active nic in your interfaces file should have sufficed in getting packets correctly routed to your gateway and on to whatever location you intended. The switch should not have conflicted. 

Since the solution was to take the server off the switch and hook it up directly to the gateway, it leads me to believe the second nic has nothing to do with it. Or it would have also caused problems on the gateway. I would open a new thread and we can get some more input on what others think. Link this thread in your new one.

---

### Post by dbqp on 2006-12-21
> Since the solution was to take the server off the switch and hook it up directly to the gateway, it leads me to believe the second nic has nothing to do with it. Or it would have also caused problems on the gateway. I would open a new thread and we can get some more input on what others think. Link this thread in your new one.


That was the same line of thinking I was having, but it is always good to hear from another and from their perspective and/or experience!

I'll try to start a new thread tonight - I'll link back to this thread and put a link on this reply stating a new thread has been started on this subject.

:D

---

