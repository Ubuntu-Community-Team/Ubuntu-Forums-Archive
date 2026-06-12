---
title: "Realtime Kernel on 12.04"
date: 2012-05-13
forum: Ubuntu Studio
---

### Post by unclernie on 2012-05-13
I've been struggling for two weeks now, trying to get jackd and Ardour to run stable on my Dell Vostro 1710.
  The builtin 02Micro fw controller is known to be troublesome, so I invested in a VIA VT6315-based expresscard, but even with that I get jack crashes as soon as I attempt to start Ardour.
  Last night, I performed a series of tweaks as suggested by the quickscan script on [http://wiki.linuxmusicians.com/doku.php?id=system_configuration](http://wiki.linuxmusicians.com/doku.php?id=system_configuration), and installed the realtime kernel from abogani's PPA ([https://launchpad.net/~abogani/+archive/realtime](https://launchpad.net/~abogani/+archive/realtime)), and finally, I was able to get ardour to start and open a simple three-track session, record, and playback some audio.
  My glee at a measure of success was tempered when I rebooted and brought up the grub menu, only to discover that the ONLY kernel it offers me is the -RT one.  I'd certainly like to have the option of booting into the standard distribution kernel as well.  Somewhere in a previous release, I thought I remember seeing a configuration option for number of previous kernel versions to retain in the grub menu, but I can't seem to find it either in the system settings menu, or anywhere in the maze that /boot/grub and /etc/grub.d have become.  Can someone help me out?

---

### Post by madeinfamous on 2012-05-13
allo unclernie!

 [install UBUNTU 12'04 LTS amd64 Generic & then...]("https://docs.google.com/document/d/1WUNiBosbcaPxu_ltmJhIgqLVKdwbkt0odwdGATHSfpo/edit") 

scroll down to: STARTUP MANAGER under ***MUSIC PRODUCTION PREPARATION***

cheers!

btw... standard ubuntu offer LOWLATENCY KERNEL 3.2.0-23 

so now... feel free to start again! ;)

I don't use ubuntu studio, too much crap in it! my thought!

---

### Post by jejeman on 2012-05-13
Give us output from
```
ls /boot/
```

---

### Post by n3mmr on 2012-05-14
> **madeinfamous said:**
> allo unclernie!

 [install UBUNTU 12'04 LTS amd64 Generic & then...]("https://docs.google.com/document/d/1WUNiBosbcaPxu_ltmJhIgqLVKdwbkt0odwdGATHSfpo/edit") 

scroll down to: STARTUP MANAGER under ***MUSIC PRODUCTION PREPARATION***

cheers!

btw... standard ubuntu offer LOWLATENCY KERNEL 3.2.0-23 

so now... feel free to start again! ;)

I don't use ubuntu studio, too much crap in it! my thought!

Actually, look at [https://launchpad.net/~danielrichter2007/+archive/grub-customizer](https://launchpad.net/~danielrichter2007/+archive/grub-customizer) instead of startup manager.!

That seems to support 12.04 much better.

There's a ppa, and you can use the packaging system the way it's intended.

---

### Post by mjhouska on 2012-05-16
So is it now safe to go from 10.04lts to 12.04lts?

---

### Post by CrocoDuck on 2012-05-16
When I installed abogani's rt kernel (it refused to boot with me) I had to update grub configuration in order to have all the voices in the grub menu. If you have GRUB2 (default in ubuntu 12.04, you cant find the files you are searching for just for this, they were used in the old GRUB version) you can do it easly by:

```
sudo update-grub
```

in a terminal. Basically, in GRUB2 the configuration is automatized by this command (seeks for kernels and makes the stuff).

If this not works try 

```
sudo update-grub2
```

I've run these a lot of time tryng to get rt kernel working... Has your kernel had a issue on "loading initial ramdisk"?

P.S. : Posting the output of 

```
ls /boot/
```

as recomended by jejeman can tell us if you have for some reason only the rt kernel in your system.

---

### Post by jejeman on 2012-05-16
> **mjhouska said:**
> So is it now safe to go from 10.04lts to 12.04lts?I wouldn't recomend. To much is changed.

---

### Post by unclernie on 2012-05-18
Well, I had checked /boot/, and yes, the old kernel files were still there.  I did run `sudo update-grub`, and in that terminal it issued a message indicating that it found the old kernel as well as the new one.
  I enabled Daniel's ppa, and installed grub-customizer.  When I started it up, it showed both kernels listed and 'active'.  But the old kernel was indented.  Hmmm....
  I restarted the machine, holding down the left shift key to bring up the grub menu...

   Aside:  I have to press the left shift key early!  It must be pressed and held while the Dell splash screen is still displayed.  The moment the screen goes black is too late!  If I press the left shift too late, the machine proceeds with the default boot, with the unfortunate side effect that the touchpad is inoperative, so the cursor is stuck in the middle, and you can't use the GUI to initiate another restart.

  ...this time I realize that the line 'previous linux versions' is not a title for the memtest lines below, but an entry in itself for a submenu.  When I select that line, I see the old kernel available and bootable.

  ...so this turns out to be no problem, just an old user not seeing what's right before him.


  Next observation/issue:  The quickscan tool which suggested that I install abogani's kernel, doesn't like abogani's kernel, because it is configured with CONFIG_HZ_250, not CONFIG_HZ_1000 as the quickscan script suggests.  I'm not complaining as yet, since jack/ardour is running without xruns at the moment, but I may install his source tree and try building a kernel with the finer-grained timer.

---

### Post by CrocoDuck on 2012-05-18
> **unclernie said:**
> Well, I had checked /boot/, and yes, the old kernel files were still there.  I did run `sudo update-grub`, and in that terminal it issued a message indicating that it found the old kernel as well as the new one.
  I enabled Daniel's ppa, and installed grub-customizer.  When I started it up, it showed both kernels listed and 'active'.  But the old kernel was indented.  Hmmm....
  I restarted the machine, holding down the left shift key to bring up the grub menu...

   Aside:  I have to press the left shift key early!  It must be pressed and held while the Dell splash screen is still displayed.  The moment the screen goes black is too late!  If I press the left shift too late, the machine proceeds with the default boot, with the unfortunate side effect that the touchpad is inoperative, so the cursor is stuck in the middle, and you can't use the GUI to initiate another restart.

  ...this time I realize that the line 'previous linux versions' is not a title for the memtest lines below, but an entry in itself for a submenu.  When I select that line, I see the old kernel available and bootable.

  ...so this turns out to be no problem, just an old user not seeing what's right before him.


  Next observation/issue:  The quickscan tool which suggested that I install abogani's kernel, doesn't like abogani's kernel, because it is configured with CONFIG_HZ_250, not CONFIG_HZ_1000 as the quickscan script suggests.  I'm not complaining as yet, since jack/ardour is running without xruns at the moment, but I may install his source tree and try building a kernel with the finer-grained timer.

I'm Happy that it was only an incompresion on the menu (I had the same:lolflag:, sorry I didn't think about that). I'm happy that you are not experiencing xruns too! Yes to change configuration you have to rebuilt, but if you are fine with that one you can take it as it comes (I'm on lowlatency and I just need to kill some precess to have the best jack experience with no xruns). So, if you are ok, keep on jammin'!

