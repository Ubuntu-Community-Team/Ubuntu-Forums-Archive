---
title: "Will PulseAudio ever work properly?"
date: 2009-10-31
forum: The Cafe
---

### Post by phenest on 2009-10-31
I've had to stay with Jaunty because the crackling and pops I got from Karmic are unbearable. It has been said that PA works fine in other distros and only Ubuntu has this problem.

---

### Post by Slug71 on 2009-10-31
Yes in Lucid, read the thread about improvements in Lucid.

---

### Post by qamelian on 2009-10-31
It already does work properly on both my laptop and desktop. I'm getting the bet sound I've ever had from Linux!

---

### Post by 23meg on 2009-10-31
Moved to Community Cafe, since this doesn't pertain specifically to Lucid.

---

### Post by hexion on 2009-10-31
The PA developer apparently was complaining about Ubuntu devs not including a needed patch into the kernel for PA to work correctly.
I think the needed patch was to be included in the kernel (or has been for 2.6.32) so, if that's correct, installing a newer kernel would eventually solve the problem.

I don't have any links though..

---

### Post by Seventh Reign on 2009-10-31
Pulse Audio works flawlessly on my 3 Installed Karmic Systems.

1 Soundblaster Audigy 2
1 Soundblaster X-Fi 
and 1 Integrated Audio

Its like upgrading from a 10" Black & White TV to a 60" HD TV .. its 1000 times better than what we had before.

---

### Post by hoppipolla on 2009-10-31
My sound is ok, totally perfect actually, but does it make a difference that I'm in KDE?

I don't know how the setups vary between KDE and Gnome.

---

### Post by FuturePilot on 2009-10-31
PulseAudio has worked perfectly for me ever since Intrepid on 5 different computers.

---

### Post by speedwell68 on 2009-10-31
I have never had an issue with PA.  I get crystal clear sound quality all of the time.

---

### Post by SunnyRabbiera on 2009-10-31
Pulse is fine here too.

---

### Post by YeOK on 2009-10-31
PulseAudio is awesome.  It Works great for me, I don't miss the ALSA mixer days at all.

---

### Post by Giant Speck on 2009-10-31
Karmic is actually the first release where sound has worked fairly well for me.  Unfortunately, I cannot say the same thing about other things, like Flash.

---

### Post by Regenweald on 2009-10-31
pulse would be phenomenal if all its blind detractors contributed a few hours of dedicated testing and bug reporting. Having said that, since hardy, my only audio problems came in the Karmic **testing** cycle.

---

### Post by phenest on 2009-10-31
I've not had a problem with PA until Karmic. It works just dandy in Jaunty.

---

### Post by VertexPusher on 2009-10-31
PulseAudio is still broken and will probably remain so for the foreseeable future.

All those who *think* their sound is working fine should take a look at the system monitor. Then remove PulseAudio and take another look.

Any application that uses sound takes 100% CPU with PulseAudio installed. How anyone can consider this normal or even acceptable is beyond me. I have a Core i7 with 8 virtual CPU cores, and after starting several sound apps (normal stuff such as Totem, Firefox with Flash, Skype, nothing special) I literally hear my CPU fan speed up. This never happened with Jaunty + ALSA, and it stopped happening right after I removed PulseAudio from Karmic.

However, things get worse with Karmic because now for the first time in Ubuntu's history, some basic GNOME applications (Nautilus, Terminal) actually refuse to start up if PulseAudio is absent. So now users are literally **forced** to either put up with a broken sound system or switch distros.

Unless I find a way to make those GNOME apps work again, I will say goodbye to Ubuntu and switch to Debian. The Debian devs have enough common sense to make PulseAudio an **optional** component which is not installed by default and not required for anything.

Ubuntu's PulseAudio mess has been around for 2 years now. With each upgrade I gave PulseAudio a fair chance and tried using it. But it failed every time. ALSA, on the other hand, just works. I **never** had issues with ALSA. And yes, ALSA is perfectly capable of software mixing, in fact has been so for at least five years.

At some point Canonical will have to pull the plug and bail out of the PulseAudio mess if they really care about making Ubuntu a viable option on the desktop. In its current state, Karmic will lose any benchmark comparison with Mac OS Snow Leopard and Windows 7. And it will suck laptop batteries empty faster than any other OS during audio operations.

