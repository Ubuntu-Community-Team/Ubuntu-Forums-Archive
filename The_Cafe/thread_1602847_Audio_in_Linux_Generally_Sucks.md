---
title: "Audio in Linux Generally Sucks"
date: 2010-10-21
forum: The Cafe
---

### Post by zer010 on 2010-10-21
Is this the standard of what we as users should come to expect from a "Great" distro? Except for 9.04 everything after has since been horrid in it's implication. The one reason I use Windows is for it's superb playback of files, both native and foreign.  this is one area in which Ubuntu fails miserably. The constant stutter of audio files form mp3 to wav or even those streaming in flash. This is certainly why most Win-inites will NEVER completely switch over. Now, if you'll excuse me. I have to spend a couple hours installing WinXP just to enjoy some media files.....

Edit: Sorry for the attitude, but this is REALLY bothersome!  If it was one area I wish Linux could excel, it would be the multimedia arena.....

---

### Post by reyfer on 2010-10-21
Not sure what is wrong with your linux, but I have no problem playing mp3, ogg, wma, and the quality on my system is superb....

---

### Post by FuturePilot on 2010-10-22
Does the Linux audio stack have issues? Yes.
Does it suck for everyone because you had a bad experience? No.

---

### Post by earthpigg on 2010-10-22
I have also had stuttering issues with audio in all forms since my in-place upgrade to 10.10, and said multimedia taking up more CPU cycles than it ought to as reported by htop.

---

### Post by johntaylor1887 on 2010-10-22
> **reyfer said:**
> Not sure what is wrong with your linux, but I have no problem playing mp3, ogg, wma, and the quality on my system is superb....

Same here.

---

### Post by isaacj87 on 2010-10-22
> **zer010 said:**
> Is this the standard of what we as users should come to expect from a "Great" distro? Except for 9.04 everything after has since been horrid in it's implication. The one reason I use Windows is for it's superb playback of files, both native and foreign.  this is one area in which Ubuntu fails miserably. The constant stutter of audio files form mp3 to wav or even those streaming in flash. This is certainly why most Win-inites will NEVER completely switch over. Now, if you'll excuse me. I have to spend a couple hours installing WinXP just to enjoy some media files.....

Edit: Sorry for the attitude, but this is REALLY bothersome!  If it was one area I wish Linux could excel, it would be the multimedia arena.....

To a certain extent, I agree. However, On my netbook and system76, I've got openSUSE and Kubuntu running beautifully. I'm also a using studio distribution utilizing both Pulse and Jack and it's working out pretty well. Not sure what's up with your install, but I've seen others with this issue. You probably should remove pulseaudio or simply search for the answer on Google. It's probably easier to do that than to wait 2 hours for XP to reinstall.

When I first started using Linux, I would of agreed with you, but times have changed. Audio and Linux play pretty nicely with each other.

---

### Post by CraigPaleo on 2010-10-22
Huh? PCLOL is the only distro I've tried where the sound didn't work OOTB. The rest... fine. :confused:

---

### Post by sxmaxchine on 2010-10-22
works better for me and my laptop was made to use windows.

---

### Post by pwnst*r on 2010-10-22
> **sxmaxchine said:**
> works better for me and my laptop was made to use windows.

So, you're saying on your laptop, that the sound "works better" than in Windows?

---

### Post by oregonbob on 2010-10-22
I have great audio on Linux, in fact better than Windows 7 on some things. Such as try to use Windows Media Center, play something, mute it and then do another audio application. You can't but in Linux I do it all the time. Windows stupid Media Center controls every media/audio process.

You either have a configuration issue or an application that isn't the best. Or maybe you are running 10.10, which one can expect to have glitches for a couple of months. That's why there is no way I would upgrade now for a tiny, insignificant number of new features. It will be good in about 6 months.

---

### Post by Khakilang on 2010-10-22
So far my Lucid is flawless. Music and movies. What music player are you using? Maybe you can try other music player and see how it goes. I use RhythmBox for music. VLC and Totem movie player for movie and flash. The good thing about Linux is if something doesn't work you can try others.

---

### Post by NightwishFan on 2010-10-22
Pull your own weight a little or complain to the alsa people if your sound stack sucks. I am not doubting you, trust me. Mine does as well. My answer is, this is the Ubuntu forums. We help people with Ubuntu problems. I am sure there are other people that are better qualified to ignore your ranting.

