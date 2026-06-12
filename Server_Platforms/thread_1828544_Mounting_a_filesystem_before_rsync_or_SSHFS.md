---
title: "Mounting a filesystem before rsync or SSHFS"
date: 2011-08-19
forum: Server Platforms
---

### Post by lone.ranger on 2011-08-19
Hi guys,

Here are a couple of my use cases:

1. From my client, I want to use SSHFS to view a mounted MVFS on the server. My problem is that after SSHFS has been established, I am not given the opportunity to use the same session to execute the command to mount it. So when I do the command ls from the client, the directory is just empty?

The question: Is there a way to execute a couple of commands using the same session used by SSHFS?

2. This is also true for GNOME-commander, say I have already connected to the server and seeing some file system. Then I want to execute a command on the server to be able to mount the FS.

3. Same with rsync. So I copy from this MVFS and unable to 'hijack' to enter a couple of commands before the sync can proceed.

Just more info: I am sort of proxying ~ setting up SSHFS to the server that will mount another FS because this FS is MVFS. The server where I am connected to is supported platform to setup MVFS whereas my client is not supported.

Some attempts I've done:
I've entered the command in the .profile in the home directory to mount the system. But for some reason, .profile does not seem to get executed when i use SSHFS or use gnome-commander.

Any thoughts?

---

### Post by howefield on 2011-08-20
Thread moved to "*Server Platforms*"

---

