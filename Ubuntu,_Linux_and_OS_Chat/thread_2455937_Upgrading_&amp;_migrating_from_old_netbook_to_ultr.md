---
title: "Upgrading &amp; migrating from old netbook to ultrabook: advice &amp; recommendations please"
date: 2020-12-31
forum: Ubuntu, Linux and OS Chat
---

### Post by full-o-beans on 2020-12-31
Hi all

This is my first posting on this forum, and I'd be really grateful for the experience of other forum users in answering the following questions.

I have enjoyed using Ubuntu Xenial and Peppermint 6 on a Samsung N220 Plus netbook (32 bit Intel 686 processor 200 MHz, 2 GiB RAM, 128 MiB HDD) for many years.


I have found Peppermint to be an excellent choice for my old and under-powered but reliable hardware: it is responsive, and very intuitive to use. Although I've looked at upgrading Peppermint, I prefer the simple interface of Peppermint 6 to more recent releases.


I am planning to buy a much more powerful 'ultrabook': HP ENVY 13-ba0010na (64 bit Intel i7 1.8 GHz with 4 cores, 16 GiB RAM, 1 TiB SSD); as this will have the extra power to allow me to process and edit video footage.


I want to migrate all my data files in my /~ directory (backed up using the Ubuntu Backup utility), and apps and settings (backed up using Aptik) to the new ultrabook.


I am not interested in having a dual boot system (I've got a couple of useful Windows apps, like Adobe suite; but these don't justify filling the SSD with Windows).
I intend to remove the pre-installed version of Windows 10 and do a complete 'clean' install of an Ubuntu distro. 


I have some questions regarding compatibility and migrating: 


1.
Peppermint 6 has all the functionality that I need at present.  
I'm sure that the new hardware will be impressively fast regardless of which distro I use, but I'm not particularly interested in installing a bigger slower distro with more bells and whistles: I'd rather have a simple GUI (which ideally has a similar feel to the Peppermint 6 GUI) and enjoy the improved performance to the max. 
The important thing is that the new distro will need to have the correct drivers to take full advantage of the new hardware.
Is Peppermint still the best option for my new hardware, or is there an alternative lightweight distro which would be a better choice to get full compatibility and maximum utilisation of the new hardware?


2.
I have seen a lot of discussion on the forums regarding whether it better to create separate partitions for the operating system and files (using GParted) prior to installing the operating system; as this makes it easier to subsequently upgrade, change, or completely re-install my operating system without risking losing / damaging my files and settings.
However I believe that many distro installation packages now provide this functionality automatically more reliably without the user having to create different partitions manually.
I still consider myself a Linux newbie and want the simplest and safest 'idiot-proof' approach which will allow for painless future upgrades, re-installation, or installation of different distros.
Would you recommend creating new partitions manually before installing my new distro, or will the installation package provide this option?
If manual partitions, please suggest details of partitions and swap file sizes etc..