---

### Post by windeguy on 2013-02-01
When I try to download abogani's rt kernel,  the launchpad.net site tells me I do not have sufficient permission to access the page despite being logged in to launchpad. 

Is there any way around that?

---

### Post by ttoine on 2013-02-02
[https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation)

All is here.

Toine

---

### Post by windeguy on 2013-02-03
> **ttoine said:**
> [https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation)

All is here.

Toine

Thank you for the suggestion.  However, that pointed me to downloading the same realtime kernel I already have installed which is

3.2.0-23-realime

When I run realtimeconfigquickscan ( I will call it quickscan)  on this kernel I can satisfy all the requirements except it reports it is not finding a kernel with real time pre-emption and the system timer is not set to 1000 Hz.

Odd that quicksan is not finding a realtime kernel to have real time pre-emption.  Is that just a bug in quickscan? 

I have no idea how important the 1,000 Hz system timer is .  

Any suggestions?  The kernel I had used previously with 10.04 LTS is
2.6.33-29 realtime and that works very well for me on another laptop. I can no longer find the 2.6.33-29 realtime kernel .deb package to try it.

[COLOR="Red"]**Please note that I edited the .config file for the kernel to set it to 1000 Hz and now it passes that test.  I think it fails the pre-emption test of 'quickscan' because the variables used in the -23 realtime kernel are named slightly differently and "quickscan" is not picking up on them. **[/COLOR]

