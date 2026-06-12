---
title: "Shift from jaunty and karmic alpha 4 first looks"
date: 2009-08-24
forum: Testimonials &amp; Experiences
---

### Post by dumblebee100 on 2009-08-24
First of all I need tell that I'm a die hard linux fan.. I have used linux from redhat linux, --> fedora 4 to fedora 10 and then I shifted to ubuntu 6.10 and then 8.04( I think ) then Jaunty and now karmic  ...This is my linux history 

After reading all my story don't feel that Im a linux critic ...if I really don't like linux I would not be using since redhat linux

Im just comparing my two ubuntu experiences and dont feel Im a windows fan or something ...I didnt boot into windows since some 3-4 months 
If I get everything which are used for general purpose computing then I never login into windows .( ohh those viruses make me sick )

**my operating systems details **
windows xp long since I know how to use a computer ( but anyways dont care bcz now Im not using it )
jaunty beta ( not a single update installed and it worked flawlessly) 
now karmic alpha 4 ( all updates installed and my linux is updated to this hour of writing  this post )

**Now I want to tell why I shifted from jaunty **

Jaunty is good but not best .. I have myraid of problems with it ..they are not huge but its like a nuisance all the time 

1) I use pidgin a lot ..I have been using before the name changed and from fedora 4 ..I dont know exact version ....Its a wonderful client but my feeling is that the development is dead slow ( do u believe this thing ..When I switch on my computer I visit the pidgin developer page first but nothing much changes there ) 
till 2.5.6 there are no much problems but out of curiosity I tried 2.5.8 but it doesnt connect to google talk and says **segmentation falut** ..
but when the same version when installed on windows it works fine ..so I installed windows version with wine and what I get all the time is pidgin.dll load error some 126 or something ..I googled up but not much help 
so since linux version and windows versions are not working for me ..I have to try pidgin portable version ...atlast this works ...but from time to time I get errors like **cannot open the file "path to pidgin portable installtion dir "**
so I have to kill it and then manually open nautilus and then again click it to load up
after a 2 months continious usage I got vexed by this non sense 

2) I have a bluetooth adapter which is motorola and I have some code on it ...right now I dont have it ..
even from fedora 4 and ubuntu I was never able to connect to my phones ( sony ericsson k800i and w580i ) with the bluetooth adapter 
I tried all the ubuntu forums, google links and edited every option in config files but nothing worked ...by following some tutorials I can detect my adapter but could not connect ..problem with hid ( my system doesnt have it..even I installed everything related to bluetooth but hid still not present )

since Im a die hard fan of linux ...guess what did I do ....I took my bluetooth adapter and packed it in the same box which it came and threw in my shelf 

I used to try now and then I mean like one or two months ( I thought that there may be some development in that field so again my bluetooth adapter may work ) but the history repeats itself every time 

3) I also have webcam ....but after some time of googling I found out that it will not work in my linux ..so the same packing and in same shelf ( dont ask me again..I threw it ) 

4) I use nautilus a lot ..so I made some buggy script by which we can toggle from button style bar to address location style ...for one session everything worked very good ..by pressing ctrl+atl+l I could toggle between both views ...but after logout and login nautilus dont open ..so I have to manually edit gconf settings from terminal and set the always-use_location_entry .to false....and that too mandatory otherwise nautilus dont open ..so I thought of reinstalling gconf again ..but it needed some 500+ mb so left it ..and continued to use only button style ....when I press the pencil button I get key not writable error everytime ( I know its mandatory but before also I used to get it after execution of script ) I had to made it mandatory false in order to run nautilus ...
so this was my problem ..so  I thought of trying another OS 

5)I used to use my phone explorer for my phone to sync with system in windows ....but in linux the close replacement was wammu ....but its not up to the mark 

6)Some years ago I used windows and winamp is really good ..I mean the sound clarity ...In linux the sound is good but not the best as compared to winamp ....I also used songbird ...Its good but high on resources ..I mean its same as firefox ..so Idont want to waste another 100mb just to listen a song ...I also know the options like quod libet .rhythmbox ,,vlc ,mplayer ..gnome-mplayer ....
and out of these I like mplayer the most ..even when compared to winamp when considering video and audio play back ...

Mplayer can display a video in split second even when the cpu is above 60-80% ( This is really awesome ..all the other video players are not even close to this great gaint ....if the developers take interest and develop a frontend to present mplayer itself..then no one ever talks about winamp or itunes)...and mplayers volume is 30% more than windows winamp but not that crystal clear( this is problem of audio drivers in linux and digital effects may add in winamp)

