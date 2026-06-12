---
title: "Ubuntu Cast: thoughts on streaming to the big screen"
date: 2017-12-19
forum: Ubuntu Application Development
---

### Post by pimmhogeling on 2017-12-19
Hi everyone,

This is an idea for an Ubuntu app. Please guide me if there is a better place to post this, as I am not familiar with this maze.

At  home, I stream videos from my Ubuntu-powered notebook to my  Chromecast-powered TV. My notebook hosts the videos. The Chromecast  downloads the videos through the local network and decodes them. My  phone is the remote. It works well. I feel perhaps other Ubuntu users  would enjoy being able to copy my setup.

[HR][/HR]
The challenge: taking  videos &#8210; perhaps DVD rips or home videos of dogs &#8210; from an Ubuntu  desktop or notebook and showing them on the biggest screen in the house.

The  old-fashioned way connects the two devices with an HDMI cable. An  increasingly popular alternative is to open the video in Google Chrome  and casting the entire tab.

The setup I have in my home has two (potential) advantages over casting a Chrome tab:
[LIST]
[*]From what I understand, casting a Chrome tab actually decodes and  simultaneously encodes any video within Chrome. This unnecessarily puts  stress on the desktop/notebook, and any hiccups on that side would cause  frame drops on the TV. My setup requires next to no effort from the  desktop/notebook, and allows the Chromecast to load parts of the content  in advance as it would with a YouTube video. I think it therefore has a  higher chance of uninterrupted playback. 
[*]My setup allows a user to  pause and resume, seek within the video, and jump to another video from  their phone. The experience is similar to that of casting content from  YouTube, Crunchyroll, or the NPO app. 
[/LIST]

An Ubuntu app could make  this setup easy to achieve. And the technology is here. (In fact,  GNU+Linux is great at being a server.)

A visual representation of my vision can be found here: [ilumbo.org/ubuntu-cast/mockup/01.png]("http://ilumbo.org/ubuntu-cast/mockup/01.png").

In  the Ubuntu app running on the desktop/notebook, a user would select  videos to make available for casting. The app would then spin up a file  server on some port.

The user would then open up an app on their  phone or tablet. It would somehow have to connect to the file server on  the desktop/notebook. Perhaps that machine knows its own IP address and  shows a QR code for the handheld (phone/tablet) to scan. Network Service  Discovery would be even easier.

Once the app on the handheld is  connected, it shows a list of the available videos. The app can cast  just like YouTube and Crunchyroll can. Once connected to a Chromecast or  "Chromecast built-in" TV, the phone serves merely as a remote.

Limitations:
[LIST]
[*]The desktop/notebook with the videos, the handheld, and the Chromecast have to be on the same network. 
[*]The videos have to be encoded in a format [supported by Google Cast]("https://developers.google.com/cast/docs/media") (essentially H.264 or VP8/"*WebM*"). 
[*]Although the handheld is no longer strictly needed once there's content on the TV, the desktop/notebook has to stay awake. 
[/LIST]

An alternative setup takes out the handheld and sends instructions directly from the Ubuntu desktop/notebook to the Chromecast.

[HR][/HR]
I  would like to ask you: how useful do you think such an app would be? Is  there any software that you know of which already does this, or part of  this? I've found [*Plex*]("https://www.plex.tv/") and *[Videostream for Google Chromecast]("https://chrome.google.com/webstore/detail/videostream-for-google-ch/cnciopoikihiagdjbjpnocolokfelagl")*, and I've read that VLC has Chromecast support as well.

If  such an app is deemed useful and fit for Ubuntu, I would like to work  on it. Relevant background: I have experience building Android apps as  well as Google Cast receivers (the things that run inside the  Chromecast), but not so much with building Ubuntu apps.

---

### Post by TheFu on 2017-12-19
Basically, this has been solved for 5+ yrs, IMHO.  I'm probably NOT the target audience.  If you are tied to a chromecast, then there isn't much point in reading farther.  

