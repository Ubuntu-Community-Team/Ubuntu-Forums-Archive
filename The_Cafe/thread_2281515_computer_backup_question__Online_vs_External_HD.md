---
title: "computer backup question:  Online vs External HD"
date: 2015-06-07
forum: The Cafe
---

### Post by jminor2 on 2015-06-07
Hi,  I know the best solution for backup/recovery for a computer is to use a cloud service like SpiderOak and an external hard drive.  But if you had to choose between the two, what would you pick.  I'm only interested is paid cloud backup services such as SpiderOak or iDrive ect... as I want secure storage.  And the external HD I'm looking at is Samsung's new TI One TB SSD.
Thanks for any advice....
John

---

### Post by user1397 on 2015-06-07
I use both personally, but I don't pay for any cloud services, just use the free ones available (google drive, dropbox, box.com, mega.co.nz).  The way I get past the security concern is I encrypt any sensitive files as a .7z file with a AES-256 password.

---

### Post by ajgreeny on 2015-06-07
I prefer to keep all my stuff locally and not trust cloud services to hold everything; perhaps I'm paranoid, but that is my feeling about this.

Therefore I rsync backups of my /home on to an external HDD formatted as ext3.  It all works brilliantly.

---

### Post by user1397 on 2015-06-07
ajgreeny, just curious, why ext3?

---

### Post by CharlesA on 2015-06-07
> **ubuntuman001 said:**
> I use both personally, but I don't pay for any cloud services, just use the free ones available (google drive, dropbox, box.com, mega.co.nz).  The way I get past the security concern is I encrypt any sensitive files as a .7z file with a AES-256 password.

I use both as well. Local backups are rdiff-backups, and I use CrashPlan for cloud/offsite backups. I kinda wish they didn't use Java since it's a nasty memory hog, but that's just how Java is.. :rolleyes:

I use my own encryption key with CrashPlan, so I feel a bit more "secure" with that instead of having to use a key based on a password or whatever.

---

### Post by ajgreeny on 2015-06-07
> **ubuntuman001 said:**
> ajgreeny, just curious, why ext3?
As opposed to what?

I thought ext4 was a bit OTT, and as I have been caught out with same-name but different letter-case filenames before now I did not want to use fat32 or ntfs.  I could have used ext2, in fact now I think more about it, I suspect it is ext2 not ext3, but the reason is the same.  It also makes sure all Linux file-permisions are retained, of course.

---

### Post by user1397 on 2015-06-07
> **ajgreeny said:**
> As opposed to what?

I thought ext4 was a bit OTT, and as I have been caught out with same-name but different letter-case filenames before now I did not want to use fat32 or ntfs.  I could have used ext2, in fact now I think more about it, I suspect it is ext2 not ext3, but the reason is the same.  It also makes sure all Linux file-permisions are retained, of course.
I see.  I don't really know the differences between ext2, ext3, and ext4 very well, that is why I asked :P

---

### Post by CharlesA on 2015-06-07
> **ajgreeny said:**
> As opposed to what?

I thought ext4 was a bit OTT, and as I have been caught out with same-name but different letter-case filenames before now I did not want to use fat32 or ntfs.  I could have used ext2, in fact now I think more about it, I suspect it is ext2 not ext3, but the reason is the same.  It also makes sure all Linux file-permisions are retained, of course.

Makes sense I guess. I've been running on ext4 for ages now. The fsck times are quite faster than with ext3, but they all share the same code base with ext4 adding improvements and new stuff on top of ext3. Use what works for you and stick with it seems logical.

---

### Post by jminor2 on 2015-06-08
Thanks for the discussion everyone.  I think I'll start with an external HD for now and keep an eye on the cloud based storage for the future.
Thanks again folks.....
John

---

### Post by Welly Wu on 2015-06-12
I use Deja-Dup to backup my /home/wellywu folder because it's built into Ubuntu and it's simple. I don't have a lot of data in my Crucial MX100 SATA-III 6 GB/s 256.00 GB solid state disk. I have a Transcend StoreJet USB 3.0 2.0 TB 5,400 RPM MIL-STD certified portable, rugged, encrypted hard disk drive where I keep my Deja-Dup backups and my media library along with my SteamOS + GNU/Linux PC game backups.

For off site backups, I use CrashPlan+ and I created my own custom encryption key. I pay for CrashPlan+ monthly Family Plan and I backup my 2015 ZaReason Zeto desktop PC, my 2013 Lenovo IdeaPad Y510P notebook PC, and my close friend's System76 Lemur Ultra Thin (lemu4) notebook PC. I prefer CrashPlan+ because it is state of the art for data backups and restoration of my personal user data and it just works in GNU/Linux. CrashPlan supports Microsoft Windows, Apple Macintosh OS X, and GNU/Linux. They are an excellent company and the turn around time for paid customers that file a technical support ticket is very fast which is usually in one business day. I use CrashPlan+ for my mass data backups. I consider their product and service to be mandatory and essential to pay for and use. It's very fast in terms of doing the initial data backup. I'm used to getting crazy fast upload and especially download speeds using CrashPlan because I have Verizon FiOS Quantum 75 MB/s symmetrical bandwidth with an unlimited data plan. I do strongly recommend CrashPlan+ over SpiderOak because of the inherent data privacy especially if you plan to share your master account with someone else so they can backup their data to your account. CrashPlan creates a unique global ID or GID for each PC so that no one is sharing data within the same master account. SpiderOak does not do this yet. Also, CrashPlan+ permits two-factor authentication using your own custom encryption key while SpiderOak does not do this. Both are memory hogs especially if you have a lot of data to backup to their data centers worldwide, but CrashPlan+ is more efficient when managing CPU and RAM consumption than SpiderOak in my previous experience.

