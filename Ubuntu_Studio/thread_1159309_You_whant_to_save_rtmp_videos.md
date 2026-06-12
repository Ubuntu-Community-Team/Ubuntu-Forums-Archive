---
title: "You whant to save rtmp videos?"
date: 2009-05-14
forum: Ubuntu Studio
---

### Post by pixel :-) on 2009-05-14
Look what i found, a script in order to "save on disk" streamed videos with rtmp protocol. All the flash videos that you can't figure where it is cashed. It still very experimental, BBC doesn't work, but with some tweak the script should work. The script can take in only one stream, but in bbc they are always two because of the small intro video.

[http://www.zap.org.au/software/utils/scripts/extract-rtmp-flv](http://www.zap.org.au/software/utils/scripts/extract-rtmp-flv)
*************************************************************
actual use, provided instructions are wrong

sudo tcpdump -i eth0 -p -s 0 -w file.tcpdump -v tcp src port 1935

As an ordinary user, open the relevant video URL in your browser window and start playback

tcpdump -r file.tcpdump -s 0 -vvv -X \ > file.tcpdump-ascii

./extract-rtmp-flv file.tcpdump-ascii file.flv

---

### Post by Dooglus on 2010-11-30
I've just had success using rtmpdump from the repositories to dump rtmp streams to disk.

I found it wasn't able to parse the URL of the stream I was dumping, but breaking it up into separate --host, --app, and --playpath arguments fixed the problem.

---

