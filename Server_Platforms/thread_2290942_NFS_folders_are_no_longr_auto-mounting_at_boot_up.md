---
title: "NFS folders are no longr auto-mounting at boot up"
date: 2015-08-16
forum: Server Platforms
---

### Post by PartisanEntity on 2015-08-16
I have a headless server running Ubuntu Server 14.04 LTS with all latest updates. It is sharing a number of folders using NFS.

Contents of may /etc/exports file:

```
    # add folders we want to share through NFS
    /mnt/raiddisk/john       (rw)
    /mnt/raiddisk/vm        (rw)
    /mnt/raiddisk           (rw)
    /mnt/raiddisk/filecopy  (rw)
    /mnt/raiddisk/movies    (rw)
    /mnt/raiddisk/jane     (rw)
    /mnt/raiddisk/svn       (rw)
    /home/vboxuser2         (rw)
    /var/www/server.johndoe.home/public_html               (rw)
    /home/john       (rw)
```

My client machines (2) are running Ubuntu Desktop 14.04 LTS with all the latest updates. And both are suddenly unable to mount the NFS shared folders at boot.

Here are only the relevant contents of my /etc/fstab file:

```
    # mount the NFS folders from the server
    192.168.1.20:/mnt/raiddisk/john                          /mnt/john                                        nfs     auto,defaults   0       0
    192.168.1.20:/mnt/raiddisk/vm                           /mnt/vm                                         nfs     auto,defaults   0       0
    192.168.1.20:/home/vboxuser2                            /mnt/vboxuser2                                  nfs     auto,defaults   0       0
    192.168.1.20:/mnt/raiddisk                              /mnt/raiddisk                                   nfs     auto,defaults   0       0
    192.168.1.20:/var/www/server.johndoe.home/public_html  /mnt/server-www                                 nfs     auto,defaults   0       0
    192.168.1.20:/home/john                                  /mnt/johnhome                                    nfs     auto,defaults   0       0
```


Up until a few days ago this set up was running perfectly fine. On my client machine the folders were being mounted at boot.

Now however (I assume since a recent update) the folders are not mounted when I boot up the machine.

They will only mount after I manually run the follwing in the terminal:

```
    sudo mount -a
```

