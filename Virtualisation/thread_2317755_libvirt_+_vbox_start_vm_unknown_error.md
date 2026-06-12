---
title: "libvirt + vbox start vm unknown error"
date: 2016-03-19
forum: Virtualisation
---

### Post by tiresias2 on 2016-03-19
Hello,


I am trying to use libvirt on  Ubuntu 14.04.1 LTS.


I tried with libvirt 1.2.2 (which comes with apt-get) and also compiled a 1.3.2 version, and had the same problem.


problem:
I have VirtualBox VM working fine. I can manage it through VBoxManage.
I installed libvirt, and i tried to use virsh.


If i do virsh -c vbox:///session list -> i see my VM
If i do virsh -c vbox::///session destroy myVmName -> i see the vm destroyed.
if i do virsh -c vbox::///session start myVmName -> I got:


error: failed to start domain 'myVmName'
error: An error occurred, but the cause is unknown


I am confused with the logging, because a tail -f /var/log/libvirt/libvirtd.log doesnt show any changes (but also when doing virsh list or destroy it works and i still dont see any changes in this log ... this log only dumps stuff when I do a service libvirt-bin restart, then i see a couple of debug messages). It looks like the deamon is never used or something like this.
 
on the virsh client side, i have plenty of "debugs" and "info", but no "errors", only "unknown dumped out on the terminal from which i do the virsh start).

If i do a virsh vbox::///session create .xml i can see the same error (cannot create, unknown error). I think it could be the same issue, something stupid i m sure.


I have attache here the virsh client logs with plenty of stuff in it but no error so far ,

If someone has experienced the same problem and want to help me, it would be fantastic :)
(also if someone can explain why doing a destroy or a list doesnt make logs appear in the daemon, i must have missed something big, it doesnt make any sense to me
(i have a :
log_level = 1
log_outputs="1:file:/var/log/libvirt/libvirtd.log" 
in the /etc/libvirt/libvirtd.conf file,
and i run the daemon using 
sudo service libvirt-bin start,
but i believe deamon will be spawned when first vbox:///session is sent from client)

---

### Post by MAFoElffen on 2016-03-21
So does this bug affect you: [https://bugs.launchpad.net/ubuntu/+source/libvirt/+bug/667076](https://bugs.launchpad.net/ubuntu/+source/libvirt/+bug/667076)

As I can see, it was never fixed... The tenders just mis-understood what the problem was and thought that it was a build.install problem, instead of it not working... because of the way it is compiled.

If those conditions are still true, then you would have to re-compile libvirt with vbox support turned on(?)

---

