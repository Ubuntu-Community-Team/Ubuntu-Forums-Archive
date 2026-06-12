---
title: "KVM problem(unable to connect to '/var/run/libvirt/libvirt-sock': Connection refused)"
date: 2010-06-30
forum: Virtualisation
---

### Post by Lord Daedra on 2010-06-30
Hello!

I going install and use KVM-based VPSes on my server (Ubuntu 10.04).

So i installed this:

#sudo aptitude install build-essential

#sudo aptitude install ubuntu-virt-server ubuntu-vm-builder bridge-utils virt-viewer

also:

#adduser `id -un` libvirtd 
(did it for `root` and `lorddaedra`)

and try check, if it work or not:

#virsh -c qemu:///system list

and I get this message:


root@electra /home/lorddaedra # virsh --connect qemu:///system list
error: unable to connect to '/var/run/libvirt/libvirt-sock': Connection refused
error: failed to connect to the hypervisor
root@electra /home/lorddaedra # 


guides I used:
[http://www.howtoforge.com/virtualization-with-kvm-on-ubuntu-9.04](http://www.howtoforge.com/virtualization-with-kvm-on-ubuntu-9.04)
[https://help.ubuntu.com/community/KVM/Installation](https://help.ubuntu.com/community/KVM/Installation)
[http://www.mythicalbeast.co.uk/linux/kvm_howto.html](http://www.mythicalbeast.co.uk/linux/kvm_howto.html)


Is it bug? Should I post it to [http://libvirt.org/contact.html](http://libvirt.org/contact.html) ?

I activated debug:
#export LIBVIRT_DEBUG=1
#export LIBVIRT_LOG_OUTPUTS="1:file:virsh.log"
#virsh -c qemu:///system list
...
#cat virsh.log


03:33:03.353: debug : virInitialize:336 : register drivers
03:33:03.368: debug : virRegisterDriver:837 : registering Test as driver 0
03:33:03.368: debug : virRegisterNetworkDriver:675 : registering Test as network driver 0
03:33:03.368: debug : virRegisterInterfaceDriver:706 : registering Test as interface driver 0
03:33:03.368: debug : virRegisterStorageDriver:737 : registering Test as storage driver 0
03:33:03.368: debug : virRegisterDeviceMonitor:768 : registering Test as device driver 0
03:33:03.368: debug : virRegisterSecretDriver:799 : registering Test as secret driver 0
03:33:03.368: debug : virRegisterDriver:837 : registering Xen as driver 1
03:33:03.368: debug : virRegisterDriver:837 : registering OPENVZ as driver 2
03:33:03.368: debug : vboxRegister:109 : VBoxCGlueInit failed, using dummy driver
03:33:03.368: debug : virRegisterDriver:837 : registering VBOX as driver 3
03:33:03.368: debug : virRegisterNetworkDriver:675 : registering VBOX as network driver 1
03:33:03.368: debug : virRegisterStorageDriver:737 : registering VBOX as storage driver 1
03:33:03.368: debug : virRegisterDriver:837 : registering remote as driver 4
03:33:03.368: debug : virRegisterNetworkDriver:675 : registering remote as network driver 2
03:33:03.368: debug : virRegisterInterfaceDriver:706 : registering remote as interface driver 1
03:33:03.368: debug : virRegisterStorageDriver:737 : registering remote as storage driver 2
03:33:03.368: debug : virRegisterDeviceMonitor:768 : registering remote as device driver 1
03:33:03.368: debug : virRegisterSecretDriver:799 : registering remote as secret driver 1
03:33:03.368: debug : virConnectOpenAuth:1337 : name=qemu:///system, auth=0x7f20d803eb80, flags=0
03:33:03.368: debug : do_open:1106 : name "qemu:///system" to URI components:
  scheme qemu
  opaque (null)
  authority (null)
  server (null)
  user (null)
  port 0
  path /system

03:33:03.368: debug : do_open:1116 : trying driver 0 (Test) ...
03:33:03.368: debug : do_open:1122 : driver 0 Test returned DECLINED
03:33:03.368: debug : do_open:1116 : trying driver 1 (Xen) ...
03:33:03.368: debug : do_open:1122 : driver 1 Xen returned DECLINED
03:33:03.368: debug : do_open:1116 : trying driver 2 (OPENVZ) ...
03:33:03.368: debug : do_open:1122 : driver 2 OPENVZ returned DECLINED
03:33:03.368: debug : do_open:1116 : trying driver 3 (VBOX) ...
03:33:03.368: debug : do_open:1122 : driver 3 VBOX returned DECLINED
03:33:03.368: debug : do_open:1116 : trying driver 4 (remote) ...
03:33:03.368: debug : doRemoteOpen:564 : proceeding with name = qemu:///system
03:33:03.369: error : doRemoteOpen:725 : unable to connect to '/var/run/libvirt/libvirt-sock': Connection refused
03:33:03.369: debug : do_open:1122 : driver 4 remote returned ERROR
03:33:03.369: debug : virUnrefConnect:259 : unref connection 0x147e060 1
03:33:03.369: debug : virReleaseConnect:216 : release connection 0x147e060



May be answer here but Im not sure: [http://wiki.hetzner.de/index.php/KVM](http://wiki.hetzner.de/index.php/KVM) (I did not do anything with kernel because was not any information about it in ubuntu-kvm guides)

P.S. My server: [http://www.hetzner.de/de/hosting/produkte_rootserver/eq6/](http://www.hetzner.de/de/hosting/produkte_rootserver/eq6/)

---

### Post by ryanrad on 2010-07-01
I just worked through this today.  Once I added my user to the libvirtd group, I got the same message.  Then I remembered that you have to log out and back in to get the new group membership to take effect.

I believe you can confirm with:
```
grep libvirtd /etc/group
```

---

### Post by pedricus on 2010-08-31
I was receiving the same error on my lucid server so i thought i would share my experience.  Being new(ish) to ubuntu/linux i made the mistake of removing the fqdn reference completely from the hosts file (this was on an internal server that doesn't need to access internet at any time, ever, so i figured i would remove this reference)

libvirt doesn't seem to like that, i found that if i just remove the domain suffix and leave the server names themselves pointing to 127.0.1.1, libvirt is okay with that and is working just fine after i put this back in.

Hope that helps if anyone comes across the same thing, it seems very obvious now, but at the time.... haha.. oh well.

~cheers.

---

