---
title: "How to run kvm without sudo"
date: 2008-06-13
forum: Virtualisation
---

### Post by ema on 2008-06-13
Hi all,

To run hardware virtualization I need to *sudo kvm*.
Is there any particular grp my username has to be added?
How to do it without the GUI (I'm a console aficionado, even in WoW I use '/invite' '/readycheck')?

Cheers,

---

### Post by ad_267 on 2008-06-13
This might help: [http://linux.byexamples.com/archives/315/how-to-shutdown-and-reboot-without-sudo-password/](http://linux.byexamples.com/archives/315/how-to-shutdown-and-reboot-without-sudo-password/)

That example uses shutdown but it should work just the same for what you want.

---

### Post by ema on 2008-06-13
> **ad_267 said:**
> This might help: [http://linux.byexamples.com/archives/315/how-to-shutdown-and-reboot-without-sudo-password/](http://linux.byexamples.com/archives/315/how-to-shutdown-and-reboot-without-sudo-password/)

That example uses shutdown but it should work just the same for what you want.

But is kvm supposed to be run with sudo usually?
Cheers,

---

### Post by ad_267 on 2008-06-13
OK I thought you were asking how to run a command without having to enter your password for sudo. I don't even know what kvm is. Maybe this will help if you haven't read it already: [https://help.ubuntu.com/community/KVM](https://help.ubuntu.com/community/KVM)

---

### Post by srodden on 2008-06-13
You should be able to run KVM without root. Your username should be in the kvm group as a part of following the installation instructions but check anyway.

What specific problem are you having?

The problem I have is in getting bridged networking operational without running running KVM as root. Due to a change implmemented in 2.6.18, you need to be root to bring up a tap interface. I started a thread on this several weeks ago but no one was able to offer a solution.

---

### Post by dendrobates on 2008-06-13
In Hardy Heron, the following command should be all you need.

*$ sudo adduser `id -un` libvirtd*

---

### Post by srodden on 2008-06-13
> The user `sean' is already a member of `libvirtd'.

---

### Post by ema on 2008-06-14
XXX@blademaster:~$ sudo adduser `id -un` libvirtd
[sudo] password for XXX: 
adduser: The group `libvirtd' does not exist.

What to do now?

Cheers,

---

### Post by srodden on 2008-06-15
I'd suggest that if the libvirtd group doesn't exist at all, you probably haven't installed everything correctly. Try using Synaptic to uninstall all KVM and libvirtd related packages, reboot then reinstall them according to the FAQ page linked in the 3rd reply, above.

---

### Post by ema on 2008-06-16
> **srodden said:**
> I'd suggest that if the libvirtd group doesn't exist at all, you probably haven't installed everything correctly. Try using Synaptic to uninstall all KVM and libvirtd related packages, reboot then reinstall them according to the FAQ page linked in the 3rd reply, above.

At the moment KVM works great even without that lib.
What is the purpose of libvirt..?
Only to authorize users?

Btw that lib is not needed by KVM otherwise why the system has let me autoclean/autoremove it?

Cheers,

---

### Post by srodden on 2008-06-16
libvirt is the API that allows programs to talk to virtualisation systems. You'll probably find the Virtual Machine Manager doesn't work properly without it.

What's your actual problem though? Will KVM not load AT ALL unless you sudo it? Or can you not open a bridged i/f (as is my case)? What's the error message you're getting?

---

### Post by ema on 2008-06-17
1) I don't/can't bridge on wireless (my drivers don't allow the os to 'forge' a nic). At least this is what I got from understanding.
2) The virtualized Windows XP is working pretty fine.
3) To run kvm in hardware virtualization mode I need to run it with sudo, otherwise isn't able to open the file used to read/write to VM (is that /proc/kvm? I don't remeber exaclty), hence if I don't want to sudo kvm I can only run qemu in emulation mode.
4) As seen on [http://kvm.qumranet.com/kvmwiki/HOWTO1]("http://kvm.qumranet.com/kvmwiki/HOWTO1") libvirtd is not needed to run kvm.

So, in order to have access to hardware VM (the file like /proc/kvm or something similar) or I run kvm with sudo or should I give everyone the access in r/w to that file?
Or install libvirtd-bin to manage it?

Thanks in advance,
Regards,

---

### Post by ema on 2008-06-18
Am I correct?
Does someone have any news?

Thanks,
Cheers,

---

### Post by igwk on 2008-06-19
Hi ema, you probably don't have the correct permissions to access the /dev/kvm file.  On my machine, if I run "ls -l /dev/kvm", I get this output:

crw-rw---- 1 root kvm 10, 232 2008-06-19 00:11 /dev/kvm

That means that the root user, or anyone in the "kvm" group can access the file.  I added myself to the "kvm" group and I can run kvm without having to use sudo.  

I don't use the virt-manager tool either -- I just run kvm directly.

---

### Post by ema on 2008-06-19
> **igwk said:**
> Hi ema, you probably don't have the correct permissions to access the /dev/kvm file.  On my machine, if I run "ls -l /dev/kvm", I get this output:

crw-rw---- 1 root kvm 10, 232 2008-06-19 00:11 /dev/kvm

That means that the root user, or anyone in the "kvm" group can access the file.  I added myself to the "kvm" group and I can run kvm without having to use sudo.  

I don't use the virt-manager tool either -- I just run kvm directly.

Great, so is there a kvm group?
Does it get created by default when I *apt-get install kvm..*?
Cheers,

---

### Post by igwk on 2008-06-20
I believe you are correct!  Though I've since switched over from using the official Ubuntu packages to compiling kvm from source.  The project is under very active development and each (fairly frequent) release fixes a bunch of bugs.

---

### Post by ema on 2008-06-20
> **igwk said:**
> I believe you are correct!  Though I've since switched over from using the official Ubuntu packages to compiling kvm from source.  The project is under very active development and each (fairly frequent) release fixes a bunch of bugs.

Good, yesterday I added myself as part of 'kvm' group but I wasn't able to access that file even if the permission said that group was rw.
I hadn't time to reboot to see if that could have fix the issue.
Though I develop in C/C++ from long time etc etc I really know a little about group management in *nix.
Shouldn't the OS check for all my group memebrship when trying to do something on a file I'm not the owner?

Cheers,

---

### Post by igwk on 2008-06-21
If you add yourself to a new group while you're logged in, it won't go into effect until you log out and log back in again.  Maybe you just needed to try logging in again?

---

### Post by ema on 2008-06-23
> **igwk said:**
> If you add yourself to a new group while you're logged in, it won't go into effect until you log out and log back in again.  Maybe you just needed to try logging in again?

Inddeed,
Solved!

Cheers,

---

