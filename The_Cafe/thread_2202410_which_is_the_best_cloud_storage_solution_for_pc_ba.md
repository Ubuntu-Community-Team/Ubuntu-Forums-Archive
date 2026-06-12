---
title: "which is the best cloud storage solution for pc backup"
date: 2014-01-29
forum: The Cafe
---

### Post by james_mascarenhas on 2014-01-29
Hi Everyone,

The Market is flooded with so many cloud storage provider and i am really not sure to which one to opt for, I have done some research and have come up with 5 to 6 company that are specialized in Cloud Storage Services.

My requirement:-

1) To take backup of everything that exist in my organization
2) Backup of every devices that we have provided for our employee

So basically i need to backup everything and store and secure it in some trusted site, your guidance will be appreciated. Here is my list that i searched :

Google Drive [http://www.google.com/drive/about.html](http://www.google.com/drive/about.html)
Amazon AWS [http://aws.amazon.com/](http://aws.amazon.com/)
Ubuntu One [https://one.ubuntu.com/](https://one.ubuntu.com/)
SugarSync [https://www.sugarsync.com/](https://www.sugarsync.com/)
EndPointVault [http://www.endpointvault.com/](http://www.endpointvault.com/)

These are some of the sites, if there exist some other sites that matches my requirement  i will be glad to go for it

Thanks In Advance

---

### Post by coffeecat on 2014-01-29
*Thread moved to **The Cafe**.*

Move from the Community Wiki Discussions sub-forum. Please see the [sticky]("http://ubuntuforums.org/showthread.php?t=2074201") for that section.

---

### Post by mastablasta on 2014-01-29
there is Skydrive soon to be Onedrive from Microsoft
dropbox
spideroak (this one is kind of slow but data is encrypted)

you can also make you own cloud... which might be a cheaper solution or not. it depends... how much data do you estimate you will backup? a few GB? a few TB?

---

### Post by SeijiSensei on 2014-01-29
Are you really sure you want to place all your confidential business documents on a publicly-accessible server even with encryption?  Have you discussed this plan with your attorney and accountant? Documents stored on your premises might have greater protections than ones stored on a cloud server if you end up in litigation.   Do these data include things like credit-card numbers?  If so, you'll need to comply with the [PCI DSS standard]("http://usa.visa.com/merchants/risk_management/cisp_merchants.html").

This sounds like an awful lot of data, more than any free service will provide.  How much are you willing to spend for an archiving service?  Perhaps that money would be better spent on a machine that does backups in your office.  

If you're concerned about surviving a fire or flood, you're probably better off writing tapes and taking them home or storing them in a safe-deposit box.

Just a hint that managing backups isn't only an IT task.  They're integral to the operation of any business, and their management needs to be treated as a serious business decision.

---

### Post by ssam on 2014-01-29
you could look at [http://rsync.net/](http://rsync.net/)

another option is to run something like owncloud which provides the features of something like drop box but can be run on your own servers. [https://owncloud.org/](https://owncloud.org/)

---

### Post by Habitual on 2014-01-29
the S3 bucket service at AWS is free to move data **in** but then you are charged for data out.
[S3 Prices]("http://aws.amazon.com/s3/#pricing")
[DragonDisk]("http://www.dragondisk.com/") for employees can copy to Amazon or Google Cloud.

> **james_mascarenhas said:**
> 1) To take backup of everything that exist in my organization
That's a pretty broad paintbrush and could consume a lot of time and resources.

What are the companies requirements?
You said "my"...

---

### Post by PJs Ronin on 2014-01-30
I would recommend any cloud not resident on US soil.

---

### Post by Roasted on 2014-01-30
The only cloud I trust is my ownCloud, nestled safetly in my basement with 3TB accessible to me any time I want.

---

### Post by mastablasta on 2014-01-30
unless the basement cathces fire or get's flooded.

i htink there are some backup guidelines which state that for serious backup the facility should be at least 50km away from location that needs backup.

---

### Post by Don_Stahl on 2014-01-30
On security, as SeijiSensei mentions: although American NSA and British GCHQ are in the news right now as data snoops, the  Russian, Chinese, and Israeli security agencies are probably well versed in data capture too. If complete privacy is a concern, I think no cloud service can be trusted no matter where the server farm is located, or what path the data travels to get there. For that matter, laws protecting or *unprotecting* data can change in ANY nation. And who's to say that every Mossad or FSB operative is above selling snooped data on the sly?

Evaluate the data to be backed up, maybe. For instance, is there any one of your users -- even just one -- who stores passwords in a plain-text file? 

Well, anyway. Not to throw cold water on your plans... if you trust encryption (and aren't paranoid), then you can make sure all your backups are encrypted *before* they hit the data highway. 

A dedicated onsite server, as several people mentioned, might be one choice. It has it's downsides, too, of course -- it means you handle the security, and if there's a breach it's your baby. And, as mastablasta writes, it's not the best disaster-recovery choice.

To safeguard against onsite disaster, I put a couple of data files on Microsoft's service (was SkyDrive, soon to be OneDrive) when I do weekly backups. But the files are just process numbers, and include nothing sensitive. And they're small -- after compression they total a few hundred mb. So you're dealing with a different proposal.

---

### Post by bashiergui on 2014-01-30
I would add that you might consider encrypting all your backups locally before sending them to the cloud. That way if someone steals the data they just get a useless blob of bytes. You would need to manage the keys locally and make sure you had a backup of the key somewhere (NOT in the cloud) in case of disaster.

Other considerations are what the cloud provider guarantees for their backups. What if they have a disaster? What's their liability? There are providers that take no responsibility for the safety of your data. What happens if law enforcement seizes the server your data is on as part of an investigation into someone else? If you use a provider in another country, how do those laws affect your data? What's the monetary loss to you if you lose the backups suddenly and forever? Is that an acceptable risk to take because of the cost savings the cloud enables?

---

### Post by rewyllys on 2014-02-01
I've been using [CrashPlan]("http://www.code42.com/crashplan/") for almost two years now, and have been thoroughly satisfied with their cloud service.  It's not free (except for a 30-day trial period), but their charges strike me as very reasonable.

---

### Post by cigtoxdoc on 2014-02-09
I have been using SpiderOak for over a year as I transition from Windows to Ubuntu.  I also have been using Data Deposit Box (aka KineticD) for Win Systems for over 5 years.  unfortunately mgmt. at KineticD is anti-Linux and they would rather lose clinets than build a front-end for Linux PCs.  KineticD has been very reliable, and I have been able to download needed files while traveling in Europe and Japan.  I cannot afford to have lost of my physical office mean loss of data.  My clients demand 24/7 support, and I need 24/7 access to my data from any PC.

John

---

### Post by CharlesA on 2014-02-09
> **SeijiSensei said:**
> Are you really sure you want to place all your confidential business documents on a publicly-accessible server even with encryption?  Have you discussed this plan with your attorney and accountant? Documents stored on your premises might have greater protections than ones stored on a cloud server if you end up in litigation.   Do these data include things like credit-card numbers?  If so, you'll need to comply with the [PCI DSS standard]("http://usa.visa.com/merchants/risk_management/cisp_merchants.html").

That could cause issues if the cloud service was compromised, but the data should be encrypted locally before sent to "the cloud" if it was that type of sensitive data.

> This sounds like an awful lot of data, more than any free service will provide.  How much are you willing to spend for an archiving service?  Perhaps that money would be better spent on a machine that does backups in your office.  

Agreed. It also depends on how much bandwidth you have available or if you want to put a dedicated line in specifically for the backups. In the case of my company, they were looking at an offsite backup solution, but since they around 3TB of data, and only two bonded T1 lines, that would take an insane amount of time to upload, so they decided to backup to external drives and ship those drives to other offices.

> If you're concerned about surviving a fire or flood, you're probably better off writing tapes and taking them home or storing them in a safe-deposit box.

Just a hint that managing backups isn't only an IT task.  They're integral to the operation of any business, and their management needs to be treated as a serious business decision.

That can work with hard drives too, but there are more moving parts on a hard drive than a tape. ;)

I still don't really understand why the majority of people I've dealt with seem to think backups are just an IT thing. Everyone should know how to make backup and what the best practices are.

> **rewyllys said:**
> I've been using [CrashPlan]("http://www.code42.com/crashplan/") for almost two years now, and have been thoroughly satisfied with their cloud service.  It's not free (except for a 30-day trial period), but their charges strike me as very reasonable.

+1ish. I used them for home use, but like I said earlier, cloud backups do not make sense if you have a lot of data and very little bandwidth unless you want to wait ***forever*** for the initial backup to complete. Granted, CrashPlan offers seed service to make the initial backup easier, but it is still a lot of data to backup.

---

### Post by buzzingrobot on 2014-02-09
I once backed up a modest-size Mac install -- 60 gigs -- to a commercial cloud backup provider.  The initial upload took 3 weeks.  

If you need really large files backed up *now*' not the day after tomorrow, this is not the best approach.

[EDIT:  At some point; backup becomes something a business should not try to handle in-house, but outsource it.  Example:  I have a friend who operates a photography/graphic arts shop.  It's her sole source of income; she employees three people.  She recently decided to move her front-end production work from Windows to Macs.  She hired a local firm to do it all. Backup was critical because the images *are* the business. Now, with the new systems, backups are, on production machines, done as a file is saved. I.e., files stored in certain directories trigger an immediate automatic file copy to servers located in the office. Files on those servers are backed up hourly to additional storage outside the office. All image files and all office management files are also backed up daily to offsite storage in a colocation facililty on hardware she now owns that is managed by the firm she hired. ]

---

### Post by rewyllys on 2014-02-10
> **CharlesA said:**
> . . . . +1ish. I used them for home use, but like I said earlier, cloud backups do not make sense if you have a lot of data and very little bandwidth unless you want to wait ***forever*** for the initial backup to complete. Granted, CrashPlan offers seed service to make the initial backup easier, but it is still a lot of data to backup.
You're quite right.  My adoption of CrashPlan took place coevally with my moving to 50Mbps service, fortunately at a reasonable price, from a very competitive local ISP in Austin.  BTW, this ISP is going to start offering 1Gbps service next month, and I've already signed up for it.

---

### Post by CharlesA on 2014-02-10
> **rewyllys said:**
> You're quite right.  My adoption of CrashPlan took place coevally with my moving to 50Mbps service, fortunately at a reasonable price, from a very competitive local ISP in Austin.  BTW, this ISP is going to start offering 1Gbps service next month, and I've already signed up for it.

Try uploading ~3TB @ 2Mbps. I think it took the better part of the year to finish.

*twitches*

---

### Post by bashiergui on 2014-02-10
I found a great list of questions to ask a cloud provider before you sign on the dotted line
[http://www.fishnetsecurity.com/6labs/blog/top-security-questions-ask-your-cloud-provider](http://www.fishnetsecurity.com/6labs/blog/top-security-questions-ask-your-cloud-provider)

---

### Post by ethan21 on 2014-11-24
Try [CloudBacko software]("http://free.cloudbacko.com/?r=1d") for backup purpose. Its really helpful for me to access my data after some how it would be deleted or if my hard disk gets crashed. But, i am using CloudBacko software for backing up data, i don't have to worry about loosing the it. So CloudBacko software gives me fully secured and protected plan for backing up my data. CLoudBacko sequentially backed up the data into multiple destination ncluding Amazon S3, AWS compatible storages, Google Cloud Storage, Google Drive, Microsoft Azure, Microsoft OneDrive, OpenStack, Rackspace Cloud Files, Dropbox, FTP / SFTP sites, external USB drive, and local / mapped network drives.

---

### Post by PJs Ronin on 2014-11-24
I really don't know why anyone uses the cloud as a backup medium.   Big hard drives are as cheap as chips these days so I back up my 'universe' to a spare monster HD, go round a lady friend's house for coffee (weekly) and swap that drive with another one she keeps for me in a 'Peanuts' lunch box in her garden shed.   Most secure storage I know of, the conversation is terrific and she makes a decent brew... win win win.

---

### Post by mastablasta on 2014-11-24
> **PJs Ronin said:**
> I really don't know why anyone uses the cloud as a backup medium.   Big hard drives are as cheap as chips these days so I back up my 'universe' to a spare monster HD, go round a lady friend's house for coffee (weekly) and swap that drive with another one she keeps for me in a 'Peanuts' lunch box in her garden shed.   Most secure storage I know of, the conversation is terrific and she makes a decent brew... win win win.

ha, ha, ha... that is correct though. if you use it just for backup that is the cheapest solution.

but if you also want to share the data... for example I setup owncloud where I can now relatively *safely* share family photos with other family members. 

otherwise yes for backups external disks are simplest and cheapest solution.

---

### Post by Tar_Ni on 2014-11-24
I would stay clear of anything Google - Microsoft - Amazon related as far as cloud storage is concerned. You should take a look at services like Mega (founded by Kim Dotcom), SpiderOak (use encryption when storing and transfering data) or JottaCloud ( based in Norway) instead.

---

