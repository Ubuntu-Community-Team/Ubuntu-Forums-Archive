---
title: "NFS 101: NFS is _not_ easy to configure and troubleshoot"
date: 2012-08-12
forum: Server Platforms
---

### Post by JackandJohn on 2012-08-12
I've been trying off and on for a couple of weeks to get nfs functioning in some sort of rational way, and it's completely stonewalling me....


[SIZE="4"]The setup[/SIZE]
I've got a mini-itx server that I've been very happy to have ubuntu on since 6.04, I'm now at 12.04
Never had a desire to set up nfs, since samba/cifs (then when the time came; netatalk) worked marvellously, and I could ignore any cpu and network overhead.

Now, I'm trying to squeeze and test all I can out of a raspberry pi with xbmc, and nfs is one way to do that.

Getting NFS to work has been painful, and very much like skateboarding through a concrete maze in the dark.

This is my /etc/exports

```
#/media/		*(rw,sync,no_root_squash)
/export *(ro,all_squash,fsid=0,insecure)
/export/G-Rated 192.168.0.0/24(rw,all_squash,insecure)
/export/PG-Rated 192.168.0.0/24(rw,all_squash,insecure)
/export/Metadata 192.168.0.0/24(rw,insecure)
```

And the bits of my /etc/fstab

```
#NFS Exports
/media/Shared/Video/Metadata /export/Metadata     nobootwait      bind    0       0
/media/Shared/Video/Movies,\040Cartoons,\040and\040TV\040-\040G\040rated /export/G-Rated	nobootwait	bind	0	0
/media/Shared/Video/Movies,\040Cartoons,\040and\040TV\040-\040PG\040-\040PG13\040rated/ /export/PG-Rated	nobootwait	bind	0	0
```

And, for good measure, a printout of the folder:

```
$ ls -la /export/
total 64
drwxrwxrwx  9 root root  4096 Aug 12 01:21 .
drwxr-xr-x 25 root root  4096 Jul 16 23:31 ..
drwxrwsrwx 28 josh josh 24576 Aug 11 18:25 Downloads
drwxrwxrwx 17 josh josh  4096 Aug 11 18:06 Educational
-rw-rw-r--  1 josh josh     0 Aug 12 01:21 FAKE.mp4
drwxrwsrwx  5 josh josh  4096 Apr  9 15:31 G-Rated
drwxrwxrwx 30 josh josh 12288 Aug  8 15:06 HD-Movies
drwxrwxrwx 10 josh josh  4096 Aug 12 02:36 Metadata
drwxrwsrwx  6 root root  4096 May 26 22:38 PG-Rated
drwxrwxrwx  6 root root  4096 Aug 12 01:21 R-Rated
```

[SIZE="4"]The frustration and head-shaking[/SIZE]

I've now progressed to where I can see the folders from XBMC, but any folder that is mounted on the server DISAPPEARS from the clients!

Example: I add ```
nfs://192.168.0.100/export/
``` through the add server dialog, and am not able to see the contents properly:

```
R-Rated
FAKE.mp4

```

Now, it took me a while to figure this out, but if I "sudo umount /export/G-Rated", and then refresh the listing, I see this:

```
G-Rated
R-Rated
FAKE.mp4
```

Of course, G-rated is empty.

I also, right from the raspberry, ran "sudo mount 192.168.0.100:/export /media/export/"
and mounted or unmounted, the G-Rated folder is empty...
Here's the mounted export folder:

```
pi@raspbmc:/media/export$ ls -la
total 36
drwxrwxrwx  9 root root 4096 Aug 12 01:21 .
drwxr-xr-x 12 root root 4096 Aug 12 02:19 ..
drwxr-xr-x  2 root root 4096 Jul 16 23:33 Downloads
drwxr-xr-x  2 root root 4096 Jul 16 23:42 Educational
-rw-rw-r--  1 pi   pi      0 Aug 12 01:21 FAKE.mp4
drwxr-xr-x  2 root root 4096 Jul 16 23:33 G-Rated
drwxr-xr-x  2 root root 4096 Jul 17 16:17 HD-Movies
drwxr-xr-x  2 root root 4096 Jul 17 23:50 Metadata
drwxr-xr-x  2 root root 4096 Jul 16 23:33 PG-Rated
drwxrwxrwx  6 root root 4096 Aug 12 01:21 R-Rated

```


