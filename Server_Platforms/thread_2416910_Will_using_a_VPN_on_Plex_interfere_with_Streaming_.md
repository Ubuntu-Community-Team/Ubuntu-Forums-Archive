---
title: "Will using a VPN on Plex interfere with Streaming capabilities?"
date: 2019-04-17
forum: Server Platforms
---

### Post by ejach2000 on 2019-04-17
Hello, I am running a Plex Media Server on Ubuntu 18.04.
I am thinking about using it with either Deluge or Transmission in the near future to torrent. The only thing that is holding me back from pulling the trigger is whether or not the streaming capabilities of Plex will be hindered if I use Deluge/Transmission behind a VPN.
I can provide any additional information if needed.
Thanks!

---

### Post by TheFu on 2019-04-17
Only if you stream outside the LAN when the VPN is active.
The LAN and hardware involved matters too.

Also, if you are running the VPN server or paying someone else will matter too.

---

### Post by ejach2000 on 2019-04-17
> **TheFu said:**
> Only if you stream outside the LAN when the VPN is active.
The LAN and hardware involved matters too.

Also, if you are running the VPN server or paying someone else will matter too.

Alright. So I would just be better off using another device to torrent?
I am just sick of constantly torrenting, and then FTP-ing the large files to my server.
Thanks for the reply!

---

### Post by TheFu on 2019-04-17
How many Linux ISOs do you need to torrent?
Nobody should be using plain FTP since around 1995. There are many convenient, secure, protocols.

---

### Post by ejach2000 on 2019-04-18
> **TheFu said:**
> How many Linux ISOs do you need to torrent? Nobody should be using plain FTP since around 1995. There are many convenience, secure, protocols.  I am VERY new to this, and that is all I know how to do &#129335;&#127996;*&#9794;&#65039; I'm open to any suggestions.

---

### Post by TheFu on 2019-04-18
There are NFS, sftp, scp, rsync, sshfs off the top of my head.
If the client is Windows, their is CIFS, sftp, scp, rsync - the sftp/scp tool most people use is WinSCP.

The ssh protocol is commonly used for Unix to Unix communications.  If you setup ssh-keys, then it is both more  convenient and more secure.  That never happen with anything else.  ssh is used by scp, sftp, sshfs and rsync between systems and it is considered secure enough for use over the internet.  They use encrypted methods for both authentication AND for the transferred data.

NFS can have encryption or not, depending on how you setup the server.  NFS is the native Unix-to-Unix network file sharing method. It is lower overhead and higher performance than other options.  It is probably best NOT to use it over the internet without a full VPN for non-experts, unless you setup the server-to-server Kerberos trust. That is a hassle.

I use rsync to mirror data directories between different systems. This is not a backup, but perfect for mirroring. Best of all, it can be automated with either push or pull methods.  Pull the files overnight, so you don't care how long it might take.

Of course, if you use a VPN to some external service provider, things can be more complex.  It depends on the network architecture.

---

### Post by slickymaster on 2019-04-18
*Thread moved to **Server Platforms**.*

---

### Post by ejach2000 on 2019-04-18
> **TheFu said:**
> There are NFS, sftp, scp, rsync, sshfs off the top of my head. If the client is Windows, their is CIFS, sftp, scp, rsync - the sftp/scp tool most people use is WinSCP.  The ssh protocol is commonly used for Unix to Unix communications.  If you setup ssh-keys, then it is both more  convenient and more secure.  That never happen with anything else.  ssh is used by scp, sftp, sshfs and rsync between systems and it is considered secure enough for use over the internet.  They use encrypted methods for both authentication AND for the transferred data.  NFS can have encryption or not, depending on how you setup the server.  NFS is the native Unix-to-Unix network file sharing method. It is lower overhead and higher performance than other options.  It is probably best NOT to use it over the internet without a full VPN for non-experts, unless you setup the server-to-server Kerberos trust. That is a hassle.  I use rsync to mirror data directories between different systems. This is not a backup, but perfect for mirroring. Best of all, it can be automated with either push or pull methods.  Pull the files overnight, so you don't care how long it might take.  Of course, if you use a VPN to some external service provider, things can be more complex.  It depends on the network architecture.  Thanks for the reply! I'll message around with the different ones you suggested.

---

### Post by TheFu on 2019-04-18
> **ejach2000 said:**
> Thanks for the reply! I'll message around with the different ones you suggested.

In my world, every system is running ssh-server and fail2ban.  ssh-server allows any ssh-based clients access.  fail2ban blocks brute force attacks. On your LAN, you can allow passwords, but over any untrusted network, like the internet, only allow keys.  There are specific settings in the sshd_config file to set up these things.  Also best to use ed25519 ssh-keys for added security.  Use ssh-copy-id to push public keys to the remote server.  If you need to hop from system to system to system, then you can use ssh-agent to pass credentials.

There's an entire world of ssh-based tools that Windows people know NOTHING about except, maybe, putty and winscp. Those are just the surface stuff.

If you are a programmer, ssh is used for all sorts of things.  git uses ssh, for example, so github, gitlab and all the git-based things do as well.

With rsync, you can control bandwidth used.            ```
  --bwlimit=RATE          limit socket I/O bandwidth
```
All these tools have manpages, so check those out for each command. The ssh manpage is a work of art.  ;)

---