7)when I used nautilus in jaunty ...it behaves strange ..when I leave my system for around 30 mins or so ...then all my mounted drives become write protected ....I mean I cant create any file or modify any thing ...so I have to close all my nautilus tabs and restart everything ( just nautilus ) another strange thing is ..when I remove thumb drive or usb memory devices like my external HDD ..without unmouting( I know that we have to unmount and then remove device but all the time I dont use it some other may also use it)  ...then next time those drives dont connect unless I restart system ...this was really annoying ...( I think that was jaunty I have was just beta ...do u people observe this )


eight)I have launchers in gnome panel I have it autohide and transparent but some times it doesnt hide ..so it makes my work harder .because I have to move all my windows to close it or else use ALT+SPACE+C 
so to rectify it I have to restart gnome-panel when ever it dont hides ...
There are also many problems ..If I write all things up ..I can write a book so I stop here


**Karmic first looks  **

1) I heard about there will be visual changes in karmic ..but I dont observe any ....the same old theme, colour ..the same login screen ....ohh **** when are these poeple gonna develop ...In a year or so we all would have mobiles which do our everyday computing even the graphics in mobiles are better than in ubuntu but still we are here at ugly gnome first looks ...( I know how to make it better ...but always first looks counts ) I think someone said about this in karmic developer summit 
anyways I dont complain about it ..bcz still its alpha 4 

2)There was much hype about the KMS issue ....I have seen the booting process video in fedora site..it was really awesome ....I thought ubuntu will be even better ...but what do I get .....grub looks ever bad ..v 1.96 ...then after the screen flickers about 4-6 times until I get login screen ...I may not acitivated KMS in some config files but they said that it will be default in karmic ..again ..its still alpha 4 ..so I will wait till final release for better review

3)XORG ....this one was really show stopper ....
my brother once worked for gsoc and his project was something about aglix ..then he used to say that
**IF LINUX HAS TO DEVELOP THEN THE FIRST STEP IS XORG**

then I said dont we have alternatives like gnome or kde or xterm ..then he said ....if we have that many alternatives for XORG ..linux will be top on market 

even from past days ..I dont have a good opinion about xorg and xserver related things .....

I never got graphics or correct resolution on the first go ...everytime I install the first thing I have to edit is xorg.conf ...and you all know that it was not easy some 2-4 years back ...
and even now in karmic ..I have to edit ....I just copied the previous xorg.conf which worked in jaunty(1200x1024 resolution) to  karmic but karmic is not respecting it I think so 

when I first booted into karmic I got 1024x768 ...everything was really big ..by the way who are still using this medium resolution.....
where is the support for higher resolutions, wide screens .and all that 

messing with xorg.conf is really not advisable for starters ...so why dont the linux people give on the fly support for these 

I edited xorg.conf ..I put vesa it worked for this 1280x1024 but slow ..

so all I have to do this after some search 
```

#!/bin/bash
sleep 3 &&
xrandr --newmode 1400x1050  121.75  1400 1488 1632 1864  1050 1053 1057 1089 -hsync +vsync
xrandr --addmode VGA1 1400x1050
xrandr --output VGA1 --mode 1400x1050
```

I have to execute this script at startup ...If I execute this directly it wont correct resolution ..so I have to make another script to call this script ..then it worked ..so till that precious 10 seconds time wasted during bootup ....again its still alpha 4 ...so no offence

4)Karmic says that it can automatically mount drives but ..does it really ...bcz it didnt worked in my case ....it even dont like fstab settings 
when I enter my password for mounting which comes at startup then any of the one partition gets mounted not all ( I have 4 other partitions which are vfat type) 

my fstab has UUID=xxxx-xxxx which I got by using "blkid" and worked flawlessly in jaunty but not in karmic ...
I know hot to edit my fstab but I dont know that karmic dont accept UUID's so I have to replace all those UUID things by labels ...otherwise karmic says those are special symbols .and it cant mount when I give the command 
```
sudo mount -a
```


5)At last I got to desktop after 6 hours of messing with all types of things ..xorg.conf ..fstab ..
now the partitions get mounted automatically but not the USB drives ..I also have a 2 gb thumb drive and 320 gb external HDD 

