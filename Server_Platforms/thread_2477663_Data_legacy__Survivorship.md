---
title: "Data legacy / Survivorship"
date: 2022-08-02
forum: Server Platforms
---

### Post by aljames2 on 2022-08-02
So my profession demands that I think about the unthinkable and help folks plan. The planner in me, has me thinking about preserving our data legacy...

I am the "computer person" as my wife would say it, in the home, implying that her technology understanding goes about as far as pressing the "on" button to start up a windows or Ubuntu desktop.  And, she can open a folder by clicking on one of them icons to view, save, edit, and open stuff like documents, pictures, downloads, etc.

There is no way anyone in my household could step into my shoes and access the backup server disks without the knowledge that I have.  My backup drives do not mount on startup.  Plus they are encrypted.  Then there is ssh'ing into the backup server, and finding the ssh keys which are in a KeePass vault with a long long long password.  No chance, the access to the data would be gone, and the computers would likely be useless to her, excepts for the 1 windows box, and the 1 Ubuntu desktop which is our daily driver that she uses, which runs in a VM on a KVM host.  I don't keep automatic updates turned on anything, perhaps I should.  Or at least set a script to run updates on a cron schedule, but I haven't done this either because I usually like to see what is being updated first.

Perhaps it's as simple as creating a portable backup USB drive (or several) that could plug into any computer with free & open access, and where this drive could be kept in our bank lockbox?  Or, hide it somewhere at home or offsite would be better.  Right now, if she wants to see some old photos, or early years videos of our kid growing up, or prior years tax returns, I have to go through my ritual of unlocking a separate encrypted drive making it viewable on our Ubuntu desktop VM.  Right now I'm looking at that drive and it is a complete brick to her.

I'm sure there are many better ways & ideas on how to pathway this data to survivors, which is what I am looking for  O:) 

Thanks as always!

---

### Post by LHammonds on 2022-08-03
#1 Document your backup procedure.
#2 Document your restore procedure.

The documentation needs to be written in such a way that someone without knowledge of the system could follow it and it needs to be less than a page log.

If your documentation cannot do that, you might want to look into how you can modify your process to still work but be less manual labor.

Multiple copies of the data and encryption is a good thing.  Having a centralized location for all the data is a good 1st step even if that means some devices are just synchronizing what they have on their machine (e.g. pushing "My Documents" or "/home") to the central storage.  Then your backup / restore automation and documentation would just be dealing with one location.

Once you have your normal "usage" of the system documented, it might be a good idea to document how someone would create the system, perform upgrades, etc.  Because if you are not around anymore, the backup/restore system will eventually go into disrepair without maintenance / upgrades.  Your family might have no interest in that level but make sure someone (such as them hiring an IT contractor) can follow that documentation and do what is necessary.  Maybe even make an advertisement for the skills necessary to perform such actions as part of the documentation so they will be able to find the right talent when needed.

LHammonds

---

### Post by aljames2 on 2022-08-04
Good ideas.  I have been pretty good at documenting (for me) along the way, but I should do better at simplifying & organizing how things work in case there is a need in the future.  Thanks LHammonds!

---

### Post by LHammonds on 2022-08-04
Oh, and just like with backups and restores, be sure to test your documentation to see if the uninitiated can even follow the documentation without aid from you.  If aid is needed, figure out how to re-word that section so it won't be needed next time (which might be simple links to external articles or to future-proof links, do something like this: [Search: Getting Started with VIM]("https://www.google.com/search?q=getting+started+with+vim+the+basics"))

---

### Post by mIk3_08 on 2022-08-05
> **LHammonds said:**
> #1 Document your backup procedure.
#2 Document your restore procedure.

The documentation needs to be written in such a way that someone without knowledge of the system could follow it and it needs to be less than a page log.

If your documentation cannot do that, you might want to look into how you can modify your process to still work but be less manual labor.

Multiple copies of the data and encryption is a good thing.  Having a centralized location for all the data is a good 1st step even if that means some devices are just synchronizing what they have on their machine (e.g. pushing "My Documents" or "/home") to the central storage.  Then your backup / restore automation and documentation would just be dealing with one location.

Once you have your normal "usage" of the system documented, it might be a good idea to document how someone would create the system, perform upgrades, etc.  Because if you are not around anymore, the backup/restore system will eventually go into disrepair without maintenance / upgrades.  Your family might have no interest in that level but make sure someone (such as them hiring an IT contractor) can follow that documentation and do what is necessary.  Maybe even make an advertisement for the skills necessary to perform such actions as part of the documentation so they will be able to find the right talent when needed.

LHammonds
This documentation is very important, it will be printed in a hard copy and it will be posted in the white board so it will not be forgotten. Hard copy is very different from the soft copy. Only those very important documents are to be printed and the others are second priorities can be in a soft copy. Maybe I will be using this some day. Thanks for this advise LHammonds. Regards and cheers

---

### Post by TheFu on 2022-08-05
Your household probably enjoys what you do for them, but isn't really interested in taking over. They will learn to live without it, if there is any maintenance needed.

The best you can hope to achieve is to find a trusted friend/family member who has an interest in migrating what you've done into something they can support.  That is unlikely, however.  This means if you are very lucky, they will pull the data out onto 1 external drive/NAS and make that available to your household, while having a separate 1 disk for backups of the most important things - likely using simple rsync to mirror the source data every week, if that often.

