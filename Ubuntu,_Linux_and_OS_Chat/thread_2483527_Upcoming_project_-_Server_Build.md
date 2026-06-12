---
title: "Upcoming project - Server Build"
date: 2023-02-01
forum: Ubuntu, Linux and OS Chat
---

### Post by Eric the Grey on 2023-02-01
Good afternoon everyone.  I come to you with a plan that I'd like to have opinions on.

I may be inheriting a Dell Optiplex 3050 small form factor PC from work when they stand down our department.  Since they have suttered our building, and there is no other in my state, they have been simply telling those they have already let go, to keep them after remotely wiping them.  I have a plan for it.

The plan:
Add a 500gb NVME drive to the box 
Replace the 500GB HD with a large (5-10TB) drive.
Possibly add a 4TB external drive to the mix.
Install Ubuntu Server.

My plan is to use the server as a combination of file server (SMB) for our windows computers to back up to, and move my Plex server (or possibly switch to Jellyfin).  

I can probably run both Plex and Jellyfin together, pointing to the same media repositories.  I did it on my current desktop which hosts my Plex server now briefly.  Moving this off of my gaming machine will allow me to shut it down at night and likely improve my systems performance. 

Once installed, I plan to create user accounts and shares for SMB. Each share will be for a specific computer (3 laptops and 2 desktops) which will run scheduled backups to the share.  If I add the USB external drive, that will probably host the SMB shares.

Plex will go on the large internal drive.  My media is currently on said external drive, attached to my PC. It is roughly 90% full now.  If I can swing the 10TB drive, it will give me a lot of room to grow.

So that's my plan.  I'm comfortable enough with the command line, but not completely fluent in Linux, so I won't be surprised that I'm overlooking something.  

Any ideas on what could or should be done different?  Better?

---

### Post by TheFu on 2023-02-02
NEVER use SMB (CIFS) for backup storage.  Cryptoware knows about these and will happily seek them out and encrypt any network storage.
Of course, you can setup parts of the storage to be used with CIFS, but just not the backup areas.
You'll want a separate physical disk for backups anyways.

I use Jellyfin and have for about a year. Switched from Plex. Both have problems.  I ran both for many months sharing the same repos.  When I did a fresh OS install (20.04), I just never bothered installing Plex. I don't miss it.    For my content, Jellyfin has much better metadata lookup. Plex wouldn't be able to find about 20% of the content or would connect it to the wrong data.  Jellyfin gets it right about 98% of the time.

Jellyfin isn't picky about audio file formats, unlike Plex which has really poor audio support.

What Plex does better is make remote access easier, provided you don't mind every button, or other input sent back to the Plex home servers.  They track EVERYTHING.  With Jellyfin, there's no tracking, except by the metadata providers YOU enable.  For me, that was the major deciding factor, plus, I have remote access to my LANs using a VPN or ssh-tunnel or SOCKS5 ssh-proxy, so remote access provided by plex wasn't needed.

