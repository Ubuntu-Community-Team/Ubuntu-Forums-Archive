---
title: "virt-manager cannot power off virtual machines"
date: 2014-06-15
forum: Virtualisation
---

### Post by Fer_Gleiser on 2014-06-15
Hi there.

I'm having a problem with KVM virtual machines. Since one of the last updates I cannot power the virtual machines off.


When I shut the machine down from the virtualised OS, the machine hangs in the "shutting down" state and it cannot be powered off.

here's what I see on [FONT=courier new]/var/log/libvirt/libvirtd.log

2014-06-10 20:31:06.612+0000: 2248: error : virQEMUCapsInitQMP:2748 : Failed to kill process 22858: Permission denied
2014-06-13 11:22:18.579+0000: 2240: error : qemuMonitorIO:656 : internal error: End of file from monitor
2014-06-16 00:36:29.385+0000: 2255: error : virProcessKillPainfully:308 : Failed to terminate process 2844 with SIGTERM: Permission denied
[/FONT]

If I try to destroy the domain with virsh I get:

[FONT=courier new]root@fgleiser-laptop:~# id 
uid=0(root) gid=0(root) groups=0(root)
root@fgleiser-laptop:~# virsh destroy windows
error: Failed to destroy domain windows
error: Failed to terminate process 2844 with SIGTERM: Permission denied
[/FONT]
Here's what I see from ps:

[FONT=courier new]libvirt+  2714  0.0  0.0 320740   464 ?        S    Jun10   0:00 /usr/bin/qemu-system-i386 -S -no-user-config -nodefaults -nographic -M none -qmp unix:/var/lib/libvirt/qemu/capabilities.monitor.sock,server,nowait -pidfile /var/lib/libvirt/qemu/capabilities.pidfile -daemonize
libvirt+  2720  0.0  0.0 259364   460 ?        S    Jun10   0:00 qemu-system-x86_64 -enable-kvm -S -no-user-config -nodefaults -nographic -M none -qmp unix:/var/lib/libvirt/qemu/capabilities.monitor.sock,server,nowait -pidfile /var/lib/libvirt/qemu/capabilities.pidfile -daemonize
libvirt+  2723  0.0  0.0 322856   460 ?        S    Jun10   0:00 /usr/bin/qemu-system-x86_64 -S -no-user-config -nodefaults -nographic -M none -qmp unix:/var/lib/libvirt/qemu/capabilities.monitor.sock,server,nowait -pidfile /var/lib/libvirt/qemu/capabilities.pidfile -daemonize
libvirt+  2844  1.3 25.0 1574424 1012092 ?     Sl   17:55   3:08 qemu-system-x86_64 -enable-kvm -name windows -S -machine pc-0.12,accel=kvm,usb=off -m 1024 -realtime mlock=off -smp 1,sockets=1,cores=1,threads=1 -uuid 068283ca-4d0f-6017-dcbb-5fefac976ee1 -no-user-config -nodefaults -chardev socket,id=charmonitor,path=/var/lib/libvirt/qemu/windows.monitor,server,nowait -mon chardev=charmonitor,id=monitor,mode=control -rtc base=localtime -no-shutdown -boot strict=on -device piix3-usb-uhci,id=usb,bus=pci.0,addr=0x1.0x2 -drive file=/var/lib/libvirt/images/windows.img,if=none,id=drive-ide0-0-0,format=raw -device ide-hd,bus=ide.0,unit=0,drive=drive-ide0-0-0,id=ide0-0-0,bootindex=1 -drive if=none,id=drive-ide0-1-0,readonly=on,format=raw -device ide-cd,bus=ide.1,unit=0,drive=drive-ide0-1-0,id=ide0-1-0 -netdev tap,fd=24,id=hostnet0 -device rtl8139,netdev=hostnet0,id=net0,mac=52:54:00:43:2a:ef,bus=pci.0,addr=0x3 -chardev pty,id=charserial0 -device isa-serial,chardev=charserial0,id=serial0 -device usb-tablet,id=input0 -vnc 127.0.0.1:0 -device cirrus-vga,id=video0,bus=pci.0,addr=0x2 -device virtio-balloon-pci,id=balloon0,bus=pci.0,addr=0x4
root      6715  0.0  0.0  11748   916 pts/10   S+   21:41   0:00 grep --color=auto qemu
libvirt+ 22858  0.0  0.0 259364   460 ?        S    Jun10   0:00 qemu-system-x86_64 -enable-kvm -S -no-user-config -nodefaults -nographic -M none -qmp unix:/var/lib/libvirt/qemu/capabilities.monitor.sock,server,nowait -pidfile /var/lib/libvirt/qemu/capabilities.pidfile -daemonize[/FONT]

