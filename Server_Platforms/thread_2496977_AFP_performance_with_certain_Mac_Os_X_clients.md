---
title: "AFP performance with certain Mac Os X clients"
date: 2024-04-18
forum: Server Platforms
---

### Post by kaynemo2 on 2024-04-18
I've been trying to figure this out, but I am at a loss...
I've got a file server running Ubuntu Server 22.04.4 LTS. It is serving a large network of various machines. Since most of them are macs of various ages, the protocol to go for me is AFP (Netatalk). Most of the time (BigSur, Sierra, Sonoma) machines are doing just fine. However there are a few machines (High Sierra for instance) that although connected the same way (dual ethernets) and via same switches and routers struggle with transfer speeds over AFP (and even more so over SMB). I have tried everything to figure out what could be the reason and can't. The difference in transfer speeds negotiating with the same Ubuntu server are drastic (Sonoma machine over wifi transfers the file in 5 minutes, while the High Sierra dual ethernet machine transfers the same file in an hour, Big Sur dual ethernet transfers the same file in less then 2 minutes). The weirdest part is if I connect to the same server from the High Sierra machine over sftp (seemingly a longer connection as it is made via Internet) that same forsaken file transfers lightning fast. Maybe someone can point me in the right direction, I can't seem to figure out what the problem is. I do feel it is a problem with the High Sierra, but can't figure out what that could be.

Any advice will be much appreciated.

UPD: As a result of a very strange course of events I figured out that the problem was in the WiFi that was enabled on that machine. And even though the service order was set to prefer Ethernet over WiFi, system didn't obey this rule. Turning off WiFi got everything flying as it should be... Stupid users :P

---

### Post by TheFu on 2024-04-19
Unix-based OSes should use NFS for network file sharing.  NFS mounts behave like local storage and are setup once for the entire client machine. All users on the client get access based on their normal Unix permissions, ownership and groups.

There is a client-uid mapping  -to- server-uid mapping program, but I've never needed it with my different Unix systems. However, I understand that 

MacOS doesn't start uids at 1000 like Linux does, so you'll either need to get that mapping working or change the UIDs for all clients so they match across all the client systems.  In a corporate environment, this happens automatically because centralized user management happens, usually via LDAP.  If you aren't using LDAP for your human authentication, just know that the UID and GID need to map or match across all the client systems.

Plus, if you use NFS, all your Unix client systems use that natively with just 1 package install for Linux - nfs-common.  I believe performance of NFS is better than all other network file protocols too.  If the machines aren't always connected to your LAN, then you'll want to use mount options that either won't mount until actually requested or have a shorter timeout so users don't feel like their system stopped working until the default timeout ends.  autofs makes that possible on Linux. There must be something equivalent for MacOS.  In the old days, the daemon was called amd - auto-mount-daemon.

Ah ... a TCP/IP connection ARE mandatory between the clients and server. The better that connection, the better the performance.  When using wifi with poor connectivity, all network performance will be impacted. It is always best to use wired, fast, ethernet, when possible.

---

### Post by Morbius1 on 2024-04-19
This is just a general question should you have nothing else to do ........

Since MacOS no longer supports AFP on it's server end replacing it with their own version of Samba since Big Sur are you planning to migrate everyone to use SMB. 

The default client protocol became smb since Mavericks I think and there still is an afp client but I wonder how long apple will support that.

Just curious.

---

