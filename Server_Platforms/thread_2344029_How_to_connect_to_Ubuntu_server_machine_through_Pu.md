---
title: "How to connect to Ubuntu server machine through Putty using script file from Windows"
date: 2016-11-21
forum: Server Platforms
---

### Post by agarwaldvk on 2016-11-21
Hi


This is in preparation for running a backup job using my Windows backup application (Genie Backup Manager Pro 9) from my Windows machine to create 'n' differential backups and 'm' backup sets of a share on Ubuntu server machine. Both the share that is being backed up and the location where the backup is being made are separate internal/external physical hard disk drives directly connected to the Ubuntu server machine.

Both these share locations would be mapped as network drives on the Windows machine.

The backup job is be defined in the aforementioned application and it is intended for this job to be called from a batch file. All the batch job does is simply copy all the folders and files from a certain location on the server to another location on the same server on a different internal or external physical HDD - nothing clever here.

I think I should be able to run this batch file from within my Windows machine - that isn't the issue as such - but the issue is how do I login to the server as an administrator without having to enter my password each time. My cursory understanding is that this can be realized using PuTTy/Plink combination using Public/Private Key Authentication from specific PC's (since I believe that this key combination is PC specific) but I don't know how it all works.

I know that there are some applications available in Ubuntu for backups but my preference is to use this Windows based application that I have and am familiar with - I had been using it previously.

I do currently connect to my server through SSH (using PuTTy). 


Best regards


Deepak

---

### Post by TheFu on 2016-11-22
The problem with using Windows to backup Linux is that critical information is lost - user, group, permissions, and ACLs aren't captured.  Plus .... just .... eeeew, Windows. ;)  Samba remote sharing uses CIFS, which drops those things.

There are at least 50 different backup tools for Linux. We aren't limited to was is preinstalled in the GUI. Ubuntu has a page on them. I use rdiff-backup, for a number of reasons.

I don't understand why you need putty for backups of Linux from Windows. Please explain, in detail, what you think this does?

Haven't used putty in years, but I vaguely remember it had a way to generate the public/private key pairs, then you can manually copy the public key to the Linux system and put it into the correct place, set the file permissions correctly to be able to ssh in without password prompts.  Bet there are step-by-step videos on youtube for this. Found a bunch: [https://www.youtube.com/watch?v=2nkAQ9M6ZF8](https://www.youtube.com/watch?v=2nkAQ9M6ZF8)

On Linux, I'm positive how to accomplish key-based ssh connections:
1) ssh-keygen
2) ssh-copy-id userid@remote-system
Be happy.
ssh-copy-id handles pushing the public key over, puts it into the correct place, ensures the file and directory permissions are correct. No muss, no fuss. From Windows, you'd have to manually handle those things. People often get them wrong and ssh is picky about the permissions of the files it needs for authentication, as it should be.

---

### Post by agarwaldvk on 2016-11-23
Hi TheFu


Thanks for your response and sorry for the delay in replying. I was actually in the middle of addressing another issue with my Ubuntu setup with the help and support from others on that one!

Anyhow! I didn't know that backing up from Windows would loose those pieces of information like permissions of files and folders  but nevertheless! there are a lot of things that I don't know!

Fair request for a better explanation - I initially had thought of detailing in the post what my full intent was but thought the better of it. Here are the details :-

I have a few more PC's in the house used by other members of the family. Further, this Ubuntu machine that is being used as a server is not a server grade machine, its a consumer grade machine which I thought would suffice  for my home purposes. Hence, I do not intend to keep in running all day everyday. Previously I had a FreeNAS machine serving as a server and I used to run a shutdown script from my main Windows PC which would seek a confirmation to run the backup job. Once confirmed, it would run the backup job through another script file and backup the stuff from the server using networked mapped drives to an external HDD connected to me main windows PC. I had the backup job defined in the Genie Backup Pro 9 application and it worked ok for me. So I thought I will continue with the same process.

