---
title: "Kernel &gt; 3.0 and M-Audio Fast Track Ultra problems with EHCI"
date: 2011-10-23
forum: Ubuntu Studio
---

### Post by nullakilla on 2011-10-23
I've got problem with M-Audio Fast Track Ultra support in my ubuntu studio 11.04.

Can start my soundcard only in high-latency mode (>40ms) and even in this mode I have XRUNs. Doesn't matter whether kernel is Low-latency or not.

This is my alsa-info.sh results: [http://www.alsa-project.org/db/?f=c3f2296dbeb507cb9c15f22c11e44b6a5305deaa](http://www.alsa-project.org/db/?f=c3f2296dbeb507cb9c15f22c11e44b6a5305deaa)

This problem occurres in all kernels. Everything works COOL only when I turn off EHCI in BIOS and HCI works in OHCI mode.

I've found out that not my soundcard fails, but EHCI kernel driver.
When I try to initialize JACK with settings BUFFER SIZE=128 and FREQUENCY=48000 I've got in **dmesg**:
```

[    1.884040] usb 6-2: new low speed USB device number 2 using ohci_hcd
[    2.336038] usb 6-3: new low speed USB device number 3 using ohci_hcd
[ 1810.546888] ehci_hcd 0000:00:12.2: force halt; handshake ffffc9000031e024 00004000 00000000 -> -110
[ 1810.546894] ehci_hcd 0000:00:12.2: HC died; cleaning up

```so you can see that EHCI USB driver dies. Other USB devices continue to work, but if you disconnect them and replug again they won't initialize.

in JACK message console:
```

[COLOR=#cc66cc]jackdmp 1.9.7[/COLOR]
 [COLOR=#cc66cc]Copyright 2001-2005 Paul Davis and others.[/COLOR]
 [COLOR=#cc66cc]Copyright 2004-2010 Grame.[/COLOR]
 [COLOR=#cc66cc]jackdmp comes with ABSOLUTELY NO WARRANTY[/COLOR]
 [COLOR=#cc66cc]This is free software, and you are welcome to redistribute it[/COLOR]
 [COLOR=#cc66cc]under certain conditions; see the file COPYING for details[/COLOR]
 [COLOR=#cc66cc]JACK server starting in realtime mode with priority 89[/COLOR]
 [COLOR=#cc66cc]control device hw:5[/COLOR]
 [COLOR=#cc66cc]control device hw:5[/COLOR]
 [COLOR=#cc66cc]audio_reservation_init[/COLOR]
 [COLOR=#cc66cc]Acquire audio card Audio5[/COLOR]
 [COLOR=#cc66cc]creating alsa driver ... hw:5|hw:5|128|2|48000|0|0|nomon|swmeter|-|32bit[/COLOR]
 [COLOR=#cc66cc]control device hw:5[/COLOR]
 [COLOR=#cc66cc]Using ALSA driver USB-Audio running on card 5 - M-Audio Fast Track Ultra at usb-0000:00:12.2-6, high speed[/COLOR]
 [COLOR=#cc66cc]ALSA: Cannot open PCM device alsa_pcm for playback. Falling back to capture-only mode[/COLOR]
 [COLOR=#cc66cc]Cannot initialize driver[/COLOR]
 [COLOR=#cc66cc]JackServer::Open() failed with -1[/COLOR]
 [COLOR=#cc66cc]Failed to start server[/COLOR]

```I don't want to wait until EHCI kernel driver is fixed and maybe problem is not straightly connected with it. Does anybody know what's the problem?

Googling gave me nothing about it, cause there too few M-Audio Fast Track Ultra users in linux community :)

---

### Post by sgx on 2011-10-26
Hi, the command   lsmod lists kernel modules, the module for maudio
cards is snd_ice1712

If it is not listed in the output of lsmod, try the command

modprobe snd_ice1712

Success is indicated by the lack of terminal output after the command.
Failure will be briefly acknowledged.

Log out, log in, and try the lsmod command again. 

If snd_ice1712 is in the output, go to the qjackctl setup panel,
and at the

Input device  >
Output device  >

click the  > widgets to see your available soundcards. Select the ones
saying snd_ice1712, or an maudio title. Mixers like
envy24control, kmix, and alsamixer-gui all display volume faders for
maudio soundcards, the warnings of no support just acknowledge the
products lack of certain hardware, which software mixers provide for.

Cheers

---

### Post by nullakilla on 2011-10-26
I'm using USB Audio Class Compliant soundcard, not PCI, so the kernel module is called snd_usb_audio. But your solution is for PCI cards

