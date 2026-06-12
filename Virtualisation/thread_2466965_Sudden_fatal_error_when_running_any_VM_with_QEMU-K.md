---
title: "Sudden fatal error when running any VM with QEMU-KVM"
date: 2021-09-11
forum: Virtualisation
---

### Post by LVDave on 2021-09-11
I'm running KUbuntu 20.04 as the host, and since yesterday, I'm getting the following error when attempting to start any VM I have set up. 

[https://imgur.com/P8zk50N](https://imgur.com/P8zk50N)

Up till now, everything worked fine. I've rebooted the system (Windows got me started doing THAT!), and noticing the "permission denied" on accessing
the kvm kernel module, I checked to be sure my user account was still a member of the "kvm" group.. It was. The only thing I could think of, was the
fact I wanted to test a flash drive I made yesterday to install OS using the Ventoy package on the flash drive. I ran "sudo kvm -hdb /dev/sdc" and it booted
the Ventoy menu. I didn't try running any vms then, until today. That "permission denied" appears to be a "smoking gun", but other than being a member
of the "kvm" group, I'm lost.. 

Thanks
Dave

---

### Post by MAFoElffen on 2021-09-14
There are three log files that you would want to look at for KVM problems...
1. $HOME/.virtinst/virt-install.log &#8211; virt-install tool log file.
2. $HOME/.virt-manager/virt-manager.log &#8211; virt-manager tool log file.
3. /var/log/libvirt/qemu/ &#8211; Log files for each running virtual machine.

Since you are having troubles with more than one VM, and it specifically notes, virt-manager, that is the log I would look at first.

You did say you installed a VM yesterday using sudo privileges, which gave that VM ownership as root, instead of a group permission, whic you may want to chenck the domain install lof for that VM...

Check the syslog, that kvm intitialized... (kvm [1]: Hyp mode initialized successfully)

And check your groups
```

$ groups
kvm libvirt

```

Then see if you can access these without problem or permission errors..

```

which qemu
which kvm
which virt-manager
kvm --version
virt-manager --version
sudo systemctl status libvirtd

```

---

### Post by LVDave on 2021-09-15
Thanks for the info.. Actually I didn't *install* a VM, I simply tested a Ventoy USB stick I'd just created, to carry the ISO files to be used FOR installing distros on bare-metal. In case you're not familiar with Ventoy, its a fantastic package that installs on a USB stick as two partitions, one called VentEFI, that boots the stick, the other partition can, when mounted, have ISO files copied to it, and when you boot the stick, you get a menu of the ISO files in the second partition and you can select which ISO you want to boot/install. I simply tested if the stick would boot to the menu. BUT... Now that I think about it, I did do the "kvm -hdb /dev/sdc" as root (sudo).. Am away from the machine with this problem right now but will check everything you listed when I get home... THANKS.. Kind of new to KVM...

---

### Post by MAFoElffen on 2021-09-15
If I do something with a VM booting off USB, then I set the details of that VM to use hardware USB pass-through... Then I boot from and write USB's from the VM... If you did that... Then I know the problem... LOL. (That is the only way a VM will boot from USB.)

It is a pain in the behind and does happen to me often. It happens even if you you take the USB out and plug it into the same USB port... I do not know why it is so picky, but it is. It's broken, until...

Open Virt-Manager, Go to the VM you had open to do that. Go to details view. Go to the USB Hardware from psychical, and remove/update. Everything will strat working again.

---

### Post by LVDave on 2021-09-17
Finally got time to try your suggestions..


Addressing the logs you mentioned, I don't have the following directories in $HOME..

$HOME/.virinst or $HOME/.virt-manager

I DO have the /var/log/libvirt/qemu with logs for each of my installed vms.. I did not see any log in the directory that might indicate it was a log for the 
USB stick test I ran that apparently caused this problem.

As for groups, my user account is a member of kvm, libvirt

Here's a weird one..

**which qemu is not found**
which kvm is /usr/bin/kvm
which virt-manager is /usr/bin/virt-manager
kvm --version is QEMU emulator version 4.2.1 (Debian 1:4.2-3ubuntu6.17)
Copyright (c) 2003-2019 Fabrice Bellard and the QEMU Project developers
virt-manager --version is 2.2.1
systemctl status libvirtd is running


As for your comment where you said you knew where the problem was, let me clarify what I did with the USB kvm boot. I did not use Virt-manager at all with
this usb test. As I mentioned earlier in the thread, from the command line, I did "sudo kvm -hdb /dev/sdc". At no time did I use virt-manager to do this test. I recall testing a USB stick with an ISO before and did not have this malfunction.

---

### Post by MAFoElffen on 2021-09-17
hmmm. Let me look 

The user's virt-manager.log is now located at $HOME/.cache/virt-manager/virt-manager.log

You had said that you now couldn't start "any" VM's. The logs of those VM's you tried to start and failed, might show "something" on why they are failing to start.

---

### Post by LVDave on 2021-09-18
Made an interesting discovery, where I can see all of my vms listed in virt-manager, if I did a "virsh list -all" I see NONE of them. Was going to try and
start one from virsh, if I can't see em, I can't start em.. Curious, is this getting to the point where I should just uninstall kvm and reinstall it?

---

### Post by Doug S on 2021-09-18
> **LVDave said:**
> Made an interesting discovery, where I can see all of my vms listed in virt-manager, if I did a "virsh list [COLOR="#FF0000"]-all[/COLOR]" I see NONE of them. Was going to try and
start one from virsh, if I can't see em, I can't start em.. Curious, is this getting to the point where I should just uninstall kvm and reinstall it?
Did you mean to write "--all"?
For example, this is what I get:
```
doug@s19:~$ [COLOR="#FF0000"]virsh list --all[/COLOR]
 Id   Name      State
--------------------------
 1    desk-ii   running
 -    desk-ff   shut off
 -    desk-hh   shut off
 -    serv-xx   shut off
```And I started the running VM via:
```
doug@s19:~$ virsh start desk-ii
Domain desk-ii started
```

---

### Post by Dennis N on 2021-09-18
> Made an interesting discovery, where I can see all of my vms listed in virt-manager, if I did a "virsh list -all" I see NONE of them.
You may need to use sudo to run that. At least that's true on Fedora, which I use as my WM host. Notice:

```
[dmn@Tyana ~]$ virsh list --all
 Id   Name   State
--------------------

[dmn@Tyana ~]$ sudo virsh list --all
[sudo] password for dmn: 
 Id   Name                 State
-------------------------------------
 -    Ubuntu-2004-BIOS     shut off
 -    Ubuntu-2010-UEFI-2   shut off
 -    Ubuntu-2104-UEFI     shut off
 -    Zorin-16-UEFI        shut off

```

---

### Post by MAFoElffen on 2021-09-19
@Dennis N:

Well no... Not on Ubuntu (for Virsh), unless you are trying to do a virsh connect. Is default for Ubuntu:
```
ubuntu_system:~$ echo $LIBVIRT_DEFAULT_URI 
qemu:///system

```
But that doesn't exist outside of Ubuntu systems for virsh, unless you
```

export LIBVIRT_DEFAULT_URI=qemu:///system

```
Which will allow non-sudo users to do that.

---

### Post by LVDave on 2021-09-23
FIXED!!!! Did a bit more googling and found what happened.. Apparently my booting that USB stick somehow caused /dev/kvm permissions to go to [noparse]root:plugdev[/noparse] instead of
root:kvm. Changed the perm to root:kvm and voila! its working again.. I would have found it sooner, but for the fact I wasn't up on what the correct permissons for /dev/kvm and google kept me in the dark until I happened to drill down far enough to see a forum that had the correct permissions. I kind of suspected it was supposed to be root:kvm, but really HATE to change things and break them even further... Thanks all who replied!!!!

Edit: I spoke too soon... After running one VM and closing it down when I tried to start a second, the error was back.. A check of /dev/kvm found that the [noparse]root/:plugdev[/noparse] perms were back.. I'm not really up on what "plugdev" does, though I strongly suspect its a "plug&play" thing for USB stuff. Now I know WHAT the problem is, but
have no idea how to prevent plugdev from stealing perms from kvm... If I manually change the kvm perm back to root:kvm, restart libvirtd and then start a vm, and then immediately look at the /dev/kvm perms again. its back to [noparse]root:plugdev[/noparse] I've tried two different vms and it happens on both..

---

### Post by MAFoElffen on 2021-09-24
Dang. 

Sorry for not being more involved with this thread the past few days... I have 14 new certifications to study for, for work. (Lenovo and HP) ...and only a week to complete them.

From the Debian Wiki:
> plugdev: **Allows members to mount**  (only with the options nodev and nosuid, for security reasons) and  umount removable devices through pmount. netdev: Members of this group  can manage network interfaces through the network manager and wicd.

And this Bug with plugdev related to kvm: [https://bugs.launchpad.net/ubuntu/+source/qemu/+bug/1884476](https://bugs.launchpad.net/ubuntu/+source/qemu/+bug/1884476)
Note remarks 3 & 4... udev rules...

And this Debian Forum post: [https://forums.debian.net/viewtopic.php?p=680731](https://forums.debian.net/viewtopic.php?p=680731)
Posts #13 & 14 where they also resolved by changing their udev rules.

That last thread goes into more details, where they found that manually changing the permissions without doing that, was ending up as not being persistent, and were getting changed back from kvm to plugdev, just like your's.

---

### Post by LVDave on 2021-09-24
Thanks!! Sorry for keeping you from you cert study.. Will scope those links out and hopefully they'll point me to a permanent fix... Good luck on the certs..

---

### Post by MAFoElffen on 2021-09-26
LOL!!! No worries.

In the past 4 Days, I've completed 7 Dell, 8 HP, and 6 Lenovo Certification Courses. I finished 13 of those in less than 24 hours. I have 4 more required Certs to renew left from Lenovo. I have until Wednesday to finish those 4. 

The way it's going, I might do some of the optional courses, just to add to my Resume. Since I did so well in such a short time, and because of my role, each training opportunity gave me credits to do more Certification Courses... that won't be charged out to the company. If it's free, I might as well take advantage of it.

Taking a break right now... Here's some links for you:
 - Since it has to do with with permissions and ownership, the title mentions "files", but the article is written for devices (/dev, device files...), which would include and work for /dev/kvm:
- [How to Configure Device File owner/group with udev rules]("https://www.thegeekdiary.com/how-to-configure-device-file-owner-group-with-udev-rules/")

More basic:, because these explain how they actually work:
 - [URL="https://www.thegeekdiary.com/beginners-guide-to-udev-in-linux/"]Beginners Guide to Udev in Linux
[/URL] - [Tutorial on how to write basic udev rules in Linux]("https://linuxconfig.org/tutorial-on-how-to-write-basic-udev-rules-in-linux")

---

### Post by LVDave on 2021-10-11
Been awhile since I posted on this topic. Still can't find anything wrong in the /etc/udev/rules.d that is responsible for changing the perms on /dev/kvm
from root:kvm to root:plugdev. So I "mcgiver'ed" it, wrote a script that sudo's "chown root:kvm /dev/kvm" and then starts virt-manager. This allows me
to start ONE each VM, which is ok, since that's all I run at one time currently. I can't start more as *somewhere* during the starting of the vm, *something*
changes /dev/kvm back to root:plugdev... Have posted this elsewhere and NObody seems to have a clue as to what the "smoking gun" is for this problem..

---

### Post by MAFoElffen on 2021-10-12
Do this and post the results to an Ubuntu Pastebin:
```

grep -r "plugdev" /lib/udev/

```

---

### Post by MAFoElffen on 2021-10-12
I just found this fix from another distro where this same thing happened way back in 2009, but should work for this now...
> 

[LIST=1]
[*]Create the file /etc/udev/rules.d/65-kvm.rules as root 
[*]Put the following line inside this file: KERNEL=="kvm", NAME="%k", GROUP="kvm", MODE="0660" 
[*]Reload rules with udevadm control --reload-rules && udevadm trigger 
[*]With an user that is member of kvm group, try to execute qemu with the -enable-kvm option. 
[/LIST]

Updated to what is current now  You could try this:
```

sudo echo -d 'KERNEL=="kvm", NAME="%k", GROUP="kvm", MODE="0660"' > /etc/udev/rules.d/65-kvm.rules
sudo udevadm control --reload-rules && sudo udevadm trigger --action=change
sudo update-initramfs -u

```
The first line should create the file with those contents. You could always just open an editor with elevated permissions and do the same...And save it to the same path and filename.

The next line would reload udev without a reboot... 

The 3rd will add the new udev rules to the boot image.

That should exclusively claim /dev/kvm as root:kvm

---

