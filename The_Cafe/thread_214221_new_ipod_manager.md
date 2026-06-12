---
title: "new ipod manager"
date: 2006-07-12
forum: The Cafe
---

### Post by Floola on 2006-07-12
I developed a new iPod manager, Floola.

If anybody is interested in beta testing:

[http://www.floola.com](http://www.floola.com)

I tested it successfully under Dapper Drake 6.06.

Tomas

---

### Post by Floola on 2006-08-12
Guys at [ipod-fun.de]("http://www.ipod-fun.de") made a nice video preview of the windows version. Take a look at it, [youtube video]("http://www.youtube.com/watch?v=hmESuB45Kc4").

Tomas

---

### Post by Polygon on 2006-08-12
it looks nice, but i cant figure out how to exactly work it...

i know how to run it, but i plugged in my ipod and it said something about configuring it, so i pressed ok.  But it doesnt show any songs or anything. But it does show my ipod in "tools > ipod information".

i tried running it from the desktop and my ipod, no luck =/

EDIT: i tried to end the program, and then try to eject my ipod. but it kept saying that the ipod was busy and couldent be ejected. so i opened up system monitor and i found that 2 foola processes (i ran folla twice) and a bunch of "df" processes where there (zombied) and i had to manually end the foola processes before i could eject my ipod (which also killed the "df" processes"

---

### Post by hanzomon4 on 2006-08-12
Well so far I like it I can't transfer wav files or video files but everything else works. Good job

---

### Post by Floola on 2006-08-12
I don't own an iPod video, so it would be great if you could help with the video transfer. The wav transfer should be doable, I think.

Drop me an email if interested.

Tomas

---

### Post by hanzomon4 on 2006-08-12
Sorry not a dev, but I'm sure someone around here is and owns a video ipod.
Also I downloaded the win version and it to works it also plays my DRM files, how is this. In the linux version I can't even play non DRM m4p files.

---

### Post by Floola on 2006-08-12
Hi,

no dev knownledge needed, it's more something like "send me that file", "try this and that"....

Anyway, about the drm: it works under windows because it uses quicktime which decodes the drm correctly as the pc you're using is one of the authorized ones. This is not possible under linux, unfortunately.

M4p are, as long as I know protected. m4a are DRM free. Floola uses an audio library ([www.fmod.org](www.fmod.org)) do to the playback which does not support m4a and aac files.

Cheers,
Tomas

---

### Post by Floola on 2006-08-13
Floola (a5) available! 

[LIST]
[*]WAV support added.
[*]playback should work now (ALSA required).
[*]some other minor enhancement.
[/LIST]

[http://www.floola.com](http://www.floola.com)

Tomas

---

### Post by Onyros on 2006-08-13
Hmmmm... I have a guess my wife will love this :P

She simply *HATES* iTunes, yet she loves her lil' iPod.

I'll post her reaction to Floola later on ;)

---

### Post by Onyros on 2006-08-13
Well, as promised, here's the feedback regarding Floola...

Utter awe ;)

She loves it, I even tried it myself and it simplifies her iPod's music management a whole lot! She can, finally, get rid of iTunes.

Congratulations on a great piece of software, mate ;)

---

### Post by Floola on 2006-08-13
What iPod does your wife own?

Keep me posted about any problem you may have.

Cheers,
Tomas

---

### Post by tribaal on 2006-08-13
Had a look at the vid, got interested, downloaded, and it works great. :)

I'll send you updates if I ever find something that isn't working the way it should :)

Thanks a lot, I needed something like that!

- trib'

---

### Post by uncreative on 2006-08-13
I'll give it a shot

---

### Post by Onyros on 2006-08-13
> **Floola said:**
> What iPod does your wife own?

Keep me posted about any problem you may have.

Cheers,
TomasCheers, Tomas ;)

She has a 4th gen iPod Mini (4GB model), and it's all bliss for her right now. She once deleted a full iPod of music because of iTunes' messiness.

I once had her trying both Anapod Explorer and ephPod, but she didn't quite like the first and the latter crashed on her twice as she was transferring songs, and she uninstalled it promptly.

For my wife, Floola is... flawless! (You gotta love the alliteration, and you can quote me on that :P)

If anything does come up, I'll keep you posted ;)

---

### Post by %hMa@?b&lt;C on 2006-08-13
I have a video iPod, and have used nothing but GTKpod so far. I *love* the interface of floola!
When i run floola with my iPod connected, i get this.
[http://img50.imageshack.us/img50/2636/screenshotpm9.png](http://img50.imageshack.us/img50/2636/screenshotpm9.png)
what does it do, and why?
also... concider opening your source;)

---

### Post by rekahsoft on 2006-08-13
I really like your work tomas...i would love to join the project on one condition...it be opensourced. Btw...Floola is done in C right?

---

### Post by hanzomon4 on 2006-08-14
> **jeffc313 said:**
> I have a video iPod, and have used nothing but GTKpod so far. I *love* the interface of floola!
When i run floola with my iPod connected, i get this.
[http://img50.imageshack.us/img50/2636/screenshotpm9.png](http://img50.imageshack.us/img50/2636/screenshotpm9.png)
what does it do, and why?
also... concider opening your source;)

It could be that gtkpod does something to the itunes db.

---

### Post by Polygon on 2006-08-14
i got this too, i just said "configure" or whatever.

and there are only 2 generations of ipod minis. yours is a second generation if the text color on the click wheel is the same color as the ipod, and the disk size is engraved on the back. otherwise its a first generation

---

### Post by Floola on 2006-08-14
> **jeffc313 said:**
> what does it do, and why?

This is more a windows a mac stuff. It setups iPod so that iTunes doesn't automatically start, set it to use disk mode, etc...

Next version won't show this under linux.

Tomas

---

### Post by Floola on 2006-08-14
> **rekahsoft said:**
> I really like your work tomas...i would love to join the project on one condition...it be opensourced. Btw...Floola is done in C right?

