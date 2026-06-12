---
title: "Pulseaudio 5.0"
date: 2014-03-10
forum: Ubuntu Development Version
---

### Post by zika on 2014-03-10
Have anyone tried PA 5.0?
Any issues?

---

### Post by formerub on 2014-03-10
zika if you are talking about PA from ppa:ubuntu-audio-dev/pulse-testing  Then everything went ok for me. Been using it for a couple of days now. Regards runrickus

---

### Post by zika on 2014-03-10
> **formerub said:**
> zika if you are talking about PA from ppa:ubuntu-audio-dev/pulse-testing  Then everything went ok for me. Been using it for a couple of days now. Regards runrickusAny idea if 5.0 (in that ppa is 4.99 still, only for Trusty, last time I've checked. using that .deb does not work in Saucy) will arrive in 13.10?

---

### Post by formerub on 2014-03-10
Having No Thread tools Sucks LOL Here is all I could Find [http://www.freedesktop.org/wiki/Software/PulseAudio/](http://www.freedesktop.org/wiki/Software/PulseAudio/)

---

### Post by zika on 2014-03-10
> **formerub said:**
> Having No Thread tools Sucks LOL Here is all I could Find [http://www.freedesktop.org/wiki/Software/PulseAudio/](http://www.freedesktop.org/wiki/Software/PulseAudio/)Read it couple of days ago. I thought that it would be better to use .deb than to compile. Sent a message to LY and will see... ;)

---

### Post by QDR06VV9 on 2014-03-11
> **zika said:**
> Read it couple of days ago. I thought that it would be better to use .deb than to compile. Sent a message to LY and will see... ;)
Just now tried to compile the tar.gz on saucy it Failed.
Will try it on trusty tonite.

---

### Post by Milos_SD on 2014-03-11
I compiled pulseaudio from git on Saucy and it works great. :)

```
pulseaudio --version
pulseaudio 5.0-6-g9271c1
```

For me, pulseaudio worked much better if I compile it, then the one from repos. Even when it was the same version. :)

P.S. I can write a HOWTO for compiling pulseaudio from git, if you guys want. :)

---

### Post by zika on 2014-03-11
> **Milos_SD said:**
> I compiled pulseaudio from git on Saucy and it works great. :)

```
pulseaudio --version
pulseaudio 5.0-6-g9271c1
```

For me, pulseaudio worked much better if I compile it, then the one from repos. Even when it was the same version. :)

P.S. I can write a HOWTO for compiling pulseaudio from git, if you guys want. :)You lead and I'll follow, as many times before with kernel(s)... ;)

---

### Post by QDR06VV9 on 2014-03-11
> **Milos_SD said:**
> P.S. I can write a HOWTO for compiling pulseaudio from git, if you guys want. :)

Show me the way zen master:)

---

### Post by Milos_SD on 2014-03-11
Here it is: [http://ubuntuforums.org/showthread.php?t=2210602&p=12954078#post12954078](http://ubuntuforums.org/showthread.php?t=2210602&p=12954078#post12954078)

---

### Post by QDR06VV9 on 2014-03-11
Crap I knew it "[COLOR=#000000][FONT=Ubuntu Mono]CFLAGS="-g
 
Thanks Milo_SD[/FONT][/COLOR]:popcorn:

---

### Post by zika on 2014-03-11
```
The following packages have unmet dependencies. libx11-xcb-dev : Depends: libx11-xcb1 (= 2:1.6.1-1ubuntu1) but 2:1.6.2+git20131002.18a5278b-0ubuntu0ricotz2 is to be installed
E: Build-dependencies for pulseaudio could not be satisfied.
```
I'll have to figure my way out of this (due to my bond with ricotz's ppas..)... ;)
Maybe next morning... ;)

---

### Post by Milos_SD on 2014-03-11
@zika: When you add a PPA, "Source" part is not added automaticaly. Go To Software Sources and check the Source part of that PPA. Then it should work.

---

### Post by zika on 2014-03-11
> **Milos_SD said:**
> @zika: When you add a PPA, "Source" part is not added automaticaly. Go To Software Sources and check the Source part of that PPA. Then it should work.I'll try that (I know that rule about deb-src and I keep adding them, but I'll check to be sure) but I think there is a strict condition for version and that is what is wrong... I'll look into that...
Update&#8321;: Nope. As I've predicted it was not that that was stopping it. Simply I do have a package ahead of the one that is fixed in dependencies... But, it is fixed in current (4.0) version of PA so I might try to go ahead with process as new one (5.0) could be a bit more lenient on that dependency... We'll see...

