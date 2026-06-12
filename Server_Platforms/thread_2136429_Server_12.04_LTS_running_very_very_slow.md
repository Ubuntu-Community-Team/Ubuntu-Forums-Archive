---
title: "Server 12.04 LTS running very very slow"
date: 2013-04-17
forum: Server Platforms
---

### Post by AmbiguousOutlier on 2013-04-17
Hello, my new server is running incredibly slow, for instance, when running a xbmc client accessing the lots of files, takes hours rather than seconds from my NAS, accessing a single large file is relatively quick. 

To load my media library takes a few minutes rather than displaying it instantaneously. 

Also I'm trying to set up mythtv backend using this command

```
ssh -X username@192.168.1.103 /usr/bin/mythtv-setup
```

on my laptop, this is painfully slow, it takes about a minute to recognise each key press.

Yet despite all of this my CPU load is next to nothing and idle time is over 99%

All I've done is, install Ubuntu Server as a samba file server, then setup all my samba drives,  copied NAS data to samba, then installed mythtv backend and finally installed OpenSSH. I've also changed my ip for the server from DHCP to static.

What things can I do to test where my bottle neck is?

Cheers, 

Things I thought might be interesting;

Linux Tomato 3.5.0-23-generic #35~precise1-Ubuntu SMP Fri Jan 25 17:13:26 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

CPU: AMD Athlon Dual Core 4850e 

top - 19:48:38 up  2:32,  3 users,  load average: 0.08, 0.05, 0.05
Tasks: 132 total,   1 running, 131 sleeping,   0 stopped,   0 zombie
Cpu(s):  0.5%us,  0.3%sy,  0.0%ni, 99.2%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   3531436k total,  1202380k used,  2329056k free,   110040k buffers
Swap:  3665916k total,        0k used,  3665916k free,   639676k cached

I'm also using btrfs and xfs if that is relevant

proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/mapper/Tomato-root /               btrfs   defaults,subvol=@ 0       1
# /boot was on /dev/sda1 during installation
UUID=fc68f15c-87a6-4cb8-9b17-a47e750898c2 /boot           ext2    defaults     $
# /fs01 was on /dev/sdb1 during installation
UUID=413368bc-0c08-41b1-a4d3-bd0246604706 /fs01           xfs     defaults     $
/dev/mapper/Tomato-root /home           btrfs   defaults,subvol=@home 0       2
/dev/mapper/Tomato-swap_1 none            swap    sw              0       0

---

### Post by TheFu on 2013-04-17
Seems like networking would be the primary area of concern. Can you describe it for each of the involved machines with network details?
* ifconfig
* route print
* netstat -rn
and how you've setup hostname resolution between the systems would be a big help.

Using btrfs and xfs seems highly advanced. Are you sure that's a good idea for your needs?
The UUID lines in your /etc/fstab appears to have issues - but I'm not an XFS user, so I could easily be wrong.  The '$' character seems misplaced to me.

I don't know anything about MythTV - well, besides that I wasn't able to get it working the 3 times I tried. I do use XBMC over a samba connection, however. It works extremely well in my situation.

---

### Post by AmbiguousOutlier on 2013-04-17
I like to be different and try new things, hence the btrfs, my server is backed up and not really critical as I could just switch over to the backup device. XFS from what I've read is supposed to be a good solution for large media files so this is what I have on my files server drives and the boot drive is btrfs. XBMC works perfectly and fast from my old NAS (now backup), playing a file pauses every 2 mins and buffers for 5 mins.

With regards to my fstab this is how the installer created it, admitedly I did use the manual method and I haven't mounted sda2 yet (I took 10% for boot and then will use the 90% for MythTV work area), I've never really altered this before. This is the output of fdisk, which doesn't look to good to me, but then I'm not sure what it's supposed to look like;

```

Disk /dev/sda: 500.1 GB, 500106780160 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976771055 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00062b30

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      499711      248832   83  Linux
/dev/sda2          501758   976769023   488133633    5  Extended
/dev/sda5          501760   976769023   488133632   8e  Linux LVM

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e2a55

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048  3907028991  1953513472   83  Linux

Disk /dev/mapper/Tomato-root: 46.2 GB, 46225424384 bytes
255 heads, 63 sectors/track, 5619 cylinders, total 90284032 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/Tomato-root doesn't contain a valid partition table

Disk /dev/mapper/Tomato-swap_1: 3753 MB, 3753902080 bytes
255 heads, 63 sectors/track, 456 cylinders, total 7331840 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/Tomato-swap_1 doesn't contain a valid partition table

```


Server - Tomato
ifconfig
```

eth0      Link encap:Ethernet  HWaddr 00:1f:d0:d9:b2:c5  
          inet addr:192.168.1.72  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:d0ff:fed9:b2c5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1433405 errors:0 dropped:5 overruns:0 frame:0
          TX packets:2632866 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:141017566 (141.0 MB)  TX bytes:3745883498 (3.7 GB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:159162 errors:0 dropped:0 overruns:0 frame:0
          TX packets:159162 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2320207482 (2.3 GB)  TX bytes:2320207482 (2.3 GB)

```

