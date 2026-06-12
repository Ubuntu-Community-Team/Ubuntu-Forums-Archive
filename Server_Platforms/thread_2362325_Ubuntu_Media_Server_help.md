---
title: "Ubuntu Media Server help"
date: 2017-05-26
forum: Server Platforms
---

### Post by stottosy on 2017-05-26
Sorry if this has been brought up before.
I'm lost with creating an Ubuntu Media server. I've be in IT for years and MCSE but completely lost with this. Maybe because I'm winding down my career and trying to solve this is not fun anymore.
I have several extra machines and trying to convert from Windows 10 media server to Ubuntu 16 server with a clean install of Ubuntu only.
My equipment:
i7-860 intel processor w/12 gig RAM
1 - 160 gig drive - for OS
1 - 160 gig drive - for apps
2 - 1 TB drives in RAID0 through bios for storage and media serving of movies.

I just want a simple media server running something like Serviio, or a dlna service and a few tools to convert .MKV and something like HandBrake converter.
I don't know what to select for the options. I've installed several times and just can't seem to get it all to fall in place. Like when the question about MDADM....No idea what it is or why I should or should not use it. Would it be simpler to just use the desktop version?
I've followed several step by step sites but still not figuring this out. No haha moments. any suggestions? too many drives?
Appreciate any info.

Thanks

---

### Post by TheFu on 2017-05-26
Don't use Fake-RAID. It is more hassle than it is worth and provides all the limitations of HW-RAID, without the performance. Definitely on the list to be avoided.

I wouldn't touch a RAID0 either.  I say this having lost all the data on 3 drives doing that, it was before I had backup religion and about 15 yrs ago.  Of course, it is all your choice.

Install the base OS with just ssh-server to start.  Only deal with 1 HDD.  This isn't Windows.  You don't need 160G for apps.  25G is plenty for the OS **and** all the applications, if you want more, give it 50G.  I'd make /var about 50G too, if you keep media metadata there. That's where Plex Server keeps it.

If you want the most flexible storage, use LVM.  Generally, I don't recommend this added complexity for someone new to linux, but if you're a Windows Admin, you've probably dealt with Veritas VM and Veritas File System.  LVM is like those, but free.  It is possible to expand or reduce a currently running ext4 file system inside a logical volume, LV.  LVs have 3 levels of indirection, so **anything** you can imagine for storage can be accomplished. Many of those things are foolish, but hey - Unix system - YOU are the boss and have to live with those decisions. If you tell the computer to do something foolish, fine. It should do it.  After all, the computer can't tell between foolish and genius commands.

There are different sorts of media servers.  If you expect to record TV, that is harder than having a library, playback system.  Recording TV needs a PVR application.  Most people use MythTV for this on Linux. It is possible to use Kodi with very specific tuner hardware.  I use an HDHR4-US.  It is a DLNA server that any DLNA client can access.  I haven't decided on a PVR program yet, so in the meantime, I use a wget script to record stuff with it scheduled through cron. That's way to nerdy for 99.999% of the world, but it works.  Kodi has a way to do these things, I just haven't bothered. To be honest, I still use Win7 media center for recording TV - never playback or anything else. 2x a day, those files are automatically moved to the i7 media box, a script locates all the likely commercials and I manually validate the cuts using vid-cutter, before transcoding everything from mpeg2 into h.264/vorb/mkv files with SRTs.

Ubuntu Server doesn't have a GUI. If you need a GUI, then you want a desktop install.  A GUI doesn't generally help with server stuff at all. Server people admin using ssh, a text interface.  GUIs don't work from 10K miles away. I admin servers around the world and can't imagine doing that if a GUI was required.

BTW, the system above is complete overkill for a linux media server.  Mine uses a $50 Pentium CPU, has about 16TB of media and needs 2G of RAM - I put 8G in because I had the sticks lying around. It runs Plex Media Server.  It doesn't have a "head" - no video, no keyboard and no mouse connected, just a power cable and network cable.  System management is through ssh.  Plex management has a web-GUI.  The storage is shared to different systems on the network via NFS, so placement of media is handled by other systems.  NFS uses native Linux file and directory permissions, so there aren't any issues with the wrong owner or plex not being able to see the media.  That same box runs about 15 other services for the LAN here with plenty of CPU left over.  However, it isn't a box for transcoding. ;(  Way too slow for that.

File permissions are central to Unix security and allowing different process IDs and userids to access files to different levels. This is pretty foreign for most Windows people. Everything on a Unix system is built around this model, so having a strong understanding is necessary to prevent confusion and frustration.

I do commercial removal and transcoding on an i7 desktop, not the server. That desktop runs Ubuntu and I use handbrake - both the GUI and the non-GUI versions.  It probably works the same as the Windows versions. I don't remember any odd dependency issues with handbrake. The packages handle those.

Playback devices are 2 Raspberry Pis - a v2 and a v3 running Kodi + PlexBMC. I like the silence that a PC can't provide in the viewing rooms.  We also have a Roku, but only use it for paid streaming services, not local stuff.  As great as a roku is, it sucks when compared to Kodi for local network media.  I find DLNA interfaces cumbersome. Kodi simplifies that.

