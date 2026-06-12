---
title: "Video on iRiver H300 using Ubuntu"
date: 2005-06-07
forum: The Cafe
---

### Post by boobytrapped on 2005-06-07
(copied from my [website](http://www.binish.com/?p=2)).

I have been really enjoying my new 40GB [iRiver H340](http://www.iriveramerica.com/prod/hd/h300.aspx).  Am I glad that I did not buy an iPod. The player has a color screen, shows up as a vfat USB Harddrive on Ubuntu Linux without any problems, and with minor tweaking, it plays even plays movies.

First of all, one of the best resources for iRiver's is the [Misticriver website](http://www.misticriver.net). This fan run website features tips, tutorials, and forums on using the iRiver devices.

I upgraded my device to the latest Korean firmware (no, this does not mean that I have Korean Text on my iRiver, it still display whatever you chose in the language settings). The Korean firmware has support for playing video. However, beware, this would mean that you'd lose the ability to play DRM music files (rights managed files that you download from online stores like napster and itunes.)

iRiver can only play movies that are in a particular format. It has to be an AVI file encoded using xvid, running at 10 frames per second. Here's a script I have been using to convert the movies that I download via bittorrent:
```

mencoder $infile -o $outfile -oac mp3lame \
-lameopts mode=2:cbr:br=128 -ovc xvid \
-xvidencopts bitrate=475:max_bframes=0 \
-vf scale=220:176,expand=220:176,harddup,pp=lb \
-af resample=44100 -ofps 10 -srate 44100

```

Ofcourse you need to install mplayer ```
sudo apt-get install mplayer-386
``` for this to work.  Actually mplayer is available for windows too.

My azureus bittorrent client has RSSFeed plugin. It automatically downloads The Daily Show for me (daily) and Doctor Who (weekly). I transcode them to the iRiver friendly format and then copy over to my iRiver. On my rather long commute to work, I enjoy Jon Stewart and crew's excellent show.

---

### Post by perfeng702 on 2009-03-29
thanks for this. I just used it.

---

