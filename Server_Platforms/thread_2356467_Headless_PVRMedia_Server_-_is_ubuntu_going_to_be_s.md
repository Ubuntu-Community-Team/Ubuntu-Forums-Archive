---
title: "Headless PVR/Media Server - is ubuntu going to be suitable for me?"
date: 2017-03-23
forum: Server Platforms
---

### Post by elsmandino2 on 2017-03-23
Hi,

I am a Linux novice and would be grateful for some advice.

I want to run a headless server that uses TVHeadend to make all my recordings and then stream them back to a number of Raspberry Pis, running Libreelec.

I also want to pool all my hard drives as one, using mergerfs?

I also need to find someway of synching the watched status of my other media in Kodi - for this, I think I will need MySQL.

Ultimately, is Ubuntu going to suit me for this?

I have been trying Openmediavault out but I am real problems with XMLTV - I need version 0.5.69-1 (because this offers the tv_grab_zz_sdjson grabber that I need to be compatible with my Schedules Direct account).  As OMV is based upon Debian Jessie, the most recent version I can get is 0.5.63-2.

Ultimately, is Ubuntu going to be a suitable distro for what I am after and what are the main differences between it and Openmediavault?

---

### Post by mastablasta on 2017-03-24
> **elsmandino2 said:**
> 
I have been trying Openmediavault out but I am real problems with XMLTV - I need version 0.5.69-1 (because this offers the tv_grab_zz_sdjson grabber that I need to be compatible with my Schedules Direct account).  As OMV is based upon Debian Jessie, the most recent version I can get is 0.5.63-2.

you can use debian backports to get the latest version. 

there is also a "testing" version of OMV.

> 
Ultimately, is Ubuntu going to be a suitable distro for what I am after and what are the main differences between it and Openmediavault?

Ubuntu comes without any GUI, openmediavault has a gui along with other configuraiton help and scripts available for the users to easilly setup their attached storage via GUI.

---

### Post by elsmandino2 on 2017-03-24
Thanks for that, mastablasta, I think I shall stick with OMV for the time-being - does seem that it is better suited for exactly what I am after.

In Layman's terms, what is does using backports mean/involve?  I have come accross this before, on Linux forums, in the past, but never quite understood what it is.

---

### Post by Tadaen_Sylvermane on 2017-03-24
I am doing all of those things with my server running Ubuntu. Only difference is my main HTPC is my server, it is direct booting to Kodi. Central mysql database for Kodi & Mythtv. File server and backup target for all computers in the house. Currently 4 lxd containers for minecraft servers. Apt-caching proxy for the lan. Torrent server. DHCP, DNS, and LTSP as well. 

For me Ubuntu is the only way to go. I do advise you avoid LVM for the drives though. I had a bad experience recently after I reinstalled with LVM for the main os drive (i wanted snapshots). Your mileage may vary. Almost lost it all. Backups are a wonderful thing. Always backup! Recovered on regular partitions and been going strong awhile now.

---

### Post by slickymaster on 2017-03-24
*Thread moved to **Server Platforms**.*

---

### Post by mastablasta on 2017-03-27
> **elsmandino2 said:**
> 
In Layman's terms, what is does using backports mean/involve?  I have come accross this before, on Linux forums, in the past, but never quite understood what it is.

you add a repository that contains a prepackaged newer version of the program to your software sources. then you can use the "apt-get install" command to install the newer version.

it is similar to Ubuntu's PPA.

does that make sense?