I should mount them manually by clicking the partition in nautilus ...
In jaunty my 320 gb hdd takes nearly 5-6 seconds to list folders ..but in karmic it takes good 15 seconds or more ..or sometimes nautilus crash 
again Its still a alpha release ..so no offense

6)Another major thing ...in jaunty my memory usage and cpu usage is very low ..
cpu <65 degrees during work ...unless I do some ripping 
RPM <3000
cpu <25 % regular work firefox 7 tabs or so gedit 3 or more tabs  nautilus 5 tabs and other things like conky, gtkdesktopinfo, tracker, etc.,
RAM nearly 250-600mb  it takes 600 if I open many applications 

( windows can never beat this values by opening these many things )

but now in Karmic even at idle the
cpu >60 %  major processors are xorg 15-20 % gconfd-2 15-20% awn-applet-activation  15-20% all the time 
cpu >75 degrees temperature when computer is idle ..if I start something it goes to 81 ...at 90 my cpu fries 
RAM far more than jaunty ..
RPM >4300 all the time 

if I open system monitor ..it itself takes 70% of my cpu( even under jaunty it uses nearly 20-25% which is so ridiculous for that application ) .so Im using 

```
ps -e | grep processname
```

All the time it's like a motor running near my ear ...this time my power bill gonna hike ..bcz 80 degrees and 4300RPM all the time is not good

My system was dead slow ..but just working ..Im happy for that ..so far my transition from jaunty to karmic doesnt made my happy .(anywas pidgin and nautilus are my major reasons for shift ..they work for me now atleast with some workaround)

7)My conky is now whited out ..I mean ..after running conky for some seconds ..the background of it becomes white ..
and some other times ..I get some strange XORG error 
and more problems with gtk-desktop-info 
I have scripts to start conky and gtk-desktop-info ..so when I executed the second I get many errors telling me that** console message ..not allowed to load local resource**

after all Im just reading from /usr/share directory ..I dont need extra permissions for that ....but still I gave permissions and changed owner of gtk-desktop-info to my account but still error persists

you can see the errors in my screenshot 

I gave every authorization in ADMINISTRATION--->AUTHORIZATIONS
but still nothing much chagnged

8)The command 
```
gnome-session-save --shutdown-dialog
```
when I press restart karmic just logs out and logs in ....this is one nuisance case 
so I have to use this command everytime from terminal
```
sudo /sbin/suhtdown -r now 
```
another is about gtk-desktop-info ...Im just reading files from /usr/share ...but it doesnt allow me to 
9) atlast my bluetooth adapter works fine without editing any config files ...now this is a real improvement 
and regarding audio and video chatting pidgin I didnt try yet 


In this review I just discussed about the cons of past and present ubuntu ...there are tons of pros which if I write .may take another book 

I expected a lot from karmic ...face book login or atleast better ones than the default 

nicer theme ...good icons ...great first looks ...smooth booting as in fedora plymouth ...on the fly different resolutions support ...automouting will be fine if it mounts all my drives ....
I searched gconf settings for nautilus ..many are deprecated ...but where are the new ones ....nautilus should have some better features like icon grid layout ...mounted partition details ..like usage and left out space ..strong integration with other applications ..like when we are extracting a archive it should ask to extract here or to a other folder ...and more options from nautilus is always welcome ....because most of the time I work on nautilus ..I want it to be perfect ...

---

### Post by bapoumba on 2009-08-24
Moved to Ubuntu Testimonials & Experiences.

---

### Post by HappyFeet on 2009-08-24
Wow. Too long for me to read. May I suggest Microsoft? I heard their profits are down this year. Perhaps you could help them out with that. ;) Btw, I'm being sincere.

---

### Post by ngsupb on 2009-08-24
> **dumblebee100 said:**
> I expected a lot from karmic ...face book login or atleast better ones than the default 

I found the same with Jaunty, nothing is changed from the first look. 

But appears they have done some good background work to reduce its resource usage. It uses about 220 mb of ram compared to 280 on 9.04 for me.


Lets wait for the design part too, it isn't finished yet

---

### Post by solwic on 2009-08-24
> **ngsupb said:**
> I found the same with Jaunty, nothing is changed from the first look. 

But appears they have done some good background work to reduce its resource usage. It uses about 220 mb of ram compared to 280 on 9.04 for me.


Lets wait for the design part too, it isn't finished yet

Ubuntu has basically looked the same from the beginning to now.  Very few changes aesthetically.  

I read somewhere that it's "supposed" to "change" in 10.04, but I wouldn't hold my breath.