If you aren't a Linux guru already, perhaps you'd be happier loading a NAS distro, say TrueNAS?  [https://arstechnica.com/gadgets/2020/06/truenas-isnt-abandoning-bsd-but-it-is-adopting-linux/](https://arstechnica.com/gadgets/2020/06/truenas-isnt-abandoning-bsd-but-it-is-adopting-linux/)  The article author works (worked?) for the company behind TrueNAS.  BTW, Jellyfin runs on TrueNAS [https://www.truenas.com/community/threads/how-to-get-started-with-jellyfin-on-truenas-scale.107433/](https://www.truenas.com/community/threads/how-to-get-started-with-jellyfin-on-truenas-scale.107433/)

I fear your storage plans don't include sufficient backup storage.   For backups of Windows, I'd strongly suggest a client/server solution like bacula.  [https://www.bacula.org/free-windows-backup-software/](https://www.bacula.org/free-windows-backup-software/)  
For Unix-based backups, I like rdiff-backup for a number of reasons, but mainly efficiency and the ease of finding and restoring files ad hoc.  I "pull" backups from client machines.  Of course, you can use bacula for that as well.

The clients cannot access the backup storage directly thanks to the client/server architecture that doesn't use shared network storage. This prevents malware from screwing with the backup storage. That is very important for all backups, but especially for MS-Windows.

I should mention that I use Jellyfin as a server, not to watch video content. For watching, I have Kodi/OSMC running on a few raspberry pi systems around the house.  There are 3 methods to get Jellyfin managed content onto the TVs here.  
* DLNA
* Jellyfin addon for Kodi
* JellyCon addon for Kodi
In general, I use a tablet running Jellyfin app to see all available content, then choose where it will be displayed.  That can be to any Kodi system in the house or local on the tablet.  It is pretty slick, usually.  I have a complex network, so the tablet isn't on the same network as the Jellyfin Server and the Players are on a different subnet than both of those other devices.  Security, but most homes would have them all on 1 network.  I just don't trust wifi ... not at all.

---

### Post by Eric the Grey on 2023-02-04
Thanks TheFu for your reply.  Sorry I haven't replied until now, but I had eye surgery and am only just now able to sit and read, and only to a point. :P  

Luckily this is not something I'm going to be doing any time soon.  I have at least another 2 months before the machine becomes available for use and then, I have to make sure I can acquire the necessary drives.   I would love to have more space for backups.  I will look into Bacula in more depth once I can do so, but after a quick look, it's unclear if it works with Windows 10/11 which comprises all our computers. The page of supported OS's only goes up to Vista, but the page you linked to Win10.  

Regarding Bacula, If I read what you wrote right, the backups are initiated from the server, and saved there as well?  That would be cool.  I would just have to make sure the wife remembers to leave her laptop open when the backups occur.  (again, I have not read much from their site yet). 

As to backup space, Only my personal gaming rig has any significant amount of data (~3.2TB), and I will probably only be able to back up my OS. Currently, I'm currently using Aoemi to create image backups to an external detachable drive.  It works very well and I've recovered my laptops drive more than once after wiping it for a temporary Linux install. I tinker around with it from time to time. It's really slow, and I haven't found a distro that I like well enough to keep on it (yet).  

I am in no way a Linux guru, more of a dabbler.  I stick with windows mainly because I'm also a gamer.  

Regarding TrueNAS, that was my first thought, but I saw that Jellyfin wasn't supported, so I dropped that thought.  Time to rethink that as well.

For Jellyfin, the real question is making it available outside my network.  That may be the biggest hurdle I have to get past.  I want to allow my brother, myself, and a few friends access to it, but don't want to provide them my plex login.  With Jellyfin, I can set up accounts providing them just the access they need.  I use my Plex from work a lot, although I'm sure that will change with the change in employers.  

Again, thanks for the reply.  I've got some reading to do, but right now, the bright screen is making my eyes water. :P

---

### Post by DuckHook on 2023-02-05
I'm sure both of you have a better handle on the Audio Video stuff than I do, but I've always wondered why people bother to install either Plex or Jellyfin?

I run a number of Kodi boxes that are connected to a plain fileserver. My movies, music, TV shows and family photos all show up in the Kodi box already organized, complete with descriptions, background notes and posters/artwork pulled from TVDB, all in a format that is attractive and informative.

I've visited both the Plex and Jellyfin sites but I've yet to gain any understanding of what either platform adds to what I already have.

By avoiding Plex or Jellyfin I keep my file server ultra lean, which allows me to use a Western Digital MyBookLive with firmware that has been replaced with OpenWRT. It sips power so lightly that I pay peanuts to run it 24/7. My assumption is that, were I to run Plex or Jellyfin, I would need a full&#8209;fledged server running at 20 times the power draw.

I guess what I'm asking is: what additional benefits do Plex/Jellyfin bring that make them worth the extra power draw, expense and hassle?

---

### Post by ajgreeny on 2023-02-05
I don't use Plex but do run Emby without its charged for premium account, simply because it is the easiest way that I'm aware of to stream my huge media library to my LG smart TV. I wish I could move to jellyfin which is open-source but at present there is no client for my TV, though it is expected in future to be available.

I do also use minidlna but that is a bit restricted in the filetypes it will stream, meaning I need to change so many of my recorded TV shows which àre .ts files to mkv or mp4, not difficult with ffmpeg but a bit of a bother and time consuming.

---

### Post by TheFu on 2023-02-05
I use Kodi for playback.  When I went multi-client, kodi's semi-support just wasn't good enough.  But I prefer Kodi's playback interface.
Kodi isn't lighter than either Plex or Jellyfin if you use it the same way.

However, I have mixed clients - some can handle only 1 type of video stream and either I need to convert every video in the collection to that format, or my streaming server needs to have transcoding capabilities.  That wouldn't work, since 1 client supports different video formats than an other and I'm not gonna have 2 pre-transcoded versions to allow playback on either of those devices.  Eventually, the devices will fail and I'll replace them with more capable R-pi v4 systems and can handle more playback types, but I don't see that happening for a few years, until those models become $50 again.

If you don't need to transcode, then a raspberry-pi can be your jellyfin media server.  Not much power is needed.  I happy to put jellyfin and my NAS in the same physical machine, but that isn't mandatory.

Plex fails on privacy nearly as much as roku fails.  If you've never looked at your router logs, you really don't understand how much data they are stealing.  Everything in your collection. Everything you play. Every voice command. Every remote click.  Everything anyone else sees, if you share media.  All of it - you've sold without being paid.  I couldn't look at myself in the mirror in the morning after doing that to my friends and family.  I just couldn't.  I'd say this is worse than using gmail, though that's pretty bad too.

For remote access into plex or jellyfin, there are many ways WITHOUT any plex account.  Like I mentioned before, I typically use a SOCKS5 ssh proxy back into the LAN, access the web interface and play things that way.  Back home, I seldom playback anything through the web interface.  It is used for scheduling OTA TV recordings.

BTW, jellyfin supports every audio media I've ever asked it to play. I suspect Kodi will too.  I must admit, audio playback using a full media center sorta sucks.  I much prefer quick any easy fuzzy searching for things to play.  I have a script for that, but sometimes use mpd.  I have mpd servers running around the house that keep up with a centralized audio NFS area.  Sometimes I just want hours of Van Halen or Beethoven or Funk.
```
 $ music-search funk
```
makes that happen.

---

### Post by Eric the Grey on 2023-02-05
> **DuckHook said:**
> I'm sure both of you have a better handle on the Audio Video stuff than I do, but I've always wondered why people bother to install either Plex or Jellyfin?

I run a number of Kodi boxes that are connected to a plain fileserver. My movies, music, TV shows and family photos all show up in the Kodi box already organized, complete with descriptions, background notes and posters/artwork pulled from TVDB, all in a format that is attractive and informative.

> **ajgreeny said:**
> I don't use Plex but do run Emby without its charged for premium account, simply because it is the easiest way that I'm aware of to stream my huge media library to my LG smart TV. I wish I could move to jellyfin which is open-source but at present there is no client for my TV, though it is expected in future to be available.

> **TheFu said:**
> I use Kodi for playback.  When I went multi-client, kodi's semi-support just wasn't good enough.  But I prefer Kodi's playback interface.
Kodi isn't lighter than either Plex or Jellyfin if you use it the same way.

This wasn't intended to become a discussion on which media software I'm using, but I do appreciate the comments.  I had forgotten about Kodi, which is something I will definitely look into.  I want to stay with a FOSS option if I do change.   I've put a lot of work into my Plex setup, including rage quitting a few years ago because of the aggravation I had with it.  Once I got it working though, it's been solid.

Anyway, thanks for the responses.  I'll most likely give each a test before deciding one way or another.  I've already ponied up for a PlexPass, I don't really want to do another.  :P

---

### Post by DuckHook on 2023-02-05
One of the things I like about these forums is the freedom we have to range far and wide. I've participated in many threads where something that at first feels like a mild digression turns into a learning opportunity that teaches me something very useful. I hope that my digression served a similar purpose.

To haul myself back on topic and answer your question more directly:

The reason that I raised the issue of the need for Plex at all was to address your question about the best use of your upcoming piece of gear. I also used to run my servers on standard boxes that I too salvaged from their earlier corporate lives. Then, about three years ago, I did my first migration of an existing MyBookLive by nuking its obsolete and dangerously unsupported firmware and replacing it with OpenWRT. This has given that tiny box a rebirth. It is now a flexible and robust little server that is easy to keep up to date and sips just the tiniest amount of power. It draws only 8 to 10 watts. I calculate an annual savings of a couple of hundred bucks of electricity at today's rates. This will only get more pronounced as our power rates continue to rise.

This strategy is so rewarding that I bought another MyBookLive so that I could run it as a nightly mirror to the existing one. I now have cheap redundancy with absurdly low power consumption. For me, the results are far superior to running another big box that draws ten times the power. I can get away with this strategy because all of my media is in either mkv, mp4, opus or flac, all formats supported by my KODI boxes. Therefore, I don't need on&#8209;the&#8209;fly transcoding which makes a simple file server a perfectly good solution. And, by avoiding additional complexity, I get the added benefit of a more robust system with fewer points of failure.

Perhaps the best use for your upcoming box is not as a server, but as a client, leaving server duties to lighter weight gear.

I don't know if this adds anything useful to your decision making process, but I hope that it provides some food for thought.

---

### Post by Eric the Grey on 2023-02-06
> **DuckHook said:**
> One of the things I like about these forums is the freedom we have to range far and wide. I've participated in many threads where something that at first feels like a mild digression turns into a learning opportunity that teaches me something very useful. I hope that my digression served a similar purpose.

No problem.  I try to be open about other points of view.  It may not change my mind in the end, but I try to at least look at them. 

> **DuckHook said:**
> Perhaps the best use for your upcoming box is not as a server, but as a client, leaving server duties to lighter weight gear.

I don't know if this adds anything useful to your decision making process, but I hope that it provides some food for thought.

One of the reasons for using this hardware is it's free.  The second, is because of the small form factor.  My original thought for this was to use a Raspberry PI, but transcoding is going to be a necessity because my video files are all over the place (avi, mp4, mkv, not to mention all different bitrates).  I know the power outlay won't be as low with this, but it'll be lower than my gaming rig running 24x7 given that I would normally shut it down at night, and when I'm at work. 

This I figured I could get started with a smaller outlay due to internal HD's being cheaper (somewhat) than external ones given the size I want. 

Until I can actually get the parts together, it may stand duty as a Linux sandbox.  I've been wanting to try SteamOS, but it won't load on my laptop as it requires a wired network to install (at least last time I checked).  The laptop is no where near a gaming machine at any rate, and that's my goal.

---

### Post by TheFu on 2023-02-07
> **Eric the Grey said:**
>  (avi, mp4, mkv, not to mention all different bitrates).  

Those are not video formats. They are just containers that hold encoded videos and encoded audio.  More and more the container matters less and less. It is the actual encoding used that matters. [https://cloudinary.com/guides/video-formats/a-primer-on-video-codecs](https://cloudinary.com/guides/video-formats/a-primer-on-video-codecs)

People get these things mixed up all the time, which leads to more confusion.

---

