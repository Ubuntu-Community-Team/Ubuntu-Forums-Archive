---
title: "Ubuntu 14.04 - Assigning static IPs to user and bandwidth monitoring"
date: 2015-03-06
forum: Server Platforms
---

### Post by Trueill on 2015-03-06
Hello,

I have a ubuntu server with 14.04 installed on it. I have 3 users and 4 static IP. I'd like to assign 1 IP to each user in a manner that whatever they use (wget, vpn, rtorrent) they connect via their assigned IP itself on the other end i.e websites see their assigned IP. This way if 1 of my user's IP gets blacklisted on 1 site, other users aren't affected with it. 

Also, my host allocated the IP in series (1.3x.2x.22 , 1.3x.2x.23 etc) and I'd like to control how my users connect via SSH. I only want them to connect via their IP AND user details. for example - while connecting to SSH (or rtorrent) I don't want user 1 to connect to user 2's IP and use his (user 1) credentials. 

And, I'd like to monitor the traffic (in and out) via that IP (hence monitoring the traffic of each user irrespective of their process)

Can I do the above mentioned with ubuntu ? I've read about alias but I'm not sure if it can help me.

---

### Post by nerdtron on 2015-03-06
> Also, my host allocated the IP in series (1.3x.2x.22 , 1.3x.2x.23 etc)  and I'd like to control how my users connect via SSH. I only want them  to connect via their IP AND user details. for example - while connecting  to SSH (or rtorrent) I don't want user 1 to connect to user 2's IP and  use his (user 1) credentials.


You can do this via ufw, but since you want to restrict ssh, you need to declare their source IP so that you won't allow to user to ssh to the wrong IP.

```
 sudo ufw allow from user1.ip.address to server.ip.address port 22
```
add more rules for the other users and then activate UFW using "sudo ufw enable"

FWIW, why not get a dedicated router for this setup? it would be a lot easier for monitoring/limiting bandwidth on ports of a router. If you want something cheap but very customizeable (i mean not a usual plug and play router but a real router that you can assign each port and IP address), you can look at mikrotik routerboard routers.

---

### Post by The Cog on 2015-03-06
The only way I can think of to force users to use a particular IP address is to use virtual machines, and have each user log into a different VM. Each VM would have one IP address allocated. In Linux, you can configure "containers" which are lightweight VMs that all share some of the underlying OS, but are distinct enough to have their own IP addresses.

iptables can police whch IP addresses can connect to which other IP addresses, but if you are using containers to separate the users then this probably is not needed. There is no way you can prevent one user trying to use someone else's login credentials though.

There are lots of ways to monitor traffic - you need to be more specific. Having each user on a separate VM should make that easier too.

---

### Post by Trueill on 2015-03-06
> **The Cog said:**
> The only way I can think of to force users to use a particular IP address is to use virtual machines, and have each user log into a different VM. Each VM would have one IP address allocated. In Linux, you can configure "containers" which are lightweight VMs that all share some of the underlying OS, but are distinct enough to have their own IP addresses.

iptables can police whch IP addresses can connect to which other IP addresses, but if you are using containers to separate the users then this probably is not needed. There is no way you can prevent one user trying to use someone else's login credentials though.

There are lots of ways to monitor traffic - you need to be more specific. Having each user on a separate VM should make that easier too.

Which virtualization technology should I be going for ? I know of 3 - OpenVZ , KVM , Xen. I read about them all and I'm tilting towards KVM. I will be using ubuntu 14.04 on host AND on VPS. I'm quite comfortable with ubuntu for a newbie.

**My main tasks**


[LIST]
[*]Create 4 VPS node and give it to 4 users
[*]Each VPS should be restricted to use 6 GB RAM. I don't want anything to burst or anything. I want to dedicate 6 GB RAM to them. It doesn't matter if they use it or not.
[*]Each VPS must have their own static IP and they should not share each other user's IP. In this manner, if 1 user manages to get banned on some site, other users won't be affected. i.e any process by 1 user originating from his VPS should use his own static IP.
[*]Each VPS should be on individual 2TB HDD (I have 4 X 2TB HDD on the server). I don't want RAID.
[*]Limiting the bandwidth used by the users to 10TB per user.
[/LIST]

---

### Post by volkswagner on 2015-03-06
I suggest KVM.

You may also consider if you will be offering public ip directly to VPS, or using NAT from host.
If you use NAT from host, you will have a single firewall (iptables) on host that can forward/direct/masquerade/etc. 
public ip's and ports.

I suggest use NAT. This will allow you to open only the ports you wish, and have a central place to administer firewall rules.

---

### Post by gordintoronto on 2015-03-07
Is the server assigning IP addresses, or a router? Normally it's a router.

---

### Post by Trueill on 2015-03-11
I installed KVM with SolusVM on a 2 TB HDD per VPS and the remaining free space I was left with was 44% (less then 1024 GB ) . This is unacceptable as I need the space (minimum 1.5TB per disk or per VM/container) . The complete setup, taking that much space is common ? 

