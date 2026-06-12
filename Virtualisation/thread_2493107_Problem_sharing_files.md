---
title: "Problem sharing files"
date: 2023-12-04
forum: Virtualisation
---

### Post by satimis on 2023-12-04
Hi all,

VirtualBox
========
Host - Ubuntu 22.04
VM - Kubuntu 22.04

It took me more than an hour unable to sort out the problem of sharing files btw Ubunu 22.04 Host and Kubuntu 22.04 VM

VirtualBox Guest Edition has been installed

sharefolder has been created on Kubuntu

On Kubuntu Terminal:
$ ls -ald /home/satimis/sharefolder/```

drwxrwxr-x 2 satimis satimis 4096 Dec  1 15:54 /home/satimis/sharefolder/

```

Also having run;
$ sudo usermod -a -G vboxsf "$USER"

Drag files from Ubuntu (host) Transfer folder
to:
Kubuntu VM sharefolder doesn't work

Is there a solution?
Or I have to install Samba to do the job?

Please help.

Thanks

Regards

---

### Post by TheFu on 2023-12-04
vboxsf never worked right. There are locking issues.

Just use NFS.  Don't use samba to share files between Unix systems. Use NFS.

---

### Post by satimis on 2023-12-04
> **TheFu said:**
> vboxsf never worked right. There are locking issues.

Just use NFS.  Don't use samba to share files between Unix systems. Use NFS.
Thanks for your advice.

Just checked other Ubuntu 22.04 VMs on this PC.  They don't have problem sharing files with the Host, Ubuntu 22.04.

Would following link be suitable for me to follow instaling NFS on Kubuntu 22.04?

