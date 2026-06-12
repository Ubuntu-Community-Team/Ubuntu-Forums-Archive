---
title: "NFS client fails to mount files on server"
date: 2009-09-07
forum: Server Platforms
---

### Post by raymondvillain on 2009-09-07
32 bit server.  Want to mount certain directories and files on a client running Jaunty (64 bit).  Both machines are desktops.  On the server, I've specified the files/directories in the /etc/exports file, and also the IP address of the client:

/srv/netshare  192.168.0.253(rw)

On the client, I've added a line to /etc/fstab:

SERVER_NAME:/srv/netshare /mnt nfs _netdev,rsize=8192,wsize=8192,soft 0 0

I thought this would mount the /srv/netshare directory located on the server SERVER_NAME at point /mnt on the client, but when I open Nautilus and navigate to /mnt, it says "...loading" and nothing else happens.

In a terminal window I can see that nothing has been mounted on /mnt.

What else is necessary in order to use this procedure successfully?

---

### Post by volkswagner on 2009-09-07
I have used this [NFS-HowTo]("http://ubuntuforums.org/showthread.php?t=249889").



Hope it helps.

EDIT:  I am not sure /mnt is the best place to mount.  I am not sure but you may want to verify that /mnt is not created on each boot.

---

### Post by yeats on 2009-09-07
on the client, what happens when you 

```
sudo mount -a
```

?

---

### Post by AndyCooll on 2009-09-07
As volkwagner says, for starters you shouldn't be mounting directly on to the /mnt directory create a folder within the /mnt directory itself, e.g.
```
sudo mkdir /mnt/netshare
```
and then mount your folder on to that.

See if that makes a difference and report back

:cool:

---

### Post by raymondvillain on 2009-09-07
Well, thanks for all the help.

Chrissharp123 suggested "sudo mount -a"

When I did that I thought nothing happened because the command prompt just popped back up, but maybe it did something.  Anyway, there was no output.

I also tried AndyCooll's suggestion to create another directory, /mnt/netshare, and use it instead of just /mnt.

The result of all this fumbling about is that now I think its working.

I saved a file on the client, and, using nautilus on the server, I can see it where it ought to be.

I am working my way through the NFS tutorial suggested by volkswagner.

Thanks again, all.

---

### Post by yeats on 2009-09-07
> When I did that I thought nothing happened because the command prompt just popped back up, but maybe it did something. Anyway, there was no output.

A principle in Linux is "no news is good news", so when commands succeed, you get the prompt back.  This means that the mount -a command mounted everything defined in /etc/fstab without problems.  You can always verify what is mounted on your system by doing:

```
mount
```

---

### Post by raymondvillain on 2009-09-07
Thanks, chrissharp123.  Does this mean I need to issue the mount command every time I log on, in order to access the share?

I know this sounds like a beginner's question, but I am really green about server stuff.

I'm marking this one SOLVED.

---

### Post by yeats on 2009-09-07
> **raymondvillain said:**
> Thanks, chrissharp123.  Does this mean I need to issue the mount command every time I log on, in order to access the share?

You said:

> On the client, I've added a line to /etc/fstab:

SERVER_NAME:/srv/netshare /mnt nfs _netdev,rsize=8192,wsize=8192,soft 0 0

/etc/fstab is where your computer looks to know which filesystems to mount at boot time.  This should take care of it.

> I know this sounds like a beginner's question, but I am really green about server stuff.

No need to apologize.  All of us had to start somewhere.

---

