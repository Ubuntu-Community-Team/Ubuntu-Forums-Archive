---
title: "virsh kvm libvert migrate problems"
date: 2009-05-07
forum: Server Platforms
---

### Post by thesheff17 on 2009-05-07
I'm trying to migrate from one virtual machine to another using the virsh command.  I have two machines running ubuntu 9.04 with the KVM stuff installed.  When I try to do the migrate command I get this:

virsh # migrate ubuntuTest qemu+ssh://vmserver06.ttr/system
error: operation failed: failed to parse XML

I have also tried to migrate it through the virt-manager which said that the current version in the ubuntu repository is out of date and does nothing when I try to migrate the server.  It says it has been fixed in the next release 0.7.0.

So I downloaded it compiled from source and now I get this:

Error migrating domain: invalid argument in only tcp URIs are supported for KVM migrations.
Traceback (most recent call last):
  File "/usr/local/share/virt-manager/virtManager/engine.py", line 556, in migrate_domain
    vm.migrate(destconn)
  File "/usr/local/share/virt-manager/virtManager/domain.py", line 1342, in migrate
    self.vm.migrate(self.connection.vmm, flags, None, dictcon.get_short_hostname(), 0)
  File "/usr/lib/python2.6/dist-packages/libvirt.py", line 378, in migrate
    if ret is None:raise libvirtError('virDomainMigrate() failed', dom=self)
libvirtError: invalid argument in only tcp URIs are supported for KVM migrations


Has anyone been able to migrate live virtual machines from one server to another with kvm/libvert/virsh?


***ADDED May 8***

I received a message on the mail list that I need to have shared storage between the devices.  So now I have this:
1) storage01
2) vmserver05
3) vmserver06

storage01 one is sharing out /root/vm/ directory through NFS.

/root/vm from storage01 is mounted at /root/vm on both vmserver05 and 06.

I have created a kvm host on vmserver05 and when I do:

 migrate --live ubuntuTest qemu+ssh://vmserver06/system
error: operation failed: failed to parse XML

---

### Post by Achlervor on 2009-05-12
Basically I am doing the same thing and it does not work with me either, however the behavior is different.

I have two Ubuntu 9.04 machines, similar hardware (Tenovo Thinkpads with Core2Duo).

Initially I had some problems with vmbuilder, it complained about unknown OS type. The reason was that virtualization was disabled in the BIOS. The error message could have been more descriptive here... well, in the end I had it working.

What I am trying to do now is migration. I would already be happy if "cold" migration worked, but live migration would of course be better.

In virt-manager the "migrate" option in the menu seems to do nothing at all.

In virsh I do:
```

virsh # migrate <vm_name> qemu+ssh://<username>@<some host>:/system
Fehler: Unknown failure
```

The result is always the same, wether I do --live (while the VM is running) or not. I have also tried putting the disc image onto an NFS share which is mounted on the same path on both systems - no success.

---

### Post by Achlervor on 2009-05-13
In the meantime I tried doing the same thing directly with KVM and it works without problems.

Again I put the HDD image file onto an NFS share which was mounted on both hosts. On host **A** I started KVM simply as 

```
kvm <image file>
```

In the resulting qemu window the qemu monitor console is accessible on CTRL-ALT-2 (which does not work i.e. from virt-manager).

Everything else is descibed here:
[http://www.linux-kvm.org/page/Migration#User_Interface]("http://www.linux-kvm.org/page/Migration#User_Interface")

The problem is that right now I don't see an easy way to automate migration (i.e. I don't know how to inject commands into qemu from a script on the host machine).

I also find it strange that this does not work from virsh. As far as I understand it, virsh is only a wrapper for convenience and should internally do the same thing, right?

---

### Post by thesheff17 on 2009-06-08
Sorry I was not getting emails when this thread was being updated.  Are you able to migrate from one server to another?  Did it require NFS share?  The problem is that I'm running out of hardware to test on because things are going to production so quickly which is out of my control.  Let me know any findings and when I have more hardware I will def test.

---

### Post by thesheff17 on 2009-11-05
bump....I haven't tried this in a long time and going to see if works with the newest Ubuntu 9.10 if I have time.  Has anyone else been able to migrate live kvm machines while they where running.  Did it require a shared storage unit?  

Let me know the commands you used or did you use virt-manager.  

For now my fix for is that I just have redundancy throughout the entire infrastructure.  So I can easily shutdown a machine without affecting anything.  Once the machine is off I scp the machine and the xml file to the new ubuntu 9.04 virtual machine server and start it up through virsh.

---

### Post by thesheff17 on 2010-09-02
After extensively testing this again with the new version of Ubuntu 10.04 I can say this feature is very defective.  I have tried this time with 3 virtual machine servers all mount to the same NFS share.

The first problem I ran into is I bridged to networks br0 and br1 and virsh migrate --live qemu+ssh://dns/system won't ever migrate over a br1 adapter.  I tried to bind libvirt-bin directly to that DNS name and IP with no luck.  To fix the above I basically rebooted and swapped br0 w/ br1 because I wanted to migrate over the private network.

Second thing I ran into is that I had to hard code DNS names of each server in the /etc/hosts files. virsh should not care about DNS names and just resolve that IP.  I'm not sure why that is so hard.  Most of the time I like to test just passing IP.

After that I finally got it to migrate from one to another but on the source the virtual machine is still there and status is shut off.  Is this normal operation?  I would prefer for the whole machine to disappear on the source.

Another problem I ran into if virsh migrate fails the virtual machine will not be able to migrate to the machines I do have working.  Also I having long waits or hangs while doing virsh list --all and virsh destroy vm080.  

virsh # destroy vm080
error: Failed to destroy domain vm080
error: Timed out during operation: cannot acquire state change lock

I can ssh into these boxes and then shutdown them now down but I need virsh destroy vm to work.

Maybe people are having better luck with eucalyptus and UEC.  So for the time being I'm just going to keep using virsh on local disk and not on a NFS share.  Hopefully I can get some more hardware to test other things but I need this stuff for production.

One thing though that I have come across is vmbuilder command.  This will create virtual machines basically in 3-4 min.  

I love this command and created a python wrapper for it. 
prerequisites:
1) Local ubuntu mirror
2) boot.sh script for post install configuration
3) vmbuilder.partition

In order to use --tmpfs=- you need to download the latest build: [https://launchpad.net/~vmbuilder/+archive/daily/+packages](https://launchpad.net/~vmbuilder/+archive/daily/+packages)

Everything is under GNU so use at your own risk. [http://pastebin.com/QdpGQA99](http://pastebin.com/QdpGQA99)

Also if someone could rename the thread to libvirt and libvert I never noticed that.

---