---

### Post by QDR06VV9 on 2014-03-11
Thank You!!!
After a little [extra]("http://ubuntuforums.org/showthread.php?t=2210602&p=12954131#post12954131")
```
pulseaudio --version
pulseaudio 5.0-15-g00922
```

Noticeable Improvement!
Or I could be under the placebo bubble.:)

---

### Post by Milos_SD on 2014-03-12
Here is my config of pulseaudio that gives much, much better sound then the default one. For this to work fully, you need to install this packages: rtkit, ladspa-sdk, swh-plugins, tap-plugins, wah-plugins. The files are located in /etc/pulse/ directory.
[default.pa]("http://ubuntuone.com/6fJtNN1fbz1tqlLMGtrUUA")
[daemon.conf]("http://ubuntuone.com/5v5KzbsZsIu0p9Uq0l3rVn")

---

### Post by QDR06VV9 on 2014-03-12
Just to confirm noticeable Improvement very clean & a little purer!
This install is Trusty
```
Distributor ID:    Ubuntu
Description:    Ubuntu Trusty Tahr (development branch)
Release:    14.04
Codename:    trusty
pulseaudio 5.0-15-g00922
3.13.0-17-generic
```
The first install was on a laptop acer-5750 intel HD Audio so noticeable difference kinda got me curious
as to how much of difference it would make on my trusty tower custom build Soundcard Audigy2 Platinum
Speakers Klipsch THX 4.1 .
Well I feel I could write review here but I'm Hooked Gona compile from here on out!!:guitar:

---

### Post by QDR06VV9 on 2014-03-12
> **Milos_SD said:**
> Here is my config of pulseaudio that gives much, much better sound then the default one. For this to work fully, you need to install this packages: rtkit, ladspa-sdk, swh-plugins, tap-plugins, wah-plugins. The files are located in /etc/pulse/ directory.
[default.pa]("http://ubuntuone.com/6fJtNN1fbz1tqlLMGtrUUA")
[daemon.conf]("http://ubuntuone.com/5v5KzbsZsIu0p9Uq0l3rVn")
The Plug-ins were a nice touch!:)
Did you add this to your tutorial?

---

### Post by zika on 2014-03-13
> **Milos_SD said:**
> Here is my config of pulseaudio that gives much, much better sound then the default one. For this to work fully, you need to install this packages: rtkit, ladspa-sdk, swh-plugins, tap-plugins, wah-plugins. The files are located in /etc/pulse/ directory.
[default.pa]("http://ubuntuone.com/6fJtNN1fbz1tqlLMGtrUUA")
[daemon.conf]("http://ubuntuone.com/5v5KzbsZsIu0p9Uq0l3rVn")Or in ~/.pulse ...

---

### Post by Milos_SD on 2014-03-13
> **runrickus said:**
> The Plug-ins were a nice touch!:)
Did you add this to your tutorial?

No I didn't. I don't know if the config will work for everyone. Because it uses realtime priority, it can't work without problems for everyone. You need custom kernel with 1000Hz and PREEMPT for it to work without issues. :)

---

### Post by QDR06VV9 on 2014-03-13
> **Milos_SD said:**
> No I didn't. I don't know if the config will work for everyone. Because it uses realtime priority, it can't work without problems for everyone. _**You need custom kernel with 1000Hz and PREEMPT for it to work without issues.**_ :)
You know i should of thought about that.
But no issues here.:D
Oh and one other thing I had to change.
In /etc/pulse/default.pa, I had to change this line:
load-module module-udev-detect tsched=1
to:
load-module module-udev-detect tsched=0

This switches pulseaudio to the older scheduling mode and gets rid of the glitches.

---

### Post by Milos_SD on 2014-03-13
> **runrickus said:**
> You know i should of thought about that.
But no issues here.:D
Oh and one other thing I had to change.
In /etc/pulse/default.pa, I had to change this line:
load-module module-udev-detect tsched=1
to:
load-module module-udev-detect tsched=0

This switches pulseaudio to the older scheduling mode and gets rid of the glitches.

That is exactly why I sad that you need kernel with 1000Hz and PREEMPT. With it, there are no sound glitches with "tsched=1". :)