I don't mind using linux based backup facility/applications. I would like to keep 2 full backup sets from the past 2 weeks and 1 differential backup since the last full backup at any point in time. I am sure this is relatively easily realizable using any of the available linux based tools - I don't know any but you can recommend me a few to look at. I would like be able to use one that supports open file backup because someone could be working on a file when the backup process is running. 

So, now you know why I was trying to initiate and run a backup job from my main windows PC.


[SIZE=3]Edit : I have been doing some googling on the available tools and I couldn't find (this is of course based on cursory research only) any that does differential backups instead of incremental. Aren't there any?

Edit 2 : Sorry I do see now that apparently Amamda can do it but I don't how - I would like to know!

[/SIZE]


Let me know what you recommended and I will definitely have a look at it.


Best regards


Deepak

---

### Post by TheFu on 2016-11-24
I have daily, automatic, backups for my systems (about 15 now, been cutting back).  The most recent backup appears as a mirror with older backups as reverse differentials.   rdiff-backup. *My signature* links might be helpful.  Incremental backups are so, so, so ... 1980s.  For 1.10x the storage of the source, I get 30 days of backups.  For 1.20x the original storage, I get 60-120 days of backups.  Clearly, the churn matters.  I use rdiff-backup for everything except:
* the OS - that's what ISOs are for.
* media files - these don't change very often and are too large for diffs to be useful. rsync instead. To fight corrupt bits, use ZFS or par2 files.

rdiff-backup is FAST too.  Usually just a few minutes after the 1st mirror is created. That first mirror is basically an rsync and takes that amount of time.  If doing remote backups, something like duplicity or zbackup which include encryption would be important.

I don't trust Windows backup tools.  A few years ago, saw tests of the main 10 tools and none of them actually worked - worked was defined as putting things back to a new disk that was identical to the disk which was backed up.  Never had that issue with Linux.  If I want an identical backup, there are 20 different tools that work and I don't have to stoop to dd/image-based backups to achieve it.

BTW, please don't use funny fonts here.

---

### Post by mastablasta on 2016-11-24
Genie Backup Manager Pro 9 says "Works on everything" - clearly it doesnt' as it doesn't seem to support sFTP. if it did then it owul dbe trivial to setup what you want (install openssh and setup keys).

if you like GUi have you looked at Areca? there are also a few others that are good an dwork on Linux and Windows. but most would compress the files. areca is Quite good for static ones, plus you can easilly Access the backed up versions with normal file browser  (or should i say FTP browser - Filezilla, winscp...)

---

### Post by agarwaldvk on 2016-11-24
Hi

TheFu - I will come back to your suggestions a trifle later - needs more considered response! I am not at your level of understanding!

mastablasta - No, I had not heard of Areca until you mentioned it and yes, I did have a look at it and seem to like it too - doesn't seem to be much different to Genie Backup Pro 9. A couple of questions though :-
Does Areca have support for open files?
Does Areca need to be installed and run on the Ubuntu machine?
Can Areca be installed on Ubuntu machine and run from Windows machine?
Can Areca be installed and run on the Windows machine?


Even with GBM, why would I need sFTP - am I not just copying the entire folder structure from one physical HDD to another on the server?

In fact, I do currently have ssh and puTTy installed and confgured and I do access my server usng puTTy. I am trying to set up the public/private key sets to be to connect non interactively through script file without password - hasn't happened yet. If I am able to set that up then I should be able to run it a script file run from my Windows PC, should I not? This script file is a batch file residing on my Windows PC (or does that need to reside on the server?). Why I want to have this script run from my Windows PC is another question - I will explain in my next post as I want to at least provide you with a response to you. But the bigger question is that based on what I understood from TheFu's response that using Windows based application like GBM to do the backup, I will lose all file and folder permissions, users, groups etc - and that is not acceptable because then the whole user based access to user specific folders will be lost defeating the whole purpose of this server setup in the context of data files. In that event, I wouldn't mind Areca (or anything else for that matter which can be set up a scheduled backup process giving the option to create 2 full backup sets and 1 differential backup - or anything better than this!)


