---
title: "Video Editing in Ubuntu with Blender"
date: 2008-12-25
forum: Ubuntu Studio
---

### Post by WinterWeaver on 2008-12-25
Hi there,

Lately I've seen many people asking about video editing in Linux, and most of the time it's greeted with disappointing answers, like: "Go back to windows if you want to edit video, it's not worth it on Linux".

The problem is that many people are using programs like, Open Movie Editor, Pitivi etc. These apps, no doubt could be good, but in my experience are not stable enough yet.

People do however forget, or possibly don't even know, that Blender 3d has a very powerful Video Sequence editor built in. I think people don't realize it's there, because blender can be quite intimidating for any newcommers, and thus they miss this feature completely at a quick glance.

So I thought I might create a Tutorial (or possibly screencast), on how to use blender 3d to do the general video editing that new users may be used to from using other apps.

So, if anyone feel that this would be a good "cause", please let me know what steps, procedures, tips and tricks etc. it is that you would like to see in such a tutorial/screencast. I'll look at the various requests, and see if I can put together a newbie guide to blender video editing.

**EDIT:** Since I dont seem to have the time these days to even touch Blender, I decided to paste a link here to the official blender documentation, on the VSE:
[http://wiki.blender.org/index.php/Doc:Manual/Sequencer/Usage](http://wiki.blender.org/index.php/Doc:Manual/Sequencer/Usage)

**EDIT:** But I think newcomers can still post in this thread with questions, as I'm sure someone here will be able to help :)



Thx for your input :)

WW

---

### Post by RedRat on 2008-12-25
I am very interested in editing video. I have asked here in the forums about video editing software, but the only suggestion so far is to use kino. Kino is a strange software package in that getting video off my digital HD camera requires a 1394 interface and kino does not seem able to capture HD output. 

Questions: 1) can blender import from video cameras, especially HD formats, i.e., 1080i?
2) can blender edit HD formatted video?
3)the user interface does look formidable, so an easy tutorial would be appreciated.

---

### Post by WinterWeaver on 2008-12-26
As for capturing from HD camera, this is something that blender does not do at the moment. Blender imports video/audio from your hard-drive, your blender animation sequences etc. Unfortunate.

As for editing HD video, my experience does not stretch that far. The only way to know is to try.

OK, so now I at least know where to start the tutorial, by listing some things that Blender can/cannot do.

I'll find out a bit more about HD editing, and it's possible that there's a plugin that could import from your camera, I'll have a quick look around.

WW

---

### Post by RedRat on 2008-12-26
WinterWeaver
Thanks for your input. It appears that my search for HD software within Linux is fruitless. Odd. This kind of software has been available in the Windoze XP and later world for some time. The old Roxio media Creator 8 could actually import via the 1394 interface HD video from my camera. I have since found out (had I just read the Help file in kino) that Kino does not support HD video.

