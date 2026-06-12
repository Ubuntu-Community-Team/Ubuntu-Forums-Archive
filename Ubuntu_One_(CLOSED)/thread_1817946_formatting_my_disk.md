---
title: "formatting my disk"
date: 2011-08-04
forum: Ubuntu One (CLOSED)
---

### Post by ilantal on 2011-08-04
My friend has a messy disk with Windows Vista and Ubuntu. If possible, one way to solve the problem is to take all the useful data and upload it to Ubuntu one. That would give an additional copy in the Ubuntu cloud.

Then we could format the disk, put on only Ubuntu and get rid of Windows. The question is: how do I guarantee that I hook back onto my original cloud? To lose the data in never-never land isn't very clever.

Thanks,
Ilan

---

### Post by ilantal on 2011-08-04
Sorry, I see there is a single sign in according to the email. I must have signed in long ago and forgotten about it. The sign in uses an email address and a password which I have long since forgotten.
At least it wouldn't be a problem to remember the password while formatting the disk.

---

### Post by Megaptera on 2011-08-04
Uploading to Ubuntu One could be slow if there's a lot of stuff. why not copy it all to external media (eg external hard drive)? That may be quicker - also you can then set up a regular backup routine.

---

### Post by ilantal on 2011-08-04
Thanks for the reply. First of all it is only limited data, pictures, songs and favorites for Firefox. It is a good idea to get data which is "valuable" to a place off disk since the disk may go bye-bye at any moment.

Your idea was my original plan. Copy the data over the LAN to one of my computers and then copy it back. I already taught my wife that she had better keep a copy of her important Windows data on my Ubuntu disk (directory shared over the LAN). No one guarantees any given disk.

---

### Post by Megaptera on 2011-08-04
In case it helps, I use Xmarks to backup and sync my bookmarks. It's compatible with Firefox, Chrome and IE. Also good for Ubuntu & Widows.

[http://www.xmarks.com/about/features](http://www.xmarks.com/about/features)

---

### Post by ilantal on 2011-08-04
Thanks. I wasn't aware of Xmarks. Personally I make very little use of bookmarks and use Google instead. However many of my friends make much heavier use of bookmarks over multiple computers and browsers.
I will look into your suggestion. Thanks again.

---

### Post by Megaptera on 2011-08-04
You're welcome!

---

### Post by duanedesign on 2011-08-04
File Sync applications/services like Dropbox and Ubuntu One do not make the best backup solution. This is because the folders are synced, meaning changes on one device are reflected on others. You could sync the folder, disconnect Ubuntu One, reinstall Ubuntu, do not copy any config files from the old install, add your computer with the fresh install to your Ubuntu one account and it would be treated as a new device and sync the files from your cloud. Though I agree with the previous post that their are better solutions for this use case.

We realize lots of people would like to use Ubuntu One as a backup. So in the next Ubuntu release Ubuntu One will have Deja Dupe integration. You will be able to select a folder to back up to your cloud storage and that folder would not reflect local changes like Cloud Folders but be static. Look for that in Oneiric Ocelot.

Thank you,
duanedesign

---

### Post by ilantal on 2011-08-04
I very much appreciate your time in answering. I was trying to kill 2 birds with one stone here. First and foremost, if something goes wrong there is backup in the cloud. My important data is COPIED to Ubuntu One, just in case another computer erases something which I need.
As long as I've got you there is a super nice feature which I use all the time in dropbox, directory sharing with other users. For example I have dropbox on my local group but I have a shared directory with Beth Israel hospital. Whenever there is clinical data I need, it gets dumped into their group on the shared folder and it appears on my machine. It has made ftp obsolete for me, and I simply can't work without dropbox.
I don't know if it is possible in Ubuntu One, if so it would be great.

For my friend, if the data were really important I would transfer it across the LAN to my disk. At least I was happy to see how pleased she was to discover Linux. She still has the old Windows Vista which just barely works.

---

### Post by duanedesign on 2011-08-11
>  directory sharing with other users. For example I have dropbox on my local group but I have a shared directory with Beth Israel hospital. Whenever there is clinical data I need, it gets dumped into their group on the shared folder and it appears on my machine. It has made ftp obsolete for me, and I simply can't work without dropbox.
I don't know if it is possible in Ubuntu One, if so it would be great.

Yes you can share folders in your $HOME with other Ubuntu One users. This is an awesome feature and something I use a lot to share files with my coworkers. You right-click on the folder and select Share. Enter the email of the person you wish to share with. They will receive an email and click a link to accept your share. These directories are kept in the 'Shared With Me' folder in your ~/Ubuntu One folder.

---

### Post by ilantal on 2011-08-11
Thanks for letting me know about that sharing feature! It is exactly what I do with dropbox. For now, most of my friends are still with Windoze, but just yesterday another friend of mine had an XP so screwed up that I told her to forget it and switch to Ubuntu. She was pleased with the results.

---

