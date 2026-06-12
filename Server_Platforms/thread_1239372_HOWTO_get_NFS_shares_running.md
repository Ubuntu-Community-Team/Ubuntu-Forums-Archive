---
title: "HOWTO: get NFS shares running"
date: 2009-08-13
forum: Server Platforms
---

### Post by fela on 2009-08-13
This is my first HOWTO really, so don't flame me.

This howto is not comprehensive, it just tells you the basics of how to get NFS (network filesystem) shares running from a server to client(s). I recommend you read all of this carefully, as you will end up making mistakes if you don't :)

I believe NFS is one of the best ways of transferring files from Linux to Linux. Nothing I've come across is as non-problematic and speedy as NFS.

First, of course you need to get the NFS shares running on the server. Login to the server, and open up a terminal:

```
sudo su
```

This logs you in as root after entering your password, so you can do anything you like. Beware - from now on you can brick your Linux installation if you're not careful.

```
apt-get install nfs-kernel-server nfs-common
```

When that's done, run (you can replace nano with any other text editor):

```
nano /etc/exports
```

Now you need to add an entry to the exports file. The syntax is this:

```
/path/to/nfs/share ipaddress1(rw,no_root_squash,async) ipaddress2(rw,no_root_squash,async)
```

You can have any number of ipaddresses, you can use hostnames instead (such as nas-server.local as in the case of my server), and there's a special way of defining multiple ip address spans:

```
192.168.1.0/25
```

In this case the share will be able to serve to any ip address that begins wit 192.168.1.0, up to 192.168.1.25.

As you might have guessed, each NFS share can only serve to the IP address(es) after it. Also, the NFS share can be any folder on the server, an example of sharing everything on the whole system (including remote filesystems mounted on the server) is this:

```
/ ipaddress1(rw,no_root_squash,async)
```

I do not recommend this as the computer (IP address) that you give it will be able to read (and write in this case) to every single file and folder that root on the server can access.

This brings us to the mount options. You might have noticed that I put

```
(rw,no_root_squash,async)
```

On each share.

What rw does, is mounts the share read/write. You can say ro instead for read-only.

no_root_squash means that the connecting computer has root permissions on every file on the NFS share (a good reason not to share /).

async makes the server reply to requests before the actual data is written to disk. This improves performance (especially if the disk is slow on the server), but if the server gets cut off or if there's a power cut, etc., then the data won't get written. So don't use this if you want extra reliability.

After you save the changes to the /etc/exports file on the server, you must also run:

```
sudo /etc/init.d/nfs-kernel-server restart
```

for the changes to take effect.

Now, onto the client.

On whichever client you've decided to use, you can mount the share like this:

```
mount ipaddress_of_server:/path/to/share /path/to/mount
```

EDIT: you might need to install nfs-common or something on the client before it connects. You can search around synaptic for a package like that if nfs-common isn't the right one.

[COLOR="Orange"]path to mount is just where you want to mount it on your client[/COLOR]. It can be anywhere you like but if you don't have permissions to write to it I think you need to be root to mount it (might have to be anyway, haven't checked yet :P). [COLOR="Red"]In which case you'd just put sudo in front of that command.[/COLOR]

If you'd like to mount the nfs share everytime the client computer boots up, edit the /etc/fstab file on the client and add:

```
ipaddress_of_server:/path/to/share /path/to/mount nfs defaults 0 0
```

That is the simplest way, of course there are more options but they're beyond the scope of this howto. To mount everything in the fstab, run:

```
sudo mount -a
```

Anyway, once you've run the mount command or added it to your fstab, you should be able to access it by navigating to /path/to/mount on your client.

That's it! I hope you enjoyed my howto, post with any questions.

---

### Post by Davlav on 2009-08-13
Hi!

Thanks for the tutorial.
I have followed to setup 2 PC's as client/server (on desktop and one jaunty server).

Unfortunately, I'm having some difficulties.

The connection is possible but when I try to move files, the process is very slow (=< 1 MB) and/or halts after copying a few MB (7.5, typically).

Both machines use an AMD Athlon 64 3000+, the client 2GB of RAM and the server 1GB. 

In addition, when I setup the fstab, it does complains "nfs is an unknown disk format".

Any ideas?

Thanks for your help!

David

---

### Post by fela on 2009-08-13
> **Davlav said:**
> Hi!

Thanks for the tutorial.
I have followed to setup 2 PC's as client/server (on desktop and one jaunty server).

Unfortunately, I'm having some difficulties.

The connection is possible but when I try to move files, the process is very slow (=< 1 MB) and/or halts after copying a few MB (7.5, typically).

Both machines use an AMD Athlon 64 3000+, the client 2GB of RAM and the server 1GB. 

In addition, when I setup the fstab, it does complains "nfs is an unknown disk format".

Any ideas?

Thanks for your help!

David

Oh sorry my bad. You might need to install nfs-common on the client, with

```
sudo apt-get install nfs-common
```

Tell me if that works. If not, just search around synaptic on the client for any nfs packages that you might need. I'm surprised it's connecting at all at the moment!

---