I believe it can create backup sets like I would like 2 full backup sets from the past 2 weeks and I differential from the latest full backup, so that is OK. The other thing is that it doesn't seem to have it own scheduler and needs to run as a cron job just as a scheduled task in Windows, yeah!


Best regards


Deepak

---

### Post by TheFu on 2016-11-24
On Unix systems, files can always be read, if there are permissions to read the files. A locked file cannot be modified by other processes, but can be read by any with permissions. That means backups don't need anything special to include a file, even if it is open by other processes.  OTOH, if the file is being written during the backup processing, there could be corrupt backups **only for that file**.  The way around this is to use snapshots to make a non-changing version of the file system and backup THAT point in time. There are other ways to accomplish backups - mainly for DBs that run all the time.

---

### Post by agarwaldvk on 2016-11-25
Hi


That is good. Now I have been doing a fair bit of reading and I think Bacula looks like a decent tool to use. Please advise if this meets your recommendation.

From what I have so far seen, it appears the backup jobs can be set up and scheduled using webmin (I have it installed already). If I were to try and hopefully successfully install and configure Bacula, then do you all think that I can create a scheduled backup system to realize the following backups :-

1. Create a full backup on day 1 - say on Sunday (week1)
2. Create a differential backup every day from Monday through to Saturday (from the full backup created on Sunday). This would mean that the differential backups created from Monday through to Friday would be redundant following the creation of the differential backup on Saturday - these may be retained as space should not be an issue
3. Create a full backup on Sunday (week 2) - retaining the full backup of week 1 but deleting all the differential backups created between Monday and Saturday of week 1
4. Create a differential backup every day from Monday through to Saturday (from the full backup created on Sunday - week 2). Again, this would mean that the differential backups created from Monday through to Friday would be redundant following the creation of the differential backup on Saturday
5. Create a full backup on Sunday (week 3) - retaining the full backup of week 2 but deleting all the differential backups created between Monday and Saturday of week 2 and also the full backup from week 1

Repeat on an on-going basis.


Best regards


Deepak

---

### Post by TheFu on 2016-11-26
Bacula is a backup tool like they had in the 1970s.  Weekly fulls, daily incrementals. Haven't used that method ...er ... ever ... outside an enterprise.  Bacula is non-trivial to configure.

I much prefer the reverse differential method. The current backup is a mirror and older backups are compressed, diffs, off each other. It makes for VERY FAST backups. 1 full, once, not weekly. Most of the time, we need to restore from the most recent backup, but somethings it is nice to look at 30, 60, 90, 120 days ago, if something bad happened or file corruption of the source happened and we didn't catch it immediately.  Plus if we are hacked (or the files are encrypted by an attacker), it is nice to have a backup method that has 30-120 versions and where the backup storage isn't mounted or even available to the machine with the issue.

Not a believer in webmin either. Gets in the way of my devops automation.

---

### Post by mastablasta on 2016-11-28
Avoid webmin.

> **agarwaldvk said:**
> 
mastablasta - No, I had not heard of Areca until you mentioned it and yes, I did have a look at it and seem to like it too - doesn't seem to be much different to Genie Backup Pro 9. A couple of questions though :-
Does Areca have support for open files?
Does Areca need to be installed and run on the Ubuntu machine?
Can Areca be installed on Ubuntu machine and run from Windows machine?
Can Areca be installed and run on the Windows machine?

Even with GBM, why would I need sFTP - am I not just copying the entire folder structure from one physical HDD to another on the server?


**Does Areca have support for open files?** - do you mean files you are working on being backed up? e.g. open excel file, Outlook mail file?
 **Does Areca need to be installed and run on the Ubuntu machine?** - it's a push program so you need "install" it on client side. do you want a pull option where server pulls files from clients?
 **Can Areca be installed on Ubuntu machine and run from Windows machine?** - again are you after push or pull? 
 **Can Areca be installed and run on the Windows machine?** Areca can be installed or uncompressed (portable) on windows PC.

