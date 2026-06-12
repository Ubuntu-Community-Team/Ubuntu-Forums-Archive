---
title: "Watching Online TV across Europe/World with VLC?"
date: 2012-04-23
forum: The Cafe
---

### Post by Sylslay on 2012-04-23
Can anyone post active links (stream like mms:// etc)
 to online TV with can be paly in VLC.
Reazon I post this topic is VLC use less power than Flash website.

I have nothing against Flash :-)

[HTML]#!/bin/bash
# Skrypt tv by Sylslay
# On GNU General Public License
cd ~
cd ..
clear

while true; do

    echo "Choose TV-online ?"
    echo ""
    echo "Stop watching press CTRL + C or CTRL +Q"
    echo ""
    echo "Available tv station:"
    select tv in Bloomberg SkyNews France24 HitTV CampusTV MassiveMag StopPlay
do
        case $tv in
	    "Bloomberg") adres="http://www.bloomberg.com/streams/video/LiveBTV200.asxx" ;;
            "SkyNews") adres="mms://live1.wm.skynews.servecast.net/skynews_wmlz_live300k";;
	    "France24") adres="mms://stream1.france24.yacast.net/f24_liveen?MSWMExt=.asf";;
	     "HitTV") adres="http://88.191.126.62:18002;stream.nsv" ;;
            "CampusTV") adres="mms://webtv-bb.de/CampusTV";;
	    "MassiveMag") adres="mms://stream01.massive-mag.tv/massivemag_mq";;
            "StopPlay") exec cd ~           
		;;
            esac
            break
break
    done
    vlc $adres ; cd ~
done[/HTML]

I found that taday:

Arirang

[HTML]mms://s3.arirang.co.kr/World_Live[/HTML]

CCTV News
[HTML]http://www.wcetv.com/asx/LIB/LIB100247_v5.asx[/HTML]

And I sean that in UK they play for test, all channels from local "cable", only for UK IP and for some time. Just for testing purpose. :-)

---

### Post by sanderj on 2012-04-23
FWIW:

My ISP Telfort (Netherlands) provides live TV, but 1) only to it's TV customers, 2) only on their home-LAN, 3) online in Silverlight-with-DRM-codes

See [http://telfort.itvonline.nl/](http://telfort.itvonline.nl/) It doesn't work for me, as the Silverlight-DRM-codecs are only available for Windows, not for Linux.

The Dutch public broadcaster NOS provides their "Journaal 24" in Silverlight, and ... Windows Media Player, which I can watch on my Ubuntu with Chrome and totem. See [http://nos.nl/nieuws/live/journaal24/wmv/](http://nos.nl/nieuws/live/journaal24/wmv/)
I don't know if you can watch it using VLC. When I use "ps -ef", it looks the URL is

mmsh://213.75.89.51/thema_journaal24-bb-public?/nos/journaal24-bb&md5=034686eee2e2c40abca57a1d9b1f33a9&t=4f95442e&MSWMExt=.asf

but that doesn't work with VLC...

---

### Post by mips on 2012-04-23
Try some of the links in this thread [http://ubuntuforums.org/showthread.php?t=1862685](http://ubuntuforums.org/showthread.php?t=1862685)

---

### Post by Sylslay on 2012-04-24
Tkanks for help and answeres.
I looking only  for links to VLC. I know that I can watch loads of channel on some pages.

Found this page  most usful for VLC

[HTML]http://beelinetv.com/  - copy link from Media tab - some works ok

http://sonic-lux.de/home/projekte/software/shoutcast_tv_lists/web/index.html[/HTML]

Reason.
Flash use about 80-90% CPU power, and can't do anything else except watching TV
 on VLC 30%. So plenty power left unleashed. Same as radios playing in terminal :-)

PS. I use realy old laptop with Ubuntu 10.04 and try usu the most of it.:guitar:

---

