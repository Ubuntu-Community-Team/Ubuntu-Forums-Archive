---
title: "NFS setup problem (RPC not registered)"
date: 2010-04-30
forum: Server Platforms
---

### Post by kudude on 2010-04-30
Hello,

I've followed several guides and am trying to get NFS working on my local network.

For starters, I think I should be able to NFS mount a drive on the server (192.168.1.65) TO the server.  From there I'll work with another client (currently 192.168.1.80)
```

$cat /etc/exports
/media 192.168.1.0/24(rw,no_subtree_check)


$cat /etc/hosts.deny
portmap mountd nfsd statd lockd rquotad : ALL


$cat /etc/hosts.allow
ALL : 192.168.1.65/255.255.255.0, 192.168.1.80/255.255.255.0

```
ran

```

$sudo exportfs -ra
$sudo /etc/init.d/nfs-kernel-server restart
$sudo /etc/init.d/portmap restart


$sudo mount 192.168.1.65:/media blah
mount.nfs: mount to NFS server '192.168.1.65:/media' failed: RPC Error: Program not registered

```
from the client:

```

$sudo mount 192.168.1.65:/media blah
mount.nfs: mount to NFS server '192.168.1.65:/media' failed: RPC Error: Program not registered

```

<tears hair out>

The guides I've read seem simple, so I must be missing something easy.  Can't figure it out, so I'm looking for help after googling for 2 hours.  Thanks

---

### Post by jgarner on 2010-04-30
do you see NFS if you query with rpcinfo -p

---

### Post by Jive Turkey on 2010-04-30
Maybe try in /etc/hosts.allow:```

ALL:192.168.1.65
ALL:192.168.1.80
```

---

### Post by ene_dene on 2010-05-01
If you use UFW firewall make sure that you'r clients have the permission to connect on server on all ports.

---

### Post by KiLaHuRtZ on 2010-05-01
```
sudo apt-get update
sudo apt-get install portmap
```

---

### Post by ene_dene on 2010-05-01
Oh yes, after editing the exports file, have you:
```
sudo exportfs -a
sudo /etc/init.d/nfs-kernel-server restart
sudo /etc/init.d/portmap restart

```
?

---

### Post by kudude on 2010-05-02
> **jgarner said:**
> do you see NFS if you query with rpcinfo -p

yes
> **Jive Turkey said:**
> Maybe try in /etc/hosts.allow:```

ALL:192.168.1.65
ALL:192.168.1.80
```

no difference
> **ene_dene said:**
> If you use UFW firewall make sure that you'r clients have the permission to connect on server on all ports.
don't know what UFW is, probably not (?) using it

> **KiLaHuRtZ said:**
> ```
sudo apt-get update
sudo apt-get install portmap
```
up to date

> **ene_dene said:**
> Oh yes, after editing the exports file, have you:
```
sudo exportfs -a
sudo /etc/init.d/nfs-kernel-server restart
sudo /etc/init.d/portmap restart

```?
yes

Now I see:

```
$ sudo mount 192.168.1.65:/media blah -v
mount: no type was given - I'll assume nfs because of the colon
mount.nfs: timeout set for Sat May  1 22:57:09 2010
mount.nfs: text-based options: 'addr=192.168.1.65'
mount.nfs: mount(2): Input/output error
mount.nfs: mount system call failed
```

but if I tail dmesg, I see:

```
[11534.140022] rpcbind: server 192.168.1.65 not responding, timed out
```

which is very different from before.  Now running from the client machine (192.168.1.80)

```
$ sudo mount 192.168.1.65:/media tmp/ -v
mount: no type was given - I'll assume nfs because of the colon
mount: wrong fs type, bad option, bad superblock on 192.168.1.65:/media,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

this just seems like a b0rked mount, though

---

### Post by ene_dene on 2010-05-02
I don't know where the problem is, but here is how I would do it.
Assumptions:
server address: 192.168.1.65
client address: 192.168.1.80

On a server I'd install portmap, nfs-kernel-server.
Edited the /etc/exports file and put:
```
/media	192.168.0.2(rw,sync,no_subtree_check)
```
then exportfs -a as you have done, restart portmap and nfs-kernel-server as you have done.
Now on server you need to check if your UFW firewall is running (check this first, before you did anything, maybe this is the problem). You do this by:
```
sudo ufw status
```
If the output is:
```
Status: active
```
Than you can, either disable the firewall (sudo ufw disable), which I wouldn't do, or you can allow all traffic from local network to server by:
```
sudo ufw allow from 192.168.1.0/24
```
To me, it's easier with firewall anyway, than with host.allow, deny. If you use firewall you don't need to put anything in host.allow, deny.

Now, you don't have to mount anything on server if you just want to share /media folder.

On client, you have to have installed nfs-client. Then you just mount the drive:
```
sudo mount -t nfs 192.168.1.80:/media /folder_of_your_choice
```
Of course, that folder needs to exist on client, and it probably needs to be empty.

Btw, I have it configured in shown way, and it worked with Ubuntu server 9.10 and now works with Ubuntu server 10.04.

---

### Post by kudude on 2010-05-02
I appreciate the clear responses, and it seems that this should be no problem from the descriptions.  

ufw ISN'T running

```
$ sudo ufw status
Status: inactive
```

after running (on the client):
```
$ sudo mount 192.168.1.65:/media blah -v
mount: no type was given - I'll assume nfs because of the colon
mount.nfs: timeout set for Sun May  2 11:44:24 2010
mount.nfs: text-based options: 'addr=192.168.1.65'
mount.nfs: mount(2): Input/output error
mount.nfs: mount system call failed

```

from the server I see this:
```
tail dmesg
[57386.570805] nfsd: last server has exited, flushing export cache
[57387.795916] svc: failed to register lockdv1 RPC service (errno 97).
[57387.797685] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[57387.797712] NFSD: starting 90-second grace period
```

I also note that it doesn't matter what I choose for the SOURCE directory to mount
192.168.1.65:/home
gives the same output as
192.168.1.65:/media

fyi:
```
$ sudo exportfs -rva
exporting 192.168.0.2:/media
```

maybe I'll upgrade to 10.04, wipe if off the server and start over cleanly.  Seems like it must be something silly

---

### Post by ene_dene on 2010-05-02
I'm sorry, but I don't know where the problem is. Perhaps someone with more experience with NFS errors could be of better help.

I hope upgrading will change something.

---

### Post by KiLaHuRtZ on 2010-05-02
Is portmap installed on both server and clients?

---

### Post by kudude on 2010-05-02
> **KiLaHuRtZ said:**
> Is portmap installed on both server and clients?

sudo apt-get install portmap on both says they're up to date

---

### Post by KiLaHuRtZ on 2010-05-02
On your server, try this in this order...

```
sudo /etc/init.d/nfs-kernel-server restart
sudo /etc/init.d/portmap restart
```

---

### Post by Metabaron on 2010-10-18
You need to restart nfsd *after* restarting portmap.

---

