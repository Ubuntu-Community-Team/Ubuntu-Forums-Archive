---
title: "Increasing KVM network interface to 1Gbps"
date: 2021-04-29
forum: Virtualisation
---

### Post by cjsmall on 2021-04-29
Xubuntu:            20.04
virt-manager:     1:2.2.1-3ubuntu2.1
virt-viewer:        7.0-2build1
qemu:               1:4.2.3ubuntu6.15

My network was recently upgraded with a 1Gbps router, and in the process of testing various machines for throughput I noticed that my Windows 10 system running under QEMU/KVM on one machine was throttled at 100Mbps.  I looked into this and see that it is using a virtual Realtek **rtl8139** device for the NIC which is set to **Bridge br0: Host device eth1**.  So even though I have 1Gbps physical Ethernet on my network and motherboard, this interface appears to be the bottleneck.  Maybe there is a reason for this configuration, or maybe, out of ignorance, I set it up incorrectly initially.  I'm wondering if there is a way to alter the settings to increase throughput and get closer to 1Gbps?  Should I change this device to **virtio** or **e1000** (or something else) and is this advised?  Does Windows 10 work with these other virtual devices and/or are there a negative system load impact from doing this?  Is there anything else I need to be aware of?  Thanks for any pointer you can offer.

---

### Post by TheFu on 2021-04-29
Don't use Realtek rtl8139. 

Always select the virtio drivers for storage controllers and NICs.  Do this regardless of the physical device. Do it now. Today.

I don't know about Win10, but there were virtio drivers available from Redhat. [https://www.linux-kvm.org/page/WindowsGuestDrivers/Download_Drivers](https://www.linux-kvm.org/page/WindowsGuestDrivers/Download_Drivers)
I always found the automatically created bridge to be slower than a manually created one.  I don't know how to do that with netplan, which is what 20.04 uses. My VM hosts are all 18.04, recently upgraded from 16.04.

And for all your desktop VMs, when you want remote desktop access into them on the LAN (not over the internet), use the SPICE protocol in the VM settings and QXL video drivers inside the VM. Nearly native performance for everything except gaming.

Popular Linux desktop distros all come with virtio NIC, disk controller drivers, and QXL display built-in. Basically, we don't have to do anything inside the linux clients for those to work.
99% of the time, I use ssh into my VMs. Spice is used seldom and over an ssh-tunnel setup using virt-viewer.

For local connections (running on the VMhost connecting to a Guest VM): ```
/usr/bin/virt-viewer -a -d  {vm-name} &
```
For remote connections:```
 /usr/bin/virt-viewer --connect qemu+ssh://{vm-hostname}/system {vm-name} &
```

---

