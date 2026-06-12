---
title: "NFS crash and results - rpc.statd won't start??"
date: 2007-12-02
forum: Server Platforms
---

### Post by rocketship on 2007-12-02
I had a complete crash while my server was mounted via NFS, and my laptop has been behaving strangely since - can anybody help?:

When booting, "Starting NFS Common Utilities" takes a long time.  Also, I can no longer mount the NFS share (though I can access the computer via SSH).

Here's what happen when I try to mount the share:

```
mount.nfs: rpc.statd is not running but is required for remote locking.
   Either use '-o nolocks' to keep locks local, or start statd.
```

When trying to start rpc.statd I get:

```
$ sudo rpc.statd -Fd
12/02/2007 17:44:35 rpc.statd[8263]: Version 1.1.0 Starting
12/02/2007 17:44:35 rpc.statd[8263]: Flags: No-Daemon Log-STDERR 
Cannot register service: RPC: Timed out
: unable to register (statd, 1, udp).
```

This is the output from /var/syslog that seems relevant:

```
Dec  2 17:09:41 asterix rpc.statd[5256]: Version 1.1.0 Starting
Dec  2 17:09:41 asterix rpc.statd[5256]: unable to register (statd, 1, udp).
Dec  2 17:09:41 asterix kernel: [  309.204000] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
Dec  2 17:10:16 asterix kernel: [  344.396000] rpcbind: server localhost not responding, timed out
Dec  2 17:10:16 asterix kernel: [  344.396000] RPC: failed to contact local rpcbind server (errno 5).
Dec  2 17:10:18 asterix kernel: [  345.852000] UDF-fs: No VRS found
Dec  2 17:10:18 asterix kernel: [  345.868000] ISO 9660 Extensions: Microsoft Joliet Level 1
Dec  2 17:10:18 asterix kernel: [  345.872000] ISOFS: changing to secondary root
Dec  2 17:10:51 asterix nfsd[5307]: nfssvc: writing fds to kernel failed: errno 5 (Input/output error)
Dec  2 17:10:51 asterix kernel: [  379.396000] rpcbind: server localhost not responding, timed out
Dec  2 17:10:51 asterix kernel: [  379.396000] RPC: failed to contact local rpcbind server (errno 5).
Dec  2 17:11:26 asterix nfsd[5307]: nfssvc: writing fds to kernel failed: errno 5 (Input/output error)
Dec  2 17:11:26 asterix kernel: [  414.396000] rpcbind: server localhost not responding, timed out
Dec  2 17:11:26 asterix kernel: [  414.396000] RPC: failed to contact local rpcbind server (errno 5).
Dec  2 17:11:26 asterix kernel: [  414.396000] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
Dec  2 17:11:26 asterix kernel: [  414.412000] NFSD: starting 90-second grace period

(...)

Dec  2 17:12:01 asterix kernel: [  449.412000] rpcbind: server localhost not responding, timed out
Dec  2 17:12:01 asterix kernel: [  449.412000] RPC: failed to contact local rpcbind server (errno 5).
Dec  2 17:12:13 asterix kernel: [  461.648000] ADDRCONF(NETDEV_UP): eth1: link is not ready
Dec  2 17:12:36 asterix kernel: [  484.412000] rpcbind: server localhost not responding, timed out
Dec  2 17:12:36 asterix kernel: [  484.412000] RPC: failed to contact local rpcbind server (errno 5).
Dec  2 17:12:36 asterix kernel: [  484.412000] lockd_up: makesock failed, error=-5
Dec  2 17:13:11 asterix kernel: [  519.412000] rpcbind: server localhost not responding, timed out
Dec  2 17:13:11 asterix kernel: [  519.412000] RPC: failed to contact local rpcbind server (errno 5).
Dec  2 17:13:11 asterix kernel: [  519.412000] nfsd: last server has exited
Dec  2 17:13:11 asterix kernel: [  519.412000] nfsd: unexporting all filesystems
Dec  2 17:13:46 asterix nfsd[5307]: nfssvc: Input/output error
Dec  2 17:13:46 asterix kernel: [  554.412000] rpcbind: server localhost not responding, timed out
Dec  2 17:13:46 asterix kernel: [  554.412000] RPC: failed to contact local rpcbind server (errno 5).
```

---

### Post by micster on 2008-01-07
Hello,
  I was having this exact same problem. I'm kinda new to Linux, but here is how I fixed it. 

 I started with the first error that says "unable to register (statd, 1, udp)" combined with what the syslog says about "rpcbind: server localhost not responding, timed out" which lead me to a post that suggested typing this on both the server and the client:
```
rpcinfo -p localhost
```on the computer running the NFS server with the folders I want to share, this is what it returned
```
mic@MediaServer:~$ rpcinfo -p
   program vers proto   port
    100000    2   tcp    111  portmapper
    100000    2   udp    111  portmapper
    100024    1   udp  32768  status
    100024    1   tcp  59900  status
    100003    2   udp   2049  nfs
    100003    3   udp   2049  nfs
    100003    4   udp   2049  nfs
    100021    1   udp  32770  nlockmgr
    100021    3   udp  32770  nlockmgr
    100021    4   udp  32770  nlockmgr
    100003    2   tcp   2049  nfs
    100003    3   tcp   2049  nfs
    100003    4   tcp   2049  nfs
    100021    1   tcp  52810  nlockmgr
    100021    3   tcp  52810  nlockmgr
    100021    4   tcp  52810  nlockmgr
    100005    1   udp  32771  mountd
    100005    1   tcp  49969  mountd
    100005    2   udp  32771  mountd
    100005    2   tcp  49969  mountd
    100005    3   udp  32771  mountd
    100005    3   tcp  49969  mountd
``` Which is good.... then try the same code on the client machine that is trying to access and mount those shares. I forget what the exact message said, but it basically timed out. 

Turns out that the "portmapper" or something on the client is timing out when it is trying to talk with the NFS Server. This is also why "Starting NFS Common Utilities" takes so long because it is basically timing out.

I should mention that they also said to try restarting the NFS server and utilities first with these commands:
```
mic@MediaServer:~$ sudo /etc/init.d/nfs-kernel-server restart
mic@MediaServer:~$ sudo /etc/init.d/portmap restart
```which seemed to fix it for other people. I'm not sure if your suppose to run them on the client machine or the server, but it would only time out for me when I ran the code on the client and did not fix my problem.

So back to why the portmapper is timing out... check your hostname,hosts, host.allow, and host.deny files for any errors on the client machine. For me it was really simple. I just edited my "/etc/hosts" and added the name of my client machine and it's I.P. in this case "playstation"
```
  GNU nano 2.0.6              File: /etc/hosts

127.0.0.1 localhost.localdomain playstation
192.168.0.196 playstation
```Just for kicks I edited my 
"/etc/network/interfaces" file and added the "loopback" part which was missing in my file.
  ```
GNU nano 2.0.6         File: /etc/network/interfaces

# Used by ifup(8) and ifdown(8). See the interfaces(5) manpage or
# /usr/share/doc/ifupdown/examples for more information.
auto lo
iface lo inet loopback
auto eth0
iface eth0 inet dhcp
```
 I followed all of this up with a "network restart" and then rebooted my machine.

I was happily surprised when it booted up in record time! If your "/etc/fstab" is properly configured you should see your NFS shares. Mine originally wasn't so you could try manually mounting them with "sudo mount -a" and see if they show up.

Hope that helps you fix your problem.
-Mic

---

