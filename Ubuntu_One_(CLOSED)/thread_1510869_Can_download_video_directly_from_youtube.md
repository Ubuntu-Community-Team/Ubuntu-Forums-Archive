---
title: "Can download video directly from youtube?"
date: 2010-06-16
forum: Ubuntu One (CLOSED)
---

### Post by rudysuryanto on 2010-06-16
Dear all, can I download directly video from youtube and dailymotion into Ubuntu one? Thank's.

---

### Post by oracle2b on 2010-06-16
There are a number of ways to download video from youtube and dailymotion.

Some command-line apps are: [clive]("http://clive.sourceforge.net/") is a command line utility for extracting (or downloading) videos from Youtube and other video sharing Web sites. It was originally written to bypass the Adobe Flash requirement needed to view the hosted videos.
It should be in the repositorys.

I prefer using [youtube-dl]("http://bitbucket.org/rg3/youtube-dl/wiki/Home"). it's realy simple to use for example, 
> youtube-dl -t -b [http://www.youtube.com/watch?v=4BJDNw7o6so](http://www.youtube.com/watch?v=4BJDNw7o6so) downloads the best quality version of the video and saves the filename as the youtube video title.

to install it, open your terminal and type in
> wget [http://bitbucket.org/rg3/youtube-dl/raw/2010.06.06/youtube-dl](http://bitbucket.org/rg3/youtube-dl/raw/2010.06.06/youtube-dl) && sudo chmod +x youtube-dl && sudo mv youtube-dl /usr/local/bin

Some GUI(Graphical User Interface) apps are: [xVideoServiceThief]("http://xviservicethief.sourceforge.net/") or just use [Downloadhelper]("http://www.downloadhelper.net/") a firefox addon and you can download from hundreds of sites.

---

### Post by meoconvn38 on 2010-06-17
You can use firefox plugin :D like here [https://addons.mozilla.org/en-US/firefox/addon/13990](https://addons.mozilla.org/en-US/firefox/addon/13990)   < --
**         1-Click  YouTube Video Download :guitar:         **

---

### Post by jmore9 on 2010-06-17
I use video download helper which is the most used one.   It will download almost any flv site video.

Just click tools, add-ons , all add-ons, then search for video download helper.  Should have at least 1/2 million dls.

---

