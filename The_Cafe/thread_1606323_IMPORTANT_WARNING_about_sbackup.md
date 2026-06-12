---
title: "IMPORTANT WARNING about sbackup"
date: 2010-10-26
forum: The Cafe
---

### Post by Docaltmed on 2010-10-26
I would like to warn the user community about a little-known bug in sbackup, and use it as an opportunity to explore some weaknesses in the open systems model.

First of all, as to the bug. I found out yesterday, to my horror, that sbackup fails without warning or notice when making backups of over 4 GB in size on FAT32 drives. The FAT filesystem cannot handle files larger than 4 GB, and when sbackup puts all the files for backup together, it is frequently larger than 4 GB in size, and thus the backup fails.

Sbackup does not notify you of the failed backup. In addition, if you go to look at the backup -- without actually trying to recover a file -- the directory structure of the backup appears to be perfectly fine. The only way I would have known about this bug is by performing a trial recovery.  

Yes, I should have tested by performing a trial restore, and I do not shirk my responsibility in that regard.

HOWEVER, in all honesty, with a bug as flagrant, and as dangerous, as this, there is no way that sbackup should be in the repositories. At the very least, there should be some notification of this extraordinary bug. However, there is not. As a matter of fact, the bug was initially reported in April of 2008, [AND SUBSEQUENTLY MARKED SOLVED!]("https://answers.launchpad.net/ubuntu/+source/sbackup/+question/30719")

As one of the bug reporters noted:

> OK, so maybe instead of saying, here is an End User product in the mainstream distro that you can use to back up to any media, perhaps someone, somewhere ought to mention that the product will not work with VFAT formatted USB hard drives, i.e. the majority of all of the consumer drives available ? That would at least warn the user in advance not to put his hopes in a backup that is doomed to failure (without even telling him) once the file size exceeds 4Gb.

In my opinion, the product is defective because it leads the user into a false sense of security, so personally, I would still class this as a bug. Why ? Because it involves data loss, and that is considered unacceptable in most other projects.

In addition, if you look at the Ubuntu Documentation [page]("https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite") for this software -- as I did before implementing the system -- once again, there is no mention of this failure.

As a result of this nexus of unfortunate events, I have now lost all of the financial data for my company for 2010, as well as other data, all of which will cost me well over $4,000 in labor costs to recover.

Costs aside, to me this highlights a significant flaw in the model that the Canonical FOSS system employs, in that there is no methodology by which the dichotomy between user relative importance and developer relative importance can be resolved. I've noted this as I've reported other bugs as well. Not that I'm assuming that all my bugs are equally important to everyone else. But as issues get passed around from group to group, responsibility for their remediation becomes first dissipated and then, eventually, evaporates entirely.

Clearly, the developer and documentation team saw this bug as being of no importance. I, and other users, regard it as mission critical. 

**I mean, in what other marketplace would a piece of software that fails so absolutely and so brilliantly be tolerated, much less given the high marks that sbackup received?**

I don't have an answer. Software development is not my field. Nonetheless, I am the user that Canonical is looking for, and users like me could advance Ubuntu's penetration significantly.

But I can guarantee that it won't happen while systemic errors like this remain in both the development process and in key applications.

---

### Post by LowSky on 2010-10-26
First I'm sorry you lost your Data. I understand that can make anyone angry if they didn't know it was occurring because of a flaw.

This isn't Ubuntu's fault. Many different companies have marketplaces for the downloading and use of software, From Apple to Sony to Google to Canonical. Most of it is safe to use but some may have issue that are not accounted for and some may not work at all. The companies that run these market places can be tightfisted or loose with control and in this case having a loose control has cost you some money.

This issue is one most computer savvy people wouldn't notice. FAT can't write over 4GB of data and its been common knowledge for a very long time. Also most Linux users shy away from FAT and use EXT, JFS, or XFS for large data backups. Most people store backups on another internal hard drive or on a server, none of which would be formatted to FAT, unless it needed Windows access. And even then NTFS would be a better choice.

Remember that Ubuntu documentation is done by the community. They may overlook something and sadly its an end user who pays the price. Community members are not paid for their work and just like Wikipedia the accuracy can be questionable. Things are checked and double checked, but sometimes issues don't occur when one doesn't test for them. I know that's a lousy answer.

When it comes to using any software for work related projects always test and retest before implementing.

---

### Post by Xianath on 2010-10-26
@Docaltmed: Sorry about the loss of data. You've learned in the hardest way a very important lesson about FOSS: no matter what they tell you, it is NOT user-driven! I encourage you to read Eric Raymond's "The Cathedral and the Bazaar" essay. You will find some eye-opening truths about FOSS, such as:

1) Most FOSS software is driven by a programmer's need
2) Users are not consumers, they are testers
3) It's free, don't use it if you don't like it

I guess it's pointless to say at this point that $4k was a lot less than you would have had to invest in a commercial solution even with the additional data loss insurance overhead. To (mis)quote Rockafeller, no one is rich enough to buy cheap.

---