---

### Post by Sasha_Aderolop on 2015-06-13
External hard drives can give you cheap storage
As we&#8217;ve mentioned above, storage prices decreased dramatically so that you can get a 100 or 200 GB hard drive at very affordable rates. Also, sizes have decreased making external hard drives extremely portable and lightweight. That way you can carry your external hard drive around making sure you have all the important files you need with you.

---

### Post by MartyBuntu on 2015-06-13
Some folks might be bandwidth cap limited, so for them I'd say go for local storage.
Also, your ISP's allotted upload speed might be painfully slow for uploading huge files to the cloud.

---

### Post by Old_Grey_Wolf on 2015-06-13
I prefer using an external HDD. For three reasons mostly: (1) it is fast, (2) I don't have to worry about the backup provider changing their policies, and (3) I have a large fireproof safe to store it in locally. If I didn't have the fireproof safe I might have considered online storage with encryption. I would have looked into storing it/them at a relatives house first.

---

### Post by QIII on 2015-06-13
One of my servers has 4 hot swap bays in a bay device.  It's on the way out in case of fire.  Pull four latches and pull out the drives on the way by.  Mrs QIII's machine and my main machine are imaged there nightly and our photos and such weekly.

---

### Post by Old_Grey_Wolf on 2015-06-13
> **QIII said:**
> One of my servers has 4 hot swap bays in a bay device.  It's on the way out in case of fire.  Pull four latches and pull out the drives on the way by.  Mrs QIII's machine and my main machine are imaged there nightly and our photos and such weekly.

What happens if you aren't there during the fire?

---

### Post by QIII on 2015-06-13
... or the burglary?

---

### Post by PhilGil on 2015-06-13
I use two USB hard drives: one that stays connected to my computer for nightly backups and one that I keep at the office and bring home for weekly backups. My most important files are also on Dropbox. Suspenders and a belt, people. You can never have too many backups.

---

### Post by QIII on 2015-06-13
If I get really ambitious, I suppose I could put compressed and encrypted files on my VPS.

---

### Post by Welly Wu on 2015-06-13
I too have a fireproof personal safe. I own a Sentry Safe. It requires two-factor authentication with a master key and combination to unlock and open it. I have a Transcend StoreJet USB 3.0 2.0 TB MIL-STD certified portable, rugged, encrypted hard disk drive. This is where I store my personal user data including my encryption keys and premium media library. I can easily put it inside my Sentry Safe for extra security, but it's not really that necessary. I chose CrashPlan+ because it is a solid product and service and I can easily afford it. I prefer CrashPlan+ because I know that my personal user data is always backed up to CrashPlan Central all of the time. That and I have an unlimited data plan and storage combination. Local backups using Deja-Dup are great as well. It's nice and easy and it's super fast using Super Speed USB 3.0. I think that cloud data backup services are the way to go and CrashPlan is leading the way in the industry. I still prefer portable, rugged, encrypted hard disk drives for the convenience of being able to put them inside my Sentry Safe. I don't like NAS technologies as I think that they are too slow compared to Super Speed USB 3.0. Direct attached storage seems to be simpler and faster along with being significantly less expensive than network attached storage.

If you are going to use a local backup strategy, then I recommend that you visit the CrashPlan website and download the free version of their software application and install and use it. The FLOSS GNU/Linux data backup software packages are okay, but a commercial solution like CrashPlan is going to be much better. If you decide to pay for CrashPlan+, then it's even better and it certainly is worth the money in my opinion and experience. Contact me if you need help installing, setting it up, and configuring it for Ubuntu 64 bit LTS GNU/Linux. I am a subject matter expert.

---

### Post by LastDino on 2015-06-14
I don't trust cloud services, but encrypting your data and storing is fair game. 

I only use 1TB passport drive that I've to take/store backups.

---

### Post by Welly Wu on 2015-06-14
The problem with local storage is multi-fold. First, you have a hard set amount of speed and capacity along with choosing a popular storage medium that will remain relevant for the foreseeable future. Second, you have the issue of protecting, defending, and securing your personal user data from natural disasters, unauthorized users, and catastrophic loss or theft of data. Third, you have to factor in the long term costs of utilizing best practices not only for data backup, but this also includes testing data restoration strategies on a regular basis. Fourth, you have to worry about data rot especially when using storage mediums and technologies that have a limited warranty period. Finally, you have to concern yourself with data erasure and secure wiping when you want to decommission an old PC or disk drive or storage medium. Let's not mention off-site data locations along with hot, cold, and warm backup sites.

Almost all of the cloud data backup and synchronization service providers use US government approved strong public encryption algorithms and secure hashing algorithms to protect the confidentiality, integrity, and availability of your data. Paying someone else to host your data make a lot more sense than taking ownership of the total costs and efforts to do it yourself over a long period of time. No single individual can afford the nearly unlimited data capacity and the services that a reputable company can offer to its' customers worldwide.