Plex media server is the best DLNA server I've found over the years, BTW.  I don't have a plex account and don't let my plex server talk directly over the internet. It uses a proxy. If I want to watch video or listen to music away from home, a which ssh-tunnel into my LAN allows it. Plex can transcode on-the-fly for any playback device or bandwidth - the pentium handles that fine.

The 2x1TB disks, I'd add those later, well after getting everything else working.  Just ignore them for now.

I've never seen Serviio. Tried minidlna, but found it didn't fit my needs.  If you only have 1 system, then Kodi is easy. If you have lots of playback systems and want a central server that keeps track of what has and hasn't been watched, then Plex is very nice.

Don't know if any of that stuff above is helpful or not.  I'm not very good at helping people new to Linux. Linux is like learning a foreign language and Windows knowledge really isn't much help - often it is a problem, actually.  Certain assumptions about how things work are often made by Windows people that just aren't true for Unix systems.  Feel free to ask for clarification.  Lots of experienced people are here.  I suspect you'd get more expert advice in this topic from the multimedia sub-forum.

Oh - mdadm is for Linux software RAID. I suspect you don't really want to use that.  RAID solves 3 problems as you know.  For a media server, 2 of those problems really aren't important. Backups solve 1001 problems, including a failed RAID setup. 
LVM would be more helpful with storage management.  While you can use both at the same time, I wouldn't, not for a media server.  LVM needs to be used from the start to be most useful. You cannot add it to pre-formatted disks. It has to be setup before a file system is laid down.

---

### Post by stottosy on 2017-05-26
Wow. thanks. Lots to read and try to understand. This used to be fun to try to hash out. Yeah my equipment is over kill. It's just stuff I have laying around. still have a few 500 Gig drives in a draw. My main PC is i5-6600K setup. All I do is get MKV convert serve up with serviio or PLEX. My TV is DLNA ready so good there. DISH is DLNA ready too but they FUBAR'd it on an system upgrade.
Thanks again. Good info.

---

### Post by TheFu on 2017-05-26
My main PC is a virtual machine, running in a private cloud. Generally accessed from a chromebook. ;)  I access the handbrake work from the chromebook too thanks to X/Windows and remote X.  Running an application on 1 system and displaying it on another is very common with Unix systems, provided that video playback isn't involved.

Much less hardware is needed if you don't use Windows. ;)

Unix is a completely different way of thinking about computing for most people.

---

### Post by SeijiSensei on 2017-05-27
I've been using minidlna as a DLNA server; it's pretty simple to configure.

Most of the time I just open video files on the server with a player application like SMPlayer.

If you need to do on-the-fly transcoding of MKVs to a format your media devices support, there is [ps3mediaserver]("https://help.ubuntu.com/community/Ps3MediaServer") which also provides DLNA services.  I find it a lot easier to use player software that supports those files directly.  SMPlayer is also available for Windows.  

The other option is to re-encode videos into the .mp4 container which most media devices support rather than doing it on-the-fly each time with ps3mediaserver.  I use [ffmpeg]("https://ffmpeg.org/") at the command prompt for tasks like this.  I recently had to recode a few videos that were in Apple's Quicktime and the .mov container to a more-widely accessible format.  For that I chose WMV3 as the video codec, AAC as the audio codec, and created the file using this command:
```
ffmpeg -i input.mov -vcodec wmv3 -acodec aac -strict -2 output.mp4
```

First time out, I'd install a desktop version of Ubuntu rather than the server version.  With the latter there's no GUI so you need to be conversant with the command prompt. I'd start by installing Ubuntu to one of the 160s.  Once you get everything installed, you can start to think about the other devices.

Like TheFu I would strongly recommend avoiding RAID0.  I would create a RAID1 array using the pair of 1 TB drives using mdadm like this:
```
sudo mdadm --create --verbose --level=1 --raid-devices=2 /dev/sdc1 /dev/sdd1
```
assuming /dev/sdc and /dev/sdd are the two 1GB drives.  I usually use fdisk first to create a single partition on each drive and mark it with the "Linux RAID" partition type, "fd".  With this arrangement Linux will detect the array components at boot and start the array even without an mdadm.conf file.  After you start the array, which is referenced as "/dev/md0," you would format the partition as ext4 with "mkfs" then mount it into the file system.
```
sudo mkfs -t ext4 /dev/md0
sudo mkdir /media/raid
sudo mount /dev/md0 /media/raid

```
If that works, you can create an entry in /etc/fstab to mount the array to /media/raid at bootup. ("/media/raid" is arbitrary, though it has become the norm to mount additional devices under the /media directory.)

---

### Post by mastablasta on 2017-05-29
why do mkv files need to be converted?

how many users will this serve? is it only one TV? i use RaspberryPi with an 8Gb card and a USB hard drive for that. if it's only one TV, your server is massive overkill. on the other hand you could use it as backup server.

RAID is needed only if you need to have it running all the time (sone one drive is operational while the other one is fixed). if this is about holding some media data then there is no need for RAID. RAID is also not a backup solution.