I have nothing against you, I just am a very single minded person. If you want help I will help you. You want to constructively criticize, I will go to bat for you. You want to rant then prepare to be given a stern talking to.

If your only problem is sound skipping; then your alsa drivers are likely buggy and you need to disable timer based scheduling in pulseaudio.

Press alt+f2 and type:
```
gksudo gedit /etc/pulse/default.pa
```

Type your password, then when the file comes up find the line that looks like:
```
load-module module-udev-detect
```

Change that to:
```
load-module module-udev-detect tsched=0
```

Save, log out and log back in. Enjoy.

---

### Post by Strategist01 on 2010-10-22
I find that my audio plays fine in Linux (10.04.1) , better than in Windows(XP Pro). Mainly because XP put all the sound to the one speaker randomly, and it went back and so on...quite frustrating. I play my music on Ubuntu and it's pretty good! The only thing I find wrong is that the bass tends to be very soft/flat. I haven't found a mixer in banshee or anywhere else so I don't know how to enhance this :/

---

### Post by johntaylor1887 on 2010-10-22
> **Strategist01 said:**
> I haven't found a mixer in banshee or anywhere else so I don't know how to enhance this :/

VLC has an equalizer.

---

### Post by Oxwivi on 2010-10-22
I'm using the built-in audo support on my Intel D865PERL motherboard, and I found increasing the volume over two bars distorts the audio.

---

### Post by Sean Moran on 2010-10-22
> **johntaylor1887 said:**
> VLC has an equalizer.
Thank you for the suggestion Mr Taylor.  I've been wondering where I might find some sort of graphic equaliser to enhance or replace my otherwise happy little rhythmbox, and that's what got me curious about the contents of this thread.  It maybe true in the context of fairness that all MP3s might be more or less equal, but not all MP3s are equalised.

:guitar:

---

### Post by WalmartSniperLX on 2010-10-22
I can understand the frustration with Ubuntu. And, the problem isn't always the fact that something doesn't work, but that we must spend time on working with the OS to get it to work because defaults don't suffice. 

But, I use my linux box for audio production. I put out mixes and playback .mp3s and other formats much better than my friend's mac can at the actual studio. Either that, they're both equally good and I'm mentally bias :P

---

### Post by Spice Weasel on 2010-10-22
I used to have problems a few years back in that a horrible buzzing noise would constantly play through headphones and speakers, but it stopped with a pulseaudio upgrade.

---

### Post by koleoptero on 2010-10-22
Actually, good sound quality was one of the reasons I ditched windows altogether. My sound card seems to be working better here. In windows the sound would be too... well not good.

> **Strategist01 said:**
> I find that my audio plays fine in Linux (10.04.1) , better than in Windows(XP Pro). Mainly because XP put all the sound to the one speaker randomly, and it went back and so on...quite frustrating. I play my music on Ubuntu and it's pretty good! The only thing I find wrong is that the bass tends to be very soft/flat. I haven't found a mixer in banshee or anywhere else so I don't know how to enhance this :/

Banshee has an equaliser for some years now. Get the latest from the banshee website.

Rhythmbox has an equaliser too. Just open a terminal and do:

```
mkdir -p ~/.local/share/rhythmbox/plugins && wget http://www.lirmm.fr/~morandat/pub/upload/Main/rb-equalizer.tar.bz2 -O- | tar xvjf - -C ~/.local/share/rhythmbox/plugins
```

An even better working eq you'll find with deadbeef. You can get that by:

```
sudo add-apt-repository ppa:alexey-smirnov/deadbeef
sudo apt-get update
sudo apt-get install deadbeef
```

---

### Post by V for Vincent on 2010-10-22
Jack is kind of a bother for me, but pulse (or alsa before) has never given me any issues.

---

