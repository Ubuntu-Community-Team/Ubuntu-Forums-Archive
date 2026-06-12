---
title: "Getting macvtap devices working on Ubuntu KVM -- cheat sheet"
date: 2011-02-14
forum: Server Platforms
---

### Post by Malor on 2011-02-14
Posted this over on Ars Technica, but figured you guys might be interested too.  On Ars, I spoiler-tagged the kernel build section, but I don't think I can do that here, so I'm sorry this is so long.

Recently, KVM added a new networking feature, "macvtap", which is a method of reducing overhead in virtualized guests for accessing the network.  Regular QEMU KVM sets up a network bridge, and then attaches virtual ethernet devices to it.  This puts a lot of load on the network stack, as each and every frame has to hit the bridge, run through ebtables, get copied to the internal bridge, get copied to every virtual device, and then run through the normal input/analysis/process stack on every guest, even if the packet wasn't intended for them.  That's a heck of a lot of work on a per-frame basis. 

Macvtap devices don't run through a bridge... they appear almost like a hardware alias on an adapter.  They have unique MAC addresses, and while the main interface does have to go into promiscuous mode to see the packets aimed at its VTAP devices, there's not a lot of work involved in transferring packets to guests, and the work seems to be on a per-guest basis.   I saw this mentioned in another thread on virtualization, and that got me curious, and I've just brought up an experimental box to do some light-duty testing with at home.

This took a fair bit of work, so I figured I'd share what I did.  I make no guarantee of fitness or acceptable performance, but at least it's running correctly and no longer spitting errors all over the system log.  Basic functionality requires a custom kernel, as Ubuntu does not compile macvtap into their shipping versions.  And suppressing all libvirt errors seems to require at least one package from Natty, iptables.  Any machine you bring up this way will take more update attention than normal.... until the Ubuntu team starts including the macvtap module in their builds, you will have to compile all your own kernel updates.

