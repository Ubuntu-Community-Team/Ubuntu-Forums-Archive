---
title: "rsync problem"
date: 2009-04-10
forum: Server Platforms
---

### Post by timteoh on 2009-04-10
Hi 

I need help to solve my rsync prob. I was able to rsync before this and everything was fine until recently. Whe I rsync I will get the following error message

rsync:opendir "/home/samba/..." failed Permission Denied

IO error encountered

Please help. I and doing an rsync to backup my server files. Thanks.

---

### Post by wkulecz on 2009-04-10
Did you perhaps forget to do sudo rsync this time?

rsync fails on the .gvfs gnome virtual file system files that are in any home directories that have been logged into at least once, but ignoring these errors has so far not caused any issues I could notice when I clone systems and boot on different hardware. Using --exclude *.gvfs makes them go away.

The IO error is potentially more serious if its a seperate error and not a cascading result of the Permission Denied, as it could result from a disk issue.

I've little actual experience with rsync, errors since it works so well, other than when I forget to sudo first and then get lots of errors on stuff my userID can't read.

--wally.

---

### Post by Kareeser on 2009-04-10
rsync is designed to work without root privleges. Check to see if the synchronized files are accessible by the remote and local user.

---

### Post by wkulecz on 2009-04-10
> rsync is designed to work without root privleges. Check to see if the synchronized files are accessible by the remote and local user.


True enough, but running it as root solves all the permissions problems making all files to be backed up accessable.  You can pretty much only count on non-root rsync getting everything if you are only backing up your home directory.

--wally.

---

### Post by timteoh on 2009-04-10
I have been doing it before for a few months and I did not get the prob. The IO error seems to be part of the permission denied message. All this while I have created a script to run the rsync and the error message just started recently. Any idea what is happening.

---

### Post by timteoh on 2009-04-10
any idea how I can scan and check the harddisk for errors. Worse case is I will have to reformat the harddisk and start from the beginning. Sigh.

---

### Post by BkkBonanza on 2009-04-10
It's very unlikely to be hard disk errors. You just don't get permission error messages for that. You'd get data error messages.

This sounds like you have recently added a file into the relevant directories that has root only permissions and now your script is tripping up on it. Check the permissions on files within the directories that the error occurs.

Change the rsync command to have -vv very verbose messages and see what file exactly it's caught up on.

---

### Post by timteoh on 2009-04-11
ok i will try and let you guys know the outcome

---

