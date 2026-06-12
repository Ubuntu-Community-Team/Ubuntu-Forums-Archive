---
title: "What you would like to see in Ubuntu Studio 10.04"
date: 2009-11-25
forum: Ubuntu Studio
---

### Post by MiCK.ca on 2009-11-25
The release of Ubuntu Studio 10 is right around the corner. As a community (whether you are a developer or just a user), We need to know what your views on the direction and the overall feel of the branch is. So let's start this:

**Tell us:**

What are you annoyances?
What programs do you want to see?
Do you want a personal say in the programs that are loaded at install time?
What good things should be expanded upon?
What do you record? (i.e. live, electronic, mix of both)


**ALSO**
Recently I Gimped up a mock of what a possible addon I'd like to see for Ubuntu Studio. It's alng the exact same idea as Ubuntu software center. 
The install could load the base system (smaller disc, even a CDRom) Then you would fire up this preinstalled GUI to handpick and setup YOUR personal Ubuntu Studio Desktop. (again this is just a mock-up and perhaps could start to be developed)
You'd have your realtime kernel already in place. Your basic apps like Synaptics and accessories would be there. 
As you can see from the screenshots that you can pick your audio/video apps much like the Ubuntu software center. but this would be for Studio apps only. Not for office or games. audio/video/graphics and restricted stuff would be here. (Ubuntu Studio Stuff)

With this addition, i feel that the developers could focus more time on stabilty and RT-Kernel work. The feel of the desktop (i.e. appearance icons etc) could be another focus. Plugging apps into this Software install GUI would be making available all that is available and the user selects what they use.


**personal note**
I typically don't use a lot of what music distros supply. (64 Studio, Musix) i load only the apps i use for my type of production. Some users are electronic based where some are acoustic, live mic types. i typically only use Ardour/Jack and the LADSPA/CMT types filters as I tend to record live drums, guitars etc.

---

### Post by dawiba on 2009-11-25
**Annoyances:**

Midi isn't all it could be. Some of the midi programs don't work (at least not as advertised :roll:).

Programs which don't fulfil their remit or are out of date (no longer developed) should be removed from the repos.

Duplication. Give people a program and advise that others are available.

The ability to uninstall individual programs that are installed by default without having to remove the whole metapackage
[B]
Programs I want to see in the install:[/B]

QTractor.
Ardour with LV2 support and midi when it's ready.
Rakarrack

**Installed Programs:**

I'd be happy to choose my programs at the install. Choosing between them at installation would be a nightmare for someone who isn't familiar with Linux equivalents of Windows/Mac programs.
[B]
Good Things:[/B]

Studio Controls works well and is a good idea, but could be more comprehensive to allow all the options to be chosen when setting up your system. It would help newcomers and those who don't like to use the terminal (that's me ;)) to get up and running with minimal fuss. This would allow quick setting up for things like audio and video groups and firewire. It could also have some means of allowing users to choose between Pulse Audio and Jack. In other words a button you would click that would choose one and force the other to give way. I'm sure many newcomers would appreciate something like this.

I don't write code, so this is all really easy for me :)

**What do I record?**

I use a firewire interface. I record audio using Ardour. I record midi using Qtractor and use this to trigger external sounds. I then record those sounds into Ardour.

---

### Post by MiCK.ca on 2009-11-25
excellent. Perhaps a set of default programs? 

this gives me another idea...i check into it and get back.

---

### Post by Sin@Sin-Sacrifice on 2009-11-25
Lmms!!

---

### Post by trulan on 2009-11-25
A new version of Studio Controls!!

With three tabs:
 - Real Time Scheduling
 - Permissions
 - 1394 FireWire Audio

