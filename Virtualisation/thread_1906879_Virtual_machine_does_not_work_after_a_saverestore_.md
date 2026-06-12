---
title: "Virtual machine does not work after a save/restore (KVM)"
date: 2012-01-10
forum: Virtualisation
---

### Post by orimarti on 2012-01-10
Hello,

I have an Ubuntu Server 10.04 with KVM, the extensions in the BIOS are enabled:

root@cluster03:~# kvm-ok
INFO: Your CPU supports KVM extensions
INFO: /dev/kvm exists
KVM acceleration can be used

The problem is that when i do a save and a restore after of a virtual machine, the screen freezes and the ping does not respond after restored. 

I've disabled the apparmor to dissmiss problems and continues not working.

Does somebody know why the vm does not restore normally?

Thanks a lot! :)

PD: the commands I'm using-->

virsh --connect qemu+ssh:///system save one-309 one-309
virsh --connect qemu+ssh:///system restore one-309



I've saved the debug logs with: 

export LIBVIRT_LOG_OUTPUTS="1:file:virsh.log" 

and this is the output (if I save logs with level 2 or greater I don't see any log which means that KVM or libvirt doesn't detect any error?):

```
10:49:31.794: debug : virInitialize:337 : register drivers
10:49:31.794: debug : virRegisterDriver:838 : registering Test as driver 0
10:49:31.794: debug : virRegisterNetworkDriver:676 : registering Test as network driver 0
10:49:31.794: debug : virRegisterInterfaceDriver:707 : registering Test as interface driver 0
10:49:31.794: debug : virRegisterStorageDriver:738 : registering Test as storage driver 0
10:49:31.794: debug : virRegisterDeviceMonitor:769 : registering Test as device driver 0
10:49:31.794: debug : virRegisterSecretDriver:800 : registering Test as secret driver 0
10:49:31.794: debug : virRegisterDriver:838 : registering Xen as driver 1
10:49:31.794: debug : virRegisterDriver:838 : registering OPENVZ as driver 2
10:49:31.794: debug : vboxRegister:109 : VBoxCGlueInit failed, using dummy driver
10:49:31.794: debug : virRegisterDriver:838 : registering VBOX as driver 3
10:49:31.794: debug : virRegisterNetworkDriver:676 : registering VBOX as network driver 1
10:49:31.794: debug : virRegisterStorageDriver:738 : registering VBOX as storage driver 1
10:49:31.794: debug : virRegisterDriver:838 : registering remote as driver 4
10:49:31.794: debug : virRegisterNetworkDriver:676 : registering remote as network driver 2
10:49:31.794: debug : virRegisterInterfaceDriver:707 : registering remote as interface driver 1
10:49:31.794: debug : virRegisterStorageDriver:738 : registering remote as storage driver 2
10:49:31.794: debug : virRegisterDeviceMonitor:769 : registering remote as device driver 1
10:49:31.794: debug : virRegisterSecretDriver:800 : registering remote as secret driver 1
10:49:31.794: debug : virConnectOpenAuth:1338 : name=qemu+ssh:///system, auth=0x7f282a1b3b80, flags=0
10:49:31.794: debug : do_open:1107 : name "qemu+ssh:///system" to URI components:
  scheme qemu+ssh
  opaque (null)
  authority (null)
  server (null)
  user (null)
  port 0
  path /system

10:49:31.794: debug : do_open:1117 : trying driver 0 (Test) ...
10:49:31.794: debug : do_open:1123 : driver 0 Test returned DECLINED
10:49:31.794: debug : do_open:1117 : trying driver 1 (Xen) ...
10:49:31.794: debug : do_open:1123 : driver 1 Xen returned DECLINED
10:49:31.794: debug : do_open:1117 : trying driver 2 (OPENVZ) ...
10:49:31.794: debug : do_open:1123 : driver 2 OPENVZ returned DECLINED
10:49:31.794: debug : do_open:1117 : trying driver 3 (VBOX) ...
10:49:31.794: debug : do_open:1123 : driver 3 VBOX returned DECLINED
10:49:31.794: debug : do_open:1117 : trying driver 4 (remote) ...
10:49:31.794: debug : doRemoteOpen:565 : proceeding with name = qemu:///system
10:49:31.794: debug : virExecWithHook:620 : ssh localhost nc -q 2>&1 | grep -q 'requires an argument';if [ $? -eq 0 ] ; then   CMD='-q 0';else   CMD='';fi;nc $CMD -U /var/run/libvirt/libvirt-sock
10:49:31.794: debug : remoteIO:8457 : Do proc=66 serial=0 length=28 wait=(nil)
10:49:31.794: debug : remoteIO:8519 : We have the buck 66 0x7f282a1ea010 0x7f282a1ea010
10:49:35.755: debug : remoteIODecodeMessageLength:7941 : Got length, now need 64 total (60 more)
10:49:35.755: debug : remoteIOEventLoop:8383 : Giving up the buck 66 0x7f282a1ea010 (nil)
10:49:35.755: debug : remoteIO:8550 : All done with our call 66 (nil) 0x7f282a1ea010
10:49:35.755: debug : remoteIO:8457 : Do proc=1 serial=1 length=56 wait=(nil)
10:49:35.755: debug : remoteIO:8519 : We have the buck 1 0x67a930 0x67a930
10:49:35.755: debug : remoteIODecodeMessageLength:7941 : Got length, now need 56 total (52 more)
10:49:35.755: debug : remoteIOEventLoop:8383 : Giving up the buck 1 0x67a930 (nil)
10:49:35.755: debug : remoteIO:8550 : All done with our call 1 (nil) 0x67a930
10:49:35.755: debug : doRemoteOpen:918 : Adding Handler for remote events
10:49:35.755: debug : doRemoteOpen:925 : virEventAddHandle failed: No addHandleImpl defined. continuing without events.
10:49:35.755: debug : do_open:1123 : driver 4 remote returned SUCCESS
10:49:35.755: debug : do_open:1143 : network driver 0 Test returned DECLINED
10:49:35.755: debug : do_open:1143 : network driver 1 VBOX returned DECLINED
10:49:35.755: debug : do_open:1143 : network driver 2 remote returned SUCCESS
10:49:35.755: debug : do_open:1162 : interface driver 0 Test returned DECLINED
10:49:35.755: debug : do_open:1162 : interface driver 1 remote returned SUCCESS
10:49:35.755: debug : do_open:1182 : storage driver 0 Test returned DECLINED
10:49:35.755: debug : do_open:1182 : storage driver 1 VBOX returned DECLINED
10:49:35.755: debug : do_open:1182 : storage driver 2 remote returned SUCCESS
10:49:35.755: debug : do_open:1202 : node driver 0 Test returned DECLINED
10:49:35.755: debug : do_open:1202 : node driver 1 remote returned SUCCESS
10:49:35.755: debug : do_open:1229 : secret driver 0 Test returned DECLINED
10:49:35.755: debug : do_open:1229 : secret driver 1 remote returned SUCCESS
10:49:35.755: debug : virDomainLookupByName:1975 : conn=0x674c50, name=one-309
10:49:35.756: debug : remoteIO:8457 : Do proc=23 serial=2 length=40 wait=(nil)
10:49:35.756: debug : remoteIO:8519 : We have the buck 23 0x67a4d0 0x67a4d0
10:49:35.756: debug : remoteIODecodeMessageLength:7941 : Got length, now need 88 total (84 more)
10:49:35.756: debug : remoteIOEventLoop:8383 : Giving up the buck 23 0x67a4d0 (nil)
10:49:35.756: debug : remoteIO:8550 : All done with our call 23 (nil) 0x67a4d0
10:49:35.756: debug : virGetDomain:345 : New hash entry 0x6749b0
10:49:35.756: debug : virDomainSave:2217 : domain=0x6749b0, to=one-309
10:49:35.756: debug : remoteIO:8457 : Do proc=55 serial=3 length=80 wait=(nil)
10:49:35.756: debug : remoteIO:8519 : We have the buck 55 0x67a4d0 0x67a4d0
10:52:23.598: debug : remoteIODecodeMessageLength:7941 : Got length, now need 56 total (52 more)
10:52:23.598: debug : remoteIOEventLoop:8383 : Giving up the buck 55 0x67a4d0 (nil)
10:52:23.598: debug : remoteIO:8550 : All done with our call 55 (nil) 0x67a4d0
10:52:23.598: debug : virDomainFree:2063 : domain=0x6749b0
10:52:23.598: debug : virUnrefDomain:422 : unref domain 0x6749b0 one-309 1
10:52:23.598: debug : virReleaseDomain:376 : release domain 0x6749b0 one-309
10:52:23.598: debug : virReleaseDomain:392 : unref connection 0x674c50 2
10:52:23.598: debug : virConnectClose:1356 : conn=0x674c50
10:52:23.598: debug : virUnrefConnect:259 : unref connection 0x674c50 1
10:52:23.598: debug : remoteIO:8457 : Do proc=2 serial=4 length=28 wait=(nil)
10:52:23.598: debug : remoteIO:8519 : We have the buck 2 0x67a4d0 0x67a4d0
10:52:23.598: debug : remoteIODecodeMessageLength:7941 : Got length, now need 56 total (52 more)
10:52:23.598: debug : remoteIOEventLoop:8383 : Giving up the buck 2 0x67a4d0 (nil)
10:52:23.598: debug : remoteIO:8550 : All done with our call 2 (nil) 0x67a4d0
10:52:23.599: debug : virReleaseConnect:216 : release connection 0x674c50
11:01:19.623: debug : virInitialize:337 : register drivers
11:01:19.624: debug : virRegisterDriver:838 : registering Test as driver 0
11:01:19.624: debug : virRegisterNetworkDriver:676 : registering Test as network driver 0
11:01:19.624: debug : virRegisterInterfaceDriver:707 : registering Test as interface driver 0
11:01:19.624: debug : virRegisterStorageDriver:738 : registering Test as storage driver 0
11:01:19.624: debug : virRegisterDeviceMonitor:769 : registering Test as device driver 0
11:01:19.624: debug : virRegisterSecretDriver:800 : registering Test as secret driver 0
11:01:19.624: debug : virRegisterDriver:838 : registering Xen as driver 1
11:01:19.624: debug : virRegisterDriver:838 : registering OPENVZ as driver 2
11:01:19.624: debug : vboxRegister:109 : VBoxCGlueInit failed, using dummy driver
11:01:19.624: debug : virRegisterDriver:838 : registering VBOX as driver 3
11:01:19.624: debug : virRegisterNetworkDriver:676 : registering VBOX as network driver 1
11:01:19.624: debug : virRegisterStorageDriver:738 : registering VBOX as storage driver 1
11:01:19.624: debug : virRegisterDriver:838 : registering remote as driver 4
11:01:19.624: debug : virRegisterNetworkDriver:676 : registering remote as network driver 2
11:01:19.624: debug : virRegisterInterfaceDriver:707 : registering remote as interface driver 1
11:01:19.624: debug : virRegisterStorageDriver:738 : registering remote as storage driver 2
11:01:19.624: debug : virRegisterDeviceMonitor:769 : registering remote as device driver 1
11:01:19.624: debug : virRegisterSecretDriver:800 : registering remote as secret driver 1
11:01:19.624: debug : virConnectOpenAuth:1338 : name=qemu+ssh:///system, auth=0x7fcfdd6b4b80, flags=0
11:01:19.624: debug : do_open:1107 : name "qemu+ssh:///system" to URI components:
  scheme qemu+ssh
  opaque (null)
  authority (null)
  server (null)
  user (null)
  port 0
  path /system

11:01:19.624: debug : do_open:1117 : trying driver 0 (Test) ...
11:01:19.624: debug : do_open:1123 : driver 0 Test returned DECLINED
11:01:19.624: debug : do_open:1117 : trying driver 1 (Xen) ...
11:01:19.624: debug : do_open:1123 : driver 1 Xen returned DECLINED
11:01:19.624: debug : do_open:1117 : trying driver 2 (OPENVZ) ...
11:01:19.624: debug : do_open:1123 : driver 2 OPENVZ returned DECLINED
11:01:19.624: debug : do_open:1117 : trying driver 3 (VBOX) ...
11:01:19.624: debug : do_open:1123 : driver 3 VBOX returned DECLINED
11:01:19.624: debug : do_open:1117 : trying driver 4 (remote) ...
11:01:19.624: debug : doRemoteOpen:565 : proceeding with name = qemu:///system
11:01:19.624: debug : virExecWithHook:620 : ssh localhost nc -q 2>&1 | grep -q 'requires an argument';if [ $? -eq 0 ] ; then   CMD='-q 0';else   CMD='';fi;nc $CMD -U /var/run/libvirt/libvirt-sock
11:01:19.624: debug : remoteIO:8457 : Do proc=66 serial=0 length=28 wait=(nil)
11:01:19.624: debug : remoteIO:8519 : We have the buck 66 0x7fcfdd6eb010 0x7fcfdd6eb010
11:01:22.993: debug : remoteIODecodeMessageLength:7941 : Got length, now need 64 total (60 more)
11:01:22.993: debug : remoteIOEventLoop:8383 : Giving up the buck 66 0x7fcfdd6eb010 (nil)
11:01:22.993: debug : remoteIO:8550 : All done with our call 66 (nil) 0x7fcfdd6eb010
11:01:22.993: debug : remoteIO:8457 : Do proc=1 serial=1 length=56 wait=(nil)
11:01:22.993: debug : remoteIO:8519 : We have the buck 1 0x6c68f0 0x6c68f0
11:01:22.994: debug : remoteIODecodeMessageLength:7941 : Got length, now need 56 total (52 more)
11:01:22.994: debug : remoteIOEventLoop:8383 : Giving up the buck 1 0x6c68f0 (nil)
11:01:22.994: debug : remoteIO:8550 : All done with our call 1 (nil) 0x6c68f0
11:01:22.994: debug : doRemoteOpen:918 : Adding Handler for remote events
11:01:22.994: debug : doRemoteOpen:925 : virEventAddHandle failed: No addHandleImpl defined. continuing without events.
11:01:22.994: debug : do_open:1123 : driver 4 remote returned SUCCESS
11:01:22.994: debug : do_open:1143 : network driver 0 Test returned DECLINED
11:01:22.994: debug : do_open:1143 : network driver 1 VBOX returned DECLINED
11:01:22.994: debug : do_open:1143 : network driver 2 remote returned SUCCESS
11:01:22.994: debug : do_open:1162 : interface driver 0 Test returned DECLINED
11:01:22.994: debug : do_open:1162 : interface driver 1 remote returned SUCCESS
11:01:22.994: debug : do_open:1182 : storage driver 0 Test returned DECLINED
11:01:22.994: debug : do_open:1182 : storage driver 1 VBOX returned DECLINED
11:01:22.994: debug : do_open:1182 : storage driver 2 remote returned SUCCESS
11:01:22.994: debug : do_open:1202 : node driver 0 Test returned DECLINED
11:01:22.994: debug : do_open:1202 : node driver 1 remote returned SUCCESS
11:01:22.994: debug : do_open:1229 : secret driver 0 Test returned DECLINED
11:01:22.994: debug : do_open:1229 : secret driver 1 remote returned SUCCESS
11:01:22.994: debug : virDomainRestore:2284 : conn=0x6c0c10, from=one-309
11:01:22.994: debug : remoteIO:8457 : Do proc=54 serial=2 length=48 wait=(nil)
11:01:22.994: debug : remoteIO:8519 : We have the buck 54 0x6c6490 0x6c6490
11:01:23.620: debug : remoteIODecodeMessageLength:7941 : Got length, now need 56 total (52 more)
11:01:23.620: debug : remoteIOEventLoop:8383 : Giving up the buck 54 0x6c6490 (nil)
11:01:23.621: debug : remoteIO:8550 : All done with our call 54 (nil) 0x6c6490
11:01:23.621: debug : virConnectClose:1356 : conn=0x6c0c10
11:01:23.621: debug : virUnrefConnect:259 : unref connection 0x6c0c10 1
11:01:23.621: debug : remoteIO:8457 : Do proc=2 serial=3 length=28 wait=(nil)
11:01:23.621: debug : remoteIO:8519 : We have the buck 2 0x6c6490 0x6c6490
11:01:23.621: debug : remoteIODecodeMessageLength:7941 : Got length, now need 56 total (52 more)
11:01:23.621: debug : remoteIOEventLoop:8383 : Giving up the buck 2 0x6c6490 (nil)
11:01:23.621: debug : remoteIO:8550 : All done with our call 2 (nil) 0x6c6490
11:01:23.622: debug : virReleaseConnect:216 : release connection 0x6c0c10
```

