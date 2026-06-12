---
title: "Do you know the stream for the Live BBC or CNN news for VLC?"
date: 2011-10-17
forum: The Cafe
---

### Post by honeybear on 2011-10-17
Hi,

We would like to watch the news in the early morning. 

Unfortunately I cannot get the url / stream from the website. Do you know the stream for the Live BBC or CNN news ? 

The stream of Sky-tv News is very a basic of the news, too basic. BBC would be ideal.

**I would like to play it with VLC (ONLY). Thanks**

Anyone could help maybe? 

Thanks

---

### Post by gsmanners on 2011-10-17
You have something against Flash?

---

### Post by An Sanct on 2011-10-17
For Sky news open this network stream
mms://live1.wm.skynews.servecast.net/skynews_wmlz_live300k

For BBC, I don't know, it is locked on my location :( but if you visit the location, where you can look at it in the browser and pinpoint the download location of the stream, VLC should handle it.

---

### Post by honeybear on 2011-10-17
> **gsmanners said:**
> You have something against Flash?

- I have nothing against Flash. Flash is a very nice application/media format.

- Considering the streams for news, for X reasons, I would rather use the VLC applications. 

Regards

> **An Sanct said:**
> For Sky news open this network stream
mms://live1.wm.skynews.servecast.net/skynews_wmlz_live300k

For BBC, I don't know, it is locked on my location :( but if you visit the location, where you can look at it in the browser and pinpoint the download location of the stream, VLC should handle it.

Thank you ! Could you eventually give me the link to the url of the FLV ?

---

### Post by mips on 2011-10-17
Are you in the UK, I've tried opening a few BBC streams but none work, I suspect it's because I'm located outside of the UK.

