---
title: "Snapshot Backup Software"
date: 2007-06-14
forum: The Cafe
---

### Post by FryerFox on 2007-06-14
I'm working on a snapshot system similar to Apple's TimeMachine (a snapshot is a copy of a directory at a certain point in time that doesn't use space for the files that haven't changed). 

But I need people to test it out and provide suggestions. I have posted in a couple of other forums (Programming and I mentioned it in a thread on Gusty), but I don't think I'm reaching the right audience. So to avoid spamming the 'serious' forums, I'm posting here in the cafe (where you can talk about anything, I guess).

From the docs:

> TimeVault is a simple front-end for making snapshots of a set of directories. Snapshots are a copy of a directory structure or file at a certain point in time. Restore functionality is integrated into Nautilus - previous versions of a file or directory that has a snapshot can be accessed by examining the properties and selecting the 'Previous Versions' tab.

Snapshots are protected from accidental deletion or modification since they are read-only by default. The super-user can delete intermediate snapshots to save space, but files and directories that existed before or after the deletion will still be accessible.

.deb installer and docs are on Launchpad:
[https://launchpad.net/timevault/+download](https://launchpad.net/timevault/+download)

Anyone interested in giving it a spin?

---

