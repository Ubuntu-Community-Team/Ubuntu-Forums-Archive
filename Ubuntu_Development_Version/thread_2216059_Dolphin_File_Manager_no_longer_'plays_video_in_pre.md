---
title: "Dolphin File Manager no longer 'plays video in preview"
date: 2014-04-09
forum: Ubuntu Development Version
---

### Post by Hazzabin on 2014-04-09
I've tried macmans ppa as per "http://www.webupd8.org/2014/03/get-firefox-and-phonon-gstreamer-to.html"

it does not fix Dolphin's problem, had hoped it might do

So does anyone know what/which packages could be needed that may fix this, and Kubuntu Dolphin doesn't work either....same issue

I can see the 'image' of the video but it doesn't play

---

### Post by mc4man on 2014-04-09
Well it would have nothing to do with the gstreamer0.10-ffmpeg plugin..

I don't use Kubuntu or Dolphin so to clarify - is the vid supposed to actually play in the preview  or display the thumb & play the audio?
(A quick test here with Dolphin produces a preview of a thumbnail image that plays the audio when clicking on the arrow but Not with the default phonon-backend-gstreamer, only with the vlc backend

---

### Post by 23dornot23d on 2014-04-09
Think its a separate thumbnailer program as dolphin does not normally show previews of videos on my own system
and I use kde 

Could be this [http://kde-apps.org/content/show.php/kffmpegthumbnailer?content=117562](http://kde-apps.org/content/show.php/kffmpegthumbnailer?content=117562)

> 
[h=3]kffmpegthumbnailer is a video thumbnailer for  kde based on ffmpegthumbnailer. The thumbnailer uses ffmpeg to decode  frames from the video files, so supported videoformats depend on the  configuration flags of ffmpeg.

This thumbnailer was designed to be as fast and lightweight as possible.[/h]


---

### Post by Hazzabin on 2014-04-09
Thanks guys for your replies and ideas

Dolphin has always played the video in preview once the 'arrow' is clicked,(least in my systems) I've had it since Ubuntu 10.04

And across pretty much all Ubuntu/Linux OS'es, tho I do know it tends to work better under KDE formats, I'm sorry I don't care much KDE's but LOVE my Dolphin!!!!

It actually was working really well and 'macman' it did after your thingie, but another update screwed it all again

---

### Post by 23dornot23d on 2014-04-09
Nothing showing in mine and I did add the [B]kffmpegthumbnailer also added digikam as that shows the 
thumbnails too ........

[IMG]http://i.minus.com/i4wp0exNmWJb0.png[/IMG]

The Files manager shows thumbnails too ........ but when clicking them a error pops up as the default
player is not working .........
[/B]

---

### Post by Hazzabin on 2014-04-09
ok mate, so I can put my image up here what do I have to do, tried a couple of times no success

ok I found it, now to find my image and post what I get  brb I hope

---

### Post by mc4man on 2014-04-09
The best I can get here (ubuntu, opening Video folder in dolphin) is thumbnails that play the audio, see screen, noting this is with the vlc backend

If the 0.10-ffmpeg plugin *did* work for a bit then likely you were using phonon & the older gstreamer backend that used gst-0.10. Now it uses gst-1.0 (and seems quite broken.

---

### Post by Hazzabin on 2014-04-09
this is what I get 1st one
[IMG][[IMG]http://img.photobucket.com/albums/v703/Hazzabeen47/Screenshot1.png[/IMG]]("http://smg.photobucket.com/user/Hazzabeen47/media/Screenshot1.png.html")[/IMG]

after clicking the arrow this happens and still doesn't play

[IMG][[IMG]http://img.photobucket.com/albums/v703/Hazzabeen47/Screenshot2.png[/IMG]]("http://smg.photobucket.com/user/Hazzabeen47/media/Screenshot2.png.html")[/IMG]

---

### Post by 23dornot23d on 2014-04-09
Mine is working now ........ had to tick information to get the right pane up
but not sure what I have got now that you have not

I added this to get miro working earlier too gstreamer0.10-ffmpeg

Last thing I loaded was the gst-0.10 dev files after seeing mc4mans post and as I say the preview panel
for the video only came up after adding the information ...... tick marker.

I did add the latest version of digikam earlier too and that brings a whole host of other things in .... but I 
know from the past it shows videos and thumbnails - so it seemed reasonable to assume it would 
bring in any other packages I might need .........

Could try it out anyway nothing to lose other than a bit of space on the hard drive ...... glad I got involved 
though as I did not realize how that dolphin video preview worked.

---

### Post by SeijiSensei on 2014-04-09
I have never seen previews for any of my H.264-encoded Matroska videos in Dolphin.  I looked around a bit for solutions to this, too, but nothing worked for me.  I hate mucking around with gstreamer; that's why I use smplayer and other programs related to mplayer and ffmpeg.  

As far as I can tell, most previews in Dolphin are broken and have been so for a long time.  In contrast, Dragon Player has no problem playing files that do not have previews in Dolphin.

The example in the posting above that works uses Flash.

---

### Post by 23dornot23d on 2014-04-09
I have it working and it plays ok ......  the video and sound are fine in the preview by the way.

____________________________________

When recording it  , using vokoscreen and playback in Linux is ok in the recording

 - its just after loading it up to You tube that it plays up with the sound stutter .......

The video is here that I just did ........ [http://youtu.be/8fwqAtW0nUc](http://youtu.be/8fwqAtW0nUc)

---

### Post by Hazzabin on 2014-04-10
> **SeijiSensei said:**
> I have never seen previews for any of my H.264-encoded Matroska videos in Dolphin.  I looked around a bit for solutions to this, too, but nothing worked for me.  I hate mucking around with gstreamer; that's why I use smplayer and other programs related to mplayer and ffmpeg.  

As far as I can tell, most previews in Dolphin are broken and have been so for a long time.  In contrast, Dragon Player has no problem playing files that do not have previews in Dolphin.

The example in the posting above that works uses Flash.

"The example in the posting above that works uses Flash"    with this are you referring to my post 

all my video players play the videos without any problems, it's just me that I like to be able to check within dolphin preview that it's after download is ok

any thanks to you all for some ideas

hey mate that video is great nice one, grrrr now to figure out my mess

---

### Post by Hazzabin on 2014-04-10
Attention Mr [COLOR=#000000]23dornot23d

I had nothing to loose, so I tried the 'digicam' install.....and wot-ya-no's it bleedin well worked.

whatever was within that it fixed the issue, now to try it on the other Ubuntu 14.04 installs

Many thanks mate

P.S.  Nope didn't work on 2 other Ubuntu 14.04 installs, 1 was Ubuntu Gnome, other Ubuntu 'Unity'   dammitt[/COLOR]

---

### Post by 23dornot23d on 2014-04-10
Just check these files are on the other machines too also mc4mans ppa from here I added.

[https://launchpad.net/~mc3man/+archive/trusty-media](https://launchpad.net/~mc3man/+archive/trusty-media)

I added this to get miro working earlier too gstreamer0.10-ffmpeg

Last thing I loaded was the gst-0.10 dev files after seeing mc4mans post and as I say the preview panel
for the video only came up after adding the information ...... tick marker.

Worth checking out - could be the combination of all the things I installed last night .

---

### Post by Hazzabin on 2014-04-10
Did a complete new install of Ubuntu 14.04 'Unity' 10th April iso, ended up with exactly same issue as per that second image I posted

even after doing all the adjustments as been suggested, still no go.

No matter, maybe at a later date a true fix will happen, anyways thanks for your suggestions......oh yeah are you using amd64 or x86, just wondering if that make a difference
all mine are amd64's

---

### Post by 23dornot23d on 2014-04-10
Mine is the 64 bit .......... but I hope a upgrade sorts it out for you .........

Latest upgrade I did was yesterday .

---