Most of the FLOSS data backup software packages available in the main Ubuntu software repository don't compare to commercial vendors. You get what you pay for most of the time folks. The more difficult aspect of FLOSS data backup software packages is picking the right solution that meets some of your needs some of the time. Most of the popular choices don't even feature the capability to test a simulated data restoration job once your initial data backup is complete. Without this, it's a crap shoot because you assume that it should work when you need to restore your data at a critical time.

Remember, when you use local backup only, you become a big fat target of opportunity for others. For most home consumers, this is not necessarily their first concern. Also, local data backups and storage technologies or mediums are targets of attackers especially stealthy and specifically targeted advanced persistent threats. Once you connect your drive to your PC using direct attached or network attached storage, it is accessible to you and your attacker. Private individuals only have a limited amount of technical skill sets, experience, and resources to defend their PCs and personal user data from a sophisticated attacker with nearly unlimited resources and time.

Most people don't even choose to purchase or use a personal safety deposit box at their local bank branch, yet this remains an effective and cost effective way to secure your local data backups and storage mediums available to the general public. If this option is not available, then cloud data backup and synchronization service providers can step in with multi-level, multi-layered, defense in depth data backup and protection services at a cost. Furthermore, most people don't choose to spread out their data backups over multiple RAID disk arrays and if they do, then they keep it in their offices or homes with their PCs thus negating the effectiveness of off-site data backups. This makes you a larger target of opportunity.

Another important consideration to take into account is that it is not technically difficult to re-purpose a malware attack designed for Apple and Microsoft customers to target GNU/Linux or BSD users. One of these days, GNU/Linux is going to gain more market share and popularity which means that attackers and malware authors are going to recode their payloads to target our communities and our data especially with cryptolocker malware. DAS and NAS local or remote storage solutions do not protect you from this attack vector. This is not a real issue today, but cloud data backup service providers go to great lengths to mitigate this specific attack vector to protect your personal user data for Apple and Microsoft customers if they choose to pay for their services.

The worst case scenario is doing what I do which is to use a single portable hard disk drive to store the majority of my personal user data. Not only is this a single target and point of failure, but it is risky. Yet, I have strong multi-level, multi-layer, and defense in depth security in my apartment. I have the master key to my apartment doors and locks. I have a Schlage Camelot door lock for my bedroom that requires another master key and either one of two six digit PIN codes to unlock my bedroom door. I have a Sentry Safe that requires another master key and combination to unlock the safe. I also have CrashPlan+ Family Plan for remote off-site data backups and restoration. Finally, I have a safety deposit box at my local PNC Bank branch located less than 0.40 miles from my apartment and I have the master keys. I also have Kensington desktop and notebook PC desk anchors, locks, and thick anti-theft cabling to lock down my PCs in my bedroom. This is going overboard, but I understand the unique and valuable data that I own beyond mere dollars and cents. The most important layer is CrashPlan+ Family Plan. It is the cornerstone of my security strategy. I enabled my master password to open the GNU/Linux desktop client. I set a custom encryption key for each PC that I own. I use Private Internet Access VPN using AES 256 bits and SHA-256 along with ECC 521 bits to encrypt my network traffic at all times. I monitor my system logs twice daily. I use Bitdefender Anti-Virus for Unices Free. I already set a simple and effective Ubuntu Uncomplicated Firewall set of rules. I installed and enabled Novell AppArmor profiles. I set the ownership rules and file permissions correctly for each important disk drive, folder, and file. I use GnuPG and I set my custom preferences in the gpg.conf file and I installed the extra strong public ciphers and secure hashing algorithms that I want to use. I installed seahorse-nautilus to enable easy file encryption and decryption using Nautilus. I use Veracrypt 1.0F-2 to encrypt my unique encryption keys and sensitive data and I enabled two-factor authentication using a unique key file. I use LastPass Premium and I own several Yubico Yubi Keys for strong two-factor authentication for my credentials and secure notes. I use KeePass 2 as a backup credentials management system just in case LastPass fails. I test my master passwords using various online and secure password strength analysis websites. I print my master credentials on paper and I keep them locked inside my Sentry Safe in my bedroom and in my safety deposit box at PNC Bank. I also have a cross cut shredder in my bedroom to destroy important paperwork and documents.

Yet, I know that local backup has more disadvantages than advantages especially in this day and age. It requires more effort and costs. It takes more skill and time including planning ahead. Local backups don't evolve to meet new threats and attack vectors effectively over time. In the end, local backups cost me more time and money especially when I decide to purchase more local storage technologies and disk drives over time. Each disk drive and volume is another target of opportunity and additional cost for me.

This is why I prefer cloud based backup service providers by a wide margin. It's usually a lot simpler, less complex, cheaper, and better in the long run.

