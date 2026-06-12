---
title: "NFS mount in /etc/fstab causes mountall plymouth command failed"
date: 2014-02-18
forum: Server Platforms
---

### Post by James_Short on 2014-02-18
I have a NFS share that I want mounted at boot time:

hostname:/vol_jenkinstools_x64linux /mnt/data/jenkinstools nfs hard,rw,nointr,rsize=32768,wsize=32768,bg,vers=3,tcp 0 2

However, in my VMware console, I see the message:

"mountall plymouth command failed"

I can hit enter and log in as usual and df -h shows that the mount is performed.

I found a few threads about this messages and it seemed to be about GUI related things but this is ubuntu server 12.04 (not desktop).

If I comment that mount in /etc/fstab, I do not see that message so it's something related to that mount.  

Thoughts?

---

### Post by James_Short on 2014-02-20
No one?

---

### Post by SeijiSensei on 2014-02-20
Do you have the system configured to start the network at boot time, or must it wait until you've logged in so that Network Manager makes the connection?  If the latter, then it's likely the problem is just one of sequencing.  The mount command during boot cannot mount the NFS share because the network is not available.  Once you log in and launch the network connection, the mount takes place.

---

### Post by James_Short on 2014-02-21
In /etc/network/interfaces I have this interface set to auto:

auto eth1
iface eth1 inet static

Wouldn't that mean they are turned on at boot time?  If not, how do I get the interface to start at boot time?

---

### Post by SeijiSensei on 2014-02-21
What about eth0?  That's the identifier for the primary network interface.  There shouldn't be an eth1 unless you have two network adapters.

Unix numbers pretty much everything starting from zero.

---

### Post by nerdtron on 2014-02-23
```
hostname:/vol_jenkinstools_x64linux /mnt/data/jenkinstools nfs hard,rw,nointr,rsize=32768,wsize=32768,bg,vers=3,t  cp 0 2
```

Have you tried using IP address instead of hostname in the fstab entry?
What is you /etc/network/interfaces and /etc/hosts file?

---

### Post by James_Short on 2014-02-24
> **SeijiSensei said:**
> What about eth0?  That's the identifier for the primary network interface.  There shouldn't be an eth1 unless you have two network adapters.

Unix numbers pretty much everything starting from zero.
I have 2 interfaces (one for a 10.x.x.x network connection and one for my 172.x.x.x VLAN network).  The NFS host is on the 172 network.

Also, I am using the IP address actually, same behavior.

---

### Post by brokenhachi on 2014-02-25
I think the problem is that the system reads /etc/fstab before it reads /etc/networking/interfaces

> The fourth field, (fs_mntops), describes the mount options associated with the filesystem.

It is formatted as a comma separated list of options. It contains at least the type of mount plus any additional options appropriate to the filesystem type. For documentation on the available options for non-nfs file systems, see mount(8). For documentation on all nfs-specific options have a look at nfs(5). Common for all types of file system are the options ``noauto'' (do not mount when "mount -a" is given, e.g., at boot time), ``user'' (allow a user to mount), and ``owner'' (allow device owner to mount), and ``**_netdev**'' (device requires network to be available). The ``owner'' and ``_netdev'' options are Linux-specific. For more details, see mount(8). 


[http://linux.about.com/od/commands/l/blcmdl5_fstab.htm](http://linux.about.com/od/commands/l/blcmdl5_fstab.htm)



edit: from the ubuntuwiki:

> To save us from retyping this after every reboot we add the following

line to /etc/fstab:

nfs-server:/   /mnt   nfs4    _netdev,auto  0  0

    where the auto option mounts on startup and the _netdev option can be used by scripts to mount the filesystem when the network is available. Under NFSv3 (type nfs) the _netdev option will tell the system to wait to mount until the network is available. With a type of nfs4 this option is ignored, but can be used with mount -O _netdev in scripts later. Currently Ubuntu Server does not come with the scripts needed to auto-mount nfs4 entries in /etc/fstab after the network is up. 


[https://help.ubuntu.com/community/NFSv4Howto](https://help.ubuntu.com/community/NFSv4Howto)

---

### Post by SeijiSensei on 2014-02-25
That bit about NFSv4 rang a bell.  I added "vers=3" among the options in /etc/fstab a while back when I was having trouble negotiating with an older NFS server.  The entry now reads:
```
server:/share  /media/mntpoint   nfs     defaults,vers=3,rsize=32768,wsize=32768 0 0
```

---

