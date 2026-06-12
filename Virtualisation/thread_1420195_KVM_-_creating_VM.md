---
title: "KVM - creating VM"
date: 2010-03-02
forum: Virtualisation
---

### Post by satimis on 2010-03-02
Hi folks,


Host - Ubuntu 9.10 64bit
Virtualizer - KVM


I followed;
Virtualization With KVM On Ubuntu 9.10
Virtualization With KVM On Ubuntu 9.10 | HowtoForge - Linux Howtos and Tutorials


to install this Virtual Machine. The steps worked without problem. But I have following points can't be resolved:-


1)
I can't find the option on vmbuilder for selecting the packages to install. (no GUI)

2)
If the OS to be installed is an iso image what command shall I run, especially Windows?

3)
I tried to run "rdesktop" to connect the VM without success. I have no idea what shall I replace for "abcd", e.g

$ rdesktop -a 16 -N 192.168.0.200:abcd

192.168.0.200 is the host ip address.

4)
Finally I install virt-manager. It works to connect the VM

Please help. TIA


B.R.
satimis

---

### Post by kiranmurari on 2010-03-03
Hi,

1) I can't find the option on vmbuilder for selecting the packages to install. (no GUI)
You can pass "--addpkg=PKG" switch to install packages

2) If the OS to be installed is an iso image what command shall I run, especially Windows?
Using "--iso=PATH" switch you can install from a ISO image.

3) I tried to run "rdesktop" to connect the VM without success. I have no idea what shall I replace for "abcd", 
e.g $ rdesktop -a 16 -N 192.168.0.200:abcd
You can use virt-viewer to connect to the VM from a remote machine. virtviewer can be used provided 
vmbuilder is asked to attach the VM to the libvirt repository. For this you need to add "--libvirt" option to vmbuilder.

To summarize, the following commands would be helpful:
The below command creates jaunty server VM from an iso image, installs vim package and adds the VM to the libvirt domain.
```
$ sudo vmbuilder kvm ubuntu -a i386 --suite jaunty --iso \
/home/user/isos/ubuntu-9.04-server-i386.iso --addpkg vim --libvirt qemu:///system
```After the above process completes, issue the following command to start the VM
```
$ virsh -c qemu:///system start ubuntu
```On the remote machine, install virt-viewer to access the VM.
```
$ sudo apt-get install virt-viewer
$ virt-viewer -c qemu+ssh://user@a.b.c.d/system ubuntu
```Hope this helps.

---

### Post by satimis on 2010-03-04
> **kiranmurari said:**
>  - snip -

To summarize, the following commands would be helpful:
The below command creates jaunty server VM from an iso image, installs vim package and adds the VM to the libvirt domain.
```
$ sudo vmbuilder kvm ubuntu -a i386 --suite jaunty --iso \
/home/user/isos/ubuntu-9.04-server-i386.iso --addpkg vim --libvirt qemu:///system
```
- snip -


Hi kiranmurari,


Thanks for your advice

$ sudo vmbuilder kvm ubuntu -a amd64 --suite karmic --iso /home/satimisu910/Downloads/ubuntu9.10_64_mini.iso --addpkg vim --libvirt qemu:///system
```

.....
VMBuilder.exception.VMBuilderException: Process (['/usr/sbin/debootstrap', '--arch=amd64', 'karmic', '/tmp/vmbuilderNvdCrb/root', 'file:///tmp/tmpXLcJVA']) returned 1. stdout: I: Retrieving Release
E: Failed getting release file file:///tmp/tmpXLcJVA/dists/karmic/Release
, stderr: 

```

Failed.

Where can find those options; e.g. -a --suite --addpkg etc.?

```

umbuilder --help
virt-install --help

```
didn't find them


Further questions:-
1)
For Debain 5.04 , Fedora 12 , Windows Vista, Windows 7, Windows Server 2008, etc. what shall I put.


2)
If I want to name VM such as vm01, vm02 etc. what can I do?

TIA

B.R.
satimis

---

