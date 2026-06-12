---
title: "Distributed file system?"
date: 2013-04-25
forum: Server Platforms
---

### Post by morthawt on 2013-04-25
I have an Ubuntu server VPS with a set amount of disk space that I cannot just modularly increase by its self. Is there any way that I can get another of the same VPS and hook them together in such a way that the free space of the new one is made part of the original one so it effectively has more space available?

I experimented with using FTP to mount a folder but I had some issues with that aside from the fact that the extra disk space is tied to that one mounted folder. Ideally I would like to have the system think there is more space generally. If theres no room on my main VPS drive then it just starts using space on the other VPS. Obviously leaving enough slack space for logs and things, because from my own experience when the disk is completely full the whole OS goes on the fritz until you clear space.

Any ideas? Is this even possible?

Thanks

---

### Post by cj13579 on 2013-04-25
Not sure if it is entirely what you are looking for but if you want the space at a particular location could you use "mount --bind"?

Consider the following drives:
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              73G   72G   1G  99% /
/dev/sdb1             190G  152G   39G  80% /media/stuff

You have stuff in /var/ftp but you need more than 1Gb of space. You could achieve what I think you want by creating the directory "/media/stuff/ftp" moving all the stuff from within /var/ftp to /media/stuff/ftp. Then use the command:

```
mount --bind /media/stuff/ftp /var/ftp
```

With this all of the stuff you actually create in /var/ftp will actually be stored in /media/stuff/ftp. Of course you need to make sure that the permissions for /media/stuff/ftp are OK for your application. Alsom this isn't persistent so it won't survive a reboot.

Help at all?

---

### Post by morthawt on 2013-04-25
Thats basically what I did but like I said the extra space was limited to that mount point. I am looking for a way to just emulate having more space available on the system with it spreading data out between other locations eg two VPS servers.

---

### Post by cj13579 on 2013-04-25
Sounds like you are looking for a clustered filesystem. Take a look at GPFS [https://help.ubuntu.com/community/SettingUpGPFSHowTo](https://help.ubuntu.com/community/SettingUpGPFSHowTo)

---

### Post by morthawt on 2013-04-25
> available for purchase I never thought I would see that with linux software. So there is no free option to do what I would like to be able to do? I cannot think of any way of attaining it. I could get two VPS but if I have a file that is bigger than 1 of the VPS's disks, what I am thinking of would not be an issue because the excess would be located at the remote disk.

---

### Post by cj13579 on 2013-04-25
GlusterFS looks to like it is free: [http://www.gluster.org/category/ubuntu/](http://www.gluster.org/category/ubuntu/)

---

### Post by morthawt on 2013-04-25
Seems you need more access than a VPS gives you. You cannot start messing with hardware and things like that. Also my linux skills are basic, I am a windows guy who has a linux VPS for reasons of functionality and learning gradually how to use linux.

---

### Post by rubylaser on 2013-04-25
[Ceph]("http://ceph.com/") is another free distributed filesystem, but seems like you just need a VPS with more resources (hard drive space).

---

### Post by morthawt on 2013-04-25
Well currently I have 1 VPS with 30 GB HDD, I could downgrade it to a 20 GB HDD and get another same 20 GB HDD so that I would have 2 VPS servers and a total of 40GB space for the same cost as I have now. If Ceph can give me a combined space for my main VPS server that would be fantastic. No clue how though, as I said I am not a linux pro. Most of what I have to do involves following guides. OpenVPN = guide. Adding iptables rules = guide. etc

---

### Post by rubylaser on 2013-04-26
If this is just for testing/learning, an old Pentium4 box or the like at home with Ubuntu server on it is the cheapest way to learn.  I wouldn't suggest you use a distributed filesystem in your case, but I was just suggesting another option to respond to your original question.  I would just suggest an NFS share from the new server to the old that you mount, and then pool with [mhddfs]("http://romanrm.ru/en/mhddfs") or aufs (I cover this as a portion of my [SnapRAID tutorial]("http://zackreed.me/articles/72-snapraid-on-ubuntu-12-04")).  Either will let you pool two (or volumes) into one storage mountpoint.  One more point, any solution you use with a separate host is only going to present that extra space at one mountpoint, not systemwide as you'd wanted originally.

---

### Post by morthawt on 2013-04-26
That seems to retain the essence of what I want though, a single location with the combined space of multiple VPS servers?

---

### Post by morthawt on 2013-04-26
So, I found a tutorial for that file system that I think I may be able to make work, my only issue is what is a "not too complicated" way to securely get the drive from the second VPS to the first one? My initial test was just a simple plain vsftpd connection, which obviously is insecure. I need the connection between the VPS' to be secure. I plan on setting up OpenVPN on the second one for an alternate location to exit on the internet with but I doubt I could do that and also connect to the first VPS VPN while still letting me VPN into the second one independently of the first.

---

### Post by TheFu on 2014-01-03
I realize this is late - really late - but did **NFSv4** not seem like a viable idea?
NFS has been around for years. Prior versions had security issues since only an IP was used as the access control, but with v4 and kerberos certs, it is very secure when the LAN is considered secure.

google "ubuntu nfs" for a number of how-tos.  Be certain to use the **autofs** on any clients.

OTOH, running this over internet IPs would be crazy. NFS is NOT encrypted.

There are many other, similar solutions, however, if using public IPs for the communication, using something like **OpenVPN** or **tun** between the systems would be smart.

If you don't need high performance, but have no other choice BUT to use public IPs on a shared network, then **sshfs** might be good enough. It has limitations (not everything in most file systems is supported) but any running sshd will provide the access at the user-level - it is FUSE, so it is slow. I use sshfs all the time for quick and dirty access to remote storage from around the world thanks to key-based authentication.

So, I hope this isn't too late for you or others to consider.  On a LAN, NFSv4 really is the best way to share storage between Linux/UNIX systems. It is so good that most people don't realize when NFS is being used.

Whether NFS is distributed or not, I guess that depends on the specific definition of distributed being used at the time.

---

