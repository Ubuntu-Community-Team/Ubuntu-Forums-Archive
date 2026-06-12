---
title: "Guests cannot boot OS on Ubuntu Server 18.04.3"
date: 2019-11-15
forum: Virtualisation
---

### Post by dragonjdw on 2019-11-15
Greetings all,

I have install Ubuntu Server 18.04.3 on a Dell 1950 with 8GB of RAM. I installed virt-manager which pulled in all the usual dependencies.

When trying to create a guest through virt-manager, the installation media (a local ISO file, in this case also Ubuntu Server 18.04.3) boots GRUB and asks about keyboard and language; and then when the kernel boots, the ramdisk loads, and the guest reboots.

I have tried this with other bootable images with the same result: kernel loads, ramdisk loads, guest reboots.

Nothing unusual/unexpected (compared to working libvirtd/qemu installations on Ubuntu desktop [non-server]) is logged in the usual places (/var/log/libvirtd/qemu/*), I have increased logging verbosity in /etc/libvirtd/libvirtd.conf with no success, etc.

Out of curiosity, I have installed Ubuntu Desktop 18.04.3 LTS on this same hardware, and have no problem getting guests running.

So, this is some problem that exists with Ubuntu Server 18.04.3, that does not exist on Ubuntu Desktop 18.04.3 LTS.

Help?

---

### Post by gardnermarquis43 on 2019-11-23
virt-manager? I'm completely new but recently installed same ubuntu version on an acer and downloaded virtualbox. I am looking to run win10 in vm, but having issues loading win10 iso OS into vm and starting machine.

---

### Post by TheFu on 2019-11-23
Sorry, I got on a roll with this response....  ignore if it isn't useful.

 gardnermarquis43 - you should start your own thread. vbox has NOTHING to do with this thread. Around here, 1 question for 1 thread is the rule. Me-too really only works if the issue has been nailed down with 50 elements and you match all 50. That pretty much NEVER happens here.

virt-manager is a GUI tool, so it needs to run under X11 from a workstation with that capability. I think only linux versions of this tool exist, but I could be wrong.

If you installed Ubuntu Server, then there isn't any GUI. That means a few things need to be setup so the client workstation can access the hypervisor server using libvirt.

On the "Server", you need ssh-server, qemu-kvm, libvirt-bin, bridge-utils packages. Probably want fail2ban too. This machine must have a static IP.  After the packages are installed, verify that the userid you will use is in the libvirtd group on the server. If that didn't happen, add it to the group.

On the "Client"/workstation, you need ssh-client, libvirt-bin, virt-manager. Verify that the userid you will use is in the libvirtd group on the client. You'll need to either use newgrp in a shell and launch virt-manager from there or logout and login again for the libvirtd group membership to be session-wide. Your choice.

Setup ssh keys from the workstation to the server so passwords are never needed again. Passwords are inconvenient for remote connections and ssh-key are both more convenient AND 1000000x more secure. Run these on the client:
```
ssh-keygen -t ed25519
ssh-copy-id -i ~/.ssh/id_ed25519.pub userid@server
```
That will be the last time you need to use a password to the "server".

The client needs to be able to find the "server" using DNS or /etc/hosts or just use the static IP for the server. If the userid is identical between the server and the client, no need to specify it for ssh connections. It will be assumed.
There is no need to use sudo or root for any virt-manager stuff. Use your normal userid.
Test the ssh connection using just the key:
```
ssh userid@server
```
You should have a terminal session on the server now.  Learning to use the ~/.ssh/config will save you lots of time. Using connection aliases for systems that you don't control or when you don't control DNS for the network is just one of the benefits. Alternate userids, non-standard ports, different ports for different users, different connection settings for different 'aliases' are all possible.  Anyone using ssh who doesn't know about this stuff should stop what they are doing NOW and learn just the trivial stuff. It will save you so much time.  The config file is used by **every** ssh application out there, so rsync, ssh, sftp, Nautilus, thunar, sshfs, x2go, rdiff-backup and 50 other tools will all honor those settings and aliases.  Ok, back to virt-manager ... 

Run virt-manager on the client, New Connection, enter the hostname or IP to the hypvisor "server" and connect. With this connection you get an overview of CPU, RAM, Network use for the hypervisor. Any created VMs will be on the left, running or not.

When creating new VMs, probably want to select NAT until you manually create a few linux bridges in a shell.  I don't know how to do that on 18.04 since netplan changed everything. In 2010, only manually created bridges worked well, so I've just always done that.

Also, probably want to avoid EFI BIOS for all guests and always use virtio for network and disk subsystems unless you have a very good reason for something else.

As for monitor and video - qxl and spice will be the fastest.  QXL drivers have to be loaded inside the guest VMs. There are setup.exe installers for Windows. Before those drivers are available, use vmvga and vnc, if you must have a GUI. Yuck.  Really, just use ssh instead.

You'll want to place the ISO files in /var/lib/libvirt/images/ to be used for installing new OSes.  This is also where file-based VM storage will happen, so might want to add a mount point for 200G or more, depending on the size of the VMs you need.
If the hostOS is configured to use LVM, then each VM can have a dedicated LV which virt-manager/libvirt will create for us.  Using LVM, you can take snapshots of a running system, then perform backups while the VM(s) continue to run.  It is fairly convenient, but having an intermediate skill with LVM is probably needed.
Remember, you are doing all the day to day management of VMs, creation, startup, shutdown, from a remote workstation over an ssh tunnel. This means you can manage your VMs safely from anywhere in the world that has ssh access to the VM host.
Console access to each VM guest is accessed through virt-manager, but there are some important limitation so this should not be the default mode used.  Lacking any other method, use ssh from the workstation to connect over the network into each guest VM.  Something like:
```
#!/bin/bash
XTERM_OPTS="-u8 -fs 16 -fa Monospace -sb -fg green -bg black"
uxterm -sb -geometry 80x25+0+0 $XTERM_OPTS -e ssh -X vpn &
```
is what I use. "vpn" is just a hostname.   Obviously, use whatever terminal and options you prefer.  Notice my ssh cmd includes X11 forwarding, so any X11/client on the remote VM can be run and a window will show up locally on my workstation provided there is a viable route between the guest and my workstation.
If you are running pure servers, no need for the -X ssh option.  Having select/paste between different VMs is very handy.  It also means you can consistently configure each guest VM.

If all the different VMs have static IPs, life will be easier.  At home, I assign static IPs to any non-portable system on the box/OS.  For laptops, I use the DHCP reservation capability of the DHCP server.  This is handy for android clients, laptops, network tv tuners, roku devices and raspberry-pis that don't have keyboards connected.

My 1st Five Minutes on a Server: [https://blog.jdpfu.com/2014/02/28/1st-five-minutes-on-a-server](https://blog.jdpfu.com/2014/02/28/1st-five-minutes-on-a-server) applies to virtual machines too.

That's what I do.  You do it your way. If you get stuck with general questions, ask away. I don't have a 18.04 hypervisor here. We stay way behind.  I bet there are at least 1000 youtube videos with step-by-step guides.

---