Here is a reference you might want to check out in regard to getting video of the 1394 port:
[http://fuocotools.byethost13.com/index.php?topic=103.0](http://fuocotools.byethost13.com/index.php?topic=103.0)

What I find particularly strange in Ubuntu is the use of this 1394 port. In order to get the damn port recognized you have to jump through a lot of hoops I found. The URL above really has helped. Why does Ubuntu and other Linux distros treat 1394 as some strange oddity when it connects via USB to just about anything. I know that apparently 1394 seem to be going away (Apple is considering dropping it from their machines, I have heard), but there are a lot of camcorders and cameras out there that still use it.

Anyway look forward to your tutorial.

---

### Post by cotcot on 2008-12-26
RedRat :
Blender VSE can edit HD video. Also 1080i and full HD. I convert AVCHD (recorded in 1440 x 1080) from my video camera to mpg (1440 x 1080) and use these in blender.

WinterWeaver :
Blender is indeed a very good video editor. It is a good idea to write something for beginners to allow a fast kick off. 
Have you checked the wiki pages on the blender website ? They explain already a lot in detail. There are also a lot of tutorials on the net about blender. 
The manuals of blender (Essential blender) is also very good for blender in general. Some command from 3D modelling are used in the VSE  as well. However the manuals are not explaining a lot about the VSE. Nevertheless I recommend studying them. At least the first chapters. These get you introduced in the user interface. 


It would be nice to explain how to start (download blender; extract and simply click blender in the extracted folder : there is nothing to install; open the video editor mode by clicking 2 times Control Right arrow); example import of video; explain how to get the sound OK > The solution is to place the variable in /etc/environment
# sudo nano /etc/environment
place SDL_AUDIODRIVER=alsa
restart the computer and launch blender

Do not forget to click on the loudspeaker icon and know that blender will not give sound if sound is already used ba another app; blender imports .wav 44100 Hz 16 bit as separate audio track an wav and mp1 in video containers. 
A word about the IPO curves would be good. 
Typical render settings for PAL or NTSC dvd as an example.
A worked out example for a combination of an alpha overlay of a transformed clip would clear up a lot (the order of layers is important). For example an image appearing over a video clip (transform scale + alpha overlay).
Click "premul" for pictures in overlay. This improves the rendered quality. (see sequencer buttons dialog; panel filters)
Titling (text made with gimp or blender in overlay); scrolling using transform.

These are a bit the items that I could not find out easily in the existing tuts when I learned the VSE. 


Blender has a big community. It is used a lot in windows as well.

---

### Post by ipburbank on 2008-12-27
I spend hours on blender every week, and there are some things I think would be nice to show:

the node editor is something that isn't listed here, but it is wonderful for color correction, and other tweeks like that.

So first off I have seen lots of questions on how to combine multiple videos, something simple to do in the VSE. also, there are many things that have to do with the effects. But the thing I find myself using is format conversion. If I have some obsure format that I need to convert to .avi or .mov or whatever, blender does the trick. Just add the video to the vse, or use it as a backbuffer and select from blender's multiple outputs. IF I have any more ideas i'll post them here.

---

### Post by WinterWeaver on 2008-12-27
Thanks guys for this good response.

I have started making a list of things to cover in the tutorial. I'm thinking of putting it up on Google docs so that everyone can get a good overview of what the novice tutorial will cover.

Will report back shortly.

ta,

WW

---

### Post by ipburbank on 2008-12-27
I actually make VFX tutorials in blender and some other free programs. If you want to get together to do this it would be cool, since I already have some tutorial templates, and S3 space to host full-res files. Just an offer, you can do it how ever you want.

~istvan

---

### Post by lkrubner on 2009-01-03
> **WinterWeaver said:**
> Hi there,
So I thought I might create a Tutorial (or possibly screencast), on how to use blender 3d to do the general video editing that new users may be used to from using other apps.

So, if anyone feel that this would be a good "cause", please let me know what steps, procedures, tips and tricks etc. it is that you would like to see in such a tutorial/screencast. I'll look at the various requests, and see if I can put together a newbie guide to blender video editing.


I think this is an extremely important tutorial. I keep getting asked about video editing, and are there open source alternatives? Myself and friends who freelance in this area (commercial 3D and animation work, some video and other advertising production) are unsatisfied with the expense involved with using Macs and the big non open source software packages.

---

### Post by ipburbank on 2009-01-03
Actually blender started as an ad campaign software package. Then it became open source and became what it is today.

---

### Post by Guitar John on 2009-01-03
My needs at the moment are simple.  I use a [Flip]("http://www.theflip.com/") to record video, some of which gets posted on my [YouTube channel]("http://www.youtube.com/user/dadgadjohn").  I sometimes want to trim things out - usually in the beginning and end.  A fade in/fade out would be nice.

Can blender - or PiTiVi for that matter - do that?

---

### Post by ipburbank on 2009-01-04
Blender can do that no problem! It can also save in just about any format you'd ever want and a few more so you can upload in a format that gets you a hi-def link.

---

### Post by fela on 2009-01-04
Cinelerra is a great video editing app for Linux. Check it out. And it's open source aswell, you can't go wrong!

---

### Post by WinterWeaver on 2009-01-04
Ok so there is most definitely a big interest in this.

I have decided to put the slides up of what the tutorial will cover. Unfortunately I was buried under a crazy deadline (freelance web development ... gotta love it), and dont have ample time to work on the tutorial just now.

Have a look at the Slides, and if anyone wants to give any suggestions, please post them here :)