---

### Post by FuturePilot on 2009-10-31
> **VertexPusher said:**
> PulseAudio is still broken and will probably remain so for the foreseeable future.

All those who *think* their sound is working fine should take a look at the system monitor. Then remove PulseAudio and take another look.

Any application that uses sound takes 100% CPU with PulseAudio installed. How anyone can consider this normal or even acceptable is beyond me. I have a Core i7 with 8 virtual CPU cores, and after starting several sound apps (normal stuff such as Totem, Firefox with Flash, Skype, nothing special) I literally hear my CPU fan speed up. This never happened with Jaunty + ALSA, and it stopped happening right after I removed PulseAudio from Karmic.

However, things get worse with Karmic because now for the first time in Ubuntu's history, some basic GNOME applications (Nautilus, Terminal) actually refuse to start up if PulseAudio is absent. So now users are literally **forced** to either put up with a broken sound system or switch distros.

Unless I find a way to make those GNOME apps work again, I will say goodbye to Ubuntu and switch to Debian. The Debian devs have enough common sense to make PulseAudio an **optional** component which is not installed by default and not required for anything.

Ubuntu's PulseAudio mess has been around for 2 years now. With each upgrade I gave PulseAudio a fair chance and tried using it. But it failed every time. ALSA, on the other hand, just works. I **never** had issues with ALSA. And yes, ALSA is perfectly capable of software mixing, in fact has been so for at least five years.

At some point Canonical will have to pull the plug and bail out of the PulseAudio mess if they really care about making Ubuntu a viable option on the desktop. In its current state, Karmic will lose any benchmark comparison with Mac OS Snow Leopard and Windows 7. And it will suck laptop batteries empty faster than any other OS during audio operations.

I'm running a number of audio applications right now with PA and none of them are taking up 100% CPU. Are you using the old version of Skype or the new Beta version? The old version and a serious issue with PA where it would peg the CPU at 100%

---

### Post by Icehuck on 2009-10-31
The real question is, "Will sound ever work perfectly in Linux?"

Apple and Microsoft got it right in the early 90's,and here in 2009, Linux still hasn't gotten right.

---

### Post by regomodo on 2009-10-31
#

---

### Post by &#1057;&#1090;&#1088;&#1072;&#1085;&#1085;&#1080;&#1082; on 2009-10-31
I've never had a problem with alsa, but I had a lot of problems with pa

---

### Post by andrewabc on 2009-10-31
> **phenest said:**
> I've had to stay with Jaunty because the crackling and pops I got from Karmic are unbearable. It has been said that PA works fine in other distros and only Ubuntu has this problem.

