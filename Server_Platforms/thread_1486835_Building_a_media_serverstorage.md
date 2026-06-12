---
title: "Building a media server/storage"
date: 2010-05-18
forum: Server Platforms
---

### Post by abucksdiver on 2010-05-18
Hi, 
I'm looking to turn an old PC I have laying around into a media server/extra file storage for the other computers in the house (Win XP, Ubuntu on a laptop, plus TV and PS3)

I'm guessing I can do this with Ubuntu server, plus suitable media server software? I will probably also want to download torrents (eventually!)

I was thinking of using VLC for the media server - any oppinions on this?

Is there anything else that I need to install? (Coming form a Windoze background, I'd rather work within a GUI environment)

I'm relatively new to Linux/ubuntu, so simple answers will be appreciated!

Thanks
Andrew

---

### Post by gobbledigook on 2010-05-18
hi there!

Ubuntu server and a samba share would be adaquate for file sharing over your LAN. For a media server do you mean to stream video to your TV through your PS3? or directly? what are the specs of the old PC?

i think to get the PS3 to see the linux box you will need to do something like this: [http://www.howtoforge.com/set-up-a-linux-playstation-3-media-server-with-ubuntu8.04]("http://www.howtoforge.com/set-up-a-linux-playstation-3-media-server-with-ubuntu8.04")

---

### Post by abucksdiver on 2010-05-18
Actually, both! (The TV can can "see" a media server if it is connected, and the PS3 can as well...)

---

### Post by jbrown96 on 2010-05-18
I've used Playstation Media Server (PMS) with a lot of success. I do mostly HD movies and many of them need to be transcoded to play, which really taxes my 2GHz Core 2 Duo. However, lower quality might work on your media.

If it's older than that and you need transcoding, then I doubt you can do it in real time. However, you could convert everything before hand with ffmpeg or mencoder. 

PMS is a Java app that's really easy to use, but you need to have a GUI system install (Ubuntu Desktop). It's probably worth a try since it's easy to setup and will be just as fast as any CLI transcoder. 

Media Tomb is another great UPnP media server that works fairly well with the PS3 (and maybe better with the TV); however, transcoding isn't as painless. It's also available in apt-get, so you don't have to install external software.

You should check your codecs (h.264, xvid, etc.) and containers (.avi, .mkv, .mp4) against the PS3 and TV supported ones to determine if you will need to transcode. That's probably the most serious consideration. If you don't need to, then mediatomb is your best bet. If you need to, then you either need a faster computer or need to start converting all your media.

---