more here: [https://backports.debian.org/](https://backports.debian.org/)

> **Introduction**

You are running Debian stable, because you prefer the Debian stable tree. It runs great, there is just one problem: the software is a little bit outdated compared to other distributions. This is where backports come in.

Backports are packages taken from the next Debian release (called "testing"), adjusted and recompiled for usage on Debian stable. Because the package is also present in the next Debian release, you can easily upgrade your stable+backports system once the next Debian release comes out. (In a few cases, usually for security updates, backports are also created from the Debian unstable distribution.)

Backports cannot be tested as extensively as Debian stable, and backports are provided on an as-is basis, with risk of incompatibilities with other components in Debian stable. Use with care!
It is therefore recommended to only select single backported packages that fit your needs, and not use all available backports


---

### Post by TheFu on 2017-03-28
So ... anything is possible, but that doesn't mean you (or I) will have the skills needed to accomplish it.

I tried to get tvheadend working a few years ago and failed.  Because of that failure, when a DLNA tuner became available, decided to get it and now I can record TV on most of my systems using wget and a URL.  It also works with all other recording software I've tried extremely well. Raspberry Pis aren't known for their I/O capabilities, so while recording a single SD stream will probably work easily, I'm not certain that a 1080p stream will record - just depends on if the I/O overwhelms the little pi USB2 subsystem. It isn't about CPU, at least with my tuner. It is purely USB2 I/O limitations due to the shared USB for all external devices.

If you use Kodi or Plex, there isn't **any** need to run a merged file system.  Putting multiple sources under a single "name" is sufficient. Plex has this built-into their web GUI. With KODI, I just edit the sources.xml file directly. Plus, when something bad happens, data recovery will be slightly more complex or nearly impossible on merged file systems. About 13 yrs ago, I lost 80% of my data over using a merged file system - 1 out of 3 disks failed. I didn't have backup religion back then. You can use symlinks to make disks appear to be merged, if you like. I used to do that in the 1990s. Coming from Windows, people don't usually know about those.

If you run a plex server, then all DLNA clients will be able to access it.  Don't think that will run on a Raspberry-Pi. I run my on a $50 Intel CPU and it has plenty of extra CPU for 10 other things. Anyway - plex keeps track of all the viewed shows/movies/videos centrally.  There are addons for Kodi - PlexBMC, but that one has been temperamental recently. It worked perfectly for the Jan-Fed on Kodi v17.x until I patched about 2 weeks ago. Since then, I've had to revert back to pure DLNA access, which works, but isn't as convenient. I'm running the plex server on Ubuntu Server. Zero GUI.  I use the OSMC kodi distro on a raspberry pi v2.  Bought the mpeg2 codec license, but not the other one.  Where I live, broadcast TV is mpeg2 using ATSC.  Your local TV may be very different, since different countries have different TV standards.  I'm using an HDHR4 dual TV tuner connected to a group of antennas pointed in different directions in the attic. Works amazingly well.

I don't have a plex account, so you don't need to give up your privacy to those guys.  Also, it isn't too hard to remote stream without a plex account, if you can setup either a VPN or ssh-based SOCKS proxy. I've used both.  Audio works great, but video will depend on the bandwidth between the client and server inside your house.  Plex lets you reduce the video bitrate so that pretty much any broadband connection will work. But this requires a powerful enough CPU to do real-time transcoding. That won't be a raspberry pi. Just not possible.

Don't know anything about openmediavault. In the last 20+ yrs, I've looked at many of those specialized storage distros. For me, they are too limiting. Cannot speak for others.

Schedule data for my OTA tuner is provided by the vendor - at least so far.  Using OSMC/Kodi and the HDHomerun plugin, the TV "just works." I haven't tried any recording. Recording is performed on different systems then fed into some automatic processing to mark commercials, let me validate those marks, remove the commercials and finally transcode the video from mpeg2 into h.264+ac3+ogg+captions into an mkv container.  Most of this is batched.

All Unix systems have a steep learning curve.  If you don't plan for this and anything doesn't work to plan, then you will be in over your head rather quickly. These system setups aren't Next --> Next --> Next --> Finished and they aren't designed to be installed by anyone. Specific skills are necessary. Plus, things break from time to time and you'll need to recognize if a slight tweak to a config file is all that is needed or a wipe and start over thing.

Backups are your friend.  Daily, automatic, versioned, backups.  Every storage device is going to fail. Hopefully, they will fail when you don't need them anymore.

None of this is to say that you cannot do it.  You can do anything you want. I just won't want to understate the effort necessary.

I'm running 2 debian-based server installs. They don't "feel" right to me. Things are just a little off. Can't quite put my finger on it, but both use systemd and that has cause me all sorts of stupid issues.  1 of them keeps deleting my network config file - coming up without any networking on a remote server sucks, so I took away the ability for the OS to modify that file anymore.

Hope this perspective helps.  The other responses are excellent.

---

### Post by Oelsner on 2017-04-05
I am running tvheadend on a headless ubuntu server.
Getting it up and running was a breeze, and my hd-homerun tuners were found by tvheadend.
It has an easy to use web ui for your management needs.
The mysql part i dont have experience with :)

