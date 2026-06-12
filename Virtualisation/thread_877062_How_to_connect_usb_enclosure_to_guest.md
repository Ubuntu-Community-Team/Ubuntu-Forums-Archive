---
title: "How to connect usb enclosure to guest"
date: 2008-08-01
forum: Virtualisation
---

### Post by satimis on 2008-08-01
Hi folks,


Ubuntu 8.04 server amd64 - host
Ubuntu 6.06 server amd64 - guest
KVM 1:62+dfsq
UBS enclosure


Please advise how to mount the USB enclosure to guest.  It can be mounted on host.  Pointer would be appreciated.  TIA


B.R.
satimis

---

### Post by jtniehof on 2008-08-01
I presume this is a hard drive enclosure? The easiest way is probably to mount the drives on your host, and then use the VBox networking to access them. If you've installed the Open Source Edition (the only version available directly through synaptic), check out [this HOWTO](http://virtualbox.org/wiki/Sharing_files_on_OSE). If you've installed the closed-source binaries from the VBox site, you can set up a shared folder. Details are on page 60 of the [user manual](http://virtualbox.org/download/1.6.4/UserManual.pdf). (Basically there's a "shared folder" setting on the VM settings, and then you can mount it with "mount -t vboxsf *name of share* *mountpoint*".)

With the closed-source version, you can also give the guest access to the USB device and mount it there...in that case, you wouldn't want to mount the drives under the host. There's a USB tab on the VM settings. I haven't played with this approach and I understand it can be fairly finicky.

Incidentally, I doubt you're running an amd64 install on the guest, as VirtualBox only does 32 bit.

---

### Post by satimis on 2008-08-01
Hi jtniehof,


Thanks for your advice and links.

> **jtniehof said:**
> I presume this is a hard drive enclosure? The easiest way is probably to mount the drives on your host, 

Yes, it is a HD.  I can mount it on the host editing files there.


> 
and then use the VBox networking to access them. If you've installed the Open Source Edition (the only version available directly through synaptic), check out [this HOWTO](http://virtualbox.org/wiki/Sharing_files_on_OSE). If you've installed the closed-source binaries from the VBox site, you can set up a shared folder. Details are on page 60 of the [user manual](http://virtualbox.org/download/1.6.4/UserManual.pdf). (Basically there's a "shared folder" setting on the VM settings, and then you can mount it with "mount -t vboxsf *name of share* *mountpoint*".)

With the closed-source version, you can also give the guest access to the USB device and mount it there...in that case, you wouldn't want to mount the drives under the host. There's a USB tab on the VM settings. I haven't played with this approach and I understand it can be fairly finicky.

I installed KVM on Ubuntu repo.  Can I run both KVM and VBox on the same PC simultaneously?


> 
Incidentally, I doubt you're running an amd64 install on the guest, as VirtualBox only does 32 bit.
This is a problem to me.  Both the host and guest are of amd64 version.


I have another thought whether I can create the enclosure as an image on KVM.  But I have to create a new image each time connecting the enclosure.


B.R.
satimis

---

### Post by y@w on 2008-08-01
> **satimis said:**
> 

I have another thought whether I can create the enclosure as an image on KVM.  But I have to create a new image each time connecting the enclosure.


Rather than gothrough all this work, I'd just mount the drive on the host and export it as an NFS share then mount it on the guest. Seems like it would be a lot simpler, plus it would make it a lot more portable.. You wouldn't have to change anything on the drive to make it accessible.

---

### Post by satimis on 2008-08-01
> **y@w said:**
> Rather than gothrough all this work, I'd just mount the drive on the host and export it as an NFS share then mount it on the guest. Seems like it would be a lot simpler, plus it would make it a lot more portable.. You wouldn't have to change anything on the drive to make it accessible.
Hi y@w,


Thanks for your advice.  Please provide more detail how to achieve it.  TIA


I found following thread;
[http://ubuntuforums.org/showthread.php?t=253581](http://ubuntuforums.org/showthread.php?t=253581)

Would it be relevent?  Thanks


B.R.
satimis

---

### Post by y@w on 2008-08-01
Hmm.. it's not really a step-by-step. Here's one from the Ubuntu wiki:

[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

---

### Post by satimis on 2008-08-01
> **y@w said:**
> Hmm.. it's not really a step-by-step. Here's one from the Ubuntu wiki:

[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)
Hi y@w,


Thanks for your URL.


I suppose the NFS installed on Host OS.  If I'm wrong please correct me.


TIA


B.R.
satimis

---

### Post by y@w on 2008-08-01
Correct, the NFS server would be the host OS and then the NFS client would be the guest OS.

---

### Post by satimis on 2008-08-02
> **y@w said:**
> Correct, the NFS server would be the host OS and then the NFS client would be the guest OS.
Thanks


1)
NFS server installation went through w/o complaint.


But I can't find /etc/netgroups.  The client, guest, is running on DHCP.  Anything I have to change here?  Thanks


2)
Encountered problem on installing NFS client on guest.

$ sudo apt-get install portmap nfs-common

It requests for "Ubuntu-Server 6.06.2 _Dapper Drake_- Release amd64" CD.  Putting the CD on Drive, it can't detect/connect the CD

```

...
Media change: please insert the disc labeled 'Ubuntu-Server 6.06.2 _Dapper Drake_- Release amd64' in the drive '/cdrom/' and press enter

```

Also tried mounting the CD on host /media/cdrom0 without result.


Please advise how to overcome this difficulty.  TIA


Edit:

I have NFS-client installation done after commenting out the line```

deb cdrom.......

```
on /etc/apt/sources.list


B.R.
satimis

---

### Post by y@w on 2008-08-04
Ok, good that's what I was going to tell you on number 2.

For the first question.. Have you installed the NIS server? I'd recommend not installing it. If not, /etc/netgroups won't exist as far as I can tell. I found a much simpler how-to. It was linked to at the bottom of that wiki page:
[http://czarism.com/easy-peasy-ubuntu-linux-nfs-file-sharing](http://czarism.com/easy-peasy-ubuntu-linux-nfs-file-sharing)

---

