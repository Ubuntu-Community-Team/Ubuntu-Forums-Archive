---
title: "KVM - Share folder between Host and Guest"
date: 2023-05-29
forum: Virtualisation
---

### Post by satimis on 2023-05-29
Hi all,

I haven't run KVM for quite long time and am now coming back.

Share folder between Host and Guest
Host - Ubuntu 22.04 Desktop
Guest - Ubuntu 22.04

On Google search I found many threads.  Would following article be right for me to follow?
Setup A Shared Folder Between KVM Host And Guest
[https://ostechnix.com/setup-a-shared-folder-between-kvm-host-and-guest/](https://ostechnix.com/setup-a-shared-folder-between-kvm-host-and-guest/)

Please advise.  Thanks

Regards

---

### Post by Dennis N on 2023-05-29
On Ubuntu, my method for this is to connect the two (guest and host) by SSH. You need to install openssh-server on the host. 

Other Locations > Connect to Server
Enter IP address of host preceded by ssh:// or sftp://

First login, you can choose to "remember" these details for a chosen time period ("forever" is an option here) in order to connect next time. 

I also make bookmarks in my guest OS to instantly connect to specific host folders.

That's all there is to it.

---

### Post by satimis on 2023-05-29
> **Dennis N said:**
> On Ubuntu, my method for this is to connect the two (guest and host) by SSH. You need to install openssh-server on the host. 

Other Locations > Connect to Server
Enter IP address of host preceded by ssh:// or sftp://

First login, you can choose to "remember" these details for a chosen time period ("forever" is an option here) in order to connect next time. 

I also make bookmarks in my guest OS to instantly connect to specific host folders.

That's all there is to it.
Thanks for your advice.

Your method is via Internet.  The method described on the document is sharing files inside the PC.  The method used by me on VirtualBox is also inside the PC.

Regards

---

### Post by Dennis N on 2023-05-29
> **satimis said:**
> Thanks for your advice.

Your method is via Internet.  The method described on the document is sharing files inside the PC.  The method used by me on VirtualBox is also inside the PC.

Regards

No, it's not using the Internet. It's a connection on the LAN.

---

### Post by satimis on 2023-05-29
> **Dennis N said:**
> No, it's not using the Internet. It's a connection on the LAN.
Would following thread be the suitable guide to install and enable ssh server on Ubuntu 22.04 host ?

How to install and enable OpenSSH on Ubuntu 22.04 LTS
[https://www.fosslinux.com/78569/install-and-enable-openssh-on-ubuntu.htm](https://www.fosslinux.com/78569/install-and-enable-openssh-on-ubuntu.htm)

Can the transfer of files works on 2 ways? i.e from host to vm and from vm to host?

How about filezilla for transferring files ?

---

### Post by tea for one on 2023-05-29
> **satimis said:**
> 
I haven't run KVM for quite long time and am now coming back.
Share folder between Host and Guest
Host - Ubuntu 22.04 Desktop
Guest - Ubuntu 22.04
This may help [https://www.debugpoint.com/share-folder-virt-manager/](https://www.debugpoint.com/share-folder-virt-manager/)
Thanks to [COLOR="#0000FF"]monkeybrain20122[/COLOR] in post 10 here [https://ubuntuforums.org/showthread.php?t=2485084&highlight=kvm](https://ubuntuforums.org/showthread.php?t=2485084&highlight=kvm)

---

### Post by ajgreeny on 2023-05-29
You can do this by making some changes in the Details of the VM which I can't remember and I'm not on my Linux box at the moment.

I'll find the bookmark I have for this later this evening.  It is very simple and effective and does not use ssh which I used to use, but simply adds a home folder from your host OS as virtio shared disk hardware.
Give me  an hour or two and I'll be back with the link I used.

Here you are.
[https://www.debugpoint.com/share-folder-virt-manager/](https://www.debugpoint.com/share-folder-virt-manager/)

It is very easy to set up; the only stumbling point I found when starting to use this was giving the **Target path** shown in screenshot #4 of that link too complicated a name - I now simply name it **Host**.  The source path is very simple and can be the full pathway of any folder in your host's home.

Good luck!

---

### Post by Dennis N on 2023-05-29
> **satimis said:**
> Would following thread be the suitable guide to install and enable ssh server on Ubuntu 22.04 host ?

How to install and enable OpenSSH on Ubuntu 22.04 LTS
[https://www.fosslinux.com/78569/install-and-enable-openssh-on-ubuntu.htm](https://www.fosslinux.com/78569/install-and-enable-openssh-on-ubuntu.htm)

Can the transfer of files works on 2 ways? i.e from host to vm and from vm to host?

How about filezilla for transferring files ?
Install on the host:
**sudo apt install openssh-server** is all you need to do.
Probably you should restart the host after installing.
Ubuntu has **openssh-client** installed by default, so nothing extra needs to be installed on the guest.

I think you can ignore the configure firewall section. None of that was necessary for me between guest and host.

I connect FROM guest TO host. The file transfers can be both ways. You have a file manager window open to some location on the host and can copy and paste to or from a window on the guest. You can also open files on the host from a guest application.

I never used the terminal to connect as the article shows. I use the file manager which remembers my connection details. I used "remember forever" and clicking on a bookmarked host folder in the guest opens that folder in the host. You can also navigate to other places on the host while connected to it.

I haven't used Filezilla in quite a while. No reason it could not connect to host, but I can't see any reason to use it instead of Files.

---

