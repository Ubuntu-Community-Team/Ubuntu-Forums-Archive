---
title: "map to ubuntu server drive"
date: 2012-01-13
forum: Server Platforms
---

### Post by Xender1 on 2012-01-13
So I have an ubuntu server, I just added an external HD to it (ntfs), now on my mothers windows computer I would like to map a network drive to this ntfs hard drive so she can back up her files. I successfully mounted the ntfs drive to /mount/MasBackup. On the server doing ls on /mount/MasBackup i can see all the files that should be there, however when I try and map the drive using the correct directory path (name of server is serv1) \\serv1\mount\MasBackup  it says it cannot find the path, anyone have any suggestions?

---

### Post by Ryan Dwyer on 2012-01-13
You need to configure Samba to share that directory. You might be able to do it through Nautilus (file manager), or you can do it by editing Samba's config file.

---

### Post by volkswagner on 2012-01-13
Yes you will want to use SAMBA on your server to share with Windows Clients.

Check the sticky at the top of this forum, specifically for [SAMBA]("https://help.ubuntu.com/10.04/serverguide/C/samba-fileserver.html").

If you run into trouble after or during the setup.  Post your smb.conf file and ask away.

Good Luck.

---