I am writing with a specific target audience: the average PC user regardless of which desktop or mobile operating system that they use at home or at work. In this context, local storage has many more disadvantages than pros weighing against it. My experience is that most people simply copy and paste their important folders and files to another disk drive and they don't encrypt it twice at a minimum if it is important or sensitive. In other words, they don't use FLOSS technologies to safeguard their personal user data like GnuPG, Veracrypt, 7-ZIP with AES 256 bits, or even put a password on their data backups. Remember, the problem with classic cryptography is that it is password based. Passwords are the weakest form of data security. A nation state has the technical subject matter experts, supercomputers, and resources to attack password based encryption systems that don't have multi-factor authentication built-in and they can crack it given enough time and money. Another important consideration is that all hard disk drives and solid state disks will eventually fail. Most hard disk drives fail after five years of usage. Solid state disks suddenly fail without warning. Ask Linus Torvalds about his old Apple MacBook Air and its' internal SSD failure himself. Most people can't afford to own multiple PCs either. Most notebook PCs have a single internal disk drive which is another single point of failure. Most GNU/Linux users choose the defaults and they don't set up a custom partitioning scheme or layout which is another big problem. The list goes on and on with regard to local based storage data backups. Once your PC or your disk drive goes belly up, that's it for most people and they begin to lose precious data because they did not pay their money for a cloud data backup service provider after something catastrophic has happened. This is the inherent problem: most people assume PCs are appliances and they think and hope that it will last them for several years with no problems. Once something bad happens, it's already too late if you rely solely on local data storage and backup.

Another important thing that I have learned is the value of available and compatible spare PC parts. I have a PC technician tool kit. I have two identical parts for RAM and internal and external storage. I actually own two Crucial MX100 SATA-III 6 GB/s 256.00 GB solid state disks for my ZaReason Zeto desktop PC and two Crucial M550 SATA-III 6 GB/s 1.0 TB solid state disks for my desktop PC along with two Transcend M.2 42 mm NGFF SATA-III 6 GB/s 256.00 GB solid state disks for my Lenovo IdeaPad Y510P notebook PC. I plan to purchase two Seagate Samsung SpinPoint M9T 2.5" 9.0 mm SATA-III 6 GB/s 2.0 TB 5,400 RPM laptop hard disk drives for my notebook PC later this year. I also have four 240 pin DIMM RAMS for my desktop PC of which total 32.00 GB. I also have four Crucial Ballistix Sport 16.00 GB 204 pin SO-DIMM RAM chips for my notebook PC. All of my PCs require dual internal disk drives just in case one fails. I used disk cloning software to create a master image and copy it on all of my internal disk drives for both PCs. If one should fail, then I can swap in the replacement and get myself back up and running. I store my spare PC components inside my Sentry Safe or safety deposit box in its' original OEM packaging including anti-static bags.

It costs me more time and money, but I'm well prepared for a disaster or emergency. Still, CrashPlan+ is the best choice for me. Local backups need to be combined with cloud data backup service providers.

---

### Post by TechTorpedo.com on 2015-06-15
One word of warning, i have tried to sync services, and they are useless. Google drive synced my data, and then i couldn't get access to it after i wiped my hard drive and reinstalled OS, 

Now i have offline backup, and once a month just do a full hardrive image to drop box

---

### Post by Welly Wu on 2015-06-15
There's a big difference between synchronization and data backup. Synchronization doesn't backup data and it's generally more difficult to restore your data using this type of cloud sync service after reinstalling your desktop OS. Data backup is designed for full restoration of personal user data and it usually does not include the OS folders and files. SpiderOak is a one stop cloud sync and data backup provider with secure file sharing built-in. It offers the complete package and zero knowledge policy for privacy, but you'll pay more for it because it is based on tiered data pools. There is no unlimited data pool or plan with SpiderOak. The other thing to note is that if you share your master account with someone else, then they have access to your data as there is no separation of personal user data within a master SpiderOak account among different users and PCs. SpiderOak also takes a longer period of time to resume its' normal operations after you reinstall your desktop OS and the SpiderOak desktop client and it repeats this long 10 step set up and synchronization process for each PC that you choose to reinstall a desktop OS. So, it takes a heck of a lot of time with each additional MB or GB that you've already uploaded to your data pool with SpiderOak. But, it's the only cloud provider that offers everything if you're willing to pay a premium. SpiderOak is tested to work with complete data restoration jobs after you reinstall your desktop OS on a PC or multiple PCs. It's essentially set and forget and press a few buttons and wait.

If I need to restore my data, then I'm using my portable hard disk drive because it's much faster and it's free of charge if I continuously edit my data and prune it over time to fit within the maximum capacity. CrashPlan+ is like paying for insurance. I hope that I never have to need to use it to restore my data, but it's there just in case of natural disasters, loss, theft, malfunction, or failures. That's how you should think about cloud storage providers. It's paying for data insurance and peace of mind.

---

### Post by mastablasta on 2015-06-16
it the restoring that is the issue. backup up is easy. so many options.

so far I sucessfully restored 2 old disks to new ones. but last one failed for no good known reason really. ok the last image I knew might be corrupted but previous one was supposed to be good but was not. I am now going to setup incremental backups. see how that works...

---

### Post by Welly Wu on 2015-06-19
I have found that many of the free GNU/Linux backup software packages to corrupt my backups over time. Some backup software don't make it easy to restore my data either. This is why I rely on CrashPlan+ because the data restoration process is guaranteed to work with CrashPlan Central. Using CrashPlan without paying for access to CrashPlan Central is also a good free choice compared to the free GNU/Linux backup packages because it is guaranteed to work including data restoration. With CrashPlan+ 4.2.0 and above, AES 256 bits is now the default encryption cipher used which means that state and federal agencies can now use CrashPlan to backup US government data up to the top secret level. Most of the other free GNU/Linux backup software don't use AES 256 bits as the default encryption cipher unless you are willing to read the manual and reconfigure the configuration text files to use it by default like the GnuPG gpg.conf file for Deja-Dup or GPG. I think that the free GNU/Linux data backup packages are all bad across the board compared to CrashPlan+. It's not worth risking the integrity of your data backups and the capability to restore your own data by using them.

