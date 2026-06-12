---
title: "How to copy files from local machine to server using SSH file transfer protocol?"
date: 2012-01-11
forum: Server Platforms
---

### Post by lohpenwei on 2012-01-11
Hi all,

now I'm using Ubuntu Server 10.04 LTS, I hope to transfer some files to the server using my local machine through SSH / puTTy. 
anyone know how? 
Thanks

Best Regards..

---

### Post by Lars Noodén on 2012-01-11
If you are just transferring files from a directory or two, then SFTP will work.  It is part of SSH, so you have it already if you have SSH.  There are SFTP clients built into FileZilla, Nautilus, Dolpin and quite a few others.  

If you are planning on transferring a large number of files from a large number of directories, then [rsync](http://en.wikibooks.org/wiki/OpenSSH/Cookbook/Automated_Backup#Backup_with_rsync) is the way to go.

---

### Post by raja.genupula on 2012-01-11
Few more information you can findout at [http://stackoverflow.com/questions/2810774/how-to-copy-files-from-local-machine-to-server-using-ssh-file-transfer-protocol](http://stackoverflow.com/questions/2810774/how-to-copy-files-from-local-machine-to-server-using-ssh-file-transfer-protocol)

---

### Post by pakkya on 2012-01-11
> **lohpenwei said:**
> Hi all,

now I'm using Ubuntu Server 10.04 LTS, I hope to transfer some files to the server using my local machine through SSH / puTTy. 
anyone know how? 
Thanks

Best Regards..

use scp command..

scp urfiles serverusername@ip:/location u want to store..

use -r option if u got any problem

---

### Post by Drenriza on 2012-01-11
#1
From local machine.
scp user@server:/file/location . 
Remote machine.
scp user@server:/file/location /where/to/place/

Downloades / uploades a single file (not a directory) and place it on the local machine.
use -r in scp to download a directory that contain files.
---------------------------------------------------------------------------
#2
From local machine.
ssh -f user@server "scp /path/to/file/ remoteUser@remoteServer:/location/to/place/file"
---------------------------------------------------------------------------
#3
From local machine.
rsync -a -r -z -v --progress --partial -e ssh USER@IP:/source/ /destination/

from remote machine.
rsync -a -r -z -v --progress --partial -e ssh /source USER@IP:/destination

Rsync is better to bigger files. Since if the link goes down, you dont need to download the entire thing again. It continues from where it left the download. From before the link went down.

Kind regards.

---

