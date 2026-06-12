---
title: "Suggestions to set up New Server 14.04 Instal"
date: 2015-06-30
forum: Server Platforms
---

### Post by Steve_Cline on 2015-06-30
I just started a project to build a home server with an old Dell Desktop for three purposes:


[LIST=1]
[*]It will function as a media system for the LED TV it is connected to using XBMC.
[*]It will function as a home server for videos, music, files, etc.
[*]It will be used as a torrent host.
[/LIST]

It has 14.04 Server installed on it with Gnome Desktop.  I have a 2TB external SSD for storage along with the 80GB on the computer.  

Are there threads or articles that would be recommended to accomplish this task?

Thanks for your help.

---

### Post by TheFu on 2015-07-01
XBMC is dead. **Kodi** is the new name.

Use **Plex Media Server** and the PlexBMC plugin for Kodi to access it. There a many reasons to do it this way. Plex lets you add different storage areas to the same media library - say you have TV shows on 3 disks - plex lets you virtually merge those into 1 "TV library". Highly convenient for this and about 20 other reasons.

Expensive SSD for media storage?  That just isn't needed. For media - a slow, cheap, multi-TB spinning disk is 5x faster than needed. Use the SSDs for something else where it would be helpful.  Plus backups are still mandatory. All storage fails and it is never at a good time.

Cannot help with torrents. For media, where I live, they are almost always illegal.

Search for "ubuntu plex server" for how-tos.  Plex and Kodi use similar media directory structures for each of the media types. There are some other plugins for Kodi that make catching up on old missed shows easy too.

PMS is a DLNA server - every DLNA client I've tried has worked well with it. Android, Roku, smartTVs, WD media devices, networked optical players, chromecast, ... The downside to Plex are:
* not F/LOSS - free to use.  No need for a plex account. 
* Transcoding needs a reasonably midrange CPU - probably 3000 passmark is the minimal CPU speed. The "old dell" might not have this, but a MB+CPU replacement for $100 solves it easily. Pentium G3258 ($60-ish) has a 4000 passmark rating.

I should say that I ran XBMC for 3 yrs before adding Plex Media Server .. wish I would have done it years earlier.

---

### Post by slickymaster on 2015-07-01
*Moved to the ***Server Platforms*** sub-forum*

---

### Post by Steve_Cline on 2015-07-01
Thanks for the advice on Plex.  I will give it a try.

---

### Post by mastablasta on 2015-07-02
what you want work just fine on RaspberiPi+Kodi or better Openelec. add a large external disk to it (with it's own power system), tell Kodi where media files are and you are done.

for torrent you install transmission service and then access the interface via web browser. 

> **TheFu said:**
> 
Use **Plex Media Server** and the PlexBMC plugin for Kodi to access it. There a many reasons to do it this way. Plex lets you add different storage areas to the same media library - say you have TV shows on 3 disks - plex lets you virtually merge those into 1 "TV library". Highly convenient for this and about 20 other reasons.


so does kodi apparently: [URL="http://kodi.wiki/view/Adding_video_sources"]http://kodi.wiki/view/Adding_video_sources
[/URL]
as i understand Plex is more oriented towards streaming videos on various devices. not something i would need at the moment.

---

### Post by TheFu on 2015-07-02
A raspberry pi makes a great end-node or playback device, not so much the center of a household media server, however.  The server needs to transcode to the format for the end-nodes.

If the media is 100% h.264/aac - then a Raspberry Pi is great. If you have other video formats - it just doesn't have the CPU needed to handle the playback when the GPU doesn't have HW support.  So, if you have 5-10 other video formats - well, that is the question. Got any xvid, WMV, mpeg4, or other videos? 

If you intend to record TV ... how well does the Raspberry Pi handle that and playback of huge mpeg2/AC3 files with 1080i content? I don't know - except that most cheap players like a chromecast or roku won't play AC3 audio. It needs to be transcoded.

---

### Post by mastablasta on 2015-07-03
1080 is fine on RPi. probably even better on latest model (more ram, faster CPU). it has hardware decoding.

anyway as far as codecs the issue is with some, yet some have to be bought (they are cheap and I haven't bought any as I didn't need them). I don't know how good it is at recording. I never tried any. I am sure faster better one will do it well better. but for the money payed Rpi does a good job.

it helps it that my eye sight is not that good so I don't really distinguish between 720 and 1080 unless I am close to the TV set :)

sometime i also forget that my package includes full HD programs. when I do watch them by accident the experience is about the same. so I am definitely not the target for a hi end system.

---