---

### Post by QDR06VV9 on 2014-03-13
> **Milos_SD said:**
> That is exactly why I sad that you need kernel with 1000Hz and PREEMPT. With it, there are no sound glitches with "tsched=1". :)
I'll Bite what kernel are you using, I have tried every kernel known to man, Pusleaudio Hates my card LOL
```
Audigy2 [SB Audigy 2 ZS [SB0353]],
```
Thats the only way I can can rid of about 40 to 50 seconds of skipping and popping.

---

### Post by Milos_SD on 2014-03-13
```
uname -a
Linux c2d-desktop 3.14.0-rc6-core2duo #1 SMP PREEMPT Mon Mar 10 13:40:16 CET 2014 x86_64 x86_64 x86_64 GNU/Linux
```

You can check my howto for compiling kernel: [http://forum.ubuntu-rs.org/Thread-kompajliranje-linux-kernela-na-ubuntu](http://forum.ubuntu-rs.org/Thread-kompajliranje-linux-kernela-na-ubuntu)
It is on Serbian, but all you need is what is in the [code] part. And enable Full PREEMPT and Timer frequency=1000Hz. You can also try -lowlatency kernel from here: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.14-rc6-trusty/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.14-rc6-trusty/) it has that two options enabled.

You are getting 40-50 seconds of skipping and popping when ever any sound starts playing?

---

