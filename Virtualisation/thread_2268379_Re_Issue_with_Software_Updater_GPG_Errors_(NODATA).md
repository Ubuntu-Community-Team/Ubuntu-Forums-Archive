---
title: "Re: Issue with Software Updater GPG Errors (NODATA)"
date: 2015-03-08
forum: Virtualisation
---

### Post by Christopher_S._Atk on 2015-03-08
I have (2) Xubuntu 14.10 x64 VMs running in VMware  Workstation  11/VMware Player.  I have VMware Workstation 11 installed on  a Windows 7  x64 machine (*which hosts one of the VMs*) and also installed on a Windows 8.1 x64 machine (*also hosts one of the VMs*).

  Neither of these VMs will execute an *apt-get update* command successfully.  I get a return error of:

[SIZE=4][FONT=courier new]root@xubuntu_x64VM:~/Desktop# apt-get update
Get:1 [[http://archive.ubuntu.com](http://archive.ubuntu.com) utopic][1] InRelease [310 B]
98% [1 InRelease gpgv 310 B] [Connecting to archive.ubuntu.com (91.189.91.23)]
[Waiting for headers] Splitting up /var/lib/apt/lists/partial  /archive.ubuntu.com_ubuntu_dists_utopic_InRelease into data and Ign  [[http://archive.ubuntu.com](http://archive.ubuntu.com) utopic][2] InRelease                                                       
E: GPG error: [[http://archive.ubuntu.com](http://archive.ubuntu.com) utopic][3] InRelease: Clearsigned file isn't valid, got 'NODATA' (does the network require authent[/FONT][/SIZE][SIZE=4][FONT=courier new]ication?)[/FONT][/SIZE]

I also have (2) Ubuntu Server 14.10 x64 VMs running on a Windows Server 2012 R2 Hyper-V box (*dedicated Hyper-V only*) which are designated as internal DNS servers in my home network.  These VMs have no problem running *apt-get update*.

---

### Post by oldos2er on 2015-03-08
Moved to Virtualisation.

---

