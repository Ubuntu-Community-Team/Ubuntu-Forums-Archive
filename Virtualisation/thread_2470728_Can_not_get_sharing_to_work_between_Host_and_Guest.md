---
title: "Can not get sharing to work between Host and Guest"
date: 2022-01-09
forum: Virtualisation
---

### Post by Jonners59 on 2022-01-09
[   	 	 	 	  ]("https://paste.ubuntu.com/p/TcqjbCMmBp/") I had to rebuild my Host and Guest machines recently, but since I have been having trouble with VirtualBox being able to share folders across from Host to Guest and vice versa.  I have set up the Shared Folders and made sure that “Read-only” is _**not**_ ticked.  I have set up mount points with user permissions and all mount fine, BUT they ONLY mount as root.  I can only use rooted nautilus to access them.  I have tried to change their ownership and access but they revert back.  I have set up Samba Sharing but again, can not access them.
 
 
 Host: Linux store 5.13.0-23-generic #23-Ubuntu SMP Fri Nov 26 11:41:15 UTC 2021 x86_64 x86_64 x86_64 GNU/Linux
 Guest: Debian 10   4.19.0-18-amd64
 Both using x11 display
 VirtualBox: Version 6.1.26_Ubuntu r145957
 
 
 Log file contents:
  [URL="https://paste.ubuntu.com/p/TcqjbCMmBp/"]
https://paste.ubuntu.com/p/TcqjbCMmBp/[/URL]

---

### Post by KBar on 2022-01-09
Two things:

[LIST=1]
[*]Make sure you install the *virtualbox-guest-additions-iso* package for your host. Then, mount this ISO in your guest and follow the instructions. You might need to also install the *gcc* and *make* packages.
[*]Allow it auto-mount. This is optimal. In your VM's settings, check under *Shared Folders* tab and uncheck mount point, and tick the automount checkbox.
[/LIST]
 
Further information is available from [https://www.virtualbox.org/manual/ch04.html](https://www.virtualbox.org/manual/ch04.html)

---

### Post by ajgreeny on 2022-01-09
I see you have secure-boot enabled.
Could that be the reason for this problem? I have never used secure-boot on any machine so have no experience of it, particularly in a virtual  machine but I can't see anything else.

---

### Post by Jonners59 on 2022-01-09
Thank you, but this is not the cause.  I always include Guest Additions and that is correctly installed.  ALso tried with and without the mount points, neither work.  But THANK YOU.

---

### Post by Jonners59 on 2022-01-09
OK, That may be worth exploring.  Where did you see that enabled?  Where is the setting?

---

### Post by KBar on 2022-01-09
> **Jonners59 said:**
> OK, That may be worth exploring.  Where did you see that enabled?  Where is the setting?

Tenth line in your log.

```
00:00:01.492395 Secure Boot: Enabled
```

One more thing I forgot to mention is that you should add your guest to the *vboxsf* group after installing Guest Additions.

---

### Post by ajgreeny on 2022-01-09
> One more thing I forgot to mention is that you should add your guest to the vboxsf group after installing Guest Additions. 
Yes, good point and something that I also didn't think about.
It's been a long time since I used VBox having moved to KVM/QEMU which is smoother, faster and all round better in my opinion.

---

### Post by Jonners59 on 2022-01-09
> **KBar said:**
> Tenth line in your log.

```
00:00:01.492395 Secure Boot: Enabled
```

Tenth line in your log.

Actually, not sure that would make a difference.  That only affects how  it boots, not operation and on another machine where I did some testing,  it is fine....  Same image.



> **KBar said:**
> One more thing I forgot to mention is that you should add your guest to the *vboxsf* group after installing Guest Additions. 
Already done....  Makes no difference.  It's the Host that gets added.  Can't add the host as it's a separate OS inside a VM.  It's adding the user to the VM profile. ```
 sudo adduser "host" vboxsf
```

Nice thought though, thanks :-)

Part of me is wondering if it's the Host sharing.  I am also having some network sharing issues, which i have yet to raise.  It's almost there and I can get to files but it's not pretty.

---

### Post by Jonners59 on 2022-01-09
> **ajgreeny said:**
> Yes, good point and something that I also didn't think about.
It's been a long time since I used VBox having moved to KVM/QEMU which is smoother, faster and all round better in my opinion.

I've been using VMware on another machine.  What is nice is the amount of memory that can be added.  Don't know KVM/QEMU..

---

### Post by KBar on 2022-01-09
> **Jonners59 said:**
> Already done....  Makes no difference.  It's the Host that gets added.  Can't add the host as it's a separate OS inside a VM.  It's adding the user to the VM profile. ```
 sudo adduser "host" vboxsf
```

No. Suppose you create *user123* in your guest Ubuntu virtual machine during its installation. First, you install the *virtualbox-guest-additions-iso* package on your host, which just places an ISO image in */usr/share/virtualbox*. Then, after installing the dependencies required to build external kernel modules within guest, you mount that ISO and run the installer script within guest. At the end of the build process, a new group called *vboxsf* is created on guest system. ```
sudo adduser user123 vboxsf
``` will add the user *user123* that was created on guest machine during installation. Reboot is required to make sure the updated modules are loaded.

Refer to [this]("https://www.virtualbox.org/manual/ch04.html") documentation.

> BUT they ONLY mount as root.This suggests that the user on guest hasn't been added to the *vboxsf* group. Run this within guest:
```
groups
```
and share the output.

---

### Post by Jonners59 on 2022-01-10
OK, had a look at this and did all the above, restart and the Guest reverted to an older state.  2nd time that's happened with this build.  So frustrating, and don't know why.  Not a happy bunny.  So today I am going to delete the couple of snapshots I created to use as backups and go through all I did in the past on the Host and Guest and revert back.  Sigh....

---

### Post by Jonners59 on 2022-01-12
Back again.
Hectic, sorry for the delay.
So rebuilt the VBox installation and been through all the pre-install installation stuff, then the VBox app, then installed all the kernel headers that matched the installed kernel then booted the Guest and added Guest Additions, also the pre-install requirements, kernel Headers of the same release..... etc.

I have set it up so I have 3 directories mounted with mount points and one without.

I managed to start a process of "Drag n Drop" between the Guest and Host desktop when it said it was in progress, collecting data and then everything froze.  I had to force a reboot of the Host PC.  I had tried opening the directory that had no mount point and was able to add and remove files and edit them in the one that mounted without a mount point before the PC froze.

Any help, please?

Log Files are here
[https://paste.ubuntu.com/p/dxNJkmJHPQ/](https://paste.ubuntu.com/p/dxNJkmJHPQ/)

---

