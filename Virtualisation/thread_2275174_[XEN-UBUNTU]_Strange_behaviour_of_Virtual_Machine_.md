---
title: "[XEN-UBUNTU] Strange behaviour of Virtual Machine bridged network"
date: 2015-04-24
forum: Virtualisation
---

### Post by fabioversity on 2015-04-24
[COLOR=#000000][FONT=Arial]Hello!

**--- System Compositiotn ---**
I am running two Virtual Machines over the XEN hypervisor both with Ubuntu Utopic 14.10:
[LIST]
[*]VM A has an armhf optimized lightweight version of the OS. 
[*]VM B has the Linaro-Developer version.[ http://releases.linaro.org/15.01/ubuntu/utopic-images/developer/]("http://releases.linaro.org/15.01/ubuntu/utopic-images/developer/linaro-utopic-developer-20150115-694.tar.gz") 
[*]The Dom0 has the same configuration of VM B. 
[/LIST]

**--- Problem Description ---**
All the machines are connected via a bridged network (*xenbr0*), held by Dom0. The network seems to work properly, and everything works for Dom0. But when I try to run an *apt-get update* or a *wget //something//* on one of the VMs, they fail and get stuck. This is what I got from BOTH the VM:

[LIST]
[*]*apt-get update* problem: 
[/LIST]
[/FONT][/COLOR]```
 root@DomU-Ubuntu2:/etc/apt# apt-get update
 Ign http://it.archive.ubuntu.com utopic InRelease                              
 Ign http://archive.canonical.com utopic InRelease                              
 Ign http://extras.ubuntu.com utopic InRelease                                  
 Ign http://ports.ubuntu.com utopic InRelease                                   
 Ign http://it.archive.ubuntu.com utopic-security InRelease                     
 Ign http://repo.linaro.org utopic InRelease                                    
 Ign http://it.archive.ubuntu.com utopic-updates InRelease                      
 Ign http://extras.ubuntu.com utopic Release.gpg                                
 Ign http://ppa.launchpad.net utopic InRelease                                  
 Ign http://archive.canonical.com utopic Release.gpg                            
 Ign http://ports.ubuntu.com utopic Release.gpg                                 
 Ign http://it.archive.ubuntu.com utopic-proposed InRelease                     
 Ign http://repo.linaro.org utopic Release.gpg                                  
 Ign http://it.archive.ubuntu.com utopic-backports InRelease                    
 Ign http://extras.ubuntu.com utopic Release                                    
 Ign http://archive.canonical.com utopic Release                                
 Ign http://ports.ubuntu.com utopic Release                                     
 Err http://it.archive.ubuntu.com utopic Release.gpg                            
   Connection failed [IP: 193.206.139.45 80]
 Ign http://repo.linaro.org utopic Release                                      
 Err http://it.archive.ubuntu.com utopic-security Release.gpg                   
   Connection failed [IP: 193.206.139.45 80]
 Ign http://ppa.launchpad.net utopic InRelease                                  
 Err http://ppa.launchpad.net utopic Release.gpg                                
   Connection failed
 Err http://it.archive.ubuntu.com utopic-updates Release.gpg                    
   Connection failed [IP: 193.206.139.45 80]
 Err http://it.archive.ubuntu.com utopic-proposed Release.gpg                   
   Connection failed [IP: 193.206.139.45 80]
 Err http://it.archive.ubuntu.com utopic-backports Release.gpg                  
   Connection failed [IP: 193.206.139.45 80]
 Ign http://it.archive.ubuntu.com utopic Release                                
 Err http://ppa.launchpad.net utopic Release.gpg                                
   Connection failed
 Ign http://it.archive.ubuntu.com utopic-security Release                       
 24% [Waiting for headers] [Waiting for headers] [Waiting for headers]
  
 ##And than it stucks##
  
```

[LIST]
[*]*wget* problem: 
[/LIST]
  ```

  root@DomU-Ubuntu2:/etc/apt# wget -d http://upload.wikimedia.org/wikipedia/commons/f/f2/Peach_flowers.jpg
 DEBUG output created by Wget 1.15 on linux-gnueabihf.
  
 URI encoding = &#8216;UTF-8&#8217;
 --2015-04-24 15:43:05--  http://upload.wikimedia.org/wikipedia/commons/f/f2/Peach_flowers.jpg
 Resolving upload.wikimedia.org (upload.wikimedia.org)... 91.198.174.208, 2620:0:862:ed1a::2:b
 Caching upload.wikimedia.org => 91.198.174.208 2620:0:862:ed1a::2:b
 Connecting to upload.wikimedia.org (upload.wikimedia.org)|91.198.174.208|:80... connected.
 Created socket 3.
 Releasing 0x00065c60 (new refcount 1).
  
 ---request begin---
 GET /wikipedia/commons/f/f2/Peach_flowers.jpg HTTP/1.1
 User-Agent: Wget/1.15 (linux-gnueabihf)
 Accept: */*
 Host: upload.wikimedia.org
 Connection: Keep-Alive
  
 ---request end---
 HTTP request sent, awaiting response... No data received.
 Closed fd 3
 Retrying.
  
 --2015-04-24 15:43:11--  (try: 2)  http://upload.wikimedia.org/wikipedia/commons/f/f2/Peach_flowers.jpg
 Found upload.wikimedia.org in host_name_addresses_map (0x65c60)
 Connecting to upload.wikimedia.org (upload.wikimedia.org)|91.198.174.208|:80... connected.
 Created socket 3.
 Releasing 0x00065c60 (new refcount 1).
  
 ---request begin---
 GET /wikipedia/commons/f/f2/Peach_flowers.jpg HTTP/1.1
 User-Agent: Wget/1.15 (linux-gnueabihf)
 Accept: */*
 Host: upload.wikimedia.org
 Connection: Keep-Alive
  
 ---request end---
 HTTP request sent, awaiting response... No data received.
 Closed fd 3
 Retrying.
  
 --2015-04-24 15:43:18--  (try: 3)  http://upload.wikimedia.org/wikipedia/commons/f/f2/Peach_flowers.jpg
 Found upload.wikimedia.org in host_name_addresses_map (0x65c60)
 Connecting to upload.wikimedia.org (upload.wikimedia.org)|91.198.174.208|:80... connected.
 Created socket 3.
 Releasing 0x00065c60 (new refcount 1).
  
 ---request begin---
 GET /wikipedia/commons/f/f2/Peach_flowers.jpg HTTP/1.1
 User-Agent: Wget/1.15 (linux-gnueabihf)
 Accept: */*
 Host: upload.wikimedia.org
 Connection: Keep-Alive
  
 ---request end---
 HTTP request sent, awaiting response... No data received.
 Closed fd 3
 Retrying.
  
 ###and so on###

```[COLOR=#000000][FONT=Arial]

[B]--- Troubleshooting ---
[/B]First of all I checked the connectivity on all the machines and the network configuration they have to ensure the correct set up of the bridged network.


[LIST]
[*]Dom0 etc/network/interfaces 
[/LIST]
[/FONT][/COLOR]```

# interfaces(5) file used by ifup(8) and ifdown(8)
 # Include files from /etc/network/interfaces.d:
 source-directory /etc/network/interfaces.d

  
 # The loopback network interface
 auto lo
 iface lo inet loopback
  
 auto eth0
 iface eth0 inet manual
  
 # Bridge setup
 auto xenbr0
 iface xenbr0 inet dhcp
   bridge_ports eth0
   bridge_stp off       # disable Spanning Tree Protocol
   bridge_waitport 0    # no delay before a port becomes available
   bridge_fd 0          # no forwarding delay
  
```

[LIST]
[*][COLOR=#000000][FONT=Arial]Dom0 network checking:[/FONT][/COLOR] 
[/LIST]
  ```
 
root@Dom0:/etc/network# brctl show
bridge name    bridge id        STP enabled    interfaces
xenbr0        8000.02c10802a11f    no        eth0
                            vif1.0
                            vif2.0
root@Dom0:/etc/network# ifconfig
 eth0      Link encap:Ethernet  HWaddr 02:c1:08:02:a1:1f  

           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
           RX packets:219867 errors:0 dropped:0 overruns:0 frame:0
           TX packets:89744 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:1000 
           RX bytes:246038371 (246.0 MB)  TX bytes:6227772 (6.2 MB)
           Interrupt:45 
  
 lo        Link encap:Local Loopback  
           inet addr:127.0.0.1  Mask:255.0.0.0
           UP LOOPBACK RUNNING  MTU:65536  Metric:1
           RX packets:384 errors:0 dropped:0 overruns:0 frame:0
           TX packets:384 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:0 
           RX bytes:29728 (29.7 KB)  TX bytes:29728 (29.7 KB)
  
 vif1.0    Link encap:Ethernet  HWaddr fe:ff:ff:ff:ff:ff  
           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
           RX packets:209 errors:0 dropped:0 overruns:0 frame:0
           TX packets:20175 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:32 
           RX bytes:17126 (17.1 KB)  TX bytes:2047409 (2.0 MB)
  
 vif2.0    Link encap:Ethernet  HWaddr fe:ff:ff:ff:ff:ff  
           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
           RX packets:1392 errors:0 dropped:0 overruns:0 frame:0
           TX packets:21130 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:32 
           RX bytes:120540 (120.5 KB)  TX bytes:2155659 (2.1 MB)
  
 xenbr0    Link encap:Ethernet  HWaddr 02:c1:08:02:a1:1f  
           inet addr:192.168.0.48  Bcast:192.168.0.255  Mask:255.255.255.0
           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
           RX packets:209463 errors:0 dropped:1 overruns:0 frame:0
           TX packets:88185 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:0 
           RX bytes:239548208 (239.5 MB)  TX bytes:6071360 (6.0 MB)[COLOR=#000000][FONT=Arial]
[/FONT][/COLOR]
```[COLOR=#000000][FONT=Arial]
  Everything seems OK as the bridge exists ad two virtual interfaces are connected to it. On the VMs side I have:


[LIST]
[*]VMs [COLOR=#000000][FONT=Arial]etc/network/interfaces[/FONT][/COLOR] 
[/LIST]
```

# interfaces(5) file used by ifup(8) and ifdown(8)
# Include files from /etc/network/interfaces.d:
source-directory /etc/network/interfaces.d

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

```
[LIST]
[*]VMs network checking: 
[/LIST]
```

root@DomU-Ubuntu2:/etc/network# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:3e:50:29:c4  
          inet addr:192.168.0.36  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:24555 errors:0 dropped:2 overruns:0 frame:0
          TX packets:1392 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2257768 (2.2 MB)  TX bytes:140028 (140.0 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:13 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1232 (1.2 KB)  TX bytes:1232 (1.2 KB)

```
Obviously they differ for MAC and IP address. Anyway, as the network seemed to be up correctly, I tried to ping all the devices in my home LAN from the VMs and Dom0 and everything went good. I than tried to ping the internet (google.com) from the VMs and Dom0 and everything was OK. As the network seemed to work properly I first went to look at the apt sources of the VMs and they only contained:
```

deb http://ports.ubuntu.com/ubuntu-ports/ utopic main universe
deb-src http://ports.ubuntu.com/ubuntu-ports/ utopic main universe

```
Which are the repos for these kind of distros I am using. Anyway, to try things out I added some of the official repos to the list, by using: [http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)


[LIST]
[*]VMs etc/apt/sources.list 
[/LIST]
[/FONT][/COLOR]```

#------------------------------------------------------------------------------#
 #                            DEFAULT UBUNTU REPOS                              #
 #------------------------------------------------------------------------------#
 deb http://ports.ubuntu.com/ubuntu-ports/ utopic main universe
 deb-src http://ports.ubuntu.com/ubuntu-ports/ utopic main universe
  
  #------------------------------------------------------------------------------#
 #                            OFFICIAL UBUNTU REPOS                             #
 #------------------------------------------------------------------------------#
 ###### Ubuntu Main Repos
 deb http://it.archive.ubuntu.com/ubuntu/ utopic main restricted universe multiverse

 deb-src http://it.archive.ubuntu.com/ubuntu/ utopic main restricted universe multiverse
  
 ###### Ubuntu Update Repos
 deb http://it.archive.ubuntu.com/ubuntu/ utopic-security main restricted universe multiverse
 deb http://it.archive.ubuntu.com/ubuntu/ utopic-updates main restricted universe multiverse
 deb http://it.archive.ubuntu.com/ubuntu/ utopic-proposed main restricted universe multiverse
 deb http://it.archive.ubuntu.com/ubuntu/ utopic-backports main restricted universe multiverse
 deb-src http://it.archive.ubuntu.com/ubuntu/ utopic-security main restricted universe multiverse
 deb-src http://it.archive.ubuntu.com/ubuntu/ utopic-updates main restricted universe multiverse
 deb-src http://it.archive.ubuntu.com/ubuntu/ utopic-proposed main restricted universe multiverse
 deb-src http://it.archive.ubuntu.com/ubuntu/ utopic-backports main restricted universe multiverse
  
 ###### Ubuntu Partner Repo
 deb http://archive.canonical.com/ubuntu utopic partner
 deb-src http://archive.canonical.com/ubuntu utopic partner
  
 ###### Ubuntu Extras Repo
 deb http://extras.ubuntu.com/ubuntu utopic main
 deb-src http://extras.ubuntu.com/ubuntu utopic main[COLOR=#000000][FONT=Arial]
[/FONT][/COLOR]
```[COLOR=#000000][FONT=Arial]
After I changed the list, nothing changed in the command output, so I tried to ping these servers, trying to figure out if I could establish a connection with them. I than used the ping command on ports.ubuntu.com and on it.archive.ubuntu.com, receiving back responses from both of them. So I changed my target and went to check the DNS servers for the VMs. I found these files empty or with the gateway address, so i changed them into:
[/FONT][/COLOR]

[LIST]
[*][COLOR=#000000][FONT=Arial]VMs etc/resolv.conf
[/FONT][/COLOR] 
[/LIST]
```
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
 #     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
 nameserver 8.8.8.8
 nameserver 8.8.4.4
```
by modifying the */etc/resolvconf/resolv.conf.d/base* file and cleaning up all the others (tail, head and original) which contained nothing anyway. After this last modification, nothing seems to be changed. 

I have not tried any other commands yet, but I suspect that the background problem is related to those I have described above. Now I don't know what I can do more to have things working. Any suggestion would be greatly appreciated!

---

### Post by dangtranngu on 2015-10-30
Hi, I've the same problem when installing dom0 and domU on Banana PI. Do you figure out how to deal with it ? thanks a lot

---

