---
title: "Working! Virt-Manager Bridged Wireless Network"
date: 2011-05-24
forum: Virtualisation
---

### Post by kleinric on 2011-05-24
Howzit, 

My wifi connection (wlan0) can't be added to a bridge. I read that this is common, but can't seem to find anyone who has the tap stuff working with Virt-manager.

I haven't completely solved the problem but I think I'm pretty close... I have managed to get a guest ubuntu, working perfectly on the network through my host (ubuntu) wireless card - bridged. Even DHCP works - with one catch.

I'm certainly no expert, these steps are a mixture of:
[LIST=1]
[*][http://serverfault.com/questions/197156/set-tap0-using-virt-manager-for-bridged-wireless](http://serverfault.com/questions/197156/set-tap0-using-virt-manager-for-bridged-wireless)
[*][http://savvyadmin.com/virtualbox-wireless-bridging-with-dhcp/](http://savvyadmin.com/virtualbox-wireless-bridging-with-dhcp/)
[*]Banging my head against a wall
[/LIST]

Install KVM/Virt-manager etc...

Install the networking tools:
```
sudo apt-get install uml-utilities parprouted bcrelay
```

Create a bridge:
```
sudo brctl addbr b0
```

Create the tap:
```
sudo tunctl -t tap0
```

Add tap0 to the bridge:
```
sudo brctl addif br0 tap0
```


Give the bridge an address. This address MUST be on a different subnet to your network - in fact I've found the address doesn't have to be close - my network at home is 10.0.0.0 and the code below still works for me:

```
sudo ip addr add 192.168.1.100/32 dev br0
sudo ip link set br0 up

```

Use parprouted to perform voodoo magic on the routing tables. If you drop the "-d" then it will run in the background.
```
sudo parprouted -d wlan0 br0
```

Finally, start bcrelay - this will make sure that broadcast traffic (like the dhcp stuff) gets pushed through the tap as well.
```
sudo bcrelay -i br0 -o wlan0
```

Then open virt manager, select your virtual machine, go to the details page. Click "Add Hardware" and go to "Network". Then set Host Device to "Specify Shared Device Name" and type in "br0" where it asks for the bridge name.

Starting the VM I find that it gets an address from the network DHCP (not the virt-manager one) without any problems. 

For some reason, parprouted doesn't find this address so no other traffic makes it back to the VM. If you manually add the line to the routing table (defeating the object of the dhcp :/ ) then parprouted finds it and you end up with two lines in the routing table. If you remove the one, the other stays and it keeps working... 
eg. If the VM was assigned 10.0.0.100 then:
```
sudo route add -host 10.0.0.100 dev br0
```

As with the line in the routing table, I find that networking works absolutely perfectly through virt-manager. 

**Question:**
If anyone knows how to get parprouted to find that new address by itself, wireless bridging would be pretty much solved in virt-manager. :) Any ideas?

Richard

---

### Post by BoredOutOfMyMind on 2011-06-02
You have compiled a great guide- What am I doing wrong in step #2 on 10.10?

> ursa-major:~$ sudo brctl addbr b0
sudo: brctl: command not found


---

### Post by BoomSie on 2011-06-06
> **BoredOutOfMyMind said:**
> You have compiled a great guide- What am I doing wrong in step #2 on 10.10?

My best guess is that you miss bridge-utils. I have it here on my system but I can't figure out which package provides this ( /usr/sbin/brctl . Synaptic provides doesn't list it, however, I'm pretty sure it came through bridge-utils or 1 of its sub dependencies )

---

### Post by BoomSie on 2011-06-08
I post a separate response after 24 hours to draw attention to this topic again.

Nice start post you made there, I only encounter 1 strange thing with bcrelay.

When I use the provided natty repository, it crashes while preventing a stack/buffer overflow. When I try to use an older version of bcrelay (bcrelay_1.2.3-1ubuntu0.2_amd64.deb) my system freezes sooner or later (so again, an overflow of some kind)

I was wondering, what architecture you use and which version of bcrelay?

I only get it working without bcrelay (and thus configuring everything manually)

---

### Post by Nattereri on 2011-10-01
In case someone else stumbles on this post like I did, the way I got my wireless card birdged was by using just 4 commands.
 
parprouted, bcrelay and two sysctl commands.
 
I put them in the /etc/network/interfaces file like so:
 
auto br1
iface br1 inet static
pre-up brctl addbr br1 setfd 0 stp off
address xxx.xxx.x.xxx
netmask xxx.xxx.xxx.x
post-up parprouted wlan0 br1
post-up bcrelay -d -i wlan0 -o br1
post-up sysctl net.ipv4.conf.wlan0.proxy_arp=1
post-up sysctl net.ipv4.conf.br1.proxy_arp=1
 
The sysctl commands enable computers on the wireless network to ping virtual guest for some reason I haven't had time to discover yet. They also have to be run after procps because of a boot sequence problem.

---

### Post by bodhi.zazen on 2011-10-03
This is how I bridge my wireless card:

[http://blog.bodhizazen.net/linux/bridge-wireless-cards/](http://blog.bodhizazen.net/linux/bridge-wireless-cards/)

---

### Post by majikins on 2012-01-09
> **kleinric said:**
> Howzit, 

My wifi connection (wlan0) can't be added to a bridge. I read that this is common, but can't seem to find anyone who has the tap stuff working with Virt-manager.

I haven't completely solved the problem but I think I'm pretty close... I have managed to get a guest ubuntu, working perfectly on the network through my host (ubuntu) wireless card - bridged. Even DHCP works - with one catch.

I'm certainly no expert, these steps are a mixture of:
[LIST=1]
[*][http://serverfault.com/questions/197156/set-tap0-using-virt-manager-for-bridged-wireless](http://serverfault.com/questions/197156/set-tap0-using-virt-manager-for-bridged-wireless)
[*][http://savvyadmin.com/virtualbox-wireless-bridging-with-dhcp/](http://savvyadmin.com/virtualbox-wireless-bridging-with-dhcp/)
[*]Banging my head against a wall
[/LIST]

Install KVM/Virt-manager etc...

Install the networking tools:
```
sudo apt-get install uml-utilities parprouted bcrelay
```

Create a bridge:
```
sudo brctl addbr b0
```

Create the tap:
```
sudo tunctl -t tap0
```

Add tap0 to the bridge:
```
sudo brctl addif br0 tap0
```


Give the bridge an address. This address MUST be on a different subnet to your network - in fact I've found the address doesn't have to be close - my network at home is 10.0.0.0 and the code below still works for me:

```
sudo ip addr add 192.168.1.100/32 dev br0
sudo ip link set br0 up

```

Use parprouted to perform voodoo magic on the routing tables. If you drop the "-d" then it will run in the background.
```
sudo parprouted -d wlan0 br0
```

Finally, start bcrelay - this will make sure that broadcast traffic (like the dhcp stuff) gets pushed through the tap as well.
```
sudo bcrelay -i br0 -o wlan0
```

Then open virt manager, select your virtual machine, go to the details page. Click "Add Hardware" and go to "Network". Then set Host Device to "Specify Shared Device Name" and type in "br0" where it asks for the bridge name.

Starting the VM I find that it gets an address from the network DHCP (not the virt-manager one) without any problems. 

For some reason, parprouted doesn't find this address so no other traffic makes it back to the VM. If you manually add the line to the routing table (defeating the object of the dhcp :/ ) then parprouted finds it and you end up with two lines in the routing table. If you remove the one, the other stays and it keeps working... 
eg. If the VM was assigned 10.0.0.100 then:
```
sudo route add -host 10.0.0.100 dev br0
```

As with the line in the routing table, I find that networking works absolutely perfectly through virt-manager. 

**Question:**
If anyone knows how to get parprouted to find that new address by itself, wireless bridging would be pretty much solved in virt-manager. :) Any ideas?

Richard

Thank you this worked for me to get my VM's to see each other for testing.

---

