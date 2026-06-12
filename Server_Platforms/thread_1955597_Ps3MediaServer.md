---
title: "Ps3MediaServer"
date: 2012-04-09
forum: Server Platforms
---

### Post by bubylou on 2012-04-09
I have Ubuntu 12.04 Server and install the ps3mediaserver via the ppa found on this [guide]("https://help.ubuntu.com/community/Ps3MediaServer"). I cannot seem to find another helpful resources that dont use the GUI interface. I have set it to run at startup and have only changed the folders option in the root config files. I am trying to connect an Xbox to the server and have also tried vlc on my computer put nothing shows up on either.
```

[main] INFO  2012-04-09 21:09:57.470 Starting PS3 Media Server 1.51.0-mencoder34587-3 (ppa:happy-neko)
[main] INFO  2012-04-09 21:09:57.471 by shagrath / 2008-2012
[main] INFO  2012-04-09 21:09:57.471 http://ps3mediaserver.org
[main] INFO  2012-04-09 21:09:57.471 https://github.com/ps3mediaserver/ps3mediaserver
[main] INFO  2012-04-09 21:09:57.471 http://ps3mediaserver.blogspot.com
[main] INFO  2012-04-09 21:09:57.471
[main] INFO  2012-04-09 21:09:57.471 Build: f1bc902f8 (Thu Mar 15 16:18:00 2012 +0800)
[main] INFO  2012-04-09 21:09:57.471 Java: 1.6.0_24-Sun Microsystems Inc.
[main] INFO  2012-04-09 21:09:57.471 OS: Linux i386 3.2.0-18-generic-pae
[main] INFO  2012-04-09 21:09:57.471 Encoding: UTF-8
[main] INFO  2012-04-09 21:09:57.471
[main] INFO  2012-04-09 21:09:57.471 Working directory: /usr/lib/ps3mediaserver
[main] INFO  2012-04-09 21:09:57.475 Temp folder: /tmp/ps3mediaserver-root
[main] INFO  2012-04-09 21:09:57.475 Logging config file: /etc/ps3mediaserver/logback.headless.xml
[main] INFO  2012-04-09 21:09:57.475 debug.log: /var/log/ps3mediaserver/root//debug.log
[main] INFO  2012-04-09 21:09:57.475
[main] INFO  2012-04-09 21:09:57.475 Profile directory: /root/.config/ps3mediaserver
[main] INFO  2012-04-09 21:09:57.475 Profile path: /root/.config/ps3mediaserver/PMS.conf
[main] INFO  2012-04-09 21:09:57.475 Profile status: rw
[main] INFO  2012-04-09 21:09:57.476 Profile name: Bubylou
[main] INFO  2012-04-09 21:09:57.476
[main] INFO  2012-04-09 21:09:57.513 Loading MediaInfo library
[main] INFO  2012-04-09 21:09:57.530 Loaded MediaInfoLib - v0.7.54
[main] INFO  2012-04-09 21:09:57.535 Loading renderer configurations from /etc/ps3mediaserver/renderers
[main] INFO  2012-04-09 21:09:57.535 Loading configuration file: SamsungWiseLink.conf
[main] DEBUG 2012-04-09 21:09:57.536 Base path set to file:///etc/ps3mediaserver/renderers/SamsungWiseLink.conf
[main] INFO  2012-04-09 21:09:57.537 Loading configuration file: Showtime3.conf
[main] DEBUG 2012-04-09 21:09:57.537 Base path set to file:///etc/ps3mediaserver/renderers/Showtime3.conf
[main] INFO  2012-04-09 21:09:57.541 Loading configuration file: AirPlayer.conf
[main] DEBUG 2012-04-09 21:09:57.541 Base path set to file:///etc/ps3mediaserver/renderers/AirPlayer.conf
[main] INFO  2012-04-09 21:09:57.544 Loading configuration file: Philips.conf
[main] DEBUG 2012-04-09 21:09:57.544 Base path set to file:///etc/ps3mediaserver/renderers/Philips.conf
[main] INFO  2012-04-09 21:09:57.546 Loading configuration file: PhilipsPFL.conf
[main] DEBUG 2012-04-09 21:09:57.546 Base path set to file:///etc/ps3mediaserver/renderers/PhilipsPFL.conf
[main] INFO  2012-04-09 21:09:57.553 Loading configuration file: SamsungAllShare.conf
[main] DEBUG 2012-04-09 21:09:57.553 Base path set to file:///etc/ps3mediaserver/renderers/SamsungAllShare.conf
[main] INFO  2012-04-09 21:09:57.555 Loading configuration file: Bravia5500.conf
[main] DEBUG 2012-04-09 21:09:57.555 Base path set to file:///etc/ps3mediaserver/renderers/Bravia5500.conf
[main] INFO  2012-04-09 21:09:57.557 Loading configuration file: Streamium.conf
[main] DEBUG 2012-04-09 21:09:57.557 Base path set to file:///etc/ps3mediaserver/renderers/Streamium.conf
[main] INFO  2012-04-09 21:09:57.559 Loading configuration file: FreecomMusicPal.conf
[main] DEBUG 2012-04-09 21:09:57.559 Base path set to file:///etc/ps3mediaserver/renderers/FreecomMusicPal.conf
[main] INFO  2012-04-09 21:09:57.561 Loading configuration file: WDTVLive.conf
[main] DEBUG 2012-04-09 21:09:57.561 Base path set to file:///etc/ps3mediaserver/renderers/WDTVLive.conf
[main] INFO  2012-04-09 21:09:57.562 Loading configuration file: Kuro.conf
[main] DEBUG 2012-04-09 21:09:57.562 Base path set to file:///etc/ps3mediaserver/renderers/Kuro.conf
[main] INFO  2012-04-09 21:09:57.564 Loading configuration file: SonyBluray.conf
[main] DEBUG 2012-04-09 21:09:57.564 Base path set to file:///etc/ps3mediaserver/renderers/SonyBluray.conf
[main] INFO  2012-04-09 21:09:57.567 Loading configuration file: iPad-iPhone.conf
[main] DEBUG 2012-04-09 21:09:57.567 Base path set to file:///etc/ps3mediaserver/renderers/iPad-iPhone.conf
[main] INFO  2012-04-09 21:09:57.570 Loading configuration file: PS3.conf
[main] DEBUG 2012-04-09 21:09:57.570 Base path set to file:///etc/ps3mediaserver/renderers/PS3.conf
[main] INFO  2012-04-09 21:09:57.576 Loading configuration file: WMP.conf
[main] DEBUG 2012-04-09 21:09:57.577 Base path set to file:///etc/ps3mediaserver/renderers/WMP.conf
[main] INFO  2012-04-09 21:09:57.578 Loading configuration file: Bravia4500.conf
[main] DEBUG 2012-04-09 21:09:57.579 Base path set to file:///etc/ps3mediaserver/renderers/Bravia4500.conf
[main] INFO  2012-04-09 21:09:57.581 Loading configuration file: N900.conf
[main] DEBUG 2012-04-09 21:09:57.581 Base path set to file:///etc/ps3mediaserver/renderers/N900.conf
[main] INFO  2012-04-09 21:09:57.583 Loading configuration file: FreeboxHD.conf
[main] DEBUG 2012-04-09 21:09:57.583 Base path set to file:///etc/ps3mediaserver/renderers/FreeboxHD.conf
[main] INFO  2012-04-09 21:09:57.584 Loading configuration file: Android.conf
[main] DEBUG 2012-04-09 21:09:57.584 Base path set to file:///etc/ps3mediaserver/renderers/Android.conf
[main] INFO  2012-04-09 21:09:57.585 Loading configuration file: Panasonic.conf
[main] DEBUG 2012-04-09 21:09:57.585 Base path set to file:///etc/ps3mediaserver/renderers/Panasonic.conf
[main] INFO  2012-04-09 21:09:57.589 Loading configuration file: BraviaEX.conf
[main] DEBUG 2012-04-09 21:09:57.589 Base path set to file:///etc/ps3mediaserver/renderers/BraviaEX.conf
[main] INFO  2012-04-09 21:09:57.592 Loading configuration file: XBMC.conf
[main] DEBUG 2012-04-09 21:09:57.593 Base path set to file:///etc/ps3mediaserver/renderers/XBMC.conf
[main] INFO  2012-04-09 21:09:57.594 Loading configuration file: XBOX360.conf
[main] DEBUG 2012-04-09 21:09:57.594 Base path set to file:///etc/ps3mediaserver/renderers/XBOX360.conf
[main] INFO  2012-04-09 21:09:57.596 Loading configuration file: Realtek.conf
[main] DEBUG 2012-04-09 21:09:57.596 Base path set to file:///etc/ps3mediaserver/renderers/Realtek.conf
[main] INFO  2012-04-09 21:09:57.598 Loading configuration file: PopcornHour.conf
[main] DEBUG 2012-04-09 21:09:57.598 Base path set to file:///etc/ps3mediaserver/renderers/PopcornHour.conf
[main] INFO  2012-04-09 21:09:57.599 Checking MPlayer font cache. It can take a minute or so.
[main] DEBUG 2012-04-09 21:09:57.599 launching: /usr/lib/ps3mediaserver/linux/mplayer
[main] INFO  2012-04-09 21:09:57.613 Done!
[main] INFO  2012-04-09 21:09:57.616 Searching for plugins in /usr/lib/ps3mediaserver/plugins
[main] INFO  2012-04-09 21:09:57.617 No plugins found
[main] INFO  2012-04-09 21:09:57.645 Registering transcoding engine: FFmpeg Audio
[main] INFO  2012-04-09 21:09:57.648 Registering transcoding engine: MEncoder
[main] INFO  2012-04-09 21:09:57.649 Registering transcoding engine: MPlayer Audio
[main] INFO  2012-04-09 21:09:57.649 Registering transcoding engine: MEncoder Web
[main] INFO  2012-04-09 21:09:57.649 Registering transcoding engine: MPlayer Video Dump
[main] INFO  2012-04-09 21:09:57.649 Registering transcoding engine: MPlayer Web
[main] INFO  2012-04-09 21:09:57.650 Registering transcoding engine: tsMuxeR
[main] INFO  2012-04-09 21:09:57.650 Registering transcoding engine: Audio High Fidelity
[main] INFO  2012-04-09 21:09:57.650 Registering transcoding engine: VLC Audio Streaming
[main] INFO  2012-04-09 21:09:57.650 Registering transcoding engine: VLC Video Streaming
[main] INFO  2012-04-09 21:09:57.650 Registering transcoding engine: dcraw Thumbnailer
[main] INFO  2012-04-09 21:09:57.651 Using forced address Bubylou
[main] INFO  2012-04-09 21:09:57.651 Created socket: Bubylou/127.0.1.1:5001
[main] DEBUG 2012-04-09 21:09:57.717 Using database URL: jdbc:h2:/var/lib/ps3mediaserver/database-root/medias
[main] INFO  2012-04-09 21:09:57.717 Using database located at: /var/lib/ps3mediaserver/database-root
[main] DEBUG 2012-04-09 21:09:58.341 Database file count: 0
[main] DEBUG 2012-04-09 21:09:58.341 Database version: 1.51.0-mencoder34587-3 (ppa:happy-neko)
[main] INFO  2012-04-09 21:09:58.350 A tiny cache admin interface is available at: http://Bubylou:5001/console/home
[main] INFO  2012-04-09 21:09:58.355 Checking shared folder: /srv/samba/share/Video
[main] INFO  2012-04-09 21:09:58.355 Checking shared folder: /srv/samba/share/Music
[main] DEBUG 2012-04-09 21:09:58.407 Sending ALIVE...
[main] DEBUG 2012-04-09 21:09:58.410 non loopback/ipv4 addresses: [/192.168.1.2]
[main] DEBUG 2012-04-09 21:09:58.410 sub address for eth0 is []
[main] DEBUG 2012-04-09 21:09:58.410 found eth0 -> 192.168.1.2
[main] DEBUG 2012-04-09 21:09:58.411 non loopback/ipv4 addresses: []
[main] DEBUG 2012-04-09 21:09:58.411 sub address for lo is []
[main] DEBUG 2012-04-09 21:09:58.411 has /127.0.0.1, which is skipped, because loopback=true, ipv6=false
[main] DEBUG 2012-04-09 21:09:58.411 found lo, without valid address
[main] INFO  2012-04-09 21:09:58.412 Using the following UUID configured in PMS.conf: 117e72d2-4d81-42a2-b526-ce84115d1fe9
[main] INFO  2012-04-09 21:10:03.308 The server should now appear on your renderer
[UPNP-AliveMessageSender] DEBUG 2012-04-09 21:10:13.306 Sending ALIVE...
[UPNP-AliveMessageSender] DEBUG 2012-04-09 21:10:38.125 Sending ALIVE...
[UPNP-AliveMessageSender] DEBUG 2012-04-09 21:10:59.765 Error while sending periodic alive message: sleep interrupted
[PMS Listeners Stopper] INFO  2012-04-09 21:10:59.765 Sending BYEBYE...
[PMS Listeners Stopper] DEBUG 2012-04-09 21:11:02.711 Forcing shutdown of all active processes
[PMS Listeners Stopper] INFO  2012-04-09 21:11:02.711 Stopping server on host Bubylou and port 5001...

```

