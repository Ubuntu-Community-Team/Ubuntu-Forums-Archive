---
title: "Desktop Apps and working with files on a LAN."
date: 2019-06-20
forum: Server Platforms
---

### Post by knoppys on 2019-06-20
Good afternoon. 

Forgive me for not posting much about my system but Im not sure where to look for what you'd be asking so feel free to request anything you need. 

Im a web developer and I have a a workstation running Ubuntu 16 and I have a HP Server in my office running Ubuntu Server 16. Basic LAMP Stack.

I access my files on the server through Nautilus using bindfs which allows me to connect by via ftp to the files on the server. This is great because it means I can run a working developmetn environment without any heavy lifting or large websites on my local machine. 

The only problem I have which is really holding me back with when I try to run programs like VSCode and its own git extension. To do this I need to open the folder and VSCode can not see the directory in the file dialogue. In short all these programs want to see a local directory, not a remote one. 

How can I go about setting up the link between my server and my desktop so that the filesystem on the remote works the same as a local file system. 

In windows I would have used something like mapping a network drive. 

TIA

---

### Post by knoppys on 2019-06-20
To give some further info:
I just ran VS Code and I got the following error when trying to use their SASS compiler. 
[COLOR=#F8F8F2][FONT=&amp]
[/FONT][/COLOR]Error:
-29
undefined
ESPIPE: invalid seek, write[COLOR=#F8F8F2][FONT=&amp] invalid seek, write
[/FONT][/COLOR]

---

### Post by TheFu on 2019-06-20
sshfs, but it will be a little slower than a full NFS mount.  Using NFSv4 over the internet requires a complex Kerberos system-to-system trust setup and encryption. I've never attempted that.

If you want an FTP-like interface, use sftp.   Pretty much all Linux file managers support the sftp:// URL or ssh:// URL. Just depends which file manager you use.

To setup ssh credentials you don't use key-based authentication, do this from the client:
```
ssh-keygen -t ed25519
ssh-copy-id -i ~/.ssh/id_ed25519.pub userid@remote
```
and if you want to setup aliases for internal access different from external access, then use the ~/.ssh/config file for those.  Very handy.

Obviously, the openssh client and server need to be installed on the 2 systems.  While you are there, probably want to install fail2ban to block brute force attacks.  There are a few other ssh security tips, but you can look those up.
ssh is used by  ssh, scp, sftp, rsync, rdiff-backup, git, virt-manager, libvirt, vim and 50 other tools.  All of them support the ~/.ssh/config file settings.

If the systems are on the same trusted LAN, definitely use NFS.  NFS rocks. Storage and permissions all work like locally connected disks.

Don't use plain FTP,  er .... ever.  Anywhere.

---

### Post by knoppys on 2019-06-20
One more thing, Im connected to the server in nautilus via FTP.

---

### Post by knoppys on 2019-06-20
Ok so just a quick one, the server is on my office and isnt accessible to the public. We are a building of shared offices and each office has their own IP range on LAN. 
So my server is on 192.168.0.40 and my desktop is on .41
So you think that connecting via ssh will give my desktop programs access to the files system on the remote server and not just in nautilus.

---

### Post by TheFu on 2019-06-20
sshfs.  Let's be clear.

But if the systems are on a trusted LAN and connected via trusted LANs, use NFS.

Both methods make remote storage available to the local machine. They aren't tied to any GUI. Both are file system to file system.  Both require you to umount the storage you mounted previously before disconnecting, though shutting down or rebooting the client will accomplish the same, safely.  Do not just unplug and walk away. That will likely cause file corruption, as it would with any file system.

NFS mounts can be added to the /etc/fstab from the client, provided the NFS server is setup already. NFS is system to system sharing, not userid to system.  Everyone can access the storage over the NFS mount.  If you only want the NFS storage available on-demand, use autofs on the client.  The nfs-server setup is the same regardless.
sshfs only needs ssh access to work. It is for one userid, not the entire system.

Since 2005, nobody, nobody, nobody, should be using plain FTP for anything.

---