---

### Post by HappyFeet on 2009-08-24
> **iRun said:**
> 
I read somewhere that it's "supposed" to "change" in 10.04, but I wouldn't hold my breath.

Even if it does not change, I will still use it, because it's the best OS I've ever used. Besides, looks are only skin deep.

---

### Post by Mike_IronFist on 2009-08-25
Why does anyone really care about how Ubuntu LOOKS?

You can customize GNOME to such obnoxious detail that you don't need to concern yourself with pointless things like its default appearance.

I don't care if Ubuntu stays plain-looking forever, because with a few clicks, I can make it prettier than Mac OSX or Windows could ever be.

Let's also not forget Compiz Fusion, and the upcoming Gnome Shell.
Both provide some serious eye-candy.

Ubuntu is extremely modular in that regard, and there's no reason to whine about how it's going to look or currently does look, because with a little bit of searching on [the Gnome-Look website]("http://gnome-look.org/") and the installation of Compiz Fusion, one can easily turn it into a gorgeous peice of software.

Also, the Karmic artwork is not coming until August 27th or 28th.

Marc Shuttleworth says Ubuntu is saying goodbye to brown, so there is rejoicing to be had there.

On a side note, if you ask me, I find Windows XP and previous iterations the ugliest OSes ever. Though Vista and 7 more than make up for those insults to the eyes.

---

### Post by running_rabbit07 on 2009-08-25
I am not going to knock other OSes but I will say that I love how I can download a new theme every month or two and make my system look totally different. This is one of the things that makes Linux so special. 

To the OP, I would recommend a fresh install of 8.04 Hardy LTS. I had the lowest idle CPU and RAM usage with that release. As far as bluetooth and webcams go, I don't use either one. I am too cheap for bluetooth and the webcam is a waste because I don't care to have people watch me geek out.

---

### Post by ad_267 on 2009-08-25
Ok to be honest I gave up reading all of that but just a few points from what I got through:

The theme isn't supposed to change a lot until the next release, but there will likely be a few small changes. And this is an alpha release, those visual changes aren't included yet.

KMS is only supported for Intel video cards in Ubuntu I believe.

It's still very early in development so expect a lot to change.

---

### Post by ngsupb on 2009-08-25
> **dumblebee100 said:**
> but now in Karmic even at idle the
cpu >60 % major processors are xorg 15-20 % gconfd-2 15-20% awn-applet-activation 15-20% all the time
cpu >75 degrees temperature when computer is idle ..if I start something it goes to 81 ...at 90 my cpu fries
RAM far more than jaunty ..
RPM >4300 all the time


Something went really wrong though :)

---

### Post by solwic on 2009-08-25
> **HappyFeet said:**
> Even if it does not change, I will still use it, because it's the best OS I've ever used. Besides, looks are only skin deep.

> **Mike_IronFist said:**
> Why does anyone really care about how Ubuntu LOOKS?

You can customize GNOME to such obnoxious detail that you don't need to concern yourself with pointless things like its default appearance.

I don't care if Ubuntu stays plain-looking forever, because with a few clicks, I can make it prettier than Mac OSX or Windows could ever be.

Let's also not forget Compiz Fusion, and the upcoming Gnome Shell.
Both provide some serious eye-candy.

Ubuntu is extremely modular in that regard, and there's no reason to whine about how it's going to look or currently does look, because with a little bit of searching on [the Gnome-Look website]("http://gnome-look.org/") and the installation of Compiz Fusion, one can easily turn it into a gorgeous peice of software.

Also, the Karmic artwork is not coming until August 27th or 28th.

Marc Shuttleworth says Ubuntu is saying goodbye to brown, so there is rejoicing to be had there.

On a side note, if you ask me, I find Windows XP and previous iterations the ugliest OSes ever. Though Vista and 7 more than make up for those insults to the eyes.

I'm not talking about themes.  Themes are easily changed (even if half the dark ones don't work properly).  I'm talking about significant DE changes.  Better panels, more inherent options in Gnome.  Think of the change from KDE 3.5 to KDE 4.  Pretty big changes aesthetically.  

And I'm not saying I'll ditch Ubuntu.  I love it, and won't use anything else.  I don't *expect* it to change.  I just wish we'd see some basic DE function/appearance changes.  Beyond what can be accomplished with a simple theme/icon change.  

Anyway, to each his or her own, I guess.

---

