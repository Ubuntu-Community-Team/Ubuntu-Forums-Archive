---
title: "Ideas for a Dropbox like synchronization, share and backup"
date: 2013-01-09
forum: The Cafe
---

### Post by grigio on 2013-01-09
Hi, I'd like to share some info about a possible self-hosted Dropbox environment in LAN or somewhere else. I know there is SparkleShare(git) or OwnCloud but I don't think git is good for big files and I'd like to store the history only in a remote server.
On the other hand rsync and unison need to compile everytime a list of what is changed or not before starting the transfer, if you have many small files is more the time needed to scan than the time spent to transfer :(

So here are the requirements and some ideas about how to implement it:
1. painless synchronization with a remote server. A daemon should watch recursively a folder and transfer or enqueue a file if it is changed (on save).
2. TimeMachine like remote snapshots, e.g. one every hour, one per week, one per month.
3. The remote working copy should be browsable without sync, via smb, nfs or web gui

Implementation ideas:
1. **inotify** isn't anymore a such "new technology" to monitor the filesystem changes. If the server is available, rsync/unison/ssh could be used to sync the changes otherwise you have "to cache" and repeat the sync sequence when the server will be available.. (how?)
2. **ZFS**. This incredible filesystem is available natively on Solaris, Freebsd, .. and Linux (Zfsonlinux). 
2./3. ZFS, snapshotting and smb/nfs/.. shares are easly doable with FreeNAS (Freebsd + WebUI). [http://www.freenas.org/features/screenshots](http://www.freenas.org/features/screenshots)

**Open problems**
- Often I just rename or move big files, is there a software smart enough to understand I'm not moving over the net a completely new file? FreeFileSync does it building a db in the root directory.
- **Shotwell**: some useful software doesn't save the editing on the file in-place but on a local db :( so If you want to share the changes you have **to export and save again** the photo :( I don't see a solution to this problem. If you share the db and the photos over the net you risk to override or corrupt the db :( because there is no lock.

That's all, if you have other suggestions, issues, other sw to suggest please reply.

---

