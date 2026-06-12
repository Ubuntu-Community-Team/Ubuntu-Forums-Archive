---
title: "Oracle VirtualBox aborts (crash) Windows 10 guest randomly"
date: 2016-12-06
forum: Virtualisation
---

### Post by Micski on 2016-12-06
I am running Oracle VirtualBox 5.1.8 on an updated Ubuntu 16.10. This host runs a Windows 10 guest. For some reason, VirtualBox will abort (crash) the Windows 10 guest at random and its data are lost. The guest is configured to use 3 GB RAM , 2 CPUs, PAE/NX, Hyper-V paravirtualization interface, 128 MB video memory and 3D acceleration. Is there a way to investigate the cause of this? Is my configuration optimal for a Windows 10 guest?

The log for the guest indicate a problem with OpenGL, which produces vector graphics and interacts with the GPU. However, the Windows 10 guest simply uses standard applications, that displays statistics. No 3D graphics.

```
00:05:49.352632 OpenGL Warning: cleaning gl error (0x502), ignoring.. (1 out of 5) ..
00:05:49.364841 OpenGL Warning: cleaning gl error (0x502), ignoring.. (2 out of 5) ..
00:05:49.379859 OpenGL Warning: cleaning gl error (0x502), ignoring.. (3 out of 5) ..
00:05:49.402106 OpenGL Warning: cleaning gl error (0x502), ignoring.. (4 out of 5) ..
00:05:49.412839 OpenGL Warning: cleaning gl error (0x502), ignoring.. (5 out of 5) ..

```

---

### Post by DuckHook on 2016-12-06
It's been literally years since I've used Windows (not since XP), but my understanding is that Win10 uses 3D even to display its basic DE&#8213;much as Ubuntu does with Unity. Therefore, there is no such thing as "no 3D graphics".

I am by no means a virtualisation guru, but anyone even hoping to help you will need:

[LIST=1]
[*]Your HW specs. Pls post output of:```
sudo lshw -sanitize
```
[*]Your VB guest config. Pls post output of:```
VBoxManage showvminfo "name_of_your_vm"
```…replacing name_of_your_vm with the actual name of your virtual machine. The quotes are required if there are any spaces in the VM name.
[*]The *host* (***not*** guest) system logs, especially *syslog*. *dmesg* right after the crash would also be helpful, although it will likely just mirror *syslog*.
[/LIST]
All of these outputs will be large, so please post your output between [noparse]```
 and 
```[/noparse] tags for clarity. Or highlight the output and use the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the *Adv Reply* toolbar.

---