If you want a pull option look at **urbackup** 

otherwise here is a nice list: [SIZE=2]https://en.wikipedia.org/wiki/List_of_backup_software
[/SIZE]
there are a few others out there, not sure if they have Linux versions and GUI. anyway if all oyur PC are Windows then you need osmethign that works on Windows (assuming you are pushing the updates to server).

**Even with GBM, why would I need sFTP - am I not just copying the entire folder structure from one physical HDD to another on the server?** - depends where clients are and how they are accesing the server. in my case we are backing up home PC's (FTP would be enough) and my family PCs which are in another building. so they send it all over sFTP, which is hopefully a secure transfer.


also follow TheFu's advice.

---

### Post by agarwaldvk on 2016-11-28
Hi mastablasta


Thanks for your response. Greatly appreciated. Here are some of the queries/clarifications. Hopefully, this might help.

> 
Does Areca have support for open files? - do you mean files you are working on being backed up? e.g. open excel file, Outlook mail file?


Yes, that is what I meant. In my situation however, its not outlook that I am looking at, its going to be more like MS Word files, MS Excel file etc. This is with reference to my home network scenario - so essentially mail services is not thatI am concerned about.


> 
Does Areca need to be installed and run on the Ubuntu machine? - it's a push program so you need "install" it on client side. do you want a pull option where server pulls files from clients?
Can Areca be installed on Ubuntu machine and run from Windows machine? - again are you after push or pull? 
Can Areca be installed and run on the Windows machine? Areca can be installed or uncompressed (portable) on windows PC.


Looks like it can be installed on Windows machine. If that is the case, once a backup job has been defined within the application, can the same be then scheduled to run (say at 3.00 am everyday) from my main Windows machine to realize the following :- 

1. Run a full backup on day 1 (Sunday of week 1)
2. Run a differential backup everyday between Monday and Friday (I do not like the idea of incremental backups hence I insist on differential - I know each have their individual merits)

Hence, at the end of Saturday of week 1, I would end up with 1 full backup and 6 differential backup.

Repeat the process in week 2 like so :-
1. Run a full backup on day 1 (Sunday of week 2)
2. Delete all the 6 differential backups from week 1
2. Run a differential backup everyday between Monday and Friday of week 2

Hence, at the end of Saturday of week 2, I would end up with 2 full backups (1 each from week 1 and 2) and 6 differential backups from week 2).

Week 3
1. Run a full backup on day 1 (Sunday of week 3)
2. Delete the full backup from week 1 and all the 6 differential backups from week 2
2. Run a differential backup everyday between Monday and Friday of week 3

Hence, at the end of Saturday of week 3, I would end up with 2 full backups (1 each from week 2 and 3) and 6 differential backups from week 3).

I would like to keep 2 backup sets


I am not so sure whether you would call this a 'push' or 'pull' - so this is what I would be doing - all the files to be backed up reside on a physical drive within the server itself. Also, the backup is also done on a separate physical drive, again, within the server. I know that this is not idea but, for my home network purposes this is perfectly acceptable.

I don't really mind where the software is installed. From what I just saw on Areca's web page, I believe that it can be made to retain the files' and folders' user, group, permissions etc. properties - which I would need to retain given not all files are visible and/or accessible to all users of the system.

Whilst, it doesn't seem to have its own scheduler per se, it appears that the 'Backup Strategy' pretty much covers it - do you think I might be able to set it up to realize what my target objective are - as detailed above?


Also, I am looking at Urbackup and from what I have so far, I like it too! Not sure, where it needs to installed and run from and it appears that it would be able to do what I need.


Thanks again. I will spend a bit more time reading up on Urbackup and Areca and between the two , may be one of these can do what I am looking to do!

