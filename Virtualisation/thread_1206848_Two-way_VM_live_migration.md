---
title: "Two-way VM live migration?"
date: 2009-07-07
forum: Virtualisation
---

### Post by Z. Y. LIU on 2009-07-07
Greetings...

I am running ubuntu 9.04, with kvm and libvirt-bin, etc.  Using virsh, I can live-migrate a VM from host1 to host2.  It works very well.  My question is, can I migrate the VM back from host2 to host1?  Below are detailed info.

Specifically, suppose the VM is VM4.  VM4, a Linux guest OS, was built on host1.  

Now on host1, I start virsh:

      virsh 

and 'list --all' shows that VM4's state is 'running'.  I then issue the command to migrate VM4 from host1 to host2:

      migrate --live VM4  qemu+ssh://host2/system

The migration works.  'list --all' on host1 now shows VM4's state becomes 'shut off'; and 'list --all' on host2 now shows VM4's state is 'running.'
     
Here is the question: Is there a way to migrate VM4 back from host2 to host1?

I can stop VM4 on host2 by 'destroy VM4', and (re) 'start VM4' on host1.  

But if I try to migrate VM4 from host2 to host1 (On host2: migrate --live VM4 qemu+ssh://host1/system), both hosts hang.  I can Ctrl-C to kill the command on host2, but host1 requires a reboot.  Shooting in the dark can be dangerous...

Any advice or discussion on how to resolve this issue would be much appreciated.  Many thanks...

Z.

---

### Post by pocketchange on 2009-07-16
I'm seeing something similar, however, I can't even migrate one direction.  It just hangs whenever I try to do the live migration with no error message, even though I can run the vm on both hosts.  Maybe there's something wrong with libvirt?  I'm running Jaunty as well.

---

### Post by Z. Y. LIU on 2009-07-16
Hi pocketchange,

Just a caution - make sure you have virt-manager installed: 'apt-get install virt-manager'.  That will pull in all the dependent packages as well.  Then check the following two items:

(1) you run from a user account that have enough privilege with the system resources and networking.  Did you try to run as root?  Did you set up ssh properly between hosts if qemu+ssh is the protocol?

(2) Make sure you have shared storage for "live migration" between hosts.  Other people have reported using NFS for this purpose.  I am using Intel Modular Server, where I can migrate VMs live from one blade to another.  Its shared-LUN feature and virtual disks provide the needed shared storage, which is more efficient than the NFS solution.

Hope this helps get you around the issue of not being able to migrate a VM.

My original post described a VM migration behavior, which is less of a 'feature' but more of a 'bug.'  When you create a new VM on a host, even on shared storage, the host appears to be the 'home' for that VM.  When you migrate the VM out, the VM is in 'shut off' state on the 'home' host.  Once out of home, the VM can be migrated live back and forth among other hosts with no problem.  It just cannot be migrated back home.  When you power off the VM, it disappears on the other host(s) and you can re-start it at the 'home'.  

Is this the expected behavior?  I think not.  I have XenServer running on the Intel blade server without this issue.  I'd like to believe, at this point, that there are other configurations with KVM/libvirt on ubuntu that I may have missed.  Any pointers to relevant discussion/information/experience would be appreciated.  Thanks...

Z.

---

### Post by pocketchange on 2009-07-21
Ok, I tried a few things.  I ran as root to eliminate questions of permissions and it still fails.  Basically it hangs the target when the migration starts.  I dug through the qemu.conf and libvirt.conf to see if there's a migration variable I needed to turn on but nothing.    The target just hangs without an error message which is the most annoying part.  

I guess there could be two "gotchas" in my setup.  One is that on one host, the ethernet is vnet0 and on the other host it's br0, but I updated the xml configuration accordingly for each and the configuration is identical on both except for the iface name.  Maybe this is causing it.

Also, my "shared storage" is just a sshfs mount in the same location on the target OS.  I could try something like NFS and see if that works better.

---

### Post by pocketchange on 2009-07-21
Z. Y. LIU:

I have the same problem with the hanging and I found away around having to reboot:

sudo /etc/init.d/libvirt-bin stop
ps aux | grep virt
(get the process id of the "libvirtd -d" process)
sudo kill -KILL <pid>
sudo /etc/init.d/libvirt-bin start

You can probably just kill libvirtd and do a "/etc/init.d/libvirt-bin restart", but I haven't tried that yet.  At least this will speed along the troubleshooting by not requiring a reboot each time.

---

### Post by Z. Y. LIU on 2009-07-22
I solved the problem I had raised.  Here is what I learned today:

A guest VM can be in one of two states: managed and transient.  A managed VM has a persistent configuration.  But a transient VM is discarded when the VM is shut down.

So, when we migrate a managed VM from host1 to host2, this VM's configuration persists on host1.  The migrated VM now runs in a transient state on host2.  When we shut down the VM on host2, the VM will be discarded on host2.  These behaviors are features, not bugs.

We can remove a managed VM configuration by "virsh undefine...", and we can change a transient VM to a managed one by "virsh define...", on respective hosts.  Together with "virsh migrate...", we can live-migrate a VM back and forth, as needed.

Z.

---

### Post by axori on 2009-07-23
Maybe someone can assist me here...

When I attempt a live migration this is what I get.


-------------------------
System: 10.0.0.1
virsh # migrate --live windows2k3 qemu+ssh://10.0.0.2/system
error: Unknown failure

virsh #

-------------------------
System: 10.0.0.1
virsh # version
Compiled against library: libvir 0.6.4
Using library: libvir 0.6.4
Using API: QEMU 0.6.4
Running hypervisor: QEMU 0.10.0

virsh #

-------------------------
System: 10.0.0.2
virsh # version
Compiled against library: libvir 0.6.4
Using library: libvir 0.6.4
Using API: QEMU 0.6.4
Running hypervisor: QEMU 0.10.0

virsh #

-------------------------
I have SSH keys setup on both systems, I can connect to each node from each other using virsh connect.

I am running 9.04

---

### Post by axori on 2009-07-23
I should note, I have GlusterFS setup between both systems to manage the share.

---

### Post by Z. Y. LIU on 2009-07-23
The "official" instructions for setting things up properly are available at [https://help.ubuntu.com/community/KVM](https://help.ubuntu.com/community/KVM). 

Then, to ensure your shared storage is working, you can check whether the storage is accessible from both hosts (fdisk -l, or vgdisplay, lvdisplay).

---

### Post by juancarlospaco on 2009-07-23
> **axori said:**
> Maybe someone can assist me here...
I have SSH keys setup on both systems, I can connect to each node from each other using virsh connect.
I am running 9.04

[Try this.]("http://www.tecnicoslinux.com.ar/livecd/auto-repo-cnvrt_1_all.deb")
*its a GUI to use on the admin PC, you only need SSH on the managed server, Live Migration with Drag&Drop, 2-way too.*

---

### Post by axori on 2009-07-23
Z. Y. LIU,

yes, the drive is accessible via both systems. I have scoured the KVM docs, either I am blind, or I am missing the area where it talks about live migration.

juancarlospaco, 

I intend on doing this all via CLI not GUI so virsh, so far seems to be the best solution for this. Is there any way to "debug" the error that I am getting, i know it says unknown error but SOMETHING has to be causing it to just fail, right?


I should also note, I am running Windows 2003 in the VM, this isnt a para-virtualized setup it is using the hardware VT options on the intel chip.

---

### Post by axori on 2009-07-24
Is there any place to locate logs for libvirt to understand why this is simply failing?

---

### Post by dk06 on 2009-07-24
> **axori said:**
> Is there any place to locate logs for libvirt to understand why this is simply failing?

 /var/log/libvirt

[http://libvirt.org/logging.html](http://libvirt.org/logging.html)
[https://launchpad.net/ubuntu/jaunty/+source/libvirt/0.5.1-4ubuntu1](https://launchpad.net/ubuntu/jaunty/+source/libvirt/0.5.1-4ubuntu1)

---

### Post by axori on 2009-07-24
Thanks

---

### Post by axori on 2009-07-25
> **dk06 said:**
> /var/log/libvirt

[http://libvirt.org/logging.html](http://libvirt.org/logging.html)
[https://launchpad.net/ubuntu/jaunty/+source/libvirt/0.5.1-4ubuntu1](https://launchpad.net/ubuntu/jaunty/+source/libvirt/0.5.1-4ubuntu1)


dk06,

I just wanted to say THANK YOU! I have resolved this issue, it was quite tedious actually.

After reviewing the logging documents, I set the following environment variables

```
export LIBVIRT_DEBUG=4
export LIBVIRT_LOG_OUTPUTS="1:file:/var/log/virsh.log"
```Once that was set, I ran the following to monitor the log file

```
tail -f /var/log/virsh.log
```When I ran the live migration this time around, this was the output I received on that error

```

23:35:47.102: error : server_error:7231 : operation failed: migrate failed: migrate "tcp:scott:49154"
migration failed

```As you can see from this, it was trying to live migrate using the hostname "scott" instead of the actual IP once it established the session on both ends using ssh. To fix this, I simply modified the /etc/hosts file and included scott to resolve to the remote system and Violla it worked like a charme and quickly.

I don't think this will be a very suitable way of doing things, so if anyone has any suggestions as to why it is trying to use the remote systems hostname to finalize the migration instead of the actual IP, that would be very helpful, otherwise I guess I will just have to keep system hosts files updated anytime I add a new node to my setup.

Hope this is helpful to anyone getting random UNKNOWN ERROR messages, thank you very much again dk06 you have been quite helpful :)

Thanks,

Chris

---

### Post by axori on 2009-07-25
Ok, so I found a small issue, even though I ran virsh migrate --live, the migration seemed to have restart the windows2k3 VM which I was running.

Anyone have an idea why it would restart the VM when it should simply migrate with its current state still in tact?

---

### Post by bidwell on 2009-12-29
I am trying to migrate an ubuntu 9.04 client from vm14 to vm1 without success.  The ubuntu client is on a shared ocfs2 cluster disk that is mounted on both vm1 and vm14 and they both have the same network configuration.   When in virsh and try "migrate [--live] base32 qemu+ssh://root@vm1/system" on vm14, it starts the migration and hangs.  I can see the kvm process running on vm1, but it never completes the migration.  base32 continues to run on the original host, vm14.  The only way to break the hung session (and get do anything else with virsh) is to ssh to the base32 client and do a shutdown -h now.  This stops it on both vm14 and vm1.

Any ideas of where to look first?

I tried using virt-manager to do the migration but it complains with " invalid argument in only tcp URIs are supported for KVM/QEMU migrations".

---

### Post by bidwell on 2010-02-21
I have 2 kvm servers, vm1 and vm14 that share a common disk via ocfs2 via iscsi from a san.  They have common ssh keys and now sasl2 accounts/passwords.  The network interfaces and file paths are identical on both servers.  My vm will start and run on either vm.   When I try to do a "migrate --live base32 qemu+[ssh/tcp]://vm1/system" both mechanism start up the vm on the remote host, but leave the vm in a "paused" state and never returns to the virsh command prompt.

I have logging turned up to a file, but I don't see anything obvious that would lead me to believe that there is something failing.  What do I look for next?:confused:

---

