---
title: "How's your backup solution?"
date: 2016-02-05
forum: The Cafe
---

### Post by markodd on 2016-02-05
So, I've been thinking about changing my backup solution and I'm interested in hearing yours.

So, how do you backup your data? To the cloud? To an external HDD? Both? To your own server? What software to you use for all that?

---

### Post by Habitual on 2016-02-05
rsync and USB.
The term "Cloud" is over-used.
It means "I don't know where my stuff is".

---

### Post by matt_symes on 2016-02-05
At the moment it's incremental rsync to my backup server using scripts containing WOL and shutdown commands, to start the backup server and to shut it down. Certain files and directories are encrypted and uploaded to the cloud.

I also make regular hard drive images of my laptop and other computers.

I'm waiting for zfs to be baked into the kernel and then I'll be looking at 'zfs send and receive' to backup incremental snapshots. I think this will be a viable backup option.

---

### Post by Old_Grey_Wolf on 2016-02-05
My backup needs are simple, and may be very different from your needs. I don't have very many changes to files in a weeks time now that I am retired. I backup to external HDD's once a week. I alternate HDD's each backup. I use rsync for servers and grsync for desktops. I keep them stored in a fireproof safe; therefore, I don't encrypt them or compress them. I do full backups; however, I only update the files that have changes since the last backup so it doesn't take very long per computer.

---

### Post by PhilGil on 2016-02-05
Nightly backup to an external hard drive using Back in Time. Weekly rsync backup to a different external hard drive that I keep at my office.

---

### Post by MartyBuntu on 2016-02-05
I make a pot of coffee on Sunday morning and do complete drive imaging of my laptop and desktop workstation on an external, eSATA connected drive, with a bootable Acronis True Image disk.

---

### Post by RI2CA on 2016-02-05
Spideroak for backup and sync. I've been using them for a couple of years and never had an issue with Linux, OSX or Windows.

---

### Post by monkeybrain20122 on 2016-02-05
I just back up some data with unison to an external drive (actually it syncs) I back up the root partition with fasrachiver so in case I break the system I can recover in about 10 minutes. It is more important for me to backup the system than the data since my system is very highly tweaked and I installed a bunch of things from source, for data I only backup some document folders and my music folders (about 25G total)

---

### Post by buzzingrobot on 2016-02-05
I don't do system backups because it's easier and quicker to reinstall.

Home, and not all directories in there, is backed up daily to an external drive via a shell script that just bundles everything up in a compressed tar archive. Recovery is accomplished by extracting an archive.  It's not fancy but it's dead easy.

The script keeps 30 days worth of archives on the external drive and that day's archive on Dropbox.

---

### Post by montag dp on 2016-02-05
I just back up the files I want to keep on my /home to external hard disks using rsync.

---

### Post by PJs Ronin on 2016-02-05
I use fsarchiver to do a daily backup of my current O/S partition to my data HD so that gives me 7 versions of my working system should I (inevitably) stuff things up.   I use rsync to copy the data partition to a second hard drive every monday.   Every six months I rsync the data partition to a USB HD and give the drive to a lady friend over coffee.   She keeps the drive in either her knicker drawer or in the tool shed, I'm not sure which.

I don't trust clouds, I don't trust governments and I'm even starting to question the efficacy of my tin hat.

---

### Post by sammiev on 2016-02-05
Lucky Backup quick and easy. :)

Clonezilla for a full HDD backup image.

---

### Post by Wadim_Korneev on 2016-02-06
I think I would be ok trusting non-sensitive data to notable companies, such as Norton.  It's a well known company, that's been around a long time, and has too much to lose, by a data breach.  They have online backup as part of their Norton 360 package.

---

### Post by matt_symes on 2016-02-06
> **Wadim_Korneev said:**
> I think I would be ok trusting non-sensitive data to notable companies, such as Norton.  It's a well known company, that's been around a long time, and has too much to lose, by a data breach.  They have online backup as part of their Norton 360 package.

I agree with this and it can be encrypted before being uploaded.

The only major downside of encryption is that it's not searchable (potentially on both content and filenames), but that may not matter if your goals don't require searchability.

EDIT:

Just thought i should mention that i don't use Norton personally though.

