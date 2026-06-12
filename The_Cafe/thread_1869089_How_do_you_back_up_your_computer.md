---
title: "How do you back up your computer?"
date: 2011-10-25
forum: The Cafe
---

### Post by rmcellig on 2011-10-25
How do you back up your computer in case disaster strikes? Do you use a method that will allow you to get up and running in no time? I'm curious because I want to find ways that are similar to the way I currently back up my Mac.

One method I know many Linux users use is to keep their Home directory on a separate drive or partition. If so, what are the steps involved to do this? This seems like a practical way because all you have to do is recover your Home directory to a new fresh install of whatever Linux distro you are using?

I have been a devoted Mac user since 1988 and always found great ways to back up my Mac. I use Carbon Copy Cloner to clone my Mac nightly to an external bootable USB drive. I use Crashplan as well so I can access my stuff anywhere if need be.

Now that I am using Linux more and more, I want to find the best most efficient and practical way to back up my Linux computer. Looking for something similar to Carbon Copy Cloner has been difficult for Linux. Sure you have Clonezilla, and Back In Time but the problem with these methods is that I cannot create nightly clones of my drive to another USB drive without having to boot from the Clonezilla CD. Maybe there is another way I don't know about?

Bottom line is that I am looking for ways to backup so that if disaster strikes or rather when disaster strikes, I can quickly get back up and running in no time.

Looking forward to hearing from all of you and your backup experiences!!

---

### Post by haqking on 2011-10-25
> **rmcellig said:**
> How do you back up your computer in case disaster strikes? Do you use a method that will allow you to get up and running in no time? I'm curious because I want to find ways that are similar to the way I currently back up my Mac.

One method I know many Linux users use is to keep their Home directory on a separate drive or partition. If so, what are the steps involved to do this? This seems like a practical way because all you have to do is recover your Home directory to a new fresh install of whatever Linux distro you are using?

I have been a devoted Mac user since 1988 and always found great ways to back up my Mac. I use Carbon Copy Cloner to clone my Mac nightly to an external bootable USB drive. I use Crashplan as well so I can access my stuff anywhere if need be.

Now that I am using Linux more and more, I want to find the best most efficient and practical way to back up my Linux computer. Looking for something similar to Carbon Copy Cloner has been difficult for Linux. Sure you have Clonezilla, and Back In Time but the problem with these methods is that I cannot create nightly clones of my drive to another USB drive without having to boot from the Clonezilla CD. Maybe there is another way I don't know about?

Bottom line is that I am looking for ways to backup so that if disaster strikes or rather when disaster strikes, I can quickly get back up and running in no time.

Looking forward to hearing from all of you and your backup experiences!!


There are tons of threads on this.

However i take a clone of a fresh built system, then another clone of everything how i like it.  Then rsync personal files on a daily basis and thats it.

I can restore system in about 10 to 15 minutes

---

### Post by rmcellig on 2011-10-25
Thanks Haqking!

When you clone, do you cone to an external drive? When you restore, what are the basic steps involved? I just want to get a handle of how this is done in the Linux world. New territory for me. Thanks!!

---

### Post by james.m on 2011-10-25
> **rmcellig said:**
> 
Looking forward to hearing from all of you and your backup experiences!!

I was using **Back in Time** on 11.04, backing up to an external hard disk. Saved me a couple of times from when I deleted a file I shouldn't have :-)

---

### Post by Lars Noodén on 2011-10-25
I recommend using rsync for the data.  It's fast and simple.

---

### Post by ratcheer on 2011-10-25
I use **Deja Dup** and back up to a folder on an external disk drive. I was using Deja Dup before it became the default backup tool in Ubuntu.

Tim

---

### Post by haqking on 2011-10-25
> **rmcellig said:**
> Thanks Haqking!

When you clone, do you cone to an external drive? When you restore, what are the basic steps involved? I just want to get a handle of how this is done in the Linux world. New territory for me. Thanks!!

boot to a clonezilla CD, clone source to destination (in my case a USB ext HDD), same to restore except you choose source image file and local disk as destination.

Simples ;-)

---

### Post by rmcellig on 2011-10-25
> **haqking said:**
> boot to a clonezilla CD, clone source to destination (in my case a USB ext HDD), same to restore except you choose source image file and local disk as destination.

Simples ;-)

Thanks! Appreciate it.

---

### Post by smellyman on 2011-10-25
lucky backup to a usb HD and lucky backup to another networked pc.

The only thing of value on my pc is pictures.  that is the only data that cannot be replaced. (for me anyway)

---

### Post by collisionystm on 2011-10-25
Clonezilla your system one time and then just rsync your /home directory nightly.

System fails... restore clonezilla. Restore /home directory. Run system updates. Boom. Done.

---

### Post by boydrice on 2011-10-25
> **Lars Noodén said:**
> I recommend using rsync for the data.  It's fast and simple.

+1 for rsync

---

### Post by sammiev on 2011-10-25
+1 for Clonezilla, I do a full backup once a week of all my OS. :)

---

### Post by ubupirate on 2011-10-25
I don't really do backups of my entire OS, just essential files.

