---
title: "kvm/qemu performance issue with apt"
date: 2018-07-21
forum: Virtualisation
---

### Post by brightdroid on 2018-07-21
Hello,

hope someone can help with this strange problem.
I've really huge network/disc performance issues within my ubuntu 18.04 kvm guest which is running on my ubuntu 16.04 kvm host.

The problem is network really only visible in apt which has download-rates of ~70 KB/s!
When I download a large file like Ubuntu Server within the guest the download-speed is 8-10 MByte/s!

The hypervisor (ubuntu server 16.04):
[LIST]
[*][COLOR=#000000]Intel i7-4770K CPU[/COLOR]
[*]32 GByte RAM
[/LIST]

xml disc config of VM:
```
[FONT=monospace][COLOR=#000000]<disk type='file' device='disk'>[/COLOR]
      <driver name='qemu' type='raw' cache='writethrough' io='threads'/>
      <source file='/var/lib/libvirt/images/client.raw'/>
      <backingStore/>
      <target dev='vda' bus='virtio'/>
      <alias name='virtio-disk0'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x07' function='0x0'/>
</disk>[/FONT]
```

iperf3 test between kvm hypervisor and guest:
```
[FONT=monospace][COLOR=#000000][ ID] Interval           Transfer     Bandwidth       Retr  Cwnd[/COLOR]
[  4]   0.00-1.00   sec  3.91 GBytes  33.6 Gbits/sec    0   3.02 MBytes        
[  4]   1.00-2.00   sec  3.24 GBytes  27.9 Gbits/sec    0   3.02 MBytes        
[  4]   2.00-3.00   sec  3.41 GBytes  29.3 Gbits/sec    0   3.02 MBytes        
[  4]   3.00-4.00   sec  3.73 GBytes  32.0 Gbits/sec    0   3.02 MBytes        
[  4]   4.00-5.00   sec  4.38 GBytes  37.6 Gbits/sec    0   3.02 MBytes        
[  4]   5.00-6.00   sec  3.88 GBytes  33.3 Gbits/sec    0   3.02 MBytes        
[  4]   6.00-7.00   sec  3.86 GBytes  33.2 Gbits/sec    0   3.02 MBytes        
[  4]   7.00-8.00   sec  3.59 GBytes  30.8 Gbits/sec    0   3.02 MBytes        
[  4]   8.00-9.00   sec  3.48 GBytes  29.9 Gbits/sec    0   3.02 MBytes        
[  4]   9.00-10.00  sec  3.43 GBytes  29.5 Gbits/sec    0   3.02 MBytes        
- - - - - - - - - - - - - - - - - - - - - - - - -
[ ID] Interval           Transfer     Bandwidth       Retr
[  4]   0.00-10.00  sec  36.9 GBytes  31.7 Gbits/sec    0             sender
[  4]   0.00-10.00  sec  36.9 GBytes  31.7 Gbits/sec                  receiver
[/FONT]
```

iperf3 test between other host on network and VM:
```
[FONT=monospace][ ID] Interval           Transfer     Bandwidth       Retr  Cwnd
[  4]   0.00-1.00   sec   112 MBytes   941 Mbits/sec    0   2.95 MBytes        
[  4]   1.00-2.00   sec   110 MBytes   924 Mbits/sec    0   2.95 MBytes        
[  4]   2.00-3.00   sec   107 MBytes   896 Mbits/sec    0   2.95 MBytes        
[  4]   3.00-4.00   sec   110 MBytes   920 Mbits/sec    0   3.10 MBytes        
[  4]   4.00-5.00   sec   109 MBytes   914 Mbits/sec    0   3.10 MBytes        
[  4]   5.00-6.00   sec   108 MBytes   910 Mbits/sec    0   3.10 MBytes        
[  4]   6.00-7.00   sec   111 MBytes   934 Mbits/sec    0   3.10 MBytes        
[  4]   7.00-8.00   sec   110 MBytes   923 Mbits/sec    0   3.10 MBytes        
[  4]   8.00-9.00   sec   109 MBytes   914 Mbits/sec    0   3.10 MBytes        
[  4]   9.00-10.00  sec   110 MBytes   927 Mbits/sec    0   3.10 MBytes        
- - - - - - - - - - - - - - - - - - - - - - - - -
[ ID] Interval           Transfer     Bandwidth       Retr
[  4]   0.00-10.00  sec  1.07 GBytes   920 Mbits/sec    0             sender
[  4]   0.00-10.00  sec  1.07 GBytes   920 Mbits/sec                  receiver
[/FONT]
```

Thanks in advance :)

