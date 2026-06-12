---
title: "Network to VM-Ware"
date: 2016-05-03
forum: Server Platforms
---

### Post by asearle on 2016-05-03
Hallo Everyone,

I need to work on a Linux server and have been given a test version of this as a VM-Ware machine.  It works fine (under VM-Ware Player).

There is a Zope Server on the VM-Ware machine that I need to connect to from the Host-PC and so I have been looking at the VNC-settings in the VM-Ware installation (on the Host-PC) in the hope that I can connect to the virtual machine through that (Port 5900) but it doesn't seem to work like that so I think I am barking up the wrong tree.

On a local-host I would connect to the server using the URL  [http://localhost:8080/](http://localhost:8080/) so what I need is the syntax (and tools?) to connect to this address in the virtual machine from a browser on the Host-PC.

Yes, virtual machines seem to be able to access the outside network from within their environment so what I need is to be able to go in the other direction.  It must be possible but all I need is a little tip to tell me where to look.

Many thanks,
Alan Searle
Cologne, Germany

---

### Post by Bucky Ball on 2016-05-03
*Thread moved to **Server Platforms**.*

---

### Post by asearle on 2016-05-05
Hallo Everyone,

I have had a few tips from colleagues telling me to set the Network Settings in the VM-Ware workstation to "Bridged" in order to be able to access the VM (virtual machine) from the host.  I have done this (and also ticked "Replicate physical network connection state").

Also I was told that the subnet masks in both the host and the client (workstation) must be the same.

On the client/workstation there is a (zope) webserver installed with the ip address 172.20.110.138.

So I ran ifconf and got the following (some text removed, in German but it should be mostly understandable) ...

```

lo        Link encap:Lokale Schleife  
          inet Adresse:127.0.0.1  Maske:255.0.0.0

vmnet1    Link encap:Ethernet  Hardware Adresse 00:50:56:c0:00:01  
          inet Adresse:192.168.93.1  Bcast:192.168.93.255  Maske:255.255.255.0

vmnet8    Link encap:Ethernet  Hardware Adresse 00:50:56:c0:00:08  
          inet Adresse:172.16.138.1  Bcast:172.16.138.255  Maske:255.255.255.0

wls3      Link encap:Ethernet  Hardware Adresse 00:1f:3c:98:6e:3f  
          inet Adresse:192.168.178.74  Bcast:192.168.178.255  Maske:255.255.255.0

```

Now I need to match up the settings so that a browser on the Host (PC) can access the webserver on the client (VM workstation) and am hoping that someone can give me some tips?  Maybe there is a HOWTO somewhere than can help me sort this out.

I am sure it is not so difficult but I do need a nudge in the right direction.

Many, many thanks,
Alan Searle
Cologne, Germany

---

### Post by SeijiSensei on 2016-05-07
You don't have an interface with an address in 172.20.110.0/24 so you need a route to it somewhere.  Since your network topology looks rather complex, I'm not sure where to add the route.  You can try installing **traceroute** on a client that needs access to Zope, then run "traceroute -n 172.20.110.138" on that machine.  Does it time out somewhere along the way?  If so, that machine lacks a route to the 172.20.110.0/24 network.

---

### Post by nerdtron on 2016-05-07
Before you changed the network setting to "Bridged" did you configure the linux VM with static IP address? If yes, you'll need to change the IP address again after you changed to "Bridge" mode since the subnet of the VM should now be the same as the subnet of the Host machine.

It would be better for us to understand if you show the ifconfig output of the Host machine and the Virtual machine.

---

### Post by asearle on 2016-05-08
Dear Mononoke,

Many thanks for the feeback.  I ran traceroute and got the following ...

```

traceroute to 172.20.110.138 (172.20.110.138), 64 hops max
  1   192.168.178.1  0,949ms  0,643ms  1,125ms 
  2   195.14.226.82  19,430ms  20,152ms  18,912ms 
  3   89.1.16.105  17,626ms  17,274ms  18,076ms 
 28   *  *  * 
 29   78.35.33.201  17,903ms !N  16,334ms !N  16,478ms !N 

```

... which confirms that I am not seeing the ip-address of the client/vm(?)

I will be posting more information in reply to nerdtron's comments so maybe you can take a look at what I post there?

Many thanks,
Alan

---

### Post by asearle on 2016-05-08
Dear nerdtron,

Many thanks for getting back to me on this.

As it is, I am reading/googling like mad to try to get my networking knowledge up to scratch.

One thing I have noticed is that it is recommended to use "Virtual Network Editor" to set this up but somehow, although I see a directory "virtual network editor" within in the directory "vmware-installer", this tool does not seem to be installed (or at least I can't work out how to open it).  Apparently the program's name is vmware-config.pl.  Do you have any tips for me there?

Regarding output from ifconfig, I re-ran this on host an on client and am even more confused with the output ...

```

enp0s25   Link encap:Ethernet  Hardware Adresse 00:1f:e2:10:56:ca  
          inet Adresse:192.168.178.96  Bcast:192.168.178.255  Maske:255.255.255.0

lo        Link encap:Lokale Schleife  
          inet Adresse:127.0.0.1  Maske:255.0.0.0

wls3      Link encap:Ethernet  Hardware Adresse 00:1f:3c:98:6e:3f  
          inet Adresse:192.168.178.74  Bcast:192.168.178.255  Maske:255.255.255.0

```

... as the vmnet-entries (that had appeared before, output in earlier posting) having disappeared even though the network was up.  I'll try a re-start (of everything) now.

The other thing that I noticed was that in my earlier ifconfig output vmnet0 (for Bridged) was missing.  That can't be right, can it?

```

eth0   Link encap:Ethernet  Hardware Adresse 00:0c:29:ed:dc:49  
          inet Adresse:172.20.110.138  Bcast:172.20.110.255  Maske:255.255.255.0

```

My other thought is that, I really don't need to give the client access to the (outside) network but really only need to access the webserver (currently 172.20.110.138, ie the client) from a browser on the host-computer.  Would I maybe get better/quicker results with NAT or Host-only settings? 

I am a bit out of my depth but my knowledge is growing (and I really do need to get this connection running) so I do hope that you can help to nudge me in the right direction.

Many thanks,
Alan

---

### Post by darkod on 2016-05-08
I haven't used VMware Player, only ESXi, so I don't know how exactly to configure the options, but like others have said I agree to use the bridge mode. You want the VM to be like inside your local LAN, and only bridge mode does that. NAT is messy for such setups. Also you need to investigate what "Replicate physical connection state" exactly means because you don't need an exact replica on the VM. The IP needs to be different but I assume this option would not replicate the IP too because that wouldn't make much sense.

In Virtual Box for example you only turn bridge mode on and that's all you need.

On the VM side, posting the ifconfig doesn't help us much. Please post the content of /etc/network/interfaces, that's much more important because your network setup is in there. After that we would be able to advise more.

---

### Post by SeijiSensei on 2016-05-08
> **asearle said:**
> ```

traceroute to 172.20.110.138 (172.20.110.138), 64 hops max
  1   192.168.178.1  0,949ms  0,643ms  1,125ms 
  2   195.14.226.82  19,430ms  20,152ms  18,912ms 
  3   89.1.16.105  17,626ms  17,274ms  18,076ms 
 28   *  *  * 
 29   78.35.33.201  17,903ms !N  16,334ms !N  16,478ms !N 

```
Can you alter the configuration of the router at 192.168.178.1?  If so, you need to add a static route on that router for the 172.20.110.0/24 network subnet.  As it stands now, the router is sending that traffic out to the public address 195.14.226.82 which doesn't know what to do with it so it keeps passing it up to other routers that also don't know what to do with it.

If all this is new to you, you probably need to talk with your IP staff.

---

### Post by nerdtron on 2016-05-08
I'm more confused on your output since you did not indicate which is the host and which is the VM on that output. Let's try not to over analyze the configuration of the network on the VM. Let's try to do this step by step.

If I understand your problem correctly:
> On a local-host I would connect to the server using the URL  [http://localhost:8080/](http://localhost:8080/) so what I need is the syntax (and tools?) to connect to this address in the virtual machine from a browser on the Host-PC.

You have an installed program on the VM which is on port 8080 and you want to access it via the browser of main Host-Computer.

If yes, here's the short answer: you don't have to configure anything at all. You just type the [http://IP.address.of.VM:8080/](http://IP.address.of.VM:8080/) on the Host-PC and you're done.

First off, just to set things right, you can do this even on NAT configuration of the VM. See below my example:
My VM has the below IP, I've set it to DHCP in the mean time just to make sure it gets the correct IP subnet:
```

nerdtron@ubuntu:~$ ifconfig 
ens33     Link encap:Ethernet  HWaddr 00:0c:29:fe:53:82  
          inet addr:192.168.183.128  Bcast:192.168.183.255  Mask:255.255.255.0
          inet6 addr: fe80::fc19:f361:b14:4c6f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:28 errors:0 dropped:0 overruns:0 frame:0
          TX packets:163 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4021 (4.0 KB)  TX bytes:15854 (15.8 KB)

```

Now on the Host-PC machine, I have this IP: 192.168.183.1. (you will notice they are on the same subnet with the VM). 
 You can see here that I can ping the Host-PC from within the VM.
```
nerdtron@ubuntu:~$ ping 192.168.183.1
PING 192.168.183.1 (192.168.183.1) 56(84) bytes of data.
64 bytes from 192.168.183.1: icmp_seq=1 ttl=128 time=0.508 ms
64 bytes from 192.168.183.1: icmp_seq=2 ttl=128 time=0.389 ms
64 bytes from 192.168.183.1: icmp_seq=3 ttl=128 time=0.343 ms

```

Now that I'm sure that I have established connectivity between host-PC and VM, I should now be able to access port 8080 of the VM from the Host-PC. 
So I can now open a web browser on the Host-PC and type [http://192.168.183.128:8080](http://192.168.183.128:8080) on the URL bar and I should be able to access the program running on port 8080 of the VM.

I did not do any manual network configuration. I just let VMware to have  a NAT configuration and allow to VM to get it's own IP given by vmware.

Remember, the main goal you want the VM and Host-PC to have at least one IP that is on the same subnet. And that they should be able to ping each other. I hope this shed some light on the issue.

---

### Post by asearle on 2016-05-10
Dear Nerdtron,

Yes, you were/are absolutely right and it is much simpler than I was assuming.

It turned out that, yes, Vmware sets up bridging automatically and that nothing needs to be changed/added (bravo VMWare!).

The problem was that the client that I was running had a static ip-address while that host was using DHCP.  I could have set a static ip-address in the host but instead I switched the client to DHCP (in /etc/network/interfaces ) and restarted the client instance and it worked.

But you need to be careful because, with DHCP, the ip-address can change.  So what I do is to run ifconfig directly after starting the client to see what ip-address has been allocated.  This can then be checked by pinging the client from the host.  If the ping works then everything is OK.

Regards and thanks,

Alan

---

### Post by MAFoElffen on 2016-05-11
I may be wrong (hopping in at a later post and skimming the posts between OP and last) ...

I support Hyper-V, Xen/Citrix, KMS, VirtulaBox, VMware's Fusion, Player, Workstatin and ESXI/VSphere... So I might be able to shed a little light on this. 

I am assuming that the OP's Host NID (network ID) is 192.168.183.0/24. I am assuming that the OP's original VM's IP when it was first installed was in the 172.20.110.0/24 NID range. Right so far?

The OP said he wanted to move the VM to the host's NID via a bridge.. The reason for goinng this way instead of a static route (which is still an option and works) is that with a virtual bridge, you can check the status of, bring it up/down... as if it were on metal. (It is easier to diagnose and manage.)

When the VM was installed, did you set the VM's NIC setting to NAT? I am thinking so, as 172.20.110.0/24 reminds me as a NAT range for a virtual network. On one of my support test boxes running current VMware Player, it has vmnet1 @ 172.16.1300/24 and vmnet8 @ 172.16.45.0/24... Both VMware Player and VirtualBox'es defualt connection is via NAT. Same with Hyper-V and KVM. Doing bridge takes a few extra steps to install and configure a bridge on the host.

For a virtual route, you could run a static hop (route rule)... but that would be a psuedo virtual router, not a bridge. (not the same NID range, you would provide a route between the different NID's) 

More common in virtual networking is to create a "bridge" between your virtual net and your host's net. (In some hypervisor's this is called a virtual switch.) In Ubuntu you are going to do this by first installing bridge-utils, then configuring your bridge. Did you install the package bridge util's?
```

sudo dpkg -l | grep bridge-utils
sudo brctl show

```
This second command will list bridges and show which interfaces they are associated with. ...Which I already do not see a bridge in any of your output, that I saw.

With recent integration of systemd, there are now more ways to configure a bridge than you can shake a stick at... which makes deciding which way you want to go a bit confusing. Some of those new ways are not well documented yet. The easiest and most documented way to create a bridge requires that you have more than one NIC, so that when you configure your bridge (associate the bridge to a port) that all bridged traffic goes through that dedicated port, without taking over your host's own connection. 

Hardest, it to try to share a single NIC for both the host and the bridge... by segmenting the port into logical layers. That assumes that the NIC hardware present in that server supports that technology. Except when you are dealing with VMware, which has their own way they do that as internally... (At least on ESXi and WorkStation.) Not sure how they do that but they do. Just set to bridge, set your ip to a host NID range and use it.

After configuring the bridge, then you reconfigure your VM to have a static IP in the Host's NID range.

Hopefully, that brief explanation, and those questions will provide enough info both ways to get you back on track. I'm now following this thread..

---