### Post by HermanAB on 2010-10-26
Nice rant, but who would be so dumb to use FAT for anything important?

---

### Post by oldfred on 2010-10-26
I made the same mistake 4 years ago. Fortunately I never needed any of the backups.:)

My excuse then was I used a FAT partition to share data with windows as the NTFS driver 4 years ago was not yet considered totally reliable and that was where my extra space was to put backup data. I did notice every backup was 4GB which seemed strange.

I now am not a fan of full backups. But I have 3 drives with, several system partitions, old Ubuntu, current Ubuntu & future Ubuntu on different drives. Too many versions of /home (only about 1gb without my data) floating around with all my data in separate data partitions. I back up /home and move into /home copies of any totally customized setting from /etc, a current list of installed apps, and a copy of bootinfo script results.txt, and back up the data I cannot recreate. But assume I will do a full reinstall if (when) a drive fails.

---

### Post by AlphaMack on 2010-10-26
> **HermanAB said:**
> Nice rant, but who would be so dumb to use FAT for anything important?

Tell that to flash and external drive manufacturers.

---

### Post by CharlesA on 2010-10-26
> **AlphaMack said:**
> Tell that to flash and external drive manufacturers.

Flash drives, yes. External drives, no. All the ones I've used have used NTFS by default.

---

### Post by cariboo on 2010-10-26
I take the other point of view, as a computer professional, it's your job to test any solution before implementing it. Especially with mission critical data, the least you should do is make a couple of test backups and then restore them to ensure that everything is working properly.

This isn't the fault of any software, be it paid or open source, you just have to man up and take the blame for your mistake. These lessons can be hard and expensive to learn, but most of us have done something stupid at one time in our career, and anyone that says it can never happen to them is living in never-never land.

---

### Post by Troublegum on 2010-10-26
This bug has been fixed a long time ago. Unfortunately, Ubuntu Lucid did ship an old version of sbackup.

---

### Post by matthewbpt on 2010-10-26
From Software Centre entry for sbackup

> Canonical does not provide updates for Simple Backup Restore. Some updates may be provided by the Ubuntu community.

IE it is part of the ***community maintained*** repository. Also [https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite](https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite) is part of the ***community maintained*** wiki. Canonical is not responsible for them and I think that more research needs to be done before one trusts a program with backups worth 4000 Dollars. Don't blame Canonical and Open Source for your mistakes... Sometimes you need to take responsibility for your own actions.

