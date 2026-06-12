---
title: "Backups!"
date: 2011-05-06
forum: Server Platforms
---

### Post by michellez on 2011-05-06
I would appreciate some help with possible solutions please :)

I have an Ubuntu server I need to back up incrementally over night. I need the back up to be stored on a USB hard drive attached locally to the server and also a Windows box remotely which I can mount a share from it on this box or FTP to, what ever is best.

I've found Bacula and rdiff. Any pro/cons of them? Anything they won't do that I want from above? Any thing else I should look at?

Any pointers appreciated!
Shell

---

### Post by michellez on 2011-05-06
Also it's a lot of data which over the internet (how it will get to the Windows share, via a VPN) would take for ever to do the first full back up. So I need it to be able to cope with me manually taking a copy off the linux box on to a USB hard drive, travelling to location 2 where the Windows machine is, and then copying it on to the share (local folder) where it will be backing up to in the long run via the share of SMB/FTP/something).

Then it also occurs to me that I need something that is friendly to the fact I do not having a full backup happening every week so if I needed to do a full restore via the remote location, I do not have to do hundreds of incremental restores to cover the full one if ever needed. Something with a separate monthly incremental maybe to reduce the amount of incremental restores required? Or am I looking into this too much and things will just deal with an original full backup + 300 days of incrementals? :s

Hope I'm making sense.

Thanks again
Shell

---

### Post by michellez on 2011-05-06
How about this idea (yeah talking to myself at the moment I know... lol). Where's the holes in it?! I know there will be some...

1) Use rsync to copy original data from Linux box to USB drive at site 1.

2) Travel to site 2. Copy data from USB drive to Windows machine. (Just thinking.. file system will need to be FAT32 for this to work unless I mess with ext3 drivers on Windows, urgh)

3) Travel back to site 1 and plug USB drive back in. Have it configured to run rdiff-backup nightly to USB hard drive.

4) Have it configured so after (3) has finished, it does a rdiff of the rdiff data to the remote Window share (with a copy of the first rsync data in it) which I would have mounted at say /mnt/remotebackup/.

---

### Post by a2j on 2011-05-06
rsync works really good for me.

[man rsync]("http://linux.die.net/man/1/rsync")

---

### Post by stmiller on 2011-05-06
Yeah rsync will do what you are after, though it can take some time to figure out what options and frequency you are after.

Also, crashplan is free for computer to computer backups:

[http://www.crashplan.com](http://www.crashplan.com)

Mac/Windows/Linux

---

### Post by ekool on 2011-05-06
I've been using rdiff-backup for about 5 years now and believe me, in that time I've had plenty of data that needed to be restored.

It's fast, secure and efficient.

I'd give a big thumbs up to rdiff-backup.

---

### Post by kgatan on 2011-05-07
If you had a linux box as the backup server in location 2 it would much easier.
Setup an rsync server on your Ubuntu server and use rsnapshots on location 2 to pull backups from the server.

Rsnapshots gives you a snapshot like backup using rsync. Its fast and easy to configure.
Each snapshot is stored in a folder as a copy of your entire backup directory but only using space of the actual changes.

There are also software to run an rsync server on windows, belive its called cygwin but im not sure on how well it works. Its possible you can push snapshots from the Ubuntu server to the cygwin windows server.

---

