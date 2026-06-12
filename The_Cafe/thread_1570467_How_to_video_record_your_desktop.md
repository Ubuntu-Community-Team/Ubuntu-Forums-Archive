---
title: "How to video record your desktop"
date: 2010-09-08
forum: The Cafe
---

### Post by t0p on 2010-09-08
I picked up this little trick from a tweet from [Hak5]("http://www.hak5.org")'s Darren Kitchen:

If you want to video record your desktop (for instance because you're making a video tutorial of something or other), open a terminal and run the following command:

```

ffmpeg -f x11grab -s 1024x768 -r 15 -i :0.0 -s 1024x768 -r 15 -sameq video.avi

```

Now your monitor video is being recorded to the file 'video.avi'.  *Minimize* (don't close) the terminal, then do whatever it is you want to be recorded.  At the end restore the terminal window and stop ffmpeg with Ctrl-C.  And there you go.

I suppose you could use the same trick to check up on what someone else is up to on the computer, if you have access to their account or they use yours, and they're not canny enough to wonder what's that ffmpeg doing in the background.

---

### Post by TyrantWave on 2010-09-08
Or you could try Kazam:

[http://www.omgubuntu.co.uk/2010/09/kazam-0-1-available-the-screencasting-bar-on-linux-just-got-raised/](http://www.omgubuntu.co.uk/2010/09/kazam-0-1-available-the-screencasting-bar-on-linux-just-got-raised/)

---

### Post by realzippy on 2010-09-08
Thanks for sharing,works.

*...and they're not canny enough to wonder what's that ffmpeg doing in the background.*

...and not canny enough to wonder why entire disc is full...   ;)

---

### Post by Rasa1111 on 2010-09-08
kazam has a way to go. 
though still decent for it's young age. lol

 Nice command, t0p. :) Thanks. <3

---

### Post by wkhasintha on 2010-09-08
Thanx for both of you.

---

### Post by undecim on 2010-09-08
looks like kazam just uses ffmpeg as well.

Is there any way to get audio with that command as well? That's pretty handy and it would be easy to make a script that lets you screencast with a hotkey.

EDIT: I suppose I could always go back and add the audio with an editor, huh?

---

### Post by t0p on 2010-09-08
> **undecim said:**
> 
EDIT: I suppose I could always go back and add the audio with an editor, huh?

I think that's the way.  If you're making this video as part of a tutorial (for instance) you may want to cut out stuff (mistakes, irrelevancies etc) or add new bits of footage.  So you do all your editing *then* add audio and it'll all marry up the way it's meant to.

---

### Post by Rasa1111 on 2010-09-08
one question~
 Where exactly does the video.avi file go to? 
I can't seem to find it.. :?:

 and that top link in your sig rocks! <3
Thanks man.

---

### Post by wojox on 2010-09-08
Pretty Sweet. Thanks for the tip.

---

### Post by wojox on 2010-09-08
> **Rasa1111 said:**
> one question~
 Where exactly does the video.avi file go to? 
I can't seem to find it.. :?:

 and that top link in your sig rocks! <3
Thanks man.

Mine was right in my Home Folder. ;)

---

### Post by Rasa1111 on 2010-09-08
> **wojox said:**
> Mine was right in my Home Folder. ;)

Thats where I figured it should be,
 Don't see it though.. lol
Maybe I did something wrong.. 
(i didnt hit enter in terminal after i put the command in)
so yea... prolly. lol
Thanks.

---

### Post by realzippy on 2010-09-08
> **wojox said:**
> Mine was right in my Home Folder. ;)


...no suprise when running command from ~/   :D

---

### Post by Rasa1111 on 2010-09-08
well aren't you just real zippy. lol :P
wise guy,
some of us are newbs y'know. :lol:

 but yeah, I redid it and it was in my home folder,
I just didnt hit enter the first time because..
well.. i was just following instructions as close as possible. lol

 But, He did say ***run*** the command, 
so mybad. lol  O_o

---

### Post by realzippy on 2010-09-08
...am real zippy as [zippy]("http://en.wikipedia.org/wiki/Zippy_the_Pinhead") is...

---

### Post by t0p on 2010-09-08
> **Rasa1111 said:**
> but yeah, I redid it and it was in my home folder,
I just didnt hit enter the first time because..
well.. i was just following instructions as close as possible. lol

 But, He did say ***run*** the command, 
so mybad. lol  O_o

Sorry my instructions weren't clear enough for you.  This is a problem when writing tuts/guides for people of differing experience - some people need very precise, point-by-point instructions, whereas some others just need a general direction and can fill in the missing pieces themselves.

Anyway, I'm glad you got it to work.  For ages I'd been trying to find a way to record the desktop.  As is often the way with Linux, it turned out to be a particular command using a common utility.  That's one reason I like Linux: on one level it's dead simple, on another level it is capable of very complex tasks.