Here is just one list I came across [http://wiki.bath.ac.uk/display/bucstech/Freewire+TV+and+Radio+using+VLC](http://wiki.bath.ac.uk/display/bucstech/Freewire+TV+and+Radio+using+VLC)

---

### Post by honeybear on 2011-10-17
> **mips said:**
> Are you in the UK, I've tried opening a few BBC streams but none work, I suspect it's because I'm located outside of the UK.

Here is just one list I came across [http://wiki.bath.ac.uk/display/bucstech/Freewire+TV+and+Radio+using+VLC](http://wiki.bath.ac.uk/display/bucstech/Freewire+TV+and+Radio+using+VLC)

Have thou tried this link [www.bbc.co.uk/bbcone/watchlive/](www.bbc.co.uk/bbcone/watchlive/) ?

I note that it ought to be potentially possible to watch it - please find here an alternative link [www.livestation.com/channels/10-bbc-world-news-english](www.livestation.com/channels/10-bbc-world-news-english) 
So this later would imply that some utilities for Linux could manage to play the video of the Live World BBC news. Ideally it would be of course VLC, since it remains One of the best players for Linux.

Sincerely

---

### Post by mips on 2011-10-17
> **honeybear said:**
> Have thou tried this link [www.bbc.co.uk/bbcone/watchlive/](www.bbc.co.uk/bbcone/watchlive/) ?

I note that it ought to be potentially possible to watch it - please find here an alternative link [www.livestation.com/channels/10-bbc-world-news-english](www.livestation.com/channels/10-bbc-world-news-english) 
So this later would imply that some utilities for Linux could manage to play the video of the Live World BBC news. Ideally it would be of course VLC, since it remains One of the best players for Linux.

Sincerely

The first link has restricted access. Second link works.

---

### Post by honeybear on 2011-10-17
> **mips said:**
> The first link has restricted access. Second link works.

Could you please grab the link for VLC?

However I note: 
"mplayer, ffplay, and vlc can't play flash on x86_64 F12 x86 64-bit."

However there are solutions for overriding and getting some things working: 
[http://www.webupd8.org/2010/03/2-ways-of-playing-youtube-videos.html](http://www.webupd8.org/2010/03/2-ways-of-playing-youtube-videos.html)

---

### Post by gsmanners on 2011-10-17
Cool. I should try that out myself. :D

---

### Post by mips on 2011-10-18
> **honeybear said:**
> Could you please grab the link for VLC?


No, but I found a this link which does not seem to be live though :(
mms://rmv8.bbc.net.uk/news/olmedia/n5ctrl/tvseq/od/bbc1/bb/wm/video/click_bb.wmv


[http://ezmyway.com/tv/](http://ezmyway.com/tv/)



.

---

### Post by honeybear on 2011-10-18
> **mips said:**
> No, but I found a this link which does not seem to be live though :(
mms://rmv8.bbc.net.uk/news/olmedia/n5ctrl/tvseq/od/bbc1/bb/wm/video/click_bb.wmv


[http://ezmyway.com/tv/](http://ezmyway.com/tv/)



.

your first link is weather... cool

Would you have the one for the LIVE BBC news please? 

thank you !!!!

---

### Post by dave01945 on 2011-10-18
you should look into [this](http://linuxcentre.net/getiplayer) you can download it from synaptic but there is documentation about it the site

---

### Post by honeybear on 2011-10-19
> **dave01945 said:**
> you should look into URL=http://linuxcentre.net/getiplayer]this[/URL] you can download it from synaptic but there is documentation about it the site

ok, I have now installed getiplayer 

```
get-iplayer - download/stream available BBC iPlayer TV and radio programmes

```

I do not understand. The results are still the same.

---

### Post by dave01945 on 2011-10-19
what command are you using you need to tell get iplayer to stream it to vlc 

```
get_iplayer --stream **123** --player"vlc -"
```

123 is the index of a program to update the index just run

```
get_iplayer
```

and to search for a specific program just type

```
get_iplayer *news*
```

that will return all results with news in them and find the index number you want you can also use 

```
get_iplayer --get **123**
```

that will save the selected program to your HDD, there is alot it can do it is worth reading the documentation

---

### Post by honeybear on 2011-10-19
I still need again to ask the admin to install this program at school. 

Then which command would you type to watch "LIVE BBC NEWS" in fullscreen? Is there available bash scripts for that by the way? (I found nothing with google) If you, could you please make one cool one for this general purpose of watching simply the news?

thank you !!!!!!!!

---

### Post by dave01945 on 2011-10-19
try this command see if it works my internet is not currently fast enough to stream

```
get_iplayer --stream 80001 --player="vlc"
```

80001 is the stream number for bbc news

---

### Post by mips on 2011-10-21
> **honeybear said:**
> 
Would you have the one for the LIVE BBC news please? 


Here you go- **rtsp://media4.lsops.net:80/bb/bbcnews_en_high.sdp**

---

### Post by honeybear on 2011-10-21
> **mips said:**
> Here you go- **rtsp://media4.lsops.net:80/bb/bbcnews_en_high.sdp**

I LOVE YOU !! :KS:KS:KS:KS :D 

it works

---

### Post by mips on 2011-10-21
There's also rtsp://media4.lsops.net:80/bb/bbcnews_en_medium.sdp which I suspect is a lower quality.

From those links I found this [http://www.thestreamdb.com/](http://www.thestreamdb.com/) which is pretty cool.

---

### Post by honeybear on 2011-10-22
> **mips said:**
> There's also rtsp://media4.lsops.net:80/bb/bbcnews_en_medium.sdp which I suspect is a lower quality.

From those links I found this [http://www.thestreamdb.com/](http://www.thestreamdb.com/) which is pretty cool.

thank you so much 

CNN international does not work :( 
 
vlc "rtmp://media2.lsops.net/live/"



and how do you play comedie central under LINUX?
rtmp://live0.seeon.tv/edge/1gb8fva4mwqr40j swfUrl=http://static.seeon.tv/jwplayer/player.swf pageUrl=http://www.seeon.tv/view/15762/Comedy_Central tcUrl=rtmp://live0.seeon.tv/edge

---

### Post by honeybear on 2011-10-22
```

 flvstreamer --rtmp rtmp://63.229.55.59/ --app fecnetwork -s http://www.earthcam.com/swf/cam_player_v2/ecnPlayer.swf -y tsoneHD1.flv -v true | mplayer -

```

---

### Post by mips on 2011-10-22
Have not played around with that yet, will have a look a bit later. Ideally they should incorporate rtmpdump into vlc so it can open this stuff natively.

Have a look at this mailing list [http://share.ihelps.net/mailman/listinfo/tvlinks_share.ihelps.net](http://share.ihelps.net/mailman/listinfo/tvlinks_share.ihelps.net) that's where i got the BBC stream from, maybe you can get a **rtsp** stream from there for CNN...

---

### Post by honeybear on 2011-10-22
> **mips said:**
> Have not played around with that yet, will have a look a bit later. Ideally they should incorporate rtmpdump into vlc so it can open this stuff natively.

Have a look at this mailing list [http://share.ihelps.net/mailman/listinfo/tvlinks_share.ihelps.net](http://share.ihelps.net/mailman/listinfo/tvlinks_share.ihelps.net) that's where i got the BBC stream from, maybe you can get a **rtsp** stream from there for CNN...

I have now CNN Live and BBC Live working over mplayer. Thanks. 

Example of RTMP for flvstreamer:
```
rtmp://live0.seeon.tv/edge/1gb8fva4mwqr40j swfUrl=http://static.seeon.tv/jwplayer/player.swf pageUrl=http://www.seeon.tv/view/15762/Comedy_Central tcUrl=rtmp://live0.seeon.tv/edge
```


I would like to create myself the RTMP 

How do you do that? 
[http://en.udirect.tv/streaming-rtbf1-live.php](http://en.udirect.tv/streaming-rtbf1-live.php)

Could you create the RTMP for this channel : [http://en.udirect.tv/streaming-rtbf1-live.php](http://en.udirect.tv/streaming-rtbf1-live.php) , please?

---