1. Under the Real Time Scheduling tab:
 - A way to manually set audio-rtprio 99, instead of just writing that line on install.
 - Memlock setting.
 - A way to set nice (or whatever the new kernels use) that actually works.
 - A button to run a 'startstudio' and 'stopstudio' script, ramping up CPU, modifying irq priorities, etc., like we are doing here:  [http://ubuntuforums.org/showthread.php?p=8377299#post8377299](http://ubuntuforums.org/showthread.php?p=8377299#post8377299)  Or maybe just a simple way to add it to qjackctl for the average user.

2. Under the Permissions tab:
 - A way to set Audio and Video Groups permissions, maybe a link to the User Properties tab in the Users and Groups gui.

3. Under the 1394 FireWire Audio tab:
 - A way of setting raw1394 permissions that does not get overwritten!
 - A checkbox to add ohci1394 to the rtprio script (in the priorities list and the non-threaded list).

4. Anything else I may have missed that gets asked about here every other day!!

---

### Post by MiCK.ca on 2009-11-25
i also have something else in the works and when i hear back from certain team members i'll run it past the community for Ubuntu Studio users. I think i could solve a lot of problem here. just keep giving us input.   thanks you guys are doing great!!

---

### Post by sgx on 2009-11-26
nvidia 6100 graphics chip always gets an incorrect resolution
maximim of 800x600. Then in xorg.conf, there are no details to adjust, just useless repetitions of detected monitor, detected mouse etc.

Even worse in 64Studio, 640x480 !

---

### Post by luctor on 2009-11-26
Sonic Visualiser should be in the repos, along with several vamp plugins.
> Sonic Visualiser is an application for viewing and analysing the contents of music audio files.

[http://www.sonicvisualiser.org/](http://www.sonicvisualiser.org/)
[http://www.vamp-plugins.org/](http://www.vamp-plugins.org/)

---

### Post by AutoStatic on 2009-11-26
> **sgx said:**
> nvidia 6100 graphics chip always gets an incorrect resolution
maximim of 800x600. Then in xorg.conf, there are no details to adjust, just useless repetitions of detected monitor, detected mouse etc.

Even worse in 64Studio, 640x480 !It's not up to the UbuntuStudio devs to fix this I reckon.

---

### Post by rylleman on 2009-11-26
I would like Ubuntu Studio to become a distro targeting audio works only, which it in effect already is.
I feel the video and graphics branches are just slapped on there and I really gain nothing from using Ubuntu Studio instead of using standard Ubuntu and adding the appropriate applications myself.
For audio you got real-time kernel etc. but for graphics/video there's nothing special really.

(Have been using Ubuntu Studio since 7.10 and records nothing except some sketch-sound for my movies.)

---

### Post by mango42 on 2009-11-26
> What are your annoyances?

Not being able to grapple with the wonderful volume of sheer creative anarchy!;)

Perhaps a panel for complete beginners showing them the options, with a note about compatibilities (eg: LMMS, no JACK; JACK + Ardour + qTractor + Audacity; explanation in non-programmer terms about PulseAudio v ALSA v etc, etc)

> What programs do you want to see?

QTractor

Far more commandline stuff GUI encapsulated (on the principle that most musos ain't programmers - but yes, I do understand that gui's take about the same time to program as all the nitty-gritty they are exposing!)

> Do you want a personal say in the programs that are loaded at install time?

Yes please - but with the caveat above - ie. explaining the pros and cons of each program in relation to the underlying core.

> What good things should be expanded upon?

I have insufficient knowledge to answer that fairly as yet but broadly "Ease of use" - reduction of the technical barriers to creativity (do you offer immortality, too? ;-)

'Fidelity of Sound' - the key to it all. Why is it that some software 'sounds' better than others? So many people used to say of early VST versions - this sounds very thin compared to <insertnamehere>. Why should this be? Surely the only place sound can get munged is at the A/D interface, after that it's just numbers, right? Hmm.

> What do you record? (i.e. live, electronic, mix of both)

A mix - eclectic flexibility is our theme (but gimme fluffy Trance any day - a soothing cushion in a world gonne madde ;-)

Thank you so much for giving users of all this incredible free software a feedback platform. The sense of co-operative community here leaves me entirely humbled. I can still remember how much energy goes into software creation. We used to say 'coding's great fun but debugging can quickly descend into nightmare...'

---

### Post by markbuntu on 2009-11-26
jack back in main so pulse-jack integration can be implemented.

---

### Post by Drunky on 2009-11-26
> **markbuntu said:**
> jack back in main so pulse-jack integration can be implemented.

This is currently in development for Lucid.

---

### Post by Drunky on 2009-11-26
> **dawiba said:**
> **Annoyances:**
[B]
Programs I want to see in the install:[/B]

Ardour with LV2 support and midi when it's ready.
Rakarrack


The latest lv2core has already been synced with Ubuntu.

Ardour with lv2 support is currently being merged with Ubuntu.  I imagine this should happen for Lucid.

Rakarrack will by synced by Lucid and is being considered for inclusion by default into Ubuntu Studio.

---

### Post by Drunky on 2009-11-26
> **MiCK.ca said:**
> excellent. Perhaps a set of default programs? 

this gives me another idea...i check into it and get back.

I'm not sure what you mean by "default programs" but here is the current audio/graphic/video programs in Ubuntu Studio Karmic...

[https://help.ubuntu.com/community/UbuntuStudio/Applications](https://help.ubuntu.com/community/UbuntuStudio/Applications)

---

### Post by Drunky on 2009-11-26
> **Sin@Sin-Sacrifice said:**
> Lmms!!

It's already in Ubuntu Studio 9.10 and I don't think there are any plans to remove it for 10.04.

See the current list of audio/graphic/video applications in Ubuntu Studio 9.10...

[https://help.ubuntu.com/community/UbuntuStudio/Applications](https://help.ubuntu.com/community/UbuntuStudio/Applications)

---

### Post by Scott L on 2009-11-27
> **luctor said:**
> Sonic Visualiser should be in the repos, along with several vamp plugins.


[http://www.sonicvisualiser.org/](http://www.sonicvisualiser.org/)
[http://www.vamp-plugins.org/](http://www.vamp-plugins.org/)

VAMP is already in the repos, just in the multiverse.  See the following:
[VAMP in the repos]("http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=vamp")
[Add multiverse repository]("https://help.ubuntu.com/community/Repositories/Ubuntu")

But if you want VAMP included in Ubuntu Studio by default either [file a bug]("https://launchpad.net/ubuntustudio") in Launchpad with the Ubuntu Studio group or send an email to the [Ubuntu Studio Developer mailing list]("https://lists.ubuntu.com/mailman/listinfo/ubuntu-studio-devel").

As far as Sonic Visualiser, you should probably follow the same suggestion above for filing a bug or emailing the list.

Regards.

---

### Post by claudio fontanelli on 2009-11-27
hello first of all a system more stable.

Dawiba ... You can provide a good setting for the music, one for video and one for web

thanks

UbuntuStudio is a wonderful idea

---

### Post by Stochastic on 2009-11-28
I'd like to see a couple of improvements:
1) More sound libraries pre-loaded on the system.  This requires open-source sound libraries (such as hydrogen drumkits or soundfonts) to be packaged for Ubuntu, then included in Ubuntu Studio.
2) More graphics formats thumbnailed by default (such as photoshop psd files).
3) A stronger colour mapping/calibration capability that's easy to use and install.

---

### Post by jitup on 2009-12-04
I think the latest version of cinelerra should be included and also tomboy or some text editing software, beside scribus.

---

### Post by babarosa on 2009-12-04
Hi,

as far as I know, the soundfont editor "swami" was removed from karmic's repos because of GTK+ issues.

I compiled Josh Green's latest CVS version which looks very fine. But Josh told me, it is still under development and he recommends using the 0.9. version.

To my mind, a sf2 editor is very important and should be added to v10.10 LTS.

Regards, Michael

---

### Post by fedexnman on 2009-12-04
1.  get  better a acoustic drum kit for hydrogen (like up to par with ezdrummer or addictive drums for windoze )
2. keep the rt kernel from 9.10 its great !!
3. keep up the great work !

---

### Post by GraysonPeddie on 2009-12-04
Anyone for The Open Octave Project?
[http://www.openoctave.org/](http://www.openoctave.org/)

It's Rosegarden but with audio and music notation features removed, but with Open Octave MIDI focused entirely on MIDI.

As for Ubuntu Studio, would it be possible to organize the audio applications and tools into separate categories like Sequencing, Plug-Ins, Soft Synths, Effects, Utilities, etc.?

---

### Post by margazhang on 2009-12-07
As a user of Ubuntu for two years, I just recently did a clean install of Ubuntu Studio 9.10 on my HP computer as I need the studio to edit audios and videos. 

As I use it now, the most annoying fact is that it does not have a panel bar showing all the opened application windows - hope you know what I mean. 

Yes, I can use the Alt-Tab combo, just like in MS Windows, to see all the opened windows. But I prefer the normal Ubuntu setting, that is, all opened windows show on a bar at the bottom of the computer screen with titles and you just click to make any one active.

Do any of you know how to do this? I am still searching.

---

### Post by margazhang on 2009-12-07
> **margazhang said:**
> Do any of you know how to do this? I am still searching.

I figured it out myself - right-click any blank area in the top panel and then select "New Panel" and a new panel is automatically added to the bottom of the screen. Then right-click any area in the bottom panel and select "Add to Panel..." and then pick "Window List" to show all the opened windows at the bottom. Viola!

Hope that this bottom panel will be there by default. Thanks!

---

### Post by DerickX on 2009-12-07
At least a bugfix of pulseaudio concerning the multichannel (m-audio) cards...

---

### Post by wkulecz on 2009-12-07
> I would like Ubuntu Studio to become a distro targeting audio works only, which it in effect already is.
I feel the video and graphics branches are just slapped on there and I really gain nothing from using Ubuntu Studio instead of using standard Ubuntu and adding the appropriate applications myself.
For audio you got real-time kernel etc. but for graphics/video there's nothing special really.

Disagree here.  Other than perhaps YouTube,  good video is built on top of first class audio.

Without top of the line audio for Linux video editing it'll never be competivative with the Mac or Windows.

At this point I'd settle for any video editor that doesn't crash in the next version 

--wally.

---

### Post by Native Dialect on 2009-12-08
I have a challenge for any of you who make full use of LMMS or Ardour or any of the other DAW applications for Ubuntu. I currently have a desktop installation of Windows XP. My laptop is a dual boot between Windows Vista and Jaunty Jackalope. Even though I think I can do without computer gaming (PS3 is looking more attractive by the minute), I simply can't do without the ability to create music. I use Reason 3, Windows Sound Recorder, Recycle, ReBirth and Audacity. Only one of those tools is available in Ubuntu.

I have Ardour, Hydrogen, LMMS and several other music production tools, but none of them seem to rub me the right way. They just aren't Reason. I fear that abandoning Windows (which means abandoning Reason) will cause me to lose out on certain types of musical production. I make a lot of game mixes that I am not sure can be replicated in any of the DAW software available for GNU/Linux. The challenge I offer, is to have somebody here replicate two songs I have made using Reason:

[http://www.youtube.com/watch?v=LNswj9kEc1U](http://www.youtube.com/watch?v=LNswj9kEc1U)

[http://www.youtube.com/watch?v=aAJ7WxGlMkM](http://www.youtube.com/watch?v=aAJ7WxGlMkM)

If anyone steps up, I will even provide the samples I use. Note however, that both of those compositions consist primarily of original work. If I can see that it is possible to recreate the music I am already making in Windows, I think I will feel comfortable about fully converting rather than being a dual booter. I do love Ubuntu. I just happen to love music more.

---

### Post by thorgal on 2009-12-08
as a Windows user, you think windows when you talk about linux. But linux does not have to be a "mirror" environment of what you already know very well. So let me suggest the following:

instead of dumping windows (if that's your implicit goal behind your post), expand your studio with a linux-ardour box only, connected to your gigabit LAN and running jack2. Install jack2 on your windows box, use the "netone" jack2 driver and use your linux box as the jack master.

Now, run your sound stuff on windows (games, whatnot) and redirect the audio to your recording box (linux-ardour).

You will have the best of both world for a while in order to get familiar with the linux audio stuff while maintaining a bit of your former workflow.

But of course, before all this, you have to be very clear with yourself on the "why you want to switch to linux" when you seem to be definitely fluent in Reason and windows.

EDIT: oh yeah, about your last comment (... love ubuntu, but ...). This is also a certain perspective you are giving here. Let me share mine: I use linux as a tool, not because I love it. I love what I do with it though :) (I am not using windows because I never had and am probably too old to learn windows ... don't laugh, but that's how I feel about it ;) )

---

### Post by dawiba on 2009-12-08
> **thorgal said:**
> EDIT: oh yeah, about your last comment (... love ubuntu, but ...). This is also a certain perspective you are giving here. Let me share mine: I use linux as a tool, not because I love it. I love what I do with it though :) (I am not using windows because I never had and am probably too old to learn windows ... don't laugh, but that's how I feel about it ;) )

Where you say Linux, say Windows. Where you say Windows, say Linux. That's probably the reason a lot of people don't try Linux. Just another perspective ;)

---

### Post by thorgal on 2009-12-08
> **dawiba said:**
> Where you say Linux, say Windows. Where you say Windows, say Linux. That's probably the reason a lot of people don't try Linux. Just another perspective ;)

hehe :)

