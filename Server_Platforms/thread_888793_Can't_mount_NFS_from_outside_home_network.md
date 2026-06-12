---
title: "Can't mount NFS from outside home network"
date: 2008-08-13
forum: Server Platforms
---

### Post by johnnybeem on 2008-08-13
Recently set up NFS on a server in my house so that I can access shared files from different computers. Now I want to extend this so I can access the files from outside my home network.

My router has a static IP (xx.xx.xx.xx) and on the local net is 192.168.0.1. The server has static IP 192.168.0.200. I thought (from searching Google a bit) that all I would have to do is forward ports 2049 and 2219 on the router to the server. But that's not working (I forwarded both TCP and UDP for both ports). There is no firewall running on the server, just on the router.

On the server...
```
$ rpcinfo -p
   program vers proto   port
    100000    2   tcp    111  portmapper
    100000    2   udp    111  portmapper
    100024    1   udp  59014  status
    100024    1   tcp  55016  status
    100003    2   udp   2049  nfs
    100003    3   udp   2049  nfs
    100003    4   udp   2049  nfs
    100021    1   udp  46358  nlockmgr
    100021    3   udp  46358  nlockmgr
    100021    4   udp  46358  nlockmgr
    100003    2   tcp   2049  nfs
    100003    3   tcp   2049  nfs
    100003    4   tcp   2049  nfs
    100021    1   tcp  59959  nlockmgr
    100021    3   tcp  59959  nlockmgr
    100021    4   tcp  59959  nlockmgr
    100005    1   udp  42752  mountd
    100005    1   tcp  37467  mountd
    100005    2   udp  42752  mountd
    100005    2   tcp  37467  mountd
    100005    3   udp  42752  mountd
    100005    3   tcp  37467  mountd
```

On the client... mounting via local network
```
$ sudo mount 192.168.0.200:/nfs/share /mnt/tmp
```
(works fine)

On the client... mounting via Internet
```
$ sudo umount /mnt/tmp
$ sudo mount xx.xx.xx.xx:/nfs/share /mnt/tmp
mount.nfs: internal error
```


Please help!! I think the problem is that mountd is listening 37467 and 42752 (not on 2219), but how do I force it to listen on 2219??

---

### Post by moonpup on 2008-08-13
Exporting NFS over the internet is an extremely bad idea from a security perspective. NFS was really designed to be used on internal protected networks.

If you just want to securely get/put some files to your home server, then learn how to use ssh and sftp/scp.

---

### Post by .nedberg on 2008-08-13
> **moonpup said:**
> Exporting NFS over the internet is an extremely bad idea from a security perspective. NFS was really designed to be used on internal protected networks.

If you just want to securely get/put some files to your home server, then learn how to use ssh and sftp/scp.

+1

No way I would use NFS over the internet. SFTP is a way better solution, though a bit harder to set up...

---

### Post by ilrudie on 2008-08-13
+1 SSH/SCP.

Allowing internet access to NFS is not a good idea.  If you really need NFS over the net try creating an ssh tunnel for the ports you need and **do not** open the NFS ports on your firewall.

---

### Post by johnnybeem on 2008-08-13
oh boy, okay :) My second question was gonna be how to make this secure lol but I guess I will try and set up an SSH tunnel. Sounds like the best option.

Thanks for the help!

---

### Post by ilrudie on 2008-08-13
Here ya go:

[http://www.howtoforge.com/nfs_ssh_tunneling](http://www.howtoforge.com/nfs_ssh_tunneling)

Its for Debian but it should at least get you 90% there.

---

### Post by windependence on 2008-08-13
> **johnnybeem said:**
> oh boy, okay :) My second question was gonna be how to make this secure lol but I guess I will try and set up an SSH tunnel. Sounds like the best option.

Thanks for the help!

What exactly are you trying to accomplish in the end? If we know that we may be able to give you a better solution.

-Tim

---

### Post by hrod beraht on 2008-08-13
> **johnnybeem said:**
> oh boy, okay :) My second question was gonna be how to make this secure lol but I guess I will try and set up an SSH tunnel. Sounds like the best option.

Thanks for the help!

Are you just trying to access some files? If so, tunneling seems a bit redundant. Just access the stuff through SSH directly. Once SSH is set up on your server, just do **Places** --> **Connect to Server** and select SSH under **Service type** and you can access through Nautilus.

Bob

---

### Post by johnnybeem on 2008-08-13
okay so lemme explain... I have 3 computers all remote from one other. One is the server (it is in my house), the other is my desktop (at school), and the last is my laptop (roams around everywhere). I want the desktop and the laptop to have the same /home/john/Documents (and a few other directories), so that the files are the same no matter which computer I'm on.

Right now since it is summer and I'm home, I have all 3 computers on the same local network and NFS works fine. But when I go to school they will be on 3 separate networks. If possible I want it to work the same way as before (a network mounted /home/john/Documents).

I realize I could do this in /etc/fstab, but instead I set up autofs - so that the shares are only mounted when I need them.

Sounds like NFS with an SSH tunnel is possible with fstab, but would it work with autofs? What's the best way to go about this?

---

### Post by windependence on 2008-08-13
I think by trying to do it via autofs you are introducing way too many variables in the mix that may not mount the share. fstab is the way to go IMHO with a secure tunnel of course. I'm sure someone can come up with a better idea for what you are doing though. At least now we understand you are trying to remotely mount your /home. That makes things clearer.

-Tim

---

### Post by StickyStyle on 2008-08-13
See if SSHFS suites your needs [http://fuse.sourceforge.net/sshfs.html](http://fuse.sourceforge.net/sshfs.html). It lets you mount remote servers over a SSH connection, with nothing more needed.
To me it sounds like it would fit your task perfectly.

---

### Post by ilrudie on 2008-08-14
Perhaps rsync is a better option then mounting it up.  When you want to edit documents on your server you rsync them out to whatever box you are working on and when you are done you rsync them back (over ssh of course).  I'm not sure if cvs, svn or git are good options for documents but there might also be some sort of remote version control for docs you could setup.  Also google docs does a pretty good job of this if you can get comforable with giving some of your documents to the cloud.

---

