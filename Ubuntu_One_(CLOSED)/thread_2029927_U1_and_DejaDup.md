---
title: "U1 and DejaDup"
date: 2012-07-20
forum: Ubuntu One (CLOSED)
---

### Post by candtalan on 2012-07-20
I am a long time user of U1, but only use it occasionally. I like DejaDup. I am trying to understand the implications of dejadup being used to send backup files to U1.

I have previously come to understand that U1 is mirroring a sync folder, which is fine for  convenient syncing and music and stuff. However, if the sync folder contains a file which is accidentally deleted, then the U1 mirror file is also deleted. This is not good for one of my needs for web storage, which is to hold backup data.

Now, with DejaDup being integrated with U1, it looks as if (and I am guessing here) dejadup  uses a method or a technique of storing dejadup backup files in U1 in such a place, or in such a way, that simple mirroring is -not- followed.

Does dejadup create a separate conditional (non mirrored) sync to U1 based on a dejadup 'local folder'? 

Will there be a 'dejadup' folder created in my U1  webstore that I will see?

U1 will still be syncing my local U1 (Home) folder of course, anyway, but this is different to the local dejadup action isn't it, because the deja backup activity would not (?) be creating a local file?

I only want to start relying on U1 with backup files until I am more clear about what happens, so I can avoid data loss.

I would be grateful for comments and any explanations about this.

---

### Post by clifford junior on 2012-07-20
im doing this right now as it is. it seems to me dejadup just does a backup and then incremental backups from that point if you set it to. it doesnt sync as soon as you make changes to the backup folder like sync in u1 or dropbox for example it does it according to your set schedule and uploads in its own format.

i think at some point dejadup will then do a full backup again instead of incremental and keep two versions of backup at all time as long as there is enough space.

ive been uploading 20gb of raw files and its been going for 3 days and still not finished/

---

### Post by candtalan on 2012-07-20
> **clifford junior said:**
> .... and uploads in its own format.


Ok, do you know if the dejadup files just sit up in U1 as a bunch  of files, visible as normal? Or does dejadup create a web store folder? etc

---

### Post by clifford junior on 2012-07-22
after 3 full days of dejadup trying to backup 20gb i got a failed 401 message but not until it had uploaded all 20gb. i then tried to fully restore to see if it was a mistake but that failed also.

ive now just synced the folder as normal instead, and its only taken about 15 hours in comparison.

moral of the story in my case, deja dup does not do a good job and syncing is the better option for reliability.

---

### Post by candtalan on 2012-07-22
I tried backing up my home to my large U1 account, and left it overnight. However I later found it had crashed after 500mb.  I was doing it in ignorance - I do not have enough information about dejadup and U1 integration (as I asked earlier)  to make an informed conclusion about this test. I later limited the files for backup (to 5gb) and left it all day, which on my connection speed was ok for it to complete, which is did successfully.

Points I noted:
during the initial setting up, I nominated a folder name on U1, and I had earlier created  that foldername in my U1 account. However, DejaDup did not use my own folder, but it created its own folder, using my nominated foldername. The folder was created automatically by the dejadup process, and the folder was marked in U1 as 'synchronised' or the like. However I can not, so far anyway, see a folder in my PC to which the U1 deja sync folder is related to.
Also, even though the backup and sending up to U1 was necessarily a long process, I could not see any progress indication, which I would like. 
I would be concerned about exactly what would happen if the PC or the connection turned off during the backup activity.

I think the DejaDup-U1 integration is a really good idea and facility, however, I very much need more information to enable my informed use, and hopefuly my constructive participation in its development.

---

### Post by Dragonbite on 2012-07-24
when DejaDup backs up  to U1, you'll find it looking at your account via a browser, under a 
~/.<computername> folder similar to when you synchronize your ~/Documents directory.

So if my computer is named "fred" it would be visible under "~/.fred"

I would think this means DejaDup creates a hidden folder (Ctrl+H will toggle hiding/showing hidden folders in Nautilus) in your /home directory.

I've given up this kind of backup so I don't have an instance I can look at currently. I'm going by memory.

---

### Post by candtalan on 2012-07-24
> **Dragonbite said:**
> when DejaDup backs up  to U1, you'll find it looking at your account via a browser, under a 
~/.<computername> folder similar to when you synchronize your ~/Documents directory.

So if my computer is named "fred" it would be visible under "~/.fred"

I would think this means DejaDup creates a hidden folder (Ctrl+H will toggle hiding/showing hidden folders in Nautilus) in your /home directory.

I've given up this kind of backup so I don't have an instance I can look at currently. I'm going by memory.

A few days afer the backup event, I see that my U1 webstore contains a folder 
~/deja-dup
Which is the folder name I myself nominated when initiating the dejadup activity. I also chose to set a password, if it makes any difference, and a typical filename in the backup set is for example
duplicity-full.20120721T091053Z.vol101.difftar.gpg
I have looked, but I cannot see any hidden files relating to dejadup integration with U1 in my local machine.
Are there any U1 devs about for more information please?

---

### Post by candtalan on 2012-07-25
I notice that there is a temp folder on (\var I think) named duplicity, so I guess this might be related to backing up direct to U1.
However, after  about an hour of backing up to U1 - and it was going ok because I could see the upload rate using System Monitor - I got a Backup Failed
message with error code 503. Which I gather is server busy. Mmm. I am -not- impressed. This is a backup process! This is the second time I think I have seen this, the first time I pretty well ignored thinking it might be my finger trouble.

---