Edit : Can you give me some pointers to where can I see some examples of a cron job scripts to schedule a backup job to realize what I am after using either Areca or UrBackup?

Edit 2:-
Did a fair bit of reading on both Areca and UrBackup. Couldn't figure out how do we actually create a scheduled job in UrBackup and run it. On Areca, it appears that to realize what I am wanting to do, it would need 2 batch/script files - one for the weekly (full backup) and one for daily (differential) backup. Do we then need another job to delete the old backup files?


Edit 3 :-
Just installed Areca on my Windows PC first as a test. These are the 3 files that it generated. From what the documentation said, I believe that I can use the Windows Scheduler and use these files to automate the backup process - I tried to create the "backup shortcut" & the "backup strategy" from their graphical interface. I don't quite get the code. Could someone please explain the generated code to me?

Code in backup_1679171114.bat file
@REM Backup script generated by Areca v7.5 on Nov 29, 2016 8:24 PM
@chcp 1252
@REM Differential backup
@REM Target Group : "workspace"
@REM Target : "Test"
@"D:/Program Files (x86)/Areca/areca_cl.exe" backup -d -c -wdir "C:\Users\AGARWA~1\AppData\Local\Temp\tmp-agarwaldvk" -config "C:/Users/agarwaldvk/.areca/workspace/1679171114.bcfg"


Code in 1679171114_every_1_days.bat file
@REM Script generated by Areca v7.5 on Nov 29, 2016 8:27 PM
@REM Target Group : "workspace"
@REM Target : "Test"
@chcp 1252
@REM This script must be run every day.
@REM Daily backup
@"D:/Program Files (x86)/Areca/areca_cl.exe" backup -c -wdir "C:\Users\AGARWA~1\AppData\Local\Temp\tmp-agarwaldvk" -config "C:/Users/agarwaldvk/.areca/workspace/1679171114.bcfg"


Code in 1679171114_every_7_days.bat file
@REM Script generated by Areca v7.5 on Nov 29, 2016 8:27 PM
@REM Target Group : "workspace"
@REM Target : "Test"
@chcp 1252
@REM This script must be run every 7 days.
@REM Merge between day 7 and day 14 
@"D:/Program Files (x86)/Areca/areca_cl.exe" merge -c -config "C:/Users/agarwaldvk/.areca/workspace/1679171114.bcfg" -from 14 -to 7
@REM Merge after day 21 
@"D:/Program Files (x86)/Areca/areca_cl.exe" merge -c -config "C:/Users/agarwaldvk/.areca/workspace/1679171114.bcfg" -delay 21


This is what I thought would replicate my desired backup philosophy!


Hey, by the way, do you know what or how to specify a FQDN (fully qualified domain name) in the context of Bacula - my Ubuntu machine is a standalone server. I don't understand this very well at all! I have read its very difficult to get Bacula properly set up and running but I thought at least if I know what information needs to be provided then I can try and give it a go!


Best regards


Deepak

---

### Post by mastablasta on 2016-11-30
> **agarwaldvk said:**
> 
Also, I am looking at Urbackup and from what I have so far, I like it too! Not sure, where it needs to installed and run from and it appears that it would be able to do what I need.


Thanks again. I will spend a bit more time reading up on Urbackup and Areca and between the two , may be one of these can do what I am looking to do!

Edit : Can you give me some pointers to where can I see some examples of a cron job scripts to schedule a backup job to realize what I am after using either Areca or UrBackup?

Edit 2:-
Did a fair bit of reading on both Areca and UrBackup. Couldn't figure out how do we actually create a scheduled job in UrBackup and run it.

 

urBackup is pulling updates, so i guess  this is done on server end. not sure how. it is using osme scripts. maybe thorugh cron. i haven't really went that deep into it as push seems a better way to do it.


> 
Do we then need another job to delete the old backup files?
i believe not, for more info see below.


