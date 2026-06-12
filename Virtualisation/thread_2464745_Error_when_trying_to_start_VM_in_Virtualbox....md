---
title: "Error when trying to start VM in Virtualbox..."
date: 2021-07-10
forum: Virtualisation
---

### Post by mark-bobak on 2021-07-10
Hi,

I'm running Ubuntu 21.04 with the default Virtualbox that comes with Ubuntu.  ([COLOR=#000000]Virtua)lBox Graphical User Interface Version 6.1.22_Ubuntu r144080)

It starts up fine, but when I try to start a VM, I get:
```

[/COLOR][COLOR=#000000]Effective UID is not root (euid=1000 egid=1000 uid=1000 gid=1000) (rc=-10)

Please try reinstalling VirtualBox.

where: SUPR3HardenedMain what: 2 VERR_PERMISSION_DENIED (-10) - Permission denied. 

```
[/COLOR]
[COLOR=#000000]So, I tried reinstalling Virtualbox.  No dice, I get the same error.  So, I tried
```

sudo chown 4755 /usr/lib/virtualbox/Virtualbox

```
but then I got the error saying that runnig as root was a no-no, due to security, which makes sense.

So, help?  Any ideas?

AdvThanksance,

-Mark[/COLOR]

[COLOR=#000000]
[/COLOR]

---

### Post by mark-bobak on 2021-07-11
More info:
If I run
```

sudo virtualbox

```
it seems to run fine.

---

### Post by MAFoElffen on 2021-07-11
That directory should be set as owned by, to be accessed by the " vboxusers" group. Is the user you are logged in as, a member of that group?
```
groups
```
If that user is not a member of that group, you missed an installation step, beyond the basic installation of just the program... Hint.

---

### Post by cryptearth on 2021-07-11
If your hardware supports it may consider using KVM instead of virtual box.

---

### Post by mark-bobak on 2021-07-11
Thanks.

My user is now in the vboxusers group;
```

mjb@bohr:~$ groups
mjb adm cdrom sudo dip plugdev lpadmin lxd sambashare vboxusers docker

```
And the /usr/lib/virtualbox directory is now group owned by vboxusers.
```

mjb@bohr:~$ ls -ld /usr/lib/virtualbox/
drwxrwxr-x 6 root vboxusers 66 Jul 11 17:35 /usr/lib/virtualbox/

```

But I am still getting the 'effective uid is not root' error.

-Mark

---

### Post by mark-bobak on 2021-07-11
Regarding KVM, I've been runnninVirtualbo, on and off, for many years, without major problems.

Is there a strong reason to try KVM?

---

### Post by MAFoElffen on 2021-07-11
You played with permissions using chmode, which may have changed things... So what are the permissions of the files within that directory?

---

### Post by mark-bobak on 2021-07-11
You asked me to change the permissions.  How else would I do that, if not with chmod?

Anyhow, here you go:

```
mjb@bohr:~$ cd /usr/lib/virtualbox/
mjb@bohr:/usr/lib/virtualbox$ ls -l
total 55856
drwxr-xr-x 2 root root       11 Jul 11 17:34 components
drwxr-xr-x 3 root root        3 Jul 11 17:34 ExtensionPacks
-rw-r--r-- 1 root root   130472 Jun 22 03:15 libvboxjxpcom.so
drwxr-xr-x 2 root root        3 Jul 11 17:35 __pycache__
drwxr-xr-x 3 root root        3 Jul 11 17:34 sdk
-rw-r--r-- 1 root root 37129272 Jun 22 03:15 UICommon.so
-rw-r--r-- 1 root root    39696 Jun 22 03:15 VBoxAuthSimple.so
-rw-r--r-- 1 root root    14808 Jun 22 03:15 VBoxAuth.so
-rwxr-xr-x 1 root root   133624 Jun 22 03:15 VBoxAutostart
-rwxr-xr-x 1 root root   183112 Jun 22 03:15 VBoxBalloonCtrl
-rwxr-xr-x 1 root root   100848 Jun 22 03:15 VBoxBugReport
-rwxr-xr-x 1 root root  1096064 Jun 22 03:15 VBoxCpuReport
-rw-r--r-- 1 root root   187928 Jun 22 03:15 VBoxDbg.so
-rw-r--r-- 1 root root  8751160 Jun 22 03:15 VBoxDD2.so
-rw-r--r-- 1 root root   256752 Jun 22 03:15 VBoxDDR0.r0
-rw-r--r-- 1 root root  2232264 Jun 22 03:15 VBoxDD.so
-rw-r--r-- 1 root root   455832 Jun 22 03:15 VBoxDDU.so
-rw-r--r-- 1 root root    39528 Jun 22 03:15 VBoxDragAndDropSvc.so
-rwxr-xr-x 1 root root    14720 Jun 22 03:15 VBoxDTrace
-rw-r--r-- 1 root root  4194304 Apr 15 13:42 VBoxEFI32.fd
-rw-r--r-- 1 root root  4194304 Apr 15 13:42 VBoxEFI64.fd
-rwxr-xr-x 1 root root    68136 Jun 22 03:15 VBoxExtPackHelperApp
-rw-r--r-- 1 root root    35368 Jun 22 03:15 VBoxGuestControlSvc.so
-rw-r--r-- 1 root root    43792 Jun 22 03:15 VBoxGuestPropSvc.so
-rwxr-xr-x 1 root root   166208 Jun 22 03:15 VBoxHeadless
-rw-r--r-- 1 root root   118096 Jun 22 03:15 VBoxHeadless.so
-rw-r--r-- 1 root root    18824 Jun 22 03:15 VBoxHostChannel.so
-rwxr-xr-x 1 root root  1963248 Jun 22 03:15 vbox-img
-rwxr-xr-x 1 root root   134208 Jun 22 03:15 vboximg-mount
-rw-r--r-- 1 root root    78408 Jun 22 03:15 VBoxKeyboard.so
-rwxr-xr-x 1 root root  1444456 Jun 22 03:15 VBoxManage
-rwxr-xr-x 1 root root  1334072 Jun 22 03:15 VBoxManageHelp
-rwxr-xr-x 1 root root    31208 Jun 22 03:15 VBoxNetAdpCtl
-rwxr-xr-x 1 root root   166208 Jun 22 03:15 VBoxNetDHCP
-rw-r--r-- 1 root root   266000 Jun 22 03:15 VBoxNetDHCP.so
-rwxr-xr-x 1 root root   166208 Jun 22 03:15 VBoxNetNAT
-rw-r--r-- 1 root root   303672 Jun 22 03:15 VBoxNetNAT.so
-rw-r--r-- 1 root root   218232 Jun 22 03:15 VBoxPython3_9.so
-rw-r--r-- 1 root root   218232 Jun 22 03:15 VBoxPython.so
-rw-r--r-- 1 root root  3510504 Jun 22 03:15 VBoxRT.so
-rwxr-xr-x 1 root root   166208 Jun 22 03:15 VBoxSDL
-rw-r--r-- 1 root root   196472 Jun 22 03:15 VBoxSDL.so
-rw-r--r-- 1 root root    64456 Jun 22 03:15 VBoxSharedClipboard.so
-rw-r--r-- 1 root root    68504 Jun 22 03:15 VBoxSharedFolders.so
-rwxr-xr-x 1 root root   122259 Jun 22 03:15 vboxshell.py
-rwxr-xr-x 1 root root  7871048 Jun 22 03:15 VBoxSVC
-rw-r--r-- 1 root root   248824 Jun 22 03:15 VBoxSVGA3D.so
-rwxr-xr-x 1 root root     4163 Apr 28 12:31 VBoxSysInfo.sh
-rwxr-xr-x 1 root root    63968 Jun 22 03:15 VBoxTestOGL
-rwxr-xr-x 1 root root    14648 Jun 22 03:15 VBoxTunctl
-rwxr-xr-x 1 root root   166208 Jun 22 03:15 VBoxVMMPreload
-rw-r--r-- 1 root root    14872 Jun 22 03:15 VBoxVMMPreload.so
-rw-r--r-- 1 root root  4306824 Jun 22 03:15 VBoxVMM.so
-rwxr-xr-x 1 root root    14648 Jun 22 03:15 VBoxVolInfo
-rwxr-xr-x 1 root root     6408 Apr 28 12:31 vboxweb-service.sh
-rwxr-xr-x 1 root root 29380912 Jun 22 03:15 vboxwebsrv
-rw-r--r-- 1 root root    52160 Jun 22 03:15 VBoxXPCOMC.so
-rwxr-xr-x 1 root root    35296 Jun 22 03:15 VBoxXPCOMIPCD
-rw-r--r-- 1 root root  1155432 Jun 22 03:15 VBoxXPCOM.so
-rwxr-xr-x 1 root root  2623296 Jun 22 03:15 VirtualBox
-rwxr-xr-x 1 root root   166208 Jun 22 03:15 VirtualBoxVM
-rw-r--r-- 1 root root  1802560 Jun 22 03:15 VirtualBoxVM.so
-rw-r--r-- 1 root root  1967376 Jun 22 03:15 VMMR0.r0
-rwxr-xr-x 1 root root 22878896 Jun 22 03:15 webtest
```

---

### Post by MAFoElffen on 2021-07-12
I guess that I worded that "wrong."

Note: Please got back to all your posts and edit them. I don't want you to get scolded by the Moderators. Any output should be encased within [ c o d e ] inserted_text [ / c o d e } tags. I typed that out by adding an extra space, so it would show up...

Usually, the first error message you are going to see after a fresh install is along the lines of:
> You are not a member of the "vboxusers" group. Please add yourself to  this group before starting Virtualbox. You could do it by using: Settings /  Security and Users / Users and Group Management. Don't forget to  re-login to your account!
Instead of getting that, you got this message:
> [COLOR=#000000]Effective UID is not root (euid=1000 egid=1000 uid=1000 gid=1000) (rc=-10)
Please try reinstalling VirtualBox.
where: SUPR3HardenedMain what: 2 VERR_PERMISSION_DENIED (-10) - Permission denied. [/COLOR][COLOR=#000000]
Which is a btt cryptic, but says the same thing... That the permissions are wrong. Not with what was installed, but that the user, you, needed to be part of the vboxusers" group. That would usually fix that... But now on looking at that error, I see that everywhere as a common problem.

Root created that directory during the install, so is the "owner." Being a part of the vboxusers group should give you read and execute right to the utilities inside that directory. No one needs to be able to write to it besides root.

If you look at the permissions bits of the files inside that directory, they usually you heard the permissions set in that directory from 4750, 4754, or 4755... Depending how locked down it is. Being Root as the owner/creator, and (eUID) group, but groups (such as vboxusers) set read and execute, with others set to either no permission, read, or read/execute. 

There is a problem there... And it should be a bug report to Launch pad, if you install a fresh install, and you get that error. And you followed it's directions, which did not correct it.

To check what it is currently, do this 
```
getfalc /usr/lib/virtualbox/
```
I have not used Virtualbox. Not is about 9-10 years. I'vhad to teach students how to use it more recently... But I mainly use KVM and
```
mafoelffen@Opti-Ubuntu-Main:~$ sudo ls -l /var/lib/libvirt/qemu/
total 36
drwxr-x--- 3 libvirt-qemu kvm 4096 Jun 25 20:50 channel
drwxr-xr-x 2 libvirt-qemu kvm 4096 Jun 25 20:51 checkpoint
drwxr-x--- 2 libvirt-qemu kvm 4096 Jul  2 00:38 domain-10-centos8-aarch64
drwxr-xr-x 2 libvirt-qemu kvm 4096 Jun 25 20:51 dump
drwxr-xr-x 2 libvirt-qemu kvm 4096 Jul  6 14:13 nvram
drwxr-xr-x 3 libvirt-qemu kvm 4096 Jun 25 20:51 ram
drwxr-xr-x 2 libvirt-qemu kvm 4096 Jun 25 20:51 save
drwxr-xr-x 3 libvirt-qemu kvm 4096 Jul  6 19:34 snapshot

mafoelffen@Opti-Ubuntu-Main:~$ getfacl -pe /var/lib/libvirt/qemu/checkpoint
# file: /var/lib/libvirt/qemu/checkpoint
# owner: libvirt-qemu
# group: kvm
user::rwx
group::r-x
other::r-x
```

Yes you could reset it to work
```

sudo chown /usr/lib/virtualbox/ root
sudo chmod -R 4755 /usr/lib/virtualbox/
```

---

### Post by monkeybrain20122 on 2021-07-14
```
I'm running Ubuntu 21.04 with the default Virtualbox that comes with Ubuntu
```

So you are installing the community version. Should uninstall and purge it and install VB from Oracle [https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads)

---

### Post by mark-bobak on 2021-07-17
Thanks monkeybrain, I tried that, got the same error.

---

### Post by MAFoElffen on 2021-07-18
LOL. Yes. I thought so. Truth be told, when I used VirtualBox, I always used the packages straight from Oracle. They were usually newer in version. I admit, that was both good and bad.

Before I first posted, I had searched for that error on Oracle, in their forums and their bug reports... and it prevalent. Many open Bug reports on this, there. Not tied to just Ubuntu, but VirtualBox itself. Even more on problems reported on the OpenSuse boards. Not saying it's related to OpenSuse,. Just that their users are having the same problems right now.

The way it should work, it that you install the packages and add yourself to the vboxusers group. That should give you the access and permission to use it.... Beyond that? Well, you could try work-arounds, but fundamentally there is something wrong with the current package, at least on your machine.. The proper thing to tell you would be to add yourself to one of their bug reports. The obvious thing is that you probable want to use a working version... Yes, that is a reoccurring problem with differing versions, but is again an active problem.

To do that, install a previous version from Oracle and see if that works for you. At least thre, you can easily access/download previous versions, and install them as a deb package. You could alslos do in from Ubuntu, but would then have to pin it to keep it from trying to update again. 

That way, while added to one of their bug reportss, you'll get an email when the status changes, and have access to it, before it gets a patch downstream, back to Ubuntu.

That's not probably not a popular answer here.. But that does get you going again, and it is just reality.

---

### Post by rsteinmetz70112 on 2021-07-18
For what it's worth. I have only installed virtual box once and seldom use it but I did install on 20.04 from the repositories and it ran fine. I installed Windows 7 in a VM and it works as well. As I mentioned I have little experience but I've found 3rd party install are often problematic.

---

### Post by mark-bobak on 2021-08-01
Well, after some email trwffice generated via the bug I reported in Launchpad,, I got an answer.
The fix is:
```
sudo chmod u+s /usr/lib/virtualbox/VirtualBoxVM
```

---

### Post by MAFoElffen on 2021-08-01
> **mark-bobak said:**
> Well, after some email trwffice generated via the bug I reported in Launchpad,, I got an answer.
The fix is:
```
sudo chmod u+s /usr/lib/virtualbox/VirtualBoxVM
```

So the permissions fix was (on the executable):
> ```
$ chmod u+s /<Path_To_File>/<File_Name>
```  The **SetGID** bit enforces group ownership on files and  directories. When it is set, any file or directory created in a  directory will get the directory's group ownership, not the user's. When  it is set on a file, the file will always be executed as its owning  group rather than as the user.
And was like Oracle Ticket #8257  > [https://forums.virtualbox.org/viewtopic.php?f=7&t=90997&sid=8a64cd72a6da713f644038712d3b86d3](https://forums.virtualbox.org/viewtopic.php?f=7&t=90997&sid=8a64cd72a6da713f644038712d3b86d3)

Happy that it is working for you now.

Please remember to use the Thread Tools in the upper right to mark this as solved so that others may find your solution...

EDIT: This is from your previous post/output in this thread:
```
ls -l /usr/lib/virtualbox/VirtualBoxVM
-rwxr-xr-x 1 root root   166208 Jun 22 03:15 VirtualBoxVM
```
How does that show now as? For my own curiosity in helping others..

---

