---
title: "sshfs in fstab"
date: 2011-04-14
forum: Server Platforms
---

### Post by pzs on 2011-04-14
I'm using sshfs as a quick and convenient remote mounting tool. It works well from the command line, using ssh keys. I also have the following line in my fstab, that means I can mount it quickly:

```

sshfs#pzs@remotehost:/remote/dir	/local/dir	fuse	defaults,idmap=user,user	0	0

```

However, when I reboot the machine it doesn't come up. There aren't any error messages in /var/log/messages, but I'm guessing that the problem is that during bootup, root is the one doing the mounting and root does not have my ssh key. 

Has anybody tackled this problem? I could just have a tiny shell script in userspace to run and mount this, but I'm trying to do this the pucker way...

---

### Post by gobbledigook on 2011-04-14
have you read the [documentation here?]("https://help.ubuntu.com/community/SSHFS#Command-line Usage")

as you are using idmap=user it appears that it shouldn't matter... your machine is creating an ssh session to the remote moachine... however the remote machine is doing all the work from its end and just piping over the mount.

plus it appears you have an extra user? idmap=user,user

---

### Post by pzs on 2011-04-15
> **gobbledigook said:**
> have you read the [documentation here?]("https://help.ubuntu.com/community/SSHFS#Command-line Usage")

That's where I got my fstab line from.

> plus it appears you have an extra user? idmap=user,user

I need that so I can do mount /local/dir without it saying "only root can do that".

I know it's the remote machine that's doing all the work, but I still need the ssh connection to tunnel the data over. The root user doesn't have permission to create that ssh tunnel, because it doesn't have access to the ssh key for my user.

---

### Post by gobbledigook on 2011-04-15
> **pzs said:**
> I need that so I can do mount /local/dir without it saying "only root can do that".

which suggests that root is not making the connection?? (this is pure speculation!) 

> **pzs said:**
>  The root user doesn't have permission to create that ssh tunnel, because it doesn't have access to the ssh key for my user.

ok... so thinking around the problem... log in as root, sudo su, connect to the remote machine and the key will be added.

alternatively there is a guide to [URL="https://help.ubuntu.com/community/SSH/OpenSSH/Keys"]ssh keys in the documentation 
[/URL]

---

