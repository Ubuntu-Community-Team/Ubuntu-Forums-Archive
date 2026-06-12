---
title: "SMPlayer - Awesome MPlayer Frontend"
date: 2007-05-02
forum: The Cafe
---

### Post by PrimoTurbo on 2007-05-02
[img]http://www.ubuntugeek.com/images/sm/2.png[/img]

Installation Information: [http://www.ubuntugeek.com/smplayer-nice-frontend-for-mplayer.html](http://www.ubuntugeek.com/smplayer-nice-frontend-for-mplayer.html)

I am used to Windows so I use Media Player Classic as my choice of a video player, however I have not been able to find a decent video player for Linux that allowed me to mimic all the features of MPC.

Totem Movie Player - Comes close but doesn't offer enough features, doesn't allow you to select output and video/audio from the player, player controls are a bit too big.

VLC Media Player - I would use VLC, BUT it doesn't offer fullscreen interface controls!!! I hate the keyboard and don't want to use it for fullscreen!

Default MPlayer - Also comes close but doesn't offer a controls/screen combination, all the skins have it separate which is stupid. If you open more then one media file you are lost with separate media controls.

SMPlayer offers everything I need, and is a lot like MPC. I even set up Mouse 1 to pause video, mouse wheel to control volume and double click to enter Full Screen. Furthermore there is good subtitle support and a nice integrated video controls with fullscreen support. Also if you close a video, the next time you open it will reopen at the seek time you closed it at! Awesome...

:guitar:

---

### Post by tbroderick on 2007-05-02
> **PrimoTurbo said:**
> 
 I even set up Mouse 1 to pause video, mouse wheel to control volume and double click to enter Full Screen. Furthermore there is good subtitle support and a nice integrated video controls with fullscreen support. Also if you close a video, the next time you open it will reopen at the seek time you closed it at! Awesome...


You do know the 'spacebar' or 'p' is pause, '0' is volume up, '9' is volume down, 'f' is fullscreen, 'j' toggles subtitles, in the default mplayer config.

---

### Post by unnes on 2007-05-02
Nice, I'll check this out; I use MPC on Windows as well. MPlayer is great, but the default interface is severely ugly.

---

### Post by reacocard on 2007-05-02
I tried this a couple days ago, works fine, except that the keybindings seem to be lost in fullscreen. Eveything else is wonderful, but without custom keybindings that work everywhere, it's useless to me. I'll stick with Xine for now.

---

### Post by kodoku on 2007-05-02
This frontend is awesome (SSA Subtitles finally have full support , ie default colors/styles!)

Except one caveat.  I cannot get it to work with Chinese subtitles (encoded utf-16) at all.  I've tried all possible options but the characters always show up as boxes.  

They worked beautifully in MPlayer, but not at all with SMPlayer.  I tried to change the settings of SMPlayer to be as similar to MPlayer as I can, but so far, no luck.  Could anybody help?

EDIT: Nevermind, it turns out that it wasn't SMPlayer, it was MPlayer itself that was having problems.  After installing the latest svn, everything's great

---

### Post by lethu on 2007-05-05
Yay! I used to use MPC too in Windows and I was seriously missing a good replacement media player or frontend. Xine was perfect under fluxbox but since I moved to gnome it stopped showing the panel in fullscreen mode which is very annoying and every other player/frontend missed capital features exactly like you said in your post, but SMPlayer has everything I want! Thank you for sharing this find : D.

---

### Post by unnes on 2007-05-05
Surprisingly, SMPlayer plays H.264 videos flawlessly on a mediocre machine (P4 2.4GHz HT) on which MPlayer, Kaffeine, Totem, and VLC all crash when trying to play H.264.

I love this!

---

### Post by CarpKing on 2007-05-06
Looks great, though i wish i didn't have to install all that KDE stuff.  For whatever reason, subtitles don't flicker on this like they do in GMplayer (whichever frontend it is that's in the repositories).  The interface is also a lot better.  I just wish someone would make something like this in GTK.

---

### Post by mrgnash on 2007-05-06
It's ok... it has a screenshot utility, which is something GMplayer seems to lack. I don't like the fact that it's KDE though.

---

### Post by tbroderick on 2007-05-06
> **mrgnash said:**
> It's ok... it has a screenshot utility, which is something GMplayer seems to lack. I don't like the fact that it's KDE though.

You can take a screenshot with mplayer.
```
mplayer -vf screenshot video.avi
```

Then just hit the 's' key and it will take a screenshot and save as a png.

---

### Post by mrgnash on 2007-05-06
> **tbroderick said:**
> You can take a screenshot with mplayer.
```
mplayer -vf screenshot video.avi
```

Then just hit the 's' key and it will take a screenshot and save as a png.

Thanks. I can't work out where it's putting the screenshots though, certainly not in the working directory.

EDIT: Nevermind, found them.

---

### Post by cdiem on 2007-05-06
Wow, that's an amazing frontend. I like mplayer in gnome, that I use - but that's unique. Right now I'm testing it in windows, and I may say, that it does things, which my default player so far (BSPlayer) could not do. Later I'm going to test how it works in gnome, since it is QT based - but so far it's a splendid piece of software to me. Thanks for posting this thread, otherwise I would have never known of its existence.

---

### Post by aidanr on 2007-05-06
urgh qt, it's be nice if it was gtk but i'll stick to no interface
[this]("http://dekorte.homeip.net/download/gnome-mplayer/") is worth checking out too

---

### Post by Shinoda on 2007-05-07
I'd prefer GTK+ as well, but apart from that SMPlayer seems awesome. Just compiled and checkinstall'd latest version. Feedback on whether the resulting (attached) deb works for you will be appreciated.> **cdiem said:**
> Right now I'm testing it in windows, and I may say, that it does things, which my default player so far (BSPlayer) could not do.[Zoom Player]("http://inmatrix.com/files/zoomplayer_download.shtml") (included in [CCCP]("http://cccp-project.net/")) is the best one for Windows imo.> **CarpKing said:**
> For whatever reason, subtitles don't flicker on this like they do in GMplayer (whichever frontend it is that's in the repositories).Have you tried disabling double buffering?

** EDIT: Newer version available.**

---

### Post by cdiem on 2007-05-08
I also had problem with the subtitles and OSD showing time flickering in Mplayer in gnome; then I chose "xv" for video output and disabled direct rendering, and this fixed it. Hope this helps.

---

### Post by PhilB on 2007-05-08
Only  installed it half hour ago so this is just my initial reaction. All the media players I have (Mplayer, Totem, Gxine, VLC, Real, Ive tried most) seem to have their quirks rendering some files, or have control issues, but so far SMPlayer has yet to fail. Everything Ive thrown at it plays just fine (so far).
Will be happy to have it as my default player. 

Phil

---

### Post by disturbedite on 2007-05-08
i created a deb package of smplayer 0.4.15 in kubuntu gutsy (i386) today.  its compiled with qt 4.2.3.  in case anyone is interested, i uploaded it here:
[http://www.content-type.com/167477130/smplayer_0.4.15-1_i386.deb.htm](http://www.content-type.com/167477130/smplayer_0.4.15-1_i386.deb.htm)
(click wait in line & download)

btw, its created with checkinstall, so if you ***do mind*** that, then don't download it...

---

### Post by rvm4000 on 2007-05-12
Hi. I'm the developer of smplayer.

First of all I'm very glad that there are so many people who like smplayer :)

I  just wanted to say two things:

1) newer versions allow to change all key shortcuts
2) smplayer is not a KDE application. It requires Qt, only Qt. You don't need to install the KDE or its libraries at all. Optionally it's possible to compile smplayer with KDE support (the only difference is that then it would use the KDE open dialogs), in that case of course it would depend on the KDE libs, but as I said this is completely optional.