---

### Post by extendedping on 2009-12-08
since I am just learning recording I can't really comment on anything but appearances. I think the default wallpaper is extremely cluttered. secondly when (as on 9.04 and 9.10) you open a few browsers (or whatever) and you realize you have to add stuff to the panel just to see the opened apps, that is a real turnoff. It makes you wonder what other strange things will lie under the hood. if those issues were fixed I would just install studio and not install ubuntu, then selectively pick studio packages. ok wallpaper which I hate is subjective, apps disappearing really needs to be fixed if non linux users who are used to an integrated desktop just working are to feel welcome.

---

### Post by Royke on 2009-12-08
That there finally is a out-of-box working realtime kernel for my machine too! I haven't been able to use rt for quite a while(feisty fawn) and no matter what (rt-kernel) i try it always ends up with a sort of system hang. Mouse and keyboard is then responding very slowly. For this i even tried 64studio's multimediakernel and in 9.04 it works reasonable, but in Karmic with a newer multimediakernel its just the same as always. I am ready to throw this pc in the garbage, but maybe someone here can provide a sollution. And i don't see why i should build my own rt-kernel when you develloper guys can do this way better. ;)
My pc is a fujitsuSiemens Scaleo p, core2duo 2*1.8GHz, 1gb ram. The motherboard is not really advanced and has not many expansionoptions, but it should be capable of running rt nevertheless.

---

### Post by markbuntu on 2009-12-08
If you want the rt kernel to work with your machine use it and file bug reports. That's what I did and it took a year but now the rt kernel works with my machine again  after not working since hardy. 

The devs really do fix stuff if you tell them something is broken.

---

### Post by Native Dialect on 2009-12-08
> **thorgal said:**
> 

instead of dumping windows (if that's your implicit goal behind your post), expand your studio with a linux-ardour box only, connected to your gigabit LAN and running jack2. Install jack2 on your windows box, use the "netone" jack2 driver and use your linux box as the jack master.

Now, run your sound stuff on windows (games, whatnot) and redirect the audio to your recording box (linux-ardour).

You will have the best of both world for a while in order to get familiar with the linux audio stuff while maintaining a bit of your former workflow.

But of course, before all this, you have to be very clear with yourself on the "why you want to switch to linux" when you seem to be definitely fluent in Reason and windows.


1) I've seen your Ardour demo on Youtube. It is alwayas convenient when people use the same online identity everywhere. You did amazing work.

2) I do enjoy things that I can do with GNU/Linux that are (as of yet) not possible in Windows. I much prefer Compiz to Windows Aero. Having four desktop spaces and the cube, make writing papers much more efficient (no need to frequently minimize and arrange windows). Ubuntu boots up much faster than my Vista partition. I even purchased an "All About Ubuntu" guide from Borders. So I am enthusiastic about the platform and the community. 

However, it is difficult to let go of certain applications that are still Windows/Mac OS only. In most cases, I have found alternatives. No Steam? Just play games like Nexuiz and Glest. No iTunes? Use the Amazon store for digital movies and music. It works great with Ubuntu. But when it comes to music production, I would have to sacrifice everything I have done thus far. I would much rather only use a single operating system, but it seems difficult to do so when I risk losing so much.

3) Thank you for the compliment about my proficiency with Reason. I do enjoy the hobby.

4) I like your suggestion. It is perhaps the best route to go. I suppose there is no real reason to use only a single operating system. After all, why should I limit my access to various tools? Still, I think it would be great to only have to rely on one product.

---

### Post by thorgal on 2009-12-09
hi there,

1- my video sucks : it shows the complete lack of a jack session management (never tried LASH or LADI stuff, so it may well be that is shows my ignorance as well). The only thing I wanted to show was that one could use some very well crafted piece of windows software in a linux audio environment, for the VSTi I use in this video is just extremely well written and never ever crashed on me unlike so many other win32 VSTs. 

2- I see what you mean: I never really understood the windows desktop (one screen cluttered with tons of windows to minimize or maximize all the time). I may be ignorant here as well though. But as time goes, I see elements in gnome or KDE strangely reminding the windows desktop ... ;) Not sure where this goes or whether this is good ...

3- hobby or not, it is nice to be fluent in some tools when creativity kicks in and the tools you know fit the bill. 

4- depending on your patience and "relationship" with computers, softwares, etc, it can be a painless but also a very painful road. In either case, you may learn a few things on the way and be inspired to explore new avenues :)

I sucessfully tested such a netjack communication between windows and linux but my not using windows on a daily basis turned the experiment into a proof of concept only. I have no real need of using a windows box in my studio due to the studio's modest size and the type of music I am into. I don't own tons of VSTs or win32 software and have not felt the need to use some that I could not run on linux via wine based wrappers (dssi-vst, wineasio, etc).

