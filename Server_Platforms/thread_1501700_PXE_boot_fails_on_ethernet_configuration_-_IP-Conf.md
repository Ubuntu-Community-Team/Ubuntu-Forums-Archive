---
title: "PXE boot fails on ethernet configuration - IP-Config"
date: 2010-06-04
forum: Server Platforms
---

### Post by yotamhc on 2010-06-04
Hi,

I am trying to setup a PXE diskless boot server (posted before but managed to solve previous problems).
Now I got stuck with a problem for hours and cannot find a solution - although it seems like a stupid mistake somewhere.

The problem is that I receive the following error message after loading kernel and initrd:
```

IP-Config: eth0 hardware address 00:0c:29:79:86:c1 mtu 1500 DHCP
[    2.775718] eth0: link up
IP-Config: no response after 60 secs - giving up
/init: .: line 3: can't open /tmp/net-eth0.conf
[   69.073555] Kernel panic- not syncing" Attempted to kill init!
[   69.073859] Pid: 1, comm: init Not tainted 2.6.32-22-generic #35-Ubuntu
< call trace - if it can help I can grab a screenshot >

```

I have consulted some guy in another forum and he says that the OS tries to get an IP address from DHCP. It should not do that as it already got IP from DHCP at the initial PXE DHCP step (I see the correct assigned IP on screen) and also I configured its /etc/network/interfaces to:
```

auto lo
iface lo inet loopback

iface eth0 inet manual

```

The nice guy said that he doesn't know whether the IP-Config stuff is something done by kernel to try and lease an address or it is something special for the ubuntu release.

Does any of you know what is it and what it means? I'm desperate already...

Thanks!
Yotam

---

### Post by yotamhc on 2010-06-04
Hi,

Maybe someone here knows why on diskless machine with PXE boot, after loading kernel and initrd and before NFS is loaded I get this message:
```

IP-Config: eth0 hardware address 00:0c:29:79:86:c1 mtu 1500 DHCP
[    2.775718] eth0: link up
IP-Config: no response after 60 secs - giving up
/init: .: line 3: can't open /tmp/net-eth0.conf
[   69.073555] Kernel panic- not syncing" Attempted to kill init!
[   69.073859] Pid: 1, comm: init Not tainted 2.6.32-22-generic #35-Ubuntu

```

Is it an ubuntu-specific issue? What is this IP-Config?
Does anyone understand the error message?

Thanks,
Yotam

---

### Post by Iowan on 2010-06-04
Threads merged.

---

### Post by yotamhc on 2010-06-04
I've got a tiny progress: found that the system requests DHCP again after initial PXE DHCP step - just before loading NFS. Problem is that the DHCP server, for some reason, does not answer these later requests.
Requests have the same MAC address but their length is different: the initial (answered) requests are of length 548 and the latter (unanswered) are only 271.

Any idea why my DHCP server does not like these requests?

Here is my dhcpd.conf file:
```

allow booting;
allow bootp;

subnet 192.168.1.0 netmask 255.255.255.0 {
  range 192.168.1.2 192.168.1.99;
  option broadcast-address 192.168.1.255;
  option routers 192.168.1.1;
  option domain-name-servers 192.168.1.1;

  filename "/pxelinux.0";
  next-server 192.168.1.115;
}

host pxe_client {
  hardware ethernet 00:0C:29:79:86:C1;
  fixed-address 192.168.2.3;
}

```

Thanks

---

### Post by uOpt on 2010-06-04
It expects to have the root filesystem mounted. This might be a general misconfiguration on your part, or somebody at Ubuntu broken diskless boot, people rarely test it when fiddling with /etc/rc

What is the rest of your boot config, the kernel parameters?

---

