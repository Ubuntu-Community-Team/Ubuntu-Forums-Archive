---
title: "Observation of Instability"
date: 2014-01-26
forum: Ubuntu, Linux and OS Chat
---

### Post by craig10x on 2014-01-26
I love using Linux and especially ubuntu...I run Ubuntu with Unity...My hardware is a Toshiba Laptop 17" screen with i3 core and intel graphics (it is about a year old)...I've noticed the following instability factors:

1) When listening to stream radio (i listen to talk radio a lot) using either the streamers from the stations themselves or iheart radio also, that you will often hear a word repeated twice...everything may sound fine for a minute or two and then one of the words spoken is "doubled" and then the rest of the sentence is fine...
for example: you might hear:   "The weather forecast for this aftertoon will be cloudy cloudy with a temperature of" and so forth...

2) When watching videos on you tube (especially music videos) there will occasionally be a momentary jump where it will skip a second or two...doesn't happen everytime, but often...

3) When listening to mp3 on a music player such as rhythmbox, the same thing (momentary jump with a second or two skipped)....doesn't happen all the times, but often...

4) When watching videos on totem or vlc media player, occasionally there will be little "jump" in the video (for a second or two)...

Now, when i ran windows 7 on this same laptop everything was super smooth and stable regarding the four items i mentioned above...
Even more recently, i ran and installed a disc for windows 8.1 and observed the same super smooth and stability just like when windows 7 was installed...

I don't recall having these things years ago, when linux was Gnome 2 (don't know if that has anything to do with it) although during those years i was mostly running computers with amd and not intel (don't know if that has anything to do with it either)

I was wondering if others have noticed any of these things on their linux systems?   I find linux to be very stable otherwise but this really makes me wonder what the heck causes these things on linux...
Why does windows seem to have the big advantage on that?

I never have posted about this before but my curiousity has gotten the better of me...all feedback will be welcome :D

---

### Post by monkeybrain20122 on 2014-01-26
Are you running 14.04? I have none of these problems with 13.04 or 13.10.

---

### Post by craig10x on 2014-01-26
Yes i am...but it's not because it's 14.04....i got it even on all the final stable versions i have run such as 13.10, 13.04 and going back even further...my current laptop is intel i3 with intel graphics and my previous one was also...prior to that, when gnome 2 was still around, i ran mostly amds and maybe an intel celeron one time (going backward in my ubuntu history which started with 8.04)...

The strange part is i get NONE of those when running windows on the very same computer...

Interesting...i was wondering what kind of hardware you have? (also, anyone else who comments regarding getting these things or not, please also mentioned what type of hardware you are using)...

---

### Post by monkeybrain20122 on 2014-01-26
I have put Ubuntu on different hardware, this is a laptop with Pentium(R) dual core and Nvidia graphic (latest driver 331.38), but I have put Ubuntu on many different machines: a Dell desktop with Amd graphic, another samsung laptop with amd graphic card (core i3), a few old Intel machines.. I have never experienced the problem you described. In fact I have never experienced this with any Linux (have done Fedora, Debian and Manjaro)

---

### Post by tgalati4 on 2014-01-26
Could be a wireless problem under linux.  Try connecting an ethernet cable and see if the behavior is the same.

---

### Post by craig10x on 2014-01-26
@monkeybrain20122:  I was beginning to think maybe it was a problem more oriented toward sandybridge (icore) processors but you mentioned that you had one with that and did not have those problems...although the brand was different (you had a samsung andi have a toshiba)....

@tgalati4: i don't use the wireless, am connected to the ethernet cable (oh and i have a high speed cable connection by the way)...

---

### Post by d-cosner on 2014-01-26
For flash you need to turn off hardware acceleration in Firefox or you will have the problems you are describing. Even with Chrome you need to right click on a flash video and turn off hardware acceleration. Sound skipping in other applications could be pulse audio problems, for example try setting VLC to use alsa and see if the problem remains. 

I have had no problems with multimedia playback in 14.04.

---

### Post by craig10x on 2014-01-26
Interesting suggestions, Don :)  Well, for an experiment, i just right clicked on a video in you tube and clicked on settings where it let me shut off Hardware Acceleration....let's see if that will take care of that 
(streams radio and online videos)...i know it is on by default and i thought it was supposed to be desirable to keep it on?  (I wonder if windows has it turned off by default)...

