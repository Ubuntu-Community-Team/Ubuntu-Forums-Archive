---
title: "2 NICs on KVM host"
date: 2024-01-05
forum: Virtualisation
---

### Post by aljames2 on 2024-01-05
I want to use my extra NIC card (1 port), that I have plugged into a PCIe slot, and assign it to my WG VPN vm.  Trying to figure out how to either assign or passthru this nic.  The KVM host is on Ubuntu 22.04 with a netplan file creating a bridge (br0) for my Nextcloud server to run on. I am not seeing a way to assign this other physical interface in virt-manager.  The only option I see under network source is either br0 or Macvtap. Perhaps Macvtap?  Or, can I set up a second bridge (br1) in the same .yaml file for this interface assignment? I’ve read some about PCI passthrough and the process seems tricky and not always reliable.  I appreciate any ideas

---

### Post by QIII on 2024-01-05
One use case in my situation:

Use ifconfig to get the names of your interfaces.  I usually assign the VM a Macvtap device with the name of the interface.  Bear in mind that macvtap does not usually facilitate direct host-to-guest communication, so you'll have to treat the VM as just another machine on your LAN.  I have 14 available NICs on this particular machine, so I can assign individual NICs to VMs permanently.  I also have a 24 port switch that everything is individually connected to.  You may not find this the best solution for your use case.