### Post by yotamhc on 2010-06-05
Here is the PXE default configuration file:
```

LABEL linux
KERNEL vmlinuz-2.6.32-22-generic
APPEND root=/dev/nfs initrd=initrd.img-2.6.32-22-generic nfsroot=192.168.1.115:/nfsroot ip=dhcp rw

```(also tried without the "ip=' part, 'ip=none' and 'ip=on' to cover all options)

Edited:
When I changed the last line to:
```

APPEND root=/dev/nfs initrd=initrd.img-2.6.32-22-generic nfsroot=192.168.1.115:/nfsroot ip=192.168.1.3:192.168.1.115:192.168.1.1:255.255.255.0:::none rw

```it worked just fine and loaded X with no problem. However, this means a separate configuration file for each machine, which I would like to avoid.

Here is how the server is seeing the DHCP requests and its response to the first request:

First request (during initial boot stage):
```

03:32:00.255217 IP (tos 0x0, ttl 20, id 1, offset 0, flags [none], proto UDP (17), length 576)
    0.0.0.0.bootpc > 255.255.255.255.bootps: BOOTP/DHCP, Request from 00:0c:29:79:86:c1 (oui Unknown), length 548, xid 0x2a7986c1, secs 4, Flags [Broadcast] (0x8000)
      Client-Ethernet-Address 00:0c:29:79:86:c1 (oui Unknown) [|bootp]
03:32:00.317616 IP (tos 0x10, ttl 128, id 0, offset 0, flags [none], proto UDP (17), length 328)
    yotam-server.local.bootps > 255.255.255.255.bootpc: BOOTP/DHCP, Reply, length 300, xid 0x2a7986c1, secs 4, Flags [Broadcast] (0x8000)
      Your-IP 192.168.1.3
      Server-IP yotam-server.local
      Client-Ethernet-Address 00:0c:29:79:86:c1 (oui Unknown) [|bootp]

```Second request (after running nfs-top script) - server does not answer this one and it fails the boot:
```

03:32:19.957269 IP (tos 0x0, ttl 64, id 0, offset 0, flags [DF], proto UDP (17), length 299)
    0.0.0.0.bootpc > 255.255.255.255.bootps: [no cksum] BOOTP/DHCP, Request from 00:0c:29:79:86:c1 (oui Unknown), length 271, xid 0xb4b70b15, secs 1, Flags [none] (0x0000)
      Client-Ethernet-Address 00:0c:29:79:86:c1 (oui Unknown) [|bootp]

```Any idea what can I do to overcome this?

Thanks!

---

### Post by uOpt on 2010-06-05
I would debug this by isolating whether it's a server or a client problem.

Do you have a disk in that client so that you can try a plain "dhclient" (no diskless boot)?

---

### Post by yotamhc on 2010-06-05
As the clients are VMs on my laptop, I started another VM running the exact same image (the one on which I created the image) and it is able to retrieve DHCP info from server using dhclient.

---

### Post by uOpt on 2010-06-05
Same MAC address, right?

To me it looks like the DHCP server doesn't like to answer a non-BOOTP request shortly after a BOOTP request.

Next step I would run a different dhcpd in a chroot.

---

### Post by yotamhc on 2010-06-05
Yes, same MAC
Isn't the second request (as I pasted from tcpdump above) a BOOTP request?
(It has this [|bootp] there...)

What do you mean by "run a different dhcpd in a chroot"?

Thanks!

---

### Post by uOpt on 2010-06-05
Hmm, yeah. The difference isn't bootp, it's flags and lifetime.

What I means is to isolate whether dhcpd or the client-side scripts are screwed up here, I would install a different Linux into a chroot (debian-stable or so) and start a dhcpd there.

---

### Post by yotamhc on 2010-06-05
OK, I'll try doing that soon and post the results.

I thought it might has something with the missing checksum in the unanswered requests but I have no idea on how to change it...

Thanks a lot for your help!

---

### Post by peetaur on 2012-01-12
> **uOpt said:**
> Same MAC address, right?

To me it looks like the DHCP server doesn't like to answer a non-BOOTP request shortly after a BOOTP request.

Next step I would run a different dhcpd in a chroot.


I had the same problem. And thank you; your comment above lead me to the answer.

I was missing:
```
allow booting;
allow bootp;
```
in dhcp.conf

---

### Post by peetaur on 2012-01-13
Actually, my change there only makes it work about 10% of the time (strange).

yotamhc's suggestion of statically assigning the IP works fine though. And this is acceptable, having 2 central config locations for N hosts (still better than normal static ips in local disks).


This suggestion (adding network device to modules; in my case "e1000") also does not work:
[https://help.ubuntu.com/community/DisklessUbuntuHowto](https://help.ubuntu.com/community/DisklessUbuntuHowto)
> 
**Gotchas**

 
[LIST]
[*]This does not work for  a PXE server running 10.04.1 LTS, nor does it work for clients trying  to run 10.04.1 LTS. The client receives an offer from DHCP, gets the  kernel, and fails while trying to load. [IMG]https://help.ubuntu.com/moin_static192/ubuntunew/img/idea.png[/IMG] **NOTE**:  It WILL work if you add required module names in  /etc/initramfs-tools/modules (module names for your network adapters,  like forcedeth or tulip) 
[/LIST]


---

### Post by alepac on 2013-04-18
I'm having the same issue. I assume that my issue is caused by the switch that is filtering the rarp request from the kernel. I noticed that my pc ethernet change from 100/Mb during PXE to 1/Gb during the kernel request. I have no issue connecting the pc directly on the serveror using other pc, with different ethernet device, and the same OS.

---

### Post by wildmanne39 on 2013-04-19
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

