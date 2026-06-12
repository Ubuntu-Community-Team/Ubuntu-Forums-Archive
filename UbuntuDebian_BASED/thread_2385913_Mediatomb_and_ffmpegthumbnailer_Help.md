---
title: "Mediatomb and ffmpegthumbnailer Help"
date: 2018-02-26
forum: Ubuntu/Debian BASED
---

### Post by hazardsneon on 2018-02-26
I am running a Ubuntu based version of armbian for an Orangepipc.  I'm using it as a file and media server.

I have Mediatomb installed an running with ffmpegthumbnailer so that I see thumbnails when browsing the content on my PS3.

However, right now, it just searches a little while into the video and grabs a screen shot.  I have cover art in the metadata for pretty much every one of the videos on the server and I would prefer that it grabbed those instead.

Is there a way to make it use the metadata image rather than the screen grab?

I found a webpage "mankier" that has a man page for ffmpegthumbnailer and it says to use -m to do this but on the latest github readme it isn't listed.  Even if it is an option I don't know how I would implement it because I think that Mediatomb is calling it.

---

