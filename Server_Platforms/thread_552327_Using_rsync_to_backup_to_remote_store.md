---
title: "Using rsync to backup to remote store"
date: 2007-09-16
forum: Server Platforms
---

### Post by Aikon- on 2007-09-16
I've recently decided that backing up my important documents and files is likely a GoodThingTM. I have a DreamHost account, so I thought using an off-site directory to store my backups would work dandy.

Obviously the initial backup will be the most time-consuming, since it has to transfer ALL files that I want backed up and from here on out only the changes will be transfered.

My question is this: How does rsync handle something like folder-renaming? Will it consider the new folder to be completely different from the old folder, thus uploading ALL of the contents in the new folder and deleting the old folder? Or can it tell that its really the same folder and just send a mv command?

Here's the rsync command I'm using:

```
rsync -az -e ssh --delete --exclude-from=/home/rsync-exclude /home/ username@host.com:home/
```

Thanks in advance,

-Aikon

---

### Post by HermanAB on 2007-09-16
No, don't rename folders.  Just base the backup on a different root subdirectory.

Note that when transferring lots of files over the internet, you may find that rsync fails every time after an hour or two.  The solution is to use the bwlimit parameter.  Limiting the BW consumption somehow allows rsync to keep going.

Maybe have a quick look at this: [http://www.aeronetworks.ca/rsync-ssh-howto.html](http://www.aeronetworks.ca/rsync-ssh-howto.html)

Cheers,

H.

---

### Post by ssam on 2007-09-16
> **Aikon- said:**
> 
My question is this: How does rsync handle something like folder-renaming? Will it consider the new folder to be completely different from the old folder, thus uploading ALL of the contents in the new folder and deleting the old folder? Or can it tell that its really the same folder and just send a mv command?


i am pretty sure it will delete and then reupload the folder/file which has been renamed.

if it is a one off, you could manually log into the remote server and rename the folder there before doing the rsync. but if you regularly rename big folders this will be a problem

---

### Post by Aikon- on 2007-09-16
> **ssam said:**
> i am pretty sure it will delete and then reupload the folder/file which has been renamed.

if it is a one off, you could manually log into the remote server and rename the folder there before doing the rsync. but if you regularly rename big folders this will be a problem

I checked with a friend at school that uses DreamHost to back up his documents as well; he said he's pretty sure it will delete the folder and re-upload.

Renaming the folder sounds reasonable though; when you rename a folder does it change the timestamp of the folder? If so, rsync might *still* consider it to need updating.. although I suppose once it goes into the folder it wouldn't find actual files that needed uploading so it wouldn't matter.

Thanks for the input guys, I'll let you know how it turns out after a week or so of using it =)

-Aikon

---