Here is the output of sudo mount -a -v:

    ```
mount.nfs: timeout set for Sun Aug 16 23:40:00 2015
    mount.nfs: trying text-based options 'vers=4,addr=192.168.1.20,clientaddr=192.168.1.7'
    mount.nfs: timeout set for Sun Aug 16 23:40:00 2015
    mount.nfs: trying text-based options 'vers=4,addr=192.168.1.20,clientaddr=192.168.1.7'
    mount.nfs: timeout set for Sun Aug 16 23:40:00 2015
    mount.nfs: trying text-based options 'vers=4,addr=192.168.1.20,clientaddr=192.168.1.7'
    mount.nfs: timeout set for Sun Aug 16 23:40:00 2015
    mount.nfs: trying text-based options 'vers=4,addr=192.168.1.20,clientaddr=192.168.1.7'
    mount.nfs: timeout set for Sun Aug 16 23:40:00 2015
    mount.nfs: trying text-based options 'vers=4,addr=192.168.1.20,clientaddr=192.168.1.7'
    mount.nfs: mount(2): No such file or directory
    mount.nfs: trying text-based options 'addr=192.168.1.20'
    mount.nfs: prog 100003, trying vers=3, prot=6
    mount.nfs: trying 192.168.1.20 prog 100003 vers 3 prot TCP port 2049
    mount.nfs: prog 100005, trying vers=3, prot=17
    mount.nfs: trying 192.168.1.20 prog 100005 vers 3 prot UDP port 36461
    mount.nfs: portmap query retrying: RPC: Timed out
    mount.nfs: prog 100005, trying vers=3, prot=6
    mount.nfs: trying 192.168.1.20 prog 100005 vers 3 prot TCP port 42598
    mount.nfs: portmap query failed: RPC: Remote system error - Connection timed out
    mount.nfs: trying text-based options 'vers=4,addr=192.168.1.20,clientaddr=192.168.1.7'
    mount.nfs: mount(2): No such file or directory
    mount.nfs: trying text-based options 'addr=192.168.1.20'
    mount.nfs: prog 100003, trying vers=3, prot=6
    mount.nfs: trying 192.168.1.20 prog 100003 vers 3 prot TCP port 2049
    mount.nfs: prog 100005, trying vers=3, prot=17
    mount.nfs: trying 192.168.1.20 prog 100005 vers 3 prot UDP port 36461
    mount.nfs: portmap query retrying: RPC: Timed out
    mount.nfs: prog 100005, trying vers=3, prot=6
    mount.nfs: trying 192.168.1.20 prog 100005 vers 3 prot TCP port 42598
    mount.nfs: portmap query failed: RPC: Remote system error - Connection timed out
    mount.nfs: trying text-based options 'vers=4,addr=192.168.1.20,clientaddr=192.168.1.7'
    mount.nfs: mount(2): No such file or directory
    mount.nfs: trying text-based options 'addr=192.168.1.20'
    mount.nfs: prog 100003, trying vers=3, prot=6
    mount.nfs: trying 192.168.1.20 prog 100003 vers 3 prot TCP port 2049
    mount.nfs: prog 100005, trying vers=3, prot=17
    mount.nfs: trying 192.168.1.20 prog 100005 vers 3 prot UDP port 36461
    mount.nfs: portmap query retrying: RPC: Timed out
    mount.nfs: prog 100005, trying vers=3, prot=6
    mount.nfs: trying 192.168.1.20 prog 100005 vers 3 prot TCP port 42598
    mount.nfs: portmap query failed: RPC: Remote system error - Connection timed out
    mount.nfs: trying text-based options 'vers=4,addr=192.168.1.20,clientaddr=192.168.1.7'
    mount.nfs: mount(2): No such file or directory
    mount.nfs: trying text-based options 'addr=192.168.1.20'
    mount.nfs: prog 100003, trying vers=3, prot=6
    mount.nfs: trying 192.168.1.20 prog 100003 vers 3 prot TCP port 2049
    mount.nfs: prog 100005, trying vers=3, prot=17
    mount.nfs: trying 192.168.1.20 prog 100005 vers 3 prot UDP port 36461
    mount.nfs: portmap query retrying: RPC: Timed out
    mount.nfs: prog 100005, trying vers=3, prot=6
    mount.nfs: trying 192.168.1.20 prog 100005 vers 3 prot TCP port 42598
    mount.nfs: portmap query failed: RPC: Remote system error - Connection timed out
    mount.nfs: trying text-based options 'vers=4,addr=192.168.1.20,clientaddr=192.168.1.7'
    mount.nfs: mount(2): No such file or directory
    mount.nfs: trying text-based options 'addr=192.168.1.20'
    mount.nfs: prog 100003, trying vers=3, prot=6
    mount.nfs: trying 192.168.1.20 prog 100003 vers 3 prot TCP port 2049
    mount.nfs: prog 100005, trying vers=3, prot=17
    mount.nfs: trying 192.168.1.20 prog 100005 vers 3 prot UDP port 36461
    mount.nfs: portmap query retrying: RPC: Timed out
    mount.nfs: prog 100005, trying vers=3, prot=6
    mount.nfs: trying 192.168.1.20 prog 100005 vers 3 prot TCP port 42598
    mount.nfs: portmap query failed: RPC: Remote system error - Connection timed out
    mount.nfs: trying text-based options 'vers=4,addr=192.168.1.20,clientaddr=192.168.1.7'
    mount.nfs: mount(2): No such file or directory
    mount.nfs: trying text-based options 'addr=192.168.1.20'
    mount.nfs: prog 100003, trying vers=3, prot=6
    mount.nfs: trying 192.168.1.20 prog 100003 vers 3 prot TCP port 2049
    mount.nfs: prog 100005, trying vers=3, prot=17
    mount.nfs: trying 192.168.1.20 prog 100005 vers 3 prot UDP port 36461
    mount.nfs: portmap query retrying: RPC: Timed out
    mount.nfs: prog 100005, trying vers=3, prot=6
    mount.nfs: trying 192.168.1.20 prog 100005 vers 3 prot TCP port 42598
    mount.nfs: portmap query failed: RPC: Remote system error - Connection timed out
    mount.nfs: trying text-based options 'vers=4,addr=192.168.1.20,clientaddr=192.168.1.7'
    mount.nfs: mount(2): No such file or directory
    mount.nfs: trying text-based options 'addr=192.168.1.20'
    mount.nfs: prog 100003, trying vers=3, prot=6
    mount.nfs: trying 192.168.1.20 prog 100003 vers 3 prot TCP port 2049
    mount.nfs: prog 100005, trying vers=3, prot=17
    mount.nfs: trying 192.168.1.20 prog 100005 vers 3 prot UDP port 36461
    mount.nfs: portmap query retrying: RPC: Timed out
    mount.nfs: prog 100005, trying vers=3, prot=6
    mount.nfs: trying 192.168.1.20 prog 100005 vers 3 prot TCP port 42598
    mount.nfs: portmap query failed: RPC: Remote system error - Connection timed out
    mount.nfs: trying text-based options 'vers=4,addr=192.168.1.20,clientaddr=192.168.1.7'
    mount.nfs: mount(2): No such file or directory
    mount.nfs: trying text-based options 'addr=192.168.1.20'
    mount.nfs: prog 100003, trying vers=3, prot=6
    mount.nfs: trying 192.168.1.20 prog 100003 vers 3 prot TCP port 2049
    mount.nfs: prog 100005, trying vers=3, prot=17
    mount.nfs: trying 192.168.1.20 prog 100005 vers 3 prot UDP port 36461
    mount.nfs: portmap query retrying: RPC: Timed out
    mount.nfs: prog 100005, trying vers=3, prot=6
    mount.nfs: trying 192.168.1.20 prog 100005 vers 3 prot TCP port 42598
    mount.nfs: portmap query failed: RPC: Remote system error - Connection timed out
    mount.nfs: trying text-based options 'vers=4,addr=192.168.1.20,clientaddr=192.168.1.7'
    mount.nfs: mount(2): No such file or directory
    mount.nfs: trying text-based options 'addr=192.168.1.20'
    mount.nfs: prog 100003, trying vers=3, prot=6
    mount.nfs: trying 192.168.1.20 prog 100003 vers 3 prot TCP port 2049
    mount.nfs: prog 100005, trying vers=3, prot=17
    mount.nfs: trying 192.168.1.20 prog 100005 vers 3 prot UDP port 36461
    mount.nfs: portmap query retrying: RPC: Timed out
    mount.nfs: prog 100005, trying vers=3, prot=6
    mount.nfs: trying 192.168.1.20 prog 100005 vers 3 prot TCP port 42598
    mount.nfs: portmap query failed: RPC: Remote system error - Connection timed out
    mount.nfs: trying text-based options 'vers=4,addr=192.168.1.20,clientaddr=192.168.1.7'
    mount.nfs: mount(2): No such file or directory
    mount.nfs: trying text-based options 'addr=192.168.1.20'
    mount.nfs: prog 100003, trying vers=3, prot=6
    mount.nfs: trying 192.168.1.20 prog 100003 vers 3 prot TCP port 2049
    mount.nfs: prog 100005, trying vers=3, prot=17
    mount.nfs: trying 192.168.1.20 prog 100005 vers 3 prot UDP port 36461
    mount.nfs: portmap query retrying: RPC: Timed out
    mount.nfs: prog 100005, trying vers=3, prot=6
    mount.nfs: trying 192.168.1.20 prog 100005 vers 3 prot TCP port 42598
    mount.nfs: portmap query failed: RPC: Remote system error - Connection timed out
    mount.nfs: Connection timed out
    mount.nfs: timeout set for Sun Aug 16 23:42:11 2015
    mount.nfs: trying text-based options 'vers=4,addr=192.168.1.20,clientaddr=192.168.1.7'
```

