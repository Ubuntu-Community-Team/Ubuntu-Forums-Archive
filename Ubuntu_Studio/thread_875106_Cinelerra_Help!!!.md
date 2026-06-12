---
title: "Cinelerra Help!!!"
date: 2008-07-30
forum: Ubuntu Studio
---

### Post by Stoppelmonster on 2008-07-30
I use Ubuntu Hardy Heron.

I recently installed Cinelerra video editor. It opens, but freezes while opening video files. How can I fix this?

---

### Post by alegallo on 2008-07-31
It would help if you could explain more precisely what's happening.

Does it freeze immediately after opening the app?
In this case, did you install the correct version (I mean, with or without OpenGL enabled, depending on your video card)?

Or does it freeze AFTER opening the app, when you load a clip?
In this case, how big are the clips?

Or does it freeze when you try to re-open a saved .xml file project? 
In this case you should unload the previewed file in the composer window before saving your project. It works for me.

In cases 2 and 3 you can try to delete the .bcast folder in your /home before opening Cinelerra. 
Sometimes it solves some problems, some of the stored settings seem to be buggy on some systems.
It does not affect the program, as it recreates the folder anew every time you open it.

Did you try uninstalling and reinstalling Cinelerra? 
I suggest you to use akirad repos, it works fine for me.

Good luck anyway! ;)

---

### Post by Stoppelmonster on 2008-07-31
I am using Cinelerra 2.1CV. The programs freezes only after I try to load a video clip, usually anywhere from 1Mb to 600Mb, I've tried several different sizes. I will uninstall and try again. I just deleted, the .bcast folder, and still no luck.

---

### Post by Tree MendUs on 2008-07-31
Hi Stoppelmonster,

Please do not remove Cinelerra from your PC.
It will do the trick.
But you will need some tweaking to the settings.

Cinelerra can work with some really massive sized files, so your file size is not likely to be the problem - unless you are working on old gear.
If you've got AMD64, and are running AMD64 (64bit) Ubuntu then gear is definitely not a problem. Though it is very handy to have RAM in excess of 0.5GB. A large swap file is handy also (say 4GB - I have found), if you have low Ram.
Remember to rake notice of the shmmax warning that come sup at the start.

First make sure that the default video settings match the kind of video that you are going to be using (most of the time) (Pal or NTSC).
Second try color systems RBG16 then RGBA16, and work up to find where it starts failing.

Then check your sound settings are roughly CD quality (to keep requirements low on your system), and are using you standard sound card setup (to prevent conflict with sound system that may also be being used by other programs).

I have had Cinelerra working fine with DV AVI type 2 captured through Kino -up tp 30GB in one file. 8 hours, in one hour sections at 13.5GB each.
Quicktime MOV is easy to output, and send to some DVD creators (which convert it). MOV is also said to be good for input files also.

There's some interpolation settings in video/rendering, and these can be played with to get success. If it is crashing, then go for linear (avoid quadratic).

Cinelerra version 3 is being worked on now. It is going to be Lumiera.
[www.lumiera.org](www.lumiera.org)

---

### Post by cotcot on 2008-07-31
I had similar problems with cinelerra until I compiled it meself. I have cinelerra running well now, OpenGL enabled.

Maybe (not sure) this helps : 

--> Settings --> Preferences -->  Playback
Check under Audio Driver the 'Stop playback locks up' check box.

---

### Post by purplepaint on 2008-07-31
> **Tree MendUs said:**
> Cinelerra version 3 is being worked on now. It is going to be Lumiera.
[www.lumiera.org](www.lumiera.org)

Thanks for that.  I'd been looking for info on Lumiera but I hadn't remembered the name.

I've tried Cinelerra a few times and never had any real success.  Until Lumiera is released, I'd recommend LiVES.

