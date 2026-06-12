---
title: "NFS Stale File Handle"
date: 2007-02-26
forum: Server Platforms
---

### Post by bobslaede on 2007-02-26
Hey.
I've set up a server running NIS/NFS for some clients using there tutorials:
[https://help.ubuntu.com/community/SettingUpNISHowTo](https://help.ubuntu.com/community/SettingUpNISHowTo)
[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

Everything worked fine until late last week. All of a sudden I'm getting "NFS Stale File Handle" errors every once and a while, in surtain directories.

I have /home/user mounted thru automount (have also tried regular mounting via fstab and so forth).

For example, ~/.mozilla/firefox/profiledir is very crazy. If i run amok, with the ls command, 90% of the time I'll either get a Permission Denied, og NFS Stale File handle message. Which meens that no user can use firefox.
Also a problem with openoffice.

Now, no user is logged in more than once at a time, and no services or stuff is moving/deleting the files from the server (which would usually cause such a problem with NFS).

The servers exports is set up like it should (rw,sync,no_subtree_check), and so is the mounts on the client. I have tried without the no_subtree_check in the exports, but with no avail.

All client machines and server is running Edgy 2.6.17-11
The server is a Dell server-something, pretty decent, gigabit network and sata raid stuff going on.

How can this be fixed, and what the f is the problem? :)

Thanks!

---

### Post by cajetanus on 2007-04-24
I can confirm this same behavior, but only on Feisty - Edgy was working perfectly.

However, you can remount the share:
```

mount -t nfs server:/directory /mnt/directory
```

And the mounted directory will be accessible. I suspect something has changed in the bootup sequence that keeps nfs from mounting at boot. The clients report the error on startup.

You might try also the options rw,hard,intr in fstab to eliminate the Mozilla and OpenOffice errors. These errors come when there are dropped packets on preferences and so forth. 'hard' option keeps the thread locked until the data has passed. The 'intr' allows the application to disconnect if there is a timeout - otherwise FF will just lockup.

The clients updated to Feisty without a single problem, so I updated the server over the weekend. Not a good move - I must say running around 15 machine Monday morning to manually mount the shares was not a fun exercize.   My work-around for now is just preventing people from rebooting.

It might be due to the new kernel as well. I am still looking into it. Sorry can't be much more of a help, but I can confirm that you aren't just seeing things :)

caj+

---

### Post by TyphoonJoe on 2007-04-25
Well since you say it fails 90% of the time and works 10% - that seems to indicate performance rather than a setup issue.

I have seen issues if you do not have enough nfs daemons running.  Requests simply become queued, and even a couple users can swamp your default nfs daemon.  

Try increasing the number of daemons, been a while since I've set up nfs, but check out:

[http://nfs.sourceforge.net/](http://nfs.sourceforge.net/)

---

### Post by trmentry on 2007-04-30
I'm getting this error on Fiesty as well.

My setup is a base install of Fiesty.  I manual mount and NFS directory when I need it.

```

sudo mount server:/home/trmentry /home/trmentry/mnt/server

```

And all is fine.  At some point, it will jsut stop working and get a:

```

Stale NFS file handle

```

I stop portmap on Fiesty and wait a little bit... restart, I'm able to then to umount it and remount it.  

This appears to be a Fiesty issue b/c my gentoo box mounting the same server doesn't have this issue.  However if Fiesty has this issue, it takes my gentoo box out along with it.  If I dont' mount Fiesty, gentoo has no issues ever.  The server is gentoo as well.

Server /etc/exports
```

/home/trmentry  xx.xx.xx.4 (rw,sync) xx.xx.xx.120 (rw,sync)

```
.4 is gentoo box that has no issues as long as fiesty (120) doesn't bork it.

Any ideas?

---

### Post by trmentry on 2007-04-30
Update:  I was reading on Gentoo forums about people having similar issues with their clients.

Appears the NFS 1.0.12 maybe the issue.  I downgraded to 1.0.6 and so far Ubuntu has no issues.  Appears that only servers on 1.0.12 had issue.  Clients can be at .12.  So I took both servers to .6 and so far so good.

---

### Post by chalex on 2007-04-30
Random link: [http://sysunconfig.net/unixtips/stale_nfs.txt](http://sysunconfig.net/unixtips/stale_nfs.txt)

Also learn the difference between hard and soft mount: [http://uw714doc.sco.com/en/NET_nfs/nfsT.mount_cmd.html](http://uw714doc.sco.com/en/NET_nfs/nfsT.mount_cmd.html)

---

### Post by jim.mccroskey on 2007-06-01
Turns out that in my case I had defined a second ip incorrectly on the client. The second ip worked but must have confused nfs. After I configed the interfaces as below the stale nfs disapeared. I had left out network and broadcast parms.

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
auto eth0

# The primary network interface
iface eth0 inet static
address 144.163.6.225
netmask 255.255.255.0
gateway 144.163.6.1
network 144.163.6.0
broadcast 144.163.6.255

auto eth0:1
iface eth0:1 inet static
address 144.163.6.226
netmask 255.255.255.0
gateway 144.163.6.1
network 144.163.6.0
broadcast 144.163.6.255

---