When i get a chance i will try changing the setting in VLC to alsa instead of pulse audio...do you know if that can be done in Rhythmbox also?

---

### Post by d-cosner on 2014-01-26
Hardware acceleration works in Windows. Flash support for Linux has never been all that great, neither has graphics drivers. Times are changing though and graphics drivers for Linux are finally getting a lot of attention.

---

### Post by craig10x on 2014-01-26
Yeah, i bet it relates to the graphic drivers...which is probably why in windows, no problem on the SAME laptop!  If this works, i may just keep the acceleration off because those stream "doubles" drive me a bit batty :rolleyes: ;)

On the music and videos in the players, it doesn't do it too often so might just leave the pulse audio on... but the most annoying has been the stream radio and you tube videos...each time i get new intel drivers from ubuntu, i will put it back on temporarily to see if the problem has been eliminated...

Unlike AMD, there are no proprietary drivers for linux from intel... so i have no options....but intel is supposed to be improving the open source drivers for linux all the time...i guess i will have to wait for them to hit the "sweet spot"...LOL

I use Google Chrome, by the way...Don...so, i have the hardware acceleration turned off and will observe in the morning as i listen to my favorite talk stations...will note if it makes the difference...

---

### Post by sammiev on 2014-01-26
@craigx can you post a stream addie of one of the stations you listen to. I have a few of those laptops I can try it on.
Thanks.

---

### Post by craig10x on 2014-01-26
@sammiev: absolutely...let me grab one...be right back...
[http://www.wbap.com/](http://www.wbap.com/)

Just one of many...sometimes i bring them up from the radio station's web page...othertimes i type it in on the web interface of:
[www.iheart.com](www.iheart.com) and listening through that...same stream problem either way....you may have to listen rather carefully for a while, the "doubles" happen at the least expected moment ;)

---

### Post by sammiev on 2014-01-26
> **craig10x said:**
> @sammiev: absolutely...let me grab one...be right back...
[http://www.wbap.com/](http://www.wbap.com/)

Just one of many...sometimes i bring them up from the radio station's web page...othertimes i type it in on the web interface of:
[www.iheart.com](www.iheart.com) and listening through that...same stream problem either way....you may have to listen rather carefully for a while, the "doubles" happen at the least expected moment ;)

Only had a chance to listen to 3 songs but all worked. I will try in the AM for an hour before work.

---

### Post by craig10x on 2014-01-27
Very good...listen to one of the talk radio stations such as wbap, kabc, wmal, wabc, etc...it's the easiest way to tell....
Meanwhile, after having shut off hardware acceleration, i did not find any improvement on the "doubles" for me...so i turned it back on...

---

### Post by sammiev on 2014-01-27
> **craig10x said:**
> Very good...listen to one of the talk radio stations such as wbap, kabc, wmal, wabc, etc...it's the easiest way to tell....
Meanwhile, after having shut off hardware acceleration, i did not find any improvement on the "doubles" for me...so i turned it back on...

Tried it this morning right up to the time I had to work and all is well. Will try it on a few laptops and post tonight. :)

Edit: Really like your radio stations you listen to.

---

### Post by monkeybrain20122 on 2014-01-27
You may want to try soundcloud with flash turned on and turned off and see if it makes a difference (it supports html5 if flash is absent) I listened to your radio station link, no issue whatsoever (though I really hate the loud mouthed guy. :))

---

### Post by craig10x on 2014-01-27
@sammiev: yeah i am a real "talk radio junkie" :D  I have about 12 stations i listen to at various times to catch certain hosts that i like and at particular hours...
@monkeybrain20122:  LOL :D

Seems like i am one of the rare ones to get this problem...and i have only had this laptop (which is my desktop) for about 2 years and it runs like a top otherwise...
So, on this computer, seems like the only way to avoid the doubles is to go back to windows...may have to live with it if i want to stay on linux and Ubuntu (my favorite distro of course)...

