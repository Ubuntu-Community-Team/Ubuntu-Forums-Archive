---
title: "Created network bridge in KVM and now I have no internet if my VM isnt running?"
date: 2018-07-24
forum: Virtualisation
---

### Post by relink2013 on 2018-07-24
Ok guys im not sure what went wrong here, but I'll start at the beginning. 


  I created a Windows 10 VM through Virtual Machine Manager, I needed  the Win10 VM on my main network, so I created a bridge in VMM through  (edit > connection details > network interfaces).
  Everything was working great...until I rebooted my computer 2 weeks  later. I had forgotten all about the bridge and it took me 2 days to  figure out why I suddenly had no network connections at all, not even an  adapter was listed in settings. 
  
So now here is what I have to do every time I reboot my computer. I  have to open VMM and enable the bridge (br1) manually, despite the fact  that it is set to "Start Mode: onboot", and then even more hilarious, I  have to start my Win10 VM, if the VM isnt running, then Ubuntu has no  network connectivity at all. Once i manually bring up the bridge, and  manually start the VM, and once Windows has fully booted, my network connection works perfectly fine until  the next time I reboot. 

  
I am running Ubuntu 18.04

---

### Post by TheFu on 2018-07-25
Ah ... just saw that you are using 18.04.  None of this applies, since they decided to switch to netplan.  You'll need to figure that out.  Sorry.

But for 16.04 and earlier, this will work:

I've been using KVM + virt-manager for 8+ yrs, but have never used the built-in bridges.  I always setup a manual bridge for each VM on the hostOS first.  All those years ago, this was required to avoid really poor performance.  I've never changed.  Sometimes, for play VMs, I'll use the built-in NAT interface.

With a hostOS bridge, the host also uses it unless you have multiple physical NICs.

For example, on the hostOS
```
$ ifconfig 
br0       Link encap:Ethernet  HWaddr 80:ee:73:yy:xx:b6  
          inet addr:172.22.22.6  Bcast:172.22.22.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:74130438 errors:0 dropped:0 overruns:0 frame:0
          TX packets:43693399 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:267586003268 (267.5 GB)  TX bytes:169028542669 (169.0 GB)
```

And some of the /etc/network/interfaces:```

# ####################################
auto eth0
iface eth0 inet manual

auto br0
iface br0 inet static
  address 172.22.22.6
  gateway 172.22.22.1
  netmask 255.255.255.0
  dns-nameservers 1.1.1.1 208.67.220.220  
  bridge_ports eth0
  bridge_fd 9
  bridge_hello 2
  bridge_maxage 12
  bridge_stp off
```

Then inside virt-manager, the VMs use br0.  They can get DHCP IPs from the network DHCP server or have static IPs following the normal static IP rules for all networks.

There's a manpage which describes the different options: **man bridge-utils-interfaces**
If you choose to go this direction, be certain to disable the bridge you setup inside libvirt.

---

### Post by relink2013 on 2018-07-29
Crap, I got hopeful when I saw a reply. ](*,)

---

### Post by TheFu on 2018-07-29
> **relink2013 said:**
> Crap, I got hopeful when I saw a reply. ](*,)

[https://ubuntuforums.org/showthread.php?t=2378252](https://ubuntuforums.org/showthread.php?t=2378252) is about 17.10 and kvm+netplan.  Seems they were on a desktop and used nm-something.  I purge networkmanager-everything from all my systems because it used to get confused over non-trivial configs.

It is possible to remove netplan and go back the ifupdown methods. There are how-tos for that.  I can't believe that netplan doesn't have a solution to create bridges. I just won't believe that.  
Google found this: [https://askubuntu.com/questions/971126/17-10-netplan-config-with-bridge](https://askubuntu.com/questions/971126/17-10-netplan-config-with-bridge) which worked for some and failed for others.

netplan.io is the official documentation. Last time I looked, didn't see a concise bridge example.  [https://blog.ubuntu.com/2017/12/01/ubuntu-bionic-netplan](https://blog.ubuntu.com/2017/12/01/ubuntu-bionic-netplan) doesn't have a bridge example that is complete enough for my needs.

[https://www.linuxtechi.com/install-configure-kvm-ubuntu-18-04-server/](https://www.linuxtechi.com/install-configure-kvm-ubuntu-18-04-server/) appears to have a useful, complete, example.  I haven't tried it.  18.04 is too new for me, but I am pretty good with google (better than 90% of the world).

---

### Post by Doug S on 2018-07-30
The [Ubuntu Server guide]("https://help.ubuntu.com/lts/serverguide/network-configuration.html.en-CA#bridging") was updated for netplan and re-published just recently. It contains a bridging example. See also [here]("https://bugs.launchpad.net/serverguide/+bug/1769007").

---