This is the official Ubuntu Documentation regarding backups [https://help.ubuntu.com/10.04/serverguide/C/backups.html](https://help.ubuntu.com/10.04/serverguide/C/backups.html)

---

### Post by K.Mandla on 2010-10-26
> **cariboo907 said:**
> This isn't the fault of any software, be it paid or open source, you just have to man up and take the blame for your mistake.
I would have to +1 this. You forced the software into a situation it can't account (or compensate) for, and as a result ... data loss. I can sympathize because I've lost data in the past too, but it sounds like something you should have researched beforehand. Sorry. :(

---

### Post by Docaltmed on 2010-10-26
> **Docaltmed said:**
>   

Yes, I should have tested by performing a trial restore, and I do not shirk my responsibility in that regard.



Man, some of you guys gotta read the posts. At no point do I shirk my responsibility. I have been my own boss for over 25 years, and I didn't get to where I am by trying to blame my employees for my mistakes. Everything that happens in this building is my responsibility, even if I wasn't there when it happened.

I just wish that developers would shoulder the same level of responsibility that I have. Knowing that many USB drives are FAT, and knowing that many users will be employing USB FAT-formatted drives to back up their computers, it was utterly irresponsible of them to (a) make absolutely no note of this issue in their documentation, and (b) to mark the problem as solved in SourceForge, when it obviously is not.

I'm not even requesting a fix to the software. Only some notification to the user that this failure exists.

My larger point is that FOSS is ultimately dependent on a bargain between developers and users. The developers get to write the code that they want to, and in return for using it, we users test it, provide feedback, implement workarounds and eventually solutions.

It's generally a good bargain. Both parts of the equation are getting value for their labor. But only if both sides hold up their end of things.

If we as users fail to test and provide feedback, it is our fault that the software that emerges is not to our liking.

And if programmers write only to please themselves, it's not software development. It's just digging a hole in order to fill it up again. 

And once producers confuse self-pleasure with fulfilling the needs of the clients, a painful course correction cannot be far ahead.

---

### Post by bedhead75 on 2010-10-26
Maybe the Ubuntu Software Center would benefit if a way of leaving user comments and ratings for specific applications was implemented...as it exists in the Android Marketplace or Apple App store for smartphone systems.  It would make Ubuntu even more user friendly and improve overall user experience for newbies who have yet to familiarize themselves with open source software.

---

### Post by toupeiro on 2010-10-26
> **Docaltmed said:**
> Man, some of you guys gotta read the posts. At no point do I shirk my responsibility. I have been my own boss for over 25 years, and I didn't get to where I am by trying to blame my employees for my mistakes. Everything that happens in this building is my responsibility, even if I wasn't there when it happened.

I just wish that developers would shoulder the same level of responsibility that I have. Knowing that many USB drives are FAT, and knowing that many users will be employing USB FAT-formatted drives to back up their computers, it was utterly irresponsible of them to (a) make absolutely no note of this issue in their documentation, and (b) to mark the problem as solved in SourceForge, when it obviously is not.

I'm not even requesting a fix to the software. Only some notification to the user that this failure exists.

My larger point is that FOSS is ultimately dependent on a bargain between developers and users. The developers get to write the code that they want to, and in return for using it, we users test it, provide feedback, implement workarounds and eventually solutions.

It's generally a good bargain. Both parts of the equation are getting value for their labor. But only if both sides hold up their end of things.

If we as users fail to test and provide feedback, it is our fault that the software that emerges is not to our liking.

And if programmers write only to please themselves, it's not software development. It's just digging a hole in order to fill it up again. 

And once producers confuse self-pleasure with fulfilling the needs of the clients, a painful course correction cannot be far ahead.

Of the various backup scripts I've written, depending on the data, I will exclude specific filesystsms as destination targets.

you can get your filesystems by just issuing mount then use sed and awk, or cut and awk to get the filesystem for the mount point.  Then, just write a simple if/then conditional statement.

I know, you're not trying to skirt your ownership in the issue, but I am offering a suggestion you can take and apply to almost any method of backup that can be automated (generally through cron). and you can prevent things like this by writing the logic in yourself, as opposed to submit a feature request for a developer to try to guess which filesystems you do or do not consider safe destination points.

---

### Post by toupeiro on 2010-10-26
> **bedhead75 said:**
> Maybe the Ubuntu Software Center would benefit if a way of leaving user comments and ratings for specific applications was implemented...as it exists in the Android Marketplace or Apple App store for smartphone systems.  It would make Ubuntu even more user friendly and improve overall user experience for newbies who have yet to familiarize themselves with open source software.

I've actually thought to myself that this would be a great feature of the software center.  In fact, so much better than a paid software category with codecs in it... :)

---

### Post by sisco311 on 2010-10-26
> **toupeiro said:**
> I've actually thought to myself that this would be a great feature of the software center.  In fact, so much better than a paid software category with codecs in it... :)

Indeed, it will be a great feature, but it's much harder to implement it...

[uwiki]SoftwareCenter[/uwiki]

---

### Post by toupeiro on 2010-10-26
> **sisco311 said:**
> Indeed, it will be a great feature, but it's much harder to implement it...

[uwiki]SoftwareCenter[/uwiki]

I'm not trying to downplay it's difficulty, just highlight it's value-add.

---

### Post by sisco311 on 2010-10-26
> **toupeiro said:**
> I'm not trying to downplay it's difficulty, just highlight it's value-add.

and I just wanted to point out that they are working on the issue.

---

### Post by marshmallow1304 on 2010-10-26
> **Docaltmed said:**
> Knowing that many USB drives are FAT, and knowing that many users will be employing USB FAT-formatted drives to back up their computers, it was utterly irresponsible of them to (a) make absolutely no note of this issue in their documentation, and (b) to mark the problem as solved in SourceForge, when it obviously is not.

As far as I can tell from reading the changelog, it **was** solved.  Someone made a fork called nssbackup to resolve that and some other issues.  Apparently most of the developers started focusing on nssbackup until it was decided that it would be merged back in at version 11.0.  The version in Lucid is 10.5.  There's the problem.


Also, I know it's your choice to use FAT32, but it's been around for 16 years and has been surpassed greatly by many filesystems, both open and proprietary.

---

### Post by ukripper on 2010-10-27
Problem - Not paid sufficient attention in making sure that your data is backed up properly.
Solution - Next time test your backups, if necessary create additional backups.

---

### Post by patrickvdbemt on 2010-11-04
People may (and they do !) ask why using FAT for backup repositories. Well, I really do not know.
But what I know for sure is that after reading through these postings I checked my system.
I am taking an sbackup on a NAS attached to my network. And just checked the error logs, I get messages telling "....gz exceeds maximum file size".
ùµ##@|@||   apparently the disc in the NAS can be formatted by the NAS baked system, formatting the disk as you guess  FAT !!  archh by buying a simple NAS all of a sudden I am again suffering from this microsoft problem. :(
What are the next steps I should take ??:confused:
Yeah yeah, it might be easy to say "build yourself a simple server with Linux and stick some discs in". I can do but 1/ I need a station 2/ the station will be powered-on all the time and 3/ cost me maintenance and money.
And I thought that just sticking a NAS on my network would do it for me !! :twisted:

---

### Post by CharlesA on 2010-11-04
Most of the NAS boxes I've seen can handle mulitiple file systems. It would be stupid to lock a storage device into using only FAT32.

---

### Post by coutts99 on 2010-11-04
> **Docaltmed said:**
> The FAT filesystem cannot handle files larger than 4 GB

This has been known for years.

Classic case of PEBKAC here

---