If your partner doesn't have any interest in learning these things, I can see her giving away all the equipment, without wiping any of it.

Whatever you leave behind, needs to be something they can manage.  That's the rule.  For most households, they would do well to have 1 backup USB drive and use that.  Anything more is just asking too much.

I'm saying this after discussing at length all the data we each have and what should be done after death.  When Mom died, I'd been managing her system remotely for a few years. She had local backups (back-in-time) and I was pulling the most important information remotely each week.  Even getting her to leave the computer on overnight for that remote backup was a fight ... that I lost.  Mom was smart, just not a computer nerd.  She'd run a huge household on very little money and had 2 college degrees - biology and business accounting. She'd been using computers since the mid--1980s.  Just so you get a feel for what can reasonably be expected from normal, intelligent, people.

I was never able to get her to use a password manager, though I was successful in getting 4 of my siblings to use them.  
Mom did do passwords smart.  She wrote down half of the complex passwords in a notebook near the computer, but the other have was only in her head.  She'd merge those for the complete credentials.  Smart, simple, effective.  I use something similar for emergency passwords when on travel and with some LUKS encrypted storage here that I cannot be certain works with yubikey challenge/response methods.

Remember, someone close has just died. They can't be expected to handle complex stuff.

---

### Post by aljames2 on 2022-08-05
Very helpful info from all of you.  Much appreciated!

Perhaps there is hope in showing my daughter some things, although she doesn't live in the household anymore.  She is a graphic designer including some web design stuff.  Funny, I was just showing her a few weeks ago how I access the backup server and run backups.  She thought it all looked pretty cool with all the CLI stuff.  We even pulled off a video montage of her from the early teen years that she got a kick out of.  What I realized as she watched what I was doing, was how disorganized by notes are, which was somewhat embarrassing and eye opening.  I knew where things were but the message resonated in my head that I need to get my crap together better.  Organizing is what I will tackle first.  Then I'll test my install, backup, & restore notes in a VM.  Fortunately, my backups are not entire system backups and can be used to restore on any fresh installation in a VM or on bare metal.

Thanks again!

---

### Post by TheFu on 2022-08-06
Even for technical people, following complex setups by someone else, unless it is their day job, just isn't gonna happen.  Now, if your daughter has a need in her profession and chooses to implement it in the same way you have, there would be value in that as a solution.  You'll want to be lead by her probably.

But be careful with some ideas, like calling something a "backup disk".  I've seen people forget that "backup" means having at least 3 copies of data.  They create a file, perhaps for days, then dutifully copy  it to the "backup" disk - all smiles.  Then they immediately delete it from their main system, so there's only 1 copy remaining on the "backup disk."  We forget to restate that backups need a 3-2-1 method.
* 3 copies of the data,
* 2 physical locations for storage (I use 500 miles apart for this part),
* 1 copy is local for quick restores and as the staging point for the remote data push.

I usually add in that any data leaving my physical control be encrypted and offer an easier 3-2-1 method for people who don't have a place 500 miles away that can be trusted.  Buy 2 USB 3.1+ HDDs of the size needed to hold all the backups for everything you need.  8TB should easily store all the critical house data - easily.  Forget all the video stuff, just keep the financial, insurance, wedding and baby stuff.  Every other week, mount one of those 8TB drives as your daily backup. Use it all week. Would be good if both used LUKS encryption.  Backup to 1 drive, daily. On Friday (or Monday?), take 1 of the drives into work and place it into a locked drawer there (never to be touched until it is swapped the following week. Use the other drive (also LUKS encrypted) for the next week of backups.  Rotate the USB drive weekly or bi-weekly.  

It isn't 500 miles, but at least if the house burns to the ground, total data loss didn't happen.

Not too hard to understand for most people. Steps can be clearly written along with some stick pictures so everyone can understand.  If you like, you could insert backup storage that never moves in the home-office environment to get the versioning, then use a simple rsync of the backup areas to the external USB storage.  I have about 20 systems here. All their most important backups fit onto a single 2TB USB3 disk.  That disk is getting a big old (so is the computer it connects to), so I'm moving to a new 8TB drive on a different system for daily, versioned, rdiff-backup storage.  I rsync that storage to a family member's system 3 states away.  He does the same.  Linux containers are great for that with access to a local drive.  We pre-seeded the data locally before setting all this up.

Of course, only you and your daughter can decide how far to take this stuff.  OTOH, adding LUKS encryption (or veracrypt) later won't be the end of the world. That's part of the freedom that having 3+ copies of the data provides.

I need to also point out that I use simple delayed mirroring for all nice-to-have huge data files (audio and videos).  That is performed using rsync. Really critical data gets manually created 10% par2 files to fight bitrot. I suppose if I'd used zfs, that wouldn't be needed.  Perhaps next time.  Back when I used optical media for some backups, the par2 files were more important and have protected against data corruption more than a few times.  This is for write-once data that seldom gets accessed - perhaps once every decade. It is quick to see if those files are corrupted when copying them to active storage.  Validating them all, say monthly, would take some CPU and effort.  But certain data is worth that effort.

---