Should I feel the need for expanding the studio with windows software, I'd definitely go the netjack way. There is an asio jack bridge for windows that can transform all asio aware apps into jack2 clients. Then, thanks to the netjack driver for windows, the apps can stream their output to other jack boxes (e.g. linux based).

---

### Post by scotty64 on 2009-12-11
- Regular maintenance releases of the rt-kernel. I think these are essential, particularly to fix critical errors related to the filesystem etc. (See my other post in this forum).
- Rosegarden 10.x (I hope it will be ready then)
- Two application menu entries to start QSynth (ALSA or Jack)
- webcamstudio ([http://sourceforge.net/projects/webcamstudio/](http://sourceforge.net/projects/webcamstudio/)) should be in the repos. It is not just a good tool to compensate for the terrible linux webcam support in Flashplayer 10.x, but a great live video tool as well.

---

### Post by Jurica on 2009-12-11
Hello!

In my studio I use Windows Xp on PC,OS9 on Mac and Ubuntu Studio 9.10 Laptops. Ubuntu Studio is a very powerful tool when it comes to music making. I found out that it works pretty great when it comes to sound synthesis. This month I made some music for a professional documentary only using a linux. And it turned out great.
Still I see that main problem is systems unstable behavior and lack of drivers
for some hardware.I think that is main thing to be focused on, but I don't think that this is developers problem. So maybe developers could talk to ALSA, hardware manufacturers or something.... Many studios are equipped with hardware that works much better on Mac or windows based PC so Ubuntu is unable to reach that pro stage and people would really like to use it. 

So when it comes to Ubuntu Studio 10.04 I would like to see:

- more driver support
- more stable system (although 9.10 has a really stable RT kernel..keep it)
- more plugins that come with install
- better arrangement of audio programs menu  
- maybe microtonal program "Scala"    
- keep the existing software that works fine

And most important of all...keep up an excellent work!
The idea is great and you are doing a great thing...I mean..free audio software, that actually works...wow...you did it and for art's sake, don't give up:D
Best from Cro
JJ

---

### Post by skipx on 2009-12-12
Full PD-Extended [http://puredata.info](http://puredata.info) !!
and maybe even arduino software although based on java..

---

### Post by Scott L on 2009-12-12
> **skipx said:**
> Full PD-Extended [http://puredata.info](http://puredata.info) !!
and maybe even arduino software although based on java..

rlameiro on IRC would second that suggestions!

In case everyone doesn't know, you can talk to other Ubuntu Studio users and the developers on IRC at #ubuntustudio and #ubuntustudio-devel.

Here is the Ubuntu Community Help Page for IRC:  [https://help.ubuntu.com/community/InternetRelayChat](https://help.ubuntu.com/community/InternetRelayChat)

Personally I still use [XChat]("https://help.ubuntu.com/community/XChatHowto") for IRC.

Come and say Hi to us and ask questions when you have problems, questions or just want to say Hi.

---

### Post by pgmer6809 on 2009-12-13
What I would like to see is a really good HOW To on the very basics.
I have been trying for a couple of years to get a Linux Audio Workstation up and running so I can clean up my LP collection.
I am a very experienced computer user, but I just cannot get everything to work.

Major annoyances:
1. Too many options, not enough explanations. For example given my goals do I need Jack? What for? 
Why would I need both Ardour and Audacity? Which one should I focus on?

2.ALSA. Nothing works as it should. There are too many connections and undocumented demons started automatically. There are too many hoops to go through to get the audio driver to load and work properly. OSS is simpler and better in this regard, but none of the video players seem to work when it is used in place of ALSA.
A nice clean minimal default ALSA setup would be nice.

3. Disk burning. This continues to be very problematic. Half the time the burner reports success but the CD is useless.
Brasero is particularly bad for this. 

4. Title creation in DVD's. It is difficult to make sense of all the different file types and folders in a typical DVD. I have not found any simple document that describes a minimal DVD layout and the relationships between the files.
I simply cannot get the tool recommended by most for DVD title creation to work. 

5. Distros and packages that require tweaking of file permissions to work. There is no excuse for this. A 'multimedia' distro should be able to define a 'media' group, automatically put the user in that group, and then give that group whatever permissions it needs to access sockets, demons, audio cards, directories, CD drives etc.

6. Speed.
The last time I just copied an audio CD using Ubuntu 9 it was so slow on a dual core Intel 2GHz machine with 8MB of ram that I had time to boot my old 1GHz single core AMD W98 machine and copy another CD before the Ubuntu one had finished.
And the Ubuntu CD/DVD burner was a more recent faster device than the w98 one.

I would really like to be able to get back to doing audio clean up on my LP's and stop wasting my time trouble shooting the tools; I hate running XP which is my only real alternative at this point.

Major suggestion.
Include in the distro a useful tutorial that addresses the basic tasks in a simple minimalist way.
If the user does not need Jack, don't mention it. (and turn it off by default). Ditto for pulseaudio or anything else  which is not needed and gets between the hardware and the application.

If Audacity is good enough to do audio editing, dont drag in Ardour. (or vice versa)

If the mainstream DVD player is ?, then just say so.

Give a foolproof example of how to insert titles in a DVD.

Explain the ALSA pipeline.

Minor suggestion:
Fix ALSA so that it does not try to create invalid device names from the mfg information on the card. I have an AUDIGY2 ZS Platinum; when ALSA tries to use this card it creates devices with commas in their names, that other programs and ALSA itself cannot use. OSS has no problems with the basics of the card, allthoug it does not see (or use) many of the extra channels and features.
pgmer6809

---

### Post by AutoStatic on 2009-12-14
> **pgmer6809 said:**
> What I would like to see is a really good HOW To on the very basics.That's a community thing, not something the Ubuntu Studio devs should provide. Besides, good documentation exists, what is it that you think is lacking?

> **pgmer6809 said:**
> Major annoyances:
1. Too many options, not enough explanations. For example given my goals do I need Jack? What for?If you ask yourself this question then you probably don't need it.
> **pgmer6809 said:**
> Why would I need both Ardour and Audacity? Which one should I focus on?Audacity. Ardour is multitracking recording software, a DAW (digital audio workstation), you don't need that to digitize your vinyl records.

> **pgmer6809 said:**
> 2.ALSA. Nothing works as it should. There are too many connections and undocumented demons started automatically. There are too many hoops to go through to get the audio driver to load and work properly. OSS is simpler and better in this regard, but none of the video players seem to work when it is used in place of ALSA.
A nice clean minimal default ALSA setup would be nice.First, that's an Ubuntu thing, not Ubuntu Studio. Second, why complicate the state of sound on your installation even more with OSS? What problems do you run into with Alsa? And why is OSS better in your opinion when 1. no video player works anymore and 2. it does not see (or use) many of the extra channels and features? And besides, neither OSSv3 nor OSSv4 are included in Karmic Koala so how did you install OSS?

> **pgmer6809 said:**
> 3. Disk burning. This continues to be very problematic. Half the time the burner reports success but the CD is useless.
Brasero is particularly bad for this.This is an Ubuntu thing also, not something Ubuntu Studio should work on. Besides, when I look at point 6 I reckon it's a hardware issue, not an Ubuntu issue.

> **pgmer6809 said:**
> 4. Title creation in DVD's. It is difficult to make sense of all the different file types and folders in a typical DVD. I have not found any simple document that describes a minimal DVD layout and the relationships between the files.
I simply cannot get the tool recommended by most for DVD title creation to work.Not an Ubuntu Studio thing either I reckon.

> **pgmer6809 said:**
> 5. Distros and packages that require tweaking of file permissions to work. There is no excuse for this.There is, it's called Linux: [http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

> **pgmer6809 said:**
> A 'multimedia' distro should be able to define a 'media' group, automatically put the user in that group, and then give that group whatever permissions it needs to access sockets, demons, audio cards, directories, CD drives etc.Totally agree on that one. Ubuntu Studio Controls should take care of this and I think we can expect some major improvements for 10.04.

> **pgmer6809 said:**
> 6. Speed.
The last time I just copied an audio CD using Ubuntu 9 it was so slow on a dual core Intel 2GHz machine with 8MB of ram that I had time to boot my old 1GHz single core AMD W98 machine and copy another CD before the Ubuntu one had finished.
And the Ubuntu CD/DVD burner was a more recent faster device than the w98 one.Sure it is not a hardware issue? And this also not something Ubuntu Stdio should work on.

> **pgmer6809 said:**
> I would really like to be able to get back to doing audio clean up on my LP's and stop wasting my time trouble shooting the tools; I hate running XP which is my only real alternative at this point.Hating an OS is not a good starting point for using Ubuntu in my opinion.

> **pgmer6809 said:**
> Major suggestion.
Include in the distro a useful tutorial that addresses the basic tasks in a simple minimalist way.That's up to the community, they're already working very hard on it. Besides, do you realise how much time it takes to write documentation? And how much money Canonical had to spent if they wanted to provide this to their users? I think it's realistic to state that if Canonical had decided to provide documentation themselves then we wouldn't be finding ourselves here.

> **pgmer6809 said:**
> If the user does not need Jack, don't mention it. (and turn it off by default).It is turned off by default. In a normal Ubuntu installation it's not even installed. And if you're using Ubuntu Studio because of the audio apps then chances are you do need Jack.

> **pgmer6809 said:**
> Ditto for pulseaudio or anything else  which is not needed and gets between the hardware and the application.That's not something Ubuntu Studio could work on. Gnome has decided to let go of ESD and use PulseAudio as the default sound daemon. So it's not even an Ubuntu thing. If you don't want to use PulseAudio then use either KDE or uninstall it and use something else, like OSS (which is a driver stack, not a sound daemon like Pulse or JACK, but that's a different discussion :)). You're free to do so, and you're an experienced computer user which implies, at least to me, that you know your way around.

> **pgmer6809 said:**
> If Audacity is good enough to do audio editing, dont drag in Ardour. (or vice versa)Anyone who advised Ardour to digitize some records doesn't know what he/she's talking about. Audacity should suffice.

> **pgmer6809 said:**
> If the mainstream DVD player is ?, then just say so.There are as many DVD players as their are tastes. Choose the one you like.

> **pgmer6809 said:**
> Give a foolproof example of how to insert titles in a DVD.Ask over here, that's what this forum is for! I can't help you though, I practically never burn DVD's.

> **pgmer6809 said:**
> Explain the ALSA pipeline.ALSA is the default sound stack of practically all distro's. It provides all the sound drivers. There isn't really much more to it actually.

> **pgmer6809 said:**
> Minor suggestion:
Fix ALSA so that it does not try to create invalid device names from the mfg information on the card. I have an AUDIGY2 ZS Platinum; when ALSA tries to use this card it creates devices with commas in their names, that other programs and ALSA itself cannot use. OSS has no problems with the basics of the card, allthoug it does not see (or use) many of the extra channels and features.
pgmer6809This is an ALSA thing, not an Ubuntu (Studio) thing. Did you file a bugreport?

Beforehand, my apologies if I may sound harsh but what I wrote down just reflects my point of view. I'm in no way involved with PulseAudio, Ubuntu Studio or ALSA, I'm just sharing my personal experience and I happen to like Ubuntu a lot.

---

### Post by wkulecz on 2009-12-16
Not strictly just for studio, but I'd sure like Amarok 1.4 back in 10.4!  Armarok 2.0 is garbage.

--wally.

---

### Post by JC Cheloven on 2010-01-06
- A sf2 editor (urgent)
- OpenShot video editor in the repos, or even in the distribution. In my experience it's almost ready, and good.
- A way to not install, or to remove, pulseaudio (untill some alsa-pulse issues are solved; for example no human way to get working the hammerfall 9632 in the presence of pulse).

Note.- imo a careful selection of video apps should stay (more or less as it is now).

---

### Post by fedexnman on 2010-01-06
1. record my desktop    compiled with jack support ( so we can make youtube tutorials )
2. the newer  beta version of hydrogen ( its got rubberband timestreching and loops now )
3. newer version of ardour
4. again thx to the guys that pkg ubuntu studio, ive finally quit using windows xp ( been learning ubuntu since 8.10 )

---

### Post by Guitar John on 2010-01-06
I'm primarily a musician, but I would have been inclined to learn how to use some of the Graphics (like Blender) if I had anything resembling a basic "HowTo."

---

### Post by Scott L on 2010-01-06
> **fedexnman said:**
> 1. record my desktop    compiled with jack support ( so we can make youtube tutorials )
2. the newer  beta version of hydrogen ( its got rubberband timestreching and loops now )
3. newer version of ardour
4. again thx to the guys that pkg ubuntu studio, ive finally quit using windows xp ( been learning ubuntu since 8.10 )

1. Don't know much about recordmydesktop
2. Hopefully Hydrogen 0.9.4 will be in Lucid
3. Ardour 2.8.2 is in Karmic, Ardour 2.8.3 is already in Lucid.  You can find Ardour 2.8.2 for Hardy [here]("https://launchpad.net/%7Eslavender/+archive/ppa").
4. I quite agree

---

### Post by m0o on 2010-01-07
I would definitely like to see the Grub eye candy thats been floating around on the forums. I doubt we'll see it on Lucid due to stability issues.

---

### Post by Stochastic on 2010-01-07
> **m0o said:**
> I would definitely like to see the Grub eye candy thats been floating around on the forums. I doubt we'll see it on Lucid due to stability issues.

Do you mean Plymouth? From what I know it will be in Lucid, but that's rather unrelated to the Ubuntu Studio team.

---

### Post by nick_geetar on 2010-01-07
I think it should come with rakarrack instead of Creox.

---

### Post by Scott L on 2010-01-07
> **nick_geetar said:**
> I think it should come with rakarrack instead of Creox.

Rakarrack has replaced Creox in Lucid.

It was discussed here, in the Ubuntu Forums:
[http://ubuntuforums.org/showthread.php?t=1341935](http://ubuntuforums.org/showthread.php?t=1341935)

On the Ubuntu Studio Users Mail List:
[https://lists.ubuntu.com/archives/ubuntu-studio-users/2009-November/005674.html](https://lists.ubuntu.com/archives/ubuntu-studio-users/2009-November/005674.html)

and on the Ubuntu Studio Developers Mail List:
[https://lists.ubuntu.com/archives/ubuntu-studio-devel/2009-November/002102.html](https://lists.ubuntu.com/archives/ubuntu-studio-devel/2009-November/002102.html)

These are great places for current news regarding Ubuntu Studio and I highly encourage all that are interested to follow these.

---

### Post by tlstudio on 2010-01-25
> **MiCK.ca said:**
> What are you annoyances?
What programs do you want to see?
Do you want a personal say in the programs that are loaded at install time?
What good things should be expanded upon?
What do you record? (i.e. live, electronic, mix of both)

Sorry if these have already been covered but here is my list of annoyances/suggestions:

1. Disable the ondemand service by default. It seems counteractive to develop a realtime kernel and then throttle the cpu(s) back to a lower speed. However, I understand many users are using laptops so maybe a checkbox could be added in Ubuntu Studio Controls for "power saving feature" but defaulted to off? Or maybe the install program could detect whether the pc is a laptop or desktop and set it accordingly?

2. When installing, the user entered during install (not sure about subsequent users) is automatically part of the audio group but not the video group. Being that UbuStu is a multimedia OS, should it not add the user to both groups? This is with regards to firewire access in my case since the video group owns the firewire device (raw1394). Could the checkbox in Ubuntu Studio Controls for firewire (raw1394) also add the current user to the video group?

3. With regards to firewire again (there really seems to be a growing trend toward firewire devices), I would like to see the rtirq package updated and a fix to the rtirq script so that it references the correct interrupt (rtc0) and add firewire (ohci1394) to the RTIRQ_NAME_LIST and RTIRQ_NON_THREADED lists in /etc/default/rtirq as per trulan's thread [http://ubuntuforums.org/showthread.php?t=1328175](http://ubuntuforums.org/showthread.php?t=1328175).

4. Ardour is truly an awesome piece of software and I would like to see 10.04 include LV2 plugin support as well as a preset grouping of plugin "favorites". There are so many plugins and it would be nice to have a go-to list already made to make the UbuStu package just work for most people out of the box. Also, I don't find the plugin menu grouping all that useful, instead of by author, could it be grouped by function? (e.g Dynamics, Time Delay, etc.) Or could the grouping format be customizable? Please forgive me if this is already the case!

I realize some of these are really just time-saving tweaks, but I think they will also reduce frustration from new users in the community. I'm very happy with UbuStu 9.10 (64) especially after having solved the ondemand/firewire "problems".

I generally only use Jack, Ardour, and Jamin. I also like Patchage and the jack meterbridge is classic. However, I actually prefer to see everything installed personally so I have whatever I could possibly need at my fingertips - I don't have internet access at the studio so installing software/updates is not simply a click away unfortunately. Also I do appreciate the graphics work that goes into UbuStu - the animated loading graphic is just cool!

I hope some of this is helpful...

Cheers,

TLStudio

---

### Post by rookworm on 2010-01-29
easy realtime jack setup, no weird manual configuration required.

---

### Post by LuridCinema on 2010-01-29
Disc Checking on shutdown !! I have installed AutoFsck and it still tries to do the checking on startup GRRRRR. Other than that hey it's a rock-solid distro which does EVERYTHING. I'm an Indie Filmmaker and I gave up on windoze and now do everything on Ubuntu...

---

### Post by TiddlyPom on 2010-02-26
For me the priorities are:

1) Realtime Kernel (100% priority) but WORKING WITH ATI/NVidia Drivers!
2) Jack daemon running as default (with qjackctl in system tray perhaps)
3) All standard audio routed through jack by pulseaudio-module-jack

See [**this link**]("http://sync-signal.com/2009/12/configuring-jack-and-pulseaudio-on-ubuntu-9-10/")

If (1) was possible then I would probably use the RT kernel on my development Ubuntu laptop as well!

Ubuntu Studio rocks (even on an antique Dell Inspiron C610 connected to a Yamaha Clavinova) as the Clavinova does most of the heavy lifting :)

Ubuntu Studio 9.10 (i386-RT)
1GHz Pentium III
512MB RAM
80 GB hard disk (PATA-133)
ATI Mobility Graphics (about GeForce 3 level - uses open source driver) - 1024x768

I can use Rosegarden, Hydrogen and Ardour absolutely fine under the RT kernel.  Trouble was I subscribed to "latest updates" and these broke pulseaudio-module-jack so I need to rebuild it without latest updates :(

Main development laptop is

Lenovo 3000 N200
Ubuntu 9.10 (x86_64)
Intel Core2 Duo (2.5GHz dual core)
4GB RAM
500GB SATA hard disk - (need more space 1TB would be nice!)
NVidia GeForce Go 7300 (1680x1050)

---

### Post by AutoStatic on 2010-02-26
> **TiddlyPom said:**
> For me the priorities are:

1) Realtime Kernel (100% priority) but WORKING WITH ATI/NVidia Drivers!I'm really eager to know if 10.04 will come with a RT kernel at all.
> **TiddlyPom said:**
> 2) Jack daemon running as default (with qjackctl in system tray perhaps)This probably won't happen in the near future but you can easily set this up yourself.
> **TiddlyPom said:**
> 3) All standard audio routed through jack by pulseaudio-module-jack[JACK is back in main]("https://bugs.launchpad.net/ubuntu/+source/jack-audio-connection-kit/+bug/510481") so this should be possible again without recompiling stuff.