---

### Post by tom-bellas3rd on 2016-02-06
Mines simple.. Just a copy and paste of Documents/pictures/music folders to a large USB disk once or twice a month. :)

---

### Post by kevdog on 2016-02-06
My current solution is backing up to a central server at home running Ubuntu.  The various clients use rsync.  I just backup the home directories.  I suppose I should back up the /etc files since that is where some customizations are.  The central server is so old I don't think I can do a WOL -- however @matt_symes -- I'd be interested in how you set this up.  I've toyed with obnam however its kind of slow.  The reason I like it, is that the backups can be encrypted using GPGkeys and the backups can be remotely mounted -- so it's possible to do some searching. It's pretty slow however and the code is being actively worked on by Larz so I'm not exactly sure I would call it a stable solution.  Larz Weinmann (the creator of the program) would probably differ on this statement.  

I too am very interested in using zfs and am in the process of setting up VM's to play with this in a test environment.  The problem as alluded to by matt_symes is that the zfs modules are not backed into the kernel due to patent restrictions.  I'm unsure if there will be ever some work around.  Possibly I'm wrong on this.  The problem is that every time the kernel is updated you need to boot from a rescue disk to add the zfs modules back into the kernel since the modules are not built into the kernel.  Supposedly there exists a dkms option, however I could never get it to work.  I guess there is a BSD option to get this to work since BSD kernel are part of the patent process with ZFS, however I'm really not excited on learning BSD if I don't have to.

---

### Post by matt_symes on 2016-02-06
Hi kevdog,

Basically the script i wrote works like this.

My backup server has a static IP address.

When the script runs it pings the backup server.
If it gets no response from the server it sends a WOL magic packet to the server and starts pinging it again.
When it gets a ping response, it then attempts to ssh into the server in an attempt get the last directory created on the last run of the script.
When it can run that that command, shh is up.
If ssh does not return the previous directory, it creates a full backup using rsync. If the previous directory is there, it creates a new directory based on the date and the PC name and then it creates an incremental backup against that previous directory.
When rsync has finished, it sync and shuts down the backup server.

It has some error handling in the script that i didn't mention above.

As you can see, it uses a push method. There have been a number of times i've though about keeping the scripts on the server and using a pull from it to do the backup. Not sure how i would do that with WOL though so i kept it as it is. Less thinking and work involved that way and it works, however if i did change it, it would be less maintenance as the scripts would be in one place.

I only use this method to back /home and certain partitions. I image drives that i consider important such as this laptop

To see if you card supports WOL

```
sudo apt-get install ethtool
sudo ethtool <iface> | grep "Wake-on"
```

You're looking for a g for the magic packet. If it supports g then you can set g using ethtool as well.
```

Supports Wake-on: pua**g**
Wake-on: **g**
```

As for zfs, i heard a rumour that debian's lawyers don't consider the licensing issues surrounding zfs to be a problem.  I really hope this is the case.

I have seriously considered using freebsd on all my machines and running Linux in a VM to get zfs, as my files are more important to me than any operating system.

My other laptop is currently running PC-BSD which i have been playing with again. I have a small server running trueOS so, you never know, i may make the switch.

---

### Post by kevdog on 2016-02-07
Ok @matt_symes -- doing some thread hijacking here.  Here is my results:
$ sudo ethtool eth0 | grep "Wake-on"
	Supports Wake-on: g
	Wake-on: g

The output is a little different than yours.  I thought you had to set something in the bios to allow WOL.  I believe that is set.  What are the steps I need to do to issue a WOL?  Possibly this belongs in a different thread.  If you don't have the time, you could just point to a tutorial.  

Agreed on the files more important that OS.  One of the major barriers for me is the firewall syntax.  I use a script to enter the iptables command at boot.  I've read about bsd firewalls that make use of pfsense and not iptables, however I'm really lost how to convert from one to the other easily -- if there is a way.

---

### Post by Welly Wu on 2016-02-07
I use simple copy and paste of my private user data including documents and my software library along with my VMWare Workstation guest virtual machines to different internal and external hard disk drives over Super Speed USB 3.0. I put a copy of my documents and software library on a USB 2.0 thumb drive that is not encrypted and I make a second copy on my portable, MIL-STD certified, encrypted USB 3.0 hard disk drive while storing both of them inside my Sentry Safe that is fire resistant for up to 30 minutes. I copy and paste my media library to my internal and external hard disk drives in small batches to reflect newly purchased premium content daily.

