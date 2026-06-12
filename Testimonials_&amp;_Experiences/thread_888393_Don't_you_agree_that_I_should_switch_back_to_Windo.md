---
title: "Don't you agree that I should switch back to Windows?"
date: 2008-08-13
forum: Testimonials &amp; Experiences
---

### Post by Diya on 2008-08-13
First of all, sorry about the long thread. I just need to get this off my chest.

The most important thing to me is music. I like composing/editing MIDI files, then adding a nice reverb to them, etc.

My soundcard, which is built into the motherboard, has a Sound Manager. That sound manager can edit the sound parameters, add a variety of reverbs, transpose (-4 ~ +4) system-wide. With just simple clicks, I can have those system-wide effects _instantly_.

The issue(s):
1) The Sound Manager is not compatible with Linux OS.

2) My soundcard doesn't support hardware MIDI playback, so I have to use Audacious (AMIDI plugin, FluidSynth Backend) to play MIDI files. However, it doesn't work with large SoundFont files. I tried 70 MB, 68 MB, and 3 MB, **none** works. The only one that works is a 76.4 **K**B which is really crappy.

3) I can't edit MIDI files unless I have a sound card that supports MIDI hardware playback. On Windows OS, this wasn't required due to driver software program.

4) Some of you may suggest using PulseAudio to add system-wide effects. I tried it, but it's so hard to add/remove effects on-the-fly. I have to enter loads of commands in terminal, and edit files. It's frustrating.

---

### Post by Vishal Agarwal on 2008-08-13
What is your motherboard Chipset no. ?

---

### Post by kaboodle_fish on 2008-08-13
I agree that if Windows suits your needs better then you should use Windows.
 
But why not consider a dual boot? Then you can have the best of both worlds.

---

### Post by werries on 2008-08-13
Have you tried Ubuntu Studio type stuff?
That or just dual boot if you want to keep ubuntu at all.

---

### Post by Crafty Kisses on 2008-08-13
You could always dual boot Linux and Windows, but as stated above you might want to look into "Ubuntu Studio", you may find this link interesting > [http://ubuntustudio.org/](http://ubuntustudio.org/)

---

### Post by zxscooby on 2008-08-13
You cant hammer nails with a screw driver.
If windows suits your needs better then use it.
Both windows and Linux are usefull tools.

---

### Post by lisati on 2008-08-13
I have dual boot on both my current machines: I use mostly Ubuntu on my laptop, because it suits what I do with it, and I use mostly XP on my desktop, because it suits what I use it for. It's up to you......

---

### Post by Methuselah on 2008-08-13
I use timidity and have been able to use large (several megabyte) soundfont files.

Anyway, if the windows setup is perfect for you stick with it or dual boot so you can continue to check on Ubuntu.

---

### Post by Diya on 2008-08-13
Okay, I'll give Ubuntu-Studio a go.

---

### Post by Crafty Kisses on 2008-08-13
> **Diya said:**
> Okay, I'll give Ubuntu-Studio a go.

Yeah, that would probably be your best bet.

---

### Post by stalkingwolf on 2008-08-13
you might also want to give EarOS a look.  Audio is its speciality.

---

### Post by ukripper on 2008-08-13
> **Diya said:**
> First of all, sorry about the long thread. I just need to get this off my chest.

The most important thing to me is music. I like composing/editing MIDI files, then adding a nice reverb to them, etc.

My soundcard, which is built into the motherboard, has a Sound Manager. That sound manager can edit the sound parameters, add a variety of reverbs, transpose (-4 ~ +4) system-wide. With just simple clicks, I can have those system-wide effects _instantly_.

The issue(s):
1) The Sound Manager is not compatible with Linux OS.

2) My soundcard doesn't support hardware MIDI playback, so I have to use Audacious (AMIDI plugin, FluidSynth Backend) to play MIDI files. However, it doesn't work with large SoundFont files. I tried 70 MB, 68 MB, and 3 MB, **none** works. The only one that works is a 76.4 **K**B which is really crappy.

3) I can't edit MIDI files unless I have a sound card that supports MIDI hardware playback. On Windows OS, this wasn't required due to driver software program.

4) Some of you may suggest using PulseAudio to add system-wide effects. I tried it, but it's so hard to add/remove effects on-the-fly. I have to enter loads of commands in terminal, and edit files. It's frustrating.

Dual boot Ubuntu/windows and do your editing stuff in windows and rest in ubuntu. Problem solved!

---

### Post by Comhra on 2008-08-13
Let us know how get on with Ubuntu Studio; I've never tried it.

---

### Post by stchman on 2008-08-13
The other forums members can correct me if I am wrong, but I believe Ubuntu Studio is just Ubuntu with the following:

- Low latency kernel
- A cool theme
- All the music, video, and image editing apps installed.

All these are available in the repos so a complete reinstall is not necessary.