### Post by Swagman on 2010-10-22
[** Mines Awesome**](http://www.youtube.com/watch?v=thUmYa6yTFU) <--- little youtube of my desktop which was created to help someone on another forum

---

### Post by cascade9 on 2010-10-22
> **Swagman said:**
> [** Mines Awesome**]("http://www.youtube.com/watch?v=thUmYa6yTFU") <--- little youtube of my desktop which was created to help someone on another forum

OCAU? Geez, for a second there I thought that you were Oblong Cheese. :lolflag:

---

### Post by kaldor on 2010-10-22
9.10 was the biggest multimedia failure distro yet (imo). 

Even if it works for some, a large lot of people have sound issues on Linux and it isn't the fault of their hardware.

---

### Post by Swagman on 2010-10-22
> **cascade9 said:**
> OCAU? Geez, for a second there I thought that you were Oblong Cheese. :lolflag:

Hahaha.. That's who the vid was for !!

---

### Post by pwnst*r on 2010-10-22
> **Strategist01 said:**
> I find that my audio plays fine in Linux (10.04.1) , better than in Windows(XP Pro). Mainly because XP put all the sound to the one speaker randomly, and it went back and so on...quite frustrating. 

I can assure you that it was not an OS issue.

---

### Post by JIGNESH RAVAL on 2010-10-22
Sometimes I have no problem playing mp3, wma, and also play well and superb....

---

### Post by pwnst*r on 2010-10-22
> **JIGNESH RAVAL said:**
> Sometimes I have no problem playing mp3, wma, and also play well and superb....

But sometimes you do...?

---

### Post by renkinjutsu on 2010-10-22
hmm..
Intel(R) Core(TM)2 Duo CPU E7200 @ 2.53GHz

I'm playing a 2048x872 h264 video at 24 fps
with 48000Hz 2 channel AAC audio

Everything's working fine for me =\
Sorry.

---

### Post by as2000 on 2010-10-22
Only issue I had was front panel jack. solved it though. as far as audio is concerned, it has always been crystal clear. it must be your hardware...

---

### Post by Grenage on 2010-10-22
I get the distinct impression that understanding the sound stack in Linux would require an A2 map, and a year of study.  It's one of the weaker points, yes.

Thankfully, it works for *most* people, *most* of the time.

---

### Post by zer010 on 2010-10-22
> **NightwishFan said:**
> Pull your own weight a little or complain  to the alsa people if your sound stack sucks. I am not doubting you,  trust me. Mine does as well. My answer is, this is the Ubuntu forums. We  help people with Ubuntu problems. I am sure there are other people that  are better qualified to ignore your ranting.

I have nothing against you, I just am a very single minded person. If  you want help I will help you. You want to constructively criticize, I  will go to bat for you. You want to rant then prepare to be given a  stern talking to.

If your only problem is sound skipping; then your alsa drivers are  likely buggy and you need to disable timer based scheduling in  pulseaudio.

Press alt+f2 and type:
```
gksudo gedit /etc/pulse/default.pa
```Type your password, then when the file comes up find the line that looks like:
```
load-module module-udev-detect
```Change that to:
```
load-module module-udev-detect tsched=0
```Save, log out and log back in. Enjoy.


Thanks! I will definitely give that a try. 
Again, I apologize for the tone of my post.

---

### Post by zer010 on 2010-10-22
That seems to have fixed my problem!  What a difference! Can't thank ya enough! Music is sanity and I am now sane!...kinda... ;)

---

### Post by idefix_7 on 2010-10-22
Hi I try to follow this ... but as a rookie I am with linux I guess I have screwed my audio.
The story is that I had audio working until I installed a mediaplayer.
I tried to fix this, looking into forums... sudo this sudo that but no sound. At last I may have done to much damage.
So my question is...how do I recover / re-install audio on my system.
[using 10.04LTS]

---

### Post by NightwishFan on 2010-10-22
> **zer010 said:**
> That seems to have fixed my problem!  What a difference! Can't thank ya enough! Music is sanity and I am now sane!...kinda... ;)

Glad to help. Since this fix works it probably means your alsa drivers are buggy and if you want you can file a bug using this. Press alt+f2 and type:
```
ubuntu-bug alsa-base
```

> **idefix_7 said:**
> Hi I try to follow this ... but as a rookie I am with linux I guess I have screwed my audio.
The story is that I had audio working until I installed a mediaplayer.
I tried to fix this, looking into forums... sudo this sudo that but no sound. At last I may have done to much damage.
So my question is...how do I recover / re-install audio on my system.
[using 10.04LTS]

You should probably start your own thread.

---

### Post by Darth Penguin on 2010-10-22
Eh? One of the improvements I noticed when I installed Ubuntu is the improvement in sound quality and a better volume control.

---

### Post by Old *ix Geek on 2010-10-23
> **zer010 said:**
> Is this the standard of what we as users should come to expect from a "Great" distro? Except for 9.04 everything after has since been horrid in its implication. The one reason I use Windows is for its superb playback of files, both native and foreign.  this is one area in which Ubuntu fails miserably. The constant stutter of audio files form mp3 to wav or even those streaming in flash.I have NO IDEA what you're talking about, as I have no problems like those you're describing. And you'd think with five computers, at least ONE of them would have audio that sucks as badly as you're saying yours does.
> This is certainly why most Win-inites will NEVER completely switch over.Strange, every FORMER windoze user I've converted to Linux is thrilled. They're not having any audio problems like you're describing either.
> Now, if you'll excuse me. I have to spend a couple hours installing WinXP just to enjoy some media files....Whatever floats your boat. But you'd be better off installing KDE. Problem solved. :)