---

### Post by ttoine on 2013-02-03
what tell "uname -a" in a terminal ?

---

### Post by windeguy on 2013-02-03
> **ttoine said:**
> what tell "uname -a" in a terminal ?

uname - a gives:

Linux mike-Aspire-9410 3.2.0-23-realtime #36~ppa1-Ubuntu SMP PREEMPT RT Wed Apr 11 06:37:34 UTC 2012 i686 i686 i386 GNU/Linux


Please note that I edited the .config file for the kernel to set it to 1000 Hz and now it passes that test. I think it fails the pre-emption test of 'quickscan' because the variables used in the -23 realtime kernel are named slightly differently and "quickscan" is not picking up on them.

---

### Post by ttoine on 2013-02-03
What is the sound card you are trying to use ?
Did you tried the -lowlatency kernel ?
Are you using a restricted videocard driver ?

Tell me if I am wrong, I understand from your first post that your sound card may be firewire... Via chipsets are the worst you can buy for Linux. The best for stability are Texas Instrument based.

---

### Post by windeguy on 2013-02-03
> **ttoine said:**
> What is the sound card you are trying to use ?
Did you tried the -lowlatency kernel ?
Are you using a restricted videocard driver ?



Tell me if I am wrong, I understand from your first post that your sound card may be firewire... Via chipsets are the worst you can buy for Linux. The best for stability are Texas Instrument based.

I have tried the low latency kernel that is standard on Ubuntu Studio. 

I am using a laptop to play virtual instruments live on stage. My current set up is two USB 2 Behringer 61 note keyboard controllers and a Behringer UControl USB connected audio output module. This set-up works quite well even with a standard kernel (I have a real time kernel set up on another laptop using Ubuntu 10.04) .  And this set-up works even better with a real time kernel.

---

### Post by ttoine on 2013-02-04
So, what is the problem you have, actually ?

---

### Post by windeguy on 2013-02-04
> **ttoine said:**
> So, what is the problem you have, actually ?

When I run realtimeconfigquickscan it tells me that I am not running a pre-emptive type kernel, which of course it is. 

And before I made a change to the kernel's config file, which I think correctly changed the timer to 1,000 Hz,  quickscan told me that I did not have a 1,000 Hz timer, which quickscan prefers.  

I suspect that realtimeconfigquickscan is just making a mistake regarding the kernel not being a pre-empt type kernel. 

As for the current performance of the kernel, I am in the middle of testing it to see how well it performs.  So far it seems to work well.

---

### Post by ttoine on 2013-02-04
For intensive midi use, the -rt kernel is known to be better than the -lowlatency. However, it is really useful if you are using jack midi instead of alsa midi. I can't check that with my available hardware, thus: I don't own a midi controler at the moment.

Check that quickscan is launched using the right user, with the right PAM settings. I think you can test with sudo and see. But think that quickscan is not design mainly for Ubuntu. And that the -rt is not developped by Abogani only for audio performance, but for indutrial purposes too.

The better way to test if the pre-empt module is available is to launch Jack in real time mode. If it starts, it means the pre-empt module is here, and that your user has the PAM right to use it.

If you need to configure GRUB, I suggest to have a look at the Grub 2 section on the Ubuntu Studio Preparation Howto, there is an example of useful configuration.

