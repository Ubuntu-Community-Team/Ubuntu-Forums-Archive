---
title: "Fstab cifs mount, what worked on Ubuntu 14.04 is not working on 16.04????"
date: 2017-07-03
forum: Server Platforms
---

### Post by scott.bouch on 2017-07-03
Hi all,

Feel like banging my head against a brick wall....

I've just given up on CentOS and gone back to Ubuntu for this reason, now find I may as well have stayed with CentOS as Ubuntu 16.04 is giving me the same grief! Wasted evening after wasted evening!
[I][B]
The Issue:[/B][/I]

Fresh install of Ubuntu 16.04

Copied to fstab the entry from my last Ubuntu install fstab (also works on my Mint PC).

Now it won't mount

fstab line:
```
[FONT=Open Sans]//192.168.1.75/volume_1/NAS1/mnt/nas cifs guest,uid=1000,iocharset=utf8        0       0
[/FONT]

```


sudo mount-a result:
```
scott@GarageServer:/etc$ sudo mount -a
mount: wrong fs type, bad option, bad superblock on //192.168.1.75/volume_1/NAS1,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)


       In some cases useful info is found in syslog - try
       dmesg | tail or so.

```


dmesg | tail result:
```

[   17.570586] audit: type=1400 audit(1499068493.607:11): apparmor="STATUS" operation="profile_load" profile="unconfined" name="lxc-container-default-with-nesting" pid=1125 comm="apparmor_parser"
[   18.598370] cgroup: new mount options do not match the existing superblock, will be ignored
[  463.488165] IPv6: ADDRCONF(NETDEV_UP): enp0s25: link is not ready
[  465.468863] e1000e: enp0s25 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx
[  465.469000] IPv6: ADDRCONF(NETDEV_CHANGE): enp0s25: link becomes ready
[ 1248.629048] FS-Cache: Loaded
[ 1248.648967] FS-Cache: Netfs 'cifs' registered for caching
[ 1248.649081] Key type cifs.spnego registered
[ 1248.649094] Key type cifs.idmap registered
[ 1248.649405] CIFS VFS: No username specified

```

My NAS uses no username or password.

Any help is really appreciated... thanks...

---

### Post by darkod on 2017-07-03
Did you install the smbclient package?

---

### Post by scott.bouch on 2017-07-03
ah, no.... thanks! will do... has assumed it would be part of a stock Ubuntu install.

Will try that now. Thanks,

---

### Post by scott.bouch on 2017-07-03
```
$ sudo apt-get install smbclient
```

After installation

```
$ sudo mount -a
```

```
mount: wrong fs type, bad option, bad superblock on //192.168.1.75/volume_1/NAS1,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)

In some cases useful info is found in syslog - try
       dmesg | tail or so.
```

Tried a reboot, still not working....

What has changed in Ubuntu between 14.04 and 16.04 regarding mounting network shares? This is a very similar issue to what I had with CentOS7, and couldn't solve. Whatever has changed, it's not just Ubuntu and is really frustrating.

