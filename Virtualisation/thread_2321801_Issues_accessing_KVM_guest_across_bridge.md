---
title: "Issues accessing KVM guest across bridge"
date: 2016-04-24
forum: Virtualisation
---

### Post by csete on 2016-04-24
I'm in the midst of building a new dual-NIC home server using Ubuntu 16.04.  I've been using the new systemd configuration to set up the network and have mostly gotten things working.  One problem I have right now is with my Windows 10 KVM VM networking.  I've set up a bridge for the network and connected the Windows VM to that bridge.  I can see that it has the proper IP address from my DHCP server.  The Guest can make outbound connections just fine, but despite having an IP address in the proper subnet, I can't connect into the Windows VM.  I'm not entirely sure where to look to properly configure this problem and could use some pointers.

Thanks!
Craig

---

### Post by Doug S on 2016-04-24
Maybe a moderator will be kind enough to move this over the the virtualization forum, as it might get better exposure there.

I haven't had any troubles with respect to my network bridge and my KVM guests upon the change from 14.04 to 16.04. My guests VM's get their IP address from my DHCP server (also a 16.04 Ubuntu server) just fine. They also are on my main LAN (Local Area Network) and accessible. 

Could you tell us more about your setup? Is your new dual-NIC home server also your DHCP server and router? Do you have just one LAN? What is it your are trying to access on your windows VM? Consider using tcpdump (or wireshark, if you prefer) to observe packet flow on your server.

---

### Post by csete on 2016-04-24
Thanks for your thoughts... and if the virtualization forum is a better place, I'm fine by that...

The server *is* my all-in-one server machine.  It acts as DHCP server (dnsmasq) and firewall (shorewall).  I have one LAN subnet.  The VM that I carried over from the old server had a VNC server running on it which is what I'm initially trying to (unsuccessfully) connect to.  Beyond that, there is the PlayOn server that is something I'd really like to properly access.  I'm happy to collect network dumps if people think there would be useful information in there...

---

### Post by Doug S on 2016-04-24
O.K. I differ from you in that my VM's run on a different server than my main server, not that it should matter.
I was only suggesting to use a packet sniffer so as to, perhaps, determine where packets are going astray, i.e. not getting there in the first place or somewhere in the return path.
Have you not been able to connect to your windows VM at all? i.e. do you know that it is even running? I assume , yes as you mentioned it is getting a proper IP address from your DHCP server. Can you even ping your windows VM?

---

### Post by jeremy31 on 2016-04-24
"*Thread moved to **Virtualisation**.*"
With a redirect left behind

---

### Post by csete on 2016-04-24
I can see the screen via virt-manager user interface, so I know it is running.  I can interact with it from that UI to see I can connect from there out to the internet.  However trying to connect host -> guest does not seem to be working.    Is there any way to trace a packet through the network stack?

---

### Post by Doug S on 2016-04-25
> **csete said:**
> The server *is* my all-in-one server machine.  It acts as DHCP server (dnsmasq) and firewall (shorewall).Would it be possible to do an experiment with your firewall disabled?

---

### Post by MAFoElffen on 2016-04-25
Please post the following from your Virtual server hosting the KVM Service:
```

ifconfig -a
sudo brctl show
sudo netctl list
cat /etc/network/interfaces

```
(To show all network connections, show all bridges and their status, show the config file... and see if those indicate anything.) 

Notes: 
-If the server has private (local NID) addresses, fine to post... but if public address, edit your output with "X's" after the first 6 numbers.
-Depending on how you installed your bridge, netctl may or may not be enabled. If netctl gets a profile error, then do:
```

systemctl list-unit-files|grep enabled

```

Also, if you could ssh into this server, please post the remote welcome screen of this . The reason for this is that that the welcome screen of a remote session will display the IP addresses of all network connections of that server... A quick way to see if an expected bridge is up or not... and show what IP address it is using for it's gateway (and be able to get the NID from that).

---

### Post by csete on 2016-04-25
> **Doug S said:**
> Would it be possible to do an experiment with your firewall disabled?

