---
title: "Allow single threaded process (OpenVPN) to use entire core?"
date: 2017-02-07
forum: Server Platforms
---

### Post by m-dw on 2017-02-07
I'm using my Atom based server as a VPN router between my LAN and a 200 Mbit/s cable internet connection. When doing speed tests via the VPN I'm unable to utilise the entire bandwidth - I typically get about 40Mbit/s, and I've increased it to about 48% by renicing the OpenVPN process to -20.

CPU utilisation on the core running the openVPN process seems to approximately match the throughput in Mbit/s - i.e. at 30Mbit/s the CPU is approx 30% utilised, and at 50Mbit/s it is 50% utilised. In my simple network engineer brain this suggests that the throughput could be pushed to 100Mbit/s if the CPU core could be fully utilised. So 2 questions:
[LIST=1]
[*]Is the server likely to be throttling the amount of CPU openVPN can use?
[*]Is it possible to override this setting?
[/LIST]

---

### Post by TheFu on 2017-02-07
For people with lots of VPN sessions and lots of bandwidth to use, they usually need a full desktop CPU - i5/i7 with AES-NI on the chip. Some links:
[https://airvpn.org/topic/10799-aes-ni-performance-analyzed/](https://airvpn.org/topic/10799-aes-ni-performance-analyzed/)
[https://community.openvpn.net/openvpn/wiki/Gigabit_Networks_Linux](https://community.openvpn.net/openvpn/wiki/Gigabit_Networks_Linux) shows that CPU offloading to the NIC is absolutely critical to get performance.

If the NIC isn't a quality Intel one, the CPU could be busy doing interrupts since Realtek and other non-intel NICs offload a bunch to the CPU.

Also be aware that **iperf** results are for ideal-world situations, not real-world.  Transferring actual data is necessary to get real-world results.

---

### Post by m-dw on 2017-02-08
Ah, good to know. Thanks. lspci says I have 2 x Intel Corporation 82574L Gigabit Network ethernet controllers, but my CPU is only an Atom D525 clocked at 1.8GHz so no aes-ni support. I am looking into the possibility of getting a hardware SSL acceleration card to offload AES-256 from the CPU, but it's a bit of an unknown, and it might not necessarily help. To be honest I don't really suffer with having "only" 40Mbit/s, but the up to 200Mbit/s contract is the only way to get unlimited downloads.

Thanks again. I've bookmarked the links for future reference.

---

### Post by TheFu on 2017-02-08
That's a popular CPU and NICs for routing.  Should be able to find lots of information on tuning.  Not sure I'd pay money for an add-on card; would just depend on the price.  The D525s I've seen didn't have room inside the case for any addons.

My personal opinion is that a router should only do routing things, not anything else.  Want security stuff to be protected by the router, not running ON the router. Others have different opinions, clearly.  Not better or worse, just different from our experiences.
[https://forum.pfsense.org/index.php?topic=42853.0](https://forum.pfsense.org/index.php?topic=42853.0) - different OS, same CPU. Doesn't provide a solution, just a few options for the driver.

---

### Post by m-dw on 2017-02-10
I agree with your opinion - I'm seriously considering getting/building a dedicated router box, but it's low on my priority list. I'll spend some time planning a router build, but there IS room in my case for a full height PCI card - it is a mini-ITX server case with 4 hot-swap disk bays. I was considering using it for a SATA addon card if I ever wanted to expand storage to external disks.

---

### Post by TheFu on 2017-02-10
Just for clarification, the VPN server is yours or is it a service offsite connect to as a client?

**gnutls-cli --benchmark-ciphers** might provide some hints on which ciphers are best to use for your VPN.

BTW, my miniITX case barely holds a single 3.5inch disk and the single PCI slot requires a 90deg riser.  It uses a pico-PSU that places the "brick" outside the case. The D525-based systems I've seen were 50% smaller than mine. No room for anything.

An Atom wouldn't make much of a storage server. I built a $120 NAS + plex + kodi + calibre + VPN + KVM server a few years ago around a new MB + G3258 CPU + old components I had lying around. It has almost 20TB connected now. About 4K passmarks of performance for a $50 CPU (amazing). It is faster than most of my other systems here. Obviously, it has more money in it now - disks, arrays, front USB3 adapters.

---

### Post by 1clue on 2017-02-10
I'm using this one:

[https://www.supermicro.com/products/motherboard/Atom/X10/A1SRM-LN7F-2758.cfm](https://www.supermicro.com/products/motherboard/Atom/X10/A1SRM-LN7F-2758.cfm), 16g RAM (goes to 64g using ECC memory), not sure what's on it for disks right now. It's an 8-core atom specifically set up for router and communications duty.  The board is designed to be a failover for an enterprise server, it has 7 Intel NICs. One is for the control of the board and the other 6 are in pairs, they can be configured to either pass through or loop in another box which would need 2 nics. I have the nics setup as regular nics.

While I can't say I have it set up satisfactorily, it's an 8-core atom designed specifically for communications. It has hardware acceleration for compression and encryption, more than just the AES instructions. My tests show it will encrypt and zip a stream and still saturate a gigabit nic, and more. It actually outruns my i7 in most communications-oriented tests.  Probably a little overkill but if you aim for a 2358 or so it will handle most home or small business applications.

Specs say the board draws 20w, so it's significantly cheaper to run than any core processor.

---

### Post by 1clue on 2017-02-10
Regarding Atom processors:

The earlier ones and pretty much anything made for an end user are pretty slow.  That said Intel has several Atom processors with variants designed for servers, communications or storage. The intent is to make a low-power processor which can handle duties normally delegated to a much larger, power-hungry system.

My c2758 outruns my i7 in many areas, but is still clearly not as strong as the i7 for general computing. Compilation, for example, the i7 is still several times faster than the atom.

---

### Post by TheFu on 2017-02-10
Thought there were some serious quality control issues with Atom C2xxx CPUs?
[https://www.theregister.co.uk/2017/02/06/cisco_intel_decline_to_link_product_warning_to_faulty_chip/](https://www.theregister.co.uk/2017/02/06/cisco_intel_decline_to_link_product_warning_to_faulty_chip/)
> Errata note AVR.54, titled "System May Experience Inability to Boot or May Cease Operation," explains that the Atom C2000 Low Pin Count bus clock outputs (LPC_CLKOUT0 and LPC_CLKOUT1) may stop functioning. Permanently.

---

### Post by 1clue on 2017-02-10
Interesting.  Now that I know about it it'll probably happen to me.  Thanks.

---

### Post by m-dw on 2017-02-11
> **TheFu said:**
> Just for clarification, the VPN server is yours or is it a service offsite connect to as a client?

**gnutls-cli --benchmark-ciphers** might provide some hints on which ciphers are best to use for your VPN.





Actually it's both. It acts as a VPN client, routing traffic from my LAN via a VPN service (silent protest against government snooping), and as an OpenVPN server for my mobile/portable devices via port forwarding over the VPN provider. Client configuration is limited by upstream bandwidth, and TBH isn't heavily used, and I don't have a choice on the encryption the VPN service uses (AES-256-CBC).


My all-purpose server does OK, and I'm not really taxing it much so far.


[LIST]
[*]Dovecot, postfix, fetchmail
[*]logitech media server (a.k.a. squeezebox server)
[*]miniDNLA server
[*]davical (cardDAV/CalDAV) (PostgreSQL)
[*]NFS
[/LIST]

I think my next task is to swap out the HDDs for something quieter (and potentially add some storage capacity at the same time).

---

### Post by TheFu on 2017-02-11
Well, you don't have any control over the bandwidth that the service provider allows. If that is your complaint, forgetaboutit.

Putting storage with files on a router .... not the smartest thing to do, IMHO. Not exactly a secure design, I'm afraid. 

Routers should route. 
Firewalls should firewall. 
VPNs should VPN.  

I could be convinced that a router and firewall go on the same machine. Adding a VPN could be a stretch.  Storage? No way. I don't even leave log files on my router. They are pushed to a more secure device.  I've seen routers with firewalls bypassed all the time using some interesting techniques.  On my desktop, I see unwanted, inbound, connections through the firewall and router that should have been blocked upstream. Coming mostly from ad networks. Basically, they keep the port opened longer than I would have thought from an old web page to trick the firewall into thinking the connection is still "active" when I think it has been closed for hours.  Plus there are many more protocols available beyond TCP and UDP. How many of those do your router really block?

Be careful out there.

---

### Post by 1clue on 2017-02-11
Regarding the c2000 series flaw above:

> An Intel spokesperson in an email to *The Register* characterized  the issue as "a degradation of a circuit element under high use  conditions at a rate higher than Intel&#8217;s quality goals after multiple  years of service."

Which means I'm probably not going to be affected.  The system is capable of many times the speed I actually use. The implications I read from the article and its links are that this only applies to situations where the chip is only marginally able to meet the demands of the task it was chosen for.

---

### Post by m-dw on 2017-02-13
> **TheFu said:**
> Well, you don't have any control over the bandwidth that the service provider allows. If that is your complaint, forgetaboutit.


I've managed approx 180mbit/s through a VPN to the same provider from my I7 equipped desktop. Neither my ISP or my VPN provider is actively or passively throttling my bandwidth, though I recognise that adding a VPN introduces several additional variables that are outside of my control.


> Putting storage with files on a router .... not the smartest thing to do, IMHO. Not exactly a secure design, I'm afraid. 

As always, I value, respect, and in this case agree with your humble opinion. Am currently restricted for space, but am planning a dedicated router build for when my office space is complete.

---

### Post by TheFu on 2017-02-13
Is it possible that 100% if a single core it being used?  Different tools show utilization differently.
Some show a 4 core with 400%.
Others show a 4 core with 100%, so no fully utilized core will ever go above 25%.

Just had to ask. Doubt this is the case here, but ...

---

### Post by 1clue on 2017-02-13
Start your monitor app and then in another terminal:

```
cat /dev/random | gzip >> /dev/null
```

See how your monitor app rates the percentages.

***PS:** My 8-core atom shows 8 cores at or near 100% using top as my monitor.*

---

### Post by TheFu on 2017-02-13
Did **gnutls-cli --benchmark-ciphers** show anything interesting?

---

### Post by m-dw on 2017-02-14
> **TheFu said:**
> Did **gnutls-cli --benchmark-ciphers** show anything interesting?

 ```
Checking cipher-MAC combinations, payload size: 16384        SALSA20-256-SHA1 102.09 MB/sec
        AES-128-CBC-SHA1 25.38 MB/sec
        AES-128-CBC-SHA256 21.68 MB/sec
             AES-128-GCM 23.00 MB/sec
       CHACHA20-POLY1305 104.27 MB/sec


Checking MAC algorithms, payload size: 16384
            SHA1 183.12 MB/sec
          SHA256 81.44 MB/sec
          SHA512 89.22 MB/sec


Checking ciphers, payload size: 16384
                3DES-CBC 6.75 MB/sec
             AES-128-CBC 29.39 MB/sec
             ARCFOUR-128 84.63 MB/sec
             SALSA20-256 0.22 GB/sec

```

Interestingly, my VPN provider uses AES-256-CBC (not shown above), so I'm guessing 45 Mbits/s isn't that bad?

> **TheFu said:**
> Is it possible that 100% if a single core it being used?  Different tools show utilization differently.
Some show a 4 core with 400%.
Others show a 4 core with 100%, so no fully utilized core will ever go above 25%.

Just had to ask. Doubt this is the case here, but ...

When running the above, one core was showing 100% utilisation. I either use gkrellmd with krells for the individual cores displaying on my desktop, or htop and results correlate in both tools.

---

### Post by 1clue on 2017-02-14
> **m-dw said:**
> ```
Checking cipher-MAC combinations, payload size: 16384        SALSA20-256-SHA1 102.09 MB/sec
        AES-128-CBC-SHA1 25.38 MB/sec
        AES-128-CBC-SHA256 21.68 MB/sec
             AES-128-GCM 23.00 MB/sec
       CHACHA20-POLY1305 104.27 MB/sec


Checking MAC algorithms, payload size: 16384
            SHA1 183.12 MB/sec
          SHA256 81.44 MB/sec
          SHA512 89.22 MB/sec


Checking ciphers, payload size: 16384
                3DES-CBC 6.75 MB/sec
             AES-128-CBC 29.39 MB/sec
             ARCFOUR-128 84.63 MB/sec
             SALSA20-256 0.22 GB/sec

```

Interestingly, my VPN provider uses AES-256-CBC (not shown above), so I'm guessing 45 Mbits/s isn't that bad?



When running the above, one core was showing 100% utilisation. I either use gkrellmd with krells for the individual cores displaying on my desktop, or htop and results correlate in both tools.

Your AES-256-CBC should, if I understand correctly, be about half of what AES-128-CBC is. And the speeds listed are megabytes/sec, not megabits/sec. Your aes-128-cbc speed is 235.12 mbps. So I think 45mbps sucks for your system.

---

### Post by m-dw on 2017-02-14
> **1clue said:**
> Your AES-256-CBC should, if I understand correctly, be about half of what AES-128-CBC is. And the speeds listed are megabytes/sec, not megabits/sec. Your aes-128-cbc speed is 235.12 mbps. So I think 45mbps sucks for your system.



OK, that's encouraging.

My 45 Mbit/s is with the CPU core doing the encryption/decryption for that specific tunnel running at 45% utilisation. This suggests I could get to 100Mbit/s at 100% utilisation. Do you think the processor is being throttled, or that there is a bottleneck somewhere between the processor and the NIC?

---

### Post by 1clue on 2017-02-14
Can you clarify the units you're using?

[LIST=1]
[*]mbps=megabits per second. 
[*]MB/s=megabytes per second. 
[*]1MB/s=8mbps 
[/LIST]

Thoughts:
[LIST=1]
[*]You're using Intel NICs.
[LIST=1]
[*]Good. 
[*]Intel NICs handle more of the network tasks than off-brand NICs. 
[*]Off-brand cards can handle the full gigabit speeds, but the CPU sees more interrupts, causing the entire system to slow down measurably. 
[/LIST]
  
[*]Your values seem to be per core.
[LIST=1]
[*]You would need two separate network streams to get multiple cores going. 
[*]You could do this by opening two speedtest windows simultaneously, or maybe two big downloads. 
[*]That would be informative if you could open N streams, one per core. 
[/LIST]
  
[*]It would be helpful if you could get upstream information:
[LIST=1]
[*]speedtest using some box directly attached to your cable modem. 
[*]Some other smart router device which can monitor what's going on on your upstream side. 
[/LIST]
  
[*]System info:
[LIST=1]
[*]How full are your disks?  Percent. 
[*]What type of disks do you have? 
[*]What type of logging do you use? 
[*]What else is going on on this box? 
[*]How are your NICs attached? PCI slots? USB? Built-in? 
[*]Do you run a gui on this box? 
[*]What other hardware is attached? 
[/LIST]
  
[/LIST]

My c2758-based box I mentioned above does extremely better than this on your tls benchmarks. Not bragging, your cpu is not designed to facilitate routing/vpn service but I'm not sure I believe the difference would be accounted for in the hardware. I would like to know what's going on here.

---

### Post by m-dw on 2017-02-15
The NICs are built in to the motherboard. The "router" is also my server but is pretty under-utilised. It is not running a GUI.

It has 5 SATA hard disks. 4 are in a raid10 software array (mdadm). The boot/system disk is also SATA attached. there is 4GBit/s RAM. The only other attached hardware is a USB3 hard disk used for backups.

Mbit/s means Megabits per second.

The speed tests were carried out from a gigabit ethernet attached workstation running UbuntuStudio 16.10, which is capable of copying a file from the server at wire-speed. Interestingly I managed to get 60Mbit/s from an Ubuntu 16.10 VM on a laptop connected wirelessly. The server/router's CPU utilisation while doing so was not appreciably more than while transferring at 45Mbit/s on the workstation. The AP is connected to the same switch as the workstation, but with 100Mbit/s uplink. so the logical and physical topology is essentially the same.

I have large frames enabled on the workstation, switch and server so I need to drop that back to default and test again (fragmentation may be playing a part). I've also noticed that throughput does depend somewhat on the actual VPN end-point I connect to, so tests are not always meaningful.

To illustrate that point I have just managed 92Mbit/s (11MBytes/s) through the VPN with a combination of bittorrent (UbuntuStudio DVD) from the server and a big download from a workstation. The CPU virtual core running openvpn reached 80% utilisation at peak download speed. I think I'll cope.

---