Make sure that has nothing to do with this bug
[crackling sound](http://ubuntuforums.org/showthread.php?p=8193272)
That's what my karmic had and it turned out to be audio power saving feature that was broken. But easily fixable.

---

### Post by Xbehave on 2009-10-31
> **Icehuck said:**
> The real question is, "Will sound ever work perfectly in Linux?"

Apple and Microsoft got it right in the early 90's,and here in 2009, Linux still hasn't gotten right.
Windows didn't get sound right until vista, why do you think foobar had to do it's own audio stack just to get a decent latency. Pulseaudio is current gen audio, alsa/oss was competitive with sound systems of the time (it then stagnated for quite some time, however drivers where a real mess in xp so it was hardly miles behind). Apple scrapped everything they had in the 90s, so i don't know how good/bad sound was for mac os <10

---

### Post by VertexPusher on 2009-10-31
> **Xbehave said:**
> Windows didn't get sound right until vista, why do you think foobar had to do it's own audio stack just to get a decent latency.
Foobar didn't do its own audio stack, it used whatever was there, MME, DirectSound, WDM Kernel Streaming, ASIO, you name it. However, low latency audio is a strain on the system and only useful for music **production** because you can't play a software synthesizer if there's a 500ms delay between hitting a key and hearing the note. For a video/audio player such as Foobar, low latency is meaningless. In fact it will only worsen overall performance.

> Pulseaudio is current gen audio, alsa/oss was competitive with sound systems of the time
PulseAudio was hyped as the great unification of sound APIs. But in fact it just added *yet another API* to all the existing ones which it failed to replace.

Some people, even in this thread, are still purporting the myth that PulseAudio introduced software mixing to Linux audio. They seriously believe that it was PulseAudio which enabled them to hear sound from YouTube and Rhythmbox at the same time. But in fact this problem was solved when Adobe switched the Flash plugin from legacy OSS to ALSA. PulseAudio had **absolutely nothing** to do with it. On the contrary, it caused issues with Flash that never occurred in a pure ALSA setup.

---

### Post by Yeti can't ski on 2009-10-31
I respect the effort of all those people working hard to implement PA in Ubuntu. 

The fact is, however, that it is still far from perfect and it is not a necessary feature for users with simple audio needs, like myself. 

I don't want to mix anything. I just want to use Ekiga (sometimes Skype), listen to some music, watch some videos and then play some games. Not simultaneously. I just want sound that works out of the box and doesn't break at every distro upgrade. 

Working to develop PA is great, but making Ubuntu totally dependent on it so that we won't have the choice of removing it - which is exactly what happened with Karmic - does not seem to be the right choice. 

IMHO it goes against flexibility, modularity and scalability, which should be strong points of Gnu-Linux.

---

### Post by Mr_Bumpy on 2009-11-01
> **hoppipolla said:**
> My sound is ok, totally perfect actually, but does it make a difference that I'm in KDE?

If you're using Kubuntu, then you don't have Pulseaudio installed.  Kubuntu does not use Pulseaudio.

---

### Post by VertexPusher on 2009-11-02
> **Mr_Bumpy said:**
> If you're using Kubuntu, then you don't have Pulseaudio installed.  Kubuntu does not use Pulseaudio.
That's interesting. A few weeks ago I read an interview with Lennart Poettering, creator of PulseAudio, in which he stated:
> I am not too concerned about most of the criticism and flames that erupt from time to time on various channels. **All the big Linux distributions have adopted PulseAudio** and it is an integral part of both the Palm Pre and the Nokia N900 devices, as well as Intel's Moblin.

That basically means that **PulseAudio has been adopted by about everyone who could adopt it. There is not really anyone who doesn't do PulseAudio anymore.**
Emphasis added. It seems he does not consider Debian and Kubuntu big Linux distributions. ;)

Well, I removed the packages pulseaudio, gstreamer0.10-pulseaudio, vlc-plugin-pulse, and installed gnome-alsamixer. Now everything works the way it should. I can run YouTube in Firefox, Totem, streaming in VLC and voice chat in Second Life **simultaneously** through ALSA without even remotely maxing out the system. No audio drop-outs, no stuttering any more. The difference is remarkable.

ALSA just rocks. :D

---

### Post by Exodist on 2009-11-02
> Emphasis added. It seems he does not consider Debian and Kubuntu big Linux distributions.

You beat me to it.. 

Debian has it in the repositories, but since its such a pain for so many at the moment its left out of the default install. (which Ubuntu should do until its fixed, hint hint)

---

### Post by VertexPusher on 2009-11-02
> **Exodist said:**
> which Ubuntu should do until its fixed, hint hint
But then it will never be fixed, because Lennart will be left without beta testers. Since the troubles of "PoetteringAudio" far outweigh its benefits, very few people would actively install it.

---

### Post by MorphingDragon on 2009-11-02
Pulse Audio works fine on Fedora. The only one I've heard crackles from are form the old AC97 chips.

---

### Post by VertexPusher on 2009-11-02
> **MorphingDragon said:**
> Pulse Audio works fine on Fedora. The only one I've heard crackles from are form the old AC97 chips.
AC'97 was phased out years ago. Even if your computer is three years old, its onboard audio controller is some variant of Intel's HDA (High Definition Audio). These components are actually very good, much better than AC'97. Yet they stutter with PulseAudio, and that's not because of a driver issue or an issue in ALSA. It's because of PulseAudio consuming way too much CPU.

Remove PulseAudio and the crackling will be gone instantly.

---

### Post by MorphingDragon on 2009-11-02
> **VertexPusher said:**
> AC'97 was phased out years ago. Even if your computer is three years old, its onboard audio controller is some variant of Intel's HDA (High Definition Audio). These components are actually very good, much better than AC'97. Yet they stutter with PulseAudio, and that's not because of a driver issue or an issue in ALSA. It's because of PulseAudio consuming way too much CPU.

