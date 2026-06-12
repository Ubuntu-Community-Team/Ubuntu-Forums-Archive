---
title: "How to pass files from your computer to VirtualBox"
date: 2007-10-20
forum: Virtualisation
---

### Post by Fixman on 2007-10-20
Is there a way to pass files from your computer to the virtual PC you have using VirtualBox?

---

### Post by bodhi.zazen on 2007-10-20
Yes.

You can share a usb device / flash drive, share a partition, or use a network protocol (samba, nfs, ftp, http, scp, sshfs).

I find the network protocols work best ...

---

### Post by stephdl on 2007-10-20
it work 's fine with samba, but you can also guive a dhcp adress to your virtual pc, like if it was plugged on your network.
it's the Host Interface Networking and bridging on Linux hosts, you can see the documentation about this on the vbox's web site
it's good way if you want to run guest server  on your host

---

### Post by arnold.pietersen on 2007-10-20
Maybe just to follow-up on this question.

I have Feisty as the host and Win XP as the guest.  In Windows I have set up a network share and can see the Feisty partition with files and folders.  However, how do I see or set up a Windows share folder in Feisty?  Thus in Feisty I want to access the Windows share folder.

Thanks

---

### Post by stephdl on 2007-10-20
normally, you take the menu connect to a server in gnome, you choose window share, and you guive the hostname of your guest or the ip adress.
but you need to say to samba that all connexion about virtualbox are authorised on linux host.

[http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

you can find the documentation of virtualbox here, the chapter of network it is nice to learn share hosting.

---