### Post by HappyFeet on 2009-08-25
> **running_rabbit07 said:**
> I love how I can download a new theme every month or two and make my system look totally different. 

Every month? Ummmm you can do what you want on a daily basis.

---

### Post by vedek on 2009-08-25
> **HappyFeet said:**
> Wow. Too long for me to read. May I suggest Microsoft? I heard their profits are down this year. Perhaps you could help them out with that. ;) Btw, I'm being sincere.
 
+1 
 
i was tempted to test karmic on my lab machine but i am resisting because i don't want to ruin it for later

---

### Post by running_rabbit07 on 2009-08-25
> **HappyFeet said:**
> Every month? Ummmm you can do what you want on a daily basis.

I know, but that is too often for me. The point was that I have the freedom to do it whenever I wanna see something different.

---

### Post by dumblebee100 on 2009-08-25
> **ngsupb said:**
> I found the same with Jaunty, nothing is changed from the first look. 

But appears they have done some good background work to reduce its resource usage. It uses about 220 mb of ram compared to 280 on 9.04 for me.


Lets wait for the design part too, it isn't finished yet

280 mb for jaunty is more than awesome because I use a lot of applications ..I opened some 5 nautilus tabs.. gedit 6 tabs ...root nautilus ,,,,gcolor2 ..firefox 7 tabs ...dont forget all other extra effects compiz ..conky gtkdesktopinfo ..many services ...still too my jaunty doesnt exceed more than 600mb in any extreme case ..I do ripping much ..even then memory print is very low ..and Im thankful to linux for this ..


well yesterday updates corrected mounting bugs I think so ..my usb drives are mounting automatically ..
Again thanks for karmic 

**Hey folks does anyone know how to disable new window when some USB drive mounts ...I just want to work with one nautilus ...when they can be opened from new tab why I need another nautilus window**

---

### Post by dumblebee100 on 2009-08-25
> **vedek said:**
> +1 
 
i was tempted to test karmic on my lab machine but i am resisting because i don't want to ruin it for later

Dont worry bro 

Just try it ..I may run into problems but u may not ...I just wrote my experience and asking for users thta even they do experience the same ..so I can report a bug 

but I warn you ...alpha versions are not for complete noobs ...

alpha versions do have new features but they will not be bug less ..so one should know how to work around them ....if anyone don't know them then please wait for the final release or RC releases ...

By the way karmic is not all that bad ..

alpha versions are for testing purposes ..so one who testes them have right to report bugs and they will do ...but normal users just complain that there is some bug ..but they dont write any bug report ..but I do

---

### Post by dumblebee100 on 2009-08-25
> **iRun said:**
> Ubuntu has basically looked the same from the beginning to now.  Very few changes aesthetically.  

I read somewhere that it's "supposed" to "change" in 10.04, but I wouldn't hold my breath.

ohh I can wait for that ....could you please gimme any proposed features for 10.4

---

### Post by dumblebee100 on 2009-08-25
> **running_rabbit07 said:**
> I am not going to knock other OSes but I will say that I love how I can download a new theme every month or two and make my system look totally different. This is one of the things that makes Linux so special. 

To the OP, I would recommend a fresh install of 8.04 Hardy LTS. I had the lowest idle CPU and RAM usage with that release. As far as bluetooth and webcams go, I don't use either one. I am too cheap for bluetooth and the webcam is a waste because I don't care to have people watch me geek out.

Hey running_rabbit 
I agree with you 
you just download themes but I do make my own themes 

lately I made a really flat theme gtkrc and metacity also ...( I didnt uploaded to gnome-look.org because I liked it much but others may not like it ..anyways I will post after some days or so )
I dont think that much of other OSes will allow me to do that ..so Im grateful to linux

---

### Post by HappyFeet on 2009-08-25
> **iRun said:**
> I just wish we'd see some basic DE function/appearance changes.  Beyond what can be accomplished with a simple theme/icon change.  


And what is *your* part in all of this? Are you part of the solution or part of the problem? Hoping and wishing *may* make it happen, but in the end, only *you* can affect change.

---

### Post by Copernicus1234 on 2009-08-25
Its easy to disable ip v6 in karmic (because its a new kernel, so it works in 9.04 as well if upgrading the kernel)

sudo sysctl -w net.ipv6.conf.all.disable_ipv6=1

Works perfectly. Internet gets much faster for me.

---