netstat -rn
```

Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG        0 0          0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0

```

Laptop - Orange
ifconfig
```

eth0      Link encap:Ethernet  HWaddr 00:1e:ec:39:6f:09  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:46 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4015 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4015 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:534620 (534.6 KB)  TX bytes:534620 (534.6 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1b:9e:f2:76:0e  
          inet addr:192.168.1.120  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:9eff:fef2:760e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2205666 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1207931 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3068981995 (3.0 GB)  TX bytes:159322111 (159.3 MB)

```

netstat -rn
```

Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG        0 0          0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 wlan0

```

XBMC - Mango
ifconfig
```

eth0      Link encap:Ethernet  HWaddr 90:2b:34:de:00:7d  
          inet addr:192.168.1.147  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::922b:34ff:fede:7d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1208204 errors:0 dropped:0 overruns:0 frame:0
          TX packets:705266 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1737534492 (1.7 GB)  TX bytes:56504871 (56.5 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:80 errors:0 dropped:0 overruns:0 frame:0
          TX packets:80 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4822 (4.8 KB)  TX bytes:4822 (4.8 KB)

```

netstat -rn
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG        0 0          0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0

```

I'm not sure what you mean by hostname resolution, clients are as is, DHCP I pressume, server has been given a static IP and referenced though a name. ie rhys@tomato. (I like my fruit) And also not sure what route print means.

Thanks for your help.

---

### Post by TheFu on 2013-04-18
Thanks for the information.  When things take a long time to eventually work, there is ususally a networking issue. You'd be amazed at the crazy network setups I've seen.
The good news is that your setup seems just fine.  All the machines are on the same subnet and the routes are fine. I don't think the delay has anything to do with your networking.  When networking isn't correct, there are 30 sec to 5 min timeouts. If multiple calls need to timeout, that would often require some multiplier of the 30 sec timeout.  Based on your initial description, that is what I figured you were experiencing.  Seems I was wrong.

*hostname resolution* is how 1 machine knows about another machine without using IP addresses.  DNS or editing the /etc/hosts file on each machine is the normal way to address this on a LAN.  Home routers often support DHCP reservations and let us enter hostnames to complete that mapping. Here's [http://blog.jdpfu.com/2011/07/18/use-your-router-to-centralize-your-network-device-management](http://blog.jdpfu.com/2011/07/18/use-your-router-to-centralize-your-network-device-management) an article about that.  Knowing which IP address my portable devices has at home, but still letting them use normal DHCP out in the world is nice. Great for troubleshooting too.

If you wonder what any command does, you should always check the man page to understand it.

fdisk is deprecated and can be dangerous with the newer GPT and 4K sector HDDs.  **parted** or** gparted** should be used going forward. Any of the older fdisk, sfdisk, cfdisk style commands are deprecated and should be avoided.  Of course, if your HDD uses MBR and has 512b sectors, then there really isn't any risk, but it would be a good time to get used to using parted now, before you forget at 3am some morning after a failure.

I'm a little lost as to why you are using X/windows forwarding with the ssh connection, but it shouldn't harm anything.

At this point, I'm at a loss for the root cause of the issue.   My samba server is fast - I routinely retrieve and push data to it at 650Mbps (plenty of disk cache available).  Of course, I don't use wifi on my network. Wifi performance is extremely localized and changes from second to second. Humans don't really have much control over wifi bandwidth. I learned this doing 1200 deployments for my day job. Streaming hidef media over wifi might be possible in a cabin in the woods away from the rest of the world, but even in my suburban home, there is just too much interference from all the different neighbors and some of the really stupid choices that seem to be made by installers or through the random channel selections - netgear really sucks at this from what I've seen.  In the USA, only (3) 2.4Ghz do not overlap with other channels - 1, 6, 11.  Choosing any other channel causes interference on at least 1 of those and perhaps 2 of them. This means everyone's bandwidth is lessened just by poor channel selection.  With wifi-N, the interference is easier to get around, but still exists, plus there are too many wifi-N standards to really know what your systems can support.  My laptop only supports 75Mbps connections, but it claims to be "wifi-N" certified.  Bunk.  Wired GigE networking just works. You can get the expected throughput and it is completely predictable how fast data will be transferred. No real concerns over interference from a microwave or smart-remote control or children's toy.

 </rant>  

Sorry about that.  I just returned from Nepal where I was trying to make  the wifi better for a monastery with about 30 monks. They have a fibre link with less than 20% the bandwidth that my home has, but still expect that all of them can watch youtube without any stuttering.  Plus the ISP appears to be really stupid - the ISP put their public IP on a /24 network!  254 other end-users are all on the same LAN with each other. It was crazy seeing the traffic from the network neighbors on the ISP.

Sorry - perhaps if you try to simplify the issue to 1 problem at a time and resolve each?  Just a thought.
* ssh performs well?
* cifs share performance is what?
* how fast are the HDDs locally?
* how fast are the HDDs over the network?
* then get into the MythTV stuff.

---

