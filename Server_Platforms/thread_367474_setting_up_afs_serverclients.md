---
title: "setting up afs server/clients"
date: 2007-02-22
forum: Server Platforms
---

### Post by jsvidyad on 2007-02-22
Hi!!!


    I'd like to setup an afs server and some afs clients. The server/clients will run either edgy or dapper. Can someone please tell me how I can set this up???

   Thanks in advance for your help.

---

### Post by kidders on 2007-02-22
Hi there,

Check out [http://www.openafs.org/](http://www.openafs.org/). There's some OpenAFS stuff in the repos that you can use.

Afaik AFS is not very commonly used. Can I ask why you chose it?

---

### Post by jsvidyad on 2007-02-24
I wanted an alternative to NFS. I want a folder on a remote computer to be mounted as my /home directory on my local computer at boot-time.

   What would you suggest????

---

### Post by jtc on 2007-02-24
How about taking a look at [sshfs]("http://fuse.sourceforge.net/sshfs.html")? It can be told to mount from /etc/fstab. Of course, since it involves mounting your homedir you won't have a ~/.ssh/, so I guess you might have to do some small tinkering in /etc/ssh/ssh_config instead.

---

### Post by jsvidyad on 2007-02-26
I tried , but I am unable to get sshfs to mount at boot-time.

---

### Post by kidders on 2007-02-28
Yeah, that would be a little tricky to achieve.

To be honest, I would strongly suggest using a well-known sharing solution, particularly for /home directories. That way, the setup instructions, along with the solutions to any common problems, are more easily available.

If you don't mind me asking, why are you reluctant to use NFS? If it's been giving you problems, we can probably find you a good solution. On the other hand, if you're tired of NFS, and looking for something new to try, there's no reason not to play around with some alternatives. :-)

**Edit:**
For your SSHFS, I would try creating directories in /home (the mount point, not the actual filesystem) for each user, and copying in all the .ssh directories. That way, SSHFS should have access to all that it needs, *before* the filesystem mount takes place. (You may have already tried this to no avail.) That approach is fraught with problems in the long term though ... but if you got it to work, it would at least be a place to start.

---

### Post by darkadept on 2007-06-07
I've been using NFS up til now but i've been running into the location-independent problem.

What I would like is to have NFS set up, but access it like you can with DFS on windows.

So instead of my client mounting "myservername_alpha:/share/stuff" and "myservername_beta:/share/morestuff";
i would like to access them like "dfsroot:/share/stuff" and "dfsroot:/share/morestuff".

Is this not possible with NFS? It sounds like AFS can do it, but I like to use more standard protocols when possible.

Another idea I had would be to have a NFS server that acts as a gateway of sorts to all my other NFS servers. Or is multiple NFS sharing a bad practice?

Anyways, thanks for the help.

---