Remove PulseAudio and the crackling will be gone instantly.

Maybe you want to read that again, You missed a keyword. I've had no trouble with Pulse Audio ON FEDORA. Not at home or at any of the computers at work. The school I kindly donate my time for uses the AC97 chips and thats the only one I've had problems with.

Would you like to prove that CPU theory?

Egimicate yourself:
[http://forums.fedoraforum.org/showthread.php?t=225660](http://forums.fedoraforum.org/showthread.php?t=225660)

---

### Post by Exodist on 2009-11-02
Back in the day when I had Slack7 on my K7-550. I had WindowMaker running with ALSA. If I was watching a movie in Xine and messed around and opened a MP3 in XMMS.  Both would still play flawlessly without any mixing issues. Thats been around 1999.
Now I can see why PA would benifit a music studio. But really if it plays. It plays. The average person isnt going to give a hoot about PA benifits that they will never see unless they are running a sound studio.

---

### Post by MorphingDragon on 2009-11-02
> **Exodist said:**
> Back in the day when I had Slack7 on my K7-550. I had WindowMaker running with ALSA. If I was watching a movie in Xine and messed around and opened a MP3 in XMMS.  Both would still play flawlessly without any mixing issues. Thats been around 1999.
Now I can see why PA would benifit a music studio. But really if it plays. It plays. The average person isnt going to give a hoot about PA benifits that they will never see unless they are running a sound studio.

Or they're running a media centre.

---

### Post by benmoran on 2009-11-02
I had some issues with Pulse during the Karmic apha stage, but it's been flawless since Karmic beta. It doesn't use more than a few cpu%, which some consider high, but it's benefits are awesome. The Karmic Pulse/Bluetooth integration is just absolutely phenominal. I love it so much that I would never use a distro without it. 

Love it or hate it, PulseAudio is here to stay.

---

### Post by Exodist on 2009-11-02
> **MorphingDragon said:**
> Or they're running a media centre.
Yea that to..

But Studio/MediaCentre users only prob make up what 1% of the average ubuntu users. I am pulling that number out my *** btw. But it seems reasonable.

I would most surely put it in Ubuntu Studio, but the desktop I would just left it in the repositories for those few who wanted it.

---

### Post by gradinaruvasile on 2009-11-02
> **MorphingDragon said:**
> 

Would you like to prove that CPU theory?



Well it happened to me too an ALL computers i tested it. Its not a constant thing, it happens sometimes when something is played. Its really frustrating. The other thing is that in some apps the sound doesnt work right if at all.
ALSA has it all that most of the users ever need. I removed PA on all computers i installed Ubuntu on. And guess what: no more problems...

---

### Post by 3rdalbum on 2009-11-02
> **VertexPusher said:**
> All those who *think* their sound is working fine should take a look at the system monitor. Then remove PulseAudio and take another look.

What am I meant to be looking for? Gnome System Monitor is using 16% on updating the graph, Opera apparently uses 8% occasionally. Pulseaudio is not even using 1%.

> Any application that uses sound takes 100% CPU with PulseAudio installed.

Not here it doesn't.

> However, things get worse with Karmic because now for the first time in Ubuntu's history, some basic GNOME applications (Nautilus, Terminal) actually refuse to start up if PulseAudio is absent.

1. Ubuntu Hardy (I think) wouldn't log into Gnome if Pulseaudio was not installed.

2. I killed Pulseaudio and Gnome-Terminal still starts up.

> At some point Canonical will have to pull the plug and bail out of the PulseAudio mess if they really care about making Ubuntu a viable option on the desktop.

I'm certainly not going to give up Pulseaudio without a fight. It's one of the best features of my desktop. Go back to Debian if you want - yes, software mixing in ALSA is nothing new, but then nothing in ALSA is. Pulseaudio is the way forward, bringing new modern features to the Linux desktop. And PA adoption and development is very high (most programs now have a specific "Pulse" output option - even including Skype).

---

### Post by Yeti can't ski on 2009-11-02
> **benmoran said:**
> Love it or hate it, PulseAudio is here to stay.

The "full-package" + "take as it is or leave it" approach seems a lot like a Windowi$$h thing (no offense meant :D).

Ok, it is great to add functionality to the system. But it is also great to have options and Karmic seems to preclude the possibility of easily getting rid of Pulseaudio. 

Just as another user said, it is as if everyone would be forced to use Compiz, without having the chance to go for something simpler or installing Xubuntu, for istance. Why that?

By the way, did anyone find a clean way of removing Pulseaudio from Karmic without losing sound in GUI applications (Mplayer, etc.)? 

This is what I am referring to: 

[https://bugs.launchpad.net/ubuntu/+source/gnome-media/+bug/440465]("https://bugs.launchpad.net/ubuntu/+source/gnome-media/+bug/440465")

---

### Post by VertexPusher on 2009-11-02
> **Yeti can't ski said:**
> By the way, did anyone find a clean way of removing Pulseaudio from Karmic without losing sound in GUI applications (Mplayer, etc.)? 

This is what I am referring to: 

[https://bugs.launchpad.net/ubuntu/+source/gnome-media/+bug/440465](https://bugs.launchpad.net/ubuntu/+source/gnome-media/+bug/440465)
Here's what I did:

First, I removed the **pulseaudio** base package and everything that depended on it (pulseaudio-esound-compat etc.). This made Gnome's volume control disappear, so I installed **gnome-alsamixer** as a replacement. For some reason, Nautilus and Gnome Terminal refused to start up while VLC was active. Removing **vlc-plugin-pulse** fixed that. Finally, I removed **gstreamer0.10-pulseaudio** to make sound work again in Totem. MPlayer already worked fine without PulseAudio.

Now I have perfect sound in all applications. The only thing that doesn't work is the control panel to configure system notification sounds in Gnome. But I never used those anyway, so I don't care. If I did, I would probably switch to Debian which is entirely ALSA-based by default.

I'll give PulseAudio another chance in six months. But after two years of failure, I don't expect too much.

---

### Post by Yeti can't ski on 2009-11-02
VertexPusher,

Thanks! I will give it a try when I have a chance.

---

### Post by HeresJohnny on 2009-11-02
> **phenest said:**
> I've had to stay with Jaunty because the crackling and pops I got from Karmic are unbearable. It has been said that PA works fine in other distros and only Ubuntu has this problem.

Actually, I don't think this is a problem with PA; I had this issue pop up suddenly on me in Jaunty, and this fix from Psyke83 put it back in shape in a jiffy:

```


$ alsamixer -Dhw

```
Somehow, the PCM gets muted (oh sure, I probably did it, PEBKAC, yada yada yada) and that results in the crackling sound you hear.  Bagels to breakfast if you try that command and adjust your mixer level, your sound will be back to normal, good as gold. Give it a shot!  Btw, only when I looked up ['sound crackling']("http://ubuntuforums.org/showthread.php?t=987252") did I find it on the forums.  Good luck!

---

### Post by phenest on 2009-11-02
> **VertexPusher said:**
> Well, I removed the packages pulseaudio, gstreamer0.10-pulseaudio, vlc-plugin-pulse, and installed gnome-alsamixer. Now everything works the way it should. I can run YouTube in Firefox, Totem, streaming in VLC and voice chat in Second Life **simultaneously** through ALSA without even remotely maxing out the system. No audio drop-outs, no stuttering any more. The difference is remarkable.

ALSA just rocks. :D

Does the hardware volume control still work?

I was going to test removing all things PA from a new Karmic guest install.
```
steve@virtual:~$ sudo apt-get remove libpulse0
[sudo] password for steve: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  gnome-applets gnome-control-center gnome-media gnome-orca gnome-panel
  gnome-session gnome-settings-daemon gstreamer0.10-pulseaudio
  indicator-applet indicator-applet-session indicator-messages
  indicator-session libasound2-plugins libcanberra-pulse libpulse-browse0
  libpulse-mainloop-glib0 libpulse0 pulseaudio pulseaudio-esound-compat
  pulseaudio-module-bluetooth pulseaudio-module-gconf pulseaudio-module-udev
  pulseaudio-module-x11 pulseaudio-utils python-speechd speech-dispatcher
  ubuntu-desktop
0 upgraded, 0 newly installed, 27 to remove and 0 not upgraded.
After this operation, 28.7MB disk space will be freed.
Do you want to continue [Y/n]? 

```
Trying to remove libpulse-mainloop-glib0 gives similar results. Too much integration.

---

### Post by slumbergod on 2009-11-02
I've never had PA working correctly. It always crackles and pops and because I usually wear earbud headphones it is even more noticeable. First thing I always do is get rid of as much of pulse as possible and go back to Alsa. Then everything works fine (except for low volume which I have concluded is never going to be fixed in Linux).

Interestingly, when I did a clean install of Xubunty Karmic, I noticed the crackle straight away and went to remove pulse...only to find pulse wasn't even installed. It was a conflict between Intel HDA sound and the power management system in Karmic. A simple config edit fixed it. 

What they did get right in this release is getting my physical volume dial to work straight away. In Jaunty it took ages for me to troubleshoot that!

---

### Post by phenest on 2009-11-02
> **phenest said:**
> Does the hardware volume control still work?

To answer my own question: removing PA stops the hardware volume controls from working.

Fixing the crackling and pops might be fixable, but until I get proper control of my LFE channel as I do in Jaunty, I won't be upgrading to Karmic.

---

### Post by CherylMPaine on 2009-11-02
PulseAudio ... work ... properly.  Usually not words I see in the same sentence.  :p  Not to be vicious, but we'll probably have a better chance at Lucent/Agere making their 56K WinModem drivers Open Source before PulseAudio works 100%.  Just my opinion.  ;)

---

### Post by Xbehave on 2009-11-02
That's some bad packaging on fedora 11
```
Removing:
 pulseaudio                                           x86_64                              0.9.15-17.fc11                              installed                              1.9 M
Removing for dependencies:
 alsa-plugins-pulseaudio                              x86_64                              1.0.21-2.fc11                               installed                               93 k
 kde-settings-pulseaudio                              noarch                              4.2-12.1                                    installed                               0.0
 paprefs                                              x86_64                              0.9.8-1.fc11                                installed                              197 k
 pulseaudio-module-gconf                              x86_64                              0.9.15-17.fc11                              installed                               22 k
 pulseaudio-module-x11                                x86_64                              0.9.15-17.fc11                              installed                               49 
```
which seams reasonable (i use kde not gnome, so perhaps it's an upstream problem because there is already no interest in maintaining an alsa version)

---

### Post by SunnyRabbiera on 2009-11-02
Pulse works fine on my hardware, it works better then ALSA here

---

### Post by phenest on 2009-11-02
> **SunnyRabbiera said:**
> Pulse works fine on my hardware, it works better then ALSA here

Whether it works or not is not the only issue. PA is too heavily integrated into Gnome to be easily removed without losing any other functionality. I removed PA and the hardware volume controls ceased working. Not good. There needs to be an option to remove PA if you don't want/need it.

---

### Post by Xbehave on 2009-11-02
> **phenest said:**
> Whether it works or not is not the only issue. PA is too heavily integrated into Gnome to be easily removed without losing any other functionality. I removed PA and the hardware volume controls ceased working. Not good. There needs to be an option to remove PA if you don't want/need it.
Why? if PA is needed to provide functionality, why should devs waste time reimplementing that functionality. Should they port gnome to QT so GTK isn't a dependency? What about OSS is it gnomes job to support OSS3 and OSS4 too?

All of this is irrelevant as AFAIK its down to how ubuntu package gnome, not gnome itself.

---

### Post by CherylMPaine on 2009-11-02
> **phenest said:**
> There needs to be an option to remove PA if you don't want/need it.


Agreed.  :(

---

### Post by Yeti can't ski on 2009-11-02
> **VertexPusher said:**
> Here's what I did:

First, I removed the **pulseaudio** base package and everything that depended on it (pulseaudio-esound-compat etc.). This made Gnome's volume control disappear, so I installed **gnome-alsamixer** as a replacement. For some reason, Nautilus and Gnome Terminal refused to start up while VLC was active. Removing **vlc-plugin-pulse** fixed that. Finally, I removed **gstreamer0.10-pulseaudio** to make sound work again in Totem. MPlayer already worked fine without PulseAudio.

Thanks so much for the suggestion, but in the end I found a less traumatic workaround. This is it: 

[http://ubuntuforums.org/showthread.php?t=1306356](http://ubuntuforums.org/showthread.php?t=1306356)

It is a way to deactivate pulseaudio with "killall" without letting it spawn back to life during the same session. 

I preferred to do so, in order to avoid possible headches upon the next upgrade to Lynx.

---

### Post by phenest on 2009-11-02
> **Xbehave said:**
> Why? if PA is needed to provide functionality, why should devs waste time reimplementing that functionality. Should they port gnome to QT so GTK isn't a dependency? What about OSS is it gnomes job to support OSS3 and OSS4 too?

All of this is irrelevant as AFAIK its down to how ubuntu package gnome, not gnome itself.

Huh!? I never said it was the fault of Gnome, just that it should be removable with losing anything in Gnome. Try removing libpulse0 without removing any part of Gnome. Removing PA should allow you to fall back to ALSA (or whatever). Nothing more, nothing less.

---

### Post by Warpnow on 2009-11-02
<Insert Anything Here> will never work properly. By the time it receives enough upgrades to be stable, it will have been replaced by a shinier, more bug-ridden piece of technology.

This law is universal.

---

### Post by VertexPusher on 2009-11-03
> **phenest said:**
> To answer my own question: removing PA stops the hardware volume controls from working.

Fixing the crackling and pops might be fixable, but until I get proper control of my LFE channel as I do in Jaunty, I won't be upgrading to Karmic.
As I said before, you can install gnome-alsamixer as a replacement.

Yes, Gnome depends on libpulse0, but there's no need to remove that. Just remove pulseaudio, gstreamer0.10-pulseaudio and vlc-plugin-pulse (if VLC is installed).

If that is too much customization for you, consider switching to Kubuntu which is PulseAudio-free by default.

---

### Post by VertexPusher on 2009-11-04
> **Yeti can't ski said:**
> I preferred to do so, in order to avoid possible headches upon the next upgrade to Lynx.
What headaches?

Changes performed by the package manager are much easier to undo than manual changes to system configuration files. If I want to revert my system to its original state, all I need to do is reinstall the "ubuntu-desktop" metapackage because it depends on all the packages I removed earlier and will pull them back in automatically.

However, if you change configuration files manually, you are on your own. There is no automatic way to revert them. You have to keep track of all the changes yourself.

---

### Post by Yeti can't ski on 2009-11-04
> **VertexPusher said:**
> What headaches?

Changes performed by the package manager are much easier to undo than manual changes to system configuration files. If I want to revert my system to its original state, all I need to do is reinstall the "ubuntu-desktop" metapackage because it depends on all the packages I removed earlier and will pull them back in automatically.

However, if you change configuration files manually, you are on your own. There is no automatic way to revert them. You have to keep track of all the changes yourself.

You are absolutely right. Still, mine is just the lazy man solution. 

In addition to a few cracks, my greatest problem with PulseAudio is having proper sound in OSS legacy software (Quake3 mods in particular), which I really don't use often anyway.

With the workaround, I can still effectively kill the bloody PA when I want or need to, without losing the standard volume applet and standard sound controls (even though gnome-alsamixer indeed rocks).

---

### Post by kuric on 2009-11-04
I'm having problems with Pulse Audio on Ubuntu 9.10.
Eg: Can't play Second Life without crashing because of PA.
Never had that problem on Ubuntu 9.04.
I had to replace it and install Esound. No more crashes now.

---

### Post by MeduZa on 2009-11-12
> **Seventh Reign said:**
> Pulse Audio works flawlessly on my 3 Installed Karmic Systems.

1 Soundblaster Audigy 2
1 Soundblaster X-Fi 
and 1 Integrated Audio

Its like upgrading from a 10" Black & White TV to a 60" HD TV .. its 1000 times better than what we had before.

I have a SB audigy2 and when I select 5.1 analog output the sound get crapy! I removed PA and now I have no volume control :(

---

### Post by Yeti can't ski on 2009-11-12
> **MeduZa said:**
>  I removed PA and now I have no volume control :(

Yeap, PA is much more deeply integrated with Karmic Koala than ever befora. A bug has been file on the issue and so on...

Still, you can control sound through gnome-alsamixer if you want...

In my case, I stop the autospawn of PA and then created a script with "killall pulseaudio" + "pulseaudio -D" in order to run legacy applications that are incompatible with it.

---

