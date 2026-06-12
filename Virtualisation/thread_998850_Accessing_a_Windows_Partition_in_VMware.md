---
title: "Accessing a Windows Partition in VMware"
date: 2008-12-01
forum: Virtualisation
---

### Post by cforput on 2008-12-01
I have searched the forums but haven't found how to do this: I want to access a Windows partition inside my VMWare. I have found how to set up a share within my Ubuntu partition but that isn't what I need.

Here is my HD configuration:

Partition 1 = Windows Vista (Yuk! I try not to use this ever)
Partition 2 = Windows NTFS (I think) partition Called DATA in Win and media/DATA in Ubuntu
Partition 3 = Ubuntu 7.10 partition
Partition 4 = VMware partition (VMware-server-2.0.0-122956.x86_64)inside Ubuntu

Not knowing what I was doing when I set up Ubuntu, I set up partition 2 in order to share files between Windows and Ubuntu. It works fine if I use my primary Vista partition but I want to access it using VMWare. I haven't found any help on accessing a Windows partition in VMware. I set up a data store off of my laptop in inventory but couldn't figure out how to set up a datastore (called VM-XP)off of my VM machine as some instructions mentioned. 

I am using NAT for my network. 
Samba is installed and I can see my printer shares under My Network Places in VMware.

Any help would be greatly appreciated.

---

### Post by HermanAB on 2008-12-01
I'm not sure what your host is but if you just want to share the occasional file, then it is hard to beat good old FTP.  There are various simple free FTP servers for Windows, including FileZilla.

---

### Post by bodhi.zazen on 2008-12-01
As an alternate to FTP there is always Samba (or NFS or SSHFS (winscp on windows). The point is you can share the directory fairly easily with a network protocol.

---

### Post by cforput on 2008-12-01
I have Samba installed so I guess I just need some help with getting it set up. I have Ubuntu as the primary OS and then VMWare to set up XP. How do I set up a datashare to a different partition. I can't figure it out. I have found directions on how to share a folder in Ubuntu but I haven't found any directions on how to set up a datashare to a completely different partition.

---

### Post by bodhi.zazen on 2008-12-02
Open nautilus

navigate to the share, say "/meida/foo"

In the media directory, right click on the directory "foo" and select sharing options from the pull down menu.

On windows mount a network share :)

---

### Post by fjgaude on 2008-12-02
Also you will need to set passwords for Samba, like so:

```
sudo smbpasswd -a <name>
```

It'll ask for the Linux password for that name, then in Windows you can get into the shares.

---