On the client machine, when I search /var/log for any NFS related lines I have the following output (I have selected only the most recent entries):

   ```
 /var/log/syslog:Aug 16 13:23:34 ubuntu kernel: [   15.128595] FS-Cache: Netfs 'nfs' registered for caching
    /var/log/syslog:Aug 16 13:23:34 ubuntu rpc.idmapd[875]: main: open(/run/rpc_pipefs/nfs): No such file or directory
    /var/log/syslog:Aug 16 21:44:48 ubuntu kernel: [30119.650872] nfs: server 192.168.1.20 not responding, timed out
    /var/log/syslog:Aug 16 21:48:00 ubuntu kernel: [30312.356845] nfs: server 192.168.1.20 not responding, timed out
    /var/log/syslog:Aug 16 22:55:50 ubuntu kernel: [   15.444005] FS-Cache: Netfs 'nfs' registered for caching
    /var/log/syslog.1:Aug 16 13:04:35 ubuntu kernel: [   15.876127] FS-Cache: Netfs 'nfs' registered for caching
    /var/log/syslog.2.gz:Aug 15 14:00:52 ubuntu kernel: [   17.467940] FS-Cache: Netfs 'nfs' registered for caching
    /var/log/syslog.3.gz:Aug 14 22:12:45 ubuntu kernel: [   14.015935] FS-Cache: Netfs 'nfs' registered for caching
    /var/log/syslog.3.gz:Aug 14 22:12:45 ubuntu rpc.idmapd[898]: main: open(/run/rpc_pipefs/nfs): No such file or directory
    /var/log/syslog.4.gz:Aug 12 22:49:49 ubuntu kernel: [   12.920639] FS-Cache: Netfs 'nfs' registered for caching
    /var/log/syslog.4.gz:Aug 12 22:49:49 ubuntu rpc.idmapd[910]: main: open(/run/rpc_pipefs/nfs): No such file or directory
    /var/log/syslog.5.gz:Aug 11 21:33:11 ubuntu kernel: [   14.363706] FS-Cache: Netfs 'nfs' registered for caching
    /var/log/syslog.6.gz:Aug 10 21:29:28 ubuntu kernel: [   12.760663] FS-Cache: Netfs 'nfs' registered for caching
    /var/log/syslog.6.gz:Aug 10 21:29:29 ubuntu rpc.idmapd[890]: main: open(/run/rpc_pipefs/nfs): No such file or directory
    /var/log/syslog.7.gz:Aug  6 20:58:35 ubuntu kernel: [   15.475703] FS-Cache: Netfs 'nfs' registered for caching
    /var/log/syslog.7.gz:Aug  7 07:37:22 ubuntu kernel: [   12.183087] FS-Cache: Netfs 'nfs' registered for caching
    /var/log/udev:KERNEL[15.324744] add      /module/nfs (module)
    /var/log/udev:DEVPATH=/module/nfs
    /var/log/udev:UDEV  [15.325094] add      /module/nfs (module)
    /var/log/udev:DEVPATH=/module/nfs
```