---

### Post by MisterGaribaldi on 2010-10-23
M-my m-my m-my m-my audio w-works w-works w-works j-just j-just j-just fiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiine in t-ten t-ten t-ten point t-ten.

N-now n-now n-now n-now n-now if I-I I-I I-I could jussssssssssssssssst g-g-g-g-get rid oooooof t-the t-the t-the st-st-st-st-st-stutt-tt-tt-tt-ering with posts h-here h-here h-here on U-bun U-bun U-buntu F-f-f-f-f-forums.... :P

Seriously, I have had absolutely no media issues in Ubuntu (any version). 10.10 has been rock-solid for me in that regard (audio, video, DVD). Of course, I also did a wipe-and-setup clean install of Ubuntu 10.10, and that likely made things less problematic.

---

### Post by matthewbpt on 2010-10-23
I've been enjoying flawless media playback since about 8.10 (8.04 had some issues as pulseaudio hadn't reached the stability is now has), the sound playback is great I even have surround sound speakers working correctly, which is more than I can say about Win7, which still gives problems with surround sound playback for me.

---

### Post by weasel fierce on 2010-10-23
A few years back, I had a fair share of trouble, but nothing recently. 10.10 is smooth for sound on my end.

---

### Post by NightwishFan on 2010-10-23
> **weasel fierce said:**
> A few years back, I had a fair share of trouble, but nothing recently. 10.10 is smooth for sound on my end.

This issue is a problem for a few cards in maverick (including mine). I learned this fix using Fedora 10 a long time ago I think.

---

### Post by Lightstar on 2010-10-23
I agree, it's bad.

I have no problems with audio for music and movies.
streaming audio, microphone (in more than one program) are my two main problems.
webcam doesn't work either.  It's not audio but It's close to it!  especially since I could use the webcam's mic if it worked, or my headset.

---

### Post by Shakz on 2010-10-23
Weird. Sorry to hear your having issues. I have ubuntu running on my Asus netbook, Dell XPS Lappy, HP Lappy and Gateway Desktop. Never had any issues at all like what your describing. I did have an issue with my netbook where headphone jack didnt work so i switched to arch on it. I have returned it to ubuntu though for meerkat and all is golden

---

### Post by cariboo on 2010-10-23
It's all well and good to complain about something in the forums, but if you really want something fixed, create a bug and provide as much information as you possibly can. A problem can't be solved if the devs don't know about it.

---

### Post by Arthur_D on 2010-10-23
In Ubuntu 10.04 sound would crash rather often, with nasty side-effects on apps (Rhythmbox skipping to next track, games would get really bad FPS, Flash would crash); Ubuntu 10.10 had that part fixed, but introduced bad graphics performance for me. So I just gave in and installed Fediora 13. Once set up with bad proprietary things, it's been the smoothest Linux experience for me since Ubuntu 9.04.

My Asus Eee netbook running UNE 10.04 doesn't have separate plugin slots for audio out and line in - it's the same port and is probably software regulated in Windows. In UNE I don't get audio out from the port, and it bothers me a bit, but not enough yet to make me search for a solution.

My point is, I think audio is one of the more troublesome areas in Linux. But this is mostly based on my experience, and your mileage may vary. I'm just sayin' my opinion. ;)

---

### Post by Sean Moran on 2010-10-24
Thanks again to the wise man who I can't find again on this thread for telling me how to mkdir -p ~/.local/share/rhythmbox/plugins && wget [http://www.lirmm.fr/~morandat/pub/upload/Main/rb-equalizer.tar.bz2]("http://www.lirmm.fr/%7Emorandat/pub/upload/Main/rb-equalizer.tar.bz2") -O- | tar xvjf - -C ~/.local/share/rhythmbox/plugin


Now I have Van Morrison blastinfg out so good on rhythmbox that I must hurry before the neighbours start knocking on my door!


They have guns so good tonot be home when they knock on my door about the good music.

"And it stoned me to my soul..."
:guitar:


Learned stickball as a formal education,
Lost a lot of fights but it taught me how to lose okay,
Thought I was the duke of Earl,
When I made it with a red-haired girl in a Chevrolet,

I'd rather laugh with the sinners than cry with the saints,
The sinners are much more fun ...
Only the good die young.

---

### Post by zer010 on 2010-10-24
> **NightwishFan said:**
> Glad to help. Since this fix works it probably means your alsa drivers are buggy and if you want you can file a bug using this. Press alt+f2 and type:
```
ubuntu-bug alsa-base
```

I wish I could say all is right in the world, but now VLC is totally garbled. Totem and Rythmbox work great, however.  Fix one thing and screw another.....ah well, such is the way things go sometimes....

---

### Post by NightwishFan on 2010-10-24
Try setting vlc to another driver like alsa or sdl.

---

### Post by zer010 on 2010-10-24
> **NightwishFan said:**
> Try setting vlc to another driver like alsa or sdl.
Changed the output module to "UNIX OSS audio output" and it's all good now. Thanks again!  :guitar:

---

### Post by sandyd on 2010-10-24
I actually have an issue with sound too, which is one of the reasons I don't use ubuntu.
Its not a ubuntu specific issue, its that when my system has a high load from compiling and stuff, any audio playback, just any sound (even a system beep) will cause a kernel panic...

---

### Post by NightwishFan on 2010-10-24
> **sandyd said:**
> I actually have an issue with sound too, which is one of the reasons I don't use ubuntu.
Its not a ubuntu specific issue, its that when my system has a high load from compiling and stuff, any audio playback, just any sound (even a system beep) will cause a kernel panic...

You have me interested. ;)

---

### Post by mrkrupp0 on 2010-10-24
Ubuntu does not have "bad" audio, it's audio playback is simply more taxing on your computer.  I have absolutely no problems with any form of media.

---

### Post by NightwishFan on 2010-10-24
> **mrkrupp0 said:**
> Ubuntu does not have "bad" audio, it's audio playback is simply more taxing on your computer.  I have absolutely no problems with any form of media.

No, audio in Linux is not the best. Optimally it more or less works though. For average users they probably will not notice, though for developers and professionals it might be lacking.

---

### Post by beew on 2010-10-24
I have a problem with VLC in 10.04. It makes a hiccup sound or other crackling noise in the beginning of some MP3 files, it just happens in the beginning and then it is fine for the rest of the track (not all  MP3s but enough to be annoying), it is not the MP3 files because playing them with other music players like Banshee or Amarok there is no noise.

I read in the forum that many people have choppy sound with VLC solved the problem by changing the output option. Tried that but it didn't work. At first the hiccups and crackling sound in the beginning of the tracks was eliminated, but then after about 10 -15 minutes there was no sound at all, even though the progress bar in VLC is moving.

This problem is solved mysteriously in 10.10. VLC sounds smooth and beautiful in Maverick. but since I don't upgrade my work machine I would still like to find a solution, otherwise I would just get rid of VLC (posted a thread in the absolute beginner section long time ago, bumped several times and the only advice I got was from some guy who posted a link to a huge document, well I am not trying to be a Linux sound engineer for crying out loud)

---

### Post by handy on 2010-10-25
I agree that Linux sound quality was really very poor for years.

These days I have NO problems with it at all.

I haven't really used Ubuntu for over 2 years though; I use Arch. So I don't know if the problem is distro specific or not?

---

### Post by NightwishFan on 2010-10-25
> **handy said:**
> I agree that Linux sound quality was really very poor for years.

These days I have NO problems with it at all.

I haven't really used Ubuntu for over 2 years though; I use Arch. So I don't know if the problem is distro specific or not?

Very few problems are distro specific.

---

### Post by handy on 2010-10-25
> **NightwishFan said:**
> Very few problems are distro specific.

I've heard that Ubuntu has one audio problem in particular.

---

### Post by NightwishFan on 2010-10-25
Seeing you around a lot in the last few minutes. :)

I know that Lennart seems to think the ubuntu 100hz 64-bit kernel is a bit insane for audio. I know that some major distributions use 250hz and no preemption.

---

### Post by Snowline on 2010-10-25
> **handy said:**
> I agree that Linux sound quality was really very poor for years.

These days I have NO problems with it at all.

I haven't really used Ubuntu for over 2 years though; I use Arch. So I don't know if the problem is distro specific or not?

Did you install pulseaudio or alsa on arch?

---