### Post by kiranmurari on 2010-03-04
Hi satimis
> .....
VMBuilder.exception.VMBuilderException: Process (['/usr/sbin/debootstrap', '--arch=amd64', 'karmic', 
'/tmp/vmbuilderNvdCrb/root', 'file:///tmp/tmpXLcJVA']) returned 1. stdout: I: Retrieving Release
E: Failed getting release file file:///tmp/tmpXLcJVA/dists/karmic/Release
, stderr: Failed
When vmbuilder is invoked, it mounts the iso image and searches for the release file. If it is not found, then it reports error and fails to create the VM. The ubuntu9.10_64_mini.iso looks strange. Is it ubuntu 9.10 64bit version? If you are trying to install ubuntu 9.10 64 bit version, please use ubuntu-9.10-server-amd64.iso available from [http://www.ubuntu.com/getubuntu/download-server](http://www.ubuntu.com/getubuntu/download-server)

> Where can find those options; e.g. -a --suite --addpkg etc.?$ vmbuilder kvm ubuntu --help

> 1) For Debain 5.04 , Fedora 12 , Windows Vista, Windows 7, Windows Server 2008, etc. what shall I put.You will not be able to create VMs based on other distros, since vmbuilder is only for creating ubuntu based virtual machines. More information about vmbuilder and its capabilities can be found at the following link:
[https://help.ubuntu.com/9.10/serverguide/C/jeos-and-vmbuilder.html](https://help.ubuntu.com/9.10/serverguide/C/jeos-and-vmbuilder.html)

> 2) If I want to name VM such as vm01, vm02 etc. what can I do?Use the "--hostname VM_NAME" switch to name the VMs as per your requirement.

So in your case the command would be:
```
$ sudo vmbuilder kvm ubuntu -a amd64 --suite karmic -- hostname vm01 --iso \
/path/to/ubuntu-9.10-server-amd64.iso --addpkg vim --libvirt qemu:///system
```Once you have created the required VMs, you can control them using libvirt tools like virsh, virt-viewer or virt-manager. Example:
```
$ sudo virsh
Connecting to uri: qemu:///system
Welcome to virsh, the virtualization interactive terminal.

Type:  'help' for help with commands
       'quit' to quit

virsh # list --all
 Id Name                 State
----------------------------------
  - vm1                  shut off
  - vm2                  shut off

virsh # start vm1
Domain vm1 started

virsh # list --all
 Id Name                 State
----------------------------------
  1 vm1                  running
  - vm2                  shut off
```Hope this helps.

---

### Post by satimis on 2010-03-04
> **kiranmurari said:**
> 

- snip -

The ubuntu9.10_64_mini.iso looks strange. Is it ubuntu 9.10 64bit version? 

- snip -



Hi kiranmurari,

Thanks for your advice.

It is a working iso image.  I ran UNethbootin to install it on an USB thumb drive.  And I use the USB thumb drive to install the host of this virtual machine.

Can I run following command to install Ubuntu from the USB thumb drive?
```

$ sudo vmbuilder kvm ubuntu -a amd64 --suite karmic -- hostname vm01 --iso \
/dev/sdb1/ --addpkg vim --libvirt qemu:///system

```

$ sudo mount /dev/sdb1 /mnt/
$ ls /mnt/ ```

ATI                   Config.Msi              ProgramData
autoexec.bat          config.sys              Program Files
Boot                  CybDefInstallInfo.log   $Recycle.Bin
bootmgr               Documents and Settings  System Volume Information
BOOTSECT.BAK          hiberfil.sys            Users
CDAVFSuserBackup.log  pagefile.sys            Windows
CDAVFSuser.log        PerfLogs

```

TIA

Other advice noted.  Thanks

B.R.
satimis

---

### Post by kiranmurari on 2010-03-05
Hi satimis,

```
$ ls /mnt/
ATI                   Config.Msi              ProgramData
autoexec.bat          config.sys              Program Files
Boot                  CybDefInstallInfo.log   $Recycle.Bin
bootmgr               Documents and Settings  System Volume Information
BOOTSECT.BAK          hiberfil.sys            Users
CDAVFSuserBackup.log  pagefile.sys            Windows
CDAVFSuser.log        PerfLogs                                          
```This looks like an installed environment. The "--iso" option expects an installer rather than an installed environment. Instead, you can try the "--raw" option and specify the path of the USB drive (/dev/sdb1).
```
$ vmbuilder kvm ubuntu --help
  --raw=PATH            Specify a file (or block device) to as first disk
                        image.
```Hope this helps.

---