[https://wiki.ubuntu.com/UbuntuStudio](https://wiki.ubuntu.com/UbuntuStudio)

---

### Post by cb951303 on 2008-08-13
try timidity to play midi files.

---

### Post by werries on 2008-08-13
> **stchman said:**
> The other forums members can correct me if I am wrong, but I believe Ubuntu Studio is just Ubuntu with the following:

- Low latency kernel
- A cool theme
- All the music, video, and image editing apps installed.

All these are available in the repos so a complete reinstall is not necessary.

[https://wiki.ubuntu.com/UbuntuStudio](https://wiki.ubuntu.com/UbuntuStudio)

Not necessarily, the JACK Audio is already set up, plugins configured nicely. Its useful for a clean install as it helps new users not have to set up the complicated issue that exists in Linux audio.

---

### Post by Antman on 2008-08-13
> **zxscooby said:**
> You cant hammer nails with a screw driver.
If windows suits your needs better then use it.
Both windows and Linux are usefull tools.
+1
I dual boot Vista and Ubuntu on my desktop. I use Vista only for Video editing with Adobe Premier and Games. I use Ubuntu for everything else.

---

### Post by cardinals_fan on 2008-08-13
> **zxscooby said:**
> You cant hammer nails with a screw driver.
If windows suits your needs better then use it.
Both windows and Linux are usefull tools.
+1

I dual-boot SliTaz and Ubuntu.  I use SliTaz for almost everything, and then boot into Ubuntu to print (I haven't got my printer drivers set up in SliTaz).

---

### Post by Diya on 2008-08-17
Hello again,

I've finally fixed the MIDI problem. I can play MIDI now via Audacious, and load SoundFont files no matter how big they are (As long as they are GM). The problem happens to be the way Audacious loads the soundfont file. I solved the problem by clicking the ">>|" (Next Song) button.

I still can't play MIDI files via Rosegarden, but I'll try to figure it out when I have the time.

---

### Post by yragrelluf on 2008-09-26
> **stalkingwolf said:**
> you might also want to give EarOS a look.  Audio is its speciality.

earos is a controversial distro, based on hardy, that violates the whole open source thing. it is just a remastered hardy with the default applications changed around, and it has the earos media center, which doesnt work very good, and the creator refuses to make a deb package to install just the media center. im using it right now as an experiment to test the different media centers right now, just until ibex is released, then i will get rid of it. I have found that XBMC is the best media center for me.

---

### Post by oldsoundguy on 2008-09-26
keep at it, and when you succeed, be sure to hang around to offer a helping hand to others with similar issues.

But "going back to Windows" for what you want to do is really not getting it done right .. Much better to go Mac if your efforts are unsatisfactory with Linux.  I know of very few professional musicians/composers that rely on Windows machines for such work.  Mac does it better and won't crash and lose a couple of days of intensive work.

---

### Post by perlluver on 2008-09-26
If you feel discouraged, take a look at this: [http://www.linuxmovies.org/software.html](http://www.linuxmovies.org/software.html), it shows all of the video and audio programs for Linux.  There have been some really great movies produced on Linux.  I would Imagine that you could produce some really sweet music.

---

### Post by steveneddy on 2008-09-26
> **kaboodle_fish said:**
> I agree that if Windows suits your needs better then you should use Windows.
 
But why not consider a dual boot? Then you can have the best of both worlds.

My thoughts exactly.

---

### Post by hyper_ch on 2008-09-27
I agree that you should go back to windows.

---

### Post by Hyside on 2008-09-27
Like previously said, try UbuntuStudio, if that doesn't cut it out for you, then migrate back to Windows. If you can afford it, switch to a Mac for your music making. 

It isn't about "OS loyalty" as much as it is having the capabilities to do what you want to do.

---

### Post by oldsoundguy on 2008-09-27
> **Hyside said:**
> Like previously said, try UbuntuStudio, if that doesn't cut it out for you, then migrate back to Windows. If you can afford it, switch to a Mac for your music making. 

It isn't about "OS loyalty" as much as it is having the capabilities to do what you want to do.

+1

That IS what it is all about.  Been pointed out here several times,  A computer is a tool (for most), not a way of life.  The reason that there are even multiple builds of programs (even Windows) is that people use them for different purposes. One size does NOT fit all!
As far as COMPUTERS go. if you want melt your eyes gaming or a complete home entertainment center, then Windows is the unit for you at present.  If you want the Hummer of programing and reliability for your home or office, then it is Linux of almost any iteration.  If you want arts and crafts and music, engineering (Autocad) or a great desktop publishing unit, Mac.  If you want video, many production companies use special built Atari computers (built along with Video Toaster) (along with Mac). 
George Lucas has banks of Sun workstations at both ILM and at Skywalker to do both film and soundtracks.
This is constantly shifting and changing and there is a definite blurring of distinctions but, whatever floats your boat. It is NOT a lifetime commitment to ONE OS or ONE thing.

---

### Post by wolfen69 on 2008-09-27
> **oldsoundguy said:**
> It is NOT a lifetime commitment to ONE OS or ONE thing.

speak for yourself and not everyone else.

---

### Post by caravel on 2008-09-27
Or you could move to Debian like I did.  Believe me it works, is stable and has signinificantly less bloat.

---

