---
title: "How good is Déjà Dup?"
date: 2015-06-26
forum: The Cafe
---

### Post by wolfv6 on 2015-06-26
I am shopping for an online backup.

Seems like Déjà Dup with Amazon S3 might be good backup system.
Are you happy with Déjà Dup?
How easy is it to restore an old version of a file?


I only need to backup 1.5 GB of data, and the first 5GB at Amazon S3 are free.
I searched the ubuntu forms for "Deja Dup" in the title, and found 14 threads in the past 6 months.
Is that because it's popular or because it has a lot of problems?

I am using Gnome desktop.

Thank you.

---

### Post by mikodo on 2015-06-26
I hope you get your answers.

Maybe I'll do the same.

At most I would want to backup there, would be less than a GB.

---

### Post by Welly Wu on 2015-06-26
It's not very good in my opinion. The problem with Deja-Dup is that it is very hard to restore individual files from separate folders. The other major problem is that larger data backups get corrupted over time with no ability to fix this problem. I strongly recommend using CrashPlan. The free version is more features rich with the capability to backup and restore individual folders and files as well as the ability to backup to another destination like an external hard disk drive or a NAS drive plus the capability to backup to another CrashPlan user's PC remotely. Most of the other GNU/Linux backup programs have a set of features intended for a specific target audience and Deja Dup aims to simplify or dumb down this process as much as possible. I have stopped using it altogether and I pay for CrashPlan+ Family Plan so that I can backup to CrashPlan Central which is one of their data centers located worldwide. The important thing to note is not necessarily data backup, but data restoration has to be perfect especially when you need to recover lost data. CrashPlan is virtually bulletproof when it comes to data restoration. It is well tested and proven.

---

### Post by wolfv6 on 2015-06-26
> **Welly Wu said:**
> The problem with Deja-Dup is that it is very hard to restore individual files from separate folders.
That's a deal killer for me.  Thanks for the heads up [COLOR=#000000]Welly Wu.[/COLOR]

I am now considering memopal.  Here is what others have said about memopal:

