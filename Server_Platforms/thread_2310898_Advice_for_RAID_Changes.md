---
title: "Advice for RAID Changes"
date: 2016-01-22
forum: Server Platforms
---

### Post by PuK84 on 2016-01-22
Howdy,

Its been a while since my last post but haven't stopped dabbling in Ubuntu! I am after some advice (not step-by-step guides, I can google that myself) regarding my home-server setup.

Currently I have a software RAID 5 configured and that is mounting to a shared folder for people on the network to access. I have services/scripts/etc that all reference folders on the RAID. What I want to achieve is to move all the shared data to its own folder (as opposed to being directly on the RAID) so I can store user specific data on the RAID for redundancy without it being shared to the whole network. How can I do this without breaking things? Should I move everything to its own folder and then create a symlink?

fstab is set up so that /dev/md0 mounts to /mnt/share.

Sorry if this makes no sense, and if more info is needed feel free to ask.

---

### Post by darkod on 2016-01-23
When you say "move to its own folder not on the RAID" it is confusing me little since the word folder is not directly related to the physical location of the data. The folders are inside the filesystem and for mounting the physical devices you use the mount points (which are only empty folders too).

So, does not on the RAID means to a new physical disk for example? Lets say you will get a new disk and it will be /dev/sdd. You will make one large partition on it called /dev/sdd1.

Using a symlink will probably be OK for the start, but long term I wouldn't use it. I see no need in such case to use symlinks.

One option is this. Under the above assumption about getting a new disk, you will rsync the shared data to /dev/sdd1 and start mounting /dev/sdd1 at /mnt/share. That way all your services/scripts related to the shared data can continue working without any modification because they refer to the mount point, not /dev/md0.

For the raid create a new mount point, like /mnt/raid for example, and you will use it for all the raid data.

Will that work for what you are trying to achieve?

---

### Post by MAFoElffen on 2016-01-23
"Folder" is more a Windows or Macintosh term relating to a file directory. >> Getting over the semantics and going on... To me, this is not really a question about RAID. RAID is just mentioned as it is in the mix. It is a question about Systems Administration strategies.

Lets talk Sys Admin concepts. I do many roles. As a Systems Admin, part of my job with is to make files physically located in many places to transparently appear to users as if it was on their machine. (A*ccess & Security*)

Why is it in many places? For physical data security. Following the logic of "*If you have all you eggs in one basket...*", if you drop that basket... So, using your business rules, the protection of some data may be more important than others... therefore RAID, Backups, Recovery plans...

Your logical storage is the collection through your storage management of your physical storage. When you segment your data, you usually think, what are the subjects and who needs access to it. When you think of it in that manner as it relates to administration, then it simplifies admin because you can give rights and privileges via usergroups. When you do the opposite and combine your physical segments, then you limited how you can control usergroup rights and privileges. (having to go down to user rights and privileges)

So, ultimately, the decision is yours, but weight all your options and weigh the cost/benefits. Sometimes when you think you are doing something to save yourself work, it may create more. But that is just my opinion.

EDIT-- The reason I answered it this way... RAID is just a layer where some of your data is on. Directories (or as you referred to as Folders), is at a different Layer
Underneath all is physical disk > partitions. 
... 
[RAID] > [LVM]. > Filesystems > Directorires > Files
... 
(Logical) Storage Manager >> Local physical disk || iSCSI || shares

---

### Post by PuK84 on 2016-01-23
Sorry, in trying to be specific I have ended up confusing myself and taking others down with me.

Currently the raid is mounting directly to /mnt/share and all the directories are located there (/mnt/share/Music, TV series, etc - hence why I say directly on the raid) I was wondering what is the best way to move all these directories to a specified "shared folder" (still on the raid) and then use the same mount point for that information. i.e I could have the "shared folder" still mounting to /mnt/share but also have /dev/md0/Wifes\ Docs mount to /mnt/Wifes\ Docs and so on?

---

### Post by darkod on 2016-01-23
No, I don't think you can mount specific subfolders from /dev/md0 to mount points. You mount the partitions (like /dev/sdXX) or raid arrays (like /dev/mdX)... But not subfolders on them.

What you could is create two or more samba shares (if that's how you do sharing) which will share the specific folder you want. Just don't forget that other folders you wish to share should not be subfolders of already shared folder. Did that make sense? :)

For example you could have 'Main Share' sharing /mnt/share/mainfolder, then 'Wife share' sharing /mnt/share/wifedocs, etc...

With permissions you will allow/block who can see each of the shares.

---

### Post by PuK84 on 2016-01-23
Ah, I figured would be the case but just wanted to make sure there wasn't an easier/"better" way to do it.

Thanks Darko!

---