Which in case I have a mere single DVD for that, and also my laptop for just in case the DVD gets scratched up.

If something happens, just format and reinstall the OS and be back up in 40 minutes. No biggie.

But this is just me.

---

### Post by malspa on 2011-10-25
> **Lars Noodén said:**
> I recommend using rsync for the data.  It's fast and simple.

That's what I use, too. For the data. With Linux, I can easily use a live CD/DVD and get a system up and running, so I really don't care about backing up the entire system most of the time. Not that I would advise against backing up the entire system, but I just don't worry about that, myself. The important thing to me is backing up the data.

---

### Post by CharlesA on 2011-10-25
> **collisionystm said:**
> Clonezilla your system one time and then just rsync your /home directory nightly.

System fails... restore clonezilla. Restore /home directory. Run system updates. Boom. Done.
Pretty much this.

I usually just use rsync/robocopy to backup my data to my server and then the server rsyncs the data to external media.

---

### Post by polardude1983 on 2011-10-25
I have my home on a separate drive and on its own partition then my OS.

I rsync my /home to an external drive nightly
I also rsync my sources.list and and sources.list.d

Then I also create a log of all my installed apps

That's about it for me

---

### Post by BigSilly on 2011-10-25
I swore by Clonezilla until it failed to restore an openSUSE 11.4 image I made a while ago. Well, it wasn't so much the image that was at fault, rather the GRUB menu that it failed to restore. I tried all sorts of GRUB fixes and commands but nothing would fix it. Gutted I was.

Now I just tend to back up my important stuff to an external drive and various DVD discs for good measure. As long as that's safe I don't tend to worry much if I lose a day reinstalling an operating system.

---

### Post by Ozor Mox on 2011-10-25
I don't care about the operating system, I can reinstall that easily. I just use rsync to copy my data across my desktop, laptop and external hard drive to keep them in sync and keep several copies. The external hard drive is also in a different physical location to the computers because I'm just that paranoid :)

---

### Post by rmcellig on 2011-10-25
I just tried something on one of my Linux computers and it worked great. It's called Redo Backup. I found the interface easier to get through than Clonezilla. I backed up the entire drive, erased the drive. Then I started up from the Redo Backup CD,located the clone I just saved and restored it back to my HD. Rebooted with no problems. Using it on my wife's PC at the moment.

Another thing I was thinking of looking into is Remastersys. Has anyone tried this before? Apparently I can back up my OS to a DVD so that if the system dies on my HD, I can use the DVD to restore it to my HD. Not sure if this app is still around. If I use rsync, I would like to use a GUI front end so that it is easier to understand for my Mom. I know about Lucky Backup and Grsync being rsync front ends. I will try Robocopy as suggested in a previous post.

---

### Post by haqking on 2011-10-25
> **rmcellig said:**
> I just tried something on one of my Linux computers and it worked great. It's called Redo Backup. I found the interface easier to get through than Clonezilla. I backed up the entire drive, erased the drive. Then I started up from the Redo Backup CD,located the clone I just saved and restored it back to my HD. Rebooted with no problems. Using it on my wife's PC at the moment.

Another thing I was thinking of looking into is Remastersys. Has anyone tried this before? Apparently I can back up my OS to a DVD so that if the system dies on my HD, I can use the DVD to restore it to my HD. Not sure if this app is still around. If I use rsync, I would like to use a GUI front end so that it is easier to understand for my Mom. I know about Lucky Backup and Grsync being rsync front ends. I will try Robocopy as suggested in a previous post.

Cool glad it worked for you.

remastersys has been forked now to re-linux

---

### Post by rmcellig on 2011-10-25
> **haqking said:**
> 

remastersys has been forked now to re-linux


What does that mean? Is it now called re-linux?

---

### Post by haqking on 2011-10-25
> **rmcellig said:**
> What does that mean? Is it now called re-linux?

it means there is a spin-off if you like and its called re-linux as remastersys is no longer developed.

[http://www.geekconnection.org/remastersys/](http://www.geekconnection.org/remastersys/)

---

### Post by BrokenKingpin on 2011-10-25
I have my server setup in Raid5, and once a week or so I backup my important data from it to an external drive. I also have some stuff that backs up to SpiderOak.

From my PCs I just make sure I store anything important on the server over the network.

---

### Post by Roasted on 2011-10-25
> **ratcheer said:**
> I use **Deja Dup** and back up to a folder on an external disk drive. I was using Deja Dup before it became the default backup tool in Ubuntu.

Tim

My story is similar.

I began using Deja Dup last year because it was a backup solution that could automatically mount SMB shares and back up to it. NFS has its advantages but it also has its disadvantages, and I wanted a very basic user level authentication for my server. Since SMB is the one stop shop protocol for Mac, Linux, and Windows, it was a no brainer.

I set up a spare computer. It was a basic computer running 11.04 I believe. The computer has a single 4gb flash drive plugged into the back and inside are two 500gb SATA HDD's set up in a RAID 1 mirror via mdadm (very easy to set up in Disk Utility). The 4gb flash drive is actually where Ubuntu is installed (with swap turned off of course since it's flash media). On that drive are 5 user shares - 1 for each family member. Inside each share is either Deja Dup data, or sub directories labeled "Desktop" and "Laptop" (if that family member has one of each), then inside each is their Deja Dup data.

