---
title: "VMware vm networking"
date: 2008-08-10
forum: Server Platforms
---

### Post by sndnichols on 2008-08-10
I have set up a jeos vm on a 8.04 server. I want to assign it a static IP and see it on the network. My goal is to use it as my webserver. I tried to do it on my own but can't I have searched for 2 days to find the solution. Yesterday I couldn't connect to the network or the web. I re-installed using the defaults in ./vmware-config.pl. In the vm, I let it use DHCP. Can someone point me to a good how to, or let me know where I went wrong? Here is the ifconfig for the host:

```
> ifconfig
eth0      Link encap:Ethernet  HWaddr 00:e0:81:b0:9d:c6  
          inet addr:192.168.0.101  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:81ff:feb0:9dc6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:388227 errors:0 dropped:0 overruns:0 frame:0
          TX packets:238408 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:382253744 (364.5 MB)  TX bytes:81436085 (77.6 MB)
          Interrupt:248 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:367 errors:0 dropped:0 overruns:0 frame:0
          TX packets:367 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:18816 (18.3 KB)  TX bytes:18816 (18.3 KB)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:c0:00:08  
          inet addr:172.16.171.1  Bcast:172.16.171.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:95 errors:0 dropped:0 overruns:0 frame:0
          TX packets:100 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```


The ifconfig from the vm:

```
> ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0c:29:4d:c4:50  
          inet addr:172.16.171.128  Bcast:172.16.171.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:81ff:feb0:9dc6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:388227 errors:0 dropped:0 overruns:0 frame:0
          TX packets:238408 errors:0 dropped:0 overruns:0 car
          collisions:0 txqueuelen:1000 
          RX bytes:382253744 (364.5 MB)  TX bytes:81436085 (77.6 MB)
          Interrupt:17 Base address:0x1400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:367 errors:0 dropped:0 overruns:0 frame:0
          TX packets:367 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:18816 (18.3 KB)  TX bytes:18816 (18.3 KB)
```

The /etc/network/interfaces for the vm is:

```
auto lo
iface lo inet loopback

auto eth0
iface eht0 inet dhcp
```


TIA

---

### Post by sndnichols on 2008-08-11
No one knows, or is this the wrong forum, or do I need to go to KVM?

---

### Post by Titan8990 on 2008-08-11
KVM is the one that is supported by the debian based OSes...

---

### Post by dacorr on 2008-08-11
when the VM was created which type of networking did you let it use, ie NAT etc

Dac

---

### Post by windependence on 2008-08-11
Firstm did you set up the VM for bridged networking? (default) If so, you just need to set up your networking correctly in the JeOS guest. It has NOTHING to do with the VM software you are using. 

Log onto the JeOS VM in a terminal or even an ssh session from another machine. Then do:

```
sudo nano /etc/network/interfaces
```

Change it to look like this only using the network parameters from YOUR network instead of my example:

```
# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.3.90
gateway 192.168.3.1
netmask 255.255.255.0
network 192.168.3.0
broadcast 192.168.3.255
```

press ctl O (letter O) to save, and ctl X to exit.

Then do:

```
sudo /etc/init.d/networking restart
```

Your VM should now have a static IP address.

One more thing, you really need to check your VMware config because your IP for the VM is 172.16.171.128 which is not even on the same subnet as your network. No wonder you can't see it. Run your config.pl again and make sure you have bridged networking set up. You don't need NAT or host only networking so you can say no to those questions.

You should really think about getting more familiar with networking in both Ubuntu and VMware if you are going to run a production machine. There is lots of good info out there.

Hope this helps, questions please ask here.

-Tim

---

### Post by windependence on 2008-08-11
> **Titan8990 said:**
> KVM is the one that is supported by the debian based OSes...

Yes however there are lots of limitations as there are on most all the VM software out there today. Some require VT aware processors and some won't do certain guest OSs. I have found VMware to be the most flexible.

-Tiim

---

### Post by sndnichols on 2008-08-11
KVM is what I used before I rebuilt my server. I had "issues" with virt-manager. when it came out there were problems connecting to the host. I didn't see a patch, but with webmin, most of the problems were minor. Overall, I was satisfied.

> when the VM was created which type of networking did you let it use, ie NAT etc

On the initial install I went with the bridged networking and manually entered the network info. I couldn't connect to anything, so I reconfigured to NAT. I still couldn't connect to anything. So I reran the config and set it up NAT and was able to get out of the machine.

> One more thing, you really need to check your VMware config because your IP for the VM is 172.16.171.128 which is not even on the same subnet as your network. No wonder you can't see it. Run your config.pl again and make sure you have bridged networking set up. You don't need NAT or host only networking so you can say no to those questions.

The vm server config is where I thought the problem would be. I have run ./vmware-config twice now. That is how I was able to get out, finally. I will run it again and pay closer attention.  

> You should really think about getting more familiar with networking in both Ubuntu and VMware if you are going to run a production machine. There is lots of good info out there.