**EDIT**: Slides are no longer on my site since it moved and I changed much of the content.
 thx,

WW

---

### Post by ipburbank on 2009-01-04
my main tutorial series is how to make VFX in blender, and some of the simpler tricks fit into the video editing, such as simple color correction in the nodes, more complex greenscreen than is offered in the VSE and other simple stuff like that. I am willing to contribute that kind of stuff, or at least suggest it as something to be covered.

~I'll post an example soon, I'v been working on this one for a few days, Istvan.

---

### Post by CinemaScope on 2009-01-05
Could you please make the tutorial step-by-step? I'm familiar with video editing (I use Vegas Pro on Windows -- though would prefer linux alternative), and periodically I try to do something with Blender, but I get lost every time. I've read about the Blender VSE from the Blender Wiki, and even made my own notes to try and understand it, but I still come unstuck. I can't even manage to move the interface windows about the way I want, so you see how far back I am from being able to really use this thing. I hope the tutorial can help a newbie like me...

---

### Post by ipburbank on 2009-01-06
Based on what I read on that slide show the plan is to start at the very beginning, so it looks like you are in luck. The first steps are actually simpler than it looks, as blender is very intimidating. but here is what I'v learned:

While key placement and interface may make no sense and actually be confusing and hard to remember for a beginner (such as mesh editing tools being the 'w' key), once you get into the swing of blender it makes perfect sense. It turns out that the golden rule of blender is one hand on the mouse and one on the keyboard, and the keyboard hand will probably be close to the 'w' key when you need it because when you need to edit a mesh to make other shapes your set of keys is in that area of the keyboard.

The point is that blender is hard to learn, but once you do it is very efficient, but you have to hang on while trying to learn. But the good news is that the menus also work, so if your forget a key then you can issue the command from a menu.

~but knowing blender is well worth it!, Istvan.

---

