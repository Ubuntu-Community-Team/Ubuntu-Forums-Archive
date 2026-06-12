---
title: "Server space"
date: 2008-12-22
forum: Server Platforms
---

### Post by any.linux12 on 2008-12-22
Hi!

I have an ubuntu server 8.04 with just the basic installation but already with 17GB! I don't want to save much space but I would like to know why my /proc is 6GB?!?!?!?!?!

---

### Post by any.linux12 on 2008-12-22
Anyone has a server?

How much space has yours /proc??

---

### Post by hictio on 2008-12-22
> **any.linux12 said:**
> Hi!

I have an ubuntu server 8.04 with just the basic installation but already with 17GB! I don't want to save much space but I would like to know why my /proc is 6GB?!?!?!?!?!

Sorry, I don't fully understand, do you mean your Server installation, without any other data added, its using 17 GB?
There is something wrong there...

Try this, to see which directory is using the most HDD space:

```

cd / (ENTER)
sudo du -sh * | less (ENTER)

```

It'll take a while to run the second one.

---

### Post by any.linux12 on 2008-12-22
yes my installation is 17GB (at least is what webmin recognises)
and ok I have openSSh and webmin but just that (no samba no lamp no nothing)

How much is you /proc????

---

### Post by cdenley on 2008-12-22
How are you determining the usage of /proc? Is it a separate partition? /proc contains links to all open files, so if you follow the links, then it can contain some very large files. Of course the links themselves are very small.

---

### Post by kavon89 on 2008-12-22
try wiping the drive (KillDisk or another safe data eraser) so it becomes unformatted and then install ubuntu server.

17GB is much too large for a system that doesn't even have a desktop.

---

### Post by koenn on 2008-12-22
don't wipe anything just yet. 

Seeing that you mention /proc, which is 6 GB of the 17 GB you mention, you should know that 
A/not all that you see as files are really files, and 
B/it's possible some files get counted twice, or more
C/not every file under / sits on your disks

explaining A/ :
*Unix/Linux present all sorts of stuff as files and directories, while they're not. Typical examples include
/proc : a processes in memory (but represented as files)
/dev/shm : shared memory, a part of RAM used to exchange data between processes

these things only exist in RAM, but because they look like files, they might get counted by 'disk usage' programs 


B/
*Linux has 'links', which is something like a "shortcut' to a file, but to most programs, these links look and behave as normal files. So it's possible that some files are counted twice or more, depending on how many links are pointing to them.

C/
* external storage that is mounted under / or a subdirectory thereof (/mnt, /media) appears as part of your filesystem, so a program that just adds up file sizes might also be counting external drives, network shares, CD-roms, ...


run ```
df -h
``` to get a more accurate readout of used disk space.

---

