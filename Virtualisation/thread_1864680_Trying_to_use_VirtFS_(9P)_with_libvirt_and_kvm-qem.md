---
title: "Trying to use VirtFS (9P) with libvirt and kvm-qemu in 11.10"
date: 2011-10-19
forum: Virtualisation
---

### Post by evlist on 2011-10-19
I am trying to use virtual filesystems with kvm-qemu and host and guest running Ubuntu 11.10.

Following [http://wiki.qemu.org/Documentation/9psetup]("http://wiki.qemu.org/Documentation/9psetup") my libvirt config includes:

```
  <devices>
    <emulator>/usr/bin/kvm</emulator>
    <disk type='file' device='disk'>
      <driver name='qemu' type='qcow2'/>
      <source file='/ext/vms/samba-ldap-rg.img'/>
      <target dev='hda' bus='ide'/>
      <address type='drive' controller='0' bus='0' unit='0'/>
    </disk>
    <controller type='ide' index='0'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x01' function='0x1'/>
    </controller>
    <filesystem type='mount' accessmode='passthrough'>
      <source dir='/home'/>
      <target dir='home'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x05' function='0x0'/>
    </filesystem>
 ...
```

The guest machine has been created using vmbuilder and I have installed linux-image-extra-virtual to get a 9p kernel modules but I haven't found a way to mount this filesystem.

When I try "mount  -t 9p -otrans=virtio,version=9p2000.L  home /media/home/" I get an error "unknown filesystem type '9p'"

Thinking that I might miss a proper mount command, I have installed 9mount from lucid (the package has been withdrawn in oneiric as orphaned and non used...) and the command "9mount 'virtio!home' /media/home/" gives me an error "mount: No such device".

I don't see any error in the logs.

What have I missed?

Is there another way to share a host repository with the guests? Another package to install?

Thanks,

Eric

---

### Post by PleaseJump on 2011-10-25
Hi Evlist,

I'm keen to get this going as well. If you have a look at the bug report below it states that you might need package libattr1-dev installed:
[https://bugs.launchpad.net/ubuntu/+source/qemu-kvm/+bug/782973](https://bugs.launchpad.net/ubuntu/+source/qemu-kvm/+bug/782973)

I've just tried to install qemu-kvm-0.15 from:
[https://launchpad.net/~bderzhavets/+archive/qemu-git](https://launchpad.net/~bderzhavets/+archive/qemu-git)
But that isn't letting the VM start after I attempt to create the directory in Virt-Manager which the qemu-kvm 14.1 was.

So I'm going to purge the bderzhavets packages and attempt to just install the libattr1 and see if that gets me there.

---

### Post by PleaseJump on 2011-10-27
So I got this working. 

GUEST VM - ubuntu 11.10 (3.0.0-12-generic) 
kernel modules - 9p, 9pnet and 9pnet_virtio (I did not manual install these, they have been available in the kernel for a while now, I beleive)

KVM HOST - ubuntu 11.10 (3.0.0-12-server) 

I used virt-manager 0.9.0 to add the 9p file system. But it ends up pretty much the same as what you had (I'm sure passthrough would work as well):

```
<filesystem type='mount' accessmode='[COLOR="Red"]squash[/COLOR]'>
      <source dir='/home/share'/>
      <target dir='[COLOR="Red"]/[/COLOR]home'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x05' function='0x0'/>
```

I mounted it with:

```
mount -t 9p -otrans=virtio,version=9p2000.L /home /home/media/
```

After that the guest should have in dmesg:

```
Installing v9fs 9p2000 file system support
```

Now I did have an issues here the filesystem mounted correctly but I could not access it. It turns out that apparmor on the host was blocking it. In the host syslog/dmesg I had an apparmor denied:

```
[88861.918211] type=1400 audit(1319641053.407:221): apparmor="DENIED" operation="open" parent=1 profile="libvirt-XXXXX-f3e7-2202-36f5-15645882f739" name="/home/media/" pid=8902 comm="kvm" requested_mask="r" denied_mask="r" fsuid=102 ouid=0

```

I tried adding to /etc/apparmor.d/abstractions/libvirt-qemu 

```
/home/media/ rw,
/home/media/** rw,
```

but in the end to get it working I did:

```

aa-complain /etc/apparmor.d/libvirt/libvirt-XXXX-f3e7-2202-36f5-15645882f739
```

If anyone can correct me on the way to get apparmor to correctly allow this, please do.

---

### Post by evlist on 2011-10-30
Hi PleaseJump,

I needed (or thought I needed ([http://lists.digium.com/pipermail/asterisk-users/2011-October/267423.html]("http://lists.digium.com/pipermail/asterisk-users/2011-October/267423.html")) USB 2.0 support and installed another Boris Derzhavets' ppa ([https://launchpad.net/~bderzhavets/+archive/seabios163]("https://launchpad.net/~bderzhavets/+archive/seabios163")) and it appears that his version of qemu has been compiled without VirtFS support meaning that I can no longer test your solution right now but I'll try to do it as soon as possible...

Many thanks for these detailed explanations!

Eric

---

### Post by evlist on 2011-10-31
PleaseJump,

Boris Derzhavets has fixed his ppa so that we can start domains with VirtFS filesystems but that didn't fix the issue I have.

A difference with your configuration is that my guest is running a 3.0.0-12-virtual kernel.

This kernel included the 9p modules:

```
vdv@samba-ldap-rg:~$ sudo find /lib -name "*9p*"
/lib/modules/3.0.0-12-virtual/kernel/net/9p
/lib/modules/3.0.0-12-virtual/kernel/net/9p/9pnet_virtio.ko
/lib/modules/3.0.0-12-virtual/kernel/net/9p/9pnet.ko
/lib/modules/3.0.0-12-virtual/kernel/net/9p/9pnet_rdma.ko
/lib/modules/3.0.0-12-virtual/kernel/fs/9p
/lib/modules/3.0.0-12-virtual/kernel/fs/9p/9p.ko

```

But it refused to load them:

```
vdv@samba-ldap-rg:~$ sudo modprobe 9p
FATAL: Module 9p not found.

```

A grep in /lib/modules/3.0.0-12-virtual/modules.dep showed that they were missed here.

I run depmod and was able to mount the 9p filesystem (and ran into the same issue that you has with apparmor that the command you gave fixed fine).

So, the root cause of my issues is probably a missing "depmod" in the post install script of the linux-image-extra-virtual package that installed the 9p modules in my *-virtual kernel!

Thanks for your help.

Eric

---

### Post by dbaxps on 2011-11-04
It's fixed now/ VirtFS support for 0.15.1 . 

View Qemu-kvm 0.15.1 & Spice USB Redirection support for Ubuntu Oneiric
[https://launchpad.net/~bderzhavets/+archive/0151-usbredir](https://launchpad.net/~bderzhavets/+archive/0151-usbredir)

VirtFS support for 0.15.0. View Qemu&Spice USB Redirection with back ported Libvirt 0.9.6 , new seabios 1.6.3 for Ubuntu Oneiric
[https://launchpad.net/~bderzhavets/+archive/seabios163](https://launchpad.net/~bderzhavets/+archive/seabios163)

---

### Post by bderzhavets on 2011-11-13
[QUOTE=evlist;11413152]PleaseJump,
[http://ubuntuforums.org/register.php?a=act&u=1493268&i=e81b5b1ee06b64bb00e79cebad205b6c8a1089b8](http://ubuntuforums.org/register.php?a=act&u=1493268&i=e81b5b1ee06b64bb00e79cebad205b6c8a1089b8)
```
vdv@samba-ldap-rg:~$ sudo modprobe 9p
FATAL: Module 9p not found.

```A grep in /lib/modules/3.0.0-12-virtual/modules.dep showed that they were missed here.

I run depmod and was able to mount the 9p filesystem (and ran into the same issue that you has with apparmor that the command you gave fixed fine).

So, the root cause of my issues is probably a missing "depmod" in the post install script of the linux-image-extra-virtual package that installed the 9p modules in my *-virtual kern


Yes, it's kernel issue ( not connected to qemu-kvm)
On my system

boris@boris-System-Product-P5Q3:~$ uname -a
Linux boris-System-Product-P5Q3 3.1.0-030100-generic #201110241006 SMP Mon Oct 24 14:07:10 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
boris@boris-System-Product-P5Q3:~$ sudo modprobe 9p
[sudo] password for boris: 
boris@boris-System-Product-P5Q3:~$ lsmod | grep 9p
9p                     48291  0 
9pnet                  58085  1 9p

---

### Post by jebus_beler on 2011-11-13
> **evlist said:**
> 
A difference with your configuration is that my guest is running a 3.0.0-12-virtual kernel.


Hi evlist,

I'm trying to use 9p filesystem access in a VM build using ubuntu-vm-builder with the same kernal as you but I even find the 9p modules.  Did you include any additional packages in order to have them included?  

thanks

---

### Post by jebus_beler on 2011-11-21
Turns out the answer was already in the first post so for reference here it is:

> **evlist said:**
> The guest machine has been created using vmbuilder and I have installed** linux-image-extra-virtual to get a 9p kernel modules** but I haven't found a way to mount this filesystem.

Guess I should read more carefully :-)

---

