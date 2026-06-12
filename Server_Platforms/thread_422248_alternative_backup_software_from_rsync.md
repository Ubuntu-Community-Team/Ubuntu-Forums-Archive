---
title: "alternative backup software from rsync"
date: 2007-04-25
forum: Server Platforms
---

### Post by himurakenshin on 2007-04-25
I wanted to know if there are any alternative software which could be used instead of rsync, and what are the advantages and disadvantages? Any help would really be appreciated.

Thanks very much.

---

### Post by jtc on 2007-04-25
I'm not sure if I'd call rsync in itself backup software. No more then cp or tar anyhow.

There are lots of different backup software out there. What kinds of backup do you want to make?

---

### Post by steevc on 2007-04-25
I use rdiff-backup to make remote, secure, incremental backups. It's all command line, but not too hard to set up. I have files listing what should be excluded. I'm mainly interested in backing up all my documents and settings. It's all stored on the remote server so that I can just copy it back if required.

As jtc said, we need to know what your requirements are.

---

### Post by himurakenshin on 2007-04-27
I use Rsync and ask it to backup a certain folder to a server with the -t and --delete modifiers. Is this not using it as a backup software? what is the difference between this method and using rdiff?

> **jtc said:**
> I'm not sure if I'd call rsync in itself backup software. No more then cp or tar anyhow.

There are lots of different backup software out there. What kinds of backup do you want to make?

The way in which I am using Rsync seems to satisfy my needs. I am doing a assignment on backup software, so I want to find a "competitor" to rsync and justify why rsync is better suited for my needs (creating a mirror at another location/hard disk)

---

### Post by jtc on 2007-04-27
Yes, rsync is a tool which can used to make backups, just as an hammer can be used to build houses. That neither makes rsync a backup software or the hammer a housebuildning tool.

What rdiff-backup (and most other backup software) do is keep different version of your saved files. Instead of just being able to restore your latest version of a document you can also restore it the way it looked, for example, ten days ago.

---

### Post by himurakenshin on 2007-04-27
Ok, now however if this functionality is not required (only the final saved version is required), would using rsync be sufficient? Plus what other alternative software is there to do this?

---

### Post by elst on 2007-04-28
> **himurakenshin said:**
> Ok, now however if this functionality is not required (only the final saved version is required), would using rsync be sufficient?

The ability to recover file versions from multiple previous points in time is key to backups, so I'd agree with jtc that rsync isn't really a backup application in itself. If you want a glimpse of what Open Source applications are currently out there, try browsing packages.ubuntu.com.

You could also take a slightly different approach and look at a "version control" system (VCS) rather than a regular backup utility. VCS handle file versioning in a sophisticated manner, and provide backups almost as a side-effect. I switched from rdiff-backup to storing my work files with Subversion, but there are several other products.

---