Deja Dup is very easy to set up. It's easy to manage and it's easy to let go and run on its own. Each box is set up to do daily backups. Every now and then Deja Dup does a full backup, but otherwise it'll do incremental backups, which tend to be a little quicker.

Only last week did I have to use Deja Dup's recovery utility. My mother had gotten a new laptop, so of course I fired up Ubuntu 11.10 and did a "restore" and sure enough the data ported over accordingly. So far, it's proven to be a solid application.

---

### Post by Legendary_Bibo on 2011-10-25
I push it back a few inches with my bare hands so it's not in the way of where people walk.

---

### Post by CharlesA on 2011-10-25
> **Legendary_Bibo said:**
> I push it back a few inches with my bare hands so it's not in the way of where people walk.
I lol'd. Thanks.

---

### Post by Brian0312 on 2011-10-25
I can reinstall Ubuntu in 15-20 mins and have it tweaked inside of an hour.   So I don't do full back ups.  I however would hate to rewrite my resume from scratch or lose my Thesis.  That's stuff you can't get back.
 
To that end, my back up process consists of copying my personal files onto two separate flash drives for redundancy and having a Live DVD on hand at all times.

---

### Post by KiwiNZ on 2011-10-25
> **Legendary_Bibo said:**
> I push it back a few inches with my bare hands so it's not in the way of where people walk.

Excellent :D

---

### Post by undecim on 2011-10-25
```
synchome () {
        DEST="$*"
        DEST="${DEST:="192.168.1.2:backup/"}"
        echo "Destination is $DEST"
        
        rsync \
                -a \
                --delete \
                --delete-excluded \
                --progress \
                --exclude=".gvfs" \
                --exclude=".cache" \
                --exclude=".local/share/Trash" \
                --exclude="nosync/" \
                ~/ \
                "$DEST"
}

```

I put that in .bashrc, and run synchome often. 192.168.1.2 is the (static) IP address of my server, where I have public key authentication set up.

You can also [make a list of installed packages]("http://www.arsgeek.com/2006/09/19/ubuntu-tricks-how-to-generate-a-list-of-installed-packages-and-use-it-to-reinstall-packages/"), and keep it in your home directory. If you add it to the beginning of that function, you will upgrade your list of packages. You could even add /etc/ to the sync to keep your system settings.

Though personally, I use any reinstalls as an excuse to get rid of software I never use anymore, and just install new software as I need it.

---

### Post by sn0m on 2011-10-25
rsync is your friend, there are also tutorials about setting an automatic ssh connection to a distal host and use cron to schedule jobs daily.
I lost my family pictures 4 years ago due to a failing hard drive.
Since then my wife's home directory, mine as well get backed up daily to family desktop via our wireless network, and also I have  4 hard drives in the desktop that also rsync to each other daily. I've never had a problem and it is probably a bit paranoic but i'd rather have that that loose any important files any more.
buon chance
sokol

---

### Post by standingwave on 2011-10-25
I rsync the data to a removable hard drive and keep one off-site at all times. I really don't bother with making a clone of the drive because in the event of a failure, the system & programs can be easily replaced. My data cannot.

---

### Post by wolfen69 on 2011-10-25
I don't save as much stuff as I used to, and only have about 41gb of stuff. And to be honest, if I lost it all, I would survive. But I just have my stuff mirrored on 2 separate drives, and also on an external drive. There's not much chance I'm going to lose anything. 

I'm personally not into RAID or NAS for backup, as I like to keep things as simple as possible.

---

### Post by alco75 on 2011-10-25
With the below script, to an external USB HDD, which probably should be off-site, but isn't.

```
#!/bin/bash
rsync -av --perms --modify-window=1 --exclude=".*/" ~/Music/ /media/250\ GB/Music/
rsync -av --perms --modify-window=1 --exclude=".*/" ~/Pictures/ /media/250\ GB/Pictures/
```

Non-media files I keep in Dropbox and don't worry about.

---

### Post by |{urse on 2011-10-25
I back up automatically i guess.
I restore with my own personalized restore dvds

I mount -o loop a slax or sysreccd image add partimage (edit the bootsplash to my liking) add the actual hard drive image itself (usually gzipped) + dd to rewrite the bootsector and a few scripts to make it as unattended as possible. My solution also uses tw_cli on init 4 so i can easily initialize my 3ware array if I need re-initialize to before I press x to restore the image. When the restore is complete the system reboots. 

Anything I ever save is mirrored so I guess that's how I back up.

[http://www.sysresccd.org/Sysresccd-manual-en_How_to_burn_a_DVD_with_SystemRescue_and_4_GB_more_files](http://www.sysresccd.org/Sysresccd-manual-en_How_to_burn_a_DVD_with_SystemRescue_and_4_GB_more_files) <-- this will help if youd like to make your own with sysreccd and partimage.

---