The research is part of why it is still offline. I have had it configured twice, but found "holes". I rebuilt it this time to CIS level 1 standards. As I noted above, I hae had it working well with KVM, but wante to try something different. Server console was much easier than virt-manager, which I couldn't get to work remotely. That may have changed in the last few months. Here is where a lot of the good information is :D


Thanks, after I run config again, I wiil get back.

---

### Post by sndnichols on 2008-08-11
Ok, still little joy. I can see the vm on the network, but I can't get out. VMnet0 doesn't show up in the host ifconfig. It looks the same as above with vmnet8 gone. During the config vmware said that vmnet0 was bridged to eth0. Does it just not show up as br0, or do I need to go to the interfaces and configure it there?

Thanks

---

### Post by sndnichols on 2008-08-11
Here is the new ifconfig for the host:

```
> ifconfig
eth0      Link encap:Ethernet  HWaddr 00:e0:81:b0:9d:c6  
          inet addr:192.168.0.101  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:81ff:feb0:9dc6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:388227 errors:0 dropped:0 overruns:0 frame:0
          TX packets:238408 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:382253744 (364.5 MB)  TX bytes:81436085 (77.6 MB)
          Interrupt:248 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:367 errors:0 dropped:0 overruns:0 frame:0
          TX packets:367 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:18816 (18.3 KB)  TX bytes:18816 (18.3 KB)

```

The ifconfig for the vm:```
> ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0c:4d:c4:50 
          inet addr:192.168.0.104  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:29ff:4efd:c450/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4042 errors:0 dropped:0 overruns:0 frame:0
          TX packets:423 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:247115 (241.3 KB)  TX bytes:38026 (37.1 KB)
          Interrupt:16 Base address:0x1400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1976 (1.9 KB)  TX bytes:1976 (1.9 KB)

```

As I mentioned before any good resources to browse/peruse is welcome.

Thanks.

---

### Post by sndnichols on 2008-08-12
Bump, for some more help.

---

### Post by windependence on 2008-08-12
Hmmm you shouldn't have to do anything to the host after you configure your bridge. 

Can you ping your gateway from your VM?

If you could post your /etc/network/interfaces on both the host and the VM, that would help too.

-Tim

---

### Post by sndnichols on 2008-08-12
I didn't try to ping the router, but I could ping host and other computers. I will try the oruter when I get home in about 5 hours. I will also post /interfaces for vm and host. Do you think I may need to add the vm to my hosts file?

---

### Post by windependence on 2008-08-12
So you could communicate with your LAN but not with anything outside on the internet? Sounds like your gateway may be misconfigured OR you have a simple DNS problem. Hopefully we can fix that. :)

-Tim

---

### Post by sndnichols on 2008-08-12
I have a linksys with the easy config advisor, I thin its called. The VM shows up on it. I turned off all the blocking and still couldn't get out. I also added the MAC address to the allowed (I use MAC filtering).

---

### Post by sndnichols on 2008-08-12
Here is the interfaces file for the host:

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.0.101
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.1
```


Here is the interfaces file for the vm:

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.0.104
        gateway 192.168.0.1
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        
```

As I was reading this, it dawned on me that perhaps the vm iface should be set o vmnet0. I am going to try that and wll post the result.

---

### Post by sndnichols on 2008-08-12
Oops DP

---

### Post by sndnichols on 2008-08-12
Well, vmnet0 didn't work. The vm said there ain't no such thing. Next I'll try vmnet8, although that should be for NAT.

Well, smae wth vmnet8. That doesn't suprise me.

---

### Post by windependence on 2008-08-12
Those are virtual interfaces. You generally don't want to mess with those. Can you ping something on the outside of your network, like yahoo.com?

Also, what is in your /etc/resolv.conf on both machines?

-Tim

---

### Post by sndnichols on 2008-08-12
The resolv.conf for the host is:

```
search natcky.rr.com
nameserver 76.85.229.110
nameserver 76.85.229.111
```

The resolv.conf for teh vm is:

```
search localdomain
nameserver 172.16.171.2

```

I think I know enough to know the vm resolv.conf is wrong, but I haven' learned enough to know what it should be. Seems like it should be the same. Am I correct/

---

### Post by windependence on 2008-08-12
Yes, there is your problem. Make the VM file the same as your host file and restart the VM network.

-Tim

---

### Post by sndnichols on 2008-08-12
If I wasn't entirely correct, it still works. What are some good books to get on this stuff? I didn't see it in the LASG, the vmware admin guide, and I missed the resolv.conf problem. I know this is a good way to learn, sort of, but I odn't need to screw stuff up later either.

Thanks

---

### Post by windependence on 2008-08-12
So it's working now? Great!

It really didn't have anything to do with VMware, just the config on your VM. Well in a way it did because the first config you did gave it a NAT address on a different subnet for your DNS. Anyway, glad you got it going. If you need any more help, please ask in the forums. I am always here in the server forum. :)

-Tim

---

