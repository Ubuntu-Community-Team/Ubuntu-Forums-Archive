---
title: "[SOLVED] Can't unmount SSH folder"
date: 2008-01-18
forum: Server Platforms
---

### Post by NateMan on 2008-01-18
I mounted a folder through ssh onto my command line server. I did this using sshfs and everything worked nice, untill all of a sudden it stopped working. I attempted to unmount the drive but it says that drive is busy and cannot be unmounted. I can't even ls the drive, when I do I get an error saying transport endpoint is not connected. I would like to unmount and then remount this drive. I would have used the much more stable nfs, however the drive is a hangover from a windows box and is an ntfs drive. I don't have the space to move the data off and rebuild the drive in ext3 for linux usage. Any ideas on how I can umount this drive? -f doesn't even help. I'd love to be able to access this drive on my gnump3d server. 
Thanks.

---

### Post by fimblo on 2008-01-28
when this happens to me I've noticed that I have a hung process who's CWD is somewhere inside the mount-point. Try looking thru the process list (ps -ef), this could help.

Alternatively, say your mount-point is /home/user/mymountpoint. Say you started a process when you were standing in /home/user/mymountpoint/foo/bar. After some hours, you're like damn, sshfs has hung and II want to umount this partition. And you're wondering what process to kill. lsof to the rescue:)

lsof | grep mymountpoint

The above command should list process name, pid, etc. do a kill on the process, and you should be fine.

/fimblo

---