chromecast is hobbled software and hardware designed by google to track which videos people watch and limit the types of video encoding allowed.  If you step away from that limited platform, lots of solutions work.  There isn't a perfect solution, as far as I'm concerned, at least not yet.

There are single app solutions.
There are client-server applications that work together which solve this.  There are multi-tiered solutions talking specific protocols between each component.
There must be 50 different ways to put these things together for a solution available today.  Most of the solutions don't require videos to be encoded in the "blessed google" formats to work either.

Over the years, I've used a few different solutions to the problem of watching content on projection systems.  A few:
1) MediaGate with internal HDD holding content.  This was directly connected to the TV/Projector. It supported about 15 different video file codecs, but was SD only.
2) WD TV Live HD with samba access to media files.  The was also directly connected to the TV/projector, but the media was network accessed (or USB connected locally).  It supported about 15 different video file codecs and HD, but didn't support some older codecs.
3) Normal laptop running XBMC with both local and remote access via NFS to media files.  NFS is more efficient than samba and removes some of the file permissions issues.  The laptop used would control how much high def content types were supported.  I started with an Asus EEE, which could handle pretty much **any** video codec, but not content over 600p resolutions.  It fixed the WD TV Live vcodec issues, but not the hi-def playback issues.  These days Kodi would be used instead of XBMC.
4) Purpose built $100 "media PC" running Kodi with newer GPU that supports HW decoding of hidef video content.  About this time, I added in a Plex Server after trying multiple DLNA servers.  Plex was much better than the others I tried for my needs.  Those included minidlna, Win7 MC, and a playstation media center.  Eventually, support for the AMD GPU for in this machine was dropped by AMD.  At this point, I moved to ... 
5) Raspberry Pi v2 or v3 running Kodi.  I use PlexBMC on kodi to interface with the media on a central plex server.  The rpi v2 needs the paid mpeg2 video codec to allow watching of live ATSC broadcast TV from networked HDHR tuners.  The rpi v3 doesn't need this mpeg2 codec, as the CPU has sufficient power. Not bad for a $48 cost (pi, case, psu).  Add in a $15 RC6 remote for a fairly complete playback solution that millions of people are using today.

I tried to use a chromecast, but found it to be extremely limited for what it could play and it didn't work disconnected from the internet.  The real issue was not being able to play TV recordings (mpeg2-ts/AC3 audio) or broadcast TV. That was unacceptable.  Plex Server does help a little, since if the server hardware is powerful enough, plex will transcode to a video format supported by the client machine, the chromecast.  A chromecast can be used as a DLNA Renderer, just with poor audio support. My chromecast is 3 yrs old, so perhaps they've fixed the lack of DTS/AC3 and 7.1 audio in newer versions?  For me, the chromecast is a youtube-only device, which really doesn't interest anyone in the house.

Also have a Roku.  This device isn't as braindead as the chromecast. It comes with a useful remote.  The video types are limited, but it does have an audio passthru that works for unsupported audio codecs.  It also supports thousands of different video providers for a relatively tiny price. I tend to use the roku for DRM'd streams. There is an Android roku remote app that **is** handy for entering text - mainly for passwords or searches.  I tend NOT to have an android device nearby when watching TV. The remote stays in the room unlike the phones/tablets.  Call this a _cultural difference_.

Whether Android devices are a viable remote is debatable.  They are not for me, at least as a primary device. I use a DLNA controller on Android (bubble-upnp) to control the DLNA Server (plex) and DLNA Renderers (Roku, Kodi machines, laptops).  This is mainly used to control music playback in different parts of the campus/house. Occasionally, bubble-upnp is used to send videos to the playback devices, but normally an rc6 remote control is used.

Thanks to using a VPN, I can completely control the Plex server and stream to my local device from anywhere in the world. This is without any plex account. My primary issue with Plex is they aren't F/LOSS.  I want the source code and the rights to make improvements that can be shared with the world.  At this point, Plex is the best answer from the less-than-perfect options.

