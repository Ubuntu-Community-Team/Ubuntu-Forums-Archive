---
title: "Guest virtualbox machine randomly stucks in &quot;Stopping&quot; state"
date: 2016-10-19
forum: Virtualisation
---

### Post by Light-kun on 2016-10-19
Hello guys!
I searched virtualbox forums and virtualisation part of local forum and didn't found any problems like mine.
I have few  different VMs in virtualbox and from time to time they getting stuck after ACPI shutdown button from phpvirtualbox interface.
Behaviour is really random: it could stuck after ACPI shutdown call while machine shows grub menu. It could shutdown and start perfectly 20 times, but on 21st time it will freeze.
The only way to  fix it is to kill VBoxHeadless process, corresponding to VM. VM becomes "Aborted" for a second and then boots normally.

My soft:
```
virtualbox is already the newest version (5.0.24-dfsg-0ubuntu1.16.04.1).
my os: Ubuntu 16.04.1 LTS 64
```

Getting this state randomly on ACPI shutdown few of my VMs (guest OSes: freebsd9_amd64/linux_amd64/empty_VM).
Found many similar old topics and bugreports (all closed due to inactivity).
Checked logs (VM and vboxSVC.log) for errors but found only hard disk warnings which couldn't affect ACPI actions failure.
Just got another stuck and in log I only see this:
```
00:07:46.560972 Console: Machine state changed to 'Stopping'
00:07:46.561360 Console::powerDown(): A request to power off the VM has been issued (mMachineState=Stopping, InUninit=0)
00:07:46.561393 Display::handleDisplayResize: uScreenId=0 pvVRAM=0000000000000000 w=720 h=400 bpp=32 cbLine=0x0 flags=0x1
```
On normal shutdown after these lines you will see:
```
Changing the VM state from 'RUNNING' to 'POWERING_OFF'
```

What i've tried already:
1) Tried to disable preview in phpvirtualboxweb, disabled 3D-acceleration in video-adapter preferences of VM.
2) apt-get --reinstall install virtualbox-dkms 
3) different guestOStype debian_32/debian_64/otherLinux_64
4) in VM settings: System->Acceleration tried different types: Legacy/Default/HyperV/Minimal/None

---

### Post by TheFu on 2016-10-19
Have you considered using the native VM solution for Linux?  KVM? If you need extremely stable, fast, VMs, I don't think anything else compares. Plus the networking is rock solid since it isn't part of the VM tool, rather it is just normal Linux networking tools leveraged for use by VMs.

These days, even for GUI guest VMs, KVM + spice are pretty great.

---

### Post by Light-kun on 2016-10-20
I'm bound to current config right now (I'm testing application for server management and vbox provides convenient interface for power and network management so far).
Thanks for suggestion, I think about alternatives more and more  because of this instability problem.

---

### Post by TheFu on 2016-10-20
Is the acpid package installed and running?  It is needed inside any guest that needs to receive shutdown from external sources.
Rather than using phpvirtualboxweb, have you tried using the normal vboxmanage and GUI client controls?  Could be a bug in the php code. Simplify and test then simplify and test.

That's all I got.

As far as KVM, there are many GUIs to control it. libvirt is the main library and there is virt-manager which provides almost the same controls as vbox. virt-manager runs on any machine on the network with ssh access to the VM host, or you can run it on the same machine if X/Windows is installed (eeew).  It is just the networking, which is controlled externally since it is a nominal Linux package/capability. A few scripts can make the networking do pretty much anything you like.  There are web interfaces for KVM too - oVirt is one that RHEL uses. I've seen it, but find the setup cumbersome. It is designed to handled hundreds of VM hosts.

Anyway, there are options. That's all.  In a production VM environment, perhaps a different choice than vbox would make sense?  You'll solve this and make the right decision for your needs, I'm certain.

---

### Post by Light-kun on 2016-10-23
On Friday I have completely removed virtualbox-5.0.24-dfsg-0ubuntu1.16.04.1 and installed original one (5.1.8) from official site.
2 days of automated tests went fine without freezes, so It looks like proper fix for me.
Thank for believing in me!

P.S. (11-nov-2016): 2 weeks without freezing. Solved!

---