---

### Post by jaywee on 2007-05-12
I use this for a month and so far so good!

---

### Post by BarfBag on 2007-05-12
That looks awesome!  I use MPlayer for videos embedded in web pages, and Xine-UI for DVD's.  Under Feisty, Xine seems to glitch a lot.  I've been forced to use VLC a few times.

One question.  Does MPlayer still not support menus?

---

### Post by Shinoda on 2007-05-13
Attached: SMPlayer 0.4.19 compiled with Qt 4.2.3 using checkinstall under Feisty.

> **rvm4000 said:**
> Hi. I'm the developer of smplayer.Hey there. Congratulations and thanks a lot for such a wonderful player. Hope you keep up the great work. I'm not sure if the package I compiled for Ubuntu meets any eventual requirements (or even if it works for everyone), but if it's good enough you may link to it from SMPlayer's site. Otherwise please tell me what else is needed or point me to some sort of guidelines.

** EDIT: Newer version available.**

---

### Post by mech7 on 2007-05-13
The icons are not very consistent :(

---

### Post by rvm4000 on 2007-05-13
> **Shinoda said:**
> Attached: SMPlayer 0.4.19 compiled with Qt 4.2.3 using checkinstall under Feisty.

Hey there. Congratulations and thanks a lot for such a wonderful player. Hope you keep up the great work. I'm not sure if the package I compiled for Ubuntu meets any eventual requirements (or even if it works for everyone), but if it's good enough you may link to it from SMPlayer's site. Otherwise please tell me what else is needed or point me to some sort of guidelines.

Yes, of course, I'll add it to the web page :)

> **mech7 said:**
> The icons are not very consistent :(

That's true. I took the icons from several sources.

But there's available another package ([smplayer-themes-0.1.tar.gz](http://smplayer.sourceforge.net/linux/download/smplayer-themes-0.1.tar.gz)) which provides some extra icon themes, made by other people, and which I think look much nicer.

---

### Post by Bapman on 2007-05-13
Hi,
I installed the deb package given on the official site on a Xubuntu feisty : **SMPlayer 0.4.19 compiled with Qt 4.2.3**. Unfortunately, after installing it, the program starts but is really ugly as you can see in the image attached. It is certainly because I am running Xfce since it seems to look good under Gnome.

Thank you for your answers ! :D

---

### Post by pmj on 2007-05-13
Yeah, smplayer is pretty awesome, despite being QT. ;)

But, can someone confirm that SSA/AS.S (dot inserted due to forum filtering) is fully supported; fonts, colors, positioning and everything? Because to me it looks just like in regular mplayer; broken, that is. I still run Edgy, though, so maybe better SSA/AS.S support has been added since then?

---

### Post by rvm4000 on 2007-05-13
> **Bapman said:**
> Hi,
I installed the deb package given on the official site on a Xubuntu feisty : **SMPlayer 0.4.19 compiled with Qt 4.2.3**. Unfortunately, after installing it, the program starts but is really ugly as you can see in the image attached. It is certainly because I am running Xfce since it seems to look good under Gnome.

According to the screenshot it seems it's using the motif style, which indeed is quite ugly.

There's two ways to fix it:

1) The easiest: run smplayer this way
*smplayer -style plastique*
or
*smplayer -style cleanlooks*

2) The best: run qtconfig
This is a tool included with Qt that allows you to change the default style, font, color... of Qt apps. All changes in qtconfig will affect all Qt-4 apps.

---

### Post by pmj on 2007-05-13
I built mplayer from svn, and ffmpeg too just to be sure, and now I too have nice, styled subs. Fantastic. And being able to use only one instance! It may be an eyesore on my otherwise so nice Gnome desktop, but there's no way I can NOT use smplayer now.

Just one thing, and I understand that this may be considered a feature, but whenever you load a new file the volume slider resets to the middle position. This is a bit annoying if you always want it on the highest volume.

---

### Post by Shinoda on 2007-05-13
> **pmj said:**
> Just one thing, and I understand that this may be considered a feature, but whenever you load a new file the volume slider resets to the middle position.Have you tried changing the default volume under Options > Preferences > Interface > Volume?

---

### Post by pmj on 2007-05-13
> **Shinoda said:**
> Have you tried changing the default volume under Options > Preferences > Interface > Volume?

I had managed to miss that option. All is good now.

---

### Post by Limitlesschannels on 2007-05-14
> **BarfBag said:**
> That looks awesome!  I use MPlayer for videos embedded in web pages, and Xine-UI for DVD's.  Under Feisty, Xine seems to glitch a lot.  I've been forced to use VLC a few times.

One question.  Does MPlayer still not support menus?

hehe, I always find it funny how everyone seems to use VLC as a somewhat last-resort player.  I completely agree, though.  It is fantastic at opening anything, yet the interface is still a hassle for me anyway.

SMplayer sounds pretty great, I guess I will have to try this out and report back.

---

### Post by Bapman on 2007-05-14
> **rvm4000 said:**
> According to the screenshot it seems it's using the motif style, which indeed is quite ugly.

There's two ways to fix it:

1) The easiest: run smplayer this way
*smplayer -style plastique*
or
*smplayer -style cleanlooks*

2) The best: run qtconfig
This is a tool included with Qt that allows you to change the default style, font, color... of Qt apps. All changes in qtconfig will affect all Qt-4 apps.

Thank you very much ! The second solution solved completely my problem !

I have one more little question : is it possible to remove the icon toolbar at the top of the player since I don't use it (there is already a menu and the right click on the mouse) and it takes some place ?

---

### Post by imon9 on 2007-05-14
First of all: thanks you and congratulation to the developer of SMplayer..it is awesome and rocking great!!!

there is some question though:
(1) the slide/seek bar doesnt really work :( i think it is mplayer problem...but perhaps someone can find a way to work around it

thanks again :) really loving it....

i hope mplayer will support DVD menu soon..then it will be so nice to use...
and i hope mplayer-plug in will support more media file type like stage6 .divx files

---

### Post by rvm4000 on 2007-05-14
> **Bapman said:**
> I have one more little question : is it possible to remove the icon toolbar at the top of the player since I don't use it (there is already a menu and the right click on the mouse) and it takes some place ?

Yes, Options->Toolbars.

