---
title: "Are there any musicians here"
date: 2011-10-11
forum: Ubuntu Studio
---

### Post by Stanley2011 on 2011-10-11
Hi,  I am new to this. Need help on getting my studio up and running. I'm have messed around with pro-audio for years install in churchs and run sound for my church, but just getting around to setting up a studio on my computer. 
Need help with what to use?
I have had no luck with Qjack,ctl is there any thing else to use?
Is there a Mixing board like a Yamaha ones etc?
But I all so what do do video / photo editing?

---

### Post by sgx on 2011-10-11
Hi, there are jackd and qjackctl guides with screenshots:

[https://help.ubuntu.com/community/HowToJACKConfiguration](https://help.ubuntu.com/community/HowToJACKConfiguration)

[https://help.ubuntu.com/community/HowToQjackCtlConnections](https://help.ubuntu.com/community/HowToQjackCtlConnections)

also search youtube for
ardour
hydrogen
zynaddsubfx
ubuntu studio

there are loads of good videos showing connections as first steps!

Harrison Mixbus is a full featured linux mixing console software

[http://www.harrisonconsoles.com/joomla/index.php?option=com_content&task=view&id=108&Itemid=42](http://www.harrisonconsoles.com/joomla/index.php?option=com_content&task=view&id=108&Itemid=42)

There is a demo, and manual to download.
Cheers

---

### Post by Stanley2011 on 2011-10-11
What is the easy sound card to set up with Ububntu?
M-auto has the Delta series and the is Blackmagic has some?

---

### Post by sgx on 2011-10-12
I have the maudio 24/96 pci, love it! Others with more needs love
delta 1010 or 1010LT, 66, and 44. snd_ice1712 is their kernel module,
envy24control is a special mixer for maudio (others also work).

Combined with an nvidia video card, and 2 gig or more ram, and you will sail smoothly on oceans of sound. Use reaper in wine, with wineasio for vsts. Rakarrack and guitarix for multi-fx, and lv2 calf, invada, and mda fx, and jamin or jackrack to host ladspa fx. Timemachine is a great simple recorder with jackd connections. Aqualung is a fine jackd music file player, to feed a backing track
to timemachine, while you overdub.

Ardour is an excellent multi-track audio recorder, and qtractor is
making progress as a full featured audio/midi sequencer.
Cheers

---

### Post by Stanley2011 on 2011-10-12
I read last night that Ubuntu studio 11.10 will be out in 3 day. They are saying that it will have the real time kernel installed, are is that just some thing they saying to get us to download it? 
I have fireware on my Asus motherboard do you thank that might be my poblem with Qjackctl? Realy do not want to use it for sound. I got a motherboard with fireware for video. It all so has USB 2.0 and 3.0. I have 4 gig of ram now. Will go to 16 gigs in time. I have and old school Nvidia GeForce 6200 TurboCache 256 MB 64-bit I will be updating the video card after the sound card. I have no onboard video card.








                    Life is short
!!!!!!!WHERE THE EASY BUTTON!!!!!!!

---

### Post by jejeman on 2011-10-12
There is no easy button. If you want to be free, if you want to use free software then learn. Free software can offer you just freedom nothing more.

Just haveing a firewire controler is no trouble for your os. While using it may give trouble for that you are using it for.

---

### Post by Stanley2011 on 2011-10-12
HI jejeman, Why would it give me  trouble for what I'm using it for? No new camcorder work with USB for live stream, yes I can use a webcam but if you are in a church a the camcorder is in the back you can,t get a close up of what is going on up front. If you have any good ideas let me know? I'm talking about small churches that don,t have a lot of money to spend on the high end  stuff. Now all of this is a try to see if I can get it up and running.

---

### Post by jejeman on 2011-10-12
> Why would it give me trouble for what I'm using it for?I didn't say that it WILL give you trouble, but it MAY give you trouble.
Firewire controlers per se are not trouble for OS.
> I have fireware on my Asus motherboard do you thank that might be my poblem with Qjackctl?No. 
Yes, if you are using firewire audio card.
> No new camcorder work with USB for live streamSome, has options to be webcams via usb. And thats one powerfull webcam.

I hope I cleared what I meant to say.

---

### Post by Stanley2011 on 2011-10-12
jejeman What camcorder has that and how much? I have been looking at this for 3 mouth the info I got was that USB was for Date transfer.

---

### Post by sgx on 2011-10-12
> **Stanley2011 said:**
> I read last night that Ubuntu studio 11.10 will be out in 3 day. They are saying that it will have the real time kernel installed, are is that just some thing they saying to get us to download it? 
I have fireware on my Asus motherboard do you thank that might be my poblem with Qjackctl? Realy do not want to use it for sound. I got a motherboard with fireware for video. It all so has USB 2.0 and 3.0. I have 4 gig of ram now. Will go to 16 gigs in time. I have and old school Nvidia GeForce 6200 TurboCache 256 MB 64-bit I will be updating the video card after the sound card. I have no onboard video card.

                    Life is short
!!!!!!!WHERE THE EASY BUTTON!!!!!!!
[https://help.ubuntu.com/community/Firewire](https://help.ubuntu.com/community/Firewire)

this doc will be some help, but each device should go in a search engine by name, with the system it is used on, with a keyword or two, like this

ubuntu firewire camcorder "Canon HF R21" 2011 -2009 -2008 -2007 -2006 -2005

having bygone years skipped in the search, gives more recent applicable results.
----------------------------------------------------------------------

As a rule, don't use new versions of any OS until the experts have had
a few months experience with it. Linux systems contain mostly beta
and alpha software releases. The elder Ubuntu 10.04 has a track record
for audio/video production, partly because the experts have learned
how to set it up and use it. (note, I am -->not<-- an expert!)

If you are helping folks with sundry systems, get familiar with
several linux setups, by using live CDs/dvds, and installs on
usbsticks, and external drives. I would suggest

Mint 11 ubuntu customized
Bodhi E17 based loosely on ubuntu/debian
AVLinux
Macpup and Puppy Studio/Studio4  puppy linux using ubuntu Lucid repos
pclinuxos  designed for stability, synaptic/rpm rolling release,
with lots of small customizations, and good remastering
And of course, ubuntu studio 10.04 and 8.04
Cheers

---

### Post by Stanley2011 on 2011-10-12
Hi, sgx I'am the sound tech at church. But the Computer record is new to me. We record the service on CD evey Sunday. Was thanking about doing DVD or live stream. been looking at that. Some of what I would like to do is for Church and some for myself.
Tanks for the help sometime it get frustrating trying to find the right word to look for something.
Yes you have to use a camcorder with i-link/fireware I know. So I figured i would try to learn it at home first.
So witch linux OS would be the best to be a all round workstation? Just getting use to ubunut 11.04
That would be good to do a live cd/dvd to help them get familiarize with Ubuntu, sorry had to go read what live CD was.

---

### Post by jejeman on 2011-10-12
> **Stanley2011 said:**
> jejeman What camcorder has that and how much? I have been looking at this for 3 mouth the info I got was that USB was for Date transfer.Well, I have to apologize to you. My old camcoder has this function, I really don't know about new ones. When I said I ment generaly. Sorry. 


> So witch linux OS would be the best to be a all round workstation? So general question, and general answer: ubuntu. ;)

---

### Post by Stanley2011 on 2011-10-12
jejeman, that camcorder is the only one out there they discontinued for drivers issue. You would thank they would have that worked out by now. so if you want a camcorder for live show you have to buy and old one.
on Ubuntu OS would like to find one that install out of box with qjackctl, realtime working I have had no luck with it. I have read and read untel my eyeball want to fall out LOL. I may just wait 2 more days for Ubuntu Studio 11.10 to see if that works for me.

---

### Post by Stanley2011 on 2011-10-12
Hi, is there any way to find or read the error messages from jack? 
How do you read the error messages in Jack?
If so how to find the fix?
Same for real time?

---

### Post by jejeman on 2011-10-12
If you use qjackctl to start jack you have message window. Open it.

As for the fix, it depends on what problem is.

---

### Post by Stanley2011 on 2011-10-12
will the erreor messages I get if I have real time check.
 p, li { white-space: pre-wrap; }  [COLOR=#999999]
[/COLOR]
[COLOR=#999999]14:32:26.753 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]14:32:26.754 Statistics reset.[/COLOR]
 [COLOR=#cccc99]14:32:26.762 ALSA connection change.[/COLOR]
 Cannot connect to server socket err = Connection refused
 Cannot connect to server socket
 jack server is not running or cannot be started
 [COLOR=#66cc99]14:32:26.770 ALSA connection graph change.[/COLOR]
 [COLOR=#999999]14:32:59.116 JACK is starting...[/COLOR]
 [COLOR=#990099]14:32:59.117 /usr/bin/jackd -t2000 -dalsa -r44100 -p256 -n3 -D -Chw:0 -Phw:0,1 -i2 -o2[/COLOR]
 Cannot connect to server socket err = Connection refused
 Cannot connect to server socket
 jack server is not running or cannot be started
 [COLOR=#999999]14:32:59.145 JACK was started with PID=3658.[/COLOR]
 no message buffer overruns
 no message buffer overruns
 jackdmp 1.9.7
 Copyright 2001-2005 Paul Davis and others.
 Copyright 2004-2010 Grame.
 jackdmp comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 JACK server starting in realtime mode with priority 10
 control device hw:0
 control device hw:0
 audio_reservation_init
 Acquire audio card Audio0
 creating alsa driver ... hw:0,1|hw:0|256|3|44100|2|2|nomon|swmeter|-|32bit
 control device hw:0
 Using ALSA driver HDA-Intel running on card 0 - HDA ATI SB at 0xfbcf4000 irq 16
 configuring for 44100Hz, period = 256 frames (5.8 ms), buffer = 3 periods
 ALSA: final selected sample format for capture: 32bit integer little-endian
 ALSA: use 3 periods for capture
 ALSA: final selected sample format for playback: 32bit integer little-endian
 ALSA: use 3 periods for playback
 [COLOR=#ff0000]14:33:06.178 Could not connect to JACK server as client. - Overall operation failed. - Server communication error. Please check the messages window for more info.[/COLOR]
 JackProcessSync::LockedTimedWait error usec = 5000000 err = Connection timed out
 Driver is not running
 Cannot create new client
 JackSocketClientChannel read fail
 Cannot open qjackctl client
 jackd: ../common/JackGraphManager.cpp:45: void Jack::JackGraphManager::AssertPort(jack_port_id_t): Assertion `port_index < fPortMax' failed.
 [COLOR=#999999]14:33:06.224 JACK was stopped successfully.[/COLOR]
 [COLOR=#cc3366]14:33:06.310 JACK has crashed.[/COLOR]

and here is the error if it is uncheck.

 p, li { white-space: pre-wrap; }  [COLOR=#990099]14:34:43.525 /usr/bin/jackd -r -t2000 -dalsa -r44100 -p256 -n3 -D -Chw:0 -Phw:0,1 -i2 -o2[/COLOR]
 [COLOR=#990099]Cannot connect to server socket err = Connection refused[/COLOR]
 [COLOR=#990099]Cannot connect to server socket[/COLOR]
 [COLOR=#990099]jack server is not running or cannot be started[/COLOR]
 [COLOR=#999999]14:34:43.536 JACK was started with PID=3671.[/COLOR]
 [COLOR=#999999]no message buffer overruns[/COLOR]
 [COLOR=#999999]no message buffer overruns[/COLOR]
 [COLOR=#999999]jackdmp 1.9.7[/COLOR]
 [COLOR=#999999]Copyright 2001-2005 Paul Davis and others.[/COLOR]
 [COLOR=#999999]Copyright 2004-2010 Grame.[/COLOR]
 [COLOR=#999999]jackdmp comes with ABSOLUTELY NO WARRANTY[/COLOR]
 [COLOR=#999999]This is free software, and you are welcome to redistribute it[/COLOR]
 [COLOR=#999999]under certain conditions; see the file COPYING for details[/COLOR]
 [COLOR=#999999]JACK server starting in non-realtime mode[/COLOR]
 [COLOR=#999999]control device hw:0[/COLOR]
 [COLOR=#999999]control device hw:0[/COLOR]
 [COLOR=#999999]audio_reservation_init[/COLOR]
 [COLOR=#999999]Acquire audio card Audio0[/COLOR]
 [COLOR=#999999]creating alsa driver ... hw:0,1|hw:0|256|3|44100|2|2|nomon|swmeter|-|32bit[/COLOR]
 [COLOR=#999999]control device hw:0[/COLOR]
 [COLOR=#999999]Using ALSA driver HDA-Intel running on card 0 - HDA ATI SB at 0xfbcf4000 irq 16[/COLOR]
 [COLOR=#999999]configuring for 44100Hz, period = 256 frames (5.8 ms), buffer = 3 periods[/COLOR]
 [COLOR=#999999]ALSA: final selected sample format for capture: 32bit integer little-endian[/COLOR]
 [COLOR=#999999]ALSA: use 3 periods for capture[/COLOR]
 [COLOR=#999999]ALSA: final selected sample format for playback: 32bit integer little-endian[/COLOR]
 [COLOR=#999999]ALSA: use 3 periods for playback[/COLOR]
 [COLOR=#ff0000]14:34:50.549 Could not connect to JACK server as client. - Overall operation failed. - Server communication error. Please check the messages window for more info.[/COLOR]
 [COLOR=#ff0000]JackProcessSync::LockedTimedWait error usec = 5000000 err = Connection timed out[/COLOR]
 [COLOR=#ff0000]Driver is not running[/COLOR]
 [COLOR=#ff0000]Cannot create new client[/COLOR]
 [COLOR=#ff0000]JackSocketClientChannel read fail[/COLOR]
 [COLOR=#ff0000]Cannot open qjackctl client[/COLOR]
 [COLOR=#ff0000]jackd: ../common/JackGraphManager.cpp:45: void Jack::JackGraphManager::AssertPort(jack_port_id_t): Assertion `port_index < fPortMax' failed.[/COLOR]
 [COLOR=#999999]14:34:50.630 JACK was stopped successfully.[/COLOR]
 [COLOR=#cc3366]14:34:50.645 JACK has crashed.[/COLOR]

Now what should I be looking for to fix it?
Is the error in red?

---

### Post by sgx on 2011-10-12
> **Stanley2011 said:**
> Hi, is there any way to find or read the error messages from jack? 
How do you read the error messages in Jack?
If so how to find the fix?
Same for real time?
There are 'messages' and 'status' windows in qjackctl when you click their buttons, to give you info. You can also start jackd from a command
Type the contents of the .jackdrc textfile in your /home/username folder, (it is the settings file saved by qjackctl)
press enter, and it starts jackd. Check that terminal window
during your sessions for system messages

Most current linux versions share the same apps, so kernels,
security defaults, and available window-managers may be the biggest differences. Some distros focus on the newest software, while others the most stable user experience. Different kernels may have or lack
a kernel module or hardware detection for the device you need to use.
But those can often be loaded later. As can other window-managers and
eyecandy. So having 4 or 5 linux in your arsenal is good luck.
ubuntu studio
mint 11
bodhi 1.2
puppy studio 3.3
pclinuxos full monte
fedora ccrma
open-suse
avlinux
remixOS

When Vista was (dreadfully)new, xp was fairly stable. When the newest ubuntu is released, the versions a few steps back are likely more stable. But with audio and video software, often the newest release has the most bugfixes, unless the release is mainly for new features. I get audio apps from 'debian unstable' repository, and yet they are very stable. ;)

---

### Post by lisati on 2011-10-12
Different things work for different people: I generally record an occasion on one or more cameras, then transfer to the computer when I get home. This has the advantages of not having too much gear to carry around, and also letting me focus on the actual recording.

---

### Post by Stanley2011 on 2011-10-12
Hi sgx so Ubuntu is at the top of you list of Linux OS, so I am assuming it is the best out of all of them?
Now I have read that the newer or Ubuntu Studio 11.04 is faster then the older ones?
As for eyecandy I don't care for that as much as I do for smooth, fast and works out of the box.
As for Ubuntu Studio there are 5 options to choose from. Now I have seen same say Ubuntu Studio 4 is that the option are the OS release?

---

### Post by Stanley2011 on 2011-10-12
> **lisati said:**
> Different things work for different people: I generally record an occasion on one or more cameras, then transfer to the computer when I get home. This has the advantages of not having too much gear to carry around, and also letting me focus on the actual recording.




Hi lisati That works if you are doing on the spot news etc. But for recording you church or etc to be on at the time it start you need to be able to stream live.
Let say I want to do a live stream of a radio show with video and i have a live band come from the area a webcam might work but that is a sensitive issue (webcam/camcorder) but let say its a high school football game will a webcam will not work. So fireware and minDV camcorder is the low cast option.

---

### Post by sgx on 2011-10-12
> **Stanley2011 said:**
> Hi, sgx I'am the sound tech at church. But the Computer record is new to me. We record the service on CD evey Sunday. Was thanking about doing DVD or live stream. been looking at that. Some of what I would like to do is for Church and some for myself.
Tanks for the help sometime it get frustrating trying to find the right word to look for something.
Yes you have to use a camcorder with i-link/fireware I know. So I figured i would try to learn it at home first.
So witch linux OS would be the best to be a all round workstation? Just getting use to ubunut 11.04
That would be good to do a live cd/dvd to help them get familiarize with Ubuntu, sorry had to go read what live CD was. I prefer
small empty distros, and add only the few apps I actually use.
You could start with 400 meg bodhi linux, and just add video apps
like openshot, lives, kino, avidemux, cinelerra, vlc, mplayer,
mencoder, ffmpeg, k3b, or even 170 meg macpup, the fewer apps,
the fewer bugs. But ubuntu Mint 11, and AVLinux are good for folks
 needing to determine what works, and then choose their favorites.
Later, you can do a custom 'light' version, if there should be
a need.
Cheers

---

### Post by Stanley2011 on 2011-10-12
Hi sgx, Let me ask this I would like to get on the Internet, offices, recorder live sound/ video, and sound, video and photo editing can I do all that on one computer are will I have to build a network?

---

### Post by sgx on 2011-10-12
> **Stanley2011 said:**
> Hi sgx so Ubuntu is at the top of you list of Linux OS, so I am assuming it is the best out of all of them?
Now I have read that the newer or Ubuntu Studio 11.04 is faster then the older ones?
As for eyecandy I don't care for that as much as I do for smooth, fast and works out of the box.
As for Ubuntu Studio there are 5 options to choose from. Now I have seen same say Ubuntu Studio 4 is that the option are the OS release?
The order is not too relevant, since what works for me, may not for thee, but I try to be a welcome guest, so mention a ubuntu first. 

I also won't make fun of my friends wife,
when sitting at her dinner table eating a drumstick she cooked!

Studio4 is an inexpensive audio/video puppy linux that is sold
ready to boot on a usbstick for $50. The previous free release,
Puppy Studio 3.3 is here,

[http://www.murga-linux.com/puppy/viewtopic.php?t=72402](http://www.murga-linux.com/puppy/viewtopic.php?t=72402)

and very good in actual use, from a cd or usbstick.
Studio4 is here:

[http://www.getstudio4.com/screenshots.html](http://www.getstudio4.com/screenshots.html)

:popcorn:

---

### Post by Stanley2011 on 2011-10-12
Studio4 is an inexpensive audio/video puppy linux that is sold
ready to boot on a usbstick for $50. The previous free release,
Puppy Studio 3.3 is here,

[http://www.murga-linux.com/puppy/viewtopic.php?t=72402](http://www.murga-linux.com/puppy/viewtopic.php?t=72402)

and very good in actual use, from a cd or usbstick.
Studio4 is here:

[http://www.getstudio4.com/screenshots.html](http://www.getstudio4.com/screenshots.html)

:popcorn:[/QUOTE]


Ok I guess if I want the work done for me get the studio4 but ever thing is free will all most ever thing andour they wnat some money for it.
when installing ubuntu studio 11.04 witch option to choose for audio recording the video I can get later
witch option will set up Qjack to work?

---

### Post by sgx on 2011-10-12
[http://en.wikipedia.org/wiki/Qjackctl](http://en.wikipedia.org/wiki/Qjackctl)

lots of topics to read, with pics and how-2

The jackd and qjackctl links are crucial for using linux audio. qjackctl is the gui for jackd, which is used to connect your software and hardware, in the order you choose.

There are good apps for most software categories, but to compete
with old established and well funded mac/windows software giants,
is no easy task. pclinuxos full monte edition, is a good choice
for all in one collections, with stability and usability as high
priority.

Studio4 is optimized and well configured, testing/using Studio 3.3
will give you an idea. Time is money, but is always running out.
Some marriages are sacrificed because people insist on the long, slow, and hard, but 'free' way, wasting precious hours that would have been better invested loving the wife and children. The true
price arrives with the divorce papers. $50 is cheap.

---

### Post by Stanley2011 on 2011-10-12
Sgx you right there. It time to stop wasting time and get something done. I made my choose I'm gone try AVlinux. thanks

---

### Post by Stanley2011 on 2011-10-12
on windows you need 64bit to get ram higher then 4gig. On Linux can you get more ram on 32bit?

---

### Post by sgx on 2011-10-12
> **Stanley2011 said:**
> on windows you need 64bit to get ram higher then 4gig. On Linux can you get more ram on 32bit?

Hi, you need a pae enabled kernel, many of them now are.
Usually pae is in the title, if its enabled.

[https://help.ubuntu.com/community/EnablingPAE](https://help.ubuntu.com/community/EnablingPAE)

Cheers

---

### Post by Stanley2011 on 2011-10-12
> **sgx said:**
> Hi, you need a pae enabled kernel, many of them now are.
Usually pae is in the title, if its enabled.

[https://help.ubuntu.com/community/EnablingPAE](https://help.ubuntu.com/community/EnablingPAE)

Cheers

Nice that save a lot of headaches trying to find hardware and software for 64bit systems.

---

### Post by Stanley2011 on 2011-10-12
Can you use PAE on all Linux systems?

---

### Post by jejeman on 2011-10-12
> Can you use PAE on all Linux systems? First, let me correct you on terminology. The operating system is called gnu/linux. And Ubuntu, AvLinux, Puppy Studio etc. are distributions of this system. They are also called Linux distributions, not systems.

So your question is: "Can you use PAE on all Linux distributions?"
Yes, if you can find one for that distribution, or compaile it your self.

---

### Post by Stanley2011 on 2011-10-12
jejeman Sorry but it seems that some are sensitive to Linux  distribution. I'm new so take it easy on me. I have used windows for 11 years. so give me time to learn the lingo. 
sgx AVlinux is not for me, It is very slow. the window opens very slowly not like Ubuntu.

---

### Post by MBybee on 2011-10-12
I use Ubuntu Studio 64bit - it works extremely well for the most part.

There's not really a *great* set of audio software for Linux, but there is some. Depends on what precisely you're doing, and how the tools work for you.


(I gave up on it myself - it remains one of the only two things I use Windows for).

Don't worry too much about terminology, the majority of the people who use Linux really couldn't care less. The rest will be all too happy to correct you.

---

### Post by Stanley2011 on 2011-10-12
> **MBybee said:**
> I use Ubuntu Studio 64bit - it works extremely well for the most part.

There's not really a *great* set of audio software for Linux, but there is some. Depends on what precisely you're doing, and how the tools work for you.


(I gave up on it myself - it remains one of the only two things I use Windows for).

Don't worry too much about terminology, the majority of the people who use Linux really couldn't care less. The rest will be all too happy to correct you.
  
Thanks MBybee. I thank I'll wait for Ubuntu Studio 11.10 to come out to start trying to use the audio software. Qjackctl is the big problem can't get it up and running. If I can't oh well. But I am starting to like Ubuntu.
Today I turned on both of my computers, one with windows vista and one with Ubuntu guess which one was ready to go? Yes Ubuntu!!!!!!

---

### Post by sgx on 2011-10-12
Stanlee, is qjackctl not installed? you can install using this command
when online

sudo apt-get install qjackctl

If it needs helper apps, you will be asked if you want to proceed.
Or use the     sudo synaptic   to open the apt-get gui. Press the synaptic 
reload button, to download the latest apps first.

To get it up and running, launch it from an audio/multimedia/sound
menu, or type    qjackctl  in a terminal window. It is usually
preconfigured to launch jackd automatically.

When it opens, refer to the pics at the links. Put a steady sound source on your soundcard line-in so you hear when the right connection is made.
Or use zynaddsubfx, as in the example in the wiki link.

Press the connect button on the lower left of the gui
In the audio and alsa tabs, click an object to connect in both the left and right sides,
then press the connect button on this panel
(not the one on the main gui). 

physical midi keyboard cable(s)or usb cable to computer
qjackctl chosen virtual midi synthesizer input to system capture
qjackctl chosen virtual midi synthesizer output to system playback

If AVLinux is used from a live cd/dvd, it will be slower than
a standard hard-disk install, as the drive must spin up sometimes,
but still good to try so many softwares. Hydrogen drum machine, rakarrack fx, zynaddsubfx/yoshimi
and phasex synthesizers, all connect in qjackctl.

Probably lots of video apps can load video clips from your hardisk,
to test their video editing or fx, or import
and find the raw video from a cabled camcorder.
Cheers

---

### Post by Stanley2011 on 2011-10-12
sgx, qjack is install just want start. Keep getting the same two error messages.
So don't know what to do I have followed evey thing I have find on how to install.
Right now I am using Ubuntu 11.04 64bit not Ubuntu Studio 11.04 64bit. just been waiting to see if I can get up on here.
Now I don't thank I have Realtime installed. I run some command and it said fail not find.
Do I need to uninstall Qjack and follow the command you gave?
OH ok need to play with AVlinux some more. but jack did not work there is that because it a live cd/dvd?
As for videos I have none on ubuntu as of now whiting to get it up and run. and on it now one thing I did see in limits.conf file is this.#<domain>      <type>  <item>         <value>
#

#*               soft    core            0
#root            hard    core            100000
#*               hard    rss             10000
#@student        hard    nproc           20
#@faculty        soft    nproc           20
#@faculty        hard    nproc           50
#ftp             hard    nproc           0
#ftp             -       chroot          /ftp
#@student        -       maxlogins       4

---

### Post by sgx on 2011-10-12
add this after the last line of /etc/security/limits.conf and save the file.

@audio          -       rtprio           99
@audio          -       nice             -15
@audio          -       memlock          unlimited
# End of file


keep the spacing. Edit: this forum post is not keeping the spacing,
use the spacing in your computers text file!

You will need to start
a text editor like
sudo gedit
sudo kwrite
use copy/paste

Reboot, and in a terminal try this basic command

jackd -d alsa -r 44100

something like this should be at the end the terminal output:

ALSA: final selected sample format for capture: 32bit integer little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 32bit integer little-endian
ALSA: use 2 periods for playback

Then start qjackctl. If it still fails,

Computer soundcard is? Videocard is? Motherboard chipset is?
Output of aplay -l is?
Output of lsmod is?
Cheers

---

### Post by lisati on 2011-10-12
> **Stanley2011 said:**
> Hi lisati That works if you are doing on the spot news etc. But for recording you church or etc to be on at the time it start you need to be able to stream live.
Let say I want to do a live stream of a radio show with video and i have a live band come from the area a webcam might work but that is a sensitive issue (webcam/camcorder) but let say its a high school football game will a webcam will not work. So fireware and minDV camcorder is the low cast option.

I thought we were talking about producing a recording, and didn't realise we were talking about a live stream. [s]Most[/s] All of the stuff I've done is for later viewing at the leisure/pleasure of the participants, and doesn't require fancy mixing and/or recording on site. :D I'm wondering if a commercially produced mixer of some description is an option.

---

### Post by Stanley2011 on 2011-10-12
Ok is it [COLOR=Red]/etc/security/limits.conf [COLOR=Black]or[/COLOR][/COLOR] is it [COLOR=Black][COLOR=Red]sudo/etc/security/limits.conf [/COLOR]or is it[/COLOR][COLOR=Red]/etc/security/limits.conf and save the file [COLOR=Black]now if not the last one how do you save the file?
Now for the limits.conf I have know how it got that way the @student,@faculiy no clue I tougth I set the user gourp with a different name?
[/COLOR]#*               soft    core            0
#root            hard    core            100000
#*               hard    rss             10000
#@student        hard    nproc           20
#@faculty        soft    nproc           20
#@faculty        hard    nproc           50
#ftp             hard    nproc           0
#ftp             -       chroot          /ftp
#@student        -       maxlogins       4     [/COLOR]

---

### Post by Stanley2011 on 2011-10-12
> **lisati said:**
> I thought we were talking about producing a recording, and didn't realise we were talking about a live stream. [s]Most[/s] All of the stuff I've done is for later viewing at the leisure/pleasure of the participants, and doesn't require fancy mixing and/or recording on site. :D I'm wondering if a commercially produced mixer of some description is an option.
Yes in time I will get A mixing board like a  Behringer Xenyx x1204UBS if it will work on linux. but I thank if I had total control of my computer would be good. But right now we are talking about live record I'm all so a Bass player/Sound tech. I ask the question can I do all of this on one machine. and someone posted about camcorder and that how we got on that subject. I would like to do both prerecording and live. All advice is good.

---

### Post by sgx on 2011-10-12
> **Stanley2011 said:**
> Ok is it [COLOR=Red]/etc/security/limits.conf [COLOR=Black]or[/COLOR][/COLOR] is it [COLOR=Black][COLOR=Red]sudo/etc/security/limits.conf [/COLOR]or is it[/COLOR][COLOR=Red]/etc/security/limits.conf and save the file [COLOR=Black]now if not the last one how do you save the file?
Now for the limits.conf I have know how it got that way the @student,@faculiy no clue I tougth I set the user gourp with a different name?
[/COLOR]#*               soft    core            0
#root            hard    core            100000
#*               hard    rss             10000
#@student        hard    nproc           20
#@faculty        soft    nproc           20
#@faculty        hard    nproc           50
#ftp             hard    nproc           0
#ftp             -       chroot          /ftp
#@student        -       maxlogins       4     [/COLOR]
sudo is a command that will get you a root prompt, which is #
The user propmpt is $

Type in your password when it is requested. So, to open the gedit text editor as the root user
sudo gedit
To open gedit including a specific textfile, add the full path to the file

sudo gedit /etc/security/limits.conf

Text files in your /home/username folder can be opened without
sudo root privileges. Like

gedit /home/stanlee/.jackdrc
Cheers
remember to maintain the existing spacing columns in
limits.conf

---

### Post by Stanley2011 on 2011-10-12
Ok sgx the file sudo gedit/etc/security/limits.conf command not found
Now what?

---

### Post by sgx on 2011-10-12
> **Stanley2011 said:**
> Ok sgx the file sudo gedit/etc/security/limits.conf command not found
Now what?

sudo gedit/etc/security/limits.conf command not found
sudo gedit /etc/security/limits.conf command not found

just a space is needed to separate gedit, from the path :)

Cheers

[https://help.ubuntu.com/community/Ubuntu%20Studio%20Upgrade%20from%20Ubuntu](https://help.ubuntu.com/community/Ubuntu%20Studio%20Upgrade%20from%20Ubuntu)

prefer the info here, slightly different than mine. Scroll down for limits.conf

---