---

### Post by arrrghhh on 2012-04-09
Is this the file you're updating?

/root/.config/ps3mediaserver/PMS.conf

I don't see anything out of the ordinary.  Have you tried running it w/o any settings changes?

By default if the software can't find an X server it should automatically fail back to console mode.  Should...

Edit - are you killing the server, or does it die on its own?  The logfile is kinda confusing.

---

### Post by bubylou on 2012-04-09
Yes that is the file i have been updating and i have been stopping it on my own.

Well i set the config back to its default setting and it now appears on vlc but still doesn't work completely and the log file seems to be spitting out some errors. Here is a chunk of it.

```

[pool-655-thread-1] DEBUG 2012-04-09 23:27:08.468 Unix process ID (convert): 3117
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:08.483 Stopping Unix process 1574: convert-620
[pool-655-thread-1] DEBUG 2012-04-09 23:27:08.484 Starting convert -size 320x180 "/srv/samba/share/Music/Usher/The MixTape/Folder.jpg" -auto-orient -thumbnail 160x90 -unsharp -0x.5 /tmp/ps3mediaserver-root/imagemagick_thumbs/Folder.jpg.jpg
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:08.489 Stopping Unix process 1579: convert-621
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:08.513 Stopping Unix process 1589: convert-622
[pool-655-thread-3] DEBUG 2012-04-09 23:27:08.520 Unix process ID (convert): 3126
[pool-655-thread-2] DEBUG 2012-04-09 23:27:08.520 Unix process ID (convert): 3122
[pool-655-thread-1] DEBUG 2012-04-09 23:27:08.532 Unix process ID (convert): 3130
[pool-659-thread-1] DEBUG 2012-04-09 23:27:08.571 Starting convert -size 320x180 "/srv/samba/share/Music/Utada Hikaru/Unknown Album/AlbumArtSmall.jpg" -auto-orient -thumbnail 160x90 -unsharp -0x.5 /tmp/ps3mediaserver-root/imagemagick_thumbs/AlbumArtSmall.jpg.jpg
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:08.572 Stopping Unix process 1593: convert-623
[pool-659-thread-2] DEBUG 2012-04-09 23:27:08.595 Starting convert -size 320x180 "/srv/samba/share/Music/Utada Hikaru/Unknown Album/Folder.jpg" -auto-orient -thumbnail 160x90 -unsharp -0x.5 /tmp/ps3mediaserver-root/imagemagick_thumbs/Folder.jpg.jpg
[pool-659-thread-1] DEBUG 2012-04-09 23:27:08.632 Unix process ID (convert): 3150
[pool-659-thread-2] DEBUG 2012-04-09 23:27:08.633 Unix process ID (convert): 3155
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:08.650 Stopping Unix process 1606: convert-624
[pool-661-thread-1] DEBUG 2012-04-09 23:27:08.656 Starting convert -size 320x180 "/srv/samba/share/Music/Yeah Yeah Yeahs/Fever To Tell/AlbumArtSmall.jpg" -auto-orient -thumbnail 160x90 -unsharp -0x.5 /tmp/ps3mediaserver-root/imagemagick_thumbs/AlbumArtSmall.jpg.jpg
[pool-661-thread-2] DEBUG 2012-04-09 23:27:08.657 Starting convert -size 320x180 "/srv/samba/share/Music/Yeah Yeah Yeahs/Fever To Tell/AlbumArt_{4DBCF4D5-0FA3-4FA2-A26D-B613BEFD9296}_Large.jpg" -auto-orient -thumbnail 160x90 -unsharp -0x.5 /tmp/ps3mediaserver-root/imagemagick_thumbs/AlbumArt_{4DBCF4D5-0FA3-4FA2-A26D-B613BEFD9296}_Large.jpg.jpg
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:08.668 Stopping Unix process 1610: convert-625
[pool-661-thread-3] DEBUG 2012-04-09 23:27:08.680 Starting convert -size 320x180 "/srv/samba/share/Music/Yeah Yeah Yeahs/Fever To Tell/AlbumArt_{4DBCF4D5-0FA3-4FA2-A26D-B613BEFD9296}_Small.jpg" -auto-orient -thumbnail 160x90 -unsharp -0x.5 /tmp/ps3mediaserver-root/imagemagick_thumbs/AlbumArt_{4DBCF4D5-0FA3-4FA2-A26D-B613BEFD9296}_Small.jpg.jpg
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:08.705 Stopping Unix process 1616: convert-626
[pool-661-thread-1] DEBUG 2012-04-09 23:27:08.720 Unix process ID (convert): 3170
[pool-661-thread-2] DEBUG 2012-04-09 23:27:08.721 Unix process ID (convert): 3172
[pool-661-thread-2] DEBUG 2012-04-09 23:27:08.727 Starting convert -size 320x180 "/srv/samba/share/Music/Yeah Yeah Yeahs/Fever To Tell/Folder.jpg" -auto-orient -thumbnail 160x90 -unsharp -0x.5 /tmp/ps3mediaserver-root/imagemagick_thumbs/Folder.jpg.jpg
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:08.746 Stopping Unix process 1625: convert-627
[pool-661-thread-3] DEBUG 2012-04-09 23:27:08.753 Unix process ID (convert): 3177
[pool-661-thread-2] DEBUG 2012-04-09 23:27:08.753 Unix process ID (convert): 3186
[pool-663-thread-3] DEBUG 2012-04-09 23:27:08.774 Starting convert -size 320x180 "/srv/samba/share/Music/Yellowcard/Ocean Avenue/AlbumArt_{36E5B864-821B-4E80-BA35-A95E2CDE7882}_Small.jpg" -auto-orient -thumbnail 160x90 -unsharp -0x.5 /tmp/ps3mediaserver-root/imagemagick_thumbs/AlbumArt_{36E5B864-821B-4E80-BA35-A95E2CDE7882}_Small.jpg.jpg
[pool-663-thread-2] DEBUG 2012-04-09 23:27:08.793 Starting convert -size 320x180 "/srv/samba/share/Music/Yellowcard/Ocean Avenue/AlbumArt_{36E5B864-821B-4E80-BA35-A95E2CDE7882}_Large.jpg" -auto-orient -thumbnail 160x90 -unsharp -0x.5 /tmp/ps3mediaserver-root/imagemagick_thumbs/AlbumArt_{36E5B864-821B-4E80-BA35-A95E2CDE7882}_Large.jpg.jpg
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:08.820 Stopping Unix process 1640: convert-628
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:08.835 Stopping Unix process 1643: convert-629
[pool-663-thread-1] DEBUG 2012-04-09 23:27:08.838 Starting convert -size 320x180 "/srv/samba/share/Music/Yellowcard/Ocean Avenue/AlbumArtSmall.jpg" -auto-orient -thumbnail 160x90 -unsharp -0x.5 /tmp/ps3mediaserver-root/imagemagick_thumbs/AlbumArtSmall.jpg.jpg
[pool-663-thread-3] DEBUG 2012-04-09 23:27:08.839 Unix process ID (convert): 3199
[pool-663-thread-2] DEBUG 2012-04-09 23:27:08.840 Unix process ID (convert): 3202
[pool-663-thread-3] DEBUG 2012-04-09 23:27:08.850 Starting convert -size 320x180 "/srv/samba/share/Music/Yellowcard/Ocean Avenue/Folder.jpg" -auto-orient -thumbnail 160x90 -unsharp -0x.5 /tmp/ps3mediaserver-root/imagemagick_thumbs/Folder.jpg.jpg
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:08.877 Stopping Unix process 1650: convert-630
[pool-663-thread-3] DEBUG 2012-04-09 23:27:08.894 Unix process ID (convert): 3216
[pool-663-thread-1] DEBUG 2012-04-09 23:27:08.895 Unix process ID (convert): 3214
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:08.900 Stopping Unix process 1657: convert-631
[pool-665-thread-1] DEBUG 2012-04-09 23:27:08.913 Retrieving http://api.flickr.com/services/feeds/photos_public.gne?id=29142919@N07&lang=en-en&format=rss_200
[pool-665-thread-2] DEBUG 2012-04-09 23:27:08.913 Retrieving http://picasaweb.google.fr/data/feed/base/user/nefuisalbum/albumid/5218433104757705489?alt=rss&kind=photo&hl=en_US
[pool-665-thread-3] DEBUG 2012-04-09 23:27:08.913 Retrieving http://picasaweb.google.fr/data/feed/base/user/cookiejarconfessionals/albumid/5229065014037788129?alt=rss&kind=photo&hl=en
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:08.943 Stopping Unix process 1671: convert-633
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:08.954 Stopping Unix process 1674: convert-632
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:08.966 Stopping Unix process 1677: convert-634
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:09.072 Stopping Unix process 1692: convert-635
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:09.126 Stopping Unix process 1703: convert-636
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:09.140 Stopping Unix process 1707: convert-637
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:09.165 Stopping Unix process 1715: convert-638
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:09.202 Stopping Unix process 1725: convert-639
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:09.256 Stopping Unix process 1736: convert-640
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:09.278 Stopping Unix process 1741: convert-641
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:09.278 Stopping Unix process 1744: convert-642
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:09.328 Stopping Unix process 1753: convert-643
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:09.375 Stopping Unix process 1770: convert-644
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:09.375 Stopping Unix process 1773: convert-645
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:09.407 Stopping Unix process 1777: convert-646
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:09.444 Stopping Unix process 1785: convert-647
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:09.524 Stopping Unix process 1810: convert-648
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:09.524 Stopping Unix process 1811: convert-649
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:09.618 Stopping Unix process 1827: convert-651
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:09.618 Stopping Unix process 1826: convert-650
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:09.696 Stopping Unix process 1843: convert-652
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:09.708 Stopping Unix process 1847: convert-653
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:09.777 Stopping Unix process 1868: convert-654
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:09.777 Stopping Unix process 1869: convert-655
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:09.815 Stopping Unix process 1875: convert-656
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:09.857 Stopping Unix process 1883: convert-657
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:09.986 Stopping Unix process 1917: convert-658
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:10.005 Stopping Unix process 1920: convert-659
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:10.065 Stopping Unix process 1938: convert-661
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:10.120 Stopping Unix process 1948: convert-662
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:10.122 Stopping Unix process 1956: convert-663
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:10.127 Stopping Unix process 1943: convert-660
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:10.206 Stopping Unix process 1974: convert-664
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:10.206 Stopping Unix process 1972: convert-665
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:10.207 Stopping Unix process 1976: convert-666
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:10.276 Stopping Unix process 1988: convert-667
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:10.322 Stopping Unix process 1999: convert-668
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:10.343 Stopping Unix process 2005: convert-669
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:10.357 Stopping Unix process 2011: convert-670
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:10.392 Stopping Unix process 2017: convert-671
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:10.460 Stopping Unix process 2039: convert-672
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:10.475 Stopping Unix process 2041: convert-673
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:10.494 Stopping Unix process 2045: convert-674
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:10.540 Stopping Unix process 2058: convert-675
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:10.599 Stopping Unix process 2073: convert-676
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:10.617 Stopping Unix process 2076: convert-677
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:10.642 Stopping Unix process 2081: convert-678
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:10.679 Stopping Unix process 2092: convert-679
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:10.789 Stopping Unix process 2115: convert-680
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:10.809 Stopping Unix process 2117: convert-681
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:10.834 Stopping Unix process 2122: convert-682
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:10.868 Stopping Unix process 2132: convert-683
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:10.912 Stopping Unix process 2149: convert-684
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:10.912 Stopping Unix process 2152: convert-685
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:10.923 Stopping Unix process 2154: convert-686
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:10.981 Stopping Unix process 2165: convert-687
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:11.051 Stopping Unix process 2182: convert-688
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:11.051 Stopping Unix process 2183: convert-689
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:11.082 Stopping Unix process 2186: convert-690
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:11.130 Stopping Unix process 2197: convert-691
[pool-669-thread-1] DEBUG 2012-04-09 23:27:11.191 Retrieving http://picasaweb.google.com/data/feed/base/user/FenderStratRocker?alt=rss&kind=album&hl=en_US&access=public
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:11.197 Stopping Unix process 2214: convert-692
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:11.223 Stopping Unix process 2218: convert-693
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:11.247 Stopping Unix process 2225: convert-694
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:11.270 Stopping Unix process 2231: convert-695
[pool-670-thread-1] DEBUG 2012-04-09 23:27:11.297 Retrieving http://picasaweb.google.com/data/feed/base/user/Jadejpg/albumid/5356325196018397969?alt=rss&hl=en_US
[pool-670-thread-2] DEBUG 2012-04-09 23:27:11.297 Retrieving http://picasaweb.google.com/data/feed/base/user/Jadejpg/albumid/5337203988569800801?alt=rss&hl=en_US
[pool-670-thread-3] DEBUG 2012-04-09 23:27:11.313 Retrieving http://picasaweb.google.com/data/feed/base/user/Jadejpg/albumid/5325068943081331905?alt=rss&hl=en_US
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:11.347 Stopping Unix process 2249: convert-696
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:11.347 Stopping Unix process 2251: convert-697
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:11.347 Stopping Unix process 2250: convert-698
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:11.430 Stopping Unix process 2267: convert-699
[pool-670-thread-2] DEBUG 2012-04-09 23:27:11.430 Retrieving http://picasaweb.google.com/data/feed/base/user/Jadejpg/albumid/5320339667911760193?alt=rss&hl=en_US
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:11.442 Stopping Unix process 2270: convert-700
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:11.455 Stopping Unix process 2277: convert-701
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:11.495 Stopping Unix process 2284: convert-702
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:11.506 Stopping Unix process 2289: convert-703
[pool-670-thread-3] DEBUG 2012-04-09 23:27:11.516 Retrieving http://picasaweb.google.com/data/feed/base/user/Jadejpg/albumid/5281335464269507457?alt=rss&hl=en_US
[pool-670-thread-2] DEBUG 2012-04-09 23:27:11.552 Retrieving http://picasaweb.google.com/data/feed/base/user/Jadejpg/albumid/5281336923761322017?alt=rss&hl=en_US
[pool-670-thread-1] DEBUG 2012-04-09 23:27:11.562 Retrieving http://picasaweb.google.com/data/feed/base/user/Jadejpg/albumid/5281337149886442177?alt=rss&hl=en_US
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:11.577 Stopping Unix process 2310: convert-704
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:11.577 Stopping Unix process 2313: convert-705
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:11.577 Stopping Unix process 2308: convert-706
[pool-670-thread-2] DEBUG 2012-04-09 23:27:11.658 Retrieving http://picasaweb.google.com/data/feed/base/user/Jadejpg/albumid/5256435183208646449?alt=rss&hl=en_US
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:11.659 Stopping Unix process 2326: convert-707
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:11.720 Stopping Unix process 2339: convert-708
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:11.721 Stopping Unix process 2340: convert-709
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:11.755 Stopping Unix process 2349: convert-710
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:11.792 Stopping Unix process 2354: convert-711
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:11.871 Stopping Unix process 2371: convert-712
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:11.879 Stopping Unix process 2375: convert-713
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:11.899 Stopping Unix process 2379: convert-714
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:11.947 Stopping Unix process 2390: convert-715
[pool-679-thread-1] DEBUG 2012-04-09 23:27:11.964 Retrieving http://podcasts.engadget.com/rss.xml
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:12.015 Stopping Unix process 2412: convert-716
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:12.015 Stopping Unix process 2415: convert-717
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:12.015 Stopping Unix process 2420: convert-718
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:12.091 Stopping Unix process 2428: convert-719
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:12.171 Stopping Unix process 2453: convert-720
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:12.171 Stopping Unix process 2454: convert-721
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:12.171 Stopping Unix process 2456: convert-722
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:12.260 Stopping Unix process 2471: convert-723
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:12.384 Stopping Unix process 2489: convert-724
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:12.395 Stopping Unix process 2491: convert-725
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:12.471 Stopping Unix process 2508: convert-726
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:12.498 Stopping Unix process 2514: convert-727
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:12.540 Stopping Unix process 2523: convert-728
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:12.565 Stopping Unix process 2528: convert-729
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:12.631 Stopping Unix process 2542: convert-730
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:12.642 Stopping Unix process 2545: convert-731
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:12.744 Stopping Unix process 2569: convert-732
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:12.770 Stopping Unix process 2575: convert-733
[pool-681-thread-1] DEBUG 2012-04-09 23:27:12.785 Retrieving http://feeds.feedburner.com/tedtalks_video
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:12.850 Stopping Unix process 2593: convert-734
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:12.865 Stopping Unix process 2597: convert-735
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:12.987 Stopping Unix process 2613: convert-736
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:13.007 Stopping Unix process 2618: convert-737
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:13.063 Stopping Unix process 2630: convert-738
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:13.063 Stopping Unix process 2632: convert-739
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:13.126 Stopping Unix process 2647: convert-740
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:13.127 Stopping Unix process 2648: convert-741
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:13.210 Stopping Unix process 2669: convert-742
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:13.224 Stopping Unix process 2671: convert-743
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:13.248 Stopping Unix process 2677: convert-744
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:13.280 Stopping Unix process 2685: convert-745
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:13.366 Stopping Unix process 2708: convert-746
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:13.380 Stopping Unix process 2710: convert-747
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:13.396 Stopping Unix process 2713: convert-748
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:13.451 Stopping Unix process 2728: convert-749
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:13.546 Stopping Unix process 2744: convert-750
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:13.568 Stopping Unix process 2747: convert-751
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:13.623 Stopping Unix process 2756: convert-752
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:13.677 Stopping Unix process 2764: convert-753
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:13.874 Stopping Unix process 2793: convert-754
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:13.899 Stopping Unix process 2796: convert-755
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:13.958 Stopping Unix process 2803: convert-756
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:14.004 Stopping Unix process 2814: convert-757
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:14.060 Stopping Unix process 2825: convert-758
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:14.080 Stopping Unix process 2827: convert-759
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:14.118 Stopping Unix process 2838: convert-760
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:14.133 Stopping Unix process 2841: convert-761
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:14.188 Stopping Unix process 2855: convert-762
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:14.211 Stopping Unix process 2860: convert-763
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:14.235 Stopping Unix process 2866: convert-764
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:14.278 Stopping Unix process 2877: convert-765
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:14.348 Stopping Unix process 2894: convert-766
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:14.349 Stopping Unix process 2897: convert-767
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:14.371 Stopping Unix process 2899: convert-768
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:14.434 Stopping Unix process 2912: convert-769
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:14.487 Stopping Unix process 2924: convert-770
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:14.507 Stopping Unix process 2928: convert-771
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:14.576 Stopping Unix process 2944: convert-772
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:14.591 Stopping Unix process 2949: convert-773
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:14.608 Stopping Unix process 2955: convert-774
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:14.644 Stopping Unix process 2965: convert-775
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:14.766 Stopping Unix process 2985: convert-776
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:14.787 Stopping Unix process 2989: convert-777
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:14.820 Stopping Unix process 2995: convert-778
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:14.832 Stopping Unix process 3003: convert-779
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:14.922 Stopping Unix process 3015: convert-780
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:14.943 Stopping Unix process 3019: convert-781
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:14.964 Stopping Unix process 3022: convert-782
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:15.002 Stopping Unix process 3029: convert-783
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:15.116 Stopping Unix process 3055: convert-784
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:15.117 Stopping Unix process 3051: convert-786
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:15.132 Stopping Unix process 3054: convert-785
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:15.194 Stopping Unix process 3068: convert-787
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:15.288 Stopping Unix process 3085: convert-788
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:15.292 Stopping Unix process 3091: convert-789
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:15.293 Stopping Unix process 3092: convert-790
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:15.355 Stopping Unix process 3106: convert-791
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:15.422 Stopping Unix process 3117: convert-792
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:15.437 Stopping Unix process 3122: convert-793
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:15.443 Stopping Unix process 3126: convert-794
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:15.484 Stopping Unix process 3130: convert-795
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:15.572 Stopping Unix process 3150: convert-796
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:15.596 Stopping Unix process 3155: convert-797
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:15.657 Stopping Unix process 3170: convert-799
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:15.657 Stopping Unix process 3172: convert-798
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:15.681 Stopping Unix process 3177: convert-800
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:15.727 Stopping Unix process 3186: convert-801
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:15.774 Stopping Unix process 3199: convert-802
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:15.794 Stopping Unix process 3202: convert-803
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:15.839 Stopping Unix process 3214: convert-804
[ImageMagick Thumbnail Failsafe] DEBUG 2012-04-09 23:27:15.851 Stopping Unix process 3216: convert-805
[UPNP-AliveMessageSender] DEBUG 2012-04-09 23:30:06.523 Sending ALIVE...
[UPNP-AliveMessageSender] DEBUG 2012-04-09 23:33:10.365 Sending ALIVE...

```