---

### Post by CharlesA on 2015-06-19
I haven't had rsync or rdiff-backup fail me. *shrugs*

---

### Post by PJs Ronin on 2015-06-20
I'm sure there are wonderful reasons why you'd want to back up to on-line storage, I just can't think of them so I use local.

Hard drives are dirt cheap and I back up my entire system using FSArchiver to one of these HDs every month.   I take the HD to a lady friend and over coffee she puts the drive (weather/insect sealed) into her garden shed.   The conversation is good, the coffee is great and it gets me out of the house for an hour.

---

### Post by mamamia88 on 2015-06-20
> **PJs Ronin said:**
> I'm sure there are wonderful reasons why you'd want to back up to on-line storage, I just can't think of them so I use local.

Hard drives are dirt cheap and I back up my entire system using FSArchiver to one of these HDs every month.   I take the HD to a lady friend and over coffee she puts the drive (weather/insect sealed) into her garden shed.   The conversation is good, the coffee is great and it gets me out of the house for an hour.

First off with cloud services like dropbox my photo backup is done automatically after snapping a picture on my phone.  This in turn gives me a local copy which i can then easily backup.  Also files in my dropbox can be pulled up on my phone without actually having a copy on my phone.  I do keep local backups using a free program called free filesync it makes everything easy but, the simplicity of the cloud is a huge selling factor for me.  I don't pay for it though I got 50gb free with my phone

---

### Post by Welly Wu on 2015-06-20
Cloud data backup service providers provide you with incredibly high uptime, availability, and reliability with carefully tested software applications that are compatible with your desktop or mobile operating system. Local storage requires that you choose a compatible and universal enough file system and this gets more complicated in a heterogeneous mixture of different devices, operating systems, file systems, and specific user requirements for access control, encryption, backup sets, etc. It is not easy or convenient to share your data and someone else's data on a single hard disk drive and if your user base grows, then it gets more complicated and the options become more limited. It also gets to be more expensive to keep purchasing more local storage technologies and drives to custom tailor a hardware and software configuration for multiple users especially if some of the users require remote access in a bidirectional flow of network traffic. At some point in time, the John and Janes of this world relying on local storage like external hard disk drives is going to meet the limitations of the interface technology or bus and the finite capacity it provides or it will fail over time because it is a mechanical hard disk drive.

Look, I must have worked for the US National Security Agency for too long of a period of time to even fathom of these different and unclassified set of challenges and opportunities that define online versus external HD storage options and products. The biggest problem with storing your data even if it is encrypted with someone whom you trust (for now) is that you give physical access to your disk drive under the temporary ownership and possession of someone else without considering if this could be a bad actor or potential risk to your data in the future. Not everybody is a spy versus spy scenario, but what if someone who holds onto your hard disk drive loses it or it gets stolen from them? These are more pressing and fundamental challenges that external HDD present that cloud data backup providers have addressed and mitigated with their products and services.

I will disclose this because I think it is relevant. I have three trusted friends of which two I visit almost daily at their apartments located very close by. I would never hand over my Transcend StoreJet portable encrypted hard disk drive to them for safekeeping...ever. Obviously, I have far more technical skill sets and experiences because I provide them with free technical support for Microsoft Windows 7 and 8.1 along with Ubuntu 64 bit LTS GNU/Linux at their pleasure and I show up on demand if they have the slightest question about how to do something on their PCs. Why don't I trust them with my personal user data? I know of other people and have a few personal experiences with doing so in my past professional life and the problems that ensued as a result even among close friends and colleagues. Requesting that your personal user data be returned upon request in a timely manner without having a verifiable custodial chain of ownership and transportation is dangerous because you have no idea if someone could have either access, modified, deleted, or lost your data if you don't have physical possession of it almost all of the time.

The other problem with FLOSS GNU/Linux data backup software is that end users have little say over features requests or even the active development or maintenance of the chosen software package over a long period of time since there is no one that you can legally sue in court if your FLOSS data backup software is no longer available. Maybe I made a huge mistake in assuming that a significant number of Ubuntu users would rather choose a FLOSS data backup software with a user friendly interface like Deja-Dup, Back in Time, or LuckyBackup. Now, compare that with a commercial solution like CrashPlan+ feature for feature and it becomes clear to me that external HDD are not going anywhere fast and they don't adapt and scale to meet unique challenges and threats too well.

I hope that this is what you take away from my comments. When you choose an external HDD and a FLOSS GNU/Linux data backup package and you loan it to someone else, you are in essence transferring temporary ownership and custodial rights and responsibilities to someone else without any way of knowing what will happen once you and your party part ways. Thus, the nature and the quality of the relationship is more paramount than the external HDD or your personal user data. If that is the case, then you perhaps should not need a data backup software package and I would suggest that copying and pasting your data to a target external HDD would be simpler, faster, and easier.

