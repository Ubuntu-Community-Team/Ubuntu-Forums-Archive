---
title: "Jack is dead"
date: 2009-10-24
forum: Ubuntu Studio
---

### Post by yermandu on 2009-10-24
Hi, i receive this error when i try start jackd.

What is ? What i need to do?


p, li { white-space: pre-wrap; }  creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
 control device hw:0
 new client: alsa_pcm, id = 1 type 1 @ 0x8f5bfe0 fd = -1
 [COLOR=#999999]01:53:03.002 JACK was stopped successfully.[/COLOR]
 [COLOR=#999999]01:53:03.004 Post-shutdown script...[/COLOR]
 [COLOR=#990099]01:53:03.004 killall jackd[/COLOR]
 [COLOR=#cc3366]01:53:03.005 JACK has crashed.[/COLOR]
 jackd: no process found
 [COLOR=#999999]01:53:03.416 Post-shutdown script terminated with exit status=256.[/COLOR]
 [COLOR=#ff0000]01:53:04.498 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.


[/COLOR]

---

### Post by AutoStatic on 2009-10-25
Hello yermandu, could you provide some more info? You can increase the verbosity in Qjackctl - Setup - Parameters - Verbose messages. And what kind of soundcard are you using?

---

### Post by yermandu on 2009-10-25
i have noted my sound card is starting in mute now ...

lspci

```
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
    Subsystem: Acer Incorporated [ALI] Device 010f
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=slow >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64, Cache Line Size: 32 bytes
    Interrupt: pin ? routed to IRQ 16
    Region 0: Memory at c0000000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

```

jackd starting in terminal

```
yermandu@xucuru:~$ jackd -R -dalsa -r44100
no message buffer overruns
jackd 0.116.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
loading driver ..
apparent rate = 44100
creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
control device hw:0
Bus error

```

Bus error ??????

qjackctl verbose message
```
  p, li { white-space: pre-wrap; }  [COLOR=#999999]12:24:09.329 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]12:24:09.342 Statistics reset.[/COLOR]
 [COLOR=#66CC99]12:24:09.463 ALSA connection graph change.[/COLOR]
 [COLOR=#CCCC99]12:24:09.677 ALSA connection change.[/COLOR]
 [COLOR=#999999]12:24:12.869 Startup script...[/COLOR]
 [COLOR=#990099]12:24:12.869 artsshell -q terminate[/COLOR]
 sh: artsshell: not found
 [COLOR=#999999]12:24:13.272 Startup script terminated with exit status=32512.[/COLOR]
 [COLOR=#999999]12:24:13.272 JACK is starting...[/COLOR]
 [COLOR=#990099]12:24:13.273 /usr/bin/jackd -v -R -dalsa -dhw:0 -r44100 -p1024 -n2[/COLOR]
 getting driver descriptor from /usr/lib/jack/jack_freebob.so
 getting driver descriptor from /usr/lib/jack/jack_firewire.so
 [COLOR=#999999]12:24:13.290 JACK was started with PID=4115.[/COLOR]
 no message buffer overruns
 getting driver descriptor from /usr/lib/jack/jack_dummy.so
 getting driver descriptor from /usr/lib/jack/jack_net.so
 getting driver descriptor from /usr/lib/jack/jack_oss.so
 getting driver descriptor from /usr/lib/jack/jack_alsa.so
 jackd 0.116.1
 Copyright 2001-2005 Paul Davis and others.
 jackd comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 JACK compiled with System V SHM support.
 server `default' registered
 registered builtin port type 32 bit float mono audio
 registered builtin port type 8 bit raw midi
 clock source = system clock via clock_gettime
 loading driver ..
 start poll on 3 fd's
 apparent rate = 44100
 creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
 control device hw:0
 new client: alsa_pcm, id = 1 type 1 @ 0x9e4c000 fd = -1
 [COLOR=#999999]12:24:13.686 JACK was stopped successfully.[/COLOR]
 [COLOR=#999999]12:24:13.686 Post-shutdown script...[/COLOR]
 [COLOR=#990099]12:24:13.687 killall jackd[/COLOR]
 [COLOR=#CC3366]12:24:13.688 JACK has crashed.[/COLOR]
 jackd: no process found
 [COLOR=#999999]12:24:14.112 Post-shutdown script terminated with exit status=256.[/COLOR]
 [COLOR=#FF0000]12:24:15.480 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]

```

---

### Post by yermandu on 2009-10-25
More information: 

Big line comand in [https://wiki.ubuntu.com/DebuggingSoundProblems](https://wiki.ubuntu.com/DebuggingSoundProblems)
```


/proc/asound/card0/codec#0:Codec: Conexant ID 2c06
/proc/asound/card0/codec#0:Vendor Id: 0x14f12c06
/proc/asound/card0/codec#0:Subsystem Id: 0x1025010f
/proc/asound/card0/codec#0:Revision Id: 0x100000
grep: /proc/asound/card*/*codec*/*: No such file or directory

```

```

~$  cat /proc/asound/cards
 0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xc0000000 irq 16

```

---

### Post by AutoStatic on 2009-10-26
Thanks for all the info! I see it's an onboard card that uses snd-hda-intel. First, you could try using 48000 as the sample rate, most onboard cards prefer that setting. And second, are you using a realtime kernel? If not, try disabling the realtime setting for JACK.
This bus error is puzzling me though, never seen that one before.

---

### Post by VooDooTom on 2009-11-05
I am interested in an solution, too. The same problems occur to me: Ubuntu Studio 9.10 current RT-Kernel and jackd won't start because of a bus error. It works with a non-RT kernel, though.

---

### Post by ElectricJake on 2009-11-08
I'm getting this error now, too. Was working fine earlier today I swear. As a matter of fact, everything was working perfectly so I haven't messed with anything I know of. maybe I updated?

---

### Post by rytmisk on 2009-11-17
I am suddenly getting exact the same error. This is both on the built-in intel soundcard as well as on my edirol UA25 usb soundcard. It seems to be connected to the realtime kernel somehow. I installed ubuntustudio from the alternate disk, and things worked fairly well, but then I discovered that the /etc/security/limits.conf file was scrambled at the end, so I "fixed" it according to the ubuntustudio preparation guide. And now it jack doesn't start at all with a bus error. I'll check some more.

Ketil

---

### Post by rytmisk on 2009-11-17
Ok a bit more info:

If I remove the line 
@audio - memlock unlimited

in /etc/security/limits.conf
or
edit it to 
@audio - memlock 500

It seem to work fine...

Strange!

Ketil

---

### Post by VooDooTom on 2009-12-01
@rytmisk: Thank you for this hint. If I change my memlock setting to 500 (KB) the „Bus error“ is gone, but jack complains about not having enough memory:

> JACK: unable to mlock() port buffers: Cannot allocate memory
JACK: unable to mlock() port buffers: Cannot allocate memory
...
cannot lock down memory for RT thread (Cannot allocate memory)

I guess one has to give the audio group more memory. On my notebook I have 1GB main memory and according to a [blog entry]("http://tapas.affenbande.org/wordpress/?page_id=73"), memlock „should“ be about the half of it. But if I set memlock to 512000 the Bus errer reappears.

With a memlock cf 5000 the first „two“ errors disappear, but the RT tread can still not be created. But if I set memlock between 60000 and 90000 it works without errors. All values above lead again to the bus error.

Cheers,
Tom

---

### Post by joseche on 2010-03-31
I am having the same problem after I added the memlock to the /etc/security/limits.conf file.

Doesn't make any sense to receive errors because doesn't have enough memory, and then have bus errors because it's too much memory.

Is this reported as a bug ?

---

### Post by hansson_14 on 2010-05-02
I get the same bus error after a clean install of Ubuntu Studio 10.04 64-bit.
Never happened under 9.04.
Anyone heard about a solution? :confused:

---

### Post by hansson_14 on 2010-05-03
Sorry, I was stupid.
I edited /etc/security/limits.conf according to what many state: set priority for RT etc - same as in System-->Administration-->Ubuntu Studio Controls.
It worked, but only after reboot. No bus error any more. :D

---

### Post by Chtfn on 2010-05-05
Sorry, I didn't understand your solution: do you mean that limits.conf shouldn't be edited by hand, but via Ubuntu Studio Controls? Does anything have to match in the settings in Jack Control?

---

### Post by Chtfn on 2010-05-05
OK, that's how it worked for me:

In System -> Administration -> Ubuntu Studio Control, I checked "enable memlock" and set it to 89 %, like I have it in my Jack Control settings when RT is checked.
I also had to edit my limits.conf to delete the memlock line I added a few days ago (Ubuntu Studio Controls edited and added its own memlock line).

After a reboot, I managed to launch the Jack Server in RT with no problem!

Thanks for your help, hansson_14!

---

### Post by ibuclaw on 2010-05-05
Thanks for your contributions, please raise a new thread if you have any new issues.

On that bombshell, closing.

Regards

---