How To Set Up an NFS Mount on Ubuntu 20.04
[https://www.digitalocean.com/community/tutorials/how-to-set-up-an-nfs-mount-on-ubuntu-20-04](https://www.digitalocean.com/community/tutorials/how-to-set-up-an-nfs-mount-on-ubuntu-20-04)

Do I need to make any change on the Host?

[B][COLOR="#FF0000"]Edit
====[/COLOR][/B]
Ah I forgot to mention;
On Kubuntu 22.04 there is already a network setup by default.  It seems requiring SMB to connect. Pls see attached screenshot

Regards

---

### Post by TheFu on 2023-12-04
I'd use the NFS guide at help.ubuntu.com, if I needed it.  NFS has basically "just worked" for 20+ yrs, so I haven't really looked at documentation beyond a quick check of NFS versions in many years.

There is an nfs-server ... so that needs to be installed on the server. It is a kernel module to make performance fly.  Between VMs and the host, you should have 25+ Gbps connections, so NFS should feel like local storage with real Unix permissions.

Go try some things and if you get stuck, post what you tried with configs.

---

### Post by satimis on 2023-12-04
> **TheFu said:**
> I'd use the NFS guide at help.ubuntu.com, if I needed it.  NFS has basically "just worked" for 20+ yrs, so I haven't really looked at documentation beyond a quick check of NFS versions in many years.

There is an nfs-server ... so that needs to be installed on the server. It is a kernel module to make performance fly.  Between VMs and the host, you should have 25+ Gbps connections, so NFS should feel like local storage with real Unix permissions.

Go try some things and if you get stuck, post what you tried with configs.

I found the document on help.ubuntu.com

**[COLOR="#FF0000"]SettingUpNFSHowTo[/COLOR]**
[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)
[B][COLOR="#FF0000"]
Do I need to install NFS on the Host Ubuntu 22.04 ?[/COLOR][/B]

If YES, I have to consider that should I make any mistake how can I come back?  I have more than 15 VMs running on this PC. That is the important point I have to consider

I will clone a new Kubuntu 22.04 for the test.

Regards

---

### Post by TheFu on 2023-12-04
What have you tired?

NFS is very light. Lighter than samba, since there's no need for translations.  NFS is used in enterprises around the world with tens of thousands of clients. At my first Unix job, all our HOME directories were NFS mounts for every workstation both in the development LAN (perhaps 50 clients) and in production LANs with 600+ clients and this was in the early 1990s. My 2 VM hosts sitting 3 ft from me are each faster than any system we had anywhere on that job, including all the servers that cost millions each.  Effectively, my VM hosts are each Cray Y-XP system from 1990.  You tend to through 2x more hardware at problems than I do, so I have ZERO concerns about NFS overhead.  

Heck, if you dropped virtualbox and used KVM+libvirt, and used virt-manager for the GUI, you'd be better off, but that's a different issue, for a different day.

---

### Post by satimis on 2023-12-04
> **TheFu said:**
> - snip -
Heck, if you dropped virtualbox and used KVM+libvirt, and used virt-manager for the GUI, you'd be better off, but that's a different issue, for a different day.
Why I need Kubuntu 22.04 is to run kdenlive.  Please see following link

How to increase font size of KDE application
[https://ubuntuforums.org/showthread.php?t=2493005](https://ubuntuforums.org/showthread.php?t=2493005)

If I can increase the font size of kdenlive running on Ubuntu 22.04 I don't need Kubuntu 22.04

On Internet searching I found;
How can I change the font size of locally installed KDE application menus and dialogs?
[https://askubuntu.com/questions/631730/how-can-i-change-the-font-size-of-locally-installed-kde-application-menus-and-di](https://askubuntu.com/questions/631730/how-can-i-change-the-font-size-of-locally-installed-kde-application-menus-and-di)

But I couldn't locate /.kde/share/config/

I found;
$ ls /home/satimis/snap/kdenlive/```

101  103  common  current

```
Can you help?

Thanks

---

### Post by MAFoElffen on 2023-12-04
But isn't that setting in the attached photo... Kubuntu: System Settings > Appearance > Fonts?

---

### Post by TheFu on 2023-12-04
> **satimis said:**
>  
Can you help?

Nope. Not my skillset.  I don't use any DE.

---

### Post by satimis on 2023-12-04
> **TheFu said:**
> Nope. Not my skillset.  I don't use any DE.
Noted.

I'm running both KVM and VirtualBox in this PC.

KVM is running on a 500G SATA6 SSD drive.  I seldomly run it.  All the times I run VirtualBox, running on a 2TB PCIe 3.0 NVMe SSD drive and with faster in speed.  Starting KVM again, it'll take me some times to update and ugrade its host, Ubuntu and its guests, some of its guests with Docker running on top.

If I can't solve the problem, I'll get an old 120G SSD to install Kubuntu 22.04 or Ubuntu 22.04 with KDE desktop, for only running Kdenlive.

Regards

---

### Post by TheFu on 2023-12-04
Best not to mix unrelated issues in the same thread.  

Kdenlive is off-topic.  Virtualization is only on-topic if you make it so. DEs and fonts are definitely not on topic for file sharing.

Cough ... [https://www.virtualbox.org/manual/ch04.html#sharedfolders](https://www.virtualbox.org/manual/ch04.html#sharedfolders) explains.

---

### Post by Morbius1 on 2023-12-05
I truly hope I'm not wasting your time but I don't understand your original post.
>  sharefolder has been created on Kubuntu
You don't create a shared folder on a VBox guest. You create it on the host through VBox for the VBox guest VM.

You can create a mount point for that host shared folder on the guest VM but if you created the share on the host graphically and specified that mount point you would not end up with these permissions:
> drwxrwxr-x 2 satimis satimis 4096 Dec  1 15:54 /home/satimis/sharefolder/
You would end up with these permissions:
> drwxrwx--- root vboxsf ....
You can make it look like your stated permissions but only if you did not specify an automount in the VBox host and added an entry into your Kubuntu VM fstab file that looks something like this:
```
HostShareName /home/satimis/sharefolder vboxsf uid=satimis,gid=satimis,umask=0002 0 0
```

Is that what you did?

---

### Post by satimis on 2023-12-05
Hi all,

Problem solved with following steps:

On Konsole of Kubuntu VM

$ sudo nano /etc/rc.local

Add following content on it```

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

mount -t vboxsf Transfer_Folder /home/satimis/sharefolder

exit 0

```

save rc.local

Again on Konsole run;```

$ sudo chmod +x /etc/rc.local

```

Reboot VM

Now this time the Transfer folder of the Host will be automatically connected.  File sharing between Host and VM works without problem.

I have performed these steps long time ago to setup file sharing between Host and VM.  I almost forgot.

If I recall correctly at that time the VMs were Gentoo and Fedora

Regards

---

### Post by TheFu on 2023-12-05
That's one method.  Not what I'd use, but if it works ... fine.

Our you could add 1 line to the /etc/fstab inside the VM that looks like this:
```
Transfer_Folder   /home/satimis/sharefolder   vboxsf     defaults 0 0
```

BTW, I wouldn't mount it under any user's HOME. This introduces issues.  Mount it under /media or /d/host and use a symbolic link from ~/sharefolder to /d/host to make access from your HOME easier.  Keep the easy access, but prevent the problems.

---

### Post by satimis on 2023-12-05
> **TheFu said:**
> That's one method.  Not what I'd use, but if it works ... fine.

Our you could add 1 line to the /etc/fstab inside the VM that looks like this:
```
Transfer_Folder   /home/satimis/sharefolder   vboxsf     defaults 0 0
```

BTW, I wouldn't mount it under any user's HOME. This introduces issues.  Mount it under /media or /d/host and use a symbolic link from ~/sharefolder to /d/host to make access from your HOME easier.  Keep the easy access, but prevent the problems.
I did it on Kubuntu Konsole;
$ mkdir /home/satimis/sharefolder

I used this method about ten years ago, simple and straight forwards.  This method doesn't require installing additional software.

---

### Post by TheFu on 2023-12-06
Nothing I wrote in #14 requires additional software either.

You do have to install the vbox guest additions, but that's required regardless.
NFS does require the nfs-server and nfs-client software, but those are so core to Linux at this point, it is like saying you won't install core-utils with ls, mv, cat, less, vi, on a system.  Whatever, we all have our individual limitations.  NFS works not just between the host and guest, but anywhere on the LAN. I understand you have 2 different computers, both running VMs. Wouldn't it be good to allow access to the storage from every VM?

---

### Post by satimis on 2023-12-06
> **TheFu said:**
>  - snip -
I understand you have 2 different computers, both running VMs. Wouldn't it be good to allow access to the storage from every VM?
In the past all VMs on my PCs accessed the central storage via LAN, the router.  Lately I changed the setup.  The central storage is now on an external 4TB USB SSD.  I just plug in the 4TB USB SSD to the PC which needs to access the data in the central storage.  It is fast and exact.

I just copy the necessary data to the Tranfer folder.  Also it is possible to allow all VMs directly access the external 4TB USB SSD

---

### Post by MAFoElffen on 2023-12-06
That is where we differ. My storage is network shares, available to all my machines without having to plug it into a machine to be available.

All my computers, at least my server, workstation, and network attached printer/scanner, are on all the time, so that they are available to anything else I have, all the time. When I need something, I don't want to have to walk to another room, connect it up, and turn it on, waiting to get to it's resources.

From what you said, and what you described, you cannot start anything concurrently, because you have to physically plug in that external drive into that specific computer before it starts. (Or it will fail.) That is a concept of a "portable device" that you carry from one device to another to share those files, but not really that of an always-available "shared resource" device, where those files are there to use all the time from different devices. 

You understand that right?

Even then... On my machines, I actually use 3"-6" USB extension cables, because I've learned that it is easier to throw those away when a USB connector gets worn out and starts failing, than having a connector fail on on a Computer or external drive, and have to think about either having the permanent port replaced, or having to replace the device. USB ports are convenient, but they wear out. I tend to reconfigure things often for different scenarios in what I am doing. I want to protect the investment I have with my computers over the years.

On my workstation, then I have hot-swap drive bays, and my USB drive caddies, where I can just plug drive in to work from, when I need to, without having to crack open the case. Connectors on SATA cables also tend to wear out. 

I think I remember that TheFu has his servers in a 'bread rack' used as his server rack, with extension cables plugged into his computers, so he doesn't have to remove the computers from it to get to the connectors behind.

All my machines have KVM. My ISO's and templates are centralized network resources on two of those. I do most of my VM test-cases on those two KVM Hosts, but are available from all.

You have been around for a long time. You are not new to Ubuntu. You do have quite some skills. I know this. My hat tipped to you for some of the things you drive yourself to do. 

I know you have a dual-boot, with two installed Ubuntu installations... One with KVM, and the other with VirtualBox. You know what we are talking about. You can do things like you want, and how you please. Do what works for you. But, at least to me, some things just make sense, and some do not.

Just some things to thing about...

---

### Post by satimis on 2023-12-06
> **MAFoElffen said:**
>  - snip -

From what you said, and what you described, you cannot start anything concurrently, because you have to physically plug in that external drive into that specific computer before it starts. (Or it will fail.) That is a concept of a "portable device", but not of a "shared resource device". 

- snip - 
That is the 4TB external USB SSD which I'm running.

SanDisk 4TB Extreme Portable SSD
[https://www.amazon.com/SanDisk-4TB-Extreme-Portable-SDSSDE61-4T00-G25/dp/B08RX4QKXS/ref=asc_df_B08RX4QKXS/?tag=hkgoshpadde-20&linkCode=df0&hvadid=675433834712&hvpos=&hvnetw=g&hvrand=14262848346660456046&hvpone=&hvptwo=&hvqmt=&hvdev=c&hvdvcmdl=&hvlocint=&hvlocphy=9061630&hvtargid=pla-1241223898967&mcid=9fa57a15285f3f6397166ebdcf1838ee&th=1](https://www.amazon.com/SanDisk-4TB-Extreme-Portable-SDSSDE61-4T00-G25/dp/B08RX4QKXS/ref=asc_df_B08RX4QKXS/?tag=hkgoshpadde-20&linkCode=df0&hvadid=675433834712&hvpos=&hvnetw=g&hvrand=14262848346660456046&hvpone=&hvptwo=&hvqmt=&hvdev=c&hvdvcmdl=&hvlocint=&hvlocphy=9061630&hvtargid=pla-1241223898967&mcid=9fa57a15285f3f6397166ebdcf1838ee&th=1)

The running computer can detect the portable SSD immediately after plugin.  It doesn't require rebooting the computer.

It is very convenient for sharing data.  I only have 2 PCs, not hundreds of PCs in multi-storey building.  To serve hundreds of PCs I need a central storage room, not a central storage device.

---

### Post by MAFoElffen on 2023-12-06
You can quibble back-and-forth about the unknown details you haven't shared between us all in unending posts, but from what you have shared...

RE: [https://ubuntuforums.org/showthread.php?t=2493107&p=14168057#post14168057](https://ubuntuforums.org/showthread.php?t=2493107&p=14168057#post14168057)

You said you mount it to your /home/satimus/sharefolder... Fine. I applaud the permanent mount point, instead of using /media for a permanent mount. That is sometime I highly recommend to others.

That is not there if that drive is not connected when you start up the machine or login... Unless:
- You either add it in the fstab like TheFu said in his post, or...
- You mount that in after you login. 

The mount tag is there always, but not always populated... It is a portable, not always available mount point. Becaseu you quickly answered him back, that you carry it from machine to machine, like he didn;t know all the details. (He didn't because you didn't share those 'yet'.) When you plug a portable USB external drive in, the default behavior is automount at /media... unless you manually mount it otherwise. <-- Like you seem to be doing.

I don't know all that you do, I am not there to see that. You tend to not share everything, so that the whole picture of that is known, so we have to guess at the possibilities of what might work for you. I try to remember what you say you have, and what you have shared in what you do, when trying to help you...

I honestly try to do what I can to help you. I sincerely care that you get answers for what you want to do...

---

### Post by satimis on 2023-12-06
> **MAFoElffen said:**
> You can quibble back-and-forth about the unknown details you haven't shared between us all in unending posts, but from what you have shared...
.....
.....
.....

What is your hidden intention dragging along on this thread?  It has been marked [Solved] already.

---

### Post by MAFoElffen on 2023-12-06
No hidden intention at all. No emotion between the lines.

You marked it as "Solved" yet kept adding posts after that. 

I added mine <--> to add to what you posted after that. Some of what you said, I felt things needed to be said to answer that. There must have been more that you might have wanted to be aware of, or you would not have posted those 'later posts'.

That is all.

Like I said. I applaud your tenacity, and drive in what you do. No disrespect meant there at all. Please take that as a compliment. That is the intent.

---

### Post by brucezubaa on 2024-01-16
Thanks for solution.

---

