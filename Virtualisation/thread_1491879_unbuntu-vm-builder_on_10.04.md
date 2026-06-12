---
title: "unbuntu-vm-builder on 10.04"
date: 2010-05-24
forum: Virtualisation
---

### Post by aidanewen on 2010-05-24
Hi,

I'm trying to create a Hardy Virtual Machine on my 10.04 server. I'm following the ubuntu guide at [https://help.ubuntu.com/community/KVM](https://help.ubuntu.com/community/KVM). I've edited my /etc/network/interfaces file and my libvirtxml.tmpl but I'm having problem with ubuntu-vm-builder. 

I've tried the following command a couple of times (I thought I might have made a typo the first time):
[INDENT]sudo ubuntu-vm-builder kvm hardy \
--arch amd64 \
--mem 2048 \
--rootsize 20480 \
--swapsize 4096 \
--kernel-flavour server \
--hostname mail \
--mirror [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) \
--components main,universe,restricted \
--name Aidan Ewen \
--user aids \
--pass ********* \
--ip 192.168.1.33 \
--dns 192.168.1.33 \
--libvirt qemu:///system
[/INDENT]
I'm getting a lot of output on the terminal (most of which means nothing to me), and eventually the lines:
[INDENT]Attribute Error: 'Hardy' Object has no attibute 'destdir'
--ip: command not found
[/INDENT]When i try to define my machine with virsh it says there's not /etc/libvirt/qemu/newvm.xml file.

I can't work out where I'm going wrong. Any ideas?

I'm also concerned that I might be creating non-working vm's on my disks. I was wondering if anyone can tell me where ubuntu-vm-builder does it's thing so I can check (will there be large files scattered around my 10.04 system or will ubuntu-vm-builder put them all in one place).

---

### Post by tapas_mishra on 2010-05-24
Hi,I today only tried for the first time.I will tell you not to do from command line.
Suppose the server where you have to create a VM is A and your laptop is where you can remotely connect to it B.
Connect to A as 
```

ssh root@A -X

```
The steps mentioned on this blog 
[http://www.ideyatech.com/2010/05/virtualization-with-ubuntu-1004-lucid-lynx/](http://www.ideyatech.com/2010/05/virtualization-with-ubuntu-1004-lucid-lynx/)
are not exactly as they say but it will help you.
Install on server in our case A if following are not present
```

sudo apt-get install kvm libvirt-bin virt-manager

```
I am assuming you have root access on A so step 2 on that blog is not needed.Make sure bridge-utils is installed
```

sudo apt-get install bridge-utils  
```
then if you know how to configure bridge then proceed ahead.
```

sudo /etc/init.d/networking restart 

```
In case you do not know what a bridge is I am pasting my sample 
/etc/network/interfaces file
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth2
iface eth2 inet manual

auto br0
iface br0 inet static
        address 192.1.100.14
        netmask 255.255.255.0
        network 192.1.100.0
        broadcast 192.1.100.255
        gateway 192.1.100.100
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 192.168.1.1
        dns-search example.domain.com
        bridge_ports eth2
        bridge_fd 9
        bridge_hello 2
        bridge_maxage 12
        bridge_stp off


```

You can copy paste the same and replace the entries for your network.

Now you are already logged on to A as root with 
ssh root@A -X
do not forget -X at the end of SSH.
Type virt-manager
a display GUI should  open on your laptop.If it does not go back and read again from the start you have done some mistake.

Now on that GUI I have forgotten how I did for the 
first time but you have to select an option to connect to localhost .
Then in some other navigation tab you will also see an option for QEMU.
Keep a CD inserted in CDROM you will be able install from the CDROM.
Step 7 on the above blog may be a bit difficult for you so just follow what ever I mentioned here.
I have done a lot of experiments on command line and after that I am giving you this suggestion take the easy path.
Once it works you always can go back to command line if you wish to learn.


After installation of your Guest VM
to be able to Guest VMs use network on A in /etc/sysctl.conf you need to change 
some value 
please read this thread for more information
[http://ubuntuforums.org/showthread.php?t=973756](http://ubuntuforums.org/showthread.php?t=973756)

---

### Post by aidanewen on 2010-06-21
That's great. All up and running. Thanks for your help.

---

### Post by tapas_mishra on 2010-06-21
Glad that I could help.

---