---

### Post by Rasa1111 on 2010-09-08
> ..am real zippy as zippy is...

oh wow,
 my uncle used to have (maybe still does) an album with a whole bunch of those comics cut out and saved. lol
Never seen it again until now, thanks!

---

### Post by Rasa1111 on 2010-09-08
> **t0p said:**
> Sorry my instructions weren't clear enough for you.  This is a problem when writing tuts/guides for people of differing experience - some people need very precise, point-by-point instructions, whereas some others just need a general direction and can fill in the missing pieces themselves.

Anyway, I'm glad you got it to work.  For ages I'd been trying to find a way to record the desktop.  As is often the way with Linux, it turned out to be a particular command using a common utility.  That's one reason I like Linux: on one level it's dead simple, on another level it is capable of very complex tasks.

No apologies mate, it was my goof.
Your instructions were very good, Im probably just over tired.
Havent been to bed yet, pulled an all nighter with the telescopes again. lol

 But looking back, your instructions would be good enough for even a super, week old noob.  
Sorry for seeming so simple. lol

 I had used other GUI based tools to record my desktop,
but they all seemed to be just a bit buggy in one place or another,
but this is the cleanest Ive been able to record my desk yet.
Very cool bit to know. thanks again! <3

---

### Post by t0p on 2010-09-08
> **realzippy said:**
> Thanks for sharing,works.

*...and they're not canny enough to wonder what's that ffmpeg doing in the background.*

...and not canny enough to wonder why entire disc is full...   ;)

Heh heh yeah.  That video.avi file will become pretty large, pretty quickly. For anyone who doesn't know how to "hide" this kind of problem: it's possibly best to direct the ffmpeg output to a large external drive where the, um, volunteer is less likely to notice.  Something like

```

ffmpeg -f x11grab -s 1024x768 -r 15 -i :0.0 -s 1024x768 -r 15 -sameq media/disk/video.avi

```

---

### Post by Swagman on 2010-09-08
How is this different from GTK-recordmydesktop ?

---

### Post by Rasa1111 on 2010-09-08
> **Swagman said:**
> How is this different from GTK-recordmydesktop ?

no GUI,
and it seems to do it without any glitches! woot! lol

---

### Post by Swagman on 2010-09-08
I tried it and it works... 

But (always a but)

Resolution is too low. I cant see half of my desktop

---

### Post by Sealbhach on 2010-09-08
glc-capture is also very good for recording high quality video from games.

[http://nullkey.ath.cx/projects/glc/](http://nullkey.ath.cx/projects/glc/)

.

---

### Post by Arthur_D on 2010-09-08
> **Swagman said:**
> I tried it and it works... 

But (always a but)

Resolution is too low. I cant see half of my desktop

Just insert your native resolution then.

```
ffmpeg -f x11grab -s [Swagman's native resolution] -r 15 -i :0.0 -s [Swagman's native resolution] -r 15 -sameq video.avi
```

---

### Post by Rasa1111 on 2010-09-08
> **Swagman said:**
> I tried it and it works... 

But (always a but)

Resolution is too low. I cant see half of my desktop

hmmm, mine comes out near perfect.
but my res is 1024x768

---

### Post by Swagman on 2010-09-08
> **Arthur_D said:**
> Just insert your native resolution then.

```
ffmpeg -f x11grab -s [Swagman's native resolution] -r 15 -i :0.0 -s [Swagman's native resolution] -r 15 -sameq video.avi
```

Yup.. That'll teach me to read the command before entering !! (res 1920x1200)

Works. Bit blurry on full screen but.. Works

ta

---

### Post by keithpeter on 2010-09-08
Hello All

+1 for RecordMyDesktop because I need sound at the time of recording. I take the point about editing in a video editor and adding a sound channel later, but its time folks, link below done in half an hour including the impress file from a scan...

[http://www.youtube.com/user/keithpeterb](http://www.youtube.com/user/keithpeterb)

I use PiTiVi to convert to .avi and to resize and to tidy up for upload to yuetoob. Ogv files produced by recordmydesktop don't work.

If you are playing tricks, make sure your stooge has a sense of humour :twisted:.

---

### Post by BLTicklemonster on 2011-10-30
Cool. Just watched and recorded, on charging bull cam, some folks putting up an inflatable bear behind the charging bull in downtown Manhattan, and they were making the bear hump the bull. 

Not sure why, but it seemed like the thing to do at the time.

Anyway, yes, the two resolutions the command show; the first is the screen resolution, the second is the target resolution, or how large you want it to be.

I created a launcher (run in terminal) in case I want to record anything in the future. Like gimp tutorials or something. Thanks for the post!

---

### Post by Elfy on 2011-10-30
Old thread closed.

---