I pay for CrashPlan+ Family that allows me to add up to ten PCs be it Windows, Mac, or GNU/Linux and backup my 2015 ZaReason Zeto and Sager NP8657 [Clevo P650-RE3] PCs to CrashPlan Central daily. I recently completed the initial data backups on both PCs.

It's easier and simpler not to mention faster for me to do a clean installation of the latest Ubuntu 64 bit GNU/Linux desktop operating system rather than to restore my data from a backup archive. I plan to try to upgrade from Ubuntu 15.10 64 bit to 16.04 64 bit LTS GNU/Linux on April 21st, 2016 on my desktop and laptop one at a time. If it is successful, then great. If it fails, then I will already have downloaded the ISO file and burned a DVD-R disc and a USB 3.0 thumb drive as Ubuntu startup disks and I will do another clean installation from scratch and stick with it for up to two years until the next Ubuntu 64 bit LTS release in April 2018.

My SteamOS + GNU/Linux PC games are purchased so I can download and install them on both PCs again in the future. For my 2015 ZaReason Zeto desktop PC, I have a second Western Digital Black 6 TB 7,200 RPM 128 MB cache desktop hard disk drive where I store my media library and PC games along with my documents and software library. If I need to reinstall the latest Ubuntu 64 bit GNU/Linux desktop operating system on my Western Digital Blue 4 TB 5,400 RPM 64 MB cache + 8 GB MLC NAND FLASH SSHD, then I will do so and copy and paste my data back onto it in a couple of hours.

I recently had to do this for Ubuntu 15.10 64 bit GNU/Linux and I expect that I will do it again for Ubuntu 16.04 64 bit LTS GNU/Linux in due time.

CrashPlan+ Family is nice to have since it's a lot cheaper than renting out a safety deposit box at my local PNC Bank branch each month. I already have a large Sentry Safe so that obviates the need to rent one out.

---

### Post by matt_symes on 2016-02-07
> **kevdog said:**
> Ok @matt_symes -- doing some thread hijacking here.  Here is my results:
$ sudo ethtool eth0 | grep "Wake-on"
	Supports Wake-on: g
	Wake-on: g

The output is a little different than yours.  I thought you had to set something in the bios to allow WOL.  I believe that is set.  What are the steps I need to do to issue a WOL?  Possibly this belongs in a different thread.  If you don't have the time, you could just point to a tutorial.  

Agreed on the files more important that OS.  One of the major barriers for me is the firewall syntax.  I use a script to enter the iptables command at boot.  I've read about bsd firewalls that make use of pfsense and not iptables, however I'm really lost how to convert from one to the other easily -- if there is a way.

Start a support thread, PM me the link and i'll talk you through it.

---

### Post by PartisanEntity on 2016-02-08
I like to learn as much as I can when tinkering around so I decided to build a small little home server to serve several services including backup.

I went with the HP N54L microserver (sold without HDDs). I added an internal drive for the OS (Ubuntu Server Edition) and 4 drives setup as raid 10.

So using Dejadup I make daily backups of my /home partition to the server through NFS. I then make a backup of the backup to an external drive attached to the server, this I do over rsync.

Lastly, for certain files I make additional backups to the cloud (SpiderOak).

---

### Post by SuperTrainStationH on 2016-02-09
I've got an external HDD I just drag and drop my stuff into every few weeks.

I used to keep a second HDD at my grandmother's house but that spiteful scoundrel Sandy went and washed it out to sea back in 2013.

---

### Post by cobalt2 on 2016-02-09
I use Tar scripts to backup 3 data sets. The home partition is backed up weekly. The other 2 are backed up only occasionally, because they are infrequently modified. This is a good method for saving time on backing up directories that are used infrequently. My backup medium is an internal SATA drive, which is disconnected when not in use. It's not much of a backup strategy, but it works.

---

### Post by Mr._Hope__Change on 2016-02-12
> **Habitual said:**
> rsync and USB.
The term "Cloud" is over-used.
It means "I don't know where my stuff is".