I'll try your suggestion monkeybrain20122...I am also hoping perhaps when firefox gets that shumway flash plug in working well that maybe it will be less troublesome with it...if it is, even though i use chrome, i wouldn't mind also opening firefox and using that to get the streams...while still surfing with Chrome...

---

### Post by monkeybrain20122 on 2014-01-27
Oh if you are using intel graphic card and saucy (you seem to switch between saucy and trusty, I would just make a small test partition if I want to test  Trusty) you may want to upgrade your drivers [https://launchpad.net/~oibaf/+archive/graphics-drivers](https://launchpad.net/~oibaf/+archive/graphics-drivers)
I think their versions are actually newer than Trusty's.

Install ppa-purge, so if anything goes wrong just purge the ppa. Or, better still, make a clone with fsarchiver so that if ppa-purge doesn't work you can always restore the old system. I always do this when doing something risky.[http://www.fsarchiver.org/QuickStart](http://www.fsarchiver.org/QuickStart)

P.S. If you want to test soundcloud using Firefox with html5 player you need to enable gstreamer. I don't know if it is enabled by default now, I have enabled it manually back in FF24 or something (about:config -> media.gstreamer.enabled=true) Also I have no luck with shumway on FF26, others claim that it works in nightly build but has to have flash installed (I think, if it works, it just needs to have some kind of flash plugin installed for the websites to detect, the flash plugin doesn't have to actually work, so gnash, or totem-vegas,--a totem based flash plugin which almost never works,-- would work for this purpose)

---

### Post by sammiev on 2014-01-30
Must say after a few days no issues at all with the same equipment.

---

### Post by craig10x on 2014-01-30
Thanks for testing, sammiev
i guess i am one of the "rare birds" that have it...oh well...

I have only had this computer (a toshiba 17" laptop which i use as a desktop replacement) for about 1 1/2 years and otherwise it runs great, so i guess short of returning to windows 7 (which was what was originally installed on here) if i want to continue using Ubuntu as my OS i will likely have to just "live with it"....

My friend said...well if you go back to windows then you won't have that...and i said "true but then, being windows, there will probably be other things i will have that i wish i didn't have ;) :D

---

### Post by craig10x on 2014-02-08
Update:  I ran the software updater this evening, so i got a bunch of the updates i would have seen saturday morning, and they included a new version of the kernel as well as a bunch of other things...
And after the installation, noticed that it seemed to take care of my instability problems!

To test, i watched TEN you tube music videos...played TEN mp3s on VLC and listened to stream radio for 20 minutes straight and did not hear one double at all!
It was all as smooth and stable as it was on windows on this toshiba laptop with i3 and intel graphics....no glitches on the music on the videos or mp3s....

I was totally shocked...have no idea of what could have induced the change in those updates, but keeping fingers crossed and hope it's a permanent change! :D
I was getting so frustrated with this i almost re-installed windows 7 and was going to remove ubuntu...if it stays like this i will be tickled pink (lol) knowing i can stay on linux and my favorite distro,
UBUNTU ;)

I guess it will remain a mystery what triggered this off...i'd love to know but... :confused:

---

### Post by malspa on 2014-02-08
> **craig10x said:**
> 
I was getting so frustrated with this i almost re-installed windows 7 and was going to remove ubuntu...

:shock:

Glad you got it fixed. I don't recall ever seeing problems like that here with any distro I've ever run.

---

### Post by craig10x on 2014-02-08
Thanks malspa...i'm running 14.04 development and as you know development gets a LOT of updates every day...i was always hoping something would come along in the updates that would make a difference on this laptop and whatever it was seems to have done the trick...i will keep my fingers crossed of course that it's something permanent...

I've had that problem on this laptop and my toshiba laptop prior to it (which also had similar specs including the i3 core and intel graphics) and with all the ubuntus (ubuntu/kubuntu/xubuntu) and ubuntu based distros (like mint, zorin, etc) it was exactly the same thing...

---

### Post by d-cosner on 2014-02-08
Good deal! Glad things are working right for you!

---