---

### Post by trulan on 2010-02-26
I'm itching to test the 2.6.33 kernel with the RT patch that has just been released.  Fortunately or not, Ubuntu has their way of operating and switching kernels midstream on a release isn't their way of operating.  But, I must say that the current RT kernel has been working flawlessly for me.  Unfortunately, it hasn't been so great in my Lucid testing install.  But that has other issues too (as alpha software will).  Karmic may just have to be our studio LTS - which it can be if good backports are maintained, like philip5 has been doing in his ppa.  Up-to-date software is more important than having a new kernel every six months.

There will be the 2.6.31-rt kernel, and there will be a 2.6.33-rt kernel.  How well they will play with Lucid, which will be built around 2.6.32, remains to be seen.  We'll have to go with the best of the two.

---

### Post by heLeN2x on 2010-03-03
**What are you annoyances?**

My soundcard is still hard to set up, I use ubuntustudio since 7.04 and had to reinstall after every release because it always broke my setup. Now I have two ubuntustudio installed on my box : the old one, and the new one, because I'm tired of tweaking after upgrading (and I often ended up with a fubar-buntu).
I still don't really understand IRQs and priorities related stuff, but I know by experience that the default setup isn't the one that works better on my box.
I found a script to check my configuration, called realtimeconfigquickscan, I don't know if it does a good job but anyway it still raises errors when ran on a clean install, so I guess there's some work to be done here.