And more often than not: "*somebody else has total control over my data*".

I have multiple profiles in Unison that I use for my main laptop; all the data is encrypted.

1. Complete system backup to a 1TB HD.
1b. A backup of the backup to a 1TB HD. 
This is done once a week.

2. ~/Documents backup to 64GB thumb drive.
2b. A backup of the backup to a 64GB thumb drive.
This is done once a day.

---

### Post by pauljw on 2016-02-12
I don't get too carried away.  I use Systemback to create a "restore point" of which there are 5 kept, oldest deleted prior to creating the current one.  Then /home is backed up to a usb 2T external HDD using syncBackup.  I do this weekly.

---

### Post by yetimon_64 on 2016-02-13
> **pauljw said:**
> ...  I use Systemback to create a "restore point"...

On 14.04 I don't see that in the repositories at all. Is that only for a newer release or is it from some other source ? Sounds an interesting idea being able to create periodic restore points for Ubuntu.

---

### Post by pauljw on 2016-02-13
> **yetimon_64 said:**
> On 14.04 I don't see that in the repositories at all. Is that only for a newer release or is it from some other source ? Sounds an interesting idea being able to create periodic restore points for Ubuntu.

It's a PPA that I added a little while back.  I have had no problems so far.

[https://launchpad.net/systemback](https://launchpad.net/systemback)

---

### Post by yetimon_64 on 2016-02-14
> **pauljw said:**
> It's a PPA that I added a little while back.  I have had no problems so far.

[https://launchpad.net/systemback](https://launchpad.net/systemback)

Thanks, I'll look into that PPA. :cool:

---

### Post by drascus on 2016-02-16
I have a pogoplug and a custom python program that does all my backing up. I came up with this idea that instead of creating backup lists and all that I basically just put a file called "check" in a directory and if my program sees that file it knows to back the directory up. my program just runs as a scheduled job or on demand if I want.

---

### Post by Linuxratty on 2016-02-25
Thumb drive or ssh into the 2and computer.

---

### Post by Shobuz99 on 2016-03-25
I have no consistent backup process. It's random.
What I would like to know is what a simple process would be to backup my HDD,
so that when I want to install a new version of Ubuntu, I can recover all my data and image files minus
the old version of Ubuntu. What I do now is just buy a new SATA drive and copy files from my current drive.
It's quite a labor and time consuming venture. Is there an easier way?

Shobuz99

---

### Post by mikodo on 2016-03-25
> **Shobuz99 said:**
> What I would like to know is what a simple process would be to backup my HDD,
so that when I want to install a new version of Ubuntu, I can recover all my data and image files minus
the old version of Ubuntu. Shobuz99

Hi,

I would start reading in the link below. Try to visualize a plan that you think you could employ. Then, when you think you have ways to do what you want, try to instigate a few tests of throw away data to backup and restore. Make notes. When you become comfortable with backing up and restoring throw away data, try it on a real data, and test it again (restoring to a different place than your original source). When you are comfortable with that, refine your backup(s) and refine your notes. Keep a copy of your successful backup and restore procedures on an usb stick or other removable node and have it available when, you need to access it to walk yourself through the process when it comes time to restore in reality. Then, do a real full backup and keep that procedure in your notes. Test restoring it to, another place other than your source. Update your notes on your removable node.

Don't hesitate to ask specific questions in threads here, about what you are doing in any of the process above. No one knows what you are comfortable doing until, you decide what you want to do and tell us how you want to achieve it.

Here is an explanation on copying and moving data in case you want to start with that: [URL="https://www.st-andrews.ac.uk/ITS/training/unix/unix2.html"]https://www.st-andrews.ac.uk/ITS/training/unix/unix2.html
[/URL]
Addendum. In case you were just wondering what each of us thought would be a  simple backup and restore utility, I use rsync. It's mentioned in the  link below.

I had to search for it. I was really impressed with the detail and thoughtfulness 1clue put in to his posts here about backups with cp.
[http://ubuntuforums.org/showthread.php?t=2315430&highlight=backup](http://ubuntuforums.org/showthread.php?t=2315430&highlight=backup)

[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

---