---

### Post by windeguy on 2013-02-12
> **ttoine said:**
> For intensive midi use, the -rt kernel is known to be better than the -lowlatency. However, it is really useful if you are using jack midi instead of alsa midi. I can't check that with my available hardware, thus: I don't own a midi controler at the moment.

Check that quickscan is launched using the right user, with the right PAM settings. I think you can test with sudo and see. But think that quickscan is not design mainly for Ubuntu. And that the -rt is not developped by Abogani only for audio performance, but for indutrial purposes too.

The better way to test if the pre-empt module is available is to launch Jack in real time mode. If it starts, it means the pre-empt module is here, and that your user has the PAM right to use it.

If you need to configure GRUB, I suggest to have a look at the Grub 2 section on the Ubuntu Studio Preparation Howto, there is an example of useful configuration.

When I first started using Ubuntu and using realtime and -rt kernels I was told that the real time mode of JACK had nothing to do with if I was running a real time kernel.  In fact I can and do run the real time mode of JACK with Ubuntu 10.04 and a standard kernel that I do not think has a pre-empt mode.  I could be wrong on that. 

The realtime -23 kernel  I am currently testing with 12.04 is not providing as good a performance as the -29 kernel I have installed in 10.04 on a different but virtually identical laptop.

Is there any way to test the -29 kernel with 12.04?

---

### Post by ttoine on 2013-02-12
I don't know.

Did you tried latest available -lowlatency kernel ?

---

### Post by windeguy on 2013-02-12
> **ttoine said:**
> I don't know.

Did you tried latest available -lowlatency kernel ?

I have a fairly recent installation of the system, so I believe it has the latest low latency kernel.  That kernel is not nearly as fast as the -29 realtime kernel on an identical hardware.

Here is one link to a discussion where Autostatic recommended a kernel for laptops in post 16 on that thread: 

