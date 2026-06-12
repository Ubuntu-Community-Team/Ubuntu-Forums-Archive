---
title: "VMWare server network access"
date: 2007-09-12
forum: Server Platforms
---

### Post by dickohead on 2007-09-12
Hey guys,

I'm not even sure if this is possible, but it seems like it should be!

Can I run an appliance inside VMWare server on an Ubuntu box and then have network users access it as if it were a *real* machine?

I'm sure it has something to do with setting up two IP addresses for one interface and bridging them correctly, but so far I have been shooting in the dark (for 8 hours now! :D).

The appliance  am trying to setup is the Astaro Security Gateway (bloody wonderful looking thing it is!).

Has anyone done this previously?

Cheers,

dickohead.

---

### Post by ruibernardo on 2007-09-12
> **dickohead said:**
> Hey guys,

I'm not even sure if this is possible, but it seems like it should be!

Can I run an appliance inside VMWare server on an Ubuntu box and then have network users access it as if it were a *real* machine?

I'm sure it has something to do with setting up two IP addresses for one interface and bridging them correctly, but so far I have been shooting in the dark (for 8 hours now! :D).

The appliance  am trying to setup is the Astaro Security Gateway (bloody wonderful looking thing it is!).

Has anyone done this previously?

Cheers,

dickohead.

Hi dickohead,

I've recently used wmware to make a vmware-server machine directly accessible from the outside. Previously, I used iptables snat/dnat function to do it with the vmnet8 interface. Although iptables allows you to make a vmware-server machine accessible from the outside with that interface, it is in an indirect way of reaching the vmware machine.

The direct way of making a vmware-server machine accessible from the outside is editing the file ```
/etc/vmware/vmnet8/nat/nat.conf 
```and add a port and destination IP in the [FONT=Fixedsys][incomingtcp][/FONT] section. For example, to make a vmware-server machine installed with a LAMP directly accessible from the outside:

```
[incomingtcp]
80 = 192.168.200.128:80
```Open that port in iptables normally in your internet interface and restart the vmware service:

```
sudo /etc/init.d/vmware-server restart
```Then, the vmware-server machine port 80 will be directly accessible from the outside, on your internet interface on port 80, and also accessible from the vmnet8 interface (all ports, as usual, on the private network).

Don't know for sure if this is what you want, but you can adapt this to other ports and other vmware machines, including several machines running on different ports on your real interface.

NOTE - Warning on the nat.conf file: "[COLOR=Red]*Use these with care - anyone can enter into your VM through these...*[/COLOR]"

---

### Post by twistedtwig on 2007-09-12
I have recently done this with windows 2003 and xp (2003 box had vm server on it, and xp was the vm box).

The 2003 box was INSIDE the network and used a bridged conenction and just got its IP from the dhcp server and was accessable mstsc etc via comp name or IP address.

I did try this a long time ago on my ubuntu box that had a direct IP address to the net and had real issues trying to get it to give it an internal IP address from the dhcp server rather than take the external one.

I ended up removing it from my ubuntu box as it didn't deal with smp (might have had wrong package but as I say it was around a year ago now).

I also had to disable the firewall on the xp box to get it to connect to the other machines (bit annoying that).

---

### Post by ruibernardo on 2007-09-12
[Wishlist] It would be great if VirtualBox had some feature like nat.conf in VMware.:idea:

---

### Post by HermanAB on 2007-09-13
Uhmmm, VMware can do bridging and NAT natively.  You can easily toggle it from the VMware console for each virtual machine.  Some can be NAT and some bridged even. There is no need to jump through any iptables configuration hoops on the host.

Just set the virtual machine to use a bridged network connection, then configure the virtual machine as if it is a standalone machine with any IP address and routes you need.

If it is difficult, then you are doing something wrong!

Cheers,

Herman

---

### Post by netlogic on 2007-09-13
> **dickohead said:**
> Hey guys,

I'm not even sure if this is possible, but it seems like it should be!

Can I run an appliance inside VMWare server on an Ubuntu box and then have network users access it as if it were a *real* machine?

I'm sure it has something to do with setting up two IP addresses for one interface and bridging them correctly, but so far I have been shooting in the dark (for 8 hours now! :D).

The appliance  am trying to setup is the Astaro Security Gateway (bloody wonderful looking thing it is!).

Has anyone done this previously?

Cheers,

dickohead.

