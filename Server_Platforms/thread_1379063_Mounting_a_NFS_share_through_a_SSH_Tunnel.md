---
title: "Mounting a NFS share through a SSH Tunnel"
date: 2010-01-12
forum: Server Platforms
---

### Post by cdog2800 on 2010-01-12
Hi, I have a server at my home which is a Ubuntu 9.1 which is setup as a NFS server using NFS v3. I am also using DYN DNS to access my home server remotely from another location using SSH. Everything works good, I can sucessfully log in to my server from my laptop via SSH, however my problem mounting my NFS share  which consists of appx. 300 mp3 files. My question is:

1 How Do I Tunnel a NFS share through a SSH tunnel?

2 Is there any other configuration? needed to be done to the router?

3 is there anything needed to be configured to the server or my laptop?

4 Manual mounts is fine for me I don't care about automounting.

I just want to be able to mount the NFS share via the SSH Tunnel and play my music and access other files from my server.
I just need the steps to set up this connection.

Any help will be greatly appreciated.

---

### Post by noway2 on 2010-01-12
I don't know the steps off hand, but one solution would be to VPN over the SSH.  From what I recall, it isn't the most efficient VPN method, but it will work.  There is some Ubuntu community documentation that describes how to do this: [https://help.ubuntu.com/community/SSH_VPN](https://help.ubuntu.com/community/SSH_VPN)

---

### Post by Lars Noodén on 2010-01-12
You'll need to track down all the ports used and tunnel those.  The **-L** argument to the ssh client can be repeated as many times as necessary.  

```

# this is not enough, but shows the idea
ssh -L 111:localhost:111 -L 2049:localhost:2049 homeserver.example.org

```

Once you know which ports, you can make a special entry for that host in ~/.ssh/config to automatically forward them when connecting

It may be necessary to force some ports to specific values just so that you can predict them:

[http://www.lowth.com/LinWiz/nfs_help.html](http://www.lowth.com/LinWiz/nfs_help.html)


Another option is to try [sshfs](http://manpages.ubuntu.com/manpages/karmic/en/man1/sshfs.1.html) which uses sftp to set up access to the remote system as a mount point on the local file system.  Since you already have an ssh connection possible, that may be the easiest.

---