---

### Post by TheFu on 2017-05-29
> **mastablasta said:**
> why do mkv files need to be converted?

MKV is just a container. It can hold almost anything. Some of the videos aren't compatible with all devices, so transcoding either in advance or on-the-fly is needed.  For example, I didn't purchase the MPEG2 decoding for my Raspberry Pi, so all TV recordings (which are mpeg2 here) needed to be transcoded to some format a Pi can handle.  h.264 decoding via hardware is built into the pi.

Same for many Android devices (tablets/phones). mpeg2 uses 5x the CPU that h.264 uses since the later is supported in the GPU.

Some shows are being streamed with h.265 now.  My Pi v2 can't handle those at 1080i resolutions. It stutters badly every 5 seconds or so.  It needs to be transcoded.

A Chromecast is VERY, VERY, VERY, picky about which video and audio codecs it supports.  It will never handle AC3 5.1 audio as broadcast TV contains or mpeg2 video. All broadcast recordings **must** be transcoded to watch them with a chromecast.  Chromecast won't play any of my old TV recordings that are xvid/mp3/avi either. Those all have to be transcoded.

Same applies to a Roku.  Roku doesn't like certain audio formats.

A chromecast is happiest with h.264 video + vorbis audio.  Plus multi-channel Vorbis audio is the highest quality audio available today that isn't patent encumbered and well supported across hw-devices. It is better than AAC.  Actually, I bet a chromecast probably prefers VP8 video over h.264.  I just haven't been impressed with VP8 results.

But 95% of current web streaming stuff that doesn't come from Google is h.264/aac in an MP4 container. That is the defacto standard for the last 4+ yrs.

By using a media server on a more powerful x86 system, I'm not stuck trying to find a different playback device just because some odd format is being provided.  With Plex Server, the client chooses the video, audio formats it wants and the server provides them via transcoding on-the-fly.  A raspberry-pi cannot handle transcoding. Heck, a slow Atom CPU cannot handle transcoding, but a $50 Pentium CPU can. Fantastic flexibility.  My $50 Pentium CPU is a NAS for the network. It does many more things here. It is also a little noisy, so it can't be in the same room we watch TV/Movies. A silent playback device works best in those locations, for us.

---

### Post by slickymaster on 2017-05-29
*Thread moved to **Server Platforms**.*

---

### Post by SeijiSensei on 2017-05-29
> **mastablasta said:**
> why do mkv files need to be converted?
Player devices like TVs often do not support the broad range of codecs and containers found in modern video files.  My LG TV will happily play some files via DLNA and refuse to play others.  I never bothered to track down the differences since the computer with those same files is directly attached to the TV.  I've had similar experiences with Sony TVs.

Typically the mp4 container is the most widely supported because it has Sony behind it.  That still doesn't mean that the player device has support for the codecs used to encode the audio and video. For a long time commercial venders eschewed support for MKV because of its open-source roots and widespread use by pirates.

---

### Post by mastablasta on 2017-05-30
> **TheFu said:**
> MKV is just a container. It can hold almost anything. Some of the videos aren't compatible with all devices, so transcoding either in advance or on-the-fly is needed.  For example, I didn't purchase the MPEG2 decoding for my Raspberry Pi, so all TV recordings (which are mpeg2 here) needed to be transcoded to some format a Pi can handle.  h.264 decoding via hardware is built into the pi.

makes sense. though i never ran into mkv that wouldn't run on the Pi. i guess i was lucky. i too didn't buy the extra codecs.

> **SeijiSensei said:**
> Player devices like TVs often do not support the broad range of codecs and containers found in modern video files.  My LG TV will happily play some files via DLNA and refuse to play others.  I never bothered to track down the differences since the computer with those same files is directly attached to the TV.  I've had similar experiences with Sony TVs.

Typically the mp4 container is the most widely supported because it has Sony behind it.  That still doesn't mean that the player device has support for the codecs used to encode the audio and video. For a long time commercial venders eschewed support for MKV because of its open-source roots and widespread use by pirates.

this makes sense as well, however the OP want's to run a media server. wouldn't that run all the media with it's Core i7 (which should run all media flawlessly). there should be no need to transcode on such a beast. unless you wan't to play the files on another device that doesn't support all codecs. or yeah maybe the user wan't to rip their DVD collection. it is allowed here where i live if it0s for personal use only. in that case they would need to transcode. or maybe they have some personal video recorded in some strange very large format - e.g. my wifes phone makes HD videos that make really huge files and if i transcode them they get a lot smaller while keeping the quality)

---

### Post by SeijiSensei on 2017-05-30
> **mastablasta said:**
> this makes sense as well, however the OP want's to run a media server. wouldn't that run all the media with it's Core i7 (which should run all media flawlessly). there should be no need to transcode on such a beast. unless you wan't to play the files on another device that doesn't support all codecs.
The OP mentioned DLNA streaming which assumes there are client player devices.  I use BubbleUPnP as a DLNA client on my Android phone with MXPlayer, and it plays pretty much everything I throw at it.  As I said, my TV does not.

---