I am not sure what I need to check to identify the issue. I have checked user permissions and file permissions, nothing has changed.

I am assuming that there was some NFS related update which has caused my configuration (on the server?) to be incompatible in some way?

---

### Post by darkod on 2015-08-17
Since NFS is over network, one thing you could try is add the _netdev option in /etc/fstab. That tells mount to wait for the network to be up before it tries to mount any network resources. Also I don't think you need the auto in the options, it mounts fstab by default (unless you have the noauto option).

So the options for the NFS entries would be like: defaults,_netdev

Also, I assume you checked that the client can ping the server, that networking works fine. Also make sure the server is running the nfs service and on the correct port.

Any firewall between the two? Could an update have reset some firewall rule?

---

### Post by TheFu on 2015-08-17
I see it is trying NFSv4 first, but your setup appears to be NFSv3 (which is fine for a home without teens on the network).
Save some time with vers=3 option on the client-side.

I agree with Darkod - looks like the startup dependencies could have changed.  I use autofs for all NFS mounts to avoid that issue. No storage is mounted until it is actually requested.  Don't know if that is workable for you or not. There are good reasons NOT to use the automounter.

My client-side auto.nfs  looks like this:```

/VMs -fstype=nfs,hard,intr,rw,async,vers=3  romulus:/raid/media/VMs
```

