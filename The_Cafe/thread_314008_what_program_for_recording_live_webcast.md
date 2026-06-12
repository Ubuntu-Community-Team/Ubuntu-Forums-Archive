---
title: "what program for recording live webcast?"
date: 2006-12-06
forum: The Cafe
---

### Post by jimrz on 2006-12-06
Looking for suggestions on what program would be best to use to record a rather long (> 5 hours) live webcast. I am running Ubuntu Edgy and would prefer something available from the repositories (or at least a .deb) and that is known to be able to handle this kind of job running unattended.

---

### Post by Roger Mudd on 2006-12-06
[Streamripper]("http://streamripper.sourceforge.net/index.php")

Here's the [FAQ]("http://streamripper.sourceforge.net/faq.php") which should answer some of your questions.

One thing to note is that it will not record Windows Media or RealPlayer streams.

---

### Post by jimrz on 2006-12-06
> **Roger Mudd said:**
> [Streamripper]("http://streamripper.sourceforge.net/index.php")

Here's the [FAQ]("http://streamripper.sourceforge.net/faq.php") which should answer some of your questions.

One thing to note is that it will not record Windows Media or RealPlayer streams.
Thanks Roger...will check it out

---

### Post by patrick295767 on 2006-12-06
> **jimrz said:**
> Looking for suggestions on what program would be best to use to record a rather long (> 5 hours) live webcast. I am running Ubuntu Edgy and would prefer something available from the repositories (or at least a .deb) and that is known to be able to handle this kind of job running unattended.

it depend if it is audio (streamripper) or video ?? 
plz give an example of stream eg.

> #! /usr/bin/perl
###########################################################################
# This is an example script that sends external metadata to streamripper.
# It implements an external program that:
#   1) Fetches a web page
#   2) Searches the web page for the artist and title information
#   3) Sends the information to streamripper on stdout
# To use this script:
#   streamripper URL -E "perl this_script META_URL"
###########################################################################
use LWP::Simple;
$url = $ARGV[0];

while (1) {
    # Fetch xml file at location $url
    my $content = get $url;

    # Get the artist and title
    if ($content =~ m/title="(.*)" artist="(.*)"/) {
        $title = "TITLE=$1\n";
        $artist = "ARTIST=$2\n";
        $end_of_record = ".\n";
        $meta_data = $title . $artist . $end_of_record;
        # Send to streamripper
        syswrite (STDOUT, $meta_data, length($meta_data));
    }
    sleep (10);
}

---

### Post by Roger Mudd on 2006-12-06
No problem. I think [MPlayer ]("http://www.mplayerhq.hu/design7/news.html")can also do this. Don't know how, but you might look into this option as well.

---

### Post by patrick295767 on 2006-12-06
> **Roger Mudd said:**
> No problem. I think [MPlayer ]("http://www.mplayerhq.hu/design7/news.html")can also do this. Don't know how, but you might look into this option as well.

that s indeed very true, ... and I guess the best option.

Btw, has someone a script ready to share via using mplayer ?  :KS :KS 
(to save us a bit of code to write and time)

if you wanna record your /dev/video from tv card:
streamer is the man

---

### Post by jimrz on 2006-12-06
> **patrick295767 said:**
> it depend if it is audio (streamripper) or video ?? 
plz give an example of stream eg.

will be a live video feed of a satalite launch...have been requested to record for a friend who will be working on site and thus unable to record...not sure, though have requested this info, what format will be used and the NASA site for the broadcast does not say (afraid will likely turn out to be either WMA or Real, hope not)

---

### Post by patrick295767 on 2006-12-06
> **jimrz said:**
> will be a live video feed of a satalite launch...have been requested to record for a friend who will be working on site and thus unable to record...not sure, though have requested this info, what format will be used and the NASA site for the broadcast does not say (afraid will likely turn out to be either WMA or Real, hope not)

mplayer is the very best in your case, i would bet


try to look the howto in man:    man mplayer
I cannot look now... 
Sleeping now for me

If someone has the mplayer code to make it,  please post & share !!

---

### Post by Roger Mudd on 2006-12-07
I did a little poking around after learning that you wanted to record a video stream. I suggest giving [VLC]("http://www.videolan.org/vlc/") a shot. [Here]("http://www.oreilly.com/pub/h/3769") is a link to some basic directions. I think they're directed towards the PC/Mac crowd. But they might just work on linux.

---

### Post by jimrz on 2006-12-07
thanks guys 

Patrick - will check out both Mplayer man + VLC

Roger  -  will also try VLC. this box is dual boot with xp, though it is rarely used I do still on occasion have to use a couple of win only thingies for work stuff,  and already have VLC on the win side if needed to make the instructions on your link work

will post back later with results

---

### Post by patrick295767 on 2006-12-09
```
A few mplayer tips i have found useful

* amplify volume in low volume media
mplayer video-name -softvol -softvol-max 500
- this will start with a low volume, u need to increase to volume using the volume keys
- instead of 10000 use the minimum value(10-10000) that works for you


* save a stream (eg rtsp://) to a file
mencoder stream-url -o output.avi -oac copy -ovc copy
- the stream url is written inside the file provided, eg inside .ram


* clip a video
mencoder input-video -o output-video -ss start-time -endpos end-time
- start-time/end-time can be seconds or hr:min:sec


* merge videos
cat videos list seperated by spaces | mencoder -oac copy -ovc copy -o output.avi -


* use 2 subtitle files with single movie file or 1 subtitle file with 2 movie files
bind a key for sifting the subtitles by cd1 duration ( in seconds ), and use this key once

```
from [http://blog.smr.co.in/cgi-bin/index.cgi/blogs/linux/1145307089.html](http://blog.smr.co.in/cgi-bin/index.cgi/blogs/linux/1145307089.html)

---

### Post by jimrz on 2006-12-10
> **Roger Mudd said:**
> I did a little poking around after learning that you wanted to record a video stream. I suggest giving [VLC]("http://www.videolan.org/vlc/") a shot. [Here]("http://www.oreilly.com/pub/h/3769") is a link to some basic directions. I think they're directed towards the PC/Mac crowd. But they might just work on linux.

THANKS ROGER !

this one appeared to be the simplest so I tried it first and it works like a charm using VLC on Edgy.

---

### Post by ubunter1 on 2007-02-10
what if i just want to watch a stream?,since i cant install the sopcast can i use the address to  put it in vlc or other to watch it?,i tried with the sopcast address and i wont work- sop://202.184.158.190:3912/865.thanks.

---