I have never deliberately decided to make someone else's external disk drive and their personal user data unavailable to them in the past especially if they were a close friend of mine at the time. However, I have made one mistake of loaning my own portable encrypted hard disk drive to a close friend and they plugged it into their PC and somehow my data got formatted or overwritten or deleted and some or all of the content became unavailable to me. It does still happen. It also happens to be the case that you may be working with multiple and similar looking external disk drives and you make a mistake and you make some or all of the data on that drive unavailable to you and that was one of your master copies. Hence, this is the problem with local storage products in that they introduce too much risk to the data by human beings that have physical access, control, or possession of each one. All of the disk manufacturers today and tomorrow can not sell their products to be stupid proof. The other salient topic is if you need to access a specific disk drive and you need to destroy or decommission a PC containing such a partition or volume discreetly. For a significant number of people, they lack the technical skills, experience, and patience to know how to securely wipe a hard disk drive which is different from securely erasing a solid state disk and the techniques involved are distinct from each other. What if you need to get rid of data and you have multiple internal and external disk drives of which some are not in your physical possession or control right now? This is why external HDDs are a bad choice as a sole means of data backup. They must be combined with cloud data backup to offer the tiniest modicum of safety, privacy, and redundancy. Ever get on a plane and your hard drive gets lost, stolen, or damaged? It happens. Ever try to connect, mount, and use an external hard disk drive on a vehicle that has a couple bumps in the road? It happens and hard drives need to stay stable position during access and usage.

How many people choose to buy conventional external hard disk drives without even considering MIL-STD certified versions for a couple of more bucks? I own a Transcend StoreJet MIL-STD USB 3.0 2.0 TB portable, encrypted, rugged hard disk drive that I usually keep locked inside my Sentry Safe which is then protected by my Schlage Camelot door lock inside my apartment doors that are usually closed and locked as well as the front door that requires another master keys that stay closed and locked. When I plug in my hard disk drive, I put it on my desk and I don't touch it while I access it even though I know this one in particular can handle a drop or two on hard surfaces. Hard disk drives are not designed for challenging environments in tough terrain while being plugged in and used at the same time.

The most common scenario is that someone finds a disk drive and they plug it into their PCs at work or at home. Then, their work or home PCs get infected with malware. What if it's your external hard disk drive that someone else finds? What if you plug in your external hard disk drive on a PC that is infected because it was around at the time and it was convenient or it was buddy's PC and he said it was cool with him.

Finally, what if you encrypted your external hard disk drive and the master password doesn't let you access your personal user data? Software based encryption can be defeated with both hardware and software attack vectors. External hard disk or thumb drive that features both robust hardware and software based security technologies and mitigation techniques cost big bucks and they usually store critical and confidential data. Own one of these and you are a big target to someone that recognizes the brand of your product model.

Today, external hard disk drives usually come in at a minimum of 500.00 GB and they go up to 12 TB or more. There's a brand and product model to suit almost any customer and their needs on the market. If that hard disk drive goes belly up, then you stand to lose some or almost all of your personal user data. Do you realize how expensive it is to lose 500.00 GB of your own data? Some data are unique and they can not be recovered period. That's the problem with external hard disk drives. A single failure costs you several dozen terabytes or more of your own data and it might just not be your fault at all. It's incredibly time consuming and expensive to recover data per gigabyte by professional companies that specialize in data recovery or extraction. If your external hard disk drive is encrypted and you put a strong passphrase on it, then it becomes almost impossible if the encrypted volume header is damaged and you failed to make a backup needed to restore it. Most data recovery companies don't specialize their work for GNU/Linux customers because the demand for home consumer data recovery business is too low or they'll charge you more money per hour or per gigabyte as their service fees.

When you fail to prepare, you are prepared to fail.

---

### Post by mamamia88 on 2015-06-22
> **Welly Wu said:**
> Cloud data backup service providers provide you with incredibly high uptime, availability, and reliability with carefully tested software applications that are compatible with your desktop or mobile operating system. Local storage requires that you choose a compatible and universal enough file system and this gets more complicated in a heterogeneous mixture of different devices, operating systems, file systems, and specific user requirements for access control, encryption, backup sets, etc. It is not easy or convenient to share your data and someone else's data on a single hard disk drive and if your user base grows, then it gets more complicated and the options become more limited. It also gets to be more expensive to keep purchasing more local storage technologies and drives to custom tailor a hardware and software configuration for multiple users especially if some of the users require remote access in a bidirectional flow of network traffic. At some point in time, the John and Janes of this world relying on local storage like external hard disk drives is going to meet the limitations of the interface technology or bus and the finite capacity it provides or it will fail over time because it is a mechanical hard disk drive.

Look, I must have worked for the US National Security Agency for too long of a period of time to even fathom of these different and unclassified set of challenges and opportunities that define online versus external HD storage options and products. The biggest problem with storing your data even if it is encrypted with someone whom you trust (for now) is that you give physical access to your disk drive under the temporary ownership and possession of someone else without considering if this could be a bad actor or potential risk to your data in the future. Not everybody is a spy versus spy scenario, but what if someone who holds onto your hard disk drive loses it or it gets stolen from them? These are more pressing and fundamental challenges that external HDD present that cloud data backup providers have addressed and mitigated with their products and services.

