---
title: "Top 10 Tricks and Tips for the svn MPlayer"
date: 2009-05-09
forum: Tutorials
---

### Post by andrew.46 on 2009-05-09
This thread is closed.

The information is now held on the community wiki at [https://help.ubuntu.com/community/MPlayerTips](https://help.ubuntu.com/community/MPlayerTips)

Thank you for your thread and the work you have done in keeping it current and of use to the community.

A thread for discussion of the wiki can be found at [http://ubuntuforums.org/showthread.php?p=12102979#post12102979](http://ubuntuforums.org/showthread.php?p=12102979#post12102979)


Support threads regarding the wiki and it's content should be created in a suitable forum.

---

### Post by jpeddicord on 2009-05-11
Nice tips. Thank you for your contribution!

---

### Post by andrew.46 on 2009-05-13
Hi jacobmp92,

> **jacobmp92 said:**
> Nice tips. Thank you for your contribution!

Thanks for your kind words,

Andrew

---

### Post by fillintheblanks on 2009-05-13
hey, my DVD menus work  :)

---

### Post by Nepherte on 2009-05-14
Perhaps it would be more useful to save the dvdnav options in the dvdnav protocol profile itself. That way you don't need to specify which profile you want to use. Like this:
```
[protocol.dvdnav]
profile-desc="Profile for reading DVD menus"
mouse-movements=yes
nocache=yes
```

Usage:
```
mplayer dvdnav://
```

Anyways, I find the usage of profiles in MPlayer a highly underestimated feature. Great that you mention it!

---

### Post by andrew.46 on 2009-05-14
Hi fillintheblanks,

> **fillintheblanks said:**
> hey, my DVD menus work  :)

Supposedly the dvd menus are still a little hit and miss but I have had no trouble. I did not mention in this guide that of course there are also the 'keypad' keys:

```

keypad 8 Select button up.
keypad 2 Select button down.
keypad 4 Select button left.
keypad 6 Select button right.
keypad 5 Return to main menu.
keypad 7 Return to nearest menu (the order of preference  
         is:  chapter->title->root).
keypad ENTER Confirm choice.

```

which I don't use myself as I use a laptop with a few key sets missing :-).

Andrew

---

### Post by andrew.46 on 2009-05-14
Hi Nepherte,

> **Nepherte said:**
> Perhaps it would be more useful to save the dvdnav options in the dvdnav protocol profile itself. That way you don't need to specify which profile you want to use. [...]
Anyways, I find the usage of profiles in MPlayer a highly underestimated feature. Great that you mention it!

I was a little torn with this as my original goal with this one was to highlight the use of *profiles* rather than delve into dvd menus as such. However you have a valid point and I shall add this is an alternative. Thanks for drawing my attention to this!

Andrew

---

### Post by fillintheblanks on 2009-05-14
yeah I noticed sometimes menus dont terminate right away and mouse over graphics graphics dont display properly, theres like a white rectangle..

this is still better than nothing though :popcorn:

---

### Post by andrew.46 on 2009-05-14
Hi fillinthe blanks,

> **fillintheblanks said:**
> yeah I noticed sometimes menus dont terminate right away and mouse over graphics graphics dont display properly, theres like a white rectangle..

this is still better than nothing though :popcorn:

Well the joy of svn is that work is continuing in this area and hopefully the dvd menus will become more sophisticated in time. I usually update every week and despite some breakages there is mostly a pleasant increase in functionality in *some* area each time.

All the best,

Andrew

---

### Post by andrew.46 on 2009-06-12
Hi jamiyoel,

> **jamiyoel said:**
> Good Tutorial. Thanks

My pleasure :-). This guide is proving to be something of a 'sleeper' but I hope one day it will take off!

All the best,

Andrew

---

### Post by mocha on 2009-06-14
Andrew,

I know you don't have an nvidia 8xxx/9xxx card as you've mentioned numerous times, but "Tip 11" would definitely be VDPAU.  It's revolutionary for desktop linux, IMHO...  Splurge the $50 to get something like a 9500GT with 512MB or greater RAM, you'll really thank yourself if you watch a lot of videos on your desktop.

---

### Post by andrew.46 on 2009-06-14
Hi mocha,

Good to hear rom you again!

> **mocha said:**
> I know you don't have an nvidia 8xxx/9xxx card as you've mentioned numerous times, but "Tip 11" would definitely be VDPAU.  It's revolutionary for desktop linux, IMHO...  Splurge the $50 to get something like a 9500GT with 512MB or greater RAM, you'll really thank yourself if you watch a lot of videos on your desktop.

Have a mentioned my modest hardware that many times :-). A laptop at that which will not actually take an upgrade video card... But your point is well taken and for my *next* computer I would be foolish not to get one with a decent card and definitely vdpau would be in there.

