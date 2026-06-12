---
title: "Heroes 3 Crashing"
date: 2010-06-25
forum: Wine
---

### Post by ep1x on 2010-06-25
I start the heroes,play about 2-3 minutes and then suddenly,wine is being terminated...
 

fixme:win:EnumDisplayDevicesW ((null),0,0x32f638,0x00000000), stub!
err: ole:CoGetClassObject class {5959df60-2911-11d1-b049-0020af30269a} not registered
err: ole:CoGetClassObject no class object {5959df60-2911-11d1-b049-0020af30269a} could be created for context 0x1
fixme: dsalsa:IDsDriverBufferImpl_SetVolumePan (0x154140,0x154588 ): stub
fixme: dsalsa:IDsDriverBufferImpl_SetVolumePan (0x154140,0x154588 ): stub
fixme: dplay:IDirectPlayLobby3AImpl_RegisterApplication :stub

---

### Post by ep1x on 2010-06-26
Please help

---

### Post by asdfoo on 2010-06-26
terminated? is there any message? crash dialog? disappears with no indication?

which version of Wine are you using?  1.2-rc5 is the most recent, open a terminal and type: wine --version

which video card and drivers do you have? are you using the most recent video driver?

---

### Post by ep1x on 2010-06-26
Sorry for the late post,got Nvidia 8600GT,Driver got driver before the latest one which is 195.x.x ,got wine 1.1.42.
Got the message before the crash :
err: seh:setup_exception_record nested exception on signal stack in thread 0009 eip 7bc72950 esp 7ffdbc7c stack 0x232000-0x330000
err: seh:setup_exception_record nested exception on signal stack in thread 0009 eip 7bc72950 esp 7ffdbc7c stack 0x232000-0x330000

---

### Post by ep1x on 2010-06-26
Please help...

---

### Post by ep1x on 2010-06-27
Someone ,please help....

---

### Post by asdfoo on 2010-06-27
no need to beg.

update to the latest version of wine, which is 1.2-rc5 and try again

---

### Post by ep1x on 2010-06-28
how?

---

### Post by asdfoo on 2010-06-28
... go to winehq.org and find the download section

---

### Post by ep1x on 2010-06-28
Got the new version,when you first posted,that i should dl it and i get the same error as the first time :

err:seh:setup_exception_record nested exception on signal stack in thread 0009 eip 7bc73040 esp 7ffdbc7c stack 0x232000-0x330000
 
FIXED

---

### Post by Self-Perfection on 2010-08-07
I have similar problem, but in my case Heroes3 hangs, not crashes. Console output:
```
$ WINEPREFIX=~/.HoMMIII wine explorer /desktop=foo,800x600 Heroes3.exe 
fixme:win:EnumDisplayDevicesW ((null),0,0x33f610,0x00000000), stub!
fixme:x11drv:X11DRV_desktop_SetCurrentMode Cannot change screen BPP from 32 to 16
err:ole:CoGetClassObject class {5959df60-2911-11d1-b049-0020af30269a} not registered
err:ole:CoGetClassObject no class object {5959df60-2911-11d1-b049-0020af30269a} could be created for context 0x1
fixme:mixer:ALSA_MixerInit No master control found on MPU-401 UART, disabling mixer
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x140808,0x18eef0): stub
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x140808,0x18eef0): stub
fixme:dplay:IDirectPlayLobby3AImpl_RegisterApplication :stub
err:seh:setup_exception_record nested exception on signal stack in thread 0024 eip 7bc73110 esp 7ffdbc7c stack 0x242000-0x340000
```
Last line ("err:ser: ...") appears in the moment when game hangs. Problem seemed related to sound: music frozes and plays repeatedly last fraction of second of music theme. I tried all combinations of audio driver and Hardware Acceleration mode but game hangs with all of them. Then I switched off audio drivers in winecfg and since that action game has not hung a time, but there is no sound so this is not complete solution. Any suggestions?

My PC uses internal sound card of Phoenix i845GEV/PEV-W83627 motherboard
$ lspci|grep audio
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)

---

### Post by kespindler on 2010-08-13
I'm not sure about your particular problems, but I was having the same problems running heroes3 in wine as well. It would start up, and almost immediately freeze my computer, and everything would be shot to hell (really difficult to get out, usually just ended up restarting etc.)

It turns out my file permissions were wrong. Nothing a couple chmods can't fix.

```

chmod 777 -R <heroes directory>
chmod +x -R <heroes directory>

```

---

### Post by kleskjr on 2010-08-13
there is heroes 3 for Linux, maybe it will be more stable than in wine

---

### Post by Self-Perfection on 2010-08-17
> **kespindler said:**
> ...

It turns out my file permissions were wrong. Nothing a couple chmods can't fix.

```

chmod 777 -R <heroes directory>
chmod +x -R <heroes directory>

```
Did not help. Also chmod +x after chmod 777 is redundant.

> **kleskjr said:**
> there is heroes 3 for Linux, maybe it will be more stable than in wine

There is linux port only for "Heroes of Might and Magic III: The Restoration of Erathia", but I want complete set, with "Armageddon&#8217;s Blade" and "The Shadow of Death".

My problem seems to be the same as in [bug #20380]("http://bugs.winehq.org/show_bug.cgi?id=20380") in wine, it is opened since 2009. There are reports that with recent kernels (since 2.6.34) game do not freeze. I havn't tried for myself upgrading kernel yet, so I cannot confirm this solution.

**Update:** I have updated kernel from [Ubuntu kernel PPA]("http://ubuntu-tweak.com/source/kernel-ppa-ppa/") to version 2.6.35-16. Now the game is stable with sound.

---

### Post by grant4353 on 2010-11-06
Sorry to bring this thread up again but...I've recently installed Heroes 3 Complete and it installed fine but when I go to play it freezes right away. I used WINE to install it and I'm using the latest version on Ubuntu, anyone have any fixes/ideas for this?

---

### Post by maruchin on 2010-11-21
Hi,

got the same problem this night.
I reinstalled wine, upgraded it to 1.3 and reinstalled heroes III.
Nothing worked. then i remembered, i had some issues with sounds lately.
So i looked into winecfg and turned off all sound drivers.
So no oss and no alsa. works for me.

hope it solves your problem too.

regards
maru

---

### Post by fluxlizard on 2010-11-21
That's interesting- I have heroes 3 gold and it is working great with wine right out of the box.

Additionally I have the linux version- not sure if it runs on the latest ubuntu or not. I stopped using a few years ago because some releases it worked, some it didn't, depending on whether the loki installer was appropriate for the release.

---

### Post by Nabo00o on 2011-08-12
Hey all sorry about the late reply, but I followed up on Self-Perfection's post and it worked!!! His link did not work though, so I found a ppa of the newest linux kernel elsewhere.
I installed it with a minor nvidia problem first, seemed I just had to tell it to like restart its configuration. After this i tried Heroes 3, and have had no problems yet!
Normally it would take about 1 (or less) to maybe 3 min before the error stopped the game.

So a big thank you from me!

---