I will disclose this because I think it is relevant. I have three trusted friends of which two I visit almost daily at their apartments located very close by. I would never hand over my Transcend StoreJet portable encrypted hard disk drive to them for safekeeping...ever. Obviously, I have far more technical skill sets and experiences because I provide them with free technical support for Microsoft Windows 7 and 8.1 along with Ubuntu 64 bit LTS GNU/Linux at their pleasure and I show up on demand if they have the slightest question about how to do something on their PCs. Why don't I trust them with my personal user data? I know of other people and have a few personal experiences with doing so in my past professional life and the problems that ensued as a result even among close friends and colleagues. Requesting that your personal user data be returned upon request in a timely manner without having a verifiable custodial chain of ownership and transportation is dangerous because you have no idea if someone could have either access, modified, deleted, or lost your data if you don't have physical possession of it almost all of the time.

The other problem with FLOSS GNU/Linux data backup software is that end users have little say over features requests or even the active development or maintenance of the chosen software package over a long period of time since there is no one that you can legally sue in court if your FLOSS data backup software is no longer available. Maybe I made a huge mistake in assuming that a significant number of Ubuntu users would rather choose a FLOSS data backup software with a user friendly interface like Deja-Dup, Back in Time, or LuckyBackup. Now, compare that with a commercial solution like CrashPlan+ feature for feature and it becomes clear to me that external HDD are not going anywhere fast and they don't adapt and scale to meet unique challenges and threats too well.

I hope that this is what you take away from my comments. When you choose an external HDD and a FLOSS GNU/Linux data backup package and you loan it to someone else, you are in essence transferring temporary ownership and custodial rights and responsibilities to someone else without any way of knowing what will happen once you and your party part ways. Thus, the nature and the quality of the relationship is more paramount than the external HDD or your personal user data. If that is the case, then you perhaps should not need a data backup software package and I would suggest that copying and pasting your data to a target external HDD would be simpler, faster, and easier.

I have never deliberately decided to make someone else's external disk drive and their personal user data unavailable to them in the past especially if they were a close friend of mine at the time. However, I have made one mistake of loaning my own portable encrypted hard disk drive to a close friend and they plugged it into their PC and somehow my data got formatted or overwritten or deleted and some or all of the content became unavailable to me. It does still happen. It also happens to be the case that you may be working with multiple and similar looking external disk drives and you make a mistake and you make some or all of the data on that drive unavailable to you and that was one of your master copies. Hence, this is the problem with local storage products in that they introduce too much risk to the data by human beings that have physical access, control, or possession of each one. All of the disk manufacturers today and tomorrow can not sell their products to be stupid proof. The other salient topic is if you need to access a specific disk drive and you need to destroy or decommission a PC containing such a partition or volume discreetly. For a significant number of people, they lack the technical skills, experience, and patience to know how to securely wipe a hard disk drive which is different from securely erasing a solid state disk and the techniques involved are distinct from each other. What if you need to get rid of data and you have multiple internal and external disk drives of which some are not in your physical possession or control right now? This is why external HDDs are a bad choice as a sole means of data backup. They must be combined with cloud data backup to offer the tiniest modicum of safety, privacy, and redundancy. Ever get on a plane and your hard drive gets lost, stolen, or damaged? It happens. Ever try to connect, mount, and use an external hard disk drive on a vehicle that has a couple bumps in the road? It happens and hard drives need to stay stable position during access and usage.

How many people choose to buy conventional external hard disk drives without even considering MIL-STD certified versions for a couple of more bucks? I own a Transcend StoreJet MIL-STD USB 3.0 2.0 TB portable, encrypted, rugged hard disk drive that I usually keep locked inside my Sentry Safe which is then protected by my Schlage Camelot door lock inside my apartment doors that are usually closed and locked as well as the front door that requires another master keys that stay closed and locked. When I plug in my hard disk drive, I put it on my desk and I don't touch it while I access it even though I know this one in particular can handle a drop or two on hard surfaces. Hard disk drives are not designed for challenging environments in tough terrain while being plugged in and used at the same time.

The most common scenario is that someone finds a disk drive and they plug it into their PCs at work or at home. Then, their work or home PCs get infected with malware. What if it's your external hard disk drive that someone else finds? What if you plug in your external hard disk drive on a PC that is infected because it was around at the time and it was convenient or it was buddy's PC and he said it was cool with him.

Finally, what if you encrypted your external hard disk drive and the master password doesn't let you access your personal user data? Software based encryption can be defeated with both hardware and software attack vectors. External hard disk or thumb drive that features both robust hardware and software based security technologies and mitigation techniques cost big bucks and they usually store critical and confidential data. Own one of these and you are a big target to someone that recognizes the brand of your product model.

Today, external hard disk drives usually come in at a minimum of 500.00 GB and they go up to 12 TB or more. There's a brand and product model to suit almost any customer and their needs on the market. If that hard disk drive goes belly up, then you stand to lose some or almost all of your personal user data. **Do you realize how expensive it is to lose 500.00 GB of your own data?** Some data are unique and they can not be recovered period. That's the problem with external hard disk drives. A single failure costs you several dozen terabytes or more of your own data and it might just not be your fault at all. It's incredibly time consuming and expensive to recover data per gigabyte by professional companies that specialize in data recovery or extraction. If your external hard disk drive is encrypted and you put a strong passphrase on it, then it becomes almost impossible if the encrypted volume header is damaged and you failed to make a backup needed to restore it. Most data recovery companies don't specialize their work for GNU/Linux customers because the demand for home consumer data recovery business is too low or they'll charge you more money per hour or per gigabyte as their service fees.

