---
title: "media server"
date: 2009-07-31
forum: Server Platforms
---

### Post by waspinator on 2009-07-31
Hi,

I would like to have a way to stream music and video (and maybe even high resolution images if possible) across the internet from my ubuntu server. 

If it was web based it would be best.

I have a dyndns account, so accessing my server from the Internet isn't a problem.

From what I understand there is a way to use the VLC client as a server also, but I could not find a good guide on how to do this.

GNUMP3d looks alright for only music streaming, but it's perhaps one of the ugliest things I have ever seen.


I have heard of darwin streaming server, but not how to use it.

iTunes has some photo streaming similar to what I'm looking for ( [http://support.apple.com/kb/HT1273](http://support.apple.com/kb/HT1273) )

It looks like VLC is the best option for video streaming and GNUMP3d is the best for music. I guess what I'm looking for is a guide to setting these up.

Can anyone give me an idea of where to start looking for a way to do this?

---

### Post by ridetheteapot on 2009-07-31
my favorite way of streaming music is mpd + icecast. you use a mpclient to control what icecast streams. not bad to set up, especially if you use mpd already.

for video i really dont know. divx quality movies are usually around 1 meg / sec bitrate right? that kinda hard to shove through the thin internet tubes. you might need to downgrade the quality while streaming - if thats the case you can't use something simple like ssh.

---

### Post by R.Bucky on 2009-08-01
Gnump3d is somewhat archaic compared to Jinzora. The interface is a little busy, but it really is great. For videos, I have not found a great option, but you might try JW FLV Media Player.[http://www.longtailvideo.com/players/jw-flv-player/]("http://www.longtailvideo.com/players/jw-flv-player/")

---

### Post by MrWES on 2009-08-01
> **waspinator said:**
> Hi,

I would like to have a way to stream music and video (and maybe even high resolution images if possible) across the internet from my ubuntu server. 

If it was web based it would be best.

I have a dyndns account, so accessing my server from the Internet isn't a problem.

From what I understand there is a way to use the VLC client as a server also, but I could not find a good guide on how to do this.

GNUMP3d looks alright for only music streaming, but it's perhaps one of the ugliest things I have ever seen.


I have heard of darwin streaming server, but not how to use it.

iTunes has some photo streaming similar to what I'm looking for ( [http://support.apple.com/kb/HT1273](http://support.apple.com/kb/HT1273) )

It looks like VLC is the best option for video streaming and GNUMP3d is the best for music. I guess what I'm looking for is a guide to setting these up.

Can anyone give me an idea of where to start looking for a way to do this?

For music, I'd look into mt-daap (aka Firefly media server) it's in the repos. It was actually created by Apple, and Rhythmbox, Aramok, and iTunes will pick up on a network mt-daap music shares. I run an mt-daapd server on my ubuntu server running Hardy 8.04.
[http://www.fireflymediaserver.org/index.php]("http://www.fireflymediaserver.org/index.php")

For streaming video you might try mediatomb.

[http://mediatomb.cc/]("http://mediatomb.cc/")

~Bill

---