I've been looking into containers as The Cog mentioned and was wondering, how secure are they ? Considering they share the same kernel . Ubuntu documentation briefly mentions that its easy to handle Applications within the containers than complete OS.

Can I accomplish my task using containers ? Assign IP to them, place those containers on separate HDD, calculate traffic for each container, and retain minimum 1.5TB space on a 2TB HDD.

> **gordintoronto said:**
> Is the server assigning IP addresses, or a router? Normally it's a router.

I've explained the system I'd like to put in. I think in my case, server will be assigning the IP thats provided to me by my DC.

---

### Post by The Cog on 2015-03-11
> **Trueill said:**
> I installed KVM with SolusVM on a 2 TB HDD per VPS and the remaining free space I was left with was 44% (less then 1024 GB ) . This is unacceptable as I need the space (minimum 1.5TB per disk or per VM/container) . The complete setup, taking that much space is common ? 
Ooh! I've never heard of SolusVM but that must be the culprit - a normal Ubuntu install only needs maybe 6G although obviously you need a lot more space for VM images. Maybe Solus came with example disk images or somethign like that?
> 
I've been looking into containers as The Cog mentioned and was wondering, how secure are they ? Considering they share the same kernel . Ubuntu documentation briefly mentions that its easy to handle Applications within the containers than complete OS.

Can I accomplish my task using containers ? Assign IP to them, place those containers on separate HDD, calculate traffic for each container, and retain minimum 1.5TB space on a 2TB HDD.

Containers should be as secure as full VMs. They're just lighter weight. You should be able to use disk images of around 10G for each guest provided they don't need lots of data, which leaves plenty of space. I don't know which VM manager to use though. I've not looked at anything other than VirtualBox and I'm not sure if that is suitable for your use case.

I was going to suggest Proxmox VE [https://www.proxmox.com/proxmox-ve](https://www.proxmox.com/proxmox-ve) but it is a full OS dedicated to running VMs, perhaps that's not what you're after either.

> 
I've explained the system I'd like to put in. I think in my case, server will be assigning the IP thats provided to me by my DC.
I expect that you would want to bridge the guest OS to the network so that they appear as separate machines. Each would have its own MAC address and IP address, either statically configured or assigned by a DHCP server.

---

### Post by TheFu on 2015-03-11
> **gordintoronto said:**
> Is the server assigning IP addresses, or a router? Normally it's a router.

Not in business server networks, IME. Only in home desktop LANs do the routers assign IPs. Inside a business, the DHCP server for the desktop LAN(s) will assign IPs and that is only if some are actually static. Usually in a business, desktops get dynamic IPs for almost all users ... unless it is a highly-nerdy company.

---

### Post by TheFu on 2015-03-11
> **The Cog said:**
> Containers should be as secure as full VMs. They're just lighter weight. You should be able to use disk images of around 10G for each guest provided they don't need lots of data, which leaves plenty of space. I don't know which VM manager to use though. I've not looked at anything other than VirtualBox and I'm not sure if that is suitable for your use case..

Containers (docker/lxc/etc) have been proven to NOT be as secure as regular virtualized hardware VMs like KVM. In another 3 yrs, assuming no more security issues are uncovered, then we can start making claims about container security.  At this point, I would only use containers inside a corporate LAN and not for any internet facing services.  Web searches of security issues for docker or lxc will quickly show there are still major security flaws.

While I think it is possible to use iptables to restrict bandwidth per-user, I've never seen it deployed for every process that a user runs. I have seen it deployed for 1 specific process - like bt.

With a KVM virtual machine assigned to each user, you can definitely provide separation of file systems, hardware, and bandwidth.  However, if you care about network security and don't want 1 KVM user seeing all the traffic from the others, you'll also need to assign either a different physical network port to each or create a specific bridge for each VM.  Search for bridging security issues to see why - and this applies to every VM technology there is - not just KVM, but Xen, VirtualBox, LXC, Docker ... openVZ .... all of them that use bridges.

**virt-manager** can be run from any Linux desktop. It will connect to the libvirt system running on hypervisors and you don't need root or remote X/Windows on the hostOS/hypervisor. Definitely zero need for any commercial software.  Linux isn't Windows. We don't need to pay to have the best software on our systems. virt-manager is pretty awesome.

---

### Post by volkswagner on 2015-03-11
May I ask why are you using SolusVM? With only 3 or 4 VM's, management should not be too much for you as an admin.
I would offer the three other users barebones VM's (hand them an ip, username, pwd, and ssh port). You as the admin should
be able to manage the VM's with virsh and or virt-manager. You don't need a GUI installed on the server to do X forwarding
to a client running X. This allows you to run the GUI virt-manager on a client pc via 'ssh -X user@hypervisor'.

I have to say, reading the licensing for SolusVM was a bit confusing. I'm still not sure, but the way I interpret.. the
host will need master lice at $10/mo and each KVM VM will need slave licenses at $2.50/mo. Does that seem correct?

Anyway, I'm sure the SolusVM allocated disk space inside the install for VM images (according to docs it's /home/solusvm/kvm). 