and the export looks like this:
```
/raid/media/VMs hadar(rw,no_root_squash,async,no_subtree_check) romulus(rw,no_root_squash,async,no_subtree_check) 
```

---

### Post by PartisanEntity on 2015-08-17
Thanks very much to the both of you for the feedback.

At this point I do not think it is a network issue because:

[LIST]
[*]Manually mounting the NFS folders works
[*]I can ping the server over the network
[*]There is an active firewall on the server and I have checked that the required ports are open
[/LIST]

What have I tried since your feedback:

[LIST]
[*]On the client: I have tried editing the entries in fstab to remove "auto", and to add "_netdev". I have also tried adding "vers=3".
[*]On the server in nfs-kernel-server I tried preventing it from using nfsv4 just to see if that helps
[/LIST]

None of these helped in getting the clients to auto-mount the NFS folders that are listed in /etc/fstab as they used to before the recent update.

One thing I noticed on the server, is that whenever I restarted the NFS server it popped up some warnings, example:

> exportfs: No host name given with /mnt/raiddisk (rw), suggest *(rw) to avoid warning
exportfs: /etc/exports [4]: Neither 'subtree_check' or 'no_subtree_check' specified for export "*:/mnt/raiddisk".
  Assuming default behaviour ('no_subtree_check').
  NOTE: this default has changed since nfs-utils version 1.0.x

I have since added the IP numbers of the clients, which got rid of one of the errors. However adding "no_subtree_check" caused my client machine to hang when viewing certain NFS folders so I have since removed that option.

**Interesting observation:**

Not sure if this is significant.

After manually mounting the folders on the client machine by running "sudo mount -a -v". It mounts all NFS folders, BUT when I check the status using the command "mount" I can see that the folders are mounted in NFS vers=4. Here an example:

```
192.168.1.20:/mnt/raiddisk on /mnt/raiddisk type nfs (rw,vers=4,addr=192.168.1.20,clientaddr=192.168.1.7,_netdev)
```

The reason I mention this is because when I initially set up the NFS server I did not specifically opt to set up in NFS version 4, I simply followed a combination of tutorials that I found:

