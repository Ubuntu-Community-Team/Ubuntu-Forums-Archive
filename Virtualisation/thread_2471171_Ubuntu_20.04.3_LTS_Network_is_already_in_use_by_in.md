---
title: "Ubuntu 20.04.3 LTS Network is already in use by interface enp3s4f0"
date: 2022-01-22
forum: Virtualisation
---

### Post by Phill_Hopkins on 2022-01-22
Hi everyone.
   
  I have been running my home production server on Ubuntu 18.04 LTS for a while now and have just rebuilt it using Ubuntu 20.04.3 LTS. For virtualisation I was previously using Virtualbox which I managed through phpVirtualbox, I have now decided to utilise KVM for my VM needs but have hit a snag while setting up.
   
  I have installed KVM and all of the dependencies, also installed Cockpit but didn’t realise that managing Windows VM’s is limited, so decided to carry on with my learning and use the CLI instead.
   
  I had successfully created a bridge br0, bridge-slave to interface enp3s4f0 and configured IP, Gateway and DNS using nmcli commands. Then successfully created my first KVM VM using virt-install and powered on. I wasn’t able to connect to the VM using RDP from my desktop PC and on running ip a found the IP addresses were not what I thought I’d configured. So tried again using the nmcli commands to no effect.
   
  I then decided to remove the bridge and slave-bridge so that I could start again but this time set the bridge up using virsh commands. I created a br0.xml file to create a bridge using br0 again, contents of the xml file below.
   
  ```
<network>

    <name>br0</name>
    <forward mode='nat'>
      <nat>
        <port start='1024' end='65535'/>
      </nat>
    </forward>
    <bridge name='br0' stp='on' delay='0'/>
    <ip address='192.168.3.187' netmask='255.255.255.0'>
    </ip>
  </network>

```   
  Then ran:
  ```
sudo virsh net-define br0.xml

  sudo virsh net-start br0

```   
  However when I started br0 I get the below error message:
  error: Failed to start network br0
  error: internal error: Network is already in use by interface enp3s4f0
   
  When I run ip a there are no bridge interfaces listed that suggest anything is slaved to enp3s4f0. it feels like somehow there is the previous br0 bridge I created still slaved to enp3s4f0.
   
  Can anyone offer some advice as to how I can rectify this issue please?
   
  Thanks
  Phill

---

### Post by Phill_Hopkins on 2022-01-23
Hi, quick update and to close out this query.

I use netplan to configure network connections with networkd as the renderer, all I needed was to change the renderer to NetworkManager and the connections then became manageable.

Problem solved :o

---

### Post by ajgreeny on 2022-01-23
Great news! 

Please mark as **SOLVED** from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to other users searching the forum.

---

### Post by MAFoElffen on 2022-01-23
??? But you could have done that with networkd also... And your assumption of creating a netwrk device Bridge "br0" using NAT is not what you said you want to do...

'NAT' or Network Address Translation, translates the addresses with a tag internally to the packet, used on the Virtual network side, within the KVM Virtual Network... Your Guests have access to the outside world, but the outside world cannot address the specific guest. On the outside of the VM Host, it the VM uses the Host's outside IP address,

That is not what a br0 bridge is, where you bridge between networks, (that is what a network bridge does, spans between networks that have that same network ID) so that your VM's can use an address that is on the same network as your Host's network. Then computers on your host network can address your VM. Isn't that what you are trying to do?

If you are using NAT, then you gain nothing over the capabilities you have with the 'default' configured VSwitch that came with KVM. Just saying.
```

mafoelffen@Mikes-ThinkPad-T520:~$ sudo ovs-vsctl show
209a93f9-151f-44aa-b248-1bc5658bd858
    Bridge br0
        Port br0
            Interface br0
                type: internal
        Port enp0s25
            Interface enp0s25
    ovs_version: "2.13.3"

mafoelffen@Mikes-ThinkPad-T520:~$ sudo virsh net-list
 Name               State    Autostart   Persistent
-----------------------------------------------------
 default            active   yes         yes
 Isolated_Net_192   active   yes         yes
 NAT_Network_172    active   yes         yes
 Routed_Net_172     active   yes         yes

```
A traditional 'br0' bridge install takes over exclusive control of a network device, that can no longer be used by the host... OpenVSwitch is a bridge that can be shared between the host and virtual network on a single Network device.

---

