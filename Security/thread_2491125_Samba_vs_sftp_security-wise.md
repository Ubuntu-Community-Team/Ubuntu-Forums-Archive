---
title: "Samba vs sftp security-wise"
date: 2023-09-26
forum: Security
---

### Post by jmbernadet on 2023-09-26
Hello

I am mounting folders from VMWare to Ubuntu Server in read-only mode and sharing over sftp. I have configured my router. I can access my files from my iPhone.


I would like to mount those shares on my MacBook '11. Would you advise against also sharing over Samba, from a security point of view? Would NFS work? Is it hard to configure?


Thanks by advance.

---

### Post by TheFu on 2023-09-27
There are different reasons to use each method.

sftp isn't a "mount", so it is used to copy files between systems and provided you use key-based authentication, never passwords, it is secure enough for use over the internet.  There are other ssh-based tools and methods which are often easier to use than sftp.  For example, I'll use **rsync** for multiple directories or **scp** for a single file. These are much easier to use than sftp, but come with exactly the same encryption and authentication.

NFS has many options including server-to-server Kerberos tickets and key-based encryption.  The main trick for NFS to work easily is that the uid and gid on all systems need to match.  Those are the numbers, not the names, when you run the 'id' command on any Unix-like OS.  NFS is the native way to make remote storage available locally and it works really, really, well. Very few, if any compromise.  But depending on how well your network and servers are managed, it may not be as easy to use, since it is server-to-server, not end-user -to- server.  NFS can be run without Kerberos or keys.  I run it this way on my LAN, but never attempt any access over the internet or from any other subnet.  If your Macbook is running a currently supported Linux, you shouldn't have issues.  Just be certain the uid+gid match and that both servers have static IPs.

NFS v4 has been around about 20 yrs now, so it is a very stable protocol and well understood.

CIFS is the least secure of all these protocols.  I'd say to only use CIFS if you have MS-Windows systems AND only provide it for those systems to access storage. Unix-based systems should use NFS or sshfs or pretty much anything except CIFS.  MSFT is constantly tweaking CIFS and perhaps in 20 - 40 more years, they will get it right.  The last 10 yrs, the CIFS protocol that MSFT uses has changed drastically and many connections were broke due to those changes.

Is NFS hard to configure?  That depends on your skills and if your systems all have the required setup.  Normally, it is 1 install package command on the client and server, followed by editing a config file on the server and modifying the /etc/fstab on the client, then restart the nfs-server daemon (there's another way, but I just restart the daemon) so the specific shares are available to the specific client(s).  Takes about 3 minutes.  OTOH, I'm not doing all the Kerberos stuff and my systems all have static IPs because I believe in a well-run network.  If you have different beliefs, YMMV.

---

### Post by jmbernadet on 2023-09-27
Thanks a lot for your precise and exhaustive answer.

---

### Post by Morbius1 on 2023-09-27
Here is a test share I just created:
```
[Test]
path = /srv/Test
read only = yes
guest ok = no
```

I'm going to access it with an antique MacBook and check it's status on the Samba server:
> vxub2204:~$ sudo smbstatus

Samba version 4.15.13-Ubuntu
.....
.....

Service      pid     Machine       Connected at                     **[COLOR="#0000CD"]Encryption[/COLOR]**   Signing     
---------------------------------------------------------------------------------------------
Test         7377    192.168.1.234 Wed Sep 27 08:08:24 AM 2023 EDT **[COLOR="#0000CD"] - [/COLOR]**           AES-128-CMAC

Password are passed encrypted but data transmission is not.

Now I will change the share definition to force encrypted transport:

> [Test]
path = /srv/Test
read only = yes
guest ok = no
server smb encrypt = required

Reconnect from the MacBook and again check it's status:
> vxub2204:~$ sudo smbstatus

Samba version 4.15.13-Ubuntu
.....
.....

Service      pid     Machine       Connected at                     **[COLOR="#0000CD"]Encryption[/COLOR]**   Signing     
---------------------------------------------------------------------------------------------
Test         7488    192.168.1.234 Wed Sep 27 08:15:23 AM 2023 EDT  **[COLOR="#0000CD"]AES-128-CCM[/COLOR]**  AES-128-CMAC

Data transfer is encrypted.

---

### Post by TheFu on 2023-09-27
> **jmbernadet said:**
> Thanks a lot for your precise and exhaustive answer.

[https://learn.microsoft.com/en-us/windows-server/storage/file-server/smb-security](https://learn.microsoft.com/en-us/windows-server/storage/file-server/smb-security) explains MSFTs attempts to increase security with smb 3.x.

And to be fair, NFS without Kerberos relies on strict IP address management and doesn't have any encryption built in. Besides enabling Kerberos and built-in NFSv4 encryption some sites that want encryption might setup an overlay grid VPN or use TLS in a way that plain FTP or HTTPS uses it.  It is a judgement call.  
[https://ubuntu.com/server/docs/service-nfs](https://ubuntu.com/server/docs/service-nfs) has details. The top half is what I do.  The bottom half has Kerberos signing and 128 or 256-bit AES encryption instructions.  I figure when I need to transfer data like that, I'll use ssh-based tools, like rsync, sftp, scp, or 50 others.

SMB 3.x is certainly easier to deploy with encryption. The real problem is that passwords tend to be used, which has been considered a failure of security for nearly 10 yrs.  Password based authentication should be avoided, especially if end-users get to choose the passwords.

Back when I had a MacOS system for about 3 weeks (returned it before my frustration caused massive breakage), the implementation between MSFT, Samba, and Apple was broke. I think the main problem with using NFS was that Apple uids started at 500, not 1000. Seems trivial and there is a uid+gid mapping tool for NFS that should address that.  The other alternative is to have centralized user and group management via LDAP, but that's a different thread, completely.

---