### Post by solwic on 2009-08-25
> **HappyFeet said:**
> And what is *your* part in all of this? Are you part of the solution or part of the problem? Hoping and wishing *may* make it happen, but in the end, only *you* can affect change.

I'm not sure why you always strike such a defensive pose on this forum, but I'll go ahead and answer this.  

My part is nothing.  I'm not a programmer, or a graphics designer.  I don't pretend to be.  I'm not demanding change, I'm merely expressing my opinion and wish to see it changed.  If the Ubuntu "designers" can't take constructive criticism without expecting someone to do their work for them, well, that's their problem.  

Besides, one isn't *required* to make a contribution to share their opinions or wishes.  It's that type of mentality that hinders progress; the idea, for instance, that we all can't drive hybrid cars and help the environment simply because we're not all mechanics or engineers.  That type of thinking is backward and counter-productive.  

As for being part of the problem, I'm not sure how that can be.  I'm not trying to block their every move to make a sleeker desktop environment.  My action is inaction.  I use Ubuntu, and love it.  I think the default look of Ubuntu is ugly, and I'm fine with continuing to change the default look with every release that refuses to change, that continues with the same, ugly default look that more people than I have been complaining about for years.  

If you have issues with my stance on this, well, that's your little red wagon.  I love Ubuntu, but it is ugly.  I hope they change it.  If they don't, they'll just keep passing the responsibility of updating an archaic desktop environment on to the very users who keep them in a job in the first place.  

Of course, wouldn't be the first time an OS company passed off their responsibilities to the end user, would it?

EDIT:  Also, if I might make a suggestion:  you'd be a much more pleasant person if you stopped taking every criticism against Ubuntu and/or Linux as a personal insult.  I know you of old, HappyFeet, and I know you're not stupid.  But your attitude is getting in your way here, I think.  You could be such a valuable resource for new users if you had but the will to see things objectively.  

Not an insult, mate, just an observation.  Nothing personal intended, and from what I can tell of the CoC, I haven't violated any "rules" by saying that.  

In any case, take it how you will.  :)

---

### Post by Sethun on 2009-08-25
> **HappyFeet said:**
> Even if it does not change, I will still use it, because it's the best OS I've ever used. Besides, looks are only skin deep.

Well said. And I agree it's a very good OS.

---

### Post by HappyFeet on 2009-08-25
> **vedek said:**
> +1 
 
i was tempted to test karmic on my lab machine but i am resisting because i don't want to ruin it for later
One more person testing karmic will not hurt. We could use more bug reporters. Even if the bug is already reported, leave a comment that you are affected as well. Every little bit helps.

---

### Post by HappyFeet on 2009-08-25
> **iRun said:**
> I'm not sure why you always strike such a defensive pose on this forum

I'm sorry you see my posts as such. I am just a realist and not a dreamer. 

Also, do I think things could change for the better and be different with ubuntu? Sure. But if I am not willing to do *my* part in all of this, then I feel I don't have a right to discredit anything. 

I am also not a programmer, but do my best to report bugs and such, *in the appropriate areas*. Whining on these forums that icons overlap on the desktop when a flash drive is inserted, does nothing. That's why you will never hear me complain about something that I can not change. I can however, go to Launchpad and report my experiences so that the developers will see that I have a problem and hopefully fix it.

Ubuntu is a community effort. If you are not part of the solution, you are part of the problem. It's not being defensive, it's being real and honest. Ubuntu belongs as much to you as it belongs to Canonical. If you don't like what I have to say, that's OK. But I do know that a lot of people *will* agree with me, so I am not alone. Go in peace and have a nice day.

Edit: The phrase "if you are not part of the solution, you are part of the problem" is not meant to be taken literally. It is meant to invoke a feeling that we are all in this together. I do realize *you* are not "blocking" canonical from achieving anything. But then again, you might not be helping either. *You* can make a difference. Just believe, and make it happen.

---

### Post by solwic on 2009-08-25
> **HappyFeet said:**
> 
Ubuntu is a community effort. If you are not part of the solution, you are part of the problem. It's not being defensive, it's being real and honest. If you don't like what I have to say, that's OK. But I do know that a lot of people *will* agree with me, so I am not alone. Go in peace and have a nice day.

Therein lies the break in your logic.  Just because I may or may not be part of the solution does not mean I have to be part of the problem. I'm a neutral observer, outside of the problem/solution equation.

Since this is the foundation the rest of your argument is based upon, the whole thing collapses.  Again, this is a sign of your defensiveness.  It's the "with us or against us" attitude.  Divisive, and good for an argument, but it doesn't get anything done.

