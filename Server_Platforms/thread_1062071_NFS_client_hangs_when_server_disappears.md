---
title: "NFS client hangs when server disappears"
date: 2009-02-06
forum: Server Platforms
---

### Post by tbraun on 2009-02-06
Hello!

I'm not much of an NFS expert, but maybe someone here can please help me?

I have an NFS server (running Xubuntu 8.10). The client is my laptop (Ubuntu 8.10). So, the server exposes a directory via NFS, which the client can mount and write to. For what it's worth, the command I issue on the client to mount the NFS share is:

[INDENT][FONT="Courier New"]sudo mount -t nfs server_ip_addr:/DATA /BACKUP -v -w -o rw,rsize=32768,wsize=32768,intr[/FONT][/INDENT]

However, when I power down the server without first unmounting on the client, the client will enter a state where some operations will just hang indefinitely.

For example, the 'df' command on the client, which showed the NFS mount as one of the available file systems before. If I power off the server but forgot to unmount on the client then 'df' will just hang trying to get information about that mount, which now has disappeared. It won't time out either. It will seemingly just hang forever.

There is a process called 'nfsiod' running on the client. I tried to kill it, even kill -9, but it doesn't want to go away. 'df' and any other accidental accesses to the mounted path will hang indefinitely.

The only way I have found to get the client out of the state is to reboot it. That doesn't seem to be right! The NFS client should detect that the server has disappeared and should eventually time out. Or I should have a command to force-unmount or reset the NFS client somehow.

Does anyone know what to do, please?

Thank you very much...

---

### Post by kpatz on 2009-02-06
Add "soft" to the -o options in your mount command or fstab.

[INDENT][FONT="Courier New"]sudo mount -t nfs server_ip_addr:/DATA /BACKUP -v -w -o rw,rsize=32768,wsize=32768,intr**,soft**[/FONT][/INDENT]

---

### Post by sd@ksu on 2012-03-15
Does not work...may be an upstart job at boot with respawn and expect fork (but with exact number) will work. But I am not sure about the fork thing..

---

