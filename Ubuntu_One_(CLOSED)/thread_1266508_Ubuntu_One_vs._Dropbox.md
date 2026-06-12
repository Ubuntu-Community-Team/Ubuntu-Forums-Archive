---
title: "Ubuntu One vs. Dropbox"
date: 2009-09-14
forum: Ubuntu One (CLOSED)
---

### Post by cprofitt on 2009-09-14
I just found a service called Dropbox ([http://www.getdropbox.com/](http://www.getdropbox.com/)) and was curious how this stacks up vs. Ubuntu One.  I have not used either one... but from reading the details they seem similar in function, but dropbox is cross-platform.

---

### Post by andrea000 on 2009-09-14
I like ubuntu one a lot better and they keep
adding features to it.Ubuntu one will not be
beta software for long.

---

### Post by aysiu on 2009-09-14
> **cprofitt said:**
> I just found a service called Dropbox ([http://www.getdropbox.com/](http://www.getdropbox.com/)) and was curious how this stacks up vs. Ubuntu One.  I have not used either one... but from reading the details they seem similar in function, but dropbox is cross-platform. You may also want to take a look at SpiderOak.

It's cross-platform but also offers you privacy and encryption.

---

### Post by cprofitt on 2009-09-14
SpiderOak is offering 50% off for EDU accounts too... this could work for the people that showed me dropbox.

---

### Post by jruschme on 2009-09-21
> **cprofitt said:**
> I just found a service called Dropbox ([http://www.getdropbox.com/](http://www.getdropbox.com/)) and was curious how this stacks up vs. Ubuntu One.  I have not used either one... but from reading the details they seem similar in function, but dropbox is cross-platform.

Dropbox is cross-platform, but the dropboxd daemon only supports Linux on x86 (maybe 64 also). OTOH, the Ubuntu One client is mostly hardware independent and the rest is easily built from source; this makes it nice if you are running Ubuntu on PowerPC, for instance.

---

### Post by aysiu on 2009-09-21
> **jruschme said:**
> Dropbox is cross-platform, but the dropboxd daemon only supports Linux on x86 (maybe 64 also). OTOH, the Ubuntu One client is mostly hardware independent and the rest is easily built from source; this makes it nice if you are running Ubuntu on PowerPC, for instance.
SpiderOak is cross-platform and supports 64-bit (not PowerPC, though).

---

### Post by Fl0ris on 2009-09-21
One of Ubuntu One's benefits is the fact it's open source which can be quite helpful for quick and innovative development. Currently I prefer Dropbox but maybe that'll change.

O.T. if you'd like to try Dropbox, here's a referral link (get 250 MB = 0,25 GB free extra space): [https://www.getdropbox.com/referrals/NTE4NjE5MDY5 ]("https://www.getdropbox.com/referrals/NTE4NjE5MDY5")

---

### Post by MrMasa on 2009-09-22
I have been using both. Ubuntu-one is very attractive but sometimes won't syncronize files in cloudy. Then I usually use Dropbox for work. Now I heard another option, "spider oak". I will try it soon.

---

### Post by MKdx on 2009-09-22
> **jruschme said:**
> Dropbox is cross-platform, but the dropboxd daemon only supports Linux on x86 (maybe 64 also). OTOH, the Ubuntu One client is mostly hardware independent and the rest is easily built from source; this makes it nice if you are running Ubuntu on PowerPC, for instance.
Then we can have UbuntuOne on ARM handhelds/phones, which would be pretty nice.

---

### Post by tatewaki on 2009-09-24
I was wondering if there are some application that makes it possible to set up a "dropbox/ubuntuone" service on our own server?

---

### Post by Fl0ris on 2009-09-26
> I was wondering if there are some application that makes it possible to set up a "dropbox/ubuntuone" service on our own server?
Currently not, Dropbox will add it in the future, I don't know what Ubuntu One's plans are.

---

### Post by joshuahoover on 2009-09-29
> **Fl0ris said:**
> Currently not, Dropbox will add it in the future, I don't know what Ubuntu One's plans are.

In the future, we're going to provide the ability to sync across a local network without any interaction with our server. This is a ways out, but it is on our roadmap.

---

### Post by Wise Ferret on 2009-09-29
Currently Dropbox has two important advantages that keep me from moving to Ubuntu One:

1. Symlinks support. With Dropbox I know every document I have in my Documents folder is safe on the web the moment I saved it with my editor application.

2. Politeness and manners. Ubuntu One is hard-coded to create its folder in my home folder. I like my home folder neat - it is a home, after all - and I want nothing but my own custom folders there. Dropbox allows me to choose where I want it located, while Ubuntu One treats my home folder like its back yard.

---

### Post by joshuahoover on 2009-09-30
> **Wise Ferret said:**
> Currently Dropbox has two important advantages that keep me from moving to Ubuntu One:

1. Symlinks support. With Dropbox I know every document I have in my Documents folder is safe on the web the moment I saved it with my editor application.

2. Politeness and manners. Ubuntu One is hard-coded to create its folder in my home folder. I like my home folder neat - it is a home, after all - and I want nothing but my own custom folders there. Dropbox allows me to choose where I want it located, while Ubuntu One treats my home folder like its back yard.

Hi Wise Ferret,

These are two of the more popular feature requests we get for Ubuntu One. We intend on delivering these in a future release.

Thanks,

Joshua

---

### Post by Fl0ris on 2009-10-01
New feature in Dropbox' last forum release: the option to sync via LAN... Faster than via their server.

---

### Post by Cato2 on 2009-10-03
I've used and given up on both Dropbox and SpiderOak, using Ubuntu Gutsy and Hardy.  I last used Dropbox in early 2009 and SpiderOak in mid 2009.  They both have some nice features, but here I am going to focus on the parts that don't work well, as you can read about the features elsewhere.

Unfortunately, I have to recommend you avoid both these services, because they are just too immature to be used, at least in my experience. Other people may have quite different experiences - I wanted a backup service primarily, and I had a lot of files (over 100,000), which maybe stressed them too much.

I wasted a lot of time trying to get both services to work. I really wanted to just buy a solid Linux backup service that was priced for a home user, but I didn't find it in these two at least.  This may sound like I have an axe to grind, but I am just a very disappointed customer.  

Bottom line: I lost some less important data with Dropbox, finding it not suitable for Linux file permissions. With SpiderOak I found a vast amount of data had not been backed up, without any warning error messages, and recovery failed in several ways as well.

I'm a Linux geek since mid 1990s, so it wasn't a lack of technical expertise either...

**DropBox**
[LIST]
[*]I tried to sync 50GB of files from Linux but couldn't get more than 2 GB to sync (on a paid account)
[*]Really Dropbox is a sync application, and is not designed for (or good at) doing backups.
[*](When I tried it at least) Dropbox did not support Linux file permissions, so you could only use it for file where this doesn't matter, e.g. plain data files but not your ~/.ssh directory and certainly not /etc (which I tried).
[*]Dropbox got confused about which side was master at one point so it synced my server-side /etc files on top of my newer /etc files on the PC.  Not helpful for something I was trying to use for backups...
[*]A lot of people seemed to be having problems with syncs not completing, but the Dropbox team were adding new features rather than focusing on reliability.  
[*]Doesn't provide specific error messages when things go wrong, i.e. your data is not being synced.
[*]Support was helpful generally but couldn't solve these problems before I gave up.
[/LIST]

**SpiderOak**
[LIST]
[*]Generally worked better re file permissions and two-way syncing.
[*]Very heavy on machine, and slow, when using a large number of files (100,000 plus).  I used this on a couple of PCs, both modern dual core based with 1 GB or 4 GB RAM.  Despite this, I had to frequently disable the SpiderOak client or set it to run at night, because the PC became unusable.  In the 1GB PC's case, SpiderOak started using swap so much that I could barely kill the client - ironically it was just pulling down the 100,000 filenames synced from the other PC, which I didn't need on that PC. (SpiderOak does this for all machines in your account, no way to turn it off I'm aware of.)
[*]Unreliable connection to servers.  Often would not be able to connect, or would take so long I'd give up.
[*]No access control on retrieval. Any SpiderOak client on the same account can see and download any file from any other client PC.  Only usable for a set of PCs used by people you trust implicitly.  No way to restrict this I could find.
[*]Good encryption model, but when you have errors you may have to send in log files which expose more details.  Also logging into their website even for forums breaks this model, as the forums use your main password used for web access to data.
[*]Very hard to track what is going on.  Unlike a backup tool, SpiderOak is based on continuous syncing, but it's very hard to check if it's working OK.  I had such a huge queue at most times that it was difficult to know if it was near finishing, and the client UI was hard to understand (although I'm a Linux geek, many terms aren't defined).  The client doesn't provide any useful specific errors on what has gone wrong.
[*]Silently failed to back up my data.  In one case this was a near disaster, because the PC had lost thousands of files (due to ext3, LVM and disk level writeback caching - "hdparm -W0 /dev/sdX" is strongly recommended!!), yet SpiderOak had failed to back up 95% of the files, including all the digital photos...  In another case I didn't have a PC crash but I noticed SpiderOak didn't backup my files for at least a month, without me noticing.
[*]Recovery failed in a couple of ways when I needed it.  First, the GUI client wouldn't download files (got stuck after a few files, but I had about 10,000 files to recover over tens of directories), then when I tried the web client, it recovered some directories but generated a corrupt and truncated ZIP file for the largest directory. 
[*]Support took several days to respond about recovery problems, and wasn't able to fix the problem. 
[/LIST]

What do I use for backup now?  I did look at some other backup/sync services but decided using open source tools would be more reliable given my experiences with these two. 
[LIST=1]
[*]sbackup (Simple Backup Suite - type "sudo aptitude install sbackup" or use Synaptic) - this is a GREAT simple tool that automates the whole backup process, almost no technical expertise needed to ensure that /home, /etc and so on are backed up.  You do need to configure it to point to an external drive, a NAS, or another PC with Windows filesharing (otherwise your backup is just more files on the same disk, which is not really a backup).  But it has a nice simple user interface, makes recovering files easy, takes care of scheduling everything, has sensible defaults, and even gets rid of older backups using a sensible scheme.  **If you don't have backups now, try using sbackup** - although it's not offsite backup it's the closest I've seen to Mozy for an easy to use backup tool on Linux.
[*]For offsite backups, I have a more complex setup using a combination of DAR (strongly recommended if you like a file archive approach, can do encryption and archive splitting, better than tar) and rsnapshot (using this now, great if you have enough disk space - very easy recovery, very fast backups, efficient use of network through rsync, can back up webhosts without installing software on them.)  However, a non-geek would have challenges getting this working as rsnapshot/rsync relies on SSH quite heavily.
[/LIST]
There are many other backup tools out there.  BackupPC is very complete, but with bigger learning curve and optimised for businesses / enterprises.  Duplicity and rdiff-backup are somewhat like rsnapshot but have disadvantages in my view for large amounts of data.

For syncing, I hope Ubuntu One will learn from these mistakes, but I'd expect that it will take a year or two to mature fully.  In the interim you might want to look at using Unison (two way syncing for Linux and Windows, open source) and a separate server, perhaps a web host.

---

### Post by zekopeko on 2009-10-03
@Cato2

Those services aren't meant to be used as backup software. They are sync services. Vast difference there.

---

### Post by itsbrad212 on 2009-10-03
i just started using ubuntu one on 9.04, and it looks promising. I wish that it came with more then 2GB

:(

---

### Post by zekopeko on 2009-10-04
> **itsbrad212 said:**
> i just started using ubuntu one on 9.04, and it looks promising. I wish that it came with more then 2GB

:(

You can pay for more...

---

### Post by Cato2 on 2009-10-04
> **zekopeko said:**
> @Cato2

Those services aren't meant to be used as backup software. They are sync services. Vast difference there.

Actually they are marketed as backup services, not just sync:
[LIST]
[*][https://spideroak.com/](https://spideroak.com/) mentions 'online backup' very prominently (first of three headlines).  

[*][http://www.getdropbox.com/](http://www.getdropbox.com/) doesn't say much on the front page but the prominent Take a Tour link leads to a page where Online Backup is mentioned as the third major feature.
[/LIST]
Since both support storing multiple versions of a file, they could be used as backup services, or even near-CDP (Continuous Data Protection) services, if they sorted out the sort of problem I'm talking about (which might need some redesign).  They would also need better error logging, like Mozy which does continuous backups as well as scheduled backups, but reports for each backup attempt with a summary of what it did (including any error status) and lets you see a detailed log file to troubleshoot errors.  

Dropbox and SpiderOak are not suitable for whole-system backup unless you first back up all files to an archive, but they could do the sort of backups that Mozy or Carbonite do on Windows, i.e. backup your most important data, which is what I wanted.

---

### Post by Kapitän Rotbart on 2009-10-04
I got DropBox and Ubuntu One. I guess it's a little inconvenient to use both rather than having the best of both worlds sync'd into one folder, but at least there's competition!

Dropbox allows me to share files between Ubuntu and my XP virtual machine. This also allows me to share files with other windeuce machines, which is quite convenient.

Ubuntu-One is Ubuntu-focused, so it's probably great for sync'ing multiple Ubuntu machines (sync Evilution mail, etc.). That's quite awesome, especially when I'll get my netbook just before Karmic's release.

I'm really glad to see the competition between these applications, this should make for rapid innovation! :D

---

### Post by tc101 on 2011-01-06
This is the most recent comparison of the two products I could find.  The author thinks Dropbox is better.


[http://www.brighthub.com/hubfolio/matthew-casperson/articles/75004.aspx](http://www.brighthub.com/hubfolio/matthew-casperson/articles/75004.aspx)

---

### Post by littlepeon on 2011-01-08
good article....in my experience the main difference is simple: its  that dropbox works and ubuntuone does not.
i have installed both on many (now 30+ machines for myself and others) and have had MANY problems with ubuntuone but very few with dropbox.
ubuntuone just is not ready for primetime--even though it is now part of a default install.
as always your mileage my vary--there are many people who have had NO problems with ubuntuone--just as there are many people who have had NO problems with the windows operating system, i and my friends are not in that minority.
at first one could say that canonical was working the bugs out of the system--however we are now years down the road and the same problems still exist. 
i have had files disappear/reappear/just freaky stuff happen with ubuntuone---so therefore i cannot recommend it till it is fixed--who knows when that will be..
i am NOT trying to argue with its supporters/staff just stating my observations..

good luck
--Peon

---

### Post by Docaltmed on 2011-01-09
> **littlepeon said:**
> good article....in my experience the main difference is simple: its  that dropbox works and ubuntuone does not.
i have installed both on many (now 30+ machines for myself and others) and have had MANY problems with ubuntuone but very few with dropbox.
ubuntuone just is not ready for primetime--even though it is now part of a default install.
as always your mileage my vary--there are many people who have had NO problems with ubuntuone--just as there are many people who have had NO problems with the windows operating system, i and my friends are not in that minority.
at first one could say that canonical was working the bugs out of the system--however we are now years down the road and the same problems still exist. 
i have had files disappear/reappear/just freaky stuff happen with ubuntuone---so therefore i cannot recommend it till it is fixed--who knows when that will be..
i am NOT trying to argue with its supporters/staff just stating my observations..

good luck
--Peon

+1.

I've been trying to use U1 for quite a while now, across several Ubuntu releases and multiple computers. The service is a terrible train wreck. I would love to use U1 because I'm such an Ubuntu fanboy, but the fact of the matter is that the service just doesn't work as advertised, or anywhere close to it.

---

### Post by lueckenhoff on 2011-03-16
> **littlepeon said:**
> good article....in my experience the main difference is simple: its  that dropbox works and ubuntuone does not.
...
--Peon

+1

I agree completely.

UbuntuOne/Dropbox reminds me of the MozillaSync/XMarks tussle.
(an outsider came in and did a great job, then the insiders tried to "take back" the lost mindshare)

Bruce

---

### Post by r-senior on 2011-03-18
+1

After problems in previous releases I just uninstalled it immediately when Maverick came along. It's having another trial on a Natty test machine (where it will stay until after official release as a fair test). 

The signs aren't good. It works for a while, then just gets itself in a twist. :(

---

### Post by jblaven on 2011-03-20
No experience with Ubuntu One, but I've used Dropbox in a mobile environment via an "iPad".  I'd have to say, it worked fairly well.  No complaints.  I could access the files across many platforms and from any location.  Very useful.

Joe

---

### Post by cub on 2011-03-21
As a student I have been frantic about losing my ongoing papers so I have made frequent copies to different computers and usb sticks. As I also do my work on three different computers I want to be able to always use the latest version. This meant a lot of copying. So I decided to have a go at this cloud thing I keep hearing about.

I started out with Dropbox since my friends use this. I has been working great actually for working on a team paper, where we can collaborate with the same documents. Well, there is no check out/check in (that we know of) so we need to keep track that we don't save the same document from different places. Other than that it's more or less perfect. Works with linux, windows and mac.

Being a ubuntu user I tried out Ubuntu One a long time ago but the sync was very random. I decided to give it another shot to be able to use the same folder on all three computers for my own work. It started out great and I was working at home with laptop 1. Booting my eee pc to let it sync, and keep working on the bus to work. At work the eee pc connected and uploaded the documents to Ubuntu One. It was a bliss. Until today. This weekend I have been working for two days straight with a paper. I save all this work directly in my Ubuntu One folder. I bring my eee pc to keep working on the bus and only get a three day old document. Crap. I get to work and my work pc also get a three day old file. Now I start to get a bit nervous, what if these two computers now have replaced the document I work all weekend with... I connect to Ubuntu One through Firefox and voila, three day old file. I start up my laptop where I did all the work, shut down the network to avoid any accidental syncing. Huge relief that the file in my Ubuntu One folder on THAT computer was the latest one. I copied it to several places.

I have been working directly in the Ubuntu One folder on all three computers. They have not been used at the same time, though they have been online. That might be a problem? Also I have not got any notice that "sync is complete" or "file uploaded" or "sync error" while working this weekend. During this work I got several notices from Dropbox that my friends had updated or uploaded files for the work we keep in Dropbox.

Yes, I might not be well educated in how Ubuntu One work. But compared to Dropbox I have the same knowledge there. I have followed the installation instructions to set it up on several computers. After that I prefer if it just works. So far, Dropbox has done that. Ubuntu One, I'm not so sure.

---

### Post by kerke on 2011-03-21
I installed Dropbox a couple of weeks ago on my Ubuntu 10.10 machines and on my office Windows 7 machine. It works very well and it syncs at light speed. With Ubuntu One, I drop a folder with just a few files in it at night, I come back in the morning and it's still syncing, and that's on all my Ubuntu 10.10 computers. I installed it on Windows and it doesn't even start. I absolutely love Ubuntu, but Ubuntu One just doesn't work for me. Can Ubuntu One be uninstalled?

---

### Post by Surachinen on 2011-05-17
personally, i use many of these backup services. im a sucker for punishment as long as i get free stuff.

i use dropbox for game saves, documents, .torrent files (not the actual downloads), and a good size picture collection. i maxxed out all the free space offers on dropbox for extra free space (lifehacker had an article on how). its great because i can share all the stuff on there with their built in tool to share things.

i use Ubuntu One for my music collection. my mp3 player only holds 2gb so i don't personally keep more than that in music. (not an avid music fan). the fact that i can stream this to droid makes this service great. if i get a bigger mp3 player, i might get a single '20 pack' of storage. another perk is the tomboy backup and contacts backup. i reformat every 6 months so this is a godsend for me

i use amazon cloud drive for my movie backups. they give you 5gb for free, and if you buy an mp3 album (i bought a $4 one) they give you a permanent upgrade to 20gb. i don't do blue ray, and most of my movies are 360p tv episodes. anything i don't give too much of a care about on this front i just burn to a data disk and throw in a safe i have.

in the 'vs' debate, i would say Dropbox wins in reliability, ubuntu one wins in features, and Amazon wins in price by a WIDE margin (though you pay by the year....)

i have not tried spideroak, but plan to look into it now. and a sheer hatred of microsoft kept me away from skydrive

---

### Post by spesheled1 on 2011-05-19
I really wanted to like Ubuntu One, but like others I have experienced problems with the sync function. I upgraded to Ubuntu 11.04 recently and hoped Ubuntu One might have better functionality, but it didn't happen. I ended up giving Dropbox a chance and it works great. Installation was easy on my Ubuntu and Windows machines. The best part about it is that it syncs perfectly! I would drop stuff in the Ubuntu One folder and the files would fail to upload. Now I drop files in the Dropbox folder and they upload without issue. I ended up removing Ubuntu One from my system. I plan on trying it again in the future though, but for now Dropbox certainly has the advantage over Ubuntu One.

---

### Post by vitorsouza on 2011-06-21
My experience is that Ubuntu One needs to improve in order to be a good replacement to DropBox. When I installed Ubuntu 10.04, I decided to give U1 a try because:

1 - For $3/month you can get more space, instead of the $10/month of DropBox (I don't really need 50 GB, 20 would be good enough);

2 - Better integration with Ubuntu.


However, the following issues made me switch back to DropBox for now (will probably try again when I install Ubuntu 10.10):

1 - U1 generates ".u1conflict" files for no reason: I'm working on a document, save it and my office app starts saying the document has been modified. When I check the folder, I see the conflicted versions. I'm the only one working on the file so I don't get where this is coming from;

2 - I could never get U1's Window client to work properly. Every time I go to Windows, U1's client consumes 100% of my CPU for a really long time and nothing happens. I liked being able to have my files available on Windows also.

Vítor Souza

---

### Post by -kg- on 2011-06-21
I'm not too keen on cloud computing myself, but as a heads-up to those using it (Dropbox specifically, but I would include all such services):

[Dropbox lets anyone log in as anyone - so check your files now!]("http://nakedsecurity.sophos.com/2011/06/21/dropbox-lets-anyone-log-in-as-anyone/")

Remember that anything you post on the web is only as secure as you make it.  Personally, I prefer to store my data locally.  Then, if it is compromised it's totally my fault.

---

### Post by waynerod on 2011-06-27
About the sync in Ubuntu One,

When I update my file, does the service delete the previous version and upload a new one? Or does it only update the changes? :confused:

---

### Post by jdunn on 2011-07-05
I tried Ubuntu One, then DropBox.  I like DropBox better because its more reliable for backing-up data.  DB also has more options and flexibility for the web version and standalone versions.  The standalone version of Dropbox is also less visually obtrusive in Nautilus than UO.  Also, DB works really well for backing-up TrueCrypt file containers when there is concern about security in the cloud.

---

### Post by jingaling on 2011-10-06
This might help:

[http://blog.jingaling.co.uk/2011/10/ubuntu-one-or-dropbox.html](http://blog.jingaling.co.uk/2011/10/ubuntu-one-or-dropbox.html)

---

### Post by mdshaver on 2011-10-13
My sentiment is similar to that of the previous posters. I am about to install 11.10. Has Ubuntu One significantly improved in reliability of sync since 11.04 or should I stick with Dropbox?

---

### Post by rft183 on 2011-10-14
Right now, I've been using both Dropbox and Ubuntu One.  I like having my data uploaded to both.  Redundant...? Yes! :)

---

### Post by rft183 on 2011-10-14
Also, I waited (paitently) until yesterday to install Ubuntu 11.10.  So I haven't had time to test U1 properly under 11.10.  Hopefully it is sitting synced when I get home.

---

### Post by CJ_Hudson on 2011-10-14
Dropbox no longer works after upgrading my system from 11.04 to 11.10.
Anyone else had similar problems?

---

### Post by rft183 on 2011-10-14
Well, it was not sitting synced when I got home, at least not according to U1.  Apparently, even though all of my files are in the directories (thanks to Dropbox's LAN sync), U1 doesn't realize that the files are actually up-to-date.  Instead it insists on re-downloading everything.  Ugh...

I just hope that once it is done re-downloading everything, there are not a zillion conflict files.

---

### Post by The Bright Side on 2011-10-15
Hey guys,

I just moved to 11.10 and am considering going to U1 from Dropbox as well. So I tooled around a bit with that and for what it's worth, here's what I found:

- First, let it be known that my desktop is still running 10.10, and my laptop is on 11.10 (GNOME Shell), both 64 bit.

[LIST]
[*]It still seems to take a while until U1 realizes that files have changed
[*]It still creates a "conflict" file instead of just updating a file when I create a newer version
[*]Sync is very slow
[*]I don't think there currently is a working U1 indicator for 11.10 (correct me if I'm wrong)
[*]Information about synchronization (e.g. % completed) is lacking. It only says "In Progress".
[/LIST]

I'll see how this changes when I have both my machines on 11.10, but I kinda see myself sticking with Dropbox for the time being. Dropbox responds within fractions of a second and updates my stuff super-fast.

On the bright side, comparing U1 in 10.10 with the one in 11.10, there is quite a lot of improvement. I think it even lets you move the U1 folder where you want it and will just remember the new position on its own. In a couple more releases, this will be a great replacement for Dropbox.

Hey, does anybody know if Dropbox works well with GNOME Shell? Does it have its own indicator?

---

### Post by vitorsouza on 2011-10-15
> **The Bright Side said:**
> Hey, does anybody know if Dropbox works well with GNOME Shell? Does it have its own indicator?

It sits in the notification bar (the one hidden at the bottom of the screen), just like an icon in a system tray (together with Skype, Empathy, Pidgin or whatever). I haven't upgraded to 11.10 yet, so my experience is from 11.04 with gnome-shell installed from the PPA.

HTH,
- Vitor

---

### Post by cub on 2011-10-15
I just upgraded my eee-pc with 11.10 and Dropbox seems to work as before.

---

### Post by SkyeFerret on 2011-10-15
The only feature missing from Ubuntu One that Dropbox has is a web interface for sharing / downloading / uploading / viewing files. I didn't use that too often when I was using Dropbox, but it's a great feature to have should the need arise and you have no other way of sharing the file.

Ooh, lookie! [https://one.ubuntu.com/files/](https://one.ubuntu.com/files/)
</oblivious>

---

### Post by Musmanno on 2011-10-17
I've always used Dropbox. I tried Ubuntu One, and it seemed like Dropbox was just more responsive in terms of syncing files. That said, I haven't tried Ubuntu One since early in the history of that service, so it may have improved.

Right now, the devs are ensuring that I stick with Dropbox, because I dislike Unity and Ubuntu One doesn't seem to show up in Gnome anywhere. 

I can't think of a reason not to use Dropbox. I've been using it for years and it is a great service.

---

### Post by pete04 on 2011-10-17
It's installed in xubuntu, both 11.04 and 11.10, so if you don't like Unity, you always have that option. I've found xubuntu to be really pretty nice and polished. DOn't feel like I'm missing much from gnome at all.

 Have had some trouble syncing U1, but I'm hoping it's just the result of load on Ubuntu's servers and will improve. The instant photo syncing for android is the main reason I want to use it.

---

### Post by rft183 on 2011-10-18
U1 finished re-syncing a couple days ago. While I was annoyed that it was downloading everything when the files already existed, it was fairly quick with my 12.5 gb.

---

### Post by Dragonbite on 2011-10-18
Dropbox works fine in 11.10.  If it doesn't, or you are running a combination that Dropbox doesn't offer (like KDE on Fedora) then just go with the server install. It works just the same except you don't get the icon on the folders as to the sync status but you do get the system tray icon with the current status and ability to pause synchronization.

I'm not fully buying into Ubuntu One because I am using across multiple distributions (like Fedora) as well as Windows.  Plus my Chrome/Chromium browser includes a "Cloud Share" which means I can have it automatically save a file, picture or whatever I (right)click on to my Dropbox.  I would love it if they could add Ubuntu One to the list.

So far.

---

### Post by joaoguimaraes on 2011-10-18
Ubuntu one and dropbox are very similar, both doo the same thing, and now ubuntu one is avaible for windows, so you can syncronise your files in Microsoft OS to.

---

### Post by goldentony111 on 2011-10-19
which is better

---

### Post by The Bright Side on 2011-10-20
I'm sticking with Dropbox. It's the one I would recommend. U1 still responds slowly.

---

### Post by alexpotter on 2011-10-20
Ubuntu One is great and all but when I tried to share a folder with my friend he couldn't see it. Also it took ages to upload a simple folder of JPEG images (not big in size). I do like Ubuntu One's dashboard and it's 5GB storage but I prefer Dropbox.

Despite Dropbox only having 2GB of space, you can refer friends and get more space. Currently I have maxed out my invites (running at 8GB) and I like Dropbox's speed most of all. It syncs really quickly and to everyone else who is sharing that folder. And because I run Ubuntu x86, I have no probs with Nautilus integration and stuff. Also Dropbox is cross-platform which I like, so my friends on Windows and my other friend on a Mac can view the files I put in (and some Android and iOS devices as well) 

For me, it's Dropbox FTW. It can't be matched by Ubuntu One (yet) in my own opinion. Obviously Ubuntu One will get better but I prefer Dropbox for now. :)

---

### Post by Dragonbite on 2011-10-20
The music and smartphone features don't interest me, since I don't buy much music and I don't have a smartphone.

The Bookmark feature is dead.

The Contacts feature doesn't seem to work since I upgraded to 11.10 (and Thunderbird).

I don't really use notes.

So there isn't too, too much different for me and how I use it between Ubuntu One and Dropbox.

So now I currently use Ubuntu One's 5 GB space for Deja Dup to back up to, and Dropbox for my regular file synchronization.  A few of the Pro's for Dropbox[LIST]
[*]Synchronize over LAN
[*]Platform/Distribution independent
[*]Manageable web interface (can move, copy and delete as easy as a local file manager)
[*]Speed
[*]Integration with other application/extensions such as Cloud Save fro Chrome/Chromium
[/LIST]

For me the Pro's for Ubuntu One are much shorter [LIST]
[*]Installed on Ubuntu 
[*]Can select different files to sync, instead of having to put them all under the Ubuntu One folder
[/LIST]

Even with this, though, I want to see Ubuntu One grow into a real competitor for Dropbox (and the others), and to help prop Ubuntu up against Apple (and iCloud) and Windows (and SkyDrive)!

Maybe, and this would be awesome, if LibreOffice gets their could-based interface working, then have Ubuntu One not only enable you to save your files and synchronize, but also open and edit files through the browser (and it saves in your U1 location) *and* you can open it locally in Ubuntu!

---

### Post by SneakPeak on 2011-10-20
Hi

I live in South Africa and I was really keen to use Ubuntu one on 11.10 but it was completely useless.  The upload speed was very, very, very, very, very, very, very, very slow.  In 4 days I managed to upload only 3MB.  I just tried DropBox and although it is slow I got 30MB up in ten minutes.  It seems South Africa's internet connections are just too slow for Ubuntu One.  It is a pity.  I would like more than the 2GB DropBox offers free but I don't want 50MB which is their next size up. (too expensive for me).

Cheers

Sneaks

---

### Post by Rifester on 2012-01-02
I currently looking for off site storage for my family photos & videos.   Nearly all of my family pictures & video are stored on our computers and I would like to have them safe in the event that something would ever happen to our house.   I have three Linux computers that I sync every month and back up to an external hard drive.  I have about 20G of pictures & videos.   Has anybody successfully set up this amount of data on Ubuntu One?   Can you sync the folders successfully between multiple computers?   I would I would prefer to support Ubuntu One but it seems like most people are using Dropbox or another service.

---

### Post by Jdogzz on 2012-01-19
The most I've stored myself on Ubuntu One is 2.7 GB of data. If you do need to store around 20 GB you'll need to pay for the extra space. But I personally use Dropbox and not Ubuntu One. Dropbox has always seemed to work much nicer and Ubuntu One's program for Windows doesn't seem to work after the initial sync. Also, there's no option to bulk download folders (only individual files) for Ubuntu One, so if you do decide to go with that, seeing as you're using all linux, you'll have to re-sync collections in order to get the data back, not just pick a folder from the site and download as Dropbox does.

---

### Post by greenpeace on 2012-01-20
I happily use both and I don't see why you have to make a decision to use only one!  I see them as suited to solving slightly different problems.

I have 4.1Gb for free with Dropbox that I use for sharing images with other members of our design team on the other side of the world... for that it's invaluable.  Works really well on all platforms etc.

After having a bunch of HDDs fail, I now have 20Gb of photos and Documents stored online with Ubuntu One (paid for).  It made transferring to a new computer really easy... all my docs and photos were there to be downloaded.

the web interfaces for both tools are pretty functional, but Dropbox's site is better for administrating the sharing.  

Also, I didn't need 50Gb of storage, and I didn't want to change the hierarchy of my directories so Ubuntu One worked out to be the best option for backing up my photos and docs.

---

### Post by Nkosi on 2012-01-22
I find DropBox to be much easier, faster to use and everything works. My non-techy wife uses it and loves it. But for security, I've stayed with U1. Bookmarks have never worked. It's quirky, so I use it just for data syncs. That part seems to be working very well, even on my extremely slow connections in Africa.

---

### Post by Whovian on 2012-07-26
I have not used U1 yet (used spideroak beforehand) but from what I read it is not fully ready for my use yet but  will be willing to try it in the near future. I have been using DB now for a couple months an like it. It sync's well with all my machines, is quick on the uploads, an just simple to use. Those that are worried about security of your documents part why not just encrypt it with TrueCrypt or other encryption method.

---

### Post by jonesyp on 2012-07-31
I like Ubuntu one as it is very tightly intergrated into Ubuntu, and you get 5GB, rather than the standard 2GB in dropbox.

Regards

Peter Jones

---

### Post by egeezer on 2012-08-03
I would rather have the 2GB of efficient, fully reliable syncing that Dropbox gives me than the 5GB of U1 that used to vanish at arbitrary moments and occasionally refuse my sign in.

---

### Post by uzumakifahim on 2012-08-04
> **egeezer said:**
> I would rather have the 2GB of efficient, fully reliable syncing that Dropbox gives me than the 5GB of U1 that used to vanish at arbitrary moments and occasionally refuse my sign in.

You are right. I also have faced the same problem with U1. But it's different from the last version, I think. Now I'm using U1 an Dropbox in both Windows and Ubuntu platform. Right now I'm facing no issues with U1. If you want, you can give a try. Hope you won't be disappointed.

Good luck. :)

---

### Post by Rifester on 2012-08-04
Ubuntu One is running great for me lately and I use the Android app to store photos to the cloud often.   Ubuntu One will not let view photos in your cloud storage.    Dropbox will let you view photos and video from your storage.

---

### Post by Sarcastic Cows on 2012-08-05
There's too much on the market to choose from. I've been using Dropbox for a while now, though, because it looked the most promising when I chose it.

I found out about U1 when I installed Ubuntu for the first time. I wasn't quite sure what it was for then, because it asked me to back up. 

But other competitors now are Skydrive, Box, Google Drive... there's plenty more.

---

### Post by First Taste Hooks You on 2012-08-07
I use Ubuntu One on my MacBook with Ubuntu, on my Acer Iconia Tab A100 and my HTC Droid Eris. Very useful, I just wish it was easier to download more then one file at the same time on my Android device (I use it to sync my music from the MacBook to all my Android devices.)

---

### Post by gavtaz on 2012-08-22
[FONT="Arial"]I love the way that when I buy music through Rhythmbox it’s uploaded to U1 but it would be good to be able to download more than one file at a time. It also works well with my Android phone, when I take a photo it’s backed-up straight away.[/FONT]

---

### Post by Dragonbite on 2012-08-22
I think Ubuntu One really needs to work on enhancing their web interface because that's something Dropbox has over it.

---

### Post by Random20210831 on 2012-08-25
Dropbox is better because shared folders, intuitive options...

---

### Post by spaceshipguy on 2012-09-20
> **jonesyp said:**
> I like Ubuntu one as it is very tightly intergrated into Ubuntu, and you get 5GB, rather than the standard 2GB in dropbox.

Me too.
I couldn't use Ubuntu 1 for a while after I did a fresh install and Ubuntu 1 no longer liked the ‘smell’ of my computer.

I'm on a new laptop now and Ubuntu 1 is working faster than Dropbox, and you get more storage - what's not to like.

---

### Post by thnewguy on 2012-09-20
Both are good services, but I really like the integration provided by Ubuntu One. For example, when I write an e-mail in Thunderbird, when I go to attach a large file, Thunderbird will offer to upload the attachment to Ubuntu One, share it and e-mail the link instead. Stuff like that really appreals to me.

The only complaint I've had with One is getting it to run on other operating systems (Windows and PC-BSD). It can be made to work, but I've found it isn't as smooth as getting it running on Ubuntu.

---

### Post by Dragonbite on 2012-09-20
I found a posting that talks about being able to connect to Ubuntu One via FTP in other distributions.

> Recently, James Henstridge from my team at Ubuntu One released u1ftp, a simple app to provide FTP access to Ubuntu One. It's deliberately designed so that it works across platforms; whether you're on Windows or OS X or Ubuntu or Kubuntu or Fedora or whatever, it should work for you, so you can access your Ubuntu One storage via FTP, and therefore if you want to you can mount your U1 storage as a drive in your file manager.

Read it here : [[COLOR="Blue"]http://www.kryogenix.org/days/2012/09/11/accessing-ubuntu-one-file-storage-via-ftp-from-any-os[/COLOR]]("http://www.kryogenix.org/days/2012/09/11/accessing-ubuntu-one-file-storage-via-ftp-from-any-os")

---

### Post by BrianBlaze on 2012-09-20
What ever happened to saving shtuff on external hard drives? lol

---

### Post by spaceshipguy on 2012-09-21
> **BrianBlaze said:**
> What ever happened to saving shtuff on external hard drives? lol

Nobody will give you a free 5GB hard drive. :-)

---