This is what I actually did, and why: you can mix and match as you see fit.
[list=1][*]Updated /etc/apt/sources.list to 'natty' from 'maverick', ran an aptitude update
[*]cd /usr/src, installed kernel-source-2.6.38.  I went for .38 from Natty, as opposed to .35 in Maverick, because .38 also adds support for nested page tables on i-series CPUs and higher, which substantially boosts virtualization performance.  You only need .35 for macvtap support, and that's probably okay if you're on Core2 and earlier.  
[*]Installed iptables
[*]Installed qemu-kvm.  I don't know that this is necessary, but it seems smart to keep KVM and the kernel in sync.  This is probably also needed for NPT support.
[*]Got source for libvirt.
[*]Set /etc/apt/sources.list back to maverick, ran aptitude update.
[*]Compiled a custom 2.6.38 kernel.  Doing this on Debian/Ubuntu is pretty involved, and I didn't find any online cheat sheets that worked 100% correctly.  
[list=A]
[*]I compile kernels as root, so I'm ignoring all the 'fakeroot' crap.  If you want to compile as a user, just prepend any call to the 'debian/rules' script with 'fakeroot'. 
[*]Extract the source; cd /usr/src, tar -jxf linux-source-2.6.38.tar.bz2.  (the actual bz2 is in the directory already, with a symlink back up here; I have no idea why they do that, as you still need to extract it from the parent directory.)
[*]```
aptitude install fakeroot build-essential install crash kexec-tools makedumpfile kernel-wedge \
devscripts libncurses5 libncurses5-dev libelf-dev libdw-dev asciidoc binutils-dev
cd linux-source-2.6.38
cp debian.master/config/amd64/config.flavour.server debian.master/config/amd64/config.flavour.yourname
debian/rules clean
debian/rules updateconfigs
debian/rules editconfigs
```
[*]It will prompt you through all the potential configs; say Y when you see yours, go into devices/network devices, and tag the macvtap device near the top of the list.  If you don't get a prompt for your kernel version, you probably failed to include the extraneous U in 'flavour', which bit me several times.
[*]```
cd debian.master/abi/2.6.38-2.29/amd64 (this line will change until the natty kernel version settles)
cp server yourname
cp server.modules yourname.modules
cd ../../../..
```
[*]Edit debian.master/etc/getabis, find 'getall amd64 generic server virtual', and add 'yourname' to the end.
[*]Edit debian.master/rules.d/amd64.mk, add yourname to the "flavours" line.  
[*]```
cp debian.master/control.d/vars.server debian.master/control.d/vars.yourname
```
[*]You can edit that vars file to add notes, if you care.
[*]```
debian/rules binary-indep DEBIAN_KERNEL_JOBS=8
debian/rules binary-perarch DEBIAN_KERNEL_JOBS=8
(if you get an error almost immediately, try mkdir debian/stamps, and rerun it, should fix it.)
debian/rules binary-yourname DEBIAN_KERNEL_JOBS=8

(substitute your number of processors for 8 in those lines)
```
[*]That should give you all the kernel packages, headers, and tools you need in /usr/src.  Note that it regenerates a new kernel-source deb, which you may want to delete. Then just dpkg --install *deb in that directory.
[*]Reboot, check uname, should be golden.[/list]
[*]Compiled a custom libvirt, adding "--with-secdriver-apparmor" to the debian/rules file.  This part isn't strictly necessary, but in theory, it's supposed to protect guests from each other, rather than just from the host.  Whether or not you use that feature, you want to custom-compile libvirt, because the Natty version will pull in a new version of libapparmor.  This strikes me as unwise unless you move up to the full Natty version of apparmor. 
[*]Installed the new kernel and libvirt, rebooted.
[*]Apparmor is not configured for vtap devices, and it will completely prevent networking from running.
[list=A][*]To the file /etc/apparmor.d/usr.lib.libvirt.virt-aa-helper, added a line "/dev/dm* r,".
[*]To the file /etc/apparmor.d/abstractions/libvirt-qemu, added a line "/dev/tap* rw,"[/list]
Note that this may not be the ideal configuration; you'd probably want to lock individual machines to specific vtap devices.  But it looks like that would take hacking on the libvirt code, because it would need to be built on a per-launch basis, since the tap devices change from run to run.
[*]Added a line to /etc/libvirt/qemu.conf, 'security_driver = "apparmor"' to support the --with-secdriver-apparmor compile-time option.
[*]Installed cgroup-bin to support libvirt's ability to use cgroups for resource limitation.  Don't know anything about this, but I was seeing lots of complaining in the logs, and this fixes it.  Note that cgroup-bin hung up for me for a LONG time during installation, but it did eventually complete.  Be patient.
[*]Because cgroups had installed so very slowly, rebooted the box.  It came up promptly; may not have been at all necessary.
[*]Installed and ran virt-manager over remote X to define my first virtual machine.  Virt-manager has no support for macvtap yet in Ubuntu, so I had to initially set the adapter as attached to the 'default' virbr0 network. 
[*]Copied /etc/libvirt/qemu/guestname.xml to /root/guestname.xml.orig, for backup.  (substitute your own name, obviously). 
[*]Copied guestname.xml.orig to guestname.xml.vtap for editing.
[*]Changed the network section to look like this:
```
<interface type='direct'>
     <source dev='eth0' mode='bridge'/>
     <mac address='52:54:xx:xx:xx:xx'/>
     <model type='virtio'/>
     <address type='pci' domain='0x0000' bus='0x00' slot='0x03' function='0x0'/>
</interface>
```
There are three "types" you can choose: "vesa", "bridge", or "private".  These control whether guests can communicate with one another over the main network.  Vesa requires a VESA-capable switch, very rare.  These switches can do 'hairpin turns', where they send a packet right back out the interface it came in on.   "bridge" handles the hairpin turn locally, likely with some performance impact.  "private" simply refuses to allow one guest to communicate with another, period.  Note that the host does not seem to be able to communicate directly with guests in "bridge" mode -- guests can see each other, but packets simply don't move between host and guests.  You would likely need to build a second, private bridged network for that.  A VESA switch probably would also allow guest->host communication.
[*]Shutdown the guest with virsh, undefined it, and redefined it from the XML; virsh shutdown guestname; virsh undefine guestname; virsh define guestname.xml.vtap.  Undefine may not be necessary, I was doing it for completeness.  
[*]Removed the network bridge; virsh net-destroy default; virsh net-undefine default.  This gets rid of the virbr0 interface and that pesky dnsmasq process.
[*]Ran a tail on the /var/log/messages file, and issued virsh start guestname.  Saw a message from apparmor about a profile_load for that machine's UUID.  No other error messages.
[*]Because I was converting existing images, I had to log in with the VNC console in virt-manager, and adjust ethernet devices.  When I was figuring all this out, my udev devices were changing constantly, and I was up to eth5 on one guest.  My guests are Debian, so I logged into the machines, ran /etc/init.d/udev stop, and edited /etc/udev/rules.d/70-persistent-net-rules, removing all the lines below the initial header.  Then I rebooted the guest.  Virtual devices came up nicely as eth0 in all cases. [/list]
Voila, working macvtap devices in Ubuntu.  To make further machines, I suggest using your initial guestname.xml.vtap file as a template.  Copy and edit that file, and then provision new machines with virsh.  Use virt-manager just for the remote console.

---