[http://ubuntuforums.org/showthread.php?t=1670196&highlight=wine-rt&page=2](http://ubuntuforums.org/showthread.php?t=1670196&highlight=wine-rt&page=2)

---

### Post by ttoine on 2013-02-12
This post has been written two years ago, before the release of Ubuntu 11.04. This is not the same distro, not the same pc... The kernel working well on one PC, laptop or workstation, is not the one who works well on another pc. It depends of too much things.

As an example, the brand new workstation of Azarecord is running a custom Ubuntu with Mixbus, a RME hdsp 9652 sound card and an AMD A6 with integrated HD7000 GPU. If the latest driver of AMD is installed via X-Edgers PPA (the free driver can not handle HD7000). And with that, the better kernel is the -lowlatency 3.2.0-36. With the -37, display is not working well. With -35, the performance is not as good. On my laptop, an some years old Thinkpad T61P with Intel CPU and nVidia gpu and Echo Audiofire sound card, the -37 is the best.

Please, don't forget that between the 10.04 and 12.04, many things have changed in Ubuntu (Alsa driver, desktop, jackd, hardware, gcc version and options, 32/64bits kernels, etc.) Even the choice of the desktop can change a lot of things. XFCE is not as stable as Gnome classic, on 12.04. Would you try to install gnome-session-fallback and try a session with Gnome classic or Gnome classic without effect ? It was the default desktop of 10.04 LTS, and maybe it can solve you performance problem. XFCE is actually a bit less stable and use a little bit more of CPU than the good old gtk desktop.

You can also fill a bug report against the developpers of the testing script. This is maybe the problem.

And if you want to test a specific kernel, you can of course build the one you want: just get the sources, install build-essentials and compile it. There is a lot of howto about compiling kernels on Internet. Just, keep in mind that Abogani kernel is developped more for scientific and industrial use in mind than for audio.

And last question: are you using alsa midi, or jackd midi ?

---

### Post by windeguy on 2013-02-12
Yes,  I appreciate that the changes in Ubuntu  will influence which kernel is best to use.  

As for using JACK versus ALSA MIDI,  I do not know for certain which I am using.  But I suspect it is ALSA MIDI after trying to do some research on that topic I found this:

[http://murks.lima-city.de/serendipity/index.php?/archives/7-ALSA-and-JACK-MIDI-explained-by-a-dummy-for-dummies.html#toc2](http://murks.lima-city.de/serendipity/index.php?/archives/7-ALSA-and-JACK-MIDI-explained-by-a-dummy-for-dummies.html#toc2)

In the latest version of Ubuntu Studio,  how can I tell and how can I set it up for JACK MIDI?

---

### Post by jejeman on 2013-02-12
In applications you choose to use ALSA or JACK MIDI. Some applications use just one of them, some can use both.
If you use ALSA driver for soundcard you can "export" ALSA MIDI ports to JACK MIDI by selecting the MIDI driver in JACK settings (if you use qjacktl). It is explained in the page you have found.

---

### Post by ttoine on 2013-02-13
The package a2jmidi is very useful in case one application is in jack midi and an other in alsa midi. You can start it once jackd is started. Firewire sound cards are only managed through Ffado and Jack, and so, only in jack midi.

In Patchage, alsa midi is in green, jack midi is in red. You will see that a2jmidi has green and red midi i/o.

---

### Post by windeguy on 2013-02-13
> **ttoine said:**
> The package a2jmidi is very useful in case one application is in jack midi and an other in alsa midi. You can start it once jackd is started. Firewire sound cards are only managed through Ffado and Jack, and so, only in jack midi.

In Patchage, alsa midi is in green, jack midi is in red. You will see that a2jmidi has green and red midi i/o.

I will look into Jack midi those utilities to run it to see if that helps. 

I will also look at using GNOME instead of KDE.  I am not sure why a distribution requiring speed for music production would switch to KDE when it is less responsive than GNOME, but there must have been reasons. 

Do you have any familiarity with WINE-RT and how to create a system using WINE-RT?  While looking for solutions I came across a vendor selling a version of Linux that promises far better performance in real time operation called Studio 13.37 (based upon Slackware)  but I was interested in seeing if there was a way to run WINE-RT in Ubuntu Studio.

---

### Post by ttoine on 2013-02-13
The more stable and optimised the desktop is, the less it will use CPU. Also, if possible, it is important to test the video drivers available for your hardware, if it is not Intel GPU: if you are using Gnome with desktop effects, or Unity, Compiz will be activated, and so, it is compulsory to have a good driver. If you Gnome without effects or Unity 2D, think that the CPU will have to compute the 2D graphics, so it may use a lot of CPU when moving windows, etc.

About Wine, before I can answer, can you just tell why you think you need Wine-RT ?

---

### Post by windeguy on 2013-02-13
> **ttoine said:**
> The more stable and optimised the desktop is, the less it will use CPU. Also, if possible, it is important to test the video drivers available for your hardware, if it is not Intel GPU: if you are using Gnome with desktop effects, or Unity, Compiz will be activated, and so, it is compulsory to have a good driver. If you Gnome without effects or Unity 2D, think that the CPU will have to compute the 2D graphics, so it may use a lot of CPU when moving windows, etc.

About Wine, before I can answer, can you just tell why you think you need Wine-RT ?

I understand your remarks regarding the most stable system being the most efficient at using resources. Thank you.

I use a lot of Windows Based virtual instruments when I play live performances. I currently use Cantablie Lite running in WINE to play a variety of VSTi's. 

My question about Wine-RT is to evaluate and deterimine if Wine-RT will allow me to use more sophisticated VSTi's without glitches (X-runs is the term normalluy used).

---

### Post by ttoine on 2013-02-13
Perhaps you should try Festige. You can find it in the KXStudio repositories, I think you already use them.

Wine-RT should be available too in KXStudio, as it is needed by Festige.

[http://kxstudio.sourceforge.net/KXStudio:Applications:FeSTige](http://kxstudio.sourceforge.net/KXStudio:Applications:FeSTige)

---