> **imon9 said:**
> there is some question though:
(1) the slide/seek bar doesnt really work :( i think it is mplayer problem...but perhaps someone can find a way to work around it

Does it happen with all files, or just some?

I know that seeking may not work with some kind of videos (like rmvb or flv), although updating mplayer to a svn version use to fix it.

---

### Post by Bapman on 2007-05-14
[QUOTE=rvm4000]Yes, Options->Toolbars.[/QUOTE]

Sorry for the dummy question and thank you again. I know have a great movie player (faster than VLC). With the display of subtitles below the movie image (but I've seen it is in the bug tracker !), it will just be perfect :D !

Keep up the great work !

---

### Post by imon9 on 2007-05-14
> **rvm4000 said:**
> 
Does it happen with all files, or just some?

I know that seeking may not work with some kind of videos (like rmvb or flv), although updating mplayer to a svn version use to fix it.

well, just certain files... is the file fault i supposed..it wont let me use the slider in any other player anyway (just checked)...

thnaks for the reply though :) i'm happy with smplayer

---

### Post by Shinoda on 2007-05-14
Attached: SMPlayer 0.4.20 compiled with Qt 4.2.3 using checkinstall under Feisty.

---

### Post by CarpKing on 2007-05-15
> **Shinoda said:**
> Attached: SMPlayer 0.4.20 compiled with Qt 4.2.3 using checkinstall under Feisty.

When trying to run it I get:

```
smplayer: error while loading shared libraries: libQt3Support.so.4: cannot open shared object file: No such file or directory
```

---

### Post by pmj on 2007-05-15
> **CarpKing said:**
> When trying to run it I get:

```
smplayer: error while loading shared libraries: libQt3Support.so.4: cannot open shared object file: No such file or directory
```

Build it yourself instead, it's very easy. And stay away from packages made by others with checkinstall.

---

### Post by DracoPsycho on 2007-05-15
Hi, first of all wanted to say that I also switched to SMplayer. But I have a question. Does compiling with Qt4 changes anything? I compiled it with Qt3 and just want to know if I don't miss anything this way. Generally using Gnome so don't know much about Qt ;)

---

### Post by maagimies on 2007-05-15
> **DracoPsycho said:**
> Hi, first of all wanted to say that I also switched to SMplayer. But I have a question. Does compiling with Qt4 changes anything? I compiled it with Qt3 and just want to know if I don't miss anything this way. Generally using Gnome so don't know much about Qt ;)Qt4 supposedly provides speed&memory improvements over Qt3, well, atleast my SMPlayer compiled with Qt4 seemed snappy :D
[Info on Qt4]("http://www.trolltech.com/products/qt/whatsnew")
edit: And I currently run SMPlayer in Gnome as well, migrated from KDE a while ago and haven't looked back, I'll try KDE4 though when it's released. But Qt remains one of my favorite toolkits for all eternity :D

---

### Post by imon9 on 2007-05-15
rvm4000,

i have another feature request this time:
(1) add a button to the main interface to open the playlist (it will be easier than 2-click at the menu or ctrl-L) :p

(2) can u support costume encoding in playlist? (some of my songs mp3 tag is in chinese, russian, korean...can u please add encoding setting?)

(3) when i tried to play a shoutcast-stream: usually other media player will show the currently playing song, but smplayer didnot... can u make it show please?

(4) can you make the playlist remove selected files by a simple "delete" key? (it is simpler to remove stuff that i added through the whole directory)

thanks in advance, work at your own pace though...! good luck and cheers for open source! and cheers for smplayer... i hope i will be added to ubuntu repositories soon.. it is a great player

---

### Post by rvm4000 on 2007-05-15
1) There's already a button in the main toolbar to open the playlist.

2) smplayer can load and save *.m3u8 files. These files are like *.m3u but encoded in UTF-8.

3) (**Edit**) check out version 0.4.21.

4) Options->Preferences->Mouse & keyboard, in the actions editor you can assign for instance the key "Delete" to the action *pl_remove_selected*.

---

### Post by rvm4000 on 2007-05-15
> **DracoPsycho said:**
> Hi, first of all wanted to say that I also switched to SMplayer. But I have a question. Does compiling with Qt4 changes anything? I compiled it with Qt3 and just want to know if I don't miss anything this way. Generally using Gnome so don't know much about Qt ;)

If you compile it with Qt >= 4.2 then you've got an option to show a icon in the system tray (the same can be achieved with Qt 3 too but it's necessary then to compile it with KDE support).

---

### Post by userundefine on 2007-05-15
As a KDE user, I'm glad to get some great programs in this gnome-heavy distro ! :)

(Although, of course, I like some gtk apps as well...)

---

### Post by DracoPsycho on 2007-05-16
> **rvm4000 said:**
> If you compile it with Qt >= 4.2 then you've got an option to show a icon in the system tray (the same can be achieved with Qt 3 too but it's necessary then to compile it with KDE support).

Thanks for the info, I'll check it out this evening. :)

---

### Post by CarpKing on 2007-05-16
It compiled nicely (had to install some qt headers and whatnot), and now I've got fully-styled subtitles in Linux for the first time!  The "extra options" field in the preferences is another potentially handy feature that I have on occasion wished gmplayer had.  Great job on this!  I might even give the Windows version a try sometime.

---

### Post by pmj on 2007-05-17
> **CarpKing said:**
> It compiled nicely (had to install some qt headers and whatnot), and now I've got fully-styled subtitles in Linux for the first time!
Wonderful, is it not? :)
Oh how we have waited for this.

---