---

### Post by elsmandino2 on 2017-04-06
Thanks very much for your help with this - really do appreciate the time you have taken to help me.

Having spent more time with Openmediavault, I have decided that it is not for me after all.

I do feel massively out of my depth, as a Linux novice, and really need a GUI until I am comfortable with the command line alone.

I think I shall install the desktop version of Ubutnu on my server for the time-being.

Could you possibly tell me a little more about not needing a merged file system - as this is the thing that I find particularly confusing as someone trying to move from Windows to Linux.

Here is my current set up:  

I have three hard drives at the moment - two 2TB and one 6TB.  

I have a piece of software, called Stablebit Drivepool, that combines those drives into a single "virtual" 10TB harddrive.

I don't ever touch the actual drives - all my network shares are done from the virtual harddrive (Video, Recordings and Docs etc).

When files are added to the shared folders, the software puts the files on any/all of the harddrives, taking into account, I/O activity and heat.

This ultimately means that whole files are split between the hard drives (though they exists in a single folder on the virtual drive).

Is this something I can recreate on Linux, therefore, without the need for a merged file system?

---

### Post by TheFu on 2017-04-06
> 
Is this something I can recreate on Linux, therefore, without the need for a merged file system?
Yes, you can but why bother?

A story ...
Years ago, I merged 3 partitions on 3 different HDDs into a single file system. 1 of those disks failed, so all the data across all 3 disks was lost.  Back then, I didn't have backup religion like I have today.

Modern media center software will virtually merge multiple file systems.  Plus, how do you backup a single 10TB file system?  I buy 2 disks for media at a time - primary and a backup which gets manually mirrored via rsync every few days after new files get added.  Media files aren't backed up like other files around here.  Other files get automatic, versioned, backups, every day. 60-120 days of versioned backups are kept for non-media files, but that is a different thing. 

Here's a small part of the "sources.xml" file for a **Kodi** machine here:
```
        <source>
            <name>Movies</name>
            <path pathversion="1">nfs://172.22.22.20/D/M/</path>
            <path pathversion="1">nfs://172.22.22.20/DD/M3/</path>
            <allowsharing>true</allowsharing>
        </source>
        <source>
            <name>TV</name>
            <path pathversion="1">nfs://172.22.22.20/D/T/</path>
            <path pathversion="1">nfs://172.22.22.20/misc/2TB/T2/</path>
            <path pathversion="1">nfs://172.22.22.20/DD/T3/</path>
            <allowsharing>true</allowsharing>
        </source>

```
2 different drives are merged under "Movies" and 3 different drives are merged for "TV".  **Plex** can do the same thing - they just have a GUI which is cumbersome to show. Kodi has a GUI too, but I'm watching some live sports on it now. ;) Images are bad in forums.  
My kodi machines are $40 raspberry Pis (completely silent) and all their data comes over the wired network via NFS.  NFS is more efficient than other networked file systems AND provide the native Unix permissions. CIFS is a poor substitute.
Of course, Plex streaming uses DLNA over http. Most of my local content is on a Plex Server.

Using Linux efficiently means learning to think in the Linux way.  *Just because you CAN do something, doesn't mean it is a good idea.*  Unix will allow you (or I) to do dumb things - it doesn't know if are intention is stupid or brilliant, unconventional, usage.