You can find details at [https://www.linux-kvm.org/page/Networking](https://www.linux-kvm.org/page/Networking) and make your choices.

---

### Post by aljames2 on 2024-01-06
Much thanks QIII, this helps, some new information I hadn’t found yet.  I should have this sorted out today.

---

### Post by MAFoElffen on 2024-01-07
RE: [https://wenchma.github.io/2016/09/07/macvtap-deep-dive.html](https://wenchma.github.io/2016/09/07/macvtap-deep-dive.html)

I did mine a bit differently... With my old Dell PE T720, I had many  NIC's as that machine was designed as a virt host... But my newer  workstation only came with a single onboard NIC. 

What I added to my workstation was a 2 port PCIe x4 lane Intel 82576 chip'ed NIC. That is SR-IOV capable where I set one of the ports as my Bridge, and the other I setup as SR-IOV, with 8 virtual ports. The NIC was $35 new. These cards come in PCIe x1 & x4 for the same price.

 I have mine setup by just adding two boot parameters, and defined in my  netplan yaml file. Then a short XML file to add it into the KVM  networking. Fairly painless.

It worked so well, and was so much easier than I remember it being prior to 18.04... That if I did it again, I would do it a bit differently... See below.

A Dell Intel i350-T4 is Quad-port and is PCIe x4 lane. Each port can be split into 8 virtual ports... And can be had between $35 to $85 dollars. That comes out to 32 ports, for about  $2.65 a port, if you picked it up on the high end of that scale ($85). A very good value, and a wise long-term investment.

I used PCIe x4, because I was worried about throughput. (Even though SR-IOV spec's are rated high) I thrash that machine and the loads I put on it... But I do have my media server on it. If it affects my wife watching what she is used to and wants to watch... It gets scary. I need to keep her happy and content. LOL.

---

### Post by aljames2 on 2024-01-16
```

                WAN
                |
             ___|_________
            |  pfSense    |
            |   Router    |
            |____ (en01)__|
                    |
                    |
                    |-------(VLAN - en01.2) 192.168.23.0 (subnet)
                    |
                    |
                    |10.11.37.0 (trunk subnet)
                    |
                ____|___
               | switch |
               |________|(dumb/unmanaged sw)
                 |  |
              ___|  |
                    |
                    |
                ____|_______
               | KVM Host   |
               |            |
               |_nic1__nic2_|
                  |     |
                  |     |
                  |     |
     10.11.37.5 (br0)   |
                  |     |
                  |     |
             (NC VM)   (WG-vpn VM)
         10.11.37.10     192.168.23.112 (VLAN)

```


Thought I'd try some ascii art. :)

This is what I am trying to do.  To use 1 port off the router, through my dumb switch, and onto my KVM host machine.  There are 2 VMs (Nextcloud & Wireguard vpn). I have other physical machines connected to this switch as well but I'm focusing on this branch.  I am thinking of involving the router to create a vlan to help with some isolation between the VPN & the KVM host, by putting the VPN on a VLAN subnet.  Essentially isolate the VPN server.

At present, I have 2 NICs on the KVM host but neither support SR-IOV.  I can run 2 cables between my dumb switch & the host but this doesn't seem to achieve the goal. I would have each VM on a separate NIC but there would be no isolation as I see it. The switch is not VLAN smart and cannot help control traffic.  I prefer not to have a managed switch.

@MAFoElffen, I did just order that PCIe Dell quad port device for the KVM host. I do know that my MB supports SR-IOV & IOMMU. Not sure I'll know how to use it when I get it, LOL...  Will I even need to deal with using a VLAN if I can get this virtual networking set up right on the host?

---

### Post by MAFoElffen on 2024-01-17
> **aljames2 said:**
> 
At present, I have 2 NICs on the KVM host but neither support SR-IOV.  I can run 2 cables between my dumb switch & the host but this doesn't seem to achieve the goal. I would have each VM on a separate NIC but there would be no isolation as I see it. The switch is not VLAN smart and cannot help control traffic.  I prefer not to have a managed switch.

@MAFoElffen, I did just order that PCIe Dell quad port device for the KVM host. I do know that my MB supports SR-IOV & IOMMU. Not sure I'll know how to use it when I get it, LOL...  Will I even need to deal with using a VLAN if I can get this virtual networking set up right on the host?
I figure with a KVM host, you can never have enough network ports to play with!!!

VLANs -- Though I have trained on them and done them, while training for CISCO CCNA... I don't find a need for them here. Besides, then to get out of that VLAN to something else, then you have to route to there.

For SR-IOV, at first I did via a vfio.conf file in modules, excluding... But then after doing that that way, I found I severely overthought that!!! It can be done a lot simpler and easier...

First your find the ID of the NIC in lspci
```

mafoelffen@msi-ubuntu:~$ lspci -nnnk | grep -E 'Ethernet'
    DeviceName: Onboard - Ethernet
06:00.0 Ethernet controller [0200]: Intel Corporation Device [8086:125c] (rev 04)
07:00.0 Ethernet controller [0200]: Intel Corporation 82576 Gigabit Network Connection [COLOR=#ff0000][8086:10c9][/COLOR] (rev 01)

```
Then in the GRUB_CMDLINE_LINUX_DEFAULT line of /etc/default/grub:
```

mafoelffen@msi-ubuntu:~$ grep 'GRUB_CMDLINE_LINUX_DEFAULT' /etc/default/grub
GRUB_CMDLINE_LINUX_DEFAULT="-- splash [COLOR=#ff0000]intel_iommu=on iommu=pt igb.max_vfs=7[/COLOR]"

```
Then, after a reboot, I do 'ip a' to confirm it's split out, then do my netplan file
```

mafoelffen@msi-ubuntu:~$ grep . /etc/netplan/00-installer-config.yaml
# This is the custom network config written by MAFoElffen
network:
  version: 2
  renderer: networkd
  ethernets:
    enp6s0:
      dhcp4: false
      dhcp6: false
      addresses:
          - 10.0.0.5/8
      nameservers:
          addresses: [8.8.8.8, 8.8.4.4]
      routes:
          - to: default
            via: 10.0.0.1
            metric: 100
            on-link: true
      mtu: 1500
## Begin SR-IOV on enp7s0f0 
    enp7s0f0:
      virtual-function-count: 7
      dhcp4: false
      dhcp6: false
      optional: yes
    enp7s0f0v0:
      link: enp7s0f0
      addresses:
          - 10.0.0.10/8
      nameservers:
          addresses: [8.8.8.8, 8.8.4.4]
      dhcp4: false
      dhcp6: false
      optional: yes
    enp7s0f0v1:
      link: enp7s0f0
      addresses:
          - 10.0.0.11/8
      nameservers:
          addresses: [8.8.8.8, 8.8.4.4]
      dhcp4: false
      dhcp6: false
      optional: yes
    enp7s0f0v1:
      link: enp7s0f0
      addresses:
          - 10.0.0.11/8
      nameservers:
          addresses: [8.8.8.8, 8.8.4.4]
      dhcp4: false
      dhcp6: false
      optional: yes
    enp7s0f0v2:
      link: enp7s0f0
      addresses:
          - 10.0.0.12/8
      nameservers:
          addresses: [8.8.8.8, 8.8.4.4]
      dhcp4: false
      dhcp6: false
      optional: yes
    enp7s0f0v3:
      link: enp7s0f0
      addresses:
          - 10.0.0.13/8
      nameservers:
          addresses: [8.8.8.8, 8.8.4.4]
      dhcp4: false
      dhcp6: false
      optional: yes
    enp7s0f0v4:
      link: enp7s0f0
      addresses:
          - 10.0.0.14/8
      nameservers:
          addresses: [8.8.8.8, 8.8.4.4]
      dhcp4: false
      dhcp6: false
      optional: yes
    enp7s0f0v5:
      link: enp7s0f0
      addresses:
          - 10.0.0.15/8
      nameservers:
          addresses: [8.8.8.8, 8.8.4.4]
      dhcp4: false
      dhcp6: false
      optional: yes
    enp7s0f0v6:
      link: enp7s0f0
      addresses:
          - 10.0.0.16/8
      nameservers:
          addresses: [8.8.8.8, 8.8.4.4]
      dhcp4: false
      dhcp6: false
      optional: yes
## End SR-IOV on enp7s0f0
## Begin Bridge on enp7s0f1
    enp7s0f1:
      dhcp4: false
      dhcp6: false
      optional: yes
  bridges:
    br0:
      interfaces: [enp7s0f1]
      addresses: [10.0.0.6/8]
      routing-policy:
         - from: 10.0.0.6
           table: 10
      # ** ADDITIONAL ROUTING POLICY **
         - to: 172.16.1.0/24
           table: 172
      # *******************************
      routes:
         - to: 0.0.0.0/0
           via: 10.0.0.1
           table: 10
      nameservers:
        addresses: [8.8.8.8, 8.8.4.4, 1.1.1.1, 1.0.0.1]
      parameters:
        stp: true
        forward-delay: 4
      dhcp4: no
      dhcp6: no
      optional: yes
## End Bridge on enp7s0f1

```
Then apply
```

sudo netplan generate
sudo netplan apply

```
Done.

---

### Post by aljames2 on 2024-01-17
Thanks for the details, this helps! 
That new&#8230; (new to me)&#8230; card arrived today, I will be working on this very soon. The extra ports will come in handy because I do want to add a few more servers to this host.

---

### Post by aljames2 on 2024-01-25
An update

I received the Dell I350-T4 Quad port card I bought, I thought it was new, at least it was advertised as such, but it wasn't.  Anyhow, after running lspci, I noticed it did not show the SR-IOV capability.  I made sure the IOMMU & SR-IOV setting was enabled on the MB as well as in grub.  After some reading on the Intel website, I learned that some of the Dell OEM cards are know to have the SR-IOV disabled on the card.  In particular the Gigabit cards.  I think there is another version, perhaps I350-T4V2 that is fine. If you get the Intel retail version of the card then it comes with SR-IOV enabled. I think Dell figured users of a gigabit card would not need SR-IOV.  Perhaps they are right. I shipped that card back.

I had another card lying around that I had thought a few years ago wasn't working but turns out it does work.  I guess I didn't know what I was doing with it previously :)   It is a Intel Gigabit ET 82576 Quad Port server adapter.  At first, I had no lights on any of the ports, so I figured my original theory of a broken card was true. Then I found a "Gen" setting in my Asus Bios for the PCIe 16_2 x4 slot.  The default setting was Auto which didn't work.  I knew this older card was likely not Gen-3 or Gen-4, so I set it to Gen-2 and voila, the card works.  I have the VFs set up now & so far so good.

Wondering if I should let the Host be assigned by itself to the MB integrated port, and put the VMs all on this card, that's what I am thinking..

---

### Post by MAFoElffen on 2024-01-27
Good job. It may help others here to share what settings and changes you made to your /etc/default/grub and /etc/netplan/<Named>.yaml file so they can do the same...

Just a thought.

---

### Post by aljames2 on 2024-01-29
> **MAFoElffen said:**
> Good job. It may help others here to share what settings and changes you made to your /etc/default/grub and /etc/netplan/<Named>.yaml file so they can do the same...

Thanks, I do plan to share all I’ve done here soon.  I am still trying to sort out getting my PCIe nic to pass through.  My issue is an error that virt-manager gives about some devices in the same IOMMU group need to be bound to a VFIO driver.  It is IOMMU group# 15. I have 18 devices all lumped in this group.  Some of which are upstream root based devices, such as a few cpu & bridge functions.  The root devices are not the issue, but all of my nics, VFs, & an onboard NVMe are also in this group.  So I either need to pass all the non-root devices through to the VM which I don’t want, or somehow detach the device I want to pass.  I have read about overriding ACU which eliminates isolation and is a last resort.

---

### Post by MAFoElffen on 2024-01-30
I do not pass my NICs through... I setup virtual networks in KVM, and use those virtual network switches from the guests.

RE:
[https://www.linux-kvm.org/page/Networking](https://www.linux-kvm.org/page/Networking)
[https://wiki.qemu.org/Documentation/Networking](https://wiki.qemu.org/Documentation/Networking)
[https://help.ubuntu.com/community/KVM/Networking](https://help.ubuntu.com/community/KVM/Networking)

Then, for example, I create a DD-WRT and PFsense VM router appliances, that I can route between those virtual networks, or an Ubuntu Server VM, that I can use as a Router appliance.

I get a bit creative in replicating virtual network schemes to satisfy what my testcases are or what I am trying to accomplish.

KVM/Qemu makes many things possible in your virtual world, if you use your imagination. The idea is to create things virtually, which would normally be in real hardware. Just because you only have one switch and router "physically", should not limit what you can do within your virtual world. Those (now_ extra 4 physical ports) now extend how your Virtual host can communicate outside that virtual network.

The easiest way to use a NIC port as dedicated is to set it as a bridged port device.

---

### Post by aljames2 on 2024-02-06
I gave up on trying to do PCI passthrough.  Learned my lesson once and for all, never again to try that.  I can explain in detail why, but it wouldn't apply to everyone, some have had success but not always possible depending on your hardware..

I ended up making a setup on this subnet that does make use of my extra quad-port ethernet card and the SR-IOV feature it supports. The sr-iov essentially makes up to 8 nics out of each physical nic, 32 total.  Althought, I have only initialized 2 virtual nics on 1 physical nic for now, can easily initialize more as needed.

Since I won't be doing PCI passthrough to my VM, I will add an SR-IOV network adapter to a KVM VM as a Virtual Function (VF) network adapter connected to a macvtap on the host.

Some of this inspired from here:
[https://www.intel.com/content/www/us/en/developer/articles/technical/configure-sr-iov-network-virtual-functions-in-linux-kvm.html](https://www.intel.com/content/www/us/en/developer/articles/technical/configure-sr-iov-network-virtual-functions-in-linux-kvm.html)

And some clues from @MAFoElffen's netplan shared earlier, thanks again !

Some facts:
- Hardware is AMD 5600x, on Asus B550-A Gaming mobo, supports IOMMU, SR-IOV, & SVM
- Ubuntu 22.04 KVM host
- My Wireguard VM started out running on my KVM bridge, same as my Host & NC server
- Goal to move WG server to its own physical interface, and have fun doing it :)
- This process is editorialized without all the outputs, instead explanation of what you should see, not always what my output was. YMMV

Here is what I did:

```

# Shut down computer
# Installed quad port nic, no wire attached yet  (WG server still on br0 for now)
# Start computer

ip a  (mobo NIC name changed as expected with the introduction of another adapter)

# See 4 new NIC ports and their names

# edit /etc/netplan/kvm-host.yaml
# ...correct my ethernet name definition in order to bring up the host network again

sudo netplan generate
sudo netplan apply
reboot  (for good measure)

ip a  (Now our mobo nic is back up)

----------------------------

# Restart computer & enter MB BIOS (F2 or DEL)
# Enable:  SR-IOV, IOMMU, & SVM
# In Advanced, Go to "Onboard Connections Configuration", & set PCIe 16_2 slot to "Gen 3"  (Auto did not work)
# Save & restart computer

----------------------------

# Now, check if this old/(new to me), NIC supports SR-IOV

sudo lshw -c network -businfo
sudo lspci -vs 0000:06:00.0  (using the pci address from previous command)

# Look for something like this in the output:
Capabilities: [160 v1] Single Root I/O Virtualization (SR-IOV)

# Do this lspci for each NIC port address to be sure each are SR-IOV capable
# Assuming our device supports SR-IOV, continue...

----------------------------

# Edit /etc/default/grub
# Add these within the quotes: amd_iommu=on iommu=pt
 (my line has some extra stuff and looks like the following)

GRUB_CMDLINE_LINUX_DEFAULT="ipv6.disable=1 amd_iommu=on iommu=pt"

sudo update-grub

# Attach ethernet wire between my chosen NIC port & the switch

reboot

# Check our switch & interface, lights should be flashing. If no lights something is wrong.

ip a  (make note of our top port name: enp6s0f0)

----------------------------

# We will now initialize SR-IOV VFs (Virtual Functions) on this port we chose.

# become root
sudo -i

cd /sys/class/net
ls -al  (see our device names)
cd ./enp6s0f0/device
ls -al  (find sriov_numvfs file)
cat sriov_numvfs  (current value should be 0)

echo 2 > sriov_numvfs
# I chose to only initialize 2 VFs for now.
# This will manually initialize 2 VFs on this port, but they won't survive boot, so we'll use our new output to write a new netplan file which will make the virtual function definitions permanent.

cat sriov_numvfs  (value should now be 2)
exit  (root)

ip a  (notice our 2 virtual nics now exist on this physical port & each with its own MAC address)
    enp6s0f0v0
    enp6s0f0v1

sudo lshw -c network -businfo  (another look to see our VFs each have a different bus address as well)

# Edit my netplan file
cd /etc/netplan

# Save a copy of the original file first
sudo cp kvm-host.yaml kvm-host.yaml.bak

# My netplan file is this:

----------------------------

#  [ for KVM + bridge + SR-IOV ]
network:
  version: 2
  renderer: networkd
# Define our Host NIC - bridge will use this NIC below
  ethernets:
    enp12s0:
      dhcp4: false
      dhcp6: false
# Define our SR-IOV NIC (Physical Function)
    enp6s0f0:
      virtual-function-count: 2
      dhcp4: false
      dhcp6: false
      optional: yes
# Define our SR-IOV VFs (Virtual Functions) on enp6s0f0
    enp6s0f0v0:
      link: enp6s0f0
      dhcp4: false
      dhcp6: false
      optional: yes
    enp6s0f0v1:
      link: enp6s0f0
      dhcp4: false
      dhcp6: false
      optional: yes
# End SR-IOV Definitions
  bridges:
    br0:
      interfaces: [enp12s0]
      addresses: [10.11.37.81/24]
      routes:
      - to: default
        via: 10.11.37.1
        metric: 100
        on-link: true
      mtu: 1500
      nameservers:
        addresses: [10.11.37.1]
      parameters:
        stp: true
        forward-delay: 4
      dhcp4: no
      dhcp6: no

----------------------------

sudo netplan generate
sudo netplan apply

ip a  (see our VFs are now set with IPs)

reboot

----------------------------

sudo lshw -c network -businfo

Bus info          Device          Class       Description
=========================================================
pci@0000:06:00.0  enp6s0f0        network     82576 Gigabit Network Connection
pci@0000:06:00.1  enp6s0f1        network     82576 Gigabit Network Connection
pci@0000:08:00.0  enp8s0f0        network     82576 Gigabit Network Connection
pci@0000:08:00.1  enp8s0f1        network     82576 Gigabit Network Connection
pci@0000:0c:00.0  enp12s0         network     Ethernet Controller I225-V
pci@0000:07:10.0  enp6s0f0v0      network     82576 Virtual Function
pci@0000:07:10.2  enp6s0f0v1      network     82576 Virtual Function


# Find our VF interface name we want to use & make a note of it
# I chose: enp6s0f0v0

# Since my VM is running on the bridge we will be editing our VM configuration to move it over to our new Virtual Function on our new interface.

virsh list --all  (shutdown VM if running)

virsh edit ubuntu-server2204_WG

# In my case, I changed this excert to match the following:

----------------------------

<devices>
…
   <interface type='direct'>
      <source dev='enp6s0f0v0' mode='passthrough'/>
   </interface>
…
</devices>

----------------------------

# Launch virt-manager & start the VM

# If errors, check:
# If no errors, also check these virtual nic settings in virt-manager:
    - Network source shows macvtap
    - Device name is our VF name (enp6s0f0v0)
    - Our MAC address exists
    - Device model is virtio

# As the VM starts, KVM creates a macvtap adapter ‘macvtap0’ on the VF specified.
# I had no errors but these are things to check even if working.

ip a  (on the host shows)

11: macvtap0@enp6s0f0v0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default qlen 500....(including it's mac address)

# It works for me

```

My diagram is something like this now:
```

                WAN
                |
             ___|_________
            |  pfSense    |
            |   Router    |
            |_____(en01)__|
              | |   |   |
           ___| |   |   |___
          ______|   |
                    |
                    |10.11.37.0 (trunk subnet)
                    |
                ____|_____
               | switch   |
               |__________|(dumb/unmanaged sw)
                  |     |
                  |     |
         (enp12s0)|     |(enp6s0f0v0 VF of enp6s0f0)
                  |     |
                __|_____|___
               | KVM Host   |
               |            |
               |_nic1__nic2_|
                  |     |
                  |     |
                  |     |
    10.11.37.81 [br0]  [macvtap passthrough to SR-IOV VF on physical nic]
                  |     |
                  |     |
             (NC VM)   (WG-vpn VM)
         10.11.37.10     10.11.37.117

```

---

### Post by MAFoElffen on 2024-02-07
Good job. 

Yes. I had to go through my own trials and errors with different combinations, until I found what worked best for me, and with what I do.

I found that passing through the NIC, is not what I want to do, as it is all one IOMMU group, so then you lose it all from the host side, and made it less valuable and flexible to me, in what I could with it from the host side, and creating differing virtual network appliances using the differing host ports that were available.

That is why I don't do the SR-IOV virtual network scheme inside KVM. I lost a lot of flexibility of my resources with that option. Just because it is possible, didn't make that a good idea. Lessons learned.

I'm still playing with that in different ways, to see what is possible, and creates the best value for me. Time will tell.

---