Yes, Mr.Dick-0-hEAD.
Actually, it is a prefer way to maintain a desktop compared to Terminal Server method. You don't have to reboot the entire server to install the latest version of IE7 or other applications for a particular client. If you deployed SAN in your network, you can easily put 10 to 20 workstations on the server. Also, moving the users workstation to a different server farm is simple as moving few files. Also, using a thin client (like WYSE terminal) is recommended, so you don't have pay for a dual license. The XP license costs will sit on the server. Also, if your company has enough bandwidth, you can now centralize administration and you have no need for local admins at sites that have less than 50 employees. Look into VMWARE ESX version.

---

### Post by netlogic on 2007-09-13
Oh, I'm so tired...
I am replying to a wrong forum on the last post.  VMWARE supports bridging and nating of the appliances.  There are many things you can do by utilizing the virtual switching, bridging, and NAT features. You can even create a VPN TOR router if you don't feel like running it natively.

---

### Post by dickohead on 2007-09-13
Alright,

I have got the following:

No firewall - REPEAT - NO FIREWALL on the Linux server (I have a router upstream blocking outside access)
VMWare running an Astaro appliance on IP address 192.168.150.5
a vmnet8 interface on my machine set as 192.168.150.1
my servers local IP is 192.168.1.112
Astaro on the server responds to [https://192.168.150.5:4444](https://192.168.150.5:4444)

I then set the VMWare interface eth1 (192.168.150.5) to:  NAT - "Used to share the hosts IP Address"

So my thinking is that on my desktop which is 192.168.1.16, If i type in [https://192.168.1.112:4444](https://192.168.1.112:4444) I should receive the Astaro gateway client on my desktop right?.... bom-bow! No go.

I set
```

[incomingtcp]
4444 = 192.168.150.1:4444

```

I then even tried:

```

[incomingtcp]
4444 = 192.168.150.5:4444

```
Thinking that maybe NAT wanted the number of the virtual machine, not the vmnet8 address.

But still I get nothing!!!

So...

Do I want to have two subnets and then bridge them with NAT forwarding a certain port of the local machine to the Virtual Machine.

OR

Do I want vmware to have it's own IP address within my REAL subnet?

I'm so confused as to how I get in touch with this baby from the outside. It all works BRILLIANTLY when I'm on the local server - not a hitch (except system beeping which i removed - whew!).

I love it when things don't work as I first imagined - perfect chance to learn something new.
:D

---

### Post by ruibernardo on 2007-09-13
> **dickohead said:**
> 
VMWare running an Astaro appliance on IP address 192.168.150.5


This should be the IP you should use on the file nat.conf, on the  [incomingtcp] section.

Don't forget to restart the vmware-server service each time you change the file nat.conf to apply the modifications.

```
sudo /etc/init.d/vmware-server restart
```You also have to open the port 4444 on the host machine.

---

### Post by Brazen on 2007-09-13
Ok, so it sounds like you are using NAT networking on your virtual appliance.  You should have chosen "bridged" networking.  Then assign and ip address to your appliance that is on the local network.  it will literally act just like it is connected directly into a switch on the network.

This is assuming you chose all the default options during the vmware installation and didn't do something like answer "no" when it asked if you want to set up bridged networking.

Now I'm not sure with your pre-built appliance, I've always built my virtual machines from scratch, but maybe the appliance defaulted to nat networking, and you just need to poweroff the virtual appliance, open up Vmware Console, look at the properties for the virtual appliance and change the NIC setting to "bridged".

---

### Post by dickohead on 2007-09-13
Thanks guys,

How do I open up port 4444 on the host machine? The server is connected directly to a switch and there is no firewall (yet) on the host machine, so all ports should be open yes?

Once I get it working, I'll lock it down then open up what I need, but at the moment I just need it talking :)

If I assign a ocal IP address to the Virtual Machine how do other machines on the network find where it is? Will VMWare update some form of entry in my switch that will tell all requests for IP X to go through IP Y?

I also have other services running on the host machine, like Samba, FTP(21), Apache(80) and SSH (22), these will continue to function if I setup a bridge from VMWare to the host... right?

---

### Post by ruibernardo on 2007-09-13
> **dickohead said:**
> 
How do I open up port 4444 on the host machine? The server is connected directly to a switch and there is no firewall (yet) on the host machine, so all ports should be open yes?

If you didn't setup a firewall on the guest, then yes. Maybe it is a problem with the host firewall. Make the vmnet8 network range or that particular IP accessible from the host.

> **dickohead said:**
> 
If I assign a ocal IP address to the Virtual Machine how do other machines on the network find where it is? Will VMWare update some form of entry in my switch that will tell all requests for IP X to go through IP Y?

The IP of the virtual machine is the one in the virtual vmnet8 network inside the host. That virtual network isn't accessible from the outside. You can confirm what is the IP with "ifconfig" command on the virtual machine.

> **dickohead said:**
> 
I also have other services running on the host machine, like Samba, FTP(21), Apache(80) and SSH (22), these will continue to function if I setup a bridge from VMWare to the host... right?

Yes, only the port 4444 of the host will be redirected to the IP you choose (on the vmnet8 network), the one you see when you do "ifconfig" on the virtual machine.

I hope this helps.

---

### Post by Brazen on 2007-09-14
> **dickohead said:**
> Thanks guys,

...
If I assign a ocal IP address to the Virtual Machine how do other machines on the network find where it is? Will VMWare update some form of entry in my switch that will tell all requests for IP X to go through IP Y?
It does it the same way a regular bridge or switch handles it - through ARP requests.  If you really want the technical detail, look up "Address Resolution Protocol" in wikipedia.

> I also have other services running on the host machine, like Samba, FTP(21), Apache(80) and SSH (22), these will continue to function if I setup a bridge from VMWare to the host... right?
yeah, they should function normally, though personally I prefer to install a very base system with only the VMWare Server on the host and then create virtual machines for services like Apache, FTP, and Samba.  Of course you will still want SSH on the host so you can administer it, and also I put Webmin on the host.

---

### Post by dickohead on 2007-09-16
Okay - bridging works fine, which is good and bad - good for this Appliance because I like having it on the local subnet, but bad for later because I want to use other appliances with NAT.

Do I need some packages installed for NAT to work correctly? Or is it all handled by VMWare?

Thank you all very much for helping me set this up!!!

Cheers,

dickohead.

---

### Post by GodsMadClown on 2007-10-16
I'm having a similar problem.  I'm running a 7.04 desktop and hosting a VM with 6.06 Server LTS.  I'm running the VM in bridged mode, and I'd like to keep it that way.  The 6.06 machine is set with a static IP (192.168.2.200) and responds to pings at that address from the host's commandline:

```
PING 192.168.2.200 (192.168.2.200) 56(84) bytes of data.
64 bytes from 192.168.2.200: icmp_seq=1 ttl=64 time=0.209 ms
64 bytes from 192.168.2.200: icmp_seq=2 ttl=64 time=0.124 ms
64 bytes from 192.168.2.200: icmp_seq=3 ttl=64 time=0.216 ms
64 bytes from 192.168.2.200: icmp_seq=4 ttl=64 time=0.145 ms
64 bytes from 192.168.2.200: icmp_seq=5 ttl=64 time=0.179 ms

--- 192.168.2.200 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 3999ms
rtt min/avg/max/mdev = 0.124/0.174/0.216/0.038 ms
```

However, I can't ssh into the machine.  I do have openssh-server installed and running, because from the commandline of the VM, I can ssh to localhost.

I've been looking at VMware documentation, but they all seem to indicate that the bridged mode would work as if the VM was connected to my network in the same way that the host was.


Am I misunderstanding something?

p.s.
I'm sorry for resurrecting an old thread, but this seemed to be exactly my problem.

---

### Post by dickohead on 2007-10-16
As for your SSH connection issues I'm not too sure, my SSH is working fine and dandy!

Could it have something to do with firewall settings?

But I did figure out my remote VMware-server console issues - I was using VMware-server in Dapper and it does not install the xinetd packages required for remote connection... woops.

So when I installed these - it worked perfectly!

I've since upgrade my server to 7.04 with the pre-built package for VMware-server and it's working flawlessly! a version of xinetd was installed as a required package.

So everything now works!

Thanks guys!!!

---

### Post by GodsMadClown on 2007-10-17
There is no firewall.  This is an internal network IP.  That is, unless VMWARE player installs some firewall that I'm not aware of.

---

### Post by dickohead on 2007-10-17
There may be a (software) firewall on the Ubuntu Linux machine...?

---

### Post by Brazen on 2007-10-17
> **GodsMadClown said:**
> There is no firewall.  This is an internal network IP.  That is, unless VMWARE player installs some firewall that I'm not aware of.

Can you ssh into the host from a remote workstation?  How about ssh'ing from the host to the vm?

This might be a network configuration issue.  Could you post your ip address, subnet, and gateway for the host, vm, and remote workstation?

---