My similar tales of woe from the CentOS forum: [https://www.centos.org/forums/viewtopic.php?f=50&t=63125&p=266068#p266068](https://www.centos.org/forums/viewtopic.php?f=50&t=63125&p=266068#p266068)

---

### Post by darkod on 2017-07-03
Try manually from the command line...
```
sudo mount -t cifs //192.168.1.75/volume_1/NAS1 /mnt/nas -o guest
```

And I think you might have an error in fstab, you need a space between the NAS1 and the mount point. At least how you pasted it, there is no space so it is all like one string. Maybe that's why mount -a fails.

---

### Post by Morbius1 on 2017-07-03
> wrong fs type, bad option, bad superblock on //192.168.1.75/volume_1/NAS1,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program
```
sudo apt install cifs-utils
```
That will install the /sbin/mount.cifs "helper program" that you are missing.

---

### Post by scott.bouch on 2017-07-03
Thanks to the [brain of ]("https://en.wikipedia.org/wiki/The_Brain_of_Morbius")Morbius, cifs-utils worked!! But only for a manual mount-a.

However, it's not automatically mounting on startup after a reboot, which is the issue I had with CentOS.

After the unsuccessful reboot, I tried what Darkod said:
```

$ sudo mount -t cifs //192.168.1.75/volume_1/NAS1 /mnt/nas1 -o guest
```

Which worked nicely to mount the drive.

So both the fstab and command line options are working, just not automatically on boot on Ubuntu 16.04, but did work on 14.04.

Anything more to check why it's failing to mount automatically, after knowing it will work manually?

Cheers,

---

### Post by Morbius1 on 2017-07-03
The usual explanation for this symptom is that the Linux boot process has become way too damn complicated. The instruction in fstab is being executed before the network stack is running on your system so it has nothing to mount.

One way around this:

** Create a script:
```
gksu gedit /etc/network/if-up.d/fstab
```
** Add this to it:
```
#!/bin/sh
mount -a
```
** Make the script executable:
```
sudo chmod +x /etc/network/if-up.d/fstab
```

Anything in if-up.d will only run after the network is up. It's essentially doing a "sudo mount -a" at every boot.

---

### Post by TheFu on 2017-07-03
Or you can setup **autofs** to handle the network mounts.  That way, the mount won't be attempted until it is actually required.

---

### Post by scott.bouch on 2017-07-03
Hi Morbius,

Great idea thanks, for some reason the script didn't work out on boot.

found this in dmesg:

[   18.944454] IPv6: ADDRCONF(NETDEV_UP): enp0s25: link is not ready
[   18.966486] FS-Cache: Loaded
[   18.985687] FS-Cache: Netfs 'cifs' registered for caching
[   18.985800] Key type cifs.spnego registered
[   18.985811] Key type cifs.idmap registered
[   19.332808] cgroup: new mount options do not match the existing superblock, will be ignored
[   20.880867] e1000e: enp0s25 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx
[   20.881015] IPv6: ADDRCONF(NETDEV_CHANGE): enp0s25: link becomes ready
**[   24.988082] CIFS VFS: Error connecting to socket. Aborting operation.**
**[   24.988085] CIFS VFS: Error connecting to socket. Aborting operation.**
**[   24.990869] CIFS VFS: cifs_mount failed w/return code = -113**
**[   24.990871] CIFS VFS: cifs_mount failed w/return code = -113**
**[   30.988052] CIFS VFS: Error connecting to socket. Aborting operation.**
**[   30.989701] CIFS VFS: cifs_mount failed w/return code = -113**
[   31.535570] audit_printk_skb: 12 callbacks suppressed
[   31.535575] audit: type=1400 audit(1499083000.012:16): apparmor="DENIED" operation="open" profile="/usr/sbin/mysqld" name="/proc/1334/status" pid=1334 comm="mysqld" requested_mask="r" denied_mask="r" fsuid=112 ouid=112
[   31.535618] audit: type=1400 audit(1499083000.012:17): apparmor="DENIED" operation="open" profile="/usr/sbin/mysqld" name="/sys/devices/system/node/" pid=1334 comm="mysqld" requested_mask="r" denied_mask="r" fsuid=112 ouid=0
[   31.535692] audit: type=1400 audit(1499083000.012:18): apparmor="DENIED" operation="open" profile="/usr/sbin/mysqld" name="/proc/1334/status" pid=1334 comm="mysqld" requested_mask="r" denied_mask="r" fsuid=112 ouid=112
[   35.264320] [UFW BLOCK] IN=enp0s25 OUT= MAC= SRC=192.168.1.220 DST=239.0.0.250 LEN=281 TOS=0x00 PREC=0x00 TTL=1 ID=49261 DF PROTO=UDP SPT=32414 DPT=32415 LEN=261 
[   35.264562] [UFW BLOCK] IN=enp0s25 OUT= MAC= SRC=192.168.1.220 DST=239.255.255.250 LEN=281 TOS=0x00 PREC=0x00 TTL=1 ID=16853 DF PROTO=UDP SPT=32410 DPT=32411 LEN=261 
[   35.426989] [UFW BLOCK] IN=enp0s25 OUT= MAC= SRC=192.168.1.220 DST=239.0.0.250 LEN=291 TOS=0x00 PREC=0x00 TTL=1 ID=49263 DF PROTO=UDP SPT=32414 DPT=32415 LEN=271 
**[   36.988124] CIFS VFS: Error connecting to socket. Aborting operation.**
**[   36.989382] CIFS VFS: cifs_mount failed w/return code = -113**

I've made **bold** what appears in red in my ssh terminal. I'm unclear if this failure is your script trying, or the regular fstab failing...

I just tried this to be sure the server can see the NAS: 

$ ping 192.168.1.75
PING 192.168.1.75 (192.168.1.75) 56(84) bytes of data.
64 bytes from 192.168.1.75: icmp_seq=1 ttl=64 time=7.04 ms
64 bytes from 192.168.1.75: icmp_seq=2 ttl=64 time=0.106 ms
64 bytes from 192.168.1.75: icmp_seq=3 ttl=64 time=0.070 ms
^C
--- 192.168.1.75 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2000ms
rtt min/avg/max/mdev = 0.070/2.408/7.049/3.281 ms

---

### Post by TheFu on 2017-07-03
The reason the ping works, is that by the time you can login, networking has been brought up. It is excellent to know that the networking is actually working, but this is a race condition between the networking and fstab processing.

Things happen quickly during boot. It is possible that the networking subsystem isn't up when the fstab is processed.  Waiting 1-5 seconds for the network to come up before processing the rest of the fstab would be nice. I don't know how to do that.  There are other solutions as described above.

As I've mentioned, using **autofs** to handle network mounts is 1 way to delay.  That would remove the fstab from the issue.  Autofs uses "real mounts", unlike some other solutions (which have NOT been mentioned above, thankfully).  If the CIFS storage is just for data and not used by any automatic servers, then this should be fine.  I use autofs (but not CIFS) for a media server.

Are you trying to run a mysql DB off a CIFS mount?  That seems like a really bad idea, if that is what is happening.

The entire way most popular Linux systems boot was changed around 2015 from a normal init/upstart method to something called systemd.  Many things have changed for the better and a few things have changed that cause issues for good and bad reasons.  This issue is happening because systemd boots much, much, much, faster.  That is a good thing, overall, but new issues related to it are being seen. This is one.

---

### Post by Morbius1 on 2017-07-03
>  Great idea thanks, for some reason the script didn't work out on boot.
Then remove it a go with option 2:

Change this in fstab:
```
[FONT=Open Sans]//192.168.1.75/volume_1/NAS1 /mnt/nas cifs guest,uid=1000,iocharset=utf8        0       0[/FONT]
```
to this:
```
[FONT=Open Sans]//192.168.1.75/volume_1/NAS1 /mnt/nas cifs guest,uid=1000,iocharset=utf8,noauto,user        0       0[/FONT]
```
noauto = will make it so it doesn't mount at boot at all which doesn't sound right but .....
user = allows an ordinary user ( not sudo ) to mount the share.

If you currently have it mounted unmount it then run this command to mount it - no sudo required:
```
mount /mnt/nas
```
If that works add an entry into your startup list: Startup Applications  > Add > In the Command Box enter:
```
mount /mnt/nas
```

It will not automount at boot but after login. Is that acceptable?

---

### Post by scott.bouch on 2017-07-03
Hi TheFu,

Another approach, thanks.. Just had a stab at it, am opening another can of worms here... and my brain is melting with trying new things... I'd rather just be able to fix the original problem..

Thanks again, Scott

---

### Post by scott.bouch on 2017-07-03
Another viable solution..

> **Morbius1 said:**
> 
If that works add an entry into your startup list: Startup Applications  > Add > In the Command Box enter:
```
mount /mnt/nas
```

It will not automount at boot but after login. Is that acceptable?

Unfortunately this is a headless system, no desktop... is there a way to achieve this start-up request at the command line / or with a config file?

Is there a way to re-schedule what order things happen in during boot? ie: could fstab be put last?

---

### Post by scott.bouch on 2017-07-03
> **TheFu said:**
> The reason the ping works, is that by the time you can login, networking has been brought up. It is excellent to know that the networking is actually working, but this is a race condition between the networking and fstab processing.

Things happen quickly during boot. It is possible that the networking subsystem isn't up when the fstab is processed.  Waiting 1-5 seconds for the network to come up before processing the rest of the fstab would be nice. I don't know how to do that.  There are other solutions as described above.

As I've mentioned, using **autofs** to handle network mounts is 1 way to delay.  That would remove the fstab from the issue.  Autofs uses "real mounts", unlike some other solutions (which have NOT been mentioned above, thankfully).  If the CIFS storage is just for data and not used by any automatic servers, then this should be fine.  I use autofs (but not CIFS) for a media server.

Are you trying to run a mysql DB off a CIFS mount?  That seems like a really bad idea, if that is what is happening.

The entire way most popular Linux systems boot was changed around 2015 from a normal init/upstart method to something called systemd.  Many things have changed for the better and a few things have changed that cause issues for good and bad reasons.  This issue is happening because systemd boots much, much, much, faster.  That is a good thing, overall, but new issues related to it are being seen. This is one.

Thank you for the explanation....  it clarifies a lot of stuff! I had no idea this was going to be such hard work, as last time around it just worked.. clearly a lot has changed! 

The NAS is purely my media collection, used by this server by PLEX Media Server. No clever jiggery pokery. This makes me want to build a new server with only internal storage.... But a daft reason for the expense.

Thanks, Scott.

---

### Post by darkod on 2017-07-03
I would use the noauto option in fstab and then put the manual command in /etc/rc.local

Edit that file and before the line 'exit 0' add something like this:
```
mount /mnt/nas
```

You don't need sudo because it runs as root. Commands you put in rc.local are executed at the end of the boot process so the network should be up by then.

Also to remind you that you can much eacily connect linux systems (all NAS devices run one version or another of linux FW) by NFS instead of CIFS. That is more for windows clients. Linux systems are happier with NFS if I'm not mistaken.

---

