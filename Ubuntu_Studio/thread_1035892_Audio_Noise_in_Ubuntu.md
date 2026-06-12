---
title: "Audio Noise in Ubuntu"
date: 2009-01-10
forum: Ubuntu Studio
---

### Post by Fedora314 on 2009-01-10
The bad kind of noise, that is.

I've been running 8.04 since it's release, and Ubuntu in general for about a year on my ThinkPad T60. Only now have I noticed that there are a myriad of audio problems that don't occur in Windows.

The first, and most critical is lots of noise present while capturing audio. I've eliminated all the usual issues - got myself a good microphone, silenced ambient noise and the like - but still, an annoying hiss appears in all my recordings. I thought it was a bad sound card but (annoyingly) Audacity records perfect audio in Windows.

So, this leads me to believe that the issue is with the Linux software running my sound card (an Analog Devices AD1981). I've switched all the switches and slid all the sliders in my volume control. I've tried isolating the problem by muting various components. As long as the capture channels are active, there is noise in the signal.

It was during this process that I came to notice a constant hiss coming through my speakers/headphones that is only quieted by muting the Master or PCM channels. If this can be solved along the way, great - otherwise, the capture problems are most important.

Since some people will skip all the paragraphs above, here are the main questions:

1) Has anyone else noticed a hiss, buzz, or noise while recording audio with Audacity?

2) Does the problem lie with Linux support of the AD1981 sound card? If so, where should I go to report this problem?

3) If anyone could point me to an explanation of how sound works in Linux (generally) that would be greatly appreciated. I've been using Ubuntu for awhile, and I've never run into anything quite so confusing before.

Cheers,
Jeremy

---

### Post by Cracauer on 2009-01-11
Do you know whether it is noise-free in Windoze?

Try a different PCI slot. But if that doesn't help only a better card will. I had to do that [looks at 6 high stack of recent soundcards]

---

### Post by tk03759 on 2009-07-06
To any future reader of this post, give this a try. I had the same problem on my laptop and this worked for me. I think it may have something to do with the fact that my laptop has two microphones preinstalled, a left and a right. I was not using those microphones when I tried this. I was using an externally attached mic to a usb port.

Open up Sound Recorder, which I believe is installed out of box. If not, I know it is in Add/Remove.

Now, go to File, and click Open Volume Control. In the Device drop down box, find the input you are using. If you're not sure which it is, pick one that seems likely, make sure it is not muted, and then click Close.

In Sound Recorder, click Record and yell into your mic a little. Watch the level bar at the bottom. If it's moving you may have found your input. If it isn't, click stop. Double check by clicking Play that no sound was recorded, and then head back into Open Volume Control to try another input.

If you found the input that is working, go to Open Volume Control, and unlink the Left and Right audio by clicking the link icon underneath the slider. Now move the right or the left volume all the way down. Then go back and try recording again and playback your sound. Keep trying until the buzz is reduced. You may have to try lowering the volume on different Devices left or right channels to get it to (generally) go away.

On my system, after fooling with this, I got the buzz reduced to completely minimal by choosing the Device "Capture: HDA NVidia - CONEXANT Analog (PulseAudio Mixer)" and turning the left channel all the way down, and the right channel down to about 90% volume.

I have no idea why this worked, but if it helps somebody then yay, or maybe it'll help someone more knowledgeable than me figure out what the actual problem is.

Good luck.

---

### Post by igorzwx on 2009-07-06
Hi Fedora!

I have the same problem on my ThinkPad R40
Noise: 50Hz + odd overtones of 50Hz

First of all, record on battery.
Try offline too.

On Dell notebook offline+battery and still enough noise

The reason of troubles seems to be PulseAudio

One Fedora user told me this:
" I don't think it is a 'bug' in pulse, it is the fact that 
pulse is a sound server and runs at a specific frame rate.  It has to 
move all sound streams to that frame rate in order to play through the 
sound device.  It uses on the fly rate conversion, and this introduces 
artifacts into the sound. "

On one box, I have already removed both ALSA and Pulse and install OSS4.
This might be a solution.
I am going to try to install FreeBSD with OSS4 in dual boot there too.
But FreeBSD is not Ubuntu, you cannot install it to any box you want.