---

### Post by orimarti on 2012-01-11
Nobody?

---

### Post by orimarti on 2012-01-12
Bump bump! ;)

---

### Post by CharlesA on 2012-01-12
I don't use KVM, but does it do the same thing if you shut it down and power if back up?

---

### Post by orimarti on 2012-01-13
> **CharlesA said:**
> I don't use KVM, but does it do the same thing if you shut it down and power if back up?

No, it does not do the same, I've tried another time with a virtual machine without any network interface and it works good.

It's strange... Maybe a bug?

---

### Post by CharlesA on 2012-01-13
> **orimarti said:**
> No, it does not do the same, I've tried another time with a virtual machine without any network interface and it works good.

It's strange... Maybe a bug?
Don't think it's a bug. Does it give you any errors about restoring the machine state? Can you restore it from virt-manager ?

---

### Post by orimarti on 2012-01-16
> **CharlesA said:**
> Don't think it's a bug. Does it give you any errors about restoring the machine state? Can you restore it from virt-manager ?

Hello CharlesA,

first of all thank you for your reply. 
When I'm doing the restore it does not give me any error, only I have a output to logs if I put the logs in debug level. 
If I restore from virt-manager it happens the same, the vm is freezed when I restore the vm.

I think that maybe its a incompatibility of libvirt with the bridges or some network library, because when the vm does not have network all goes well.

