---
title: "Would you be interested by a flash media player plugin for MPLAYER?"
date: 2010-01-24
forum: The Cafe
---

### Post by frenchn00b on 2010-01-24
Hello,

Lot of plugins / pathes are in development for mplayer. One particularly might be offering playing url showing flash media player broadcast or video. Would you have interest in it, and would this be reasonably useful for you to achieve this by the next year, 2011, for Ubuntu or the next Ubuntu distro release?

---

### Post by SuperSonic4 on 2010-01-24
I wouldn't mind flash support for mplayer. Any idea how long it will be before it gets into SVN?

---

### Post by Skripka on 2010-01-24
> **SuperSonic4 said:**
> I wouldn't mind flash support for mplayer. Any idea how long it will be before it gets into SVN?

Mplayer-plugin has pretty much ceased development, from what I've seen.  Arch pulled it from extra.  And their Sourceforge page is dead.

[http://www.mplayerhq.hu/homepage/](http://www.mplayerhq.hu/homepage/)

[http://mplayerplug-in.sourceforge.net/index.php](http://mplayerplug-in.sourceforge.net/index.php)
-last update 2008

---

### Post by frenchn00b on 2010-01-24
> **Skripka said:**
> Mplayer-plugin has pretty much ceased development, from what I've seen.  Arch pulled it from extra.  And their Sourceforge page is dead.

[http://www.mplayerhq.hu/homepage/](http://www.mplayerhq.hu/homepage/)

[http://mplayerplug-in.sourceforge.net/index.php](http://mplayerplug-in.sourceforge.net/index.php)
-last update 2008

the problem actually is that there is numerous issues and this is a particularly difficult plugin, or too ... difficult, too complex to be anytime coded. 

Just to simply retrieve the url / flash link of a firefox webpage showing of flash : good luck ! I would be easy if one could do right click on firefox, and get the swf/flv... link... but this is not the case, and will not be in the next years.. or up to now.




for windows:
> 
Getting HTTP/RTMP stream URLs from Adobe Flash player

Replay Media Catcher can find .FLV video and .MP3 audio stream URLs from Adobe Flash player and record them automatically.

FLV Recorder can find .FLV video stream URLs from Adobe Flash player and record them automatically.

You may also find RTMP and HTTP flash stream URLs with URL finders. Most of them can find HTTP stream URLs. But Project URL Snooper can find flash .FLV video stream URLs starting with both http:// and rtmp://. 


---

### Post by Xbehave on 2010-01-24
> **Skripka said:**
> Mplayer-plugin has pretty much ceased development, from what I've seen.  Arch pulled it from extra.  And their Sourceforge page is dead.

[http://www.mplayerhq.hu/homepage/](http://www.mplayerhq.hu/homepage/)

[http://mplayerplug-in.sourceforge.net/index.php](http://mplayerplug-in.sourceforge.net/index.php)
-last update 2008
The code still works though ( it doesn't handle flash videos but it seams to handle opening the flv file directly pretty well. ) and [http://kdekorte.googlepages.com/gecko-mediaplayer](http://kdekorte.googlepages.com/gecko-mediaplayer) is a working replacement for it, the only problem i can see is you would have to implement enough actionscript to actually open the flv and it would still beak a lot of functionality.

---

### Post by frenchn00b on 2010-01-24
> **Xbehave said:**
> The code still works though ( it doesn't handle flash videos but it seams to handle opening the flv file directly pretty well. ) and [http://kdekorte.googlepages.com/gecko-mediaplayer](http://kdekorte.googlepages.com/gecko-mediaplayer) is a working replacement for it, the only problem i can see is you would have to implement enough actionscript to actually open the flv and it would still beak a lot of functionality.

give for example a try, a tricky url one: 
 mplayer "http://wwitv.com/portal.htm?http://wwitv.com/tv_channels/b5005.htm" 
seems that it is pretty difficult to be handled ...

then you do : 

> sudo wireshark
then click onto  the first left icon, 
then click on eth1 or eth0
then > host IP:PORT to check it
then 
> mplayer host IP:PORT

---

### Post by Psumi on 2010-01-25
gstreamer should have a flash plugin too. :| if mplayer gets one that is.

---

### Post by laser_b on 2010-03-02
For those who are interested, there's an alternative to Url Snooper in Linux: [pyurlsnooper]("http://sourceforge.net/projects/pyurlsnooper/").

---

