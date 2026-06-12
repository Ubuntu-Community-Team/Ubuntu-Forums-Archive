---
title: "Record your desktop with recordmydesktop ;)"
date: 2006-11-06
forum: Tutorials
---

### Post by loell on 2006-11-06
[SIZE="4"]**[http://recordmydesktop.sourceforge.net]("http://recordmydesktop.sourceforge.net")**[/SIZE]
a nice screen/desktop video recorder, try it :)

**note: ** [SIZE="5"]you can now install it from the repository  through ADD/REMOVE[/SIZE]

[COLOR="Red"]installation command[/COLOR]:  **sudo apt-get install gtk-recordmydesktop**

you can find it in Applications menu --> sound and video --> gtk-recordmydesktop


**[COLOR="Blue"]Using Recordmydesktop[/COLOR]**

in command line console type the command **recordmydesktop** 
you can stop the recording by pressing **ctrl-c**
or in gui-front just click record, and just click the white square on system tray to stop
the output is in **ogg **video format however you can convert it to **avi** by **mencoder**

example 

    > mencoder -idx input.ogg -ovc lavc -oac mp3lame -o output.avi
    *note install mencoder if its not installed by doing  ```
sudo aptitude install mencoder 
```

then you can upload it to youtube or wherever.

[SIZE="3"]video sample(s)
[B]by Sandman32 [http://www.youtube.com/watch?v=2FZ9N_YEo3g]("http://www.youtube.com/watch?v=2FZ9N_YEo3g") (beryl 0.1.2 burn and water effects)
             [http://www.youtube.com/watch?v=XJWYSfGvITA]("http://www.youtube.com/watch?v=XJWYSfGvITA")(warcraft III demo)
by Sandman32[http://www.youtube.com/watch?v=VwzsrpHRxtY]("http://www.youtube.com/watch?v=VwzsrpHRxtY")(beryl  /water effect)
by iadanr [http://www.youtube.com/watch?v=RF7FgWcIxg8]("http://www.youtube.com/watch?v=RF7FgWcIxg8")(beryl)
[/B][/SIZE]

enjoy :)

---

### Post by loell on 2006-11-07
one roughly made video demo using this tool

[http://www.youtube.com/watch?v=_6OlnyEKlXY]("http://www.youtube.com/watch?v=_6OlnyEKlXY")

i encourage anybody using this tool to also post your samples :)

---

### Post by sibrand on 2006-11-07
Doesn't work with Beryl... does anyone know a recorder that does ? :(

---

### Post by loell on 2006-11-07
> **sibrand said:**
> Doesn't work with Beryl... does anyone know a recorder that does ? :(

i think there is a beryl specific plugin that can video capture beryl animations.

---

### Post by loell on 2006-11-12
just an update release, it can now record beryl/compiz
refer to the first post ;)

---

### Post by giuliastro on 2006-11-12
> **loell said:**
> just an update release, it can now record beryl/compiz
refer to the first post ;)

Nice job! It works here with Beryl + NVidia. Actually my video are not that smooth but I guess I'd need a quad core to have smooth Beryl videos..

---

### Post by xfile087 on 2006-11-12
Maybe it's just me (i'm new to Linux) but when I record my desktop at full resolution (1280x1024) the recorded video won't open in anything. If I record at 640x480 it will play but the colour seems washed out?

Beryl enabled or disabled - same results...


**I found out it's a bug with my graphics card driver!**

---

### Post by loell on 2006-11-12
> **giuliastro said:**
> Nice job! It works here with Beryl + NVidia. Actually my video are not that smooth but I guess I'd need a quad core to have smooth Beryl videos..

perhaps try

```
recordmydesktop --quick-subsampling --zero-compression
```

for maximum performance :)

---