The only way I can power it off is doing a "sudo kill" the PID

There is a permission problem somewhere but I cannot find it, any ideas where I should look?

thanks in advance for your help

---

### Post by TheFu on 2014-06-16
When I've seen this, it was because ACPI wasn't enabled in the guestOS.
For Linux guests, that can mean that acpid package wasn't installed.

I don't know how to get this solved for Windows.  I don't shutdown Windows from outside the VM.

---

### Post by Fer_Gleiser on 2014-06-16
it doesnt matter what the OS is. the problem exists whether it's a Linux, Windows or FreeBSD guest.

You shut it down from within the virtual machine, but the VM never powers itself off.

---

### Post by TheFu on 2014-06-16
Which ubuntu release and which libvirt version?

---

### Post by Fer_Gleiser on 2014-06-16
Here you have, sorry i forgot to include that
[FONT=courier new]
root@fgleiser-laptop:~# libvirtd --version
libvirtd (libvirt) 1.2.2

root@fgleiser-laptop:~# cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=14.04
DISTRIB_CODENAME=trusty
DISTRIB_DESCRIPTION="Ubuntu 14.04 LTS"[/FONT]

---

### Post by TheFu on 2014-06-16
Ok - I have 1 machine with that setup.
* Linux client
* BSD client

Both just shutdown cleanly using the virt-manager, right click - shutdown (shutdown) option.  No need to "force" anything.
Do the /var/log/libvirt/ logs help?

---

### Post by Fer_Gleiser on 2014-06-16
Yes, they say "Permission denied". In my first post I pasted the logs :(

There must be a simple file mode or configuration file problem somewhere

---

### Post by TheFu on 2014-06-16
Have you ever screwed with the permissions?
How old is this installation?
Did it ever work previously?
Is your userid in the **libvirtd** group on the server?

Besides that - I've never needed to do anything special. I do not run as root - ever.

---

### Post by Fer_Gleiser on 2014-06-16
> Have you ever screwed with the permissions?

No that I'm aware of. It happened after I upgraded from 13.10 to 14.04, so maybe they got screwed up during the upgrade 

> How old is this installation?

The laptop is 3 years old, but I keep it up to date

> Did it ever work previously?

yes, it was working without any issues until a month ago or so. I noticed it after the upgrade.

> Is your userid in the **libvirtd** group on the server?

it is:

[FONT=courier new]root@fgleiser-laptop:~# grep libvirt /etc/group
libvirtd:x:123:fgleiser
[/FONT]

Thanks for your help

---

### Post by TheFu on 2014-06-16
**id** is how I check group membership.

I only run LTS and my install is 12.04 --> 14.04 upgrade. It is a pure VM server - nothing loaded except VM specific stuff. No destop, no GUI, just kvm, bridge, and libvirt.  virt-manager is run remote.

Might help if you check the file permissions for everything libvirt related ... and the VM file permissions, of course.  Sorry, I'm not any more help.

---

### Post by apos on 2014-07-10
Hi,

I can confirm this problem an it drives me nuts for over half a year now.

There are various threads out there but no solution in sight!

The problem is:
[LIST]
[*]shutdown the virtual machine via libvirt-manager
[*]perform cloning tasks (which only work with a shutdown machine)
[/LIST]

The only way is shutting down the machine (while it does not turn off completely), then logging in as root and kill the running libvirt-process associated with the virtual machine.

And I like to be the one, to force a shutdown. Sometimes this is necessary! The system should do this.
Not any problems with VMware or VitualBox in this case. And no problems with kvm after an update, I don't remember any more, because I really did not expect such a hassly which such a standard software in an LTS server release.

See: [https://answers.launchpad.net/ubuntu/+source/virt-manager/+question/249171](https://answers.launchpad.net/ubuntu/+source/virt-manager/+question/249171)

Greets Axel

---

### Post by apos on 2014-07-10
I found a corresponding bug here (did not find the time to test).

The problem seems to be related to the  **apparmor profile**!

[https://bugs.launchpad.net/ubuntu/+source/libvirt/+bug/1324393](https://bugs.launchpad.net/ubuntu/+source/libvirt/+bug/1324393)

After 

       service apparmor teardown

I can shutdown the machine :guitar:
So this is definitely a problem of a

I did:

  apt-get install --reinstall apparmor

And everything works now.

---