we can disscuss this here:
[http://ubuntuforums.org/showthread.php?t=1202857](http://ubuntuforums.org/showthread.php?t=1202857)

---

### Post by jumbofishmeat on 2009-07-06
I've had that same noise, which is a sort of hiss at around 50Hz. I have always attributed it to my sound card, as i do not have a very impressive system on my computer. i think there must be some sort of electronic interference in there.

also, @igorzwx, the only time having the charger attached messes with the sound is when you are hooked up to a seperate a/c system, thus causing a ground loop. when you are confined to usb/internal microphones you don't get the ground loop, thus not affecting the recorded sound.

I believe it is a hardware issue, and the only thing i've done to solve it is to take it out using the equalizer. It works, and doesn't noticibly affect the recording, but it was tough reducing the specific bands. The only solution i found was to record things using my MicroTrack. It is isolated, and runs off of flash memory. It was also cheaper than getting a new sound chip. Anyways, i would be glad to hear if anyone else has an actual fix.

---

### Post by igorzwx on 2009-07-06
Hi all!

What works well for me is this:

1. on battery

2. iMic USB

3. online or offline - it does not matter

On the old box for experiments, I removed ALSA and Pulse, installed OSS4 instead.
Fantastic sound.
Skype works much better than with Pulse.
But USB audio devices are not supported...
OSS4 deserves a try.

---

### Post by igorzwx on 2009-07-06
on battery! Without AC, of course.

DSL modem can also supply 50Hz (on Dell notebooks)

---

### Post by igorzwx on 2009-07-06
I do not believe that it is hardware,
because I had not such problems with Ubuntu 6.10

I installed Ubuntu 6.10 in 2006, and used untill 2009.04
Then I changed to Ubuntu 9.04.
And the problems began.

---

### Post by tgalati4 on 2009-07-06
pulseaudio would also explain the difference between audacity recordings between linux and Windows.  Presumably, Windows uses DirectX to address the sound hardware directly (similar to OSS4) so that you get a cleaner signal at the sacrifice of sound server patching and individual application volume control.

You could write a script to turn off pulseaudio during Audacity sessions and then turn back on afterwards for general desktop use.

Or blast pulseaudio completely from your system.

Try running Dynebolic Live CD.  That has a low-overhead, real-time kernel that is helpful for recording sessions.

---

### Post by igorzwx on 2009-07-06
What script?

sudo killall pulseaudio

And you can record from the internal sound card.

Do you want to have the evil back?

Plug in an USB audio device, and pulse is with you again.

You cannot record from USB thing without pulse.
You can kill it how want, it does not help.

---

### Post by igorzwx on 2009-07-06
Just installed FreBSD in dual boot with Ubuntu on my old box (of 2001),
which I use for experiments.
Firefox is incredibly fast.

---

### Post by tgalati4 on 2009-07-07
You will have to search the forums for scripts to turn off pulseaudio with audacity.

Your usb hardware is probably supported under alsa.

Freebsd is solid.  A different, yet familiar, experience.

---

### Post by igorzwx on 2009-07-07
I am testing Ubuntu 9.04 with OSS4 on my old box
for experiments.
The sound seems to be fixed.
Pulse is completely removed. ALSA too.
But general performance is not impressive.
Ubuntu 9.04 seems to be not a good system at all.
Ubuntu 6.10 was much better.

---

### Post by networm1230 on 2009-07-07
make shore you have all G streamer plugin's. 

look at (plug and play) in your Bios. 

you may wont to use you motherboards sound port or sound card.

---

### Post by igorzwx on 2009-07-07
What plugins?
What soundcard?

You see, I am running Ubuntu 9.04 with Pulse and ALSA on IBM notebook.
Some weeks ago, if I would try noise removal in Audacity with a 5 second wave,
I would get "logout" and black screen.
Then I should login once more.
I am only busy fixing the system now.
It is not only Pulse, everything is...

On another box with Ubuntu 9.04 and OSS4,
I can at least hear a normal sound without the so-called "artefacts".

---

### Post by igorzwx on 2009-07-07
And to connect my old box to the net,
I had to hack /boot/grub/menu.lst
using some old howto of 2005.
It took some days to dig it out.

The DreamLinux, by the way, has the same illness.

---

### Post by networm1230 on 2009-07-07
G streamer are plugins for sound and video [http://gstreamer.freedesktop.org/](http://gstreamer.freedesktop.org/)

are you can find theme in the repository,Add/remove

install all availability Gstreamer plugins.

go to your sound setting and test all. you may wont to use your motherboards sound chip set

---

### Post by igorzwx on 2009-07-08
Hi Neworm!

Let us try your solution, but I may need your advice.
First of all, I presume that all Gstreamer plugins one may need
are already installed from the very beginning.
I have a lot of such things installed.

On the box with Ubuntu 9.04 with ALSA and Pulse, I installed a lot
Gstreamer plugins (+pulse and alsa), except for very exotic ones
and those for OSS4.
On the box with Ubuntu 9.04 with OSS4, I have the streamer plugs for OSS4,
and those for ALSA and Pulse are, of course, removed.

Can you tell me exactly, which plug is missing?

By the way, I have already installed PC-BSD in dual boot with Ubuntu on the
old box for experiments.
However, it seems that PC-BSD is too heavy for the old box,
and it seems that PC-BSD has much more Pulse than Ubuntu.
The sound produced by PC-BSD om my old box is increadibly bad.

In comparison with PC-BSD, Ubuntu 9.04 looks great!

"you may wont to use your motherboards sound chip set".
This does not help. 
What helps for IMB notebook is battery without AC.
And Dell notebook should also be offline (but still enough noise).

I will try to find that magic script
"to turn off pulseaudio with audacity."

Best,
Igor

---

### Post by igorzwx on 2009-07-08
I am gooling the script for Audacity now

Google told me this:
 [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/275998](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/275998)

[LIST=1]
[*]**[Bug #275998 in *pulseaudio* (*Ubuntu*): “internal mic capture very low [B]...**]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/275998")[/B]

 Recording worked in Hardy and works in intrepid if I *turn off pulseaudio* (which is not **....** Internal Mic does not work even for "Sound Recorder" and "*Audacity*". **....** running - the default /etc/init.d/*pulseaudio* startup *script* fails to do **...** From what I've read on this *forum* and elsewhere, it seems that most users **...**
[https://bugs.launchpad.net/](https://bugs.launchpad.net/)**ubuntu**/+.../**pulseaudio**/+bug/275998 - [Cached]("http://209.85.135.132/search?q=cache:meh_Sdq2yKEJ:https://bugs.launchpad.net/ubuntu/%2Bsource/pulseaudio/%2Bbug/275998+Ubuntu+forum+scripts+to+turn+off+pulseaudio+with+audacity&cd=4&hl=en&ct=clnk") - [Similar]("http://www.google.com/search?hl=en&q=related:https://bugs.launchpad.net/ubuntu/%2Bsource/pulseaudio/%2Bbug/275998")
[/LIST]

---

### Post by igorzwx on 2009-07-08
Tgalati4! Many thanks for the hint!

This might be an ideal solution: 
[http://www.pulseaudio.org/wiki/PerfectSetup#Audacity](http://www.pulseaudio.org/wiki/PerfectSetup#Audacity)

Using pasuspender to momentarily suspend pulseaudio is another way to 
use Audacity. 

pasuspender -- audacity <argument> 

Actually, the most affected applications seem to be Skype and Ekiga. 

I hope this works. 


man pasuspender

NAME 
       pasuspender - Temporarily suspend PulseAudio 

SYNOPSIS 
       pasuspender [options] -- PROGRAM [ARGUMENTS ...] 

       pasuspender --help 

       pasuspender --version 

DESCRIPTION 
       pasuspender is a tool that can be used to tell a local PulseAudio sound 
       server to temporarily suspend access to the  audio  devices,  to  allow 
       other  applications  access  them  directly.  pasuspender  will suspend 
       access to the audio devices, fork a child process, and when  the  child 
       process terminates, resume access again. 

       Make sure to include -- in your pasuspender command line before passing 
       the subprocess command line (as  shown  above).  Otherwise  pasuspender 
       itself  might end up interpreting the command line switches and options 
       you intended to pass to the subprocess. 
 Manual page pasuspender(1) line 1

---

### Post by AFarris01 on 2009-07-10
I just wanted to say that I*get absolutely no artifacts/odd noise at all when recording through sound recorder, or audacity, using ubuntu 9.04, 32 & 64 bit, on a laptop or desktop.  It may just be an issue with support for some hardware...

just my 2 cents

---

### Post by igorzwx on 2009-07-10
Drivers might be a problem too.
But in this case the processor power is the most likely problem.

It seems that Skype and Ekiga are affected by PulseAudio more than 
anything else. 
We tested Skype and Ekiga with my friend in Ukraine. 
If you call from the box with Pulse from Germany to Ukraine,  
it is impossible to communicate. 
If you call from the box with OSS4, quality is fantastic.
Much better than when you call inside a German town by ordinary telephone.

Have you tried Skype or Ekiga with Pulse?

I do not play games, but it was reported something similar to what
I had with Skype and Ekiga:
[http://insanecoding.blogspot.com/2009/06/state-of-sound-in-linux-not-so-sorry.html](http://insanecoding.blogspot.com/2009/06/state-of-sound-in-linux-not-so-sorry.html)

But the most terrible problem is security.
Ukrainian kids armed with Frenzy LiveCD can hack your box during 10 minutes
(English documentation is also available).

I have already removed the evil from all my boxes.

---

### Post by igorzwx on 2009-07-11
Just an example:
[http://arstechnica.com/apple/news/2009/03/safari-successfully-exploited-in-seconds-in-pwn2own-contest.ars](http://arstechnica.com/apple/news/2009/03/safari-successfully-exploited-in-seconds-in-pwn2own-contest.ars)
           **Safari successfully exploited in seconds in Pwn2Own contest**

           As security researcher Charlie Miller predicted, he successfully gained control of a MacBook through an exploit of the Safari browser for the second year in a row at CanSecWest. Pwn2Own contestants also successfully hacked IE8 and FireFox 3 shortly thereafter.
           By            [Chris Foresman]("http://arstechnica.com/authors/chris-foresman/")           | Last updated March 19, 2009  1:01 PM CT
         
 
[http://cansecwest.com/](http://cansecwest.com/)

---

### Post by igorzwx on 2009-07-27
PulseAudio secutity problem:
[http://www.theregister.co.uk/2009/07/17/linux_kernel_exploit/](http://www.theregister.co.uk/2009/07/17/linux_kernel_exploit/)
**[Clever attack exploits fully-patched *Linux kernel* • The Register]("http://www.theregister.co.uk/2009/07/17/linux_kernel_exploit/")**

The exploit code was released Friday by *Brad Spengler* of grsecurity, **...** "Why is it that whenever there is an exploitable *vulnerability* in *Linux*, **...**
[www.theregister.co.uk/2009/07/17/](www.theregister.co.uk/2009/07/17/)**linux**_**kernel**_exploit/ - [Cached]("http://209.85.135.132/search?q=cache:wZBH3pYFhz0J:www.theregister.co.uk/2009/07/17/linux_kernel_exploit/+vulnerability+linux+kernel+PulseAudio+Brad+Spengler&cd=2&hl=en&ct=clnk") - [Similar]("http://www.google.com/search?hl=en&q=related:www.theregister.co.uk/2009/07/17/linux_kernel_exploit/")

QUOTE:
The "NULL pointer dereference" bug has been confirmed in versions 2.6.30 and 2.6.30.1 of the Linux kernel, which Spengler said has been incorporated into only one vendor build: version 5 of Red Hat Enterprise Linux that's used in test environments. The exploit works only when a security extension knows as SELinux, or Security-Enhanced Linux, is enabled. Conversely, it also works when audio software known as PulseAudio is installed.
End of QUOTE

---

### Post by Stochastic on 2009-07-27
igorzwx, you seem to be having a conversation with yourself in this thread - and it's going WAY off topic.  Please reign yourself in before moderation does it for you.  Thanks.

---

### Post by igorzwx on 2009-07-28
You are absolutely right.
For example, I asked a security question on Security
forum some weeks ago (more exactly, it was moved from here).
Nobody is going to answer.
So, do you think better not to ask questions at all?

---

### Post by igorzwx on 2009-07-28
And, by the way, it is everywhere now.
Try to ask economists why they are making this or that reforms.
There are technocrats, or experts, they know everything.

And in a word, I just wanted to explain by that example
why PulseAudio might be also a security risk.
I believe that this information might be useful for people.

---

### Post by igorzwx on 2009-08-03
[COLOR=#980101]**[ubuntu]**[/COLOR] 			 			[How to remove PulseAudio and fix sound with ALSA and ESound]("http://ubuntuforums.org/showthread.php?t=1230561")
[http://ubuntuforums.org/showthread.php?t=1230561](http://ubuntuforums.org/showthread.php?t=1230561)

[B]Audacity works (playback and recording).
VLC works.
Skype works too.[/B]

---