What was your partition scheme like prior to installing SolusVM? What's it like now?

```
sudo df -h
sudo du -h / --max-depth=1

```

As you must already know, if you want four VM's and only have four hard drives, one VM will need to share
disk space with the host OS drive (you won't be able to dedicate an individual drive to four VM's).

According to SolusVM docs the following are the only supported operating systems:
CentOS 5/6
RHEL 5/6
Scientific Linux 5/6

What is your host operating system?

---

### Post by gordintoronto on 2015-03-11
> **TheFu said:**
> [GC]Is the server assigning IP addresses, or a router? Normally it's a router.[end]

Not in business server networks, IME. Only in home desktop LANs do the routers assign IPs. Inside a business, the DHCP server for the desktop LAN(s) will assign IPs and that is only if some are actually static. Usually in a business, desktops get dynamic IPs for almost all users ... unless it is a highly-nerdy company.

My company uses pfSense as its "router." All the desktops get static IP addresses (based on MAC address) so I can log on to them in the evening to apply updates, install software, etc. They each have unique terminal server ports.

I'm not sure how nerdy an accounting company can be. In the past 12 months, we've upgraded from XP to 8.1 pro, moved locations, and opened the first branch office. It's been one challenge after another for IT support.

In the near future, Server 2012 R2 might become the DHCP server, we're still looking at this. Suggestions?

---

### Post by Trueill on 2015-03-12
> **volkswagner said:**
> May I ask why are you using SolusVM? 

I thought it would make my life easier.

> **volkswagner said:**
> I have to say, reading the licensing for SolusVM was a bit confusing. I'm still not sure, but the way I interpret.. the
host will need master lice at $10/mo and each KVM VM will need slave licenses at $2.50/mo. Does that seem correct?

There is master license and slave (host) license. 

**Ideal situation** -

Idealistically, you must put your master on a separate dedicated server (or VPS from other provider) and attach your host to that master as a slave. In this manner, since your master won't have any virtualization under it and it is just connected to nodes (slave/host) it will be called "Master without virtualization" or "Slave only license" and you will be charged $2.5/month. 

Now, you need to buy slave license which come in 3 flavors 

Slaves = Unlimited Virtual Servers ( $10 per slave per month)
Mini Slaves = 5 Virtual Servers Maximum ( $5 per slave per month)
Micro Slaves = 2 Virtual Servers Maximum ( $2.5 per slave per month)

So in my case, since I have less than 5 virtual servers on 1 slave, I will pay $2.5/month (since I've put master on another VPS of mine) + $5/month (mini slaves -I have 4 VPS) == $7.5 /month

[B]What people do

[/B]Since they don't want to spend money on dedicated server and just host a master on it, they put VPS's under it. Then you will need a master license named "Master License" and they will charge you $10/month for master plus the amount for slave as I've explained above.

> **volkswagner said:**
> 

What was your partition scheme like prior to installing SolusVM? What's it like now?

```
sudo df -h
sudo du -h / --max-depth=1

```



```
df -hFilesystem      Size  Used Avail Use% Mounted on
/dev/sda2        79G  3.3G   72G   5% /
tmpfs           7.8G     0  7.8G   0% /dev/shm
/dev/sda1       485M   66M  394M  15% /boot
/dev/sda5       2.0G  3.5M  1.9G   1% /tmp



```

```
 du -h / --max-depth=14.0K    /media
16K     /lost+found
0       /misc
0       /net
27M     /lib64
4.0K    /srv
4.0K    /cgroup
4.0K    /mnt
196K    /dev
7.9M    /bin
0       /selinux
438M    /home
56M     /boot
48K     /scripts
du: cannot access `/proc/11682/task/11682/fd/4': No such file or directory
du: cannot access `/proc/11682/task/11682/fdinfo/4': No such file or directory
du: cannot access `/proc/11682/fd/4': No such file or directory
du: cannot access `/proc/11682/fdinfo/4': No such file or directory
0       /proc
0       /sys
8.0K    /opt
19M     /sbin
140M    /vz
92K     /root
524K    /tmp
269M    /lib
1.6G    /usr
41M     /etc
556M    /var
3.2G    /



```

Although, my sdb1 isn't showing here as i've created a volume group with it and my VM is stored in that.

```
 vgs  VG   #PV #LV #SN Attr   VSize VFree
  vgb    1   1   0 wz--n- 1.82t 2.00g



```

It is showing 2g free but its little less than 1 tb free in real. I made a VPS for 1.82tb and it blocked the completed HDD

> **volkswagner said:**
> According to SolusVM docs the following are the only supported operating systems:
CentOS 5/6
RHEL 5/6
Scientific Linux 5/6

What is your host operating system?

My host OS is CentOS 6 but my VPS OS is 14.04 ubuntu

---