### Post by megahead13 on 2007-05-18
Great player!!! If only mplayer supported DVD menus... Only one problem (not SMplayer's fault): I set it to be the default player for my video files, but when I clik to open such a file, Kaffeine is loaded, instead of SMplayer. Any ideas on that?

---

### Post by Shinoda on 2007-05-20
> **megahead13 said:**
> Only one problem (not SMplayer's fault): I set it to be the default player for my video files, but when I clik to open such a file, Kaffeine is loaded, instead of SMplayer. Any ideas on that?At least in Gnome I have to set SMPlayer as the default app per file type (i.e. video format), don't know about KDE though (if that's yours). You may also try and uninstall Kaffeine, in case you don't need it anymore.

---

### Post by megahead13 on 2007-05-21
Well, I solved it, but not the way I would expect... Thanx anyway :)

PS From a little search in the forum, I saw that many people had the same problem, not only with SMplayer, but also with VLC, etc. And yes, I 'm refering to Kubuntu

---

### Post by rvm4000 on 2007-05-24
Hi again.

I installed a kubuntu 7.04 in a vmware virtual machine. I've just made two deb packages for smplayer:

[smplayer_0.4.28_i386.deb](http://smplayer.sourceforge.net/linux/download/debs/smplayer_0.4.28_i386.deb)
[smplayer-themes_0.1_all.deb](http://smplayer.sourceforge.net/linux/download/debs/smplayer-themes_0.1_all.deb)

Although created in kubuntu, they should work on ubuntu too.

Could you test if they really work (and dependencies are right and so on)?

BTW, compiled with Qt 3 (without KDE support)

---

### Post by TheMono on 2007-05-24
Been using this player exclusively for a while. It is brilliant - plus the development is extremely fast, with a request I reported about the OSD in a Xinerama setup being fixed in a couple of days.

Here's a 64 bit package if anyone needs it (Kubuntu Feisty). This is NOT made with checkinstall, it is a proper dh_make and dpkg-buildpackage package. Having said that, it isn't as professional as a MOTU package...

(Edit: Hopefully fixed broken dependencies)
(Edit 2: Instead of depending on mplayer, now depends on either mplayer or mplayer-nogui, since mplayer depends on stuff not included in Kubuntu out of the box)

---

### Post by cdiem on 2007-05-30
As I have expressed my excitement over a previous version of SMplayer in windows, I'd like to bow before the creator of this amazing piece of software. Just a while ago, only with the download of 7 additional packages from the ubuntu repos, I tried the version 0.5.0 (deb package from the website). It's all that I've ever wanted from a player. It's amazing, genial, whatever you say - I like this player so much. Thanks a lot to the developer, who, not only has created such a masterpiece, but also emits new versions so often (and even in my own language). The 0.5.0. version runs blazing fast on my Ubuntu-gnome on Fuzitsu Siemens Amilo Pro v3505, faster than any other player (mplayer, gxine and totem inclusive). This is my new default player.

---

### Post by Bapman on 2007-05-30
I totally agree with cdiem. So here ends my quest of an equivalent to Media Palyer Classic from Windows !

---

### Post by Healey on 2007-06-08
Hi

Please can someone tell me how to remove SMPlayer ???

I dont like it because it changes my sound settings - When I exit smplayer I have to turn the system sound setting up again  !!!!

it also stops mplayer from working properly

Please Please - How do I uninstal SMPlayer

I have tried ADD/REMOVE but it cannot find it !!!

Regards

Healey

---

### Post by cdiem on 2007-06-08
Healey, if you have used a .deb package to install it, the command
> sudo apt-get remove --purge smplayer
or
> sudo dpkg -r smplayer
in a terminal should work. You can try also to find it in the Synaptic package manager, it should be listed as an "installed locally" software. 
If you have built it from a tarball, opening a terminal, navigating to the directory where you had built it, and making the command 
> sudo make uninstall
should work. I'm really amazed of your wish, but everyone has the right to have a taste; to me, smplayer (though not totally complete!) is probably the most composite video player under linux (because of all the tweaks it allows you to make). I haven't still tried kafeine and kplayer though; they may be nice (however they are kde applications, and I like gnome right now). Good luck in searching a good substitute for smplayer!

---

### Post by Healey on 2007-06-08
Hi

Thanks for your reply I will give that a try

The reason that I want to remove it, is because it does something with my sound. Sound is the one thing that I must have and it is the one thing that I always have problems with. Feisty solved the sound problem for me so I dont want that to change.

I dont know why when I close SMPlayer the system sound settings change - I have to double click the sound icon and slide the volume and PCM controls back up again !!! - i dont know why !!

I also dont know why it has stopped  mplayer from working - This all sounds a little bit like windows - install new software and something else fails - If you see what I mean

If there is a setting in SMPlayer that I can change so that it does not change my system settings when I exit  then I would try it !!


Thanks and Regards

Healey

---

### Post by cdiem on 2007-06-08
If you want SMplayer not to use the system volume control, then you should hit Ctrl+P (which opens the preferences), then in the "General" tab you should check the box "Use software volume control". This is it, smplayer should no longer change the volume of your system. As for the disabling of Mplayer, I have difficulties to tell you why it does not work; by me it is just fine (although I use mostly smplayer recently instead of it). Hope this helps.

---

### Post by Healey on 2007-06-08
Thanks Cdiem

I will give that setting a try and see what happens

Thanks for your time

Best Regards

Healey

---

### Post by rvm4000 on 2007-06-08
I don't know how SMPlayer could have done that mplayer didn't work, as SMPlayer does not touch the mplayer config (or anything related to it) at all.

About your problem with the audio, the "Use software volume control" option should work. That way mplayer won't touch the mixer at all.

---

### Post by pmj on 2007-06-09
So, what do you all think of the interface? Do you really use all the buttons it has? I thought it was a bit cluttered and couldn't help poking around in the source to try to fix it. Turned out that it would require more work than I'm willing/able to do to implement all my ideas (such as replacing the big sound slider with a Gnome style pop-up slider button, only display audio and subtitle buttons if they're needed for the current video, only display the previous/next chapter buttons if the video has chapters, and a few more things), but at least it's a bit cleaner, and it was super easy to do.

If more people would like a simpler, smarter GUI, maybe we should send in some ideas. Actually, a customizable toolbar might be something that's planned already; isn't that the KDE way?

---

### Post by Healey on 2007-06-09
Hi

Referenece Mplayer


The error I get when trying to play a DVD with Mplayer after installing SMPlayer :-

           " Error opening/Initializing the selected video_out (-vo) device "

I am NOT an expert so I cannot say that SMPlayer caused this problem. But Mplayer worked fine before the installation and now it does not. What am i supposed to think ??

I am not blaming anything - I am just reporting what I see

I have now removed SMPlayer and I still get the same error 

Thanks for your help

Regards

Healey

---

### Post by pmj on 2007-06-09
> **Healey said:**
> Hi

Referenece Mplayer


The error I get when trying to play a DVD with Mplayer after installing SMPlayer :-

           " Error opening/Initializing the selected video_out (-vo) device "

I am NOT an expert so I cannot say that SMPlayer caused this problem. But Mplayer worked fine before the installation and now it does not. What am i supposed to think ??

I am not blaming anything - I am just reporting what I see

I have now removed SMPlayer and I still get the same error 

Thanks for your help

Regards

Healey

I thought someone said that SMPlayer doesn't touch any of mplayer's config files.

Which video output driver do you have selected now? Try switching to xv or x11 if it's not one of them. Try changing this in both SMPlayer and mplayer in case they do conflict with each other somehow.

---

### Post by Healey on 2007-06-09
Hi

I have tried switching to xv and x11 but now when I try to open the DVD - Mplayer screen opens and then closes again.

It does not play the DVD - Totem plays the same DVD perfectly so I dont think its the DVD or the hardware

AS for SMPlayer not touching Mplayer - I have been on to the web site and found the following quote

"SMPlayer intends to be a complete front-end for MPlayer, from basic features like playing videos, DVDs, and VCDs to more advanced features like support for MPlayer filters and more."

Surely it must interact with Mplayer - Or am I wrong ???

Regards and thanks

Healey

---

### Post by Shinoda on 2007-06-09
> **Healey said:**
> Surely it must interact with MplayerQuite a lot of course, but afaik it uses MPlayer ignoring and not touching its config. Have you tried purging and reinstalling MPlayer?```
sudo aptitude purge mplayer
sudo aptitude install mplayer
```As for uninstalling SMPlayer, if you installed it from a deb, I would also recommend the above method, i.e.,```
sudo aptitude purge smplayer
```or, if you'd like to keep its settings in your system (e.g. for an eventual reinstallation),```
sudo aptitude remove smplayer
```

---

### Post by rvm4000 on 2007-06-09
> **Healey said:**
> AS for SMPlayer not touching Mplayer - I have been on to the web site and found the following quote

"SMPlayer intends to be a complete front-end for MPlayer, from basic features like playing videos, DVDs, and VCDs to more advanced features like support for MPlayer filters and more."

Surely it must interact with Mplayer - Or am I wrong ???

Of course, it's a mplayer front-end so it has to run it. But everything is passed through parameters in the command line, the mplayer config is not touched at all. I assure you (I'm the developer of smplayer, BTW).

One thing that might have happened is that, because of dependencies, when you installed smplayer, another version of mplayer (maybe an update) were installed too.

It seems that in ubuntu there are two packages for mplayer: mplayer and mplayer-nogui. Look which one you have installed.

Also look at the ~/.mplayer/config. Paste it here.

It also will be very useful to paste all mplayer output when trying to play a file, that way we could see better where the problem is.

---

### Post by Healey on 2007-06-09
Hi

I tried the following

sudo aptitude purge mplayer
sudo aptitude install mplayer

but Mplayer still does not work - I get the same errors

Regards

Healey

---

### Post by Healey on 2007-06-09
Hi

Also look at the ~/.mplayer/config. Paste it here.

I get :

# Write your default config options here!


I guess that means it is empty

Regards

Healey

---

### Post by rvm4000 on 2007-06-09
Uninstalling a program, even with *purge* won't remove the config in your home. 

Is there anything else in the ~/.mplayer directory? You may delete or rename the ~/.mplayer directory to be sure you start again with an empty config.

Try to play a file. Try first with *-vo xv*. If it fails try with *-vo x11*, and then with *-vo gl2*.

If none works, copy and paste here the output of mplayer.

---

### Post by cdiem on 2007-06-10
Please, try the following command in a terminal, after you insert the DVD into your drive:
> mplayer -vo xv dvd://
and paste the output of the terminal here. 
After that, try in a terminal
> gedit  ~/.mplayer/gui.conf 
and paste the text file here.
You can also try to go to the preferences of Mplayer, the "Video" tab, and try one at a time all of the video drivers there. I think that at least one of the drivers should work for you (that means, select a driver (gl for instance), close mplayer, open mplayer, try to open a file with mplayer). Also, if SMplayer works fine with you, could you please tell us which output devices you use for video and audio (that is, in "preferences", "general" tab, "output devices"). If they work for you with SMplayer, I cannot think of a reason, for which they would not work for you with Mplayer. That's it, I'm out of ideas for now. Good luck!

---

### Post by Shinoda on 2007-06-10
> **rvm4000 said:**
> Uninstalling a program, even with *purge* won't remove the config in your home.Hm, at least according to Synaptic's help, the (I'm guessing equivalent) "Complete Removal" option only applies to Debian. Is that also the case with aptitude's [FONT=Courier New]purge[/FONT] and apt-get's [FONT=Courier New]--purge[/FONT]? And if so, does that mean using "remove" or "purge" (or Synaptic's "Removal" or "Complete Removal") under Ubuntu gives the same result, i.e., untouched config in [FONT=Courier New]/home[/FONT] then?

---

### Post by Healey on 2007-06-10
Hi

Thanks for you help

Hi This is what I got from the terminal  


mplayer -vo xv dvd://

MPlayer 2:1.0~rc1-0ubuntu9 (C) 2000-2006 MPlayer Team
CPU: Genuine Intel(R) CPU           T1300  @ 1.66GHz (Family: 6, Model: 14, Stepping: 8)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing dvd://.
There are 23 titles on this DVD.
There are 1 chapters in this DVD title.
There are 1 angles in this DVD title.
number of audio channels on disk: 0.
number of subtitles on disk: 0
MPEG-PS file format detected.
MPEG: No audio stream found -> no sound.
VIDEO:  MPEG2  720x576  (aspect 2)  25.000 fps  6000.0 kbps (750.0 kbyte/s)
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 720 x 576 (preferred colorspace: Mpeg PES)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try adding the scale filter, e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [libmpeg2] MPEG 1/2 Video decoder libmpeg2-v0.4.0b
Selected video codec: [mpeg12] vfm: libmpeg2 (MPEG-1 or 2 (libmpeg2))
==========================================================================
Audio: no sound
Starting playback...
VDec: vo config request - 720 x 576 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [xv] 720x576 => 768x576 Planar YV12 
V:   0.7  12/ 12 ??% ??% ??,?% 0 0 

Exiting... (End of file)


Regards

Healey

---

### Post by Healey on 2007-06-10
Hi

This is what I got from

gedit  ~/.mplayer/gui.conf

enable_audio_equ = "no"
vo_driver = "xmga"
vo_panscan = "0.000000"
vo_doublebuffering = "yes"
vo_direct_render = "no"
vo_dxr3_device = "/dev/em8300-0"
v_framedrop = "0"
v_flip = "-1"
v_ni = "no"
v_idx = "-1"
vf_pp = "no"
vf_autoq = "0"
vf_lavc = "no"
ao_driver = "alsa"
ao_volnorm = "no"
softvol = "no"
ao_surround = "no"
ao_extra_stereo = "no"
ao_extra_stereo_coefficient = "1.000000"
dvd_device = "/dev/dvd"
cdrom_device = "/dev/cdrom"
osd_level = "1"
sub_auto_load = "yes"
sub_unicode = "no"
sub_pos = "100"
sub_overlap = "no"
font_factor = "0.750000"
font_text_scale = "5.000000"
font_osd_scale = "6.000000"
font_blur = "2.000000"
font_outline = "2.000000"
font_autoscale = "3"
cache = "no"
cache_size = "2048"
playbar = "no"
load_fullscreen = "no"
show_videowin = "yes"
stopxscreensaver = "no"
autosync = "no"
autosync_size = "0"
gui_skin = "default"
gui_save_pos = "yes"
gui_main_pos_x = "455"
gui_main_pos_y = "598"
gui_video_out_pos_x = "454"
gui_video_out_pos_y = "257"
equ_band_00 = "0.000000"
equ_band_01 = "0.000000"
equ_band_02 = "0.000000"
equ_band_03 = "0.000000"
equ_band_04 = "0.000000"
equ_band_05 = "0.000000"
equ_band_06 = "0.000000"
equ_band_07 = "0.000000"
equ_band_08 = "0.000000"
equ_band_09 = "0.000000"
equ_band_10 = "0.000000"
equ_band_11 = "0.000000"
equ_band_12 = "0.000000"
equ_band_13 = "0.000000"
equ_band_14 = "0.000000"
equ_band_15 = "0.000000"
equ_band_16 = "0.000000"
equ_band_17 = "0.000000"
equ_band_18 = "0.000000"
equ_band_19 = "0.000000"
equ_band_20 = "0.000000"
equ_band_21 = "0.000000"
equ_band_22 = "0.000000"
equ_band_23 = "0.000000"
equ_band_24 = "0.000000"
equ_band_25 = "0.000000"
equ_band_26 = "0.000000"
equ_band_27 = "0.000000"
equ_band_28 = "0.000000"
equ_band_29 = "0.000000"
equ_band_30 = "0.000000"
equ_band_31 = "0.000000"
equ_band_32 = "0.000000"
equ_band_33 = "0.000000"
equ_band_34 = "0.000000"
equ_band_35 = "0.000000"
equ_band_36 = "0.000000"
equ_band_37 = "0.000000"
equ_band_38 = "0.000000"
equ_band_39 = "0.000000"
equ_band_40 = "0.000000"
equ_band_41 = "0.000000"
equ_band_42 = "0.000000"
equ_band_43 = "0.000000"
equ_band_44 = "0.000000"
equ_band_45 = "0.000000"
equ_band_46 = "0.000000"
equ_band_47 = "0.000000"
equ_band_48 = "0.000000"
equ_band_49 = "0.000000"
equ_band_50 = "0.000000"
equ_band_51 = "0.000000"
equ_band_52 = "0.000000"
equ_band_53 = "0.000000"
equ_band_54 = "0.000000"
equ_band_55 = "0.000000"
equ_band_56 = "0.000000"
equ_band_57 = "0.000000"
equ_band_58 = "0.000000"
equ_band_59 = "0.000000"



Strange thing is - Mplayer worked before

Regards

Healey

---

### Post by rvm4000 on 2007-06-10
I don't see any error message in the mplayer output.

Maybe the first title in the disc contains the DVD menus (which mplayer doesn't show).
Try to play a different title:

mplayer -vo xv dvd://2
mplayer -vo xv dvd://3
...

> **Healey said:**
> vo_driver = "xmga"

Have you tried to change in gmplayer the video driver from xmga to xv?

---

### Post by Healey on 2007-06-11
Hi

Thanks for the reply

Doing this -   mplayer -vo xv dvd://2

Opens the DVD minimised and it starts to play - It then freezes and will NOT shut down !!!

Maybe its better if I use Totem - It plays very well

Best regards

Healey

---

### Post by rvm4000 on 2007-06-11
This is really strange. Can you play other videos (mpeg, avi...) or does it fail too?

Have you tried to remove (or rename) the ~/.mplayer directory?

---

### Post by Healey on 2007-06-11
Hi

Yes it is really strange

Yes I can play clips from Web pages

I tried uninstalling using synaptic and deleting the .mplayer folder then re installing using synaptic and I still get the same problem

The PC I am using is a laptop - So I decided that I would have a look at my desktop version of Mpalyer - It has the same problem - NOW THAT is really strange

Both machines had Mplayer installed originally using Automatix - But I dont think that is the problem I have never had any problems using Automatix before

Anyway as I said before - totem is working very well

Thanks for you help so far

Healey

---

### Post by zeeR on 2007-06-12
Well, I THOUGHT this was a good movie player...but after installing and removing some stuff on ubuntu, now it's simply unusable. I didn't remove anything related to qt or mplayer...But now i tried reinstalling everything. The problem is that after opening a movie, it takes almost 10 seconds for smplayer to load it! then it runs normally, but any minor change i do on the settings, for example, and more 10 seconds to resume the movie...I tried this with different filetypes, and with files that worked perfectly before.
I really liked it, but now I'm getting more and more disappointed with Ubuntu.

---

### Post by rvm4000 on 2007-06-12
I've got reports about that 10 second delay. It seems to happen when mplayer tries to disable the screensaver.

Uncheck the option "Disable screensaver" in Preferences->General and see if that fixes the delay.

---

### Post by zeeR on 2007-06-13
> **rvm4000 said:**
> I've got reports about that 10 second delay. It seems to happen when mplayer tries to disable the screensaver.

Uncheck the option "Disable screensaver" in Preferences->General and see if that fixes the delay.

Thanks a lot, that fixed it! I submitted a bug to the bug tracker, on the Smplayer website, hope they can make it even better :-D

---

### Post by rvm4000 on 2007-06-13
I'm afraid this can't be fixed in smplayer. It just passes the option -stop-xscreensaver to mplayer. If that option doesn't work well then either it's a mplayer bug or maybe it's a problem in gnome (it seems this only happens in gnome).

So I suggest you to try to reconfigure the screensaver in gnome and see if the problem goes away, or update mplayer to see if the problem has already been fixed.

---

### Post by imon9 on 2007-06-15
hi Rvm4000,

can i request some new features? SMPLayer playlist is good, but the playlist always opens in the middle of the screen and do not remember it's position. (same thing happen with smplayer main windows).. can you make:
(1) then remember previous position 
(2) can you make them sticky? eg: if i stick the playlist to the bottom of main-window, then i close them and then move the main window around, then when i reopen the playlist, it will still stick below main-window. (same thing if i stick it to the side of main-window)

other request:
(3) can you make the playlist build-into the main windows as "side bar" (like totem?" & autoresize if there is no video playing (eg, if i'm playing audio, then the playlist will occupy the whole width, if video is present, then it is added to the side of the currently playing video as side-bar)

thanks in advance... smplayer is great!!! in fact, super great!!!

---

### Post by cdiem on 2007-06-19
rvm4000, I have a question. Can subtitles be displayed under the movie, in the black part of the screen? If yes, how? Thanks in advance.

---

### Post by Shinoda on 2007-06-19
> **cdiem said:**
> Can subtitles be displayed under the movie, in the black part of the screen?Video > Aspect ratio > 16:9 Letterbox

---

### Post by cdiem on 2007-06-20
Thanks a lot. Actually, the 4:3 works even better for me. SMplayer is great!

---

### Post by Shinoda on 2007-06-20
> **cdiem said:**
> Actually, the 4:3 works even better for me.My bad, I forgot not everyone owns a widescreen monitor. :>

---

### Post by Jamie Jackson on 2007-06-27
I'm having a tough time finding SMPlayer in the repos. Where is it?

---

### Post by Shinoda on 2007-06-28
[Official site]("http://smplayer.sf.net/") | [Feisty debs]("http://ubuntuforums.org/showthread.php?t=472149") | [Gutsy debs]("http://ubuntuforums.org/showthread.php?t=440351")

---

### Post by pickarooney on 2007-06-28
I installed Smplayer, used it twice, really lked it, but now it won't play videos any more.
When I run it from the command line and try to read a file, nothing happens in the interface and the shell I get this message:
```

Debug: MplayerProcess::init_rx
Warning: Core::startMplayer: mplayer process didn't start

```

Mplayer still works fine on its own.

[edit]
For some reason (and I *know* I didn't touch this option) the path to mplayer changed itself to /usr/share/mplayer from /usr/bin/mplayer. Changing it back all is well.

Another question: is it possible to switch aspect ratio with a shortcut key? I can't find this option in the list.

---

### Post by Jamie Jackson on 2007-06-28
> **Shinoda said:**
> [Official site]("http://smplayer.sf.net/") | [Feisty debs]("http://ubuntuforums.org/showthread.php?t=472149") | [Gutsy debs]("http://ubuntuforums.org/showthread.php?t=440351")

Thanks, Shinoda, but I'm specifically wondering about repos. 

How does such an established, popular app *not* make it into the Ubuntu repos? That sort of thing confuses me. (I'm new to Ubuntu, thought, so there's a lot that confuses me.)

Thanks,
Jamie

---

### Post by Shinoda on 2007-06-28
> **Jamie Jackson said:**
> How does such an established, popular app *not* make it into the Ubuntu repos?Maybe only now is it getting popular and established. Give it time.> **Jamie Jackson said:**
> That sort of thing confuses me. (I'm new to Ubuntu, thought, so there's a lot that confuses me.)lol

---

### Post by Jamie Jackson on 2007-06-28
> **Shinoda said:**
> Maybe only now is it getting popular and established. Give it time.

You know, I think you're right. I think I saw something that led me to believe that SMPlayer had been around and established for longer than I thought. I could have swore that I saw threads dating back to 2004, but now I think I was completely wrong about that. Poking around again, it seems that the buzz only started this year.

*.deb installation it is, thanks.

---

### Post by Shinoda on 2007-06-28
> **Jamie Jackson said:**
> *.deb installation it is, thanks.Actually repos are all about installing debs too, only the process is automated. :]

---

### Post by rvm4000 on 2007-06-29
> **reacocard said:**
> I tried this a couple days ago, works fine, except that the keybindings seem to be lost in fullscreen. Eveything else is wonderful, but without custom keybindings that work everywhere, it's useless to me. I'll stick with Xine for now.

Has anyone else had this problem?

---

### Post by Trogdor 20X6 on 2007-07-01
I've been having a problem with SMPlayer where it won't play any videos if the screensaver has come on. SMPlayer would be working then if I lock the session or just let the screensaver turn on it won't work after I would come back.

---

### Post by rvm4000 on 2007-07-01
Have you tried checking the option "Don't repaint the background of the video window" in Preferences->Advanced?

---

### Post by Trogdor 20X6 on 2007-07-02
Tried it now and it didn't work. I don't know why but if the screensaver ever starts if I try using smplayer anytime after that it won't play any video files.

---

### Post by rvm4000 on 2007-07-02
Have you tried setting x11 as video driver?

---

### Post by Trogdor 20X6 on 2007-07-02
Yeah. That's the driver I always use.

---

### Post by rvm4000 on 2007-07-03
That's strange.
Is there any error message in the mplayer log?

---

### Post by Trogdor 20X6 on 2007-07-03
> /usr/bin/mplayer -noquiet -nofs -sub-fuzziness 1 -identify -slave -vo x11 -ao alsa -zoom -nokeepaspect -input conf=/usr/share/smplayer/input.conf -stop-xscreensaver -wid 58720279 -colorkey 131586 -monitoraspect 1.25 -subfont-autoscale 1 -subfont-text-scale 5 -subcp ISO-8859-1 -aid 1 -subpos 100 -contrast 0 -brightness 0 -hue 0 -saturation 0 -ss 826 -osdlevel 0 -vf-add expand=osd=1 -noslices -vf-add screenshot -softvol -softvol-max 110 /home/carlos/downloads/Doctor Who S03E13 Last of the Time Lords [MM].avi 

MPlayer 2:1.0~rc1-0ubuntu9.1 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Pentium(R) D CPU 2.80GHz (Family: 15, Model: 4, Stepping: 7)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
stderr: Can't open joystick device /dev/input/js0: No such file or directory
stderr: Can't init input joystick
stderr: mplayer: could not connect to socket
stderr: mplayer: No such file or directory
stderr: Failed to open LIRC support. You will not be able to use your remote control.
Terminal type `unknown' is not defined.

Playing /home/carlos/downloads/Doctor Who S03E13 Last of the Time Lords [MM].avi.
AVI file format detected.
ID_VIDEO_ID=0
ID_AUDIO_ID=1
VIDEO:  [XVID]  640x368  12bpp  25.000 fps  821.0 kbps (100.2 kbyte/s)
Clip info:
 Software: VirtualDubMod 1.5.4.1 (build 2178/release)
ID_CLIP_INFO_NAME0=Software
ID_CLIP_INFO_VALUE0=VirtualDubMod 1.5.4.1 (build 2178/release)
ID_CLIP_INFO_N=1
ID_FILENAME=/home/carlos/downloads/Doctor Who S03E13 Last of the Time Lords [MM].avi
ID_DEMUXER=avi
ID_VIDEO_FORMAT=XVID
ID_VIDEO_BITRATE=821016
ID_VIDEO_WIDTH=640
ID_VIDEO_HEIGHT=368
ID_VIDEO_FPS=25.000
ID_VIDEO_ASPECT=0.0000
ID_AUDIO_FORMAT=85
ID_AUDIO_BITRATE=116416
ID_AUDIO_RATE=0
ID_AUDIO_NCH=0
ID_LENGTH=3084.24
xscreensaver_disable: Could not find XScreenSaver window.
Opening video filter: [screenshot]
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
ID_VIDEO_CODEC=ffodivx
==========================================================================
Forced audio codec: mad
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 48000 Hz, 2 ch, s16le, 128.0 kbit/8.33% (ratio: 16000->192000)
ID_AUDIO_BITRATE=128000
ID_AUDIO_RATE=48000
ID_AUDIO_NCH=2
Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3)
==========================================================================
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
ID_AUDIO_CODEC=mad
Starting playback...
VDec: vo config request - 640 x 368 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.74:1 - prescaling to correct movie aspect.
ID_VIDEO_ASPECT=1.7391
VO: [x11] 640x368 => 640x368 Planar YV12  [zoom]
stderr: gnome_screensaver_control()SwScaler: using unscaled yuv420p -> bgr24 special converter
stderr: X11 error: BadMatch (invalid parameter attributes)
stderr: 
stderr: 
stderr: MPlayer interrupted by signal 6 in module: decode_video
ID_SIGNAL=6
stderr: - MPlayer crashed. This shouldn't happen.
stderr:   It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
stderr:   gcc version. If you think it's MPlayer's fault, please read
stderr:   DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
stderr:   won't help unless you provide this information when reporting a possible bug.

X11 error. And I found that it works when I have the Run MPlayer in its own window option selected. But I like it better when SMPlayer keeps to one window.

---

### Post by BobLand on 2007-07-03
rm400 - a big thank you.  
This is by far the best video player for me, that is.  

However, I have one small problem.  I can't go "next" or "back" with any of the buttons or shortcuts.  I can, however, set the left mouse click (LogiTech MX500 configured for 7 buttons) to go "play next" but I have the right button set to "play back" and it shows a menu instead.

Any ideas?

thanks for you great software!
bobland

BTW, the plastique and clear themes don't work.

---

### Post by rvm4000 on 2007-07-03
> **BobLand said:**
> However, I have one small problem.  I can't go "next" or "back" with any of the buttons or shortcuts.  I can, however, set the left mouse click (LogiTech MX500 configured for 7 buttons) to go "play next" but I have the right button set to "play back" and it shows a menu instead.

First of all be sure you're using at least version 0.5.11. There was a bug in previous versions and the "previous" and "next" shorcuts didn't work.

Now go to the shortcut editor (Preferences->Keyboard & mouse) and set the keys you want for the actions "play_next" and "play_prev".

> **Trogdor 20X6 said:**
> X11 error. And I found that it works when I have the Run MPlayer in its own window option selected. But I like it better when SMPlayer keeps to one window.

As you said this problem happens once the screensaver has come on, could you try disabling the option "Disable screensaver" in Preferences->General?

---

### Post by BobLand on 2007-07-03
I'm using 0.5.21
Doesn't matter what I set any buttons to, they don't work.  Also, I set the mouse to try pl_next and next_chapter.  In both cases, the mouse seems to go to a random chapter.  Sometimes the beginning, sometimes the end, mostly just somewhere in the middle.

Play list only shows dvd://1 01:31:06.  Next/Previous doesn't work here.

Browse->Chapter displays chapters by number.  That works.

bobland

---

### Post by Trogdor 20X6 on 2007-07-04
> **rvm4000 said:**
> 
As you said this problem happens once the screensaver has come on, could you try disabling the option "Disable screensaver" in Preferences->General?
That didn't work either. I don't know what the problem is but it only seems to happen when I use x11.

I switched it to xv but now I have a new problem. The contrast is too high when I use SMPlayer. Whenever I set it lower using > xvattr -a XV_CONTRAST -v 64SMPlayer changes it back to the old settings when I play a video.
**Edit:** I added -contrast -50 to the extra options to pass to mplayer that seems to normalize it.

---

### Post by rvm4000 on 2007-07-04
> **BobLand said:**
> I'm using 0.5.21
Doesn't matter what I set any buttons to, they don't work.  Also, I set the mouse to try pl_next and next_chapter.  In both cases, the mouse seems to go to a random chapter.  Sometimes the beginning, sometimes the end, mostly just somewhere in the middle.

Play list only shows dvd://1 01:31:06.  Next/Previous doesn't work here.

Browse->Chapter displays chapters by number.  That works.

bobland

For dvd chapters, go to Preferences->Performance and be sure that the option "Fast seek to chapters in dvds" is unchecked.

The options "play previous" and "play next" refer to the items in the playlist. They are not for changing chapters.

---

### Post by rvm4000 on 2007-07-04
> **Trogdor 20X6 said:**
> **Edit:** I added -contrast -50 to the extra options to pass to mplayer that seems to normalize it.

Another thing that you can do is open the video equalizer, play a video, set the desired contrast, and then press the button "Set as default values". That will make that all new videos will use those values in the equalizer as default values. 
The problem is that videos played previously will still use the previous contrast, as they remember it  from previous sessions.

---

### Post by BobLand on 2007-07-04
OK.  Glad you cleared up the difference between next playlist and next chapter.  Found the @ and ! and all works fine.

Great program, excellent support!
bobland

---

### Post by ShadowVlican on 2007-09-30
how do i set SMPlayer to become the default player for all my video files?

---

### Post by Shinoda on 2007-09-30
> **ShadowVlican said:**
> how do i set SMPlayer to become the default player for all my video files?
Under GNOME, right-click file > Properties > Open With. Repeat for each type/format.

---

### Post by andrew.46 on 2007-10-02
Hi,

 Great tip:

> **tbroderick said:**
> You can take a screenshot with mplayer.
```
mplayer -vf screenshot video.avi
```

Then just hit the 's' key and it will take a screenshot and save as a png.

 mplayer can also ouptut pngs for every frame of a movie file:

```
$ mplayer -vo png movie_file.mpg
```

 Make sure you have plently of disk space :-) Works with gif and jpg as well.

                     Andrew

---

### Post by capink on 2008-01-01
> **imon9 said:**
> 

other request:
(3) can you make the playlist build-into the main windows as "side bar" (like totem?" & autoresize if there is no video playing (eg, if i'm playing audio, then the playlist will occupy the whole width, if video is present, then it is added to the side of the currently playing video as side-bar)


I second the part about the width of the playlist when docked on the sidebar. I wish it could have a horizontal scroll bar like totem.

---

### Post by Jeroi on 2008-01-06
I made from latest source QT4 amd64 deb packet, but it is too big (1,4mb) to upload it to forums. If you developer want to check that it works and add this packet to sourceforge so that ubuntu, kubuntu and other debian based amd64 users can dl latest version for their architechture. I can send the packet with email or other way if there is a good way.

For the playlist, I am suggesting fullscreen playlist when moving mouse to leftend of the fullscreen. Then playlist would slide from left to right and you could then move mouse on top of the playlist to edit items in it. Moving mouse of from playlist would make playlist slide away and if not moved mouse like 10sec playlist would slide away automatically.

---

### Post by Kimm on 2008-01-06
If anyone is interested. Heres a .deb I compiled for amd64:

[http://rapidshare.com/files/81777864/smplayer_0.5.62_amd64.deb.html](http://rapidshare.com/files/81777864/smplayer_0.5.62_amd64.deb.html)

Its _not_ a checkinstall package, so it resolves dependencies. Its compiled for qt4 btw.

---

### Post by samwyse on 2008-01-06
Nice, other mplayer guis I've tried have lacked in different ways. I don't know how I've missed this player. I've been using Kaffeine, but it's a bit messy and it doesn't play all videos properly like mplayer.

---

### Post by Lostincyberspace on 2008-01-06
I have been using it for a while now some times I have problems with knotify but most of the time it is fine.

---

### Post by pilat on 2008-05-19
I have some questions:

The very first one: is there an option to call mplayer with **only** path to the file (and let mplayer to decide on the rest of options automatically)?

I have a strange problem, probably with my ATI driver. Anyway, when I run:

```
mplayer dvd://1
```
-- or (when compositing enabled) --
```
mplayer -vo x11 dvd://1
```

I gives much smoother playback, in comparison to when I try to play the same DVD in SMPlayer. I noticed, that SMPlayer sends lots of parameters to mplayer executable, but I'm really not mplayer-guru, to understand which ones affect the performance in the lion's share...


Q2. What are "Double buffering" and "Direct rendering" options (Video tab, under Prferences) exactly? What would be the best config for AVIVO cards users (fglrx v8.3 driver, from Kubuntu 8.04's repos)?



btw, Very good work! The best front-end to mplayer I've ever seen ;-)

---

### Post by rvm4000 on 2008-05-19
> **pilat said:**
> I have some questions:

The very first one: is there an option to call mplayer with **only** path to the file (and let mplayer to decide on the rest of options automatically)?

No.

> **pilat said:**
> 
I have a strange problem, probably with my ATI driver. Anyway, when I run:

```
mplayer dvd://1
```
-- or (when compositing enabled) --
```
mplayer -vo x11 dvd://1
```

I gives much smoother playback, in comparison to when I try to play the same DVD in SMPlayer. I noticed, that SMPlayer sends lots of parameters to mplayer executable, but I'm really not mplayer-guru, to understand which ones affect the performance in the lion's share...

By default smplayer uses no cache for dvds (chapter switching may not work with it), but you can try to set a cache (Preferences->Performance->Cache) and see if it works better.

> **pilat said:**
> Q2. What are "Double buffering" and "Direct rendering" options (Video tab, under Prferences) exactly? What would be the best config for AVIVO cards users (fglrx v8.3 driver, from Kubuntu 8.04's repos)?

Click on the "Help" button in the preferences dialog to know more about those options.

---

### Post by mMirai on 2012-04-10
Does anyone know how I can take a screenshot as a jpeg? I look through the .config and .input files, but can't find anything about it.

---

### Post by sisco311 on 2012-04-10
> **mMirai said:**
> Does anyone know how I can take a screenshot as a jpeg? I look through the .config and .input files, but can't find anything about it.

Please don't BUMP old threads. Start a new one with your question in the [Absolute Beginner Talk]("http://ubuntuforums.org/forumdisplay.php?f=326") or [Multimedia & Video]("http://ubuntuforums.org/forumdisplay.php?f=334") forum.

Thread closed.

---

