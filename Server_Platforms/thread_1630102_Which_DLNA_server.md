---
title: "Which DLNA server?"
date: 2010-11-24
forum: Server Platforms
---

### Post by fkjensen on 2010-11-24
Hi guys,
 
I want to install a DLNA server on my ubuntu home server.
It will primarily be used for photo browsing on my PS3, but general media support would be nice. (I use Squeezebox server for music.)
What are my options, and what are the main difference between them?
 
Best regards,
Frank

---

### Post by arrrghhh on 2010-11-24
PS3MediaServer is hands down my favorite.  Unfortunately it's not in the repo's, but it's well worth the inital trouble to setup - because it "just works".

To make sure my post isn't biased, there's also uShare and Mediatomb.  I really liked Mediatomb, my biggest issue with it was I couldn't get it to transcode files to the PS3.  PS3MediaServer does it flawlessly.

---

### Post by fkjensen on 2010-11-25
It looks like it got a graphical interface. Can I use it on a server only installation?
 
Best regards,
Frank

---

### Post by cjav on 2010-11-26
I tried severals, and even when I do agree PS3MediaServer is the easiest to setup, I ended falling in love with MediaTomb, it have a more Linux feeling and specially good in a server environment.

The transcoding part was the only part I struggled a little setting up, but when I did it the results were wonderful!, I attached my config.xml copy it to /etc/mediatomb/ and you should good to go.

Regards,
Carlos

---

### Post by arrrghhh on 2010-11-26
> **fkjensen said:**
> It looks like it got a graphical interface. Can I use it on a server only installation?

Yes, I run PS3MediaServer completely headless.  There's a PMS.conf file you can configure manually, or you can run the GUI (forwarded over ssh, if you want...) and then just configure it once that way and have it run from a startup script... a gentleman over in the PS3MediaServer forums has quite a nice repo setup for it.  [Here's](http://ps3mediaserver.org/forum/viewtopic.php?f=3&t=5589&sid=bc9134a6383eac419b520377b43d3e6b) the thread.

---

### Post by annoyingrob on 2010-11-26
I've played with PS3 Media Server, and found it to work great. Another vote for it.

---

### Post by borischan on 2010-12-08
Maybe a silly question, but is PS3 media server only good for PS3?
I'm also trying to find a good (easy to set up) dlna server for my Hitachi TV, which claims to be dlna compatible. Had some success using Buffalo NAS, except file format issues.
With my Ubuntu machine I'm banging my head against the wall. If there is a good guide out there for the non computer wizards amongst us, please share:D

---

### Post by arrrghhh on 2010-12-09
> **borischan said:**
> Maybe a silly question, but is PS3 media server only good for PS3?
I'm also trying to find a good (easy to set up) dlna server for my Hitachi TV, which claims to be dlna compatible. Had some success using Buffalo NAS, except file format issues.
With my Ubuntu machine I'm banging my head against the wall. If there is a good guide out there for the non computer wizards amongst us, please share:D

PS3 Media Server will work with anything that's DLNA compliant - however, just because something says it's DLNA compliant, doesn't mean it's completely compliant.  In my experience, the PS3 is one of the best devices out there for DLNA compliance.  There's a few others, Popcorn Hour comes to mind, and I think the WD set-top box is very good as well.  Most TV's... not so good unfortunately.  Maybe the brand brand new ones, but my 2009 "works"... but not nearly as well as the PS3 does ;)

---

### Post by borischan on 2010-12-09
Thanks arrrghhh, nothing to lose by trying! I'll report back if I get any success

---

### Post by borischan on 2010-12-09
Quick update...
Got PS3 Media server installed on my machine, Ubuntu 10.04LTS server, with gnome. Haven't tried any settings yet apart from running it..
First a message saying I'm running a rendered other than PS3, 2 units are visible. Unknown (actually is a Buffalo Link Theater), second is WD TV, it's a Hitachi Plasma 42" DLNA (allegedly).

The trusty BLT connects and plays anything it is compatible with, always has, great machine.
The TV sees the PS3 server, but won't play video, incompatible format. However it will play MP3 audio, which it wouldn't using mediatomb, so a step in the right direction.

Any recommendations or advice on transcoding? 

Thanks

---

### Post by arrrghhh on 2010-12-10
Hrm, can I see a log from PMS?

I didn't really have to do much in the way of transcoding - if the PS3 supported it, the video would "just work".

However, there are a lot of video formats the PS3 (and I'm sure your TV) do not support.  For these, you'll need a fairly beefy server hardware-wise - but you can transcode on-the-fly - you can force it by choosing the "##Transcode##" folder.  It'll give you a directory listing of the same files, but with different transcoding options.  It all depends on what is supported... I really had to wrestle with transcoding, and I still have some issues but they are now rare.  The biggest issue I ran into was multithreaded transcoding - I upgraded from a dual-core proc to a quad-core and didn't see any improvement in 1080p transcoding, until I compiled mplayer-mt and ffmpeg-mt.  I should probably make a guide... I still feel like I can do better tho.  I should make the guide and see what people recommend for improvements :p

---

### Post by sjhupp on 2010-12-11
Does this work at all for xbox360 (read some posts that said yes)?  I'm a poor preb with no PS3 .. yet :(

I need something that can feed my 360 my media, and used ushare years ago (but looks dead now?), tried Mediatomb (but no 360 support) and no luck yet with fuppes (OMG, what config in which config file?!). Twonky might be next to try...
Can PS3 media server provide a resonable folder view also?
Thanks.

---

### Post by arrrghhh on 2010-12-11
> **sjhupp said:**
> Does this work at all for xbox360 (read some posts that said yes)?  I'm a poor preb with no PS3 .. yet :(

I need something that can feed my 360 my media, and used ushare years ago (but looks dead now?), tried Mediatomb (but no 360 support) and no luck yet with fuppes (OMG, what config in which config file?!). Twonky might be next to try...
Can PS3 media server provide a resonable folder view also?
Thanks.

Go to their [website](http://code.google.com/p/ps3mediaserver/) man!  They do say there's 'basic' support, but evidently the DLNA implementation on the 360 is awful... No surprise there really...

---