[LIST]
[*][https://help.ubuntu.com/14.04/serverguide/network-file-system.html](https://help.ubuntu.com/14.04/serverguide/network-file-system.html)
[*][https://www.digitalocean.com/community/tutorials/how-to-set-up-an-nfs-mount-on-ubuntu-14-04](https://www.digitalocean.com/community/tutorials/how-to-set-up-an-nfs-mount-on-ubuntu-14-04)
[/LIST]


**Questions:**

[LIST=1]
[*]Since mounting manually through terminal is working, would it make sense to looking into setting auto mounting of NFS? (i.e. not using /etc/fstab?) If yes, any good step by step instructions? (I have never done this before, so far all my experience with NFS has been through using /etc/fstab on the client machines).
[*]
[*]Would it make sense to look into the possibility of rolling back updates related to NFS? (I know probably not a good idea, but I am desperate since I use NFS in order to have Dejadup make automated backups of both client machines to the server, as well as the general convenience of using NFS in general).
[*]
[*]Lastly, what else can I try/check?
[/LIST]

---

### Post by TheFu on 2015-08-17
NFSv4 - doesn't that require a kerberos trust between the servers to work?  You would KNOW if that was configured. Otherwise NFSv4 shouldn't work - no way, no how.  Or am I wrong?

DejaDup doesn't need NFS - it definitely supports other network protocols - ssh, ftp, s3, and a few others, for example.

You can test autofs, but I doubt it will help. Perhaps if you try my settings in the fstab and export? Those are working here - 14.04 clients/server here. Did you try them all, as a set, or just a few?

If the manual mount is working, I'd probably just add an entry to the end of rc.local to do that at the end of booting ... then worry about troubleshooting this when more convenient.

---

### Post by PartisanEntity on 2015-08-18
> **TheFu said:**
> NFSv4 - doesn't that require a kerberos trust between the servers to work?  You would KNOW if that was configured. Otherwise NFSv4 shouldn't work - no way, no how.  Or am I wrong?

I am not sure. If my memory serves me correctly, I was looking at one tutorial that mentioned you can use NFSv4 and not enable kerberos.

> **TheFu said:**
> DejaDup doesn't need NFS - it definitely supports other network protocols - ssh, ftp, s3, and a few others, for example.

That is good to know. But I currently make a complete backup of my /home directory, if I use a different method, will that still maintain all file and folder permissions? (I thought the advantage of using NFS is that it is native to Linux and maintains all the meta data and file/folder permissions ?)

> **TheFu said:**
> You can test autofs, but I doubt it will help. Perhaps if you try my settings in the fstab and export? Those are working here - 14.04 clients/server here. Did you try them all, as a set, or just a few?

I did not try all your settings as a set, can I simply copy them as is into my /etc/fstab? (When I tried some of your settings, and then running "sudo mount -a -v" it complained about not understanding what -fstype means?)

> **TheFu said:**
> If the manual mount is working, I'd probably just add an entry to the end of rc.local to do that at the end of booting ... then worry about troubleshooting this when more convenient.

Thanks for the suggestion. I may try that as a las resort. Can I copy the entries from /etc/fstab as is and paste them at the end of rc.local or do I have to amend them first?

---

### Post by PartisanEntity on 2015-08-18
> **TheFu said:**
> I see it is trying NFSv4 first, but your setup appears to be NFSv3 (which is fine for a home without teens on the network).
Save some time with vers=3 option on the client-side.

I agree with Darkod - looks like the startup dependencies could have changed.  I use autofs for all NFS mounts to avoid that issue. No storage is mounted until it is actually requested.  Don't know if that is workable for you or not. There are good reasons NOT to use the automounter.

My client-side auto.nfs  looks like this:```

/VMs -fstype=nfs,hard,intr,rw,async,vers=3  romulus:/raid/media/VMs
```

and the export looks like this:
```
/raid/media/VMs hadar(rw,no_root_squash,async,no_subtree_check) romulus(rw,no_root_squash,async,no_subtree_check) 
```

There is something I do not quite understand from looking at your settings. Isn't "romulus" one of your clients? How come it is in your auto.nfs file? Wouldn't it be pointing to itself in your example from your auto.nfs file?

---

### Post by TheFu on 2015-08-18
> **PartisanEntity said:**
> There is something I do not quite understand from looking at your settings. Isn't "romulus" one of your clients? How come it is in your auto.nfs file? Wouldn't it be pointing to itself in your example from your auto.nfs file?

romulus is a client AND a server. The auto.nfs file is from hadar. Both run virtual machines and use shared storage located on romulus. The storage must be networked AND it must be mounted in exactly the same location for "live migrations" to work.  At the time I set this up, I didn't have a dedicated NFS server on the network.

Other questions ... 

* rc.local is just a script file.  You'll need mount commands just like you'd type in a shell there, but written in the shell scripting way - never assume any environment exists. [http://blog.jdpfu.com/2014/04/01/linux-troubleshooting-101-scripting](http://blog.jdpfu.com/2014/04/01/linux-troubleshooting-101-scripting)

* duplicity-based backup tools store all the metadata as part of the "chunking" inside the backup sets. Take a look at the target area - it is all 5MB "chunks" of stuff there - permissions, ACLs, owners are "inside" too.  Even if you shoved those backups to FAT16 storage, the permissions will be retained. 
If you were using rsync, rsnapshot (or similar hard-link-based tools for versioning), then storing on a Linux file system would matter, but it still looses changes in permissions over time.

* fstype is already part of the mount cmd, so it isn't an "option" like the other parts. The other things are. Of course, the manpage explains this and you are definitely in the RTFM stuff with this. ;)

---

### Post by SeijiSensei on 2015-08-18
NFSv4 has been the default version in Ubuntu for quite some time now.  I've been using "vers=3" for at least a few years on my home LAN.

---

### Post by PartisanEntity on 2015-08-18
Just wondering, does this look normal?

Output of "rpcinfo -p <host>:

```
rpcinfo -p 192.168.1.20
   program vers proto   port  service
    100000    4   tcp    111  portmapper
    100000    3   tcp    111  portmapper
    100000    2   tcp    111  portmapper
    100000    4   udp    111  portmapper
    100000    3   udp    111  portmapper
    100000    2   udp    111  portmapper
    100024    1   udp  53329  status
    100024    1   tcp  44922  status
    100003    2   tcp   2049  nfs
    100003    3   tcp   2049  nfs
    100003    4   tcp   2049  nfs
    100227    2   tcp   2049
    100227    3   tcp   2049
    100003    2   udp   2049  nfs
    100003    3   udp   2049  nfs
    100003    4   udp   2049  nfs
    100227    2   udp   2049
    100227    3   udp   2049
    100021    1   udp  51314  nlockmgr
    100021    3   udp  51314  nlockmgr
    100021    4   udp  51314  nlockmgr
    100021    1   tcp  45361  nlockmgr
    100021    3   tcp  45361  nlockmgr
    100021    4   tcp  45361  nlockmgr
    100005    1   udp  33411  mountd
    100005    1   tcp  35858  mountd
    100005    2   udp  45993  mountd
    100005    2   tcp  40341  mountd
    100005    3   udp  37837  mountd
    100005    3   tcp  38336  mountd
```

And output of nmap <host>:

```
Nmap scan report for server.files.home (192.168.1.20)
Host is up (0.00023s latency).
Not shown: 919 filtered ports, 73 closed ports
PORT      STATE SERVICE
21/tcp    open  ftp
22/tcp    open  ssh
80/tcp    open  http
111/tcp   open  rpcbind
548/tcp   open  afp
2049/tcp  open  nfs
8200/tcp  open  trivnet1
10000/tcp open  snet-sensor-mgmt

Nmap done: 1 IP address (1 host up) scanned in 3.70 seconds
```

---

### Post by TheFu on 2015-08-18
Looks normal to me.

Why bother with ssh on the LAN when telnet is just like plain FTP?

---

### Post by PartisanEntity on 2015-08-18
> **TheFu said:**
> Looks normal to me.

Why bother with ssh on the LAN when telnet is just like plain FTP?

I use ssh to terminal into the server.

I recently had to enable plain ftp because my IP cam doesn't support any other protocol.

---

### Post by PartisanEntity on 2015-08-18
Do I need to open any other ports for NFS? (Mind you this was working fine for months and months now, unless some requirements changed):

```


*filter

# Allow all loopback (lo0) traffic and drop all traffic to 127/8 that doesn't use lo0
-A INPUT -i lo -j ACCEPT
-A INPUT -d 127.0.0.0/8 -j REJECT

# Accept all established inbound connections
-A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT

# Allow all outbound traffic - you can modify this to only allow certain traffic
-A OUTPUT -j ACCEPT

# Allow HTTP and HTTPS connections from anywhere (the normal ports for websites and SSL).
-A INPUT -p tcp --dport 80 -j ACCEPT
-A INPUT -p tcp --dport 443 -j ACCEPT

# Allow ports 111 and 2049 tcp/udp for NFS sharing to work
-A INPUT -p tcp --dport 2049 -m state --state NEW -j ACCEPT
-A INPUT -p udp --dport 2049 -m state --state NEW -j ACCEPT
-A INPUT -p tcp --dport 111 -m state --state NEW -j ACCEPT
-A INPUT -p udp --dport 111 -m state --state NEW -j ACCEPT
# Allow port 548 for TimeMachine and AFP
-A INPUT -p tcp --dport 548 -m state --state NEW -j ACCEPT
-A INPUT -p udp --dport 548 -m state --state NEW -j ACCEPT
# Allow port for phpvirtualbox
-A INPUT -p tcp --dport 18083 -m state --state NEW -j ACCEPT
-A INPUT -p udp --dport 18083 -m state --state NEW -j ACCEPT
-A INPUT -p tcp --dport 9000:9100 -m state --state NEW -j ACCEPT
-A INPUT -p udp --dport 9000:9100 -m state --state NEW -j ACCEPT
# Allow port for webmin
-A INPUT -p tcp --dport 10000 -m state --state NEW -j ACCEPT
-A INPUT -p udp --dport 10000 -m state --state NEW -j ACCEPT
# Allow ports for minidlna
-A INPUT -p tcp --dport 8200 -m state --state NEW -j ACCEPT
-A INPUT -p udp --dport 1900 -m state --state NEW -j ACCEPT
# Allow ports for FTP
-A INPUT -p tcp -m tcp --dport 21 -j ACCEPT
-A OUTPUT -p tcp -m tcp --dport 21 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 20 -j ACCEPT
-A OUTPUT -p tcp -m tcp --dport 20 -j ACCEPT
-A INPUT -p tcp --dport 49152:65534 -m state --state RELATED,ESTABLISHED,NEW -j ACCEPT

# Allow SSH connections
#
# The -dport number should be the same port number you set in sshd_config
#
-A INPUT -p tcp -m state --state NEW --dport 22 -j ACCEPT

# Allow ping
-A INPUT -p icmp --icmp-type echo-request -j ACCEPT

# Log iptables denied calls
-A INPUT -m limit --limit 5/min -j LOG --log-prefix "iptables denied: " --log-level 7

# Drop all other inbound - default deny unless explicitly allowed policy
-A INPUT -j DROP
-A FORWARD -j DROP

COMMIT
```

---

### Post by TheFu on 2015-08-18
> **PartisanEntity said:**
> I use ssh to terminal into the server.

I recently had to enable plain ftp because my IP cam doesn't support any other protocol.

Ah - IP-cams do tend to suck from a security standpoint.

Back to NFS ... I haven't changed any firewall rules for NFS in years.

---

### Post by PartisanEntity on 2015-08-18
OK thanks so much for all the feedback.

I am currently about to set up the autofs route.

---

### Post by PartisanEntity on 2015-08-18
Unless I did it wrong, the autofs method did not work. 

The /etc/rclocal method worked:

I put "mount -a" in /etc/rc.local (before the "exit 0" line) and it works. My machine takes a little longer to show the desktop after I log in, but once it displays the desktop my NFS shares are mounted.

I can live with this "dirty" fix for now. Hoping the main issue will be resolved some time.

Thanks so much TheFu and darkod :)

---