In any case, I'm done discussing this.  You think your way, I'll think mine, and we'll all be happy.  :)

Cheers.

---

### Post by running_rabbit07 on 2009-08-25
After reading some of the posts, I find it amazing how every time someone starts a thread with constructive criticism, there are always people that take complete offense. Not much Ubuntu going around.

---

### Post by solwic on 2009-08-25
> **running_rabbit07 said:**
> Not much Ubuntu going around.

Never was, sadly.  "Ubuntu" is a grand idea, but there's a reason grand ideas always remain grand ideas:  they're unrealistic.  

Ah well.  :biggrin:

---

### Post by Dullstar on 2009-08-26
OH PLEASE.  Is it THAT hard to change the theme that you can't do it without complaining?  I'd show a picture of my custom theme (I like it, but there's no law saying you have to), but I'm to lazy to upload it right now.  The theme I am using actually was just made by combining elements from the themes that came with Jaunty.

---

### Post by Tamlynmac on 2009-08-26
Yawn....

So many of these threads could easily be perceived as Recurring Discussions. The same verbiage and complaints. Hopefully, Karmic will provide some with fresh ideas.

I don't care what OS others use. I use what works for my family & I and have for quite a while. I don't waste time complaining about Windows or comparing one OS to another. Why bother? The number one criteria (for us) of any OS, is that it meet our requirements and provides us with a stable platform. Benefits like maleware free - are a bonus. Ubuntu & FOSS have met that challenge time and again.

Should we find that an OS no longer meets our requirements, we will seek out an agreed upon alternative and convert. I will not waste time or energy pointing out deficiencies on a forum. Once I've made the decision there's no reason to seek approval or waste time endeavoring to convince others.

IMHO, all should decide what OS best fits their needs and "Simply Use What Works". I seriously doubt using one OS over another, represents a life threating decision for most of us.

Just my $0,02_** **_

---

### Post by HappyFeet on 2009-08-27
In the spirit of what this thread was originally about, I have to say karmic is giving me some big  troubles. But I guess this is to be expected at this point. And yes, I am reporting everything that I can. Hopefully I am making a difference, no matter how small. But it's definitely not ready for everyday use.

---

### Post by dumblebee100 on 2009-08-28
recent trouble from myside 

I have a mega ones I think 

my cpu is 100% at idle ..
the major culprits are 

pulseaudio -->70 + 
gconfd-2   -->20 +
xorg       -->10-15

these things varies  +/- 10 cpu %

so I stopped the process pulseaudio ( I thought that it will free my cpu ..anyways at that time I dont need sound ..Im not listening to anything )
so after stopping there are another set of processess which took over

sreadahead  -->50+
gconfd-2    -->40+
xorg        -->10-15

these things varies accordingly to achive 100% .....
other things are stable but I cant use my CPU running 100% all the time ...so I just moved to windows temporarily ...I got this situation after upgrading to latest pulseaudio .. Ithink it broke my system ...so when are the patched packages comming ..then I will upgrade and move to ubuntu ..

does any on of you observe this ..

---

### Post by Tamlynmac on 2009-08-28
No.

I suggest you post your question in the appropriate help section. You might also search the sections for similar issues. The answer may already exist.

Note:
The help sections are specifically for that purpose.

---

### Post by mdsmedia on 2009-08-28
> **dumblebee100 said:**
> recent trouble from myside 

I have a mega ones I think 

my cpu is 100% at idle ..
the major culprits are 

pulseaudio -->70 + 
gconfd-2   -->20 +
xorg       -->10-15

these things varies  +/- 10 cpu %

so I stopped the process pulseaudio ( I thought that it will free my cpu ..anyways at that time I dont need sound ..Im not listening to anything )
so after stopping there are another set of processess which took over

sreadahead  -->50+
gconfd-2    -->40+
xorg        -->10-15

these things varies accordingly to achive 100% .....
other things are stable but I cant use my CPU running 100% all the time ...so I just moved to windows temporarily ...I got this situation after upgrading to latest pulseaudio .. Ithink it broke my system ...so when are the patched packages comming ..then I will upgrade and move to ubuntu ..

does any on of you observe this ..
I'm assuming you're using hardware capable of running Windows 7, so I won't ask the obvious "what are your system specs" question.

Please ask in the appropriate support forums, because you've obviously got some system problems.

---