To move a little OT: I mentioned on another guide that in fact I have finally made a decision to retire from the svn *installation* guides for MPlayer that I have undertaken for several years now. In part because I have slipped behind the times with vdpau, FFmpeg-mt, coreavc and the like but mostly because Karmic is shipping with a decent MPlayer package. And of course rvm has a PPA with a decent copy as well :-).

All the best,

Andrew

---

### Post by learningcurb on 2009-06-20
Hi, I found this page while browsing [http://ubuntuforums.org/showthread.php?t=834672](http://ubuntuforums.org/showthread.php?t=834672).  The command line trick "unrar p -inul myarchive.rar | mplayer -cache 2048 -" of using mplayer to play files inside a rar archive is very cool!

---

### Post by andrew.46 on 2009-06-20
Hi learningcurb,

> **learningcurb said:**
> Hi, I found this page while browsing [http://ubuntuforums.org/showthread.php?t=834672](http://ubuntuforums.org/showthread.php?t=834672).  The command line trick "unrar p -inul myarchive.rar | mplayer -cache 2048 -" of using mplayer to play files inside a rar archive is very cool!

Looks like the gratuitous plug for my own guide has worked well :-). Mind you I still think the scaletempo filter is the coolest thing of all of the tips.

Andrew

---

### Post by Jose Catre-Vandis on 2009-11-23
Hi Andrew46

Really loving the mplayer guides. You mention in your top tips playing of playlists. Anyway that you know of to get mplayer to crossfade or can it only cope with linear playback?

---

### Post by andrew.46 on 2009-11-24
Hi Jose,

> **Jose Catre-Vandis said:**
> You mention in your top tips playing of playlists. Anyway that you know of to get mplayer to crossfade or can it only cope with linear playback?

Unfortunately I believe this cannot be done yet. I note however that in the MPlayer source tree under DOCS/tech/wishlist:


> Filters

[...]

 * crossfade filter (audio and video)

So perhaps one day this will come? Mind you at the top of the wishlist I also see the following:

> If wishes were fishes, we'd all cast nets ...

All the best,

Andrew

---

### Post by Jose Catre-Vandis on 2009-11-24
> **andrew.46 said:**
> Hi Jose,



Unfortunately I believe this cannot be done yet. I note however that in the MPlayer source tree under DOCS/tech/wishlist:




So perhaps one day this will come? Mind you at the top of the wishlist I also see the following:



All the best,

Andrew

Thanks Andrew :)

---

### Post by jellyfisharepretty on 2009-12-08
Definitely my favourite "trick" with svn MPlayer is enabling joystick support.  I used your wonderful howto to compile MPlayer with joystick support by adding only --enable-joystick to the configure options.

Bought a cheap (< 10$) wireless gamepad.  Makes a great RF remote control for watching movies !! Only had to write a few lines in MPlayer's input.conf and it was done.

Anyway, thanks Andrew for writing all this good stuff about MPlayer, it makes my favourite video player even better.

---

### Post by andrew.46 on 2009-12-09
Hi jellyfish,

> **jellyfisharepretty said:**
> Anyway, thanks Andrew for writing all this good stuff about MPlayer, it makes my favourite video player even better.

Thanks for your kind words!

Andrew

---

### Post by JBAlaska on 2009-12-09
You made one error in your guide. The greatest movie of all time is not The Matrix...It's [Vanishing Point 1971](http://www.imdb.com/title/tt0067927/)

J/K

Great Guide!

---

### Post by andrew.46 on 2009-12-09
Hi JB,

> **JBAlaska said:**
> You made one error in your guide. The greatest movie of all time is not The Matrix...It's [Vanishing Point 1971](http://www.imdb.com/title/tt0067927/)

Which reminds me a little of the xkbd discussion of the *other* Matrix movies: [http://xkcd.com/566/](http://xkcd.com/566/). And I am afraid that you are completely wrong, the Matrix is still the greatest :).

Andrew

---

### Post by andrew.46 on 2010-05-17
Hi,

I have added some brief details to this guide for turning video ouput into a Matrix simulation with *-vo matrixview*. Now if I could only decide on the red or the blue pill.....

Andrew

---

### Post by m45t3r on 2010-05-17
Nice tips, some I already knew (like the -ao matrixview) but some others I didn't and they are simple awesome.

After compiling a MPlayer from Uoti's git this player is now my favorite:).

---

### Post by andrew.46 on 2010-05-18
Hi m45t3r,

It is nice to burrow around in the man pages and dig out a few gems or this great media player :).

Andrew

---

### Post by m45t3r on 2010-05-18
This is one of my favorites tricks:
** Playing videos in TTY (yep, without X.org :O)**