### Post by Tadaen_Sylvermane on 2021-04-30
> [COLOR=#000000]I always found the automatically created bridge to be slower than a manually created one. I don't know how to do that with netplan, which is what 20.04 uses. My VM hosts are all 18.04, recently upgraded from 16.04.[/COLOR]

This is what I use on my desktop which is Ubuntu 20.04 desktop with pci pass through for a windows kvm virtual machine that I do my games on.

```
network:
 version: 2
 renderer: networkd
 ethernets:
  eth0:
   dhcp4: false
   dhcp6: false
 bridges:
  br0:
    interfaces: [eth0]
    dhcp4: false
    dhcp6: false
    addresses: [192.168.1.15/24]
    gateway4: 192.168.1.1
    nameservers:
     addresses: [192.168.1.1]
```

---

### Post by cjsmall on 2021-05-01
I installed the virtio-win-0.1.185.iso image and finally figured out how to update all the drivers*.  The Ethernet is using the virtio device and Properties is now reporting 10Gbps.  When I run a browser speed test, I'm getting around 300Mbps (which is 5-6 times faster than what i was getting before!), vs. another native Windows 10 machine hardwired to my network which gets 900+Mbps which is similar to my Xubuntu machine.  Is this the kind of performance I should expect or do you think there is a problem and throughput should be higher than this?

Thanks for pointing me in the right direction regarding these drivers.  I don't know why I never ran across this issue before.  I didn't even know that upgrading like this was an option!





* It's a shame that this driver installation process cannot be better automated and installed as part of the native VM software.  It's not too difficult once you've been through it and look back, but no single set of instructions matched my configuration, so there was a lot of work to do to figure out what was actually being described.

---

### Post by cjsmall on 2021-05-01
[[COLOR=#000000]Tadaen_Sylvermane[/COLOR]]("https://ubuntuforums.org/member.php?u=1914514"):

Out of curiosity, where is this code located on your system?  On my system there is nothing like it in the XML file for the VM under /etc/libvirt/qemu.

---

### Post by TheFu on 2021-05-01
> **cjsmall said:**
> I installed the virtio-win-0.1.185.iso image and finally figured out how to update all the drivers*.  The Ethernet is using the virtio device and Properties is now reporting 10Gbps.  When I run a browser speed test, I'm getting around 300Mbps (which is 5-6 times faster than what i was getting before!), vs. another native Windows 10 machine hardwired to my network which gets 900+Mbps which is similar to my Xubuntu machine.  Is this the kind of performance I should expect or do you think there is a problem and throughput should be higher than this?

Thanks for pointing me in the right direction regarding these drivers.  I don't know why I never ran across this issue before.  I didn't even know that upgrading like this was an option!

* It's a shame that this driver installation process cannot be better automated and installed as part of the native VM software.  It's not too difficult once you've been through it and look back, but no single set of instructions matched my configuration, so there was a lot of work to do to figure out what was actually being described.

Upgrading like what? I'm confused?  Do you mean picking better virtual hardware?  That's normal for every hypervisor.  The KVM performance tuning website spells out some other things that can be done to improve performance.

On the same physical host, I see 20Gbps+ using virtio drivers.
```
$ iperf3  -c hadar
Connecting to host hadar, port 5201
[  5] local 172.22.22.3 port 35424 connected to 172.22.22.6 port 5201
....
[ ID] Interval           Transfer     Bitrate         Retr
[  5]   0.00-10.00  sec  27.0 GBytes  **23.2** Gbits/sec    0             sender
[  5]   0.00-10.00  sec  27.0 GBytes  **23.2 Gbits**/sec                  receiver
iperf Done.

```
I've seen 34Gbps when the host wasn't busy. It is transcoding some videos now.

With Windows, drivers are just too much hassle.  When there is a boot issue, you'll consider whether using virtio was a smart choice.  I  sometimes wish I'd gone with PRO/1000 and SCSI drivers instead, because those are built-into Windows. When Windows won't boot, you'll need to load drivers, since MSFT hasn't decided that virtio drivers should be default. Every hypervisor supports them - well, perhaps whatever hypervisor MSFT makes doesn't, but all the others do.

Linux has virtio support built-in and has for 10 yrs or so. It is only a Microsoft OS problem and only Microsoft can fix it. Complain to them. While you are at it, complain that they don't provide ssh-copy-id too!  It took them about 20 yrs to support ssh and they left off that tool?

In general, I don't have to install **any** VM specific stuff for my Linux VM systems to fly.

---

### Post by TheFu on 2021-05-01
netplan config files go into /etc/netplan/ ...

---

### Post by cjsmall on 2021-05-03
Never used or ran across netplan before.  All my network hardware interfaces were automatically configured years ago when Ubuntu was first installed and I simply configure new machines by setting up the hosts, networks, etc. files.  Does netplan just automate this or is it doing something more?

There currently are no files under /etc/netplan/.  Is there a way to auto-generate a **00-installer-config.yaml** file that is an accurate snapshot of the existing network configuration?  I saw nothing for this in the manpages or the documents I read online.

---

### Post by TheFu on 2021-05-03
A fresh install of 20.04 Server asks for network configuration information if you don't use DHCP. Answer those questions correctly and it will create a netplan.yaml file and might work.  Netplan was introduced around 17.10, but upgrades from 16.04 --> 18.04 don't force a switch.  I don't know about 20.04. Haven't done any upgrades to that release, only a few fresh installations.

If you change the virtual network adapter from a slow one to virtio, doesn't the network subsystem on Xubuntu pick that up and make it work?

Answers for many questions are different depending on whether it is a desktop install or a server install. 
For desktops, perhaps someone else will explain for the Xubuntu Desktop Users Guide will have answers?  IDK. 
I don't use network-manager to manage my network settings on any Ubuntu, so I'm not the best person to ask about that. Sorry.

---

### Post by Tadaen_Sylvermane on 2021-05-03
Is this an upgrade from 16.04 or previous? If so then that is likely the issue. The upgrade to 18.04 didn't automatically switch to netplan. It's something you needed to do manually. You may still be on ifupdown (right name?). On a desktop install there should at least be a minumum config file like this when done from 18.04 > now.

```
network:
 version: 2
 renderer: NetworkManager
```

On a server if you did a static ip during install it should look like this. Adjust to match your configuration of course.

```
network:
 version: 2
 renderer: networkd
 ethernets:
  eth0:
   dhcp4: false
   dhcp6: false
   addresses: [192.168.1.10/24]
   gateway4: 192.168.1.1
   nameservers:
    addresses: [8.8.8.8, 8.8.4.4]
```

[https://itectec.com/ubuntu/ubuntu-how-to-enable-netplan-on-ubuntu-server-upgraded-from-16-04-to-18-04/](https://itectec.com/ubuntu/ubuntu-how-to-enable-netplan-on-ubuntu-server-upgraded-from-16-04-to-18-04/)

---

### Post by cjsmall on 2021-05-05
I don't exactly remember the initial Xubuntu install, but I'm guessing it was 16.04 or 16.10.  I did incremental OS upgrades for every release up to 20.04, and decided to stop there and just jump between LTS releases going forward.  Nowhere in that upgrade cycle did netplan get activated and I never ran across it prior to this discussion.  Yes, I've used ifup/ifdown/ifquery/ifconfig/xinetd in addition to manually editing the network files ever since migrating from Solaris to the current Linux system.

I suspect that there is a lot more to using netplan than just creating the /etc/netplan/00-installer-config.yaml.  Online documentation refers to other configuration files, and I'm guessing that some existing networking services need to be stopped and others started in order to get this working properly.  And what benefit would I garner?  So far, it just seems like a new configuration front-end.  Is there more to netplan than that?

---

### Post by TheFu on 2021-05-06
> **cjsmall said:**
> I suspect that there is a lot more to using netplan than just creating the /etc/netplan/00-installer-config.yaml.  Online documentation refers to other configuration files, and I'm guessing that some existing networking services need to be stopped and others started in order to get this working properly.  And what benefit would I garner?  So far, it just seems like a new configuration front-end.  Is there more to netplan than that?

I don't know what, if anything, netplan improved.  For the last 10 yrs, most Linux changes have seemed to be about developers chasing "the new hotness" for CV padding.  Many changes with reason were to fix issues that nobody had.
I do know that netplan config created by the installer didn't work for me on 18.04 Server until Feb 2020. Prior installations all failed. Upgrades retained the ifup/down packages and config files, which I'm still using on all my 18.04 systems.

I have a few test 20.04 and test 21.04 systems using netplan for trivial needs.  My dislike of network-manager is about the same as my dislike for pulse audio, resolvconf, and avahi.  All of those broke things that were already working for something way too big, way tooo complex and way toooooo unneeded.
Netplan isn't any better or worse than the old "interfaces" file, IMHO.  It uses YAML, which almost all programmers know already, to provide structure to config settings. Meh. Not bad, not good, except we have to learn something new.  Would have been nice if a conversion tool from interfaces --> netplan.yaml was included by default that handled 99% of possible settings. The most common stuff really isn't THAT different, just needs keywords to be converted and almost any scripting language (perl, python, ruby) can easily dump a structure as YAML correctly.

With netplan, don't leave any excess .yaml files in the config directory. Rename the extension to disable them.  
```
$ ls /etc/netplan/
01-ens3-static.yaml
```
is what my 20.04 file looks like. It is a bonehead file:
$ more /etc/netplan/01-ens3-static.yaml 
```
network:
  version: 2
  renderer: networkd
  ethernets:
     ens3:
       addresses:
          - 172.22.22.3/24
       dhcp4: false
       dhcp6: false
       gateway4: 172.22.22.1
       nameservers:
         addresses: [ 172.22.22.80, 172.22.22.81  ]

```
Then I run
```
sudo netplan generate
sudo netplan apply --debug
```

I still don't see the improvement with this over older methods.  The file requirements are much more complex than what was needed before. Somehow, it must be systemd's fault. We know that, right? ;)

---

### Post by cjsmall on 2021-05-07
I don't know why my last reply disappeared.

I've been upgrading incrementally ever since 16.04 or 16.10 (can't remember exactly) up through 20.04.  I decided to stop that and now only jump between LTS releases.  Nowhere during those upgrades was netplan mentioned or offered.  I never heard about it until reading this thread.

Anyway, what benefit would it offer me at this point?  It seems like just another front-end way of managing the network files.  Other than setting up the initial network and very occasionally adding a new machine to the host file or replacing a router, I really do very little reconfiguring the network.  However, maybe I'm missing something.

---

### Post by TheFu on 2021-05-07
Most people using a GUI would use network-manager.
Netplan is for non-GUI setups (i.e. servers) and for people like me who hate network-manager with a passion.

The difficulty happens when someone needs a bridge and isn't happy with the default NAT setup that libvirt provides.  Back in 2010, the networking that any hypervisor setup was really slow when compared to what we could accomplish with the brctl or "interfaces" file, so I stopped using everything else back then.  On GigE networks, the bridge-utils provides 920Mbps. On 10GigE connections, there is openv-switch which does much better, but isn't worth it for GigE.

---

### Post by cjsmall on 2021-05-08
Oops, there's my repeated comment!.  Thank you for the detailed netplan info.  I guess I won't touch things that don't need fixing but it's great to know about all of this for when I run into it in the future.

---

### Post by Doug S on 2021-05-08
I agree with TheFu's last few comments. I stayed with server 16.04 as long as I could and went back to ifupdown for my short time with server 18.04. I went directly from 16.04 to Debian Bullseye for my main server, because I didn't want to use netplan. My test server is Ubuntu 20.04 though.

---

