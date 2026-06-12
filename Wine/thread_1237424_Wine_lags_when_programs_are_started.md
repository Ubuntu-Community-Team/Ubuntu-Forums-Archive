---
title: "Wine lags when programs are started"
date: 2009-08-11
forum: Wine
---

### Post by crtbt on 2009-08-11
First off I'm new to Linux, so sorry if you have to explain something twice to me.

Basically my problem is Wine heavily lags whenever I run a new Wine program, or within 30 seconds of running one.  This just started happening recently; until a few days ago everything seemed to be running fine.

I first noticed the problem in foobar2000, where I've set up the metacity global hotkey options to run the program with command line options to essentially give me multimedia keyboard control of the program.  For example, when I hit the next key this command runs

```
wine "/home/alex/.wine/dosdevices/c:/Program Files/foobar2000/foobar2000.exe" /next
```So that foobar skips to the next track.  The first symptom I noticed was that about 15-30 seconds after using the multimedia keys the sound would start "skipping", looping the same 1-2 second bit over a few times, then resuming normally.  When I hit the actual "next", "prev", etc. buttons in the program (on the screen, not the keyboard) everything behaves fine.  I also noticed that the sound skipped similarly when I first opened foobar and first pressed play (even without using the keyboard).

At first I thought it was a sound problem.  I started experimenting a little and found that the same thing happened in WinAmp.  In native Linux audio players like Rhythmbox I didn't have any similar problems, though.  I noticed that whenever the skipping occurred my CPU would jump to 100%, and the process causing the jump was wineserver.  I found that if I had Rhythmbox and foobar2000 playing simultaneously, when foobar started skipping Rhythmbox would continue playing without any issues.

I then noticed that whenever the skipping happened foobar and every other wine program lagged or was temporarily frozen, while all the native Linux apps still worked fine.  And I saw that when opening other Wine programs, like the configuration panel and Notepad, even when foobar isn't running, there were similar CPU spikes and lags from wineserver.  So the problem doesn't seem to just have to do with the sound.

What's bothering me is that this just started happening.  A few days ago it was working fine.  Additionally, it seems that since I've started trying to solve the problem it has actually gotten worse; when it started the sound would skip for only a few seconds, and now it usually skips for about 15 seconds.  I've tried to fix the system by removing and rolling back packages that were installed since the last time I remember it working right, but nothing seems to help.  Here is what I believe happened between when everything was fine and when I first noticed the problem:

[LIST]
[*]I installed the cdrdao package.
[*]I upgraded flashplugin-installer because Ubuntu told me to.
[*]I accidentally installed new graphics drivers and screensaver packages from [https://launchpad.net/~tormodvolden/+archive/ppa]("https://launchpad.net/%7Etormodvolden/+archive/ppa") because I had tried it before and forgot to remove it from my software sources and just accepted the Ubuntu upgrade message without thinking.  But these wouldn't start (not) working until I restarted later...
[*]I installed Audacity.
[*]I installed the Windows app Soulseek using Wine.
[*]I installed Nicotine+.
[*]I installed Mixxx.
[*]I installed the jackd and qjackctl packages because I thought it would get Mixxx working.
[*]I uninstalled the jackd and qjackctl packages because I got Mixxx working without them.
[*]I restarted my computer and it didn't work right because of those graphics drivers.  I reverted back to the original drivers and screensaver pack and got the graphics working again.
[/LIST]
Somewhere along the line there Wine got messed up.  I've since uninstalled most of that stuff (Audacity, Soulseek, Nicotine+, Mixxx... everything except cdrdao and flashplugin-installer... and I'm pretty sure I didn't miss anything) but Wine is still giving me trouble.

Here are my specs:

[LIST]
[*]Ubuntu 9.04 Jaunty
[*]Wine 1.0.1
[*]AMD Athlon 2600+
[*]1GB RAM
[*]Abit NF7-S v2 Motherboard
[*]ATI Radeon 9600 256MB
[*]All Wine settings default except sound (ALSA, full hardware acceleration, 44100 Hz, 16 bit, DirectSound driver emulation)
[/LIST]
Also, I don't know if it's related, but every Wine program I run from the terminal gives this error:

```
err:reg:SCSI_getprocentry bus id line scan count error (fscanf returns 0, expected 4)
```Thanks,
Alex

---

### Post by crtbt on 2009-08-11
This problem seems to be getting worse and fast... when I made this thread a few hours ago it was taking me about 30 seconds to start up foobar2000.  Right now it just took at least 5 minutes and the amount of skipping when I press the multimedia keys has gone from about 15 seconds to over 90.  Restarting doesn't help at all, it might even be making it worse.  I've also noticed that the whenever I start new programs (this doesn't happen when I use the multimedia keys and the program is already running, however) the amount of memory in use goes up to obscenely high level.  When I started WinAmp wineserver was using about 600 MB and winamp.exe was using about 200 MB. Once the program is fully started it drops back to a lower level.  Something similar happened with foobar.  Here's the full terminal output for both of those programs:

WinAmp:
```
alex@alex-desktop:~$ wine "C:\Program Files\Winamp\winamp.exe"
err:reg:SCSI_getprocentry bus id line scan count error (fscanf returns 0, expected 4)
^Terr:ntdll:RtlpWaitForCriticalSection section 0x7f0048 "heap.c: HEAP.critSection" wait timed out in thread 001c, blocked by 0009, retrying (60 sec)
Terminated
```(I had to force quit because it was taking forever to close.)

foobar2000:
```
alex@alex-desktop:~$ wine "C:\Program Files\foobar2000\foobar2000.exe"
err:reg:SCSI_getprocentry bus id line scan count error (fscanf returns 0, expected 4)
fixme:win:RegisterShellHookWindow (0x1002a): stub
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:EnumDisplayDevicesW ((null),0,0x32cce8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32cce8,0x00000000), stub!
fixme:dciman:DCICreatePrimary 0x400 0x2ab128c
err:ole:CoGetClassObject class {1968106d-f3b5-44cf-890e-116fcb9ecef1} not registered
err:ole:CoGetClassObject class {1968106d-f3b5-44cf-890e-116fcb9ecef1} not registered
err:ole:create_server class {1968106d-f3b5-44cf-890e-116fcb9ecef1} not registered
fixme:ole:CoGetClassObject CLSCTX_REMOTE_SERVER not supported
err:ole:CoGetClassObject no class object {1968106d-f3b5-44cf-890e-116fcb9ecef1} could be created for context 0x17
fixme:dciman:DCICreatePrimary 0x41c 0x2ab1ca4
```(I'm still running it now.)

edit: I found that my users.reg file was an absurd 436 MB in size and tracked down the problem to an entry from Winamp.  Uninstalling Winamp brought the registry file back to normal size and everything is running fine now.

---

