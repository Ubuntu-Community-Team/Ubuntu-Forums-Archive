---
title: "Performance impact of full disk encryption?"
date: 2009-11-22
forum: Security
---

### Post by blueshiftoverwatch on 2009-11-22
How much would using full disk encryption of varying types effect the performance of a hard drive? IE, the time it takes to read/write data and to load programs.

What about CPU usage?

---

### Post by iponeverything on 2009-11-22
I can't give you any benchmarks or anything, but from using it it seems quite responsive with a good disk, but it did have an issue of going out to lunch for about 5 seconds or more every now again. I found this a bit annoying, but nothing I couldn't live with. 

I keep a second drive with full disk encryption that I rsync when I go on the road.  It does provide some peace of mind.

---

### Post by blueshiftoverwatch on 2009-11-22
I've heard from two friends that it's barely noticeable. but have read on various websites that it's very noticeable.

Does it have any effect (besides generally being quicker) if you use it with RAID0?

---

### Post by tubbygweilo on 2009-11-22
blueshiftoverwatch,
If full disk encryption is a *must* have then any question of a performance hit is not relevant but if the full disk encryption is a *nice* to have then performance might be an issue. If you do not need all the benefits offered by full disk encryption then encrypting just the data you consider sensitive might give you the best of both worlds.

---

### Post by rookcifer on 2009-11-22
It depends on which cipher is being used.  The default is AES-256, which is pretty fast since it was written in assembler.  Serpent will be a little slower.

The benchmarks I have seen (Phoronix, etc.) say that AES-256 gives about a 5% performance hit.  Not bad at all.

---

### Post by blueshiftoverwatch on 2009-11-22
> **rookcifer said:**
> The benchmarks I have seen (Phoronix, etc.) say that AES-256 gives about a 5% performance hit.  Not bad at all.
That doesn't sound too bad.

What encryption application would you recommend using? A friend who's really into security said that he's using Fedora over Ubuntu because it gives you the option to encrypt your entire disk by default. Because when you have to set it up after the OS is already installed it's a huge pain.

---

### Post by michaelzap on 2009-11-22
> **blueshiftoverwatch said:**
> That doesn't sound too bad.

What encryption application would you recommend using? A friend who's really into security said that he's using Fedora over Ubuntu because it gives you the option to encrypt your entire disk by default. But when you have to set it up after the OS is already installed it's a huge pain.

Full-disk encryption is easy with Ubuntu if you use the Alternate CD installer. I just did it this afternoon and it takes maybe 60 seconds longer than a regular installation. I've never noticed any performance hit with LUKS full-disk encryption on any relatively new computer, and personally I think it's a bit more stable than home directory (+swap) encryption.

---

### Post by HermanAB on 2009-11-23
Howdy,

The performance hit is negligible.  While compiling a kernel I have measured it to be about 3% slower with full encryption.  So if you want to recover that little penalty, simply change from Ext3 to JFS or XFS.

---

### Post by blueshiftoverwatch on 2009-11-24
> **HermanAB said:**
> The performance hit is negligible.  While compiling a kernel I have measured it to be about 3% slower with full encryption.  So if you want to recover that little penalty, simply change from Ext3 to JFS or XFS.
Or Ext4 if I wanted to live dangerously. From what I've read Ext3 and 4 are designed as good general purpose FS's while JFS and XFS are specifically designed for handling large files quickly, at the expensive of handling smaller files quickly.

---

### Post by scorp123 on 2009-11-24
> **blueshiftoverwatch said:**
> Or Ext4 if I wanted to live dangerously. Ext4 is stable now. And fast as hell. I use it on my fully encrypted disks and if I wouldn't know that the disks are encrypted I wouldn't be able to notice anything.

> **blueshiftoverwatch said:**
>  JFS and XFS are specifically designed for handling large files quickly Yes. But XFS *can* have ugly side effects, e.g. on certain systems and with certain disks it doesn't take sudden power failures lightly. On a bad day when and if XFS crashes (e.g. sudden power failure) whatever file happened to be open at that time may end up being overwritten with binary 0's ... result: empty files.

Imagine this: You're watching a movie. These days that would be a ~700 MB *.avi file of some sorts. And suddenly there's a power failure ... bammmm, everything turns dark. The lights come back on, you boot your computer again with the intent to continue the movie ... only to find an empty file now.

This has happened to me. And to others, e.g. here:

