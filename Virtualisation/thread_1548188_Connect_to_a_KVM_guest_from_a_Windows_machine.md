---
title: "Connect to a KVM guest from a Windows machine"
date: 2010-08-07
forum: Virtualisation
---

### Post by ResilientBiscuit on 2010-08-07
I got Ubuntu server set up with KVM. I am trying to figure out how to actually get a Windows guest installed without using a GUI on the server machine. Ideally I would like to be able to view the guest using a machine running Windows 7. Is there some software that will allow me to connect to the machine? I know I can do it with remote desktop after it is installed but I am not sure how to handle it before that. Thanks!

---

### Post by tapas_mishra on 2010-08-07
You need putty

---

### Post by ResilientBiscuit on 2010-08-08
I got putty. I assume I need to combine that with some other program to actually see the screen of the guest machine because its more than just a console, right?

Basically how do I install windows on Ubuntu server with no GUI installed.

---

### Post by tapas_mishra on 2010-08-08
Well  I will suggest use a Linux Machine for Remote Connection since that will help you to do a lot of things and then try the following I have done what you are doing many times but I did not used Windows installation I installed Linux remotely on a computer which did not had GUI.

But in your case in Windows you can install CygWin I have not tried it myself 
Here is what I will suggest to do what you are trying to.

Get a Linux machine such as your laptop or if you are using  Windows then use CygWin on it.

```

Step 1
dd if=/dev/cdrom of=/home/user/windws.iso bs=1024 count=1

```

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

### Post by ResilientBiscuit on 2010-08-08
Thanks tapas_mishra,
with your instructions I got it almost there.

Then I just had to add the line:


<graphics type='vnc' port='5900' autoport='no' listen='192.168.1.21' keymap='en-us'/>

to the xml configuration file for my guest computer. At this point I used TightVNC to connect to the guest.

It feels a bit clunky though. 192.168.1.21 is the address of the host so I am not sure how this would end up working if I had more than one guest running. 

Thanks!

---