I followed these instructions to accept all with iptables [http://wiki.loovsys.eu/index.php/Clear_all_iptable_rules_and_allow_everything](http://wiki.loovsys.eu/index.php/Clear_all_iptable_rules_and_allow_everything) but didn't see any difference.  No ping and no VNC connection.

---

### Post by csete on 2016-04-25
```

&#9584;&#9472;&#10148;  ifconfig -a
br0       Link encap:Ethernet  HWaddr 92:b2:35:a2:a5:92
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::90b2:35ff:fea2:a592/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2806320 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3432793 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:515458026 (515.4 MB)  TX bytes:4712835619 (4.7 GB)

dmz0      Link encap:Ethernet  HWaddr 00:05:1b:xx:xx:xx
          inet6 addr: fe80::205:1bff:fed0:13ad/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2774244 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3901937 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:519697107 (519.6 MB)  TX bytes:4742645572 (4.7 GB)

enp1s0    Link encap:Ethernet  HWaddr 48:0f:cf:xx:xx:xx
          inet addr:192.168.15.3  Bcast:192.168.15.255  Mask:255.255.255.0
          inet6 addr: fe80::4a0f:cfff:fe42:6bad/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3317833 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1702567 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:4078014620 (4.0 GB)  TX bytes:184820599 (184.8 MB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:145969 errors:0 dropped:0 overruns:0 frame:0
          TX packets:145969 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1
          RX bytes:305462637 (305.4 MB)  TX bytes:305462637 (305.4 MB)

virbr0    Link encap:Ethernet  HWaddr 52:54:00:5a:4d:b8
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

virbr0-nic Link encap:Ethernet  HWaddr 52:54:00:5a:4d:b8
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vnet0     Link encap:Ethernet  HWaddr fe:54:00:e4:fc:d3
          inet6 addr: fe80::fc54:ff:fee4:fcd3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:93898 errors:0 dropped:0 overruns:0 frame:0
          TX packets:447054 errors:0 dropped:331642 overruns:0 carrier:0
          collisions:0 txqueuelen:500
          RX bytes:24542064 (24.5 MB)  TX bytes:120511168 (120.5 MB)

```

```

&#9584;&#9472;&#10148;  sudo brctl show                                                                                                                                         1 &#8629;

bridge name	bridge id		STP enabled	interfaces
br0		8000.92b235a2a592	no		dmz0
							vnet0
virbr0		8000.5254005a4db8	yes		virbr0-nic

```

```

&#9584;&#9472;&#10148;  sudo netctl list
sudo: netctl: command not found

```

NOTE: I'm using systemd configuration files, so I don't have an interfaces file.

---

### Post by csete on 2016-04-25
I'm not sure if this is at all related.  I have also noticed that after I reboot the system that, while DNSMasq is up and running, it doesn't appear to be accessible to servers on the network.  If I restart the DNSMasq service then things start working.  Is there some kind of timing or ordering issue in my networking setup?  I have to say that I still don't have a feel for how the systemd networking stuff really works.

Thanks again for anything you can do to help.
Craig

---

### Post by Doug S on 2016-04-25
You are doing things somewhat differently than I. Sorry, I do not know what to suggest.

---

### Post by csete on 2016-04-26
> **Doug S said:**
> You are doing things somewhat differently than I. Sorry, I do not know what to suggest.

Thanks for the attempts to help.  At this point, I think I'm going to step back and replace systemd networking configuration with old school /etc/network/interfaces configuration and match up to the way my old server was configured.  Having done some reading last night, it seems like maybe the systemd networking stuff is a bit too new and I really don't need the more dynamic nature of that system.

Unfortunately, I likely can't try to do something like that until this weekend, so I won't know for sure until later if I can make that work any better.

Thanks again,
Craig

---

### Post by Doug S on 2016-04-26
> **csete said:**
> At this point, I think I'm going to step back and replace systemd networking configuration with old school /etc/network/interfaces configuration and match up to the way my old server was configured.Even though my servers are 16.04, I am still using /etc/network/interfaces ( I actually never thought to do otherwise).

---

### Post by MAFoElffen on 2016-04-26
> **Doug S said:**
> Even though my servers are 16.04, I am still using /etc/network/interfaces ( I actually never thought to do otherwise).
Honestly, 4 of my Virtual Server Host Servers are also. In the 15.10 and 16.04 dev cycles, I forced myself to try out some of the systemd features, such as brctl and kernel virtualization with nspawn... But those 4 servers (mentioned earlier) where servers that were previously 14.04 LTS, so already had existing virtual networking setup. The older methods still work.

The newer methods look cleaner from the outside, works like a charm when successfully setup... but a mess to setup and a nightmare to diagnose. (...finding out what a user might have done.) When I start telling users (whom I don't know how much Linux skills they possess) to start editing system files under the hood ... that can break their system in a heart-beat if not done right, I get nervous. The "new" (using systemd) is not "common-user friendly."

I'm thinking I need to spend some time setting up a thread to explain Virtual Networking in Ubuntu 16.04. An explanation and tutorial in layman's terms. I think that would solve most of these misunderstanding and these new issues. (hopefully) Or if you want to collaborate on that, I do have finals coming up next week, but after that... I will have a lot more time. (Either that, or write a script or app to simplify those configurations...)

> **csete said:**
> ```

&#9584;&#9472;&#10148;  ifconfig -a
br0      inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::90b2:35ff:fea2:a592/64 Scope:Link

dmz0   inet6 addr: fe80::205:1bff:fed0:13ad/64 Scope:Link

enp1s0 inet addr:192.168.15.3  Bcast:192.168.15.255  Mask:255.255.255.0
          inet6 addr: fe80::4a0f:cfff:fe42:6bad/64 Scope:Link

virbr0  inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0

virbr0-nic 

vnet0   inet6 addr: fe80::fc54:ff:fee4:fcd3/64 Scope:Link

```

```

&#9584;&#9472;&#10148;  sudo brctl show                                                                                                                                         1 &#8629;

bridge name    bridge id        STP enabled    interfaces
br0        8000.92b235a2a592    no        dmz0
                            vnet0
virbr0        8000.5254005a4db8    yes        virbr0-nic

```

```

&#9584;&#9472;&#10148;  sudo netctl list
sudo: netctl: command not found

```

NOTE: I'm using systemd configuration files, so I don't have an interfaces file.
Please explain yourself. Post the files you edited to have systemd dynamically configure your bridge? Or post the script you are using to functionally do the same?

Because this >> "Command not found" << on the netctl command indicates that you did not configure a bridge via manually using the systemd brctl ... so how did you configure that bridge? (br0 and dmz0?) br0 is functional. dmz0 is not.

The next step would be to post the output from what I last asked about:
```

systemctl list-unit-files|grep enabled

```

---

### Post by Doug S on 2016-04-26
> **MAFoElffen said:**
> But those 4 servers (mentioned earlier) where servers that were previously 14.04 LTS, so already had existing virtual networking setup. The older methods still work.That is exactly my case as well.

> **MAFoElffen said:**
> I'm thinking I need to spend some time setting up a thread to explain Virtual Networking in Ubuntu 16.04. An explanation and tutorial in layman's terms. I think that would solve most of these misunderstanding and these new issues. (hopefully) Or if you want to collaborate on that, I do have finals coming up next week, but after that... I will have a lot more time. (Either that, or write a script or app to simplify those configurations...)Putting on my Ubuntu doc team hat, I would be very interested in any subject matter expert input that could be used to improve this area of [the Ubuntu Serverguide]("https://help.ubuntu.com/lts/serverguide/libvirt.html").

---

### Post by csete on 2016-04-28
I switched back to using /etc/network/interfaces today and it didn't make a difference.   While looking at the Windows guest again it asked me something about configuring the network.  It was at that point that I realized that while bringing the KVM host over I had some setup issues and it created a couple of new Windows network connections along the way.  It turns out that those network connection resets caused Windows Firewall to kick in and it was Windows Firewall blocking the connections.  I honestly feel foolish that I didn't think about the Windows Firewall side of things as the culprit from the beginning.

Now that I know the systemd configuration is not to blame, I will probably switch back to using that since it seems like that is the future direction.  Are there any known issues with persistent network link naming?  I was able to get one of my NIC's named "dmz0" using a link file with MAC address.  However, I've been unable to get the other network interface to be "inet0" no matter what I specify in the link file.  It is like it either isn't matching or if it is matching that something else is overriding the name change and setting it back to enp1s0.  This is by no means a big deal, but it would be nice to be able to get both interfaces named the way that I would like.

Thanks,
Craig

---

### Post by MAFoElffen on 2016-04-30
So now that the Win Firewall is allowing, dmz0 is working?

---

### Post by csete on 2016-04-30
> **MAFoElffen said:**
> So now that the Win Firewall is allowing, dmz0 is working?

Actually dmz0 was always working for everything except into the Windows guest.  Now the guest is working as expected as well.

As I mentioned previously, my only remaining open question is trying to get the other interface renamed to "inet0" using the new persistent naming support.  For some reason, it won't "take" no matter what I try for the match expression and I'm not seeing any errors in the logs.

---

