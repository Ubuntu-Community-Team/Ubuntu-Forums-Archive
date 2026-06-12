---
title: "Securly stream music to iphone?"
date: 2014-12-15
forum: Server Platforms
---

### Post by sangsterthegangster on 2014-12-15
Hello,

I have a Ubuntu 14.04 Web/file server that I would like to use to stream music to my iPhone and other devices over the internet (like Spotify or Pandora). I am looking for a solution that is not clunky and have had a bit of a hard time finding something that id feel comfortable placing on a publicly accessible server.

 I've seen things like Plex server but they all seem like they are made for a home network. 

Just wondering if anyone could give me suggestions for how this might be done securely?


Thanks in advance!

---

### Post by QIII on 2014-12-15
Spotify and Pandora pay royalties to artists for making their music available on publicly accessible servers.

We cannot support the potential for copyright infringement.  "Publicly accessible" implies more than just logging in to a private server to transfer private files for one's own purposes.

Closed.

---

### Post by Elfy on 2014-12-16
Re-opened.

As long as this does not turn into "How do I stream music to the world without dealing with the legaility" we're not going to be worried.

---

### Post by TheFu on 2014-12-16
I didn't see the OP asking to do anything illegal. There wasn't any mention of sharing, just making it available to his/her remote devices. Did I misread?

However, I don't know of any non-clunky way to accomplish it either and for the security aspect, a VPN will be required, like openvpn. Then just use Plex Server since your remote devices would be on the same LAN subnet.  How clunky is this?  I suppose it depends on the VPN client app and the DLNA client/renderer you choose to run on the device.  I've never used the Plex client, but I do use BubbleUPnP on Android and do find it clunky if the connection fails.

Using this method, no Plex website login is needed either. Your media is YOUR media, even if the Plex team has a major bug and opens the content of your system(s) to the world.

Plex Server has been a nice solution for us. Was running XBMC for a few years before and still use XMBC as a player in the main room with PlexBMC plugin, which limited playback to just that single audio/video setup. With Plex Server, any DLNA client/renderer seems to be available on the network to display the media - it definitely works with all the DLNA clients I've tried and streaming to a chromecast works, provided the media is in a supported format (or the Plex server can transcode on-the-fly to what the renderer needs).

---

### Post by volkswagner on 2014-12-17
I'm not sure if you need an open source solution.

I have tried Jinzora in the past, but the documentation and support were nearly non-existent.

Here is a link to a [list of possibilities]("http://alternativeto.net/software/jinzora/"), key words were "Jinzora Alternative".

Some you may be able to secure via the web server and some you may be able to run via VPN.

I was kinda excited when Amazon offered unlimited music storage for Prime members, until I read [this article]("http://techland.time.com/2011/07/08/why-amazons-unlimited-cloud-music-storage-deal-is-partly-bogus/") explaining the serious limitations.

---

### Post by ted.drain on 2014-12-21
If you're talking about streaming your own music to your phone, I can recommend madsonic ([http://www.madsonic.org/](http://www.madsonic.org/)) which is a free fork of subsonic.  Any subsonic iphone app should work fine with it (iSub, ???).  I'm an android user so I use an app call ultrasonic which works great.  I use plex for pictures and video but I think madsonic works a lot better for music.

---