"XFS Destroys Files"
[http://ubuntuforums.org/showthread.php?t=1025412](http://ubuntuforums.org/showthread.php?t=1025412)

I used to have XFS on my servers ... but since Ext4 is out I've been switching my systems over to Ext4. So far it has survived all crashes, e.g. we intentionally unplugged a running server from power just to see if Ext4 would lose any data ... So far everything seems OK. The nice thing about Ext4 seems to be that it is reliable as Ext3 but performs as well and fast as XFS.

I personally would not recommend to use XFS on a system that has no UPS. If sudden power failures are an issue then you risk losing files with XFS. And with full-disk encryption this only gets worse.

So if you want known reliability: Use Ext3. If you trust the kernel developers and their promises that Ext4 is stable now: Use Ext4. As I said: It's really really fast and I have not experienced any weird issues with Ext4 so far.

Also the support forums seem to be silent regarding Ext4 troubles? I'd assume that if there were any obvious problems we'd see far more postings and complaints in the support sections ... ?

---

### Post by blueshiftoverwatch on 2009-11-24
> **scorp123 said:**
> I personally would not recommend to use XFS on a system that has no UPS. If sudden power failures are an issue then you risk losing files with XFS. And with full-disk encryption this only gets worse
Does JFS have all the benefits of XFS but less risk of data corruption?

---

### Post by bodhi.zazen on 2009-11-24
> **blueshiftoverwatch said:**
> Does JFS have all the benefits of XFS but less risk of data corruption?

IMO, yes.

I would also add that in the vast majority of cases you are not going to notice the performance of various file systems on your disk and I would take benchmarks with a large grain of salt. How many times do you create then delete 10,000 i Kb files ?

Also there is more to consider then benchmarks.

[http://www.linux.com/feature/31939](http://www.linux.com/feature/31939)
[http://www.linux.com/articles/31966](http://www.linux.com/articles/31966)

As with most things you will find better performance with better / faster hardware.

With all that said, I have seen noticeable differences on older low end computers. On such systems I think ext4 is as fast as jfs or xfs.

I would also say that data loss with xfs, from personal experience, can be more then 1 file, it can be the entire partition / hd. And it is not limited to power failure, it can happen if you system locks up and you need to do a hard re-boot (pull the power cord or hold the power button).

Of the 3 file systems you mentioned my advice would be ext4 > jfs > xfs

---

### Post by viking_maniac on 2009-12-03
I'm trying Ubuntu 9.10 64-bit with LUKS full disk encryption.
 
At first glance, it seems to go pretty well. But when I use TrueCrypt in addition to encrypt second partitions/drives, then something weird is happening: the mouse is actually lagging during some light work! Even though the CPU is almost resting at a few percents, the mouse actually lags when moving it. That disappointed me big time since this has _never_ happened on any Windows machine of mine; even not when all cores are working at 100% continuously.
 
I don't know what the issue is, since I've asked about this and not gotten any replies. I don't know what causing this, if it's "normal" on Ubuntu/Gnome/Linux or not.
 
:confused:

---

### Post by michaelzap on 2009-12-03
> **viking_maniac said:**
> I'm trying Ubuntu 9.10 64-bit with LUKS full disk encryption.
 
At first glance, it seems to go pretty well. But when I use TrueCrypt in addition to encrypt second partitions/drives...

You're using TrueCrypt in addition to LUKS?!? Use one or the other, but not both. That's a sure-fire way to slow your computer down to a crawl and then lose all of your data on the first disk error.

If you need to encrypt Windows partitions, stick with TrueCrypt and you'll be fine.

---

### Post by fargle on 2009-12-04
> **michaelzap said:**
> You're using TrueCrypt in addition to LUKS?!? Use one or the other, but not both. That's a sure-fire way to slow your computer down to a crawl and then lose all of your data on the first disk error.

If you need to encrypt Windows partitions, stick with TrueCrypt and you'll be fine.

I don't agree - I use full-disk encryption, with LUKS doing the system partition, swap, and my user home partition, along with Truecrypt doing the rest of the drive, and no problems whatsoever.  I've been doing this with no problems since Hardy on a Dell XPS M1330 that's about 1.5 years old with a Core Duo 1.6 gHz processor.  I don't notice encryption at all, other than possibly a somewhat noticeable impact when doing bulk backups off a Truecrypt volume onto an external Truecrypt volume.

This laptop isn't exactly a powerhouse for this day and age, so I'd say there's something else going on.

---

### Post by Demosthenesaus on 2009-12-08
I've got a MSI Wind U100 dual Intel Atom 1.6GHz normally running at 800MHz for power saving.  I installed Ubuntu 9.01 with full disk encryption (except /boot of course) and also enabled /home encryption for the fun of it to see what would happen.

I can't say I've really noticed any difference.  I guess I will notice in the battery life if there is an issue, but so far ok.

Is running LUKS and /home encryption at the same time a really bad idea?  I'm tempted to go back and re-install to disable it unless there is a way to disable it without re-installing?  I thought seeing it is a shared netbook between a few users that /home encryption would not be a bad idea if it did not cause problems?

---

### Post by michaelzap on 2009-12-08
Just seems kind of redundant to me, but if you don't notice a performance hit maybe it doesn't matter. Of course that also gives you two ways to lose your data in the event of an encryption failure of some kind. That's never happened to me, and I suppose if you have your data backed up it's irrelevant anyway.

---

### Post by Demosthenesaus on 2009-12-08
Is there any easy way to remove /home encryption without having to re-install?

---

### Post by michaelzap on 2009-12-08
> **Demosthenesaus said:**
> Is there any easy way to remove /home encryption without having to re-install?

I would think you could just create a new user with an unencrypted home directory and copy all of your files and settings to that user's home directory (and you probably need to chown it all to that user when you're done).

---

### Post by blueshiftoverwatch on 2009-12-08
> **Demosthenesaus said:**
> Is there any easy way to remove /home encryption without having to re-install?
Why would you want to unencrypt /home? If anything, that's teh directory that you'd want to encrypt if nothing else because if your like most people, all of your personal information is stored there.

---

### Post by scaine on 2009-12-09
> **blueshiftoverwatch said:**
> Why would you want to unencrypt /home? If anything, that's teh directory that you'd want to encrypt if nothing else because if your like most people, all of your personal information is stored there.

Because he's already LUKS enabled his entire disk anyway (see his previous post).

Sorry, I have no idea how to undo encryption.  Possibly search the Ubuntu WIKI?

---

### Post by Demosthenesaus on 2009-12-09
It was easier to just reinstall without /home encryption and just full LUKS encryption.  Even on the tiny netbook I can't really tell a difference, but it's just for net surfing and email anyway.

---

### Post by blueshiftoverwatch on 2009-12-12
> **scaine said:**
> Because he's already LUKS enabled his entire disk anyway (see his previous post).
Oh, I misread what he was saying.

---

### Post by Jekshadow on 2009-12-12
I have two layers of encryption running (Drive + Home Directory) and I do not notice any slowdown at all.

---

### Post by blueshiftoverwatch on 2009-12-26
Encryption is a huge pain, I've decided to go without it.

I just tried out OpenSUSE and encrypted swap, /home, and the partition where I keep my virtual machine HD images. You can't encrypt / by default (even if /boot is on a separate non-encrypted partition) without going through a [huge ordeal]("http://en.opensuse.org/Encrypted_Root_File_System"). I have to type in a long passcode for each encrypted partition at startup and I can never get the thing exactly right without having to type it in at least 3 times for each partition, and I'm young and have steady hands. I don't know how people do it. For that matter, I don't know how people of my parent's generation ever typed their papers on a type writer where you had to manually edit typos with whiteout either.

When I factor that into the equation. I guess I don't really **need** disk encryption.

---

### Post by BkkBonanza on 2009-12-27
I think the ecryptfs encrypted home is pretty sweet. You can use a usb key if you really want to have 2-factor authentication (I currently don't need that) and you only have your normal login password to mount it when booting. No hassle at all and you at least know that when your notebook gets stolen the data isn't going to be explored. That's really what most people need without getting too paranoid. 

On current computers I'd just get rid of the swap before I'd bother encrypting it. I watch it's use with conky and it rarely ever gets touched. You can get all crazy about possible vulnerabilities but then you may just end up not doing anything because the hassle factor is too high. 

If you seriously have the need for 100% confidentially then you just have to live with the extra work involved. I don't have anything on my machine I'd go to jail for. The chances of someone going to extremes to gain my data are remote, and the consequences minimal. All security decisions need to factor in the time element, risk and degree of consequences involved before deciding how far to take it.

Regarding performance - according to Dustin Kirkland, who was involved with the ecryptfs development on Ubuntu, the slowdown measured about 1%. Not something I'd worry about at all. You can gain that back and more by using ext4. He has a tutorial on his blog for converting your home to an encrypted home that only takes a few minutes to do. 

IMHO this is an easy solution that gets you 99% of the way there. It may not handle every possible attack vector but it handles the most likely ones.


PS. I combine this with periodic use of sfill and srm (secure delete package) to clean things up now and then. If I want to delete something that may be important I secure delete it (have it integrated into Nautilus). And every few weeks I wipe the free space with sfill.

---

### Post by blueshiftoverwatch on 2009-12-27
> **BkkBonaza said:**
> I think the ecryptfs encrypted home is pretty sweet.
Is this the same as the ability to encrypt /home during Ubuntu's installation?
> **BkkBonaza said:**
> periodic use of sfill and srm (secure delete package) to clean things up now and then. If I want to delete something that may be important I secure delete it (have it integrated into Nautilus). And every few weeks I wipe the free space with sfill.
I've used those tools before, very neat stuff.

---

### Post by BkkBonanza on 2009-12-27
Yes. In the recent version installs this option is implemented using ecryptfs.

---

### Post by blueshiftoverwatch on 2009-12-28
> **BkkBonaza said:**
> Yes. In the recent version installs this option is implemented using ecryptfs.
The only bad thing is that the encryption password is the same as your user password. So if you want a password that is actually secure and not easily cracked you'd have to make it much longer. But you'd also have to enter in that long password every time you wanted to do an administrative task involving sudo.

---

### Post by Jekshadow on 2009-12-28
> **blueshiftoverwatch said:**
> The only bad thing is that the encryption password is the same as your user password. So if you want a password that is actually secure and not easily cracked you'd have to make it much longer. But you'd also have to enter in that long password every time you wanted to do an administrative task involving sudo.

Not fully true, your login password is used to encrypt another randomly generated password that is used to decrypt your home directory. Also, about the long password, you get used to it over time, and you begin to type it faster. I have a login password that's over 30 characters and composed of random characters for my normal password, and I can type it in in under five seconds.

---

### Post by BkkBonanza on 2009-12-28
As I mentioned, if you want that extra step of security with ecryptfs home encryption then the best thing is to symlink the key file. Your password allows decrypting the key file but if the key file is on a usb key then they need that as well as your password. 

The key is much longer and more random than your password. It usually sits in /home/.ecryptfs/<user>/.ecryptfs/wrapped-passphrase but if you replace that with a symlink to your usb key then it can be kept there instead. You also need to add an entry in fstab so that usb key volume gets consistently mounted somewhere for the symlink to work.

This method then gives you easy-to-use 2 factor authentication where you need the password and the key. I keep one of those really small ones on my key ring so it's always in my pocket. Even if someone can brute force the password they won't get the  data without my keyring. I generally use an 8 char fully random password as well, so it's moderately secure and easy to use.

---

### Post by michaelzap on 2009-12-28
If you are the only user of this computer then LUKS full-disk encryption might be a better option. You'd enter one password to decrypt the disk at boot and then your user password would be separate. After trying out encrypted home on my recent Ubuntu installations for the last few months I'm probably going back to LUKS from now on.

---

### Post by BkkBonanza on 2009-12-28
Obviously we're now going around in circles. My suggestion to use encrypted home was for the user above who was using full disk encryption and was fed up with entering extra passwords for each partition at boot, in addition to the login password. I mean, you either have the extra hassle or you don't... take your pick.

Unsubscribed.

---

### Post by blueshiftoverwatch on 2009-12-28
> **Jekshadow said:**
> Not fully true, your login password is used to encrypt another randomly generated password that is used to decrypt your home directory.
Is there any limit to how long you can make your Ubuntu user password? If no, will using a longer password (like a pass phrase) interfere with certain applications that may ask you for your password?

---

### Post by blueshiftoverwatch on 2009-12-30
I noticed that after I logged onto Ubuntu it asked me to make a custom passphrase instead of the default randomly generated one in case something happened to where the system didn't boot and I needed to manually decrypt my information to recover it.

A terminal window came up where I put in the passphrase. But it didn't ask me a second time for my passphase. That seems kinda risky for ever a standard password. Let alone a pass phrase. The Ubuntu devs should probably do something so that it asks you a second time and calls you out if the two aren't exactly the same.

---

### Post by DouglasAWh on 2011-10-23
For those of you saying FDE is not noticeable, what sort of hardware were you running?

I just booted up an IDE drive without encryption with 8.04 and it runs MILES faster than my SATA drive with encryption running 11.04. I don't know if it is 11.04 that is slow or the drive but I was absolutely floored at how quick the drive was.

The machine in question is a P4. Yeah, I'm rockin' it old school.

---

### Post by fargle on 2011-10-25
Well, I have a Dell XPS M1330 laptop with a 4500 RPM drive, 500 GB.  It has a Core 2 Duo 2.0 GHz and 2 GB of RAM.

I have /boot unencrypted, root encrypted with LUKS, swap encrypted with LUKS and a random key, a ramdisk for /tmp, my home directory mounted when I log in with pam-mount (LUKS), and about 450 GB of the drive encrypted with TrueCrypt, which is where most of the data is stored, of course.

So, this is definitely not a powerhouse system!

Having laid that out - I don't notice FDE at all, except in one case: when I hook up a USB drive also encrypted with TrueCrypt and back up the big partition.  In that case, it maxes the CPU handily and I think there's a bit of a performance hit with the double encryption.  Even then, though, that's a big bulk operation that I can let run without caring.

In short, even on this older box (3.5 years old) it works well.  When I upgrade next year, I don't think there will be much of a chance of noticing it under any scenario.

---

### Post by DouglasAWh on 2011-10-26
> **fargle said:**
> In short, even on this older box (3.5 years old) 

The box I am talking about is 8 years old, but fair enough.

---

