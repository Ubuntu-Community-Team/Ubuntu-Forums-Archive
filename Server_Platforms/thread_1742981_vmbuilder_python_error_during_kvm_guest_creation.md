---
title: "vmbuilder python error during kvm guest creation"
date: 2011-04-29
forum: Server Platforms
---

### Post by cdehahn on 2011-04-29
Ubuntu Server 10.10 with updates
kernel KVM enabled
 
I have been trying to create a KVM guest using vmbuilder. It gets to the deploy section and dies with a python error. I have searched all over and all I find are links to old bugs. KVM cannot be broken on 10.10. What can I be doing wrong? Pointers greatly appreciated.
 
vmbuilder script:
 
[FONT=Calibri][SIZE=3]#!/bin/sh[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]# ubuntu-vm-builder script for sss.ddd.ddd[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]#[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]ubuntu-vm-builder kvm maverick -o \[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]--domain sss.ddd.ddd \[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]--dest /disk1/Virtual_Machines/sss \[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]--arch amd64 \[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]--hostname sss \[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]--mem 4096 \[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]--user dummy \[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]--pass password \[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]--ip xxx.xx.xx.xx \[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]--mask 255.255.240.0 \[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]--net xxx.xx.xx.xx \[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]--bcast xxx.xx.xx.xx \[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]--gw xxx.xx.xx.xx \[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]--dns yyy.yyy.y.yy \[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]--components main, universe \[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]--addpkg acpid \[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]--addpkg vim \[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]--addpkg openssh-server \[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]--addpkg avahi-daemon \[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]--libvirt qemu:///system ;[/SIZE][/FONT]
 
The error (transcribed, may have typos)
 
[FONT=Calibri]Calling hook: deploy[/FONT]
[FONT=Calibri]libvir: Remore error : server closed connection:[/FONT]
[FONT=Calibri]Traceback (most recent call last):[/FONT]
[FONT=Calibri]File "/usr/bin/ubuntu-vm-builder", line 24, in <module>[/FONT]
[FONT=Calibri]uvb-main[/FONT]
[FONT=Calibri]File "/usr/lib/python2.6/dist-packages/VMBuilder/contrib/cli.py", line 121, in main[/FONT]
[FONT=Calibri]hypervisor.finalise(destdir)[/FONT]
[FONT=Calibri]File "/usr/lib/python2.6/dist-packages/VMBuilder/hypervisor.py", line 78, in [/FONT]
[FONT=Calibri]finalise[/FONT]
[FONT=Calibri]self.call hooks('deploy', destdir)[/FONT]
[FONT=Calibri]File "/usr/lib/python2.6/dist-packages/VMBuilder/distro.py, line 66 in [/FONT]
[FONT=Calibri]call_hooks[/FONT]
[FONT=Calibri]call_hooks(self, *args, **kwargs)[/FONT]
[FONT=Calibri]File "/usr/lib/python2.6/dist-packages/VMBuilder/util.py", line 158, in [/FONT]
[FONT=Calibri]call_hooks[/FONT]
[FONT=Calibri]getattr(plugin, func, log_no_such_method))(*args, **kwargs)[/FONT]
[FONT=Calibri]File "/usr/lib/python2.6/dist-packages/VMBuilder/plugins/libvirt/_init_.py", line 83, in deploy[/FONT]
[FONT=Calibri]self.conn.defineXML(vmxml)[/FONT]
[FONT=Calibri]File "/usr/lib/python2.6/dist-packages/libvirt.py", line 1299, in defineXML[/FONT]
[FONT=Calibri]if ret is None:raise libvirtError('virDomainDefineXML()failed', conn=self)[/FONT]
[FONT=Calibri]libvirt.libvirtError: server closed connection:[/FONT]

[FONT=Calibri]Thanks for any help.[/FONT]

[FONT=Calibri]Chris[/FONT]

---

### Post by sunpower on 2011-06-07
The error you are seeing happens when the virbr0 (or whatever the name in your case is, is in use.) I found this out by trial and error. 

So in effect to use ubuntu-vm-builder you have to allow your other KVM guests to be offline for a moment. There are other ways to create a KVM guest, which maybe allow you to keep the existing guests running, but I have not used those.

To solve your problem, type

```
sudo ifconfig virbr0 down
```


Then you need to restart your networking:

```
sudo /etc/init.d/networking restart
```

You can do this even if you are connected to a remote server, it should come right up and keep your connection open to the remote server.

Now check if the virbr0 is gone:
 
```
ifconfig 
```
 
(sudo not needed because you just look at the info)

If the virbr0 is still there, you need to find out what brings it up again: KVM networking on autostart or maybe you have it in your /etc/network/interfaces -file. But to be able to create a KVM virtual machine useing ubuntu-vm-builder you cannot have it on.

Also make sure you have libvirt-bin on. Try
```
sudo /etc/init.d/libvirt-bin stop
sudo /etc/init.d/libvirt-bin stop 
```
Mere restart will not do the trick for some eason - apparently there needs to be at least some periods for the OS to do whatever it needs to do in between the start and stop.

You also neet to make sure you are not trying to overwrite an existing KVM guest.
Check the defined guests with
```
virsh -c qemu:///system list
```
and if you have existing guest with the same name and you know that you want to get rid of it, then 
```
virsh undefine [name]
```

Hope this helps.

Olli

---