If you absolutely must merge files/directories, there are always symbolic links.  It is common to use those from a HOME directory to access other, extra, storage on a different disk. I do that all the time.  I also have symlinks for convenience from 
/D/M2 --> /D2/M
/D/M3 --> /D3/M
so basically, there are M, M2, M3 directories under /D/.  Something similar is for home videos, photos, and TV shows.  When a disk gets full, I'll buy 2 more, add /D4 and /Backups/D4 to the system and start placing new media onto that new set of primary and backup disks.  My JBOD addon card can support 16 HDDs, so that's 8 primary and 8 backup disks (32TB usable).

The only way I know to learn Linux beyond the 10% provided by a GUI is to stop using the GUI and start thinking the Unix-way following the "[Unix philosophy]("https://en.wikipedia.org/wiki/Unix_philosophy")." You can look that up.  Start by not using a file manager - use the shell always. Soon, you will learn to glob files and move them around like a boss. GUIs will be way too slow 99% of the time (not always, there are times when a GUI is handy, about 1%).  After about 6 months doing that, you'll have learned when using a GUI is better and that will serve you for the rest of your life.  The same commands I learned in 1994 still work, generally.  The same scripts I wrote back then generally still work too, though my scripting-fu is much stronger these days.

Without a GUI, you'll learn the other 90% of Unix and all the real powerful things possible.  Much of that happens due to automation.  I don't "surf the web" anymore. I have a system that pulls the stories/content I'm interested in, organizes it, and makes it available to me from anywhere in the world. If I'll be off-line, then I can dump that content into an epub document for my tablet or netbook. When or if I read something isn't known by anyone else. If I retain a copy isn't known.  

My systems (and the content) are available from anywhere in the world that has internet connectivity without any 3rd party being involved. 

If you are still convinced to use a merged file system, please search for all the issues people have had with them over the years.  There are about 10 different tools for this, each with different issues.  LVM is probably the most tested. ZFS is well tested too. UnionFS and mergeFS have some unexpected problems. And there are a few others to be considered.  You'll definitely want 100%-know-you-can-restore backups with any of them.  I was using LVM with my data loss problem.  I still use LVM everywhere today, but not to merge file systems across different HDDs.

Also, other people will have different experiences and will come to different conclusions than I. Worth listening to them as well.

---

### Post by mastablasta on 2017-04-07
> **elsmandino2 said:**
> 
This ultimately means that whole files are split between the hard drives (though they exists in a single folder on the virtual drive).


so one drive fails (and they do fail) and you can lose it all? it's like RAID0, no one actually uses it, only maybe someone thta has small drives and needs them merged.

check out Ajenti GUI. it doens't have as many plug ins/add ins, but it can be a help when you edit configuration files, move files arround etc.

---

### Post by elsmandino2 on 2017-04-07
> **mastablasta said:**
> so one drive fails (and they do fail) and you can lose it all? it's like RAID0, no one actually uses it, only maybe someone thta has small drives and needs them merged.

check out Ajenti GUI. it doens't have as many plug ins/add ins, but it can be a help when you edit configuration files, move files arround etc.

Sorry - my earlier post was a bit ambiguous.

My current system moves whole files to each hard drive rather than spreading individual files over multiple hard drives - i.e. I have JBOD, rather than Striping.

This means that if I lose one of the three disks, only the files on that particular disk are lost - all files on the remaining hard disks remain intact.

I have just had a look at Ajenti GUI and it looks like a fantastic piece of software.  Am I correct in thinking that if I install Ubuntu Server, I can install this and control the headless server with a GUI on any other Linux PC?

---

### Post by elsmandino2 on 2017-04-07
> **TheFu said:**
> Yes, you can but why bother?

A story ...
Years ago, I merged 3 partitions on 3 different HDDs into a single file system. 1 of those disks failed, so all the data across all 3 disks was lost.  Back then, I didn't have backup religion like I have today.

Modern media center software will virtually merge multiple file systems.  Plus, how do you backup a single 10TB file system?  I buy 2 disks for media at a time - primary and a backup which gets manually mirrored via rsync every few days after new files get added.  Media files aren't backed up like other files around here.  Other files get automatic, versioned, backups, every day. 60-120 days of versioned backups are kept for non-media files, but that is a different thing. 