If your proposal is to replace a Plex Server with something new that will be completely F/LOSS, then you'll want to make a DLNA server.  DLNA has a number of issues which make it less useful in a household. Mainly the lack of any access controls over content to be played.

Ubuntu is just Linux. A properly created Linux service will run on any Linux, including Ubuntu.  If you insist on targetting only Ubuntu desktops, then you'll be limiting your community from many of the most technical people.  Ubuntu Desktop development tools that are specifically designed for Ubuntu-only use are more about easily making a pretty GUI than anything underneath.  To make a useful media server, one that can transcode the content to what a chromecast needs, you'll want to leverage ffmpeg and a few other existing projects. Transcoding is mandatory, if you are stuck with a chromecast, IMHO.  It is next to useless without it. Standard Unix-style development is how I develop for Linux systems.  The OS is the IDE after all.

Just looked at your image file - I wouldn't use a file server. I'd use a streaming protocol.  File servers just aren't necessary for things like this and certain file server protocols which are likely have issues that you don't want to deal with like file permissions.

BTW, I have played with a node.js server that streams to DLNA renderers.  It was painful to use, so I stopped trying to deal with it.  Mainly it used lots of odd ports for communications, but didn't clearly document each and the purpose for each.  Linux users tend to firewall everything. I do.  If you don't explain exactly which ports need to be open between exactly which systems, forgetaboutit.
[https://www.npmjs.com/package/castnow](https://www.npmjs.com/package/castnow) was the project.  There are many others, it seems. [https://www.npmjs.com/browse/keyword/chromecast](https://www.npmjs.com/browse/keyword/chromecast)

Or did I completely miss the point?

---

### Post by pimmhogeling on 2017-12-19
Thanks for your input, Fu-boss!

I am not *tied* to the Chromecast, but in my house it is the only input the TV has (besides a Wii U).

Not too long ago, I had a similar setup to the last three you mentioned: with a "media" PC connected to the TV. Somewhere in the late summer of 2017 we ditched the PC and have been watching everything through the Chromecast since. (Live) TV, films, series, online content. I personally love the setup and find that watching content on the big screen but controlling it on the small (touch) screen is more pleasant than anything I've tried before.

You have quite a different experience. You've tried the Chromecast, but the spectrum of possibilities it offers is too narrow for you. That is something I definitely understand as well.

Whether this app would make any sense stands or falls by how many users with a Chromecast-centered TV arrangement exist. So your input and anyone's input on this is very valuable. (Even though you would indeed not be the target audience. I wouldn't even really be the target audience. We've already answered our own needs.)

[HR][/HR]
The idea would be to make it FOSS, yes. From the app that runs on Ubuntu, to the app that runs on Android, to the receiver that runs inside the Chromecast.

I see no need to make any of it specific to Ubuntu. (I just love the sound of *Ubuntu Cast* over, well… *Linux Cast* or *SC2C* for a working title.)

Using a protocol designed for streaming rather than a protocol designed for file transfer makes a lot of sense.

---

### Post by TheFu on 2017-12-19
"ubuntu cast" might sound like a nice name, but it isn't highly unique, so searching for it on the internet would be a total failure.  The internet is full of projects that fail because their names aren't something unique enough to be found.  For example, I run a "typo" blog server.  Just try to find anything about that on the internet. Hint: it is NOT typo3.  10 yrs after the project started, they finally renamed it. This is a competitor to WP.  

People interested in casting content to a DLNA-renderer on their LAN will probably have lots of content that is stored in older video files.  I'm watching an xvid encoded video now for example.  Plex is transcoding it into h.264 video and leaving the mp3 audio alone for playback.

Anyways, I hope those node.js project links are helpful.  Lots of progress has happened. Hopefully, you'll find a project that will appreciate your skills. Good luck!

---

### Post by again? on 2017-12-19
@pimmhogeling
Have you tried [Plex]("https://www.plex.tv/downloads/") with the [android app]("https://play.google.com/store/apps/details?id=com.plexapp.android")?

---

