---
title: "Can Samba on Linux integrate well with Mac OS X workstations?"
date: 2016-11-28
forum: Server Platforms
---

### Post by danielclements on 2016-11-28
I have around 15 workstations, both Mac and Windows machines connected to a Ubuntu Linux fileserver running Samba. There seems to be an issue that the Macs are not inheriting the explicit file and directory permissions set in the Samba config file (they are ignoring group permissions). I don't know whether the problem lies with the Macs' Samba implementation or the Samba config, or maybe both. Any help on this would be greatly appreciated. Thanks

---

### Post by TheFu on 2016-11-28
OSX is Unix. Why not use NFS for those clients?  Things will "just work" that way. NFS is the native network file service for all Unix systems.  Owners, groups, permissions will all be native (though root from client systems is rejected on NFS storage by default).  Only trick is to centralize the passwd/group files (and user accounts) so they all match across all systems. You'll need to migrate them on each system, if that isn't already the situation on your network.  Then use samba/CIFS only for those workstations that need it - Windows.

I need to say that I've only run OSX for a few weeks before returning the system (samba on OSX had a bug for a few weeks that broke it completely), but it is Unix underneath and should have native support for NFS.
[https://www.cyberciti.biz/faq/apple-mac-osx-nfs-mount-command-tutorial/](https://www.cyberciti.biz/faq/apple-mac-osx-nfs-mount-command-tutorial/) appears as a reasonable OSX for NFS how-to. Looks like Unix to me - that is a good thing.

---

### Post by Morbius1 on 2016-11-29
Why not post the output of the following command so the folks here can see how the Linux Samba server is set up:
```
testparm -s
```
I have a Linux / MacOS network here and use Samba primarily because Samba ( by another name ) is the default file sharing mechanism in MacOS these days. If I can see how you are set up perhaps I can reproduce your problem.

---

### Post by TheFu on 2016-11-29
Morbius can definitely help getting SMB to work if that is the need for your clients.

Don't know if this helps or not: 
* [https://apple.stackexchange.com/questions/19470/nfs-afp-smb-advantages-and-drawbacks-on-a-mac-os-system](https://apple.stackexchange.com/questions/19470/nfs-afp-smb-advantages-and-drawbacks-on-a-mac-os-system) Appears that Apple's SMB/CIFS clients weren't very good at some point in 2016.
* [https://serverfault.com/questions/460795/sharing-folder-from-linux-to-mac-samba-or-nfs](https://serverfault.com/questions/460795/sharing-folder-from-linux-to-mac-samba-or-nfs)

The *tyranny of the default* isn't always the best choice for all situations, though it often is good-enough.

---