**What programs do you want to see?**

I'm really happy with the current program list :)
I use Renoise as my main composing tool and Ardour is the best DAW I've ever tried (but I never tried protools), there's all I need for audio analysis, mastering, djing...
Maybe more weird experimental softsynths ?

Oh, I know... I want Electricsheep as the default screensaver.

**Do you want a personal say in the programs that are loaded at install time?**

I think there's already something like this in the CLI installer, I don't need something more specific. Anyway the total size of a clean install is decent, I never thought about removing software to have more space.

**What good things should be expanded upon?**

Ubuntustudio Controls is a good idea, but it should control more system parameters.
A diagnosis tool (integrated to US Controls) would be handy : how much global latency do I have ? Did I set the right priority values ? are my irqs ok ? is there anything that does not work completely right ?

**What do you record? (i.e. live, electronic, mix of both)**

Mix of both, and I use it for live performance too.


I tried other audio-aimed distros, but I always went back to ubuntustudio (well, except 8.10, this one never worked for me) : 64studio is very stable, but the apps are way too old. Gentoo with proaudio worked really fine and I enjoyed using cutting edge builds, but I eventually screwed it all up. Ubuntustudio provides up-to-date software, ease of use, and stability, it just suits my needs so keep up the good work!

---

### Post by AutoStatic on 2010-03-05
What about the debconf jackd.template that installs an audio.conf file in */etc/security/limits.d/* ? Won't this cause conflicts with Ubuntu Studio Controls? Or does Ubuntu Studio Controls modify this file and not */etc/security/limits.conf* ?