Here's a small part of the "sources.xml" file for a **Kodi** machine here:
```
        <source>
            <name>Movies</name>
            <path pathversion="1">nfs://172.22.22.20/D/M/</path>
            <path pathversion="1">nfs://172.22.22.20/DD/M3/</path>
            <allowsharing>true</allowsharing>
        </source>
        <source>
            <name>TV</name>
            <path pathversion="1">nfs://172.22.22.20/D/T/</path>
            <path pathversion="1">nfs://172.22.22.20/misc/2TB/T2/</path>
            <path pathversion="1">nfs://172.22.22.20/DD/T3/</path>
            <allowsharing>true</allowsharing>
        </source>

```
2 different drives are merged under "Movies" and 3 different drives are merged for "TV".  **Plex** can do the same thing - they just have a GUI which is cumbersome to show. Kodi has a GUI too, but I'm watching some live sports on it now. ;) Images are bad in forums.  
My kodi machines are $40 raspberry Pis (completely silent) and all their data comes over the wired network via NFS.  NFS is more efficient than other networked file systems AND provide the native Unix permissions. CIFS is a poor substitute.
Of course, Plex streaming uses DLNA over http. Most of my local content is on a Plex Server.

Using Linux efficiently means learning to think in the Linux way.  *Just because you CAN do something, doesn't mean it is a good idea.*  Unix will allow you (or I) to do dumb things - it doesn't know if are intention is stupid or brilliant, unconventional, usage.

If you absolutely must merge files/directories, there are always symbolic links.  It is common to use those from a HOME directory to access other, extra, storage on a different disk. I do that all the time.  I also have symlinks for convenience from 
/D/M2 --> /D2/M
/D/M3 --> /D3/M
so basically, there are M, M2, M3 directories under /D/.  Something similar is for home videos, photos, and TV shows.  When a disk gets full, I'll buy 2 more, add /D4 and /Backups/D4 to the system and start placing new media onto that new set of primary and backup disks.  My JBOD addon card can support 16 HDDs, so that's 8 primary and 8 backup disks (32TB usable).

The only way I know to learn Linux beyond the 10% provided by a GUI is to stop using the GUI and start thinking the Unix-way following the "[Unix philosophy]("https://en.wikipedia.org/wiki/Unix_philosophy")." You can look that up.  Start by not using a file manager - use the shell always. Soon, you will learn to glob files and move them around like a boss. GUIs will be way too slow 99% of the time (not always, there are times when a GUI is handy, about 1%).  After about 6 months doing that, you'll have learned when using a GUI is better and that will serve you for the rest of your life.  The same commands I learned in 1994 still work, generally.  The same scripts I wrote back then generally still work too, though my scripting-fu is much stronger these days.

Without a GUI, you'll learn the other 90% of Unix and all the real powerful things possible.  Much of that happens due to automation.  I don't "surf the web" anymore. I have a system that pulls the stories/content I'm interested in, organizes it, and makes it available to me from anywhere in the world. If I'll be off-line, then I can dump that content into an epub document for my tablet or netbook. When or if I read something isn't known by anyone else. If I retain a copy isn't known.  

My systems (and the content) are available from anywhere in the world that has internet connectivity without any 3rd party being involved. 

If you are still convinced to use a merged file system, please search for all the issues people have had with them over the years.  There are about 10 different tools for this, each with different issues.  LVM is probably the most tested. ZFS is well tested too. UnionFS and mergeFS have some unexpected problems. And there are a few others to be considered.  You'll definitely want 100%-know-you-can-restore backups with any of them.  I was using LVM with my data loss problem.  I still use LVM everywhere today, but not to merge file systems across different HDDs.

Also, other people will have different experiences and will come to different conclusions than I. Worth listening to them as well.

You guys on here speak so much sense - this is the sort of information that needs to be rolled out to people like me, trying to get off Windows.

I must admit that moving around files by the terminal only is something that is still painstakingly slow (it feels weird to imagine where things are in your heard rather than seeing it on the screen) - I shall definitely persevere with this until it becomes second nature.

I am definitely starting to see what you are getting at now, with regards to not having to merge file systems.

