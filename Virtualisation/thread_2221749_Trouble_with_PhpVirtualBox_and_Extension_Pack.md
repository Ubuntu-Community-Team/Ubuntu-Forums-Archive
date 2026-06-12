---
title: "Trouble with PhpVirtualBox and Extension Pack"
date: 2014-05-03
forum: Virtualisation
---

### Post by glenak1911 on 2014-05-03
Hi all, this is my first post, so please let me know if there is any more information needed or anything. 

I'm currently setting up a Linux Server, trying to get more practice for a potential admin job as well as personal experience, and I'm having trouble configuring my virtual machines. 

My first problem is that when I create a Virtual Machine using phpVirtualBox, I'm unable to configure the remote desktop server port. When I create a virtual machine the RDP port is read and struck through.

Here is my linux version information:
```

vboxuser@MediaBox:~$ uname -or3.13.0-24-generic GNU/Linux

```

Here is my VirtualBox information:
```

vboxuser@MediaBox:~$ VBoxManage -version
4.2.24r92790

```

I read that perhaps the extenstion pack from Oracle should be downloaded to enable the RPD access, but when I try to install it I receive the following error:
```

vboxuser@MediaBox:~$ VBoxManage extpack install Oracle_VM_VirtualBox_Extension_Pack-${vbox_ver/r/-}.vbox-extpack
0%...
Progress state: NS_ERROR_FAILURE
VBoxManage: error: Failed to install "/home/vboxuser/Oracle_VM_VirtualBox_Extension_Pack-4.2.24-92790.vbox-extpack"
VBoxManage: error: The installer failed with exit code 127: Error creating textual authentication agent: Error opening current controlling terminal for the process (`/dev/tty'): No such device or address
VBoxManage: error: Details: code NS_ERROR_FAILURE (0x80004005), component ExtPackManager, interface IExtPackManager
VBoxManage: error: Context: "int handleExtPack(HandlerArg*)" at line 1126 of file VBoxManageMisc.cpp

```

Has anyone encountered this error? If so, what was the workaround? Or if not, where would you suggest I start to troubleshoot this issue?

The variable vbox_ver is the result of VBoxManage --version, FYI.

---