---

### Post by TheFu on 2018-07-22
Ooops. 

Seems you are complaining that foreign servers aren't fast enough for you?
Expecting similar throughput over a WAN connection doesn't make sense.  If you only have dialup WAN connectivity, expecting the performance of a fibre network WAN connection doesn't make sense.

You can manually download the packages.  When you do that, what is the transfer rate?  Just trying to determine if this is a WAN issue or an APT issue.

IMHO, 10Mbps is a HUGE amount for any foreign server to provide, especially if they aren't pushing hidef video streams.

---

### Post by brightdroid on 2018-07-23
Sure, but as you can see in the attachments the host (apt_host.png) has about 10 MB/s and the kvm guest only 70 KB/s, which does not make sense.

I think it's not an network issue, cause of the good iperf3 results.

Thanks

---

### Post by TheFu on 2018-07-23
> **brightdroid said:**
> Sure, but as you can see in the attachments the host (apt_host.png) has about 10 MB/s and the kvm guest only 70 KB/s, which does not make sense.

I think it's not an network issue, cause of the good iperf3 results.

Thanks

It isn't a network issue INSIDE your network. You and I cannot control what happens on internet servers.
We can troubleshoot by using different programs to pull the data we want which might prove that 1 program has an issue if it is slower than others. Try getting the data using wget, curl, browser, and apt.   Make a table.  If only 1 program is much  slower than the others, look for options that may cause that.  

BTW, I cannot read those attachments. Text it too small for my old eyes. Text, not images,  lets me control the size and saves bandwidth.

---

### Post by brightdroid on 2018-07-23
Sure, but as I already wrote I get "full" (internet-) bandwidth on my kvm-_host_ with the same apt-repo servers, while getting only around 70 KBit/s in my guest.
And this reproducible... so it's not an issue with my network or the repo-server bandwidth.

It's only affecting "apt" not wget as you can see:

**apt on kvm guest:**
```
$ apt-get download linux-image-4.15.0-29-generic
Get:1 http://archive.ubuntu.com/ubuntu bionic-updates/main amd64 linux-image-4.15.0-29-generic amd64 4.15.0-29.31 [7879 kB]
Fetched 7879 kB in 1min 50s (71.8 kB/s)
```

[B]apt on kvm host (shortly after this)

[/B]```
$ apt-get download linux-image-4.4.0-130-generic
Get:1 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 linux-image-4.4.0-130-generic amd64 4.4.0-130.156 [22.1 MB]
Fetched 22.1 MB in 2s (9591 kB/s)
```

---

### Post by TheFu on 2018-07-23
Sorry, I got mixed up between multiple threads and my own issues.

How is the bridge configured?  Mine is in the interfaces file, since I had performance issues using the automatic bridges that libvirt provides.
Also, which driver is used by the guest VM? All of mine use virtio.

I had an issue with 1 VM over the weekend. It couldn't ping any public internet IPs. None.  All the other VMs on the same host didn't show the same issue.   After about 18 hrs, it fixed itself without any help from me.

What I did to troubleshoot was 
* check firewalls for blocking
* check firewalls for QoS
* check all routing
* Did the same on the host machine
* Did the same on the local router
* Did the same on the WAN router
* Ran iperf3 tests between VMs and physical servers.
* Looked through the logs
* Looked through the change management data for each system.
* Compared the network settings from a working VM on the same host with the VM having issues.
I did uncover an issue here, but only scheduled time to fix it next weekend during a maintenance window.

As a workaround, have you considered running a local APT caching system? Effectively is is both a cache and a proxy, so packages are locally stored on the LAN whenever requested by any client. My systems are snowflakes, all different, so only about 60% of the packages are shared and the cache does help with it.

---

### Post by brightdroid on 2018-07-24
Found the issue in "/etc/apt/apt.conf.d/50unattended-upgrades":
```
Acquire::http::Dl-Limit "70";
```

So problem fixed after removing the line / adding a comment.

---

### Post by TheFu on 2018-07-24
> **brightdroid said:**
> Found the issue in "/etc/apt/apt.conf.d/50unattended-upgrades":
```
Acquire::http::Dl-Limit "70";
```

So problem fixed after removing the line / adding a comment.

Good find.
Checked all the systems here.  The limit is commented out by default on all of them, so it appears that the default was changed on the machine. 

To help the community, please mark the thread as "SOLVED" -- Thread Tools near the top of the page.

---