If I understand correctly, are you saying that if I have harddrive1 with a movies folder on it and then harddrive2 with a movies folder, I could just add both sources to Kodi and that would play them back as if they are essentially combined as a single folder?

Using the same principle, how would I set up set up the three disks with TVHeadend?  Would I have to dedicate a single Harddrive for all my recordings or would it be possible to add all three hard drives as sources for recordings?

I guess the reason why I bought the Stablebit software was because I am not particularly good at working out the best way to spread folders over my server hard drives.

For example, as mentioned above, I have two 2TB and one 6TB Hard Drive.  I had a huge folder called "Videos" that was 6.5TB in size.  I couldn't work out whether it was best to fill the first two hard drives up completely and then put the rest on the bigger or whether I should fill each of the harddrives so that each had the same % usage.  

Furthermore, regardless of the method used, I had to start calculating what subfolders would fit onto each hard drive.

With Stablebit, I just combined them, dumped everything on the new disk and everything seemed to sort itself out.

Am I overthinking/complicating matters with this approach?

---

### Post by TheFu on 2017-04-07
Yes, I think you are over complicating it.

I'm still concerned that you didn't mention backups at all.  Every HDD is going to fail. We don't know when. Hopefully, it is after we are done, but that isn't something we worry about.

To move files around, learn file "globbing" through regex.  Moving 1 or 1,000 files of similar names is trivial.  Plus, you've probably been warped by Windows with *.exe and *.* stuff.  On Unix, * is all that is needed to match everything in the same directory.  I routinely use *v - to match all *mkv files or *[v4] to match all mkv and mp4 files.  If I want to limit to just Buffy* files, then Bu* is probably enough in a directory.

Plus, kodi and plex have a requirement for TV shows and movies to be placed into their own directories.  I actually put each TV season into a different subdirectory S1, S2, S3 ... having too many files in 1 directory is asking to lose some (after all, directories are just a list of files and subdirectories stored in a file).  Almost everything on Unix systems is a file.  Understanding this basic idea leads to some interesting realizations.  The monitor is a file. Same for the mouse, keyboard, disk drive, partitions, webcam, ... all files.  Directories are files, files are files. Drivers are files.  Any device is a file.  Simple, but elegant. Unix file and directory permissions ... what are they?  Files.  There is 1 thing that isn't a file - a process. That's it. There isn't anything else besides processes and files.  All files have an owner, group, and permissions.

To see how much storage files use (or directories), use 
df -h
du -sh 

Want to sort those by size?
du -sh |sort -h
Want the order reversed?
du -sh |sort -hr

BTW, for media being accessed in a home, where files are stored really doesn't matter as much as how you backup those files.  The network should be fast enough.  The disks are all fast enough.  Having a super-speedy disk (SSD) for hidef media files just isn't needed. It doesn't matter.  OTOH, having faster networking and disks for backups DOES matter. If backups take too long, you won't do them.

I cannot answer any tvheadend questions. Don't use it. Tried it and failed a few years ago. It seemed overly complex for what it does.  With an HDHR4 tuner, it isn't needed, IMHO. Can't see what storage has to do with it at all.  Record to temp locations, then move them to your "watch now" location and delete when done.  For those few shows you want to archive, move them into your TV structure as required by the media center software you use. Eventually, delete what you are done with.  For example, I'll watch iZombie (commercials removed), but not keep it.  I'll keep The Expanse and when all the episodes are done, watch them with all the commercials removed.

I haven't paid for any software on Linux for use at home, ever. It is all F/LOSS. To get out of the Windows-state-of-mind: [http://blog.jdpfu.com/2017/03/31/learning-linux-condensed](http://blog.jdpfu.com/2017/03/31/learning-linux-condensed)

And never forget, just because something is possible, that doesn't make it a good idea.  IMHO, GUIs for server management fall into that category.  They are usually a way to provide attackers complete control over your systems, quicker.  Most people new to Linux don't have sufficient knowledge to set these up in a secure way.  Unix security is full of subtle considerations which take time to understand.

Sorry for babbling.

---

