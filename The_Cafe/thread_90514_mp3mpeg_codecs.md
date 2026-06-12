---
title: "mp3/mpeg codecs"
date: 2005-11-15
forum: The Cafe
---

### Post by missmoondog on 2005-11-15
more of a rant than a question per se, but man, there has to be an easier way to get audio and video working in ubuntu? took a couple days to get my 5 machines working correctly in 5.04. now i upgraded 1 machine to 5.10 and it was even more rediculous. i can easily see why so many people give up on linux. WAY to many hoops to have to jump through. now that the frustration from that is over (until i start trying to update my next box), it's time to rock!

---

### Post by aysiu on 2005-11-15
It's not Linux--it's Ubuntu. For more on why, read [this](http://wiki.ubuntu.com/RestrictedFormats).

In the meantime, there's also [Easy Ubuntu](http://www.ubuntuforums.org/showthread.php?t=84742) and [Automatix](http://www.ubuntuforums.org/showthread.php?t=80295).

Otherwise, Blag and Mepis have a whole bunch of proprietary codecs, as does Linspire.

---

### Post by bionnaki on 2005-11-16
installing multimedia codecs is real easy - should take no longer than 20 mins - depending how how quickly you can download the packages.

here's how:

> 1. Get(download) and install various codecs from repositories

    * sudo apt-get install gstreamer0.8-plugins
    * sudo apt-get install gstreamer0.8-lame
    * sudo apt-get install gstreamer0.8-ffmpeg
    * sudo apt-get install lame
    * sudo apt-get install sox
    * sudo apt-get install ffmpeg
    * sudo apt-get install mjpegtools
    * sudo apt-get install vorbis-tools
    * sudo apt-get install flac

2. then download and install w32 codec and libdvdcss2 (search forums for download location)

    * sudo dpkg -i w32codecs_20050412-0unofficialubuntu2_i386.deb
    * sudo dpkg -i libdvdcss2_1.2.8-1unofficialubuntu3_i386.deb

3. REGISTER codecs with the command

    * gst-register-0.8

4. Get and install xine (or gxine - what I prefer on gnome)
     
    * sudo apt-get install gxine


once you've down all of this in order...right-click on whatever media file you have and associate them with a media player. for video, I use gxine. for music I use beep-media-player. for firefox embedded media, follow these instructions: [http://www.ubuntuforums.org/showthread.php?t=60505&highlight=mplayer+plugins](http://www.ubuntuforums.org/showthread.php?t=60505&highlight=mplayer+plugins)

Also, install flash for firefox via synaptic. the package is called "flashplayer-mozilla"

piece of cake.

---

### Post by ruffneck on 2005-11-16
Awesome bionnaki! Thanks alot...works a charm.

---

### Post by missmoondog on 2005-11-16
this is exactly my point. how in the world would any new user ever figure all this stuff out? it's not that well documented on any site that i've searched, although i have figured it out on all 5 of my systems. this is also exactly why i still think linux is one stupid os!! :???:  one of the very first things anybody is going to look for is how to make their audio/video players work and that info is next to impossible to find all in one spot. until now anyway! 

thank  you, bionnaki



[QUOTE=bionnaki]installing multimedia codecs is real easy - should take no longer than 20 mins - depending how how quickly you can download the packages.

here's how:



once you've down all of this in order...right-click on whatever media file you have and associate them with a media player. for video, I use gxine. for music I use beep-media-player. for firefox embedded media, follow these instructions: [http://www.ubuntuforums.org/showthread.php?t=60505&highlight=mplayer+plugins](http://www.ubuntuforums.org/showthread.php?t=60505&highlight=mplayer+plugins)

Also, install flash for firefox via synaptic. the package is called "flashplayer-mozilla"

piece of cake.[/QUOTE]

---

### Post by poptones on 2005-11-16
When I used windows, I used windows 2000. I worked on video projects and that required avisynth, codecs, and to watch it in a decent manner required installing a player... I think I used bsplayer.

Anyway, the point is when I had to install windows recently to recover some data off some pgp encrypted cds it took hours just to get the crap installed that I need to run. About 6:30 this evening I shut the machine down and had to reinstall after wiping the boot sector on my main drive; in about an hour and a half I was booting back into the same desktop I was using when I shutdown. 

Oh yeah... and the partition I partially wiped? took about half a day but I've recovered nearly everything using nothing more than the tools in the default install. You'll pay a hundred bucks or more for a tool to allow you to recover data like that from a fubar'd windows partition.

You'll get it. In six months windows will seem like a prison to you.

---

### Post by allans on 2005-11-16
You could always use an open source codec like ogg, depends how many mp3s you have I guess.

Allan

---

### Post by poofyhairguy on 2005-11-16
[QUOTE=missmoondog]this is exactly my point. how in the world would any new user ever figure all this stuff out? [/QUOTE]

They don't have to:

[http://ubuntuforums.org/forumdisplay.php?f=77](http://ubuntuforums.org/forumdisplay.php?f=77)

---

### Post by aysiu on 2005-11-16
[QUOTE=poofyhairguy]They don't have to:

[http://ubuntuforums.org/forumdisplay.php?f=77](http://ubuntuforums.org/forumdisplay.php?f=77)[/QUOTE] Yeah, I linked to that earlier, Poofyhairyguy. Anyone who calls Linux a stupid OS isn't going to listen to anything to the contrary (even if Linux isn't an OS!)

---

### Post by bulldogzerofive on 2005-11-16
[QUOTE=missmoondog]this is exactly my point. how in the world would any new user ever figure all this stuff out? [/QUOTE]

I am a fairly new user and i did not find it difficult at all.  It demands that you realize that what you thought you knew about computing was really just knowledge of windows.  GNU/Linux is a different OS and demands a different approach.  Be willing to learn.

[QUOTE=missmoondog]it's not that well documented on any site that i've searched, although i have figured it out on all 5 of my systems.  [/QUOTE]

There are many, many threads on this and other forums that answer this question.  Just do a search for "howto multimedia codecs" and you will see what I mean.  Bear in mind that in many places following these instructions is illegal.  You cannot use software that you do not have the rights to.

[QUOTE=missmoondog]this is also exactly why i still think linux is one stupid os!! :???:  [/QUOTE]

I am sure "they" could make GNU/linux work just like windows, but i am sure in the process GNU/Linux would lose its advantages (freedom, stability, security, speed, etc).  If you do not like it you do not need to call it stupid (with all the people who donated so much time and effort to make this free system for you).  Please, either work to help improve it, accept it as is, or do not use it.  Name calling gets us nowhere.

[QUOTE=missmoondog]one of the very first things anybody is going to look for is how to make their audio/video players work and that info is next to impossible to find all in one spot. until now anyway! 
[/QUOTE]


I repeat my first point.


2.  Your frustration toward GNU/Linux is mis-directed.  I agree that it is stupid to have to track this stuff down.  However, the culprits are not the folks who develop linux.  The fact that these proprietary things work at all in GNU/Linux is in fact tribute to their skill.  The culprits are people who insist that you pay for their work (like MP3 developers) or refuse to allow redistribution of their "free of charge" stuff (like Sun with Java).  Complain to them.  If you want all the codecs, you have to pay for an operating system or media player that paid for the rights to them, or pirate them.  Ubuntu is Free and will not engage in illegal activity.  If, like the rest of us, you would like codecs to be open source (and therefore free of cost to you), start supporting open source initiatives, even if in the short term it makes things harder for you.

---

### Post by GeneralZod on 2005-11-16
[QUOTE=bulldogzerofive]Stuff[/QUOTE]

*Excellent* post :)

---

### Post by Kyral on 2005-11-16
You don't even have to track it down anymore. Its integrated into the Help System of GNOME.

Just click that little life-perserver and right there is the section entitled "5.10 Starter Guide"

Though I do wish they linked to Ubuntuforums in there

---