3.
I'll be migrating my apps and settings from a 32 bit system to a 64 bit system.
Will Backup and Aptik take care of this automatically ? 
If not, is there a better option for migrating and updating my apps to 64 bit versions automatically (I've got several thousand apps and packages installed, so manually installing all of these will be a pain!).


I have contacted HP's technical support helpline regarding compatibility of the HP Envy 13 with Ubuntu, but they tell me that they have no experience of Linux OS, and are unable to offer any advice.

Many thanks in anticipation

With best wishes for the New Year

---

### Post by dino99 on 2020-12-31
Welcome here

i understand you have a great experience with Pippermint (which i dont) but your future device will have plenty room to install what you want. Indeed the Pippermint forum is the right place for your questions. With recent hardware its a good idea to choose a recent OS too to have the kernel supporting all the embeded chipsets. So download a recent iso and let the installer doing a fresh install. Then you will be able to copy/paste or import your saved data; no matter if they come from a 32 or 64 bits system or whatsoever.

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[http://cdimage.ubuntu.com/ubuntu/daily-live/current/](http://cdimage.ubuntu.com/ubuntu/daily-live/current/)         Choose the amd64 image for the latest in progress release (which i daily use)

---

### Post by rsteinmetz70112 on 2020-12-31
You should migrate to a 64 bit OS 32 bits will be gone soon. That will require a new installation of the OS. You will then need to install whatever applications you need beyond the standard ones, and set the configurations. If your data is in /home (make /home a separate partition) or some other discrete location backing it up and restoring it is easy. I also typically create a filesystem called /files for shared or other stored files. In the olden days when disks were small and expensive separate filesystems were set up for other things. I sometimes still set up a small /temp filesystem because sometimes a process can go crazy and fill the logs or other directories with crazy amounts of stuff. I have seen it fill  / completely causing all sorts of problems, but that's not commonly done today.

What may be more challenging is configuring your apps to match your previous system, especially due to changes in the system since Xenial. Xenial only has a short time before EOL.  I 

You may want to install Xenial amd64 on your new system then configure it then do-release-upgrade. That way you can directly copy your existing configuration files. All of this assumes that you have made significant configuration changes, which I avoid unless absolutely necessary. If you haven't done a lot of configuration I find it's usually easier to just start over and fix the things you can't live with.

Feel free to ignore my rantings :cool:

---

### Post by CatKiller on 2020-12-31
> **full-o-beans said:**
> I have contacted HP's technical support helpline regarding compatibility of the HP Envy 13 with Ubuntu, but they tell me that they have no experience of Linux OS, and are unable to offer any advice.

FWIW, if you don't have your heart particularly set on the HP, Dell sell ultrabooks with Ubuntu pre-installed: the XPS 13 Developer Edition.

---

### Post by mikewhatever on 2020-12-31
It looks like Peppermint 6 is old and unsupported. It has been a bad idea to use it until now, and I hope you migrate to something else asap.
I am also not sure why you ask about Peppermint OS here on Ubuntu Forums. Peppermint has a dedicated forum: [https://forum.peppermintos.com/](https://forum.peppermintos.com/).

---

### Post by CatKiller on 2020-12-31
> **full-o-beans said:**
> I'd rather have a simple GUI (which ideally has a similar feel to the Peppermint 6 GUI) and enjoy the improved performance to the max. 

From reading up on Peppermint, it seems they started with Lubuntu and then mix-and-matched liberally from the applications included with Xubuntu and Ubuntu Mate. Any of those would make a good starting point - you can try them out from the live installer to see which you prefer - and then do your own mixing and matching.

---

### Post by full-o-beans on 2020-12-31
Many thanks all for your speedy and helpful advice - all greatly appreciated.

@catkiller: Many thanks for the suggestion of the Dell Ultrabooks - will definitely look into this option !

@dino99 & mikewhatever - Completely agree that my upgrade from Peppermint 6 is long overdue ;-)
Apologies if I seem to have posted in the wrong forum: To clarify, I'm not looking to stick with Peppermint for my new distro if something better is out there. Ubuntu seems to be the most widely supported version of Linux, and is very user-friendly for newbies like myself. Trouble is with so many distros to choose from I'm not sure which would be the best option for compatibility with the HP Envy (for example, which distros support HPs touchscreen and audio drivers ?); hence grateful for any personal experience / recommendations.

@rsteinmetz70112: Many thanks for your recommendation to urgently upgrade to 64 bit (unsupported on my ancient 32 bit  Samsung netbook): your trick of installing Xenial amd64 initially and then upgrading with do-release-upgrade is a really neat workaround, but as you say, it might be safer to start over. 

Will Aptik be any help at all in automating the process when migrating from a 32 to 64 bit platform?
I'm hoping if I install and run the latest release of Aptik on my new 64 bit machine it might be able to open the backup list of Apps created on the old 32 bit Samsung Netbook, but then download and and install the latest 64 bit versions of the apps rather than 32 bit versions of the apps...If so, this would save me a lot of time downloading and installing apps manually.

Thanks also for your advice re: creating /home and /files partitions.
Seems like this is a better approach than installing everything to the same partition.
I've used GParted a couple of times previously many years ago, but I'm a little anxious about creating new partitions manually in case I get things wrong and screw up my installation before I've even begun using my new distro and my shiny new hardware!
Do recent Ubuntu distros give the user the option to create separate partitions automatically as part of the installation process ?
If so, this would be great !
If not, could you possibly advise on what size partitions I should allocate, and maybe a link to a good tutorial for beginners on how to do this manually using eg. GParted.

Thanks again all for your recommendations and support

BW

---

### Post by TheFu on 2020-12-31
Aptik will only help with data, nothing else. Has that tool been maintained?

Might I suggest you look through these forums for people using HP laptops and having issues.  You may want to rethink choosing HP.  Lenovo and Dell seem to have better compatibility with Linux.

All the other stuff is so dependent on your opinion and skill level that I wouldn't presume to make any suggestions.

**Part 1: Backup everything needed.**

If it were me, I'd copy all my data off. For typical end users, that would be held in your HOME directory.

Then I'd copy any system configuration files that I'd modified manually.  These should be in /etc/ somewhere.  Hard to remember each file if you don't take proactive steps AS-YOU-MODIFY them over weeks, months, years.  I always add a comment to files that I modify with :thefu: so I can quickly grep and find them.  In the meantime, /etc/ is relatively tiny, so it is part of my daily, automatic, versioned, backups.

Then I copy off everything in /usr/local/ ... everything there was something that I've manually installed. Period. No exceptions.

Then I'd make a list of all manually installed packages. This is slightly in-exact, but **apt-mark showmanual** will get all the manual packages, but it will get some automatic packages too.  Shove this into a file, use normal redirection, then you can use that list to reinstall later. 

**Part 2: Do a minimal, fresh install of the new OS**
Simple is better.  I setup storage in a specific way. Not many people do it like I do. I've posted about that setup in these forums multiple times, if you care.

**Part 3: Restore everything in the same order backed up.**
[LIST=1]
[*] HOME directory  - a simple copy everything back
[*] System settings - only those I specifically modified!!! Don't touch new stuff that doesn't need it.
[*] /usr/local/ - a simple copy everything back
[*] Tell APT about the list of manually installed packages and have it reinstall those.  Ensure there isn't any i386/i686 architecture specified for the packages.
[/LIST]

As the packages are reinstalled, the settings you put back will be see and used.

This assumes you put any services and the data they use back where they were before.  That is a file system location. The partitions don't matter to programs.

**Absolutely Critical Stuff**
When you backup and restore, the owner, group, permissions, ACLs and xattrs must be retained.  Backup tools handle this for us.  For files in your HOME, it isn't all that critical, but for everything else in /etc/ and elsewhere, it is critical to security that the file metadata be correctly retained. If not, either it won't work or system security can be completely compromised.

Some other references:
[LIST]
[*]My Script: [https://ubuntuforums.org/showthread.php?t=2436006](https://ubuntuforums.org/showthread.php?t=2436006) has more discussion.
[*]Restoring backups: [https://ubuntuforums.org/showthread.php?t=2389631&p=13757986#post13757986](https://ubuntuforums.org/showthread.php?t=2389631&p=13757986#post13757986)
[*]aljames2 script w/ LVM snapshots: [https://ubuntuforums.org/showthread.php?t=2422831&p=13935233#post13935233](https://ubuntuforums.org/showthread.php?t=2422831&p=13935233#post13935233)
[*]rsnapshot: rsync + hardlinks for versioned backups (requires Linux file system like ext4)
[LIST]
[*][https://popey.com/blog/2020/12/straightforward-linux-backups-with-rsnapshot/](https://popey.com/blog/2020/12/straightforward-linux-backups-with-rsnapshot/)
[*][https://www.cyberciti.biz/faq/linux-unix-apple-osx-bsd-rsync-copy-hard-links/](https://www.cyberciti.biz/faq/linux-unix-apple-osx-bsd-rsync-copy-hard-links/)
[/LIST]
[/LIST]

---

### Post by full-o-beans on 2021-01-02
Just to clarify re: my original question 2 above: 
It seems that it is definitely helpful to make separate partitions if there are multiple users or operating systems.
However I'll be the only user on the new ultrabook; and I'm not a fan of Windows, even if it comes pre-installed for free; so I don't see any benefit in wasting my SSD space with Windows and running a dual boot system. 

Would you still recommend creating a separate /data partition for a single-user, single-OS setup, and if so; what are the risks and benefits of doing this ?
If a /data partition is recommended, do modern distro installers generally give the option to create this automatically during the installation process ?
If not, then I guess I would have to do this manually with GParted prior to installing the new distro. 
What settings would you recommend for the SSD file system type (? is ext4 still best choice ?), partition sizes, and swap file size etc; given the above spec of the new ultrabook ?
(I'll probably want to share data files with both Mac and Windows machines in future, but will do this via an external HDD formatted using ExFat / EFS which I believe is common to Linux, Mac, and Windows).

@TheFu: Many thanks for your detailed and helpful reply, links, and step-by-step instructions for migrating.
Since my original posting, I've found some reports of compatibility problems with running Linux on the HP Envy, so will check out Lenovo and Dell as you and @catkiller recommend.
I've previously always used Backup (GUI for DejaDup): Simple to use, but even with my current small HDD it takes over 6h to create and verify a complete encrypted image of all the contents of my /home folder, which is a real disincentive to backing up as frequently as I ought to !
Before I made the move to Linux, there used to be a Windows app called ViceVersa Pro, which provided fast differential backup with an simple intuitive GUI. I wasn't aware of any Linux equivalent, but rdiff-backup sounds perfect (especially if run as a cron job). I've tried to download a copy of rdiff-backup from Github to experiment with prior to migrating to the new ultrabook, but legacy versions don't seem to be available for my ancient 32 bit machine and Xenial OS. 
No matter: I'll definitely include this on my new install. Thanks again for this recommendation.


Apologies for the number and wide range of questions that I'm asking in this thread: 
I'm hoping that if I plan properly I can make the transition to my new hardware and new OS as quick and painless as possible, and get everything working together correctly from the start, rather than making any mistakes which I then regret or have to find workarounds for.

Thanks again for your support and patience.
Best wishes

---

### Post by TheFu on 2021-01-02
Why not just install from the repos?
**sudo apt install  rdiff-backup**
I'm using that version on all my systems, except 20.04 which switched to python3 and broke the client-server connection to my backup server.  I used 32-bit 16.04 for years until last June on a desktop here. No problems with rdiff-backup between 32-bit and 64-bit clients/servers at all.

---

### Post by full-o-beans on 2021-01-03
@TheFu: 
I've installed rdiff-backup on my 32 bit Netbook from the repos as you recommended and done some test backups and restores. 
It is really simple to use straight out of the box, and extremely fast and efficient; but also has powerful configuration options to make it more flexible if needed. I'm surprised that this app hasn't received more publicity, but I guess the lack of encryption and GUI may be a turn-off for some people.
After a bit of Googling, it seems that Duplicity has similar functionality to rdiff-backup, but offers encryption, is allegedly faster, and uses less HDD space: [https://blog.roundside.com/duplicity-vs-rdiff-backup-in-action/](https://blog.roundside.com/duplicity-vs-rdiff-backup-in-action/)
so I will also look further into this option.
For now though, it seems rdiff-backup is the perfect solution to making fast mirror backups and transferring files to my new Ubuntu install. No excuses for not backing up more frequently now! Thanks again for the excellent recommendation.

---

### Post by Hagar Delest on 2021-01-03
I would recommend a dedicated partition for the user data, even if single user and/or single OS. It helps keeping things separate. In case of reinstall, fewer chances to lose anything. I don't have my /home on a separate partition but symlinks pointing to a separate partition for documents and some application profiles (Firefox, LibreOffice...).

I would also recommend keeping MS Windows. Just resize it. Mine is 80GiB with still plenty of space available on that partition. On a big drive, it does not cost much and you may need it in the future for whatever reason. Personally, I rented a scanner for "old" negatives and it only works on MS Windows. Thus, very glad I had kept it!

Partitioning is no big deal, it can even be done in MS Windows now, without 3rd party application. Personally, I've 2 dedicated partitions 20GiB each for the distro installation. When there is an upgrade, I use the other partition. Thus I start with a brand new install, My documents are still in their dedicated partition, I just have to copy the links from the previous distro to the new /home and that's all. Plus the reinstallation of my favorite applications but in single apt-get install line with all the apps listed is fine.
Having 2 partitions for the system (/) allows to roll back to the previous one in case there is a problem (it occurred once actually in my case).

---

### Post by TheFu on 2021-01-03
Some things to consider, 

That link is for trivial backups. Trying to make claims about the time 30G of data backups/restores will need based on 2 minute tests smaller than 1GB is just crazy.  If you are a programmer and use lots of tiny source files, there might be some bearing, but probably not.  Networking and storage don't work that way. We cannot extrapolate from samples so different.  My testing of 100G backups using Duplicati and rdiff-backup showed that rdiff-backup was over 8x faster than duplicati; 45 minutes vs 8.5 hours.  Duplicati is based on duplicity.  But if you're full backups only take 2 minutes, then by all means, use those data points.  How much do performance really matter in that situation?

Duplicity, deja-dup, duplicati are all related and check many boxes for what ideal backup tools can do, but they work very differently from rdiff-backup.  Both don't mandate that native Linux storage be used and both capture file metadata changes over times, which is a failure in almost all other F/LOSS backup tools on Unix systems like rsync, rsnapshot, timeshift, back-in-time, ... 

rdiff-backup let's us control the encryption used.  ssh is used for the network portion and encryption on storage can be anything we choose to setup, perhaps LUKS, but it is up to us. encfs, encryptfs, or file-system included encryption are all options.  OTOH, the most recent backup appears like a mirror with rdiff-backup, so restores can be performed of that last backup using other tools like cp, rsync, tar c| ssh |tar x, whatever.  They are reverse-differential backups, which are good and bad.  Only the first backup will be a "full" backup.  I have systems with rdiff-backup where the last "full" was performed years ago. Since then, they have all been differential backups, usually needing just a few minutes.  Restoring a backup from 39 days ago is pretty easy.  
```
sudo rdiff-backup -r 39D {backup location} {target restore location}
```
The {backup location} can be 1 file, a directory tree, or an entire backup set. There are include/exclude options, as you've seen.  I once needed to restore a corrupted DB from 39 days ago. Just that mariaDB file, not anything else. It was pretty easy to drop it into a temporary location, then move it into the correct place with correct permissions.  I wasn't 100% positive when the corruption happened, so I moved 7 days at a time through the backups until I got close.  Generally, I keep 90 days of backups, minimum, for every system.  Some higher risk systems get 180 days of versioned backups.

duplicity stores backups in chunk files that are not useful to humans. Only duplicity will be used to perform a restore.  And because they follow the 1970 backup schedule:
```
S M T W T F S
- – - – - – - 
D D D D D D M
D D D D D D F
D D D D D D F
D D D D D D F
```

Basically, we are expected to do a full backup every week.  How long will a full backup take? How much bandwidth?
If I need 180 days of duplicity versioned backups and I'm doing 1 full backup each week ... how much storage is that?  Say I can live with a more little risk and only keep monthly full backups, that's still 6 months or 6x the size of the original backups, right?  Is duplicity really more efficient on storage?  Even with 50% compression that's still 3x the original storage, not including the daily diffs.  Going longer than 1 month between fulls - that's just crazy.  [https://askubuntu.com/questions/625521/duplicity-deja-dup-full-backup-frequency](https://askubuntu.com/questions/625521/duplicity-deja-dup-full-backup-frequency)

But if you need to store the backups on remote storage that you don't control and are forced to use non-secure network transfers like plain FTP, then duplicity really is the best choice.

The amount and type of data that changes each day will drastically impact how much storage is needed.  The only way to know for certain is by doing your own tests. YMMV.  Over the decades, I've tested at least 20 different backup solutions.  For a long time, I used rsnapshot-like methods which are based on rsync.  Eventually, my needs outgrew that rsync could handle, mainly due to huge files. When daily backups were taking 90 minutes per system and I needed to backup 20 systems, it had to be changed.  I looked at lots of different tools - that was around 2011.  

About once a year I have to use one of those backups to restore for some reason. Almost always it was due to my stupidity, but not always. ;)  I tend to not make the same mistake twice ... unless it is a mistake that I do over and over and over and over (once did that with the sudoers file).

---

### Post by full-o-beans on 2021-01-03
@Hagar: Many thanks for your recommendation re: partitions. 
Sounds like this is the way to go, even for my simple single user set up.
I'm assuming that the Ubuntu distro installers don't offer the option to do this automatically during setup.
 I've used GParted for this purpose once many years ago, but am a bit anxious in case I screw up! 
Can you recommend a good step-by-step idiots' guide to doing this, and also a description of how to set up symlinks to access data on a different partition ?

@TheFu: I'm grateful for your extensive experience and very helpful response: rdiff-backup is the way to go!
One question (and apologies if this is moving off-topic from my original post)
>>>[COLOR=#000000]Only the first backup will be a "full" backup. I have systems with rdiff-backup where the last "full" was performed years ago. 
[/COLOR]As all subsequent incremental backups depend on the integrity of the first backup, would this be a potential vulnerability if the back-up medium was to get corrupted ? 

 If so, how do you mitigate against this in practice - do you also schedule regular "full" / disc image backups (eg. once a week) in addition to the more frequent incremental backups (eg. every day) ?
(In my case, the back up medium will be a mirror on a simple USB HDD - maybe I should use two mirrors on two different USB HDDs ?). Many thanks.

PS I'm leaning more towards a Lenovo X1 Carbon Gen 8 Thinkpad as hardware of choice thanks to comments on this thread...

---

### Post by QIII on 2021-01-03
> **full-o-beans said:**
> Many thanks for your recommendation to urgently upgrade to 64 bit (unsupported on my ancient 32 bit  Samsung netbook): your trick of installing Xenial amd64 initially and then upgrading with do-release-upgrade is a really neat workaround, but as you say, it might be safer to start over.

Yes, whatever you do, *starting over* with a 64-bit OS is critical.

There are those of us here (I bet TheFu is one, too!) who started with 8-bit machines (yes, really) and watched people drag their feet going to 16, then 32, then 64-bit.  The 8-bit and 16-bit wells have dried up and the 32-bit well is running low.

And although do-release-upgrade generally works for most, why not start afresh if you are going to 64-bit?  20.04 will be supported until April 2023 for most of the flavors, 2025 for vanilla Ubuntu.

---

### Post by Hagar Delest on 2021-01-03
You can do the partitioning during install. You've to the last option IIRC, something not very clear, like "I want to do it manually", don't remember the exact wording. It will open GParted and then you can create your partitions. Select EXT4 for the file system. Resize Windows if not done yet (80GiB should be enough but better do that first in Windows so that you're sure there is enough space; it may require the removal of unwanted applications).
You can have 1 or 2 partitions for the system (/), 30GiB each should be fine depending on how you set up your documents. Then a partition for your documents (say 50 to 100GiB), one for your profiles (10 GiB) and one for your downloads for example (100GiB). You can provide the partitions a label, easier to remember at the next upgrade.
When creating the partitions, provide the mounting point. My configuration is that on the partition for documents, I've a folder for my own documents (say Hagar). The mounting point is /home/All/Documents for the partition (to be typed in the mounting point entry when creating the partition). Then, once the system is installed, I delete the standard "Documents" folder in the /home/username/ directory and replace it with a symlink: ln -s /home/All/Documents/Hagar Documents. The /home/username/Documents will then point to the /Hagar folder.
Do the same for the /Downloads folder and for the profiles. For the profiles, the mounting point can be /home/All/Profiles and then add a folder for each application, like "Mozilla" for Firefox, then in your /home: ln -s /home/All/Profiles/Mozilla .mozilla.
Note that such partitioning can be done afterward, so play with it with a bit and change it after you've evaluated what is best for you.
You should read some tutos about partitions and symlinks to be used to it before actually doing it.

---

### Post by full-o-beans on 2021-01-03
@QII: Thanks! Will start afresh with 64-bit OS and 64-bit versions of all my apps.
I was hoping Aptik might help automatically migrate all my existing 32-bit apps to the latest 64-bit versions to save me from installing all my apps manually one at a time on the new hardware, but it sounds as though its safest to do this manually.
Not a problem: good opportunity for some spring cleaning and weeding out some of those many apps that I've installed but never use ;-)

@Hagar: Many thanks for the explanation of how to set up and size partitions: really helpful. 
I'll try to find some on line tutorials and do some more reading before doing this.
>>> [COLOR=#000000]Note that such partitioning can be done afterward, so play with it with a bit and change it after you've evaluated what is best for you.
[/COLOR]This is very reassuring and good to know ! Thanks again for your help.

---

### Post by CatKiller on 2021-01-03
> **Hagar Delest said:**
> You can do the partitioning during install. You've to the last option IIRC, something not very clear, like "I want to do it manually", don't remember the exact wording. 
I believe that option is labelled as "something else."

---

### Post by TheFu on 2021-01-03
> **full-o-beans said:**
>  
@TheFu: I'm grateful for your extensive experience and very helpful response: rdiff-backup is the way to go!
One question (and apologies if this is moving off-topic from my original post)
>>>[COLOR=#000000]Only the first backup will be a "full" backup. I have systems with rdiff-backup where the last "full" was performed years ago. 
[/COLOR]As all subsequent incremental backups depend on the integrity of the first backup, would this be a potential vulnerability if the back-up medium was to get corrupted ? 

 If so, how do you mitigate against this in practice - do you also schedule regular "full" / disc image backups (eg. once a week) in addition to the more frequent incremental backups (eg. every day) ?
(In my case, the back up medium will be a mirror on a simple USB HDD - maybe I should use two mirrors on two different USB HDDs ?). Many thanks.

PS I'm leaning more towards a Lenovo X1 Carbon Gen 8 Thinkpad as hardware of choice thanks to comments on this thread...

rdiff-backup is a reverse-incremental backup. That means that the most recent backup looks like a mirror of the files. It is a "full", but created using diffs only.  If you want more copies of the backups (which is a good idea), then use rsync to mirror the rdiff-backup are somewhere else.  I do that for business needs off to another server on the internet.

Really, once you run even a tiny rdiff-backup and looked at the created backup areas, it will become clear how this works.  Run a backup of /etc/ ... then modify 1 file, say /etc/hosts ... insert an extra space or comment, any change will do.  Then run the exact same rdiff-backup command again.  Now, go into the backup target directory and look around.  You'll see a /etc/ , but you'll also see an rdiff-backup-data/ directory.  Under here, you'll see a set of increments/ then in each directory with any changes, there are timestamped files with .diff.gz names.  Also, if you change any permissions or ACLs or xattrs, those will be captured in metadata files, even if the file doesn't change.  rdiff-backup has a number of reporting options.  --list-increments and --list-increment-sizes are handy.  /etc/ is tiny, but a very important directory to backup, so ensuring you get all those files correctly, with the metadata (owner, group, permissions, ACLs, xattrs) to go with the file is critical when it comes time to restore.

Nothing gets stored anywhere else except the backup-target location.  When you are done, just delete that location from the disk.

How would you restore the files?  Ones from now or yesterday or last week?  Understanding these things BEFORE you commit would be the minimal level of skill for any backup solution.  Be certain you know how.  Create some notes. Ensure those notes are in your backups too. ;)

Go play with it a little. You'll see.

---

### Post by full-o-beans on 2021-01-04
@TheFu: Thanks: I have enjoyed playing with and learning about the different options for rdiff-backup. 
If I understand correctly:

rdiff-backup will automatically verify each differential backup after it is performed using CRC or similar, so there is no danger of unexpected data loss due to a failed or incomplete backup.

After the first full backup, each time I do a differential backup, it will create a new diff.gz file, and these will take up some space on my host HDD or SSD. However, these files are compressed and pretty small in size, and (as you suggested in a previous post) I can set up rdiff-backup to only keep the diff.gz files corresponding to the most recent *n* incremental backups; or only keep the diff.gz files created in the last *n* days or months, and delete all of the other diff.gz files; so there should never be a problem with cumulatively filling my up host HDD with zillions of diff.gz files. 

Restoring the backup is just a simple case of using the standard command line cp command to copy the mirror of the most recent incremental backup to the host drive eg.
[FONT=inherit]cp -R mirror_of_data/. host_folder_for_data/
- or I can use the rdiff-backup command options if I want to select and restore a specific earlier version of the differential backup.

[/FONT]And if I want the mirror to be encrypted or compressed, I can just run zip with the encryption option (or any similar encryption and/or compression utility) against the mirror from the command line eg: 
zip -e archivename.zip mirror_of_data/

 Thanks for recommending rsync to periodically mirror my rdiff-backup from one external HDD to a second external HDD (which I'll keep in a completely separate physical location) - eg:
rsync -rlptgoD --delete /media/mirror1 /mirror2/

Again, I wasn't aware of this powerful and simple solution.
I hope this link might be helpful in explaining the options to other newbies like myself who have not used rsync before:
[https://superuser.com/questions/1334510/rsync-options-i-should-use-to-clone-external-drive](https://superuser.com/questions/1334510/rsync-options-i-should-use-to-clone-external-drive)

I'm considering trying to run the backup script for rdiff-backup and rsync using anacron rather than cron, as I understand that cron is a good choice for machines which are always running (eg. servers); whereas anacron is a good choice for machines which are frequently turned on and off (eg. desktop and laptop computers). If the laptop is switched off when one or more anacron jobs are scheduled (eg. the laptop is switched off for a day or two when daily backups are scheduled), then the backup script will automatically run once (and only once) the next time that the laptop is booted up.

Thanks again for your clear explanations and for sharing your valuable experience about backups. It is really helpful - not just for migrating to my new system, but also for having a simple and robust system in place for all my future backups; and for my general learning about Linux.

---

### Post by TheFu on 2021-01-04
> **full-o-beans said:**
> 
rdiff-backup will automatically verify each differential backup after it is performed using CRC or similar, so there is no danger of unexpected data loss due to a failed or incomplete backup.

rdiff-backup will complain clearly when it fails. I know that much.  Also, if you don't notice that, the next backup run will say something like, "prior backup failed, rolling back".  I've seen that twice in about 10 years. When it happened, I wasn't able to correct the corruption problem and ended up moving the prior backup area for that server to a different location, then starting the backups again in the prior location.  After 30 days of the new backups working, the old area would be removed - I use 'at' for that, so I don't forget.  My backup storage has a few hundred GB of extra space and most server backups with 90 days use only 10-25G.

> **full-o-beans said:**
> After the first full backup, each time I do a differential backup, it will create a new diff.gz file, and these will take up some space on my host HDD or SSD. However, these files are compressed and pretty small in size, and (as you suggested in a previous post) I can set up rdiff-backup to only keep the diff.gz files corresponding to the most recent *n* incremental backups; or only keep the diff.gz files created in the last *n* days or months, and delete all of the other diff.gz files; so there should never be a problem with cumulatively filling my up host HDD with zillions of diff.gz files. 
It sounds like you've missed what reverse differential means.  The last backup looks like a mirror of the source.  Only N+1  thru N+180 have diff.gz files.  The current backup always looks the same as an rsync mirror.  You can only remove the backups from the oldest files and you should use rdiff-backup to do that.  Sorry if I wasn't clear about that.  If you remove any intermediate backup diffs, you've just broken all older backups.  The diffs are relative to each other. Only the latest backup doesn't care about diffs, but every older backup is a set of diffs from that, applied in order.  

It is the difference between SCCS and RCS software version control systems, if that helps.  SCCS works like backup programs in the 1970s and in the way that duplicity works.  Full + diffs moving forward.  RCS and rdiff-backup work with full + diffs, moving backward.  That probably isn't helpful. Ignore it if you don't know anything about SCCS or RCS.

> **full-o-beans said:**
> Restoring the backup is just a simple case of using the standard command line cp command to copy the mirror of the most recent incremental backup to the host drive eg.
[FONT=inherit]cp -R mirror_of_data/. host_folder_for_data/[/FONT]
- or I can use the rdiff-backup command options if I want to select and restore a specific earlier version of the differential backup.
Well, you really need to use ```
sudo cp -rp mirror_of_data/ host_folder_for_data
``` and there are probably a few other options needed to handle symlinks and sparse files correctly.  Usually, people would use **sudo rsync ** to exactly copy many directories, not cp.  I used cp really to explain that is what you need. For 1 file, sure, fine.  But for entire directory structures, please use rsync.

Note how I used code tags, not fonts?

> **full-o-beans said:**
> 
And if I want the mirror to be encrypted or compressed, I can just run zip with the encryption option (or any similar encryption and/or compression utility) against the mirror from the command line eg: 
zip -e archivename.zip mirror_of_data/

zip, tar, and tools like that really aren't meant for system backups.  They are designed for 500MB or less stuff.  Anything larger, there are better answers, IMHO.  And really tar with compression would beat zip or bzip because it maintains owners, groups and handles ACLs, sparse files, etc.  As you learn more, you'll learn why Unix has these different tools and why they are important.
The key thing is never modify the backup file storage area directly. Only copy stuff from it, non-destructively, unless you intend to delete everything there anyway.  

> **full-o-beans said:**
> 
 Thanks for recommending rsync to periodically mirror my rdiff-backup from one external HDD to a second external HDD (which I'll keep in a completely separate physical location) - eg:
rsync -rlptgoD --delete /media/mirror1 /mirror2/

I'd use ```
sudo rsync -avzS --delete {Backup area}  {clone area}
```
I've been burned by sparse files, if that isn't clear.

> **full-o-beans said:**
> 
Again, I wasn't aware of this powerful and simple solution.
I hope this link might be helpful in explaining the options to other newbies like myself who have not used rsync before:
[https://superuser.com/questions/1334510/rsync-options-i-should-use-to-clone-external-drive](https://superuser.com/questions/1334510/rsync-options-i-should-use-to-clone-external-drive)

Be very careful with that answer.  It was for an exFAT file system.  That implies many things that do not apply with native Linux file systems are used.

> **full-o-beans said:**
> 
I'm considering trying to run the backup script for rdiff-backup and rsync using anacron rather than cron, as I understand that cron is a good choice for machines which are always running (eg. servers); whereas anacron is a good choice for machines which are frequently turned on and off (eg. desktop and laptop computerss). If the laptop is switched off when one or more anacron jobs are scheduled (eg. the laptop is switched off for a day or two when daily backups are scheduled), then the backup script will automatically run once (and only once) the next time that the laptop is booted up.

Yep, or you can just ensure that your desktop/laptop run their backups at a known time and shutdown (or standby) after, automatically.

> **full-o-beans said:**
> Thanks again for your clear explanations and for sharing your valuable experience about backups. It is really helpful - not just for migrating to my new system, but also for having a simple and robust system in place for all my future backups; and for my general learning about Linux.

rdiff-backup can be too different for people to understand. Sometimes the old hardlink backup methods that **rsnapshot**, back-in-time and 20 other "tools" on Linux act like they invented are easier for people to understand.  Sometimes people only want 1 backup a week and don't see the need for more than 5 total, but want to limit wasted storage. rsnapshot can do those things.  Understanding **hardlinks** and **symbolic** links is something to which Windows people don't really get much exposure. It was only in the last few years that MSFT finally added support for them into NTFS. MSFT attempted something like symlinks with their "libraries", but because "libraries" were only available for .Net programs, they never worked correctly. 

Anyway, glad to have helped.

---

### Post by full-o-beans on 2021-01-05
@TheFu: Thanks again for taking the time to explain and clarify things, and for correcting my attempts at command line examples - hugely appreciated!  I think I've finally got my head around exactly how rdiff-backup does its stuff, and am in awe of the authors for coming up with such an elegant and beautiful solution.
I've just been reminded that I've been posting in a Chat sub-forum; and this thread is better suited to a Technical sub-forum :oops:, so I'll end this thread here. This is my first posting on Ubuntuforums.org, and I want to thank the moderators and community for all your kind contributions and support. Wishing you all a safe and happy 2021.

---

