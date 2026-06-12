---
title: "Configuring Ubuntu 10.10 Server in VMware?"
date: 2011-02-17
forum: Server Platforms
---

### Post by hostingservices on 2011-02-17
Hey there, this is my first post on the forums ):P. So to begin, I have attempted to set up ubuntu server 10.10 on my home network. I only have one computer and access to windows is a must for me, so what I have been doing is installing the server via VMware as a virtual server. Now, I have been able to successfully set up a server that works on the LAN, but for some reason I have been unable to get access to the server via the external ip address.

I will list all known information about my network, host computer and VMware.

I'm currently using VMware Workstation. For the virtual machine I have installed, I have allocated 500 GB of space to a partition on my 2 TB external hard drive. The network is currently set to NAT, but I would much prefer to Bridge the network so that the guest would be assigned a unique LAN address.

The host computer is a laptop. It is connected to the internet through a wireless router. I can successfully host a teamspeak server that accepts incoming traffic from the internet. The operating system that is installed is Windows Vista.

The network is set up as follows:

[IMG]http://a.dyndns.com/images/kb/hosts.gif[/IMG]
The host's LAN address is 192.168.1.50 and is connect to the Router which has an address of 192.168.1.1. I am using a Netgear WNDR3300v1 wireless router. The webserver itself would likely have the IP 192.168.1.2 in the circumstance that the network was bridged for the virtual machine. So the WAN Interface would be the modem my company has provided which has assiged the external IP 24.113.92.228. The modem is a cable modem, the brand is a motorola surfboard. 

I have tried many tutorials on the web, including "The Perfect Server Ubuntu 10.10" so please do not just recommend a tutorial or some guide to set up the server.

To be honest, I know very little about Ubuntu and have been working with it for 3 days. I have learned a lot about using the cmd, but unfortunately I haven't really been able to learn a lot about configuring files. I'd say the thing I really need help with is getting the server to work through SSH, DNS and Apache.

I look forward to any help possible. If you have any further questions please ask.

---

### Post by ashikaga on 2011-02-17
Hi there,

Is this a port-forwarding issue? If your router doesn't allow you to forward incoming HTTP requests to a specific IP on your LAN, you may need to get one that does. Your model does not seem to be listed on the relevant Netgear [page]("http://kbserver.netgear.com/kb_web_files/n101145.asp") for configuring port forwarding. The online Netgear documentation [here]("http://kb.netgear.com/app/answers/detail/a_id/1166") seems to suggest that unless your model's docs explicitly say otherwise, then all incoming ports are closed. I don't have any Netgear stuff so I'm just assuming that's correct.

---

### Post by hostingservices on 2011-02-17
My router has port forwarding/port triggering. I'm not sure if the ports are the issue or not.

Ports Forwarding:

80
9987

Ports Triggering:

22
53
25999

Those are all the ports being forwarded and triggered.

---

### Post by Neo@Matrix on 2011-02-17
If I where U (luckily I am not :) ) I would set static IP address for all boxes on the UR LAN, than I would use DMZ for the 192.168.1.50, It would expose this virtual server to the internet. By static IP addresses in LAN network , U would avoid problems of DHCP LAN IP  address exp. Also DMZ would forward all ports to the server by default.
I have much-a-like network with multi-servers.

---

### Post by hostingservices on 2011-02-17
> If I where U (luckily I am not :smile:  ) I would set static IP address for all boxes on the UR LANI am only using my laptop to host this server. The host OS is Vista like I said. I'm running the server through VMware.

The IP of Vista is xxx.xxx.xxx.50 while the VM is xxx.xxx.xxx.2. (Too lazy to type whole address.) Both are set are reserved by my router for the corresponding Machine.

> than I  would use DMZ for the 192.168.1.50, It would expose this virtual server  to the internet.I've already assigned xxx.xxx.xxx.2 as the default DMZ server.

> By static IP addresses in LAN network , U would avoid  problems of DHCP LAN IP  address exp. Yeah, that was the first thing I learned when trying to host a teamspeak server on my Vista machine. My TS Server works wonderfully unlike my linux server.

> Also DMZ would forward all ports  to the server by default.Well I hope that could solve any problems. I honestly have no way of really checking to see if my server is up until I have apache server installed. I could then check through a proxy to see if its accessible to the internet.

> I have much-a-like network with multi-servers.I'm not sure if my network itself is the cause behind my issues or if its the configuration of the server itself or a combination. I only plan to host one linux server for the time being since its still a trial and error process.

[Update] I just tried connection to my external address via PuTTY and I managed to connect to my server, though I'm not completely sure if its accessible to the internet or not. So as far as I'm concerned, unless one of you would be interested in testing my server access via SSH for me this topic is still up for assistance.

[Error] I am attempting to install apache, but I for some reason get "temporary failure resolving 'security.ubuntu.com." Does anybody know how to fix this error?

---

### Post by Neo@Matrix on 2011-02-17
Sure , I'll gladly assist U in any way. PM me the link to UR server , and I'll try to connect.
I have a network of 12 servers hosting 20+ domains , might help with my xp.

Check ur settings for update sources...

---

### Post by hostingservices on 2011-02-17
Thank you, I've sent you the external IP.

[Update] My current problems have been resolved. My server is now working. To test my server go to [www.ondemandteamspeak.co.cc]("http://ubuntuforums.org/ww.ondemandteamspeak.co.cc"). Thank you for your help everyone.

---

