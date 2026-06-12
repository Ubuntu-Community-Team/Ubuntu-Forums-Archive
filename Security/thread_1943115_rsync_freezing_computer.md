---
title: "rsync freezing computer"
date: 2012-03-19
forum: Security
---

### Post by kevdog on 2012-03-19
So I ran across an interesting finding.

I originally ran rsync and it synced from client to Ubuntu server 164Gb of data.  I then changed the directory structure on the server -- basically moving the entire data a few subdirectories deeper.

I then re-ran the rsync operation, and due to a change in the inode numbers, the sync operation had to go through all the files.  This process however has locked up the server multiple times on multiple attempts -- Locking up means -- I can't pop open a terminal, and can reboot, I can't log in remotely.  I need to do a hard reset.  

I'm fairly certain this isn't supposed to happen.  I could only imagine a similar type action with various users on similar type systems.

Here is the last syslog.1 entry:
Mar 18 07:54:47 MrGiggles NetworkManager[1388]: <info> Unmanaged Device found; s
tate CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889))
Mar 18 07:56:27 MrGiggles rsyslogd: [origin software="rsyslogd" swVersion="5.8.1
" x-pid="1285" x-info="http://www.rsyslog.com"] rsyslogd was HUPed

---

### Post by papibe on 2012-03-19
Hi kevdog.

I've experienced frozen-like behaviour when rsync run out of space, and keeps slowly trying to sync anyway.

I've seen that even when there is enough space, but the filesystem is tight for it, rsync may significantly slow down when transferring big files.

Taking that into consideration I've separated my home's backup rsync command to deal with big files. For example, for VirtualBox's vdi files I use the --inplace option.

Just some thoughts.
Regards.

EDIT: if space is indeed the problem, you may want to test the option --delete-before too.

---

### Post by Ms. Daisy on 2012-03-19
> **papibe said:**
> Taking that into consideration I've separated my home's backup rsync command to deal with big files. For example, for VirtualBox's vdi files I use the --inplace option.
I need to try that option- rsync won't copy my vdi files no matter what I've tried.

@Kevdog, could you be running into file name length limit issues now that you're a few subdirectories deeper?

---

### Post by kevdog on 2012-03-19
I tried a few scenarios. I can do another actual sync of the 168 gb structure without error (i have 1.2 tb available), but if i change the directory structure and rerun the sync on the new directory structure it fails and locks.

---

### Post by papibe on 2012-03-19
> **Ms. Daisy said:**
> @Kevdog, could you be running into file name length limit issues now that you're a few subdirectories deeper?
Interesting idea. Although ext3/4 doesn't have path limits, other filesystems do.

@kevdog: what filesystem are you using on the server?

Regards.

---

### Post by kevdog on 2012-03-20
Ext4 for the server

---

### Post by kevdog on 2012-03-20
I'll end my rant with this thread -- but how damn annoying this problem is -- it freezes the entire computer -- the only way to resolve the issue is to hard reset the computer.  I can understand network communication failing, connections being dropped, but for the entire rsync process to lock the computer -- totally unacceptable.

/rant

---