> 
Edit 3 :-
Just installed Areca on my Windows PC first as a test. These are the 3 files that it generated. From what the documentation said, I believe that I can use the Windows Scheduler and use these files to automate the backup process - I tried to create the "backup shortcut" & the "backup strategy" from their graphical interface. I don't quite get the code. Could someone please explain the generated code to me?

Code in backup_1679171114.bat file
@REM Backup script generated by Areca v7.5 on Nov 29, 2016 8:24 PM
@chcp 1252
@REM Differential backup
@REM Target Group : "workspace"
@REM Target : "Test"
@"D:/Program Files (x86)/Areca/areca_cl.exe" backup -d -c -wdir "C:\Users\AGARWA~1\AppData\Local\Temp\tmp-agarwaldvk" -config "C:/Users/agarwaldvk/.areca/workspace/1679171114.bcfg"


Code in 1679171114_every_1_days.bat file
@REM Script generated by Areca v7.5 on Nov 29, 2016 8:27 PM
@REM Target Group : "workspace"
@REM Target : "Test"
@chcp 1252
@REM This script must be run every day.
@REM Daily backup
@"D:/Program Files (x86)/Areca/areca_cl.exe" backup -c -wdir "C:\Users\AGARWA~1\AppData\Local\Temp\tmp-agarwaldvk" -config "C:/Users/agarwaldvk/.areca/workspace/1679171114.bcfg"


Code in 1679171114_every_7_days.bat file
@REM Script generated by Areca v7.5 on Nov 29, 2016 8:27 PM
@REM Target Group : "workspace"
@REM Target : "Test"
@chcp 1252
@REM This script must be run every 7 days.
@REM Merge between day 7 and day 14 
@"D:/Program Files (x86)/Areca/areca_cl.exe" merge -c -config "C:/Users/agarwaldvk/.areca/workspace/1679171114.bcfg" -from 14 -to 7
@REM Merge after day 21 
@"D:/Program Files (x86)/Areca/areca_cl.exe" merge -c -config "C:/Users/agarwaldvk/.areca/workspace/1679171114.bcfg" -delay 21



it does what is says (REM is commenting line in .bat files) all you need to is set up Windows task to run as specified (so run every day, run every 7 days). the rest is done per yoru setup. e.g. Merge between day 7 and day 14, Merge after day 21. so your newer backups are "merged" with old backup.

now you can see that what scriprt does is run the command line version of Areca and then pulls your setup from the backup config file (.bcfg). 

i didn't get the differential.bat as i am running the incremental one. at work i do have the one i run every day, then one that is run every 7 days and another one ran every 28 days.
i am backing up to a usb flash drive, incremental backup, only zipping the files. 
first it creates the original backup and then it adds more and merges as necessary (see some pics).

their documentation they made is quite good and explains it all well.

---

### Post by agarwaldvk on 2016-12-01
Hi mastablasta


Thanks again.

Two questions :-

1. To me, the backup file and the every_1_ day file both appear to be identical - so I would I believe that I can only run the every_1_ day file everyday
    What does the command @chcp 1252               'Is this the code page definition?
2. Do I necessarily need to merge these differential backups - my preference is have a separate backup for each backup that is run
    For that, do I just comment out the merge lines? And if I do that then all the files become identical. How does the program then know that it has to make 1 full backup, 6 differential backups and then repeat the process keeping 2 backup sets from the last 2 weeks? These must be specified in the config file - do you think you might be able to reproduce an example of the config file that will give me an idea as to how to specify these parameters as I don't get it at the moment!

Would you be able to explain that to me. I have also been doing some reading on 'Backup2l' and I quite like it too. I did make another posting seeking advice on my understanding of how it works and also seeking advice on things that I don't understand. Do you want to comment on that?

I may then be in a better position to decide which application to go for - I am very very new to linux based systems - I know it can a patience test for the likes of you all who know so much about these things trying to provide solutions to absolute beginners. So please bear with me.

I will get there eventually!


Best regards


Deepak

---