When you fail to prepare, you are prepared to fail.
I have an external harddrive connected to my desktop.  I use a program when I'm bored that parodies all my important folders on my computer onto the external drive.  The odds of both dying at the exact same time are very unlikely. If one dies I replace it and get right back up and running in no time at all.   I keep 3 copies of all my data and it takes me about 30 seconds when I'm bored sitting at my computer to do so.   I like cloud storage but, if i had to pay for it I probably wouldn't.

---

### Post by Matejko on 2015-06-24
In my opinion best way is making backup on online-storage service. But not always... It depends of data which you have to archive. I'm making a lot of videos - thousands of gigabytes of video files and stills. It is heavily problematic to send it via my poor network connection (asymmetric - 15DL/2UP). But if your data is mostly little files (but of course important), ex. documents, data sheets, databases etc. you should choose online-backup method.


If local - remember to make copy always on three separate devices and store it in different localisation, just for safety.

---

### Post by tdmeskimo on 2015-07-09
Hi, I see this thread is a few weeks old, but my backup is a FreeNAS box.  I have a 3 TB hdd in one of my desktops, and then sync my 3 Tb with my FreeNAS.  Sometimes I save directly to my FreeNAS, but when I sync both my 3 TB HDD and FreeNAS are in sync.  As you can see I prefer a local backup, my only use for a Dropbox which I have but need to move some file would be for Dropbox on my android tablet.  then I can do what ever on my desktop and sync to my tablet!  No paid service for backing up for me.  :-)

---

### Post by tdmeskimo on 2015-07-09
Hi, I see this thread is a few weeks old, but my backup is a FreeNAS box.  I have a 3 TB hdd in one of my desktops, and then sync my 3 Tb with my FreeNAS.  Sometimes I save directly to my FreeNAS, but when I sync both my 3 TB HDD and FreeNAS are in sync.  As you can see I prefer a local backup, my only use for a Dropbox which I have but need to move some file would be for Dropbox on my android tablet.  then I can do what ever on my desktop and sync to my tablet!  No paid service for backing up for me.  :-)

---

### Post by gordintoronto on 2015-07-10
My solution is an external hard drive enclosure, and then I have a couple of large drives for it, which I swap back and forth, so there is never a time when I don't have some form of backup. For current small projects, I use Dropbox. It would take weeks, and many dollars, to back up my entire hard drive to Dropbox.

At the office, we have a dedicated "backup computer" which has a swappable internal drive, and we back up the server to it every night. (Bi-weekly full backups, then daily incrementals.) At the end of the month we put in a new drive and take the old one off-site. Because of the type of business, we do not reuse drives. We used to use tape, but backing up across the network runs five times as fast, and media costs a third as much -- and there is some hope that we could read the backup 10 years from now, which is really unlikely with tape. (Mostly because we have switched to a different tape format about every seven years.)

---

### Post by Welly Wu on 2015-07-18
I configured my Verizon FiOS Quantum Gateway Router and CrashPlan+ GNU/Linux 4.2.0 64 bit desktop clients to enable both my Lenovo IdeaPad Y510P and ZaReason Zeto PCs to backup to each other. Both of my PCs have dual internal disk drives of which the primary one is a SATA-III 6 GB/s 256.00 GB solid state disk where I installed Ubuntu 14.04.2 64 bit LTS GNU/Linux, my favorite software applications, packages, libraries, and dependencies, and I store my private user data. The second internal disk drive is either a 1.0 TB laptop hard disk drive or a Crucial M550 SATA-III 6 GB/s 1.0 TB solid state disk in my notebook and desktop PCs respectively. I configured CrashPlan+ to backup my private user data to the second internal disk drive as an extra destination. So, both PCs backup to three destinations including CrashPlan Central, the second internal 1.0 TB disk drive, and to each other automatically. This helps to ensure the integrity, redundancy, and safety of my private user data at all times. I keep a copy of my private user data on my Transcend StoreJet USB 3.0 2.0 TB MIL-STD certified portable, rugged, encrypted hard disk drive just in case. I usually put it inside my Sentry Safe so that it stays offline. Backups are important!

---

### Post by Welly Wu on 2015-07-19
Earlier this morning, I finally got CrashPlan+ to backup to my Transcend StoreJet portable, rugged, encrypted hard disk drive. So, I now have a fourth destination for my backups. It's fast as heck. It took less than one hour to backup several hundreds of gigabytes to the PCs and internal disk drives along with the portable external hard drive. My ZaReason Zeto desktop PC backed up over 1.2 TB of data from the primary Crucial MX100 SATA-III 256 GB SSD to the Crucial M550 SATA-III 6 GB/s 1.0 TB SSD in less than thirty minutes! I was getting crazy fast data backup performance.

---

### Post by Skaperen on 2015-07-20
my 2 TB external USB _3.0_ drive is *bootable* just in case i might be limited to one device while restoring.  i use _rsync_ in a big script to make *[reverse-increment]("https://en.wikipedia.org/wiki/Incremental_backup#Reverse_incremental") style* backups

---