No, it's written in REALBasic ([http://www.realsoftware.com](http://www.realsoftware.com)). 
There are many reasons because I prefer to keep the source closed, at least for the moment.

Cheers,
Tomas

---

### Post by drobvice on 2006-08-14
I thought your program looked interesting and submitted it to digg:

[http://www.digg.com/linux_unix/Floola_new_cross_platform_iPod_manager_Linux_Windows_and_Mac]("http://www.digg.com/linux_unix/Floola_new_cross_platform_iPod_manager_Linux_Windows_and_Mac")  :)

---

### Post by %hMa@?b&lt;C on 2006-08-14
+1 digg

---

### Post by Floola on 2006-08-14
Good news everyone! Floola is now localizable! 

It's easy and FUN.

It's easy because you don't need any programming knowledge (there' a simple application that helps you do the translation).
Translation take some time as there are approximately 300 phrases to translate.

So only if really really interested:
- register to site ([http://www.floola.com](http://www.floola.com))
- email me your username

I'll activate a translator account.

Tomas

---

### Post by Floola on 2006-08-16
Floola (a6) available.

[http://www.floola.com](http://www.floola.com)

**I'm looking for translators**.

Tomas

---

### Post by micmic on 2006-08-17
Hi,
   with Ubuntu 6.06 and my iPod 4Gb, Floola show me the information but nothing else, no tracks.
   with WXP (win version) no problem, 1 minute reading and here they are.

Thanks in advance and sorry for my english

--> Ups: sorry, my iPod mount on sdb (usually sda), work fine

---

### Post by Floola on 2006-08-18
Floola (a7) available!

Dutch and spanish translation added.

Tomas

---

### Post by micmic on 2006-08-18
:)

Testing

Note: the Genre menu and the Add in Song menu (Shift+ctrl+A) don't appear with the translator application :(
The feedback and donation sentences are also in original language

---

### Post by Polygon on 2006-08-19
hey, with version a7, the problem i had with no music or anything showing up went away. i can now see my songs on my ipod mini second gen. on floola:

[[IMG]http://img201.imageshack.us/img201/5111/screenshotbg5.th.png[/IMG]](http://img201.imageshack.us/my.php?image=screenshotbg5.png)

ill try syncing later, thanks

---

### Post by The Noble on 2006-08-19
Ah, thank you! I lost my iPod when I came back from Europe, so I can't test right now. I was looking at an iriver or the likes, but your infernal software may change my mind!

---

### Post by Floola on 2006-08-19
Should anyone find other untranslated parts please report.

I found that many parts of preferences were not translated. This will be fixed in one of next releases.

Thanks,
Tomas

---

### Post by micmic on 2006-08-20
Another untranslated parts: menu add to iPod, lost items

---

### Post by mark_e_wallace on 2006-08-20
Tomas -

Quick question about Floola. I have multiple (like, ten or so) albums in my database called "Greatest Hits", each from different artists. With Floola, can I edit, say, the Bruce Springsteen version of "Greatest Hits" and make it "Bruce Springsteen's Greatest Hits" ? It frustrates me on my iPOD to look through the album listing and not be able to find Springsteen's Greatest Hits as its own listing.

Thanks,

Mark

---

### Post by Floola on 2006-08-21
Yes you can. Select songs then Song->Edit.

Tomas

---

### Post by SirKillalot on 2006-08-23
cool, now only the linux kernel needs to work with my ipod then I will be able to load songs on my device from my pc... that would be so awsome T_T

---

### Post by Hg80 on 2006-08-23
Does it play the music files through the ipod, isnt there an issue with the DRM of downloaded tracks from itunes store?

---

### Post by Floola on 2006-08-23
Floola (well actually fmod, the audio lib) won't playback files with DRM under linux. Under win and mac it will use quicktime so there's no problem.

Tomas

---

### Post by Joedude on 2006-08-24
will this work under Ubuntu 6.0.6? WWill it work with a Motorola V3i? It's one of those mobile phones that requires itunes to transfer music from your computer to your phone (in other words it's a 512MB IPOD/Mobile phone...

---

### Post by Floola on 2006-08-24
It is Motorola ready but I would need to add a couple of things in code. If interested contact me privately.

Tomas

---

### Post by Floola on 2006-08-27
Floola a9 available!

Motorola phones compatible
artwork fixed and optimized
new gui layout
many bug fixed

[http://www.floola.com](http://www.floola.com)

Enjoy,
Tomas

---

### Post by pianoboy3333 on 2006-08-27
If you guys are looking for other ipod managers, you should also take a look at [http://www.rockbox.org/](http://www.rockbox.org/) rockbox is another great firmware for ipods, irivers, and cowon x5/l/v's.

---

### Post by %hMa@?b&lt;C on 2006-08-28
Hi, 
I am working on a different app, for my camera, and was wondering if you cold please tell me how you get to connect to a USB device in REALbasic.  Preferably using libUSB

---

### Post by Floola on 2006-09-01
a11 released!

Fixed several bugs (audio pop, artwork window and many more, freespace errror on startup). Added BPM column. Artwork should finally work.

Enjoy,
Tomas

---

### Post by sinaen on 2006-09-06
Hi i get this error when i try to execute Floola from my ipod. cant it be done? i had a belief that that would work
shell#: /bin/bash ./Floola
./Floola: ./Floola: cannot execute binary file
      
and if you could it would be nice to get m4a and m4b support. so you can add audiobooks and acc-files, as you know the ipod firmware recognizes this and puts it in a audiobook folder. :)

---

### Post by Bastanteroma on 2006-09-08
In Dapper I get the following error:

Runtime Error 4: Failed Assertion
Press OK to Continue
Press Cancel to Quit.

Please report what caused this error
along with the information below.

../Common/plugin.cpp: 6490
Failure Condition: 0
The application cannot continue because a needed file cannot be installed. libpng.so.3: cannot open shared object file: No such file or directory

The readme describes making a symlink:
Floola requires libpng3 to be installed or in case you've got a newer libpng version installed that you make a symbolic link so that /usr/lib/libpng.so.3 points to /usr/lib/libgpng.so. This can be done in terminal typing:
cd /usr/lib
sudo ln -s libpng.so libpng.so.3

But that didn't work, nor did trying to make a link to libpng12.so.0 which is what I've apparently got, using the same form, as in : sudo ln -s libpng12.so.0 libpng.so.3  


Any ideas?

---

### Post by Floola on 2006-09-09
Should be fixed in next version.

Tomas

---

### Post by Floola on 2006-09-10
a12 available!

artwork bug fixed
png library problem fixed
minor improvements here and there

Enjoy,
Tomas

**sinaen** have you tried just ./Floola ?

---

### Post by Floola on 2006-09-27
Floola a13 is out.

A performance problem under linux was fixed, so now it should be way faster than before.
iTunes 7 compatibility added (was a problem with iPod videos only)

Enjoy,
Tomas

---

### Post by micmic on 2006-09-28
Hi, I found a bug:
With a12, when I reorder a playlist with several tracks my iPod crash... I mean: the tracks dissapear and I use gtkpod with orphan and I found them

---

### Post by Floola on 2006-09-28
Any playlist?

Tomas

---

### Post by uzd4ce on 2006-09-29
I just installed it in Ubuntu and it looks pretty cool so far.  My question is about podcasts.  How can I use Floola to get podcasts to my iPod?

Is it similar to GTKPod where I use Ipodder or something to download them and then Floola to tranfer?  

Thanks

---

### Post by uzd4ce on 2006-09-29
I have another related question.

When transferring files to the iPod, is simply selecting a genre of Podcast enough to have it recognized as a podcast and appear in the podcasts menu on the iPod?  With the listened/not listened icons and everything?

Thanks

---

### Post by Floola on 2006-09-30
The only big feature missing in Floola is podcasts, but it's on top of todo list once a couple of other bugs are fixed.

Changing genre is not enough.

Tomas

---

### Post by Area51mafia on 2006-10-01
Is Floola compatible with the 1.2 Firmware for the 5G iPods? I used it on mine earlier quite nicely, and it worked perfectly transfering the files and whatnot. But when checking "iPod Info" it says i'm running firmware version 1.1, not that it's a big deal though.

Oh, and could there be an option when adding songs to "add a directory" or "add a file", sorta like iTunes has it? Having to open Nautilus and navigate to where my music is and then drag the files onto it can be a real hassle.

Also, does it support gapless playback at all? I don't know how iTunes does it's gapless playback, so I'm not sure if it's easily reproducable or not. If not, that's alright.

Good job!

---

### Post by Floola on 2006-10-07
Yes, Floola is now compatible with 1.2 firmwares. You can add videos (.mp4 and .m4v) to your iPod. It still does not support gapless playback, it might in future.

New version is available. It's now much faster when browsing iPod content, it has a much better smart playlist decode engine and many many bug were fixed.

Enjoy,
Tomas

---

### Post by Floola on 2006-10-13
Floola beta 6 released. Various bug fixed.

---

### Post by uzd4ce on 2006-10-13
I've been experimenting with various ways to get podcasts onto my iPod recently, and have run into different problems with each program.

Even though it doesn't do podcasts per se, I've pretty much settled on Floola (with the help of Ipodder to download podcasts) as my program of choice.  Both Amarok and GTKPod don't do video podcasts for me, which Floola does.  

Even though they're not recognized as podcasts, at least the video files transfer.  Same with my audio podcasts.  They don't appear in the iPod's Podcasts section, but they show in the Recently Added playlist, so that works for me.

After transferring any files, I get a popup "Unknown Error" for each file. So if I transferred 50 files, I have to hit "OK" 50 times to clear all the windows.

Is this a known but, and has the newest version addressed it?

One other feature I'd like to see is this:
When adding files through the Add Song menu item, I'd like to be able to simply drag over a complete directory (like where I download my podcasts) and have it ignore any files already added.

When I did that this morning, I ended up with multiples of each file.

When deleting files from the iPod, it would be nice to be able to select many files, and then delete them all at one time, rather than having to wait for each to delete as you go through your list.


Thanks

---

### Post by Floola on 2006-10-13
"Unknown error": I couldn't find that error, can you report exactly the error message. If it says "unknown rule" or "unknown action" it has been fixed in latest version.

The feature request about the add songs is in the todo list (not on top). You can use the duplicate feature as a workaround, it's quite fast.

You should be able to select several songs (holding CTRL key) then choosing Song->delete. There was a bug where the right click would deselect current selection. This has been solved in current version.

Cheers,
Tomas

---

### Post by uzd4ce on 2006-10-13
Yeah, you're right, it said "Unknown Rule".  

I'm looking forward to trying the new version when I get home tonight.  Thanks for all your work on it.

---

### Post by silhouette on 2006-10-13
I'm trying to access my friend's iPod using Floola, but it seems Floola isn't recognizing it. He's got one of the new Nanos, so that may be it. It may also be that Linux itself isn't recognizing the iPod. The iPod doesn't need to be Windows-formatted, does it?

---

### Post by futz on 2006-10-14
> **silhouette said:**
> I'm trying to access my friend's iPod using Floola, but it seems Floola isn't recognizing it. He's got one of the new Nanos, so that may be it. It may also be that Linux itself isn't recognizing the iPod. The iPod doesn't need to be Windows-formatted, does it?
I've got a new Nano second gen. Linux sees it fine and Floola works just fine too.

I believe the stock format for it is FAT32. I know because I botched it all up and had to format it and reinstall the software with iTunes on a windoze box.

---

### Post by Floola on 2006-10-21
Floola b7 available. Video upload should work now. If anybody finds other m4v or mp4 that aren't uploaded correctly please let me know via email.

[http://www.floola.com](http://www.floola.com)

Thanks!

---

### Post by Floola on 2006-10-27
I think it would be nice to include Floola in multiverse. As I have very little time and virtually no experience with packaging, I would like to know if there's someone interested in creating a package for Floola.

Please contact me by email.

Thanks,
Tomas

---

### Post by doggbert on 2006-10-31
I receive the following error when trying to playback an mp3...

Error: FMOD error: Internal FMOD error(code #37). (gtkpod722258.mp3)

any thoughts?

---

### Post by gosh on 2006-10-31
I get this message when running ./Floola:

```
Floola needs df installed. Please install it. Floola will now quit.
```

What is df?

---

### Post by daithik on 2006-11-05
what is the difference between floola and YamiPod - [http://www.yamipod.com/main/modules/home/](http://www.yamipod.com/main/modules/home/) ?

---

### Post by silhouette on 2006-11-05
> **gosh said:**
> I get this message when running ./Floola:

```
Floola needs df installed. Please install it. Floola will now quit.
```

What is df?

df is a GNU utility to inspect disk space usage. It's included in the "coreutils" package, which you should have installed (you can check this by running "dpkg -l coreutils". If nothing shows up, you don't have it installed).

---

### Post by Polygon on 2006-11-05
> **Floola said:**
> I think it would be nice to include Floola in multiverse. As I have very little time and virtually no experience with packaging, I would like to know if there's someone interested in creating a package for Floola.

Please contact me by email.

Thanks,
Tomas

you could check out this page about getting software into multiverse

[https://wiki.ubuntu.com/MOTU/Packages/New](https://wiki.ubuntu.com/MOTU/Packages/New)

---

### Post by dasuberdog on 2006-11-05
If foola doesn't quit on me for one reason it quits on me for another.  Seems like most of it was a weirded out ipod that i finally got deleted with gtkpod.  Remind me never to use gtkpod again.  Anyway now it doesn't seem to be quitting on me.  I like the program...  Super easy.

---

### Post by andykrueger on 2006-11-09
When trying to run in Dapper, I get this message:

./floola: error while loading shared libraries: libcups.so.2: cannot open shared object file: No such file or directory

I do have libcups.so.2 in /usr/lib.  Can someone help me out please?

---

### Post by sw_ on 2006-11-29
just wanted to say that there's a new version that finally supports propper video transfering.

i find this is the easy way of managing your ipod without having to deal with gtkpod and the whole lib things. plus, artwork works;) :D 

still in early devel stage, but i'll never use amarok or gtkpod to manage my g5 ipod again.

---

### Post by drobvice on 2006-11-29
Can you point floola to a directory to sync?  I download podcasts and would like this option to minimize clicks and not drag and drop everything.  I can sync in a couple of clicks with gtkpod.

---

### Post by teeleef on 2006-11-30
Tomas,  I can't downolad Floola from your site.   Login and password screen keeps appearing.... any help or another mirror site?


Teeleef

---

### Post by Floola on 2006-12-01
Small problem with my mirror. Should be working ok now.

---

### Post by Floola on 2006-12-06
beta 20 is available! Greatly improved. Relies on gstreamer or xine so playback shouldn't be a problem anymore.

---

### Post by gentlemanmasher on 2006-12-09
What video formats can I put on the ipod or is it only mpeg 4

---

### Post by Anagonda on 2006-12-12
Wow, this is a nice app! I hated itunes in windows. And after I totally changed to ubuntu I hated gtkpod. Atlast a nice program to manage ipod!

It would be nice to have own "file browser" so I don't have to open nautilus or konqueror to drag files. But thats just a small thing.

---

### Post by Anagonda on 2006-12-12
Ok, now I found a little "bug". I got about 10 seasons of Simpsons in my ipod but floola says "0 videos" at the bottom right.

But I can find all the episodes with floola, theres that music icon on them and when I click edit, overview it says "Show in video" So is there a window for videos or what does this mean?

---

### Post by gentlemanmasher on 2006-12-12
I love this tool.  I wish there was a way to search by video and music.

---

### Post by Floola on 2006-12-12
> **gentlemanmasher said:**
> I wish there was a way to search by video and music.

Was added to beta 22 :-)

---

### Post by Floola on 2006-12-17
beta 23 available. Update strongly suggested as this version comes with many fixes and a new interesting feature, fast-mode. Under preferences->advanced you can enable this option which should significally increase speed of application.

[http://www.floola.com](http://www.floola.com)

---

### Post by gentlemanmasher on 2006-12-19
Will there be options for Photo's coming up.

---

### Post by Floola on 2006-12-19
No.

---

### Post by Floola on 2007-01-08
Beta 26 available! Since last posted version there's new folder sync feature, which should be fairly easy to use. Many bug fixes as well.

[http://www.floola.com](http://www.floola.com)

---

### Post by darkhatter on 2007-01-28
I guess this thread is dead now but can you add a feature to auto convert flac and ogg files to something a ipod can listen to.

---

### Post by Anagonda on 2007-01-31
Today I tried the newest beta. Now I see my videos on the bottom numbers.

But now I'm wondering is there anyway to browse the videos only? Because I can't remember the names of the videos I have. So it's not possible to search for them and I can't find them on the listings(artist,album,genre)
If theres not "browse videos only" option is it hard to add in the future?

---

### Post by Floola on 2007-02-04
In next version, b28, you can choose which media type to show.

I'm also looking for beta testers for the new podcast feature. If interested contact me via email, [http://www.floola.com](http://www.floola.com)

---

### Post by Floola on 2007-02-06
For those interested in trying the podcast feature: [http://www.floola.com/modules/newbb/viewtopic.php?topic_id=32&forum=1](http://www.floola.com/modules/newbb/viewtopic.php?topic_id=32&forum=1)

Tomas

---

### Post by Fingerz91 on 2007-02-07
Floola is great! However, for the next version, I think their should be a change generation option..... for those of us who own two types of ipods (i have a video and shuffle for my wife)

How exactly does Floola remember my preferences without writing files?

---

### Post by Floola on 2007-02-07
preferences are stored on iPod under iPod_Control\floola

HTH,
Tomas

---

### Post by Fingerz91 on 2007-02-08
> **Floola said:**
> preferences are stored on iPod under iPod_Control\floola

HTH,
Tomas

OK! I wasnt sure.... 

I love the program

---

### Post by Macdelaney on 2007-02-10
Hi, i'm new to both Linux and Floola.
I have an 80Gb iPod Video, and i've been having this problem:
mac@mac-desktop:~/Desktop/Floola-linux$ ./Floola
./Floola: error while loading shared libraries: libcups.so.2: cannot open shared object file: No such file or directory
mac@mac-desktop:~/Desktop/Floola-linux$ whereis libcups.so.2
libcups.so: /usr/lib/libcups.so.2 /usr/lib/libcups.so
mac@mac-desktop:~/Desktop/Floola-linux$

I don't know if i'm doing something wrong here, or if the files should be anywere else. 
Does anyone know how to fix this?
Thanks

---

### Post by Floola on 2007-02-10
64bit system? if so you'll need to install 32bit libcups as well.

---

### Post by Macdelaney on 2007-02-10
Forgot to mention that :P
Any idea on how to do that?
Thanks

---

### Post by Floola on 2007-02-10
have you tried copying libcups.so.2 to /usr/lib32? Post results. Thanks

---

### Post by Macdelaney on 2007-02-10
I tried that and i got the same problem, this is what i did:
mac@mac-desktop:/$ sudo cp /usr/lib/libcups.so.2 /usr/lib32/libcups.so.2
Password:
mac@mac-desktop:~/Desktop/Floola-linux$ ./Floola
./Floola: error while loading shared libraries: libcups.so.2: cannot open shared object file: No such file or directory

Did i copied it wrong or something? Also, this is something i find strange and can't understand it:
mac@mac-desktop:~/Desktop/Floola-linux$ whereis libcups.so.2
libcups.so: /usr/lib/libcups.so.2 /usr/lib/libcups.so

I mean, should be another entry in /usr/lib32?
Thanks

---

### Post by Floola on 2007-02-10
The problem is Floola looks for the 32bit version of a couple of libs (for ex libcups). I don't have a 64bit env so I never tried, but many users reported to have used floola successfully with your setup. Maybe someone else can give you a better hint.

---

### Post by Macdelaney on 2007-02-10
Great, Thanks.
Does anyone here got to run it in 64bits?

---

### Post by corefile on 2007-02-23
What is the license (GPL? BSD?)for this App? Where is the source for the app?

---

### Post by Floola on 2007-02-23
it's a freeware closed code application

---

### Post by uzd4ce on 2007-02-23
I just started testing Floola again (b30).  I'm specifically interested in the podcast functions.

Even after using it for a week or two, I'm still not sure exactly how it's supposed to work.  

[LIST]
[*]I've been running it from the desktop.  Am I supposed to, or do I need to, intall/run it from the Ipod directly?
[*]I need to run it from two different computers, one Ubuntu one WinXP.  Can I run one version off the Ipod or will I need different versions for each OS?
[*]When I ran it from the second computer, I think it downloaded the same podcast episodes as the last time.  What does it consider "new"?
[*]How do I unusbscribe from a podcast?
[/LIST]

I do like the program, particularly since it lets me sync podcasts at home, instead of with iTunes at work.  Any advice would be appreciated.

Thanks

---

### Post by Floola on 2007-02-23
Hi


> **uzd4ce said:**
> I just started testing Floola again (b30).  I'm specifically interested in the podcast functions.

Even after using it for a week or two, I'm still not sure exactly how it's supposed to work.  

[*]I've been running it from the desktop.  Am I supposed to, or do I need to, intall/run it from the Ipod directly?
Any location is ok.

> **uzd4ce said:**
> [*]I need to run it from two different computers, one Ubuntu one WinXP.  Can I run one version off the Ipod or will I need different versions for each OS?
You'll need one ver for each OS

> **uzd4ce said:**
> [*]When I ran it from the second computer, I think it downloaded the same podcast episodes as the last time.  What does it consider "new"?
Double check, it's weird it did dowload twice the same ep.


> **uzd4ce said:**
> [*]How do I unusbscribe from a podcast?
There's still no concet of *unsubscribe* as I still didn't found a user friendly way to implement it. At the moment either download manually selecting episodes or at worst delete podcast.


> **uzd4ce said:**
> 
I do like the program, particularly since it lets me sync podcasts at home, instead of with iTunes at work.  Any advice would be appreciated.

Thanks


HTH

---

### Post by uzd4ce on 2007-02-23
I know for sure that it re-downloaded episodes that were already on the iPod from iTunes.  I'll check again if it doesn't recognize ones that were originally downloaded with Floola at home.

Thanks for your reply.

---

### Post by %hMa@?b&lt;C on 2007-02-23
just to let you know, my brother, who uses windows loves your app.  I conviced him not to use iTunes, and he loves using floola with his 2g shuffle!

---

### Post by uzd4ce on 2007-02-28
I've been using the podcasting functions for a week or so now.  Everything pretty much works enough that I can dith iTunes, aside for the fact that I can't get video podcasts to work.  They download fine, but when they transfer they're not recognized as video podcasts.  I can see the file from the audio Podcasts menu, but it won't play there either.

Are video podcasts supposed to work, or is support limited to video podcasts for now?  Is there another way I could get the video file to the iPod?

I'm trying to load the Diggnation (small Quicktime) feed.  It works fine from iTunes.

Thanks

Ps  I'm now using beta32.

Pps  By the way, I deleted all of the episodes, and it appears to have unsubscribed me from the feed.  I'm trying to add the feed again, but I get an error about invalid feed url.  The feed is at [http://revision3.com/diggnation/feed/quicktime-small](http://revision3.com/diggnation/feed/quicktime-small).  Does it give an error because it's not a .xml?

---

### Post by Floola on 2007-03-28
Beta 35 is available. Huge performance boost with large artwork libraries. Many podcast issues fixed.

[http://www.floola.com](http://www.floola.com)

---

### Post by 454redhawk on 2007-04-17
> **Floola said:**
> Beta 35 is available. Huge performance boost with large artwork libraries. Many podcast issues fixed.

[http://www.floola.com](http://www.floola.com)


Floola: error while loading shared libraries: libcups.so.2: cannot open shared object file: No such file or directory

Mepis64 v6.5 (KDE)

Any suggestions?

---

### Post by jknotzke on 2007-04-29
Looks really fantastic. It's considerably ahead of most of the other Linux based iPod managers.

   Not sure if this has been asked before but:

   [LIST=1]
[*]Support Chapters in podcasts
[*]Download artwork from amazon or other artwork database
[/LIST]

  Thanks!

   J

---

### Post by smurphs on 2007-05-09
just wanted to say a quick thankyou for this software. i've been looking for something like this for months! here is your medal:

   _/\_
 VstarV
  /_ /\_\


Well done.

---

### Post by Dr Sketch on 2007-07-12
Hoping someone can help on this one...  I'm running it on a 64 bit machine (yeah, it causes a ton of problems).  I hunted down and installed all the libraries it needs to run, and it works fine when there isn't an iPod attached.  When there is an iPod attached, it loads then freezes (completely quits responding) and just sits there.  I installed the 32 bit version of xine (tried gstreamer, and it complained about it), but I also have the 64 bit versions of both gstreamer and xine installed.  Is it trying to load one of those instead?  It could also be a problem caused by the iPod: it has 4400 tracks on it, and they were all loaded by gtkpod.  gtkpod writes the same table for the MP3s that iTunes does, so that shouldn't be the problem, theoretically anyway...  Anyone have any ideas???

---

### Post by H.E. Pennypacker on 2007-07-12
> **Floola said:**
> it's a freeware closed code application

That is very unfortunate, and I hope you'll change your mind one day.

---

### Post by cometdog on 2007-07-29
No matter what folder I try to add under "sync folders..." the files column always says "0 found."  Is this intended to be a way to keep an ipod synchronized with music on the HDD?  If so how do I use it?  Is this intended to search the subdirectories recursively?

Other comments:
I have just switched to Ubuntu from Windows XP, where I used to use iTunes to manage my music.  I'm looking at Floola as part of my due diligence of checking out the different options available in Linux.  So far I am impressed with the light, quick feel of the program and the logical layout.

I'm disappointed, however, to find that Floola is not open source.  I could understand this if it's a matter of wanting to maintain control of the program and define a direction for it in early stages of development.  Seems like open source applications often have a problem with feeling like they were designed by committee, and where everyone and their brother junked it up by adding their own favorite feature.  Perhaps this is a reason why Floola so far is elegant and purposeful.

But its closed-source nature makes me uncomfortable about the future of the project.  When an application is open source I can depend on it to be there indefinitely, as long a it is relevant enough to maintain community interest.  When it's open source, discussions such as this thread are contributing to building community knowledge.

When a program closed source the benefits and learning from these discussions go into a black hole from which they may never emerge.  When it's closed source the time and effort that the community puts into the program by getting to know it, providing feedback on usage, interface, and bugs, could end up only used to line the developer's pockets if the developer decides to start charging for the software.

Please let us know if you are considering ever opening the source code.

---

### Post by diegogarvar on 2007-08-01
i'm wondering the same thing

---

### Post by timo1023 on 2007-08-01
I have the same problem, cometdog. I try to sync folders and it says 0 files found. How can this be fixed?

---

### Post by Floola on 2007-08-01
Hi,

I won't start a closed source vs open source discussion on ubuntuforums as it wouldn't make much sense. I chose this solution and hope that nevertheless you enjoy the application. Ohterwise there's gtkpod that afaik is a valid and good open source alternative.

About the bug, I'll check it as soon as I can. I'm working on a major feature at the moment which should be much appreciated...

Meanwhile you can add songs to iPod manually. Menu item->add...

HTH,
Tomas

---

### Post by Floola on 2007-08-03
Floola 1.5 is out! There are several bug fixes and a new feature to convert unsupported audio/video formats using FFmpeg. Unsupported formats include also YouTube an MySpace videos which can be added with 1 click just pasting the video page url.
Find more about this web download feature here:
[http://www.floola.com/modules/wiwimod/index.php?page=docs_troubleshooting](http://www.floola.com/modules/wiwimod/index.php?page=docs_troubleshooting) (see web download)

I tested this only briefly under linux and it seem to work so please give some more feedback if you can.

**Note**
FFmpeg has to be installed under /usr/local/bin compiling a recent SVN trunk as described for example here:
[http://po-ru.com/diary/bleeding-edge-ffmpeg-on-ubuntu-feisty](http://po-ru.com/diary/bleeding-edge-ffmpeg-on-ubuntu-feisty)

**Note2**
Support for other online video sharing site can be added fairly easily so if you think other sites besides YouTube and MySpace should be included drop a note


[*http://www.floola.com*]("http://www.floola.com")

---

### Post by thelinux_guy on 2007-08-03
This is a wonderful application! Even better than GTKpod! I'm am so looking forward to future releases :)

[IMG]http://i181.photobucket.com/albums/x278/JasonXD5/Screenshot.png[/IMG]

---

### Post by mpospisil on 2007-08-07
First Floola started off working great.  But now when I try opening Floola on my video ipod I get this error.

init error:
mhod, 1198, 5

To hide further error messages, hold shift while closing this window.  

How do I fix this error?  Please help.  I have been looking for a good ipod program for ubuntu because I don't like gtkpod.

---

### Post by Coruba67 on 2007-08-12
How do I get the friggin m4p files playing using floola... nice program!  :)  Just won't play those files I download of the itunes music store - which unfortunately I can't seem to get the other half of doing it any other way - and the music won't play in Ubuntu...

Does anyone know how to get this working...  Its that stoopid encryption thats being used - can't seem to get anything to decode it.

---

### Post by zeph7r on 2007-09-08
any solution to that "You have to mount your iPod in a folder under /mnt or /media" error so far?

This is really what's keeping me from running it..

Greets

---

### Post by rhenrick on 2007-12-22
I downloaded the latest version of Floola a minute ago and extracted the files. When i click on FLOOLA nothing happens. I made sure it is executable, which it is. ANY IDEAS? Also, i read that it can be installed and launched from your iPod. How is this possible?

Thanks in advance!
MERRY CHRISTMAS!

---

### Post by Nano Geek on 2007-12-22
I don't know if this has been asked before, but do the newest iPods work with Floola?

Thanks in Advance.

---

### Post by tomauty on 2007-12-22
> **asjdfwejqrfjcvm msz34rq33 said:**
> I don't know if this has been asked before, but do the newest iPods work with Floola?

Thanks in Advance.

Yes they do, I just synced some things on my Classic and it works just fine. Pretty fast too.

---

### Post by tomauty on 2007-12-22
> **rhenrick said:**
> I downloaded the latest version of Floola a minute ago and extracted the files. When i click on FLOOLA nothing happens. I made sure it is executable, which it is. ANY IDEAS? Also, i read that it can be installed and launched from your iPod. How is this possible?

Thanks in advance!
MERRY CHRISTMAS!

I do it by navigating to the folder in the terminal and typing ./Floola.

I couldn't get it to work by clicking either.

---

### Post by Nano Geek on 2007-12-22
> **tomauty said:**
> Yes they do, I just synced some things on my Classic and it works just fine. Pretty fast too.Wow that's great.
I'll try it now. 

Thanks a lot.

---

### Post by rhenrick on 2007-12-22
> **tomauty said:**
> I do it by navigating to the folder in the terminal and typing ./Floola.

I couldn't get it to work by clicking either.

Thanks for the tip, however this is what i get:

ryan@WryunUbuntu710:~/Desktop/Floola-linux$ ./Floola
[COLOR="Red"]./Floola: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory[/COLOR]

Any ideas?

Thanks!

EDIT:
I found a solution to my problem. I installed libstdc++5 and libstdc++6,
Found solution here: [http://www.floola.com/modules/wiwimod/index.php?page=docs_troubleshooting](http://www.floola.com/modules/wiwimod/index.php?page=docs_troubleshooting)
Look under LINUX and the first recommendation is to install the files.
Now Floola will launch when i click on it! WAHOO!
... I just need to wait for Christmas to get my iPod! LOL

---

### Post by Nano Geek on 2007-12-23
Also, if the creator of this program is still here, I ask him if he might release his program under an open-source license. 

It'd be less work for you, and we'd get more features.
A win-win situation. :)

---

### Post by DeadSuperHero on 2007-12-23
If I get an iPod for Christmas, I'm soooo trying this out!
A few questions:
-Can you only put m4a/mp4 songs on it?
-Is there any iPod that it doesn't work with?
-Can it sync with iTunes? (I don't really actually care if it can't, but I am curious.)

---

### Post by hipotermia on 2008-01-21
i'm using 7.04 and floola, but i can't add songs to my ipod 80gb classic

i select a folder, drag them to the icon, and after that, nothing...

---

### Post by PaganBlasphemy on 2008-07-22
> **rhenrick said:**
> 
EDIT:
I found a solution to my problem. I installed libstdc++5 and libstdc++6,
Found solution here: [http://www.floola.com/modules/wiwimod/index.php?page=docs_troubleshooting](http://www.floola.com/modules/wiwimod/index.php?page=docs_troubleshooting)
Look under LINUX and the first recommendation is to install the files.
Now Floola will launch when i click on it! WAHOO!
... I just need to wait for Christmas to get my iPod! LOL

Note that the command in their troubleshooting docs is wrong, it should be as so:

```
sudo apt-get install libstdc++5
```

sudo apt-get install libstc++6 doesn't return any hits, libstdc++6 was already installed for me.  libstdc++5 appears to be the correct library.

---

### Post by Floola on 2008-07-25
Floola 3.2 is available! Photo support greatly improved.

Get latest version here: [http://www.floola.com](http://www.floola.com) (to save bandwidth please download via bittorrent).

Tomas

---

### Post by ironwolfe on 2008-08-11
if I try running floola from a command window it says "Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed"

I've never used anything else than Floola and itunes.

I am trying to run it under:

OLPC - sugar
OLPC - Fedora /w XFCE Desktop
OLPC - xubuntu (from SD Flash)
Nokia N800 Internet Tablet - OS2008 (no ipod connected - host usb coming)

I have all the dependencies satisfied - but I am not sure what this error is requiring.

I have run as root and limited user, under xubuntu i tried sudo

I have tried versions 3.2, 3.0 and 2.9.6.

It works with the same ipod in Ubuntu 7.10 and Windows XP.

My guess is that it is missing some important dependency for GTK 2.0

I am going to try it on a hardy version of xubuntu and see if that works. What distro are you using?

---

### Post by Floola on 2008-09-28
Good news for iPod nano 4G owners! Floola 3.6 supports new model. Big overall improvements.

Get latest version here: [http://www.floola.com](http://www.floola.com) (to save bandwidth please download via bittorrent).

Tomas

---

### Post by Ripfox on 2008-09-28
Do you have plans to support IPhone or Ipod Touch?

---

### Post by Floola on 2008-09-29
As long as there's no way to mount the iPhone regularly (and not via wifi through SSH) I don't plan to add support to those devices. It's not easy to setup, it requires a jailbroken device and it's slow. In the future it might be possible.

---

### Post by thedon_1 on 2008-09-30
I get a problem using this. I used it once yesterday and really liked it but now when i open the program i get the floola main window and then a small empty box, no test what so ever and the program just hangs.

This is when i run floola with or wothout the ipod connected.

Im using Ubuntu 8.04.

Any ideas? I really like this program and want to use it as my main ipod maanger.

---

### Post by Floola on 2008-09-30
Weird. Try deleting the Floola folder under iPod_Control in your iPod.

---

### Post by Floola on 2008-10-11
New version available! Massive improvements (also in podcast management).


Visit [http://www.floola.com](http://www.floola.com)

---

### Post by maxxum on 2008-10-12
I tried the latest Floola on my 8.04 x64 Ubuntu installation with my 160gb 6th gen ipod. I supplied the correct fwid and it said the id seems allright. But it closes as soon as I launch it. When launching from the command line, it says 
```
Cannot find libgstreamer
Cannot find linxine
Segmentation fault
```

I have both gsteramer and xine installed in ubuntu. Ubuntu names these files as:
```
libgstreamer0.10-0
libxine1 (that is a number 1 after libxine)
```

So I am not sure what the problem is..

---

### Post by Floola on 2008-10-12
You're missing 32bit version of the libraries. See [http://ubuntuforums.org/showthread.php?t=640464&page=3&highlight=floola+gstreamer](http://ubuntuforums.org/showthread.php?t=640464&page=3&highlight=floola+gstreamer)

---

### Post by maxxum on 2008-10-12
It loaded after following instructions from that thread. I added two songs initially. Now when I reconnect and attempt to add more songs, it does not do so. I click Item -> Add and drag the files to the new window but the Add button never becomes active.

---

### Post by apd on 2008-10-13
getting this error message..

Sub PreferencesWindow.PreferencesWindow.Save( PreferencesWindow.PreferencesWindow )
Sub PreferencesWindow.PreferencesWindow.BtnSave_Action( PreferencesWindow.PreferencesWindow )
Sub Window.ShowModal()
Sub isiPodConnectedTimer.Event_Action()

any clues?
apd

---

### Post by graabein on 2008-10-13
> **Floola said:**
> New version available! Massive improvements (also in podcast management).


Visit [http://www.floola.com](http://www.floola.com)

I might be blind but I'm not seeing any links for screenshots?

---

### Post by apd on 2008-10-13
it says "Ipod not connected".
 well, it´s connected alright.

---

### Post by apd on 2008-10-13
and now it won´t quit when trying to close it..

---

### Post by apd on 2008-10-13
Im not even close on getting my hands on a windows machine to do the whole Itunes-thing described on Floola homepage.

---

### Post by Floola on 2008-10-25
Floola 3.8 is out. Many bug fixes. Tag read/write from mp3/aac files was greatly improved and podcast adding should be working fine now. Albanian translation added.

Get latest version here: [http://www.floola.com](http://www.floola.com) (to save bandwidth please download via bittorrent).

Tomas

---

### Post by Floola on 2008-11-09
for graabein: I've added some screenshots on the main page.


Meanwhile I released 3.9 which mainly improves podcast adding to iPod, which is now much faster.

As always get latest version here: [http://www.floola.com](http://www.floola.com) (to save bandwidth please download via bittorrent).

Tomas

---

### Post by Keith Hedger on 2008-11-09
> **Onyros said:**
> Hmmmm... I have a guess my wife will love this :P

She simply *HATES* iTunes, yet she loves her lil' iPod.

I'll post her reaction to Floola later on ;)

Have u ever thought of using rockbox? I use it exclusively and have done for over a year it does so much more than apples software ( ta least on my old ipod photo)
Home page is here:
[http://www.rockbox.org](http://www.rockbox.org)

---

### Post by stinkinrich88 on 2008-11-14
it'd be great if floola could support 64bit. the workaround messed my ubuntu up last time I tried it (problems with libc6 on updates, etc). Also, I still couldn't use it because it still had problems such as no flac support etc.

---

### Post by Floola on 2008-12-12
Floola 4.2 is out. Google Calendars can be synched just with one click. Many bug fixes. Slovak translation added.

Get latest version here: [http://www.floola.com](http://www.floola.com) (to save bandwidth please download via bittorrent).

Tomas

---

### Post by sanjit on 2008-12-14
I'll give that a go. Hopefully, no segmentation faults. Thanks.

UPDATE: No such luck.

---

### Post by Floola on 2009-05-24
Floola 5.1.1 is out. This version features major speed improvements and fixes several linux specific issues.

Get latest version here: [http://www.floola.com](http://www.floola.com) (to save bandwidth please download via bittorrent).

Tomas

---

### Post by Gucko on 2009-05-24
The screenshot page doesn't work dude

---

### Post by hanzomon4 on 2009-05-24
It works with the iPhone? seriously?

---

### Post by .Maleficus. on 2009-05-24
> **hanzomon4 said:**
> It works with the iPhone? seriously?
No.
[quote=Floola's Main Page]Floola is a freeware application to efficiently manage your iPod or your Motorola mobile phone (any model supporting iTunes except iPhone and iPod touch)[/quote]

---

### Post by DAE_JA_VOO on 2009-05-24
If this works with my 3rd Gen iPod Shuffle, I'll be happy :D

---

### Post by Floola on 2009-05-24
DAE_JA_VOO: if you try it please give feedback just to know if it's compatible with the new shuffle. Also remember to run iTunes at least once before using Floola, as stated in online docs.

---

### Post by Noah_Kapiolani on 2009-05-24
Yes, please tell us if this works with 3rd Generation iPods!!!  The day that i find a linux compatible program that can simply access the iPod and also be able to remove or copy said music is the day i will buy a shiny new iPod  Scores of iPod fans await with baited breath

---

### Post by Floola on 2009-08-21
Floola 5.3 is out now. [http://www.floola.com](http://www.floola.com)

Now much faster than before.

---

### Post by Floola on 2010-10-23
Floola 6.0 was released! Biggest new feature is Facebook integration to share music played in Floola with friends.

Get it now here: [http://www.floola.com](http://www.floola.com)

---