---

### Post by arrrghhh on 2012-04-09
> **bubylou said:**
> Yes that is the file i have been updating and i have been stopping it on my own.

Can you not kill the server and leave it up?  Can you post that file?

---

### Post by bubylou on 2012-04-10
Already done. Now i have new problem from the above log file. That was at the end of the debug file.

---

### Post by bubylou on 2012-04-10
Well all my videos work just fine now but my music doesn't work correctly. Seems to be something with the album images. I can navigate through vlc to artists and albums but albums cannot be opened to get to the songs. Same logs as in my second post.

---

### Post by arrrghhh on 2012-04-10
> **bubylou said:**
> Well all my videos work just fine now but my music doesn't work correctly. Seems to be something with the album images. I can navigate through vlc to artists and albums but albums cannot be opened to get to the songs. Same logs as in my second post.

Honestly this forum is not going to be your best bet for this particular piece of software.  I use PS3MediaServer, but can only help ya so much... past initial setup I haven't run into many issues, so haven't done much troubleshooting with this particular application.

Instead of hoping someone else on here knows more about this software than me, I would go ahead and first SEARCH the PS3MediaForums - they're quite good.  After you've exhausted their FAQ's & searched a bit (you've done your due diligence in other words) post up a thread.  They've helped me before, there's everyone from developers to users posting on those forums ;).

---

### Post by bubylou on 2012-04-10
Thanks for the help ill check out the forums for a solution.

---

