---
title: "Drbd"
date: 2008-08-01
forum: Server Platforms
---

### Post by vragec on 2008-08-01
Hello 

I have a problem. I have sucessufully installed DRBD and everything works o.k., but the copying works only manual. I would like to know, how could I automated the process of copying?...when first computer goes out (blacksout) that the back up computer would work? I know that the transfer of IPs goes through DNS, what about the transfer of data?
How to make data to copy itself in realtime with help of DRBD an other software ?

---

### Post by clivelr on 2008-12-07
> **vragec said:**
> Hello 

I have a problem. I have sucessufully installed DRBD and everything works o.k., but the copying works only manual. I would like to know, how could I automated the process of copying?...when first computer goes out (blacksout) that the back up computer would work? I know that the transfer of IPs goes through DNS, what about the transfer of data?
How to make data to copy itself in realtime with help of DRBD an other software ?

Hi,

The answer is to use hearbeat. Heartbeat can be seen as a layer on top of drbd that monitors both hosts, as soon as the primary goes down longer than a certain time then the hearbeat on the secondary will ensure the filesystem is unmounted on the primary and then mounted on the secondary host. After this happens the secondary host then becomes primary - when the "old" primary comes back up it will assume the secondary role.

I have just got this implemented using a filesystem and mysql. When the primary goes down the filesystem on the secondary is mounted and the mysql daemon is started there.

Here is a good howto - which helped me out getting it to work. Although it sounds like you will not use it for mysql - the theory behind it remains the same. 
[http://marksitblog.blogspot.com/2007/07/mysql-5-high-availability-with-drbd-8.html]("http://marksitblog.blogspot.com/2007/07/mysql-5-high-availability-with-drbd-8.html")

Clive

---

### Post by Philio on 2008-12-07
You do not use heartbeat to copy the data as such, however you need to have the active machine assigned as primary, then DRBD will sync all changes to the primary machine over to the secondary. This is what heartbeat will do for you.

You should test this manually before setting heartbeat to ensure you definately have DRBD working correctly! The fact that your asking how you copy data suggests you haven't done this.

```
cat /proc/drbd
```

Should show something like this if DRBD nodes are up, correctly configured and communicating:

```
$ cat /proc/drbd
version: 8.0.11 (api:86/proto:86)
GIT-hash: b3fe2bdfd3b9f7c2f923186883eb9e2a0d3a5b1b build by phil@mescal, 2008-02-12 11:56:43
 0: cs:Connected st:**Secondary/Secondary** ds:**Inconsistant/Inconsistant** C r---
    ns:4732 nr:29794928 dw:29800744 dr:5783 al:31 bm:814 lo:0 pe:0 ua:0 ap:0
        resync: used:0/31 hits:416 misses:54 starving:0 dirty:0 changed:54
        act_log: used:0/257 hits:1423 misses:33 starving:0 dirty:2 changed:31

```

Make one machine primary, this should cause DRBD to automatically start syncing the nodes and you should end up with something like this:

```
$ cat /proc/drbd
version: 8.0.11 (api:86/proto:86)
GIT-hash: b3fe2bdfd3b9f7c2f923186883eb9e2a0d3a5b1b build by phil@mescal, 2008-02-12 11:56:43
 0: cs:Connected st:**Primary/Secondary** ds:**UpToDate/UpToDate** C r---
    ns:4732 nr:29794928 dw:29800744 dr:5783 al:31 bm:814 lo:0 pe:0 ua:0 ap:0
        resync: used:0/31 hits:416 misses:54 starving:0 dirty:0 changed:54
        act_log: used:0/257 hits:1423 misses:33 starving:0 dirty:2 changed:31
```

At this point you can format the DRBD partition:

```
mkfs.ext3 /dev/drbd0
```

You can now mount the DRBD parition:

```
mount -t ext3 /dev/drbd0 /mnt/drbd
```

Try copying some files over, unmounting, making the other machine primary and mounting it and checking your files are still there.

At this point when your sure it's working install heartbeat.

You just need something like this in your haresources file:

primary.hostname.com drbddisk::r0 Filesystem::/dev/drbd0::/mnt/drbd::ext3

This should be identical on both machines.

---

