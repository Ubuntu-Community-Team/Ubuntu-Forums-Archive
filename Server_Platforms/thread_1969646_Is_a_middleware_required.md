---
title: "Is a middleware required?"
date: 2012-04-30
forum: Server Platforms
---

### Post by deepakdeshp on 2012-04-30
I am planning to deploy an Apache  web server on Ubuntu server 10.04 . It will mostly serve big audio and video files . Do I need to use any middleware or application server like  like Tomcat? Since there are no java components, Tomcat may not help.

 There will be at most 50 simultaneous connections to the web server. How to size for hardware like cpu and memory for this load?

---

### Post by elico on 2012-05-01
what audio and video files will you serve?
50 connections is not that much.
you will need fast HD or raid array to serve those files fast.
most of basic server hardware should be what you need (dual\quad core) depends exactly on the files size but 4gb should do the job.
by the way what is the clients\server bandwidth?(you will need to fit you HD\raid speed to the clients bandwidth).

---

### Post by deepakdeshp on 2012-05-01
> **elico said:**
> what audio and video files will you serve?
50 connections is not that much.
you will need fast HD or raid array to serve those files fast.
most of basic server hardware should be what you need (dual\quad core) depends exactly on the files size but 4gb should do the job.
by the way what is the clients\server bandwidth?(you will need to fit you HD\raid speed to the clients bandwidth).

Do you mean that the HD / RAID speed should be equal to or more than the clients bandwidth? But this bandwidth will vary depending on how many clients are connected. The clients will connect to the server over a single wireless router and there will not be any other networking equipment like switches etc.

The files will be of different types like mpeg , .wav etc and the average size of the files around 700 MB.

 software RAID using  ordinary SATA disks will be a cheaper solution. Hardware RAID would be costly. Any comments on this?

---

### Post by Gyokuro on 2012-05-01
Hi

If I read correct you will serve your files over Wifi? Then your bottleneck is your WLAN - a quad core with at least 8GB RAM should handle this easy depends on your HD setup (software raid with 4 disks with LVM should handle this fine).

---

### Post by SeijiSensei on 2012-05-02
Fifty streaming clients over wireless sounds like a recipe for laggy video to me.  What resolution(s) are the files?  You might need to go as low as 240p.  What codecs are you using for encoding?  H.264/AAC in the Flash container?  XviD/MP3 in the AVI container?

---

### Post by deepakdeshp on 2012-05-02
> **SeijiSensei said:**
> Fifty streaming clients over wireless sounds like a recipe for laggy video to me.  What resolution(s) are the files?  You might need to go as low as 240p.  What codecs are you using for encoding?  H.264/AAC in the Flash container?  XviD/MP3 in the AVI container?

I am not aware of the video and audio formats and what would make it more efficient. The content will be pulled by Android tablets. So it looks like I need some software/ browser add ons on the client side. Please suggest.

---

### Post by SeijiSensei on 2012-05-02
Do you already have the files?  Try playing one from the command line with mplayer and see what it reports.

---

### Post by deepakdeshp on 2012-05-02
> **SeijiSensei said:**
> Do you already have the files?  Try playing one from the command line with mplayer and see what it reports.

The client will be Android and hence it may not have mplayer.

---

### Post by SeijiSensei on 2012-05-02
No, I meant if you want to find out how the files are encoded, you can play one with mplayer on Ubuntu and see what it reports like this:

```

$ mplayer /path/to/somefile.mkv

Playing somefile.mkv.
libavformat version 53.21.0 (external)
libavformat file format detected.
[matroska,webm @ 0xb6bc9d80]max_analyze_duration reached
[matroska,webm @ 0xb6bc9d80]Estimating duration from bitrate, this may be inaccurate
[lavf] stream 0: video (h264), -vid 0
[lavf] stream 1: audio (aac), -aid 0
VIDEO:  [H264]  1280x720  0bpp  23.976 fps    0.0 kbps ( 0.0 kbyte/s)

```

This one has H.264 video at 720p resolution and AAC audio.

---

### Post by deepakdeshp on 2012-05-03
> **SeijiSensei said:**
> No, I meant if you want to find out how the files are encoded, you can play one with mplayer on Ubuntu and see what it reports like this:

```

This one has H.264 video at 720p resolution and AAC audio

```.

That is is excellent information. I never know that mplayer was so powerful and provided such a wealth of information. 

But once we have information like a file has has H.264 video at 720p resolution and AAC audio, what steps do I take next to ensure efficient delivery of the audito/video to the Android clients?

---

### Post by SeijiSensei on 2012-05-03
Well if there are fifty of them connecting over wifi, I'm going to guess that you won't be able to send them all 720p content simultaneously without running into bandwidth issues.  Files like this can have bitrates in the 1500-2000 Mbit/sec range.  A 54 Mbit line might handle a few dozen simultaneous streams, though the fact that 802.11 wifi is half-duplex will probably be a limiting factor as well.

As for what happens on the Android end, I don't know.  I don't have a smartphone.  Doing a Google search for "media player android" brings up a variety of options including a build of VLC for Android.  That might be your best choice if you need to support a wide variety of codecs and containers.

You can probably deliver the streams using Apache; tell the phone's browser to launch VLC to handle AVI, MP4, MKV, etc. URLs.  A more efficient approach would be to use NFS since it's a UDP protocol that just blasts the packets over the network.  Connecting an Android phone to an NFS share is way outside my pay grade, though.

