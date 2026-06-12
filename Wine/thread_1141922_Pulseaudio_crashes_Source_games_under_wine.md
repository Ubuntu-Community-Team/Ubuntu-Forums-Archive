---
title: "Pulseaudio crashes Source games under wine"
date: 2009-04-28
forum: Wine
---

### Post by Jorenko on 2009-04-28
Ever since upgrading to jaunty, I am getting the following backtrace from both TF2 and L4D after anywhere from 5-15 minutes of play.

```
E: memblock.c: Assertion 'b' failed at pulsecore/memblock.c:438, function pa_memblock_acquire(). Aborting.
wine: Assertion failed at address 0xf7f8c425 (thread 0065), starting debugger...
Unhandled exception: assertion failed in 32-bit code (0xf7f8c425).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:f7f8c425 ESP:392fe690 EBP:0000617a EFLAGS:00000202(   - 00      - - I1)
 EAX:00000000 EBX:00006152 ECX:0000617a EDX:00000006
 ESI:6ed1b5f0 EDI:f7df1ff4
Stack dump:
0x392fe690:  392fe6a0 f7cbe9a0 f7df1ff4 392fe7c0
0x392fe6a0:  392fe7c8 f7cc0368 00000006 392fe740
0x392fe6b0:  00000000 7cc2e790 392fe6f8 7cc36fb4
0x392fe6c0:  7cc493c8 6695a010 7ffbc000 7cc36da1
0x392fe6d0:  00000000 392fe810 392fe7b8 00000073
0x392fe6e0:  00b76eb4 626d656d 6b636f6c 203a632e
Backtrace:
=>0 0xf7f8c425 (0x0000617a)
  1 0x00000000 (0x00000000)
0xf7f8c425: movl        $0x2b,%ecx

```

Lots of searching reveals that the wine guys won't touch your problem unless you've got pulseaudio disabled, and it seems to be implicated by the backtrace I'm getting too. So, I set out to disable it.

However, no matter how much I try, it won't stay disabled. `killall pulseaudio`, `pulseaudio -k`, No matter what I try, I confirm that it's gone, run the game, have it crash again, and when I check it's running again!

Has anyone else had this problem, or does anyone know of a way to *actually* disable pulse temporarily?

---

### Post by cogadh on 2009-04-28
Run it with "pasuspend" like this:
```
pasuspend wine foo.exe
```

---

### Post by Jorenko on 2009-04-30
Nope, pasupender doesn't change the behavior one bit.

---

### Post by hikaricore on 2009-05-01
Then likely pulse isn't causing it.
Have you tried actually killing pulseaudio first?

---

### Post by atfrase on 2009-05-04
Such are the wonders of PulseAudio and Wine, which have never worked well together.  Starting a year ago when 8.04 switched to PA, people started reporting problems like this one; despite numerous bug reports full of comments from annoyed users, the developers on both sides continue to blame each other and nothing gets fixed.

---

### Post by YokoZar on 2009-05-05
[https://bugs.launchpad.net/bugs/367379](https://bugs.launchpad.net/bugs/367379)

---

### Post by Emanuele_Z on 2009-05-18
Actually is Pulseaudio's fault.
Compared to 8.10, PA is way better now, but again this
[http://appdb.winehq.org/commentview.php?iAppId=1922&iVersionId=14154&iThreadId=48364](http://appdb.winehq.org/commentview.php?iAppId=1922&iVersionId=14154&iThreadId=48364)
is a report on what happens with PA and wine (WoW this time).

Why does Ubuntu started to include this solution as default when is clearly **not** in a release status?

---

### Post by cogadh on 2009-05-18
Ubuntu wasn't the only one, I believe Fedora went to Pulse around the same time, not sure about any other distros though. I've been asking why Ubuntu went with Pulse since they started with it (8.04? 8.10?), but I've never got a straight answer.

---

### Post by Emanuele_Z on 2009-05-19
> **cogadh said:**
> Ubuntu wasn't the only one, I believe Fedora went to Pulse around the same time, not sure about any other distros though. I've been asking why Ubuntu went with Pulse since they started with it (8.04? 8.10?), but I've never got a straight answer.

Indeed, that's the problem...
What is the reason behind switching to PA?
ALSA is working great for 95% of users.
Now, people that want enhanced audio can install PA themselves...or am I wrong?

Really, what is the reason behind switching to PA?

Cheers,

---

### Post by hikaricore on 2009-05-19
> **Emanuele_Z said:**
> Indeed, that's the problem...
What is the reason behind switching to PA?
ALSA is working great for 95% of users.
Now, people that want enhanced audio can install PA themselves...or am I wrong?

Really, what is the reason behind switching to PA?

Cheers,


So... screw the other 5% of us? Thanks.

---

### Post by cogadh on 2009-05-19
Damn 5%, ruining it for the rest of us!:p

---

### Post by Devilman13 on 2009-05-21
> **hikaricore said:**
> So... screw the other 5% of us? Thanks.

Basically, yeah. LOL Pulseaudio is teh suck.

---

### Post by alex.rayu on 2009-05-21
It has been lasting for so long now that it should be for everyone who just installs/updates Ubuntu like the first thing you do is to brush your teeth in the morning:

```
$ sudo apt-get remove pulseaudio
```

---

### Post by PacketCollision on 2009-07-27
I solved the problem in CIV4 at least by simply editing /etc/pulse/client.conf and setting "disable-shm = yes" instead of "disable-shm = no".

running:
```
killall pulseaudio && start-pulseaudio-x11
```
should activate the changes.

---