[LIST=1]
[*]Switch to TTY (Ctrl+Alt+F1);
[*]Now you can use either of tip 6 options (except the matrixview, because this one need X.org):```
mplayer -vo aa -monitorpixelaspect 0.5 myfile.mp4
``````
mplayer -vo caca myfile.mp4
```
[*]Ok, funny. But I want to watch THE video and not lots of letter dacing in my screen. So I can try these:```
#mplayer -vo fbdev myfile.mp4 
``````
#mplayer -vo fbdev2 myfile.mp4 
``````
#mplayer -vo directfb myfile.mp4 
```
[*]And impress your friends playing TRUE videos in terminal:popcorn:.
[/LIST]
Note: you need to use these options as superuser (using "sudo mplayer" or simply type "sudo su") because you need write access to /dev/yourgpu (simply talking, your GPU RAM).
Note 2: note that the framebuffer not always work. In my netbook with Intel GMA945 using X.org's drivers it's completely fine, even with subtitles. But on my desktop with NVIDIA's proprietary driver it didn't work and even crash my system (Update: got a working framebuffer with NVIDIA's proprietary drivers following these instructions: [http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/](http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/)).
Note 3: you can change the size of the video using "-zoom -x 1024 -y 576" options (where "1024" and "576" are the desired resolution).
[B]
Warning: because you are using direct access to your hardware this trick CAN CRASH YOUR SYSTEM. Just a reboot and everything will work again, but I recommend that you save all your job before playing with this.[/B]

---

### Post by xzero1 on 2010-05-28
Is there an easy way to scale to a virtual size so that the monitor acts as a window centered on the virtual video? This can be done playing with the crop values, but it is hard to get the values to retain the proper aspect ratio. It can also be done with zooming with compiz. Can it be done easily with mplayer alone?

---

### Post by andrew.46 on 2010-05-28
Hi xzero1,

I will admit I am not completely sure what you mean I'm afraid :(. Are you referring to the 'geometry' options of either MPlayer or your terminal? 

Andrew

---

### Post by andrew.46 on 2010-05-28
Hi m45t36,

> **m45t3r said:**
> ```
#mplayer -vo fbdev myfile.mp4 
```

You may be interested in embellishing this line a little. The framebuffer driver is not aware of screensize so you can not only tell it the size but subsequently you can manipulate where your video shows on the screen. For example on my laptop I run the framebuffer on a 640 x 480 screen and I like the video to play in the middle of the screen. This can be done as follows:

```
mplayer -vo fbdev -screenw 640 -screenh 480 -geometry 50%:50% myfile.mp4 
```  

Now how cool is that :). **Edit: **Actually it is so cool I have added it to the guide...

Andrew

---

### Post by xzero1 on 2010-05-29
> **andrew.46 said:**
> Hi xzero1,

I will admit I am not completely sure what you mean I'm afraid :(. Are you referring to the 'geometry' options of either MPlayer or your terminal? 

Andrew

Sorry, if I was unclear. I simply want to view the video with the the borders cropped out and with the movie's original aspect ratio.

I found an answer to my own question. Mplayer has an experimental -panscanrange option. If I set it to something around -.45 when viewing the video fullscreen, the "w" and "e" keys will zoom out and in respectively. The docs mention this number is a zoom factor??!? Can anyone explain exactly how this number relates to the video size? At least its easier than using crop. Note this is only supported with the gl driver although xv seems to work for me.

---

### Post by andrew.46 on 2012-05-13
This guide has been transferred to the Ubuntu Wiki:

MPlayerTips
[https://help.ubuntu.com/community/MPlayerTips](https://help.ubuntu.com/community/MPlayerTips)

but support is still available from this Forums thread.

Andrew
May 13th, 2012.

---

### Post by jos.ferraris on 2012-06-11
Hi, I'm playing  around with the ttys and the video from fbdev2 drivers and i'm really surprised how good could be... but, i've noticed a problem: if i play a video on tty1 for example, if i switch to another tty i still see the video.... and all the ttys are unusable; for my porpouse, i wpuld like to get tmux or screen play with tty and watch videos while work on files etc, but for some apps i need a single tty windows but if i'm playing a video i can't use any of the other tty for the mentioned problem... have you any resource or link i can view for?
thank you


srry for the english

---

### Post by Merrattic on 2012-07-09
Attempting to change pitch whilst leaving tempo alone.

Suggested syntax is:
> mplayer -af scaletempo=scale=1.0:speed=pitch input.mp3(this works, and using the [  & ] keys I can change the pitch by 1.10 then 1.21 and then 1.33)

and then (from man mplayer) to add:
> ´[ speed_mult 0.9438743126816935´ and ´] speed_mult 1.059463094352953´to input.conf to change by musical semitone.

But the input.conf should look like this:

> #pitch control
[ speed_mult 0.9438743126816935
] speed_mult 1.059463094352953


This is useful for playing along to music and for whatever reason the music is in the wrong key (or the band tuned up or down in the studio!!)

---