---

### Post by CharlesA on 2012-01-16
> **orimarti said:**
> 
I think that maybe its a incompatibility of libvirt with the bridges or some network library, because when the vm does not have network all goes well.

Could be. I've only messed around with KVM on a CentOS box but I didn't have any problems saving/restoring guests. :(

---

### Post by imachavel on 2012-01-16
ok so this is vmware as in citrix and not really a virtual box issue huh? I myself have never had problems saving virtual machines state and reopening it. The library causes the issue huh? Interesting. Well I have no advice except to possibly switch between NAT and bridged networking, my best guess is you have done so many times huh?

perryg
technologov
sasquatch

these guys are all great at virtualbox forums. I don't know if you prefer vmware over virtualbox, but the concept should basically be the same, I've never heard of them kicking people off a forum over using a different software source either. Well, what can I say. 

Did you have to pay for this?:

A toolkit to interact with the virtualization capabilities         of recent versions of Linux (and other OSes), see our         [project goals]("http://libvirt.org/goals.html") for details.

If you didn't, then is there any other software that will do this:

A toolkit to interact with the virtualization capabilities         of recent versions of Linux (and other OSes), see our         [project goals]("http://libvirt.org/goals.html") for details.       ??

with vmware? That very well might be the problem.

[http://libvirt.org/drvqemu.html](http://libvirt.org/drvqemu.html)

libvirt is a driver huh? obviously to help kvm extend further from the bios into higher level code, and allow you to use kvm with the virtual machines? How is your usb filter doing with that? So, are there alternatives? Can you uninstall libvirt from synaptic and use alternative driver? I've never configured kvm with a device filter and I assume it's a usb filter since my version of kvm connects via usb.:confused:

---

### Post by CharlesA on 2012-01-16
What are you talking about? The problem is with KVM, not VirtualBox or VMWare (or Citrix for that matter).

[KVM = Kernel Virtual Machine]("https://help.ubuntu.com/community/KVM").

---