### Post by rrnbtter on 2014-02-08
Greetings, 
I use 14.04 on a Toshiba single core and I have no problems with Radio  Tray or direct stream such as Nascar on Del Marva. I am betting that  your problem was related to a processor balancing act. If the stream was  switched from one core to another there could be a glitch in picking up  the stream from cache. I do believe that Linux dynamically allocates  programs on multicore systems whereas on Windows systems the programs  are statically assigned by the user. A kernel update addressing this  problem could go un-noticed. This is just a shot in the dark but very  possible. As you probably already know, we have been getting heavy  updates from Trusty including a new kernel everyday lately. It isn't  impossible that the problem could reappear.

---

### Post by craig10x on 2014-02-08
@rrnbtter:  You know, that sounds like a very logical possibility...glad you have the technical prowess to explain that to me in "layman's terms" ;)
Well, if it is kernel related, i sure hope a future kernel update on here won't undo it...and yes, i noticed there have been a  lot of kernel updates lately (3 in the last 3 days!)...

I never had the problem when i ran Toshibas with AMDs (though they did run a lot hotter) and also didn't have it when i ran an intel celeron as opposed to the sandy bridge 4 core (i3)....

So, I will be keeping my "fingers crossed" and hope for the best! :rolleyes:

---

### Post by rrnbtter on 2014-02-08
Greetings, 
@craig10x
Pleased to return the favor. Ubuntu problems do have a tendency to skip in and out of reality. Like an astroid bouncing across a time warp :)

---

### Post by craig10x on 2014-02-10
@rrnbtter: too funny :D

Well, so far so good...got lots of updates since but no change...just as good as it has been since i got those saturday updates...it could have been something in the kernel itself or one of the other many updates that was included...i guess i will never know what did it, but whatever it was, i hope it keeps doing it!  I've seen things get fixed that stayed that way permanently so i am really hoping that will be the case with this particular one ;)   I was "this close" to pulling out my windows 7 restore discs :shock:   Now i can stay a happy Ubuntu-ite :mrgreen:

---

### Post by malspa on 2014-02-10
craig10x, did try any other distros on this hardware? If so, were you seeing the same issues?

---

### Post by craig10x on 2014-02-10
Actually i did try others on this computer, malspa (the now defunct solus os which was debian based) and Linux Mint Debian Edition on my previous Toshiba (which was also i3 and intel graphics and had the same ubuntu problems)...and as i recall, they did not have it...On both laptops, ubuntu and it's variations (kubuntu/xubuntu) and Linux Mint and Zorin Os (ubuntu based) all had the instability problems...

I also had no problem with this on all my previous computers but they were mostly amds or intel cellerons or pentiums (which are not multi-core of course)...

---

### Post by malspa on 2014-02-10
Well, the important thing is that things look okay now.

I don't really care which OS anyone uses, but just because it's *you*, craig10x (as if I actually *know* you), I would have tried to convince you to go with a different distro rather than resort to Windows. :)

---

### Post by craig10x on 2014-02-10
I hear you, malspa...it probably would have been ok on the debian based distros, but i really REALLY prefer Ubuntu as i feel it has certain refinements and polish that the debian based ones just don't seem to have...an example is the patching that ubuntu uses that gives such outstanding web page rendering...i'd miss that...that's why i am so glad it got corrected on Ubuntu so that i can stay with it...
Also, these days (since the advent of unity) Ubuntu has become a darn good looking distro and i enjoy the "eye candy" :D

---

### Post by malspa on 2014-02-10
Yeah, I know what you mean. Even though I use other distros (Debian and Arch are my favorites these days), I really like Unity, and I have no intentions of getting rid of my Ubuntu installation. I'm looking forward to 14.04 (I haven't budged from 12.04 yet), and I was hoping that the issues you mentioned here wouldn't be something I'd have to deal with in the next LTS release.

---

### Post by craig10x on 2014-12-27
The problem seems to be unique to the 3.13 kernel on sandybridge hardware like i have...I run 14.10 now (which has the 3.16 kernel) and despite numerous updates, it has not lost one degree of media stability...
Where as once the 3.13 got messed up (in one of it's early updates on ubuntu) it has never improved on my hardware, no matter how many updates to it came in after that...
Best solution if one has this problem (as i did) is to move AWAY from the 3.13. kernel as fast as possible...i did and have not looked back :D

---

