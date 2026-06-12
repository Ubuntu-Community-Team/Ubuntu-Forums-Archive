---
title: "Password-protect a folder"
date: 2018-12-30
forum: Security
---

### Post by jonathanese on 2018-12-30
Currently, I have an ubuntu 18.04 server that I'm using as my fileserver and gateway (is this a bad combination?)

I have some data that isn't particularly sensitive but I want it password-protected. It's a really large folder, if you catch my drift.

Anyway, I currently have this data stored in a 64GB Veracrypt file that has to be mounted as a virtual drive. This was the only way I saw to protect it. But this has to be resized now and again and is prone to corruption which causes all the data to be inaccessable.

Note that this is being accessed over a network.

Is there a way that this data could be stored in a folder that just needs a password to access (both on the server and on the client PC)? The client PC is Windows-based so I'm using a Samba server to host the data.

---

### Post by TheFu on 2019-01-01
> an ubuntu 18.04 server that I'm using as my fileserver and gateway (is this a bad combination?)
Yes. Routers should perform routing and firewalling.  It is too easy for a misconfiguration to allow all the storage to be available to anyone on the internet by accident.
> 
I have some data that isn't particularly sensitive but I want it password-protected. It's a really large folder
No "drift" needed.  It is your data, so you should provide access only to people you consider worthy.  For internet access, I'd use sftp.  For LAN access, I'd use NFS.  Normal file+directory permissions should be sufficient for network access control using those 2 protocols. You can encrypt the underlying partition using mdcrypt + LUKS if you like.  The tool to do this is called **cryptsetup**.  It works on a partition or LV level, not on top of a file system.  There are tools like encryptfs or encfs which do work at the directory level, but both of those have poor performance and can leak metadata about the files.  Both have been removed from default use in Ubuntu.

I wouldn't use Veracrypt unless I absolutely needed cross platform support (booted by different OSes).  If you only need network access and Linux is the host, then I'd stick with LUKS.

Windows ... ewwww.  I feel dirty.  Use WinSCP to access the files using the sftp protocol, especially over the internet.  If you trust the LAN, you can use Samba/CIFS, but it won't play nice with encryption at the directory level.  Stick with partition or LV level encryption and Samba won't know the difference provided the storage is unlocked  and mounted.

You didn't mention internet access, but when accessing files over the internet, ssh-based tools like scp, sftp, rsync, sshfs, or 50 others should be used with ssh-keys, never passwords.  Passwords are a security failure. Use keys.  **ssh keys are one of the only things I know which are both more convenient AND more secure.**

If you must use samba over the internet, then you'll need to use it inside a full VPN like openvpn. There are huge performance problems doing this.  If you can, use a Linux client.  There are just so many other options for secure storage access from Linux clients to linux servers.

---