### Post by aidanr on 2006-11-12
[http://www.youtube.com/watch?v=RF7FgWcIxg8](http://www.youtube.com/watch?v=RF7FgWcIxg8)

works pretty well, although using it without those two switches you posted resulted in a crash when pressing ctrl+c

---

### Post by loell on 2006-11-12
> **aidanr said:**
> [http://www.youtube.com/watch?v=RF7FgWcIxg8](http://www.youtube.com/watch?v=RF7FgWcIxg8)

works pretty well, although using it without those two switches you posted resulted in a crash when pressing ctrl+c

really? ok we will let the developer know about this,

cool video, can you show more, if you have spare time :mrgreen:

---

### Post by iovar on 2006-11-12
> **aidanr said:**
> [http://www.youtube.com/watch?v=RF7FgWcIxg8](http://www.youtube.com/watch?v=RF7FgWcIxg8)

works pretty well, although using it without those two switches you posted resulted in a crash when pressing ctrl+c

If it happened after pressing ctrl-c it's the --zero-compression switch. 
(though I can't imagine why yet)
The program must have left a  folder rMD-session-(num) on your home folder, which you should delete(it probably takes up lots of space).

Can you tell me what files where in the folder?
Also did it procceed at all at the encoding or did it crash immediately?
Last thing, if it's not much trouble, can you try again?
I haven't added error handling on IO yet, so it might have been a
simple read error(or a previous write error).


thanks.

EDIT:Aidanr I see there's one more video on you account that is not correct. I can't make out the output, 
but counting the lines it seems to be v0.2.6 (unless you've run with --no-wm-check).
Can you verify on this, because beryl has changed the name it reports a couple of times and 
I want to make sure I haven't missed any of it.

---

### Post by aidanr on 2006-11-12
thats weird, i reinstalled and it works now without those switches:-k 
earlier it crashed immediately without encoding, it printed out 15 or 20 lines of errors, can't remember what they were now, at least one of them was to do with /usr/lib/libogg.so, and it left that folder in my home directory

i installed the old version first, then the gtk frontend, then installed the newer version, then uninstalled both and just now reinstalled the newer version again

anyway, works now, very nice app:)

btw yes the other video was with the earlier version

---

### Post by BLTicklemonster on 2006-11-12
What kind of resource hog is this? Could one possibly run this and a game at the same time to record what is going on?

---

### Post by iovar on 2006-11-12
> **aidanr said:**
> thats weird, i reinstalled and it works now without those switches:-k 
earlier it crashed immediately without encoding, it printed out 15 or 20 lines of errors, can't remember what they were now, at least one of them was to do with /usr/lib/libogg.so, and it left that folder in my home directory

i installed the old version first, then the gtk frontend, then installed the newer version, then uninstalled both and just now reinstalled the newer version again

anyway, works now, very nice app:)

btw yes the other video was with the earlier version

Oops, when I've read your previous post, I thought it was the switches that caused the problem. Anyway though, it was probably a random read or
write error. I'll make sure to get those before releasing the final version.


Thanks a lot for claryfing things!

---

### Post by iovar on 2006-11-12
@BLTicklemonster:
If it is a relatively light game, on a low resoulution and on a strong pc, then maybe...

I got this on my p4 3.2 on 640x480@15 fps:
[http://video.google.com/videoplay?docid=-807141800269084169&hl=en](http://video.google.com/videoplay?docid=-807141800269084169&hl=en)
running the program like this:
recordmydesktop --quick-subsampling --zero-compression --full-shots --with-shared -windowid  0x4000076 -o warzone2100-1.ogg -v_quality 24 -s_quality 4    

(to get a windowid you need to run xwininfo first)

As you see a-v sync is bad(sound stays 2-3 seconds ahead)
It also needed about 1gb of free space for the 5 minute recording.


Other than that, to anyone using this program, or istanbul,
you can upload ogg/theora directly on google video. 
I don't know why they don't mention it on the accepted formats, but it works fine.

---

### Post by ChadMC on 2006-11-12
I need some help getting my sound to record. I've messed with some things in alsamixer and I've tried the built in gnome mixer. I just can't get any sound to record. I'd like it to record anything that plays in my desktop. Like music for example. I've even tried to get it to work with a mic. but I can't get that to work either.

Anyways, very nice program. I got it recording my beryl desktop much better than xvidcap could do.

---

### Post by BLTicklemonster on 2006-11-12
Um how do you get it to turn off once you start recording?

---

### Post by ChadMC on 2006-11-12
If you are using the command-line, press CTRL-C. I haven't really used the GUI tool, but I think it's an icon in the taskbar.

---

### Post by djsroknrol on 2006-11-13
When I try to install the deb with the deb installer, I get a message to the effect that the dependency of the deb is unsatisfyable libasound2.

I thought I was missing the file, but it's there..I tried to disable sound capture, but that didn't help..

Any ideas?

---

### Post by iovar on 2006-11-13
> **djsroknrol said:**
> When I try to install the deb with the deb installer, I get a message to the effect that the dependency of the deb is unsatisfyable libasound2.

I thought I was missing the file, but it's there..I tried to disable sound capture, but that didn't help..

Any ideas?

It's an edgy package, not a dapper one. Looking at [http://packages.ubuntu.com/](http://packages.ubuntu.com/),
shows that you can satisfy the dependency (libasound2 (>> 1.0.11) , while dapper is at 1.0.10) ,
if you enable the backports repository.

---

### Post by djsroknrol on 2006-11-13
> **iovar said:**
> It's an edgy package, not a dapper one. Looking at [http://packages.ubuntu.com/](http://packages.ubuntu.com/),
shows that you can satisfy the dependency (libasound2 (>> 1.0.11) , while dapper is at 1.0.10) ,
if you enable the backports repository.

That's the version of libasound2 that's on my computer according to Synaptic...any other ideas?

---

### Post by gorilla_king on 2006-11-13
yeah i'm having the same problem the libasound2 thing and synaptic says i'm upto date with the 1.0.10 but like you said edgy eft has the 1.0.11 so how do i upgrade to the new one without updating to edgy eft yet?
thanks in advance

---

### Post by loell on 2006-11-13
a dapper deb package must be created, i can't create a dapper package, because my pc is all edgy now, perhaps someone can volunteer for building the dapper package of recordmydesktop

---

### Post by yabbadabbadont on 2006-11-13
Have you posted a link to the sources yet?  If you did, I must have missed it...

---

### Post by d3v1ant_0n3 on 2006-11-13
I installed the prog, and ran it. It seems to try and record (the tray icon is the same as istanbuls, right?)

After stopping the recording, it ran my CPU to the ground for 5 mins or so, and them came up with error 11.

It's places a file in my /home folder called out.ogg, which, according to the thumbnail at least, seems to be the recording. If I try and open it in any player, however, it opens, and then closes immediately.

Suggestions?

---

### Post by loell on 2006-11-13
> **yabbadabbadont said:**
> Have you posted a link to the sources yet?  If you did, I must have missed it...

sorry, what sources do you mean?

---

### Post by loell on 2006-11-13
> **d3v1ant_0n3 said:**
> I installed the prog, and ran it. It seems to try and record (the tray icon is the same as istanbuls, right?)

After stopping the recording, it ran my CPU to the ground for 5 mins or so, and them came up with error 11.

It's places a file in my /home folder called out.ogg, which, according to the thumbnail at least, seems to be the recording. If I try and open it in any player, however, it opens, and then closes immediately.

Suggestions?

what's the size of out.ogg , its seems you installed the older pacakge release, casue the new one is just the command line
and no gtk front end yet

---

### Post by yabbadabbadont on 2006-11-13
> **loell said:**
> sorry, what sources do you mean?

The source code to the program... so that it can be built on Dapper, or any other Linux flavor for that matter.

---

### Post by loell on 2006-11-13
> **yabbadabbadont said:**
> The source code to the program... so that it can be built on Dapper, or any other Linux flavor for that matter.

oh, i see

its in 
[http://recordmydesktop.sourceforge.net]("http://recordmydesktop.sourceforge.net")

---

### Post by loell on 2006-11-13
the developer is recommending the cvs though. as it can record berl/compiz

---

### Post by yabbadabbadont on 2006-11-13
> **loell said:**
> oh, i see

its in 
[http://recordmydesktop.sourceforge.net]("http://recordmydesktop.sourceforge.net")

Thanks.

---

### Post by yabbadabbadont on 2006-11-13
> **loell said:**
> the developer is recommending the cvs though. as it can record berl/compiz

Good to know.  By the way, I'm not volunteering to package it up for Dapper.  I have no problem building stuff from source, but I don't have any experience with creating a proper deb file (with all the dependencies and such).  I just figured that whoever did volunteer would need to know from where to get the code.

---

### Post by yabbadabbadont on 2006-11-13
By the way, the project's homepage doesn't work without javascript being enabled...  That is generally not a good thing.

---

### Post by d3v1ant_0n3 on 2006-11-13
I removed the version I installed yesterday, and installed the 2.6 CVS-1 version (CLI only).

Installed fine. Ran with:

andi@andi-laptop:~$ recordmydesktop --quick-subsampling --zero-compression
Initial recording window is set to:
X:0   Y:0    Width:1024    Height:768
Adjusted recording window is set to:
X:0   Y:0    Width:1024    Height:768
Your window manager appears to be beryl


Detected 3d compositing window manager.
Reverting to full screen capture at every frame.
To disable this check run with --no-wm-check
(though that is not advised, since it will probably produce faulty results).

Initializing...
Recording on device hw:0,0 is set to:
2 channels at 22050Hz
Capturing!
Shutting down.Saved 134 frames in a total of 444 requests
....
Encoding started!
This may take several minutes.
Pressing Ctrl-C will cancel the procedure (resuming will not be possible, but
any portion of the video, which is already encoded won't be deleted).
Please wait...
[99%] 
Encoding finished!
Wait a moment please...
   
Done.
Written 10911001 bytes
(10360192 of which were video data and 550809 audio data)

Cleanning up cache...
Done!!!
Goodbye!


Ended up with an out.ogg file of 138.4Kb.

Which really doesn't seem right (surely that's WAY too small for a video file?)

---

### Post by loell on 2006-11-13
> **yabbadabbadont said:**
> By the way, the project's homepage doesn't work without javascript being enabled...  That is generally not a good thing.

iovar or john the project developer have been monitoring this thread, rest assure, that your site feedback can reach him :)

---

### Post by gorilla_king on 2006-11-13
still unsure about what to do about the libasound2 thing, and i decided i would just go ahead and upgrade to edgy overnite and now it's giving me problems and doesn't want to upgrade. crap.

---

### Post by loell on 2006-11-13
@d3v1ant_0n3 indeed the file size is too small

---

### Post by djsroknrol on 2006-11-13
I solved the libasound2 problem by getting the dev files for it...even got the gtk frontend to install...it's great...records my Beryl or Gnome sessions fine....but....

It only plays them back in a Beryl session...same thing as a previous poster's is experiencing...Mplayer opens and then shuts down in a Gnome playback...any clues as to why?

---

### Post by gorilla_king on 2006-11-13
well, ok, i realized i screwed up my sources list at some point so i got that straightened out and had to upgrade nearly two hundred packages...done now..installed libasound2-dev and i am still getting the sae error as before when trying to install the deb. just giving up for the night. i'll check this thread tomarrow afternoon to see if there are any developements on the issue.

Good night to all,
thomas

---

### Post by iovar on 2006-11-14
**gorilla_king** :

If this command:
```
apt-cache show libasound2 |grep Version
```

shows any less than 1.0.11, the package can't be installed.
If you are on edgy, you should already have it. If you are on dapper according to 
[http://packages.ubuntu.com/](http://packages.ubuntu.com/) you can get it by enabling the backports repository. 
libasound2-dev is only required for compilation.
I can only go around guessing how djsroknrol installed by getting the dev package. 
Maybe he has backports already enabled and installing  libasound2-dev forced the upgrade on libasound2 too.

But, perhaps you should wait until someone makes a package for dapper.
I wouldn't want this program to become the reason for anyone breaking his installation...


**yabbadabbadont **:
> By the way, the project's homepage doesn't work without javascript being enabled... That is generally not a good thing.
I know I should get rid of it alltogether and use php. It's certainly 
within my long-term plans, but I don't spend much time with it (obviously)
so it'll have to wait...

Also, to get the latest compy of the code you need to run these:

```
cvs -d:pserver:anonymous@recordmydesktop.cvs.sourceforge.net:/cvsroot/recordmydesktop login 
```
(empty password)


```
 cvs -z3 -d:pserver:anonymous@recordmydesktop.cvs.sourceforge.net:/cvsroot/recordmydesktop co -P recordmydesktop
```



@**d3v1ant_0n3**:
According to this:
> Done.
Written 10911001 bytes
(10360192 of which were video data and 550809 audio data)

You've written 10 mb's. It's a straight count of fwrite returns and I cannot imagine why it would be wrong. 
What I can think though is that you checked the wrong file. After the first file is written(out.ogg), 
subsequesnt sessions will not overwrite it( in the cvs version).

Instead they're stored incrementally like this **out.ogg.1, out.ogg.2** etc.

So if you used the command line all the way, check again what files you 
have in the directory you launced the program from(probably your home).
There's also the --overwite option which will not change the name and will erase any previous ones.


@**djsroknrol**:
On a normal gnome session try this :
mplayer -vo x11 out.ogg
and then this
mplayer -vo xv out.ogg

And write back what happened(if it played the video).
Check also if the file "Experience ubuntu.ogg" in the /usr/share/example-content/ folder gives you any of this behavior.
This way we can make sure it's not something related to your configuration.





Did I miss anyone? Just woke up, so I got to go make some coffee...

---

### Post by djsroknrol on 2006-11-14
OK....It seems to be my installation or capture output file...

> mplayer -vo x11 out.ogg
and then this
mplayer -vo xv out.ogg

didn't work, but the "Experience Ubuntu.ogg" file (Which is wonderful by the way...I've never seen it) plays fine.

What would you suggest I do at this point?

---

### Post by iovar on 2006-11-14
Can you make a small capture and send it to me by email or upload it 
somewhere and provide a link?
This way I can check if it is correctly encoded and get an idea about 
where and how this problem manifests, within the encoding loop.

And if possible post here the output of 
```
mplayer -vo x11 -msglevel all=6 out.ogg
```
(it will be quite a lot of output so you might want to make it a txt attachment)

Also, I assume, that this is happening repeatedly, right?

---

### Post by xfile087 on 2006-11-14
1280x1024 won't play back on mine... odd. But the uploaded YouTube version works. 

[http://www.youtube.com/watch?v=endG_5OpBxs]("http://www.youtube.com/watch?v=endG_5OpBxs")

---

### Post by iovar on 2006-11-14
> **xfile087 said:**
> 1280x1024 won't play back on mine... odd. But the uploaded YouTube version works. 

[http://www.youtube.com/watch?v=endG_5OpBxs]("http://www.youtube.com/watch?v=endG_5OpBxs")

Please run the program again with the argument 
-v_quality 32
to set a lower quality than the default 63(full quality)
and test playback again.

It might be an issue with the default values being of the top, since they're 
set to full, something that an encoder is more likely to go on with
than a player. 


Also, **xfile087**, before uploading on youtube you transcoded to avi right?
Is that file playable?


Also, I need someone to give the exact output of this

```
mplayer -vo x11 -msglevel all=6 out.ogg
```

And if possible, post a link to an unmodified file. 

Otherwise there's nothing I can do.

Thanks.

---

### Post by xfile087 on 2006-11-14
Yep I transcoded to avi before posting to avi.

I figure out why 1280x1024 video wouldn't play. It was the default video plugin, once I changed it - all video plays fine. I'm new to Linux so I didn't realize - but i'm learning!

[http://mattdryden.com/output.txt](http://mattdryden.com/output.txt) is the output 
[http://mattdryden.com/output.ogg](http://mattdryden.com/output.ogg) is the video <- at full quality

I don't know if you still need it or if that's what you even wanted but it's there anyway.

---

### Post by iovar on 2006-11-14
Well, since the file is playable ,then no prob.

Thanks for coming back with thorough feedback:KS 

Also, --full-shots --with-shared is no longer needed
(it gets autoenabled under beryl/compiz).


Cool desktop BTW ;) .

---

### Post by Sandman32 on 2006-11-14
Great program!  Thank you very much, I was looking for a way to record ubuntu+beryl to show it to some friends and this worked perfectly!  Once it finishes uploading to google I'll edit in a link.

Edit: Ended up putting it up on youtube.com in an AVI file.  Here is the link [http://www.youtube.com/watch?v=VwzsrpHRxtY](http://www.youtube.com/watch?v=VwzsrpHRxtY)

---

### Post by loell on 2006-11-14
> **Sandman32 said:**
> Great program!  Thank you very much, I was looking for a way to record ubuntu+beryl to show it to some friends and this worked perfectly!  Once it finishes uploading to google I'll edit in a link.

Edit: Ended up putting it up on youtube.com in an AVI file.  Here is the link [http://www.youtube.com/watch?v=VwzsrpHRxtY](http://www.youtube.com/watch?v=VwzsrpHRxtY)

wow, very cool, this is one of smoothest recorded video of beryl  with recordmydesktop.

do you have any command parameters that you've added in recording this demo?

i'll add the video link in the first post :)

---

### Post by Sandman32 on 2006-11-14
I used this command to run start the capturing

[HTML]recordmydesktop --quick-subsampling --zero-compression[/HTML]

Like you said, for maximum performance!:D

---

### Post by loell on 2006-11-14
i see ;)

 its from iovar , he gave it on anther thread i just posted it here :mrgreen: 
 
 i also recorded beryl but iv'e got flickering frames ](*,)

---

### Post by loell on 2006-11-15
:)

another video demonstration [http://www.youtube.com/watch?v=XJWYSfGvITA]("http://www.youtube.com/watch?v=XJWYSfGvITA")
 wine and warcraft III demo

lol, i'd have to set my screen resolution to 640 X 480 just to capture it with recordmydesktop

make sure to view it in full screen :D

---

### Post by djsroknrol on 2006-11-15
I thought about how I could U/L the .ogg files to someplace where I could link to them for inspection, but drew a blank...

So, I tried the next thing I could think of....I pulled the files to another compy on the intranet using Dapper as well and both could be viewed. When I say both, I'm refering to captures done in a Beryl session as well as a Gnome session.

I obviously forked something in my Mplayer to view them in my Gnome session...It's very strange that I can see them in a Beryl session only. Any suggestions?

---

### Post by Sandman32 on 2006-11-16
I think google video will let you upload .ogg videos.  On your other question I'm not sure, hopefully someone else can help.

---

### Post by Sandman32 on 2006-11-18
New video up, I made my desktop cooler so I had to show it off.  I had too much running this time so there is a little more slow down ](*,) 

Enjoy!

[http://www.youtube.com/watch?v=2FZ9N_YEo3g](http://www.youtube.com/watch?v=2FZ9N_YEo3g)

---

### Post by loell on 2006-11-18
ahh beryl 0.1.2 !:KS  cool burn effect :) 
i'll paste it in the first post

---

### Post by loell on 2006-11-20
0.3 was just released, download the deb packages in the first post :KS 

thank you iovar, you've made screencasting in linux a little more easier and  nicer :mrgreen:

---

### Post by evilme on 2006-11-20
Could anyone help me with the sound setup(alsamixer i think)?:confused: 
Is this even possible to record sound directly from my soundcard?
Or had i take a mic?

Video record is just fine, 0.3 runs really smooth with beryl, but i
don't get any sound to work! :evil: 

Any suggestions

---

### Post by iovar on 2006-11-20
It is possible to record directly from the soundcard.

alsamixer may be confusing so you better try with some graphical mixer
(like gnome-mixer and kmix, but I don't know which one is in xfce).

In kmix and alsamixer, the channel is named wave, so it probably is named 
that way in gnome-mixer too. You have to enable the channel and raise the volume, too.


Anyway, the proccess in alsamixer should be simple, too.
All ,you have to do is launch, press **TAB to view the capture channels** and
then **move with the left-right arrows** over the channel named wave.
You **toggle recording on/off by pressing space** and you can **change the volume with the up-down arrows**.

That may not be very helpfull but take a look at the attached video.

---

### Post by evilme on 2006-11-20
Ok, thank you! But...
umm... if i run alsamixer(+TAB) wave is not available...:confused: 
Only Mic,Phone,Aux,Capture and so on. But no Wave is shown...
Maybe my soundcard(VIA8235) don't supported that kind of option.
That meant that my records,with this card, will never have sound! :evil:
Or is only a plugin needed?:-k

---

### Post by loell on 2006-11-20
you can also install gnome-alsamixer

by doing

```
sudo aptitude install gnome-alsamixer
```

run gnome-alsamixer then check rec in the capture slidebar

---

### Post by iovar on 2006-11-20
Uhmm, sorry, I should have known these controls are srecific to the soundcard. But then I've always had sb's so I'm too used to them.

There 's no plugin required, the driver simply shows the available
channels. Have you tried enabling everything?
I would have thought that this is very basic functionality, so it might be
there under some obscure name.
It is more likely that you will get help with this if you post a separate 
thread, though.


Anyway, if all else fails, you can always try with a mic setup...

EDIT: you can try something like this, too:

~$ amixer set Wave 100 cap

and this to see if there's anything named like wave
in your device .

~$ amixer controls |grep name=\'Wave

---

### Post by evilme on 2006-11-20
Yes, i've already try to enable all features...  
Without real success. There is a scratching sound, so  that it is better without.
I also think that wave has to be a basic funktion.
However, i'll try again, tomorrow!
Nevertheless,thank you. Now I know the cause.

BTW: nice idea to record your example.  That's forum-future:mrgreen:

---

### Post by hikaricore on 2006-11-21
looks nice but...

[I][hikaricore@devistate:/media/devistate (151.4 Mb)]$ recordmydesktop
_Only 24bpp color depth mode is currently supported._
[/I]

kinda kills my buzz. hehe.

---

### Post by evilme on 2006-11-21
After playing around with my soundcard about an hour it works now...
I only had to disable '3d' and enable 'mix'](*,) 

Here is a small test
[http://www.youtube.com/watch?v=JEveP2QHZvI]("http://www.youtube.com/watch?v=JEveP2QHZvI")

---

### Post by loell on 2006-11-21
very good choice of music video , it somehow blends with beryl

---

### Post by s_h_a_d_o_w_s on 2006-11-24
Awww man sorry but this looks really cool how do I satisfy libasound2 (.11) in dapper? Thanks I'm eager to show ubuntu to my friends on youtube!

---

### Post by loell on 2006-11-24
are you trying to install the edgy deb package in dapper,
or are you trying to compile it in dapper?

if your trying to compile it
just install libasound2-dev via apt

---

### Post by s_h_a_d_o_w_s on 2006-11-24
Well I was trying it with the edgy.deb but thats a no-go. Installed libasound2-dev but how and where do I compile it? I've never really compiled anything from source. :-)

---

### Post by loell on 2006-11-24
well, i think there are many tutorials for compiling source

like this [Tutorial]("https://help.ubuntu.com/community/CompilingEasyHowTo?highlight=%28compiling%29")

you can download the source code at
[http://recordmydesktop.sourceforge.net]("http://recordmydesktop.sourceforge.net")

---

### Post by s_h_a_d_o_w_s on 2006-11-24
I'm getting a little problem:

I run ./configure:
checking for deflate in -lz... yes
checking for IceOpenConnection in -lICE... yes
checking for SmcOpenConnection in -lSM... yes
checking for XOpenDisplay in -lX11... yes
checking for XShmQueryVersion in -lXext... yes
checking for XFixesQueryExtension in -lXfixes... yes
checking for XDamageQueryExtension in -lXdamage... no
configure: error: Can't find libXdamage


Any ideas?

---

### Post by loell on 2006-11-24
you can search for libraries via
```
apt-cache search name_of_the file
```

from the output you posted, you need 

libxdamage-dev

---

### Post by s_h_a_d_o_w_s on 2006-11-24
checking for bind_textdomain_codeset... yes
checking for msgfmt... /usr/bin/msgfmt
checking for dcgettext... yes
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for PYGTK... configure: error: You need pygtk >=2.4 and the appropriate development headers to proceed
giga@ubuntuzilla:/usr/local/src/gtk-recordMyDesktop-0.3.0r1$ sudo apt-get install pygtk
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package pygtk
giga@ubuntuzilla:/usr/local/src/gtk-recordMyDesktop-0.3.0r1$ sudo apt-get install pygtk-dev
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package pygtk-dev
giga@ubuntuzilla:/usr/local/src/gtk-recordMyDesktop-0.3.0r1$

idk what to do here, its gettin late. Any ideas?

---

### Post by loell on 2006-11-24
search it via apt-cache like the previous, or else you will ask me every dependencies the program will require, and it will be too long ;)

---

### Post by s_h_a_d_o_w_s on 2006-11-24
K,thanks. I got that sucker installed. now to watch some of my own vids.

---

### Post by s_h_a_d_o_w_s on 2006-11-28
[http://www.youtube.com/watch?v=RdziljM2MuI](http://www.youtube.com/watch?v=RdziljM2MuI)

Test video, didn't really have an idea of what to capture. :-)

---

### Post by skyshock21 on 2006-12-01
Meh, it's entirely too choppy with my ATI Radeon 9000 card.  Even with those two options you posted earlierIs there anything else I can try besides those two switches?

---

### Post by loell on 2006-12-01
since 0.3.0 i only used the gui front-end, i do hope iovar can give you more tips ;)

---

### Post by iovar on 2006-12-01
I'm not sure how new/old a radeon 9000 is, but a quick search pointed to 
a 2002 article. There are also many other factors that may influence
performance and for this program ,cpu has at least the same level of
importance with the graphics card. 

So what I mean is that I don't know if you should
be getting any better performance and if the application is misbehaving.

Also note that compiz/beryl recording will probably work only on
recent computers and there's not much to be done on this.

In any case though, the default framerate(15) is a high one and if
for any reason the pc can't take it, the end result will be worse 
than choosing a lower one. So try lowering that until you find 
one that you can record comfortably. 
And then, you can also lower the resolution, a little bit.


Also if remember well, radeons had open-source accel up to 9200
so the driver shouldn't be a problem, right?

Bottomline, sorry but there's no other switch (than --zero-compression
and --quick-subsampling) that can have a real effect.

---

### Post by loell on 2006-12-02
recently tuxmachines featured [Fizzball]("http://www.grubbygames.com/fizzball/") 

i just thought, i'd made a[COLOR="Red"][SIZE="4"] [Fizzball video demo[/SIZE][/COLOR]]("http://video.google.com/videoplay?docid=-5004950449003406369&hl=en") :mrgreen:

---

### Post by Stormx on 2006-12-04
Yo. Really appreciate some help here:

Using all the defaults, the graphics record fine, the sound doesn't. The sound skips and finishes a long way before the video. I've tried a lot of stuff but drawn a blank. Any ideas?

---

### Post by s_h_a_d_o_w_s on 2006-12-08
Bump and how do you get sound working?

---

### Post by loell on 2006-12-08
install and run gnome-alsamixer

check the checkbox "mix"

---

### Post by s_h_a_d_o_w_s on 2006-12-08
Thanks it worked :-)

---

### Post by bg1256 on 2006-12-10
I installed it, and according to the system monitor, it runs.

However, I can't stop it with ctrl-c, and I can't find where it saves the movie - if it's actually recording and saving it at all.

---

### Post by loell on 2006-12-10
it usually saves on your home directory, try the gui front-end if for some odd reason it won't stop by pressing ctrl+c

---

### Post by bg1256 on 2006-12-10
> **loell said:**
> it usually saves on your home directory, try the gui front-end if for some odd reason it won't stop by pressing ctrl+c

I didn't realize there was a gui front end.  How do I run that?  And I did find a short recording in my home folder, but it only recorded about 3-4 seconds worth of material.

edit: well, it seems that it only recorded one video but I attempted to make 3.  Hmm...

---

### Post by loell on 2006-12-10
download and install the gui-front end, attached from the first post.

---

### Post by krypto_wizard on 2006-12-13
Nice find. I was looking for something like this for a while.

Thanks

---

### Post by loell on 2006-12-13
nah.. i could not take the credit ;)  , John has been promoting and working hard to improve this program. he's the man , he's been here helping in this forum too.

---

### Post by josevitor on 2006-12-14
```
 josevitor@Ubuntu:~$ gtk-recordmydesktop
bash: gtk-recordmydesktop: comando não encontrado
josevitor@Ubuntu:~$ gtk-recordMyDesktop
Traceback (most recent call last):
  File "/usr/bin/gtk-recordMyDesktop", line 30, in ?
    from recordMyDesktop import rmdSimple
ImportError: No module named recordMyDesktop
 
```

I'm using Dapper Drake and :
recordmydesktop_0.3.0r2-1_i386.deb
gtk-recordmydesktop_0.3.0r2-1_i386.deb

There is no GUI for Dapper? ](*,)

---

### Post by blonder on 2006-12-14
I have some problems,i hope someone can help me 

> 
marcus@LinuxLaptop:~$ recordmydesktop
Initial recording window is set to:
X:0   Y:0    Width:1920    Height:1200
Adjusted recording window is set to:
X:0   Y:0    Width:1920    Height:1200
Your window manager appears to be beryl


Detected 3d compositing window manager.
Reverting to full screen capture at every frame.
To disable this check run with --no-wm-check
(though that is not advised, since it will probably produce faulty results).

Initializing...
Playback frequency 22050Hz is not available...
Using 44100Hz instead.
Recording on device hw:0,0 is set to:
2 channels at 44100Hz
Capturing!
An error occured while reading sound data:
 Input/output error
An error occured while reading sound data:
 Input/output error


---

### Post by loell on 2006-12-14
does this occur always? anyway,

```
recordmydesktop --nosound
```

will record your desktop without error but without sound.

---

### Post by blonder on 2006-12-14
> 
marcus@LinuxLaptop:~$ recordmydesktop --nosound

        Error parsing arguments.
        Type --help or -h for usage.


Whats wrong ?

---

### Post by loell on 2006-12-14
oops a typo

it should be

```
recordmydesktop --no-sound 
```

---

### Post by blonder on 2006-12-15
Thats it, thanks

but i dont know what is the problem with my sound on my dell inspiron 9400

---

### Post by A_POET on 2006-12-15
Hi I have been recording pretty well, but I get the frame breakups i think which result in these "lines" anytime i do something in beryl (i.e. rotate cube) was wondering if there is something i need to do? im recording a 1280 x 1024 desktop, is there anyway to set it so it records that size but outputs to a smaller resolution?

i tried using those/most tags in this thrad mention previously, same thing...thanks for any insight in advance.

---

### Post by iki488 on 2006-12-15
both links (recordmydesktop and gtk-recordmydesktop) in the first post point to recordmydesktop ! so where can I download the package gtk-recordmydesktop.

---

### Post by loell on 2006-12-15
> **iki488 said:**
> both links (recordmydesktop and gtk-recordmydesktop) in the first post point to recordmydesktop ! so where can I download the package gtk-recordmydesktop.

thanks for notifying, the link was already edited and corrected. :)
you can now download gtk-recordmydesktop from the first post

---

### Post by iki488 on 2006-12-15
> **loell said:**
> thanks for notifying, the link was already edited and corrected. :)
you can now download gtk-recordmydesktop from the first post

thanks ;)

---

### Post by ronniet on 2006-12-18
I'm using Dapper and have installed both **recordmydesktop** and the **gtk-recordmydesktop**

When I run *recordmydesktop --no-sound* it works fine.

When I run *gtk-recordmydesktop* I get:
> Traceback (most recent call last):
  File "/usr/bin/gtk-recordMyDesktop", line 30, in ?
    from recordmydesktop import rmdSimple
ImportError: No module named recordmydesktop

Line 30 in the gtk-recordMyDesktop is:
> from recordMyDesktop import rmdSimple

Any idea whats causing this error? I'd rather use the GUI since i'm a bit of a numpty with the shell... :-? 

**_PS_**: is there an easy way to put like notes onto the videos? Ideally i'd like to create tutorials on video...

---

### Post by loell on 2006-12-18
its an edgy deb package, so it's not compatible with dapper. try video editors like avidemux or jahshaka. if there is afeature for adding notes to a video.

i'll try to make a deb package for dapper maybe tommorow.

---

### Post by loell on 2006-12-18
seems like google video has that caption/note feature

[http://video.google.com/support/bin/answer.py?answer=26577]("http://video.google.com/support/bin/answer.py?answer=26577")

---

### Post by ronniet on 2006-12-19
> **loell said:**
> seems like google video has that caption/note feature
[http://video.google.com/support/bin/answer.py?answer=26577]("http://video.google.com/support/bin/answer.py?answer=26577")

Not exactly what I meant, I was thinking more like little post-it notes on the screen or little speech balloons, but its still a useable solution though so **thank you!**

I could just make a simple **.SRT** file for subtitles to go with my **.AVI** file...  :)

Oh and thanks, that'd be really cool if you could create the Dapper **.DEB** file..  :KS

---

### Post by loell on 2006-12-20
3.1 update, download the dapper deb package from the first post :)

---

### Post by jcroot on 2006-12-23
I tried this and it did work ok, but one question...

Can somebody please tell me any details about this code:

mencoder -idx input.ogg -ovc lavc -oac mp3lame -o output.avi

I think this command is use to convert your out put video file to avi... but where in the code do I have to enter the path of my video?

---

### Post by loell on 2006-12-25
> **jcroot said:**
> I tried this and it did work ok, but one question...

Can somebody please tell me any details about this code:

mencoder -idx input.ogg -ovc lavc -oac mp3lame -o output.avi

I think this command is use to convert your out put video file to avi... but where in the code do I have to enter the path of my video?

its actually
mencoder -idx > path to input.ogg -ovc lavc -oac mp3lame -o > path to output.avii

---

### Post by boolean12 on 2006-12-30
what should i do to make Recordmydesktop capture my Beryl screen!? i can't make it, since i read that it has such ability... but don't know how? :( 
what should i download??

any help would be much appreciated! :)

---

### Post by loell on 2006-12-30
> **boolean12 said:**
> what should i do to make Recordmydesktop capture my Beryl screen!? i can't make it, since i read that it has such ability... but don't know how? :( 
what should i download??

any help would be much appreciated! :)

download and install the deb package from the first post , then just record your beryl screen.

---

### Post by boolean12 on 2007-01-01
i already did that (installed both labeled for EDGY) video recording works for GNOME session, but not for Beryl/Xgl :( don't know...
do i need to set up recorder or what?
please be more accurate! thanks in advance

regards

---

### Post by loell on 2007-01-01
what is the output, of recordmydesktop when you record beryl?

there are no extra steps in recording beryl with recordmydesktop, in my case as well as others who posted screen recordings in this thread, just click the record button in gtk-recordmydesktop, or just invoke recordmydesktop in the command line.

---

### Post by neoaddict on 2007-01-02
Hello everyone,

I can finally get sound and video working in recordmydesktop, but the sound is very... "scratchy".  There's some sort of random sound in the background, but I can record the sound.  Any ideas?

---

### Post by loell on 2007-01-02
i've had a scratchy sound before, just adjust your mixer or specifically use gnome-alsamixer,
i forgot what option i modified to make the scratchy sound go away, but just play with it.

---

### Post by neoaddict on 2007-01-02
OK, I lowered the volume on Capture to 0, and that seems to have worked.
One final problem - the video tends to lag behind the audio for some reason, any ideas?

---

### Post by loell on 2007-01-02
are you using edgy or dapper? edgy's deb package a bit older (0.3.0) but i think 0.3.1 has already fix that problem, i'll try to make deb package for 0.3.1 edgy.

---

### Post by neoaddict on 2007-01-02
Using Edgy.

---

### Post by loell on 2007-01-02
ok i'll try to make a newer edgy package later tonight

---

### Post by boolean12 on 2007-01-03
> **loell said:**
> what is the output, of recordmydesktop when you record beryl?

there are no extra steps in recording beryl with recordmydesktop, in my case as well as others who posted screen recordings in this thread, just click the record button in gtk-recordmydesktop, or just invoke recordmydesktop in the command line.

sorry for late reply, output file is OGG

---

### Post by jcroot on 2007-01-07
I'm using the following code to convert my ogg video to avi but it says: Command not found.

Code:

mencoder -idx /home/supremo/out.ogg -ovc lavc -oac mp3lame -o /home/supremo/output.avi

My video is in my home directory and it's called: out.ogg

---

### Post by loell on 2007-01-08
yeah, i haven't been clear on the video conversion, my apologies ](*,) 

mencoder is part of mplayer , if mplayer is installed then mencoder is installed

you can install mencoder by

```
sudo apt-get install mecoder
```

---

### Post by jcroot on 2007-01-08
> **loell said:**
> yeah, i haven't been clear on the video conversion, my apologies ](*,) 

mencoder is part of mplayer , if mplayer is installed then mencoder is installed

you can install mencoder by

```
sudo apt-get install mecoder
```

Thanks man, I will try this.

---

### Post by jcroot on 2007-01-08
It did work ok, but the code to install is wrong:

Right code: 

sudo apt-get install mencoder

---

### Post by loell on 2007-01-09
> **jcroot said:**
> It did work ok, but the code to install is wrong:

Right code: 

sudo apt-get install mencoder

yup, a typo

---

### Post by Ryan H on 2007-01-13
For some reason my mouse isn't showing up correctly, it just shows a mutilated outline, besides that everything works flawlessly, but the mouse is annoying.

-Ryan H

---

### Post by Adler on 2007-01-19
Hi All,

I'm Googling my little brain out here. I've got RecordMyDesktop going great, can convert the .ogg file to an .avi, and have three YouTube postings showing my Beryl Desktop off. Cool!

Go [Here]("http://www.youtube.com/watch?v=19q2dy42vjI"), [here]("http://www.youtube.com/watch?v=ngJOt6DA6fE"), or [here]("http://www.youtube.com/watch?v=V7OZF__DTgo").

Anybody figured out how to record sound with RecordMyDesktop? 

Adler

---

### Post by neoaddict on 2007-01-19
Get GNOME Alsa Mixer and enable mix I think.

---

### Post by Adler on 2007-01-20
neoaddict,

I am thinking that I need to enter an audio device, per the snapshot below.

[[IMG]http://img264.imageshack.us/img264/9486/beryl168gk.th.png[/IMG]](http://img264.imageshack.us/my.php?image=beryl168gk.png)

Adler

---

### Post by loell on 2007-01-20
iovar pointed it out, that its the default sound device , usually you don't need to adjust it.
what is the output when you enable mix in gnome-alsamixer?

---

### Post by Adler on 2007-01-20
loell,

I've got Gnome Alsa-Mixer

[[img=http://img128.imageshack.us/img128/9523/beryl174bi.png]](http://imageshack.us)

And want to run Streamtuner, with a station playing, then use RecordMyDesktop to record my Beryl Video.

[[IMG]http://img266.imageshack.us/img266/4593/beryl189bb.th.png[/IMG]](http://img266.imageshack.us/my.php?image=beryl189bb.png)

This making sense? Or, what am I missing here?

Adler

---

### Post by loell on 2007-01-20
i see , and it did not capture the sound from streamtuner?

well, i've had that problem too , when i enabled mix , some of the games won't capture the sound.

---

### Post by Adler on 2007-01-20
loell,

My last post didn't show my Gnome Alsa-Mixer. Let's try again --

[[IMG]http://img128.imageshack.us/img128/9523/beryl174bi.th.png[/IMG]](http://img128.imageshack.us/my.php?image=beryl174bi.png) 

I don't see what impact this would have on RecordMyDesktop unless to specify a device.

I have made Vids, while running Streamtuner, with music playing, but the .gg file that I get has no sound.

Thanks for that reply.

Adler

---

### Post by NickPresta on 2007-01-20
I don't know if this is specified anywhere but you should be using Python2.4 with GTK-RMD. I installed the Edgy packages (both RMD and GTK-RMD) and when I ran the GUI, I would get the "cannot find record my desktop module" python error. I assume the binary was compiled with Python2.4.

I had /usr/bin/python linked to /usr/bin/python2.5 so I had to explicitly use /usr/bin/python2.4 /usr/bin/gtk-recordMyDesktop.

Just thought I should point that out.

---

### Post by Adler on 2007-01-20
NickPresta,

I've got no dependency issues, or faults. I can record Beryl Desktops in both RecordMyDesktop, and Istanbul. I get the usual .ogg files, which I convert to .avi to post to YouTube.

Right now I've just used Istanbul, which gave me Audio, as well as, Video. But, the Audio was horrible.

I'm not sure what I did, but I now have audio. LOL! I may have to change the record level in something, but I am making progress.

Do you, or anybody else, have YouTube postings, in orderto give us further clues?

Adler

---

### Post by NickPresta on 2007-01-20
Adler, you're using Python2.5 with gtk-RMD?

---

### Post by Adler on 2007-01-20
NickPresta,

I'm right now installing everything Python per your recommendation. I don't find gtk-RMD in my repositories.

As it stands Istanbul works, but I have to be careful as to the Audio stream. I may have to use some of my .mp3s versus stream audio. **That** may be the problem.

RecordMyDesktop is still an issue. 

Anybody have a good example of success?

BTW, I've got Beryl running so, so, good off my Notebook with the ATI Radeon Xpress 200M card. Cool!

Adler

---

### Post by loell on 2007-01-20
success ? ;)  there are video samples on the first post made by several individuals :D
but the 64th post showed that it can capture sound 

[http://www.youtube.com/watch?v=JEveP2QHZvI]("http://www.youtube.com/watch?v=JEveP2QHZvI")

by evilme

---

### Post by loell on 2007-01-20
[http://video.google.com/videoplay?docid=-5004950449003406369&q=fizzball]("http://video.google.com/videoplay?docid=-5004950449003406369&q=fizzball")
i made this video, but like i said i could not capture the game's sound, so i just played an opera music via xmms in the background and it did captured the sound

---

### Post by Adler on 2007-01-21
loell,

I think the issue here might be trying to record the Desktop, and at the same time Streaming audio. Then combine the two.

I'm now getting some of my best .mp3's together, and then play them in the background.

BTW, one of my Streamtuner channels sounded good, but that was not music.

Adler

---

### Post by Drakx on 2007-02-12
Hmm an intesting tool ill check it out see which i like best xvidcap or this :)

---

### Post by Adler on 2007-02-12
Drakx,

I did manage to get RecordMyDektop going, make sure that you get the GUI. The output is .ogg / Vorbis, which I converted to an .avi file. I used a mencoder command in shell.

I've a bunch of YouTube vids going -- try this [one]("http://www.youtube.com/watch?v=KVmH087F2AY"). Cool!

Adler

---

### Post by loell on 2007-02-12
i like the soundtrack, i have to say, you've got a good taste in music :) 
did you ever solve the problem in recording with streaming audio?

---

### Post by Adler on 2007-02-12
> i like the soundtrack, i have to say, you've got a good taste in music

loell,

I have an amazing collection of .mp3s. I never did sovle the issue of streaming Audio. 

I have streamtuner installed, which offers a great deal of music. I can record to .mp3 what I listen to, but I just dug into my .mpg collection, and not too deeply. I just installed the first of one of my many DVD collections to my HDD, and thought to try it again. It worked.

Back to RecordMyDesktop. As far as I am concerned this is a "Killer App". Cool!

Adler

---

### Post by loell on 2007-02-12
true, this is one of the killer apps, i wonder if ubuntu video team is using this tool.

oh well, i just hope ioviar (recordmydesktop's sole developer) is still checking on this thread ;)

---

### Post by Adler on 2007-02-12
> true, this is one of the killer apps, i wonder if ubuntu video team is using this tool.

oh well, i just hope ioviar (recordmydesktop's sole developer) is still checking on this thread

loell,

Agreed -- Killer App. Makes showing off t0 M$ users that much more fun. Plus, we have all those basic resources -- Firefox (Swiftfox), Evolution, IM, etc.

Adler

---

### Post by bg1256 on 2007-02-16
Thanks for the howto.  It works great.

I'm a little confused as to how to change a video from .ogg to .avi, however.

When and where do I run the command to do this?

Thanks.

---

### Post by Adler on 2007-02-16
bg1256,

Here's the how-to. Firstly you'll need mencoder installed. Get it through Synaptic.

Then in shell run either of these two commands:

For PAL:
Code:
mencoder -o output_file.avi -ovc lavc -lavcopts vbitrate=5000:vhq -ffourcc DX50 -oac pcm -srate 48000 -ofps 25 your_movie.mov

For NTSC:
Code:
mencoder -o output_file.avi -ovc lavc -lavcopts vbitrate=5000:vhq -ffourcc DX50 -oac pcm -srate 48000 -ofps 29.97 your_movie.mov

I assume your Vid is in your Home file. Then where it says "your_movie.mov", change it to /home/whatever/your movie name. Click, and your vid gets converted to an .avi file. It might take a minute or two. The .avi should land in your Home file.

Let us know how it works out.

Adler

---

### Post by Bossieman on 2007-02-23
How can I solve this?


leif@Dimension-5000:~$ mencoder -idx out.ogg -ovc lavc -oac mp3lame -o out.avi
MEncoder 1.0rc1-4.1.2 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Pentium(R) 4 CPU 2.80GHz (Family: 15, Model: 4, Stepping: 1)
CPUflags: Type: 15 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 SSE SSE2

MPlayer was compiled without libmp3lame support.
leif@Dimension-5000:~$

---

### Post by Bossieman on 2007-02-24
Just solved it!
download lame source and configure with
./configure --prefix=/usr

Then reinstall mplayer. Worked for me!

---

### Post by chinaski on 2007-02-25
it's a great software, but there's no much I can do with it because it takes too many resources, so if I want to record a desktop session to illustrate for example how good Linux works and then it takes from 5 to 15 seconds to open a program like Firefox, it's not nice

my machine has a AMD Sempron 3000+ with 768mb ram pc2700 and system resources go up to 100% when recording

---

### Post by Gen2ly on 2007-02-25
I use this to record an online game I tinker about with.  Its Awesome.  I'm not able to to full screen but it's still freakin' AWESOME!  It's nice to finally be able to demonstrate what I'm doing to other ppl.  I imagine it could be very useful for tutorials too.

---

### Post by ronniet on 2007-03-04
Couldn't get the GTK front end to work (error about *egg.trayicon* ??!)but the RecordMyDesktop command works fine in the Konsole...

[http://www.youtube.com/watch?v=be3HRdwQGmM](http://www.youtube.com/watch?v=be3HRdwQGmM)  :popcorn: 

Recorded as you do, then resized and converted to XviD using MEncoder.  :KS

---

### Post by javalang on 2007-03-14
What's the apt repository for recordmydesktop please?
:)

---

### Post by loell on 2007-03-14
> **javalang said:**
> What's the apt repository for recordmydesktop please?
:)

since it was accepted in debian a couple of moths ago , probably theres a repo  in testing/unstable section.  and maybe this is also available fiesty repo

---

### Post by Adler on 2007-03-14
javalang,

If you read the thread here you'll find that you need to get both recordmydesktop, and the gui. I'd compiled both. 

As far as I can tell there is no complete set-up in the repos.

Sorry.

Adler

---

### Post by javalang on 2007-03-16
Hi, i am stuck on:
configure: error: You need pygtk >=2.4 and the appropriate development headers to proceed
I found apt-get cache in this thread but how to use it? How can i fix this?
Thanks.

---

### Post by Adler on 2007-03-16
javalang,

I'm trying to help you along here. Did you try compiling recordmy desktop? If you did you will notice in the command line certain packages that are / might be missing. Then go to Synaptic and pull them down. Then try again.

Some one else might jump in here. Also, remember you want the GUI.

Adler

---

### Post by javalang on 2007-03-16
> **Adler said:**
> javalang,

I'm trying to help you along here. Did you try compiling recordmy desktop? If you did you will notice in the command line certain packages that are / might be missing. Then go to Synaptic and pull them down. Then try again.

Some one else might jump in here. Also, remember you want the GUI.

Adler

This error is from gtk-recordmydesktop when i try to do this [http://recordmydesktop.sourceforge.net/faq.php#frontend2](http://recordmydesktop.sourceforge.net/faq.php#frontend2)  and i've installed the other from .deb.

---

### Post by loell on 2007-03-16
you must have     python-gtk2-dev installed

also if your trying to compile the current gtk-recordmydesktop you must also compile recordmydesktop command line tool.

---

### Post by javalang on 2007-03-16
> **loell said:**
> you must have     python-gtk2-dev installed

also if your trying to compile the current gtk-recordmydesktop you must also compile recordmydesktop command line tool.

Thanks, it works great.

---

### Post by Adler on 2007-03-16
loell,

Just to help javalang -- go here -- [http://linux.softpedia.com/get/Multimedia/Video/recordMyDesktop-15059.shtml](http://linux.softpedia.com/get/Multimedia/Video/recordMyDesktop-15059.shtml). Follow the instructions. Make sure that you have all the dependencies installed. Then do the ./configure / make / make install and be sure that you've done the command line to go to where you have put the downloaded package. 

You can launch recordmydesktop" from shell with sudo recordmydesktop, but you really want the gtk-recordmydesktop @ [http://packages.debian.org/cgi-bin/download.pl?arch=all&file=pool%2Fmain%2Fg%2Fgtk-recordmydesktop%2Fgtk-recordmydesktop_0.3.3-1_all.deb&md5sum=f229d58726a3f7c5e7b34b28cc55763e&arch=all&type=main](http://packages.debian.org/cgi-bin/download.pl?arch=all&file=pool%2Fmain%2Fg%2Fgtk-recordmydesktop%2Fgtk-recordmydesktop_0.3.3-1_all.deb&md5sum=f229d58726a3f7c5e7b34b28cc55763e&arch=all&type=main)

Then, you should get something like this --

[[IMG]http://img261.imageshack.us/img261/210/snapshot9wv4.th.png[/IMG]](http://img261.imageshack.us/my.php?image=snapshot9wv4.png)

I hope that this helps with this great app.

Adler

---

### Post by javalang on 2007-03-17
> **Adler said:**
> loell,

Just to help javalang -- go here -- [http://linux.softpedia.com/get/Multimedia/Video/recordMyDesktop-15059.shtml](http://linux.softpedia.com/get/Multimedia/Video/recordMyDesktop-15059.shtml). Follow the instructions. Make sure that you have all the dependencies installed. Then do the ./configure / make / make install and be sure that you've done the command line to go to where you have put the downloaded package. 

You can launch recordmydesktop" from shell with sudo recordmydesktop, but you really want the gtk-recordmydesktop @ [http://packages.debian.org/cgi-bin/download.pl?arch=all&file=pool%2Fmain%2Fg%2Fgtk-recordmydesktop%2Fgtk-recordmydesktop_0.3.3-1_all.deb&md5sum=f229d58726a3f7c5e7b34b28cc55763e&arch=all&type=main](http://packages.debian.org/cgi-bin/download.pl?arch=all&file=pool%2Fmain%2Fg%2Fgtk-recordmydesktop%2Fgtk-recordmydesktop_0.3.3-1_all.deb&md5sum=f229d58726a3f7c5e7b34b28cc55763e&arch=all&type=main)

Then, you should get something like this --

[[IMG]http://img261.imageshack.us/img261/210/snapshot9wv4.th.png[/IMG]](http://img261.imageshack.us/my.php?image=snapshot9wv4.png)

I hope that this helps with this great app.

Adler

It is working fine now, just like your picture, thanks to all.

---

### Post by Adler on 2007-03-17
javalang,

I'm glad to have helped.

Adler

---

### Post by Schalken on 2007-03-25
This app is great. It has a working GUI and records smooth crisp videos, unlike Istanbul.

The only problem is I can't get it to record sound (sound playing in apps, not a mic). The advanced options has the sound device set to "hw:0,0", is this correct?

Also, can it record to another format such as MPG, WMV, or MOV providing the right encoders are installed, or is the quality loss of transcoding from OGG to one of these neglectable?

---

### Post by loell on 2007-03-25
install and run gnome-alsamixer

check the checkbox mix,



afaik with transcoding, none or if there is a loss of quality its barely noticeable. 
oh it will never record to a format that is not open, the dev answered that question when i asked him a couple of months ago :)

---

### Post by Schalken on 2007-03-25
That did it, cheers! But why isn't that option enabled by default?

---

### Post by loell on 2007-03-25
> **Schalken said:**
> That did it, cheers! But why isn't that option enabled by default?

sound source hw0:0 is the default, its the  system that didn't make the mixing as default.

---

### Post by Schalken on 2007-03-25
Yeah, thats what I mean. Why isn't the "Mix" checkbox on by deafault?

---

### Post by loell on 2007-03-25
because its not a good idea  to enable mixing by default in ubuntu.  many user don't want to record sound mix with other sound, so its best to off it by default.

---

### Post by hall on 2007-03-25
Hey, does anyone know how to recover a session given a crash? 

I have the directory 'rMD-session-$SESSION_ID'  containing audio.pcm and img.out

---

### Post by Adler on 2007-03-26
loell,

What I found was that, if I ran an .mp3 in the background, versus streaming audio I could get both Vid and Audio. The Beryl Desktop off my Notebook works for me.

Now, since I run several of the cooler Beryl options -- like Snow, and Fire, I'm having a few problems. It seems that the frame capture rate isn't fast enough. No big deal. I run the ATI Radeon Xpress 200M card, and had to compile the drives. 

Many haven't remembered that the resuled file output is in the .ogg / Vorbis format.

To convert it use this to go to .avi -

Here's the how-to. Firstly you'll need mencoder installed. Get it through Synaptic.

Then in shell run either of these two commands:

For PAL:
Code:
mencoder -o output_file.avi -ovc lavc -lavcopts vbitrate=5000:vhq -ffourcc DX50 -oac pcm -srate 48000 -ofps 25 your_movie.mov

For NTSC:
Code:
mencoder -o output_file.avi -ovc lavc -lavcopts vbitrate=5000:vhq -ffourcc DX50 -oac pcm -srate 48000 -ofps 29.97 your_movie.mov

I assume your Vid is in your Home file. Then where it says "your_movie.mov", change it to /home/whatever/your movie name. Click, and your vid gets converted to an .avi file. It might take a minute or two. The .avi should land in your Home file.

Let us know how it works out.

The above is a direct rip-off of another posting here regarding the conversion process.

I'm hoping this helps every one with this great app!

Adler

---

### Post by dbbolton on 2007-04-01
i skimmed through and didn't see anything about this, but my out put just shows the cursor and a black background.

---

### Post by loell on 2007-04-02
what were you trying to do?

 i've also had this symptoms when i tried recording warcraft.

---

### Post by kr0n1x on 2007-04-02
hi, i need the command to convert the out.ogg to out.avi but WITHOT any sound (the *.ogg file haven't audio)

in first post, there is this command:
```
mencoder -idx input.ogg -ovc lavc -oac mp3lame -o output.avi
```

what command i need to convert simply the video only? (because the audio doesn't exist)

thanks, bye :)

(sorry my bad english)

---

### Post by gtcoffee on 2007-04-03
hi...
i have my music on while i recording, 
however the out.ogg doesnt have sound..
why ???

thanks !!

---

### Post by shavenlunatic on 2007-04-07
thanksd for line on how to convert from ogg, i kept getting errors :)

---

### Post by MyR on 2007-04-11
problem: whenever i try to open the created ogg or avi the player windows opens and immediately closes.

sample files:
[http://unifyingtheory.net/out.ogg](http://unifyingtheory.net/out.ogg)
[http://unifyingtheory.net/out.avi](http://unifyingtheory.net/out.avi)

I noticed someone else had this problem and was able to fix it, mentioning something about a video plugin.

Any ideas? thanks.

---

### Post by loell on 2007-04-13
what are you trying to record, desktop effects, plain desktop, or fullscreen games?

---

### Post by MyR on 2007-04-13
i want to desktop effects. everything that appears on the screen.
sorry my website is down for some reason :/ i can send the files via email if you want to have a look.

---

### Post by loell on 2007-04-13
what is the size of the ogg file after recording it?

---

### Post by MyR on 2007-04-16
0.6mb after recording a couple seconds

---

### Post by loell on 2007-04-17
strange,

can you do a recording, by just using the command line "recordmydesktop"

and post the whole text output of the command here.

---

### Post by MyR on 2007-04-19
Initial recording window is set to:
X:0   Y:0    Width:1920    Height:1200
Adjusted recording window is set to:
X:0   Y:0    Width:1920    Height:1200
Your window manager appears to be beryl


Detected 3d compositing window manager.
Reverting to full screen capture at every frame.
To disable this check run with --no-wm-check
(though that is not advised, since it will probably produce faulty results).

Initializing...
Recording on device hw:0,0 is set to:
2 channels at 22050Hz
Capturing!
Saved 53 frames in a total of 95 requests
Shutting down.....
Encoding started!
This may take several minutes.
Pressing Ctrl-C will cancel the procedure (resuming will not be possible, but
any portion of the video, which is already encoded won't be deleted).
Please wait...
[96%] 
Encoding finished!
Wait a moment please...
   
Done.
Written 961557 bytes
(871761 of which were video data and 89796 audio data)

Cleanning up cache...
Done!!!
Goodbye!

here is some of what totem spits out after it crashes trying the run the ogg:
0xffffe410 in __kernel_vsyscall ()
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb72b4a8c in pthread_cond_timedwait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb744f58e in xine_play () from /usr/lib/libxine.so.1
#3  0x00000000 in ?? ()

Thread 9 (Thread -1243198560 (LWP 29474)):
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb72b4a8c in pthread_cond_timedwait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#2  0xb7452dff in _x_metronom_init () from /usr/lib/libxine.so.1
No symbol table info available.
#3  0xb5e6445c in ?? ()
No symbol table info available.
#4  0xb5e64464 in ?? ()
No symbol table info available.
#5  0x0836cac8 in ?? ()
No symbol table info available.
#6  0xb5e6445c in ?? ()
No symbol table info available.
#7  0x00000013 in ?? ()
No symbol table info available.
#8  0x00000000 in ?? ()
No symbol table info available.

Thread 8 (Thread -1259627616 (LWP 29475)):
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb72b7bf6 in __nanosleep_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#2  0xb747b842 in xine_usec_sleep () from /usr/lib/libxine.so.1
No symbol table info available.

Thread 7 (Thread -1268057184 (LWP 29478)):
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb707a803 in poll () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#2  0xb46b519f in ?? ()
   from /usr/lib/xine/plugins/1.1.2/xineplug_ao_out_alsa.so
No symbol table info available.
#3  0xb46af3b8 in ?? ()
No symbol table info available.
#4  0x00000001 in ?? ()
No symbol table info available.
#5  0x0000014d in ?? ()
No symbol table info available.
#6  0x00000000 in ?? ()
No symbol table info available.

Thread 6 (Thread -1276720224 (LWP 29479)):
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb707a803 in poll () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#2  0xb6f43cb8 in snd_pcm_wait_nocheck () from /usr/lib/libasound.so.2
No symbol table info available.
#3  0xb6f43e99 in snd_pcm_wait () from /usr/lib/libasound.so.2
No symbol table info available.
#4  0xb46b585d in ?? ()
   from /usr/lib/xine/plugins/1.1.2/xineplug_ao_out_alsa.so
No symbol table info available.
#5  0x089cd158 in ?? ()
No symbol table info available.
#6  0x000f4240 in ?? ()
No symbol table info available.
#7  0x0000006c in ?? ()
No symbol table info available.
#8  0xb6f06050 in ?? () from /usr/lib/libasound.so.2
No symbol table info available.
#9  0xb6fb6890 in ?? ()
No symbol table info available.
#10 0xb7f10ff4 in ?? () from /lib/ld-linux.so.2
No symbol table info available.
#11 0x087fa7e0 in ?? ()
No symbol table info available.
#12 0x00000003 in ?? ()
No symbol table info available.
#13 0x46270c92 in ?? ()
No symbol table info available.
#14 0x064c03c8 in ?? ()
No symbol table info available.
#15 0x00000000 in ?? ()
No symbol table info available.

Thread 5 (Thread -1289213024 (LWP 29480)):
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb72b834b in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#2  0xb7e6a1b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
No symbol table info available.
#3  <signal handler called>
No symbol table info available.
#4  0xb702537c in memcpy () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#5  0xb122812c in ?? ()
   from /usr/lib/xine/plugins/1.1.2/xineplug_decode_theora.so
No symbol table info available.
#6  0xb5630d80 in ?? ()
No symbol table info available.
#7  0xae6679e0 in ?? ()
No symbol table info available.
#8  0x000003c0 in ?? ()
No symbol table info available.
#9  0x9999999a in ?? ()
No symbol table info available.
#10 0x3ff99999 in ?? ()
No symbol table info available.
#11 0x32315659 in ?? ()
No symbol table info available.
#12 0x00000003 in ?? ()
No symbol table info available.
#13 0x00000000 in ?? ()
No symbol table info available.

Thread 4 (Thread -1299493984 (LWP 29481)):
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb72b4a8c in pthread_cond_timedwait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#2  0xb7461228 in _x_ao_channels2mode () from /usr/lib/libxine.so.1
No symbol table info available.

Thread 3 (Thread -1307886688 (LWP 29482)):
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb72b4816 in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#2  0xb746616c in xine_event_wait () from /usr/lib/libxine.so.1
No symbol table info available.
#3  0x08963e50 in ?? ()
No symbol table info available.
#4  0x00000001 in ?? ()
No symbol table info available.
#5  0xb74661f4 in xine_event_wait () from /usr/lib/libxine.so.1
No symbol table info available.
#6  0x00000000 in ?? ()
No symbol table info available.

Thread 2 (Thread -1382311008 (LWP 29485)):
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb72b7bf6 in __nanosleep_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#2  0xb747b842 in xine_usec_sleep () from /usr/lib/libxine.so.1
No symbol table info available.
#3  0xad9b9434 in ?? ()
No symbol table info available.
#4  0x00000000 in ?? ()
No symbol table info available.

Thread 1 (Thread -1226217808 (LWP 29466)):
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb72b4a8c in pthread_cond_timedwait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#2  0xb744f58e in xine_play () from /usr/lib/libxine.so.1
No symbol table info available.
#3  0x00000000 in ?? ()
No symbol table info available.
#0  0xffffe410 in __kernel_vsyscall ()

---

### Post by PaulFXH on 2007-04-23
I was intrigued by the eulogies being poured on this app throughout this thread and decided to try it on my HP Pavilion dv1000 laptop running Edgy with Beryl (Intel 945GM integrated graphics card).

No problem with the install (both command line and GUI versions) and after recording I get an .ogg file which seems the right size.
Then I convert this to an .avi file (5.2MB for 39 seconds) using mencoder. So far, so good.

Then I try to play it in Totem and get 39 seconds of a black screen. Hmmm.....
Same thing in mplayer and in WMP10 (sent the .avi over to my WinXP machine).

Perhaps I'm missing some codecs or something.
Can anybody advise?

Thanks
Paul

---

### Post by loell on 2007-04-23
maybe somehow a wrong DISPLAY is recorded its usually set to default by the application, i have no experience in setting DISPLAY ID. perhaps you can get more reliable answer in [http://sourceforge.net/projects/recordmydesktop/]("http://sourceforge.net/projects/recordmydesktop/")

in forums/help section.

---

### Post by PaulFXH on 2007-04-23
@loell
Thanks for the quick reply.
I had a look through the website you mentioned but did not find anything that was at all relevant.
Perhaps I will post to that forum and see if the developer can help me.

Thanks again
Paul

---

### Post by PaulFXH on 2007-04-23
I've just tried to run the .avi file I got after converting the .ogg file recorded by recordMyDesktop using Totem but from a terminal and get the following messages which seem to be of relevance to my problem. Here they are:
> ** Message: don't know how to handle video/mpeg, mpegversion=(int)4, framerate=(fraction)15/1, width=(int)1280, height=(int)768
** Message: don't know how to handle video/mpeg, mpegversion=(int)4, framerate=(fraction)15/1, width=(int)1280, height=(int)768
The first of these two identical messages was received before the .avi file was run and the second showed up just after it finished. Only a black screen was visible throughout, however.
Could it be that this app has a problem with a widescreen output?

Perhaps it might be useful also to post the terminal output when I run recordMyDesktop from the terminal which is as follows:
> Initial recording window is set to:
X:0   Y:0    Width:1280    Height:768
Adjusted recording window is set to:
X:0   Y:0    Width:1280    Height:768
Your window manager appears to be beryl


Detected 3d compositing window manager.
Reverting to full screen capture at every frame.
To disable this check run with --no-wm-check
(though that is not advised, since it will probably produce faulty results).

Initializing...
Buffer size adjusted to 4096 from 4096 frames.
Opened PCM device hw:0,0
Playback frequency 22050Hz is not available...
Using 48000Hz instead.
Recording on device hw:0,0 is set to:
2 channels at 48000Hz
Capturing!
Saved 177 frames in a total of 182 requests
Shutting down.....
Encoding started!
This may take several minutes.
Pressing Ctrl-C will cancel the procedure (resuming will not be possible, but
any portion of the video, which is already encoded won't be deleted).
Please wait...
[100%] 
Encoding finished!
Wait a moment please...
   
Done.
Written 1569661 bytes
(896366 of which were video data and 673295 audio data)

Cleanning up cache...
Done!!!
Goodbye!


Thanks for any suggestions
Paul

---

### Post by pepotiger on 2007-04-23
thnx mate

---

### Post by loell on 2007-04-23
> **PaulFXH said:**
> I've just tried to run the .avi file I got after converting the .ogg file recorded by recordMyDesktop using Totem but from a terminal and get the following messages which seem to be of relevance to my problem. Here they are:

The first of these two identical messages was received before the .avi file was run and the second showed up just after it finished. Only a black screen was visible throughout, however.
Could it be that this app has a problem with a widescreen output?

Perhaps it might be useful also to post the terminal output when I run recordMyDesktop from the terminal which is as follows:


Thanks for any suggestions
Paul

i'm just probably  hitting in the dark here, in gtk-recordmydesktop can you limit your screen area of recording? say x:500 y:500 and try to play it. perhaps this could be a limitation of players in playing large resolution.

---

### Post by PaulFXH on 2007-04-23
@loell
Thanks for the suggestion however, it didn't seem to improve matters. When I tried to run the resultng .avi file in Totem (from a terminal), I got an almost identical message to the last time except with reference to the smaller screen size. So, there's something else amiss. Codecs?

> ** Message: don't know how to handle video/mpeg, mpegversion=(int)4, framerate=(fraction)15/1, width=(int)464, height=(int)512
** Message: don't know how to handle video/mpeg, mpegversion=(int)4, framerate=(fraction)15/1, width=(int)464, height=(int)512

---

### Post by i386DX on 2007-04-23
When I disable 'encode on the fly' the sound and video aren't in sync (sound comes after). With 'encode on the fly' enabled its perfectly in sync, but the video 'hangs' sometimes due the massive load on my cpu.

How can I make the sound an video perfectly in sync with disabled 'encode on the fly?'

---

### Post by PaulFXH on 2007-04-23
Well, the problem isn't resolved but there's a light at the end of the tunnel.
I installed a bunch of codecs relevant to Totem from [here]("https://help.ubuntu.com/community/RestrictedFormats") using this code:
```
sudo apt-get install gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gxine libxine-main1 libxine-extracodecs ogle ogle-gui
```
Now when I run the already recorded .avi files in Totem, no error message appears. However, the screen still remains largely black except for about 250 milliseconds (estimated:) )at the start and end of the file when a very nice clear image of my desktop is visible.
So, it does appear to be a codec problem. I'll google around to try to totally resolve this before posting back.

---

### Post by MyR on 2007-04-23
apparently i can sucessfully play my videos using ```
mplayer -vo x11 out.ogg
``` i set the video driver for mplayer to gl and now they play with mplayer without using command line. awesome. problem solved!

as a side note, the oggs created by recordmydesktop dont validate:
:~$ oggz-validate out.ogg
out.ogg: Error:
serialno 0852657047: missing *** eos

~$ oggz-validate out.ogg.1
out.ogg.1: Error:
00:00:00.203: serialno 0975404694: Packet out of order (previous 00:00:01.733)
00:00:00.412: serialno 0975404694: Packet out of order (previous 00:00:04.200)
00:00:04.498: serialno 0975404694: Packet out of order (previous 00:00:04.866)
00:00:04.731: serialno 0975404694: Packet out of order (previous 00:00:06.266)
serialno 1583551684: missing *** eos
serialno 0975404694: missing *** eos

---

### Post by loell on 2007-04-23
thanks for sharing, others might run into this problem.

---

### Post by ImpelGD on 2007-04-24
Thanks for posting the info in this topic - recorded for the first time yesterday. :)

Is it possible to have the output scaled down, resulting in a smaller ogg file by any chance?

---

### Post by loell on 2007-04-24
you can lower the video quality , and you can also specify your screen area for recording. converting it to avi will also reduce the file size.

---

### Post by ImpelGD on 2007-04-24
Ok, thanks. Scaling would be a brilliant addition. Does anyone know of a video processing utility which can scale video down?

---

### Post by PaulFXH on 2007-04-25
I've made quite some progress in getting recordMyDesktop to work on my computer (HP Pavilion dv1000 laptop---integrated Intel 945GM graphics card) since my last post a couple of days ago.
However, things are still not quite perfect. So, I would appreciate any comments or guidance to move things up to 100%.

Here's what's good:
1) If I run mplayer from a terminal, although an enormous error message is given, the video (unconverted .ogg file) will play in full and looks great. Note that this only occurrs if the screen size (or the video/sound quality) are reduced. If I run mplayer without having taken these precautions before recording the video, mplayer just opens and immediately shuts down without showing anything. An error message is printed complaining about insufficient resources.
The error message I get is as follows:

> MPlayer 2:0.99+1.0pre8-0ubuntu8 (C) 2000-2006 MPlayer Team 
CPU: Intel(R) Celeron(R) M CPU 410 @ 1.46GHz (Family: 6, Model: 14, Stepping: 8) 
CPUflags: MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1 
Compiled with runtime CPU detection. 
 
 
Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied 
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts. 
Opening joystick device /dev/input/js0 
Can't open joystick device /dev/input/js0: No such file or directory 
Can't init input joystick 
Setting up LIRC support... 
mplayer: could not connect to socket 
mplayer: No such file or directory 
Failed to open LIRC support. 
You will not be able to use your remote control. 
 
Playing out.ogg.13. 
[Ogg] stream 0: video (Theora v3.2.0), -vid 0 
[Ogg] stream 1: audio (Vorbis), -aid 0 
Ogg file format detected. 
VIDEO: [theo] 832x592 24bpp 15.000 fps 0.0 kbps ( 0.0 kbyte/s) 
========================================================================== 
Opening audio decoder: [libvorbis] Ogg/Vorbis audio decoder 
AUDIO: 22050 Hz, 1 ch, s16le, 90.0 kbit/25.51% (ratio: 11248->44100) 
Selected audio codec: [vorbis] afm: libvorbis (OggVorbis Audio Decoder) 
========================================================================== 
open: No such file or directory 
Couldn't open: /dev/mga_vid 
open: No such file or directory 
Couldn't open: /dev/mga_vid 
[VO_TDFXFB] Can't open /dev/fb0: Permission denied. 
[VO_3DFX] Unable to open /dev/3dfx. 
========================================================================== 
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family 
[theora @ 0x87dc78c]Missing extradata! 
Could not open codec. 
VDecoder init failed :( 
Opening video decoder: [theora] Theora/VP3 
VDec: vo config request - 832 x 592 (preferred colorspace: Planar YV12) 
VDec: using Planar YV12 as output csp (no 0) 
Movie-Aspect is 1.41:1 - prescaling to correct movie aspect. 
VO: [xv] 832x592 => 832x592 Planar YV12  
Selected video codec: [theora] vfm: theora (Theora (free, reworked VP3)) 
========================================================================== 
alsa-init: using device default 
alsa: 48000 Hz/1 channels/2 bpf/32768 bytes buffer/Signed 16 bit Little Endian 
AO: [alsa] 48000Hz 1ch s16le (2 bytes per sample) 
Starting playback... 
A: 5.6 V: 3.5 A-V: 2.104 ct: 0.043 53/ 53 96% 45% 28.2% 50 0  
 
************************************************ 
**** Your system is too SLOW to play this! **** 
************************************************ 
 
Possible reasons, problems, workarounds: 
- Most common: broken/buggy _audio_ driver 
- Try -ao sdl or use the OSS emulation of ALSA. 
- Experiment with different values for -autosync, 30 is a good start. 
- Slow video output 
- Try a different -vo driver (-vo help for a list) or try -framedrop! 
- Slow CPU 
- Don't try to play a big DVD/DivX on a slow CPU! Try some of the lavdopts, 
e.g. -vfm ffmpeg -lavdopts lowres=1:fast:skiploopfilter=all. 
- Broken file 
-MPlayer 2:0.99+1.0pre8-0ubuntu8 (C) 2000-2006 MPlayer Team 
CPU: Intel(R) Celeron(R) M CPU 410 @ 1.46GHz (Family: 6, Model: 14, Stepping: 8) 
CPUflags: MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1 
Compiled with runtime CPU detection. 
 
 
Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied 
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts. 
Opening joystick device /dev/input/js0 
Can't open joystick device /dev/input/js0: No such file or directory 
Can't init input joystick 
Setting up LIRC support... 
mplayer: could not connect to socket 
mplayer: No such file or directory 
Failed to open LIRC support. 
You will not be able to use your remote control. 
 
Playing out.ogg.13. 
[Ogg] stream 0: video (Theora v3.2.0), -vid 0 
[Ogg] stream 1: audio (Vorbis), -aid 0 
Ogg file format detected. 
VIDEO: [theo] 832x592 24bpp 15.000 fps 0.0 kbps ( 0.0 kbyte/s) 
========================================================================== 
Opening audio decoder: [libvorbis] Ogg/Vorbis audio decoder 
AUDIO: 22050 Hz, 1 ch, s16le, 90.0 kbit/25.51% (ratio: 11248->44100) 
Selected audio codec: [vorbis] afm: libvorbis (OggVorbis Audio Decoder) 
========================================================================== 
open: No such file or directory 
Couldn't open: /dev/mga_vid 
open: No such file or directory 
Couldn't open: /dev/mga_vid 
[VO_TDFXFB] Can't open /dev/fb0: Permission denied. 
[VO_3DFX] Unable to open /dev/3dfx. 
========================================================================== 
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family 
[theora @ 0x87dc78c]Missing extradata! 
Could not open codec. 
VDecoder init failed :( 
Opening video decoder: [theora] Theora/VP3 
VDec: vo config request - 832 x 592 (preferred colorspace: Planar YV12) 
VDec: using Planar YV12 as output csp (no 0) 
Movie-Aspect is 1.41:1 - prescaling to correct movie aspect. 
VO: [xv] 832x592 => 832x592 Planar YV12  
Selected video codec: [theora] vfm: theora (Theora (free, reworked VP3)) 
========================================================================== 
alsa-init: using device default 
alsa: 48000 Hz/1 channels/2 bpf/32768 bytes buffer/Signed 16 bit Little Endian 
AO: [alsa] 48000Hz 1ch s16le (2 bytes per sample) 
Starting playback... 
A: 5.6 V: 3.5 A-V: 2.104 ct: 0.043 53/ 53 96% 45% 28.2% 50 0  
 
************************************************ 
**** Your system is too SLOW to play this! **** 
************************************************ 
 
Possible reasons, problems, workarounds: 
- Most common: broken/buggy _audio_ driver 
- Try -ao sdl or use the OSS emulation of ALSA. 
- Experiment with different values for -autosync, 30 is a good start. 
- Slow video output 
- Try a different -vo driver (-vo help for a list) or try -framedrop! 
- Slow CPU 
- Don't try to play a big DVD/DivX on a slow CPU! Try some of the lavdopts, 
e.g. -vfm ffmpeg -lavdopts lowres=1:fast:skiploopfilter=all. 
- Broken file 
- Try various combinations of -nobps -ni -forceidx -mc 0. 
- Slow media (NFS/SMB mounts, DVD, VCD etc) 
- Try -cache 8192. 
- Are you using -cache to play a non-interleaved AVI file? 
- Try -nocache. 
Read DOCS/HTML/en/video.html for tuning/speedup tips. 
If none of this helps you, read DOCS/HTML/en/bugreports.html. 
 
A: 37.2 V: 37.9 A-V: -0.634 ct: 2.036 569/569 82% 21% 16.7% 248 0  
alsa-uninit: pcm closed 
 
Exiting... (End of file) 
 

Here's what's not so good:
1) If I run mplayer from a GUI, it gives the following error and then shuts down:
> Error opening/initializing the selected video_out (-vo) device.
2) Running Totem from either the GUI or a terminal, gives normally just a black screen with brief snatches of the desktop visible momentarily at both the beginning and end of the video. However, if I move the Totem window and wobble (Beryl) it, the video sometimes actually shows up as it should.

It appears, therefore, as if this laptop (1.46 GHz CPU, 512 MB RAM) is not quite up to the job of showing these videos. Why, however, does mplayer work better than Totem?
Also, is there anything I can do to allay the negative influences of the laptops lack of resources?

Thanks
Paul

---

### Post by loell on 2007-04-25
> **PaulFXH said:**
> I've made quite some progress in getting recordMyDesktop to work on my computer (HP Pavilion dv1000 laptop---integrated Intel 945GM graphics card) since my last post a couple of days ago.
However, things are still not quite perfect. So, I would appreciate any comments or guidance to move things up to 100%.

Here's what's good:
1) If I run mplayer from a terminal, although an enormous error message is given, the video (unconverted .ogg file) will play in full and looks great. Note that this only occurrs if the screen size (or the video/sound quality) are reduced. If I run mplayer without having taken these precautions before recording the video, mplayer just opens and immediately shuts down without showing anything. An error message is printed complaining about insufficient resources.
The error message I get is as follows:



Here's what's not so good:
1) If I run mplayer from a GUI, it gives the following error and then shuts down:

2) Running Totem from either the GUI or a terminal, gives normally just a black screen with brief snatches of the desktop visible momentarily at both the beginning and end of the video. However, if I move the Totem window and wobble (Beryl) it, the video sometimes actually shows up as it should.

It appears, therefore, as if this laptop (1.46 GHz CPU, 512 MB RAM) is not quite up to the job of showing these videos. Why, however, does mplayer work better than Totem?
Also, is there anything I can do to allay the negative influences of the laptops lack of resources?

Thanks
Paul

yeah, i feel the same about mplayer being better than totem, theres not much we can do about it, you can try totem-xine or gnome-mplayer too if you ever want similar user interface with totem.

i think your laptop is more than adequate for a dekstop, but it only slows down because you're using beryl.

---

### Post by PaulFXH on 2007-04-25
> but it only slows down because you're using bery
Problem is, most of what I'd like to record on my desktop involves Beryl.
But, such is life!
When I get back to my home base in 6 weeks time I'll be able to try out this app on a much more powerful desktop. That'll be interesting.
BTW, any views on why mplayer runs fine (other than grumbling a bit) from a terminal but gives a fatal error message from the GUI?

---

### Post by PaulFXH on 2007-04-26
@loell
More progress. The developer (John) suggested I try this command in mplayer
```
mplayer -vo x11 out.ogg
```
which asks mplayer to run with an x11 rather than an Xv backend.
As a result, now mplayer can play fullscreen videos of my desktop without problems.
Additionally, sound works perfectly for me.

So, if only I could configure mplayer (and Totem) to run with an x11 backend, I could probably run these .ogg files straight from the GUIs instead of having to go through the terminal.
Any idea how to do this?

Thanks
Paul

---

### Post by MyR on 2007-04-27
> **PaulFXH said:**
> 
So, if only I could configure mplayer (and Totem) to run with an x11 backend, I could probably run these .ogg files straight from the GUIs instead of having to go through the terminal.
Any idea how to do this?

mplayer is easy to configure:
right click on it somewhere and choose preferences. under the video tab you can choose x11. restart it for chagnes to take effect.
not sure about totem.

---

### Post by charly4711 on 2007-04-27
@ImpelGD: xvidcap can scale down your input

---

### Post by charly4711 on 2007-04-27
but that aside, you could always use mencoder or ffmpeg to scale down your video dimensions in a post-processing step.

---

### Post by PaulFXH on 2007-04-27
@MyR
Thanks for your tip on configuring mplayer.
You're right, that was easy, and now I can start mplayer from the GUI.
However, when I start a fullscreen desktop video (which apparently doesn't work with the Xv extension) from the terminal it still doesn't run. I need to use the "mplayer -vo x11 file.name" command to get it to work.
This is surprising as I thought configuring it to use x11 as you had pointed out would be sufficient for terminal starts as well.
Also, running from a GUI, I get a "Could not start codec" error, although it still plays.
In terminal mode, the error turns out to be
> Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
[theora @ 0x87dc78c]Missing extradata!
Could not open codec.
VDecoder init failed :(

I tried installing some theora and libavcodec stuff from Synaptic, but I still get this error.
Any ideas how to eliminate this?
Thanks
Paul

---

### Post by MyR on 2007-04-28
it doesnt seem like there's much to be done about the «could not open codec» error. [http://www.mail-archive.com/debian-bugs-dist@lists.debian.org/msg338746.html](http://www.mail-archive.com/debian-bugs-dist@lists.debian.org/msg338746.html)

could try compiling mplayer from source after installing the theora lib.

---

### Post by PaulFXH on 2007-04-28
@MyR
Thanks again. That's a pity about that bug.
However, I notice in post #191 that you say
> i set the video driver for mplayer to gl and now they play with mplayer without using command line. awesome. problem solved!
Can I assume that using this driver, rather than the x11 I am currently using I can both record fullscreen videos of my desktop WITHOUT seeing that error message pop up?
If so, this will totally solve my problem.

Incidentally, although this thread is now very long and has been going for at least 6 months, there has been relatively little discussion about playing the videos from this app on your own or another computer. The emphasis seems to have been largely directed to uploading them to Youtube.
I have now finally got to the point where I can replay my desktop recordings using the mplayer GUI (using the x11 rather than the default Xv driver) other than the fact that this annoying, but actually ineffectual, error message pops up.

Is there any other way to successfully get fullscreen desktop video recordings from this app to play without problems?

---

### Post by MyR on 2007-04-28
> **PaulFXH said:**
> @MyR
Can I assume that using this driver, rather than the x11 I am currently using I can both record fullscreen videos of my desktop WITHOUT seeing that error message pop up?

no, the error is still there. it is a minor annoyance as far as i'm concerned since the video plays fine.

also, i've since switched to the x11 driver. mplayer crashes when moving the player window around in beryl while using the gl driver; i wouldn't recommend it.

---

### Post by PaulFXH on 2007-04-28
Oh well, thanks anyway.

It seems therefore that there is no clean way to play fullscreen videos of your desktop recorded with recordMyDesktop on your own computer without getting this error message.
A minor problem I agree, but it does just take a little of the gloss off what would otherwise be quite a marvellous app.

@loell, as you are the guy who started this thread, I would really welcome your view on this difficulty.

---

### Post by loell on 2007-04-28
> **PaulFXH said:**
> 
 as you are the guy who started this thread, I would really welcome your view on this difficulty.

i'm well aware of the discussion, but i' have no knowledge on how encoding works on the detail and the workings of different movie players available, i'm glad that Myr had digg into this deeper thanks to him. :)

---

### Post by PaulFXH on 2007-04-28
Thanks for your rapid respomse, loell
But, actually, my question is a lot more simple than you seem to have imagined. I simply wanted to know if you or anybody you know have been able to get the output file (whether it's .ogg or .avi) from a fullscreen desktop recording by recordMyDesktop to play on the same computer without errors?

---

### Post by loell on 2007-04-28
without errors? yeah,

 i'm not running any compositors right now, and am still recording when i feel like, i haven't got any errors in playing them in both ogg and avi.

---

### Post by PaulFXH on 2007-04-29
@loell
Thanks for your reply.
If this is the case, then you've just got to tell me more as I can't get my FULLSCREEN desktop videos to play without showing the error popup I already referred to.

Also, I run Beryl with a 1280x1024 resolution. This is a summary of the results I get when trying to run the .ogg file (remember, I'm talking only about the FULLSCREEN video---smaller videos give much less trouble):

Totem (gstreamer): Opens but then shuts down without playing
GXine: Same as Totem
mplayer (Xv driver): Same again
mplayer (x11 driver): Plays the video clearly with sound (for me anyway) but a popup error occurs at the start.

If you can do better with the FULLSCREEN video please tell me how (what player, what backend, anything else relevant)

Thanks
Paul

---

### Post by MyR on 2007-04-29
here you go PaulFXH

install vlc media player (it's awesome)

to configure it to play x11:
settings > preferences > video > output modules.
check the box at the bottom "advanced options"
change video output module to x11 and save.
no errors!

---

### Post by PaulFXH on 2007-04-29
@MyR
That's very good news. Thanks a lot for discovering this.
Unfortunately I can't try it out right now as I toasted my Ubuntu install yesterday while trying to upgrade to Feisty.
Nevertheless, I'm looking forward to checking it out when I get things starightened out today or tomorrow.

---

### Post by audax321 on 2007-05-05
For those of you having the problem where Totem crashes when loading the video I found this to work on my laptop (even fixed graphical issues with Beryl and playing videos):

1. Open /home/username/.gnome2/totem_config

2. Find the following section:

```

# video driver to use
# string, default: auto
#video.driver:auto

```

3. Change that section to:

```

# video driver to use
# string, default: auto
#video.driver:auto
video.driver:xshm

```

Hope that helps.

---

### Post by MyR on 2007-05-05
thanks for the tip audax321

this works with one slight drawback; it does play in totem but i notice it cuts a second or so off of the end of the video. vlc is the best media player (for everything) imo.

---

### Post by audax321 on 2007-05-05
MyR

That is strange, it doesn't seem to cut anything off on mine. It might be that the xshm plugin just works for my laptop (integrated Intel GMA 900) because I know the opengl plugin doesn't work for me, but it does for others. Maybe substituting other plugins in there may rectify the problem? Oh well, guess I just got lucky with that one.

On another note, I have great respect for someone who can put up with vlc. :) It is a nice program, but I hate how it resizes the window when you load a video. It just drives me insane. Is there a way around that? The only option I could really find was to have it zoom the video to 75% of its size, but I'd rather have it never resize so I can adjust the window size myself like totem does. Whenever I load a video that has the same dimensions as my entire desktop it blows the window up.  If you know a way around that let me know. Nothing wrong with having two players installed just in case I need it.

:)

---

### Post by Linux_Noobie on 2007-05-05
Help. (See Screenshot)

---

### Post by audax321 on 2007-05-06
> **Linux_Noobie said:**
> Help. (See Screenshot)

You need to set your color depth to 24. Its actually strange it wasn't set to that to begin with, so I'm wondering if you video card even supports it. You can try this, but make sure you print it out in case things go wrong:

In terminal:

1. sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_bak

2. gksudo gedit /etc/X11/xorg.conf

In gedit:

3. Find a section similar to the following (your resolutions may be different):

```

DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1680x1050" "1440x900" "1280x800" "1024x640" "800x500"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1680x1050" "1440x900" "1280x800" "1024x640" "800x500"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1680x1050" "1440x900" "1280x800" "1024x640" "800x500"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1680x1050" "1440x900" "1280x800" "1024x640" "800x500"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1680x1050" "1440x900" "1280x800" "1024x640" "800x500"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1680x1050" "1440x900" "1280x800" "1024x640" "800x500"
	EndSubSection

```

4. You want to change the DefaultDepth line to 24 AND make sure that there is a section similar to this:

```

SubSection "Display"
		Depth		24
		Modes		<YOUR LIST OF RESOLUTIONS HERE>
	EndSubSection

```

5. Save and Exit

6. CNTRL+ALT+BACKSPACE will restart the X server and hopefully all your settings will be successful. If not, you will need to get to a prompt. Either the X server will just die out and take you to a prompt OR you can press CNTRL+ALT+F1 to get to a prompt.

7. To restore your old settings if something went wrong at terminal type:

```
sudo mv /etc/X11/xorg.conf_bak /etc/X11/xorg.conf
```
```
sudo /etc/init.d/gdm restart
```

Hope that helps. Don't blame me if something goes screwy, but I think that should do it :]

---

### Post by blonder on 2007-05-06
I have a Problem with the gtk gui,it does not Start to encode and still stands by 0 %.
My Problem is the Sound,in Terminal with this Command it works perfekt: 

> recordmydesktop --no-sound


My System: Dell Inspiron 9400

---

### Post by y-man on 2007-05-06
Hi guys,

I am on Dapper. Installed 3.1.

I am trying to records a 3D window:

[INDENT]
$ recordmydesktop --with-shared --full-shots --quick-subsampling --zero-compression -fps 12 -x 112 -y 84 -width 800 -height 600 -windowid 0x3c00003
[/INDENT]

On finishing the play, I hit ctrl-C, after working for a while encoding stops partway:

[INDENT]========Saved 7245 frames in a total of 7243 requests
Shutting down.....
Encoding started!
This may take several minutes.
Pressing Ctrl-C will cancel the procedure (resuming will not be possible, but
any portion of the video, which is already encoded won't be deleted).
Please wait...
[29%]   [Cache File 1]
Encoding finished!
[/INDENT]

As much of it that's been encoded is great, but I cannot get the full thing done.

Any ideas will be much appreciated.

Thanks,

---

### Post by y-man on 2007-05-06
Replying my own post of two hour ago.

I have since found out that I was running out of cache file space. It seems to default to / (possibly /tmp), and my / is almost full.

I specified -workdir $HOME, and all went well. I think default for -workdir is *not* $HOME as man page says.

---

### Post by renewip on 2007-05-28
My output file (out.ogg for default) has just a "blue screen of death" when it played for all time. Why? :((
this is an example:
[http://anhtt.k48ca.googlepages.com/out.ogg](http://anhtt.k48ca.googlepages.com/out.ogg)

---

### Post by loell on 2007-05-28
i don't see any blue screen in your sample, i see your KDE desktop though ;)

---

### Post by hakimaki on 2007-05-28
Everytime I try to watch the output file, it closes down on me.  Why?

---

### Post by hakimaki on 2007-05-28
Ok im guessing its a resolution issue becuase if I select a smaller part of the screen, it will play.  So how do I record my entire desktop 1280X1024 and then view it?

---

### Post by hakimaki on 2007-05-28
> **audax321 said:**
> For those of you having the problem where Totem crashes when loading the video I found this to work on my laptop (even fixed graphical issues with Beryl and playing videos):

1. Open /home/username/.gnome2/totem_config

2. Find the following section:

```

# video driver to use
# string, default: auto
#video.driver:auto

```

3. Change that section to:

```

# video driver to use
# string, default: auto
#video.driver:auto
video.driver:xshm

```

Hope that helps.

Beautiful! Thank you!

---

### Post by kevdog on 2007-06-17
Mplayer works great for playback if you use -vo x11 option however I cant seem to configure vlc media player correctly.  I dont see where I set a similar option -- option menu suggested by previous post does not exist.

---

### Post by iovar on 2007-06-17
> **kevdog said:**
> Mplayer works great for playback if you use -vo x11 option however I cant seem to configure vlc media player correctly.  I dont see where I set a similar option -- option menu suggested by previous post does not exist.

Maybe you missed the "advanced " checkbox?

> **MyR said:**
> 
to configure it to play x11:
settings > preferences > video > output modules.
**check the box at the bottom "advanced options"**


Check the attached video. It's exactly the procedure that MyR described.

---

### Post by mumushi on 2007-06-19
installed recordmydesktop using the onein the repo but when i try to preview the file it just terminate my player. i installed all posible codecs to play avi or ogg files. Installed memcoder and converted the file to avi but still i can't preview it. It always terminates the player. 

Any ideas whats going on? Thanks in advance.

---

### Post by kevdog on 2007-06-20
This is going to sound like possibly the dumbest post ever but when I go to 
settings > preferences > video >   [With advanced options checked]

There is no output modules.  I looked!.  There is the following:
Enable Video
Grayscale Video Output
Fullscreen Video Output
Drop Late Frames
Skip Frames
Quiet Syncro 
Overlay video output
Always on top
Disable ScreenSaver

Snapshot
...
...
...
Window
...
...
...
Fix HDTV height
Window Decorations
Video Title
Video Allignment
Zoom video


Thats it --- Did I miss something???

---

### Post by iovar on 2007-06-20
kevdog:

Did you watch the attached video?
What you are describing is the "**video**" settings tab itself. The "**output modules**" option is not on it.
**It is on the on the option tree on the left** and can be seen after **expanding** the "**video**" entry.


Please watch the video attached on my previous post and you'll understand what I mean.

---

### Post by kevdog on 2007-06-20
The video was a great -- it explained everything
Thanks

Im surprised that as far as clarity of the video, it makes such a big difference

About the video -- nice touch with the stretching woman in the back ground :)

---

### Post by SadaraX on 2007-06-24
I can record video just fine but I am having trouble getting my sound to work. Every time I record there is no sound in the output file. I checked in /tmp while the program was recording and there is a file called audio.pcm that seems to be created and hold.

I have tried various alsa devices but none of them seem to work. On the command line I tried running the program with:

recordmydesktop -device hw:0,0
or
recordmydesktop -device plughw:0,0

Both of these run, but no sound is recorded. I checked all my alsamixer audio input and everything is set to enabled with good recording levels.

---

### Post by lamadredelsapo on 2007-07-09
You just saved my life with those packages. Is it possible to save the video directly in mpeg? Otherwise i'll use ffmpeg to convert it.

---

### Post by loell on 2007-07-09
you can't convert it directly , iovar, intends to keep it this way, to encourage the linux community to use the Ogg   free format. ;)

so you'll just gonna have to use other tools to convert it :)

---

### Post by Ryan Sullivan on 2007-07-12
Hello, im new to this record my desktop. I have done a few videos (with beryl) and converted them to avi using mencoder.  But the thing is my videos come out sorta jumpy and slow with alot of delay. Could someone try and help me with this problem please. 

I really want to make videos.

---

### Post by loell on 2007-07-12
mostly this issue is related to your hardware , more powerful CPU's tend to have smoother videos.

---

### Post by diablo75 on 2007-07-14
This works, but I have one minor issue that involves Beryl.

Video playback gets flickery when I rotate the cube.  Horizontal blips cut through the cube and window, making them transparent and I can see the sky dome.  This is only seen after the capture has been done.

I'm running a pentium 4 2.8 mhz, 768 megs of ram, and a GeForce 5600 Go with 128 megs of ram.

Any suggestions on how to get the video cleaned up?

---

### Post by wconstantine on 2007-07-16
This works great but I have some problems when I want to record gaming. The game is floating on nicely but when I watch the video my games seem to have like 2-3 fps. =/

---

### Post by Uber Nooblett on 2007-08-19
I seem to be having a problem, not sure why exactly as seem to have done everything advised.

I start recordmydesktop either through the frontend or konsole and it seems to record it ok, however when I go to the file to play it seems to play a quick sound then crashes whichever player I'm playing it in. I have tried encoding it to avi which also seemed to happen ok, but once again it wont play.

I'm running Beryl + Kiba Dock on an AMD 64 x2, 4gb ram + 8800GTS @ 2560 x 1024 and would like to do a capture.

thanks in advance: code for install/record/encode is below. Will supply any more info required

```
jj@jj-desktop:~$ sux
Password:
root@jj-desktop:/home/jj# sudo apt-get install recordmydesktop gtk-recordmydesktop
Reading package lists... Done
Building dependency tree
Reading state information... Done
recordmydesktop is already the newest version.
gtk-recordmydesktop is already the newest version.
The following packages were automatically installed and are no longer required:
  libzvbi-common gstreamer0.10-plugins-ugly libzvbi0 libsexy2 python-eyed3
  python-xml gstreamer0.10-gnomevfs libsidplay1 python-gst0.10 libsoup2.2-8
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@jj-desktop:/home/jj# recordmydesktop
Initial recording window is set to:
X:0   Y:0    Width:2560    Height:1024
Adjusted recording window is set to:
X:0   Y:0    Width:2560    Height:1024
Your window manager appears to be beryl


Detected 3d compositing window manager.
Reverting to full screen capture at every frame.
To disable this check run with --no-wm-check
(though that is not advised, since it will probably produce faulty results).

Initializing...
Opened PCM device hw:0,0
Recording on device hw:0,0 is set to:
1 channels at 22050Hz
Buffer size set to 4096 frames.
Capturing!
Shutting down.Saved 303 frames in a total of 303 requests
....
Encoding started!
This may take several minutes.
Pressing Ctrl-C will cancel the procedure (resuming will not be possible, but
any portion of the video, which is already encoded won't be deleted).
Please wait...
[100%]
Encoding finished!
Wait a moment please...

Done.
Written 20600563 bytes
(20382473 of which were video data and 218090 audio data)

Cleanning up cache...
Done!!!
Goodbye!
root@jj-desktop:/home/jj# sudo aptitude install mencoder
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initialising package states... Done
Building tag database... Done
The following NEW packages will be installed:
  mencoder
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 3462kB of archives. After unpacking 8897kB will be used.
Writing extended state information... Done
Get:1 http://security.ubuntu.com feisty-security/multiverse mencoder 2:1.0~rc1-0ubuntu9.1 [3462kB]
Fetched 3462kB in 5s (621kB/s)
Selecting previously deselected package mencoder.
(Reading database ... 123363 files and directories currently installed.)
Unpacking mencoder (from .../mencoder_2%3a1.0~rc1-0ubuntu9.1_amd64.deb) ...
Setting up mencoder (1.0~rc1-0ubuntu9.1) ...
root@jj-desktop:/home/jj# mencoder -idx input.ogg -ovc lavc -oac mp3lame -o output.avi
MEncoder 2:1.0~rc1-0ubuntu9.1 (C) 2000-2006 MPlayer Team
CPU: AMD Athlon(tm) 64 X2 Dual Core Processor 4200+ (Family: 15, Model: 75, Stepping: 2)
CPUflags: Type: 15 MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
File not found: 'input.ogg'
Failed to open input.ogg.
Cannot open file/device.

Exiting...
root@jj-desktop:/home/jj# mencoder -idx output.ogg -ovc lavc -oac mp3lame -o output.avi
MEncoder 2:1.0~rc1-0ubuntu9.1 (C) 2000-2006 MPlayer Team
CPU: AMD Athlon(tm) 64 X2 Dual Core Processor 4200+ (Family: 15, Model: 75, Stepping: 2)
CPUflags: Type: 15 MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
File not found: 'output.ogg'
Failed to open output.ogg.
Cannot open file/device.

Exiting...
root@jj-desktop:/home/jj# mencoder -idx out.ogg -ovc lavc -oac mp3lame -o output.avi
MEncoder 2:1.0~rc1-0ubuntu9.1 (C) 2000-2006 MPlayer Team
CPU: AMD Athlon(tm) 64 X2 Dual Core Processor 4200+ (Family: 15, Model: 75, Stepping: 2)
CPUflags: Type: 15 MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
success: format: 0  data: 0x0 - 0x13a7088
[Ogg] stream 0: video (Theora v3.2.0), -vid 0
[Ogg] stream 1: audio (Vorbis), -aid 0
Ogg file format detected.
VIDEO:  [theo]  2560x1024  24bpp  15.000 fps    0.0 kbps ( 0.0 kbyte/s)
[V] filefmt:18  fourcc:0x6F656874  size:2560x1024  fps:15.00  ftime:=0.0667
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 22050 Hz, 1 ch, s16le, 90.0 kbit/25.51% (ratio: 11248->44100)
Selected audio codec: [ffvorbis] afm: ffmpeg (FFmpeg Vorbis decoder)
==========================================================================
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
[theora @ 0xe29e50]Missing extradata!
Could not open codec.
VDecoder init failed :(
Opening video decoder: [theora] Theora/VP3
VDec: vo config request - 2560 x 1024 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 2.50:1 - prescaling to correct movie aspect.
videocodec: libavcodec (2560x1024 fourcc=34504d46 [FMP4])
Selected video codec: [theora] vfm: theora (Theora (free, reworked VP3))
==========================================================================
MP3 audio selected.

Skipping frame!
Pos:   0.0s      1f ( 6%)  0.00fps Trem:   0min   0mb  A-V:0.000 [0:0]
Skipping frame!
Pos:   0.0s      2f ( 6%)  0.00fps Trem:   0min   0mb  A-V:0.007 [0:0]
Skipping frame!
Pos:   0.0s      3f ( 6%)  0.00fps Trem:   0min   0mb  A-V:0.013 [0:0]
Skipping frame!
Pos:   0.0s      4f ( 6%)  0.00fps Trem:   0min   0mb  A-V:0.019 [0:0]
Skipping frame!
Writing header...5f ( 6%)  0.00fps Trem:   0min   0mb  A-V:0.025 [0:0]
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.

4 duplicate frame(s)!
Pos:   0.4s      7f ( 8%)  0.00fps Trem:   0min   5mb  A-V:0.043 [0:0]
1 duplicate frame(s)!
Pos:   1.6s     24f (14%) 17.08fps Trem:   0min   5mb  A-V:0.135 [3787:127]
Skipping frame!
Pos:  20.3s    305f (100%) 20.30fps Trem:   0min   3mb  A-V:0.076 [1180:127]
Flushing video frames
Writing index...
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.

Video stream: 1180.183 kbit/s  (147522 B/s)  size: 2989797 bytes  20.267 secs  305 frames

Audio stream:  127.706 kbit/s  (15963 B/s)  size: 319422 bytes  20.010 secs
root@jj-desktop:/home/jj#
                                                                          
```

---

### Post by MyR on 2007-08-19
> **Uber Nooblett said:**
> when I go to the file to play it seems to play a quick sound then crashes whichever player I'm playing it in.
you need to configure your video player(s) to play using x11. instructions are in this thread.

peace

---

### Post by fadeup on 2007-08-31
Hi everyone,

I've read through most of this thread and done a lot of searching, but can't see this problem... I'm recording both with the GUI and command line, but the audio and video is jittery. I've tried audio alone with Audacity and it's fine...

When using the command line I see this message;

```
 james@jbinspubuntu:~$ recordmydesktop --quick-subsampling --zero-compression
Initial recording window is set to:
X:0   Y:0    Width:1280    Height:800
Adjusted recording window is set to:
X:0   Y:0    Width:1280    Height:800
Your window manager appears to be Metacity

Initializing...
Opened PCM device hw:0,0
Playback frequency 22050Hz is not available...
Using 44100Hz instead.
Recording on device hw:0,0 is set to:
2 channels at 44100Hz
Buffer size set to 4096 frames.
Capturing!
Broken pipe: Underrun occurred.
Broken pipe: Underrun occurred.
```

There's a long list of 'Broken pipe: Underrun occurred.'

```
Broken pipe: Underrun occurred.
Shutting down.Saved 94 frames in a total of 105 requests
....
Encoding started!
This may take several minutes.
Pressing Ctrl-C will cancel the procedure (resuming will not be possible, but
any portion of the video, which is already encoded won't be deleted).
Please wait...
[99%] 
Encoding finished!
Wait a moment please...
   
Done.
Written 808162 bytes
(612894 of which were video data and 195268 audio data)

Cleanning up cache...
Done!!!
Goodbye!
```

I changed the frequency in the GUI to 44100Hz and it sounded the same. Just wondered if anyone had any ideas? 

Cheers

---

### Post by iovar on 2007-08-31
I don't remember where I've seen it, but if you are using a
laptop. plug it in. The power saving features can degrade performance.

Apart that, change the device to plughw:0,0 and record with the defaults
(22050 hz, 1 channel). High settings need more cpu and can cause more
frequent underruns.

---

### Post by Weird Al on 2007-08-31
Is it possible, or is it intended to be possible, for the image to be resized as it is recorded? Is it possible to use hardware for this?

I'm no expert, nor even a rookie, at this, but if there were someway of taking what's on screen at a lower resolution and then compressing (or not compressing) *that* on the fly, then we'd have a low-res output from a normal-res input. Thus it would be easier to record games, especially ones where you can't see what's going on if you lower your resolution too much.

Am I barking up the wrong postman?

---

### Post by iovar on 2007-08-31
> **Weird Al said:**
> Is it possible, or is it intended to be possible, for the image to be resized as it is recorded? Is it possible to use hardware for this?


Possible? No.
Intended ? Maybe.


The problem with 3d games is that the usually require to much CPU on their
own. And the typical methods provided from X for capturing, are very
inefficient in this case. 
So caching a smaller image may not be enough to allow capture of games
at large resolutions. 

Given that, I want to experiment first with alternate methods of capture,
before trying to implement something like scaling.

Meanwhile, if you are using the feisty version (0.3.0.something) you might
want to remove it and try the latest source package. 0.3 was the first 
version with cache and it was very inefficient space and CPU-wise. 
0.3.6 should provide notable improvements.

---

### Post by loell on 2007-09-01
hi, i've updated the deb package of this thread, 0.3.6  fiesty deb package is available in the first post, 

i must say, the speed improvement is noticeable 

 thanks, iovar =D>

---

### Post by patambrosio on 2007-09-01
i blogged about recordmydesktop [here]("http://ubuntuchocolate.wordpress.com/2007/09/01/howto-screen-capture-in-ubuntu-feisty-fawn/").

and thanks to loell, now i know how to convert videos, but um, **how do i convert and scale down the dimensions of the video i'm encoding?** i can't find my answers in the DOCS. nahihilo ako sa docs nila-- btw pinoy din ako, hehehe.

---

### Post by loell on 2007-09-01
> **patambrosio said:**
> i blogged about recordmydesktop [here]("http://ubuntuchocolate.wordpress.com/2007/09/01/howto-screen-capture-in-ubuntu-feisty-fawn/").

and thanks to loell, now i know how to convert videos, but um, **how do i convert and scale down the dimensions of the video i'm encoding?** i can't find my answers in the DOCS. nahihilo ako sa docs nila-- btw pinoy din ako, hehehe.

hello :)

to scale down the video through mencoder , add this as a parameter ie ```
-vf scale=320:240
``` to convert it to 320 X 240 resolution,  adjust accordingly.

---

### Post by patambrosio on 2007-09-01
thanks loell. :D

---

### Post by iovar on 2007-09-01
> **loell said:**
> hi, i've updated the deb package of this thread, 0.3.6  fiesty deb package is available in the first post, 

i must say, the speed improvement is noticeable 

 thanks, iovar =D>


Thanks loell :) 
It's always better and more beneficial to the program, to have the latest
(and greatest/buggiest?)  packaged and ready, for the users to try.

---

### Post by loell on 2007-09-01
yeah, i also notice that the file encoding had gone drastically smaller than the the video file encoded in previous version, all the while i thought that ogg encoding takes up a lot of space than avi.

---

### Post by berteh on 2007-09-28
I got an old but stable distro, so just made recordmydesktop 0.3.6 packages for Ubuntu Dapper, no JACK sound support compiled though.

[URL="http://ubuntuforums.org/attachment.php?attachmentid=44618&stc=1&d=1190987003"]
recordmydesktop 0.3.6 deb package for dapper[/URL]

[gtk-recordmydesktop 0.3.6 deb package for dapper]("http://ubuntuforums.org/attachment.php?attachmentid=44619&stc=1&d=1190987003")

---

### Post by Nooreazy on 2007-09-28
I use sound recorder works wonders! 

i believe   the code is 
```
sudo apt-get install sound-recorder
```
programs light and easy to use

---

### Post by rainwalker on 2007-10-01
I hope this hasn't been mentioned anywhere in the 26 pages of this thread, but is it normal for recordmydesktop to run exreemmeeellyyy slow while running Beryl?
I'm trying to record all the neat stuff it can do, but it goes way too slow!
And yes, I know there are ones on youtube I could use but I want to do it myself.

---

### Post by MyR on 2007-10-01
> **rainwalker said:**
> is it normal for recordmydesktop to run exreemmeeellyyy slow while running Beryl?

performance is generally a function of your computer's hardware capability: cpu speed, ram, hdd speed, etc. try lowering the frame rate and using the other performance enhancements on recordmydesktop. hope this helps.

peace

---

### Post by loell on 2007-10-01
theres also a misconception, that all those  youtube beryl videos are recorded through recordmydesktop et al , when in fact many of those, are recorded with a high performance videocam. 

though this doesn't mean that recordmydesktop can't do a decent recording with beryl , its just the performance varies from pc to pc.

---

### Post by bubble_bobble on 2007-10-06
Hi, neat program. 

I want to add voice commentary added with a microphone to a movie file. After trying Kino and a couple other programs, I stumbled upon recordmydesktop.

My goal is to add audio to a video file on my computer. recordmydesktop does work well for me. RMD captures the video on my desktop and captures my microphone audio alright, but when I open a  video file in mplayer, RMD doesn't capture the video or audio of that video file, and displays a black box instead.

Is there a method I am overlooking that will allow me to capture a video file from mplayer as well as capture microphone audio with this program? Can anyone suggest a program that can do what I need done?

A video demonstration of my dilemma: Will edit with a video when youtube "processes" it. It's nothing very revealing though.

I want to see if I can complete this project using only Linux.

Thank you!

---

### Post by Adler on 2007-10-06
bubble_bobble,

This might be long shot, but did you convert your .ogg/Vorbis output to .avi?

Try this in Shell:

mencoder -o output_file.avi -ovc lavc -lavcopts vbitrate=5000:vhq -ffourcc DX50 -oac pcm -srate 48000 -ofps 25 your_movie.mov

I assume your Vid is in your Home file. Then where it says "your_movie.mov", change it to /home/whatever/your movie name. Click, and your vid gets converted to an .avi file. It might take a minute or two. The .avi should land in your Home file.

Adler

---

### Post by bubble_bobble on 2007-10-07
> **Adler said:**
> bubble_bobble,

This might be long shot, but did you convert your .ogg/Vorbis output to .avi?

Try this in Shell:

mencoder -o output_file.avi -ovc lavc -lavcopts vbitrate=5000:vhq -ffourcc DX50 -oac pcm -srate 48000 -ofps 25 your_movie.mov

I assume your Vid is in your Home file. Then where it says "your_movie.mov", change it to /home/whatever/your movie name. Click, and your vid gets converted to an .avi file. It might take a minute or two. The .avi should land in your Home file.

Adler

Yeah I tried different  video files, and all give the same result, a black box in the recorded desktop video.

---

### Post by Adler on 2007-10-08
> Yeah I tried different video files, and all give the same result, a black box in the recorded desktop video.

bubble_bobble,

Again - a long shot. Do you have all the mencoder components installed or can't you record? Normally, you should get some kind of output. Do you have anything in your /Home folder?

Adler

---

### Post by eye208 on 2007-10-17
> **bubble_bobble said:**
> My goal is to add audio to a video file on my computer. recordmydesktop does work well for me. RMD captures the video on my desktop and captures my microphone audio alright, but when I open a  video file in mplayer, RMD doesn't capture the video or audio of that video file, and displays a black box instead.
This is because video output does not really go to the desktop window but to a hardware-controlled overlay window instead. It's separate from the desktop and cannot be captured by RMD (as far as I know).

Some video players can be configured not to use XVideo or OpenGL overlays but X11 video instead. But this will increase CPU load and degrade visual quality when the video is scaled up or down.

Instead of using RMD to add the voice-over, I would recommend using Audacity to record just the audio and then a video editor (such as Blender's sequence editor) to mix it with the original audio/video. You can always use tools such as mplayer/mencoder/ffmpeg to separate or replace audio and video streams. If done properly (using stream copy mode) this will not affect the image quality of the original video at all.

---

### Post by Adler on 2007-10-18
eye208,

Now what a minute.

I run Linux Mint Cassandra. I pick a simple music track from my music Library and run it using Audacity. I get it to play in the background, the simply click gtk-recordMyDesktop, and start recording things.

I've no need to mix, or mash what is going on with my Desktop. I'm running those cool 3D Desktop managers for a while now and record them when I want.

[http://www.youtube.com/watch?v=9sBaQZAAn4s](http://www.youtube.com/watch?v=9sBaQZAAn4s)

I simply think that this thread has now become too confusing. 

Adler

---

### Post by loell on 2007-10-19
adler,

i think eye208 made his technical point , as the previous post/page is asking why he can't record a video played in a player, thus eye208 explained and suggested it.

---

### Post by Adler on 2007-10-19
loell,

Thanks for correcting me. I do know that getting this all done is an important element for success.

At this point I don't think that I can not offer any more support. 

Adler

---

### Post by loell on 2007-10-19
> **Adler said:**
> 
 I do know that getting this all done is an important element for success.


i'm not quite sure i get what you mean, since a support thread is just a support thread.

> **Adler said:**
> 
At this point I don't think that I can not offer any more support. 
 

that's just fine, people do come and go in different threads, and this thread won't be an exception. 

see ya around ;)

---

### Post by Adler on 2007-10-19
> that's just fine, people do come and go in different threads, and this thread won't be an exception. 

loell,

We come and go in Threads, Forums, and Linux distros. But, want to see everyone have success with Ubuntu, and those .deb distros.

Adler

---

### Post by loell on 2007-10-19
> **Adler said:**
> loell,

We come and go in Threads, Forums, and Linux distros. But, want to see everyone have success with Ubuntu, and those .deb distros.

Adler

I still don't understand what this has got to do with the thread topic **recodmydesktop**

anyway, best of luck.

---

### Post by Adler on 2007-10-19
> I still don't understand what this has got to do with the thread topic recodmydesktop

loell,

I think that I was one of the original posters here. If not, I worked my way through an ATI Notebook card, then Beryl, Compiz-Fusion.

Should there not be recordMyDesktop included with Ubuntu?

I think that is my point here regarding recordMyDesktop.

Adler

---

### Post by loell on 2007-10-19
adler,

you really are confusing me, and I am starting to question your intentions on your recent successive posts, which is not helpful to the thread.

you can refer to the first page of the original posters if you are unsure if you are one of **orginal posters**.

> Should there not be recordMyDesktop included with Ubuntu?

yes there is r**ecordmydesktop** in the repo  for fiesty and also in gutsy which originally came from debian. 

**but this thread was created before fiesty,  to offer recordmydektop for edgy at that time.**

and the hope to give feedback to iovar for the benefit of recordmydesktop project. 

you never had to announce your withdrawal of support, whatever that may be.

as anybody can ask questions and anybody can post answers in the thread.

-loell

---

### Post by Adler on 2007-10-19
> 
you really are confusing me, and I am starting to question your intentions on your recent successive posts, which is not helpful to the thread.

loell,

I'll not post again here. I'm against against such responses. 

Adler

---

### Post by bubble_bobble on 2007-10-22
Thank you very much Adler for your suggestions.

eye208, that looks like helpful support you gave, and now I know there exists a program called Blender's sequence editor that sounds like it is worth using to complete my task. Thanks.

---

### Post by brennydoogles on 2007-10-22
I wrote a little script to convert the ogg outputs to avi as prescribed in the first post (just to make things simple. To run it, simply place it in your path (either /usr/bin or your own personal bin/ folder if you have added your own path), navigate to the folder with the screencast and type ```
ogg2avi.sh screencast.ogg
``` while replacing screencast.ogg with the name of your ogg file. It will ask you what you would like to call your avi, and type the desired filename without the extension, and voila! You have an AVI!

---

### Post by loell on 2007-10-22
nice little script :)

---

### Post by brennydoogles on 2007-10-22
> **loell said:**
> nice little script :)

Thank you very much!

---

### Post by brennydoogles on 2007-10-24
> **brennydoogles said:**
> I wrote a little script to convert the ogg outputs to avi as prescribed in the first post (just to make things simple. To run it, simply place it in your path (either /usr/bin or your own personal bin/ folder if you have added your own path), navigate to the folder with the screencast and type ```
ogg2avi.sh screencast.ogg
``` while replacing screencast.ogg with the name of your ogg file. It will ask you what you would like to call your avi, and type the desired filename without the extension, and voila! You have an AVI!

ok, I have made a few changes to the script. Now, it will create a ~/screencasts directory, inside of which will be a folder for ogg's and avi's. after it converts the screencast, it will now rename the ogg to the same thing as you had it name the avi, and move both to their respective folders in your new screencast directory. I am also trying to find a way to have the script autorun after a screencast is taken, in which case you will have two copies of the video after every screencast, a youtube version, and an ogg version.

---

### Post by RAV TUX on 2007-10-24
> **loell said:**
> [SIZE=4]**[http://recordmydesktop.sourceforge.net](http://recordmydesktop.sourceforge.net)**[/SIZE]
a nice screen/desktop video recorder, try it :)

**update: available package for the latest version 0.3.6 fiesty deb package**

notable improvements: more efficient, and snappier than the previous version






update: recordmydeskop is on fiesty repository,  ```
sudo apt-get install recordmydesktop gtk-recordmydesktop
```for beginners you can also install it through ADD/REMOVE applications

[SIZE=4]3.1 dapper deb package[/SIZE]

[SIZE=5][COLOR=Red][recordmydesktop 3.1]("http://ubuntuforums.org/attachment.php?attachmentid=21416&stc=1&d=1166662741")[/COLOR][/SIZE]

[SIZE=5][COLOR=Red][gtk-recordmydesktop 3.1]("http://ubuntuforums.org/attachment.php?attachmentid=21415&stc=1&d=1166662741")
[/COLOR][/SIZE]



==============================================

download the two edgy **deb packages**
[SIZE=4]**[edgy deb package]("http://www.ubuntuforums.org/attachment.php?attachmentid=19714&d=1164066359")**[/SIZE] -- [COLOR=Red]command line[/COLOR]

[B][SIZE=4][gtkrecordmydesktop  edgy deb package]("http://www.ubuntuforums.org/attachment.php?attachmentid=19713&d=1164066359") requires recordmydesktop
[/SIZE][/B] -- [COLOR=Red]gui-front-end[/COLOR]



**[COLOR=Blue]Using Recordmydesktop[/COLOR]**

in command line console type the command **recordmydesktop** 
you can stop the recording by pressing **ctrl-c**

or in gui-front just click record, and just click the white square on system tray to stop

the output is in **ogg **video format however you can convert it to **avi** by **mencoder**

example 

    
    *note install mencoder if its not installed by doing  ```
sudo aptitude install mencoder 
``` in command line

then you can upload it to youtube or wherever.

[SIZE=3]video sample(s)
[B]by Sandman32 [http://www.youtube.com/watch?v=2FZ9N_YEo3g](http://www.youtube.com/watch?v=2FZ9N_YEo3g) (beryl 0.1.2 burn and water effects)
             [http://www.youtube.com/watch?v=XJWYSfGvITA](http://www.youtube.com/watch?v=XJWYSfGvITA)(warcraft III demo)
by Sandman32[http://www.youtube.com/watch?v=VwzsrpHRxtY](http://www.youtube.com/watch?v=VwzsrpHRxtY)(beryl  /water effect)
by iadanr [http://www.youtube.com/watch?v=RF7FgWcIxg8](http://www.youtube.com/watch?v=RF7FgWcIxg8)(beryl)
[/B][/SIZE]

enjoy :)Will this work in Gutsy and in e17?

---

### Post by Adler on 2007-10-24
> Thank you very much Adler for your suggestions.

bubble_bobble,

Well, thank you for that.

brennydoogles,

Thanks for your script!

Adler

---

### Post by loell on 2007-10-24
> **RAV TUX said:**
> Will this work in Gutsy and in e17?

yes, definitely, and there is recordmydesktop on gutsy repo.

---

### Post by Adler on 2007-10-26
Hi All,

I've a lot of YouTube videos going regarding Linux 3D Desktops using Beryl and compiz-Fusion. I've recorded these with recordMyDesktop.

What I would like to do is add / edit all these uploads to include an introduction screen e.g. one slide to show / tell what the viewer will be looking at. 

Basically, I would need a video editor, but I am not sure what to use.

BTW, here is my latest upload to YouTube...

[http://www.youtube.com/watch?v=Evle8rSxaDE](http://www.youtube.com/watch?v=Evle8rSxaDE)

Thanks for any help here.

Adler

---

### Post by godofwar on 2007-10-27
nvm asked a dumb Q. works greaT!

---

### Post by kr0n1x on 2007-10-29
i made a video with gtk-recordmydesktop.

the file is ok, but i've a problem playing it. i found the "fix" here: [http://recordmydesktop.iovar.org/faq.php#I](http://recordmydesktop.iovar.org/faq.php#I)

there's a problem with the resolution of the video (same as my screen resolution), and the problem there is also if i convert the ogg to avi with mencoder.

can i resize the video? (ogg and avi...) i don't know the command to resize a video :) can anyone help me? thanks

---

### Post by Baby Boy on 2007-10-31
Help, I can't make a video of my desktop. The program just freezes at 0% when it starts encoding when I want to save the video. :confused:

---

### Post by Scimu on 2007-11-01
Thanks a lot.. Works perfectly under Gutsy Gibbon!

---

### Post by flyingsolo on 2007-11-11
I'm having the same problem--it doesn't seem to be actually encoding and sits at the 0% level. (Gutsy, compiz running)  Would like to use for Gimp tutorials for local photo club.

---

### Post by loell on 2007-11-11
and you are using the version from gutsy repository?

---

### Post by flyingsolo on 2007-11-11
yes-just reloaded it to be sure via synaptic; if I run in command line, it seems to not detect sound device. I have a logitech USB headset with microphone attached.  I would have thought the 'video' component at least would have been captured maybe with silence on audio channel.

OK--few hours later but now I tried a capture with 'audio' selection turned off & it works perfectly fine so the issue I originally had is related to audio detection.

---

### Post by loell on 2007-11-11
hmm, its seems this does happened even in later versions? we'll gonna have to wait for iovar to figure this out or possibly fix this.

---

### Post by Baby Boy on 2007-11-14
> **flyingsolo said:**
> yes-just reloaded it to be sure via synaptic; if I run in command line, it seems to not detect sound device. I have a logitech USB headset with microphone attached.  I would have thought the 'video' component at least would have been captured maybe with silence on audio channel.

OK--few hours later but now I tried a capture with 'audio' selection turned off & it works perfectly fine so the issue I originally had is related to audio detection.

Yep, it's working perfectly now, thanks a lot.

---

### Post by flyingsolo on 2007-11-15
> **Baby Boy said:**
> Yep, it's working perfectly now, thanks a lot.

Well, I would suggest it isn't 'perfect' if the video and audio can't be recorded together.  (I know you can work around by doing audio in audacity but isn't it the goal of the program to allow integrated audio and video recording?)

---

### Post by Adler on 2007-12-04
Hi Guys,

I had to get back here. I went back to Ubuntu, through SuSE, then Linux Mint to get the correct code to change those .ogg outputs to go to YouTube.

You have to love Linux Mint!

---

### Post by eggdeng on 2008-01-14
Seems there are still no packages for edgy in the repos. Loell's links are still good though. Thanks for keeping it up to date.

---

### Post by maxxum on 2008-01-30
This is a great app. I love it. Thanks for making it. Sometimes I record multiple sections of the screen simultaneously and it becomes difficult to keep track which taksbar icon corresponds to which section being recorded. It would help if there was some mechanism to distinguish between them. I know this would be hard to implement, if at all possible. One would think that each taskbar icon would be of different color and the recording black box corresponding to that icon would be of the same color. 
Regardless, it is an extremely useful app and all I need to figure out is how to record sound using the alsa mixer.

---

### Post by orvils on 2008-02-02
All the videos I record on my laptop are in graycale :( On my other PC everything is fine. 
Does anybody know how to switch between color/grayscale mode?

---

### Post by whaase on 2008-02-03
Very cool program, but i find it jittery when recording. System really bogs. Any ideas?

---

### Post by stmiller on 2008-03-03
> **whaase said:**
> Very cool program, but i find it jittery when recording. System really bogs. Any ideas?

Get a faster computer? :) 

*ducks*

---

### Post by Adler on 2008-03-03
Guys,

I've done a lot of 3D Linux Desktops on YouTube. They are[ here]("http://www.youtube.com/user/jjmacey").

I've done these all using recordMyDesktop. 

I'd like to add Text or Slides to the videos that I produce or have saved . Is there a good application out there?

I'm doing this all from native Linux, and not a video camera.

I've been looking to do this forever!

Adler

---

### Post by WFGeppetto on 2008-03-11
I don't currently have time to read this entire thread; I will as soon as I get home this evening.

I am here now, to praise this program.  It took a couple of attempts to figure it out, but once I did, it was very easy to use.  I still have to work out the sound, but honestly, I don't care if it records sound, and I'm sure that when I read the whole thread, I will find those answers.

One thing I think is weird, but I suspect I will figure out tonight, is the fact that it saves as .ogg.  That isn't weird by itsself, but this is the second install of Ubuntu I've done (I crowded the old one, trying out different apps, and not properly maintaining).  On the first install, I ran recordmydesktop to show some friends how sweet Ubuntu is.  I can't say for sure, but I am almost positive that it saved as an .flv that time, because I had no trouble at all uploading it to my Photobucket account.  This time however, I cannot do so, because .ogg is not supported.  I'm sure I'll find a way to convert it, but is there a way to have it save as .flv to begin with.

If not, how did I get it to work the first time?  I'd link the video, but it was intended for personal friends, and it shows personal information.  The second video was intended for these forums, but it's .ogg, and I don't know what to do about it.  If the answer is in this thread, I'll find it.  But if there is an easy answer, I'd appreciate it.

Again, that's not my purpose right now.  I'm sure I'll figure it out.  I just wanted to say, I really dig this app.  It's even easier than anything like it that I've used in windows, which is my native tongue, so to speak.

---

### Post by Adler on 2008-03-11
WFGeppetto,

I know the problem that you are struggling with here. The output is in the .ogg/Vorbis format, which YouTube also does not accept.

To convert the output to the .Avi format I use this script in Shell:

Firstly, you'll need mencoder installed. Get it through Synaptic.

Then in shell run either of these two commands:

For PAL:
Code:
mencoder -o output_file.avi -ovc lavc -lavcopts vbitrate=5000:vhq -ffourcc DX50 -oac pcm -srate 48000 -ofps 25 your_movie.mov

For NTSC:
Code:
mencoder -o output_file.avi -ovc lavc -lavcopts vbitrate=5000:vhq -ffourcc DX50 -oac pcm -srate 48000 -ofps 29.97 your_movie.mov

I assume your Vid is in your Home file. Then where it says "your_movie.mov", change it to /home/whatever/your movie name. Click, and your vid gets converted to an .Avi file. It might take a minute or two. The .Avi should land in your Home file.

Let us know how it works out.

BTW, I found this solution long ago, I'm sure somewhere here in the Ubuntu Forums.

Adler

---

### Post by WFGeppetto on 2008-03-11
Hey, thanks a bunch, Adler!  

I don't have time to follow up right now, but I will a bit later tonight, and I'll come back with the results. 

I appreciate the response!

---

### Post by Twitch6000 on 2008-03-12
thanks for the program but,I get and error saying,Recording finish error 256.
Parsing related or something.I even got the most updated version.This is the only recorder that will start up for me and it won't record =[.Can someone help me fix the issue lol.

---

### Post by WFGeppetto on 2008-03-17
Yay! I've got it all working now. 

Btw, for video conversion, ffmpeg has a gtk front end manager (a graphical interface) called winff.  Winff makes ffmpeg easy as pie.  Conversion is crazy easy, I can't recommend this enough.

here's my [video](http://s193.photobucket.com/albums/z150/wfgeppetto/?action=view&current=outogg.flv)

---

### Post by SnakeHips on 2008-03-30
Here's one i made earlier...
[http://uk.youtube.com/watch?v=gSNulSDONCM](http://uk.youtube.com/watch?v=gSNulSDONCM)

fyi - there's a Ubuntu group on Youtube.
[http://uk.youtube.com/groups_layout?name=ubuntu](http://uk.youtube.com/groups_layout?name=ubuntu)

---

### Post by SnakeHips on 2008-03-30
> **maxxum said:**
> This is a great app. I love it. Thanks for making it. Sometimes I record multiple sections of the screen simultaneously and it becomes difficult to keep track which taksbar icon corresponds to which section being recorded. It would help if there was some mechanism to distinguish between them. I know this would be hard to implement, if at all possible. One would think that each taskbar icon would be of different color and the recording black box corresponding to that icon would be of the same color. 
Regardless, it is an extremely useful app and all I need to figure out is how to record sound using the alsa mixer.

In terminal type alsamixer

press tab key to select "capture"

press right arrow key to highlight "mix" press spacebar to select

hope it helps.

---

### Post by jerbroo on 2008-04-01
When I play any of my test screen captures made with recordmydesktop all I see is a blue screen as the video plays.  I'm using kaffiene.

Any suggestions?

...missing codec file?

thanks

---

### Post by brennydoogles on 2008-04-03
> **jerbroo said:**
> When I play any of my test screen captures made with recordmydesktop all I see is a blue screen as the video plays.  I'm using kaffiene.

Any suggestions?

...missing codec file?

thanks

I doubt it would be a missing codec since recordmydesktop records to an open source video format. I would try downloading VLC and trying it```
sudo aptitude install vlc
```

---

### Post by jerbroo on 2008-04-09
Thanks! 
  Though that didn't actually fix the problem (vlc is already installed), it did prompt me to run vlc from a terminal.  From there it gave malloc errors.  The chip in my laptop (Intel Corporation Mobile 945GM/GMS/940GML Express Inte\
grated Graphics Controller) uses shared memory and appearently there's a bug.  After applying the following fix and restarting X (log out and in again) I can play my screen captures!  wooohooo!

The fix is to add these line to the Device section of the xorg.conf file:
        Option "VideoRam" "65536"
        Option "CacheLines" "1980"


....So, my section looks like this.  

Section "Device"
        Identifier      "Intel Corporation Mobile 945GM/GMS/940GML Express Inte\
grated Graphics Controller"
        Boardname       "i810"
        Busid           "PCI:0:2:0"
        Driver          "i810"
        Screen  0
        Option "VideoRam" "65536"
        Option "CacheLines" "1980"
EndSection

The original post is here: [http://ubuntuforums.org/archive/index.php/t-194746.html](http://ubuntuforums.org/archive/index.php/t-194746.html)

---

### Post by brennydoogles on 2008-04-10
Sweet! Throw a vid on Youtube, and show us!

---

### Post by suoko on 2008-04-15
RE: Convert files in tmp?
By: John Varouhakis (iovarProject Admin) - 2007-11-22 08:24
I'm afraid that there is no standard procedure on rescuing sessions 
(it is planned for 0.3.7 though) 
 
The easiest way to do it now, is probably the following: 
 
1)rename your files like this: img.out=>img.out.1 ,img.out.1=>img.out.2 and so on. 
 
2)start a new recordMyDesktop recording session,  
using identical settings as the crashed session. 
 
3)find it's folder with the temporary files of the new session(while 
recording) and paste the files you want to rescue. 
 
4) stop the new session and let it encode. 
 
 
Normally, what will happen is that the old 
recording will be collated on the end of the new one.  
The problem of course is that you will have the contents  
of the new session at the beginning of the old. 
 
 
You can minimize this effect by using this script: 
[http://recordmydesktop.iovar.org/files/rescue_rmd.gz](http://recordmydesktop.iovar.org/files/rescue_rmd.gz) 
 
Place it somewhere in your path and then cd to 
the rMD-session-12517/ directory . Then simply 
run the script. 
 
If you used custom settings (fps, width,height) 
in the initial recording you need to modify the  
script and mirror these. 
 
 
 
Feel free to ask if you have any questions on the  
procedure. 
 
 
 
 
John.- 


[https://sourceforge.net/forum/forum.php?thread_id=1785293&forum_id=590957](https://sourceforge.net/forum/forum.php?thread_id=1785293&forum_id=590957)

UPDATE:
In order to recover the audio I copy audio.pcm together with img.out.1(I don't rename it to audio.pcm.1 otherwise I got no audio at all)
The problem with this procedure is that the audio goes out of sync but can be adjusted (though it's an hard work with kino)

---

### Post by bprof on 2008-04-28
I've tried recordmydesktop, here is what I did:
1-Open the application (GUI)
2-Clicked record
3-When finished stopped recording and clicked save as.
4-Gave a name and location

The result nothing was saved.

I did the same steps but this time after selecting a Window, still I got the same result.

Then I tried to give a name first, then select a window the result was this error:

recordmydesktop has exited with status:256
Description: error while parsing the arguments.

Any help as to what went wrong?

---

### Post by neurotranslator on 2008-05-14
I got problem with gtk record my desktop. The video is no in sync with audio. [There is audio delay]("http://www.youtube.com/watch?v=wzJPFMM4Mq4"). I am looking for help. Please if someone has got solution post it. Thanks

---

### Post by purplepaint on 2008-05-18
sorry if this sounds like a stupid question, but I'm still new to all this stuff...

what if I can't find an option called "mix" to check?

---

### Post by ShadowMKII on 2008-06-15
I also cannot find a "mix" option either.

I have three "Captures" and I have set them all to 100%, but I still have no results. That is even when I use the "GNOME ALSA Mixer" application from Synaptic (they accomplish the same thing.)

---

### Post by DonnyB4e56 on 2008-06-22
I can't stop recording by pressint CTRL+C it's not working.

---

### Post by brennydoogles on 2008-06-24
> **DonnyB4e56 said:**
> I can't stop recording by pressint CTRL+C it's not working.

if you are running the app from terminal make sure the terminal window is selected before you do Ctrl +c. If you are not running in terminal, then ctrl+c won't do anything, and you will need to click stop on the GUI option.

---

### Post by Duudo on 2008-07-26
> **bprof said:**
> I've tried recordmydesktop, here is what I did:
1-Open the application (GUI)
2-Clicked record
3-When finished stopped recording and clicked save as.
4-Gave a name and location

The result nothing was saved.

I did the same steps but this time after selecting a Window, still I got the same result.

Then I tried to give a name first, then select a window the result was this error:

recordmydesktop has exited with status:256
Description: error while parsing the arguments.

Any help as to what went wrong?

I have the same problem.. -.-'

---

### Post by miranto on 2008-07-30
hi i am new at linux, i installed recordmydesktop or at least i think i did, hehe and when i hit the record button it will take a second for an error msg to come up saying: 
Recording has finished
recordmyDesktop has exited with status: 256
Description:Error while parsing the arguments.

Please help

---

### Post by loell on 2008-07-30
can you execute **recordmydesktop** on the terminal, see message you will get.

---

### Post by Adler on 2008-07-30
Hi All,

I had recordMyDesktop going very well. My system crashed, now I want to see the guide to recording.

recordmyDesktop is installed, where is the How To? I did it so well before.

Regards,

Adler

---

### Post by dugh on 2008-08-19
I and others had gtk-recordmydesktop working fine in Ubuntu Gutsy, but then it stopped working in Ubuntu Hardy.  It hangs after the recording is over, while it is encoding or saving to disk or whatever.

See for example:
[http://ubuntuforums.org/showthread.php?p=5621812](http://ubuntuforums.org/showthread.php?p=5621812)
[http://ubuntuforums.org/showthread.php?t=756707](http://ubuntuforums.org/showthread.php?t=756707)

Using recordmydesktop from the command seems to work fine, although I haven't learned how to limit it to one window yet.

Is there a fix for this somewhere?

---

### Post by loell on 2008-08-19
> **dugh said:**
> I and others had gtk-recordmydesktop working fine in Ubuntu Gutsy, but then it stopped working in Ubuntu Hardy.  It hangs after the recording is over, while it is encoding or saving to disk or whatever.

See for example:
[http://ubuntuforums.org/showthread.php?p=5621812](http://ubuntuforums.org/showthread.php?p=5621812)
[http://ubuntuforums.org/showthread.php?t=756707](http://ubuntuforums.org/showthread.php?t=756707)

Using recordmydesktop from the command seems to work fine, although I haven't learned how to limit it to one window yet.

Is there a fix for this somewhere?

i haven't check with recordmydesktop's project site for a while now, althoughits really strange that you get it working in the command line but it won't if executed with gtk-recordmydesktop.

---

### Post by Samizdat on 2008-09-11
rMD doesn't work well at all in my Hardy 8.04 setup.  The audio is fantastic, but the video either plays back in about three seconds, even if it's a three minute recording, or there's no video at all except a black screen (when trying to record music visualizations, for instance).

What's wrong here?  Must I buy a DVB card and a VDR?  Must I install Ubuntu server edition?  Or must I merely install the "correct DVB modules?"  If the last, *which* are the correct modules?

Any help here greatly appreciated.

---

### Post by mocha on 2008-09-12
I downloaded and compiled the latest versions from their homepage and it works fine.

---

### Post by Valodes on 2008-09-16
Thanks Dude this really great program you rock give you :KS:KS:KS:KS:KS

bey

---

### Post by JohnParker on 2008-09-20
I there any way to record full screen? 1440x900?

---

### Post by warped0ne on 2008-10-08
The tutorial at the beginning of this post is very good, but here's a link to a short video of the actual process of installing the Record My Desktop and Mencoder software.

[http://home.mchsi.com/~tk1/recordmydesktop.swf](http://home.mchsi.com/~tk1/recordmydesktop.swf)

I wanted to include instructions on how to actually use the software as well, but Record My Desktop doesn't work in my virtual installation of Ubuntu, sorry.

---

### Post by mrpurple on 2008-11-19
hi, i'm under ubuntu 8.10 amd 64.
i'm tryng to record a video from my pc. I'd like to capture also the audio of the video that i'm watching , if is possible.
i just installed and getting this:

```
~$ recordmydesktop
Initial recording window is set to:
X:0   Y:0    Width:1680    Height:1050
Adjusted recording window is set to:
X:0   Y:4    Width:1680    Height:1040
Your window manager appears to be compiz


Detected 3d compositing window manager.
Reverting to full screen capture at every frame.
To disable this check run with --no-wm-check
(though that is not advised, since it will probably produce faulty results).

Initializing...
Buffer size adjusted to 4096 from 4096 frames.
Opened PCM device hw:0,0
Playback frequency 22050Hz is not available...
Using 44100Hz instead.
Recording on device hw:0,0 is set to:
2 channels at 44100Hz
Capturing!
X Error: BadAccess (attempt to access private resource denied)
Bad Access on XGrabKey.
Shortcut already assigned.
X Error: BadAccess (attempt to access private resource denied)
Bad Access on XGrabKey.
Shortcut already assigned.
X Error: BadAccess (attempt to access private resource denied)
Bad Access on XGrabKey.
Shortcut already assigned.
X Error: BadAccess (attempt to access private resource denied)
Bad Access on XGrabKey.
Shortcut already assigned.
Broken pipe: Overrun occurred.
Broken pipe: Overrun occurred.
Broken pipe: Overrun occurred.
Broken pipe: Overrun occurred.
Broken pipe: Overrun occurred.
Broken pipe: Overrun occurred.
Broken pipe: Overrun occurred.
Broken pipe: Overrun occurred.
Broken pipe: Overrun occurred.
Broken pipe: Overrun occurred.
Broken pipe: Overrun occurred.
Broken pipe: Overrun occurred.
Broken pipe: Overrun occurred.
Broken pipe: Overrun occurred.
Broken pipe: Overrun occurred.
Broken pipe: Overrun occurred.
Broken pipe: Overrun occurred.
Broken pipe: Overrun occurred.
Broken pipe: Overrun occurred.
Broken pipe: Overrun occurred.
Broken pipe: Overrun occurred.
Broken pipe: Overrun occurred.
Broken pipe: Overrun occurred.
Broken pipe: Overrun occurred.
Broken pipe: Overrun occurred.
Broken pipe: Overrun occurred.
Broken pipe: Overrun occurred.
Broken pipe: Overrun occurred.
Broken pipe: Overrun occurred.
Broken pipe: Overrun occurred.
Broken pipe: Overrun occurred.
Broken pipe: Overrun occurred.
Broken pipe: Overrun occurred.
Broken pipe: Overrun occurred.
Broken pipe: Overrun occurred.
^C
*********************************************

Cached 18 MB, from 4294967245 MB that were received.
Average cache compression ratio: 0 %

*********************************************
Saved 607 frames in a total of 651 requests
Shutting down.....
STATE:ENCODING
Encoding started!
This may take several minutes.
Pressing Ctrl-C will cancel the procedure (resuming will not be possible, but
any portion of the video, which is already encoded won't be deleted).
Please wait...
[49%] ^C
Encoding finished!
Wait a moment please...
   
Done.
Written 5655443 bytes
(4536445 of which were video data and 1118998 audio data)

Cleanning up cache...
Done!!!
Goodbye!
```

i did some try from gtk and video are good but no audio.

---

### Post by Adler on 2008-11-19
mrpurple,

Are you running 8.10 64-bit on that AMD processor?

Regards,

Adler

---

### Post by mrpurple on 2008-11-19
no the processor is intel core duo
but i did again a try from the gtk-recordmydesktop just now and i can record the video, with microphone audio.
Seems that is not possible record the sound coming from the computer (mean file or video showing while capturing)

---

### Post by wtstommy on 2008-11-20
I seem to be having exactly the same problem as Mrpurple, and my desktop runs extremely slow when I run recordmydesktop.

---

### Post by mrpurple on 2008-11-20
for the performance check that under advanced the tab performance has the flag on zero compression.
for audio from pc don't know yet.

---

### Post by Adler on 2008-11-20
Hi All,

I ran across [[COLOR="DarkRed"]this[/COLOR]]("http://linux-magazine.com/online/blogs/productivity_sauce_dmitri_s_open_source_blend_of_productive_computing/screencasts_on_linux_made_easy") today.

I hope this helps.

Regards,

Adler

---

### Post by Dyonas on 2008-12-20
I hope I'm not pulling up a long dead topic but I've been trying to use recordmydesktop for a while and manage to - but without audio.  The option to select audio (gtkrecmydesktop) is listed as "DEFAULT" in an editable text box but I want it to record the audio I hear, not the mic source and I don't know how to do this.  Can anyone tell me how to go about altering it so I can record audio as I hear it?

I don't intend to do it for this but it's the best way to give an example.  If I was on YouTube and set it up I can record the video but audio is only taken from the front mic port (laptop).  If no mic is plugged in then the audio is missing.  I'm sure it's a simple thing to do but I'm a relatively new Linux user and don't know where to start.

---

### Post by purplepaint on 2008-12-20
> **Dyonas said:**
> I hope I'm not pulling up a long dead topic but I've been trying to use recordmydesktop for a while and manage to - but without audio.  The option to select audio (gtkrecmydesktop) is listed as "DEFAULT" in an editable text box but I want it to record the audio I hear, not the mic source and I don't know how to do this.  Can anyone tell me how to go about altering it so I can record audio as I hear it?

I don't intend to do it for this but it's the best way to give an example.  If I was on YouTube and set it up I can record the video but audio is only taken from the front mic port (laptop).  If no mic is plugged in then the audio is missing.  I'm sure it's a simple thing to do but I'm a relatively new Linux user and don't know where to start.
From what I've learnt, it seems that the ability to "record what you hear" is a hardware issue.  The only method I've found for my laptop (which works extremely well) is to connect your mic jack to your headphone jack via a female-to-female connector.

I can't remember whether or not I had to fiddle around with Alsamixer settings.

---

### Post by rvkbob on 2009-01-26
Many thanks for all the help. I found, with Ubuntu 8.10, that I can indeed record my desktop but not the sound. Does anyone know what to turn on to allow sound capture from the desktop? I've tried recording a bit from a YouTube video and all I get is the video.

BTW, I had to mencoder the .ogg to a .avi to get Movie Player to play it at all.

Any help will be appreciated. I'm a rookie at this movie stuff.;)

---

### Post by rfkrocktk on 2009-02-05
I've also been having my fair share of crap while dealing with recordmydesktop :)
One thing is that the GUI only seems to record roughly 50% of the time, though it's worse if I'm trying to record audio with the video. I don't know what that's all about, but I can deal with using terminal to run recordMyDesktop. 
The other thing is audio. I finally think I got recording audio to work thanks to hours of googling and watching tutorials on the subject. I got Skype running just fine and I'm totally stoked on getting that working, but recordMyDesktop is another story. Sometimes from commandline, it'll work, sometimes it will become unresponsive to Ctrl-C. When I run it from commandline with audio, I get the following output:

> rfkrocktk@rfkrocktk-ubuntu:~$ recordmydesktop -device hw:default,0
Initial recording window is set to:
X:0   Y:0    Width:1280    Height:800
Adjusted recording window is set to:
X:0   Y:0    Width:1280    Height:800
Your window manager appears to be Metacity

Initializing...
Buffer size adjusted to 4096 from 4096 frames.
Opened PCM device hw:default,0
Playback frequency 22050Hz is not available...
Using 44100Hz instead.
Recording on device hw:default,0 is set to:
1 channels at 44100Hz
Capturing!
Broken pipe: Underrun occurred.
Broken pipe: Underrun occurred.
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7a38767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb7a388b1]
#2 /usr/lib/libX11.so.6 [0xb7e91421]
#3 /usr/lib/libX11.so.6(XNextEvent+0x74) [0xb7e79734]
#4 recordmydesktop [0x8051776]
#5 /lib/tls/i686/cmov/libpthread.so.0 [0xb7d574fb]
#6 /lib/tls/i686/cmov/libc.so.6(clone+0x5e) [0xb7b10e5e]
Broken pipe: Underrun occurred.
Broken pipe: Underrun occurred.
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7a38767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb7a3881e]
#2 /usr/lib/libX11.so.6 [0xb7e91518]
#3 /usr/lib/libX11.so.6 [0xb7e91cb2]
#4 /usr/lib/libX11.so.6 [0xb7e91fcf]
#5 /usr/lib/libX11.so.6(XNextEvent+0x8b) [0xb7e7974b]
#6 recordmydesktop [0x8051776]
#7 /lib/tls/i686/cmov/libpthread.so.0 [0xb7d574fb]
#8 /lib/tls/i686/cmov/libc.so.6(clone+0x5e) [0xb7b10e5e]
Broken pipe: Underrun occurred.
Broken pipe: Underrun occurred.
Broken pipe: Underrun occurred.
Broken pipe: Underrun occurred.
Broken pipe: Underrun occurred.
Broken pipe: Underrun occurred.
Broken pipe: Underrun occurred.
Broken pipe: Underrun occurred.
Broken pipe: Underrun occurred.
Broken pipe: Underrun occurred.
Broken pipe: Underrun occurred.
Broken pipe: Underrun occurred.
Broken pipe: Underrun occurred.
Broken pipe: Underrun occurred.
Broken pipe: Underrun occurred.
Broken pipe: Underrun occurred.
Broken pipe: Underrun occurred.
Broken pipe: Underrun occurred.
Broken pipe: Underrun occurred.
Broken pipe: Underrun occurred.
Broken pipe: Underrun occurred.
Broken pipe: Underrun occurred.
Broken pipe: Underrun occurred.
Broken pipe: Underrun occurred.
Shutting down.Saved 32 frames in a total of 75 requests
....
Encoding started!
This may take several minutes.
Pressing Ctrl-C will cancel the procedure (resuming will not be possible, but
any portion of the video, which is already encoded won't be deleted).
Please wait...
[98%] 
Encoding finished!
Wait a moment please...
   
Done.
Written 1419070 bytes
(1358345 of which were video data and 60725 audio data)

Cleanning up cache...
Done!!!
Goodbye!


If it actually puts out the file, it is semi-watchable, but no sound is present and it will play back at less than a frame per second, in fact my video player's scrubber bar won't even move. If no audio is included in the file, it usually plays back fine, but sometimes it will be impossible to exit the terminal using Ctrl-C, it just won't do anything. When I use the --no-sound parameter, this is what my output looks like:

> rfkrocktk@rfkrocktk-ubuntu:~$ recordmydesktop --no-sound
Initial recording window is set to:
X:0   Y:0    Width:1280    Height:800
Adjusted recording window is set to:
X:0   Y:0    Width:1280    Height:800
Your window manager appears to be Metacity

Initializing...
Capturing!
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7aac767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb7aac8b1]
#2 /usr/lib/libX11.so.6 [0xb7f05421]
#3 /usr/lib/libX11.so.6(XNextEvent+0x74) [0xb7eed734]
#4 recordmydesktop [0x8051776]
#5 /lib/tls/i686/cmov/libpthread.so.0 [0xb7dcb4fb]
#6 /lib/tls/i686/cmov/libc.so.6(clone+0x5e) [0xb7b84e5e]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7aac767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb7aac81e]
#2 /usr/lib/libX11.so.6 [0xb7f05518]
#3 /usr/lib/libX11.so.6(_XReply+0x140) [0xb7f06200]
#4 recordmydesktop [0x804b159]
#5 recordmydesktop [0x8051083]
#6 recordmydesktop [0x804f21c]
#7 /lib/tls/i686/cmov/libpthread.so.0 [0xb7dcb4fb]
#8 /lib/tls/i686/cmov/libc.so.6(clone+0x5e) [0xb7b84e5e]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7aac767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb7aac8b1]
#2 /usr/lib/libX11.so.6 [0xb7f05421]
#3 /usr/lib/libX11.so.6(XNextEvent+0x74) [0xb7eed734]
#4 recordmydesktop [0x8051776]
#5 /lib/tls/i686/cmov/libpthread.so.0 [0xb7dcb4fb]
#6 /lib/tls/i686/cmov/libc.so.6(clone+0x5e) [0xb7b84e5e]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7aac767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb7aac81e]
#2 /usr/lib/libX11.so.6 [0xb7f05518]
#3 /usr/lib/libX11.so.6(_XReply+0x140) [0xb7f06200]
#4 recordmydesktop [0x804b159]
#5 recordmydesktop [0x8051083]
#6 recordmydesktop [0x804f21c]
#7 /lib/tls/i686/cmov/libpthread.so.0 [0xb7dcb4fb]
#8 /lib/tls/i686/cmov/libc.so.6(clone+0x5e) [0xb7b84e5e]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7aac767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb7aac8b1]
#2 /usr/lib/libX11.so.6 [0xb7f05421]
#3 /usr/lib/libX11.so.6(XNextEvent+0x74) [0xb7eed734]
#4 recordmydesktop [0x8051776]
#5 /lib/tls/i686/cmov/libpthread.so.0 [0xb7dcb4fb]
#6 /lib/tls/i686/cmov/libc.so.6(clone+0x5e) [0xb7b84e5e]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7aac767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb7aac81e]
#2 /usr/lib/libX11.so.6 [0xb7f05518]
#3 /usr/lib/libX11.so.6(_XReply+0x140) [0xb7f06200]
#4 /usr/lib/libXfixes.so.3(XFixesGetCursorImage+0xb8) [0xb7c47608]
#5 recordmydesktop [0x804e7e6]
#6 /lib/tls/i686/cmov/libpthread.so.0 [0xb7dcb4fb]
#7 /lib/tls/i686/cmov/libc.so.6(clone+0x5e) [0xb7b84e5e]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7aac767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb7aac8b1]
#2 /usr/lib/libX11.so.6 [0xb7f05421]
#3 recordmydesktop [0x804b174]
#4 recordmydesktop [0x8051083]
#5 recordmydesktop [0x804f21c]
#6 /lib/tls/i686/cmov/libpthread.so.0 [0xb7dcb4fb]
#7 /lib/tls/i686/cmov/libc.so.6(clone+0x5e) [0xb7b84e5e]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7aac767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb7aac81e]
#2 /usr/lib/libX11.so.6 [0xb7f05518]
#3 /usr/lib/libX11.so.6 [0xb7f05cb2]
#4 /usr/lib/libX11.so.6 [0xb7f05fcf]
#5 /usr/lib/libX11.so.6(XNextEvent+0x8b) [0xb7eed74b]
#6 recordmydesktop [0x8051776]
#7 /lib/tls/i686/cmov/libpthread.so.0 [0xb7dcb4fb]
#8 /lib/tls/i686/cmov/libc.so.6(clone+0x5e) [0xb7b84e5e]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7aac767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb7aac8b1]
#2 /usr/lib/libX11.so.6 [0xb7f05421]
#3 /usr/lib/libX11.so.6(XNextEvent+0x74) [0xb7eed734]
#4 recordmydesktop [0x8051776]
#5 /lib/tls/i686/cmov/libpthread.so.0 [0xb7dcb4fb]
#6 /lib/tls/i686/cmov/libc.so.6(clone+0x5e) [0xb7b84e5e]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7aac767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb7aac81e]
#2 /usr/lib/libX11.so.6 [0xb7f05518]
#3 /usr/lib/libX11.so.6(_XReply+0x140) [0xb7f06200]
#4 /usr/lib/libXfixes.so.3(XFixesGetCursorImage+0xb8) [0xb7c47608]
#5 recordmydesktop [0x804e7e6]
#6 /lib/tls/i686/cmov/libpthread.so.0 [0xb7dcb4fb]
#7 /lib/tls/i686/cmov/libc.so.6(clone+0x5e) [0xb7b84e5e]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7aac767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb7aac8b1]
#2 /usr/lib/libX11.so.6 [0xb7f05421]
#3 /usr/lib/libX11.so.6(XNextEvent+0x74) [0xb7eed734]
#4 recordmydesktop [0x8051776]
#5 /lib/tls/i686/cmov/libpthread.so.0 [0xb7dcb4fb]
#6 /lib/tls/i686/cmov/libc.so.6(clone+0x5e) [0xb7b84e5e]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7aac767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb7aac81e]
#2 /usr/lib/libX11.so.6 [0xb7f05518]
#3 /usr/lib/libX11.so.6(_XReply+0x140) [0xb7f06200]
#4 recordmydesktop [0x804b159]
#5 recordmydesktop [0x8051083]
#6 recordmydesktop [0x804f21c]
#7 /lib/tls/i686/cmov/libpthread.so.0 [0xb7dcb4fb]
#8 /lib/tls/i686/cmov/libc.so.6(clone+0x5e) [0xb7b84e5e]
Saved 197 frames in a total of 240 requests
Shutting down......
Encoding started!
This may take several minutes.
Pressing Ctrl-C will cancel the procedure (resuming will not be possible, but
any portion of the video, which is already encoded won't be deleted).
Please wait...
[100%] 
Encoding finished!
Wait a moment please...
   
Done.
Written 1800612 bytes
(1800612 of which were video data and 0 audio data)

Cleanning up cache...
Done!!!
Goodbye!


Can anyone help me debug this?

---

### Post by halovivek on 2009-02-05
i will try this one in home :)

---

### Post by mwwoj on 2009-03-09
> **iovar said:**
> @BLTicklemonster:
If it is a relatively light game, on a low resoulution and on a strong pc, then maybe...

I got this on my p4 3.2 on 640x480@15 fps:
[http://video.google.com/videoplay?docid=-807141800269084169&hl=en](http://video.google.com/videoplay?docid=-807141800269084169&hl=en)
running the program like this:
recordmydesktop --quick-subsampling --zero-compression --full-shots --with-shared -windowid  0x4000076 -o warzone2100-1.ogg -v_quality 24 -s_quality 4    

(to get a windowid you need to run xwininfo first)

As you see a-v sync is bad(sound stays 2-3 seconds ahead)
It also needed about 1gb of free space for the 5 minute recording.


Other than that, to anyone using this program, or istanbul,
you can upload ogg/theora directly on google video. 
I don't know why they don't mention it on the accepted formats, but it works fine.

How you managed to record sound?

I do not know why I cannot record sound at all..

Do I need sth extra?

I tried via microphone/usb microphone/jack mocrophone
... all works with othe programs  (skype etc.)

---

### Post by mdshaver on 2009-05-14
I think my difficulty with recording sound stems from a bug in the gnome volume control. My interest is simply to record audio from an online presentation along with the video so I do not have any use for recording from the mic. In the recordmyDesktop online documentation, it mentions that a wave/mix/capture option must be selected in the Gnome Volume Control. I did select Capture but it seems that when I toggle it on and close it, the program does not remember it. Everytime I open the Gnome Volume Control, the capture option is de-selected. Recording video seems to work fine but I'd like to have audio too.

---

### Post by Arup on 2009-05-14
Select ALSA in sound for recording.

---

### Post by mdshaver on 2009-05-15
I'm sorry buy could you please be more specific. I don't think selecting ALSA is the issue but if you could provide more detail I would appreciate it.

---

### Post by loell on 2009-05-15
i've had successes before in recording all sound output  by using **gnome-alsamixer**

---

### Post by Arup on 2009-05-15
> **loell said:**
> i've had successes before in recording all sound output  by using **gnome-alsamixer**

Same here, I have had no issues at all either using built in Realtek or my old Yamaha Waveforce DS-XG.

---

### Post by Adler on 2009-05-17
Arup,

I'm now running Ubuntu 9.04. I just switched back after running openSuSE11.1

In the past I'd done a lot of compiz-Fusion 3D [YouTube]("http://www.youtube.com/user/jjmacey") videos with Linux Mint running recordMyDesktop.

What apps have you downloaded?

Best Regards,

JJMacey

---

### Post by dipaish on 2009-05-19
To install record my desktop in Ubuntu Jaunty

deep@deep-laptop:~$ sudo apt-get install gtk-recordmydesktop

After installing you can record and save the recorded video which is in ogv format which can be a headache. Forget going to terminal and typing codes. Instead read the tutorial at this [site]("http://info123.org/tutorials/54-how-to-convert-ogv-file-format-to-avi-or-any-other-format-") 
[URL="http://www.youtube.com/watch?v=6zdlanIuz7Y"]
Click here to Watch the video to change the file from ogv to other formats:[/URL]

---

### Post by Arup on 2009-05-19
> **Adler said:**
> Arup,

I'm now running Ubuntu 9.04. I just switched back after running openSuSE11.1

In the past I'd done a lot of compiz-Fusion 3D [YouTube]("http://www.youtube.com/user/jjmacey") videos with Linux Mint running recordMyDesktop.

What apps have you downloaded?

Best Regards,

JJMacey


Adler,

I have downloaded the usual Audacity, Avidemux, WinFF as well as Skype, Google Earth etc. All from the repos so far, haven't used getdeb yet. I have nvidia as well as dual GPU ATI 4850 but I don't use Compiz etc. Just have metacity on.

---

### Post by Adler on 2009-05-21
Hi All,

I remember mencoder as part of the packages that I'd downloaded in the past, and used terminal to convert the ogg / vorbis output to .avi with

> Here's the how-to. Firstly you'll need mencoder installed. Get it through Synaptic.

Then in shell run either of these two commands:

For PAL:
Code:
mencoder -o output_file.avi -ovc lavc -lavcopts vbitrate=5000:vhq -ffourcc DX50 -oac pcm -srate 48000 -ofps 25 /home/jjmacey/OpenSuse11.0LoveWillGetYouInTheEnd.ogv

For NTSC:
Code:
mencoder -o output_file.avi -ovc lavc -lavcopts vbitrate=5000:vhq -ffourcc DX50 -oac pcm -srate 48000 -ofps 29.97 your_movie.mov

I assume your Vid is in your Home file. Then where it says "your_movie.mov", change it to /home/whatever/your movie name. Click, and your vid gets converted to an .avi file. It might take a minute or two. The .avi should land in your Home file.

Best Regards,

JJMacey

---

### Post by Mauri24 on 2009-05-31
I use the      [recordmydesktop_0.3.0-1_i386.deb]("http://ubuntuforums.org/attachment.php?attachmentid=19714&d=1164066359") version... This version have a GUI or not? because i can't install the latest version ;) (some error)

EDIT: the update manager have updated the recordmydesktop application, now I dunno wich version it is, btw I can't find it in the application bar (the gui version I mean, with the terminal it works well ;))


LoooooL never mind, just did this for the GUI ;)

```
[COLOR=#008000]sudo apt-get install gtk-recordmydesktop[/COLOR]
```

---

### Post by ActiveFrost on 2009-06-06
Does anybody know how to set this up so I could use auto-zoom feature ( like on Camtasia, etc. - otherwise, it's impossible to read the text and other things on YouTube ) ?

---

### Post by tad1073 on 2009-06-06
how can I get recordMyDesktop to recognize my sound card

---

### Post by Winterheart on 2009-10-05
I have an nVidia 2200+ with 128 MB video RAM and recordmydesktop doesn't work well. Is the cause lost because my video card or I can still change some options to make it work?

---

### Post by OpenGuard on 2009-10-07
Is there a way to enable some kind of auto-zoom like in Camtasia ( perfect feature for YouTube-size videos ) ?

---

### Post by Arup on 2009-10-08
> **Adler said:**
> Arup,

I'm now running Ubuntu 9.04. I just switched back after running openSuSE11.1

In the past I'd done a lot of compiz-Fusion 3D [YouTube]("http://www.youtube.com/user/jjmacey") videos with Linux Mint running recordMyDesktop.

What apps have you downloaded?

Best Regards,

JJMacey


Hi JJMacey,

I have downloaded quite a few apps, are you looking for something specific?

regards
Arup

---

### Post by nicklausmichael on 2009-11-03
Heres mine! lol
[http://www.youtube.com/watch?v=EHVI5--_sxE](http://www.youtube.com/watch?v=EHVI5--_sxE)

---

### Post by ctsdownloads on 2009-11-05
Good luck if you are using ATI proprietary drivers! :mad:

```
cat ~/gtk-recordMyDesktop-crash.log
#This is the command given at initialization:
recordmydesktop -o /home/matt/Desktop/save -fps 15 -channels 2 -freq 22050 -device pulse -v_quality 63 -s_quality 10 -workdir /tmp --overwrite 


#recordMyDesktop stderror output:
Initial recording window is set to:
X:0   Y:0    Width:1280    Height:1024
Adjusted recording window is set to:
X:0   Y:0    Width:1280    Height:1024
Your window manager appears to be compiz


Detected 3d compositing window manager.
Reverting to full screen capture at every frame.
To disable this check run with --no-wm-check
(though that is not advised, since it will probably produce faulty results).

Initializing...
Buffer size adjusted to 4096 from 4096 frames.
Opened PCM device pulse
Recording on device pulse is set to:
2 channels at 22050Hz
X Error: BadAccess (attempt to access private resource denied)
Bad Access on XGrabKey.
Shortcut already assigned.
X Error: BadAccess (attempt to access private resource denied)
Bad Access on XGrabKey.
Shortcut already assigned.
X Error: BadAccess (attempt to access private resource denied)
Bad Access on XGrabKey.
Shortcut already assigned.
X Error: BadAccess (attempt to access private resource denied)
Bad Access on XGrabKey.
Shortcut already assigned.
Capturing!
```

It's even worse with Copiz-Fusion disabled...running the cat log actually starts the recordmydesktop backend! WTF? Thanks ATI!

---

### Post by Puzzled Guy on 2009-12-03
How come, of all the videos I saw, mine seems to have a relatively better resolution?

Anyway, if your videos have a bad resolution when uploaded to YouTube, try this procedure:

Type in the terminal:
```
recordmydesktop  nameofoutput
```
If you want to have a delay of 5 seconds before it starts recording, type:
```
recordmydesktop -delay 5  -o nameofoutput
```

To stop the recording, press ctr + c in the terminal.
Wait for the processing to complete.
Can't find the video? Look in your home directory
EX: if you change the directory to /home/user/Videos before you record, your video gets saved in the "Videos" directory, got it?

.ogv looks quite bad on YouTube so, convert it to .avi
Open the Terminal again in the directory where you saved the video in and enter the command:
```
mencoder -idx input.ogv -ovc lavc -oac mp3lame -o output.avi
```
change input.ogv to the name of the file to convert and output.avi to the name of the converted file. NOTE: You have to install mencoder first if it isn't already (it is very good at preserving the video quality)

The resolution will be the same after the conversion
See my video on youtube: [http://www.youtube.com/watch?v=7ySTp0_NLKo](http://www.youtube.com/watch?v=7ySTp0_NLKo)
And compare the resolution with something like this: [http://www.youtube.com/watch?v=CaJi580BAb8](http://www.youtube.com/watch?v=CaJi580BAb8)

No offense pedalcat, just needed a video to demonstrate with...:p

Oh, by the way, tell me if it is any better. Send me a private message

---

### Post by suniyo on 2009-12-19
I have a strange problem, that video and audio is not synced with each other even if i keep my framerate and freuency high. Do anyone here knows why it is not syncing?? Pls reply as I have followed the thread and have read everything but have this one single problem.
Thanks in advance.

---

### Post by Zetheroo on 2010-01-18
As suniyo said the video and audio are out of sync. I have tried all kinds of settings and have run it from the terminal as well with the same annoying results. 

Istanbul on the other hand does not have issues with audio and video sync ... but it lacks some key features. 

Xvidcap does not record audio for me.

I have also done screencasting with ffmpegg but that leaves me with massive files and again ffmpeg lacks many key features of creating a screencast.

Screencasting in Linux seems pretty hopeless ... :(

We desperately need a way to get this working in Linux.

---

### Post by wayfarer_boy on 2010-01-20
I found that I had audio sync problems (in both compiz and metacity) when I used -delay in recordmydesktop.  I removed the -delay option, and audio synced fine when tested in both composite managers.  I now use the sleep command instead:

```
sleep 5; recordmydesktop options...
```

---

### Post by nanotube on 2010-01-20
> **wayfarer_boy said:**
> I found that I had audio sync problems (in both compiz and metacity) when I used -delay in recordmydesktop.  I removed the -delay option, and audio synced fine when tested in both composite managers.  I now use the sleep command instead:

```
sleep 5; recordmydesktop options...
```

i suggest you file that bug with the recordmydesktop project. seems like it's a simple oversight-type bug that should be easily fixable.

---

### Post by Zetheroo on 2010-01-20
Ok, I have fixed it up and its working perfectly now! :D

[HERE]("http://techiesrus.wordpress.com/2010/01/19/another-look-at-gtk-recordmydesktop-in-ubuntu-9-10/") is what I did!

---

### Post by wayfarer_boy on 2010-01-22
> **nanotube said:**
> i suggest you file that bug with the recordmydesktop project. seems like it's a simple oversight-type bug that should be easily fixable.

Filed at [https://bugs.launchpad.net/ubuntu/+source/recordmydesktop/+bug/511113](https://bugs.launchpad.net/ubuntu/+source/recordmydesktop/+bug/511113)

---

### Post by nanotube on 2010-01-22
> **wayfarer_boy said:**
> Filed at [https://bugs.launchpad.net/ubuntu/+source/recordmydesktop/+bug/511113](https://bugs.launchpad.net/ubuntu/+source/recordmydesktop/+bug/511113)

cool, let's see how long it takes for someone to take notice... :)

---

### Post by Skippy le Grand Gourou on 2010-01-27
To people having sound issues, make sure that the correct channel is enabled for capture in alsamixer*: type "alsamixer" in a terminal, then press [tab] or F4 to go to the capture devices panel, then check that the right channel (for instance "Mix" to record all sounds) has the word "CAPTUR" in red at its bottom. If not, select the channel with arrows and press [space]. Exit with [Esc], retry to record and enjoy.

BTW note that ffmpeg is also able to capture the desktop*:
```
ffmpeg -f oss -i /dev/audio -f x11grab -s 320x240 -r ntsc -i :0.0 capture.mpg
```

---

### Post by hachel on 2010-01-29
hi there,

I've been able to capture my entire desktop comfortably with rmd.
But just now I tried it again and the output was really sloppy, only showing a frame every 4 to 5 seconds on average.
Now, neither while recording nor while playing the output-file (a 1280x1024 theora) was my cpu anywhere near the 10% (thats 10, not 100) hurdle.

So why might that be? Any ideas?

PS: I can record my desktop with ffmpeg without any problems.

---

### Post by nanotube on 2010-01-30
> **Skippy le Grand Gourou said:**
> To people having sound issues, make sure that the correct channel is enabled for capture in alsamixer*: type "alsamixer" in a terminal, then press [tab] or F4 to go to the capture devices panel, then check that the right channel (for instance "Mix" to record all sounds) has the word "CAPTUR" in red at its bottom. If not, select the channel with arrows and press [space]. Exit with [Esc], retry to record and enjoy.

BTW note that ffmpeg is also able to capture the desktop*:
```
ffmpeg -f oss -i /dev/audio -f x11grab -s 320x240 -r ntsc -i :0.0 capture.mpg
```

hey, that works rather nicely, too - thanks for the tip :)

---

### Post by kung fu buntu on 2010-02-02
**NOT WORKING**... driving me insane!!!

> recordmydesktop --on-the-fly-encoding -v_quality 63  -v_bitrate 2000000 -fps 20 --full-shots  --no-sound  -workdir .  -o foo.ogv

I followed the tips in [http://thefunkcorner.blogspot.com/2009/05/trials-with-recordmydesktop.html](http://thefunkcorner.blogspot.com/2009/05/trials-with-recordmydesktop.html)
I tried lots of stuff and nothing worked properly.

And for the moment, I'm not even talking about audio... just some decent video capture.

The problem is that the recorded video seems like it's a fast forward recording. As if 10 seconds become one second.

If I change the -fps to something like 8, I can get a "almost decent" recording with slow movement on the screen.


What I would like to be able:
to open a video file in smplayer and record the desktop as it plays, both video and sound.


Any help?

---

### Post by verb3k on 2010-02-03
> **kung fu buntu said:**
> **NOT WORKING**... driving me insane!!!



I followed the tips in [http://thefunkcorner.blogspot.com/2009/05/trials-with-recordmydesktop.html](http://thefunkcorner.blogspot.com/2009/05/trials-with-recordmydesktop.html)
I tried lots of stuff and nothing worked properly.

And for the moment, I'm not even talking about audio... just some decent video capture.

The problem is that the recorded video seems like it's a fast forward recording. As if 10 seconds become one second.

If I change the -fps to something like 8, I can get a "almost decent" recording with slow movement on the screen.


What I would like to be able:
to open a video file in smplayer and record the desktop as it plays, both video and sound.


Any help?

You can use FFmpeg:
[http://ubuntuforums.org/showthread.php?t=1392026](http://ubuntuforums.org/showthread.php?t=1392026)

---

### Post by hachel on 2010-02-03
> **kung fu buntu said:**
> **NOT WORKING**... driving me insane!!!



I followed the tips in [http://thefunkcorner.blogspot.com/2009/05/trials-with-recordmydesktop.html](http://thefunkcorner.blogspot.com/2009/05/trials-with-recordmydesktop.html)
I tried lots of stuff and nothing worked properly.

And for the moment, I'm not even talking about audio... just some decent video capture.

The problem is that the recorded video seems like it's a fast forward recording. As if 10 seconds become one second.

If I change the -fps to something like 8, I can get a "almost decent" recording with slow movement on the screen.


What I would like to be able:
to open a video file in smplayer and record the desktop as it plays, both video and sound.


Any help?

that sounds like the same problem I described a few posts before. If it is, than it has to do with the new version of libtheora. Apparently it handles things differently and all programs using it have to update the way they're handling it.
Someone created a bug-report on the sourceforge-page of recordmydesktop [http://sourceforge.net/tracker/?func=detail&aid=2888673&group_id=172357&atid=861428](http://sourceforge.net/tracker/?func=detail&aid=2888673&group_id=172357&atid=861428)
And its widley discussed here within fedora: [https://bugzilla.redhat.com/show_bug.cgi?id=525155](https://bugzilla.redhat.com/show_bug.cgi?id=525155)

Until the author updates rmd changing the bitrate to 200000 worked for me: ```
recordmydesktop --v_bitrate 2000000
```.

By the way, I switched to ffmpeg, see link above. It gives me much better results in the quality of the video.

---

### Post by kung fu buntu on 2010-02-07
> **hachel said:**
> Until the author updates rmd changing the bitrate to 200000 worked for me: ```
recordmydesktop --v_bitrate 2000000
```.That didn't work for me. Nor 200,000 nor 2,000,000 (you have said both values in your messsage).

> **hachel said:**
> By the way, I switched to ffmpeg, see link above. It gives me much better results in the quality of the video.
I'm also trying to go that way. Well, I already can, but there are still some pending issues.

In any case, I had already done several screencasts using recordmydesktop and they're all choppy (ie, weird frame rates) and eat up lot of HDD. I would like to convert them.

I tried > ffmpeg -i input.ogg  -vcodec libx264 -vpre hq -crf 22 -threads 0    out.mkv but the resulting video still ends up with weird frame rates, and in particular, it confuses mplayer which thinks it's 24 minutes when it's only about 12.
The fact is that, if RMD and libtheora didn't sucked, the proper recording would have 24 minutes. But isntead it gets "fast play" and only takes about half the time.
How do I fix this?

---

### Post by Retrograde77 on 2010-03-09
> **hachel said:**
> that sounds like the same problem I described a few posts before. If it is, than it has to do with the new version of libtheora. Apparently it handles things differently and all programs using it have to update the way they're handling it.
Someone created a bug-report on the sourceforge-page of recordmydesktop [http://sourceforge.net/tracker/?func=detail&aid=2888673&group_id=172357&atid=861428](http://sourceforge.net/tracker/?func=detail&aid=2888673&group_id=172357&atid=861428)
And its widley discussed here within fedora: [https://bugzilla.redhat.com/show_bug.cgi?id=525155](https://bugzilla.redhat.com/show_bug.cgi?id=525155)

Until the author updates rmd changing the bitrate to 200000 worked for me: ```
recordmydesktop --v_bitrate 2000000
```.

By the way, I switched to ffmpeg, see link above. It gives me much better results in the quality of the video.

Thanks for that :) been having a nightmare trying to get the gui one to work, or any of the screencap apps to be honest but this works perfect :)

---

### Post by martyboy on 2010-05-29
Hello,

New linux user here, have to say I'm loving Ubuntu.

OK, heres my problem, ive installed a couple of games using the software center and i also installed the recordmydesktop app so I could record some game footage for youtube, however when I start recording the game window everything completely slows down and the game becomes unplayable, this also happens when I try to record with xvidcap.

I have ubuntu installed along side windows vista (using the wubi installer), I have no problems recording PC gameplay using camtasia. Here are my system specs.

Total amount of system memory 4.00 GB RAM 
Intel core 2 duo processor 
Display adapter type ATI Radeon HD 2400 PRO 
  Total available graphics memory 1535 MB 
        Dedicated graphics memory 128 MB 
        Dedicated system memory 0 MB 
        Shared system memory 1407 MB 
  Display adapter driver version 8.612.0.0 
  Primary monitor resolution 1024x768 

the system info I got from vista as im not sure how to get sytem info like that on ubuntu.

I have installed/configured the third party driver for my ati card ( i think ).

What do I need to make game recording smooth? new graphics card or do i need a new driver?

Thanks for your help.

---

### Post by triva911 on 2010-08-08
I now installed recordmydesktop via ubuntu software center ,and when I record my desktop I have black video with cursor on export .....
I have installed graphic driver , cairo-dock , google-widgets , compiz .....
And I have now problem when i need to take Screenshot ... i have a black picture with curosor on export ...
I am ubuntu 10.04 user...
... how to fix it ... PLZ HELP

---

### Post by karmila on 2010-09-05
I'm trying to record some actions with compiz using gtk-recordmydesktop  and i satisfied with the quality of the resulted video. But one think that still bother me is I can't drag window between workspaces in expo mode. Yes expo is appear but i can't drag any window at all. Any idea?

---

### Post by AlexanderDGreat on 2010-09-07
@trivia & karmila - maybe you should post this in multimedia, some people have more knowledge there.

---

### Post by gewone on 2010-11-09
I have installed recordmydesktop plus gtk-recordmydesktop packages.
Having issues aswell. Simply said, program freezes every time I try encode.

```
root@buntbox:~# recordmydesktop foobar.ogv
Initial recording window is set to:
X:0   Y:0    Width:1920    Height:1080
Adjusted recording window is set to:
X:0   Y:4    Width:1920    Height:1072
Your window manager appears to be compiz


Detected compositing window manager.
Reverting to full screen capture at every frame.
To disable this check run with --no-wm-check
(though that is not advised, since it will probably produce faulty results).

Initializing...
Buffer size adjusted to 4096 from 4096 frames.
Opened PCM device default
Recording on device default is set to:
1 channels at 22050Hz
Capturing!
^C
*********************************************

Cached 3 MB, from 353 MB that were received.
Average cache compression ratio: 99.0 %

*********************************************
Saved 45 frames in a total of 46 requests
Shutting down..^C^C

```

Then it freezes. I actually have to grep PID and kill (with -9 instruction) to get rid of it. My computer should be fine. AMD Phenom II 945 3GHz, 4GB DDR3.

Any ideas? Xvidcap tends to work, although I'd like the feature just having to click a window to get it properly targeted, which recordmydesktop provides.

---

### Post by ssri on 2010-11-22
> **suoko said:**
> RE: Convert files in tmp?
By: John Varouhakis (iovarProject Admin) - 2007-11-22 08:24
I'm afraid that there is no standard procedure on rescuing sessions 
(it is planned for 0.3.7 though)
Well, recordmydesktop is up to 0.3.8 as of this post and I just wanted to tell others about the rescue option that has been included since 0.3.7.  I suffered a segfault when recording a screencast and managed to recover the recorded portion (along with its audio) via this command:
```
$ recordmydesktop --rescue path_to_data
```

---

### Post by ilap on 2010-11-28
I think the gtk-recormydesktop and recordmydesktop is the most buggies and annoying software I ever used. I just wanted to record a window with this "great" sw, but I could not do anything at all. Oooh, understand so, I should be more specific.:)
I did the following in a fresh maverick install (not hacked at all).
1. Applications -> Sound -> Desktop Record
2. Select the window to capture
3. Start record and all of the Sudden the gtk-r... window disappeared and can not be seen anywhere nor in the taskbar so nowhere.

Ooooh, it was running, therefore I killed the recordmydesktop /w -SIGTERM signal. No any ~out.ogg output generated. No, probs I will use the --rescue options for the /tmp/rmD-XXXX dir, which came back /w a SEGFAULT at the end of processing the cache files. So, congratulations, very useful SW it should just work out of box.:) But, what does it do I have no clue.

---

### Post by datacrusher on 2011-01-27
Im verry annoyed with this app since i have a very specific usage for it, i need to record using jack audio inputs. the gui is very promissing, but the errors are random and impossible to troubleshoot, in a mailing list i saw a bug that reports that trying many times one of them the capture starts, so i pointed that way, and fine tuned a command line following the .log it generates in my user folder. 

some code:
```
recordmydesktop -o /home/guerrilha/Vídeos/rade --freq 44100 --overwrite --use-jack bridge-5336:monitor_1 bridge-5336:monitor_4
Initial recording window is set to:
X:920   Y:0    Width:104    Height:768
Adjusted recording window is set to:
X:912   Y:0    Width:112    Height:768
Your window manager appears to be Metacity

Initializing...
Capturing!
^C
*********************************************

Cached 0 MB, from 42 MB that were received.
Average cache compression ratio: 99.0 %

*********************************************
Saved 130 frames in a total of 129 requests
Shutting down.....
STATE:ENCODING
Encoding started!
This may take several minutes.
Pressing Ctrl-C will cancel the procedure (resuming will not be possible, but
any portion of the video, which is already encoded won't be deleted).
Please wait...
[100%] 
Encoding finished!
Wait a moment please...
   
Done.
Written 56994 bytes
(56175 of which were video data and 819 audio data)

Cleanning up cache...
Done!!!
Goodbye!

```

this is one line that recorded, but it grabs a tiny bit of my right side on the screen. if I try to set the height width by hand it just wont work.

```
guerrilha@dtcrshr:~/Vídeos$ recordmydesktop -o /home/guerrilha/Vídeos/radio -x 0 -y 0 --width 800 --height 600 --freq 44100 --overwrite --use-jack bridge-5336:monitor_1 bridge-5336:monitor_4
Window size specification out of bounds!(current resolution:1152x864)

```

when it works, it gets random values for X, Y and H, W. Is there a REAL way to set this size by hand? out of clues here, and the gui dont work at all.

---

### Post by datacrusher on 2011-01-27
this launchpad bug report follows this errors: 
[https://bugs.launchpad.net/ubuntu/+source/recordmydesktop/+bug/621188](https://bugs.launchpad.net/ubuntu/+source/recordmydesktop/+bug/621188)

---

### Post by kkapil on 2011-02-24
> **loell said:**
> [SIZE=4]**[http://recordmydesktop.sourceforge.net](http://recordmydesktop.sourceforge.net)**[/SIZE]
a nice screen/desktop video recorder, try it :)

:) 
                                              Thaks buddy:D

---

### Post by Dlambert on 2011-03-09
Works in 10.10! thanks

---

### Post by Dlambert on 2011-03-09
> **martyboy said:**
> Hello,

New linux user here, have to say I'm loving Ubuntu.

OK, heres my problem, ive installed a couple of games using the software center and i also installed the recordmydesktop app so I could record some game footage for youtube, however when I start recording the game window everything completely slows down and the game becomes unplayable, this also happens when I try to record with xvidcap.

I have ubuntu installed along side windows vista (using the wubi installer), I have no problems recording PC gameplay using camtasia. Here are my system specs.

Total amount of system memory 4.00 GB RAM 
Intel core 2 duo processor 
Display adapter type ATI Radeon HD 2400 PRO 
  Total available graphics memory 1535 MB 
        Dedicated graphics memory 128 MB 
        Dedicated system memory 0 MB 
        Shared system memory 1407 MB 
  Display adapter driver version 8.612.0.0 
  Primary monitor resolution 1024x768 

the system info I got from vista as im not sure how to get sytem info like that on ubuntu.

I have installed/configured the third party driver for my ati card ( i think ).

What do I need to make game recording smooth? new graphics card or do i need a new driver?

Thanks for your help.


This is completely normal. think of it this way, the game is being rendered and has fps, and the RMD is recording that as its being rendered at a certain amount of fps, so the graphics card is running double.

---

### Post by gstla on 2011-03-10
Apologies for this newbie question, but where exactly is the output file located? I know that it's been made and encoded, I just can't find it o_O.

---

### Post by Hero1969 on 2011-03-10
Should be /home.

---

### Post by ahso4271 on 2011-04-28
still on 10.04 how to record a window only? ie how can i get the window id?
Or has xvidcap etc. been fixed to work in 11.04?
Thanks

Ok recorded fine but now how to convert to avi?

---

### Post by Cfhs_1 on 2011-05-15
> **ahso4271 said:**
> still on 10.04 how to record a window only? ie how can i get the window id?
Or has xvidcap etc. been fixed to work in 11.04?
Thanks

Ok recorded fine but now how to convert to avi?

At the bottow left corner of the program there is a "Select Window" button, click that, then click anywhere in the window you want to record. You can also go into the "advanced" dialogue box and in the Misc tab there is an option for selected recording windows to she the metacity,compiz, etc window border or not. Also I would recommend disabling the outline capture area on screen option when recording one select windows because somethimes the outline will show up on the recorded video. Hope this helps, happy recording!

Regards,
NCB

As for converting to AVi, I'd go with Mencoder, or ffmpeg. Here is a good guide:
[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

---

### Post by jman4117 on 2011-05-23
Does anyone know what would cause the CLI version of this app stop recording the audio after about 5-7min? It seems to do this about 50% of the time. I don't know if the GUI version does this or not as I can't get it to record properly. I really need an app to screencast up to 30min at a time with sound and this is the only one I've managed to have work at all.

---

### Post by Skyper17 on 2011-06-14
No 64 Bit :(

---

### Post by MrSS on 2011-06-15
Thanks! I rally want to share my tutorials using screen capturing apps.

---

### Post by altjx on 2011-08-28
How come I'm the only one it seems like that's having a problem getting it to encode? I've been sitting at 0% for about 2-3 minutes now. Recorded a 10-15 second video.
Been sitting at this for 15 minutes now... 
```
alt0n@alt0n-linux:~$ recordmydesktop --quick-subsampling
Initial recording window is set to:
X:0   Y:0    Width:1920    Height:1080
Adjusted recording window is set to:
X:0   Y:4    Width:1920    Height:1072
Your window manager appears to be Compiz


Detected compositing window manager.
Reverting to full screen capture at every frame.
To disable this check run with --no-wm-check
(though that is not advised, since it will probably produce faulty results).

Initializing...
Buffer size adjusted to 4096 from 4096 frames.
Opened PCM device default
Recording on device default is set to:
1 channels at 22050Hz
Capturing!
^C
*********************************************

Cached 23 MB, from 533 MB that were received.
Average cache compression ratio: 95.6 %

*********************************************
Saved 68 frames in a total of 69 requests
Shutting down..

```

---

### Post by Cosmopolitan1 on 2011-09-09
Hello guys,

The program works but I can't stop recording.
Before it the stop rec button appeared but now I don't have it anymore.
The shortcut is also not working ctrl+c.
Any idea what to do? ):P

---

### Post by cprofitt on 2011-09-13
I have made a record my desktop tutorial [here]("http://www.youtube.com/watch?v=A0Tn3Z8OklQ")

I hope this helps update this tutorial and helps people looking to do this under 11.04

---

### Post by Goofball Jungle on 2011-11-08
Hey Guys

I've installed the packages and it starts and records. The only problem I'm experiencing is the movie is a bit choppy, I changed the frames p/s but I know that isn't the solution. 

The real problem that's bothering me now is the fact that I can't properly record my dual monitor desktop. The measurements are 1080x3840 and I am currently running Maverick.

Ideas, solutions love to hear em.

---

### Post by ahso4271 on 2012-04-19
cannot get sound via inline. Any help?

---

### Post by leeauteprep on 2012-06-27
i do record my desktop using ezvid free screen recorder for windows. it can be a great alternative if you want. i used it a lot and so far it performs well and it's also a freeware, so nothin to worry about :D

hmm you can check it out [http://ezvid.com/screen-capture](http://ezvid.com/screen-capture)

---

### Post by 3dmatrix on 2012-10-05
With record my Desktop i get a strange problem - it keeps doing somthing and there is a black rectangular border on the screen (the area being captured) but nothing happens beyond that. q or c or Ctrl+c nothing stops it. If i forcibly try closing all windows that border is still there. The only way is to reboot. And ofcourse i also do not get the screen captured video.

---

### Post by marcus15 on 2012-10-24
Have a nice day, I am using recordmydesctop and the ogv file i want to convert for avi whit mancoder, but i have the folowing error:
Cannot set LAME options, check bitrate/samplerate, some very low bitrates
(<32) need lower samplerates (i.e. -srate 8000).
If everything else fails, try a preset.
Exiting...
what is wrong?

---

### Post by marcus15 on 2012-10-24
Have a nice day, I am using recordmydesctop and the ogv file i want to  convert for avi whit mancoder, but i have the folowing error:
Cannot set LAME options, check bitrate/samplerate, some very low bitrates
(<32) need lower samplerates (i.e. -srate 8000).
If everything else fails, try a preset.
Exiting...
what is wrong?

---

### Post by sdowney717 on 2012-11-20
I can not stop the recording when doing full screen when using gtk-recordmydesktop front end

I get a white bar at top and no ability to use any of the menus.
This is on cinnamon and gnome3 desktops.

What you can do is open a terminal by typing alt-F2
type gnome-terminal
type htop
find the pid number
open a tab
type kill pid number

and then you get control of the machine back
so it is very hard to use this program.
surprised no one else talks about how difficult to stop recording full screen.

---

### Post by sdowney717 on 2012-11-20
I found other people have the same problem.

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=650353](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=650353)

all control of the application is cut off and they have to kill by a shell command like me.

Surprised that there are not more complaints or a fix, so to me seems like not enough users to notice or perhaps this app crashes their system so they reboot and give up. If it is running and recording and you dont do anything, it could fill up your drive.

---

### Post by Jacques Duflos on 2013-03-03
Hello there,
I have a little problem encoding my .ogv file to .avi. It's puzzling because it used to work in Ubuntu 10.x and now I switched to 12.10 it doesn't.
I use the command line 
```
mencoder input.ogv -ovc xvid -oac mp3lame -xvidencopts pass=1 -o output.avi
```
And as a result, every frame that is identical to the one before is deleted. So the video goes twice faster than the sound.
Here is the final message in the terminal :
```
1 duplicate frame(s)!
Pos: 112.3s   1535f ( 7%) 74.52fps Trem:   4min 114mb  A-V:-0.133 [542:84]

1 duplicate frame(s)!
Pos: 113.0s   1545f ( 7%) 74.55fps Trem:   4min 114mb  A-V:-0.133 [539:84]

1 duplicate frame(s)!
Pos: 113.5s   1551f ( 7%) 74.57fps Trem:   4min 114mb  A-V:-0.107 [537:84]

Too many audio packets in the buffer: (4096 in 819846 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.

Flushing video frames.
Writing index...
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.

Video stream:  537.671 kbit/s  (67208 B/s)  size: 7625968 bytes  113.467 secs  1551 frames

Audio stream:   84.661 kbit/s  (10582 B/s)  size: 1206129 bytes  113.972 secs
```

But I can not figure out where to put the -ni option in the code line. I have tried at every places and it did not change a thing.

Any ideas please ?
Jacques

---

