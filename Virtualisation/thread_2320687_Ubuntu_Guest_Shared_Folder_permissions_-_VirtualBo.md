---
title: "Ubuntu Guest Shared Folder permissions - VirtualBox"
date: 2016-04-16
forum: Virtualisation
---

### Post by tppund on 2016-04-16
I have mounted a folder from my Host machine (Win10) on my Ubuntu 15.10 guest. After using virtualbox dialogues to pair the folders I have placed the following mount dialogue in /etc/rc.local.  It works, but the permissions within the shared folder are all set to chmod 777. I receive an "invalid mode" error when trying to set with "sudo chmod -R 755 */". 

```
sudo mount -t vboxsf -o uid=tpund,gid=tpund Source /home/tpund/Source
```

I'm aware that the mount command is blocking my attempts to change the permissions on the shared files, I just can't find the correct mount command to use to achieve chmod 755 permissions.

Any help would be appreciated.

---

### Post by howefield on 2016-04-16
Thread moved to the "*Virtualisation*" forum.

---

### Post by tppund on 2016-04-16
Answering my own question, I got the answer on the #ubuntu IRC channel.

the mount command changed to: [COLOR=#000000][/COLOR]```
sudo mount -t vboxsf -o uid=1000,gid=1000,umask=0022 Source /home/tpund/Source[COLOR=#000000][/COLOR]
```did the trick.

---

### Post by TheFu on 2016-04-16
But that doesn't make chmod work.  For that, you need to perform win-uid to unix-uid mapping. There is a way to do that for samba. Not sure how much of CIFS virtualbox implements. [https://www.samba.org/samba/docs/using_samba/ch09.html](https://www.samba.org/samba/docs/using_samba/ch09.html) scroll down to the username map section.

Of course, if you only need to allow access for 1 userid, there are easier answers.

If you have solved this, please mark the thread as solved in the thread tools to save time for others.

---

### Post by ajgreeny on 2016-04-16
Assuming you as user are a member of the group vboxsf in your guest Ubuntu OS and you have set up the folder to automount in the VBox manager there should be no need to do anything more, as far as I'm aware.

I have 6 VMs in VBox 5.0.16, 5 of which are Linux distros and the sixth is WinXP, and all of those manage the shared folder with no work required by me to change permissions.

I am using Xubuntu 14.04 as host, not Windows, but I'm not sure that should make any difference to this problem of yours

---