[SIZE="4"]The part where I question WHY and wonder if Ubuntu is still trying to be friendly[/SIZE]

I've tried following every NFS troubleshooting I can find, including the wrongly-named "Troubleshooting" section of [https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

A quick rundown of thing's I've tried:
changed /etc/default/nfs-common to include RPCGSSDOPTS="-vvv"
changed /etc/default/nfs-kernel-server to include RPCSVCGSSDOPTS="-vvv"
Searched for log messages while connecting, mounting, reconnecting, etc:
 tail /var/log/daemon.log (as suggested by [https://help.ubuntu.com/community/NFSv4Howto#Troubleshooting](https://help.ubuntu.com/community/NFSv4Howto#Troubleshooting) - no such log any more)
 ls -la /var/log/ (Looking for all files with ~now as the modify date)
 tail /var/log/kern.log
 dmesg (These last two at least mentioned NFSD, but only that it started, nothing past that)
 "sudo /etc/init.d/nfs-kernel-server stop" , then "/usr/sbin/rpc.nfsd -d auth -d ugid" (Attempted a bunch of switches to make it run in terminal.. no such luck)




[SIZE="4"]*Started skimming yet?*[/SIZE]

As well you should.. All I wanted was to test NFS, and even through using the internet, have been completely unable to... I even thought that as a basic service, it would have rational and readable troubleshooting documents, like logs in /var/log/*.


If I have missed something Critical, please tell me so I can fix it, then I can update at least 3 wikis and 7 forum threads... I would gladly take a facepalm moment at this point...

---

### Post by HermanAB on 2012-08-12
Howdy,

I'm just wondering whether all NFS related services are running.  AFAIK, NFS uses multiple daemons: rpcbind, portmap and nfs-server (may also use also rquotad, mountd, statd, and lockd).  If rpcbind is not running, or if your firewall is blocking high ports, then you would have access problems which may explain some of the weirdness.

Try debugging things using 'telnet 2049' and 'rpcinfo -p localhost|grep "nfs" or some such.

---

### Post by Merrattic on 2012-08-12
This thread / howto has served me well for years. Follow to the letter and you should be up and running.

[http://ubuntuforums.org/showthread.php?t=249889&highlight=NFS](http://ubuntuforums.org/showthread.php?t=249889&highlight=NFS)

That said, I always use samba to connect my media shares to XBMC

---

### Post by JackandJohn on 2012-08-12
Good suggestions for troubleshooting steps, and here is the output:

I ran across [http://ubuntuforums.org/showthread.php?t=249889&highlight=NFS](http://ubuntuforums.org/showthread.php?t=249889&highlight=NFS) about half way through the process, but it seems outdated (specifically, the stuff about portmap)
Besides that, I did follow everything ( sudo mount server.mydomain.com:/files /files was especially timely )

Verifying TCP connectivity from the raspberry:
```
pi@raspbmc:~/$ nc -vvv 192.168.0.100 2049
Connection to 192.168.0.100 2049 port [tcp/nfs] succeeded!
```
Note: This iteration of this server is very lax on security (Since it's internal, and only holds stuff I don't mind sharing): no firewall has been enabled. I did run sudo ufw disable, just in case.

Verified running services on the server:
```
josh@simba:~/$ rpcinfo -p localhost|grep nfs
    100003    2   tcp   2049  nfs
    100003    3   tcp   2049  nfs
    100003    4   tcp   2049  nfs
    100003    2   udp   2049  nfs
    100003    3   udp   2049  nfs
    100003    4   udp   2049  nfs

```

Any attempts to verify portmap are redirected to rpcbind (making me think that portmap is depreciated in 12.04), but I do see nfs processes running:
```
josh@simba:~$ ps -A|grep nfs
  833 ?        00:00:00 nfsiod
18871 ?        00:00:00 nfsd4
18872 ?        00:00:00 nfsd4_callbacks
18873 ?        00:00:00 nfsd
18874 ?        00:00:00 nfsd
18875 ?        00:00:00 nfsd
18876 ?        00:00:00 nfsd
18877 ?        00:00:00 nfsd
18878 ?        00:00:00 nfsd
18879 ?        00:00:00 nfsd
18880 ?        00:00:00 nfsd
```


As far as I'm concerned, linux should represent ultimate diagnostic power.. I should be able to:

-Set it up (success)
-See that it's not working (success)
-Test network connectivity (success)
-Test service connectivity (kindof)
-Enable verbose logging on the service (fail)
-Watch logs as I'm testing (fail)
-See something like "user connected, only displaying what user has rights to" along with a user ID, or "Could not list directory, bind mounts not supported" (fail)
-Make appropriate changes (hopefully this will be success later)
-Thank every person that's helped along the way

---

### Post by JackandJohn on 2012-08-12
I will add this as well:

[SIZE="4"]On the Server:[/SIZE]
```
josh@simba:/export$ ls -la
total 64
drwxrwxrwx  9 root root  4096 Aug 12 01:21 .
drwxr-xr-x 25 root root  4096 Jul 16 23:31 ..
drwxrwsrwx 28 josh josh 24576 Aug 11 18:25 Downloads
drwxrwxrwx 17 josh josh  4096 Aug 11 18:06 Educational
-rw-rw-r--  1 josh josh     0 Aug 12 01:21 FAKE.mp4
drwxr-xr-x  2 root root  4096 Jul 16 23:33 G-Rated
drwxrwxrwx 30 josh josh 12288 Aug  8 15:06 HD-Movies
drwxrwxrwx 10 josh josh  4096 Aug 12 02:36 Metadata
drwxrwsrwx  6 root root  4096 May 26 22:38 PG-Rated
drwxrwxrwx  6 root root  4096 Aug 12 01:21 R-Rated
```

/etc/exports
```
#/export 192.168.0.0/24(rw,all_squash,insecure)
/export/G-Rated 192.168.0.0/24(rw,all_squash,insecure)
/export/PG-Rated 192.168.0.0/24(rw,all_squash,insecure)
/export/Metadata 192.168.0.0/24(rw,insecure)

```

[SIZE="4"]On the raspberry:[/SIZE]
```
pi@raspbmc:/media$ sudo mount 192.168.0.100:/export /media/export
```

```
pi@raspbmc:/media$ ls -la /media/export/
total 20
drwxrwxrwx  9 4294967294 4294967294 4096 Aug 12 01:21 .
drwxr-xr-x 12 root       root       4096 Aug 12 02:19 ..
drwxr-xr-x  2 4294967294 4294967294 4096 Jul 16 23:33 G-Rated
drwxrwxrwx 10 4294967294 4294967294 4096 Aug 12 02:36 Metadata
drwxrwsrwx  6 4294967294 4294967294 4096 May 26 22:38 PG-Rated

```


EDIT: As I was preparing this post, I found out that actually creating an export for "/export" was causing some problems with trying to understand what was going on. I think it may be the cause of vanishing folders...

As you see above, /export is commented out.

doing "sudo mount 192.168.0.100:/export /media/export" as above, actually resulted in being able to see the files inside the folders!

Also, adding nfs://192.168.0.100/export/PG-Rated to XBMC (remote path "export/PG-Rated") allows me to view and play files.


[SIZE="4"]AND; It's much zippier![/SIZE]


One caveat: Adding nfs://192.168.0.100/export to XBMC now does not connect, and it complains about this, but it just means specifying each subfolder individually.

---

### Post by Merrattic on 2012-08-19
Odd! You should only need to export "/export" to be able to mount it on the client....

---

### Post by pyrokinetic on 2012-08-25
I have issues with this too, I also have a RPi and have previously had it working using SMB shares hosted on Windows computers, the second I try accessing ANYTHING Ubuntu-related then I hit a brick wall, Can't access SMB or NFS shares and I'm tearing my hair out. :(

Which distro are you running on your pi? I've got Xbian 0.6.2.

---

### Post by User4519 on 2013-07-11
I realize this is an old post (am actually looking for a solution to a different problem I'm having), but just wanted to throw this in there:

When you have multiple nested exports like that on the same tree, you need to add **[FONT=courier new]crossmnt[/FONT]** as an option, and also give a unique **[FONT=courier new]fsid[/FONT]** to each export, or the "child exports" won't be contained in any parent export, e.g.:

```
/export 192.168.0.0/24(rw,all_squash,insecure,crossmnt,fsid=1)
/export/G-Rated 192.168.0.0/24(rw,all_squash,insecure,crossmnt,fsid=2)
/export/PG-Rated 192.168.0.0/24(rw,all_squash,insecure,crossmnt,fsid=3)
/export/Metadata 192.168.0.0/24(rw,insecure,crossmnt,fsid=4)
```

You may have to add **[FONT=courier new]no_subtree_check[/FONT]**, too.

---

