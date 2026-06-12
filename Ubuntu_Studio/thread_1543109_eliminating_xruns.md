---
title: "eliminating xruns"
date: 2010-07-31
forum: Ubuntu Studio
---

### Post by oleink on 2010-07-31
Hey,
I worked to eliminate xruns but I still get crackling and stuff like that.  I was wondering if an interface (I'm getting one either way) would help reduce and lower xruns and if I would be able to make my latency better with an interface.  my onboard sound isn't the greatest. It is a SigmaTel STAC9228 and ATI RS690/780 HDMI.  So if anyone could either help me reduce xruns extremely and/or let me know if an interface would be helpful in making the sound quality better, eliminating xruns, and being able to make the latency better that would be helpful.  Thanks a ton in advance

-Jordan

---

### Post by JC Cheloven on 2010-07-31
First thing to see is whether your system is properly configured for audio or not. Do you have a  working rt kernel, and such? Here you have a [quick checklist]("http://ubuntuforums.org/showthread.php?t=1525165&page=2") (it's for lubuntu but anyway).

As for the external device, your question is rather complex to answer. Which kind of device are you thinking about? Anyway, you can stretch your latency as far as you don't experience xruns, which in turn depends on many factors, both hardware and configuration related. A decent device will be always better than an integrated sigmatel audio chip though,

In the forums, there are plenty of user experiences which can give you a clue on what to expect. Here are some recent ones in which I participated (not saying they're better because of that LOL):

[http://ubuntuforums.org/showthread.php?t=1505953](http://ubuntuforums.org/showthread.php?t=1505953)
[http://ubuntuforums.org/showthread.php?t=1324473&page=2](http://ubuntuforums.org/showthread.php?t=1324473&page=2)
[http://ubuntuforums.org/showthread.php?t=1449800](http://ubuntuforums.org/showthread.php?t=1449800)

Hope this helps
JC

---

### Post by oleink on 2010-07-31
> **JC Cheloven said:**
> First thing to see is whether your system is properly configured for audio or not. Do you have a  working rt kernel, and such? Here you have a [quick checklist]("http://ubuntuforums.org/showthread.php?t=1525165&page=2") (it's for lubuntu but anyway).

As for the external device, your question is rather complex to answer. Which kind of device are you thinking about? Anyway, you can stretch your latency as far as you don't experience xruns, which in turn depends on many factors, both hardware and configuration related. A decent device will be always better than an integrated sigmatel audio chip though,

In the forums, there are plenty of user experiences which can give you a clue on what to expect. Here are some recent ones in which I participated (not saying they're better because of that LOL):

[http://ubuntuforums.org/showthread.php?t=1505953](http://ubuntuforums.org/showthread.php?t=1505953)
[http://ubuntuforums.org/showthread.php?t=1324473&page=2](http://ubuntuforums.org/showthread.php?t=1324473&page=2)
[http://ubuntuforums.org/showthread.php?t=1449800](http://ubuntuforums.org/showthread.php?t=1449800)

Hope this helps
JC

Thanks a bunch for the reply.  I had lowlatency kernel installed.  But now I just installed Maverick and was wondering where i should get the rt for it but I'm about to google it and do some research.  I had an rt kernel but not now

Also btw I'm going with a cheap interface but i figured it would still be better than the onboard and was hoping i'd be able to bump some things up.  I can go at 44100hz now with 128 (for most things but sometimes need higher) frames/period without any noticeable xruns (although I haven't recorded because I don't have an interface yet) and was hoping the external sound card would be able to help me bump it to 44800 and 64 or 32

---

### Post by oleink on 2010-07-31
> **JC Cheloven said:**
> First thing to see is whether your system is properly configured for audio or not. Do you have a  working rt kernel, and such? Here you have a [quick checklist]("http://ubuntuforums.org/showthread.php?t=1525165&page=2") (it's for lubuntu but anyway).

As for the external device, your question is rather complex to answer. Which kind of device are you thinking about? Anyway, you can stretch your latency as far as you don't experience xruns, which in turn depends on many factors, both hardware and configuration related. A decent device will be always better than an integrated sigmatel audio chip though,

In the forums, there are plenty of user experiences which can give you a clue on what to expect. Here are some recent ones in which I participated (not saying they're better because of that LOL):

[http://ubuntuforums.org/showthread.php?t=1505953](http://ubuntuforums.org/showthread.php?t=1505953)
[http://ubuntuforums.org/showthread.php?t=1324473&page=2](http://ubuntuforums.org/showthread.php?t=1324473&page=2)
[http://ubuntuforums.org/showthread.php?t=1449800](http://ubuntuforums.org/showthread.php?t=1449800)

Hope this helps
JC

ok got the real time kernel which reduced xruns by itself (i'm getting no crackling a 44800mhz and 128 frames/period and depending on what software I'm using i can set to 64 frames a period too.)  Now,  I'm not sure how to adjust the /etc/security/limits.conf file for my hardware and such.  That I will need help on.. Any help appreciated

---

### Post by JC Cheloven on 2010-08-01
> **oleink said:**
>  (...) Now,  I'm not sure how to adjust the /etc/security/limits.conf file for my hardware and such.  That I will need help on.. Any help appreciated

Try this, it's a usual recommendation that should work just fine ```

@audio - rtprio 99
@audio - memlock unlimited
```

As for the card, if PCI isn't an option (because I understand we're talking about a laptop), then cheap==usb. 
I'd say that your potential market starts from a very basic device (for ex, something from turtle beach, available for some 15eur I think), to something as the m-audio FastTrack, able to record at 48kHz, 24bit (about 78eur if memory helps). Be aware that the set of audio cards which works in linux is quite small compared to the general market. So, search in the forums before purchase!

JC

---

### Post by AutoStatic on 2010-08-01
Other things you could consider:
[LIST][*]Disable CPU frequency scaling
[*]Disable Compiz (Desktop Effects)
[*]Don't use a bloated DE like Gnome or KDE but use a lighter one (XFCE, LXDE or for the less faint hearted something like Fluxbox, Openbox, Awesome or IceWM)
[*]Run the realtimeconfigquickscan script: [http://realtimeconfigquickscan.googlecode.com/hg/realTimeConfigQuickScan.pl](http://realtimeconfigquickscan.googlecode.com/hg/realTimeConfigQuickScan.pl)
And try to follow the pointers it gives
[*]Check your IRQ's, your soundcard might share an IRQ with other devices
[*]Refrain from using Ubuntu alpha releases
[/LIST]

---

### Post by oleink on 2010-08-01
> **JC Cheloven said:**
> Try this, it's a usual recommendation that should work just fine ```

@audio - rtprio 99
@audio - memlock unlimited
```

As for the card, if PCI isn't an option (because I understand we're talking about a laptop), then cheap==usb. 
I'd say that your potential market starts from a very basic device (for ex, something from turtle beach, available for some 15eur I think), to something as the m-audio FastTrack, able to record at 48kHz, 24bit (about 78eur if memory helps). Be aware that the set of audio cards which works in linux is quite small compared to the general market. So, search in the forums before purchase!

JC

alright sweet thanks!

---

### Post by oleink on 2010-08-01
> **AutoStatic said:**
> Other things you could consider:
[LIST][*]Disable CPU frequency scaling
[*]Disable Compiz (Desktop Effects)
[*]Don't use a bloated DE like Gnome or KDE but use a lighter one (XFCE, LXDE or for the less faint hearted something like Fluxbox, Openbox, Awesome or IceWM)
[*]Run the realtimeconfigquickscan script: [http://realtimeconfigquickscan.googlecode.com/hg/realTimeConfigQuickScan.pl](http://realtimeconfigquickscan.googlecode.com/hg/realTimeConfigQuickScan.pl)
And try to follow the pointers it gives
[*]Check your IRQ's, your soundcard might share an IRQ with other devices
[*]Refrain from using Ubuntu alpha releases
[/LIST]

alright. I've got gnome installed but I guess i could install a different Desktop interface.  Though Gnome is actually less bloated than XFCE (only in ubuntu) and is definitely lihgter than windows and osx

---

### Post by mango42 on 2010-08-01
I've noticed quite a few posts advocating the inclusion of ```
@audio - memlock unlimited
``` in limits.conf - I suppose this is provisional on Jack calculating the actual locked memory required, as it always throws out an error message to the effect that 'unlimited' is 'dangerous'?

@**AutoStatic** Can you recommend a blow-by-blow account on the best way of removing (or at least not booting into..!) Gnome, which I like, to XFCE, of which I have no experience...yet :)

Anything to squeeze some more performance (and less xruns when I try to run JAMin) out of this Thinkpad whilst I wrestle with 64bit & ffado on the other box.

ps: Hope you had a great holiday.

---

### Post by trulan on 2010-08-01
> **AutoStatic said:**
> Refrain from using Ubuntu alpha releases
LOL - you don't say?

Actually I've had quite a lot of fun using Ubuntu Alpha releases - that's a great learning experience.  Of course if you're running the Alpha, rather than expecting it to work, you should count it a pleasant, unexpected surprise when it actually does work.

(FWIW - The big audio-related change in Ubuntu Maverick is the switch from the old legacy firewire driver stack to the new Juju stack - that's what pulled me into Maverick testing.  There's still a few kinks to work out of the new setup, of course.  But things are definitely moving in the right direction for us firewire audio guys.  Exciting stuff!)

Back to the matter at hand - Autostatic gave a great list of potential causes for xruns - CPU scaling is a big culprit, and IRQ conflicts are also a common problem for laptops.

---

### Post by trulan on 2010-08-01
> **mango42 said:**
> I've noticed quite a few posts advocating the inclusion of ```
@audio - memlock unlimited
``` in limits.conf - I suppose this is provisional on Jack calculating the actual locked memory required, as it always throws out an error message to the effect that 'unlimited' is 'dangerous'?
I've never seen a definitive answer on this.  Jack throws an error if memlock is unlimited, Ardour throws an error if it isn't unlimited.  Both programs come from the basically the same people - go figure...

> @**AutoStatic** Can you recommend a blow-by-blow account on the best way of removing (or at least not booting into..!) Gnome, which I like, to XFCE, of which I have no experience...yet :)

Anything to squeeze some more performance (and less xruns when I try to run JAMin) out of this Thinkpad whilst I wrestle with 64bit & ffado on the other box.
I'm not Autostatic, but I've done this a few times - Basically you just install xubuntu-desktop (for XFCE) or lubuntu-desktop (for LXDE) and that will pull all the necessary dependencies.  Then you can choose which one to boot in the sessions box at the gdm login screen (after you select your username but before you enter your password).  

Removing a desktop environment (should you choose to do so) is a bit harder - or maybe I just didn't do it right.  I recently converted my old desktop from Xubuntu to Lubuntu (LXDE has improved quite a bit recently, and its footprint is even smaller than XFCE).  I just started removing packages in Synaptic, and watching carefully what else it wanted to remove.

---

### Post by oleink on 2010-08-01
> **trulan said:**
> I've never seen a definitive answer on this.  Jack throws an error if memlock is unlimited, Ardour throws an error if it isn't unlimited.  Both programs come from the basically the same people - go figure...


I'm not Autostatic, but I've done this a few times - Basically you just install xubuntu-desktop (for XFCE) or lubuntu-desktop (for LXDE) and that will pull all the necessary dependencies.  Then you can choose which one to boot in the sessions box at the gdm login screen (after you select your username but before you enter your password).  

Removing a desktop environment (should you choose to do so) is a bit harder - or maybe I just didn't do it right.  I recently converted my old desktop from Xubuntu to Lubuntu (LXDE has improved quite a bit recently, and its footprint is even smaller than XFCE).  I just started removing packages in Synaptic, and watching carefully what else it wanted to remove.

Honestly XFCE is pretty bloated.  May i suggest LXDE.  Honestly I love it and it is pretty smooth and way less bloated than XFCE which is actually more bloated than gnome (as far as ubuntu goes.)  At least if you use XFCE take a look at this itll help eliminate some bloat [http://art.ubuntuforums.org/showthread.php?p=8051487]("http://art.ubuntuforums.org/showthread.php?p=8051487")

Honestly I think I may stick with gnome for recording.  LXDE is certainly the fastest of all but it is buggy....  Anyway so XFCE is bloated and LXDE is buggy.  XFCE actually takes up about a gig and a half more space than gnome (ONLY IN UBUNTU** Note that I'm not saying xfce isn't generally lightweight.)  Like I've said LXDE is a bit buggy and that isn't helpful.  KDE was pretty much a disapointment to me.  It was slower than gnome for me and kinda grossed me out with how it looked and performed.  I like sleek and smooth and Gnome is the closest you can get IMHO out of ANY operating system I've ever tried (Remember XFCE is normally more lightweight than gnome but we have a problem with it in ubuntu for some reason and it comes with way too much bulk.)  Honestly I love lubuntu too but as i said LXDE is buggy

---

### Post by JC Cheloven on 2010-08-01
@ trulan, mango42:
In my experience, the memlock thing is somehow as the swap. 
- In theory, you may get out of ram, and this sounds terrible, but swap will save you in that situation. In practice, if you have a reasonably recent pc, swap will be never used and it becomes a pretty useless waste of space. Other people will say it's like condoms: "better having it and don't needing it, than the opposite". To each one his own :)
- In theory, memlock=unlimited could use all you ram for audio, which sounds terrible. In practice that never happens, and (I've read somewhere) should be a worry only in multi-user environments. But do you know anyone doing audio in a multiuser machine?.
Nevertheless, I didn't advocate for memlock=unlimited, it was a compromise answer to avoid answering Oleink with another question. Please note than in the [link I gave him formerly]("http://ubuntuforums.org/showthread.php?t=1525165&page=2"), a value of 650000 was suggested for memlock, for a machine with 1 Gb ram.

@ oleink:
Regarding your last post, when talking about FOSS, Gnu-Linux, and how they compare to xyz alternatives (usually proprietary ones), I often say "It will improve if we use it".
So if you think that lxde/LUbuntu **could** optimally fit your needs, but is buggy at the moment, it makes sense for you trying to use it (perhaps as dual boot), help building a community around those, reporting bugs, and making it improve as far as you can. Free software are us; if everyone waits until things get better by themselves, they will never get better.

---

### Post by oleink on 2010-08-01
> **JC Cheloven said:**
> 
@ oleink:
Regarding your last post, when talking about FOSS, Gnu-Linux, and how they compare to xyz alternatives (usually proprietary ones), I often say "It will improve if we use it".
So if you think that lxde/LUbuntu **could** optimally fit your needs, but is buggy at the moment, it makes sense for you trying to use it (perhaps as dual boot), help building a community around those, reporting bugs, and making it improve as far as you can. Free software are us; if everyone waits until things get better by themselves, they will never get better.

I agree 100%.  It is LXDE itself that is buggy.  It would have to be to help LXDE get better because Ubuntu is doing a good job with Lubuntu itself:  In fact they've fixed some of the bugginess (if i can use that word) with some of their other software

---

### Post by mango42 on 2010-08-02
[QUOTE="trulan"]Removing a desktop environment (should you choose to do so) is a bit harder - or maybe I just didn't do it right.[/QUOTE]

I wouldn't dare unless I was ready for a complete re-install anyway! If *you* have trouble then I know not to go there ;)

Many thanks for the responses. Sounds like I'll be sticking with Gnome for the foreseeable future. However there's a bit of a catch22 in your excellent advice to 'pitch in' with helping to identify bugs, **JC Cheloven**, as it presupposes the user actually realises what's going on and can identify what the problem might be! Personally, I find that 99 times out of 100 it turns out to be 'user error' anyway ;)

This area is perhaps best left to those amongst us who program daily and are well up to speed on the foibles and intricacies of real time Linux. Having said that, I am daily blown away by the sheer flexibility and smoothness of operation of UbuntuStudio - It was never this much fun before :D

---

### Post by AutoStatic on 2010-08-02
> **mango42 said:**
> I've noticed quite a few posts advocating the inclusion of ```
@audio - memlock unlimited
``` in limits.conf - I suppose this is provisional on Jack calculating the actual locked memory required, as it always throws out an error message to the effect that 'unlimited' is 'dangerous'?Setting it to unlimited could be dangerous, especially on systems with little RAM. With this setting you're allowing processes to use all available memory so you're running the risk of locking your machine up because it's out of memory. But on most modern systems this should be no issue. I always set memlock to unlimited and never encountered any serious problems.

> **mango42 said:**
> @**AutoStatic** Can you recommend a blow-by-blow account on the best way of removing (or at least not booting into..!) Gnome, which I like, to XFCE, of which I have no experience...yet :)I don't use XFCE myself, I prefer IceWM. What I always do is installing IceWM, create a specific music account, choose IceWM as the Desktop Environment in GDM and that's it actually. I don't uninstall Gnome, simply because I'm still having other accounts on those machines that use Gnome. Also, some parts of Gnome can also be of use in an IceWM session. And of course I have to configure my IceWM session afterwards.

> **mango42 said:**
> ps: Hope you had a great holiday.Yeah, it was great! I even managed to record/create some ideas despite all the Kronenbourps :D

[http://linux.autostatic.com/temp/theinfiniterepeat-sleepylittlelou-mixdown.ogg](http://linux.autostatic.com/temp/theinfiniterepeat-sleepylittlelou-mixdown.ogg)

---

### Post by oleink on 2010-08-02
> **AutoStatic said:**
> Setting it to unlimited could be dangerous, especially on systems with little RAM. With this setting you're allowing processes to use all available memory so you're running the risk of locking your machine up because it's out of memory. But on most modern systems this should be no issue. I always set memlock to unlimited and never encountered any serious problems.

I don't use XFCE myself, I prefer IceWM. What I always do is installing IceWM, create a specific music account, choose IceWM as the Desktop Environment in GDM and that's it actually. I don't uninstall Gnome, simply because I'm still having other accounts on those machines that use Gnome. Also, some parts of Gnome can also be of use in an IceWM session. And of course I have to configure my IceWM session afterwards.

Yeah, it was great! I even managed to record/create some ideas despite all the Kronenbourps :D

[http://linux.autostatic.com/temp/theinfiniterepeat-sleepylittlelou-mixdown.ogg](http://linux.autostatic.com/temp/theinfiniterepeat-sleepylittlelou-mixdown.ogg)

wow iceWM looks pretty good

---

### Post by AutoStatic on 2010-08-02
It sure does :)

---

### Post by oleink on 2010-08-02
> **AutoStatic said:**
> It sure does :)

Thanks.  I'll have to look into that more :popcorn:

---

### Post by mango42 on 2010-08-03
Yes, setting up separate accounts sounds eminently sensible, as does a separate /home partition. Hmm, time for a brush with Clonezilla and a clean out. Thanks for the advice.

[QUOTE="AutoStatic"]Yeah, it was great! I even managed to record/create some ideas despite all the Kronenbourps[/QUOTE]

LOL - you certainly have some notable brews up your way. I'm teetotal but can't resist an occasional Leffe if it's offered - just for the taste, mind ;) Did you get to 'sample' the after-FX from those two wheelbarrow-fuls? ;-)

I'm off to hear your latest and check out IceWM...

---

### Post by oleink on 2010-08-04
I'm still running into a lot of xruns and idk what to do

---

### Post by oleink on 2010-08-04
I cut it way down and now I only get xruns when opening certain softwares.  Btw will I be able to get better latency with a uca222 than my onboard sound (SigmaTel STAC9228)

---

### Post by AutoStatic on 2010-08-05
Probably yes, that STAC onboard thingy is pretty horrible. Got a similar soundchip in my notebook and anything is better than that.

---

### Post by oleink on 2010-08-05
> **AutoStatic said:**
> Probably yes, that STAC onboard thingy is pretty horrible. Got a similar soundchip in my notebook and anything is better than that.

Haha alright thanks a bunch.  Right now I'm pretty broke but I ordered the behringer interface because it was like the only thing I could afford and if I can get a better latency with it now that'll be great because I have already been able to pull off what some people consider to be decent latency and only get xruns when I open certain applications while qjackctl is running.  Thanks (eventually I'll get something professional but that'll be a while from now and I can at least start with the uca222)

---

### Post by JC Cheloven on 2010-08-06
> **oleink said:**
> Haha alright thanks a bunch.  Right now I'm pretty broke but I ordered the behringer interface because it was like the only thing I could afford and if I can get a better latency with it now that'll be great because I have already been able to pull off what some people consider to be decent latency and only get xruns when I open certain applications while qjackctl is running.  Thanks (eventually I'll get something professional but that'll be a while from now and I can at least start with the uca222)

Just a question: do you experience also xruns when not using jack? Have you tried a simpler recording program using directly the alsa driver? 
For the shake of testing this, I can suggest the simplest (well, whithin reasonable) I'm aware of: MHWaveedit. It's in the repos.

Either way, please come back with your experiences with the behringer device!

JC

---

### Post by oleink on 2010-08-06
> **JC Cheloven said:**
> Just a question: do you experience also xruns when not using jack? Have you tried a simpler recording program using directly the alsa driver? 
For the shake of testing this, I can suggest the simplest (well, whithin reasonable) I'm aware of: MHWaveedit. It's in the repos.

Either way, please come back with your experiences with the behringer device!

JC

I havent tried with other stuff no... Maybe I should.  I've actually been able to reach 17.4msec latency which isn't fantastic but it's ok with the onboard sound.  With the UCA222 I'm hoping to closer to 10msec or lower... Hopefully that's a reasonable goal although even 17.4 isn't really noticeable as it is (I needed the usb in for recording anyway {got a mixer to go with it} and am hoping i can acheive lower latency at the same time.) thanks again and I will report back as soon as I have some tests.

---

### Post by oleink on 2010-08-07
UCA222 came in today and like i said I had had a 17msec latency.  I am able to acheive about a 10msec latency now with xruns only when opening or closing certain programs

---

### Post by oleink on 2010-08-07
quick questions:  Would it be smarter for me to partition my drive and run a distro specifically for recording with no extra software installed?
Can LXDE run all the Ubuntu Studio/64 Studio software?

---

### Post by JC Cheloven on 2010-08-07
> **oleink said:**
> quick questions:  Would it be smarter for me to partition my drive and run a distro specifically for recording with no extra software installed?
NOT, IMO. But perhaps you should consider: 
1) Several kernels to boot in grub. It's generally advised to have at least one regular kernel (not rt) to boot from.
2) Several desktop environments to choose from (several kinds of sessions), at the time of booting. So you can choose gnome or openbox or whatever.

> Can LXDE run all the Ubuntu Studio/64 Studio software?
In my experience, yes. I managed to do everything I needed, after proper configuration (which in general is not that different). Only some dedicated desktop software (compiz, a nice menu editor, a nice keyboard shortcut editor...) will be missing.

---

### Post by oleink on 2010-08-08
> **JC Cheloven said:**
> NOT, IMO. But perhaps you should consider: 
1) Several kernels to boot in grub. It's generally advised to have at least one regular kernel (not rt) to boot from.
2) Several desktop environments to choose from (several kinds of sessions), at the time of booting. So you can choose gnome or openbox or whatever.


In my experience, yes. I managed to do everything I needed, after proper configuration (which in general is not that different). Only some dedicated desktop software (compiz, a nice menu editor, a nice keyboard shortcut editor...) will be missing.
Ok cool cause I think LXDE will be way way faster than gnome.  My latency goal is 8.7 with no xruns and I'm at 10 now which isn't bad and you cant hear the delay

---

### Post by AutoStatic on 2010-08-08
There's still so much you could tweak to achieve lower latencies:
[list][*]Use the noatime and nodiratime parameters in your fstab (Ubuntu defaults to relatime afaik)
[*]Use Ext3 instead of Ext4, although I think with the 2.6.31 realtime kernel you shouldn't experience much difference
[*]Use rtirq-init to prioritize the USB stuff (you need a realtime kernel for this, no preempt one)
[*]Run JACK at a higher priority, by default it runs at 50 afaik. Try 70 for example (not higher, then JACK could get in the way of other important processes)
[*]Add a line to your */etc/sysctl.conf* file concerning inotify to reduce overhead: ```
fs.inotify.max_user_watches = 524288
```
[*]Add a line to your */etc/sysctl.conf* file to prevent xruns caused by swapping:```
vm.swappiness = 10
```
[*]Use a lighter DE
[*]Disable the Ondemand service if you don't need it (when you're on a desktop for example)
[*]Disable all other services you don't need for audio production: bluetooth, cups, kerneloops, ondemand, pulseaudio, saned, winbind etc.[/list]

And there's probably more you can do, for example I always uninstall apt-xapian-index because whenever its cronjob starts it's xruns galore.

---

### Post by oleink on 2010-08-08
> **AutoStatic said:**
> There's still so much you could tweak to achieve lower latencies:
[list][*]Use the noatime and nodiratime parameters in your fstab (Ubuntu defaults to relatime afaik)
[*]Use Ext3 instead of Ext4, although I think with the 2.6.31 realtime kernel you shouldn't experience much difference
[*]Use rtirq-init to prioritize the USB stuff (you need a realtime kernel for this, no preempt one)
[*]Run JACK at a higher priority, by default it runs at 50 afaik. Try 70 for example (not higher, then JACK could get in the way of other important processes)
[*]Add a line to your */etc/sysctl.conf* file concerning inotify to reduce overhead: ```
fs.inotify.max_user_watches = 524288
```
[*]Add a line to your */etc/sysctl.conf* file to prevent xruns caused by swapping:```
vm.swappiness = 10
```
[*]Use a lighter DE
[*]Disable the Ondemand service if you don't need it (when you're on a desktop for example)
[*]Disable all other services you don't need for audio production: bluetooth, cups, kerneloops, ondemand, pulseaudio, saned, winbind etc.[/list]

And there's probably more you can do, for example I always uninstall apt-xapian-index because whenever its cronjob starts it's xruns galore.

Thanks.  I'll do the swapiness and limits.conf editing (and maybe switch to lxde when recording).  I'm pretty new to linux still (not new new but I haven't been using it for more than about half a year probably.) what is noatime and nodiratime??

---

### Post by maghoxfr on 2010-08-08
This thread is gold! I'll try some of this stuff, because I'm still trying to achieve a fine performance for audio recording/playing.

---

### Post by AutoStatic on 2010-08-08
> **oleink said:**
> what is noatime and nodiratime??Those are mount parameters. from **man mount**:
> atime  Update inode access time for each access. This is the default. (edit: not for Ubuntu, Ubuntu uses relatime afaik)
noatime   Do not update inode access times on this file system (e.g, for faster access on the news spool to speed up news servers).
...
relatime   Update inode access times relative to modify or change time.  Access time is only updated if the previous access time was earlier than the current modify or change time. (Similar  to noatime, but doesn't break mutt or other applications that need to know if a file has been read since the last time it was modified.)

I'm just reading [here]("http://lwn.net/Articles/245002/") that noatime includes nodiratime. nodiratime is the equivalent of noatime, but then for directory inodes instead of (file) inodes.

But what noatime does is reducing disk writes/reads, so this could help in making your system perform better.

---

### Post by oleink on 2010-08-10
I did a fresh install and lowered my processes and was able to acheive an 8msec latency.  But I cannot check the qjackctl "realtime" box and I'm not sure why.. It won't start if it's checked

---

### Post by maghoxfr on 2010-08-10
I've just installed 2.6.31-12 realtime kernel from Igor Bogani's PPA and is running great. I was having drivers issues with my last rt kernel (2.6.31-11) but with this one I had to tweak nothing. I did an hour session and 0 xrun. That was not usual for me.

---

### Post by oleink on 2010-08-10
> **maghoxfr said:**
> I've just installed 2.6.31-12 realtime kernel from Igor Bogani's PPA and is running great. I was having drivers issues with my last rt kernel (2.6.31-11) but with this one I had to tweak nothing. I did an hour session and 0 xrun. That was not usual for me.

awesome maybe i should upgrade to that kernel:

I'm using 2.6.31-10

---

### Post by maghoxfr on 2010-08-10
I'm very far from being an expert, what I did was install it to try it out because I was having issues with the other rt kernels, and it was really too much for me to handle. But this kernel is working great, I even have the plymouth splash screen properly working with the right res. 

In terms of performance (which is what really matters) I could only test it for an hour or so, I'll test it further tonight.

> I'm pretty new to linux still (not new new but I haven't been using it for more than about half a year probably.)

Just like me. I'm hooked though...

---

### Post by oleink on 2010-08-10
> **maghoxfr said:**
> I'm very far from being an expert, what I did was install it to try it out because I was having issues with the other rt kernels, and it was really too much for me to handle. But this kernel is working great, I even have the plymouth splash screen properly working with the right res. 

In terms of performance (which is what really matters) I could only test it for an hour or so, I'll test it further tonight.



Just like me. I'm hooked though...

Awesome.  I'm hooked too!! I can't put my computer down most of the time which isn't good for my schoolwork unless I'm typing a paper

---

### Post by AutoStatic on 2010-08-10
> **maghoxfr said:**
> I've just installed 2.6.31-12 realtime kernel from Igor Bogani's PPA and is running great. I was having drivers issues with my last rt kernel (2.6.31-11) but with this one I had to tweak nothing. I did an hour session and 0 xrun. That was not usual for me.That kernel is from the beginning of March. Later on he moved it to his Broken PPA to ultimately delete it. I wonder where you got it from. Or am I overseeing something?

---

### Post by maghoxfr on 2010-08-10
Oh, I see. It wasn't in Bogani's PPA but on LP-PPA-falk-t-j-lucid/lucid. What test should I run to check it's performance? I didn't do any search but I will now, I just saw it on synaptic and didn't hesitate to try it, I was looking for a kernel I didn't had to tweak much and it looked perfect.

Is there any terminal based tests I could do to it?

[EDIT] I've found this [here]("https://bugs.launchpad.net/ubuntu/+source/linux-rt/+bug/534398")

Man, it was too good to be true. I'll have to go back and fight vs. 2.6.31-11 I guess.

---

### Post by RaumTrug on 2010-08-10
oleink: not setting the "realtime" option will result in very "unstable" (dropouts/xruns at high cpu load) jack sound! believe me, without even realtime kernel can't do much. I guess you'll be able to get better latencies (but 8ms is already good) when you manage to start jack in realtime mode.

what does the "messages" window say when you try to start qjackctl with realtime ticked? there should be some pointer to why it can't start up, if it's not telling any cause for jack shutting down again, try the "verbose output" option, too, it will make the messages window a bit more talkative.

I hope you have altered limits.conf/audio.conf realtime/memlock permissions already?

---

### Post by oleink on 2010-08-10
> **RaumTrug said:**
> oleink: not setting the "realtime" option will result in very "unstable" (dropouts/xruns at high cpu load) jack sound! believe me, without even realtime kernel can't do much. I guess you'll be able to get better latencies (but 8ms is already good) when you manage to start jack in realtime mode.

what does the "messages" window say when you try to start qjackctl with realtime ticked? there should be some pointer to why it can't start up, if it's not telling any cause for jack shutting down again, try the "verbose output" option, too, it will make the messages window a bit more talkative.

I hope you have altered limits.conf/audio.conf realtime/memlock permissions already?

I got it to work.  Thanks for your concern.  I can only do it in root though.  It says I'm not part of the audio group even though I am.  But it works in root and now I have real time and don't get any xruns at 8msec latency

---

### Post by AutoStatic on 2010-08-11
What does the **groups** command in a terminal give? And what does QjackCtl output exactly when you run it as a normal user?

---

### Post by oleink on 2010-08-11
> **AutoStatic said:**
> What does the **groups** command in a terminal give? And what does QjackCtl output exactly when you run it as a normal user?

jordan@jordan-laptop:~$ groups
jordan adm dialout cdrom audio video plugdev lpadmin admin sambashare




jordan@jordan-laptop:~$ qjackctl
Suspending PulseAudio

```
09:31:47.112 Patchbay deactivated.
09:31:47.115 Statistics reset.
09:31:47.290 ALSA connection graph change.
09:31:47.480 ALSA connection change.
09:32:02.854 Startup script...
09:32:02.857 artsshell -q terminate
sh: artsshell: not found
09:32:03.261 Startup script terminated with exit status=32512.
09:32:03.261 JACK is starting...
09:32:03.262 /usr/bin/jackd -dalsa -r48000 -p128 -n3 -D -Chw:2 -Phw:2
09:32:03.266 JACK was started with PID=2006.
jackd 0.118.0
Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
Memory locking is unlimited - this is dangerous. You should probably alter the line:
     @audio   -  memlock    unlimited
in your /etc/limits.conf to read:
     @audio   -  memlock    1444032
no message buffer overruns
JACK compiled with System V SHM support.
loading driver ..
Enhanced3DNow! detected
SSE2 detected
apparent rate = 48000
creating alsa driver ... hw:2|hw:2|128|3|48000|0|0|nomon|swmeter|-|32bit
control device hw:2
control open "hw:2" (No such file or directory)
ALSA lib pcm_hw.c:1401:(_snd_pcm_hw_open) Invalid value for card
ALSA lib pcm_hw.c:1401:(_snd_pcm_hw_open) Invalid value for card
ALSA: Cannot open PCM device alsa_pcm for playback. Falling back to capture-only mode
cannot load driver module alsa
09:32:04.310 JACK was stopped successfully.
09:32:04.311 Post-shutdown script...
09:32:04.311 killall jackd
jackd: no process found
09:32:04.728 Post-shutdown script terminated with exit status=256.
09:32:05.362 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
```

---

### Post by maghoxfr on 2010-08-11
@oleink

I don't know if this is what is happening to you but sometimes, in jack I have to specify which card to use because as I have other usb audio devices, their names change when tuning on/off the computer. I know there's a way to leave a fix name to each device but I hadn't any time to do so.

I have an usb webcam (that jack considers as a posible input) an usb interface and the onboard device. Their hw:_,_ change sometimes when I turn on the pc.

---

### Post by oleink on 2010-08-11
> **maghoxfr said:**
> @oleink

I don't know if this is what is happening to you but sometimes, in jack I have to specify which card to use because as I have other usb audio devices, their names change when tuning on/off the computer. I know there's a way to leave a fix name to each device but I hadn't any time to do so.

I have an usb webcam (that jack considers as a posible input) an usb interface and the onboard device. Their hw:_,_ change sometimes when I turn on the pc.

Yeah I've had that happen and thanks for the input.  That isn't the problem although when I posted my output I may have forgotten to change it because I didn't have my interface plugged in at the time.

---

### Post by oleink on 2010-08-11
> **AutoStatic said:**
> What does the **groups** command in a terminal give? And what does QjackCtl output exactly when you run it as a normal user?

I actually got it working now.  I don't know how this happened because I haven't edited the audio.conf file since the first time but somehow the @rtprio got # (commented) out.  Got rid of that and it works fine

---

### Post by AutoStatic on 2010-08-11
> **maghoxfr said:**
> I don't know if this is what is happening to you but sometimes, in jack I have to specify which card to use because as I have other usb audio devices, their names change when tuning on/off the computer. I know there's a way to leave a fix name to each device but I hadn't any time to do so.There are two ways to do this:
[LIST=1]
[*]The hard way: by editing */etc/modprobe.d/alsa-base.conf* and setting an index number for each soundcard on your system. You can then address each soundcard as hw:1, hw:2 etc. respectively
[*]The easy way: check the card names with **aplay -l** (you need the one between the brackets [] ) and use this name as in hw:cardname. You can enter this manually in the Interfaces field of the Setup window of QjackCtl or on the commandline.
[/LIST]

---

### Post by AutoStatic on 2010-08-11
> **oleink said:**
> I actually got it working now.  I don't know how this happened because I haven't edited the audio.conf file since the first time but somehow the @rtprio got # (commented) out.  Got rid of that and it works fineCool! Enjoy your tweaked system!

---

### Post by maghoxfr on 2010-08-11
> **AutoStatic said:**
> The easy way: check the card names with **aplay -l** (you need the one between the brackets [] ) and use this name as in hw:cardname. You can enter this manually in the Interfaces field of the Setup window of QjackCtl or on the commandline.


I'll take the easy way! Not that I'm lazy but I'm not a developer and changing code blindly takes lots of time and most of the times I end up breaking something in the system.

Thank you, I'll do it asap! :D

---

### Post by oleink on 2010-08-11
> **AutoStatic said:**
> Cool! Enjoy your tweaked system!

Thanks and thanks for all your help!

---

### Post by AutoStatic on 2010-08-11
The easy way is in this case also the best way imho. You address the card by its hardware name, that's where it's for! Besides, a designation like hw:1 is not as clear as hw:UA-25EX :p

---

### Post by maghoxfr on 2010-08-11
> **AutoStatic said:**
> The easy way is in this case also the best way imho. You address the card by its hardware name, that's where it's for! Besides, a designation like hw:1 is not as clear as hw:UA-25EX :p

I agree 100%. Little by little I am getting somewhere!

---

### Post by AutoStatic on 2010-08-11
Arrrgggh, you need the name between the brackets of the output of** cat /proc/asound/cards** :oops:

Sorry, time to go to bed...

---

### Post by maghoxfr on 2010-08-11
> **AutoStatic said:**
> Arrrgggh, you need the name between the brackets of the output of** cat /proc/asound/cards** :oops:

Sorry, time to go to bed...

Oh, allright, thank you very much. I'll try it tomorrow. I can't wait to get home and put my hands on my pc. I think I need help...not the kind this forum can provide! LOL

Thanks man

---

### Post by oleink on 2010-08-12
> **maghoxfr said:**
> This thread is gold! I'll try some of this stuff, because I'm still trying to achieve a fine performance for audio recording/playing.

This thread has been pretty cool.  Glad it helped other people too.

---

### Post by maghoxfr on 2010-08-12
@oleink

How much latency (ms) did you achieved in the end? And what DE did you choose? 

Right now I'm trying 2.6.33-6-rt (from bojo42 PPA) with the nVidia patched drivers (from falkTX PPA), so far doing good. I have IceWM and Openbox to try out too. I'll be doing some tweaks mentioned in this thread and I'd be good to go!!!

@Autostatic

Thanks for the tip on Qjackctl, it's working great.



> Add a line to your /etc/sysctl.conf file concerning inotify to reduce overhead:

[QUOTE]fs.inotify.max_user_watches = 524288
Add a line to your /etc/sysctl.conf file to prevent xruns caused by swapping:

> vm.swappiness = 10[/QUOTE]
I'm sorry to be asking this but, when you say "add a line" is just adding that line at the end of the file?

---

### Post by oleink on 2010-08-12
> **maghoxfr said:**
> @oleink

How much latency (ms) did you achieved in the end? And what DE did you choose? 

Right now I'm trying 2.6.33-6-rt (from bojo42 PPA) with the nVidia patched drivers (from falkTX PPA), so far doing good. I have IceWM and Openbox to try out too. I'll be doing some tweaks mentioned in this thread and I'd be good to go!!!

@Autostatic

Thanks for the tip on Qjackctl, it's working great.




I'm sorry to be asking this but, when you say "add a line" is just adding that line at the end of the file?

I got 8msec and I can probably do lower.  I don't get any xruns at 8.  I stuck with gnome.

And answering for autostatic:  Yeah add it at the end of the page (I know this isn't my question but i did that)

[http://webcache.googleusercontent.com/search?q=cache:YiU9EeYHb4QJ:www.zolved.com/synapse/view_content/28224/How_to_tune_your_Ubuntu_PC_for_faster_performance_+make+ubuntu+faster+swappiness&cd=1&hl=en&ct=clnk&gl=us]("http://webcache.googleusercontent.com/search?q=cache:YiU9EeYHb4QJ:www.zolved.com/synapse/view_content/28224/How_to_tune_your_Ubuntu_PC_for_faster_performance_+make+ubuntu+faster+swappiness&cd=1&hl=en&ct=clnk&gl=us")

---

### Post by maghoxfr on 2010-08-12
> **oleink said:**
> I actually got it working now.  I don't know how this happened because I haven't edited the audio.conf file since the first time but somehow the @rtprio got # (commented) out.  Got rid of that and it works fine

[Link 1]("https://help.ubuntu.com/community/UbuntuStudioPreparation")
> The nice setting has been commented out with a purpose, according to one of the main authors of JACK allowing users to renice processes is not necessary. 

[This]("http://wiki.linuxmusicians.com/doku.php?id=system_configuration#limits.conf") is good too.

---

### Post by oleink on 2010-08-12
> **maghoxfr said:**
> [Link 1]("https://help.ubuntu.com/community/UbuntuStudioPreparation")


[This]("http://wiki.linuxmusicians.com/doku.php?id=system_configuration#limits.conf") is good too.

seems like good stuff.  I'll have to take a look at it tomorrow

---

### Post by maghoxfr on 2010-08-13
I could only get 17.4 ms, I couldn't lower that. I guess that my humble Multimix 4 won't let me. I've added the swapiness and sysctl.conf lines suggested by autostatic, I set the CPU scaling to "performance", I tried lighter DE (openbox, IceWM), I have rtirq but haven't tweaked it ([this]("http://subversion.ffado.org/wiki/IrqPriorities") is too much for me, I don't dare to modify it blindly :confused:)... 

My audio.conf
```
@audio   -  rtprio     99
@audio   -  memlock    unlimited
#@audio   -  nice      -19
```

I didn't uncommented "#@audio   -  nice      -19" because on the link I posted it said that:
> According to Paul Davis, one of the authors of JACK, allowing users to renice processes in a real-time audio environment is: ... a mistake that has been propagated around the net for a few years. It has absolutely nothing useful to do with realtime, low latency audio and should not be used by apps or system configuration for this purpose. It's very unfortunate that this myth took hold.

Priority: 70
Frames/Period: 256
Sampling rate: 44100 (my card supports 16bit, 44100)
Periods/Buffer: 3

I can't even start jack with other settings (leaving 44100 fix). This long cycle error pops up when I assign 128 frames periods instead of 256 (but changing any parameter retrieves me the same error)latency should be 8.71 which would be awesome:
```
11:57:59.621 Script de inicio...
11:57:59.622 artsshell -q terminate
Cannot connect to server socket err = ConexiÃ³n rechazada
Cannot connect to server socket
jack server is not running or cannot be started
Cannot connect to server socket err = ConexiÃ³n rechazada
Cannot connect to server socket
jack server is not running or cannot be started
11:57:59.626 Cambió el gráfico de conexiones ALSA.
sh: artsshell: not found
11:58:00.023 El script de inicio finalizó con estado 32512.
11:58:00.023 JACK está iniciándose...
11:58:00.024 /usr/bin/jackd -P70 -p128 -dalsa -r44100 -p128 -n3 -D -Chw:default -Phw:2,1 -S -Xseq
11:58:00.026 JACK se inició con PID=2622.
no message buffer overruns
no message buffer overruns
jackdmp 1.9.5
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2009 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK server starting in realtime mode with priority 70
audio_reservation_init
Acquire audio card Audio0
Acquire audio card Audio2
creating alsa driver ... hw:2,1|hw:default|128|3|44100|0|0|nomon|swmeter|-|16bit
Using ALSA driver HDA-Intel running on card 2 - HDA NVidia at 0xdbef8000 irq 23
configuring for 44100Hz, period = 128 frames (2.9 ms), buffer = 3 periods
ALSA: final selected sample format for capture: 16bit little-endian
ALSA: use 3 periods for capture
ALSA: final selected sample format for playback: 16bit little-endian
ALSA: use 3 periods for playback
port created: Midi-Through:midi/playback_1
port created: Midi-Through:midi/capture_1
port created: TiMidity:midi/capture_1
port created: TiMidity:midi/capture_2
port created: TiMidity:midi/capture_3
port created: TiMidity:midi/capture_4
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
11:58:00.226 Cambios en las conexiones ALSA.
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
11:58:07.236 No puede conectarse al servidor JACK como cliente. - La operación global falló. - Error de comunicación con el servidor. Por favor revise la ventana de mensajes para mas información.
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
11:58:07.365 Cambió el gráfico de conexiones ALSA.
alsa_driv
11:58:07.370 JACK ha sido detenido satisfactoriamente.
11:58:07.371 Script de post - apagado...
11:58:07.372 killall jackd
11:58:07.375 JACK ha petado.
er_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
11:58:07.814 El script de post - apagado finalizó con estado 256.
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackProcessSync::LockedTimedWait error usec = 5000000 err = Connection timed out
Driver is not running
JackSocketClientChannel read fail
Cannot create new client
Cannot open qjackctl client
JackAudioDriver::ProcessAsync: read error, skip cycle
Unknown request -1
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
jackd: ../common/JackGraphManager.cpp:45: void Jack::JackGraphManager::AssertPort(jack_port_id_t): Assertion `port_index < fPortMax' failed.
jackd: proceso no encontrado
11:58:11.990 No puede conectarse al servidor JACK como cliente. - La operación global falló. - No puede conectarse al servidor. Por favor revise la ventana de mensajes para mas información.
Cannot connect to server socket err = ConexiÃ³n rechazada
Cannot connect to server socket
jack server is not running or cannot be started
11:58:20.811 No puede conectarse al servidor JACK como cliente. - La operación global falló. - No puede conectarse al servidor. Por favor revise la ventana de mensajes para mas información.
Cannot connect to server socket err = ConexiÃ³n rechazada
Cannot connect to server socket
jack server is not running or cannot be started
11:58:38.492 No puede conectarse al servidor JACK como cliente. - La operación global falló. - No puede conectarse al servidor. Por favor revise la ventana de mensajes para mas información.
Cannot connect to server socket err = ConexiÃ³n rechazada
Cannot connect to server socket
jack server is not running or cannot be started
```

However if i set sampling rate to 192000 I get 4ms latency no problem. My doubt is: if my audio interface (I use it as an IN while I set the onboard one as OUT) specs support 44100, how can it be that setting sampling rate to 192000 worksk fine? I suspect a total misconception about smapling rate from my part, but I've haven't read any place that eradicates that doubt of mine.

Thanks

---

### Post by AutoStatic on 2010-08-13
Matías, try using only your Alesis for both in and out. Using two completely different soundcards is causing your issues as far as I can tell. I've experimented with two different cards for a very short while, way to unstable at lower latencies.

---

### Post by maghoxfr on 2010-08-13
> **AutoStatic said:**
> Matías, try using only your Alesis for both in and out. Using two completely different soundcards is causing your issues as far as I can tell. I've experimented with two different cards for a very short while, way to unstable at lower latencies.

You are right, if I only use the Alesis I can get lower latencies with no problem! The only reason I had a two different cards for IN/OUT is because this card doesn't allow me to regulate the volume of the pc sound and the volume of the guitar IN of the console independently, so in the headhone mix, let's say I'm using rakarrack, I always listen to a clean guitar very loud and the fx from rakarrack softly on the background. If I could choose on the interface to listen only to the sound comming from the computer it'd be great but I don't think that's possible, withouth the intterface having to be electronically modifyed. I didn't thought of that when I bought it.

Is it harmful to the interface to set jack sampling rate to 192000 when the interface only suppports 44100? Because if not, I'd could do 4ms latency which is fine by me.

Thanks

---

### Post by oleink on 2010-08-13
> **maghoxfr said:**
> I could only get 17.4 ms, I couldn't lower that. I guess that my humble Multimix 4 won't let me. I've added the swapiness and sysctl.conf lines suggested by autostatic, I set the CPU scaling to "performance", I tried lighter DE (openbox, IceWM), I have rtirq but haven't tweaked it ([this]("http://subversion.ffado.org/wiki/IrqPriorities") is too much for me, I don't dare to modify it blindly :confused:)... 

My audio.conf
```
@audio   -  rtprio     99
@audio   -  memlock    unlimited
#@audio   -  nice      -19
```

I didn't uncommented "#@audio   -  nice      -19" because on the link I posted it said that:



I don't know how that is a myth because I couldn't use realtime without that

---

### Post by maghoxfr on 2010-08-13
Originally Posted by **oleink**
> I don't know how that is a myth because I couldn't use realtime without that
I don't know either, I'm just quoting, I'm not able to do such claim! I can do realtime with it commented out, I wish I could tell why. But if it works, the best for you is leaving it uncommented and for me commented out!
I guess that there's going to have to spend some time researching a bit to know the answer for that.

---

### Post by AutoStatic on 2010-08-13
> **oleink said:**
> I don't know how that is a myth because I couldn't use realtime without thatWithout what? With nice uncommented? You only need **memlock** and **rtprio**. The **nice** setting is not necessary, that's why it is commented.

---

### Post by AutoStatic on 2010-08-13
> **maghoxfr said:**
> I don't know either, I'm just quoting, I'm not able to do such claim! I can do realtime with it commented out, I wish I could tell why. But if it works, the best for you is leaving it uncommented and for me commented out!
I guess that there's going to have to spend some time researching a bit to know the answer for that.I put it up there in both the LinuxMusicians and the Ubuntu wiki after Paul Davis, the original author of JACK, pointed this out to me. If users want or need to prioritize audio applications they have to add the **rtprio** line to */etc/security/limits.conf* or */etc/security/limits.d/audio.conf*. In the case of JACK itself, as soon as you tick the Realtime option in QjackCtl and leave the Priority field as it is (on default) then JACK wants to run at the default priority, which is 50. If the **rtprio** line is not there or if it is commented then JACK simply won't start.
When it comes to the **nice** setting in the limits.conf/audio.conf file, it does practically nothing. If JACK doesn't work or if you have latency issues (xruns) then this has nothing to do with the **nice** setting. oleink, did you ever use the **renice** command? Probably not so in your case the nice setting doesn't do anything either.

The limits.conf/audio.conf file itself is being read by the PAM subsystem (Pluggable Authentication Modules). What this subsystem does is allowing normal, non-root users to modify certain system settings. The **memlock** setting allows applications that run under a user account to lock more memory then they could normally. The **rtprio** setting allows applications to prioritize their threads and also allows users to prioritize apps and/or processes themselves (this can be done with the **chrt** command).

Hopefully this makes things a bit clearer.

---

### Post by maghoxfr on 2010-08-13
> **AutoStatic said:**
> I put it up there in both the LinuxMusicians and the Ubuntu wiki after Paul Davis, the original author of JACK, pointed this out to me... 

Hopefully this makes things a bit clearer.

Yes it does, thanks for the explanation, and I overlooked it but now I see at the end of the page link "Last modified: 2010/08/13 09:49 by autostatic".

Great thank you Jeremy

---

### Post by oleink on 2010-08-13
I got my latency down even more.  I've got a 5.33msec latency!   :popcorn:

---

### Post by maghoxfr on 2010-08-14
> Quote:
Originally Posted by oleink  
quick questions: Would it be smarter for me to partition my drive and run a distro specifically for recording with no extra software installed?
NOT, IMO. But perhaps you should consider: 
1) Several kernels to boot in grub. It's generally advised to have at least one regular kernel (not rt) to boot from.
2) Several desktop environments to choose from (several kinds of sessions), at the time of booting. So you can choose gnome or openbox or whatever.

I still can't see why is not advisable to have separate installations, one for audio specifically. Other than having too many primary partitons I don't see any problem, or even two separate HDD. Right now I have 2.6.33-6-rt and I can't get the graphics card working on the generic kernel as well as in the rt. I can in one or the other but not both, so I should find a workaround but it demands time (which I  lack this days). I think that If I did a fresh, separate install for audio I should do fine. I'm not doing it but I'd like to know why is not advisable, just out of curiosity!

> I got my latency down even more. I've got a 5.33msec latency! 

Awesome, man! Are you using the uca222? Can you control volume of the signal comming from your computer and the input signal separetely on that interface? Because I can't in mine and it kills me when playing with rakarrack for instance, to listen to my clean guitar more than the processed signal. I am forced to have the interface as IN and the integrated as OUT, reducing jack performance, as Autostatic pointed out. If I'm editing or playing with my keyboard I can use only my interface, the problem is with guitar or mic, because they use the interface as input. I can't complain though, 4ms is not bad!

Can you tell me the specs in your jack setup?

Thanks!

---

### Post by AutoStatic on 2010-08-14
> **oleink said:**
> I got my latency down even more.  I've got a 5.33msec latency!   :popcorn::D Then try going for the lowest setting possible for USB which is 2ms. You need to do some maths to get there (or use Google)  but it is possible. Don't expect a super stable setup in that case though ;)

---

### Post by AutoStatic on 2010-08-14
> **maghoxfr said:**
> I still can't see why is not advisable to have separate installations, one for audio specifically. Other than having too many primary partitons I don't see any problem, or even two separate HDD. Right now I have 2.6.33-6-rt and I can't get the graphics card working on the generic kernel as well as in the rt. I can in one or the other but not both, so I should find a workaround but it demands time (which I  lack this days). I think that If I did a fresh, separate install for audio I should do fine. I'm not doing it but I'd like to know why is not advisable, just out of curiosity!To each his own. Personally I wouldn't advise against it, neither would I recommend it. If you feel comfortable with a separate install for your audio setup, that's great. I don't use separate installations myself. Simply because I think it is not necessary.

> **maghoxfr said:**
> Awesome, man! Are you using the uca222? Can you control volume of the signal comming from your computer and the input signal separetely on that interface? Because I can't in mine and it kills me when playing with rakarrack for instance, to listen to my clean guitar more than the processed signal.Then something's wrong in your setup or JACK connections. Or you should disable any direct monitoring on your card.

---

### Post by trulan on 2010-08-14
> **maghoxfr said:**
> I still can't see why is not advisable to have separate installations, one for audio specifically. Other than having too many primary partitons I don't see any problem, or even two separate HDD.
As Autostatic said, to each his own on this issue.  I do use two separate installations, one dedicated to audio production.  I have questioned whether or not this is necessary, but it's how I'm set up at this point.  I have Ubuntu, with stuff that feels 'messy' to me, like Open Office, VirtualBox, VMWare, and then I have an install of AVLinux which is lightweight to begin with and I stripped it down even further.

But here's the deal:  I have all the audio stuff installed in Ubuntu as well, and I can run pretty much everything from there if I want to.  So maybe my AVLinux partition is just wasted space.  I could also say that I have a backup OS in the somewhat likely event that my chronic tinkering breaks something important. ;)

I use 2.6.33-rt for everything in both installations.  I do keep a generic kernel around in Ubuntu but I haven't booted it in months.  As was stated, often when you patch something to work with the RT kernel it breaks it with the generic kernel, and it's just too much trouble to be undoing and redoing patches for a kernel I never use anyway.

And lastly, if it's all about getting the milliseconds of latency as low as possible, check this out:  I was able to get my firepod to sync up at 0.667 ms! :shock:  (while testing the new firewire stack, which will be default for Ubuntu Maverick Meerkat.)  No, it was not stable, it was not x-run free - I just had to see how far I could push it.:twisted:

---

### Post by maghoxfr on 2010-08-14
> I use 2.6.33-rt for everything in both installations. I do keep a generic kernel around in Ubuntu but I haven't booted it in months.
Yes, I think I'm going to follow that advice. The thing is that thigs go so slow on the general account I have that I want to pull my hairs out! I'll stick to ubuntu though, (I like synaptic and PPAs really make my life easier, I don't know if other distros have that possiibility). I'll keep my rt for everything, trying to solve that little speed problem of the general account (I have separate accounts so one for general stuff and other for audio).

> I was able to get my firepod to sync up at 0.667 ms!
That can't even be called latency!!! That's great.

> Then something's wrong in your setup or JACK connections. Or you should disable any direct monitoring on your card.
I won't go long here because it's not the topic of the thread, but I don't think JACK's connections are wrong, what has flaws is the design of the interface, I can't choose not to hear direct monitoring. I'll have to work around that.

I think today I'll have everything worked out (I hope so) next step is routing pulseaudio through jack\\:D/ And then I finally get to record something...

Thanks people!

---

### Post by oleink on 2010-08-15
> **maghoxfr said:**
> I still can't see why is not advisable to have separate installations, one for audio specifically. Other than having too many primary partitons I don't see any problem, or even two separate HDD. Right now I have 2.6.33-6-rt and I can't get the graphics card working on the generic kernel as well as in the rt. I can in one or the other but not both, so I should find a workaround but it demands time (which I  lack this days). I think that If I did a fresh, separate install for audio I should do fine. I'm not doing it but I'd like to know why is not advisable, just out of curiosity!



Awesome, man! Are you using the uca222? Can you control volume of the signal comming from your computer and the input signal separetely on that interface? Because I can't in mine and it kills me when playing with rakarrack for instance, to listen to my clean guitar more than the processed signal. I am forced to have the interface as IN and the integrated as OUT, reducing jack performance, as Autostatic pointed out. If I'm editing or playing with my keyboard I can use only my interface, the problem is with guitar or mic, because they use the interface as input. I can't complain though, 4ms is not bad!

Can you tell me the specs in your jack setup?

Thanks!

I don't even know how to do those separately.  I use a mixer so I just adjust my input on there and my output on the uca222

---

### Post by maghoxfr on 2010-08-15
> I don't even know how to do those separately. I use a mixer so I just adjust my input on there and my output on the uca222

Ok thanks.

---

### Post by JC Cheloven on 2010-08-15
Hi, I carry on reading this thread quietly. Very interesting. My thanks to the involved forumites :)
As for the allusion:

> 
Originally Posted by oleink:
quick questions: Would it be smarter for me to partition my drive and run a distro specifically for recording with no extra software installed?

Originally Posted by JC Cheloven:
NOT, IMO. But perhaps you should consider:
1) Several kernels (...)
2) Several desktop (...)

> **maghoxfr said:**
> I still can't see why is not advisable to have separate installations, one for audio specifically. (...) but I'd like to know why is not advisable, just out of curiosity!

Sorry if I gave the impression of implying that it's not advisable. I didn't mean this exactly. I meant that it isn't specially smarter, as asked in the question. Simply, in my experience, it makes no difference IF YOU USE GNU-LINUX. Here my aforementioned experience:

I have a [Carillon computer]("http://www.carillonac1.com/") which is, in principle conceived as a dedicated audio machine. It has two hard disks, one fast for the OS, and one big for the audio, and quite good specs overall despite being a bit aged. I bought it with xp 64 bits, and my advice for that OS would be very different: "don't update, don't connect it to the internet, don't install anything unrelated, don't use it for anything else...". Because that OS is prone to mess itself as things gets installed/uninstalled/MSupdated. 

Having been in that, I started using a specific 64 studio installation for audio, in a separated partition from other non-audio linux installations etc. I gradually realized that things here were just different. Installing something don't mess anything. Things seem to simply stay in your hard disk when you don't use them. As they should be. With some basic care about unwanted running processes, I noticed that the audio performance was unaltered. 

Now I use the ubuntu studio installation in this computer, with rt kernel only, for everything: web stuff, openoffice&latex documents, audio&video edition, python learning ... Well, I have other partitions, but I use them to test other OS, mainly out of curiosity.

That was it... :D
JC

---

### Post by maghoxfr on 2010-08-16
Thanks for the further explanation, I see your point now, I misunderstood in the beginning.

> Now I use the ubuntu studio installation in this computer, with rt kernel only, for everything: web stuff, openoffice&latex documents, audio&video edition, python learning ... Well, I have other partitions, but I use them to test other OS, mainly out of curiosity.

My dream, right there, what else can I say. I'd love to achieve that I am now running ia pretty stable, high performance rt, but I'm struggling a bit. I'll get there eventually though!

I completely understand what you say about XP, it has to be quarantained and isolated from the universe when used for audio, or any proffessional purpose for that matter.

This last couple of days I've been slacking off tweaking my system and I've been making some music, it's been a while for me, but I've achieved a pretty good setup for me right now, with the aid of this thread mainly. So time to rock:guitar:!!!

My next goal is routing pulseaudio through jack, but in a few days, becausue right now I'm enjoying this like a child with a new toy!

Thanks JC

---

### Post by AutoStatic on 2010-08-16
> **maghoxfr said:**
> My next goal is routing pulseaudio through jackI thought this thread was about eliminating xruns?

;)

---

### Post by maghoxfr on 2010-08-16
> I thought this thread was about eliminating xruns?
Yeah, sorry! I was just mentioning though, I'm not discussing that here, I'm already in another thread about that. ; )

---

### Post by oleink on 2010-08-16
Ha.  I'm glad this thread turned into some good stuff.  I've enjoyed it and I got my question answered

---

### Post by maghoxfr on 2010-09-06
I'm using the 2.6.31-10-rt kernel, i just want to know if any of the tweaks proposed in this thread can end up on terribly slow performance. Programs open very slow sometimes, dragging windows gets frustrating, dockbars are just impossible (except awn). I just want to know if this slow performance could be a product of the tweaks made. Else, if I run out of ideas, I'll have to take it to the pc tecnician but, I'm broke so let's hope that's not the case:icon_frown:

Weird thing (or not, after all that's what this thread was created), audio works great.

Thanks

---

### Post by AutoStatic on 2010-09-07
> **maghoxfr said:**
> I'm using the 2.6.31-10-rt kernel, i just want to know if any of the tweaks proposed in this thread can end up on terribly slow performance. Programs open very slow sometimes, dragging windows gets frustrating, dockbars are just impossible (except awn).The rt kernel detects if you're running a composite window manager and then deliberately slows everything down ;)

> **maghoxfr said:**
> I just want to know if this slow performance could be a product of the tweaks made. Else, if I run out of ideas, I'll have to take it to the pc tecnician but, I'm broke so let's hope that's not the case:icon_frown:And what if you use a non-compositing WM, like Metacity? Do the problems persist? What kind of GPU do you have?

---

### Post by maghoxfr on 2010-09-07
I have an AMD Athlon 64x2 dual core 6000+, 2 Gb RAM, Nvidia 8400 GS, 300 Gb HDD. Now it's running acceptable, yesterday it was awful all day, it's like that it fluctuates. I can't comparre it to windows performance because it's always been was awful (that's why I migrated ;)). I'm going to install a new 10.04 in a new partition just to see if it's that. I have metacity installed, I think it came by default. 

Thanks

---

### Post by Pablo_F on 2010-09-07
Hi Matías, 

I have the same card. It is OK here.  You could have a look at its temperature. 

sudo apt-get install sensors-applet
Then run:
sudo sensors-detect

I chose the default answers, of course (in my ignorance). 

Reboot and add the sensors applet to the panel. My GPU is now at 66 ºC, which I think is rather hot but it works well. Don't forget to clean the heat dissipator.

Cheers! Pablo

---

### Post by AutoStatic on 2010-09-07
> **maghoxfr said:**
> I have an AMD Athlon 64x2 dual core 6000+, 2 Gb RAM, Nvidia 8400 GS, 300 Gb HDD. Now it's running acceptable, yesterday it was awful all day, it's like that it fluctuates.It shouldn't fluctuate, then there's some rogue service or application spoiling all the fun. And did you try the nouveau driver instead of the proprietary nvidia driver?

> **maghoxfr said:**
> I have metacity installed, I think it came by default.But did you also try working with just Metacity? So by installing either fusion-icon or by disabling Desktop Effects altogether?

---

### Post by maghoxfr on 2010-09-07
Thanks Pablo and Jeremy, I disabled all effects and installed the aplet for temperature (56ºC). I should do some cleaning, this is a dusty town! I'm considering getting 2 extra Gb RAM. Now it's running pretty acceptable, I think I'll do a new install to have the full featured Ubuntu separately though. Audio is doing perfect though, so no complaints.

---

### Post by JC Cheloven on 2010-09-10
Hey, I missed this sequel :)

"Terribly slow performance", "dockbars are just impossible", and "it's like that it fluctuates"...
... that kind of things do suggest something going wrong in your system, like a process eating your cpu, eating your ram, or some incompatibility (==bug) among your nvidia/motherboard and the kernel. Hey, you have a 2 core x64, a nvidia graphics, and 2Gb ram. This should be largely enough to move your desktop very snappy even in the worse combination of normal circumstances. Even a crappy laptop with an integrated Intel graphics chip can! (I use such one these days).

So please, if your pc isn't responsive as a gunshot, even at a times, monitor(*) your cpu and memory activity and look at the top or htop command when the desktop seems to slow down. Also try to disable net connection when not needed, and disable automatic updates (when ubuntu does this it seems to forget about the world :-/ ), trying to isolate the problem.

(*) I have always at sight cpu, ram, net, and disc usages. The simple system monitor applet that can be added to a panel does the trick, see pic. Also conky does it nicely... there are choices.

JC

---

### Post by maghoxfr on 2010-10-02
Just to finish the branch I accidentally opened in this thread; I solved the bad behaviour of my pc by installing the propietary nvidia drivers, I didn't have them don't know why.

---

