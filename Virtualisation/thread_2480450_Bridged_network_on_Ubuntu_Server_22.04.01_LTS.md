---
title: "Bridged network on Ubuntu Server 22.04.01 LTS"
date: 2022-10-30
forum: Virtualisation
---

### Post by Jesper_Poulsen on 2022-10-30
Hey

I'm trying to set up a couple of VM's with KVM/Qemu. They are supposed to be on the same network as the host. I have tried out a couple of guides found on the internet but to no avail.

Will someone please tell me how to do it?


Best regards

---

### Post by Doug S on 2022-10-30
I had some troubles when I did it with a new computer on 20.04, but it turned out to be the kernel not new enough for the processor. My notes are [here]("https://ubuntuforums.org/showthread.php?t=2461631&p=14036896#post14036896").

---

### Post by Jesper_Poulsen on 2022-10-30
I do not have that problem. :-)

The server is a ProLiant from 2020.

---

### Post by Doug S on 2022-10-30
My notes are for what I did in the end that worked. My troubles were all an earlier waste of time. That same referenced thread also points to another thread on askubuntu, as I observe you posted the same question there.

---

### Post by Jesper_Poulsen on 2022-10-30
I might have more success with this answer than the one at askubuntu. I do, however, need a fully DHCP-solution as I am not in control of IP-address delegation on the network.

---

### Post by Doug S on 2022-10-30
> **Jesper_Poulsen said:**
> I do, however, need a fully DHCP-solution as I am not in control of IP-address delegation on the network.The notes I referred you to are for a fully DHCP solution.

---

### Post by Jesper_Poulsen on 2022-11-07
> **Doug S said:**
> I had some troubles when I did it with a new computer on 20.04, but it turned out to be the kernel not new enough for the processor. My notes are [here]("https://ubuntuforums.org/showthread.php?t=2461631&p=14036896#post14036896").

Sorry for the delay.

I have followed your guide and while I'm using virt-manager to setup my VM I have no IPv4 connection from the guest.
I have setup the network interface as virtio and installed the support in the gueat OS (Windows 10).

 What am I missing here?

The host is running in a VirtualBox-VM on my home PC (Linux) with bridged networking. When it works I can replicate the setup (minus the VirtualBox VM) on the ProLiant.

---

### Post by MAFoElffen on 2022-11-07
I liked your Instructions Doug S...

I have a few more virtual networks and subnets, besides just my bridge...

Just sharing "Mine" for KVM:
```

mafoelffen@opti-ubuntu:~/Scripts$ virsh net-list --all
 Name          State    Autostart   Persistent
------------------------------------------------
 default       active   yes         yes
 host-bridge   active   yes         yes
 Isolated      active   yes         yes
 Open          active   yes         yes
 Routed        active   yes         yes

mafoelffen@opti-ubuntu:~/Scripts$ awk '{print $0}' /etc/netplan/00-installer-config.yaml
# This is the network config written by 'subiquity'
network:
  version: 2
  renderer: networkd
  ethernets:
    enp3s0:
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
    enp4s0:
      dhcp4: false
      dhcp6: false
      optional: yes

  bridges:
    br0:
      interfaces: [enp4s0]
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


```

I see that the OP added another piece of the puzzle:
[QUOTE=Jesper_Paulsen]The host is running in a [COLOR=#ff0000]VirtualBox-VM[/COLOR] on my home PC (Linux) with bridged networking[/QUOTE]

---

### Post by Jesper_Poulsen on 2022-11-08
> **MAFoElffen said:**
> 
Just sharing "Mine" for KVM:

I'm on a DHCP'd network.

> 
I see that the OP added another piece of the puzzle:

It's not a piece of the puzzle where it will be used in the end. I just created that extra virtual scenario so I can figure out how to get it working. My Windows-VM cannot see anything through the network interface, so something is wrong on the KVM/QEMU-system. The KVM/QEMU-VM has full access to the world around it. I even use virt-manager through ssh.

---

### Post by Doug S on 2022-11-08
> **Jesper_Poulsen said:**
> I have followed your guide and while I'm using virt-manager to setup my VM I have no IPv4 connection from the guest.
I have setup the network interface as virtio and installed the support in the gueat OS (Windows 10).

 What am I missing here?I don't know. You will have to post file relevant contents and such, for us to look at/into.

---

### Post by MAFoElffen on 2022-11-08
> **Jesper_Poulsen said:**
> I'm on a DHCP'd network.
The NetPlan file I posted of mine, instead of being a dedicated NIC for the bridge (alone), is shared between the host and the virtuals, even though it has a static address for the interface, what is bridged between the virtual network and the host network, are being assigned DHCP settting from my host network's router. So the Guests using "that" bridge, I have the choice to use Static settings or assigned DHCP. The big difference is I share the physical device.


> **Jesper_Poulsen said:**
> It's not a piece of the puzzle where it will be used in the end. I just created that extra virtual scenario so I can figure out how to get it working. My Windows-VM cannot see anything through the network interface, so something is wrong on the KVM/QEMU-system. The KVM/QEMU-VM has full access to the world around it. I even use virt-manager through ssh.
It sort of begs the questions of explaining how all those pieces fit together... Not just is your virtual network, but in your host network, and how the Guest fits into the virtual scheme. Is it a nested Guest?

I do beta testing for both KVM/QEMU, and VMware vSphere Hosts. I stopped using VirtualBox, back about 6 years ago. But when I used to have to support all Virtual Host systems, including KVM, vSphere, VirtualBox, Hyper-V, Centrix / XenServer, etc. I am also a Cisco CCENT / CCNA, so I often replicate complex networking in and through my virtual network schemes, or use virtual appliances in my host network...

So I start out a bit different in my networking diagnostics when I put on my Network Administrator hat on... Is there a working NIC? Is there a physical/logical connection through from point A to point B to the first (virtual) switch or gateway... To see that, what is the network layout? Often, in my network plan, I draw out in a charting program to document to show how the pieces fit together. It you temporary give the Guest a static address, can it ping the gateway, and or the DHCP server?

Then what are the virtual switches, bridges, and physical network appliances. What does your network xml file look like? What does your NetPlan file look like? What does the xml of your KVM guest look like? What is the config of your Virtual Guest VM look like? And how does that piece fit in with your KVM Host? (Because it sounds like it might be nested...)

So yes, I see things and my mind, (which is very detail oriented), and it starts spinning through all the combinations of what "might be" and it peaks my curiosity. Please paint me a picture of what you have and what is going on... I do nested virtualizations. As you can see from the attached photo, because I am a Developer and have to do a lot of testing, my own infrastructure is a bit more complex than most people. 

I do not want to high-jack Doug's work. Providing information, and pointing out what I see from that...That will help Doug S help you.

---