---

### Post by 4String_Gal on 2010-03-09
Hi Mick,

The main thing that I would like is for all of the applications in the audio production to work with JACK.

I'm running a 64 bit machine with a firewire sound card (and onboard sound disabled in BIOS). So, if an audio application doesn't work with JACK (and FFADO) then I can't use it.

I'm fairly new to Ubuntu Studio, and overall I really like it. I am keeping a file of things I had trouble with, and will share once I have it more together.

Thanks and looking forward to 10.04!

-Susan

---

### Post by markbuntu on 2010-03-10
Now that jack is back in main then perhaps we can get the now available pulse-jack modules included in the ubuntustudio metapackage and include the script to load them in Execute script after startup.

It would go a long way to getting more casual users interested in ubuntustudio and bring more support for the project.

If anyone is testing lucid and could help with testing this and reporting any bugs they encounter it would help get this dialed in. If you need the script:
```

#load pulseaudio jack modules
#!/bin/bash
pactl load-module module-jack-sink
pactl load-module module-jack-source

```

Copy this somewhere and make it executable and then in jack control/setup/options add the path to it in Execute scripts after startup and check the box.

---

### Post by AutoStatic on 2010-03-10
> **markbuntu said:**
> Now that jack is back in main then perhaps we can get the now available pulse-jack modules included in the ubuntustudio metapackage and include the script to load them in Execute script after startup.You mean that these scripts should be loaded by default?

---

### Post by markbuntu on 2010-03-10
Yeah, that would be the idea. Unless pulseaudio is removed I really don't see any point in not doing so.

---

### Post by 4String_Gal on 2010-03-11
> **markbuntu said:**
> Yeah, that would be the idea. Unless pulseaudio is removed I really don't see any point in not doing so.

(about the pulse-jack modules scripts being loaded on startup)

I hope this doesn't happen. Perhaps it could be an option for people who want it, something that could be set somewhere.

I don't use pulseaudio for anything, having only a firewire card and no other audio. So, I just use JACK and FFADO. I even have Flash outputting to JACK, thanks to a lovely driver I found here:

[http://www.christeck.de/wp/2010/01/10/playing-your-favourite-flash-music-via-jack-and-firewire/](http://www.christeck.de/wp/2010/01/10/playing-your-favourite-flash-music-via-jack-and-firewire/)

It works great. Maybe that's something to add to Ubuntu Studio.

Cheers!

-Susan

---

### Post by AutoStatic on 2010-03-11
> **4String_Gal said:**
> I hope this doesn't happen. Perhaps it could be an option for people who want it, something that could be set somewhere.Me neither. I use JACK on my audio machine and PulseAudio on my workstation/desktop. That's where those daemons are designed for and they shouldn't get intertwined too much.

---

### Post by markbuntu on 2010-03-11
Then pulse should be removed from ubuntustudio.

---

### Post by AutoStatic on 2010-03-11
Or give the user the option to use a ~/.pulse/client.conf file so that PulseAudio can be disabled without respawning.

---

### Post by markbuntu on 2010-03-12
Yeah, pulseaudio autospawning should definitely be disabled since any system sounds will spawn it the way things are now.

---

### Post by kazakore on 2010-03-13
Not been using it enough to make any real observations so far but from everything I've read and my limited experience Pulse Audio should not be the default standard for something targeted at audio/multimedia usage. Jack and ALSA seemed to work well and is flexible enough for everybody to work to their needs. Pulse Audio may simplify things for people on a workstation just wanting to listen to the occasional tune or watch the odd movie but it really doesn't seem suited for professional applications.

Also heard good things about the PXU plugins on another site recently and couldn't see them in the repository. May be worth considering if I'm not just being blind.

[http://sourceforge.net/projects/pxu/](http://sourceforge.net/projects/pxu/)

---

### Post by chkneater on 2010-03-13
I have one word and I really mean this so I will say it in caps: DOCUMENTS!!  Seriously, it would help IMMENSELY just to have manuals for some of the junk that gets thrown into the studio versions.  I still can't get jack to run in realtime.  It would be nice to be able to pull up the manual when I have problems and fix it myself then to have to post a topic and wait for replies.

---

### Post by chkneater on 2010-03-13
> **trulan said:**
>  Karmic may just have to be our studio LTS - which it can be if good backports are maintained, like philip5 has been doing in his ppa.  Up-to-date software is more important than having a new kernel every six months.
.

Amen to that, it's frustrating that everytime I upgrade Ubuntu, there is already a new version being tested and there seems to be lack of support for the previous versions.  At this rate the alphabet will be used up by Halloween and they'll have to makeup animals to name it after.  I just think that more effort should be made to *refine* and perfect a version as best as possible before starting new projects.

---

### Post by rlameiro on 2010-03-14
> **chkneater said:**
> I have one word and I really mean this so I will say it in caps: DOCUMENTS!!  Seriously, it would help IMMENSELY just to have manuals for some of the junk that gets thrown into the studio versions.  I still can't get jack to run in realtime.  It would be nice to be able to pull up the manual when I have problems and fix it myself then to have to post a topic and wait for replies.

[https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation)

---

### Post by Pablo_F on 2010-03-14
**What programs do you want to see in ubuntustudio lucid?**

Please ubuntu devs, deprecate gtick in favour of [gtklick]("http://das.nasophon.de/gtklick/"). gtklick is a frontend for klick. The user would see gtklick in the sound and video menu. klick is command line. 

I use ubuntustudio to make some music. I am amateur. I mainly use hydrogen, ardour, rakarrack, Jc_Gui and a VSTi through dssi-vst or (lately) festige. 

Cheers! Pablo

---

### Post by ken78724 on 2010-03-15
since my 1.5 gig download extracted on my laptop but would not run without uninstalling and losing what looked like extremely great work, I'd like to see a "How to perhaps with synaptic package manager advice on getting the grub loader past humps in the recovery process." I noticed the opening page that was visible looked outstanding. But that all of which went by the wayside and my ooos and aaas too. Keep it up! I do not know how to build what I saw come up on my new laptop. 

On this PC, karmic comes up saying edubuntu which is nice but ... 

Looking forward to UbuStu 10.04. Hurrah!

Kenneth

---

### Post by s.Oliver on 2010-03-15
like many post before i would like the entries of the music production better grouped.

i wish there is a possibility to route mic input in realtime through jack and through some effect plugins to add reverb, chorus, compressor and so on. i don't know if it's possible, but it would be great.

---

### Post by s.Oliver on 2010-03-15
audacity with jack input and output ports to connect multiple sound sources to record.

---

### Post by minor ubuntoid on 2010-03-15
I would like to see:

* A help system that contains help for all the installed applications, or at least links to the on-line help
* In the installer, guided partitioning modified to include parameters for aligning to erase blocks on SSDs (over LVM and LUKS) so we can get maximum disc bandwidth
* Pulseaudio disabled by default
* Jack launched on startup by default
* One-click switching between unthrottled and power-saving CPU settings

Thanks!

---

### Post by devehf on 2010-03-15
MIXXX and other DJ applications for managing libraries of audio recordings, playlists, burning CD-Audio with printed jewel case inserts, syncing to USB removable media with playlists that can be used in other devices.

---

### Post by rookworm on 2010-03-26
oh, and I'd like to see gRIP added back to the repositories. It was a great ripping program.

---

### Post by lkkgaladi on 2010-04-15
I would like to see the developers include web development tools like DreamWeaver and Flash. (I'm sure there must be something like those packages for linux)

---

### Post by mango42 on 2010-04-16
I would like to see all the developers take a good loooong holiday in the sun once Lucid Lynx is finalized! :)

Karmic's fine the way it is (I was genuinely blown away by the sheer professionalism of the KK LiveCD install, as opposed to upgrading) - Lucid can only be even smoother.

:popcorn:

---

### Post by deepredblood on 2010-04-17
does this support m-audio fasttrack pro?

---

### Post by Native Dialect on 2010-04-17
> **deepredblood said:**
> does this support m-audio fasttrack pro?


Ubuntu Studio is merely a package, like other *nix distributions. It is merely a compilation of FOSS that is focused on creative output (e.g. video editing/production and music editing/production). Really, your concern depends on which DAW you plan to use. LMMS (Linux Multi-Media Studio) for instance, does not work with Fast Track (to my knowledge). On the other hand, Fast Track does (to the best of my knowledge) function with Ardour. Happy hunting my friend.

---

### Post by Native Dialect on 2010-04-17
I don't know if this has been suggested (I have not read the entire thread), or if it has been resolved, but I would love to see VSTi support in Ardour and LMMS. It bothers me that many popular DAWs do not make use of VSTs. There are many VSTs that are absolutely free. Perhaps not open source, which I know is the core philosophy of the Linux community, but it would still be nice for those of us who appreciate the higher quality of sampling that comes with a VST versus the typical MIDI instruments found in your standard DAW.

---

### Post by Scott L on 2010-04-18
> **deepredblood said:**
> does this support m-audio fasttrack pro?

[http://ubuntuforums.org/showthread.php?t=1444856&highlight=fast+track+pro](http://ubuntuforums.org/showthread.php?t=1444856&highlight=fast+track+pro)

This is a good thread in which AutoStatic helped someone with their Fast Track Pro.

You can search the forums for more threads.

---

### Post by melchez on 2010-04-20
5Dwm as an optional desktop. 
For studio work (graphics/audio) the 5Dwm has a nice clean area. One reason that help make IRIX the OS of choice back in the day for studio work.

---

### Post by kalisteboat on 2010-04-29
Hello and thanks for this fabulous hope you've been giving for musicians.

First of all, the only thing i need for Ubuntu Studio is stability.
I have tried all the previous versions up to 9.10, on 3 computers over these 3 last years and i never succeed to record one song.

So i ask for stability because i feel that the potential is enourmous but i've been forcing to use Sonar on windows to work.

I really don't understand why so many people are able to use Ubuntu studio as a regular audio system. I am not a complete beginer with linux system but i never manage to stabilise Jack.

I used a home made desktop computer, a Dell Inspirion laptop and now a ASUS F9SG laptop with 3go RAM and the result is always the same : crash of jack before 5mn of use (and most of the time with only Rosegarden or Hydrogen).
My audio interface : EDIROL UA700, EDIROL UR80, UA-25, PCR-1 (i used to work for this company from Roland Group)  ;-)

Do you think that the Edirol prod are not compatible enough ?

Why, why, why ?   :-k

Nevertheless, Thanks for your huge work.

---

### Post by AutoStatic on 2010-04-30
> **kalisteboat said:**
> Hello and thanks for this fabulous hope you've been giving for musicians.Hello kalisteboat and welcome!

> **kalisteboat said:**
> First of all, the only thing i need for Ubuntu Studio is stability.
I have tried all the previous versions up to 9.10, on 3 computers over these 3 last years and i never succeed to record one song.I've found 8.04, 9.04 and 9.10 to be rock solid. I'm currently using 9.10 and I can work for hours without any stability issues or xruns in JACK.

> **kalisteboat said:**
> I really don't understand why so many people are able to use Ubuntu studio as a regular audio system. I am not a complete beginer with linux system but i never manage to stabilise Jack.What stability issues do you have with JACK? Maybe it's an idea to start a separate topic to get JACK stable?

> **kalisteboat said:**
> Do you think that the Edirol prod are not compatible enough ?The UA-25 is a kick *** device, works like a charm in Ubuntu and I have never had any problems with it. Like I said, maybe it's best to create a new topic to figure out why JACK crashes.

---

### Post by mango42 on 2010-04-30
Hi kalisteboat,

I have had the opposite experience, especially with Karmic Koala! Dunno why this should be 'cos I'm really not that computerate and the learning curve would have been impossibly steep without the staunch and kindly support offered here. I've noticed from threads where people are dealing with issues surrounding Edirol units that they are usually solved fairly rapidly. 

I suppose I am not making great demands on an audio 4x4 + MIDI 8x8 system but I have never had a smoother experience, either tracking or mastering. Perhaps it has to do with your workflow procedures vis-a-vis the software you have chosen?

I've refined to the following, in this order:-

QJackCtl (careful attention to setup page works wonders ;)
Hydrogen
QTractor
Calf plugins
Ardour

but most of my system is outboard analog so mixing down often goes out to tape then back into Audacity for digital distribution, *after* closing down Jack ;-)

Now I finally have my AMD laptop back from repair, I can use 32bit UbuntuStudio just running USB MIDI and Audacity on a T43 Thinkpad and 64bit UbuntuStudio on the AMD doing the audio side + FX

And all for 'free'? Can't be bad... :guitar:

Perhaps if you were to ask specific questions in separate threads, one of the amazing 'bleeding edge' guys around here would be sure to help you out. Then there's the wealth of info on the various Wiki's etc.

Just yesterday, I wiped the last Windows partition off my systems. Relief!

---

### Post by psidrum on 2010-05-05
Like to see WineAsio , JackctlMMC in Ubuntu Studio

---

### Post by artyone on 2010-05-05
Howdy Folks, first post here after getting the Karmic Koala release in the mail and loading it to a Toshiba Tecra M5.

1st load I did kinda wrong, no broadband, but got a few things right so I reloaded again and with broadband and it went fine until I downloaded and added a .flv download function to Firefox then had some trouble doin' the nvidia drivers... 'puter started  locking up.

So 3rd install I did properly and then updated the KK then downloaded LL and loaded that then used the update manager to do the graphics accelerator and so far it seems stable... but I haven't tried any music programs yet.

One thing I really liked about KK was the buttons to move pages up and down wre both at the bottom so it was really easy with the laptop controls but with LL it's gone back to buttons at the top and bottom. But then again this is my first Linux ever so until I learn more I'm kinda doing the steep learning curve thing.

I want to be able to download youtube stuff and play with it in various editors so what are my best options. I'm going to bring my desktop over to openSuse and would probably do all downloading of odds and ends on that then convert it and put it on sticks for the laptop. Any suggestions?

---

