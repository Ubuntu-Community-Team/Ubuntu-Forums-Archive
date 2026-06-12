---
title: "How to play music from the command line"
date: 2011-03-03
forum: Tutorials
---

### Post by shantiq on 2011-03-03
The information in this thread has been moved to [https://help.ubuntu.com/community/PlayMusicFromCommandLine](https://help.ubuntu.com/community/PlayMusicFromCommandLine)


A thread for discussion of the wiki page only can be found here [http://ubuntuforums.org/showthread.php?t=2012415](http://ubuntuforums.org/showthread.php?t=2012415)


Thread closed.

Some people like myself do not thrive on Library-type players and prefer players like xmms audacious or deadbeef and would rather even play their current discs/music files straight from the command-line; call it the **Zen** school of music-playing :KS:KS    [as in pared down]


[CENTER][ATTACH]220048[/ATTACH]
[/CENTER]
This is a short howto for those people


USING  gnome-open-terminal     or    gnome-terminal



so to get a great handy command-line music player  [looks like a player and is independent from folders and other open terminals]



**1.**  ```
 sudo apt-get-install gnome-open-terminal
```

**2.** Open Music folder/Right-click/Choose Open In terminal

**3.** enter  ```
nvlc */./*
``` 



or refine to cut out random txt/image files     to    ```
nvlc */./*flac *ape *wv *shn *aac *m4a *mp3        
```  and any other music extensions you have   you can also simplify this with an alias   see [**here**]("http://ubuntuforums.org/showpost.php?p=12037205&postcount=6")


  there you go....  arrows for navigation


[B]PS
[/B]


a short [**video**]("http://www.youtube.com/watch?v=6jQC9iYWin4")   to illustrate



**also easy way to have hotkeys to pause/play   and go to next track  **  can be set in vlc **global** preferences and will work with nvlc too


================================================================

[B]3 routes in detail
[/B]



I propose 3 routes here   [SoX]("http://sox.sourceforge.net/") which has many functions; NVLC which is part of the VLC package and Mplayer which can be used from the command line too



[B]
1.[/B] First SoX is really marvelous usually described as the Swiss Army knife of sound processing programs it is perfect for our purpose here



> sudo apt-get install sox libsox-fmt-all



say you have a bunch of flacs    it will play them which a simple command


```
play * flac

```but with Sox you can add filters thus

```
play * flac bass +4 gain +2 reverb

```will add quite a bit of bass reverb and added volume

for all options run   ```
man SoX
```it accommodates a lot of formats

> AUDIO FILE FORMATS: 8svx aif aifc aiff aiffc al amb amr-nb amr-wb anb au avi avr awb cdda cdr cvs cvsd cvu dat dvms f32 f4 f64 f8 ffmpeg flac fssd gsm gsrt hcom htk ima ircam la lpc lpc10 lu m4a m4b maud mp2 mp3 mp4 mpg nist ogg prc raw s1 s16 s2 s24 s3 s32 s4 s8 sb sds sf sl smp snd sndfile sndr sndt sou sox sph sw txw u1 u16 u2 u24 u3 u32 u4 u8 ub ul uw vms voc vorbis vox wav wavpcm wmv wv wve xa
PLAYLIST FORMATS: m3u pls
CTRL+c gets you to the next track if you hit CTRL+c and hit c twice it stops play



2.NVLC is simply superb as a command line player it looks quite nice for starters

[CENTER]
[[IMG]http://img690.imageshack.us/img690/867/97104002.th.png[/IMG]](http://img690.imageshack.us/img690/867/97104002.png)[ATTACH]220048[/ATTACH]
[/CENTER]



you summon it this way   ```
nvlc */./*
``` to enter every folder and play every file in turn.  If you are in a single folder simply enter ```
nvlc *
``` or ```
nvlc *.flac  or whichever extension you are playing
```and it can be used almost as well as the GUI version  left and right arrows will move along your file as great speed

keys "a" and "z" control up and down volume   space bar to stop and start    and info on your track with i

h to find all your options


=========================================================



=======================================================

**3.**
Now neither SoX nor Nvlc can handle [shorten]("http://ubuntuforums.org/attachment.php?attachmentid=174028&d=1288481430") which is a format that i favour and this is where **Mplayer **came in handy; and of course it can used for all formats handled by Mplayer and that is like NVLC a lot of formats

even easier here    go into the folder and then enter ```
mplayer *
```   or add your extension if you only want one specific extension played   ie  ```
mplayer *.wv
```**if you** want to enter all the music subfolders in your Music folder and play all the music files with mplayer you can use this little code As is or as a script


```
for i in */
do
  cd "$i"
mplayer *
  cd ..
done
```or even more simply   ```
mplayer */./*
```    will do the same


**Other Tips**
==============================================

[B]TO  PLAY A CUEFILE

 ```
nvlc name.cue
```[/B]

==============================================

[B]TO NAVIGATE ON NVLC AND MPLAYER

[/B]Use top-bottom-left-right arrows


see further up for info on hotkeys & alias script

---

### Post by adeee on 2011-03-03
Nice how to. :P

---

### Post by linuxbasiccommand on 2011-03-04
> **adeee said:**
> Nice how to. :P
Thanks! i'm looking

---

### Post by shantiq on 2012-02-28
will play all lossless and lossy formats


[CENTER]see here for visual [ATTACH]213421[/ATTACH] in Guake[/CENTER]


> for i in */
do
  cd "$i"
nvlc *.cue
  cd ..
done     save as nvlc.sh   and make executable and save in Music



In Terminal

```
cd Music
```    [assuming all your music folders containing cues are in Music   if not change obviously]

enter   ```
./nvlc.sh
```     it will open and play your first cuefile


CTRL +C   takes you to the next cuefile
n and p take you to next and previous track in current cuefile
SHIFT b lets you navigate all folders
h   TO SEE ALL OPTIONS
c   to go black and white   [sadly no longer available]  **well turns out it has been replaced by   > nvlc --nocolor**

---

### Post by nothingspecial on 2012-02-28
Hi shantiq,

Try this to play your collection randomly :)

```
mplayer -quiet -shuffle -playlist <(find ~/Music -type f)
```

---

### Post by shantiq on 2012-02-28
cute:KS   return key to move to next one

one more handy tool

---

### Post by shantiq on 2012-05-02
actually there is even another  way    apart from gnome-terminal

and that is gnome-open-terminal



so to get a great handy command-line music player  [looks like a player and is independent from folders and other open terminals]



**1.**  ```
 sudo apt-get-install gnome-open-terminal
```

**2.** Open Music folder/Right-click/Choose Open In terminal

**3.** enter  ```
nvlc */./*
```   there you go....  arrows for navigation



you can refine of course if you want to see only certain files played   ie

```
 nvlc  */./*.flac *m4a *.mp3 *ape *wv  *cue

```


[CENTER][[IMG]http://img220.imageshack.us/img220/6341/screenshotfrom201205021.th.png[/IMG]](http://img220.imageshack.us/img220/6341/screenshotfrom201205021.png)[/CENTER]


also works with mplayer [navigation not as supple of course]

```
 mplayer */./*.flac *m4a *.mp3 *ape *wv

```







[CENTER]








[/CENTER]

---

### Post by shantiq on 2012-06-17
a short [**video**]("http://www.youtube.com/watch?v=wPu7h-Aeh6Y")   to illustrate



also easy way to have hotkeys to pause/play   and go to next track    can be set in vlc **global** preferences and will work with nvlc too



see  [ATTACH]219878[/ATTACH]

---

### Post by Amanuntu on 2012-06-17
Thanks help really appreciated:P

---

### Post by Elfy on 2012-06-29
This thread is closed. 
 
The information is now held on the community wiki at  [https://help.ubuntu.com/community/PlayMusicFromCommandLine](https://help.ubuntu.com/community/PlayMusicFromCommandLine)
 
Thank you for your thread and the work you have done in keeping it current and of use to the community. 
 
A thread for discussion of the wiki can be found at  [http://ubuntuforums.org/showthread.php?t=2012415](http://ubuntuforums.org/showthread.php?t=2012415)
 
 
Support threads regarding the wiki and it's content should be created in a suitable forum.

---

