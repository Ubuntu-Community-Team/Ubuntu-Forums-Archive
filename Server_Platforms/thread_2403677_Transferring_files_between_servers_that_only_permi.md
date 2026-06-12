---
title: "Transferring files between servers that only permit public key authentication"
date: 2018-10-14
forum: Server Platforms
---

### Post by Robert_Boutin on 2018-10-14
I'm sure this has been asked already but I can't find where.

My servers don't permit password login as they are exposed to the world.  I am fine when I am SSHing into my servers from my laptop using PUTTY with my locally stored private key, but I am having a problem trying to transfer data between servers.  I can temporarily enable password authentication but I'm afraid I may forget to disable it when I'm finished.  I know I can store my private key on my servers to allow them to authenticate as needed.  I thought I just needed to place my private key in my .ssh folder alongside my authorized_keys file but that's not working.  I've been searching to see if I have a permission problem, a naming problem, an sshd_config problem, or some altogether different problem but haven't had any success.

Can somebody point me to a tutorial that explains how to set up public key authentication for server to server file transfers?

Thanks

---

### Post by wildmanne39 on 2018-10-14
*Thread moved to **Server Platforms for a more appropriate fit**.*

---

### Post by TheFu on 2018-10-15
NEVER put a private key anywhere except on the client system where it was created OR on an off-line backup drive (flash).  If you put it on the server, you've just given the "keys to the kingdom away".

Servers should only have the public key.  On Unix, use the ssh-copy-id program to push the correct public file to the right place, with the right permissions.

From Windows clients, if you have ssh-keys working, there is a program, I think it is called pscp.exe that should use those keys to support transfers.  I'd expect WinSCP which is an scp/sftp client to work with the same keys (just put the private key where winscp says it is needed).

Private keys stay on the client.  Each client machine should used a different set of keys.  You can have multiple keys for different or the same purpose.  On Unix client systems, ssh key management is much easier thanks to ssh-copy-id and the ~/.ssh/config file.
There should be no need to touch the /etc/ssh/sshd_config file unless you want to alter settings like forcing the use of keys, limiting client-IP access, or blocking access to sftp, scp from ssh-only clients.  From Unix clients, you can ask for more logging output using the -vvv options. More 'v's adds verbosity.  

Sorry, but I don't have many details about Windows. Just don't use it enough.

---

### Post by SeijiSensei on 2018-10-15
rsync will use SSH with your keys to do file transfers.  You'd need to have a corresponding entry in /root/.ssh/authorized_keys on the backup server if you need root permissions.

---

