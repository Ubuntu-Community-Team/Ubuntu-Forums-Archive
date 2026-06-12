---
title: "Trouble putting together video clips in OpenShot"
date: 2010-03-01
forum: Ubuntu Studio
---

### Post by beastrace91 on 2010-03-01
I have four different .m4v video files that I encoded from DVDs using h264 (used the program Handbrake to do so). I have imported them into an OpenShot project and cut up each of the films so I have just the select scenes I would like from each. The video plays 100% fine in the preview Window however when I export the video regardless of what settings I use some of the clips come out as just black with audio, others are a frozen frame with audio, and others work 100% fine. I'm running Ubuntu 9.10 64bit.

Any suggestions on what is wrong/what I can to do to resolve this issue? I was counting on using OpenShot for a project for work I need by Thursday... :(

~Jeff

---

### Post by madeinfamous on 2010-03-01
allo beastrace91,

hope this help, (sorry for the french in my capture)

[IMG]http://sites.google.com/site/nueusx/openshot-export.png[/IMG]

this is the only way I've been able to export my video.

what is important is "All Format & AVI(h.264)"

you can choose less frame/second and another quality setting

have a nice week :)

---

### Post by beastrace91 on 2010-03-01
Same result when I use those settings... However I am seeing this message in terminal which may be why I am getting it:

```
consumer_avformat.c: video codec libx264 unrecognised - ignoring

```

However I checked synaptic and the libx264-67 package and libx264-dev are installed... Suggestions?

~Jeff

---

### Post by beastrace91 on 2010-03-01
Update: So I also have a 32bit system running Mint 8 (which has every media codec under the sun installed on it) and when I move the OpenShot project and video files over to it I get the exact same results and error message in terminal (video codec libx264 unrecognised - ignoring). How can I make x264 encoding work on my systems? Are there certain packages I need to add beyond standard media packages?...

Regards,
~Jeff

---

### Post by madeinfamous on 2010-03-01
allo again beastrace91,

hum...

is it in the repo. by default in 9'10 ? i don't really remember,

so here's the ppa i use for it in any case :

[https://launchpad.net/~jonoomph/+archive/openshot-edge]("https://launchpad.net/~jonoomph/+archive/openshot-edge")

version i got is 1.0.0-1 and i'm also on 9'10amd64

hope this help, i'll see if i think of something else :)

---

### Post by beastrace91 on 2010-03-02
Thanks for trying to help but it appears I am simply up **** creek without a paddle :-/

[http://openshotusers.com/forum/viewtopic.php?f=11&t=238](http://openshotusers.com/forum/viewtopic.php?f=11&t=238)

~Jeff

---