3GB free, version history, proprietary
[http://www.memopal.com/online-storage/](http://www.memopal.com/online-storage/)

Imediate real-time automatic backups
Web version allows you to search for specific files to restore
Client version you select the Restore button and then double click through a list of folders
No option to create your own encryption key
[http://cpureport.com/memopal-review/](http://cpureport.com/memopal-review/)

Italian based
American users may experience some slight slow down of their backup process
[http://www.cloudwedge.com/online-backup-reviews/memopal-review/](http://www.cloudwedge.com/online-backup-reviews/memopal-review/)

Everyone seems to love CrashPlan.
memopal is not as perfect as CrashPlan, but for 1.5 GB, memopal is $60/yr less than CrashPlan.

---

### Post by Welly Wu on 2015-06-27
You and I have no idea what kind of data or capacities we will need in the next several years. The reason why I don't like data plans is because I'm limited in terms of the aggregate data pool and bandwidth and this is compounded by the fact that not everybody in this world has access to an Internet service provider that has an unlimited data plan for home residential consumers. There is a good reason why a lot of people recommend CrashPlan. If you take a look at your current data and its' storage size and you choose an online backup company that has a plan that meets your current needs, then there will be growing pains. What if you decide to purchase another newer PC or if you inherit an older PC that you would like to use? What if you choose to grow your data and storage needs?

The real expense is switching. Just like switching PCs and desktop or mobile operating systems can be expensive in terms of time and money, so too is switching from one online backup company to another one. Remember, this is an investment of your private user data to be held temporarily by another company far away from your home or office. If you don't take these simple considerations into account, then you will wind up spending more of your time and money in the long run.

CrashPlan is here to stay for the foreseeable future. I'm not trying to sell you to this company, but I have probably thought this out more carefully than you have and I have certainly done my homework. There is a risk with going with a company that is not an industry leader when it comes to online backup. If the company folds, then your data goes with it. I can't tell you how many online backup and synchronization companies have come and gone in the past five years alone. Canonical, the creators of Ubuntu, used to have their Ubuntu One cloud synchronization service and it went belly up along with their customers' private data as just one example in the past five years.

Let me make a suggestion: take a closer look into CrashPlan+. Try the free version to test the waters. Send me a private message if you need help installing or configuring it. Once you realize the features that can be unlocked as a paying customer and you see its' benefits, then that should convince you to give it more serious consideration.

This is your private user data. You get to choose with whom to do business, but remember that it's still your data that you're trying to backup to a remote server somewhere in this world.

---

### Post by wolfv6 on 2015-06-27
Hi Welly Wu.
You make some good points.

I don't consider memopad a permanent solution.
If memopal goes out of business I would have to learn another backup service, or migrate entirely to cloud applications.
The only reason I have a PC is to write software and CAD.  Once those are hosted in the cloud I won't need a backup service.

---

### Post by Welly Wu on 2015-06-27
Listen, you don't really want to upload your private user data to some company somewhere in the world if it is not going to be a long term commitment. Avoid this scenario if possible in the first place. I think that you need to do more research into online backup versus cloud synchronization service providers.

You may want to research SpiderOak: [https://www.spideroak.com](https://www.spideroak.com). They give you almost everything. They are a bit pricey, but you get absolute privacy.

---

### Post by wolfv6 on 2015-06-27
Hi Welly Wu,
Nothing on my PC needs to be hidden.  My PC contains no sensitive financial information or sensitive identity like social security number.  I am not a political activist.  My software and CAD projects are open source.

My sensitive data is encrypted on a Web application (like LastPass for example) and is not on my PC.

In a few years I will have no PC to backup.  I will have a thick client (like Chrome OS for example).  I am just waiting for on-line CAD and on-line software development tools to mature.

I understand the difference between online backup and cloud synchronization service providers.  memopad is an online backup service.

---

### Post by Welly Wu on 2015-06-27
Google Chrome OS is not a thick client. It is a very thin client.

Have you considered building your own cloud data backup solution? You could purchase a network attached storage product and download and install Own Cloud to host your own files. It will be more expensive upfront, but you will be able to save on long term costs and you have physical control of your data. There are commercial solutions available like Western Digital's My Cloud Personal Cloud or Seagate Central, but they are designed for Microsoft Windows or Apple Macintosh OS X. You may want to consider simply copying and pasting your personal user files to a NAS drive as well.

It may be more expensive for you to purchase an online cloud backup subscription if you have less than 2.0 GB of data. A free solution that you may want to consider is SpiderOak since they will give you up to 5.0 GB of cloud storage capacity for free of charge. If you refer several friends and they sign up for SpiderOak, then you can earn more free cloud storage capacity up to a certain limit. This will involve no financial costs to you. The one thing that you must remember about SpiderOak is that it relies on 100.00% zero knowledge privacy. You must make sure that you remember your user ID and master password. There are no password reset features available. Two-factor authentication is in beta test phase and it is not officially supported so do not log into your SpiderOak account on the website to enable this specific feature yet or you could get locked out of your account permanently. As long as you redeem an electronic coupon at the time when you register your free SpiderOak account, you should be able to have up to 5 - 6 GB of free cloud storage capacity for the lifetime of your account. If you can keep your personal data storage needs within that limit, then this is the best solution for you and you get the benefits of SpiderOak which integrates cloud data backup, synchronization, and secure file sharing services combined along with their zero knowledge privacy. Perhaps you should investigate this company in detail. It seems to be the right fit for you.

---

### Post by wolfv6 on 2015-06-27
The SpiderOak free 2 GB plan is only a 60 trial. [https://spideroak.com/about/price-list](https://spideroak.com/about/price-list)
Please correct me if I am wrong.

I want my backups off site, so I will not build my own cloud data backup.

---

### Post by Welly Wu on 2015-06-27
Yes, you are correct. This frustrates me to no end. SpiderOak keeps changing their pricing plans and they keep making their product and service more expensive over time. They still offer the 30 GB data plan for $7.00 USD per month which is kind of expensive, but it would fit your needs and provide you with sufficient storage capacity for the near future.

Otherwise, it's a pretty tight market if you are a GNU/Linux user. It's either CrashPlan or SpiderOak and not much else unless you want to build your own cloud storage solution.

Perhaps you should reconsider shopping for a cloud backup provider given how little data you need to backup. A direct attached storage external hard disk drive might be best for you. Simply copying and pasting your personal user files might be the best solution, but it requires more frequent upkeep of your data over time. No matter what, do not use Deja-Dup for your personal backup needs. You might want to consider the FLOSS LuckyBackup. Do not use Back in Time as there is no simple method to perform data restoration using their GUI.

Remember, cloud data backup providers are designed for customers that have more than 100.00 GB of personal user data that they need to backup to their data centers worldwide. You don't fit that category.

---

### Post by Welly Wu on 2015-06-27
[http://www.techrepublic.com/blog/five-apps/five-linux-backup-tools-that-wont-let-you-down/](http://www.techrepublic.com/blog/five-apps/five-linux-backup-tools-that-wont-let-you-down/)

Please read this article. The author presents a strong case and review for LuckyBackup. I have rarely used it, but it seems to work and it's free. This article is a bit dated, but the data backup software packages are within the main Ubuntu software repositories. I'd recommend LuckyBackup to you in your case rather than a cloud backup provider.

---

### Post by wildmanne39 on 2015-06-27
I would have to agree that Déjà Dup has or had issues at least the last time I used it, it backed up the files great but I could not restore them.
[http://www.techsupportalert.com/content/best-free-online-backup-sites.htm](http://www.techsupportalert.com/content/best-free-online-backup-sites.htm)

---

### Post by mikodo on 2015-06-27
> **Welly Wu said:**
> Listen, you don't really want to upload your private user data to some company somewhere in the world if it is not going to be a long term commitment. Avoid this scenario if possible in the first place. I think that you need to do more research into online backup versus cloud synchronization service providers.

You may want to research SpiderOak: [https://www.spideroak.com](https://www.spideroak.com). They give you almost everything. They are a bit pricey, but you get absolute privacy.

Yes. I looked into SpiderOak. A bit into CrashPlan. A lot into TarSnap  [http://www.tarsnap.com/index.html](http://www.tarsnap.com/index.html) TarSnap's dev and singular maintainer (Dr. Colin Percival), is a true genius. He is interesting to read about. I was hell-bent on using his very cheap service (for the small amount of data I would want to backup on the cloud), until I woke up and wondered what would happen if he died. Case closed for that. I am going to continue looking into CrashPlan.

Thanks, for sharing your insights.

---

### Post by wolfv6 on 2015-06-27
> **Welly Wu said:**
> A direct attached storage external hard disk drive might be best for you.
I want off-site backups.

> **Welly Wu said:**
> cloud data backup providers are designed for customers that have more than 100.00 GB of personal user data that they need to backup to their data centers worldwide. You don't fit that category.
How is backup size relevant?

---

### Post by Welly Wu on 2015-06-27
If you want off-site backup, then I suggest that you open an account at your local bank branch and rent a safety deposit box. This is what I do with PNC Bank located on Franklin Avenue in Nutley, New Jersey. My Transcend StoreJet portable, rugged, encrypted hard disk drive and the Super Speed USB 3.0 cable are stored at my bank branch inside my safety deposit box. It requires that I and a PNC Bank employee use two separate master keys and there is a written audit trail requiring valid US government ID to be presented before I can access my safety deposit box.

Backup size is relevant to you as a paying customer because you wind up spending your money to backup little data which means greater profits for the company. The less data that you have to backup to an online cloud backup provider, the greater the profits that the company receives on a monthly or annual basis at your cost. Once you upload 100 - 150 GB of your personal user data to a cloud backup provider, they start losing money in general. You wrote that you have 1.50 GB of data which is not that much.

I don't think that it is worth it for you to consider a cloud backup service provider in your particular case. It would be cheaper for you to quick format and encrypt an external hard disk drive and store it with a trusted family member of close friend if you want to avoid the cost structure of paying for a safety deposit box for such little data. Cloud backup service providers make it affordable for mass data backups in excess of 100.00 GB or more for each customer and PC. If your data does not require top secret security and it is so little in capacity, then you will be much better off having a discussion with a family member or friend to have temporary custodial ownership of your external hard disk drive in your personal situation.

Don't develop tunnel vision and insist on cloud backup if it is not a good fit for your situation.

---

### Post by mikodo on 2015-06-27
Maybe the OP wants to have an on-line storage, so that it is  *immediately available. Storing a device outside of the home,  wouldn't do that. That is why I am considering one. In the OP's case,  there might even be others he/she wants to share code with, when it is  needed. Not after driving across town or such.

---

### Post by Welly Wu on 2015-06-27
That is a possibility, but please remember that almost all of these cloud backup and synchronization service providers will incrementally raise their prices for the services that they offer over time so it will only get more expensive in the long term future. That is an important fact that needs to be considered when investigating a cloud backup or synchronization service provider.

For my father, my close friends, and myself, CrashPlan+ Family Plan made the most sense. My father has roughly 900.00 GB of personal user data. My close friend has roughly 115.00 GB of personal user data and it is private. I have 1.1 - 1.2 TB of personal user data of which only a fraction is considered to be unique and definitely top secret. For us, CrashPlan+ Family Plan is the right cloud data backup service provider because it is so affordable and it is available for all major desktop operating systems and the installation and configuration of the desktop client is pretty easy and straightforward. The additional security features of using AES 256 bits SHA-256 bits along with a custom encryption key and GID for each PC ensure privacy and data security. The unlimited data plan for each user and PC is a plus. I own a 2015 ZaReason Zeto desktop PC and a 2013 Lenovo IdeaPad Y510P notebook PC. My close friend owns my former 2012 System76 Lemur Ultra (lemu4) notebook PC. My father owns a Lenovo IdeaPad Z400 Touch notebook PC running Microsoft Windows 8.1 Home 64 bit. CrashPlan+ allows us to add external disk drives and add it to our backup selection or sets at no additional charge. With respect to GNU/Linux, it is fairly easy to edit the /etc/fstab file to mount a NAS drive at boot up and it can be added to CrashPlan+. We don't plan to purchase many desktop or notebook PCs in the future so the CrashPlan+ Family Plan permits us to add up to 10 PCs with unlimited data plans for each one. This is why close investigation and careful research has led to to conclude that it is the right product and service that best fits our needs.

With SpiderOak, you can make an unlimited number of changes to existing files and each one will be backed up for up to 30 days. CrashPlan+ allows unlimited changes to all files that are backed up forever. You can even set a custom backup set whereby you choose specific drives, partitions, volumes, folders, and files along with its' own custom file version history depth cue and backup frequency schedule and you can create an unlimited number of individual backup sets and all of your data is backed up permanently so long as you continue to pay your monthly or annual subscription bills. SpiderOak doesn't have this capability.

It is still possible to download and install the free CrashPlan GNU/Linux desktop client and connect an external disk drive to backup your personal user data and store it off-site on your own terms.

An important consideration to make is the backup frequency and file version history. Most cloud backup service providers provide a limited number of file version histories and a fixed backup frequency to provide real-time backup of files automatically. SpiderOak does not allow the user to make a highly granular number of changes to file version history and backup frequency with their current desktop client. CrashPlan+ does. It provides unlimited file version history and customizable backup frequencies for each PC. This is an important feature that is not often discussed when comparing CrashPlan+ to its' competitors and for some people they don't know these facts and it becomes a problem when they need to restore a specific file version in the future for some reason.

This is why I strongly recommended CrashPlan+ to the OP if he requires off-site cloud backup. Amazon S3 and Jungle Disk do not provide many robust features especially when used with Deja-Dup.

You get what you pay for most of the time.

---

### Post by mikodo on 2015-06-27
Correct. SpiderOak's lack of deduplication, and it's progressive bit creep, winds up costing one more and more. That is why I turned away from it. It does have a very good security model though.

---

### Post by wolfv6 on 2015-06-27
I like on-line backup service because it's automatic and off-site.
3 GB at memopal is free [http://www.memopal.com/prices/](http://www.memopal.com/prices/)

I just stumbled onto **s3cmd sync**[COLOR=#000000][FONT=Verdana] command, which [/FONT][/COLOR][COLOR=#000000][FONT=Verdana]is similar to a unix [/FONT][/COLOR]*rsync *[COLOR=#000000][FONT=Verdana]command.
[/FONT][/COLOR]http://s3tools.org/s3cmd
[http://s3tools.org/s3cmd-sync](http://s3tools.org/s3cmd-sync)
[http://aws.amazon.com/s3/pricing/](http://aws.amazon.com/s3/pricing/)

I used rsync to make backups to a USB stick, before switching to Windows 7 and online backups with Mozy.
I really liked rsync, but want automatic off-site backups.  With s3cmd sync I can have both.
I will take a closer look at s3cmd sync tomorrow.

---

### Post by Welly Wu on 2015-06-27
SpiderOak is gaining more local, state, and federal customers for select information and data, but it is losing more home consumers at a cost. CrashPlan recently upgraded to version 4.2.0 which now includes the usage of AES 256 bits with SHA-256 so now everybody can benefit not just the US government employees. Remember, Oracle Java 8 is required and it is incrementally improved over version 7 to use CrashPlan+. CrashPlan+ has custom .ini and .conf files that the customer can edit to configure the Oracle Java virtual memory size and other settings to make it compatible with Ubuntu GNU/Linux. You will also need to modify your /etc/fstab tmpfs settings so that the Oracle Java SWT files can be loaded as required by CrashPlan+. Once this is set, then CrashPlan+ will launch normally and you can have an Ubuntu Unity launcher icon as well. Configuring CrashPlan+ is fairly simple and it only requires one restart of the CrashPlan Engine to make the changes take into effect without requiring your PC to restart itself. This will enable full speed uploads during your initial data backup to CrashPlan Central.

I am using Private Internet Access VPN with AES 256 bits, SHA-256, and ECC 521 bits and CrashPlan+ consistently achieves roughly 14.00 MB/s upload speeds after I have learned how to install and configure it for maximum speed and performance. My initial data backup of roughly 1.125 TB was done in as little as two days because the speed fluctuated and it gradually got much faster as more data was uploaded to CrashPlan Central.

SpiderOak is a resource hog and PC Magazine reviewed it and they concluded that it is among the slower performance cloud backup service providers due to its zero knowledge privacy policy and the way in which the company designed its' product and service. It does indeed feature data de-duplication, but there is a 10 step syndication process that each user and PC must complete before you can upload or download data from SpiderOak's data centers in California. The more PCs and the more data that reside on SpiderOak's data centers, the longer amount of time this 10 step syndication process will take each time a new PC is added to a primary SpiderOak account or if a user has to reinstall their desktop operating system and go through the 10 step syndication process all over again for each PC. This costs you more time.

Remember, CrashPlan+ has a synchronization process that does both block level and file level double verification to ensure 100.00% bit-perfect data backups using the TCP protocol which checks for errors using parity checks. It doesn't take a long period of time even if you have 10 PCs and several terabytes of data on each PC to finish the synchronization process and it only requires two separate steps. This is why CrashPlan+ is much lighter on PC resources and it is much faster than SpiderOak.

Obviously, I have tried both so I know what I'm writing about. Furthermore, I have tried most of the popular FLOSS GNU/Linux data backup software packages and they each have their flaws. Almost all of them don't offer real-time data backups, file version history, independent backup sets, and data de-duplication features that commercial software products and services offer as a standard feature.

My close friend backed up his data to CrashPlan Central in as little as four hours totalling roughly 110 - 115 GB using his Private Internet Access VPN credentials and encrypted network connection. My father is almost done backing up nearly 900.00 GB of his personal user data to CrashPlan Central and I just installed it less than a day and a half ago on his notebook PC.

---

### Post by mikodo on 2015-06-27
Alright. I stand corrected.

Obviously, I didn't read the part about SpiderOak's data deduplication on their web-site.

Thank you.

---

### Post by rewyllys on 2015-06-29
I second Welly Wu's recommendation of CrashPlan.  I've used it for just over three years now, using it to store both my Linux Mint /home folder and my wife's Windows User folder on her Windows computer.

For additional protection, I use LuckyBackup nightly on my /home directory.

And, finally, a good deal of my /home directory is under my Dropbox directory, which shares it with my wife's computer, and with Dropbox's online storage.

As a result, I have not lost any files unrecoverably in the last three years.

---

### Post by obake2 on 2015-07-26
I prefer Wuala over SpiderOak:

[http://lifehacker.com/the-best-cloud-storage-services-that-protect-your-priva-729639300](http://lifehacker.com/the-best-cloud-storage-services-that-protect-your-priva-729639300)

SpiderOak is based in the US, and if you are concerned abot privacy, then you must avoid any US based cloud or email services. Wuala on the other hand is Wuala is registered and located in Switzerland.

Please note that both are proprietary software.

[http://www.cloudwards.net/spideroak-or-wuala-which-is-more-secure/](http://www.cloudwards.net/spideroak-or-wuala-which-is-more-secure/)


For local back up storage, I prefer to use [BACK IN TIME]("http://backintime.le-web.org/") which is available the Ubuntu's repository.



See also: [List of File Storage & Sync]("https://prism-break.org/en/all/#file-storage-sync")

---

### Post by RichardET on 2015-07-30
> **Welly Wu said:**
> It's not very good in my opinion. The problem with Deja-Dup is that it is very hard to restore individual files from separate folders. The other major problem is that larger data backups get corrupted over time with no ability to fix this problem. I strongly recommend using CrashPlan. The free version is more features rich with the capability to backup and restore individual folders and files as well as the ability to backup to another destination like an external hard disk drive or a NAS drive plus the capability to backup to another CrashPlan user's PC remotely. Most of the other GNU/Linux backup programs have a set of features intended for a specific target audience and Deja Dup aims to simplify or dumb down this process as much as possible. I have stopped using it altogether and I pay for CrashPlan+ Family Plan so that I can backup to CrashPlan Central which is one of their data centers located worldwide. The important thing to note is not necessarily data backup, but data restoration has to be perfect especially when you need to recover lost data. CrashPlan is virtually bulletproof when it comes to data restoration. It is well tested and proven.

I use a in house server with 2 TB, expandable to 8 TB;  it's alot more secure than any cloud system.

---

### Post by RichardET on 2015-07-30
> **rewyllys said:**
> I second Welly Wu's recommendation of CrashPlan.  I've used it for just over three years now, using it to store both my Linux Mint /home folder and my wife's Windows User folder on her Windows computer.

For additional protection, I use LuckyBackup nightly on my /home directory.

And, finally, a good deal of my /home directory is under my Dropbox directory, which shares it with my wife's computer, and with Dropbox's online storage.

As a result, I have not lost any files unrecoverably in the last three years.

But 4 years ago, you did?

---

