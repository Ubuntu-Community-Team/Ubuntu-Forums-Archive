---
title: "Unable to install linux-headers-4.4.0-131"
date: 2018-08-09
forum: Virtualisation
---

### Post by rockcreektech on 2018-08-09
I have two virtual machines running 16.04.4 LTS Server. They are hosted on a Nutanix cluster using Acropolis Hyper-visor. Both of them are producing error messages when I attempt to run a "dist-upgrade". I've tried doing: 
```
sudo apt-get clean
```
```
sudu apt-get -f install
```
 ```
sudo rm -rf /var/lib/apt/lists/*
sudo apt-get update
```
I've tried using "--fix-missing" and I've disabled IPv6. Nothing seems to make any difference. Nothing else causes any errors (including just "upgrade"), but when I run "dist-upgrade" I end up with:
```
mylogin@MYSERVER:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
The following NEW packages will be installed:
  linux-headers-4.4.0-131 linux-headers-4.4.0-131-generic
The following packages will be upgraded:
  linux-generic linux-headers-generic linux-image-generic
3 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 10.0 MB/10.9 MB of archives.
After this operation, 78.4 MB of additional disk space will be used.
Do you want to continue? [Y/n] Y
Err:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main i386 linux-headers-4.4.0-131 all 4.4.0-131.157
  Connection failed [IP: 91.189.91.23 80]
Err:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main i386 linux-headers-4.4.0-131 all 4.4.0-131.157
  Connection failed [IP: 91.189.91.23 80]
E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-4.4.0-131_4.4.0-131.157_all](http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-4.4.0-131_4.4.0-131.157_all).
deb  Connection failed [IP: 91.189.91.23 80]

E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```

At first I thought it might be an issue with the Ubuntu archive server, but now it's been going on for two days. I've found in other threads that it's possibly due to something with the vm network interface, but I can't seem to find a solution. Any suggestions would be greatly appreciated.

---

### Post by LHammonds on 2018-08-09
If you ping the domain name, does it resolve to an IP?

Example:
```
# ping us.archive.ubuntu.com -c 3
PING us.archive.ubuntu.com (91.189.91.26) 56(84) bytes of data.
64 bytes from hanger.canonical.com (91.189.91.26): icmp_seq=1 ttl=50 time=53.7 ms
64 bytes from hanger.canonical.com (91.189.91.26): icmp_seq=2 ttl=50 time=53.7 ms
64 bytes from hanger.canonical.com (91.189.91.26): icmp_seq=3 ttl=50 time=53.6 ms

--- us.archive.ubuntu.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 53.657/53.704/53.742/0.035 ms
```

---

### Post by rockcreektech on 2018-08-13
> **LHammonds said:**
> If you ping the domain name, does it resolve to an IP?

Example:
```
# ping us.archive.ubuntu.com -c 3
PING us.archive.ubuntu.com (91.189.91.26) 56(84) bytes of data.
64 bytes from hanger.canonical.com (91.189.91.26): icmp_seq=1 ttl=50 time=53.7 ms
64 bytes from hanger.canonical.com (91.189.91.26): icmp_seq=2 ttl=50 time=53.7 ms
64 bytes from hanger.canonical.com (91.189.91.26): icmp_seq=3 ttl=50 time=53.6 ms

--- us.archive.ubuntu.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 53.657/53.704/53.742/0.035 ms
```

Hi LHammonds,

Thank you for replying. Yes is does resolve. Here's my output:

```

# ping us.archive.ubuntu.com -c 3
PING us.archive.ubuntu.com (91.189.91.26) 56(84) bytes of data.
64 bytes from hanger.canonical.com (91.189.91.26): icmp_seq=1 ttl=49 time=63.1 ms
64 bytes from hanger.canonical.com (91.189.91.26): icmp_seq=2 ttl=49 time=46.1 ms
64 bytes from hanger.canonical.com (91.189.91.26): icmp_seq=3 ttl=49 time=46.3 ms

--- us.archive.ubuntu.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 46.100/51.866/63.159/7.985 ms

```

---

### Post by LHammonds on 2018-08-13
Hmm...you resolve the DNS name to the same IP that I do and can ping it.

Looking back at your dist-upgrade error, it is saying failed to connect to "91.189.91.23" which is a slightly different IP than the DNS name which resolves to "91.189.91.26"

I just ran a ping on .23 and it responded.

I plugged the IP into a browser and it turned into "https://usn.ubuntu.com/"

Try to ping the .23 IP.  If you can ping it and can see it respond in a web browser, I don't know why apt is not able to connect to it.

Do you have any outbound HTTP (port 80) blocks in your software or hardware firewall rules?

**EDIT #1:** I just checked my 16.04 servers and they are running the 4.4.0-131-generic kernel.  All of them run inside VMware on top of ESXi 6.5.0 so the virtualization hardware is a bit different but the paths to get the updates should have been the same.

**EDIT #2**: I wonder if this is somehow messing with you (related to upgrade program): [upgrade bug]("https://lists.ubuntu.com/archives/ubuntu-release/2018-August/004556.html")

LHammonds

---

### Post by rockcreektech on 2018-08-17
Hi LHammonds,

Whatever the issue was, it has resolved itself with the update to 4.4.0.133-generic. Thanks again for taking the time to try to help me figure this out.

---

