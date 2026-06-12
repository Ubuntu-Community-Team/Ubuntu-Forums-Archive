---
title: "KVM &amp; networking question"
date: 2015-05-06
forum: Virtualisation
---

### Post by dnedzel on 2015-05-06
I am pretty new to Ubuntu, hope someone can point me in the right direction:

 - I have ubuntu 14.04.2 LTS installed on a machine on my home network, this is the host
 - I am running KVM
 - I have a VM also running Ubuntu 14.04.2 for Apache2, this is the guest
 - I want to host a website in this Web Server that is available from other machines on my home network

I think I need to use a bridged network interface on my host.

I went thru the setting up a bridge network section in: [https://help.ubuntu.com/community/KVM/Networking](https://help.ubuntu.com/community/KVM/Networking)

I can see the web page in a browser in the guest and the host, but not from a separate machine on my home network.  Right now I am not using DNS, I just enter the ip address of the guest into the address on the browser.

I can't ping the guest from the other machine.

Any ideas what I am missing?  I am not sure where to start looking for the problem.

thanks, in advance, for any help!

- Derrick

---

### Post by TheFu on 2015-05-06
What is the IP for the host and the guest? What are the other network settings like netmask, gateway, DNS for each?

Any firewall settings?

If you are willing to always use the IP address, fine.
Or you can have your router run DNS and provide DHCP reservations.
Or you can modify the /etc/hosts file on every machine in the house.

I do both. Ansible makes keeping the /etc/hosts files consistent fairly easy.

---

### Post by dnedzel on 2015-05-06
Thanks for responding.  Here is info you asked for:

**host**
derrick@derrick-Inspiron-3847:~$ ifconfig
br0       Link encap:Ethernet  HWaddr b0:83:fe:50:13:ee  
          inet addr:192.168.0.7  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::b283:feff:fe50:13ee/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:45543 errors:0 dropped:0 overruns:0 frame:0
          TX packets:53657 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:11190836 (11.1 MB)  TX bytes:25489222 (25.4 MB)

eth0      Link encap:Ethernet  HWaddr b0:83:fe:50:13:ee  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:62044 errors:0 dropped:0 overruns:0 frame:0
          TX packets:53657 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:15446462 (15.4 MB)  TX bytes:25489222 (25.4 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:132336 errors:0 dropped:0 overruns:0 frame:0
          TX packets:132336 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:87523582 (87.5 MB)  TX bytes:87523582 (87.5 MB)

virbr0    Link encap:Ethernet  HWaddr fe:54:00:63:4a:ff  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3107 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3020 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:470791 (470.7 KB)  TX bytes:3888937 (3.8 MB)

vnet0     Link encap:Ethernet  HWaddr fe:54:00:63:4a:ff  
          inet6 addr: fe80::fc54:ff:fe63:4aff/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3107 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24399 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:514289 (514.2 KB)  TX bytes:5004558 (5.0 MB)

wlan0     Link encap:Ethernet  HWaddr ec:0e:c4:5a:53:4f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

**guest**
derrick@derrick-Inspiron-3847:~$ ifconfig
br0       Link encap:Ethernet  HWaddr b0:83:fe:50:13:ee  
          inet addr:192.168.0.7  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::b283:feff:fe50:13ee/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:45543 errors:0 dropped:0 overruns:0 frame:0
          TX packets:53657 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:11190836 (11.1 MB)  TX bytes:25489222 (25.4 MB)

eth0      Link encap:Ethernet  HWaddr b0:83:fe:50:13:ee  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:62044 errors:0 dropped:0 overruns:0 frame:0
          TX packets:53657 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:15446462 (15.4 MB)  TX bytes:25489222 (25.4 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:132336 errors:0 dropped:0 overruns:0 frame:0
          TX packets:132336 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:87523582 (87.5 MB)  TX bytes:87523582 (87.5 MB)

virbr0    Link encap:Ethernet  HWaddr fe:54:00:63:4a:ff  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3107 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3020 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:470791 (470.7 KB)  TX bytes:3888937 (3.8 MB)

vnet0     Link encap:Ethernet  HWaddr fe:54:00:63:4a:ff  
          inet6 addr: fe80::fc54:ff:fe63:4aff/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3107 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24399 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:514289 (514.2 KB)  TX bytes:5004558 (5.0 MB)

wlan0     Link encap:Ethernet  HWaddr ec:0e:c4:5a:53:4f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

Firewall - I have a firewall on my router which is enabled.  I just have the default Ubuntu install on the host, I haven't done anything a software firewall there.
I am willing to use the IP address, at least for now.  I may setup dns on the router at a later time, but one thing at a time.

thanks again for any suggestions!
- Derrick

---

### Post by TheFu on 2015-05-06
The GuestOS must have a different IP on 192.168.0.x/24.
Or did you show the wrong output? wlan shouldn't be seen any any guestOS. You must boot into the guestOS to get the IP from it. 

Also - it would be helpful for reading if "code tags" are used so things line up.

---

### Post by dnedzel on 2015-05-06
Oops, sorry, my mistake:

```
**Host** - derrick-Inspiron-3847

derrick@derrick-Inspiron-3847:~$ ifconfig
br0       Link encap:Ethernet  HWaddr b0:83:fe:50:13:ee  
          inet addr:192.168.0.7  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::b283:feff:fe50:13ee/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:79396 errors:0 dropped:0 overruns:0 frame:0
          TX packets:94908 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:21062380 (21.0 MB)  TX bytes:51411515 (51.4 MB)

eth0      Link encap:Ethernet  HWaddr b0:83:fe:50:13:ee  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:99461 errors:0 dropped:0 overruns:0 frame:0
          TX packets:94907 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:26247806 (26.2 MB)  TX bytes:51411449 (51.4 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:252708 errors:0 dropped:0 overruns:0 frame:0
          TX packets:252708 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:196615656 (196.6 MB)  TX bytes:196615656 (196.6 MB)

virbr0    Link encap:Ethernet  HWaddr fe:54:00:63:4a:ff  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7249 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7386 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:982978 (982.9 KB)  TX bytes:9812951 (9.8 MB)

vnet0     Link encap:Ethernet  HWaddr fe:54:00:63:4a:ff  
          inet6 addr: fe80::fc54:ff:fe63:4aff/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7249 errors:0 dropped:0 overruns:0 frame:0
          TX packets:31410 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:1084464 (1.0 MB)  TX bytes:11066222 (11.0 MB)

wlan0     Link encap:Ethernet  HWaddr ec:0e:c4:5a:53:4f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

derrick@derrick-Inspiron-3847:~$
[B]

Guest[/B] - derrick-Standard-PC-i440FX-PIIX-1996 (name assigned by KVM)

derrick@derrick-Standard-PC-i440FX-PIIX-1996:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 52:54:00:63:4a:ff  
          inet addr:**192.168.122.60**  Bcast:192.168.122.255  Mask:255.255.255.0
          inet6 addr: fe80::5054:ff:fe63:4aff/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:31557 errors:0 dropped:4 overruns:0 frame:0
          TX packets:7347 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11171283 (11.1 MB)  TX bytes:1096902 (1.0 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1643 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1643 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:150301 (150.3 KB)  TX bytes:150301 (150.3 KB)
```

KVM assigns ip address in a different range than what I have setup on my router.  Router DHCP config'd to assign: 192.168.0.2-100, KVM assigns this VM: 192.168.122.60

I don't understand why VM's don't just use DHCP like a regular computer, but maybe it's because there isn't a physical NIC so KVM has to either do bridging or NAT?  My lack of networking knowledge is showing!  :-)

thanks,
- Derrick

---

### Post by dnedzel on 2015-05-06
Shoot - when I created message it kept formatting but when I posted it went away.  How do I use code tags to avoid this?

Sorry!
- Derrick

---

### Post by Bucky Ball on 2015-05-06
[code] tags, please, as requested. ;)

I have done the last post for you. Please see the last link in my signature. Thanks.

* Oops, just saw your last post. Apologies. I have added code tags to your last terminal output posted. Edit that and have a look. ;)

---

### Post by dnedzel on 2015-05-06
Nevermind - found a description:  [http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

will repost with code tags - give me a minute.

thx

---

### Post by Bucky Ball on 2015-05-06
See my previous posts ...

---

### Post by dnedzel on 2015-05-06
**host ** - derrick-Inspiron-3847
```

derrick@derrick-Inspiron-3847:~$ ifconfig
br0       Link encap:Ethernet  HWaddr b0:83:fe:50:13:ee  
          inet addr:192.168.0.7  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::b283:feff:fe50:13ee/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:79396 errors:0 dropped:0 overruns:0 frame:0
          TX packets:94908 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:21062380 (21.0 MB)  TX bytes:51411515 (51.4 MB)

eth0      Link encap:Ethernet  HWaddr b0:83:fe:50:13:ee  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:99461 errors:0 dropped:0 overruns:0 frame:0
          TX packets:94907 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:26247806 (26.2 MB)  TX bytes:51411449 (51.4 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:252708 errors:0 dropped:0 overruns:0 frame:0
          TX packets:252708 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:196615656 (196.6 MB)  TX bytes:196615656 (196.6 MB)

virbr0    Link encap:Ethernet  HWaddr fe:54:00:63:4a:ff  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7249 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7386 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:982978 (982.9 KB)  TX bytes:9812951 (9.8 MB)

vnet0     Link encap:Ethernet  HWaddr fe:54:00:63:4a:ff  
          inet6 addr: fe80::fc54:ff:fe63:4aff/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7249 errors:0 dropped:0 overruns:0 frame:0
          TX packets:31410 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:1084464 (1.0 MB)  TX bytes:11066222 (11.0 MB)

wlan0     Link encap:Ethernet  HWaddr ec:0e:c4:5a:53:4f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

**Guest** - derrick-Standard-PC-i440FX-PIIX-1996
```

derrick@derrick-Standard-PC-i440FX-PIIX-1996:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 52:54:00:63:4a:ff  
          inet addr:192.168.122.60  Bcast:192.168.122.255  Mask:255.255.255.0
          inet6 addr: fe80::5054:ff:fe63:4aff/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:31557 errors:0 dropped:4 overruns:0 frame:0
          TX packets:7347 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:11171283 (11.1 MB)  TX bytes:1096902 (1.0 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1643 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1643 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:150301 (150.3 KB)  TX bytes:150301 (150.3 KB)

```


KVM assigns ip address in a different range than what I have setup on my router. Router DHCP config'd to assign: 192.168.0.2-100, KVM assigns this VM: 192.168.122.60

I don't understand why VM's don't just use DHCP like a regular computer, but maybe it's because there isn't a physical NIC so KVM has to either do bridging or NAT? My lack of networking knowledge is showing!

thanks,
- Derrick

---

### Post by Doug S on 2015-05-06
> **dnedzel said:**
> I don't understand why VM's don't just use DHCP like a regular computer,They can, and you are almost there, since you already have the bridge set up. You just need to tell your VM to use it.

There are other ways to do this, but here is how I do it:
For an existing VM, use virsh edit and change this area (substitute your MAC, as I just copied one of mine)):```
    <interface type='network'>
      <mac address='52:54:00:0d:ed:95'/>
      <source network='default'/>
      <model type='virtio'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x03' function='0x0'/>
    </interface>
```To this:```
    <interface type='bridge'>
      <mac address='52:54:00:0d:ed:95'/>
      <source bridge='br0'/>
      <model type='virtio'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x03' function='0x0'/>
    </interface>
```

---

### Post by dnedzel on 2015-05-06
Thanks Doug - do I run virsh in the host or the guest? 

thanks!

---

### Post by Doug S on 2015-05-06
> **dnedzel said:**
> do I run virsh in the host or the guest? You run virsh edit in the host, with the guest not running. You are going to edit the guests definition file. Say your guest name was desk_dev, then the definition file will be /etc/libvirt/qemu/desk_dev.xml. But you must use "virsh edit desk_dev" (from any directory) to to the edit as some checks are done upon save exit from the editor.

Note 1: the default editor used by virsh edit is as defined by the $EDITOR environment variable, or VI if it does not exist. add export EDITOR="/bin/nano" to your ~/.bashrc file to set, for example, nano as your default editor.

Note 2: There is a way to do this with virt-manager, but I do not use it and do not know how.

---

### Post by TheFu on 2015-05-06
You can run virsh or virt-manager from anywhere on the network - it can use an ssh connection to manage VMs.
virt-manager is 1000x easier than virsh - it is a GUI like virtualBox or vSphere.

Don't use the built-in bridge (the one that was created by libvirt automatically) if you care about stability. 
a) it is NAT
b) it goes up and down
c) a manually created bridge is rock, stable.

virt-manager has an "apply" button when you are editing settings for a VM.
virt-manager can be run from anywhere on the network that has ssh access into the VM host.
There are a few things that virt-manager cannot do but for a beginner - it makes everything around KVM VMs easier.  What won't it do?
* create qcow2 virtual HDDs
* create lxc containers
Those are the big ones off my head. There are probably other things too, but I don't use them.

virt-manager means never needing to have Windows to manage a group of VM hosts with a GUI. ;) !!!!!!  That always bothered me about vsphere.  OTOH, I don't think there is a Windows virt-manager client, so you'll want a Linux desktop "somewhere" to manage VMs.

Plus with libvirt on the hostOS and management workstation (which can be the same or different systems), the VM manager doesn't need root/sudo. Membership in the libvirtd group is sufficient authority to create, manage, start, stop, destroy, and delete VMs.

I've been meaning to make a short video about setting of KVM + virt-manager ... someday.  Most people only show these things on 1 PC.  My KVM servers are headless - doesn't matter - as long as the machine running virt-manager is running X/Windows and virt-manager w/ ssh access.
[http://blog.jdpfu.com/ALE/ALE-NW/2014_04-virtualization.html](http://blog.jdpfu.com/ALE/ALE-NW/2014_04-virtualization.html) has a presentation I've given on this. Bridge config is on pg 15. This isn't really meant to be presented without a speaker - sorry.

BTW - if you are the last poster and need to update something, please just edit your last post. We don't need 30 posts with the same ifconfig. ;)

---

### Post by dnedzel on 2015-05-06
Doug and TheFu,

Thanks so much guys!  This is super helpful info!  Up to my eyeballs in iOS coding right now, will work on the KVM networking this evening.  Should be pretty easy now.

---