### Post by QDR06VV9 on 2014-03-13
> **Milos_SD said:**
> [code]
You are getting 40-50 seconds of skipping and popping when ever any sound starts playing?
Yes Sir.
The -lowlatency kernel from here: [http://kernel.ubuntu.com/~kernel-ppa...14-rc6-trusty/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v3.14-rc6-trusty/") A bit buggy for me.
I will give your other option a  try.
Thanks Milos_SD

---

### Post by QDR06VV9 on 2014-03-13
No Joy:(
Still had to edit load-module module-udev-detect tsched=0
```
Distributor ID:    Ubuntu
Description:    Ubuntu Trusty Tahr (development branch)Release:    14.04
Codename:    trusty
pulseaudio 5.0-15-g00922
3.14.0-031400rc6-lowlatency

```
I tell Ya It's a _**conspiracy**_ from pulseaudio to _**demise **_sound-blaster cards:lolflag:  
I really have tried everything known to man(since the arrival of pulseaudio)  but the only thing that works
is tsched=0
But Hey The Improvement that I have got from PA 5.0 Is _**well worth it**_.
I can literaly pick out each instrument playing
Again Many Thanks Milos_SD

---

### Post by zika on 2014-03-13
> **runrickus said:**
> No Joy:(
Still had to edit ```
load-module module-udev-detect tsched=0
```Instead of turning tsched off try leaving it on and changing clock-source```
/bin/echo hpet >/sys/devices/system/clocksource/clocksource0/current_clocksource
```

---

### Post by QDR06VV9 on 2014-03-13
> **zika said:**
> Instead of turning tsched off try leaving it on and changing clock-source```
/bin/echo hpet >/sys/devices/system/clocksource/clocksource0/current_clocksource
```

Thanks zika but no joy still,  the popping never went away the skipping however was gone.
There is a slight increase in quality if I do not go bonkers hearing the popping.lol
By chance do you have my same card SB Audigy 2 ZS [SB0353]?
 I have read every post I could find since the beginning of pulseaudio's conception they just did not have us in mind.

I have just now tried this.
```
Distributor ID:    Ubuntu
Description:    Ubuntu Trusty Tahr (development branch)
Release:    14.04
Codename:    trusty
pulseaudio 5.0-15-g00922
3.13-6.dmz.1-liquorix-amd64
Linux me-Aspire-M3300 3.13-6.dmz.1-liquorix-amd64 #1 ZEN SMP PREEMPT Wed Mar 12 03:30:02 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

```
Getting closer. Will play with it some more in the morning.

---

### Post by QDR06VV9 on 2014-03-14
Works Flawlessly on the lappy Acer-5570

```
Distributor ID:    Ubuntu
Description:    Ubuntu 13.10
Release:    13.10
Codename:    saucy
3.14.0-031400rc6-lowlatency
pulseaudio 5.0-15-g00922
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC269VB Analog [ALC269VB Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

---

### Post by QDR06VV9 on 2014-03-14
It would appear That I was correct About that sound-card SB Audigy 2 ZS [SB0353] not working well.
Broke out my spare tower with about the same specs  [AMD] K8 [Athlon64/Opteron] 3 Gigs of ram.
Sound Card  Audigy2 [SB Audigy 2 [SB0240]]
And well I am dumb founded??
Works Flawlessly.
```
Distributor ID:    UbuntuDescription:    Ubuntu 13.10
Release:    13.10
Codename:    saucy
Linux me-M61SME-S2 3.14.0-031400rc6-lowlatency #201403100035 SMP PREEMPT Mon Mar 10 05:05:27 UTC 2014 i686 athlon i686 GNU/Linux
pulseaudio 5.0-18-g868a

```
What I dont get is they are pretty much the same cards Just rewritten.

---

### Post by zika on 2014-03-14
When tacking about crackling and other artifacts in sound one thing is often forgotten. It is not only result of latency and such stuff. It is, very often, result of missmatch of parameters in either ALSA or Pulseuadio or Jack etc... Once You get that micro-parameters settled You can get very fine sound... So, very often, it is better to be in peace with a higher latency due to (in my case DAC) parameters of HW that should be respected... If only I could get back time spend in chasing these daemons until I've got it (almost) right and recognized hw limitations... I'd be much younger... ;)
Blaming ALSA, PA, jack is much easier but very non-productive, I've learned...
Very much as MTU value in networking... ;)

---

### Post by QDR06VV9 on 2014-03-14
> **zika said:**
> Blaming ALSA, PA, jack is much easier but very non-productive, I've learned...
Very much as MTU value in networking..;). 
Agreed.
This little outing I took on started bringing back some some strong frustrations I went through way back then.
So Ill shut-up now.;)
Besides who can stay mad with beautiful notes and tones flying out of my speakers :-\"
Regards Rick:)

---

### Post by zika on 2014-03-15
> **runrickus said:**
> So Ill shut-up now.;)By no means do not, not on my behalf. That was not my intention...
Latency is precariuos beast... ;)

---

### Post by QDR06VV9 on 2014-03-15
> **zika said:**
> 
_Latency is precariuos beast... _;)
It sure seems that way..LOL 

```
By no means do not, not on my behalf. That was not my intention...
```
This is my most passionate flaw pulseaudio! I Just don't like filling threads up with my unimportant views.
But I think this is fitting.
```
This PulseAudio issue has had me climbing the walls over the last couple  of months(for me years). 
I sincerely hope someone will take note and push for a  concerted effort to resolve a problem that has plagued the system 
for  nearly half a decade. And should the developers *not *be capable  of solving this issue, I would ask the major distributions
 (those that  depend upon PA) to find an alternative! This problem is going to only  become worse as more and more people start 
playing games on Steam. How  shameful would that be if Linux begins to start gaining serious momentum  on the desktop, 
only to have it shot down because of a faulty sound  server?
``` 
Thanks zika:wink:

---

### Post by zika on 2014-03-15
You've just made me clean a bit of mess that hanged in my PC-sound (USB>S/PDIF>reclocker>DAC>...) for couple of weeks...
You've just made me go through whole stuff, clean Jack set-up, make it RT perfect (rtirq-init, threadirqs in Grub, ...), clean PulseAudio settings stuff and get rid of some glitches i had lurking around and no patience to bring all to the clarity and sound I had weeks ago. Now it is like it should be. So &#8222;thanks&#8220; goes to You gentlemen...
As I said, latency is overrated... ;) But surely needed in just right amount and places...

---

### Post by zika on 2014-03-19
Pulseaudio 5.0 is available (now) from ppa:ubuntu-audio-dev/pulse-testing (trusty)...
Nice...

---

### Post by QDR06VV9 on 2014-03-19
Yes Indeed! Nice.

I still have this one audio card from hell?!?
```
List of PLAYBACK Hardware Devices ****
/usr/bin/pulseaudio: symbol lookup error: /usr/bin/pulseaudio: undefined symbol: pa_inotify_start
card 0: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
[COLOR=#0000cd][U]card 1: Audigy2 [SB Audigy 2 ZS [SB0353]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 32/32[/U][/COLOR]
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
  Subdevice #31: subdevice #31
card 1: Audigy2 [SB Audigy 2 ZS [SB0353]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 1: Audigy2 [SB Audigy 2 ZS [SB0353]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Audigy2 [SB Audigy 2 ZS [SB0353]], device 4: p16v [p16v]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Has been a complete thorn in side since pulseaudio's birth.
Rant Over now..;)
But I few things I do now I'll share incase someone else is interested this is for Audigy2 [SB Audigy 2 ZS [SB0353]] only.
Make sure you have a realtime kernel installed:
<Removed>
```
dpkg -l | grep linux-rt
```
If that doesn't list anything, you'll need to install one:
_****Not needed on 3.14.0-031400rc7-lowlatency (Trusty)Without RealTime****_ 
```
sudo apt-get install linux-rt linux-headers-rt
```
Milos_SD has a How To [HERE]("http://forum.ubuntu-rs.org/Thread-kompajliranje-linux-kernela-na-ubuntu") for RealTime kernel.
Ubuntu Studio uses the realtime kernel by default; I'm not sure it uses the same apt repositories as standard Ubuntu. 
    After you've got the kernel you still need to set up real-time access for your applications.
    All you have to do for this is give your audio group permissions to access the rtprio, nice, and memlock limits. To do this, you just need to run these commands, which will add some lines 
o the file /etc/security/limits.conf
```
sudo su -c 'echo @audio - rtprio 99 >> /etc/security/limits.conf'
sudo su -c 'echo @audio - nice -19 >> /etc/security/limits.conf'
sudo su -c 'echo @audio - memlock unlimited >> /etc/security/limits.conf'
```
Then I just kill pulseaudio,
```
pulseaudio -k
```
Well This works for me your mileage may vary!
Even Though I bad mouth pulseaudio **Alot** It is starting to come in better.
Although I wish I had the time back I have spent configuring and Tinkering with pulseaudio I figure I would be in my Mid 20s Sheesh!![IMG]http://www.sherv.net/cm/emo/angry/smashing-computer.gif[/IMG]
Regards:D

---

### Post by zika on 2014-03-19
Do not forget```
threadirqs
```among many other things that are (let'say) needed for good &#8222;rt-sound&#8220;... ;)
Not to mention that: Modyfying /etc/security/limits.conf should not be done on Ubuntu 10.04 and later... ;)
As far as I know...

---

### Post by QDR06VV9 on 2014-03-19
> **zika said:**
> Do not forget```
threadirqs
```among many other things that are (let'say) needed for good „rt-sound“... ;)
_Not to mention that: Modyfying /etc/security/limits.conf should not be done on Ubuntu 10.04 and later._.. ;)
As far as I know...
The underlined is true But that's not something I care about for audio workstations [IMG]http://linuxmusicians.com/images/smilies/icon_wink.gif[/IMG]
For me this works.
```
ps -Leo rtprio,cmd,pid  | grep irq
     - [ksoftirqd/0]                   3
     - [ksoftirqd/1]                  26
     - [ksoftirqd/2]                  31
     - [ksoftirqd/3]                  36
     - [kvm-irqfd-clean]             624
     - /usr/sbin/irqbalance         1073
     - grep --color=auto irq        8208

```

---

### Post by Milos_SD on 2014-03-19
@runrickus: I never sad that 3.14.0-031400rc7-lowlatency is RT. It does have things needed for lowlatency (full preempt and 1000Hz), but it doesn't have realtime patchset. :)

---

### Post by QDR06VV9 on 2014-03-19
> **Milos_SD said:**
> @runrickus: I never sad that 3.14.0-031400rc7-lowlatency is RT. It does have things needed for lowlatency (full preempt and 1000Hz), but it doesn't have realtime patchset. :)
Ok Must have misunderstood [THIS]("http://ubuntuforums.org/showthread.php?t=2210336&page=3")  post #24
Do you see any Problems with my layout?

---

### Post by zika on 2014-03-19
> **runrickus said:**
> The underlined is true But that's not something I care about for audio workstations [IMG]http://linuxmusicians.com/images/smilies/icon_wink.gif[/IMG]
For me this works.
```
ps -Leo rtprio,cmd,pid  | grep irq
     - [ksoftirqd/0]                   3
     - [ksoftirqd/1]                  26
     - [ksoftirqd/2]                  31
     - [ksoftirqd/3]                  36
     - [kvm-irqfd-clean]             624
     - /usr/sbin/irqbalance         1073
     - grep --color=auto irq        8208

```Irqbalance is (in my book, I might be wrong, a great no-no for audio...
Just a snapshot:```
:~$ ps -e|grep irq
    3 ?        00:00:08 ksoftirqd/0
   26 ?        00:00:08 ksoftirqd/1
   31 ?        00:00:08 ksoftirqd/2
   44 ?        00:00:00 irq/9-acpi
   69 ?        00:01:10 irq/19-ehci_hcd
   70 ?        00:00:00 irq/16-ohci_hcd
   71 ?        00:00:00 irq/17-ohci_hcd
   72 ?        00:00:00 irq/18-ohci_hcd
   73 ?        00:00:00 irq/17-ohci_hcd
   74 ?        00:00:00 irq/18-ohci_hcd
   76 ?        00:00:00 irq/12-i8042
   77 ?        00:00:00 irq/1-i8042
   79 ?        00:00:00 irq/8-rtc0
  144 ?        00:00:00 irq/14-pata_ati
  145 ?        00:00:00 irq/15-pata_ati
  151 ?        00:00:03 irq/22-ahci
  407 ?        00:00:00 irq/16-snd_hda_
  408 ?        00:00:00 irq/43-snd_hda_
  451 ?        00:00:23 irq/44-radeon
  704 ?        00:00:09 irq/42-eth0
```

---

### Post by QDR06VV9 on 2014-03-19
> **zika said:**
> Irqbalance is (in my book, I might be wrong, a great no-no for audio...
Just a snapshot:```
:~$ ps -e|grep irq
    3 ?        00:00:08 ksoftirqd/0
   26 ?        00:00:08 ksoftirqd/1
   31 ?        00:00:08 ksoftirqd/2
   44 ?        00:00:00 irq/9-acpi
   69 ?        00:01:10 irq/19-ehci_hcd
   70 ?        00:00:00 irq/16-ohci_hcd
   71 ?        00:00:00 irq/17-ohci_hcd
   72 ?        00:00:00 irq/18-ohci_hcd
   73 ?        00:00:00 irq/17-ohci_hcd
   74 ?        00:00:00 irq/18-ohci_hcd
   76 ?        00:00:00 irq/12-i8042
   77 ?        00:00:00 irq/1-i8042
   79 ?        00:00:00 irq/8-rtc0
  144 ?        00:00:00 irq/14-pata_ati
  145 ?        00:00:00 irq/15-pata_ati
  151 ?        00:00:03 irq/22-ahci
  407 ?        00:00:00 irq/16-snd_hda_
  408 ?        00:00:00 irq/43-snd_hda_
  451 ?        00:00:23 irq/44-radeon
  704 ?        00:00:09 irq/42-eth0
```
Advise Taken.;)
I have been a crazed man [IMG]http://www.sherv.net/cm/emo/angry/smashing-computer.gif[/IMG] I want my Superb Audio back that I had on maverick!!
I am so close, but like a moth to flame(LOL) Im going to try implementing some packages from ubuntu-studio
This **will** be fun!?!

---

### Post by QDR06VV9 on 2014-03-19
> **zika said:**
> Irqbalance is (in my book, I might be wrong, a great no-no for audio...
You were of course correct! Into a streaming audio session I was getting about 2 seconds of jittering resume to normal and 
again a few minutes later.
Latest:
```
set ENABLED=0 in /etc/default/irqbalance
```

---

### Post by zika on 2014-03-19
> **runrickus said:**
> You were of course correct! Into a streaming audio session I was getting about 2 seconds of jittering resume to normal and 
again a few minutes later.
Latest:
```
set ENABLED=0 in /etc/default/irqbalance
```
Or```
echo "manual" | sudo tee /etc/init/irqbalance.override
```...

---

### Post by QDR06VV9 on 2014-03-19
> **zika said:**
> Or```
echo "manual" | sudo tee /etc/init/irqbalance.override
```...
Done 
Your kind of handy to have around:D.
At last I have Achieved Perfection [SIZE=4]**Yeah Me**[/SIZE]!
Just Installed ubuntu-studio session!
OMG!! Toys everywhere!(fiendish grin) How Come nobody suggested XFCE to me before(as I duck the flying fists)
Any way with all the goodies I am a very happy camper!
Who Needs a RT kernel anyway <overrated>:p
Even Though I can achieve RT in studio and a patch. <again overrated>
Great Job Studio Devs!! XFCE was an added bounus!;)
[IMG]http://replygif.net/i/675.gif[/IMG]

---

### Post by zika on 2014-03-21
It bugged me so hard that I had to try. I've removed all rt and lowlatency adjustments on a machine that came to my desk. I've got onto it newest PulseAudio and used just vanilla settings... It works like a charm, even better in some cases than heavily tweaked rt and lowlatency environment does... So, caveat my friends... I've even reduced all other tweaks on that machine (in BIOS etc.) and found out that PA even likes more not super-charged settings of memory etc but the most relaxed one... One other caveat: refrain from using AppArmor or You will get piles of /run/shm/pulse-shm* files... Even without AppArmor You do get them but in much less manner... I'll have to investigate those shared-memory files, that's something that might riun Your PA experience... Nothing nice cron job could not fix... ;)

---

### Post by QDR06VV9 on 2014-03-21
> **zika said:**
>  Even without AppArmor You do get them but in much less manner... I'll have to investigate those shared-memory files, that's something that might riun Your PA experience... Nothing nice cron job could not fix... ;)
Yes I get them!
This will not fix those however have you tried “KXStudio Team” team PPA
Latency Audio?
If you want here is the info
```
“KXStudio Team” team PPA
Latency Audio
https://launchpad.net/~kxstudio-team/+archive/ppa
```
I was in heaven yesterday just listening to my new audio box:D I feel like a kid in  a candy store!!\\:D/

---

### Post by zika on 2014-03-21
> **runrickus said:**
> Yes I get them!
This will not fix those however have you tried &#8220;KXStudio Team&#8221; team PPA
Latency Audio?
If you want here is the info
```
&#8220;KXStudio Team&#8221; team PPA
Latency Audio
https://launchpad.net/~kxstudio-team/+archive/ppa
```
I was in heaven yesterday just listening to my new audio box:D I feel like a kid in  a candy store!!\\:D/I'm glad You're happy...
I've done much for sound in last 24 hours going just exactly the opposite way I've been doing for months...
As for tha ppa You've suggested, I like headline:
> 
DO NOT USE THIS PPA!
 See the updated instructions here:
[http://kxstudio.sourceforge.net/Repositories](http://kxstudio.sourceforge.net/Repositories)but I still used jack from there to see what's new... ;)
It seems I've found the way to fight jack refusing sometimes stubbornly to restart... Just because of those /run/shm/pulse-shm* files...
Great weekend for hacking sound... :)

---

### Post by QDR06VV9 on 2014-03-21
> **zika said:**
> I'm glad You're happy...
I've done much for sound in last 24 hours going just exactly the opposite way I've been doing for months...

1st. Thank You. You have been a tremendous time saver for me.  Can't forget Milos_SD Much appreciated. 
2nd I have totally changed the way I handle my audio now!:guitar:

```
As for tha ppa You've suggested, I like headline:
 	 		 			 			 				DO NOT USE THIS PPA!
 See the updated instructions here:
[http://kxstudio.sourceforge.net/Repositories](http://kxstudio.sourceforge.net/Repositories) 			 		
 	
 
but I still used jack from there to see what's new... :wink:
```
I had a hunch.;)
```
Great weekend for hacking sound... :smile:
```
Indeed! Have A Great Weekend zika.
Regards

---

### Post by zika on 2014-04-01
Couple of kernel-boot-line-switches made it even nicer... ;)
Even made be go back to lowlatency...
Can hardly wait for some of new stuff in 3.15: [http://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/?id=971eae7c99212dd67b425a603f1fe3b763359907](http://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/?id=971eae7c99212dd67b425a603f1fe3b763359907) ...

---

### Post by QDR06VV9 on 2014-04-01
Just got done reading that!
My excitement is also hopeful and high.:)

---

### Post by zika on 2014-04-01
It might even creep into 999 kernel before 3.15-rc1 gets cooked... ;)
[http://www.phoronix.com/scan.php?page=news_item&px=MTY1MDg](http://www.phoronix.com/scan.php?page=news_item&px=MTY1MDg)

---

### Post by zika on 2014-04-02
As I've anticipated: take a look at today's 999 kernel changes... ;)

---

### Post by cariboo on 2014-08-19
To keep others from adding to this outdated thread, it is now closed.

---