---

### Post by deepakdeshp on 2012-05-04
> **SeijiSensei said:**
> 
You can probably deliver the streams using Apache; tell the phone's browser to launch VLC to handle AVI, MP4, MKV, etc. URLs.  A more efficient approach would be to use NFS since it's a UDP protocol that just blasts the packets over the network.  Connecting an Android phone to an NFS share is way outside my pay grade, though.

That is a good suggestion to set up the nfs server and serve the contents. Are there any guidelines which type of files are more efficient to transfer ? .mp4, or whatever encoding, codeecs etc. If I know this information, all the other files can be converted to this file type and they will be served from the server.

But the Android tablets will require root access to mount the nfs share, which will not be possible. [http://forum.archosfans.com/viewtopic.php?f=59&t=36010](http://forum.archosfans.com/viewtopic.php?f=59&t=36010)

---

### Post by SeijiSensei on 2012-05-04
> **deepakdeshp said:**
> That is a good suggestion to set up the nfs server and serve the contents. Are there any guidelines which type of files are more efficient to transfer ? .mp4, or whatever encoding, codeecs etc. If I know this information, all the other files can be converted to this file type and they will be served from the server.

Files are files.  They're all going to be transferred as a bitstream.  XviD in the AVI container is probably the most compatible combination since it doesn't require the same horsepower to decode the video that H.264 does.  XviD has slightly lower video quality than H.264 for equivalently-sized files, but on a tablet you may not notice the difference, especially at lower resolutions like 360p or 480p.  You'd have to test the actual devices you're intending to use to see what works best in your case.  

> But the Android tablets will require root access to mount the nfs share, which will not be possible. [http://forum.archosfans.com/viewtopic.php?f=59&t=36010](http://forum.archosfans.com/viewtopic.php?f=59&t=36010)

I use NFS, but I have root privileges and just mount the remote share into the client's filesystem.  I can watch HD video across a wifi connection using NFS without any visible lags.  Of course, I'm just one user watching one stream.

It is possible to configure an NFS server so that ordinary users can mount shares, but it takes some work to avoid needing root privileges (use a port > 1024, make the mount command suid, etc.).  Search Google for "mount nfs as user" for tips.  How all of this relates to Android is a whole other issue about which I know zero.  I did see some stuff out there about an SMB ("Samba") client for Android, so that's a possibility, but it's a TCP service.  If you go the TCP route, you might as well use HTTP as the transport and let the browser launch the media player when it opens a video URL.

RTSP is another possibility, and Apple's [Darwin]("http://www.howtoforge.com/apples-darwin-streaming-server-on-centos-5.2") server also runs on Linux.  I think VLC can also stream over RTSP.  If you're distributing the same stream to all the clients simultaneously, you might want to look into using [multicasting]("http://forum.videolan.org/viewtopic.php?f=13&t=12138") to conserve bandwidth.  Again these are areas where I'm not really able to help.  I'd guess that using VLC on both ends might be the easiest solution to set up.

---

### Post by gordintoronto on 2012-05-04
The other interesting question is, what upload speed does your ISP and network hardware support? If you're on a consumer-grade connection, you won't be supporting 50 simultaneous clients -- or 4, either.

---

### Post by SeijiSensei on 2012-05-04
From what I can tell, the OP is talking about distributing the streams over a local wifi network to clients with Android tablets.  A school setting, perhaps?

---

### Post by deepakdeshp on 2012-05-06
> **SeijiSensei said:**
> From what I can tell, the OP is talking about distributing the streams over a local wifi network to clients with Android tablets.  A school setting, perhaps?
Yest thats right a school set up.

---

### Post by deepakdeshp on 2012-05-06
> **gordintoronto said:**
> The other interesting question is, what upload speed does your ISP and network hardware support? If you're on a consumer-grade connection, you won't be supporting 50 simultaneous clients -- or 4, either.

There wil not be any ISP . All the contents will be stored on the server and distributed to the tablets over the intranet. No content will come from internet to the tablets.

---

### Post by deepakdeshp on 2012-05-06
> **SeijiSensei said:**
> Darwin[/URL] server also runs on Linux.  I think VLC can also stream over RTSP.  If you're distributing the same stream to all the clients simultaneously, you might want to look into using [multicasting]("http://forum.videolan.org/viewtopic.php?f=13&t=12138") to conserve bandwidth.  Again these are areas where I'm not really able to help.  I'd guess that using VLC on both ends might be the easiest solution to set up.

it will be an Ubuntu desktop which will be the server. Same file simultaneously is another good tip. But sometimes it may be different files being served over the intranet.

---

### Post by deepakdeshp on 2012-05-10
NFS protocol seems to be the way to go. It is much faster than other protocols.

[http://wdtvforum.com/main/index.php?topic=5393.0](http://wdtvforum.com/main/index.php?topic=5393.0)

---

### Post by SeijiSensei on 2012-05-10
I'm not surprised that NFS outperforms those other protocols, but isn't there still a problem with ordinary users mounting NFS shares on Android devices?  Or did you find a solution for that?

---

### Post by deepakdeshp on 2012-05-10
I didnt find a solution how ordinary users can mount the shares on their tablets.

---