---

### Post by nullakilla on 2011-10-31
Recently I've found out that problem is in my USB EHCI controller. Now I cooperate with Alan Stern to get my ATI EHCI working.

---

### Post by sgx on 2011-11-01
New support for Fast Track Pro is announced in the newest
AVLinux 5.02 release.

Give it a try!

[http://www.remastersys.com/forums/index.php?topic=1756.0](http://www.remastersys.com/forums/index.php?topic=1756.0)

Cheers

---

### Post by nullakilla on 2011-11-05
> **sgx said:**
> New support for Fast Track Pro is announced in the newest
AVLinux 5.02 release.

Give it a try!

[http://www.remastersys.com/forums/index.php?topic=1756.0](http://www.remastersys.com/forums/index.php?topic=1756.0)

Cheers

Fast Track Pro and Ultra are supported with ALSA 1.0.24 drivers (included in recent linux kernels) and your exotic AVLinux is not needed.
As i wrote before, my problem is not in ALSA, but in my USB Enhanced Host Controller Interface, hence ehci-hcd driver should be appropriately modified. 

Also it can be hardware problem. AMD SB600-SB700 southbridges are quite buggy

---

### Post by sgx on 2011-11-05
The kernel support for the fastTrack Ultra in AVLinux 5.02
is the result of great effort. AVLinux is not exotic.
It is standard debian, with lots of software installed
and configured, so musicians can play more, and work less.

This blog details a process reaching a solution:

[http://joegiampaoli.blogspot.com/2011/06/m-audio-fast-track-pro-for-debian-linux.html](http://joegiampaoli.blogspot.com/2011/06/m-audio-fast-track-pro-for-debian-linux.html)

This is some history that chronicles the current support
for fastTrack devices:

[http://forums.m-audio.com/showthread.php?714-Not-a-problem.-FastTrack-on-linux](http://forums.m-audio.com/showthread.php?714-Not-a-problem.-FastTrack-on-linux)

more fastTrack kernel info

[http://yomix.org/info/blog/2011/07/14/m-audio-fast-track-pro-special-features-now-enabled-linux/](http://yomix.org/info/blog/2011/07/14/m-audio-fast-track-pro-special-features-now-enabled-linux/)

Cheers

---

### Post by VoiceOfRhemorha on 2011-11-10
Hello! I'm not sure, am I right with the topic, but I have a problem. 

I use line 6 guitarport (usb interface), it worked fine with an old kernel, but after upgrade to 3rd version, the problems appeared. Jack tries to start, but fails after ~15 seconds. Is it caused by change of realtime to non-realtime kernel?

---

### Post by sgx on 2011-11-10
Hi, if you have a live cd/dvd from the previous version, boot it and
run the lsmod command from it, and compare the output to the updated system lsmod output. If some modules are missing, issue the command

sudo modprobe name-of-missing-one

If an empty prompt returns, the command was successful, reboot, and try again. There is some line6 firmware package available to install,
which may help, you'll have to google its whereabouts. I think Puppy Studio has it by default.

I would 'upgrade' back to your working system, and test new ones on an external hard-drive installation.

Cheers

---

### Post by VoiceOfRhemorha on 2011-11-10
thank you for your answer.
I've re-installed 11.10 version, and all work "from box"=)
I've decided not to make experiments and to use UbuntuStudio as a fail-safe and stable OS, but on the other drive I'll install some other distro to build and install bleeding edge software without any risk to loose important  work =)

---

### Post by gg0815 on 2012-11-17
hello,
I have the same problem with my new fast track ultra as it describes [nullakilla]("http://ubuntuforums.org/member.php?u=1261124").
has one of the attending here ever seen or found a solution for this problem. I use the fast track pro so fars, there are no problems.
@[sgx]("http://ubuntuforums.org/member.php?u=203350") I also tested the av-linux distribution kernel 3.0.36 and 3.2.16. The same problem.

gunnar

---

### Post by gg0815 on 2012-11-22
The solution was now Vanilla 3.6.7.
quite stable's not true. but the occasional errors are harmless.

my dream would now have a way to use the internal Gagets of Ultra to (effects and mixer).
just a dream ;-)

---

### Post by gg0815 on 2012-11-26
ok, I did not want to believe. It really does everything ( Effect and Routing ). Perfect and easy, in the mixer. Thanks Felix, Mark and Takashi

gg

---

### Post by wildmanne39 on 2012-11-27
Old thread closed.

---

