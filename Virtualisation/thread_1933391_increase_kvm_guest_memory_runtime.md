---
title: "increase kvm guest memory runtime"
date: 2012-02-29
forum: Virtualisation
---

### Post by wbloos on 2012-02-29
Hi,

I am pretty new to virtualization. I have a host under my desk that is running 5 guests on kvm.
-the host (the physical server) runs ubuntu server 11.04 (natty)
-the guest (the virtual server) runs ubuntu server 10.04 (lucid)
-the client (my laptop) runs ubuntu desktop 11.10 (oneiric)
I use virt-manager ("Virtual Machine Manager") on my laptop to manage (and install) the guests.

Problem:
One guest currently needs a lot of memory, it's swappig a lot. I closed the other guests down for a while and i now want to increase the memory that this guest may use, without having to start over on the calculations.
(btw closing down guests that were already idle didn't help at all to lower the high "load" on the host system)

virt-manager offers a button for increasing that memory (click the blue "i" for "information" in the toolbar of the virtual server that you have logged in to, select the "memomy" and increase the amount).
But it didn't work for me:
"These changes will take effect after the next guest shutdown.
Details:
this function is not supported by the connection driver: virDomainSetMaxMemory

Traceback (most recent call last):
  File "/usr/share/virt-manager/virtManager/details.py", line 2305, in _change_config_helper
    func(*args)
  File "/usr/share/virt-manager/virtManager/domain.py", line 743, in hotplug_both_mem
    self.hotplug_maxmem(maxmem)
  File "/usr/share/virt-manager/virtManager/domain.py", line 729, in hotplug_maxmem
    self._backend.setMaxMemory(maxmem)
  File "/usr/lib/python2.7/dist-packages/libvirt.py", line 842, in setMaxMemory
    if ret == -1: raise libvirtError ('virDomainSetMaxMemory() failed', dom=self)
libvirtError: this function is not supported by the connection driver: virDomainSetMaxMemory"

I've read ([link]("http://www.semanticlab.net/index.php/KVM_increase_CPU_and_RAM_during_runtime")) that this should be possible with the qemu monitor, using:
```
info ballon - shows the allocated memory
balloon 256 - sets the memory to 256MB
```
But was having trouble reaching the qemu monitor to find out if this actually works.

I've been searching a lot on google and found a lot of (partially confusing) material. What's confusing is that it sometimes seems unclear on which of the 3 machines which software needs te be installed and run.
Also people will use different client software to connect to (whatever computer) and that client is usually not installed, so you also have to find out what it is, if you really need it, what package provides it, etc.
I do not need a graphical display, so VNC is not really what i need, but i would have been happy if it had worked.
I also read that accessing the qemu monitor is very much discouraged, which made the virt-manager developers disable access to it ([link]("https://bugzilla.redhat.com/show_bug.cgi?id=239532")).
Here is a quote about that discouragement in the manpage of virsh:"NOTE: Use of the following commands is strongly discouraged.  They can cause libvirt to become confused and do the wrong thing on subsequent operations. Once you have used this command, please do not report problems to the libvirt developers; the reports will be ignored.". 

Anyhow, i've found a way to issue the command to the qemu monitor now.
It doesn't seem to work, sadly. I would love to know why.

I found the solution here ([link]("http://blog.vmsplice.net/2011/03/how-to-access-qemu-monitor-through.html")).
I use following command on the *host* system (in a ssh session):
```
wbloos@dbservertje2:~$ which virsh
/usr/bin/virsh
wbloos@dbservertje2:~$ virsh qemu-monitor-command --hmp lucid-topo-conv 'info balloon'
balloon: actual=2048
wbloos@dbservertje2:~$ virsh qemu-monitor-command --hmp lucid-topo-conv 'balloon 10240'
wbloos@dbservertje2:~$ virsh qemu-monitor-command --hmp lucid-topo-conv 'info balloon'
balloon: actual=2048

```

btw the domain name is the name that you gave the virtual server.
should you have forgotten the name, you can look it up on the host with:
```
ps fax|grep kvm
```
it's the parameter "-name"

Hope this helps some people that are searching for similar stuff.
If you have any tips for me to increase the mem during runtime, please respond.

Cheers

---

### Post by akiran on 2012-03-06
Hi wbloos,

Thank you for your post, it was helpful for me.

I managed to change the current memory at runtime but not the max memory. 

I have a VM with the following configuration 

[HTML]<domain type='kvm'>
  <name>u-server-1-guest-9</name>
  <memory>4145728</memory>
  <currentMemory>3145728</currentMemory>
  <vcpu>1</vcpu>
..
<memballoon model='virtio'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x05' function='0x0'/>
    </memballoon>
  </devices>
</domain>[/HTML]With this configuration my VM starts with 3G of RAM and I can be extended to 4G.

On the Host:
```
$ sudo virsh -c qemu:///system
virsh # qemu-monitor-command --hmp u-server-1-guest-9 --cmd 'info balloon'
balloon: actual=3072
```On the VM:
```
[u-server-1-guest-9 ~]$ free -m
             total       used       free     shared    buffers     cached
Mem:          2808        343       2464          0         14        125
-/+ buffers/cache:        203       2604
Swap:          999          0        999

```On the Host:
```
virsh # qemu-monitor-command --hmp u-server-1-guest-9 --cmd 'balloon 4000'
virsh # emu-monitor-command --hmp u-server-1-guest-9 --cmd 'info balloon'
balloon: actual=4000

```On the VM:
```
[u-server-1-guest-9 ~]$ free -m
             total       used       free     shared    buffers     cached
Mem:          3736        352       3383          0         15        129
-/+ buffers/cache:        207       3528
Swap:          999          0        999
```

I hope that this post will help somebody,

This link was interested : [http://rwmj.wordpress.com/2010/07/17/virtio-balloon/](http://rwmj.wordpress.com/2010/07/17/virtio-balloon/)

Cheers

---

### Post by wbloos on 2012-03-07
ok, so that was what i should have done, high enough for max, set current to what i really want to use. 

I missed it because the virt-manager GUI doesn't offer it. It just says: "Memory (RAM): " and then a box that is showing 1024 MB, you can change it.
Would be nice if they would offer the 2 options like they do for the disk space.

I might as well set max to something absurdly high then... i'm missing the point of having such a setting at all. Or is there an effect of <memory> other than that you can't raise <currentMemory> above it??

I'll look into editting that definition file manually. Thanks.
Maybe if the max allows it, users can just use the GUI to increase the memory. I'll give that a try.

Cheers!

---

