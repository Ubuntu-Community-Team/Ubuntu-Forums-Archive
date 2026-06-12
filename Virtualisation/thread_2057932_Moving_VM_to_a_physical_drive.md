---
title: "Moving VM to a physical drive ??"
date: 2012-09-14
forum: Virtualisation
---

### Post by kpruhs on 2012-09-14
I have been working on a Mac for a few years (web applications developer, python/django) but running Ubuntu Desktop 12.04 as a VM using VirtualBox. I have a very comfortable dev environment configured in Ubuntu and want to completely ditch OSX and use Ubuntu as my primary OS. Is there any way I can move my Ubuntu installation from the VM to a partition as the primary boot OS? I want to do it without having to go through the process of completely reinstalling and reconfiguring a brand new Ubuntu install? I've invested too much time in configuring things to have to start all over. 

Any help would be greatly appreciated.

Kurt

---

### Post by TheFu on 2012-09-14
> **kpruhs said:**
> I have been working on a Mac for a few years (web applications developer, python/django) but running Ubuntu Desktop 12.04 as a VM using VirtualBox. I have a very comfortable dev environment configured in Ubuntu and want to completely ditch OSX and use Ubuntu as my primary OS. Is there any way I can move my Ubuntu installation from the VM to a partition as the primary boot OS? I want to do it without having to go through the process of completely reinstalling and reconfiguring a brand new Ubuntu install? I've invested too much time in configuring things to have to start all over. 

I've never done this on Apple hardware - I'm certain it is more complicated due to the UEFI abomination, but for other hardware it is pretty easy.

The type of VM you used matters. Different VMs will present different physical hardware to Linux running inside a VM.  Almost always, Linux can cope correctly with the changes for anything - except the NIC. You'll have to manually deal with that.

From a very high level, here are the steps.


[LIST=1]
[*]update and dist-upgrade your VM Ubuntu. You want all software to be current before starting.
[*]Make a backup and verify it. I'm serious.  Things can go really wrong.  This backup needs to be to a disk that honors Linux file permissions and ownership.  EXT4 is probably the best answer today. This disk needs to be accessible from both the VM AND the running Ubuntu OS  later on the physical machine.
[*]Create a list of all packages running on the VM - **dpkg --get-selections > pkg-list** does that. Shove those into a file.
[*]Remove any VM "guest additions"
[*]Install the exact same version of Ubuntu to a new HDD installed in the Mac. If 64-bit, use 64-0bit. If 32-bit, use a 32-bit version.
[*]update and dist-upgrade your new physical Ubuntu.
[*]Take that backup disk and connect it to the newly installed OS.
[*]Take the list of packages that you made previously and use **dpkg --set-selections < pkg-list** to tag all that you want installed on the new system.
[*]Tell dpkg to install everything in the current list.  If you didn't install any programs outside the package manager, you are now 100% current with software between both machines. Pretty great, huh?
[*]Now it is a matter of restoring the settings that you changed inside the VM.  If you have a great backup tool, you can just restore from the backup into the new machine and all will be fine ... er ... mostly.  Things that will likely ruin your day include any funky Apple hardware, EUFI, the different network card,  .... that should be it.  Be prepared to correct those issues.  The network card is usually just easy to remove the old lines inside** /etc/udev/rules.d/70-persistent-net.rules **and reboot.
[*]Generally, it is 100% safe to restore your HOME without any concern.
[*]/**etc** - will have a few hardware specific items like the **fstab** and udev stuff previously mentioned.
[*]**/var** probably has your website stuff, but if this is a dynamic site, then you need to worry about the DBMS files and things shoved under **/usr/share** or** /usr/local**
[*]Any proprietary video drivers will need to be installed now.
[*]If you installed anything outside the package manager, you need to migrate that over too ... manually.
[/LIST]
Anyway, I hope this is helpful.  I've migrated about 15 VMs to other VM technologies and this has worked for me.  Have you considered creating a VM server?  Then you can put multiple client OSes under it, do development for different clients in a separate VM and not risk any corruption between the different client VMs.  You can also freeze an entire VM, push it to any external disk, perhaps on a shelf, and have it there with all the development environment ready should that client come back later.  A 1TB HDD can hold the backups for thousands of client VMs.  You'll also be able to offer a "web-site restore" feature to those clients after they try to change something in the config and break it.

---

### Post by kpruhs on 2012-09-24
> **TheFu said:**
> I've never done this on Apple hardware - I'm certain it is more complicated due to the UEFI abomination, but for other hardware it is pretty easy.

The type of VM you used matters. Different VMs will present different physical hardware to Linux running inside a VM.  Almost always, Linux can cope correctly with the changes for anything - except the NIC. You'll have to manually deal with that.

From a very high level, here are the steps.


[LIST=1]
[*]update and dist-upgrade your VM Ubuntu. You want all software to be current before starting.
[*]Make a backup and verify it. I'm serious.  Things can go really wrong.  This backup needs to be to a disk that honors Linux file permissions and ownership.  EXT4 is probably the best answer today. This disk needs to be accessible from both the VM AND the running Ubuntu OS  later on the physical machine.
[*]Create a list of all packages running on the VM - **dpkg --get-selections > pkg-list** does that. Shove those into a file.
[*]Remove any VM "guest additions"
[*]Install the exact same version of Ubuntu to a new HDD installed in the Mac. If 64-bit, use 64-0bit. If 32-bit, use a 32-bit version.
[*]update and dist-upgrade your new physical Ubuntu.
[*]Take that backup disk and connect it to the newly installed OS.
[*]Take the list of packages that you made previously and use **dpkg --set-selections < pkg-list** to tag all that you want installed on the new system.
[*]Tell dpkg to install everything in the current list.  If you didn't install any programs outside the package manager, you are now 100% current with software between both machines. Pretty great, huh?
[*]Now it is a matter of restoring the settings that you changed inside the VM.  If you have a great backup tool, you can just restore from the backup into the new machine and all will be fine ... er ... mostly.  Things that will likely ruin your day include any funky Apple hardware, EUFI, the different network card,  .... that should be it.  Be prepared to correct those issues.  The network card is usually just easy to remove the old lines inside** /etc/udev/rules.d/70-persistent-net.rules **and reboot.
[*]Generally, it is 100% safe to restore your HOME without any concern.
[*]/**etc** - will have a few hardware specific items like the **fstab** and udev stuff previously mentioned.
[*]**/var** probably has your website stuff, but if this is a dynamic site, then you need to worry about the DBMS files and things shoved under **/usr/share** or** /usr/local**
[*]Any proprietary video drivers will need to be installed now.
[*]If you installed anything outside the package manager, you need to migrate that over too ... manually.
[/LIST]
Anyway, I hope this is helpful.  I've migrated about 15 VMs to other VM technologies and this has worked for me.  Have you considered creating a VM server?  Then you can put multiple client OSes under it, do development for different clients in a separate VM and not risk any corruption between the different client VMs.  You can also freeze an entire VM, push it to any external disk, perhaps on a shelf, and have it there with all the development environment ready should that client come back later.  A 1TB HDD can hold the backups for thousands of client VMs.  You'll also be able to offer a "web-site restore" feature to those clients after they try to change something in the config and break it.
I havent had time to test your method yet but it sounds like it should be just what I need. I will update this thread when I get a chance to work on this. Thanks for the help.

---