Website: [http://lives.sourceforge.net/](http://lives.sourceforge.net/)

Download (so you don't have to compile it from source): [http://www.getdeb.net/app.php?name=lives](http://www.getdeb.net/app.php?name=lives)

I've found myself promoting LiVES a lot recently, but I've been using it for a short while and it really does everything I want it to (but I was impressed by what I saw when Cinelerra loaded up so I'll be looking out for Lumiera which I assume is intended to require less configuration to get it working).

---

### Post by Stoppelmonster on 2008-08-04
Ok, so, I've tried changing setting, galore: No Bueno! I uninstalled Cinelerra, a second time for good. I tried lives, ok, but not what I's looking for. So, I booted Win XP Pro and converted all of my video files to DV.AVI and was able to smoothly load, edit, etc;... with Kino. I need nothing else right now, I guess. A good program to convert any Video format ever into any video format ever... ... ...? Any suggestions? Kino ...FTW!!  xD

---

### Post by Sean4000 on 2008-08-04
I do believe, from what I gathered from the lumiera freenode, that Lumiera will be huge! It is geared to professionals and will be in the same league as FCP and AVID MC.

I cannot wait for this app!

---

### Post by foxfire99 on 2008-08-26
I am also trying very hard to run Cinelerra with Ubuntu 8.04 on an HP DV5000Z laptop.  I have downloaded and installed via synaptic pkg mgr and everything works except that it hangs in the Program Window GUI when I try to do any "Load Backup" ... 

Cinelerra crashes a lot and this function is absolutely essential ... otherwise I would just switch off of WinXP entirely and be using Cinelerra and Ubuntu for professional work producing video presentations and tutorials.

If no one else is getting this to work, I'll give up for now. But if anyone is being successful, please let me know ... I'm willing to reinstall and start over from the beginning! 

I would also be willing to try it with OpenSUSE before returniing to Windows if that is necessary.

Any advice is appreciated,

Thanks!

Phillip

---

### Post by wkulecz on 2008-08-27
I tried installing Lives.  Seemed to go fine, but program doesn't work, or is so slow as to be unusable, maybe if I waited for the loading frames counter to go to zero from 17775 seconds remaining it might have done something :(.

I hate to say this, but if you actually need to edit video just buy the cheapest new Windows PC you can find and get Sony Vegas Video Movie Studio for it.  Should be in the $500 price range and you can actually get video projects done.

Video editing on Linux is barely at Win 95 levels -- meaning if it works you are lucky, if you expect it to work on the hardware you happen to have you are foolish.

The only Cinelerra I've been able to do anything with but crash was on the dynebolic live CD.

---

### Post by pcjunkie on 2008-08-29
I am not having much luck either. Cinelerra crashes on render often, the compositor window has totally flipped out. Complains about ogg imports. I like it and wished it would work but no lick. Others have also crashed.

---

### Post by purplepaint on 2008-08-29
> **wkulecz said:**
> I tried installing Lives.  Seemed to go fine, but program doesn't work, or is so slow as to be unusable, maybe if I waited for the loading frames counter to go to zero from 17775 seconds remaining it might have done something :(.

I hate to say this, but if you actually need to edit video just buy the cheapest new Windows PC you can find and get Sony Vegas Video Movie Studio for it.  Should be in the $500 price range and you can actually get video projects done.

Video editing on Linux is barely at Win 95 levels -- meaning if it works you are lucky, if you expect it to work on the hardware you happen to have you are foolish.

The only Cinelerra I've been able to do anything with but crash was on the dynebolic live CD.

While I agree that video editing on Linux is still in its early stages, I would say that everyone's experience is different.

I've not had a smooth-sailing experience on Windows yet when it comes to video editing.  I'll admit that I've never tried Sony Vegas, but I've used Adobe Premier Pro (which seems to be what many see as the benchmark for video editing software that Linux applications should reach) on PCs with various specs (one of which was top of the range at the time) and I've experienced far more problems - mainly unexplained crashing - than I've had with LiVES on Ubuntu.

---

### Post by maschicago on 2008-08-30
I've been using Cinelerra for about 9 months without a problem.  I've used it under Gutsy and Hardy.  I'm using the AMD64 bit version of the OS, and I've got an NVIDIA 8500 GT card.  Excellent results.  The app crashed a few times under Gutsy, but hasn't under Hardy.

---

### Post by Bartje on 2008-08-30
Cinelerra might be the only real app on Linux for video-editing but now I've experienced some trouble and I really start to hate it !!!

I've made quite some vidoe-work for a dancer, for her show. I've had a harddrive crash a couple of weeks ago, luckily everything was on a different disk. So now I re-installed cinelerra, to continue the work on the video, and I can't open any of the files anymore. Whenever I try to open a file, cinelerra hangs!!! It's not an issue with rights, it's not an issue with corrupted files. It's just f*c*i*g cinelerra that crashes all the time. Now I'm forced to give her the video-recordings, and tell her I can't work for her now!!

My personal work is lost too. I just can't open any of the files anymore. No error-messages, no lost files, no problems with rights... God I hate it!!!

I tried Cinelerra from CVS and the latest, Cinelerra 4 from Heroïne.... 
Now, one last attempt, Cinelerra 4, compiled, not the binary version.
If that doesn't work, bye cinelerra... I hope the new initiative, Lumiera will be a lot better!

---

### Post by Bartje on 2008-08-30
It's over... I can't do the videowork anymore. I've compiled cinelerra 4, from Heroïne, the only result is that the cvs version doesn't work anymore either... yes, really, it has disappeared, even though I did not do 'make install'. It just doesn't open anymore.

I've re-installed from the akirad repositories, and I've got a working version, but 80 % of my cinelerra-files (xml) won't work anymore. Cinelerra just hangs when opening the file, without any error message ... 

Bye cinelerra, I'll have to try something else

---

### Post by akir4d on 2008-08-30
I suggest you to reset cinelerra settings, move or delete ~/.bcast and restart cinelerra. Also be sure that you don't have any previous compiled files on /usr/local
byez

Paolo Rampino aka Akirad

---

### Post by Bartje on 2008-08-31
I'm sorry akir4d, cinelerra is just not stable, nor reliable enough for serious video-editing. I'm really sorry, but this software is crap. Loading a file works sometimes, sometimes not... it hangs all the time, crashes all the time.. .I mean, I just have tried a video of 20 min. I've spent countless hours editing, had to experience about 25 to 35 hang-ups, and now I just can't open the f*c**ng file anymore... 

I don't have the time to try loading a file 50 times to get it working the 51st time. With this experience I don't want to risk loosing days of work anymore.

By the way, I just lost a job as video-artist because of this. The video would have been shown in a dance-performance. Now I've got to tell her to look for someone else, because I don't have the time anymore to get it right...

Let's beg the gods Lumiera will do it right!!!

---

### Post by akir4d on 2008-08-31
I respect you. But I have only invited you to try again, because many professional users use cinelerra for its production (and someone from my repository).

byez

Paolo Rampino aka Akirad

---

### Post by JC Cheloven on 2008-08-31
> I am not having much luck either. Cinelerra crashes on render often, the compositor window has totally flipped out. Complains about ogg imports. I like it and wished it would work but no lick. Others have also crashed.

Hi, my 2p suggestion: have you tried avidemux, or pitivi?

I don't mean that they would compare to cinelerra (in theory), but I haven't sophisticated needs in video editing, and for example avidemux does everything I want. And never crashed or messed anything.

Greetings

---

### Post by Bartje on 2008-09-06
I appreciate you try to help akir4d. I really do, and I've tried your tips, I've tried other versions of cinelerra, I've tried building it from source... Everything I've tried, but nothing makes cinelerra stable enough for real use. If it is really used by professionals, it will be in their spare time, as enthousiasts trying out software, or by professionals who can afford wasting countless hours of restarting and retrying (but that is highly improbable).

It's dead simple, everywhere I look, I read huge amounts of text about people that say cinelerra is too buggy.. Well, they're right.

JC Cheloven, thanks for your tips, but the applications you use are not enough for me. I use them too. Pitivi is way too basic and Avidemux is just good enough for some basic cutting, adjusting and converting. But Avidemux is impressive. Sadly enough it doesn't read/write .dv video.

---

### Post by cotcot on 2008-09-06
> **Bartje said:**
> I appreciate you try to help akir4d. I really do, and I've tried your tips, I've tried other versions of cinelerra, I've tried building it from source... Everything I've tried, but nothing makes cinelerra stable enough for real use. If it is really used by professionals, it will be in their spare time, as enthousiasts trying out software, or by professionals who can afford wasting countless hours of restarting and retrying (but that is highly improbable).

It's dead simple, everywhere I look, I read huge amounts of text about people that say cinelerra is too buggy.. Well, they're right.

JC Cheloven, thanks for your tips, but the applications you use are not enough for me. I use them too. Pitivi is way too basic and Avidemux is just good enough for some basic cutting, adjusting and converting. But Avidemux is impressive. Sadly enough it doesn't read/write .dv video.
Have you tried blender VSE ? It has quite some features that cinelerra has also (keyframes).
BTW cinelerra is not crap or crashing all the time for everybody. I have it running very stable (compiled it myself). But now i use more the blender VSE.

---

### Post by scorpio2002 on 2008-09-13
After using cinerella for some weeks, I must admit that it is not usable at all. Probably, it is programmed in an awful manner, it often hangs or quits without reporting any error(I'm ok with issues, but a good piece of software should at least notify you the problem). And I'm working with projects that last less than 10 mins. Really, I'm disappointed and that is not the way of writing a piece of software. I've spent so much time learning and practicing with cinerella, but in the end I feel I just lost my time -.-"

---

### Post by Stoppelmonster on 2011-10-11
scorpio2002, I agree.

---

### Post by sgx on 2011-10-14
Before this gets locked for posting to a phantom topic from 2008 :P
( I do it too, so you're not alone :( )

shut off everything you can in the bios, except drives,
(take notes!) network, acpi, plug-n-play, ioapic, etc

In software, shut off anything that suddenly does something,
or appears, screen-lock, screen-saver, power management, system
audio sounds, 3D systems, uninstall pulse audio if it is lurking.

An nvidia graphics card, not the very newest, and an maudio
soundcard, will make your life much easier, and having a
matched pair of fast hard-drives, is also very good luck. High end
work in linux, demands choosing from a limited set of hardware,
that is known to work. Blaming bedroom coders, when you have gear
that is not fully supported, helps no-one. Then try
ubuntu, avlinux or

[http://www.murga-linux.com/puppy/viewtopic.php?t=72402](http://www.murga-linux.com/puppy/viewtopic.php?t=72402)

Puppy Studio 3.3

Cheers

---

