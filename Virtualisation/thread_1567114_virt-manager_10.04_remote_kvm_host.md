---
title: "virt-manager 10.04 remote kvm host"
date: 2010-09-03
forum: Virtualisation
---

### Post by aidanewen on 2010-09-03
I have several virtual machines running on my 10.04 server. I generally administer them using virsh over ssh. However when I create new VM (as I'm trying to do now), I use virt-manager. This is so that I can work through the installation steps from my vm operating system iso image.

Up till now virt-manager has had no trouble connecting to the qemu host on my server. Suddenly virt-manager won't connect to my host. it asks for the root password of the server (3 times), then tells me:
[INDENT]Unable to open a connection to the libvirt management daemon.

Libvirt URI is: qemu+ssh://root@192.168.1.33/system

Verify that:
 - The 'libvirt-bin' package is installed
 - The 'libvirtd' daemon has been started
 - That you have access to '/var/run/libvirt/libvirt-sock'
[/INDENT][INDENT]Details:
[/INDENT][INDENT]Unable to open connection to hypervisor URI 'qemu+ssh://root@192.168.1.33/system':
cannot recv data: Connection reset by peer
Traceback (most recent call last):
  File "/usr/share/virt-manager/virtManager/connection.py", line 896, in _try_open
    None], flags)
  File "/usr/lib/python2.6/dist-packages/libvirt.py", line 111, in openAuth
    if ret is None:raise libvirtError('virConnectOpenAuth() failed')
libvirtError: cannot recv data: Connection reset by peer

Maybe you need to install ssh-askpass in order to authenticate.
[/INDENT]libvirt-bin is installed libvirtd seems to be running fine and I have access to /var/run/libvirt/libvirt-sock.

I'm not sure what's changed (I suppose I've run apt-get upgrade on both the server the the machine running virt-manager).

Any suggestions would be greatly appreciated.

---

### Post by aidanewen on 2010-09-06
[FONT=&quot]Don't know what the problem with virtual manager was but have managed to get through the installation process using virt-viewer and logging in as a user rather than root. Something like:
 
 [/FONT]
  [FONT=&quot]virt-viewer -c qemu+ssh://user@192.168.1.11/system guestVM

Even then there seemed to be some glitches as it only let me in on my second password attempt (I repeated the process and this was always the case).[/FONT]

---