### Post by ikisham on 2009-01-09
I'm trying to make a very simple video, just one still picture (75s long) and an audio track (almost as long).
Added a JPG picture to VSE and stretched it from frame 1 to 75; added a WAV file and stretched it from frame 4 to frame 72; set 'image duration' (Y shortcut) to 75; in the 'render buttons' I set FPS to 1, format FFMPG, size 305x208p (same as the original pic), video output AVI, audio output MP3 and enabled 'multiplex audio'; set the home folder and file name, with 'extensions' enabled; at 'anim' tab, enabled 'do sequence', start 1, end 75. At the 'sequencer buttons' in the 'edit'tab, I left the default 'replace' both for the image and the audio files for 'strip blend mode'.
I turned off Compiz just in case and disabled the screensaver since any action would make the rendering process stop. My hardware is Celeron 2.53GHz and 768 MB RAM (video off-board). After 35 min it showed no signs of rendering (and actually didn't..)
It's something so simple I'm trying to do but it's quite important. I would really appreciate some help even if it's a how-to in Kino for accomplishing this (no 'windows movie maker' here).
Thanks. ( I've put this post in 'absolute begginers talk' but maybe it's useful here too)

---

### Post by ipburbank on 2009-01-10
Does blender normally render for you? start blender, and with the default setup (a cube, camera, and lamp) press f12 or render and see if that works.

If this doesn't work then there is a problem with blender on your system, if it does then I can send you a test file to try rendering, or you can post your file and I can try rendering it. This would eliminate all configuration problems in blender, and me sending you a file would test for configuration errors on your system.

~I hope I can help - Istvan.

---

### Post by ikisham on 2009-01-10
Thank you very much, Istvan. Blender renders ok here (on the test).
The image and the audio I'm using are here:
[DivShare File - momentos_agudos_da_transicao_planetaria.wav](http://www.divshare.com/download/6287032-1ff)
url=http://www.divshare.com/download/6287019-8ed][img]http://www.divshare.com/img/thumb/6287019-8ed.jpg[/img][/url]

Actually I managed to do something with 'AV Video Karaoke Maker' in Win 2000. It's so simple but it cut a bit of the audio and I can't select the duration of the video. The basics is done but if you don't bother helping me I still would appreciate trying to do it with Blender.
Tx

---

### Post by ikisham on 2009-01-10
Sorry, here's the download link for the image:
[http://www.divshare.com/download/6287019-8ed](http://www.divshare.com/download/6287019-8ed)

---

### Post by ipburbank on 2009-01-10
So rendering isn't the problem. Try just using a video in the sequence editor, and see if that renders, (add the video, and click do sequence, and then render)

---

### Post by ikisham on 2009-01-10
Did you mean click 'anim'? I've seen that if the output format is jpeg it renders ok (with no sound, of course) but if I put FFMpeg to render it as video with audio it doesn't work. I've seen in synaptic and it seems I have the required libraries (I don't understand of these things but most ubuntu supported and related to FFMpeg are installed).
Tx

---

### Post by ipburbank on 2009-01-10
ok, then can you animate a plain old cube with ffmpeg as the output?

---

### Post by ikisham on 2009-01-10
In 3D view the cube renders (RENDER button) both with Jpeg or FFMPeg selected, but 'do sequence' must not be selected. ANIM button works with Jpeg output (with 'do sequence' selected the animation seems to be working but there's no cube, just a black window) but with FFMpeg it gives an 'Error initializing video stream' both with 'do sequence' selected or not.

---

### Post by ipburbank on 2009-01-10
check out this thread:

[http://blenderartists.org/forum/showthread.php?t=96538](http://blenderartists.org/forum/showthread.php?t=96538)

~hope that is what you are looking for!

---

### Post by ikisham on 2009-01-10
Thank you, Istvan. I tried to output as AVI Raw but it output all the frames separately and from 76 to 250, black frames (I set to animate only 75 frames).
[[IMG]http://img181.imageshack.us/img181/1954/screenshot2ay9.th.png[/IMG]](http://img181.imageshack.us/my.php?image=screenshot2ay9.png)
[[IMG]http://img209.imageshack.us/img209/4247/screenshot1lo9.th.png[/IMG]](http://img209.imageshack.us/my.php?image=screenshot1lo9.png)
[[IMG]http://img209.imageshack.us/img209/9141/screenshotdg5.th.png[/IMG]](http://img209.imageshack.us/my.php?image=screenshotdg5.png)
But I will still try ZS4 in Windows, maybe it works for me.

---

### Post by ikisham on 2009-01-10
That emoticon went by itself there...

---

### Post by ipburbank on 2009-01-10
Where did you set the end frame? it should be done right below the animate button.

---

### Post by WinterWeaver on 2009-01-11
(on a side note) - I used to have strange issues when trying to use ffmpeg for render output. I later installed ffmpeg manually for creating a webapp that does video streaming. Since then I haven't had those issues in blender. I'm not quite sure if they are related, but I t sure feels like it's working better now.

---

### Post by ikisham on 2009-01-11
ipburbank : start frame 1 end frame 75

WinterWeaver : do you think I should embroil myself in this FFMpeg manual installation? I really haven't much experience with linux.

---

### Post by WinterWeaver on 2009-01-11
Nah, not right now. If you have audio issues, first check whether you can choose another audio format for output. If none of these work, it could be worth trying to do a manual ffmpeg install.

EDIT: Installing things manually is sometimes a bit of a nightmare for newbies, so only do that as a last resort.

BUT, note that I cannot be 100% sure whether or not it was ffmpeg that was the issue in my case, which is why I only mentioned it in passing.

By the way, I have created a little screencast with your example above. Downloaded the image and wave file. Currently I'm doing a little voice-over (edit: as soon as my wife finishes the hoovering >.< lol ) for the clip, and will upload it to youtube for you :)

ta,

WW

---

### Post by ikisham on 2009-01-11
WW, do you mean you're gonna upload a little tutorial on how to make a screencast? Well that may not matter as I'll have a look anyway..
Thank you.
Btw, it seems that LiVES does slideshows. Last time I couldn't enter the site for the ubuntu version but I'll keep trying.

---

### Post by WinterWeaver on 2009-01-11
> **ikisham said:**
> WW, do you mean you're gonna upload a little tutorial on how to make a screencast? Well that may not matter as I'll have a look anyway..
Thank you.
Btw, it seems that LiVES does slideshows. Last time I couldn't enter the site for the ubuntu version but I'll keep trying.

nope, not a tutorial on how to make a screencast. I've done the example you posted above, of the still image, and adding a audio track, rendering it etc.

I just need to add some voice-overs to explain what I'm doing. Then I'll upload it to Youtube or google video or something the like.

---

### Post by CharmlessMan on 2009-01-11
I didn't feel like starting a thread for this question & I'm on my way out so here goes:

WHat's a good movie editing program for UBunto? I used to use POwer Director on Windows XP.

I'm looking for something that can read my camera's MOI/MOD files. And easy to use .........for now.

Also if there's any better audio programs other than Audacity please share. THanks :)

---

### Post by ipburbank on 2009-01-11
I like kino for taking video off a camera, and saving it as a file, but all bender after that. Audacity is the best OS audio software I know of.

---

### Post by RedRat on 2009-01-11
> **ipburbank said:**
> I like kino for taking video off a camera, and saving it as a file, but all bender after that. Audacity is the best OS audio software I know of.

The only problem is that, at least as of now and with the kino version I have installed, it doesn't capture HD digital video off my camcorder. I pretty much want to shoot in HD now that I have an HD set. The stuff I have shot so far really looks looks great in 1080i.

---

### Post by ipburbank on 2009-01-11
hmm. well i'm in middle school, and can't afford 1080i equipment, so I haven't been faced with this problem.

~sorry, Istvan.

---

### Post by RedRat on 2009-01-11
> **ipburbank said:**
> hmm. well i'm in middle school, and can't afford 1080i equipment, so I haven't been faced with this problem.

~sorry, Istvan.
Well you work with what you have. From my initial experiences with kino, it appears to function much like Adobe Premier Elements and looks pretty good. The funny thing is that once you download (I did it on my XP windows machine) and get the high def video as either a HD-DV or mpeg file, kino seems able to handle the format. Odd that it does not capture the HD-DV from my camcorder. Maybe next update.

---

### Post by patchin_house on 2009-01-19
Please do get back to us with the URL for your tutorial when it's ready. And, yes, let's have a screencast to go with it. I've been fascinated with Blender for many years, but have yet to really get creative with it (or have the time for it). Maybe a video editing tutorial will be the best route.

Philip David
2009.01.19

---

### Post by WinterWeaver on 2009-01-19
I'm basically done with the example mentioned earlier. Unfortunately work duties caught up with me and deadlines are around the corner.

Just a notice that I'm still looking forward to finish this, as soon as I have the spare time.

Will keep you guys posted.

WW

---

### Post by FakeOutdoorsman on 2009-01-20
> **ikisham said:**
> ipburbank : start frame 1 end frame 75

WinterWeaver : do you think I should embroil myself in this FFMpeg manual installation? I really haven't much experience with linux.
I wrote a tutorial on manually installing FFmpeg to help simplify things for us Ubuntu users:

[HOWTO: Compile the latest ffmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

---

### Post by Chrisj303 on 2009-01-21
Is there anything that can compete with Final Cut for Linux yet?

I tried Cinerella a while back, but was really dissapointed with the GUI and filters/transistions - and more so the lack of quality plug-ins.

This was about a year ago. 

I'm running on a Macbook Pro - and have FCP installed, but am trying to migrate over to Ubuntu as much as possible, Video and audio editing is what I need most.

---

### Post by WinterWeaver on 2009-01-21
> Is there anything that can compete with Final Cut for Linux yet?

If you want something the same quality as FCP, I suggest you stick with it on mac os. You wont find anything even close to FCP on linux.

But I also suggest you also play around with blender in your spare time. You may just be able to find that is is sufficient for your particular use case or a couple of tiny projects. By doing this you can get involved by submitting suggestions or bugs to the blender team, and they can develop a better platform for the future. ;)

---

### Post by ipburbank on 2009-01-21
FCP has has a great interface, but I can do almost everything on linux. the problem is it takes many programs, and much longer to make your own transitions etc.

---

### Post by 4ebees on 2009-01-23
Hi there,

This would be a great project.

If you don't mind, when it's up and running, I'd like to link to it on my site:

[www.youcantdothatinlinux.com](www.youcantdothatinlinux.com)

The site is mostly to distribute information and tips I've picked up about editing video and creating DVDs in Linux, as well as to provide an aggregating link to other applications and other sites with useful how-tos etc.

The site is new and slowly growing. A link to something like yours would be a great addition.

---

### Post by ipburbank on 2009-01-23
I have quite a few video editing on linux tutorials, just go to youtube and search for ipburbank, and anything starting with

All Free VFX -

Is a video. Some of them are rough videos, infact all of them. I am currently struggling with the ubuntu audio issue, and hence some of my audio might get out of sync. I will be fixing this in the future, as well as making it much more professional looking. If you would like full-quality videos I can host them, and will be as soon as I get around to that.

---

### Post by Ng Oon-Ee on 2009-01-31
Thumbs up for this idea, I know I've been overwhelmed (and still am) by existing options for video editing in Linux. Process goes something like:-

1. Start-up Blender
2. Stare at the dot in the middle of the screen and the whole gray mess
3. Click on something random
4. Look at the result (which I don't understand)
5. Try to alt-tab (doesn't work, I think I ran it full-screen)
6. Exit Blender

:D

---

### Post by WinterWeaver on 2009-02-04
> **ipburbank said:**
> I have quite a few video editing on linux tutorials, just go to youtube and search for ipburbank, and anything starting with

All Free VFX -

Is a video. Some of them are rough videos, infact all of them. I am currently struggling with the ubuntu audio issue, and hence some of my audio might get out of sync. I will be fixing this in the future, as well as making it much more professional looking. If you would like full-quality videos I can host them, and will be as soon as I get around to that.

I wasn't aware that your vids are on Youtube :)
Thats great, and there are plenty!

Maybe we can put together a website to categorize these videos?

---

### Post by ipburbank on 2009-02-04
indeed, I had a site up, but I gave up on it. you can see what i had at

istvan.us/allfreevfx -- still in building stage

I may continue that page again, but I am currently on another project with a friend of mine.

---

### Post by WinterWeaver on 2009-02-04
I could put together a site for this (I'm a web developer) if you are interested. (since we are doing this for the community, I'll create and host it for free, so long of course its not too big :P )

---

### Post by ipburbank on 2009-02-04
ya! that would be great! I can give you the full-res versions of the files, and if you would like also the files I use to make the videos (blender files, python scripts, source files etc.)

---

### Post by WinterWeaver on 2009-02-09
Cool, I'll start working on something as soon as I have some free time. I'm on holiday now so I'll probably find a moment or two somewhere. Betweeen meeting family and friends :)

---

### Post by sadnub on 2009-02-10
I stumbled across this thread looking for video recording/editing software. I read about all of it and went to downloaded and install Blender and yes it does look ETREMELY intimidating. I was actually wondering if it is possible to record video with a usb hue webcam with blender?

---

### Post by ipburbank on 2009-02-10
yes, it is very intimating. the trick is know where one or two things are that you need, and after that you can slowly learn the rest as you go.

Blender can not connect to a usb video camera at the moment, but kino or similar programs are good. I find kino easy to use, and gets the job done without extra 'features' in my way ;)

~blender also has many good tutorials, use google to find them - Istvan.

---

### Post by sadnub on 2009-02-10
Thanks Ill give kino a shot and as for blender ive looked at a few tutorials and its all about creating 3D models and stuff.

---

### Post by ipburbank on 2009-02-10
also as we will show in this thread there are many other tools, such as:

[http://www.youtube.com/watch?v=itws2NpR09I](http://www.youtube.com/watch?v=itws2NpR09I)

which i made from:

[http://www.youtube.com/watch?v=NkJhQmSe6nQ&feature=channel](http://www.youtube.com/watch?v=NkJhQmSe6nQ&feature=channel)

to do this I used masking, and compositing, not in the VSE (video sequence editor)! that was a goal of this project. I did this in 10 hours too! There are tutorials on youtube as well, feel free to check them out.

---

### Post by cotcot on 2009-02-11
> **sadnub said:**
> Thanks Ill give kino a shot and as for blender ive looked at a few tutorials and its all about creating 3D models and stuff.
That is because you google on 'blender'. If you google on 'blender VSE' you will find specific tuts for the Video Sequence Editor function of blender. [[COLOR="Red"]Here[/COLOR]]("http://wiki.blender.org/index.php/Manual/Using_VSE") is an example.

---

### Post by sadnub on 2009-02-12
Oh ok lol, Thats an interface im a little more familiar with. This blender program is like everything in one. Its pretty much awesome. You just need to get used to the commands which i am trying to do. Thanks alot for all the help guys! =)

---

### Post by punong_bisyonaryo on 2009-03-11
> **ikisham said:**
> In 3D view the cube renders (RENDER button) both with Jpeg or FFMPeg selected, but 'do sequence' must not be selected. ANIM button works with Jpeg output (with 'do sequence' selected the animation seems to be working but there's no cube, just a black window) but with FFMpeg it gives an 'Error initializing video stream' both with 'do sequence' selected or not.

What I know is that Do Sequence will render what you have in the video sequence editor, so that must be off if you're rendering in 3D.

I have this same problem, but I used Blender for editing a video, not for 3D. When I choose FFMPEG, I get a "Error Initializing Stream" if I select Multiplex Audio. If I don't select Mux Audio, it doesn't show an error, but it still just sits there doing nothing.

---

### Post by ipburbank on 2009-03-11
I run ubuntu linux, and blender 64bit with python 2.5

I just today was able to use ffmpeg and the VSE (video sequence editor) to render out video and audio with no hitches.

One place to try is the irc channel #blender  --- they offer good help, and you might just see me there ;)

---

### Post by punong_bisyonaryo on 2009-03-12
Are you using the latest FFMPEG compiled from source? I'm using the one built-into Ibex 32-bit. I've noticed that with some FFMPEG codecs I choose, if I choose Multiplex Audio, it doesn't work. The last I was able to try with success was HuffYuv, with AC3 (or was it AAC?) and it seemed to work. I have to try again later when I get home.

---

### Post by punong_bisyonaryo on 2009-03-13
Ok, after installing FFMPEG from source, I'm still having problems. The blender versions I've tried was the Blender from Intrepid repositories, and from getdeb. So far, I've only had luck with AVI HuffYUV with PCM audio (AC3 starts animating, but when you play back the output, the sound is broken, as in only occasional scratches comes out).

I have no idea what to do, but if HuffYUV PCM is the only thing that works, well that's that. And a deadline is a deadline. I'll just reconvert in Avidemux or something.

---

### Post by Ascenti0n on 2009-03-13
> Ok, after installing FFMPEG from source, I'm still having problems

This is why people pay a lot of money for a commercially available NLE, particularly if it is crucial to their work or business.

You need big bucks to develop something that takes thousands of development hours to build. It's just not worth the the wasted time, unless it's for a hobby and you have the time.

---

### Post by WinterWeaver on 2009-03-14
>.<

I finally had some free time today to finish that video tutorial... And now I cannot find the screencasts I captured ](*,)

I think I must have absentmindedly deleted it at some point :mad:

.... sigh ....

Anyway, on another topic, has anyone ever tried the video editor LiVES? [http://lives.sourceforge.net/](http://lives.sourceforge.net/)

If so, how is it, and how does it compare to others?

---

### Post by punong_bisyonaryo on 2009-03-14
@Ascenti0n, yeah, nothing critical anyway. Just a personal project with a deadline. Thinking about it, it's a good thing HuffYUV (lossless) and PCM (uncompressed) was the combination that worked. At least I could make my high quality "master copies" with blender and transcode them using Avidemux. Imagine if I could only export in MPEG-1!

@WinterWeaver, I've tried it a long time ago. And...no, it just didn't do it for me. For a short time, I also tried Open Movie Editor, and I think it's really doing great in the simple video projects category, the best and most stable I've tried of the herd. But it's kinda annoying how the developer keeps on insisting on the latest, bleeding-edge video libraries (read: not in repos). And after trying Blender (I needed something more powerful), I think it's still the best albeit scary to newbies.

---

### Post by Guruji on 2009-03-15
maybe you could have a look at this site:
[http://www.totallyblended.com/NEW_INDEX/tutes/tutes.html](http://www.totallyblended.com/NEW_INDEX/tutes/tutes.html)

it has video tutorials about blender, and 3 are an introduction to the video editor. That might be some useful information for you tutorial.

---

### Post by WinterWeaver on 2009-03-15
I've actually been wondering if I have the time of late. I currently dont have even the slightest little "blender" moment, haven't touched the program in about 3 months now :(
It's unfortunate, but I have to face the facts that I dont have the time to do what I promised >.<

However, since we have had a couple of responses in this thread pointing to existing tutorials, I think it would be best to rather list the different tutorials that others have done. We can do that in the first post of this thread.

Thoughts?

---

### Post by ipburbank on 2009-03-15
I can continue the old idea to an extent, though I might have some limits. If there are requests I can see if I can make a tutorial, but a directory of tutorials might also be nice.

---

### Post by RedRat on 2009-03-15
There is no good reason to re-invent the wheel. Why not take a look at the tutorials and see what needs to be made more clear. Instead of designing a brand new tutorial entirely from scratch, see what the others offer and see if they miss the boat in some areas--that is going to more than likely. This would save you a lot of time but still allow your creative juices to flow.

---

### Post by ipburbank on 2009-03-16
Indeed, I agree completely. That is where this thread comes in, if any blender artists have questions that are un-answerable by the current slew of tutorials, please, let me know and I can fix that problem.

---

### Post by EvilRobot on 2009-05-05
> **Guruji said:**
> maybe you could have a look at this site:
[http://www.totallyblended.com/NEW_INDEX/tutes/tutes.html](http://www.totallyblended.com/NEW_INDEX/tutes/tutes.html)

it has video tutorials about blender, and 3 are an introduction to the video editor. That might be some useful information for you tutorial.

Thanks Guruji, for posting that link. I've been looking for some decent Blender tutorials for a while now and these are pretty well done.

---

### Post by wkulecz on 2009-05-06
> This is why people pay a lot of money for a commercially available NLE, particularly if it is crucial to their work or business.


And exactly which comercially available NLE will offer a money back garauntee?

While unfortunately, Linux has a ways to go before I'd call it usable for "real" video work, I've spent a ton of money and still had many problems doing NLE on Windows!

Mac could be better, but it sure is more expensive, and my experience with Mac users is they generally tend to be in denial about problems, buying upgrades and new hardware without complaints to "fix" issues.

--wally.

---

