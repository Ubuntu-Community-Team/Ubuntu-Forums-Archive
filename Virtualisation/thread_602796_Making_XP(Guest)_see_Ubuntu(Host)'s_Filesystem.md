---
title: "Making XP(Guest) see Ubuntu(Host)'s Filesystem"
date: 2007-11-04
forum: Virtualisation
---

### Post by Folk Theory on 2007-11-04
to make it short:
I Installed virtualbox on my ubuntu 7.10
i added an windows XP guest

i installed and it works fine but i CAN'T ACCESS my linux files from it, so,
how do i make windows see its host's files?

Thanks in advance,

---

### Post by Mike'sHardLinux on 2007-11-04
You can install the Samba server software on the Ubuntu host. Then tell it which folders you want to share. In Gutsy, this is pretty easy. Look in System -> Administration -> Shared Folders.

After you have Samba running on the host, your windows guest should be able to browse to the host's shares.

One more thing, in order for the guest to be able to see the host, they both should be on the same subnet. I use VMware, not VirtualBox, so I don't know if this is already set up by default. Just thought I'd mention it.

---

### Post by Folk Theory on 2007-11-04
i did this and somehow it still can't browse them...
any ideas why?

---

### Post by Mike'sHardLinux on 2007-11-04
There are a few things you can check.

1) Make sure the Samba service is actually running on the Ubuntu host. At the command line, type: sudo /etc/init.d/samba start
Also, for the future, in System -> Administration -> Services, be sure "Folder sharing service (samba)" is checked so that it will always start automatically, unless you don't want it to.

2) Your firewall could be interfering. IIRC, you have to open ports 137, 138, 139 and 445 for windows file-sharing to work properly.

3) Sometimes, if the host and guest are not in the same workgroup, they may have trouble seeing each other. This is not usually the case. You can try to connect to the host by browsing to \\<host's ip address> in windows explorer. Anyway, you may want to make sure they are in the same workgroup.

4) I almost forgot, after you share the folder(s), depending on how Samba is setup, you probably need to create a Samba user/password. At the commandline, type sudo smbpasswd -a <username> . Then, on the windows guest, when you browse to the host, it'll ask for the username/password.

5) One other possibility is that the permissions on the shared folder on the host may not be allowing the share to be seen on the network.

Hope this helps!

---

### Post by eagledrc on 2008-03-11
I need help on something related...
[http://ubuntuforums.org/showthread.php?t=718060](http://ubuntuforums.org/showthread.php?t=718060)

---

