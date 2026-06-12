---
title: "Mounting directories via NFS from 12.04 Server extremely slow"
date: 2012-08-09
forum: Server Platforms
---

### Post by darius.k on 2012-08-09
Good morning everyone,

I have an NFS-Server running 12.04. For its setup I followed these guides:
[https://help.ubuntu.com/community/NFSv4Howto](https://help.ubuntu.com/community/NFSv4Howto)
[https://help.ubuntu.com/community/SettingUpNFSHowTo#NFS_Server](https://help.ubuntu.com/community/SettingUpNFSHowTo#NFS_Server)

/etc/exports
```
/srv/teams/ 192.168.0.0/21(rw,sync,no_subtree_check)
```

/etc/fstab (Server)
```
(...)
/home/users /srv/teams none bind 0 0
```

Mounting the NFS shares generally works flawlessly. But I want to store the user's home directories on the server, which is, I believe, a fairly common usage for NFS.
So I went ahead and added the following line to the /etc/fstab on the client workstations.

/etc/fstab (Client)
```
192.168.1.254:/srv/teams /home/users nfs4 rw,hard,intr,nolock,auto,noatime,rsize=32768,wsize=32768 0 0
```

First I stumbled across [Bug #870874 „LDAP user with automounted nfs homedir cannot login“]("https://bugs.launchpad.net/ubuntu/+source/at-spi2-core/+bug/870874") (also concerns non-LDAP systems), but using the workarounds from the comments, I could deal with that.
Now login works on the client workstations, but it takes multiple minutes to get to the desktop and performance there is horrible, even though server and clients are fairly good.
The network is 100BASE-T; the client is connected via a switch to the server and there are no other devices connected to the network. The server contains 5 network cards, each interface is ought to contain one subnet with clients attached via a switch. Currently only one NIC is used (eth1, 192.168.1.254), all others are disabled (via ifconfig eth0 down, ifconfig eth2 down, etc.).

Running nfsstat, I saw that there were 300+ retrans, but I couldn't find the configuration file to increase the number of nfsd threads, plus I'm quite stunned that my setup performs that bad with just the server and one client on a 100Mbit/s network.

The server is an i3, with 16GB RAM, the HDDs are a RAID0 of two WD Velociraptors.

Is there anything obvious that I'm missing? Have anyone of you had similar problems before? Maybe you could point me to some good resources that might help me.

Thanks for your time :)

---

