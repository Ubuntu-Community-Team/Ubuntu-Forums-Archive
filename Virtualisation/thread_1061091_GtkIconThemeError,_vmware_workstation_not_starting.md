---
title: "Gtk::IconThemeError, vmware workstation not starting"
date: 2009-02-05
forum: Virtualisation
---

### Post by KTM76 on 2009-02-05
Hi all.

When I try to start vmware workstation from terminal, I get the following error message:

terminate called after throwing an instance of 'Gtk::IconThemeError'

vmware workstation 6.5.1 refuses to start. However, if I log in to ubuntu as guest user, I can start vmware, but when I'm logged in as my standard user it fails to start. Starting vmware from the terminal ends with the following message:

vermagic: 2.6.27-9-generic SMP mod_unload modversions
terminate called after throwing an instance of 'Gtk::IconThemeError'
eivind@w700:~$ terminate called after throwing an instance of 'Gtk::IconThemeError'

The log files in /tmp give me the following information:

Jan 28 15:20:25.457: vmui| System libcrypto.so.0.9.8 library is older than our library (90807F < 90808F)
Jan 28 15:20:25.501: vmui| Caught signal 6 -- pid 711
Jan 28 15:20:25.501: vmui| SIGNAL: eip 0x7f699ed73fd5 esp 0x7fffb064a8e8 ebp 0x7f69a3667770

Jan 28 15:20:25.501: vmui| SymBacktrace[0] 00007fffb064a320 rip=00007f69a0b47d0c in function Util_BacktraceWithFunc in object /usr/lib/vmware/lib/libvmwarebase.so.0/libvmwarebase.so.0 loaded at 00007f69a0830000
Jan 28 15:20:25.501: vmui| SymBacktrace[1] 00007fffb064a340 rip=00007f69a0c1b292 in function (null) in object /usr/lib/vmware/lib/libvmwarebase.so.0/libvmwarebase.so.0 loaded at 00007f69a0830000
Jan 28 15:20:25.501: vmui| SymBacktrace[2] 00007fffb064a4a0 rip=00007f69a74f20f0 in function (null) in object /lib/libpthread.so.0 loaded at 00007f69a74e3000
Jan 28 15:20:25.501: vmui| SymBacktrace[3] 00007fffb064a8e8 rip=00007f699ed73fd5 in function gsignal in object /lib/libc.so.6 loaded at 00007f699ed41000

It could be something wrong with my Ubuntu installation, because when I start gedit I notice a similar error message:

(gedit:12629): Gtk-WARNING **: Unable to locate theme engine in module_path: "ubuntulooks"

My version of Ubuntu is 8.10 64-bit, kernel version 2.6.27-11-generic.

Hope someone is able to help.

Eivind

---

